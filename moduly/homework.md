# Úkoly

Související endpointy: [přílohy](attachment.md), [označování hotových/nehotových úkolů](student-done.md)

## Požadavek
```
GET /api/3/homeworks (?from=YYYY-MM-dd) (?to=YYYY-MM-dd)
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Parametry `from` a `to` jsou nepovinné. `from` má výchozí hodnotu 14 dní nazpět, `to` jeden den dopředu. Bakaláři poté vrátí všechny úkoly, které byly zadané nebo mají datum odevzdání v tomto rozsahu. Tzn. když `from == to == "2020-10-20"`, tak nedostanete úkol, který byl zadaný 19. 10. a má být odevzdaný 21. 10.

API ```3.14.0```
```200 OK```

```json
{
   "Homeworks":[
      {
         "ID":"XLBJULQIGG",
         "DateStart":"2020-11-10T00:00:00+01:00",
         "DateEnd":"2020-11-11T00:00:00+01:00",
         "Content":"Text zadaného úkolu/nDokonce ve dvou řádcích/na ještě k tomu s odkazem https://github.com/bakalari-api/bakalari-api-v3",
         "Notice":"",
         "Done":true,
         "Closed":true,
         "Electronic":false,
         "Hour":7,
         "Class":{
            "Id":"XL",
            "Abbrev":"X.A",
            "Name":"X. A"
         },
         "Group":{
            "Id":"BJ",
            "Abbrev":"Sk",
            "Name":"Skupina"
         },
         "Subject":{
            "Id":"44",
            "Abbrev":"Skrtk",
            "Name":"Předmět"
         },
         "Teacher":{
            "Id":"U5JMC",
            "Abbrev":"Př",
            "Name":"Příjmení Jméno"
         },
         "Attachments":[
            {
               "Id":"xx...xx",
               "Name":"Soubor.pdf",
               "Type":"application/pdf",
               "Size":123456
            }
         ],
         "Finished":false
      },
      ...
  ]
}  
```

API ```3.13.0``` a níže
Navíc existovali parametry ```DateAward```, ```DateControl```, ```DateDone```, pro změnu neexistovalo ```Finished```.

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


