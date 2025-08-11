# Protocol

## Sapphichat Communication Protocol

This section describes the technical specifications and communication protocols used by Sapphichat.

### Overview
Sapphichat is a very simple and understandable protocol designed for secure and efficient messaging.

SapphiTalk is the base of the protocol. It implements the core features of Sapphichat, while SapphiTalk+ extends it with additional functionalities like federation.

| Feature                | SapphiTalk | SapphiTalk+ |
|------------------------|------------|-------------|
| Core Messaging         | ✅         | ✅          |
| Presence Indicators    | ✅         | ✅          |
| Message History        | ✅         | ✅          |
| End-to-End Encryption  | ✅         | ✅          |
| Socket.IO Support      | ✅         | ✅          |
| Federation Support     | ❌         | ✅          |

We have chosen to make a distinction between SapphiTalk and SapphiTalk+ to allow for a simpler implementation of the core features while providing an option for advanced users to use federation capabilities.

Not every user needs federation, and SapphiTalk is designed to be easy to deploy and use without it.

### Key Features

- Simple to deploy a server and connect clients 
- Real-time messaging
- Group chat support
- File sharing capabilities
- Presence indicators
- Message history synchronization
- End-to-end encryption
- Support for multiple platforms (CLI, web, mobile, desktop)
- Easy to update, backup and restore data

### User identification

- Users are identified by their unique usernames, which are case-sensitive. Usernames can contain only lowercase letters and must be at least 1 character and at most 16 characters long. Usernames are not allowed to contain spaces or special characters.
- An account can have a display name, which is used to identify the user in the chat. The display name can be changed at any time and is not required to be unique. It can contain letters, numbers, spaces, and special characters.
- Passwords are mandatory, and must be securely stored and hashed on the server side. Passwords must be at least 8 characters long and contain at least one uppercase letter, one lowercase letter, one number, and one special character.

### Identification Format

- Users are identified by the following format:
```
@username@instance.tld
```
Where `username` is the username of the user and `instance` is the server instance (e.g., `sapphichat.example.com`).

- Groups are identified by the following format:
```
#groupname@instance.tld
```
Where `groupname` is the name of the group and `instance` is the server instance (e.g., `sapphichat.example.com`).

- DMs (Direct Messages) are identified by the following format:
```
@username1@instance1.tld > @username2@instance2.tld
```
Where `username1` and `username2` are the usernames of the users and `instance1` and `instance2` are the server instances (e.g., `sapphichat.example.com`).

The order of the usernames in the DM identifier does not matter, as it is a direct message between two users.

### API Documentation

Continue reading the [endpoints](./endpoints/index.md) section for detailed API endpoints and usage examples.