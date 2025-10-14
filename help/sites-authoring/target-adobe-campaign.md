---
title: Uw Adobe Campaign als doel instellen
description: U kunt gerichte ervaringen voor Adobe Campaign maken nadat u segmentatie hebt ingesteld.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: fc6fccba-41c5-4c13-aac0-b4ef67767abe
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization,Integration
role: User,Admin,Architect,Developer
source-git-commit: 389d5fa8de320a7237fc8290992a33743b15db99
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Je Adobe Campaign als doelgroep instellen{#targeting-your-adobe-campaign}

Als u uw Adobe Campaign-nieuwsbrief als doel wilt instellen, moet u eerst segmentatie instellen. Deze is alleen beschikbaar in de klassieke gebruikersinterface (voor clientcontext). Daarna kunt u gerichte ervaringen voor Adobe Campaign creëren. Beide worden beschreven in deze sectie.

## Segmentatie instellen in AEM {#setting-up-segmentation-in-aem}

Als u segmentatie wilt instellen, moet u de klassieke UI gebruiken om de segmenten in te stellen. De overige stappen kunnen worden uitgevoerd in de standaardinterface.

De opstellingssegmentatie omvat het creëren van segmenten, een merk, een campagne, en ervaringen.

>[!NOTE]
>
>Segment-id moet worden toegewezen aan de segment aan de Adobe Campaign-zijde.

### Segmenten maken {#creating-segments}

Segmenten maken:

1. Open de [&#x200B; segmentation console &#x200B;](http://localhost:4502/miscadmin#/etc/segmentation) bij **&lt;host>:&lt;port>/miscadmin#/etc/segmentation**.
1. Creeer een pagina en ga een titel in - bijvoorbeeld, **AC Segmenten** - en selecteer het **Segment (Adobe Campaign)** malplaatje.
1. Selecteer de gemaakte pagina in de structuurweergave aan de linkerkant.
1. Creeer een segment, bijvoorbeeld, richtend mannelijke gebruikers, door een pagina onder het segment te creëren u genoemd Mannelijk creeerde en het **Segment (Adobe Campaign)** malplaatje selecteert.
1. Open de gecreeerde segmentpagina en sleep identiteitskaart van het a **Segment** van sidekick op de pagina.
1. Dubbelklik het bezit, ga identiteitskaart die in dit geval vertegenwoordigt in, het mannelijke segment in Adobe Campaign - bijvoorbeeld, **MANNELIJKE** wordt bepaald - en klik **O.K.**. Het volgende bericht moet worden weergegeven: *`targetData.segmentCode == "MALE"`*
1. Herhaal de stappen voor een ander segment, bijvoorbeeld een segment dat zich richt op vrouwelijke gebruikers.

### Een merk maken {#creating-a-brand}

Een merk maken:

1. In **Plaatsen**, navigeer aan de **omslag van Campagnes** (bijvoorbeeld, in Wij.Retail).
1. Klik **creëren Pagina** en ga een titel voor de pagina in, bijvoorbeeld, Wij.Retail Merk en selecteer het **Merk** malplaatje.

### Een campagne maken {#creating-a-campaign}

Een campagne maken:

1. Open de **Merk** pagina u creeerde.
1. Klik **creëren Pagina** en ga een titel voor uw pagina in, bijvoorbeeld, wij.Retail Campagne, en selecteer het **malplaatje van de Campagne** en klik **creëren**.

### Ervaringen maken {#creating-experiences}

Zo creëert u ervaringen voor segmenten:

1. Open de **pagina van de Campagne** u creeerde.
1. Creeer ervaringen voor uw segmenten door **te klikken creëren Pagina** en een titel voor uw pagina in te gaan, bijvoorbeeld, Male aangezien u een ervaring voor het Mannelijke segment creeert, en selecteer het **3&rbrace; malplaatje van de Ervaring &lbrace;.**
1. Open de pagina voor het maken van ervaring.
1. Klik **uitgeven**, dan onder Segmenten klikt **Punt** toevoegen.
1. Ga de weg aan het mannelijke segment, bijvoorbeeld, **/etc/segmentation/ac-segments/man** in en klik **O.K.**. Het volgende bericht zou moeten verschijnen: *de Ervaring wordt gericht op: Mannelijk*
1. Herhaal de vorige stappen om een ervaring voor alle segmenten, bijvoorbeeld, het vrouwelijke doel tot stand te brengen.
