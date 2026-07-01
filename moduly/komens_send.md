# Komens

## Poslání nové zprávy (komens)

### Požadavek

```http
POST /api/3/komens/message
Content-Type: application/json; charset=utf-8
Authorization: Bearer ACCESS_TOKEN
```

Do těla vstupuje mimo jiné i typ příjemce(ů) a seznam jejich identifikátorů z
[komens/message-types](/moduly/komens_message-types.md) modulu.

Parametry pod atributem `Recipients` jsou nepovinné, ale dokáží ovlivnit zprávu.

```jsonc
{
  "MessageType": "OBECNA",
  "Title": "Nadpis",
  "Text": "Text zprávy",
  "RecipientType": "U",
  "Recipients": ["AABBC"],
  "Lifetime": null,
  "DateFrom": null,
  "DateTo": null,
  "PreviousMessageId": null,
  "CopyForClassTeacher": false,
  "CopyForParent": false,
  "EmailNotification": false,
  "SendAsDirector": false,
  "RequireConfirmation": true,
  "TypeOfRatingId": null,
  "Scale": null,
  "Attachments": [],
  "DraftDate": null,
}
```

### Odpověď

```jsonc
{
  "Message": "",
}
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
{ "Message": "The requested resource does not support http method 'GET'." }
```
