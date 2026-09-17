# Deployment

## MuleSoft backend

The Mule application is configured with:

- Listener host: `0.0.0.0`
- Listener port: `8081`
- Listener path: `/api/*`
- API resource: `/currencies/{currency}`

Deploy the Mule application to the target MuleSoft runtime and note the public base URL.

## Browser UI

The UI is static and can be hosted by any static web host, including Vercel.

Before production publishing, set the `API_BASE_URL` constant in `app.js` to the public MuleSoft base URL. Do not include `/api/currencies/{currency}` in that value.

For example, if the public backend is:

```text
https://currency-api.example.com
```

the UI automatically requests:

```text
https://currency-api.example.com/api/currencies/USD
```

## CORS

If the UI and MuleSoft API use different origins, configure CORS on the MuleSoft API to allow the UI origin. A successful API call in Postman does not guarantee that a browser request will succeed because browsers enforce CORS.

## Secrets

Never put the upstream exchange-provider API key in `app.js` or another browser-delivered file. Store credentials in MuleSoft secure properties/environment configuration.

## Deployment checklist

- [ ] Mule application starts successfully.
- [ ] `GET /api/currencies/USD` returns JSON.
- [ ] Public API uses HTTPS.
- [ ] CORS allows the deployed UI origin.
- [ ] `API_BASE_URL` points to the deployed MuleSoft base URL.
- [ ] No provider API key is exposed in frontend code.
- [ ] UI currency selectors contain the complete project catalogue.
- [ ] Test connection succeeds.
- [ ] A real conversion succeeds.