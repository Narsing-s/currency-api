# Currency API

A MuleSoft-based REST Currency API with a browser Currency API Explorer.

## What it includes

- Mule 4.9 application
- RAML 1.0 API contract
- APIKit routing
- HTTP listener on port `8081`
- `GET /api/currencies/{currency}` endpoint
- External exchange-rate service integration
- APIKit error handling
- Responsive browser currency converter
- Complete currency catalogue from the project API example
- Automatic frontend endpoint configuration
- Vercel-compatible static UI
- Documentation under `docs/`

## Run locally

Start the Mule application and make sure the listener is available at:

```text
http://localhost:8081
```

Then open the project UI. No endpoint needs to be entered by the user. The UI builds requests automatically:

```text
http://localhost:8081/api/currencies/{currency}
```

Example:

```text
GET http://localhost:8081/api/currencies/USD
```

## UI

The converter supports amount entry, From/To currency selection, swap, live conversion, and API connection testing. It displays connection, HTTP, JSON, CORS, and missing-rate errors in the result panel.

## Project structure

```text
currency-api/
├── index.html
├── app.js
├── styles.css
├── docs/
│   ├── README.md
│   ├── ARCHITECTURE.md
│   ├── API.md
│   ├── UI.md
│   ├── DEPLOYMENT.md
│   ├── TROUBLESHOOTING.md
│   └── RESUME.md
└── src/
    └── main/
        ├── mule/
        │   └── currency-api.xml
        └── resources/
            └── api/
                ├── currency-api.raml
                └── examples/
                    └── file.json
```

## Configuration

The frontend endpoint is intentionally defined in `app.js` from the Mule listener configuration. For a production deployment, update `API_BASE_URL` once to the public MuleSoft API base URL and redeploy the UI. Users should not be asked to configure it.

Do not expose upstream exchange-provider API keys in frontend JavaScript. Use MuleSoft secure properties/environment configuration for secrets.

## Documentation

See [`docs/README.md`](docs/README.md) for the complete documentation index.