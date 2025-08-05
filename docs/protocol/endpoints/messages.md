# Gestion des Messages

Les endpoints de messages permettent d'effectuer toutes les opérations CRUD (Create, Read, Update, Delete) sur les messages dans les conversations.

## Opérations sur les messages

### Envoyer un message (Create)

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/messages/send/:conversationId` | <span class="method-post">`POST`</span> | Envoyer un message dans une conversation | ✅ Oui | `content` | `conversationId` | Envoie un message dans la conversation spécifiée |

**Paramètres d'URL :**
- `conversationId` **(obligatoire)** - ID de la conversation

**Paramètres du body :**
- `content` **(obligatoire)** - Contenu du message à envoyer

**Exemple de body :**
```json
{
  "content": "Bonjour, comment allez-vous ?"
}
```

### Récupérer les messages (Read)

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/messages/:conversationId/:page` | <span class="method-get">`GET`</span> | Obtenir les messages d'une conversation | ✅ Oui | - | `conversationId`, `page` | Retourne la liste des messages avec pagination |

**Paramètres d'URL :**
- `conversationId` **(obligatoire)** - ID de la conversation
- `page` **(obligatoire)** - Numéro de page pour la pagination

**Système de pagination :**
- La pagination commence à la page 1
- Chaque page contient un nombre fixe de messages (défini par le serveur)
- Les messages sont triés du plus récent au plus ancien

### Modifier un message (Update)

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/messages/edit/:conversationId/:messageId` | <span class="method-put">`PUT`</span> | Modifier un message dans une conversation | ✅ Oui | `content` | `conversationId`, `messageId` | Modifie le message spécifié |

**Paramètres d'URL :**
- `conversationId` **(obligatoire)** - ID de la conversation
- `messageId` **(obligatoire)** - ID du message à modifier

**Paramètres du body :**
- `content` **(obligatoire)** - Nouveau contenu du message

**Exemple de body :**
```json
{
  "content": "Message modifié"
}
```

### Supprimer un message (Delete)

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/messages/delete/:conversationId/:messageId` | <span class="method-delete">`DELETE`</span> | Supprimer un message d'une conversation | ✅ Oui | - | `conversationId`, `messageId` | Supprime le message spécifié de la conversation |

**Paramètres d'URL :**
- `conversationId` **(obligatoire)** - ID de la conversation
- `messageId` **(obligatoire)** - ID du message à supprimer

## Permissions et restrictions

!!! warning "Permissions"
    - **Modification** : Seul l'auteur du message peut le modifier
    - **Suppression** : Seul l'auteur du message ou un administrateur de la conversation peut supprimer un message
    - **Lecture** : Seuls les membres de la conversation peuvent lire les messages

!!! info "Limitations"
    - Les messages peuvent avoir une taille maximale (définie par le serveur)
    - Il peut y avoir une limite de temps pour modifier ou supprimer un message
    - Certains types de contenu peuvent être restreints (liens, médias, etc.)

## Opérations CRUD

Cette section suit le modèle CRUD standard :

- **C**reate → `POST /messages/send/:conversationId`
- **R**ead → `GET /messages/:conversationId/:page`
- **U**pdate → `PUT /messages/edit/:conversationId/:messageId`
- **D**elete → `DELETE /messages/delete/:conversationId/:messageId`
