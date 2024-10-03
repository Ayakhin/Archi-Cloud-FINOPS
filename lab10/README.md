# Lab 10: Configuring Azure Backup and Recovery Services

## Objectif
L'objectif de ce laboratoire est de configurer et gérer les sauvegardes pour les machines virtuelles (VM) et les fichiers Azure en utilisant les services de sauvegarde d'Azure. Ce laboratoire inclut la création d'un Recovery Services Vault, la configuration des politiques de sauvegarde, et l'exécution d'opérations de sauvegarde et de restauration.

## Étapes Suivies

### 1. Création d'un Recovery Services Vault

#### Explication
Le Recovery Services Vault est un service de stockage pour vos sauvegardes. Il permet de gérer les sauvegardes et les restaurations de manière centralisée.

#### Commandes / Étapes
- Accédez au **Portail Azure**.
- Cherchez **Recovery Services vaults** et sélectionnez l'option.
- Cliquez sur **Ajouter** et remplissez les informations :
  - **Nom** : Choisissez un nom pour votre vault.
  - **Abonnement** : Sélectionnez l'abonnement Azure.
  - **Groupe de ressources** : Créez un nouveau groupe ou choisissez-en un existant.
  - **Région** : Choisissez la région pour le vault.
- Cliquez sur **Vérifier + créer**, puis sur **Créer**.

Capture d'écran
1/2
![image](https://github.com/user-attachments/assets/eec58171-ce98-4af9-bf01-00714614fffe)

2/2
![image](https://github.com/user-attachments/assets/eeaf3c2e-c073-446e-8f47-264a4ccfdb7a)


### 2. Configuration de la sauvegarde pour les VMs et les fichiers Azure

#### Explication
Cette étape consiste à sélectionner les ressources que vous souhaitez sauvegarder.

#### Commandes / Étapes
- Dans le vault créé, allez dans **Backup**.
- Sélectionnez **Azure Virtual Machine** ou **Azure File Share**.
- Suivez les instructions pour sélectionner les VMs ou fichiers à sauvegarder.

Capture d'écran
1/2
![image](https://github.com/user-attachments/assets/86cae3e0-6225-491b-9dbc-1e01a82c929b)
2/2
![image](https://github.com/user-attachments/assets/4cbc28e2-ddac-4618-9e92-88ef20de59dc)


### 3. Effectuer une opération de sauvegarde

#### Explication
Une sauvegarde manuelle permet de créer une copie instantanée des données pour une récupération future.

#### Commandes / Étapes
- Dans le vault, allez à **Protected items** et cliquez sur **Backup items**.
- Sélectionnez l'élément à sauvegarder.
- Cliquez sur **Sauvegarder maintenant**

Capture d'écran
1/3
![image](https://github.com/user-attachments/assets/a0bc034d-67e1-40ba-8976-d6c61e4eb019)

2/3
![image](https://github.com/user-attachments/assets/0c921e81-a709-48ba-8dbe-8ab361cb70fb)

3/3



### 4. Restauration d'une opération de sauvegarde

#### Explication
La restauration vous permet de récupérer des données à partir de sauvegardes précédentes.

#### Commandes / Étapes
- Dans **Backup items**, sélectionnez l'élément à restaurer.
- Cliquez sur **Restore** et suivez les instructions pour choisir les options de restauration.

Capture d'écran
![image](https://github.com/user-attachments/assets/88634075-ff92-4ad5-ae6c-e5ef8f2858dc)

### 5. Implémentation de politiques de sauvegarde et de rétention

#### Explication
Les politiques de sauvegarde définissent la fréquence et la durée de conservation des sauvegardes.

#### Commandes / Étapes
- Dans le vault, cliquez sur **Backup Policies**.
- Créez ou modifiez une politique existante pour définir la fréquence des sauvegardes et les règles de rétention.
- Appliquez cette politique aux ressources sauvegardées.

Capture d'écran
1/2
![image](https://github.com/user-attachments/assets/d8aabb6d-c3db-4b75-a6d8-8b096bf0b8e0)

2/2
![image](https://github.com/user-attachments/assets/1219f0ae-5ac9-4ecd-bac5-49955aafe4cd)

## Conclusion
Ce laboratoire a permis de découvrir les fonctionnalités de sauvegarde et de restauration offertes par Azure. L'utilisation de Recovery Services Vault facilite la gestion des sauvegardes pour les machines virtuelles et les fichiers, assurant ainsi la protection des données critiques.

## Ressources Utiles
- [Documentation officielle d'Azure sur les Recovery Services Vaults](https://learn.microsoft.com/fr-fr/azure/backup/recovery-services-vault-overview)
- [Guide de sauvegarde pour Azure Virtual Machines](https://learn.microsoft.com/fr-fr/azure/backup/backup-azure-vms)
- [Restaurer des données avec Azure Backup](https://learn.microsoft.com/fr-fr/azure/backup/backup-restore-data)
