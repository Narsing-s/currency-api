# Architecture

## Overview

The project is a Mule 4 Currency API with a lightweight browser-based explorer.

```text
User
  |
  v
Browser UI
  |
  | GET /api/currencies/{currency}
  v
MuleSoft HTTP Listener :8081
  |
  v
APIKit Router
  |
  v
Currency Flow
  |
  | GET latest/{currency}
  v
Exchange-rate provider
```

## MuleSoft components

- **HTTP Listener:** listens on `0.0.0.0:8081`.
- **API base path:** `/api/*`.
- **APIKit:** routes requests according to `currency-api.raml`.
- **Currency flow:** reads the `{currency}` URI parameter and calls the upstream exchange-rate service.
- **Error handling:** APIKit errors are mapped to HTTP responses such as 400, 404, 405, 406, 415, and 501.

## UI components

- `index.html` — application structure.
- `styles.css` — responsive visual design.
- `app.js` — currency catalogue, conversion logic, endpoint configuration, validation, and error handling.

The UI endpoint is intentionally configured in code rather than entered by the user. It points to the Mule listener base URL and builds `/api/currencies/{currency}` automatically.

## Important security note

The Mule application contains upstream provider configuration. Provider credentials/API keys should be stored as secure properties or environment variables and should not be exposed in browser JavaScript, documentation, screenshots, or public repositories.