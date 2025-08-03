## SapphiTalk REST API Protocol Endpoints

This section describes the endpoints used in the SapphiTalk protocol for communication between clients and servers.

These endpoints are used for various operations such as sending messages, managing groups, handling user authentication and more.

### Endpoints Overview

#### Base API Endpoint
- **GET https://sapphichat.sapphichat.org/api**
    - This is the base endpoint for accessing the SapphiChat API for the instance `sapphichat.sapphichat.org`.
    - It provides a list of information about the available endpoints and their functionalities.

    - Response:
        - `version`: The version of the API.
        - `implemented_protocols`: A list of protocols implemented by the server (for example, `sapphitalk`, `sapphitalkplus`, `socketio`).

#### Authentication Endpoints
- **POST /auth/register**: Register a new user.
    - Request Body:
        - `username`: The desired username for the new user. (mandatory)
        - `displayName`: The display name for the new user. (mandatory)
        - `password`: The password for the new user. (mandatory)
        - `tos`: A boolean indicating whether the user agrees to the terms of service. (mandatory, must be true)
    - Response:
        - `success`: A boolean indicating whether the registration was successful.
        - `message`: Confirmation of successful registration.
    - Error Response:
        - `success`: A boolean indicating failure.
        - `error`: An error message if registration fails.
- **POST /auth/login**: Authenticate a user and return a session token.
    - Request Body:
        - `username`: The username of the user. (@username@instance.tld) (mandatory)
        - `password`: The password of the user. (mandatory)
    - Response:
        - `token`: The session token for the authenticated user.
    - Error Response:
        - `success`: A boolean indicating failure.
        - `error`: An error message if authentication fails.
- **GET /account/me**: Retrieve the authenticated user's account information.
    - Headers:
        - `Authorization`: Bearer token for authentication.
    - Response:
        - `success`: A boolean indicating whether the request was successful.
        - `username`: The username of the authenticated user.
        - `displayName`: The display name of the authenticated user.
        - `createdAt`: The timestamp of when the account was created.
    - Error Response:
        - `success`: A boolean indicating failure.
        - `error`: An error message if the request fails.
#### Messaging Endpoints