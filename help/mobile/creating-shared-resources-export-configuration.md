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
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Configuratie voor gedeelde bronnen exporteren{#creating-shared-resources-export-configuration}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**Vereiste**:
>
>Voordat u leert over het maken en wijzigen van gedeelde bronnen, raadpleegt u [Inhoud synchroniseren](/help/mobile/mobile-ondemand-contentsync.md) de basisbeginselen te begrijpen.

Adobe Experience Manager (AEM) Mobiele gebruikers gebruiken Content Sync om live-inhoud te exporteren naar statische inhoud voor gebruik in mobiele apps. Deze export vindt plaats wanneer inhoud vanuit AEM Mobile wordt geüpload naar Mobile On-Demand Services.

De eigenschap ***dps-exportTemplate*** in de bovenstaande tabel wordt het pad naar de exportconfiguraties van de app gedefinieerd. Stel deze eigenschap in om gedeelde bronnen te maken en te wijzigen.

In de volgende bronnen worden gedeelde bronnen van AEM voor uploaden naar AEM Mobile beschreven.

Met gedeelde HTML-bronnen kunnen artikelen HTML-bronnen delen die anders voor alle artikelen zouden worden gedupliceerd. Deze bronnen kunnen pictogrammen, lettertypen, JavaScript en css bevatten.

De configuratie voor inhoudssynchronisatie vindt u op **&lt;dps-exporttemplate>/dps-HTMLResources>** moet worden geconfigureerd om alle inhoud te exporteren die een artikel vereist voor statische rendering van eigenschappen op een apparaat.

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
1. Bladeren naar dit pad *[/etc/contentSync/templates/dps-we-limited-app/dps-HTMLResources](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-HTMLResources)* om de gedeelde voorbeeldbronnen weer te geven.

   U kunt alle eigenschappen bekijken die voor het creëren van uw gedeelde middelen zoals aangetoond in het hieronder cijfer worden vereist:

   ![chlimage_1-145](assets/chlimage_1-145.png)

>[!NOTE]
>
>De gedeelde middelen zouden moeten worden geupload of worden uitgevoerd naar AEM Mobile On-demand Services wanneer om het even welke gedeelde middelen veranderen.
