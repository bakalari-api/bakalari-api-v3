# GDPR

## Informace o pověřenci pro ochranu osobních údajů

### Požadavek

```http
GET /api/3/gdpr/commissioners
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

Informace o pověřenci pro ochranu osobních údajů

```jsonc
{
  "Commissioners": [
    {
      "Id": "ABC01",
      "Name": "Jméno Příjmení",
      "Mobile": "123 456 789",
      "Phone": "",
      "Email": "gdpr@gdpr.gdpr",
      "Web": "gdpr.com",
      "DataBox": "",
    },
  ],
}
```

## Chyby

### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{"Invalid token request."}
```

### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
