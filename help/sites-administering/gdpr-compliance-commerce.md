---
title: AEM handel - gereedheid van de GDPR
seo-title: AEM Commerce - GDPR Readiness
description: "AEM handel - gereedheid van de GDPR"
seo-description: null
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# AEM handel - gereedheid van de GDPR{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy; zoals GDPR, CCPA enz.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018. Zie voor meer informatie [GDPR-pagina in het Adobe Privacy Center](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Zie [Gereedheid AEM GDPR](/help/managing/data-protection-and-privacy.md) voor nadere bijzonderheden.

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

In onze out-of-the-box Integraties van de Handel, is AEM de ervaringslaag, die de diensten verbruikt en gegevens terugstuurt naar het platform van de klantenhandel dat op een headless wijze loopt.

Voor sommige handelsplatforms slaan wij profielinformatie op ( `/home/users`) en commerciële tokens (aan login in het handelsplatform) in AEM. Voor deze gebruiksgevallen, gelieve te lezen [Afhandeling van GDPR-verzoeken voor het AEM Platform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Afhandeling van GDPR-verzoeken om AEM handel {#handling-gdpr-requests-for-aem-commerce}

Voor de integratie van de Salesforce-Commerce Cloud slaat AEM Commerce geen relevante GDPR-informatie op. U moet het verzoek doorsturen naar de [Salesforce Cloud](https://documentation.demandware.com/).

Voor de hybris- en IBM WebSphere-integratie zijn er gegevens in AEM. U moet de opdracht [GDPR-instructies AEM Platform](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) en bedenk deze vragen :

1. **Waar worden mijn gegevens opgeslagen/gebruikt?** In de cache geplaatste gegevens van gebruikersprofielen, zoals naam, handelgebruikers-id, token, wachtwoord, adresgegevens, enzovoort, worden AEM weergegeven.
1. **Met wie deel ik de gedekte GDPR-gegevens?** Een bijwerking van relevante GDPR-gegevens in AEM Handel wordt niet opgeslagen (behalve relevante profielinformatie, zoals hierboven vermeld), maar wordt doorgestuurd naar het handelsplatform.
1. **Mijn gebruikersgegevens verwijderen**? Verwijder het gebruikersprofiel in AEM en activeer de gebruikersverwijdering op het handelsplatform.

>[!NOTE]
>
>Kijk eens naar de [hybris wiki](https://wiki.hybris.com/) of de [Websphere Commerce-documentatie](https://www-01.ibm.com/support/docview.wss?uid=swg27036450) indien nodig.
