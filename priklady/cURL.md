## příklad použití API v cURL

Žádost o login v cURL:  
```shell
curl https://example.cz/api/login -H "Content-Type":"application/x-www-form-urlencoded" -d "client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD" --ssl-no-revoke 
```
Url na začátku je vysvětleno v [README](../README.md)
  
V parametru `-d` se musí `USERNAME` vyměnit za uživatelské jméno a `PASSWORD` vyměnit za uživatelské heslo.
  
Vyšle request o login.  
Output lze použít v `.bat` scriptech.
