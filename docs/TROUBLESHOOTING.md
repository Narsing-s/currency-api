# Troubleshooting

## "Configure endpoint" message

The manual endpoint setting has been removed from the UI. The browser uses the endpoint configured in `app.js` from the Mule listener code.

Development target:

```text
http://localhost:8081/api/currencies/{currency}
```

If the UI cannot connect, make sure the Mule application is running and listening on port `8081`.

## Connection failed

Check:

1. Mule runtime is running.
2. Port `8081` is reachable.
3. `GET /api/currencies/USD` returns JSON.
4. Browser CORS allows the UI origin.
5. The UI is not being opened from a context that blocks requests to the backend.

## HTTP 404

Confirm that the request path is exactly:

```text
/api/currencies/USD
```

The Mule listener uses `/api/*` and APIKit routes the `/currencies/{currency}` resource.

## Invalid JSON

The UI expects the Mule API to return JSON. Check the upstream response and the Mule transform before the response is sent to the browser.

## Target rate not found

The selected target currency must exist in the upstream response. The UI checks several common response structures before reporting that the target rate is missing.

## CORS error

If Postman works but the browser does not, inspect the browser console for CORS errors. Configure the MuleSoft API to allow the deployed UI origin.

## Production UI still points to localhost

Update the single `API_BASE_URL` constant in `app.js` to the public MuleSoft base URL and redeploy the static UI. End users should never have to enter the endpoint manually.