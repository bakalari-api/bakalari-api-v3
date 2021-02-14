# Seznam škol

Toto téma bylo diskutováno v [bakalari-api/bakalari-api#38](https://github.com/bakalari-api/bakalari-api/issues/38).

## Získání seznamu měst

### Požadavek

```
GET https://sluzby.bakalari.cz/api/v1/municipality
Accept: application/json
```

### Odpověď

```json
[
  {
    "name": "",
    "schoolCount": 2
  },
  {
    "name": "Albrechtice",
    "schoolCount": 1
  },
  {
    "name": "Aš",
    "schoolCount": 3
  },
  ...
]
```

bez ```Accept: application/json``` vrací stejná data, jen ve XML struktuře

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ArrayOfmunicipalityInfo xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
   <municipalityInfo>
      <name />
      <schoolCount>2</schoolCount>
   </municipalityInfo>
   <municipalityInfo>
      <name>Albrechtice</name>
      <schoolCount>1</schoolCount>
   </municipalityInfo>
   <municipalityInfo>
      <name>Aš</name>
      <schoolCount>3</schoolCount>
   </municipalityInfo>
   ...
</ArrayOfmunicipalityInfo>
```

## Seznam škol

### Požadavek

```
GET https://sluzby.bakalari.cz/api/v1/municipality/$mesto
Accept: application/json
```

Parametr ```mesto``` musí být správně URL encoded, například
Benešov u Prahy → Bene%C5%A1ov%20u%20Prahy

U měst s tečkou ve jméně (*např.: Ostrava-Mar.Hory*) server vrací ```404```, pro platnou odpověď je nutno použít pouze část před tečkou (*Ostrava-Mar*)

### Odpověď

```json
{
  "name": "beroun",
  "schools": [
    {
      "id": "SYHKTAAAAB",
      "name": "Mateřská škola Montessori Beroun a Základní škola s.r.o.",
      "schoolUrl": "https://montessori-beroun.bakalari.cz"
    },
    {
      "id": "SYDATAAABA",
      "name": "Základní škola, Beroun - Závodí, Komenského 249",
      "schoolUrl": "https://zavodi.bakalari.cz"
    },
    {
      "id": "SYDATAADKO",
      "name": "Manažerská akademie, soukromá střední škola",
      "schoolUrl": "https://maberoun.bakalari.cz/"
    },
    ...
  ]
}
```

bez ```Accept: application/json``` vrací stejná data, jen ve XML struktuře

```xml
<municipality
  xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <name>beroun</name>
  <schools>
    <schoolInfo>
      <id>SYHKTAAAAB</id>
      <name>Mateřská škola Montessori Beroun a Základní škola s.r.o.</name>
      <schoolUrl>https://montessori-beroun.bakalari.cz</schoolUrl>
    </schoolInfo>
    <schoolInfo>
      <id>SYDATAAABA</id>
      <name>Základní škola, Beroun - Závodí, Komenského 249</name>
      <schoolUrl>https://zavodi.bakalari.cz</schoolUrl>
    </schoolInfo>
    <schoolInfo>
      <id>SYDATAADKO</id>
      <name>Manažerská akademie, soukromá střední škola</name>
      <schoolUrl>https://maberoun.bakalari.cz/</schoolUrl>
    </schoolInfo>
    ... 
  </schools>
</municipality> 
```
