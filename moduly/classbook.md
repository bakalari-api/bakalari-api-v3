# Třídní kniha

## Přehled hodin

```
GET /api/3/classbook?from=YYYY-MM-DDTHH:mm:ss.SSS&to=YYYY-MM-DDTHH:mm:ss.SSS
"Authorization: Bearer ACCESS_TOKEN"
```

Parametry `from` a `to` určují interval vrácených hodin.

Odpověď obsahuje dny v `Days` a číselník vyučovacích hodin v `Hours`. U hodin v jednotlivých dnech se mohou objevit například pole `Id`, `LessonId`, `Label`, `Notice`, `PrivateNotice`, `Tags`, `Theme`, `ClassBookLevel`, `WeekTheme`, `HourId`, `Date`, `Start`, `Duration`, `HourCaption`, `HourTime`, `Subject`, `Groups`, `EditableGroups`, `ChangeText` a `Supervision`.

```json
{
  "Days": [
    {
      "Date": "2026-09-22T00:00:00+02:00",
      "DayOfWeek": 2,
      "DayDescription": "",
      "DayType": "WorkDay",
      "Hours": [
        {
          "Id": "2026092207AA",
          "LessonId": "20260922070700045",
          "Label": "1",
          "Theme": "Ukázkové téma",
          "ClassBookLevel": "SecondLevel",
          "HourId": 7,
          "Subject": {"Id": "1", "Abbrev": "MAT", "Name": "Matematika"},
          "Groups": [{"ClassId": "1A", "Id": "AA", "Abbrev": "1.A", "Name": "1.A"}],
          "EditableGroups": ["AA"]
        }
      ]
    }
  ],
  "Hours": [
    {"Id": 7, "Caption": "5", "BeginTime": "11:50", "EndTime": "12:35", "Start": 710, "Duration": 45}
  ]
}
```

## Zapsání hodiny

```
POST /api/3/classbook/$ID
"Content-Type: application/json"
"Authorization: Bearer ACCESS_TOKEN"
```

`$ID` je identifikátor záznamu třídní knihy a musí odpovídat poli `Id` v těle požadavku.

```json
{
  "Id": "2026092207AA",
  "LessonId": "20260922070700045",
  "ClassBookLevel": "SecondLevel",
  "Label": "1",
  "Notice": "",
  "PrivateNotice": "",
  "Tags": [],
  "Theme": "Ukázkové téma",
  "WeekTheme": "",
  "Groups": [{"Id": "AA", "ClassId": "1A"}]
}
```

Při úspěchu vrací aktuální přehled třídní knihy ve stejném formátu jako `GET /api/3/classbook`.

## Štítky hodin

```
GET /api/3/classbook/lessonTags
"Authorization: Bearer ACCESS_TOKEN"
```

```json
[
  {"Id": "AA", "Abbreviation": "EC1", "Title": "Projekt"}
]
```
