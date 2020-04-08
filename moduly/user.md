# User

Vrací informace o uživateli

```
GET /api/3/user
Content-Type: application/x-www-form-urlencoded
"Authorization: Bearer ACCESS_TOKEN"
```

## Chyby
při starém/neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."}```

(Je možné, že o velkých prázdninách nebude vracet pololetí a možná ani moduly...)

Příklad
```
{
  "UserUID":"4823/moje_id",
  "Class":{
    "Id":"XL",
    "Abbrev":"X.A",
    "Name":"X. A"
  },
  "FullName":"příjmení jméno, X.A",
  "SchoolOrganizationName":"škola",
  "SchoolType":null,
  "UserType":"parents",
  "UserTypeText":"rodič",
  "StudyYear":3,
  "EnabledModules":[
    {
      "Module":"Komens",
      "Rights":[
        "ShowReceivedMessages",
        "ShowSentMessages",
        "ShowNoticeBoardMessages",
        "SendMessages",
        "ShowRatingDetails"
      ]
    },
    {
      "Module":"Absence",
      "Rights":[
        "ShowAbsence",
        "ShowAbsencePercentage"
      ]
    },
    {
      "Module":"Events",
      "Rights":[
        "ShowEvents"
      ]
    },
    {
      "Module":"Marks",
      "Rights":[
        "ShowMarks",
        "PredictMarks"
      ]
    },
    {
      "Module":"Timetable",
      "Rights":[
        "ShowTimetable"
      ]
    },
    {
      "Module":"Substitutions",
      "Rights":[
        "ShowSubstitutions"
      ]
    },
    {
      "Module":"Subjects",
      "Rights":[
        "ShowSubjects",
        "ShowSubjectThemes"
      ]
    },
    {
      "Module":"Homeworks",
      "Rights":[
        "ShowHomeworks"
      ]
    },
    {
      "Module":"Gdpr",
      "Rights":[
        "ShowOwnConsents",
        "ShowChildConsents",
        "ShowCommissioners"
      ]
    }
  ],
  "SettingModules":{
    "Common":{
      "$type":"CommonModuleSettings",
      "ActualSemester":{
        "SemesterId":"2",
        "From":"2020-01-04T00:00:00+01:00",
        "To":"2020-07-14T23:59:59+02:00"
      }
    }
  }
}
```