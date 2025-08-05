# Gestion des Conversations

Les endpoints de conversation permettent de créer, gérer et quitter des conversations individuelles ou de groupe.

## Création de conversations

### Conversation privée (Message Direct)

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/conversations/create/dm/:identity` | <span class="method-post">`POST`</span> | Créer une conversation de message direct | ✅ Oui | - | `identity` | Format de l'identité : @username@instance.tld |

**Paramètres d'URL :**
- `identity` **(obligatoire)** - Identité de l'utilisateur avec qui créer la conversation

### Conversation de groupe

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/conversations/create/group` | <span class="method-post">`POST`</span> | Créer une conversation de groupe | ✅ Oui | `name`, `description`, `members` | - | Les membres sont un tableau d'identités |

**Paramètres requis :**
- `name` **(obligatoire)** - Nom du groupe
- `description` *(optionnel)* - Description du groupe
- `members` *(optionnel)* - Tableau des identités des membres à ajouter

**Exemple de body :**
```json
{
  "name": "Mon Groupe",
  "description": "Description du groupe",
  "members": ["@user1@instance.tld", "@user2@instance.tld"]
}
```

## Gestion des conversations

### Liste des conversations

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/conversations` | <span class="method-get">`GET`</span> | Obtenir la liste des conversations | ✅ Oui | - | - | Retourne la liste des IDs de conversation |

### Quitter une conversation

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/conversations/leave/:conversationId` | <span class="method-post">`POST`</span> | Quitter une conversation | ✅ Oui | - | `conversationId` | Quitte la conversation spécifiée |

**Paramètres d'URL :**
- `conversationId` **(obligatoire)** - ID de la conversation à quitter

!!! info "Note"
    - Pour les conversations de groupe, quitter la conversation vous retire de la liste des membres
    - Pour les messages directs, cela masque la conversation de votre liste
    - Si vous êtes le dernier membre d'un groupe, la conversation sera supprimée
