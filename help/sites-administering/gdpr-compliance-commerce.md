---
title: AEM handel - gereedheid van de GDPR
seo-title: AEM Commerce - GDPR Readiness
description: Leer over de procedures om GDPR- verzoeken in AEM Handel te behandelen en hoe te om hen te gebruiken.
seo-description: null
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
source-git-commit: 3400df1ecd545aa0fb0e3fcdcc24f629ce4c99ba
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# AEM handel - gereedheid van de GDPR{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>De GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals de GDPR en de CCPA.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018. Zie de [GDPR-pagina in het Adobe Privacy Center](https://business.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Zie [Gereedheid AEM GDPR](/help/managing/data-protection-and-privacy.md) voor nadere bijzonderheden.

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

Met de integratie van de Handel van de Adobe uit-van-de-doos, is AEM de ervaringslaag, die de diensten verbruikt en gegevens terugstuurt naar het platform van de klantenhandel dat op een headless wijze loopt.

Voor sommige handelsplatforms, slaat de Adobe profielinformatie op ( `/home/users`) en commerciële tokens (om u aan te melden bij het handelsplatform) in AEM. Voor deze gebruiksgevallen leest u [Behandeling van GDPR-verzoeken voor het AEM Platform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Afhandeling van GDPR-verzoeken om AEM handel {#handling-gdpr-requests-for-aem-commerce}

Voor de integratie van de Salesforce-Commerce Cloud slaat AEM Commerce geen GDPR-relevante informatie op. Het verzoek doorsturen naar de [Salesforce Cloud](https://documentation.b2c.commercecloud.salesforce.com/DOC1/index.jsp).

Voor de integratie van hybris en HCL WebSphere® Commerce, zijn er sommige gegevens in AEM. Gebruik de [GDPR-instructies AEM Platform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) en bedenk de volgende vragen :

1. **Waar worden mijn gegevens opgeslagen/gebruikt?** Informatie over gebruikersprofielen in de cache, zoals naam, gebruikersnaam, token, wachtwoord en adresgegevens, zoals AEM.
1. **Met wie deel ik de gedekte GDPR-gegevens?** Een bijwerking van relevante GDPR-gegevens in AEM Handel wordt niet opgeslagen (behalve relevante profielinformatie, zoals hierboven vermeld), maar wordt doorgestuurd naar het handelsplatform.
1. **Mijn gebruikersgegevens verwijderen**? Verwijder het gebruikersprofiel in AEM en activeer de gebruikersverwijdering op het handelsplatform.

>[!NOTE]
>
>Kijk eens naar de [hybris wiki](https://wiki.hybris.com/) of de [HCL WebSphere® Commerce-documentatie](https://help.hcltechsw.com/commerce/index.html), indien nodig.
