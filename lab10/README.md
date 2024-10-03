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

### 2. Configuration de la sauvegarde pour les VMs et les fichiers Azure

#### Explication
Cette étape consiste à sélectionner les ressources que vous souhaitez sauvegarder.

#### Commandes / Étapes
- Dans le vault créé, allez dans **Backup**.
- Sélectionnez **Azure Virtual Machine** ou **Azure File Share**.
- Suivez les instructions pour sélectionner les VMs ou fichiers à sauvegarder.

### 3. Effectuer une opération de sauvegarde

#### Explication
Une sauvegarde manuelle permet de créer une copie instantanée des données pour une récupération future.

#### Commandes / Étapes
- Dans le vault, allez à **Protected items** et cliquez sur **Backup items**.
- Sélectionnez l'élément à sauvegarder.
- Cliquez sur **Backup Now**.

### 4. Restauration d'une opération de sauvegarde

#### Explication
La restauration vous permet de récupérer des données à partir de sauvegardes précédentes.

#### Commandes / Étapes
- Dans **Backup items**, sélectionnez l'élément à restaurer.
- Cliquez sur **Restore** et suivez les instructions pour choisir les options de restauration.

### 5. Implémentation de politiques de sauvegarde et de rétention

#### Explication
Les politiques de sauvegarde définissent la fréquence et la durée de conservation des sauvegardes.

#### Commandes / Étapes
- Dans le vault, cliquez sur **Backup Policies**.
- Créez ou modifiez une politique existante pour définir la fréquence des sauvegardes et les règles de rétention.
- Appliquez cette politique aux ressources sauvegardées.

## Conclusion
Ce laboratoire a permis de découvrir les fonctionnalités de sauvegarde et de restauration offertes par Azure. L'utilisation de Recovery Services Vault facilite la gestion des sauvegardes pour les machines virtuelles et les fichiers, assurant ainsi la protection des données critiques.

## Ressources Utiles
- [Documentation officielle d'Azure sur les Recovery Services Vaults](https://learn.microsoft.com/fr-fr/azure/backup/recovery-services-vault-overview)
- [Guide de sauvegarde pour Azure Virtual Machines](https://learn.microsoft.com/fr-fr/azure/backup/backup-azure-vms)
- [Restaurer des données avec Azure Backup](https://learn.microsoft.com/fr-fr/azure/backup/backup-restore-data)
