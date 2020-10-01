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
POST /api/3/komens/messages/noticeboard
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Vrací komens připnuté k noticeboard.
Vrací výchozí odpověď.


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