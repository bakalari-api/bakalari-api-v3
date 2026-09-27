# Detail hodiny

`$ID` ve všech následujících cestách je `LessonId` získané například z přehledu třídní knihy.

## Absence v hodině

```
GET /api/3/lesson/$ID/absence
"Authorization: Bearer ACCESS_TOKEN"
```

Odpověď obsahuje `LessonId`, `ClassBookRecordId`, `AbsencesGroups`, `HourId`, `Start`, `Duration`, `Hours` a `SchoolEvents`. Každá položka `AbsencesGroups` obsahuje skupinu, nastavení typů absence a seznam absencí žáků.

```json
{
  "LessonId": "20260922070700045",
  "ClassBookRecordId": null,
  "AbsencesGroups": [
    {
      "StudentsAbsences": [
        {
          "Student": {"IsAdult": false, "RegistrationNumber": 1, "Id": "S001", "Abbrev": "N. N.", "Name": "Anonymní žák"},
          "Absences": [],
          "StudentReleased": false
        }
      ],
      "AbsentTypeOptions": [
        {"AbsentType": "", "AbsentKindEnabled": false, "AbsentKindRequired": false, "AbsentNoteEnabled": false, "AbsentKinds": [], "NextAbsentType": ""}
      ],
      "Group": {"ClassId": "1A", "Id": "AA", "Abbrev": "1.A", "Name": "1.A"}
    }
  ],
  "HourId": 7,
  "Start": 710,
  "Duration": 45,
  "Hours": [{"Id": 7, "Caption": "5", "BeginTime": "11:50", "EndTime": "12:35", "Start": 710, "Duration": 45}],
  "SchoolEvents": []
}
```

## Poslední probírané téma

```
GET /api/3/lesson/$ID/past
"Authorization: Bearer ACCESS_TOKEN"
```

```json
{
  "LessonId": "20260922070700045",
  "LastTheme": "Ukázkové téma",
  "NextLabel": "2"
}
```

## Rozvrh skupin hodiny

```
GET /api/3/lesson/$ID/studentsTimetable
"Authorization: Bearer ACCESS_TOKEN"
```

Vrací rozvrh skupin, kterých se hodina týká.

```json
{
  "StudentTimetables": [
    {
      "Hours": [{"Id": 7, "Start": 710, "Duration": 45}],
      "Id": "AA",
      "Abbrev": "1.A",
      "Name": "1.A"
    }
  ]
}
```
