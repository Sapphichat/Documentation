## SapphiTalk REST API Protocol Endpoints

This section describes the endpoints used in the SapphiTalk protocol for communication between clients and servers.

These endpoints are used for various operations such as sending messages, managing groups, handling user authentication and more.

### Base API Endpoint

| Endpoint | Method | Description | Auth Required | Notes |
|----------|---------|-------------|---------------|-------|
| `/api` | <span class="method-get">`GET`</span> | Base endpoint providing API information and available protocols | ❌ No | Returns API version and implemented protocols |

### Authentication Endpoints

| Endpoint | Method | Description | Auth Required | Request Parameters | Notes |
|----------|---------|-------------|---------------|-------------------|-------|
| `/account/register` | <span class="method-post">`POST`</span> | Register a new user account | ❌ No | `username` **(required)**, `displayName` **(required)**, `password` **(required)**, `tos` **(required)** | Terms of service must be true |
| `/account/login` | <span class="method-post">`POST`</span> | Authenticate user and get session token | ❌ No | `username` **(required)**, `password` **(required)** | Username format: @username@instance.tld |
| `/account/me` | <span class="method-get">`GET`</span> | Get authenticated user's account info | ✅ Yes | - | Returns identity in @username@instance.tld format |
| `/account/logout` | <span class="method-post">`POST`</span> | Log out authenticated user | ✅ Yes | - | Invalidates session token |
| `/account/me` | <span class="method-delete">`DELETE`</span> | Delete user account | ✅ Yes | `password` **(required)** | Permanent account deletion |

### Messaging Endpoints

| Endpoint | Method | Description | Auth Required | Request Parameters | Notes |
|----------|---------|-------------|---------------|-------------------|-------|
| `/messages/create/dm/:identity` | <span class="method-post">`POST`</span> | Create direct message conversation | ✅ Yes | `identity` **(required, URL param)** | Identity format: @username@instance.tld |
| `/messages/create/group` | <span class="method-post">`POST`</span> | Create group conversation | ✅ Yes | `name` **(required)**, `description` *(optional)*, `members` *(optional)* | Members as array of identities |