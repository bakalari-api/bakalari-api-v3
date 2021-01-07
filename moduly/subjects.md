# Předměty

vrací seznam předmětů a informace o jejich učitelích

## Požadavek
```
GET /api/3/subjects
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

```200 OK```
``` json
{
 "Subjects":[
    {
       "SubjectID":"28",
       "SubjectName":"Český jazyk a literatura",
       "SubjectAbbrev":"ČJL",
       "TeacherID":"UZBNM",
       "TeacherName":"Příjmení jméno",
       "TeacherAbbrev":"Př",
       "TeacherEmail":"email@skola.cz",
       "TeacherWeb":"",
       "TeacherSchoolPhone":null,
       "TeacherHomePhone":null,
       "TeacherMobilePhone":null
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

