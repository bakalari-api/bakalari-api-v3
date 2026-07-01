# Web - možnosti webu školy

Tento modul v podstatě slouží jako taková sonda, která ukazuje, co má server
nastavené a zapnuté: jaké moduly jsou povolené, jaká nastavení jsou zapnutá,
atd.

## Možnosti spolupráce webové verze s aplikací

### Požadavek

```http
GET /api/3/webmodule
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

```http
200 OK
```

```jsonc
{
  "WebModules": [
    {
      "IconId": "dokumenty",
      "SubMenu": null,
      "Url": "next/dokumentyPrehled.aspx",
      "Name": "Dokumenty",
    },
    {
      "IconId": "vyukoveZdroje",
      "SubMenu": null,
      "Url": "next/TeachingResources.aspx",
      "Name": "Výukové zdroje",
    },
  ],
  "Dashboard": {
    "IconId": null,
    "SubMenu": null,
    "Url": "next/dash.aspx",
    "Name": null,
  },
}
```

## Přihlášení do prohlížeče přes token

### Získání tokenu

#### Požadavek

```http
GET /api/3/logintoken
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

#### Odpověď

Jednorázový token pro autorizaci na webu bakalářů; login token.

```http
200 OK
```

```jsonc
"XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```

<!-- TODO: tohle mi přijde redundantní. Možná odebrat?
-->

### Přihlášení

#### Požadavek

```http
GET /api/3/login/LOGIN_TOKEN?returnUrl=next/dash.aspx
```

#### Odpověď

Úspěšné přihlášení vrací v hlavičce `Location` požadované umístění

```http
302 Found
Location: /next/dash.aspx
```

Neúspěšné přihlášení vrací adresu přihlašovací stránky.

```http
302 Found
Location: /login?ReturnUrl=next/dash.aspx
```

#### Chyby

##### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

##### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```
