# AGENTS.md

## Účel repozitáře

Tento repozitář dokumentuje reverzně analyzované endpointy Bakaláři API v3. Neobsahuje implementaci klienta ani automatizovaný build.

## Struktura

- `README.md` je vstupní stránka dokumentace.
- `endpoints.md` je centrální seznam známých endpointů a odkazy na jejich dokumentaci.
- `login.md` popisuje autentizaci.
- `moduly/` obsahuje dokumentaci jednotlivých modulů API; jeden soubor může pokrývat více souvisejících endpointů.
- `priklady/` obsahuje samostatné ukázky požadavků v různých jazycích a HTML.

## Zásady úprav

- Piš česky a zachovávej současný stručný styl Markdownu.
- Před popisem endpointu ověř metodu, cestu, požadované hlavičky, parametry a ukázkové odpovědi. Neuváděj domněnky jako ověřená fakta.
- Pro nový nebo přejmenovaný endpoint aktualizuj také `endpoints.md`; odkazuj na existující soubor modulu nebo jej vytvoř v `moduly/`.
- Zachovej přesné názvy polí, hodnoty enumů a rozlišení velkých a malých písmen ze skutečné odpovědi API.
- Nezveřejňuj přístupové tokeny, hesla, osobní údaje žáků ani URL konkrétních škol, pokud nejsou zjevně anonymizované.
- U příkladů používej zástupné hodnoty jako `$ID`, `example.com` a smyšlená data.

## Formát dokumentace

- Řiď se strukturou nejbližšího existujícího souboru daného modulu, aby byly endpointy konzistentní.
- Při přidání odkazu používej relativní Markdown odkazy a ověř, že cíl existuje.
- U příkladů požadavků i odpovědí preferuj malé, samostatně srozumitelné ukázky.

## Ověření změn

Pro tento repozitář nejsou definovány testy ani linter. Před odevzdáním:

1. Zkontroluj změny pomocí `git diff --check`.
2. Ověř všechny nové nebo změněné relativní odkazy a kotvy.
3. Projdi vykreslení Markdownu, zejména bloky kódu, seznamy a tabulky.
