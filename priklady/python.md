# Příklad práce s API v Pythonu

## Sehnání access tokenu pomocí knihovny `requests`:

Pro práci je třeba Python knihovna `requests`. Rychlá instalace:

```bash
python -m pip install requests
```

Rychlé sehnání access tokenu:

```python
import requests

url = 'https://example.cz/api/login'
head = {'Content-Type': 'application/x-www-form-urlencoded'}
body = 'client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD'

response = requests.post(url, data=body, headers=head)
token = response.json()['access_token']
```

Adresa školy `url` je vysvětlená v [README](../README.md).

Hlavička `head` je slovník, který pro každé volání API obsahuje hlavičku
`'Content-Type': 'application/x-www-form-urlencoded'`.

V query stringu je potřeba nahradit `USERNAME` uživatelským jménem a `PASSWORD`
heslem.

Program použije funkci `requests.post`, která pošle HTTP POST request na url s
danou hlavou a tělem. Odpověď je JSON objekt, ze kterého je vyčten access token.
