# Lab 12: Using Azure Resource Manager (ARM) Templates

## Objectif
Ce laboratoire a pour but de déployer une application multi-tier sur Azure en utilisant un **Azure Resource Manager (ARM) template**. Nous allons paramétrer le modèle, le déployer via Azure CLI, et valider les déploiements tout en résolvant les éventuelles erreurs.

## Étapes

### 1. Créer un Modèle ARM
Nous avons défini un modèle ARM qui contient la structure de base suivante :
- **Backend** : Une base de données SQL.
- **Frontend** : Une machine virtuelle ou un service App Web.

#### Exemple de structure JSON de base :
```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {},
  "variables": {},
  "resources": [
    // Backend : Base de données SQL
    // Frontend : Application Web ou Machine Virtuelle
  ],
  "outputs": {}
}
```

2. Paramétrer le Modèle
Nous avons ajouté des paramètres pour rendre le modèle plus réutilisable. Par exemple, nous avons défini un paramètre pour le nom du groupe de ressources et la région :

```json
"parameters": {
  "resourceGroupName": {
    "type": "string",
    "defaultValue": "myResourceGroup",
    "metadata": {
      "description": "Nom du groupe de ressources."
    }
  }
}
```



4. Déployer les Ressources via Azure CLI
Nous avons utilisé Azure CLI pour déployer les ressources définies dans notre modèle ARM.

Commandes utilisées :
Création du groupe de ressources :

```bash
az group create --name myResourceGroup --location eastus
```

Déploiement du modèle :
```bash
az deployment group create --resource-group myResourceGroup --template-file ./template.json
```

4. Validation et Dépannage
Nous avons également validé le modèle avant le déploiement pour nous assurer qu'il ne contenait pas d'erreurs :

```bash
az deployment group validate --resource-group myResourceGroup --template-file ./template.json
```

```bash
az deployment group show --name deploymentName --resource-group myResourceGroup
```

Résultat
Le déploiement a réussi, et nous avons maintenant une application multi-tier en place avec un backend de base de données SQL et un frontend hébergé sur Azure.

Screenshots
Capture d'écran 1 : Modèle ARM JSON.
Capture d'écran 2 : Déploiement du modèle via Azure CLI.
Capture d'écran 3 : Résultat final dans le portail Azure.
Conclusion
Ce laboratoire a permis d'apprendre comment utiliser les ARM templates pour automatiser et standardiser le déploiement de ressources sur Azure. L'automatisation via ARM rend la gestion de l'infrastructure plus efficace et réplicable.
