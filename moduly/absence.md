# Absence

## Požadavek
```
GET /api/3/absence/student
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Absence podle dní a podle předmětů

```200 OK```
``` json
{
   "PercentageThreshold":0.18,
   "Absences":[
      {
         "Date":"2020-02-30T00:00:00+01:00",
         "Unsolved":0,
         "Ok":5,
         "Missed":0,
         "Late":0,
         "Soon":0,
         "School":0
      }
	  ...
   ],
   "AbsencesPerSubject":[
      {
         "SubjectName":"Český jazyk a literatura",
         "LessonsCount":18,
         "Base":3,
         "Late":0,
         "Soon":0,
         "School":0
      }
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




