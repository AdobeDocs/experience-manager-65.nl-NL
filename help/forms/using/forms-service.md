---
title: Forms Service
seo-title: Forms Service
description: In het artikel worden de Forms-service beschreven en worden de taken beschreven die u met Forms kunt uitvoeren.
seo-description: The article describes Forms service and the form-related tasks you can perform using Forms service.
uuid: 3258d3c2-8755-4815-8c97-b2cfb9a9dfd4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: a9695d10-43ec-40eb-942f-7720abaa0973
exl-id: bd1216e4-2248-484b-a3c1-c209da4ff94f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 5%

---

# Forms Service {#forms-service}

## Overzicht {#overview}

Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die doorgaans in Designer worden gemaakt. De Forms-service geeft elk formulierontwerp dat u ontwikkelt weer als PDF-documenten.

De dienst van Forms laat organisaties ook toe om hun intelligente processen van de gegevensvangst uit te breiden door elektronische vormen als Adobe PDF in te voeren. U kunt de service ook gebruiken voor het importeren en exporteren van gegevens van en naar bestaande PDF forms.

Gebruik de Forms-service om het volgende te doen:

* Render PDF forms op basis van sjabloon- en XML-gegevens.
* Integratie van formuliergegevens inschakelen om gegevens te importeren in en te extraheren uit PDF forms.
* Formulieren weergeven op basis van fragmenten.

## PDF forms maken  {#creating-pdf-forms-nbsp}

Met de Form-service kunt u PDF forms maken voor het vastleggen van gegevens. Doorgaans begint u met een AEM Forms Designer-sjabloon. Gebruik de `renderPDFForm` (link naar Javadoc) van de Forms-service om deze sjabloon om te zetten in een PDF-formulier.

De eerste parameter van de `renderPDFForm` bewerking is de naam van het sjabloonbestand (bijvoorbeeld `ExpenseClaim.xdp`). U kunt het sjabloonbestand opslaan in een lokaal bestandssysteem, in een CRX-opslagplaats of op een HTTP- of FTP-locatie. U kunt de locatie van het sjabloonbestand opgeven door de hoofdmap van de inhoud in te stellen in het dialoogvenster `PDFFormRenderOptions` parameter van de `renderPDFForm` bewerking. Zie Javadoc voor meer informatie over andere opties die u kunt opgeven voor de `PDFFormRenderOptions` parameter.

De `renderPDFForm` bewerking kan ook XML-gegevens accepteren. De XML-gegevens worden met de sjabloon samengevoegd wanneer u een PDF-formulier maakt, zodat het gegenereerde PDF formulier de opgegeven gegevens bevat. De tweede parameter voor de `renderPDFForm` De bewerking kan een Document-object (Javadoc) accepteren dat XML-gegevens bevat.

## Gegevens extraheren uit PDF forms  {#extracting-data-from-pdf-forms-nbsp}

Gebruik de `exportData` (Javadoc) van de Forms-service om gegevens-XML uit een PDF-formulier te extraheren. Deze bewerking accepteert een document als eerste parameter. U kunt de gegevens exporteren als een XDP-document of als een XML-bestand. Als u de gegevens als een XML-bestand exporteert, worden de XDP-envelop door de geëxporteerde gegevens verwijderd en wordt een onbewerkt XML-bestand geretourneerd. U kunt deze rangschikking opgeven met de tweede parameter.

## Gegevens importeren in PDF forms {#importing-data-into-pdf-forms}

Met de Forms-service kunt u ook een PDF-formulier samenvoegen dat is gemaakt met AEM Forms Designer of met de `renderPDFForm` bewerking met XML-gegevens. De `importData` (Javadoc) de verrichting van de dienst van Forms keurt de PDF vorm en de gegevens van XML goed en keert een PDF vorm met gegevens XML terug.

## Formulieren weergeven op basis van fragmenten {#rendering-forms-based-on-fragments}

Forms-service kan formulieren genereren op basis van fragmenten die u maakt met AEM Forms Designer. Een fragment is een herbruikbaar onderdeel van een formulier. Het wordt opgeslagen als een afzonderlijk XDP-bestand dat in meerdere formulierontwerpen kan worden ingevoegd. Een fragment kan bijvoorbeeld een adresblok of juridische tekst bevatten.

Met fragmenten kunt u het maken en onderhouden van grote aantallen formulieren vereenvoudigen en versnellen. Voeg bij het maken van een formulier een verwijzing in naar het vereiste fragment dat het fragment in het formulier moet weergeven. De fragmentverwijzing bevat een subformulier dat naar het fysieke XDP-bestand wijst.

Hieronder ziet u de voordelen van het gebruik van fragmenten:

* **Inhoud opnieuw gebruiken**: U kunt inhoud opnieuw gebruiken in meerdere formulierontwerpen. Maak een fragment als u delen van dezelfde inhoud snel opnieuw wilt gebruiken in meerdere formulieren. Het kopiëren of opnieuw maken van de inhoud duurt langer. Fragmenten voor onderdelen die vaak voorkomen in een formulierontwerp, zorgen ook voor een consistente inhoud en weergave in alle formulieren die ernaar verwijzen.
* **Algemene updates**: U kunt globale wijzigingen in meerdere formulieren slechts eenmaal aanbrengen in een bestand. U kunt de inhoud, scriptobjecten, gegevensbindingen, lay-out of stijlen in een fragment wijzigen. Alle XDP-formulieren die naar het fragment verwijzen, weerspiegelen de wijzigingen.
* **Gedeeld formulier maken**: U kunt het maken van formulieren delen met verschillende bronnen. Formulierontwikkelaars met ervaring in het schrijven van scripts of andere geavanceerde functies van AEM Forms Designer kunnen fragmenten ontwikkelen en delen die gebruikmaken van scripts en dynamische eigenschappen. Formulierontwerpers kunnen de fragmenten gebruiken om formulieren te ontwerpen. Bovendien kunnen ze de fragmenten gebruiken om ervoor te zorgen dat alle onderdelen van een formulier een consistente weergave en functionaliteit hebben in meerdere formulieren.
