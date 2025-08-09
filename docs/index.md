# 🏳️‍🌈 Welcome to the Sapphichat documentation!

<img src="/img/Sapphichat-logo.png" alt="Sapphichat logo" width="100" style="border-radius: 20px;"/>

Sapphichat is a modern communication platform (that doesn't exist yet...) designed for secure and efficient messaging.

!!! danger "🚨 EU Chat Control Law"
    **Are you scared by the new EU law about Chat Control? We are too. That's why we have started this project.**
    
    We sincerely believe that **privacy is a fundamental human right**, and we are committed to building a platform that respects and protects user privacy.
    
    **We will do everything we can to ensure that Sapphichat is a safe and secure communication tool for everyone. That's is a promise.**

!!! warning "Sapphichat is in work in process, we need your help!"
    This documentation is a work in progress. If you find any issues or have suggestions, please contribute to the project on GitHub.
    This project is relatively new, and we are looking for contributors to help us improve it.

This documentation will help you understand how to use Sapphichat and SapphiTalk effectively.

## Our goal

Not like Matrix, or other messaging protocols (where you need more than 4 or more docker containers to run it 💀), we want Sapphichat to be simple to deploy on a server, by running a single command and connect to the server with a client to configure it with a GUI, you can have access to a fully functional chat server with federation if you configure it to allow it.

## Sapphichat software structure

Our goal is to provide a complete chat solution, including:

### Active / Planned Modules

| Module                 | Description                                                                             | Language / Technology             | Progress Status |
|------------------------|-----------------------------------------------------------------------------------------|-----------------------------------|-----------------|
| Sapphichat-backend     | Implementation of SapphiTalk & SapphiTalk+ protocols with SQLite and PostgreSQL support | Node.JS, Express                  | Thinking... 💭  |
| Sapphichat-CLI         | Command-line interface client for developers to test the protocol                       | Node.JS or Python                 | Thinking... 💭  |
| Sapphichat-web         | Web client for Sapphichat                                                               | Node.JS, EJS and Express          | Thinking... 💭  |
| Sapphichat-iOS         | iOS client for Sapphichat                                                               | Swift                             | Thinking... 💭  |
| Sapphichat-Android     | Android client for Sapphichat                                                           | Kotlin                            | Thinking... 💭  |

### Obsolete Modules

| Module                | Description                                                      | Language / Technology | Progress Status |
|-----------------------|------------------------------------------------------------------|-----------------------|-----------------|
| Sapphichat-backendv1  | Implementation of SapphiTalk with only SQLite support            | Node.JS               | Obsolete 🚫     |
| Sapphichat-iOSv1      | iOS client for Sapphichat written in Swift                       | Swift                 | Obsolete 🚫     |
