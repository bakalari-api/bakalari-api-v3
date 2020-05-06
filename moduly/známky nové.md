# Nové známky

## Požadavek
```
GET /api/3/marks/count-new
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď
vrací počet nových známek jako číslo

Zatím pokaždé vrátilo nulu, zkoušel jsem i před zobrazením známky v aplikaci, zřejmě bude nenulová pouze před zobrazením push notifikace.

```200 OK```
```0```

## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```



