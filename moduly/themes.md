# Témata

vrací seznam hodin a jejich témata za celý školní rok v daném předmětu

## Požadavek
```
GET /api/3/subjects/themes/{subject_id}
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```
Případná mezera v `{subject_id}` se nahradí `%20`.

## Odpověď

```200 OK```
``` json
{
   "Subject":{
      "Id":"28",
      "Abbrev":"ČJL",
      "Name":"Český jazyk a literatura"
   },
   "Themes":[
      {
         "Date":"2019-09-03T00:00:00+02:00",
         "Theme":"Světový realismus",
         "Note":"",
         "HourCaption":"1. hod",
         "LessonLabel":"1"
      },
      {
         "Date":"2019-09-05T00:00:00+02:00",
         "Theme":"D a VJR",
         "Note":"",
         "HourCaption":"6. hod",
         "LessonLabel":"2"
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
