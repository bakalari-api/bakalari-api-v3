# User

## Informace o lokaci žáka

### Požadavek

```http
GET /api/3/user/student-at-school
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

<details>
    <summary>API <code>3.43.0</code></summary>

```jsonc
false
```

</details>

## Přístupový systém

Školní server musí mít modul [Přístupový
systém](https://napoveda.bakalari.cz/index.html?wa_pristsys.htm)

[user.md](moduly/user.md)

```jsonc
{
  "EnabledModules": [
    {
      "Module": "AccessSystem",
      "Rights": ["CanShowStudentPresentAtSchool"],
    },
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
