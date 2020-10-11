# GDPR

## Požadavek
```
GET /api/3/gdpr/commissioners
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Informace o pověřenci pro ochranu osobních údajů

```200 OK```
``` json
{
  "Commissioners": [
    {
      "Id": "ABC01",
      "Name": "Jméno Příjmení",
      "Mobile": "123 456 789",
      "Phone": "",
      "Email": "gdpr@gdpr.gdpr",
      "Web": "gdpr.com",
      "DataBox": ""
    }
  ]
}
```

## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```




