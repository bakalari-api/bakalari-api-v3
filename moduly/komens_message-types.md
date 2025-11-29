# Typy zpráv (komens)

Tento endpoint vrací list `MessageTypes` obsahující typy účtů, kterým lze odeslat nová zpráva. U každého typu účtu je se seznam odpovídajících příjemců (učitelů).

Na konci zprávy se nachází seznam `Recipients` obsahující všechny příjemnce na škole (učitele). 

## Požadavek
```
GET api/3/komens/message-types
"Content-Type: application/json"
"Authorization: Bearer ACCESS_TOKEN"
```

## Odpověď

```200 OK```
```json
{
  "MessageTypes": [
    {
      "Abbreviation": "OBECNA",
      "Name": "Obecná zpráva",
      "ShowEmailNotification": false,
      "HasTitle": true,
      "RecipientsTypes": [
        {
          "Code": "U",
          "Name": "učitel",
          "ShowCopyForClassTeacher": false,
          "ShowCopyForDirector": false,
          "ShowCopyForParent": false,
          "TypeOfSelection": "ONE",
          "Recipients": [
            {
              "Code": "AABBC",
              "IsDefault": false,
              "Abbreviation": "",
              "DisplayName": "Jan Novák Ing.",
              "Name": "Jan Novák Ing."
            }
          ]
        },
        {
          "Code": "UV",
          "Name": "učitelé - všichni",
          "ShowCopyForClassTeacher": false,
          "ShowCopyForDirector": false,
          "ShowCopyForParent": false,
          "TypeOfSelection": "ZERO",
          "Recipients": []
        }
      ],
      "SuperType": "Message",
      "ShowConfirmation": true
    },
    {
      "Abbreviation": "OMLUVENKA",
      "Name": "Omluvení absence",
      "ShowEmailNotification": false,
      "HasTitle": false,
      "RecipientsTypes": [
        {
          "Code": "U",
          "Name": "učitel",
          "ShowCopyForClassTeacher": false,
          "ShowCopyForDirector": false,
          "ShowCopyForParent": false,
          "TypeOfSelection": "ONE",
          "Recipients": [
            {
              "Code": "AABBC",
              "IsDefault": true,
              "Abbreviation": "",
              "DisplayName": "Jan Novák Ing.",
              "Name": "Jan Novák Ing."
            }
          ]
        }
      ],
      "SuperType": "Message",
      "ShowConfirmation": false
    }
  ],
  "Recipients": [
    {
      "Name": "Jan Novák Ing.",
      "Abbreviation": "",
      "Code": "AABBC",
      "DisplayName": "Jan Novák Ing."
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