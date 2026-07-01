# Login

Slouží k získání a obnově tokenů pro přístup k API

## Požadavek

```http
POST /api/login
Content-Type: application/x-www-form-urlencoded
```

## První přihlášení

Body: `client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD`

Výsledek requestu: _(Počty znaků jsou pouze orientační, aby někdo nebyl zaskočen
jejich délkou, která se od starších verzí API rapidně změnila)_

```jsonc
{
  "bak:ApiVersion": "3.13.0",
  "bak:AppVersion": "1.35.1029.1",
  "bak:UserId": "XXXXX",
  "access_token": "ACCESSTOKEN - 2556 znaků",
  "refresh_token": "REFRESHTOKEN - 3459 znaků",
  "id_token": "id_token - 872 znaků", // není vždy dostupné
  "token_type": "Bearer",
  "expires_in": 3599,
  "scope": "openid profile offline_access bakalari_api",
}
```

Pro starší verze API vypadá odpověď následovně:

```jsonc
{
  "access_token": "ACCESSTOKEN",
  "token_type": "bearer",
  "expires_in": 599,
  "refresh_token": "REFRESHTOKEN",
  "bak:ApiVersion": "3.8.0",
  "bak:AppVersion": "1.28.306.4",
  "bak:UserId": "XXXXX",
}
```

Pro práci s dalšími endpointy je nezbytné používat tzv. access token pomocí
hlavičky `Authorization: Bearer $ACCESSTOKEN`

## Přihlášení pomocí refresh tokenu

Body: `client_id=ANDR&grant_type=refresh_token&refresh_token=REFRESHTOKEN`

Vrací stejnou strukturu body jako při prvním přihlášení. Zdá se, že i refresh
token asi po měsíci bez obnovy vyprší a je nutné nové přihlášení pomocí loginu a
hesla.

## Význam tokenů

Tokeny jsou standardní tokeny [JWT](https://www.jwt.io/introduction), tudíž
obsahují hlavičku, tělo, a ocásek (s podpisem) a tečky oddělující jednotlivé
části.

Po dekódování z base64 vypadají jednotlivé části takto:

### Hlavička `ACCESS_TOKEN`

```jsonc
{
  "alg": "RSA-OAEP",
  "enc": "A256CBC-HS512",
  "kid": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "typ": "at+jwt",
}
```

### Hlavička `REFRESH_TOKEN`

```jsonc
{
  "alg": "RSA-OAEP",
  "enc": "A256CBC-HS512",
  "kid": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "typ": "oi_reft+jwt",
}
```

### Tělo

```jsonc
{
  "sub": "XXXXXX",
  "oi_au_id": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "jti": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "azp": "ANDR",
  "at_hash": "XXXXXXXXXXXXXXXXXXXXXX",
  "oi_tkn_id": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "aud": "ANDR",
  "exp": 1601454600, //platný 30 minut
  "iss": "https://bakalari.skola.cz/",
  "iat": 1601452800,
}
```

## Chyby

Vždy odpovídá s `400 Bad Request`

### Nesprávné údaje

```jsonc
{
  "error": "invalid_grant",
  "error_description": "Špatný login nebo heslo",
}
```

### Neplatný refresh token

```jsonc
{
  "error": "invalid_grant",
  "error_description": "The specified token is invalid.",
}
```

### Opakované použití refresh tokenu

```jsonc
{
  "error": "invalid_grant",
  "error_description": "The specified refresh token has already been redeemed.",
}
```

_Aktuální verze API má v sobě chybu (pokud to tedy není funkce), že jeden
refresh token jde použít vícekrát pro získání rozdílných validních párů tokenů.
Tato chybová odpověď se začne objevovat až po čtvrtém requestu se stejným
tokenem. Tzn. jdou vygenerovat až 3 access tokeny a 3 refresh tokeny z jednoho
refresh tokenu. K této duplikaci tokenů by ale běžně nemělo docházet, a proto ji
prosím nepoužívejte (+není 100% zdokumentovaná) a uchovávejte vždy poslední pár
tokenů_

### Chybějící grant type

```jsonc
{
  "error": "invalid_request",
  "error_description": "The mandatory 'grant_type' parameter is missing.",
}
```

### Chybějící client ID

```jsonc
{
  "error": "invalid_client",
  "error_description": "The mandatory 'client_id' parameter is missing.",
}
```

### Chybějící `client_id` nebo `grant_type` na starší API

```jsonc
{
  "error": "invalid_client",
  "error_description": "Unknown Client or invalid grant type.",
}
```
