---
title: Forms Service
seo-title: Forms Service
description: In het artikel worden de Forms-service beschreven en worden de taken beschreven die u met Forms kunt uitvoeren.
seo-description: In het artikel worden de Forms-service beschreven en worden de taken beschreven die u met Forms kunt uitvoeren.
uuid: 3258d3c2-8755-4815-8c97-b2cfb9a9dfd4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: a9695d10-43ec-40eb-942f-7720abaa0973
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Forms Service {#forms-service}

## Overzicht {#overview}

Met de service Forms kunt u interactieve toepassingen maken voor het vastleggen van gegevens die formulieren valideren, verwerken, transformeren en leveren die doorgaans in Designer worden gemaakt. De service Forms geeft elk formulierontwerp dat u ontwikkelt, weer als PDF-document.

Met Forms Service kunnen organisaties ook hun intelligente processen voor het vastleggen van gegevens uitbreiden met behulp van elektronische formulieren als Adobe PDF&#39;s. U kunt de service ook gebruiken voor het importeren en exporteren van gegevens van en naar bestaande PDF-formulieren.

Gebruik de service Formulieren om het volgende te doen:

* PDF-formulieren renderen op basis van sjabloon- en XML-gegevens.
* Integratie van formuliergegevens inschakelen om gegevens te importeren in en te extraheren uit PDF-formulieren.
* Formulieren weergeven op basis van fragmenten.

## PDF-formulieren maken {#creating-pdf-forms-nbsp}

Met de Form-service kunt u PDF-formulieren maken voor het vastleggen van gegevens. Doorgaans begint u met een AEM Forms Designer-sjabloon. Met de bewerking `renderPDFForm` (koppeling naar JavaDoc) van de service Forms kunt u deze sjabloon converteren naar een PDF-formulier.

De eerste parameter van de `renderPDFForm` bewerking is de naam van het sjabloonbestand (bijvoorbeeld `ExpenseClaim.xdp`). U kunt het sjabloonbestand opslaan in een lokaal bestandssysteem, in een CRX-opslagplaats of op een HTTP- of FTP-locatie. U kunt de locatie van het sjabloonbestand opgeven door de hoofdmap van de inhoud in te stellen in de `PDFFormRenderOptions` parameter van de `renderPDFForm` bewerking. Zie Javadoc voor meer informatie over andere opties die u voor de `PDFFormRenderOptions` parameter kunt opgeven.

De `renderPDFForm` bewerking kan ook XML-gegevens accepteren. De XML-gegevens worden met de sjabloon samengevoegd wanneer u een PDF-formulier maakt, zodat het gegenereerde PDF-formulier de opgegeven gegevens bevat. De tweede parameter voor de `renderPDFForm` bewerking kan een object Document (Javadoc) accepteren dat XML-gegevens bevat.

## Gegevens uit PDF-formulieren extraheren {#extracting-data-from-pdf-forms-nbsp}

Gebruik de bewerking `exportData` (Javadoc) van de service Forms om gegevens-XML uit een PDF-formulier te extraheren. Deze bewerking accepteert een document als eerste parameter. U kunt de gegevens exporteren als een XDP-document of als een XML-bestand. Als u de gegevens als een XML-bestand exporteert, worden de XDP-envelop door de geëxporteerde gegevens verwijderd en wordt een onbewerkt XML-bestand geretourneerd. U kunt deze rangschikking opgeven met de tweede parameter.

## Gegevens importeren in PDF-formulieren {#importing-data-into-pdf-forms}

Met Forms Service kunt u ook een PDF-formulier samenvoegen dat is gemaakt met AEM Forms Designer of de `renderPDFForm` bewerking met XML-gegevens. Met de bewerking `importData` (Javadoc) van Forms worden het PDF-formulier en de XML-gegevens geaccepteerd en wordt een PDF-formulier met XML-gegevens geretourneerd.

## Formulieren weergeven op basis van fragmenten {#rendering-forms-based-on-fragments}

Forms-service kan formulieren genereren op basis van fragmenten die u maakt met AEM Forms Designer. Een fragment is een herbruikbaar onderdeel van een formulier. Het wordt opgeslagen als een afzonderlijk XDP-bestand dat in meerdere formulierontwerpen kan worden ingevoegd. Een fragment kan bijvoorbeeld een adresblok of juridische tekst bevatten.

Met fragmenten kunt u het maken en onderhouden van grote aantallen formulieren vereenvoudigen en versnellen. Voeg bij het maken van een formulier een verwijzing in naar het vereiste fragment dat het fragment in het formulier moet weergeven. De fragmentverwijzing bevat een subformulier dat naar het fysieke XDP-bestand wijst.

Hieronder ziet u de voordelen van het gebruik van fragmenten:

* **Inhoud opnieuw gebruiken**: U kunt inhoud opnieuw gebruiken in meerdere formulierontwerpen. Maak een fragment als u delen van dezelfde inhoud snel opnieuw wilt gebruiken in meerdere formulieren. Het kopiëren of opnieuw maken van de inhoud duurt langer. Fragmenten voor onderdelen die vaak voorkomen in een formulierontwerp, zorgen ook voor een consistente inhoud en weergave in alle formulieren die ernaar verwijzen.
* **Algemene updates**: U kunt globale wijzigingen in meerdere formulieren slechts eenmaal aanbrengen in een bestand. U kunt de inhoud, scriptobjecten, gegevensbindingen, lay-out of stijlen in een fragment wijzigen. Alle XDP-formulieren die naar het fragment verwijzen, weerspiegelen de wijzigingen.
* **Gedeeld formulier maken**: U kunt het maken van formulieren delen met verschillende bronnen. Formulierontwikkelaars met ervaring in het schrijven van scripts of andere geavanceerde functies van AEM Forms Designer kunnen fragmenten ontwikkelen en delen die gebruikmaken van scripts en dynamische eigenschappen. Formulierontwerpers kunnen de fragmenten gebruiken om formulieren te ontwerpen. Bovendien kunnen ze de fragmenten gebruiken om ervoor te zorgen dat alle onderdelen van een formulier een consistente weergave en functionaliteit hebben in meerdere formulieren.

