# SapphiTalk REST API Endpoints

This section describes the endpoints used in the SapphiTalk protocol for communication between clients and servers.

!!! info "Protocol Version"
  The SapphiTalk/SapphiTalk+ protocol is currently at version **0.0.1**. If an update is published, you’ll need to update your implementation.

## API URL Structure

The API URL is structured as follows:

```
https://<instance>/api/<endpoint>
```

For example, to register a new account, you would use the endpoint:

```
https://<instance>/api/account/register
```

## Endpoint Organization

Endpoints are organized by categories:

- **[Base API](base.md)** - Root endpoint providing API information
- **[Authentication](authentication.md)** - User account and session management
- **[Conversations](conversations.md)** - Conversation creation and management
- **[Messages](messages.md)** - Message sending and management

## Conventions

### ID

IDs in the API must be **UUIDv4** and unique across the entire system.

!!! warning
    For federation, your instance must verify that any received ID is a valid **UUIDv4**.

### HTTP Methods

- <span class="method-get">`GET`</span> - Data retrieval
- <span class="method-post">`POST`</span> - Creating new resources
- <span class="method-put">`PUT`</span> - Updating existing resources
- <span class="method-delete">`DELETE`</span> - Deleting resources

### Authentication

- ✅ **Authentication required** - Endpoint requires a valid session token
- ❌ **No authentication** - Endpoint is accessible without authentication

## Response Format

All API responses follow a consistent JSON format:
```json
{
  "success": boolean,
  "message": "string (optional)",
  "data": "object (optional)",
  "error": "string (optional, only when success is false)"
}
```

### Success Response
```json
{
  "success": true,
  "data": {
    // Response data here
  }
}
```

### Error Response
```json
{
  "success": false,
  "error": "Error message",
  "code": "ERROR_CODE"
}
```
