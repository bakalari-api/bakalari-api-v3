## příklad práce s API v jazyku Javascript

Sehnání access tokenu pomocí metody fetch:
```javascript
url = "https://example.cz/api/login"
header = {"Content-Type": "application/x-www-form-urlencoded"}
body = "client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD"

async function getToken() {
  var response = await fetch(url, {
    method: "POST",
    headers: header,
    body: body
  })

  var responseJson = await response.json()
  return responseJson.access_token
}
```

Adresa školy `url` je vysvětlená v [README](readme.md).  

Hlavička `header` je slovník, který začíná pro všechny requesty na API s `"Content-Type": "application/x-www-form-urlencoded"`.  

Do těla `body` se zadává stanovený string `"client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD"`, kde se `USERNAME` vymění za uživatelské jméno a `PASSWORD` za uživatelské heslo.  

V Javascriptu je metoda `fetch()` asynchroní, a proto nejde pouze spustit, je třeba definovat si asynchroní funkci pomocí `async function`. Metoda `fetch()` vrací `Promise`, na jehož `response` je potřeba vyčkat pomocí `await`.  
Poté je potřeba response převést do formátu JSON.  
To provedeme pomocí `await response.json()`.  
Z JSON formátu poté stačí vyčíct access_token.
