# Lab 6: Configuring Azure Active Directory (Azure AD)

## Objectif
Ce laboratoire a pour but de configurer Azure Active Directory (Azure AD), de gérer les utilisateurs et les groupes, de configurer l'authentification multi-facteur (MFA), d'enregistrer des applications et de définir des politiques d'accès conditionnel.

## Étapes Suivies

### 1. Création et gestion des utilisateurs et des groupes dans Azure AD

#### Explication
Azure AD permet de gérer les utilisateurs et groupes pour faciliter l'accès aux ressources.

#### Étapes
- Dans le **Portail Azure**, recherchez **Azure Active Directory**. (Dans mon cas je n'avais pas le role malheuresement)
- Accédez à **Utilisateurs** pour ajouter un nouvel utilisateur.
- Créez un **Groupe** en allant dans la section **Groupes** et ajoutez des utilisateurs au groupe.

#### Capture d'écran
![Gestion des utilisateurs et groupes](./screenshots/user-group-management.png)

### 2. Configuration de l'authentification multi-facteur (MFA)

#### Explication
L'authentification multi-facteur (MFA) ajoute une couche de sécurité supplémentaire en demandant une seconde forme d'authentification.

#### Étapes
- Accédez à **Azure Active Directory** > **Sécurité** > **MFA**.
- Activez MFA pour les utilisateurs spécifiques en accédant à **Gérer les utilisateurs MFA**.
- Sélectionnez les utilisateurs concernés et activez l'authentification multi-facteur.

#### Capture d'écran
![Configuration MFA](./screenshots/mfa-setup.png)

### 3. Configuration des enregistrements d'application et des Principaux de Service

#### Explication
Les applications doivent être enregistrées dans Azure AD pour interagir avec les services. Un Principal de Service est nécessaire pour qu'une application puisse s'authentifier auprès des ressources Azure.

#### Étapes
- Accédez à **Azure Active Directory** > **Enregistrements d'applications**.
- Cliquez sur **+ Nouvel enregistrement** pour créer une nouvelle application.
- Accédez ensuite à **Principaux de service** pour associer un Principal de Service à l'application.

#### Capture d'écran
![Enregistrement d'application](./screenshots/app-registration.png)

### 4. Implémentation des politiques d'accès conditionnel

#### Explication
Les politiques d'accès conditionnel permettent de contrôler l'accès aux applications en fonction de certaines conditions, comme l'exigence de l'authentification multi-facteur en dehors du réseau d'entreprise.

#### Étapes
- Accédez à **Azure Active Directory** > **Sécurité** > **Accès conditionnel**.
- Créez une **Nouvelle politique** et configurez les conditions d'accès.
- Appliquez la politique aux utilisateurs et aux applications spécifiques, puis configurez les conditions pour exiger MFA si nécessaire.

#### Capture d'écran
![Accès conditionnel](./screenshots/conditional-access.png)

### Conclusion
Ce laboratoire m'a permis de gérer les utilisateurs et groupes dans Azure AD, de configurer l'authentification multi-facteur pour renforcer la sécurité, d'enregistrer des applications et de définir des politiques d'accès conditionnel afin de sécuriser l'accès aux applications et ressources.

