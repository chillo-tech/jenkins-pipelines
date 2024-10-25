## Créer des credentials à utiliser dans Jenkins

## Sur github
- Cliquer sur l'**image du profil**
- Cliquer sur **settings**
- Aller tout en bas dans le menu de gauche
- Cliquer sur **Developper settings**
- Ciquer sur **Personal access tokens** puis **Tokens (classic)**
- Cliquer sur **Generate new token** puis **Generate new token(classic)**
- Donner un nom(Note) au token
- Sélectionner **repo**
- Tout en bas enregistrer avec **Generate token**
- Copier le token en lieu sure

## Sur Jenkins
- Cliquer sur **Tableau de bord**
- Cliquer sur **Administrer Jenkins**
- Cliquer sur **Credentials**
- Dans la section **Stores scoped to Jenkins** cliquer sur **system**
- Cliquer sur **Identifiants globaux (illimité)**
- Cliquer sur **Add credentials**
- Saisir les informations
    - Type **Nom d'utilisateur et mot de passe**
    - Portée **Global**
    - Nom d'utilisateur **NOM_D_UTILISATEUR_GITHUB**
    - Mot de passe **TOKEN_GENERE_SUR_GITHUB**
    - ID **IDENTIFIANT_A_UTLISER_DANS_LES_JOBS**
- Cliquer sur **Create**


