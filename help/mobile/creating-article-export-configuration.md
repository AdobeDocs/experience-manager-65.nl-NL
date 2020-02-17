---
title: Artikel-exportconfiguratie maken
seo-title: Artikel-exportconfiguratie maken
description: Volg deze pagina voor meer informatie over het exporteren van inhoud van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
seo-description: Volg deze pagina voor meer informatie over het exporteren van inhoud van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Artikel-exportconfiguratie maken{#creating-article-export-configuration}

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

In de volgende bronnen wordt beschreven hoe u inhoud exporteert van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.

Artikelen hebben inhoud die moet worden geëxporteerd en geüpload. Een deel van deze inhoud kan worden gedeeld tussen artikelen.

Gebruik [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) om de inhoud samen te verzamelen en een pakket ***Gedeelde bronnen*** te maken.

De configuratie ContentSync gevonden bij **&lt;dps-exportTemplate>/dps-article>** zou moeten worden gevormd om alle inhoud en artikel uit te voeren die voor bezit statische teruggeven op apparaat wordt vereist.

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
1. Blader naar dit pad [/etc/contentSync/templates/dps-we-onbeperkt-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article)om de gedeelde voorbeeldbronnen weer te geven.

   U kunt alle eigenschappen bekijken die voor het creëren van uw gedeelde middelen zoals aangetoond in het hieronder cijfer worden vereist:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikelen moeten worden geüpload of geëxporteerd naar AEM Mobile On-Demand Services wanneer de inhoud van artikelen verandert.

