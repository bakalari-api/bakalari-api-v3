# API info

## Požadavek
```
GET /api
```

## Odpověď

Přehled všech dostupných API verzí

```200 OK```
``` json
[{"ApiVersion":"3.12.0","ApplicationVersion":"1.32.625.2","BaseUrl":"api/3"}]
```



## Požadavek

```
GET /api/3
```

## Odpověď

Informace o API (v tomto případě verze 3)

```200 OK```
``` json
{"ApiVersion":"3.12.0","ApplicationVersion":"1.32.625.2","BaseUrl":"api/3"}
```



## Chyby

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```







