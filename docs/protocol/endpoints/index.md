# SapphiTalk REST API Endpoints

Cette section décrit les endpoints utilisés dans le protocole SapphiTalk pour la communication entre clients et serveurs.

!!! info "Version du Protocole"
    Le protocole SapphiTalk/SapphiTalk+ est actuellement en version **0.0.1**. Si une mise à jour est publiée, il sera nécessaire de mettre à jour le client.

## Structure de l'URL API

L'URL de l'API est structurée comme suit :

```
https://<instance>/api/<endpoint>
```

Par exemple, pour enregistrer un nouveau compte, vous utiliseriez l'endpoint :

```
https://<instance>/api/account/register
```

## Organisation des Endpoints

Les endpoints sont organisés par catégories :

- **[Base API](base.md)** - Endpoint racine fournissant les informations de l'API
- **[Authentification](authentication.md)** - Gestion des comptes utilisateurs et sessions
- **[Conversations](conversations.md)** - Création et gestion des conversations
- **[Messages](messages.md)** - Envoi et gestion des messages

## Conventions

### Méthodes HTTP

- <span class="method-get">`GET`</span> - Récupération de données
- <span class="method-post">`POST`</span> - Création de nouvelles ressources
- <span class="method-put">`PUT`</span> - Mise à jour de ressources existantes
- <span class="method-delete">`DELETE`</span> - Suppression de ressources

### Authentification

- ✅ **Authentification requise** - L'endpoint nécessite un token de session valide
- ❌ **Pas d'authentification** - L'endpoint est accessible sans authentification

### Format des identités

Les identités utilisateur suivent le format : `@username@instance.tld`
