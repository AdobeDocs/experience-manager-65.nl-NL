---
title: Het filter Referrer instellen op Leeg maken
seo-title: Setting Your Referrer Filter to Allow Empty
description: Volg deze pagina voor meer informatie over het filter Referrer. Als u wilt dat de AEM Mobile Application Viewer apps kan weergeven op uw Author-instantie, moet u het referentiefilter voor de HTML instellen op 'allow empty'.
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 2f02f541-92db-469b-bf23-ec64d2e282ff
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Het filter Referrer instellen op Leeg maken{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework nodig hebben (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Als u wilt dat de AEM Mobile Application Viewer apps kan weergeven op uw Author-instantie, moet u het referentiefilter voor de HTML instellen op &#39;allow empty&#39;.

Als u niet van plan bent de Application Viewer te gebruiken om toepassingen in ontwikkelings- en faseringsstaten te bekijken, hoeft u de standaardinstelling van het referentiefilter niet te wijzigen.

Navigeer binnen de actieve versie van Auteur van AEM naar: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) en zoek naar &#39;Apache Sling Referrer Filter&#39;. Klik om het referentiefilter te bewerken en schakel het selectievakje &#39;Lege toestaan&#39; in (zie de afbeelding hieronder). Klik vervolgens op de knop Opslaan en sluit de browserpagina.

![Filterinstellingen referentie](assets/chlimage_1-106.png)
