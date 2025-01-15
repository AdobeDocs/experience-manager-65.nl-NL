---
title: Configuratie voor gedeelde bronnen exporteren
description: Volg deze pagina voor meer informatie over het exporteren van gedeelde bronnen uit Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 576b4567-c7b6-4196-84e7-47e980637540
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Configuratie voor gedeelde bronnen exporteren{#creating-shared-resources-export-configuration}

{{ue-over-mobile}}

>[!CAUTION]
>
>**Vereiste**:
>
>Alvorens over het creëren van en het wijzigen van gedeelde middelen te leren, zie [ Synchronisatie van de Inhoud ](/help/mobile/mobile-ondemand-contentsync.md) om de basisconcepten te begrijpen.

Adobe Experience Manager (AEM) Mobiele gebruikers gebruiken Content Sync om live-inhoud te exporteren naar statische inhoud voor gebruik in mobiele apps. Deze export vindt plaats wanneer inhoud vanuit AEM Mobile wordt geüpload naar Mobile On-Demand Services.

Het bezit ***dps-exportTemplate*** die in lijst hierboven wordt vermeld, bepaalt de weg aan de de uitvoervormen van app. Stel deze eigenschap in om gedeelde bronnen te maken en te wijzigen.

In de volgende bronnen worden gedeelde bronnen van AEM voor uploaden naar AEM Mobile beschreven.

Met gedeelde HTML-bronnen kunnen artikelen HTML-bronnen delen die anders voor alle artikelen zouden worden gedupliceerd. Deze bronnen kunnen pictogrammen, lettertypen, JavaScript en css bevatten.

De configuratie van de Synchronisatie van de Inhoud die bij **wordt gevonden &lt;dps-exportTemplate>/dps-HTMLResources>** zou moeten worden gevormd om al inhoud en artikel uit te voeren dat voor bezit statische teruggeven op apparaat wordt vereist.

>[!CAUTION]
>
>U kunt de onderstaande stappen uitvoeren om voorbeelden van gedeelde bronnen weer te geven, alleen als u beschikt over:
>
>* de voorbeeldinhoud geïnstalleerd
>* AEM uitvoeren
>* geen gevormde douanecontext of een verschillende haven
>

Zie de onderstaande stappen voor een voorbeeld van een gedeelde bron:

1. Open CRXDE Lite op uw AEM.
1. Blader naar dit pad *[/etc/contentSync/templates/dps-we-onbeperkt-app/dps-HTMLResources ](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)* om de steekproef gedeelde bronnen te bekijken.

   U kunt alle eigenschappen bekijken die voor het creëren van uw gedeelde middelen zoals aangetoond in het hieronder cijfer worden vereist:

   ![ chlimage_1-145 ](assets/chlimage_1-145.png)

>[!NOTE]
>
>De gedeelde middelen zouden moeten worden geupload of worden uitgevoerd naar AEM Mobile On-demand Services wanneer om het even welke gedeelde middelen veranderen.
