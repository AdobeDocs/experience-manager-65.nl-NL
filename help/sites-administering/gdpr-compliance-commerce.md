---
title: AEM Commerce - GDPR-gereedheid
description: Meer informatie over de procedures voor het verwerken van GDPR-aanvragen in AEM Commerce en over het gebruik ervan.
contentOwner: carlino
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
solution: Experience Manager, Experience Manager Sites
feature: Compliance
role: Admin, Developer, Leader, User
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# AEM Commerce - GDPR-gereedheid{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>De GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals de GDPR en de CCPA.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018. Zie de [ pagina GDPR bij het Centrum van de Privacy van Adobe ](https://business.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Zie [ AEM GDPR Gereedheid ](/help/managing/data-protection-and-privacy.md) voor verdere details.

![ screen_shot_2018-03-22at111606 ](assets/screen_shot_2018-03-22at111606.jpg)

Met de integratie van Commerce buiten de doos van Adobe, is AEM de ervaringslaag, die de diensten verbruikt en gegevens terugstuurt naar het platform van de klantenhandel dat op een headless wijze loopt.

Voor sommige handelsplatforms, slaat Adobe profielinformatie ( `/home/users`) en handelstokens (aan login in het handelsplatform) in AEM op. Voor deze gebruiksgevallen, lees [ Behandelende GDPR- Verzoeken voor het Platform van AEM ](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![ screen_shot_2018-03-22at111621 ](assets/screen_shot_2018-03-22at111621.jpg)

## Afhandeling van GDPR-verzoeken voor AEM Commerce {#handling-gdpr-requests-for-aem-commerce}

Voor de Salesforce Commerce Cloud-integratie slaat AEM Commerce geen relevante GDPR-informatie op. Door:sturen het verzoek aan de [ Wolk van Salesforce ](https://documentation.b2c.commercecloud.salesforce.com/DOC1/index.jsp).

Voor de hybris- en HCL WebSphere® Commerce-integratie zijn er gegevens beschikbaar in AEM. Gebruik de [ GDPR instructies van het Platform van AEM ](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) en overweeg deze vragen:

1. **waar wordt mijn gegevens opgeslagen/gebruikt?** Informatie over gebruikersprofielen in de cache, zoals naam, gebruikersnaam, token, wachtwoord en adresgegevens, zoals weergegeven in AEM.
1. **met wie deel ik de overdekte gegevens GDPR?** Een update van relevante GDPR-gegevens in AEM Commerce wordt niet opgeslagen (behalve relevante profielinformatie, zoals hierboven vermeld), maar wordt doorgestuurd naar het handelsplatform.
1. **hoe te om mijn gebruikersgegevens** te schrappen? Verwijder het gebruikersprofiel in AEM en activeer de gebruikersverwijdering op het handelsplatform.

>[!NOTE]
>
>Heb een blik bij de [ hybris wiki ](https://wiki.hybris.com/) of de [ documentatie van Commerce WebSphere® HCL ](https://help.hcltechsw.com/commerce/index.html), indien nodig.
