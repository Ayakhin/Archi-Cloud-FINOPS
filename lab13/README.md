# Lab 13: Implémentation d'Azure Key Vault

## Objectif

Ce laboratoire vise à implémenter Azure Key Vault pour la gestion des secrets, des clés et des certificats, ainsi que pour intégrer Key Vault avec une application.

## Étape 1 : Création d'Azure Key Vault

1. **Connexion au Portail Azure**
   - Connectez-vous à [portal.azure.com](https://portal.azure.com).

2. **Création d'un Groupe de Ressources**
   - Allez dans **"Groupes de ressources"**.
   - Cliquez sur **"Ajouter"** pour créer un nouveau groupe.
   - Remplissez les informations nécessaires, puis cliquez sur **"Créer"**.

3. **Création du Key Vault**
   - Cliquez sur **"Créer une ressource"**.
   - Recherchez **"Key Vault"** et sélectionnez-le.
   - Cliquez sur **"Créer"**.
   - Remplissez les informations : nom, groupe de ressources et localisation.
   - Cliquez sur **"Vérifier + créer"**, puis sur **"Créer"**.


Capture d'écran

![image](https://github.com/user-attachments/assets/f254a166-d749-48ab-a766-f8c935e2d9f1)

## Étape 2 : Stockage et Récupération de Secrets, Clés et Certificats

### Stockage d'un Secret

1. Ouvrez le Key Vault créé.
2. Cliquez sur **"Secrets"**.
3. Cliquez sur **"Générer/Importer"**.
4. Remplissez le nom et la valeur du secret.
5. Cliquez sur **"Créer"**.

Capture d'écran

![image](https://github.com/user-attachments/assets/852a813f-3b59-435c-b812-43e49712323a)

### Récupération d'un Secret

1. Accédez à la section **"Secrets"** de votre Key Vault.
2. Cliquez sur le secret pour voir sa valeur.

Capture d'écran

![image](https://github.com/user-attachments/assets/8779d369-0511-43e8-b25f-94b92022f336)

### Stockage d'une Clé

1. Dans le menu, cliquez sur **"Clés"**.
2. Cliquez sur **"Générer/Importer"**.
3. Remplissez le nom et le type de protection.
4. Cliquez sur **"Créer"**.

Capture d'écran

![image](https://github.com/user-attachments/assets/7f9128a6-6376-481b-b159-c65a991b582e)

### Récupération d'une Clé

1. Dans la section **"Clés"**, cliquez sur le nom de la clé pour voir les détails.

Capture d'écran

![image](https://github.com/user-attachments/assets/d18be5f7-2bae-4b92-926a-32a6e5de73c8)

### Stockage d'un Certificat (Optionnel)

1. Dans le menu, cliquez sur **"Certificats"**.
2. Cliquez sur **"Générer/Importer"**.
3. Remplissez les informations requises.
4. Cliquez sur **"Créer"**.

Capture d'écran

![image](https://github.com/user-attachments/assets/de26bcef-f193-4edc-b5d6-04ac84b4ba4f)


### Récupération d'un Certificat

1. Accédez à la section **"Certificats"** et cliquez sur le certificat créé pour voir ses détails.

Capture d'écran

![image](https://github.com/user-attachments/assets/18efc6c6-3ad0-49f5-8a40-c68f9bc0aac0)

## Étape 3 : Intégration de Key Vault avec une Application

1. **Configuration de l'Application**
   - Assurez-vous que votre application peut accéder à Key Vault en configurant les permissions.

2. **Ajout d'une Politique d'Accès**
   - Dans le menu de gauche, allez dans **"Politiques d'accès"**.
   - Cliquez sur **"Ajouter une politique d'accès"**.
   - Sélectionnez les autorisations souhaitées et le principal.
   - Cliquez sur **"Enregistrer"**.

Capture d'écran

![image](https://github.com/user-attachments/assets/f6a91552-c44c-4a09-8230-3939a71136c2)

## Étape 4 : Configuration de la Surveillance

1. Allez dans **"Journaux d'activité"** pour voir l'historique des opérations.
2. Configurez des alertes si nécessaire en cliquant sur **"Alertes"** et en suivant les instructions.

Capture d'écran

![image](https://github.com/user-attachments/assets/4d4b0603-5eee-4ad7-97bf-d673486ac2cc)

## Étape 5 : Utilisation d'une Clé dans une Application

1. **Développement de l'Application**
   - Utilisez les SDK Azure appropriés pour récupérer des secrets ou des clés.

2. **Test de l'Application**
   - Vérifiez que l'application peut accéder aux secrets ou clés sans problème.

## Conclusion

Ce laboratoire a démontré comment utiliser Azure Key Vault pour gérer efficacement les secrets, les clés et les certificats, et comment intégrer Key Vault avec une application pour sécuriser la gestion des secrets.
