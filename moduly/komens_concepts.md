# Komens

## Získat všechny koncepty

Získá všechny koncepty uživatele

## Požadavek
```
Post /api/3/komens/concepts
"Content-Type: application/json; charset=utf-8"
"Authorization: Bearer ACCESS_TOKEN"
```


## Odpověď

```3.52.1``` ```200 OK```
``` jsonc
{
  "Messages": [
    {
      "AttachmentsCount": 0,
      "RecipientsCount": 0,
      "Id": 1234,
      "Title": "",
      "Text": "",
      "Sender": {
        "Id": "id",
        "Type": "parents",
        "Name": "Jan Novák"
      },
      "LifeTime": "ToRead", //nullable Enum "ToConfirm", "ToRead", "ToRemoval", "Validity"
      "MessageType": "OBECNA",
      "DateFrom": null,
      "DateTo": null,
      "Scale": 0,
      "TypeOfRatingType": null,
      "TypeOfRatingId": 0,
      "SendOptions": {
        "$type": "SendOptions",
        "EmailNotification": false,
        "CopyForClassTeacher": false,
        "CopyForParent": false,
        "CopyForDirector": false,
        "CopyForStudent": false,
        "RequireConfirmation": false,
        "SendAsDirector": false
      },
      "Inserted": "2026-09-23T10:28:12+02:00",
      "Modified": "2026-09-23T10:27:12+02:00",
      "RecipientType": "U"
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

