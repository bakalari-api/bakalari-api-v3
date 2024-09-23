# Komens

## Poslání nové zprávy (komens)

## Požadavek
```
POST /api/3/komens/message
"Content-Type: application/json; charset=utf-8"
"Authorization: Bearer ACCESS_TOKEN"
```

Do těla vstupuje mimo jiné i typ příjemce(ů) a seznam jejich identifikátorů z [komens/message-types](/moduly/komens_message-types.md) modulu.

Parametry pod atributem `Recipients` jsou nepovinné, ale dokáží ovlivnit zprávu.

```json
{
  "MessageType": "OBECNA",
  "Title": "Nadpis",
  "Text": "Text zprávy",
  "RecipientType": "U",
  "Recipients": [
    "AABBC"
  ],
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
  "DraftDate": null
}
```

## Odpověď

```200 OK```
``` json
{
  "Message": ""
}
```

## Chyby
při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při GET

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'GET'."} ```