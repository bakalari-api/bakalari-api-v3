# Informační kanál

vrací data informačního kanálu

```
GET https://campaign.bakalari.cz/bannerinfo/mobileapp/$CampaignCategoryCode
```

```CampaignCategoryCode``` je hodnota vracená pomocí [user](user.md) modulu



## Vrací

dosud nezdokumentováno

```json
{
  "banners":null
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



