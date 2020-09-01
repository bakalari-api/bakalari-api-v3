# Události

## Požadavek

Všechny události:
```
GET /api/3/events (?from=YYYY-MM-dd)
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

Pouze události uživatele:
```
GET /api/3/events/my (?from=YYYY-MM-dd)
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

Veřejné události:
```
GET /api/3/events/public (?from=YYYY-MM-dd)
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

S ```from``` vrací události od tohoto data
Bez ```from``` vrací události z celého školního roku

```200 OK```

``` json
{
   "Events":[
      {
         "Id":"TBVQN",
         "Title":"Název události",
         "Description":"",
         "Times":[
            {
               "WholeDay":true,
               "StartTime":"2019-09-02T00:00:00+02:00",
               "EndTime":"2019-09-02T23:59:00+02:00"
            },
            {
               "WholeDay":false,
               "StartTime":"2019-09-03T08:00:00+02:00",
               "EndTime":"2019-09-03T10:45:00+02:00"
            }
         ],
         "EventType":{
            "Id":"SA",
            "Abbrev":"škol",
            "Name":"školní akce"
         },
         "Classes":[
            {
               "Id":"XS",
               "Abbrev":"1.A (celá)",
               "Name":"1. A (celá třída)"
            }
         ],
         "ClassSets":[

         ],
         "Teachers":[
            {
               "Id":"U  12",
               "Abbrev":"Ha",
               "Name":"Příjmení jméno"
            }
         ],
         "TeacherSets":[

         ],
         "Rooms":[
            {
               "Id":"SR",
               "Abbrev":"1a",
               "Name":""
            }
         ],
         "RoomSets":[

         ],
         "Students":[
            {
               "Id":"GQ1DS",
               "Abbrev":"",
               "Name":"Příjmení Jméno"
            }
         ],
         "Note":null,
         "DateChanged":"2019-08-30T10:30:00+02:00"
      }
   ]
}
```



Přibližně v polovině letních prázdnin začnou servery znepřístupňovat data z minulého roku, oba moduly začnou posílat prázdný seznam. Pokud ale specifikujeme ```from``` parametr (například na 1. září uplynulého školního roku) vrací modul ```my``` sice stále prázdný seznam, ale ```public``` funguje "jako normálně". Jelikož ovšem staré třídy, místnosti a žáci zřejmě neexistují v backendu v použitelné verzi, vrací server tento tvar:

```json
"Classes":[
   {
      "Id":"",
      "Abbrev":" ()",
      "Name":" ()"
   },
   ...
],
"Teachers":[
   {
      "Id":"UQBOA",
      "Abbrev":"FZ",
      "Name":"Funguje beze změny"
   },
   ...
],
"Rooms":[
   {
      "Id":"",
      "Abbrev":"",
      "Name":""
   },
   ...
],
"Students":[
  //prázdné, i když zde původně byli
]
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




