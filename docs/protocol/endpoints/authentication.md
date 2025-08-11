# Account Endpoints

Account endpoints handle account creation, login, and user session management.

## Account Management

### Register New Account

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/account/register` | <span class="method-post">`POST`</span> | Register a new user account | ❌ No | Terms of service must be accepted |

**URL Example:**
```
POST https://instance.tld/api/account/register
```

**Request Body:**
```json
{
  "username": "string", // Mandatory
  "displayName": "string", // Mandatory
  "password": "string", // Mandatory
  "tos": true // Mandatory
}
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "message": "Account created successfully",
    "userId": "user-123",
    "identity": "@username@instance.tld"
  }
}
```

### User Login

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/account/login` | <span class="method-post">`POST`</span> | Authenticate user and obtain session token | ❌ No | Username format: @username@instance.tld |

**URL Example:**
```
POST https://instance.tld/api/account/login
```

**Request Body:**
```json
{
  "identity": "@username@instance.tld", // Mandatory
  "password": "string" // Mandatory
}
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "token": "session-token-here",
    "identity": "@username@instance.tld",
    "expiresAt": "2025-08-10T12:00:00Z"
  }
}
```

This token must be provided in the `Authorization` header as a Bearer token on endpoints that require authentication. **Store this token in a safe place**.

### Edit Account Information

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/account/me` | <span class="method-put">`PUT`</span> | Update user account information | ✅ Yes | Only updates fields provided in the request body |

**URL Example:**
```
PUT https://instance.tld/api/account/me
```

**Request Body:**
```json
{
  "displayName": "string", // Optional
  "password": "string" // Optional
}
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "message": "Account information updated successfully"
  }
}
```

## Session Management

### Account Information

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/account/me` | <span class="method-get">`GET`</span> | Get authenticated user account information | ✅ Yes | Returns identity in @username@instance.tld format |

**URL Example:**
```
GET https://instance.tld/api/account/me
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "identity": "@username@instance.tld",
    "displayName": "User Display Name",
    "accountCreated": "2025-01-01T00:00:00Z",
    "isVerified": true
  }
}
```

### Logout

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/account/logout` | <span class="method-post">`POST`</span> | Log out authenticated user | ✅ Yes | Invalidates session token |

**URL Example:**
```
POST https://instance.tld/api/account/logout
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "message": "Successfully logged out"
  }
}
```

## Account Deletion

### Delete User Account

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/account/me` | <span class="method-delete">`DELETE`</span> | Delete user account | ✅ Yes | Permanent account deletion |

**URL Example:**
```
DELETE https://instance.tld/api/account/me
```

**Request Body:**
```json
{
  "password": "string" // Mandatory
}
```

**Response Example:**
```json
{
  "success": true,
  "data": {
    "message": "Account deleted successfully"
  }
}
```

!!! warning "Warning"
    Account deletion is **permanent** and **irreversible**. All associated data will be lost.
