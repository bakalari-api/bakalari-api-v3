# Platby

## Celkový stav třídního fondu

### Požadavek

```http
GET /api/3/payments/classfund/summary
Content-Type: application/json
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

```jsonc
{
  "StudentNameWithClass": "Novák Jan (1.A)",
  "Balance": 1000.0,
  "Spent": -5052.97,
}
```

## Seznam provedených plateb (po měsících)

### Požadavek

```http
GET /api/3/payments/classfund (?sort=asc nebo ?sort=desc) (?search=hledám)
Content-Type: application/json
Authorization: Bearer ACCESS_TOKEN
```

Parametr `sort` může být `asc` (od nejstaršího data po nejnovější) nebo `desc`
(od nejnovějšího data po nejstarší).

Parametr `search` může být libovolný textový řetězec, který není prázdný (vrátí
pak chybu `400 Bad request`). Nuly a případné speciální znaky převedeme
standartně pomocí URL kódování.

### Odpověď

```jsonc
{
  "MonthlyData": [
    {
      "Date": "2024-09-01T00:00:00+02:00", // datum, kterým měsíc začíná
      "MonthlyBalance": 160,
      "Items": [
        {
          "Description": "Kino 1.A",
          "Date": "2024-09-04T00:00:00+02:00",
          "Amount": -40,
        },
        {
          "Description": "Příjem z banky (Jana Nováková)",
          "Date": "2024-09-02T00:00:00+02:00",
          "Amount": 200,
        },
      ],
    },
    {
      "Date": "2024-08-01T00:00:00+02:00",
      "MonthlyBalance": -50,
      "Items": [
        {
          "Description": "Pracovní sešit Chemie 1",
          "Date": "2024-08-29T00:00:00+02:00",
          "Amount": -400,
        },
        {
          "Description": "Příjem z banky (Jan Novák)",
          "Date": "2024-08-01T00:00:00+02:00",
          "Amount": 350,
        },
      ],
    },
  ],
}
```

V případě, že `sort` nespecifikujeme, systém vrátí platby sestupně.

## Vložit peníze

Vrací údaje pro vkládání peněz do fondu, mobilní aplikace na základě těchto dat
vytváří QR kód (není vytvářen serverem).

### Požadavek

```http
GET /api/3/payments/classfund/paymentsinfo
Content-Type: application/json
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

```jsonc
{
  "Instructions": "Pro platbu do třídního fondu použijte níže uvedený bankovní účet, specifický a variabilní symbol.",
  "BankAccount": "76327632/0300",
  "VariableSymbol": 123456789,
  "SpecificSymbol": 1111,
  "Amount": 0,
  "Message": "1.A  Novák Jan třídní fond",
}
```

## Chyby

### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```

### Prázdný parametr `search`

```http
400 Bad Request
```

```jsonc
{
  "Message": "The request is invalid.",
  "ModelState": {
    "$type": "HttpError",
    "search.String": {
      "$type": "String[]",
      "$values": ["A value is required but was not present in the request."],
    },
  },
}
```
