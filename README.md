# Bakaláři API verze 3

Analýza třetí verze API školního systému Bakaláři.

Toto rozhraní (tedy API) primárně slouží ke komunikaci mezi mobilní aplikací *Bakaláři OnLine* a servery jednotlivých škol.

## URL

Všechny adresy [v seznamu endpointů](endpoints.md) začínají lomítkem. Část před lomítkem se pro každou školu liší, odpovídá umístění webové aplikace Bakaláři.

**Příklad:** Pokud je přihlášení do Bakalářů na adrese `https://www.example.com:444/login`, pak bude „část před lomítkem“ odpovídat `https://www.example.com:444`. Adresa modulu marks tedy bude `https://www.example.com:444/api/3/marks`.

## Aplikace postavené na Bakaláři API (Verze 1 & 3)
* Co si na zítra přidat a co z tašky vyndat podle Bakalářů: https://github.com/kokolem/bakalari-next-day
* Bakalarium - neoficiální klient pro Android https://github.com/kokolem/Bakalarium
* Python knihovna: https://github.com/vakabus/pybakalib
* Dart knihovna: https://github.com/soptikha2/bakalari ([pub](https://pub.dartlang.org/packages/bakalari))
* Bakalab – neoficiální klient aplikace Bakaláři: [www.bakalab.org](https://www.bakalab.org)
* Průměr Známek - aplikace pro výpočet váženého průměru s možností předvídání známek (funkční offline): [Průměr Známek na Google Play](https://play.google.com/store/apps/details?id=cz.fely.weightedaverage)
* Lepší Rozvrh - rychlejší klient pro rozvrh (funguje i offline). [Google Play](https://play.google.com/store/apps/details?id=cz.vitskalicky.lepsirozvrh&utm_source=bakalari-api), [GitHub](https://github.com/vitSkalicky/lepsi-rozvrh/)
* Bakaláři klient - Klient Bakaláři pro Windows: https://github.com/Nkaskaj/BakalariClient
* Online token generator - jednoduchý generátor tokenů pro API 1 i API 3 https://ondrovywebovky.cz/token/

Některé další programy a nástroje pracující s tímto API najdete na https://github.com/bakalari-api.

## Kam dál?

* [**Přihlášení (login)**](login.md)
* [**Endpointy**](endpoints.md)
* [Seznam škol](schools_list.md)
* [Bakaláři API v1](https://github.com/bakalari-api/bakalari-api)
* [GitHub organizace Bakaláři API](https://github.com/bakalari-api)
