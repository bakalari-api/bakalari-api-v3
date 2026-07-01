# Zastupování

## Požadavek

```http
GET /api/3/substitutions (?from=YYYY-MM-dd)
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

## Odpověď

Bez `from` parametru vrací 14 dní od pondělí tohoto týdne S `from`
parametrem vrací 14 dní od data včetně.

```jsonc
{
  "From": "2020-06-15T00:00:00+02:00",
  "To": "2020-06-29T00:00:00+02:00",
  "Changes": [
    {
      "ChangeSubject": null,
      "Day": "2020-06-15T00:00:00+02:00",
      "Hours": "1. hod",
      "ChangeType": "Removed",
      "Description": "Vyjmuto z rozvrhu",
      "Time": "8:00 - 8:45",
      "TypeAbbrev": null,
      "TypeName": null,
    },
    {
      "ChangeSubject": null,
      "Day": "2020-06-18T00:00:00+02:00",
      "Hours": "1. hod",
      "ChangeType": "Added",
      "Description": "Přidáno do rozvrhu",
      "Time": "8:00 - 8:45",
      "TypeAbbrev": null,
      "TypeName": null,
    },
    {
      "ChangeSubject": null,
      "Day": "2020-02-28T00:00:00+01:00",
      "Hours": "3. - 4. hod",
      "ChangeType": "Canceled",
      "Description": "přednáška",
      "Time": "10:00 - 11:40",
      "TypeAbbrev": null,
      "TypeName": null,
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

### Neplatné datum

```http
400 Bad Request
```

```jsonc
{
  "Message": "The request is invalid.",
  "ModelState": {
    "$type": "HttpError",
    "from": {
      "$type": "String[]",
      "$values": ["The value 'VADNÝ_DATUM' is not valid for Nullable`1."],
    },
  },
}
```
