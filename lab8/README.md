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
    - Région : West Europe
    - Type de tarification : S0 (Standard)
    - Groupe de ressources : MyResourceGroup
  - Cliquer sur **Créer**.

#### Capture d'écran
![Création Ressource Cognitive Services](./screenshots/cognitive-services-resource.png)

### 2. Développement d'une Application Utilisant l'API Text Analytics

#### Explication
Développer une application pour interagir avec l'API Text Analytics et analyser le sentiment d'un texte donné.

#### Commandes / Étapes
- Utilisation de **Python** :
  - Installer la bibliothèque Azure :
    ```bash
    pip install azure-ai-textanalytics
    ```
  - Écrire le code pour analyser le sentiment :
    ```python
    from azure.ai.textanalytics import TextAnalyticsClient
    from azure.core.credentials import AzureKeyCredential

    endpoint = "https://<YOUR_RESOURCE_NAME>.cognitiveservices.azure.com/"
    key = "<YOUR_KEY>"
    text_analytics_client = TextAnalyticsClient(endpoint=endpoint, credential=AzureKeyCredential(key))

    documents = ["I had a wonderful experience!"]
    response = text_analytics_client.analyze_sentiment(documents=documents)

    for doc in response:
        print(f"Sentiment: {doc.sentiment}, Confidence scores: {doc.confidence_scores}")
    ```

#### Capture d'écran
![Développement Application API](./screenshots/development-api.png)

### 3. Analyse du Sentiment et des Phrases Clés

#### Explication
Utiliser les fonctionnalités de l'API pour analyser le sentiment et extraire des phrases clés du texte fourni.

#### Commandes / Étapes
- Pour analyser des phrases clés, utiliser :
    ```python
    key_phrases_response = text_analytics_client.extract_key_phrases(documents=documents)
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
