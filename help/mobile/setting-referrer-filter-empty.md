---
title: Het filter Referrer instellen op Leeg maken
description: Meer informatie over het filter Referrer. Als u wilt dat de Adobe Experience Manager (AEM) Mobile Application Viewer apps kan weergeven op uw Author-instantie, moet u het HTML-referentiefilter instellen op 'allow empty'.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: 2f02f541-92db-469b-bf23-ec64d2e282ff
source-git-commit: 6799f1d371734b69c547f3c0c68e1e633aa63229
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Het filter Referrer instellen op Leeg maken{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Als u wilt dat de Adobe Experience Manager (AEM) Mobile Application Viewer apps kan weergeven op uw Author-instantie, moet u het HTML-referentiefilter instellen op &#39;allow empty&#39;.

Als u niet van plan bent de toepassingsviewer te gebruiken om toepassingen in ontwikkelings- en faseringsstaten te bekijken, hoeft u de standaardinstelling van het referentiefilter niet te wijzigen.

Navigeer binnen de actieve versie van Auteur van AEM naar: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) en zoek naar &#39;Apache Sling Referrer Filter&#39;. Klik om het referentiefilter te bewerken en schakel het selectievakje &#39;Lege toestaan&#39; in (zie de afbeelding hieronder). Klik vervolgens op de knop Opslaan en sluit de browserpagina.

![Filterinstellingen referentie](assets/chlimage_1-106.png)
