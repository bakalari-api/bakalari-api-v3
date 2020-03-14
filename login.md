# Login
Endpoint `/api/login`

POST request

Content-Type: application/x-www-form-urlencoded

## První přihlášení
Body: `client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD`

Výsledek requestu:
```json
{
  "access_token": "ACCESSTOKEN",
  "token_type": "bearer",
  "expires_in": 599,
  "refresh_token": "REFRESHTOKEN",
  "bak:ApiVersion": "3.8.0",
  "bak:AppVersion": "1.28.306.4",
  "bak:UserId": "GTU4V"
}
```

Pro práci s dalšími endpointy je nezbytné používat tzv. access token pomocí hlavičky `Authorization: Bearer ACCESSTOKEN`

## Přihlášení pomocí refresh tokenu
Body: `client_id=ANDR&grant_type=refresh_token&refresh_token=REFRESHTOKEN`

Výsledek requestu:
```json
{
  "access_token": "ACCESSTOKEN",
  "token_type": "bearer",
  "expires_in": 599,
  "refresh_token": "REFRESHTOKEN",
  "bak:ApiVersion": "3.8.0",
  "bak:AppVersion": "1.28.306.4",
  "bak:UserId": "GTU4V"
}
```

## Chyby

Bez client_id, nebo grant_type dostaneme

```
{
  "error": "invalid_client",
  "error_description": "Unknown Client or invalid grant type."
}
```

Bez validního refresh_token je odpovědí následující:

```
{
  "error": "invalid_grant"
}
```
