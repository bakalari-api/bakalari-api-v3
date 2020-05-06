# Známky

vrací předměty a jejich známky

## Požadavek
```
GET /api/3/marks
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```


## Odpověď
Čeština je příkladem klasického známkování (1, 1-, ...).
matematika je příkladem procentuálního / bodového známkování
```200 OK```

```json
{
  "Subjects":[
    {
      "Marks":[
        {
          "MarkDate":"2020-01-28T00:00:00+01:00",
          "EditDate":"2020-02-17T08:33:00+01:00",
          "Caption":"Májovci + R + L",
          "Theme":"",
          "MarkText":"3",
          "TeacherId":"UZBNM",
          "Type":"O",
          "TypeNote":"písemná práce",
          "Weight":5,
          "SubjectId":"28",
          "IsNew":false,
          "IsPoints":false,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BNMPSLI70(",
          "PointsText":"",
          "MaxPoints":0
        },
        { 
          "MarkDate":"2020-02-13T00:00:00+01:00",
          "EditDate":"2020-02-20T07:36:00+01:00",
          "Caption":"D - Nedlouho po zahájení",
          "Theme":"",
          "MarkText":"3-",
          "TeacherId":"UZBNM",
          "Type":"W",
          "TypeNote":"písemka střední",
          "Weight":3,
          "SubjectId":"28",
          "IsNew":false,
          "IsPoints":false,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BNMVP:T:1N",
          "PointsText":"",
          "MaxPoints":0
        },
        {
          "MarkDate":"2020-02-13T00:00:00+01:00",
          "EditDate":"2020-02-20T07:36:00+01:00",
          "Caption":"VJR - Ještě než si Josef",
          "Theme":"",
          "MarkText":"2",
          "TeacherId":"UZBNM",
          "Type":"W",
          "TypeNote":"písemka střední",
          "Weight":3,
          "SubjectId":"28",
          "IsNew":false,
          "IsPoints":false,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BNMVP:T:1O",
          "PointsText":"",
          "MaxPoints":0
        }
      ],
      "Subject":{
        "Id":"28",
        "Abbrev":"ČJL ",
        "Name":"Český jazyk a literatura"
      },
      "AverageText":"2,86 ",
      "TemporaryMark":"",
      "SubjectNote":"",
      "TemporaryMarkNote":"",
      "PointsOnly":false,
      "MarkPredictionEnabled":true
    },
    {
      "Marks":[
        {
          "MarkDate":"2020-01-30T00:00:00+01:00",
          "EditDate":"2020-02-06T13:13:00+01:00",
          "Caption":"1. Statistika",
          "Theme":"",
          "MarkText":"82",
          "TeacherId":"USBOY",
          "Type":"Z",
          "TypeNote":"zkoušení písemné",
          "Weight":4,
          "SubjectId":"10",
          "IsNew":false,
          "IsPoints":true,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BOYV.N}FF4",
          "PointsText":"",
          "MaxPoints":100
        },
        {
          "MarkDate":"2020-02-07T00:00:00+01:00",
          "EditDate":"2020-02-12T18:14:00+01:00",
          "Caption":"2. Analyt.g. 1",
          "Theme":"",
          "MarkText":"76",
          "TeacherId":"USBOY",
          "Type":"Z",
          "TypeNote":"zkoušení písemné",
          "Weight":4,
          "SubjectId":"10",
          "IsNew":false,
          "IsPoints":true,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BOYD[1O_=V",
          "PointsText":"",
          "MaxPoints":100
        },
        {
          "MarkDate":"2020-02-21T00:00:00+01:00",
          "EditDate":"2020-02-25T16:07:00+01:00",
          "Caption":"3. Analyt. g. 2",
          "Theme":"",
          "MarkText":"100",
          "TeacherId":"USBOY",
          "Type":"Z",
          "TypeNote":"zkoušení písemné",
          "Weight":4,
          "SubjectId":"10",
          "IsNew":false,
          "IsPoints":true,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BOYVG*|:2|",
          "PointsText":"",
          "MaxPoints":100
        },
        {
          "MarkDate":"2020-03-06T00:00:00+01:00",
          "EditDate":"2020-03-06T16:00:00+01:00",
          "Caption":"4. Analyt. g.",
          "Theme":"",
          "MarkText":"83",
          "TeacherId":"USBOY",
          "Type":"Z",
          "TypeNote":"zkoušení písemné",
          "Weight":4,
          "SubjectId":"10",
          "IsNew":false,
          "IsPoints":true,
          "CalculatedMarkText":"",
          "ClassRankText":null,
          "Id":"BOYP9PG6KS",
          "PointsText":"",
          "MaxPoints":100
        }
      ],
      "Subject":{
        "Id":"10",
        "Abbrev":"M   ",
        "Name":"Matematika"
      },
      "AverageText":"0,85 ",
      "TemporaryMark":"",
      "SubjectNote":"",
      "TemporaryMarkNote":"",
      "PointsOnly":false,
      "MarkPredictionEnabled":true
    },
	...
  ]
}
```



## Chyby

při starém / neplatném ACCESS TOKENU

```401 Unauthorized```
```{"Message":"Authorization has been denied for this request."}```

při POST

```405 Method Not Allowed```
```{"Message":"The requested resource does not support http method 'POST'."} ```

