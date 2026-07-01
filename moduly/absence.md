# Absence

## Požadavek

```http
GET /api/3/absence/student
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

## Odpověď

Absence podle dní a podle předmětů bez oprávnění `ShowAbsencePercentage` vrací
prázdné `AbsencesPerSubject`

```jsonc
{
  "PercentageThreshold": 0.18,
  "Absences": [
    {
      "Date": "2020-02-30T00:00:00+01:00",
      "Unsolved": 0,
      "Ok": 5,
      "Missed": 0,
      "Late": 0,
      "Soon": 0,
      "School": 0,
      "DistanceTeaching": 0,
    },
    /// ...
  ],
  "AbsencesPerSubject": [
    {
      "SubjectName": "Český jazyk a literatura",
      "LessonsCount": 18,
      "Base": 3,
      "Late": 0,
      "Soon": 0,
      "School": 0,
      "DistanceTeaching": 0,
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

### Chybná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
