---
title: AEM handel - gereedheid van de GDPR
seo-title: AEM handel - gereedheid van de GDPR
description: 'null'
seo-description: 'null'
uuid: 7ca26587-8cce-4c75-8629-e0e5cfb8166c
contentOwner: carlino
discoiquuid: c637964a-dfcb-41fe-9c92-934620fe2cb3
translation-type: tm+mt
source-git-commit: 85a3dac5db940b81da9e74902a6aa475ec8f1780
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# AEM handel - GDPR-gereedheid{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy; zoals GDPR, CCPA enz.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018. Zie de [GDPR-pagina in het Adobe Privacy Center](https://www.adobe.com/privacy/general-data-protection-regulation.html) voor meer informatie.

>[!NOTE]
>
>Zie [AEM GDPR-gereedheid](/help/managing/data-protection-and-privacy.md) voor meer informatie.

![screen_shot_2018-03-22at111606](assets/screen_shot_2018-03-22at111606.jpg)

In onze out-of-the-box Integraties van de Handel, is AEM de ervaringslaag, die de diensten verbruikt en gegevens terugstuurt naar het platform van de klantenhandel dat op een headless wijze loopt.

Voor sommige handelsplatforms, slaan wij profielinformatie ( `/home/users`) en handelstkens (aan login in het handelsplatform) in AEM op. Lees voor deze gevallen [GDPR-verzoeken voor het AEM Platform afhandelen](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![screen_shot_2018-03-22at111621](assets/screen_shot_2018-03-22at111621.jpg)

## Afhandeling van GDPR-verzoeken om AEM handel {#handling-gdpr-requests-for-aem-commerce}

Voor de integratie van de Salesforce-Commerce Cloud slaat AEM Commerce geen relevante GDPR-informatie op. U zou het verzoek aan [Salesforce Cloud](https://documentation.demandware.com/) moeten door:sturen.

Voor de hybris- en IBM WebSphere-integratie zijn er gegevens in AEM. U zou [AEM Platform GDPR instructies](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) moeten gebruiken en deze vragen overwegen:

1. **Waar worden mijn gegevens opgeslagen/gebruikt?** In de cache geplaatste gegevens van gebruikersprofielen, zoals naam, handelgebruikers-id, token, wachtwoord, adresgegevens, enzovoort, worden AEM weergegeven.
1. **Met wie deel ik de gedekte GDPR-gegevens?** Een bijwerking van relevante GDPR-gegevens in AEM Handel wordt niet opgeslagen (behalve relevante profielinformatie, zoals hierboven vermeld), maar wordt doorgestuurd naar het handelsplatform.
1. **Hoe kan ik mijn gebruikersgegevens** verwijderen? Verwijder het gebruikersprofiel in AEM en activeer de gebruikersverwijdering op het handelsplatform.

>[!NOTE]
>
>Bekijk de [hybris wiki](https://wiki.hybris.com/) of [documentatie van de Handel van Websphere](https://www-01.ibm.com/support/docview.wss?uid=swg27036450) indien vereist.

