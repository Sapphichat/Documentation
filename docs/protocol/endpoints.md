## SapphiTalk REST API Protocol Endpoints

This section describes the endpoints used in the SapphiTalk protocol for communication between clients and servers.

These endpoints are used for various operations such as sending messages, managing groups, handling user authentication and more.

### Base API Endpoint

| Endpoint | Method | Description | Auth Required | Notes |
|----------|---------|-------------|---------------|-------|
| <span class="endpoint">/api</span> | <span class="method-badge method-get">GET</span> | Base endpoint providing API information and available protocols | <span class="auth-optional">❌</span> | Returns API version and implemented protocols |

### Authentication Endpoints

| Endpoint | Method | Description | Auth Required | Request Parameters | Notes |
|----------|---------|-------------|---------------|-------------------|-------|
| <span class="endpoint">/account/register</span> | <span class="method-badge method-post">POST</span> | Register a new user account | <span class="auth-optional">❌</span> | <span class="param-required">`username` ✅</span>, <span class="param-required">`displayName` ✅</span>, <span class="param-required">`password` ✅</span>, <span class="param-required">`tos` ✅</span> | Terms of service must be true |
| <span class="endpoint">/account/login</span> | <span class="method-badge method-post">POST</span> | Authenticate user and get session token | <span class="auth-optional">❌</span> | <span class="param-required">`username` ✅</span>, <span class="param-required">`password` ✅</span> | Username format: @username@instance.tld |
| <span class="endpoint">/account/me</span> | <span class="method-badge method-get">GET</span> | Get authenticated user's account info | <span class="auth-required">✅</span> | - | Returns identity in @username@instance.tld format |
| <span class="endpoint">/account/logout</span> | <span class="method-badge method-post">POST</span> | Log out authenticated user | <span class="auth-required">✅</span> | - | Invalidates session token |
| <span class="endpoint">/account/me</span> | <span class="method-badge method-delete">DELETE</span> | Delete user account | <span class="auth-required">✅</span> | <span class="param-required">`password` ✅</span> | Permanent account deletion |

### Messaging Endpoints

| Endpoint | Method | Description | Auth Required | Request Parameters | Notes |
|----------|---------|-------------|---------------|-------------------|-------|
| <span class="endpoint">/messages/create/dm/:identity</span> | <span class="method-badge method-post">POST</span> | Create direct message conversation | <span class="auth-required">✅</span> | <span class="param-required">`identity` (URL param) ✅</span> | Identity format: @username@instance.tld |
| <span class="endpoint">/messages/create/group</span> | <span class="method-badge method-post">POST</span> | Create group conversation | <span class="auth-required">✅</span> | <span class="param-required">`name` ✅</span>, <span class="param-optional">`description` ❌</span>, <span class="param-optional">`members` ❌</span> | Members as array of identities |