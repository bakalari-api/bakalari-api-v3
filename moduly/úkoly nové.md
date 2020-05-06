# Nové úkoly


## Požadavek
```
GET /api/3/homeworks/count-actual
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```


## Odpověď
vrací počet úkolů s hodnotou ```"Closed":false```

```200 OK```
```6```


## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```
