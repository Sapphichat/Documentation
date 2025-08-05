# Base API Endpoint

L'endpoint de base fournit des informations essentielles sur l'API et les protocoles disponibles.

## Endpoint racine

| Endpoint | Méthode | Description | Auth Requise | Paramètres Body | Paramètres URL | Notes |
|----------|---------|-------------|--------------|-----------------|----------------|-------|
| `/` | <span class="method-get">`GET`</span> | Endpoint de base fournissant les informations de l'API et les protocoles disponibles | ❌ Non | - | - | Retourne la version de l'API et les protocoles implémentés |

## Réponse

L'endpoint retourne les informations suivantes :

- **Version de l'API** - Version actuelle de l'implémentation
- **Protocoles disponibles** - Liste des protocoles supportés (ex: `sapphitalk`, `sapphitalkplus`, `sapphisocket`)
- **Informations sur l'instance** - Métadonnées de l'instance du serveur

## Exemple de réponse

```json
{
  "version": "0.0.1",
  "protocols": ["sapphitalk", "sapphitalkplus", "sapphisocket"],
  "instance": {
    "name": "Instance SapphiTalk",
    "description": "Une instance SapphiTalk"
  }
}
```
