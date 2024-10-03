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

![Capture d'écran - Création de la zone DNS](URL_DE_VOTRE_CAPTURE_1)

## Étape 2 : Gérer les Enregistrements DNS
1. Accédez à votre **Zone DNS** depuis le portail Azure.
2. Cliquez sur **"Enregistrements"**.
3. Cliquez sur **"Ajouter un enregistrement"**.
4. Choisissez le type d'enregistrement à ajouter (A, CNAME, etc.) et remplissez les informations nécessaires.

![Capture d'écran - Gestion des enregistrements DNS](URL_DE_VOTRE_CAPTURE_2)

## Étape 3 : Configurer la Vérification de Domaine
1. Ajoutez un enregistrement TXT pour prouver que vous possédez le domaine, en suivant les instructions fournies par le service Azure.
   
![Capture d'écran - Configuration de la vérification de domaine](URL_DE_VOTRE_CAPTURE_3)

## Étape 4 : Implémenter des Alias DNS (CNAME)
1. Retournez à votre zone DNS.
2. Cliquez sur **"Ajouter un enregistrement"** et choisissez **CNAME**.
3. Remplissez les détails nécessaires et cliquez sur **"OK"**.

![Capture d'écran - Ajout d'un enregistrement CNAME](URL_DE_VOTRE_CAPTURE_4)

## Étape 5 : Tester la Configuration DNS
1. Utilisez des outils comme `nslookup` ou des vérificateurs DNS en ligne pour tester vos enregistrements DNS.

   ```bash
   nslookup exemple.com
