# Nové známky

## Počet nových známek

### Požadavek

```http
GET /api/3/marks/count-new
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

Zatím pokaždé vrátilo nulu, zkoušel jsem i před zobrazením známky v aplikaci,
zřejmě bude nenulová pouze před zobrazením push notifikace.

```http
200 OK
```

```
0
```

### Chyby

#### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

#### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
