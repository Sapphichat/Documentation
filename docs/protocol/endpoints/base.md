# Base API Endpoint

The base endpoint provides essential information about the API and available protocols.

## Root Endpoint

| Endpoint | Method | Description | Auth Required |
|----------|--------|-------------|---------------|
| `/` | <span class="method-get">`GET`</span> | Free endpoint | ❌ No |

**URL Example:**
```
GET https://instance.tld/
```

Returns, for example, a static HTML page to test API connectivity or to display a welcome message.

| Endpoint | Method | Description | Auth Required | Notes |
|----------|--------|-------------|---------------|-------|
| `/api` | <span class="method-get">`GET`</span> | Base endpoint providing API information and available protocols | ❌ No | Returns API version and implemented protocols |

**URL Example:**
```
GET https://instance.tld/api
```

## Response

The endpoint returns the following information:

- **API Version** - Current implementation version
- **Available Protocols** - List of supported protocols (e.g., `sapphitalk`, `sapphitalkplus`, `sapphisocket`)
- **Instance Information** - Server instance metadata

## Response Example

```json
{
  "success": true,
  "data": {
    "version": "X.X.X",
    "protocols": ["sapphitalk", "sapphitalkplus", "sapphisocket"],
    "instance": {
      "name": "Sapphichat Instance",
      "description": "A Sapphichat instance"
    },
    "custom": {
      "hello": "Hello community! Welcome to Sapphichat. 🏳️‍🌈",
    }
  }
}
```

You can add custom messages in the "custom" key. Use this to display a welcome message or any other information you want to provide to the user, or for technical purposes (for example returning uptime).

Clients must ignore the "custom" key if they do not recognize its contents.