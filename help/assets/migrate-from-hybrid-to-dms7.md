---
title: Migreren van Dynamic Media - Hybride modus naar Dynamic Media - S7 modus
description: Leer hoe u uw exemplaar van Dynamic Media - hybride modus naar de modus Dynamic Media - S7 kunt migreren
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: Business Practitioner, Administrator
exl-id: 07f0803c-4ec4-4745-8214-63370e9d0282
feature: Scene7 mode,Hybrid mode
translation-type: tm+mt
source-git-commit: c9aec973faf4caef741961d92a6f258646aeddb7
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 2%

---

# Informatie over het overstappen van Dynamic Media-Hybrid naar Dynamic Media-Scene7 {#about-migrating}

Dynamic Media-Hybrid is een oudere versie van de integratie van Dynamic Media met Adobe Experience Manager. De Hybride versie werd voor het eerst ingevoerd in AEM (Adobe Experience Manager) 6.1. Hoewel Adobe de hybride modus blijft ondersteunen, heeft deze modus geen voorkeur (Dynamic Media-Scene7 is de voorkeursmodus). Het biedt ook geen ondersteuning voor nieuwe functies, zoals SmartCrop en panoramische afbeeldingen. En Dynamic Media-Scene7 wel.

De volgende belangrijke verschillen tussen Dynamic Media-Hybrid en Dynamic Media-Scene7 zijn van belang:

* Structuur van URL&#39;s.
* Ingestie van video&#39;s.
* Het maken en opslaan van afbeeldingsuitvoeringen.
* Configuratie en referenties van de cloud (provisioning).

Er zijn twee opties beschikbaar wanneer u van Dynamic Media-Hybrid naar Dynamic Media-Scene7 gaat. De eerste optie is simpelweg een nieuw geval van Dynamic Media-Scene7 op AEM. De tweede mogelijkheid is om uw bestaande exemplaar van Dynamic Media-Hybrid te migreren naar Dynamic Media-Scene7. Met deze optie geeft u een overzicht van het tabelformulier onder de stappen en overwegingen die u tijdens het verplaatsen wilt uitvoeren.

>[!IMPORTANT]
>
>Adobe raadt u aan geen Dynamic Media-Hybride implementatie naar Dynamic Media-Scene7 te migreren op exemplaren van de live productie.

## Optie 1 - Een nieuw exemplaar van Dynamic Media-Scene7 aanbieden op AEM {#provision-new-dms7}

Overweeg eenvoudig vers te beginnen met een nieuw, voorzien exemplaar van Dynamic Media-Scene7 op Adobe Experience Manager. Naast het opnemen en verwerken van middelen via Dynamic Media Cloud Service, wordt een Adobe-controle van het gebruik van bedrijfsmiddelen, workflows en componenten ten zeerste aanbevolen. In veel gevallen kunnen aangepaste componenten en workflows worden vervangen door nieuwere, out-of-the-box functies.

## Optie 2 - Uw bestaande exemplaar van Dynamic Media-Hybrid migreren naar Dynamic Media-Scene7 {#process-for-migrating}

| Stap | Taak | Overwegingen |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author instance. | U moet uw bestaande exemplaar van Dynamic Media-Hybrid Author voor reservedoeleinden handhaven tot de resterende stappen in dit migratieproces met succes worden voltooid. |
| 2 | Een gekloonde instantie Auteur starten in de modus Dynamic Media-Scene7. |  |
| 3 | Configureer in Adobe Experience Manager Cloud Services Dynamic Media met Dynamic Media-Scene7-referenties. | Adobe moet de Dynamic Media-Scene7-voorziening goedkeuren. U hebt naast Dynamic MediaM-Hybrid ook Dynamic Media-Scene7 omgevingen die gedurende een beperkte periode worden ondersteund. |
| 4 | Maak zo nodig een migratiebundel om elementen in te voeren.<br>Verwijder de lokale PTIFF-bestanden die zijn gemaakt tijdens de eerste opname in Dynamic Media-Hybrid. | Als alle elementen momenteel beschikbaar zijn in uw Dynamic Media-Hybrid-instantie, bevat een kloon van die al deze elementen. Daarom is geen bundel nodig. |
| 5 | Workflow voor het bijwerken van elementen uitvoeren om elementen te synchroniseren met Dynamic Media Cloud Service. | Adobe raadt u aan de updateworkflow batchgewijs uit te voeren, zodat de bestanden kunnen worden gecomprimeerd. |
| 6 | Viewer-, afbeeldings- en videovoorinstellingen migreren. |  |
| 7 | Doorloop de elementen waarnaar wordt verwezen in het beheer van webinhoud en werk de bijbehorende URL&#39;s bij. |  |
| 8 | Migreer aangepaste workflows ter ondersteuning van de nieuwe Dynamic Media-Scene7-modus (handmatige updates). |  |
| 9 | Verifieer uw upload en configuratie van het Beheer van de Inhoud van het Web. |  |
| 10 | Na verificatie kunt u een goedkeuring verkrijgen om Dynamic Media-Hybride auteur uit te schakelen (als een terugval behouden). |  |
| 11 | Verwijder de Dynamic Media-Hybrid Author-instantie na ongeveer een maand succesvol gebruik van Dynamic Media-Scene7. |  |
