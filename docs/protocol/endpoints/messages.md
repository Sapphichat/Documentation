# Messages Management

Message endpoints allow you to perform all CRUD (Create, Read, Update, Delete) operations on messages within conversations.

## Message Operations

### Send Message (Create)

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/messages/send/:conversationId` | <span class="method-post">`POST`</span> | Send a message in a conversation | ✅ Yes | Sends a message to the specified conversation |

**URL Example:**
```
POST https://instance.tld/api/messages/send/conv-123
```

**URL Parameters:**
- `conversationId` **(required)** - Conversation ID

**Request Body:**
```json
{
  "content": "Hello, how are you?"
}
```

**Required Parameters:**
- `content` **(required)** - Message content

**Response Example:**
```json
{
  "success": true,
  "messageId": "msg-789",
  "conversationId": "conv-123",
  "content": "Hello, how are you?",
  "author": "@username@instance.tld",
  "timestamp": "2025-08-09T12:00:00Z"
}
```

### Retrieve Messages (Read)

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/messages/:conversationId/:page` | <span class="method-get">`GET`</span> | Get messages from a conversation | ✅ Yes | Returns message list with pagination |

**URL Example:**
```
GET https://instance.tld/api/messages/conv-123/1
```

**URL Parameters:**
- `conversationId` **(required)** - Conversation ID
- `page` **(required)** - Page number for pagination

**Pagination System:**
- Pagination starts at page 1
- Each page contains a fixed number of messages (defined by server)
- Messages are sorted from newest to oldest

**Response Example:**
```json
{
  "success": true,
  "conversationId": "conv-123",
  "page": 1,
  "totalPages": 5,
  "messages": [
    {
      "messageId": "msg-789",
      "content": "Hello, how are you?",
      "author": "@user1@instance.tld",
      "timestamp": "2025-08-09T12:00:00Z",
      "edited": false
    },
    {
      "messageId": "msg-788",
      "content": "Good morning!",
      "author": "@user2@instance.tld",
      "timestamp": "2025-08-09T11:58:00Z",
      "edited": false
    }
  ]
}
```

### Edit Message (Update)

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/messages/edit/:conversationId/:messageId` | <span class="method-put">`PUT`</span> | Edit a message in a conversation | ✅ Yes | Edits the specified message |

**URL Example:**
```
PUT https://instance.tld/api/messages/edit/conv-123/msg-789
```

**URL Parameters:**
- `conversationId` **(required)** - Conversation ID
- `messageId` **(required)** - Message ID to edit

**Request Body:**
```json
{
  "content": "Edited message content"
}
```

**Required Parameters:**
- `content` **(required)** - New message content

**Response Example:**
```json
{
  "success": true,
  "messageId": "msg-789",
  "conversationId": "conv-123",
  "content": "Edited message content",
  "author": "@username@instance.tld",
  "timestamp": "2025-08-09T12:00:00Z",
  "editedAt": "2025-08-09T12:05:00Z",
  "edited": true
}
```

### Delete Message (Delete)

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/messages/delete/:conversationId/:messageId` | <span class="method-delete">`DELETE`</span> | Delete a message from a conversation | ✅ Yes | Deletes the specified message from the conversation |

**URL Example:**
```
DELETE https://instance.tld/api/messages/delete/conv-123/msg-789
```

**URL Parameters:**
- `conversationId` **(required)** - Conversation ID
- `messageId` **(required)** - Message ID to delete

**Response Example:**
```json
{
  "success": true,
  "message": "Message deleted successfully",
  "messageId": "msg-789",
  "conversationId": "conv-123"
}
```

## Permissions and Restrictions

!!! warning "Permissions"
    - **Edit** : Only the message author can edit it
    - **Delete** : Only the message author or a conversation administrator can delete a message
    - **Read** : Only conversation members can read messages

!!! info "Limitations"
    - Messages may have a maximum size (defined by server)
    - There may be a time limit for editing or deleting messages
    - Certain content types may be restricted (links, media, etc.)

## CRUD Operations

This section follows the standard CRUD model:

- **C**reate → `POST /messages/send/:conversationId`
- **R**ead → `GET /messages/:conversationId/:page`
- **U**pdate → `PUT /messages/edit/:conversationId/:messageId`
- **D**elete → `DELETE /messages/delete/:conversationId/:messageId`
