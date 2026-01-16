# Podepsání známek

Podepíše zvolené známky.

## Požadavek
```
POST /api/3/marks/SetClassificationConfirmation
"Content-Type: application/json"
"Authorization: Bearer ACCESS_TOKEN"
```

do těla je nutné poslat seznam `ID` předmětů k podepsání ve formě `list`

```json
["01YE)R1-5Q","01YE)R1-7V", ...]
```

## Odpověď
Vrací 

Vrací prázdnou odpověď ```200``` při úspěchu.
Vrací prázdnou odpověď ```204``` pokud "nic" neproběhlo (známky byly již podepsány)


## Chyby

při starém / neplatném ACCESS TOKENU:

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při použití GET/PUT:

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```

Pokud chybí tělo requestu ve formátu `list`:

```500```
```{'Message': 'An error has occurred.'}```
