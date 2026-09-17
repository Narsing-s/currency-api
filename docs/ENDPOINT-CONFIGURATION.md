# Endpoint Configuration

The UI does not ask users to enter an endpoint.

The MuleSoft listener is configured on `0.0.0.0:8081` and the API flow listens under `/api/*`. The RAML resource is `/currencies/{currency}`.

Therefore the browser endpoint is:

`http://localhost:8081/api/currencies/{currency}`

For example:

`http://localhost:8081/api/currencies/USD`

The UI builds this URL automatically from the configured application endpoint. In a deployed environment, replace the application-level base URL with the public MuleSoft URL; users should still never have to type it.
