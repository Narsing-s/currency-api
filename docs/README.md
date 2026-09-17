# Currency API Documentation

This folder contains the project documentation for the MuleSoft Currency API and its browser UI.

## Documents

- [Architecture](./ARCHITECTURE.md) — request flow and project components.
- [API Guide](./API.md) — RAML resource, endpoint format, response handling, and supported currencies.
- [UI Guide](./UI.md) — converter behavior and automatic backend configuration.
- [Deployment](./DEPLOYMENT.md) — MuleSoft backend and static UI deployment notes.
- [Troubleshooting](./TROUBLESHOOTING.md) — common endpoint, CORS, HTTP, and response problems.
- [Resume](./RESUME.md) — resume-ready project description and responsibilities.

## Source of truth

The API contract is defined in `src/main/resources/api/currency-api.raml`. The Mule listener is defined in `src/main/mule/currency-api.xml`. The UI currency catalogue follows the currency codes represented by the RAML example response in `src/main/resources/api/examples/file.json`.

## Quick start

1. Start the Mule application.
2. Confirm the listener is available on `http://localhost:8081`.
3. Open the UI.
4. Choose an amount, source currency, and target currency.
5. Select **Convert**.
6. Use **Test connection** when you want to verify the MuleSoft endpoint.

The UI does not ask end users to enter an API endpoint. The endpoint is defined in `app.js` from the listener configuration used by the Mule application.