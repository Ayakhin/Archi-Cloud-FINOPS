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
<img width="1280" alt="Capture d'écran 2024-10-02 142935" src="https://github.com/user-attachments/assets/fb0934f5-44fd-4d76-9bca-17b843331777">


Explication
Les blobs sont des objets de données dans le compte de stockage. Nous allons créer un conteneur et uploader un fichier.

2. Upload de Blobs
Explication
Les blobs sont des objets de données dans le compte de stockage. Nous allons créer un conteneur et uploader un fichier.

Capture d'écran
1/2
<img width="1280" alt="Capture d'écran 2024-10-02 155837" src="https://github.com/user-attachments/assets/3326f483-236c-4764-a039-246b2db95bcf">

2/2
<img width="1280" alt="Capture d'écran 2024-10-02 161418" src="https://github.com/user-attachments/assets/7164fdd7-907c-4418-815e-f12d6c1bbc4c">

Commandes / Étapes
Utilisation de l'Azure CLI :
Créer un conteneur et uploader un fichier :

az storage container create --name monconteneur --account-name MonStorageAccount --public-access blob
az storage blob upload --container-name monconteneur --name monfichier.txt --file /chemin/vers/monfichier.txt --account-name MonStorageAccount


3. Signature d'Accès Partagé (SAS)
Explication
Une signature d'accès partagé permet d'accorder un accès limité aux ressources d'un compte de stockage, sans partager la clé d'accès.

Commandes / Étapes
Utilisation de l'Azure CLI :
Générer une SAS pour le conteneur :

az storage container generate-sas --name monconteneur --account-name MonStorageAccount --permissions rwdl --expiry 2024-10-10T00:00Z --https-only

Capture d'écran
<img width="1280" alt="Capture d'écran 2024-10-02 162547" src="https://github.com/user-attachments/assets/90927c63-9990-4132-b300-29217ba82a26">


4. Mise en Place des Politiques de Gestion du Cycle de Vie
Explication
Les politiques de gestion du cycle de vie permettent d'automatiser la gestion des données, comme la suppression de blobs après une certaine période.

Commandes / Étapes
Utilisation de l'Azure CLI :
Appliquer une politique de gestion du cycle de vie :

az storage account management-policy create --account-name MonStorageAccount --policy @lifecycle-policy.json

az storage account management-policy create --account-name MonStorageAccount --policy @lifecycle-policy.json

Capture d'écran
<img width="1280" alt="Capture d'écran 2024-10-02 162927" src="https://github.com/user-attachments/assets/0348ebf4-2c39-4b0f-b8e0-f76158647f23">

Conclusion
Ce laboratoire a permis de configurer un compte de stockage Azure, d'uploader des blobs, de mettre en place des SAS pour un accès sécurisé, et d'implémenter des politiques de gestion du cycle de vie. Ces compétences sont essentielles pour la gestion efficace des données sur Azure.
