# Nové úkoly

## Počet otevřených úkolů

### Požadavek

```http
GET /api/3/homeworks/count-actual
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

Vrací počet úkolů s hodnotou `"Closed":false`

```http
200 OK
```

`6`

## Chyby

### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
