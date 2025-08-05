# Endpoints d'Authentification

Les endpoints d'authentification gèrent la création de comptes, la connexion, et la gestion des sessions utilisateur.

## Gestion des comptes

### Enregistrement d'un nouveau compte

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/account/register` | <span class="method-post">`POST`</span> | Enregistrer un nouveau compte utilisateur | ❌ Non | `username`, `displayName`, `password`, `tos` | - | Les conditions d'utilisation doivent être acceptées |

**Paramètres requis :**
- `username` **(obligatoire)** - Nom d'utilisateur unique
- `displayName` **(obligatoire)** - Nom d'affichage de l'utilisateur
- `password` **(obligatoire)** - Mot de passe du compte
- `tos` **(obligatoire)** - Acceptation des conditions d'utilisation (doit être `true`)

### Connexion utilisateur

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/account/login` | <span class="method-post">`POST`</span> | Authentifier l'utilisateur et obtenir un token de session | ❌ Non | `username`, `password` | - | Format du nom d'utilisateur : @username@instance.tld |

**Paramètres requis :**
- `username` **(obligatoire)** - Identité complète de l'utilisateur
- `password` **(obligatoire)** - Mot de passe du compte

## Gestion des sessions

### Informations du compte

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/account/me` | <span class="method-get">`GET`</span> | Obtenir les informations du compte de l'utilisateur authentifié | ✅ Oui | - | - | Retourne l'identité au format @username@instance.tld |

### Déconnexion

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/account/logout` | <span class="method-post">`POST`</span> | Déconnecter l'utilisateur authentifié | ✅ Oui | - | - | Invalide le token de session |

## Suppression de compte

### Supprimer un compte utilisateur

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/account/me` | <span class="method-delete">`DELETE`</span> | Supprimer le compte utilisateur | ✅ Oui | `password` | - | Suppression définitive du compte |

**Paramètres requis :**
- `password` **(obligatoire)** - Mot de passe pour confirmer la suppression

!!! warning "Attention"
    La suppression d'un compte est **définitive** et **irréversible**. Toutes les données associées au compte seront perdues.
