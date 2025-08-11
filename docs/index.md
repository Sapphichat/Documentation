# 🏳️‍🌈 Welcome to the Sapphichat documentation!

<img src="/img/Sapphichat-logo.png" alt="Sapphichat logo" width="100" style="border-radius: 20px;"/>

Sapphichat is a modern communication platform (that doesn't exist yet...) designed for secure and efficient messaging.

!!! danger "🚨 EU Chat Control Law"
    **Are you scared by the potential new EU law about Chat Control? We are too.**

    We sincerely believe that **privacy is a fundamental human right**, and we are committed to building a platform that respects and protects user privacy.

    **We will do everything we can to ensure that Sapphichat is a safe and secure communication tool for everyone. That's a promise.**

!!! warning "Sapphichat is a work in progress, we need your help!"
    This documentation is a work in progress. If you find any issues or have suggestions, please contribute to the project on GitHub.
    This project is relatively new, and we are looking for contributors to help us improve it.

This documentation will help you understand how to use Sapphichat and SapphiTalk effectively.

## Our goal

Unlike Matrix or other messaging protocols (which can require four or more Docker containers to run 💀), we want Sapphichat to be simple to deploy on a server. By running a single command and connecting to the server with a client (GUI) to configure it, you can access a fully functional chat server. Federation is optional and can be enabled if needed.

## Sapphichat software structure

Our goal is to provide a complete chat solution, including:

### Active / Planned Modules

| Module                 | Description                                                                             | Language / Technology             | Progress Status |
|------------------------|-----------------------------------------------------------------------------------------|-----------------------------------|-----------------|
| Sapphichat-backend     | Implementation of SapphiTalk & SapphiTalk+ protocols with SQLite and PostgreSQL support | Node.js, Express                  | Thinking... 💭  |
| Sapphichat-CLI         | Command-line interface client for developers to test the protocol                       | Node.js or Python                 | Thinking... 💭  |
| Sapphichat-web         | Web client for Sapphichat                                                               | Node.js, EJS and Express          | Thinking... 💭  |
| Sapphichat-iOS         | iOS client for Sapphichat                                                               | Swift                             | Thinking... 💭  |
| Sapphichat-Android     | Android client for Sapphichat                                                           | Kotlin                            | Thinking... 💭  |

### Obsolete Modules

| Module                | Description                                                      | Language / Technology | Progress Status |
|-----------------------|------------------------------------------------------------------|-----------------------|-----------------|
| Sapphichat-backendv1  | Implementation of SapphiTalk with only SQLite support            | Node.js               | Obsolete 🚫     |
| Sapphichat-iOSv1      | iOS client for Sapphichat written in Swift                       | Swift                 | Obsolete 🚫     |
