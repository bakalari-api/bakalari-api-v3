# Informační kanál, reklamy (campaign)

Vrací data informačního kanálu. Pro více informací [viz #23](https://github.com/bakalari-api/bakalari-api-v3/issues/23).

```
GET https://campaign.bakalari.cz/bannerinfo/$Location/$CampaignCategoryCode
```

* `Location` odpovídá platformě a umístění (`mobileapp`, `LargeBanner` nebo `SmallBannersPanel`),
* `CampaignCategoryCode` je hodnota vracená pomocí [user](moduly/user.md) modulu.



## Vrací

```json
{
  "banners": [
    {
      "messageId": 1049,
      "imageUrl": "https://www.bakalari.cz/images/kampane/NadaceAlbatros-TalentifyMe-Rodic-340x330.jpg",
      "linkUrl": "https://www.talentify.me/cs-cz",
      "priority": 50
    }
  ]
}
```



## Chyby

V případě neplatného ```CampaignCategoryCode``` vrací

```json
{
  "type":"https://tools.ietf.org/html/rfc7231#section-6.6.1",
  "title":"An error occured while processing your request.",
  "status":500,
  "detail":"Invalid category",
  "traceId":"00-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx-xxxxxxxxxxxxxxxx-00"
}
```



