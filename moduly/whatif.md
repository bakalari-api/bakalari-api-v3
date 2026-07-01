# Předvídač

## Výsledek průměru z Předvídače včetně seznamu známek

### Požadavek

```http
POST /api/3/marks/what-if
"Content-Type: application/json; charset=utf-8"
"Authorization: Bearer ACCESS_TOKEN"
```

Do těla vkládáme kopii známek předmětu z [/api/3/marks](/moduly/marks.md) podle
následující ukázky a poté předvídané známky (mají ID null).

```jsonc
[
  {
    "Id": "BNMPSLI70(",
    "MarkText": "3",
    "Weight": 5,
    "MaxPoints": 0,
    "SubjectId": "28",
  },
  {
    "Id": "BNMVP:T:1N",
    "MarkText": "3-",
    "Weight": 3,
    "MaxPoints": 0,
    "SubjectId": "28",
  },
  {
    "Id": null,
    "MarkText": "1",
    "Weight": 3,
    "MaxPoints": 0,
    "SubjectId": "28",
  },
]
```

### Odpověď

```http
200 OK
```

```jsonc
{
  "Marks": [
    {
      "MarkDate": "2020-01-28T00:00:00+01:00",
      "EditDate": "2020-02-17T08:33:00+01:00",
      "Caption": "Májovci + R + L",
      "Theme": "",
      "MarkText": "3",
      "TeacherId": "UZBNM",
      "Type": "O",
      "TypeNote": "písemná práce",
      "Weight": 5,
      "SubjectId": "28",
      "IsNew": false,
      "IsPoints": false,
      "CalculatedMarkText": "",
      "ClassRankText": null,
      "Id": "BNMPSLI70(",
      "PointsText": "",
      "MaxPoints": 0,
    },
    {
      "MarkDate": "2020-02-13T00:00:00+01:00",
      "EditDate": "2020-02-20T07:36:00+01:00",
      "Caption": "D - Nedlouho po zahájení",
      "Theme": "",
      "MarkText": "3-",
      "TeacherId": "UZBNM",
      "Type": "W",
      "TypeNote": "písemka střední",
      "Weight": 3,
      "SubjectId": "28",
      "IsNew": false,
      "IsPoints": false,
      "CalculatedMarkText": "",
      "ClassRankText": null,
      "Id": "BNMVP:T:1N",
      "PointsText": "",
      "MaxPoints": 0,
    },
    {
      "MarkDate": "2020-02-21T15:34:12+01:00",
      "EditDate": "2020-02-21T15:34:12+01:00",
      "Caption": null,
      "Theme": null,
      "MarkText": "1",
      "TeacherId": null,
      "Type": null,
      "TypeNote": null,
      "Weight": 3,
      "SubjectId": "28",
      "IsNew": false,
      "IsPoints": false,
      "CalculatedMarkText": "",
      "ClassRankText": null,
      "Id": null,
      "PointsText": "",
      "MaxPoints": 0,
    },
  ],
  "Subject": {
    "Id": "28",
    "Abbrev": "ČJL ",
    "Name": "Český jazyk a literatura",
  },
  "AverageText": "2,59 ",
  "TemporaryMark": "",
  "SubjectNote": "",
  "TemporaryMarkNote": "",
  "PointsOnly": false,
  "MarkPredictionEnabled": true,
}
```

### Chyby

#### Předmět s hodnotou `MarkPredictionEnabled` nastavenou na `false`

```http
403 Forbidden
```

```jsonc
{ "Message": "An error has occurred." }
```

#### Neplatný ACCESS TOKEN

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

#### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'GET'." }
```
