# Předměty

Vrací seznam předmětů a informace o jejich učitelích.

## Požadavek

```http
GET /api/3/subjects
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

## Odpověď

```jsonc
{
  "Subjects": [
    {
      "SubjectID": "28",
      "SubjectName": "Český jazyk a literatura",
      "SubjectAbbrev": "ČJL",
      "TeacherID": "UZBNM",
      "TeacherName": "Příjmení jméno",
      "TeacherAbbrev": "Př",
      "TeacherEmail": "email@skola.cz",
      "TeacherWeb": "",
      "TeacherSchoolPhone": null,
      "TeacherHomePhone": null,
      "TeacherMobilePhone": null,
    },
    // ...
  ],
}
```

## Chyby

### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
