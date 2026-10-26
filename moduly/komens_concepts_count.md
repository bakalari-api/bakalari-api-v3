# Komens

## Počet konceptů

Získá počet konceptů uživatele

## Požadavek
```
Get /api/3/komens/concepts/count
"Content-Type: application/json; charset=utf-8"
"Authorization: Bearer ACCESS_TOKEN"
```


## Odpověď

```3.52.1``` ```200 OK```
``` json
0
```

## Chyby
při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```

