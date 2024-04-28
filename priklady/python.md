## příklad práce s API v jazyku Python

Sehnání access tokenu pomocí knihovny requests:  

Pro práci je třeba Python knihovna `requests`. Rychlá instalace:  
```shell
python -m pip install requests
```

rychlé sehnání access tokenu:  
```python
import requests

url = 'https://example.cz/api/login'
head = {'Content-Type': 'application/x-www-form-urlencoded'}
body = 'client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD'

response = requests.post(url, data=body, headers=head)
token = response.json()['access_token']
```

Adresa školy `url` je vysvětlená v [README](readme.md).  
  
Hlavička `head` je `dict`, který začíná pro každý API call začíná s `'Content-Type': 'application/x-www-form-urlencoded'`.  
  
Data je stanovený string, kde `USERNAME` se vymění za uživatelské jméno a `PASSWORD` se vymění za uživatelské heslo.  
  
Program použije funkci `requests.post`, která pošle HTTP POST request na url s danou hlavou a tělem.  
Odpověď je pak převedena to formátu JSON, ze kterého je vyčten access token.
