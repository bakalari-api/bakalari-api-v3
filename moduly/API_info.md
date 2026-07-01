# API info

## Přehled všech dostupných API verzí

### Požadavek

```http
GET /api
```

### Odpověď

```jsonc
[
  {
    "ApiVersion": "3.12.0",
    "ApplicationVersion": "1.32.625.2",
    "BaseUrl": "api/3",
  },
]
```

## Informace o API

### Požadavek

```http
GET /api/3
```

### Odpověď

```jsonc
{
  "ApiVersion": "3.12.0",
  "ApplicationVersion": "1.32.625.2",
  "BaseUrl": "api/3",
}
```

## Chyby

### Chybná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
