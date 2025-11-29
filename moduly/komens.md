# Komens

## Dotazy na seznamy komens

### Odpověď

Veškeré otázky, které vracejí nějaký seznam komens, je vrací v tomto formátu.

``` json
{
  "Messages": [
    {
      "$type": "GeneralMessage",
      "Id": "1234",
      "Title": "Obecná zpráva",
      "Text": "<div>HTML encoded zpráva</div>",
      "SentDate": "2020-08-31T09:02:44+02:00",
      "Sender": {
        "Id": "UZYNQ",
        "Type": "administrator",
        "Name": "Jan Novák (ředitelství)"
      },
      "Attachments": [],
      "Read": true,
      "LifeTime": "ToRead",
      "DateFrom": null,
      "DateTo": null,
      "Confirmed": true,
      "CanConfirm": false,
      "Type": "OBECNA",
      "CanAnswer": true,
      "Hidden": false,
      "CanHide": true,
      "RelevantName": "ředitelství",
      "RelevantPersonType": "administrator"
    }
  ]
}
```

### Dotazy

Bakaláři podporují tyto seznamy komens.

```
POST /api/3/komens/messages/received
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací přijaté komens.
Vrací výchozí odpověď.


```
POST /api/3/komens/messages/sent
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací odeslané komens.
Vrací výchozí odpověď.


```
POST /api/3/komens/messages/noticeboard
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací komens připnuté k noticeboard.
Vrací výchozí odpověď.


## Dotaz na jednotlivý komens

### Dotazy

```
GET /api/3/komens/messages/{received/sent}/$ID
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací detail jednoho komens podle kategorie ve formátu jednoho JSON objektu komens.

### Odpověď

``` json
{
  "Message": {
    "$type": "SentMessageWithRecipientsDetail",
    "Recipients": [
      {
        "RecipientId": "UZYNQ",
        "UserType": "teacher"
      }
    ],
    "RecipientsProcessed": [
      {
        "RecipientId": "UZYNQ",
        "UserType": "teacher",
        "ActionDate": "2025-02-23T23:47:07+01:00",
        "ParentPersons": []
      }
    ],
    "Persons": [
      {
        "Id": "UZYNQ",
        "UserType": "teacher",
        "PersonId": "UZYNQ",
        "FirstName": "Jan",
        "MiddleName": "",
        "LastName": "Novák",
        "Degree": "Ing.",
        "DegreeBehind": "",
        "ClassAbbreviation": null
      },
      {
        "Id": "AABBCC",
        "UserType": "student",
        "PersonId": "GV{OI",
        "FirstName": "Honza",
        "MiddleName": null,
        "LastName": "Vomáčka",
        "Degree": null,
        "DegreeBehind": null,
        "ClassAbbreviation": "4ITB"
      }
    ],
    "Attachments": [],
    "DateFrom": "2025-02-19T00:00:00+01:00",
    "DateTo": "2025-02-21T23:59:59+01:00",
    "CanConfirm": false,
    "CanAnswer": false,
    "CanHide": true,
    "CanDelete": false,
    "Id": "1234",
    "Title": "omluvenka: Honza Vomáčka, 1.B",
    "Text": "<div>HTML encoded zpráva</div>",
    "SentDate": "2025-02-23T23:46:55+01:00",
    "Sender": {
      "Id": "AABBCC",
      "Type": "student",
      "Name": "Honza Vomáčka, 1.B"
    },
    "Read": true,
    "LifeTime": "ToConfirm",
    "Confirmed": true,
    "Type": "OMLUVENKA",
    "Hidden": false,
    "RelevantName": "Ing. Jan Novák",
    "RelevantPersonType": "teacher"
  }
}
```


## Dotaz na označení komens jako přečtené


```
PUT /api/3/komens/message/$ID/mark-as-read
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Nastavuje komens jako přečtený v systému Bakalářů. (Doporučuji zavolat zároveň při získávání detailu zprávy při atributu `Read` na `false`)

Vrací prázdnou HTTP odpověď `204`.


## Dotazy na počet nepřečtených komens


### Odpověď

Vrací počet nepřečtených komens v daném seznamu.

``` json
0
```

### Dotazy

```
GET /api/3/komens/messages/received/unread
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací počet přijatých komens.
Vrací výchozí odpověď.


```
GET /api/3/komens/messages/noticeboard/unread
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací počet komens připnutých k noticeboard.
Vrací výchozí odpověď.

## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```


