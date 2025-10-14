---
title: Artikel-exportconfiguratie maken
description: Volg deze pagina voor meer informatie over het exporteren van inhoud van Adobe Experience Manager (AEM) voor uploaden naar AEM Mobile.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 5295f383-3b46-4456-9177-65de68e39a85
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Artikel-exportconfiguratie maken{#creating-article-export-configuration}

{{ue-over-mobile}}

>[!CAUTION]
>
>**Vereiste**:
>
>Voorafgaand aan leren over het creëren van en het wijzigen van gedeelde middelen, zie [&#x200B; Synchronisatie van de Inhoud &#x200B;](/help/mobile/mobile-ondemand-contentsync.md) om de basisconcepten te begrijpen.

AEM Mobile-gebruikers gebruiken Content Sync om live-inhoud te exporteren naar statische inhoud voor gebruik in Mobile Apps. Deze export vindt plaats wanneer inhoud vanuit AEM Mobile wordt geüpload naar Mobile On-Demand Services.

Het bezit ***dps-exportTemplate*** die in lijst hierboven wordt vermeld, bepaalt de weg aan de de uitvoervormen van app. Stel deze eigenschap in om gedeelde bronnen te maken en te wijzigen.

In de volgende bronnen wordt beschreven hoe u inhoud uit Adobe Experience Manager (AEM) exporteert om te uploaden naar AEM Mobile.

Artikelen hebben inhoud die moet worden geëxporteerd en geüpload. Een deel van deze inhoud kan worden gedeeld tussen artikelen.

Het gebruik [&#x200B; ContentSync &#x200B;](/help/mobile/mobile-ondemand-contentsync.md) om de inhoud samen te verzamelen en a ***Gedeelde het pakket van Middelen*** tot stand te brengen.

De configuratie ContentSync die bij **wordt gevonden &lt;dps-exportTemplate>/dps-article>** zou moeten worden gevormd om alle inhoud en artikel uit te voeren die voor bezit statische teruggeven op apparaat wordt vereist.

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
1. Blader naar dit pad [&#x200B; /etc/contentSync/templates/dps-we-limited-app/dps-article &#x200B;](http://localhost:4502/crx/de/index.jsp#/etc/contentsync/templates/dps-we-unlimited-app/dps-article) om de gedeelde voorbeeldbronnen weer te geven.

   U kunt alle eigenschappen bekijken die voor het creëren van uw gedeelde middelen zoals aangetoond in het hieronder cijfer worden vereist:

   ![&#x200B; chlimage_1-134 &#x200B;](assets/chlimage_1-134.png)

>[!NOTE]
>
>Artikelen moeten worden geüpload of geëxporteerd naar AEM Mobile On-demand Services wanneer de inhoud van een artikel verandert.
