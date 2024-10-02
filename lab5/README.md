# Lab 5: Implementing Azure SQL Databases

## Objectif
L'objectif de ce laboratoire est de déployer une base de données SQL sur Azure, de configurer les règles de pare-feu pour autoriser l'accès des clients, d'importer des données dans la base, et de configurer la géo-réplication pour assurer la haute disponibilité.

## Étapes Suivies

### 1. Déploiement d'une instance Azure SQL Database

#### Explication
Azure SQL Database est une base de données relationnelle dans le cloud gérée par Microsoft. Le déploiement d'une instance permet de créer une base de données SQL accessible via internet.

#### Commandes / Étapes
- Utilisation du **Portail Azure** :
  - Recherche de **SQL Databases** dans la barre de recherche.
  - Création d'une nouvelle base de données avec les paramètres suivants :
    - Groupe de ressources : `Rayan_Azure_SQL`
    - Nom de la base de données : `MonSQLDatabase`
    - Serveur : Création d'un nouveau serveur SQL.
    - Tarification : Choisir un niveau **Basique** ou **Standard** selon vos besoins.

#### Capture d'écran
![Déploiement Base SQL](./screenshots/sql-deployment.png)

### 2. Configuration des paramètres du pare-feu

#### Explication
Pour autoriser l'accès à votre base de données SQL depuis un client (ex. : Azure Data Studio), vous devez configurer les règles du pare-feu pour inclure l'adresse IP du client.

#### Étapes
- Dans le portail Azure, accédez à votre base de données SQL.
- Dans les paramètres de la base de données, cliquez sur **Set server firewall**.
- Ajoutez l'adresse IP de votre machine locale en cliquant sur **Add client IP**.
- Enregistrez les modifications.

#### Capture d'écran
![Configuration Pare-feu SQL](./screenshots/sql-firewall-settings.png)

### 3. Importation des données dans la base de données

#### Explication
L'importation de données permet d'ajouter des informations dans les tables de votre base de données. Cela peut se faire via des outils comme Azure Data Studio ou SQL Server Management Studio (SSMS).

#### Commandes / Étapes
- Connectez-vous à votre base de données avec **Azure Data Studio** ou **SSMS**.
- Utilisez la fonctionnalité **Import Flat File** pour charger des fichiers CSV ou saisissez des commandes SQL pour insérer des données.
  - Exemple de requête SQL pour insérer des données :
    ```sql
    INSERT INTO [dbo].[MaTable] (ID, Nom, Prenom)
    VALUES (1, 'Dupont', 'Jean');
    ```

#### Capture d'écran
![Importation de données](./screenshots/sql-data-import.png)

### 4. Implémentation de la géo-réplication pour la haute disponibilité

#### Explication
La géo-réplication vous permet de répliquer votre base de données dans une région secondaire pour assurer une continuité de service en cas de panne dans la région principale.

#### Étapes
- Accédez à la page de votre base de données SQL dans Azure.
- Dans les paramètres de la base de données, sélectionnez **Geo-Replication**.
- Choisissez une région secondaire pour la réplication (ex. : `East US`).
- Cliquez sur **OK** pour démarrer la réplication.

#### Capture d'écran
![Géo-réplication SQL](./screenshots/sql-geo-replication.png)

### Conclusion
Ce laboratoire m'a permis de comprendre comment déployer et gérer une base de données SQL sur Azure, ainsi que la configuration des règles de pare-feu et la géo-réplication pour garantir la haute disponibilité des données.
