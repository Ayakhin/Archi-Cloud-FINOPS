# Lab 7: Implementing Azure Functions

## Objectif
L'objectif de ce laboratoire est de créer et de déployer une fonction serverless en utilisant Azure Functions, de l'intégrer avec Azure Storage ou Azure Queue, et de surveiller les performances et les journaux de la fonction.

## Étapes Suivies

### 1. Création d'une Azure Function App

#### Explication
Une Function App est un environnement dans lequel vos fonctions Azure s'exécutent. Elle fournit les ressources nécessaires pour héberger et exécuter vos fonctions.

#### Commandes / Étapes
- Utilisation du **Portail Azure** :
  - Recherche de **Function App** dans la barre de recherche.
  - Cliquez sur **Créer** et remplissez les informations suivantes :
    - Nom de l'application : `MyFunctionApp`
    - Groupe de ressources : `MyResourceGroup`
    - Région : `West Europe`
    - Plan d'hébergement : Plan de consommation (serverless)
    - Runtime stack : `Python`

#### Capture d'écran
![image](https://github.com/user-attachments/assets/cc98f5ba-c9ea-47ad-9a8d-2f930f627691)


### 2. Développement d'une fonction serverless déclenchée par une requête HTTP

#### Explication
Les Azure Functions peuvent être déclenchées par divers événements, comme une requête HTTP. Ici, nous créons une fonction qui répondra à une requête HTTP GET.

#### Commandes / Étapes
- Accédez à la **Function App** créée, puis dans **Functions**, créez une nouvelle fonction avec le déclencheur **HTTP Trigger**.
- Développez votre fonction directement dans l'éditeur Azure avec le code suivant (en JavaScript) :
  
  ```javascript
  module.exports = async function (context, req) {
      const name = (req.query.name || (req.body && req.body.name));
      if (name) {
          context.res = {
              body: "Hello, " + name
          };
      }
      else {
          context.res = {
              status: 400,
              body: "Please pass a name in the query string or in the request body"
          };
      }
  };
```
