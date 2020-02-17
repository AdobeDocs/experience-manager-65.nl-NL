---
title: Configuratie voor gedeelde bronnen exporteren
seo-title: Configuratie voor gedeelde bronnen exporteren
description: Volg deze pagina voor meer informatie over het exporteren van gedeelde bronnen van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
seo-description: Volg deze pagina voor meer informatie over het exporteren van gedeelde bronnen van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
uuid: 99b8ff94-8135-4643-a15b-aa6fb91f5401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: 1edf6c76-ccb1-40b6-bdf6-924f1461cd28
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Configuratie voor gedeelde bronnen exporteren{#creating-shared-resources-export-configuration}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

>[!CAUTION]
>
>**Vereiste**:
>
>Alvorens over het creëren van en het wijzigen van gedeelde middelen te leren, zie de Synchronisatie [van de](/help/mobile/mobile-ondemand-contentsync.md) Inhoud om de basisconcepten te begrijpen.

AEM Mobile-gebruikers gebruiken Content Sync om live-inhoud te exporteren naar statische inhoud voor gebruik in mobiele apps. Deze export vindt plaats wanneer inhoud wordt geüpload naar Mobile On-Demand Services van AEM Mobile.

De eigenschap ***dps-exportTemplate*** die in de bovenstaande tabel wordt vermeld, definieert het pad naar de exportconfiguraties van de app. Stel deze eigenschap in om gedeelde bronnen te maken en te wijzigen.

In de volgende bronnen wordt beschreven hoe u gedeelde bronnen van Adobe Experience Manager (AEM) kunt exporteren om te uploaden naar AEM Mobile.

Met gedeelde HTML-bronnen kunnen artikelen HTML-bronnen delen die anders voor alle artikelen moeten worden gedupliceerd en kunnen pictogrammen, lettertypen, javascript en css worden opgenomen.

De configuratie van de Synchronisatie van de Inhoud die bij **&lt;dps-exportTemplate>/dps-HTMLResources>** wordt gevonden zou moeten worden gevormd om al inhoud uit te voeren een artikel voor bezit statische teruggeven op apparaat.

>[!CAUTION]
>
>U kunt de onderstaande stappen uitvoeren om voorbeelden van gedeelde bronnen weer te geven, alleen als u beschikt over:
>
>* de voorbeeldinhoud geïnstalleerd
>* AEM-instantie uitvoeren
>* geen gevormde douanecontext of een verschillende haven
>



Zie de onderstaande stappen voor een voorbeeld van een gedeelde bron:

1. Open CRXDE Lite op uw AEM server.
1. Blader naar dit pad *[/etc/contentSync/templates/dps-we-oneindig-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)*om de gedeelde voorbeeldbronnen weer te geven.

   U kunt alle eigenschappen bekijken die voor het creëren van uw gedeelde middelen zoals aangetoond in het hieronder cijfer worden vereist:

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>De gedeelde middelen zouden moeten worden geupload of worden uitgevoerd naar de Mobiele On-Demand Services van AEM wanneer om het even welke gedeelde middelen verandert.

