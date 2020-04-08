# Stáhnutí přílohy

```
GET /api/3/komens/attachment/ID_PRILOHY
"Authorization: Bearer ACCESS_TOKEN"
```

Přestože z URL endpointu se zdá, že funguje pouze pro přílohy zpráv, tento endpoint vrací i přílohy z domácích úkolů.

`ID_PRILOHY` je samozřejmě %-kódované (mezera = `%20`)

## Chyby

- při starém/neplatném `ACCESS_TOKEN`u: Kód 401, `{"Message":"Authorization has been denied for this request."}`
- při `POST`: Kód 405, `{"Message":"The requested resource does not support http method 'POST'."}`
- při neplatném `ID_PRILOHY`: Kód 404, `{"Message":"An error has occurred."}`

## Odpověď

```
HTTP/2 200
Content-Length: 1757
Content-Type: application/octet-stream
Content-Disposition: attachment; name="=?utf-8?B?TmV2ZXIgZ29ubmEgZ2l2ZSB5b3UgdXAudHh0?="; filename*=utf-8''%4E%65%76%65%72%20%67%6F%6E%6E%61%20%67%69%76%65%20%79%6F%75%20%75%70.txt
...
```
Pokud vše proběhne v pořádku, server vrátí požadovanou přílohu jako soubor. Název souboru je v hlavičce
`Content-Disposition`.

### Název souboru

Hlavička `Content-Disposition` je trochu složitější.

Název souboru lze získat buďto z parametru `name` (který by u přílohy podle [specifikace][1]
vůbec neměl být, říká totiž z kterého `<input type="file">` soubor pochází), nebo z parametru `filename*`.

Pokud obsahuje název pouze ASCII znaky, parametr `name` vypadá takto: `name=<filename>`. V opačném případě vypadá takto:
`name="=?utf-8?B?<STRING>?="`. Daný string dekódujete na bajty pomocí base64, a ty pak dekódujete na text pomocí utf-8

Parametr `filename*` vždy obsahuje text `utf-8''` a za ním %-kódovaný název.

Python kód pro získání názvu:

```python
from cgi import parse_header
from base64 import b64decode
from urllib.parse import unquote

h = "attachment; name=\"=?utf-8?B?TmV2ZXIgZ29ubmEgZ2l2ZSB5b3UgdXAudHh0?=\"; filename*=utf-8''%4E%65%76%65%72%20%67%6F%6E%6E%61%20%67%69%76%65%20%79%6F%75%20%75%70.txt"

# z parametru name
filename = parse_header(h)[1]["name"]
if filename.startswith("=?utf-8?B?"):
    filename = b64decode(filename[10:-2]).decode()

# z parametru filename*
filename = unquote(parse_header(h)[1]["filename*"][7:])
```
[1]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Disposition
