# Příklad práce s API v jazyku Javascript

## Sehnání access tokenu skrz `fetch()`

```javascript
async function getToken(schoolUrl, username, password) {
  const url = `${schoolUrl}/api/login`;
  const head = {
    "Content-Type": "application/x-www-form-urlencoded",
  };
  const body = `client_id=ANDR&grant_type=password&username=${username}&password=${password}`;

  const response = await fetch(url, {
    method: "POST",
    headers: head,
    body: body,
  });

  const responseJson = await response.json();
  return responseJson.access_token;
}

getToken("https://example.cz", "user", "password").then((res) =>
  console.log(res),
);
```

Adresa školy `url` je vysvětlená v [README](../README.md).

Hlavička `head` je slovník, který začíná pro všechny requesty na API s
`"Content-Type": "application/x-www-form-urlencoded"`.

Do těla `body` se zadává stanovený string
`"client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD"`, kde
se `USERNAME` vymění za uživatelské jméno a `PASSWORD` za uživatelské heslo.

V Javascriptu je metoda `fetch()` asynchroní, a proto nejde pouze spustit, je
třeba definovat si asynchroní funkci pomocí `async function`. Metoda `fetch()`
vrací `Promise`, na jehož `response` je potřeba vyčkat pomocí `await`. Poté je
potřeba response převést do formátu JSON. To provedeme pomocí `await
response.json()`. Z JSON formátu poté stačí vyčíct access_token.
