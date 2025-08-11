# Conversations Management

Conversation endpoints allow you to create, manage, and leave individual or group conversations.

## Creating Conversations

### Private Conversation (Direct Message)

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/conversations/create/dm/:identity` | <span class="method-post">`POST`</span> | Create a direct message conversation | ✅ Yes | Identity format: @username@instance.tld |

**URL Example:**
```
POST https://instance.tld/api/conversations/create/dm/@user@instance.tld
```

**URL Parameters:**
- `identity` **(required)** - Identity of the user with whom to create the conversation

**Response Example:**
```json
{
  "success": true,
  "data": {
    "conversationId": "123e4567-e89b-12d3-a456-426614174000",
    "type": "dm",
    "participants": [
      "@user1@instance.tld",
      "@user2@instance.tld"
    ],
    "createdAt": "2025-08-09T12:00:00Z"
  }
}
```

### Group Conversation

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/conversations/create/group` | <span class="method-post">`POST`</span> | Create a group conversation | ✅ Yes | Members is an array of identities |

**URL Example:**
```
POST https://instance.tld/api/conversations/create/group
```

**Request Body:**
```json
{
  "name": "My Group", // Mandatory
  "description": "Group description", // Mandatory
  "members": ["@user1@instance.tld", "@user2@instance.tld"] // Mandatory
}
```

**Response Example:**
```json
{
  "success": true,
  "conversationId": "conv-456",
  "type": "group",
  "name": "My Group",
  "description": "Group description",
  "members": [
    "@creator@instance.tld",
    "@user1@instance.tld",
    "@user2@instance.tld"
  ],
  "createdAt": "2025-08-09T12:00:00Z"
}
```

## Managing Conversations

### List Conversations

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/conversations` | <span class="method-get">`GET`</span> | Get list of conversations | ✅ Yes | Returns list of conversation IDs |

**URL Example:**
```
GET https://instance.tld/api/conversations
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "conversations": [
      {
        "conversationId": "123e4567-e89b-12d3-a456-426614174000",
        "type": "dm",
        "participants": ["@user1@instance.tld", "@user2@instance.tld"],
        "lastActivity": "2025-08-09T11:30:00Z"
      },
      {
        "conversationId": "123e4567-e89b-12d3-a456-426614174000",
        "type": "group",
        "name": "My Group",
        "memberCount": 5,
        "lastActivity": "2025-08-09T10:15:00Z"
      }
    ]
  }
}
```

### Leave Conversation

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/conversations/leave/:conversationId` | <span class="method-post">`POST`</span> | Leave a conversation | ✅ Yes | Leaves the specified conversation |

**URL Example:**
```
POST https://instance.tld/api/conversations/leave/123e4567-e89b-12d3-a456-426614174000
```

**URL Parameters:**
- `conversationId` **(required)** - ID of the conversation to leave

**Response Example:**
```json
{
  "success": true,
  "data": {
    "message": "Successfully left conversation",
    "conversationId": "123e4567-e89b-12d3-a456-426614174000"
  }
}
```

!!! info
    - For group conversations, leaving removes you from the member list
    - For direct messages, this hides the conversation from your list
    - If you are the last member of a group, the conversation will be deleted
