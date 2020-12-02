---
title: Migreren van dynamische media - hybride modus naar dynamische media - S7-modus
description: Leer hoe u uw instantie van Dynamische media - hybride modus naar Dynamische media - S7-modus migreert
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: f466193a259d9e8869d7f79eafda1be20869e4af
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 2%

---


# Info over de overgang van Dynamic Media-Hybrid naar Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid is een oudere versie van Dynamic Media-integratie met Adobe Experience Manager. De Hybride versie werd voor het eerst ingevoerd in AEM (Adobe Experience Manager) 6.1. Hoewel Adobe de hybride modus blijft ondersteunen, heeft deze de voorkeur (Dynamic Media-Scene7 is de voorkeursmodus). Het biedt ook geen ondersteuning voor nieuwe functies, zoals SmartCrop en panoramische afbeeldingen. Dynamic Media-Scene7 doet dat.

De extra belangrijkste verschillen tussen Dynamische media-Hybride en Dynamische media-Scene7 omvatten het volgende:

* Structuur van URL&#39;s.
* Ingestie van video&#39;s.
* Het maken en opslaan van afbeeldingsuitvoeringen.
* Configuratie en referenties van de cloud (provisioning).

Er zijn twee opties beschikbaar wanneer u van Dynamic Media-Hybrid naar Dynamic Media-Scene7 gaat. De eerste optie is eenvoudig een nieuw geval van Dynamische Media-Scene7 op AEM te verstrekken. De tweede optie is het migreren van uw bestaande instantie van Dynamic Media-Hybrid naar Dynamic Media-Scene7. Met deze optie geeft u een overzicht van het tabelformulier onder de stappen en overwegingen die u tijdens het verplaatsen wilt uitvoeren.

>[!IMPORTANT]
>
>Adobe raadt u aan om een Dynamic Media-Hybrid-implementatie niet te migreren naar Dynamic Media-Scene7 op liveproductieexemplaren.

## Optie 1 - Een nieuwe instantie van Dynamic Media-Scene7 op AEM {#provision-new-dms7} aanbieden

Overweeg eenvoudig vers te beginnen met een nieuwe, provisioned instantie van Dynamic Media-Scene7 op Adobe Experience Manager. Naast het opnemen en verwerken van middelen via Dynamic Media Cloud Service wordt een Adobe-controle van het gebruik van middelen, workflows en componenten ten zeerste aanbevolen. In veel gevallen kunnen aangepaste componenten en workflows worden vervangen door nieuwere, out-of-the-box functies.

## Optie 2 - Uw bestaande instantie van Dynamic Media-Hybrid migreren naar Dynamic Media-Scene7 {#process-for-migrating}

| Stap | Taak | Overwegingen |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author-instantie. | U zou uw bestaand geval van Dynamische media-Hybride Auteur voor reservedoeleinden moeten handhaven tot de resterende stappen in dit migratieproces met succes worden voltooid. |
| 2 | Een gekloonde instantie Auteur starten in de modus Dynamisch media-Scene7. |  |
| 3 | Configureer in Adobe Experience Manager-Cloud Services Dynamic Media met Dynamic Media-Scene7-referenties. | Adobe moet de Dynamic Media-Scene7-voorziening goedkeuren. U hebt naast Dynamic MediaM-Hybrid ook dynamische Media-Scene7 omgevingen die gedurende een beperkte periode worden ondersteund. |
| 4 | Maak zo nodig een migratiebundel om elementen in te voeren.<br>Verwijder de lokale PTIFF-bestanden die tijdens de eerste opname zijn gemaakt in Dynamic Media-Hybrid. | Als alle elementen momenteel beschikbaar zijn in de instantie Dynamic Media-Hybrid, bevat een kloon van die elementen al deze elementen. Daarom is geen bundel nodig. |
| 5 | Werk de workflow voor het bijwerken van elementen uit om elementen te synchroniseren met Dynamic Media Cloud Service. | Adobe raadt u aan de updateworkflow batchgewijs uit te voeren, zodat de bestanden kunnen worden gecomprimeerd. |
| 6 | Viewer-, afbeeldings- en videovoorinstellingen migreren. |  |
| 7 | Doorloop de elementen waarnaar wordt verwezen in het beheer van webinhoud en werk de bijbehorende URL&#39;s bij. |  |
| 8 | Migreer aangepaste workflows ter ondersteuning van de nieuwe Dynamic Media-Scene7-modus (handmatige updates). |  |
| 9 | Verifieer uw upload en configuratie van het Beheer van de Inhoud van het Web. |  |
| 10 | Na controle, krijg een goedkeuring om Dynamische media-Hybride Auteur onbruikbaar te maken (handhaaf als daling terug). |  |
| 11 | Verwijder de Dynamic Media-Hybrid Author-instantie na ongeveer een maand succesvol gebruik van Dynamic Media-Scene7. |  |
