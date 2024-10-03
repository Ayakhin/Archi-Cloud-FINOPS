# Lab 8: Using Azure Cognitive Services

## Objectif
L'objectif de ce laboratoire est de créer une ressource Cognitive Services, de développer une application qui utilise l'API Text Analytics, d'analyser le sentiment et les phrases clés à partir d'un texte d'exemple, et de surveiller l'utilisation de l'API tout en gérant les clés.

## Étapes Suivies

### 1. Création d'une Ressource Cognitive Services

#### Explication
La ressource Cognitive Services permet d'accéder aux fonctionnalités d'IA d'Azure, notamment l'analyse de texte.

#### Commandes / Étapes
- Utilisation du **Portail Azure** :
  - Accéder au **Portail Azure** et cliquer sur **Créer une ressource**.
  - Rechercher **Cognitive Services** et sélectionner **Text Analytics**.
  - Remplir les informations nécessaires :
    - Nom de la ressource : MyCognitiveService
    - Région : West US
    - Type de tarification : F0 (Standard)
    - Groupe de ressources : MyResourceGroup
  - Cliquer sur **Créer**.

#### Capture d'écran
![image](https://github.com/user-attachments/assets/e2339aeb-21cb-4919-8bbe-8908b983afeb)


### 2. Développement d'une Application Utilisant l'API Text Analytics

#### Explication
Développer une application pour interagir avec l'API Text Analytics et analyser le sentiment d'un texte donné.

#### Commandes / Étapes
- Utilisation de **C#** :

  - Écrire le code pour analyser le sentiment :
```C#
using System;
using System.IO;
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Text.Json.Serialization;
using System.Threading.Tasks;

namespace CluSample
{
    public class Program
    {
        private static HttpClient _client;
        private static string _baseUri;
        public static async Task Main()
        {
            // Setup
            // _baseUri = "https://westus2.api.cognitive.microsoft.com/language/customize-conversation";
            // _baseUri = "https://cluresource.cognitiveservices.azure.com/language/customize-conversation";
            _baseUri = "https://YOUR_ENDPOINT/language/customize-conversation";

            _client = new HttpClient();
            _client.DefaultRequestHeaders.Add("ocp-apim-subscription-key" "YOUR_API_KEY");

            var projectName = "mytestproject";

            // Create new project by importing a project's JSON file.
            var projectJson = File.ReadAllText("my_clu_project.json");
            await ImportProjectAsync(projectName, projectJson);

            // Train the project.
            await TrainProjectAsync(projectName "myfirstmodel");

            // Deploy the trained model.
            await DeployProjectAsync(projectName "myfirstmodel" "production");
        }

        private static async Task ImportProjectAsync(string projectName, string projectJson)
        {
            string pollingUrl;

            // Submit the import request.
            using (var content = new StringContent(projectJson, Encoding.UTF8 "application/json"))
            {
                // Specify the format of the file being imported. 
                content.Headers.Add("format" "clu");

                var requestUri = $"{_baseUri}/projects/{projectName}/import?api-version=DEFINE-API-VERSION";
                using (var response = await _client.PostAsync(requestUri, content))
                {
                    response.EnsureSuccessStatusCode();
                    pollingUrl = response.Headers.Location.AbsoluteUri;
                }
            }

            // Wait for the import to finish.
            var importSucceeded = false;
            do
            {
                using (var response = await _client.GetAsync(pollingUrl))
                {
                    response.EnsureSuccessStatusCode();
                    var responseBody = await response.Content.ReadAsStringAsync();

                    var jobDetails = JsonSerializer.Deserialize<JobDetails>(responseBody);
                    if (jobDetails.Status == JobStatus.failed)
                    {
                        throw new Exception($"Deployment failed. JobId: {jobDetails.JobId}");
                    }

                    importSucceeded = jobDetails.Status == JobStatus.succeeded;
                }

                await Task.Delay(TimeSpan.FromSeconds(1));
            }
            while (!importSucceeded);
        }

        private static async Task TrainProjectAsync(string projectName, string modelName)
        {
            var trainingRequestPayload = new TrainingRequestPayload { TrainingModelName = modelName };

            string pollingUrl;

            // Submit the training request.
            var body = JsonSerializer.Serialize(trainingRequestPayload);
            using (var content = new StringContent(body, Encoding.UTF8 "application/json"))
            {
                var requestUri = $"{_baseUri}/projects/{projectName}/train?api-version=2021-07-15-preview";
                using (var response = await _client.PostAsync(requestUri, content))
                {
                    response.EnsureSuccessStatusCode();
                    pollingUrl = response.Headers.Location.AbsoluteUri;
                }
            }

            // Wait for the training to finish. This may take some time.
            var trainingSucceeded = false;
            do
            {
                using (var response = await _client.GetAsync(pollingUrl))
                {
                    response.EnsureSuccessStatusCode();
                    var responseBody = await response.Content.ReadAsStringAsync();

                    var jobDetails = JsonSerializer.Deserialize<JobDetails>(responseBody);
                    if (jobDetails.Status == JobStatus.failed)
                    {
                        throw new Exception($"Training failed. JobId: {jobDetails.JobId}");
                    }

                    trainingSucceeded = jobDetails.Status == JobStatus.succeeded;
                }

                await Task.Delay(TimeSpan.FromSeconds(1));
            }
            while (!trainingSucceeded);
        }

        private static async Task DeployProjectAsync(string projectName, string modelName, string deploymentName)
        {
            var deploymentRequestPayload = new DeploymentRequestPayload { TrainingModelName = modelName };

            string pollingUrl;

            // Create or update the deployment to point to our latest deployed model.
            var body = JsonSerializer.Serialize(deploymentRequestPayload);
            using (var content = new StringContent(body, Encoding.UTF8 "application/json"))
            {
                var requestUri = $"{_baseUri}/projects/{projectName}/deployments/{deploymentName}?api-version=2021-07-15-preview";
                using (var response = await _client.PutAsync(requestUri, content))
                {
                    response.EnsureSuccessStatusCode();
                    pollingUrl = response.Headers.Location.AbsoluteUri;
                }
            }

            // Wait for the deployment to finish.
            var deploymentSucceeded = false;
            do
            {
                using (var response = await _client.GetAsync(pollingUrl))
                {
                    response.EnsureSuccessStatusCode();
                    var responseBody = await response.Content.ReadAsStringAsync();

                    var jobDetails = JsonSerializer.Deserialize<JobDetails>(responseBody);
                    if (jobDetails.Status == JobStatus.failed)
                    {
                        throw new Exception($"Deployment failed. JobId: {jobDetails.JobId}");
                    }

                    deploymentSucceeded = jobDetails.Status == JobStatus.succeeded;
                }

                await Task.Delay(TimeSpan.FromSeconds(1));
            }
            while (!deploymentSucceeded);
        }

        private class TrainingRequestPayload
        {
            [JsonPropertyName("trainingModelName")]
            public string TrainingModelName { get; set; }
        }

        private class DeploymentRequestPayload
        {
            [JsonPropertyName("trainingModelName")]
            public string TrainingModelName { get; set; }
        }

        private class JobDetails
        {
            /// <summary>
            /// Gets or sets the Job ID.
            /// </summary>
            [JsonPropertyName("jobId")]
            public string JobId { get; set; }

            /// <summary>
            /// Gets or sets the Job Created Date Time.
            /// </summary>
            [JsonPropertyName("createdDateTime")]
            public DateTime CreatedDateTime { get; set; }

            /// <summary>
            /// Gets or sets the Job Last Updated Date Time.
            /// </summary>
            [JsonPropertyName("lastUpdatedDateTime")]
            public DateTime LastUpdatedDateTime { get; set; }

            /// <summary>
            /// Gets or sets the Job Expiration Date Time.
            /// </summary>
            [JsonPropertyName("expirationDateTime")]
            public DateTime? ExpirationDateTime { get; set; }

            /// <summary>
            /// Gets or sets the Job Status.
            /// </summary>
            [JsonPropertyName("status")]
            public JobStatus Status { get; set; }
        }

        [JsonConverter(typeof(JsonStringEnumConverter))]
        private enum JobStatus
        {
            notStarted
            inProgress
            succeeded
            partialSuccess = 4
            failed
        }
    }
}
```

#### Capture d'écran
![image](https://github.com/user-attachments/assets/722d5eea-6ff1-4d01-a774-569f9731431d)


### 3. Analyse du Sentiment et des Phrases Clés

#### Explication
Utiliser les fonctionnalités de l'API pour analyser le sentiment et extraire des phrases clés du texte fourni.

#### Commandes / Étapes
- Pour analyser des phrases clés, utiliser :
    ```python
    var response = client.ExtractKeyPhrases("My cat might need to see a veterinarian.");
    ```

### 4. Surveillance de l'utilisation de l'API et Gestion des Clés

#### Explication
Surveiller l'utilisation de l'API et gérer les clés d'accès à partir du portail Azure.

#### Commandes / Étapes
- Accéder à la ressource Cognitive Services dans le **Portail Azure**.
- Vérifier les statistiques d'utilisation sous la section **Analyse**.
- Gérer les clés sous **Clés et points de terminaison**.

### Conclusion
Ce laboratoire m'a permis de découvrir comment créer et interagir avec une ressource Cognitive Services sur Azure, d'analyser le sentiment et d'extraire des phrases clés à partir de textes. Cela m'a également familiarisé avec la gestion des clés et la surveillance de l'utilisation des API.
