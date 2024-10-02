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
    - Groupe de ressources : `Rayan_Azure`
    - Nom du plan : `MonAppServicePlan`
    - Région : `West US`
    - Tarification : `F1 (Free Tier)`

#### Capture d'écran
1/2
![image](https://github.com/user-attachments/assets/7aedd52c-9727-4243-ac46-ee2170ad3a6f)

2/2
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/79e92f18-b8a6-4b38-aa97-5b1c327e1609">


### 2. Déploiement de l'Application Web

#### Explication
Le déploiement de l'application permet de mettre en ligne un site web ou une API en utilisant l'App Service.

#### Commandes / Étapes
- Utilisation du **Portail Azure** : 
  - Aller dans **App Services** et créer une nouvelle application.
  - Configuration :
    - Nom : `MonApplicationWeb`
    - Plan App Service : `MonAppServicePlan`
    - Runtime : `NODE|18-lts`

#### Capture d'écran
1/2
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/046ad845-d790-4cb7-a985-b3fdf3bb22f2">

2/2
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/a7462f6b-4d0d-4963-896f-b763b241b247">

### 3. Configuration d'un Domaine Personnalisé et Certificat SSL

#### Explication
Afin de rendre l'application plus professionnelle, nous ajoutons un domaine personnalisé et sécurisons la communication via SSL.

#### Étapes
- Ajout d'un domaine personnalisé dans **Custom Domains**.
- Téléversement et configuration du certificat SSL dans **TLS/SSL Settings**.

#### Capture d'écran
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/a7cb4224-ef17-41b8-92a6-c6ed188e26e9">
Ci dessus dans la capture d'écran c'est ici que l'on creer son dommaine personnalisé

<img width="1280" alt="image" src="https://github.com/user-attachments/assets/763bc6ab-a864-4999-a3d7-aa6b8af3d641">
Ci dessus c'est dans cette endroit que figure le certificat SSL/TLS lorsqu'on se met à niveau

Les commandes suivante sur azure CLI permette aussi de le faire 
Ajouter un domaine personnalisé:
az webapp config hostname add --resource-group <ResourceGroupName> --webapp-name <AppName> --hostname <customdomain>

Ajouter un certificat SSL
az webapp config ssl bind --certificate-thumbprint <Thumbprint> --ssl-type SNI --name <AppName> --resource-group <ResourceGroupName>

### 4. Implémentation des "Deployment Slots" (Staging et Production)

#### Explication
Les "Deployment slots" permettent de tester une nouvelle version de l'application sur un environnement de staging avant de la pousser en production.

#### Étapes
- Aller dans **Deployment Slots** de l'application Web.
- Créer un nouveau slot **staging** et y déployer la nouvelle version de l'application.

#### Capture d'écran
<img width="1280" alt="image" src="https://github.com/user-attachments/assets/17faee63-78b0-4073-95d4-64931006beee">
En fesant l'ugrade ont choisi une formule qui nous permettra par le deploiment d'un emplacement 

### Conclusion
Ce laboratoire m'a permis de découvrir le processus de création, déploiement et gestion d'une application web sur Azure, tout en explorant les possibilités de configuration avec des domaines personnalisés et des certificats SSL. L'ajout des "deployment slots" facilite la gestion des versions en staging et production.
