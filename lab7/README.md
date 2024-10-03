# Lab 7: Implementing Azure Functions

## Objectif
Le but de ce laboratoire est de créer et de déployer une application serverless en utilisant Azure Functions, et de l'intégrer avec Azure Storage.

## Étapes Suivies

### 1. Création d'une Azure Function App

#### Explication
Azure Functions permet de créer des applications serverless qui réagissent à des événements ou des requêtes HTTP.

#### Commandes / Étapes
- Utilisation du **Portail Azure** : 
  - Recherche de **Function App** dans la barre de recherche.
  - Création d'une application de fonctions avec les options suivantes :
    - Groupe de ressources : `MyResourceGroup`
    - Nom de l'application : `MyFunctionApp`
    - Runtime : `Python 3.9`
    - Plan : `B1 (Basic)`

#### Capture d'écran
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/90718f0f-cd30-4dd0-8fcd-5e74fe0f5f37">



### 2. Développement d'une Fonction HTTP Trigger

#### Explication
Nous avons créé une fonction Python déclenchée par une requête HTTP qui prend un paramètre `name` et retourne un message personnalisé.

#### Commandes / Étapes
- Utilisation du **Portail Azure** :
  - Aller dans la **Function App**, cliquer sur **Functions** et ajouter une nouvelle fonction de type **HTTP Trigger**.
  - Modifier le code pour traiter la requête HTTP et retourner un message.

#### Capture d'écran
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/5cc65dcf-6c2e-49c1-bff4-665fb58bfea7">


### 3. Intégration avec Azure Storage

#### Explication
Nous avons modifié la fonction pour qu'elle enregistre le nom reçu dans une requête HTTP dans un conteneur Azure Blob Storage.

#### Étapes
- Ajouter une bibliothèque Azure Storage dans la fonction :
  - Installer le package `azure-storage-blob` via **requirements.txt** dans la fonction.
- Modifier la fonction pour écrire dans un blob.

#### Capture d'écran
![Integration Azure Storage](./screenshots/azure-storage-integration.png)

### 4. Surveillance et Logs

#### Explication
Nous avons surveillé les performances de la fonction et vérifié les journaux via le portail Azure.

#### Capture d'écran
![Monitoring Function](./screenshots/function-monitoring.png)

### Conclusion
Ce laboratoire m'a permis de découvrir comment créer et déployer des Azure Functions, intégrer une fonction serverless avec Azure Blob Storage et surveiller les performances à l'aide des outils intégrés d'Azure.
