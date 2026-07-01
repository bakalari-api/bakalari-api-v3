# User

## Informace o uživateli

### Požadavek

```http
GET /api/3/user
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer ACCESS_TOKEN
```

### Odpověď

<details>
    <summary>API <code>3.14.0</code></summary>

```jsonc
{
  "UserUID": "1234/moje_id",
  "CampaignCategoryCode": "xxxxxxxxxxxxxxx_viz_níže_xxxxxxxxxxxxxxx",
  "Class": {
    "Id": "XL",
    "Abbrev": "X.A",
    "Name": "X. A", // nebo také prázdné!
  },
  "FullName": "Příjmení Jméno, X.A",
  "SchoolOrganizationName": "škola",
  "SchoolType": null,
  "UserType": "parents",
  "UserTypeText": "rodič",
  "StudyYear": 1,
  "EnabledModules": [
    {
      "Module": "Komens",
      "Rights": [
        "ShowReceivedMessages",
        "ShowSentMessages",
        "ShowNoticeBoardMessages",
        "SendMessages",
        "ShowRatingDetails",
        "SendAttachments",
      ],
    },
    {
      "Module": "Absence",
      "Rights": ["ShowAbsence", "ShowAbsencePercentage"],
    },
    {
      "Module": "Events",
      "Rights": ["ShowEvents"],
    },
    {
      "Module": "Marks",
      "Rights": ["ShowMarks", "ShowFinalMarks", "PredictMarks"],
    },
    {
      "Module": "Timetable",
      "Rights": ["ShowTimetable"],
    },
    {
      "Module": "Substitutions",
      "Rights": ["ShowSubstitutions"],
    },
    {
      "Module": "Subjects",
      "Rights": ["ShowSubjects", "ShowSubjectThemes"],
    },
    {
      "Module": "Homeworks",
      "Rights": ["ShowHomeworks"],
    },
    {
      "Module": "Gdpr",
      "Rights": ["ShowOwnConsents", "ShowChildConsents", "ShowCommissioners"],
    },
    {
      "Module": "Campaign",
      "Rights": ["ShowCampaign"],
    },
  ],
  "SettingModules": {
    "Common": {
      "$type": "CommonModuleSettings",
      "ActualSemester": {
        "SemesterId": "2",
        "From": "2020-01-04T00:00:00+01:00",
        "To": "2020-07-14T23:59:59+02:00",
      },
    },
  },
}
```

</details>

### Význam `CampaignCategoryCode`

Používá se u [informačního kanálu (campaign)](../campaign.md).

Po base64 dekódování dostaneme tuto strukturu:

```jsonc
{
  "sid": "1234", // první část UserUID
  "ut": 69,
  "sy": 1, // study year
}
```

Study year se může na mobilu a na webu lišit, [viz
#23](https://github.com/bakalari-api/bakalari-api-v3/issues/23).

### Chyby

#### Neplatný access token

```http
401 Unauthorized
```

```jsonc
{ "Message": "Authorization has been denied for this request." }
```

#### Neplatná metoda

```http
405 Method Not Allowed
```

```jsonc
{ "Message": "The requested resource does not support http method 'POST'." }
```

(Je možné, že o velkých prázdninách nebude vracet pololetí a možná ani moduly…)
