# Komens

## Nový koncept

## Požadavek
```
Post /api/3/komens/concept
"Content-Type: application/json; charset=utf-8"
"Authorization: Bearer ACCESS_TOKEN"
```


## Tělo

```3.52.1```
``` jsonc
{
  "ConceptData": {
    "ConceptId": 12345,
    "MessageType": "OBECNA",
    "Title": "Abcd",
    "Text": "<p>text</p>",
    "RecipientType": "U",
    "Recipients": ["ABCDE"],
    "LifeTime": null,
    "DateFrom": null,
    "DateTo": null,
    "PreviousMessageId": null,
    "TypeOfRatingId": null,
    "Scale": null,
    "Attachments": []
  },
  "SendOptions": {
    "EmailNotification": false,
    "CopyForClassTeacher": false,
    "CopyForParent": false,
    "CopyForDirector": false,
    "CopyForStudent": false,
    "RequireConfirmation": false,
    "SendAsDirector": false
  }
}
```

## Odpověd

```3.52.1``` ```200 OK```
``` jsonc
{
    "Message":""
}
```

## Chyby
při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při GET

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'GET'."} ```

## Koncept

## Požadavek
```
Get /api/3/komens/concept/$ID
"Content-Type: application/json; charset=utf-8"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověd

```3.52.1``` ```200 OK```
``` jsonc
{
  "Message": {
    "Attachments": [],
    "RecipientId": "ABCD",
    "Recipients": [
      {
        "RecipientId": "ABCD",
        "UserType": "student"
      }
    ],
    "Id": 123456,
    "Title": "Abcd",
    "Text": "<p>text</p>",
    "Sender": {
      "Id": "ABCDE",
      "Type": "student",
      "Name": "Jan Novak"
    },
    "LifeTime": "ToRead",
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
      "RequireConfirmation": true,
      "SendAsDirector": false
    },
    "Inserted": "2026-09-23T10:28:12+02:00",
    "Modified": "2026-09-23T10:28:12+02:00",
    "RecipientType": "U"
  }
}
```

## Chyby
při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```

