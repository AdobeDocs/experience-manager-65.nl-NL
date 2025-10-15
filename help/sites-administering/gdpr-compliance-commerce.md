---
title: AEM Commerce - GDPR-gereedheid
description: Meer informatie over de procedures voor het verwerken van GDPR-aanvragen in AEM Commerce en over het gebruik ervan.
contentOwner: carlino
exl-id: 3a483b9d-627a-41d3-8ac1-66f9c5e89ad5
solution: Experience Manager, Experience Manager Sites
feature: Compliance
role: Admin, Architect, Developer, Leader, User, Data Architect, Data Engineer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# AEM Commerce - GDPR-gereedheid{#aem-commerce-gdpr-readiness}

>[!IMPORTANT]
>
>De GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals de GDPR en de CCPA.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018. Zie de [&#x200B; pagina GDPR bij het Centrum van de Privacy van de Adobe &#x200B;](https://business.adobe.com/nl/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Zie [&#x200B; AEM GDPR Gereedheid &#x200B;](/help/managing/data-protection-and-privacy.md) voor verdere details.

![&#x200B; screen_shot_2018-03-22at111606 &#x200B;](assets/screen_shot_2018-03-22at111606.jpg)

Met uit-van-de-doos integratie van Commerce van de Adobe, is AEM de ervaringslaag, die de diensten verbruikt en gegevens terug naar het platform van de klantenhandel verzendt dat op een headless wijze loopt.

Voor sommige handelsplatforms, slaat de Adobe profielinformatie ( `/home/users`) en handelstkens (aan login in het handelsplatform) in AEM op. Voor deze gebruiksgevallen, lees [&#x200B; Behandelende GDPR- Verzoeken naar het AEM Platform &#x200B;](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

![&#x200B; screen_shot_2018-03-22at111621 &#x200B;](assets/screen_shot_2018-03-22at111621.jpg)

## Afhandeling van GDPR-verzoeken om AEM Commerce {#handling-gdpr-requests-for-aem-commerce}

Voor de integratie van de Salesforce-Commerce Cloud slaat AEM Commerce geen relevante GDPR-informatie op. Door:sturen het verzoek aan de [&#x200B; Cloud Salesforce &#x200B;](https://documentation.b2c.commercecloud.salesforce.com/DOC1/index.jsp).

Voor de hybris- en HCL WebSphere® Commerce-integratie zijn er gegevens in AEM. Gebruik de [&#x200B; instructies van AEM Platform GDPR &#x200B;](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md) en overweeg deze vragen:

1. **waar wordt mijn gegevens opgeslagen/gebruikt?** Informatie over gebruikersprofielen in de cache, zoals naam, gebruikersnaam, token, wachtwoord en adresgegevens van AEM.
1. **met wie deel ik de overdekte gegevens GDPR?** Een update van voor GDPR relevante gegevens in AEM Commerce wordt niet opgeslagen (behalve relevante profielinformatie, zoals hierboven vermeld) maar wordt doorgestuurd naar het handelsplatform.
1. **hoe te om mijn gebruikersgegevens** te schrappen? Verwijder het gebruikersprofiel in AEM en activeer de gebruikersverwijdering op het handelsplatform.

>[!NOTE]
>
>Heb een blik bij de [&#x200B; hybris wiki &#x200B;](https://wiki.hybris.com/) of de [&#x200B; documentatie van Commerce WebSphere® HCL &#x200B;](https://help.hcltechsw.com/commerce/index.html), indien nodig.
