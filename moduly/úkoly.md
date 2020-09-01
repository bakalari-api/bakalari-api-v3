# Úkoly

## Požadavek
```
GET /api/3/homeworks (?from=YYYY-MM-dd)
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Bez ```from``` parametru vrací úkoly 2 měsíce nazpět.
S ```from``` vrací úkoly od zadaného data do nynějška. Pokud úkol začíná například 1. a končí 10., po vyžádání například 5. se vrátí také, i když začal dříve.

Část odpovědi serveru ze dne 2020-05-05

```200 OK```
``` json
{
  "Homeworks":[
	{
      "ID":"XL80UFFIGI",
      "DateAward":"0001-01-01T00:00:00+01:00",
      "DateControl":null,
      "DateDone":"0001-01-01T00:00:00+01:00",
      "DateStart":"2020-05-05T00:00:00+02:00",
      "DateEnd":"2020-05-06T00:00:00+02:00",
      "Content":"Text zadaného úkolu/nDokonce ve dvou řádcích/na ještě k tomu s odkazem https://github.com/bakalari-api/bakalari-api-v3",
      "Notice":"",
      "Done":false,
      "Closed":false,
      "Electronic":false,
      "Hour":8,
      "Class":{
        "Id":"XL",
        "Abbrev":"X.A",
        "Name":"X. A"
      },
      "Group":{
        "Id":"80",
        "Abbrev":"SCvM",
        "Name":"Seminář a cvičení z matematiky"
      },
      "Subject":{
        "Id":"46",
        "Abbrev":"SCvM",
        "Name":"Seminář a cvičení z matematiky"
      },
      "Teacher":{
        "Id":"UAMUL",
        "Abbrev":"Př",
        "Name":"Příjmení jméno"
      },
      "Attachments":[
		{
          "Id":"UAMULAAAAA",
          "Name":"Obrázek.jpg",
          "Type":"image/jpeg",
          "Size":0
        },
		{
          "Id":"U   4AAAAG",
          "Name":"dokument.pdf",
          "Type":"application/pdf",
          "Size":609435
         },
		 ...
      ]
    },
    {
      "ID":"XL80UE^IUW",
      "DateAward":"0001-01-01T00:00:00+01:00",
      "DateControl":null,
      "DateDone":"0001-01-01T00:00:00+01:00",
      "DateStart":"2020-04-29T00:00:00+02:00",
      "DateEnd":"2020-05-05T00:00:00+02:00",
      "Content":"Text úkolu",
      "Notice":"",
      "Done":true,
      "Closed":false,
      "Electronic":false,
      "Hour":8,
      "Class":{
        "Id":"XL",
        "Abbrev":"X.A",
        "Name":"X. A"
      },
      "Group":{
        "Id":"80",
        "Abbrev":"SCvM",
        "Name":"Seminář a cvičení z matematiky"
      },
      "Subject":{
        "Id":"46",
        "Abbrev":"SCvM",
        "Name":"Seminář a cvičení z matematiky"
      },
      "Teacher":{
        "Id":"UAMUL",
        "Abbrev":"Př",
        "Name":"Příjmení jméno"
      },
      "Attachments":[

      ]
    },
	{
      "ID":"XL0CUDRKUC",
      "DateAward":"0001-01-01T00:00:00+01:00",
      "DateControl":null,
      "DateDone":"0001-01-01T00:00:00+01:00",
      "DateStart":"2020-03-17T00:00:00+01:00",
      "DateEnd":"2020-04-30T00:00:00+02:00",
      "Content":"Text úkolu",
      "Notice":"",
      "Done":true,
      "Closed":true,
      "Electronic":false,
      "Hour":10,
      "Class":{
        "Id":"XL",
        "Abbrev":"X.A",
        "Name":"X. A"
      },
      "Group":{
        "Id":"0C",
        "Abbrev":"celá",
        "Name":"celá třída"
      },
      "Subject":{
        "Id":" 3",
        "Abbrev":"D",
        "Name":"Dějepis"
      },
      "Teacher":{
        "Id":"UUBP0",
        "Abbrev":"Př",
        "Name":"Příjmení jméno"
      },
      "Attachments":[

      ]
    },
	...
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

při špatně naformátovaném datu

```400 Bad Request```
``` json
{
   "Message":"The request is invalid.",
   "ModelState":{
      "$type":"HttpError",
      "from":{
         "$type":"String[]",
         "$values":[
            "The value 'VADNÝ_DATUM' is not valid for Nullable`1."
         ]
      }
   }
}
```


