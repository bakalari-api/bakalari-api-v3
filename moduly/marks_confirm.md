# Podepsání známek

Podepíše zvolené známky.

## Požadavek

```http
POST /api/3/marks/SetClassificationConfirmation
Content-Type: application/json
Authorization: Bearer ACCESS_TOKEN
```

Do těla je nutné poslat seznam `ID` předmětů k podepsání ve formě `list`

```jsonc
["01YE)R1-5Q", "01YE)R1-7V" /* ... */]
```

## Odpověď

### Úspěch

```http
200 OK
```

### Známky jsou již podepsané

```http
204 No Content
```

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

### Chybějící či neplatné tělo

```http
500 Internal Server Error
```

```jsonc
{ "Message": "An error has occurred." }
```
