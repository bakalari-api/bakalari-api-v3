Endpoint /api/login
POST request

tělo jako form urlencoded
client_id       ANDR
grant_type      refresh_token
refresh_token   ???


Bez client_id, nebi grant_type dostaneme

```
{
  "error": "invalid_client",
  "error_description": "Unknown Client or invalid grant type."
}
```

bez validního refresh_token

```
{
  "error": "invalid_grant"
}
```
