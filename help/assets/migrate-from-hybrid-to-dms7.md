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

---


# Info over de overgang van dynamische media-hybride naar dynamische media-Scene7 {#about-migrating}

Dynamic Media-Hybrid is een oudere versie van Dynamic Media-integratie met Adobe Experience Manager. De Hybride-versie werd voor het eerst geïntroduceerd in AEM (Adobe Experience Manager) 6.1. Hoewel Adobe de hybride modus blijft ondersteunen, heeft dit niet de voorkeursmodus (Dynamische media-Scene7 heeft de voorkeur). Het biedt ook geen ondersteuning voor nieuwe functies, zoals SmartCrop en panoramische afbeeldingen. Terwijl Dynamic Media-Scene7 dat doet.

De extra belangrijkste verschillen tussen Dynamische media-Hybride en Dynamische media-Scene7 omvatten het volgende:

* Structuur van URL&#39;s.
* Ingestie van video&#39;s.
* Het maken en opslaan van afbeeldingsuitvoeringen.
* Configuratie en referenties van de cloud (provisioning).

Er zijn twee opties beschikbaar wanneer u van Dynamische media-Hybride naar Dynamische media-Scene7 beweegt. De eerste optie is eenvoudig voorziening een nieuw geval van Dynamische media-Scene7 op AEM. De tweede optie moet uw bestaande instantie van Dynamische media-Hybride aan Dynamische media-Scene7 migreren. Met deze optie geeft u een overzicht van het tabelformulier onder de stappen en overwegingen die u tijdens het verplaatsen wilt uitvoeren.

>[!IMPORTANT]
>
>Adobe raadt u aan om een dynamische media-hybride implementatie niet naar Dynamic Media-Scene7 te migreren voor live productieinstanties.

## Optie 1 - Levering een nieuw geval van Dynamische media-Scene7 op AEM {#provision-new-dms7}

Overweeg eenvoudig om vers met een nieuwe, provisioned instantie van Dynamische Media-Scene7 op de Manager van de Ervaring van Adobe te beginnen. Naast het opnemen en verwerken van middelen via Dynamic Media Cloud Service wordt een Adobe-controle van het gebruik van middelen, workflows en componenten ten zeerste aanbevolen. In veel gevallen kunnen aangepaste componenten en workflows worden vervangen door nieuwere, out-of-the-box functies.

## Optie 2 - Het migreren van uw bestaande instantie van Dynamische media-Hybride aan Dynamische Media-Scene7 {#process-for-migrating}

| Stap | Taak | Overwegingen |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author-instantie. | U zou uw bestaand geval van Dynamische media-Hybride Auteur voor reservedoeleinden moeten handhaven tot de resterende stappen in dit migratieproces met succes worden voltooid. |
| 2 | De gekloonde instantie van de Auteur van het begin op Dynamische media-Scene7 wijze. |  |
| 3 | In de Diensten van de Wolk van de Manager van de Ervaring van Adobe, vorm Dynamische Media met Dynamische media-Scene7 geloofsbrieven. | Adobe moet de Dynamische Media-Scene7 levering goedkeuren. U zult gelijktijdige Dynamische MediaM-Hybride en Dynamische Media-Scene7 milieu&#39;s hebben die voor een beperkte tijd zullen worden gesteund. |
| 4 | Maak zo nodig een migratiebundel om elementen in te voeren.<br>Verwijder de lokale PTIFF-bestanden die tijdens de eerste opname zijn gemaakt in Dynamic Media-Hybrid. | Als alle elementen momenteel beschikbaar zijn in de instantie Dynamic Media-Hybrid, bevat een kloon van die elementen al deze elementen. Daarom is geen bundel nodig. |
| 5 | Werk de workflow voor het bijwerken van middelen uit om elementen te synchroniseren met Dynamic Media Cloud Service. | Adobe raadt u aan de updateworkflow batchgewijs uit te voeren, zodat u de gegevens kunt comprimeren. |
| 6 | Viewer-, afbeeldings- en videovoorinstellingen migreren. |  |
| 7 | Doorloop de elementen waarnaar wordt verwezen in het beheer van webinhoud en werk de bijbehorende URL&#39;s bij. |  |
| 8 | Migreer om het even welke douanewerkschema&#39;s om de nieuwe Dynamische media-Scene7 wijze (handupdates) te steunen. |  |
| 9 | Verifieer uw upload en configuratie van het Beheer van de Inhoud van het Web. |  |
| 10 | Na controle, krijg een goedkeuring om Dynamische media-Hybride Auteur onbruikbaar te maken (handhaaf als daling terug). |  |
| 11 | Verwijder de Dynamic Media-Hybrid Author-instantie na ongeveer een maand succesvol gebruik van Dynamic Media-Scene7. |  |
