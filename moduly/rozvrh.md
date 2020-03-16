#Rozvrh

##stálý rozvrh:

```
GET /api/3/timetable/permanent
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCES_TOKEN"
```

##aktuální rozvrh:

```
GET /api/3/timetable/actual?date=YYYY-MM-dd
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCES_TOKEN"
```

##Chyby

při starém/neplatném ACCES TOKENU (asi bude všude stejné)
```{"Message":"Authorization has been denied for this request."}```

při POST
```{"Message":"The requested resource does not support http method 'POST'."}```

při špatně naformátovaném datu
```
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

Příklad běžného rozvrhu
```
{
  "Hours":[
    {
      "Id":2,
      "Caption":"0",
      "BeginTime":"7:05",
      "EndTime":"7:50"
    },
    {
      "Id":3,
      "Caption":"1",
      "BeginTime":"8:00",
      "EndTime":"8:45"
    },
    {
      "Id":4,
      "Caption":"2",
      "BeginTime":"8:55",
      "EndTime":"9:40"
    },
    {
      "Id":5,
      "Caption":"3",
      "BeginTime":"10:00",
      "EndTime":"10:45"
    },
    {
      "Id":6,
      "Caption":"4",
      "BeginTime":"10:55",
      "EndTime":"11:40"
    },
    {
      "Id":7,
      "Caption":"5",
      "BeginTime":"11:50",
      "EndTime":"12:35"
    },
    {
      "Id":8,
      "Caption":"6",
      "BeginTime":"12:40",
      "EndTime":"13:25"
    },
    {
      "Id":9,
      "Caption":"7",
      "BeginTime":"13:35",
      "EndTime":"14:20"
    },
    {
      "Id":10,
      "Caption":"8",
      "BeginTime":"14:30",
      "EndTime":"15:15"
    },
    {
      "Id":11,
      "Caption":"9",
      "BeginTime":"15:20",
      "EndTime":"16:05"
    },
    {
      "Id":12,
      "Caption":"10",
      "BeginTime":"16:10",
      "EndTime":"16:55"
    }
  ],
  "Days":[
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 6",
          "TeacherId":"U  12",
          "RoomId":"0X",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"Translace"
        },
        {
          "HourId":4,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 9",
          "TeacherId":"URBOT",
          "RoomId":"5H",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":5,
          "GroupIds":[
            "0D"
          ],
          "SubjectId":"15",
          "TeacherId":"U  12",
          "RoomId":"2F",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":6,
          "GroupIds":[
            "0D"
          ],
          "SubjectId":"15",
          "TeacherId":"U  12",
          "RoomId":"2F",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":7,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":8,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"11",
          "TeacherId":"U   4",
          "RoomId":"GZ",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        }
      ],
      "DayOfWeek":1,
      "Date":"2020-03-02T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"WorkDay"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":4,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"38",
          "TeacherId":"UNBO4",
          "RoomId":"0X",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":5,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":6,
          "GroupIds":[
            "0M"
          ],
          "SubjectId":"30",
          "TeacherId":"U  32",
          "RoomId":"C0",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":7,
          "GroupIds":[
            "7Z"
          ],
          "SubjectId":"13",
          "TeacherId":"UZBN3",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"The UK - revision"
        },
        {
          "HourId":8,
          "GroupIds":[
            "80"
          ],
          "SubjectId":"46",
          "TeacherId":"UAMUL",
          "RoomId":"9B",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":10,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 3",
          "TeacherId":"UUBP0",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":11,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"12",
          "TeacherId":"UQBOM",
          "RoomId":"51",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"Samostatn├í pr├íce"
        }
      ],
      "DayOfWeek":2,
      "Date":"2020-03-03T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"WorkDay"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":4,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"27",
          "TeacherId":"UZBN3",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"ID Future forms"
        },
        {
          "HourId":5,
          "GroupIds":[
            "7Z"
          ],
          "SubjectId":"13",
          "TeacherId":"UZBN3",
          "RoomId":"RR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"London"
        },
        {
          "HourId":6,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"11",
          "TeacherId":"U   4",
          "RoomId":"GZ",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":8,
          "GroupIds":[
            "80"
          ],
          "SubjectId":"46",
          "TeacherId":"UAMUL",
          "RoomId":"ZY",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":9,
          "GroupIds":[
            "0M"
          ],
          "SubjectId":"30",
          "TeacherId":"U  32",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"Text, Comic"
        }
      ],
      "DayOfWeek":3,
      "Date":"2020-03-04T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"WorkDay"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":4,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"9B",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":5,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"27",
          "TeacherId":"UZBN3",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"1A Ages and stages"
        },
        {
          "HourId":6,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 9",
          "TeacherId":"URBOT",
          "RoomId":"5H",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":8,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"12",
          "TeacherId":"UQBOM",
          "RoomId":"51",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":9,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 3",
          "TeacherId":"UUBP0",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        }
      ],
      "DayOfWeek":4,
      "Date":"2020-03-05T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"WorkDay"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"27",
          "TeacherId":"UZBN3",
          "RoomId":"RR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"Holidays Game"
        },
        {
          "HourId":4,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 6",
          "TeacherId":"U  12",
          "RoomId":"06",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"Translace"
        },
        {
          "HourId":5,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":7,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"téma"
        },
        {
          "HourId":8,
          "GroupIds":[

          ],
          "SubjectId":null,
          "TeacherId":null,
          "RoomId":null,
          "CycleIds":[

          ],
          "Change":{
            "ChangeSubject":null,
            "Day":"2020-03-06T00:00:00+01:00",
            "Hours":"6. hod",
            "ChangeType":"Removed",
            "Description":"Vyjmuto z rozvrhu (NJ, jméno)",
            "Time":"12:40 - 13:25",
            "TypeAbbrev":null,
            "TypeName":null
          },
          "HomeworkIds":[

          ],
          "Theme":null
        },
        {
          "HourId":9,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"38",
          "TeacherId":"UNBO4",
          "RoomId":"SR",
          "CycleIds":[
            "1"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":"Trh s jablky - hra"
        }
      ],
      "DayOfWeek":5,
      "Date":"2020-03-06T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"WorkDay"
    }
  ],
  "Classes":[
    {
      "Id":"XL",
      "Abbrev":"X.a",
      "Name":" X. a"
    }
  ],
  "Groups":[
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0D",
      "Abbrev":"X.a Chl",
      "Name":" X. a chlapci"
    },
    {
      "ClassId":"XL",
      "Id":"0D",
      "Abbrev":"X.a Chl",
      "Name":" X. a chlapci"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0M",
      "Abbrev":"X.a NjV1",
      "Name":" X. a N─Ťmeck├Ż jazyk Vejborov├í"
    },
    {
      "ClassId":"XL",
      "Id":"7Z",
      "Abbrev":"X.a KAJ2",
      "Name":" X. a Konverzace v Aj 2"
    },
    {
      "ClassId":"XL",
      "Id":"80",
      "Abbrev":"X.a SCvM",
      "Name":" X. a Semin├í┼Ö a cvi─Źen├ş z matematiky"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.a S2",
      "Name":" X. a Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"7Z",
      "Abbrev":"X.a KAJ2",
      "Name":" X. a Konverzace v Aj 2"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"80",
      "Abbrev":"X.a SCvM",
      "Name":" X. a Semin├í┼Ö a cvi─Źen├ş z matematiky"
    },
    {
      "ClassId":"XL",
      "Id":"0M",
      "Abbrev":"X.a NjV1",
      "Name":" X. a N─Ťmeck├Ż jazyk Vejborov├í"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.a S2",
      "Name":" X. a Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.a S2",
      "Name":" X. a Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.a S2",
      "Name":" X. a Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.a S2",
      "Name":" X. a Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.a",
      "Name":" X. a"
    }
  ],
  "Subjects":[
    {
      "Id":" 6",
      "Abbrev":"B",
      "Name":"Biologie"
    },
    {
      "Id":" 9",
      "Abbrev":"Z",
      "Name":"Zeměpis"
    },
    {
      "Id":"15",
      "Abbrev":"TV",
      "Name":"Tělesná výchova"
    },
    {
      "Id":"28",
      "Abbrev":"─îJL",
      "Name":"Český jazyk a literatura"
    },
    {
      "Id":"11",
      "Abbrev":"F",
      "Name":"Fyzika"
    },
    {
      "Id":"38",
      "Abbrev":"ZSV",
      "Name":"Základy společenských věd"
    },
    {
      "Id":"10",
      "Abbrev":"M",
      "Name":"Matematika"
    },
    {
      "Id":"30",
      "Abbrev":"NJ",
      "Name":"Německý jazyk"
    },
    {
      "Id":"13",
      "Abbrev":"KAJ",
      "Name":"Konverzace v anglickém jazyce"
    },
    {
      "Id":"46",
      "Abbrev":"SCvM",
      "Name":"Seminář a cvičení z matematiky"
    },
    {
      "Id":" 3",
      "Abbrev":"D",
      "Name":"Dějepis"
    },
    {
      "Id":"12",
      "Abbrev":"Ch",
      "Name":"Chemie"
    },
    {
      "Id":"27",
      "Abbrev":"AJ",
      "Name":"jméno"
    }
  ],
  "Teachers":[
    {
      "Id":"U  12",
      "Abbrev":"Ha",
      "Name":"jméno"
    },
    {
      "Id":"URBOT",
      "Abbrev":"JT",
      "Name":"jméno"
    },
    {
      "Id":"UZBNM",
      "Abbrev":"Kr",
      "Name":"jméno"
    },
    {
      "Id":"U   4",
      "Abbrev":"Ji",
      "Name":"jméno"
    },
    {
      "Id":"UNBO4",
      "Abbrev":"Tr",
      "Name":"jméno"
    },
    {
      "Id":"USBOY",
      "Abbrev":"UM",
      "Name":"jméno"
    },
    {
      "Id":"U  32",
      "Abbrev":"VJ",
      "Name":"jméno"
    },
    {
      "Id":"UZBN3",
      "Abbrev":"Sa",
      "Name":"jméno"
    },
    {
      "Id":"UAMUL",
      "Abbrev":"Mz",
      "Name":"jméno"
    },
    {
      "Id":"UUBP0",
      "Abbrev":"Sc",
      "Name":"jméno"
    },
    {
      "Id":"UQBOM",
      "Abbrev":"BP",
      "Name":"jméno"
    }
  ],
  "Rooms":[
    {
      "Id":"0X",
      "Abbrev":"B",
      "Name":""
    },
    {
      "Id":"5H",
      "Abbrev":"5p",
      "Name":""
    },
    {
      "Id":"2F",
      "Abbrev":"Tv1",
      "Name":""
    },
    {
      "Id":"SR",
      "Abbrev":"3a",
      "Name":""
    },
    {
      "Id":"GZ",
      "Abbrev":"F",
      "Name":""
    },
    {
      "Id":"C0",
      "Abbrev":"2p",
      "Name":""
    },
    {
      "Id":"9B",
      "Abbrev":"2a",
      "Name":""
    },
    {
      "Id":"51",
      "Abbrev":"CH",
      "Name":""
    },
    {
      "Id":"RR",
      "Abbrev":"J 33",
      "Name":""
    },
    {
      "Id":"ZY",
      "Abbrev":"7p",
      "Name":""
    },
    {
      "Id":"06",
      "Abbrev":"IVTN",
      "Name":""
    }
  ],
  "Cycles":[
    {
      "Id":"1",
      "Abbrev":"B",
      "Name":"Lichy 1"
    }
  ]
}
```

Příklad stálého rozvrhu
```{
  "Hours":[
    {
      "Id":2,
      "Caption":"0",
      "BeginTime":"7:05",
      "EndTime":"7:50"
    },
    {
      "Id":3,
      "Caption":"1",
      "BeginTime":"8:00",
      "EndTime":"8:45"
    },
    {
      "Id":4,
      "Caption":"2",
      "BeginTime":"8:55",
      "EndTime":"9:40"
    },
    {
      "Id":5,
      "Caption":"3",
      "BeginTime":"10:00",
      "EndTime":"10:45"
    },
    {
      "Id":6,
      "Caption":"4",
      "BeginTime":"10:55",
      "EndTime":"11:40"
    },
    {
      "Id":7,
      "Caption":"5",
      "BeginTime":"11:50",
      "EndTime":"12:35"
    },
    {
      "Id":8,
      "Caption":"6",
      "BeginTime":"12:40",
      "EndTime":"13:25"
    },
    {
      "Id":9,
      "Caption":"7",
      "BeginTime":"13:35",
      "EndTime":"14:20"
    },
    {
      "Id":10,
      "Caption":"8",
      "BeginTime":"14:30",
      "EndTime":"15:15"
    },
    {
      "Id":11,
      "Caption":"9",
      "BeginTime":"15:20",
      "EndTime":"16:05"
    },
    {
      "Id":12,
      "Caption":"10",
      "BeginTime":"16:10",
      "EndTime":"16:55"
    }
  ],
  "Days":[
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 6",
          "TeacherId":"U  12",
          "RoomId":"0X",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":4,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 9",
          "TeacherId":"URBOT",
          "RoomId":"5H",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":5,
          "GroupIds":[
            "0D"
          ],
          "SubjectId":"15",
          "TeacherId":"U  12",
          "RoomId":"2F",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":6,
          "GroupIds":[
            "0D"
          ],
          "SubjectId":"15",
          "TeacherId":"U  12",
          "RoomId":"2F",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":7,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":8,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"11",
          "TeacherId":"U   4",
          "RoomId":"GZ",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        }
      ],
      "DayOfWeek":1,
      "Date":"2020-03-09T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"Holiday"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":4,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"38",
          "TeacherId":"UNBO4",
          "RoomId":"0X",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":5,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":6,
          "GroupIds":[
            "0M"
          ],
          "SubjectId":"30",
          "TeacherId":"U  32",
          "RoomId":"C0",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":7,
          "GroupIds":[
            "7Z"
          ],
          "SubjectId":"13",
          "TeacherId":"UZBN3",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":8,
          "GroupIds":[
            "80"
          ],
          "SubjectId":"46",
          "TeacherId":"UAMUL",
          "RoomId":"9B",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":10,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 3",
          "TeacherId":"UUBP0",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":11,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"12",
          "TeacherId":"UQBOM",
          "RoomId":"51",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        }
      ],
      "DayOfWeek":2,
      "Date":"2020-03-10T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"Holiday"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":4,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"27",
          "TeacherId":"UZBN3",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":5,
          "GroupIds":[
            "7Z"
          ],
          "SubjectId":"13",
          "TeacherId":"UZBN3",
          "RoomId":"RR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":6,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"11",
          "TeacherId":"U   4",
          "RoomId":"GZ",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":8,
          "GroupIds":[
            "80"
          ],
          "SubjectId":"46",
          "TeacherId":"UAMUL",
          "RoomId":"ZY",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":9,
          "GroupIds":[
            "0M"
          ],
          "SubjectId":"30",
          "TeacherId":"U  32",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":10,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"11",
          "TeacherId":"U   4",
          "RoomId":"ZW",
          "CycleIds":[
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":11,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"11",
          "TeacherId":"U   4",
          "RoomId":"ZW",
          "CycleIds":[
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        }
      ],
      "DayOfWeek":3,
      "Date":"2020-03-11T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"Holiday"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":4,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"9B",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":5,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"27",
          "TeacherId":"UZBN3",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":6,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 9",
          "TeacherId":"URBOT",
          "RoomId":"5H",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":8,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"12",
          "TeacherId":"UQBOM",
          "RoomId":"51",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":9,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 3",
          "TeacherId":"UUBP0",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        }
      ],
      "DayOfWeek":4,
      "Date":"2020-03-12T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"Holiday"
    },
    {
      "Atoms":[
        {
          "HourId":3,
          "GroupIds":[
            "0X"
          ],
          "SubjectId":"27",
          "TeacherId":"UZBN3",
          "RoomId":"RR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":4,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":" 6",
          "TeacherId":"U  12",
          "RoomId":"06",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":5,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"28",
          "TeacherId":"UZBNM",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":7,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"10",
          "TeacherId":"USBOY",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":8,
          "GroupIds":[
            "0M"
          ],
          "SubjectId":"30",
          "TeacherId":"U  32",
          "RoomId":"84",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        },
        {
          "HourId":9,
          "GroupIds":[
            "0C"
          ],
          "SubjectId":"38",
          "TeacherId":"UNBO4",
          "RoomId":"SR",
          "CycleIds":[
            "5",
            "4",
            "3",
            "2",
            "1",
            "0"
          ],
          "Change":null,
          "HomeworkIds":[

          ],
          "Theme":""
        }
      ],
      "DayOfWeek":5,
      "Date":"2020-03-13T00:00:00+01:00",
      "DayDescription":"",
      "DayType":"Holiday"
    }
  ],
  "Classes":[
    {
      "Id":"XL",
      "Abbrev":"X.A",
      "Name":"X. A"
    }
  ],
  "Groups":[
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0D",
      "Abbrev":"X.A Chl",
      "Name":"X. A chlapci"
    },
    {
      "ClassId":"XL",
      "Id":"0D",
      "Abbrev":"X.A Chl",
      "Name":"X. A chlapci"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0M",
      "Abbrev":"X.A NjV1",
      "Name":"X. A Německý jazyk"
    },
    {
      "ClassId":"XL",
      "Id":"7Z",
      "Abbrev":"X.A KAJ2",
      "Name":"X. A Konverzace v Aj 2"
    },
    {
      "ClassId":"XL",
      "Id":"80",
      "Abbrev":"X.A SCvM",
      "Name":"X. A Seminář a cvičení z matematiky"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"7Z",
      "Abbrev":"X.A KAJ2",
      "Name":"X. A Konverzace v Aj 2"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"80",
      "Abbrev":"X.A SCvM",
      "Name":"X. A Seminář a cvičení z matematiky"
    },
    {
      "ClassId":"XL",
      "Id":"0M",
      "Abbrev":"X.A NjV1",
      "Name":"X. A Německý jazyk"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0X",
      "Abbrev":"X.A S2",
      "Name":"X. A Skupina 2"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    },
    {
      "ClassId":"XL",
      "Id":"0M",
      "Abbrev":"X.A NjV1",
      "Name":"X. A Německý jazyk"
    },
    {
      "ClassId":"XL",
      "Id":"0C",
      "Abbrev":"X.A",
      "Name":"X. A"
    }
  ],
  "Subjects":[
    {
      "Id":" 6",
      "Abbrev":"B",
      "Name":"Biologie"
    },
    {
      "Id":" 9",
      "Abbrev":"Z",
      "Name":"Zeměpis"
    },
    {
      "Id":"15",
      "Abbrev":"TV",
      "Name":"Tělesná výchova"
    },
    {
      "Id":"28",
      "Abbrev":"─îJL",
      "Name":"Český jazyk a literatura"
    },
    {
      "Id":"11",
      "Abbrev":"F",
      "Name":"Fyzika"
    },
    {
      "Id":"38",
      "Abbrev":"ZSV",
      "Name":"Základy společenských věd"
    },
    {
      "Id":"10",
      "Abbrev":"M",
      "Name":"Matematika"
    },
    {
      "Id":"30",
      "Abbrev":"NJ",
      "Name":"Německý jazyk"
    },
    {
      "Id":"13",
      "Abbrev":"KAJ",
      "Name":"Konverzace v anglickém jazyce"
    },
    {
      "Id":"46",
      "Abbrev":"SCvM",
      "Name":"Seminář a cvičení z matematiky"
    },
    {
      "Id":" 3",
      "Abbrev":"D",
      "Name":"Dějepis"
    },
    {
      "Id":"12",
      "Abbrev":"Ch",
      "Name":"Chemie"
    },
    {
      "Id":"27",
      "Abbrev":"AJ",
      "Name":"Anglický jazyk"
    }
  ],
  "Teachers":[
    {
      "Id":"U  12",
      "Abbrev":"Ha",
      "Name":"Mgr. Karel H..."
    },
    {
      "Id":"URBOT",
      "Abbrev":"JT",
      "Name":"Mgr. Tomáš J..."
    },
    {
      "Id":"UZBNM",
      "Abbrev":"Kr",
      "Name":"Mgr. Karel K.."
    },
    {
      "Id":"U   4",
      "Abbrev":"Ji",
      "Name":"RNDr. Josef J.."
    },
    {
      "Id":"UNBO4",
      "Abbrev":"Tr",
      "Name":"Mgr. Jaroslav T..."
    },
    {
      "Id":"USBOY",
      "Abbrev":"UM",
      "Name":"Mgr. Martina H.."
    },
    {
      "Id":"U  32",
      "Abbrev":"VJ",
      "Name":"Mgr. Jitka V.."
    },
    {
      "Id":"UZBN3",
      "Abbrev":"Sa",
      "Name":"Mgr. Jana S.."
    },
    {
      "Id":"UAMUL",
      "Abbrev":"Mz",
      "Name":"Mgr. Petr M.."
    },
    {
      "Id":"UUBP0",
      "Abbrev":"Sc",
      "Name":"Mgr. Boleslav S.."
    },
    {
      "Id":"UQBOM",
      "Abbrev":"BP",
      "Name":"Ing. Pavel B..."
    }
  ],
  "Rooms":[
    {
      "Id":"0X",
      "Abbrev":"B",
      "Name":""
    },
    {
      "Id":"5H",
      "Abbrev":"5p",
      "Name":""
    },
    {
      "Id":"2F",
      "Abbrev":"Tv1",
      "Name":""
    },
    {
      "Id":"SR",
      "Abbrev":"Xa",
      "Name":""
    },
    {
      "Id":"GZ",
      "Abbrev":"F",
      "Name":""
    },
    {
      "Id":"C0",
      "Abbrev":"2p",
      "Name":""
    },
    {
      "Id":"9B",
      "Abbrev":"2a",
      "Name":""
    },
    {
      "Id":"51",
      "Abbrev":"CH",
      "Name":""
    },
    {
      "Id":"RR",
      "Abbrev":"J 33",
      "Name":""
    },
    {
      "Id":"ZY",
      "Abbrev":"7p",
      "Name":""
    },
    {
      "Id":"ZW",
      "Abbrev":"LF",
      "Name":""
    },
    {
      "Id":"06",
      "Abbrev":"IVTN",
      "Name":""
    },
    {
      "Id":"84",
      "Abbrev":"J 37",
      "Name":""
    }
  ],
  "Cycles":[
    {
      "Id":"5",
      "Abbrev":"F",
      "Name":"Lichy 3"
    },
    {
      "Id":"4",
      "Abbrev":"D",
      "Name":"Sudy 3"
    },
    {
      "Id":"3",
      "Abbrev":"E",
      "Name":"Lichy 2"
    },
    {
      "Id":"2",
      "Abbrev":"C",
      "Name":"Sudy 2"
    },
    {
      "Id":"1",
      "Abbrev":"B",
      "Name":"Lichy 1"
    },
    {
      "Id":"0",
      "Abbrev":"A",
      "Name":"Sudy 1"
    }
  ]
}```