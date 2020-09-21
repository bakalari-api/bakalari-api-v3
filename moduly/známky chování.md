# Výchovná opatření

vrací kázeňské přestupky a pochvaly (třídního učitele, ředitele) za celou dobu studia

## Požadavek
```
GET /api/3/marks/measures
"Content-Type: application/x-www-form-urlencoded"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

```200 OK```
``` json
{
  "PedagogicalMeasures":[
    {
      "SchoolYear":"2018/19",
      "Semester":"2",
      "TypeLabel":"důtka třídního učitele",
      "Date":"2019-02-18T00:00:00+01:00",
      "TypeId":"dTU",
      "Text":"Důtka tř&#237;dn&#237;ho učitele za nevhodn&#233; chov&#225;n&#237; během vyučov&#225;n&#237;"
    },
    {
      "SchoolYear": "2017/18",
      "Semester": "2",
      "TypeLabel": "pochvala třídního učitele",
      "Date": "2018-04-16T00:00:00+02:00",
      "TypeId": "pTU",
      "Text": "za &#250;čast v olympi&#225;d&#225;ch z odborn&#253;ch předmětů"
    }
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
