---
title: Artikel-exportconfiguratie maken
seo-title: Creating Article Export Configuration
description: Volg deze pagina voor meer informatie over het exporteren van inhoud van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
seo-description: Follow this page to learn about exporting content from Adobe Experience Manager (AEM) for upload to AEM Mobile.
uuid: 089bc15b-669e-4623-bdbb-fd9abf46e098
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: bc681589-5d46-44cd-888d-b0722a2fd006
exl-id: 5295f383-3b46-4456-9177-65de68e39a85
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Artikel-exportconfiguratie maken{#creating-article-export-configuration}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>**Vereiste**:
>
>Alvorens over het creëren van en het wijzigen van gedeelde middelen te leren, zie [Inhoud synchroniseren](/help/mobile/mobile-ondemand-contentsync.md) de basisbeginselen te begrijpen.

AEM Mobile-gebruikers gebruiken Content Sync om live-inhoud te exporteren naar statische inhoud voor gebruik in Mobile Apps. Deze export vindt plaats wanneer inhoud vanuit AEM Mobile wordt geüpload naar Mobile On-Demand Services.

De eigenschap ***dps-exportTemplate*** in de bovenstaande tabel wordt het pad naar de exportconfiguraties van de app gedefinieerd. Stel deze eigenschap in om gedeelde bronnen te maken en te wijzigen.

In de volgende bronnen wordt beschreven hoe u inhoud uit Adobe Experience Manager (AEM) exporteert om te uploaden naar AEM Mobile.

Artikelen hebben inhoud die moet worden geëxporteerd en geüpload. Een deel van deze inhoud kan worden gedeeld tussen artikelen.

Gebruiken [ContentSync](/help/mobile/mobile-ondemand-contentsync.md) om de inhoud samen te verzamelen en een ***Gedeelde bronnen*** pakket.

De ContentSync-configuratie gevonden op **&lt;dps-exporttemplate>/dps-article>** moet worden geconfigureerd om alle inhoud te exporteren die een artikel vereist voor statische rendering van eigenschappen op een apparaat.

>[!CAUTION]
>
>U kunt de onderstaande stappen uitvoeren om voorbeelden van gedeelde bronnen weer te geven, alleen als u beschikt over:
>
>* de voorbeeldinhoud geïnstalleerd
>* uitvoeren, AEM
>* geen gevormde douanecontext of een verschillende haven
>


Zie de onderstaande stappen voor een voorbeeld van een gedeelde bron:

1. Open CRXDE Lite op uw AEM.
1. Bladeren naar dit pad [/etc/contentSync/templates/dps-we-onbeperkt-app/dps-article](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article)om de gedeelde voorbeeldbronnen weer te geven.

   U kunt alle eigenschappen bekijken die voor het creëren van uw gedeelde middelen zoals aangetoond in het hieronder cijfer worden vereist:

   ![chlimage_1-134](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikelen moeten worden geüpload of geëxporteerd naar AEM Mobile On-demand Services wanneer de inhoud van een artikel verandert.
