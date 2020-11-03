# Rozvrh

## Aktuální rozvrh:
[Příklad běžného rozvrhu](rozvrh_priklady/bezny.json)
formát data ```YYYY-MM-dd```

```
GET /api/3/timetable/actual?date=YYYY-MM-dd
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Stálý rozvrh:
[Příklad stálého rozvrhu](rozvrh_priklady/staly.json)

```
GET /api/3/timetable/permanent
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Prázdniny

[Příklad prázdnin](rozvrh_priklady/prazdniny.json)

O svátcích a prázdninách vrací u dnů prázdné ```Atoms``` a v parametru ```DayType``` místo ```WorkDay``` hodnoty ```Holiday``` nebo ```Celebration```
Někdy vrací i jméno události ```"DayDescription":"Nový rok"```, ```"Mistr Jan Hus"```

Pokud jsou celý týden prázdniny/volno, všechno mimo ```Hours``` je prázdné

Pro požadavky na data před začátkem aktuálního školního roku vrací 1. školní týden, resp. dny od 1. září.

Pokud je 1. září o víkendu, vrací  pro něj hodnotu  ```"DayType":"Weekend"```
Pokud je 1. září například v úterý, vrací pouze 4 dny

Na konci školního roku vrací dny až do 31.8. Pro pozdější data opět vrací poslední týden prázdnin



### Změny

Změny jsou také řešené pomocí variací ```ChangeType```

Třídní absence je řešená použitím ```Canceled``` parametru

```json
"Change":{
  "ChangeSubject":null,
  "Day":"2020-02-26T00:00:00+01:00",
  "Hours":"1. - 3. hod",
  "ChangeType":"Canceled",
  "Description":"Obecná absence třídy",
  "Time":"8:00 - 10:45",
  "TypeAbbrev":"Absc",
  "TypeName":"Obecná absence třídy"
}
```
```Added``` - změna nebo přidání hodiny

```json
"Change":{
  "ChangeSubject":null,
  "Day":"2020-02-24T00:00:00+01:00",
  "Hours":"3. hod",
  "ChangeType":"Added",
  "Description":"Přidáno do rozvrhu: B, H. Karel, B",
  "Time":"10:00 - 10:45",
  "TypeAbbrev":null,
  "TypeName":null
}
```
```Removed``` - odstranění hodiny

```json
"Change":{
  "ChangeSubject":null,
  "Day":"2020-02-26T00:00:00+01:00",
  "Hours":"7. hod",
  "ChangeType":"Removed",
  "Description":"Přesun na 26.2., 4. hod (NJ, V. Jitka)",
  "Time":"13:35 - 14:20",
  "TypeAbbrev":null,
  "TypeName":null
}
```
```RoomChanged``` - změna místnosti

```json
"Change": {
  "ChangeSubject": null,
  "Day": "2020-10-13T00:00:00+02:00",
  "Hours": "2. hod",
  "ChangeType": "RoomChanged",
  "Description": "Změna místnosti: 33 (01)",
  "Time": "8:55 - 9:40",
  "TypeAbbrev": null,
  "TypeName": null
}
```
## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."}```

při špatně naformátovaném datu
```400 Bad Request```

```json
{
  "Message":"The request is invalid.",
  "ModelState":{
    "$type":"HttpError",
    "date":{
      "$type":"String[]",
      "$values":[
        "The value 'CHYBNÝ_ŘETĚZEC' is not valid for Nullable`1."
      ]
    }
  }
}
```



