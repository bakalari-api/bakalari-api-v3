# Login
Slouží k získání a obnově tokenů pro přístup k API


## Požadavek
```
POST /api/login
Content-Type: application/x-www-form-urlencoded
```



## První přihlášení

Body: `client_id=ANDR&grant_type=password&username=USERNAME&password=PASSWORD`

Výsledek requestu:
*(Počty znaků jsou pouze orientační, aby někdo nebyl zaskočen jejich délkou, která se od starších verzí API rapidně změnila)*

```json
{
   "bak:ApiVersion":"3.13.0",
   "bak:AppVersion":"1.35.1029.1",
   "bak:UserId":"XXXXX",
   "access_token":"ACCESSTOKEN - 2556 znaků",
   "refresh_token":"REFRESHTOKEN - 3459 znaků",
   "id_token":"id_token - 872 znaků",
   "token_type":"Bearer",
   "expires_in":3599,
   "scope":"openid profile offline_access bakalari_api"
}
//starší verze API
{
  "access_token": "ACCESSTOKEN",
  "token_type": "bearer",
  "expires_in": 599,
  "refresh_token": "REFRESHTOKEN",
  "bak:ApiVersion": "3.8.0",
  "bak:AppVersion": "1.28.306.4",
  "bak:UserId": "XXXXX"
}
```

Pro práci s dalšími endpointy je nezbytné používat tzv. access token pomocí hlavičky `Authorization: Bearer ACCESSTOKEN`



## Přihlášení pomocí refresh tokenu
Body: `client_id=ANDR&grant_type=refresh_token&refresh_token=REFRESHTOKEN`

Vrací stejnou strukturu body jako při prvním přihlášení.
Zdá se, že i refresh token asi po měsíci bez obnovy vyprší a je nutné nové přihlášení pomocí hesla



## Význam tokenů

Tokeny jsou složeny z jednotlivých částí oddělených tečkami
```REFRESH``` token je složen z ```ACCESS``` tokenu a další části

první část ```ACCESS```/```REFRESH``` tokenu po dekódování pomocí Base64

```json
{
   "alg":"RSA-OAEP",
   "enc":"A256CBC-HS512",
   "kid":"XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
   "typ":"oi_reft+jwt"
}
```

```ID token``` je zpracovaný podle ```JWT``` standardu

```json
Header
{
  "alg": "RS256",
  "kid": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "typ": "JWT",
  "x5t": "XXXXXXXXXXXXXXXXXXXXXXXXXXX"
}

Body
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
  "iat": 1601452800
}
```



## Chyby

Bez ```client_id```, nebo ```grant_type``` dostaneme

```
{
  "error": "invalid_client",
  "error_description": "Unknown Client or invalid grant type."
}
```

Bez validního ```refresh_token``` je odpovědí následující:

```
{
  "error":"invalid_grant",
  "error_description":"The specified token is invalid."
}
```
