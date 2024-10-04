# Lab 15: Implementing Azure DevOps for CI/CD Pipelines

## Introduction
Dans ce laboratoire, nous allons configurer Azure DevOps pour créer des pipelines CI/CD afin de construire et déployer une application sur Azure App Service.

## Étape 1: Créer une organisation et un projet Azure DevOps

1. **Accéder à Azure DevOps**
   - Allez sur [Azure DevOps](https://dev.azure.com) et connectez-vous.

   ![image](https://github.com/user-attachments/assets/040149f7-bca5-425e-9f0a-3b54170c581a)


2. **Créer une organisation**
   - Cliquez sur "Créer une organisation" et suivez les instructions.

   ![Capture d'écran de la création d'une organisation](chemin/vers/votre/capture2.png)

3. **Créer un projet**
   - Cliquez sur "Nouveau projet", donnez un nom à votre projet et cliquez sur "Créer".

   ![Capture d'écran de la création d'une organisation](chemin/vers/votre/capture2.png)

## Étape 2: Créer un dépôt Git et commettre du code

1. **Accéder au dépôt**
   - Dans votre projet, allez dans l'onglet "Repos   ".

   ![image](https://github.com/user-attachments/assets/06ae3d95-9129-4d73-8cbe-343167ea956a)

2. **Créer un nouveau dépôt**
   - Cliquez sur "Nouveau dépôt" et donnez-lui un nom.

   ![Capture d'écran de la création d'un dépôt](chemin/vers/votre/capture5.png)

3. **Cloner le dépôt et ajouter du code**
   - Clonez le dépôt localement, ajoutez votre code et commettez-le.

   ![Capture d'écran du clonage du dépôt](chemin/vers/votre/capture6.png)

## Étape 3: Configurer un pipeline CI

1. **Accéder aux pipelines**
   - Allez dans l'onglet "Pipelines".

   ![Capture d'écran de l'onglet Pipelines](chemin/vers/votre/capture7.png)

2. **Créer un nouveau pipeline**
   - Cliquez sur "Créer pipeline" et sélectionnez votre dépôt.

   ![Capture d'écran de la création d'un pipeline](chemin/vers/votre/capture8.png)

3. **Configurer le pipeline**
   - Ajoutez votre configuration YAML pour le pipeline CI.

   ![Capture d'écran de la configuration YAML](chemin/vers/votre/capture9.png)

4. **Enregistrer et exécuter le pipeline**
   - Cliquez sur "Enregistrer et exécuter".

   ![Capture d'écran de l'exécution du pipeline](chemin/vers/votre/capture10.png)

## Étape 4: Configurer un pipeline CD

1. **Créer un pipeline de publication**
   - Allez dans l'onglet "Pipelines de publication" et cliquez sur "Créer un pipeline de publication".

   ![Capture d'écran de la création d'un pipeline de publication](chemin/vers/votre/capture11.png)

2. **Sélectionner un modèle**
   - Choisissez un modèle de déploiement pour Azure App Service.

   ![Capture d'écran de la sélection d'un modèle de déploiement](chemin/vers/votre/capture12.png)

3. **Configurer le pipeline**
   - Configurez les paramètres de votre application et les déclencheurs.

   ![Capture d'écran de la configuration du pipeline de publication](chemin/vers/votre/capture13.png)

4. **Enregistrer et exécuter le pipeline**
   - Enregistrez votre pipeline de publication et exécutez-le.

   ![Capture d'écran de l'exécution du pipeline de publication](chemin/vers/votre/capture14.png)

## Conclusion
Nous avons mis en place un projet Azure DevOps avec des pipelines CI/CD pour construire et déployer une application sur Azure App Service. Ce laboratoire a démontré comment automatiser le processus de développement et de déploiement à l'aide d'Azure DevOps.

## Références
- [Documentation Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/?view=azure-devops)
