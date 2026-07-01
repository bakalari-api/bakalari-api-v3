# Témata

Vrací seznam hodin a jejich témata za celý školní rok v daném předmětu.

## Požadavek

```http
GET /api/3/subjects/themes/{subject_id}
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

`subject_id` je URL-kódované.

## Odpověď

```jsonc
{
  "Subject": {
    "Id": "28",
    "Abbrev": "ČJL",
    "Name": "Český jazyk a literatura",
  },
  "Themes": [
    {
      "Date": "2019-09-03T00:00:00+02:00",
      "Theme": "Světový realismus",
      "Note": "",
      "HourCaption": "1. hod",
      "LessonLabel": "1",
    },
    {
      "Date": "2019-09-05T00:00:00+02:00",
      "Theme": "D a VJR",
      "Note": "",
      "HourCaption": "6. hod",
      "LessonLabel": "2",
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
