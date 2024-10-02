# Lab 3: Deploying Azure App Service Web Apps

## Objectif
L'objectif de ce laboratoire est de déployer une application web en utilisant Azure App Service, configurer un domaine personnalisé et des certificats SSL, et implémenter des "deployment slots" pour staging et production.

## Étapes Suivies

### 1. Création d'un App Service Plan

#### Explication
L'App Service Plan est le socle sur lequel sera déployée notre application. Il détermine la puissance de calcul et la configuration de l'application.

#### Commandes / Étapes
- Utilisation du **Portail Azure** : 
  - Recherche de **App Service Plans** dans la barre de recherche.
  - Création d'un plan avec les options suivantes : 
    - Groupe de ressources : `MyResourceGroup`
    - Nom du plan : `MyAppServicePlan`
    - Région : `West Europe`
    - Tarification : `F1 (Free Tier)`

#### Capture d'écran
![Création App Service Plan](./screenshots/app-service-plan.png)

### 2. Déploiement de l'Application Web

#### Explication
Le déploiement de l'application permet de mettre en ligne un site web ou une API en utilisant l'App Service.

#### Commandes / Étapes
- Utilisation du **Portail Azure** : 
  - Aller dans **App Services** et créer une nouvelle application.
  - Configuration :
    - Nom : `MyWebApp`
    - Plan App Service : `MyAppServicePlan`
    - Runtime : `Node.js 14`

#### Capture d'écran
![Déploiement Web App](./screenshots/web-app-deployment.png)

### 3. Configuration d'un Domaine Personnalisé et Certificat SSL

#### Explication
Afin de rendre l'application plus professionnelle, nous ajoutons un domaine personnalisé et sécurisons la communication via SSL.

#### Étapes
- Ajout d'un domaine personnalisé dans **Custom Domains**.
- Téléversement et configuration du certificat SSL dans **TLS/SSL Settings**.

#### Capture d'écran
![Configuration Domaine Personnalisé](./screenshots/custom-domain-ssl.png)

### 4. Implémentation des "Deployment Slots" (Staging et Production)

#### Explication
Les "Deployment slots" permettent de tester une nouvelle version de l'application sur un environnement de staging avant de la pousser en production.

#### Étapes
- Aller dans **Deployment Slots** de l'application Web.
- Créer un nouveau slot **staging** et y déployer la nouvelle version de l'application.

#### Capture d'écran
![Deployment Slots](./screenshots/deployment-slots.png)

### Conclusion
Ce laboratoire m'a permis de découvrir le processus de création, déploiement et gestion d'une application web sur Azure, tout en explorant les possibilités de configuration avec des domaines personnalisés et des certificats SSL. L'ajout des "deployment slots" facilite la gestion des versions en staging et production.
