# Lab 4: Managing Azure Storage Accounts and Blobs

## Objectif
L'objectif de ce laboratoire est de créer un compte de stockage Azure avec différentes options de réplication, uploader et gérer des blobs, configurer des signatures d'accès partagé (SAS) pour un accès sécurisé, et mettre en œuvre des politiques de gestion du cycle de vie.

## Étapes Suivies

### 1. Création d'un Compte de Stockage

#### Explication
Le compte de stockage est utilisé pour héberger des données, notamment des blobs. Nous choisissons la réplication **LRS** pour assurer la redondance des données.

#### Commandes / Étapes
- Utilisation de l'**Azure CLI** :
```bash
```

az storage account create --name MonStorageAccount --resource-group MyResourceGroup --location westus --sku Standard_LRS
Capture d'écran

Explication
Les blobs sont des objets de données dans le compte de stockage. Nous allons créer un conteneur et uploader un fichier.

Commandes / Étapes

Capture d'écran

2. Upload de Blobs
Explication
Les blobs sont des objets de données dans le compte de stockage. Nous allons créer un conteneur et uploader un fichier.

Commandes / Étapes
Utilisation de l'Azure CLI :
Créer un conteneur et uploader un fichier :

az storage container create --name monconteneur --account-name MonStorageAccount --public-access blob
az storage blob upload --container-name monconteneur --name monfichier.txt --file /chemin/vers/monfichier.txt --account-name MonStorageAccount


Voici le markdown pour ton README du Lab 4: Managing Azure Storage Accounts and Blobs, formaté de la même manière que pour le Lab 3 :

markdown
Copier le code
# Lab 4: Managing Azure Storage Accounts and Blobs

## Objectif
L'objectif de ce laboratoire est de créer un compte de stockage Azure avec différentes options de réplication, uploader et gérer des blobs, configurer des signatures d'accès partagé (SAS) pour un accès sécurisé, et mettre en œuvre des politiques de gestion du cycle de vie.

## Étapes Suivies

### 1. Création d'un Compte de Stockage

#### Explication
Le compte de stockage est utilisé pour héberger des données, notamment des blobs. Nous choisissons la réplication **LRS** pour assurer la redondance des données.

#### Commandes / Étapes
- Utilisation de l'**Azure CLI** :
  - Créer un compte de stockage avec la commande suivante :
  ```bash
  az storage account create --name MonStorageAccount --resource-group MyResourceGroup --location westus --sku Standard_LRS
Capture d'écran

2. Upload de Blobs
Explication
Les blobs sont des objets de données dans le compte de stockage. Nous allons créer un conteneur et uploader un fichier.

Commandes / Étapes
Utilisation de l'Azure CLI :
Créer un conteneur et uploader un fichier :
bash
Copier le code
az storage container create --name monconteneur --account-name MonStorageAccount --public-access blob
az storage blob upload --container-name monconteneur --name monfichier.txt --file /chemin/vers/monfichier.txt --account-name MonStorageAccount
Capture d'écran

3. Signature d'Accès Partagé (SAS)
Explication
Une signature d'accès partagé permet d'accorder un accès limité aux ressources d'un compte de stockage, sans partager la clé d'accès.

Commandes / Étapes
Utilisation de l'Azure CLI :
Générer une SAS pour le conteneur :

az storage container generate-sas --name monconteneur --account-name MonStorageAccount --permissions rwdl --expiry 2024-10-10T00:00Z --https-only

Capture d'écran

4. Mise en Place des Politiques de Gestion du Cycle de Vie
Explication
Les politiques de gestion du cycle de vie permettent d'automatiser la gestion des données, comme la suppression de blobs après une certaine période.

Commandes / Étapes
Utilisation de l'Azure CLI :
Appliquer une politique de gestion du cycle de vie :

az storage account management-policy create --account-name MonStorageAccount --policy @lifecycle-policy.json

az storage account management-policy create --account-name MonStorageAccount --policy @lifecycle-policy.json

Capture d'écran

Conclusion
Ce laboratoire a permis de configurer un compte de stockage Azure, d'uploader des blobs, de mettre en place des SAS pour un accès sécurisé, et d'implémenter des politiques de gestion du cycle de vie. Ces compétences sont essentielles pour la gestion efficace des données sur Azure.
