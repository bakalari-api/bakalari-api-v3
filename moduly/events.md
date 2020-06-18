# Události

## Požadavek

Všechny události:
```
GET /api/3/events
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

Pouze události uživatele:
```
GET /api/3/events/my
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Vrací události z celého školního roku

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

## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```




