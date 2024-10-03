# Lab 14: Configuration d'Azure DNS et Domaines Personnalisés

## Objectifs du Lab
- Créer une zone DNS Azure.
- Gérer les enregistrements DNS pour un domaine personnalisé.
- Configurer la vérification de domaine et le mapping pour les services Azure.
- Implémenter des alias DNS (CNAME) et des ensembles d'enregistrements.

## Étape 1 : Créer une Zone DNS Azure
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Cliquez sur **"Créer une ressource"** dans le menu de gauche.
3. Recherchez **"Zone DNS"** et sélectionnez-la.
4. Cliquez sur **"Créer"** et remplissez les informations requises.
   - Nom de la zone : `exemple.com`
   - Groupe de ressources : `Nom_du_groupe`
   - Région : `westus`
5. Cliquez sur **"Vérifier + créer"**, puis sur **"Créer"**.

![image](https://github.com/user-attachments/assets/c52013e7-1b8e-4997-a9fb-67fe4760270c)


## Étape 2 : Gérer les Enregistrements DNS
1. Accédez à votre **Zone DNS** depuis le portail Azure.
2. Cliquez sur **"Enregistrements"**.
3. Cliquez sur **"Ajouter un enregistrement"**.
4. Choisissez le type d'enregistrement à ajouter (A, CNAME, etc.) et remplissez les informations nécessaires.

![image](https://github.com/user-attachments/assets/8de490ca-4995-4b7b-9fb3-ca59f4864d0c)


## Étape 3 : Configurer la Vérification de Domaine
1. Ajoutez un enregistrement TXT pour prouver que vous possédez le domaine, en suivant les instructions fournies par le service Azure.

<img width="1280" alt="image" src="https://github.com/user-attachments/assets/ecdaf854-ba29-4dfb-a263-0fc46f6b0707">
Nécéssite d'utiliser le domaines personnaliser mais pour cela il faut se mettre à jour et cela dépasse mon budget au niveau de la formule

## Étape 4 : Implémenter des Alias DNS (CNAME)
1. Retournez à votre zone DNS.
2. Cliquez sur **"Ajouter un enregistrement"** et choisissez **CNAME**.
3. Remplissez les détails nécessaires et cliquez sur **"OK"**.

![image](https://github.com/user-attachments/assets/874f29bd-9a14-4839-a03d-be70718fd7c9)


## Étape 5 : Tester la Configuration DNS
1. Utilisez des outils comme `nslookup` ou des vérificateurs DNS en ligne pour tester vos enregistrements DNS.

   ```bash
   nslookup exemple.com
   ```
