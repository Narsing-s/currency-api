# UI Guide

## User flow

The UI is designed so a user can start using the converter without entering backend configuration.

```text
Amount + From + To
       |
       v
    Convert
       |
       v
http://localhost:8081/api/currencies/{From}
       |
       v
    Rate lookup
       |
       v
Amount × Rate = Result
```

## Available actions

- **Amount:** accepts positive numeric values.
- **From:** contains the complete currency catalogue used by the project example.
- **To:** contains the same catalogue.
- **Swap:** exchanges From and To values.
- **Convert:** calls the MuleSoft API and calculates the result.
- **Test connection:** calls the configured USD endpoint to verify connectivity.
- **Navigation links:** jump to Converter, API, and About sections.
- **GitHub:** opens the project repository.

## Endpoint configuration

There is no endpoint input for end users. `app.js` contains the backend base URL derived from the Mule listener configuration:

```js
const API_BASE_URL = 'http://localhost:8081';
```

The request path is built automatically:

```text
{API_BASE_URL}/api/currencies/{currency}
```

If the backend host changes for a deployment, update the single `API_BASE_URL` constant rather than asking every user to configure the endpoint.

## Error states

The UI displays a readable message for:

- missing/invalid amount
- backend unavailable
- HTTP error response
- invalid JSON
- missing target rate
- CORS/browser access failure

## Production note

For a hosted UI, replace the development `localhost` base URL with the public MuleSoft API base URL in the application source before publishing the UI. The user still does not need to enter anything.