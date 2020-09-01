# Web

## Možnosti webu školy
## Požadavek

```
GET /api/3/webmodule
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Možnosti spolupráce webové verze s aplikací

```200 OK```
``` json
{
   "WebModules":[
      {
         "IconId":"dokumenty",
         "SubMenu":null,
         "Url":"next/dokumentyPrehled.aspx",
         "Name":"Dokumenty"
      }
   ],
   "Dashboard":{
      "IconId":null,
      "SubMenu":null,
      "Url":"next/dash.aspx",
      "Name":null
   }
}
```



## Přihlášení do prohlížeče přes token

### Získání tokenu

## Požadavek

```
GET /api/3/logintoken
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

Jednorázový token pro autorizaci na webu bakalářů - ```LOGIN_TOKEN```

```200 OK```

``` json
"XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
```



### Přihlášení

## Požadavek

```
GET /api/3/login/LOGIN_TOKEN?returnUrl=next/dash.aspx
```

## Odpověď

Úspěšné přihlášení vrací v header ```Location``` požadované umístění

```302 Found```
```
Location: /next/dash.aspx
```

Neúspěšné přihlášení vrací adresu přihlašovací stránky

```302 Found```
```
Location: /login?ReturnUrl=next/dash.aspx
```




## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```



