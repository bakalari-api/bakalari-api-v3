# User

Vrací informace o lokaci žáka.

## Požadavek
```
GET /api/3/user/student-at-school
Content-Type: application/x-www-form-urlencoded
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

API ```3.43.0```
```200 OK```

```json
false
```

Vrací bool

## Přístupový systém
Školní server musí mít modul [Přístupový systém](https://napoveda.bakalari.cz/index.html?wa_pristsys.htm)

[user.md](moduly/user.md)
```json
{
  "EnabledModules": [
    {
      "Module": "AccessSystem",
      "Rights": [
        "CanShowStudentPresentAtSchool"
      ]
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
```{"Message":"The requested resource does not support http method 'POST'."}```
