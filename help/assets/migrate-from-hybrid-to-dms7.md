---
title: Migreren van Dynamic Media - Hybride modus naar Dynamic Media - S7 modus
description: Leer hoe u uw exemplaar van Dynamic Media - hybride modus naar de modus Dynamic Media - S7 kunt migreren
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
feature: Scene7 Mode,Hybrid Mode
exl-id: 07f0803c-4ec4-4745-8214-63370e9d0282
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 2%

---

# Over de overgang van Dynamic Media-Hybrid naar Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid is een oudere versie van de integratie van Dynamic Media met Adobe Experience Manager. De Hybride versie werd voor het eerst geïntroduceerd in Adobe Experience Manager 6.1. Hoewel Adobe de Hybride modus blijft ondersteunen, heeft deze modus geen voorkeur. Dynamic Media-Scene7 is de voorkeursmodus. De hybride modus ondersteunt ook geen nieuwe functies, zoals Smart Crop en panoramische afbeeldingen, terwijl Dynamic Media-Scene7 deze ondersteunt.

De volgende belangrijke verschillen tussen Dynamic Media-Hybrid en Dynamic Media-Scene7 zijn van belang:

* Structuur van URL&#39;s.
* Ingestie van video&#39;s.
* Het maken en opslaan van afbeeldingsuitvoeringen.
* Configuratie en referenties van de cloud (provisioning).

Er zijn twee opties beschikbaar wanneer u van Dynamic Media-Hybrid naar Dynamic Media-Scene7 gaat. De eerste optie is simpelweg een nieuw geval van Dynamic Media-Scene7 op Experience Manager aan te bieden. De tweede mogelijkheid is om uw bestaande exemplaar van Dynamic Media-Hybrid te migreren naar Dynamic Media-Scene7. Met deze optie geeft u een overzicht van het tabelformulier onder de stappen en overwegingen die u tijdens het verplaatsen wilt uitvoeren.

>[!IMPORTANT]
>
>De Adobe raadt u aan om een Dynamic Media-Hybride implementatie niet naar Dynamic Media-Scene7 te migreren op exemplaren van de levende productie.

## Optie 1 - Een nieuw geval van Dynamic Media-Scene7 op Experience Manager aanbieden {#provision-new-dms7}

Overweeg eenvoudig vers te beginnen met een nieuw, voorzien exemplaar van Dynamic Media-Scene7 op Adobe Experience Manager. Naast het opnemen en verwerken van middelen via Dynamic Media Cloud Service wordt een Adobe-controle van het gebruik van bedrijfsmiddelen, workflows en componenten ten zeerste aanbevolen. Vaak kunt u aangepaste componenten en workflows vervangen door gebruik te maken van nieuwere, out-of-the-box functies.

## Optie 2 - Uw bestaande exemplaar van Dynamic Media-Hybrid migreren naar Dynamic Media-Scene7 {#process-for-migrating}

| Stap | Taak | Overwegingen |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author instance. | Bewaar uw bestaande exemplaar van Dynamic Media-Hybrid Author voor terugvaldoeleinden tot de resterende stappen in dit migratieproces met succes zijn voltooid. |
| 2 | Een gekloonde instantie Auteur starten in de modus Dynamic Media-Scene7. |  |
| 3 | Configureer in Adobe Experience Manager-Cloud Servicen Dynamic Media met Dynamic Media-Scene7-referenties. | Adobe moet de levering Dynamic Media-Scene7 goedkeuren. Als dusdanig, hebt u gelijktijdig Dynamic MediaM-Hybrid en Dynamic Media-Scene7 milieu&#39;s die door Adobe, maar slechts voor een beperkte tijd worden gesteund. |
| 4 | Maak een migratiebundel, zodat u elementen naar wens kunt invoeren.<br> Schrap lokale PTIFFs die tijdens aanvankelijke opname in Dynamic Media-Hybrid werden gecreeerd. | Als alle elementen momenteel beschikbaar zijn in uw Dynamic Media-Hybrid-instantie, bevat een kloon van die al deze elementen. Daarom is geen bundel nodig. |
| 5 | Werk de workflow voor het bijwerken van elementen uit, zodat u elementen kunt synchroniseren met Dynamic Media Cloud Service. | Adobe raadt u aan de updateworkflow batchgewijs uit te voeren, zodat u de gegevens kunt comprimeren. |
| 6 | Viewer-, afbeeldings- en videovoorinstellingen migreren. |  |
| 7 | Doorloop de elementen waarnaar wordt verwezen in het beheer van webinhoud en werk de bijbehorende URL&#39;s bij. |  |
| 8 | Migreer aangepaste workflows die u de nieuwe Dynamic Media-Scene7-modus (handmatige updates) wilt ondersteunen. |  |
| 9 | Verifieer uw upload en configuratie van het Beheer van de Inhoud van het Web. |  |
| 10 | Na verificatie kunt u goedkeuring verkrijgen om Dynamic Media-Hybride auteur uit te schakelen (als fallback onderhouden). |  |
| 11 | Verwijder de Dynamic Media-Hybrid Author-instantie na ongeveer een maand succesvol gebruik van Dynamic Media-Scene7. |  |
