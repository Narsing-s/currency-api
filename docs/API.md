# API Guide

## RAML contract

The RAML contract is located at `src/main/resources/api/currency-api.raml`.

### Resource

```http
GET /api/currencies/{currency}
```

Example:

```http
GET http://localhost:8081/api/currencies/USD
```

The `{currency}` value is passed from the URI parameter to the Mule flow, which calls the upstream `latest/{currency}` resource.

## Response

The UI accepts common exchange-rate response shapes, including:

- `rates.{TARGET}`
- `conversion_rates.{TARGET}`
- `exchange_rates.{TARGET}`
- a direct target-code property
- `quotes.{TARGET}`
- combined quote keys such as `{BASE}{TARGET}`

## Currency catalogue

The browser selectors include the currency codes represented in `src/main/resources/api/examples/file.json`. When the RAML example is expanded with additional currency codes, the UI catalogue should be regenerated/updated so the new codes are visible.

## Request lifecycle

1. Browser selects a source currency.
2. UI calls `/api/currencies/{source}`.
3. Mule APIKit matches the RAML resource.
4. Mule stores the URI parameter in `vars.currency`.
5. Mule calls the upstream exchange-rate service.
6. Mule returns JSON to the browser.
7. UI locates the target rate and calculates `amount × rate`.

## Error behavior

The UI reports invalid amounts, connection failures, HTTP failures, invalid JSON, missing target rates, and browser CORS failures without exposing a raw stack trace.