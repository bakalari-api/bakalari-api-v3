# Bakaláři API verze 3

Analýza třetí verze API školního systému Bakaláři.

Toto rozhraní (tedy API) primárně slouží ke komunikaci mezi mobilní aplikací *Bakaláři OnLine* a servery jednotlivých škol.

## URL

Všechny adresy [v seznamu endpointů](endpoints.md) začínají lomítkem. Část před lomítkem se pro každou školu liší, odpovídá umístění webové aplikace Bakaláři.

**Příklad:** Pokud je přihlášení do Bakalářů na adrese `https://www.example.com:444/login`, pak bude „část před lomítkem“ odpovídat `https://www.example.com:444`. Adresa modulu marks tedy bude `https://www.example.com:444/api/3/marks`.

## Aplikace postavené na Bakaláři API verze 3

* Průměr Známek – aplikace pro výpočet váženého průměru s možností předvídání známek (funkční offline): [Průměr Známek na Google Play](https://play.google.com/store/apps/details?id=cz.fely.weightedaverage)
* Lepší Rozvrh – rychlejší klient pro rozvrh (funguje i offline). [Google Play](https://play.google.com/store/apps/details?id=cz.vitskalicky.lepsirozvrh&utm_source=bakalari-api), [GitLab](https://gitlab.com/vitSkalicky/lepsi-rozvrh/)
* Online token generator – jednoduchý generátor tokenů pro API v1 i v3: https://ondrovywebovky.cz/token/
* Java wrapper pro API v3: https://github.com/PanJohnny/Baka4J
* [Plochý rozvrh](https://github.com/Tomsanik/plochy-rozvrh) – snadno dostupný, přehledný a aktuální rozvrh jako součást tapety plochy.
* Asynchronní API k Bakalářům [async-bakalari-api3](https://github.com/schizza/async-bakalari-api3) ([dokumentace](https://async-bakalari-api.schizza.cz)

## Kam dál?

* [**Přihlášení (login)**](login.md)
* [**Endpointy**](endpoints.md)
* [Seznam škol](schools_list.md)
* [Bakaláři API v1](https://github.com/bakalari-api/bakalari-api)
* [GitHub organizace Bakaláři API](https://github.com/bakalari-api)
