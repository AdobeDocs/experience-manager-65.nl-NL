---
title: Aanbevolen procedures voor HTML5-formulieren
description: Stem uw op XFA gebaseerde HTML5 Forms af voor de beste prestaties.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
content-type: reference
docset: aem65
feature: HTML5 Forms
exl-id: 62ff6306-9989-43b0-abaf-b0a811f0a6a4
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---

# Aanbevolen procedures voor HTML5-formulieren{#best-practices-for-html-forms}

## Overzicht {#overview}

AEM Forms heeft een component met de naam HTML5-formulieren. Hiermee kunt u bestaande XFA-PDF forms (XDP-bestanden) renderen in de HTML5-indeling. Dit document bevat richtlijnen en aanbevelingen om de laadtijd te verminderen en de prestaties van HTML5-formulieren op mobiele apparaten te verbeteren.

De meeste mobiele apparaten hebben een beperkte verwerkingscapaciteit en geheugencapaciteit. Het helpt bij het verbeteren van de stand-bytijd van mobiele apparaten. De webbrowsers die op een mobiel apparaat worden uitgevoerd, hebben toegang tot beperkte bronnen (beperkt geheugen en verwerkingsmogelijkheden). Nadat de limiet is bereikt, wordt het browsergedrag traag. Dit document bevat aanbevelingen om de grootte van een HTML5-formulier te controleren. Een kleiner formulier schendt de geheugen- en verwerkingsvermogenslimieten van een apparaat niet en zorgt voor een vloeiende ervaring.

Hoewel de aanbevelingen die in dit artikel worden besproken gericht zijn op HTML5-formulieren, zijn deze ook van toepassing op XFA-PDF forms. Deze beste praktijken dragen collectief bij tot de algemene prestaties van HTML5 vormen. Het vereist een zorgvuldige planning om efficiënte en productieve vormen te ontwikkelen. Laten we beginnen:

## Knooppunten zijn valuta van HTML5-vormen, ze verstandig uitgeven {#nodes-are-currency-of-html-forms-spend-them-wisely}

Over het algemeen heeft een XFA-formulier meerdere elementen. Bijvoorbeeld tabel, tekstveld en afbeeldingen. Elk element heeft verscheidene eigenschappen om het gedrag en de verschijning van het element te controleren. Wanneer een XFA-formulier wordt weergegeven in de HTML5-indeling, worden alle XFA-elementen en de bijbehorende eigenschappen geconverteerd naar Model- of HTML DOM-knooppunten. Deze knopen voegen aan de grootte en de ingewikkeldheid van DOM toe. De HTML5-vorm traag renderen.

Het is voor de browsers gemakkelijker om een leaner DOM terug te geven. U kunt dus de volgende optimalisaties uitvoeren op een XFA-formulier om het aantal knooppunten te verminderen. Maak daarom een leaanse DOM-structuur:

* Gebruik de eigenschap caption om een label aan een veld toe te voegen. Gebruik geen apart tekstelement om een label toe te voegen. Het helpt bij het afvallen van extra gewicht, wat leidt tot prestatiewinst. Het helpt ook om layoutkwesties te vermijden.
* Beperk het aantal tekstelementen op een formulier tot een absoluut minimum. Teken elementen zijn handig voor het verbeteren van de leesbaarheid en het uiterlijk, maar beschikken niet over opslagmogelijkheden voor informatie. U wordt aangeraden meerdere Tekstelementen tekenen samen te voegen tot één tekstelement Tekenen. Laat geen steen ongedraaid om een formulier leaner te maken.

## Lite-formulieren presteren beter, houd de bronnen gecomprimeerd {#lite-forms-perform-better-keep-the-resources-compressed}

Een HTML5-formulier kan meerdere externe bronnen bevatten, zoals afbeeldings-, JavaScript- en CSS-bestanden. Telkens wanneer een browser een formulier aanvraagt, worden de externe bronnen via het netwerk verzonden. De tijd die nodig is om over het netwerk te reizen, is evenredig aan de grootte van de bestanden.

Daarom is het verkleinen van de omvang van de externe middelen en het gebruik van alleen de absoluut noodzakelijke middelen de voorkeursmethode om de prestaties van de formulieren te verbeteren. U kunt de volgende optimalisaties uitvoeren op een XFA-formulier om de grootte van externe bronnen van een formulier te beperken:

* Gebruiken [gecomprimeerde afbeeldingen](/help/assets/best-practices-for-optimizing-the-quality-of-your-images.md). Het vermindert de netwerkactiviteit en de hoeveelheid geheugen die nodig is om een formulier te genereren. Daarom neemt de laadtijd van het formulier aanzienlijk af.
* Gebruik de minify optie in AEM Configuration Manager (Day CQ HTML Library Manager) om JavaScript- en CSS-bestanden te comprimeren. Zie voor meer informatie [OSGi-configuratie-instellingen](/help/sites-deploying/osgi-configuration-settings.md).
* Webcompressie inschakelen. Hiermee verkleint u de grootte van de aanvragen en reacties die afkomstig zijn van een formulier. Zie voor meer informatie [Prestaties afstemmen op AEM Forms Server](https://helpx.adobe.com/aem-forms/6-3/performance-tuning-aem-forms.html).

## Houd de interesse levend, toon alleen de vereiste velden  {#keep-the-interest-alive-show-only-required-fields}

Een HTML5-formulier kan in honderden pagina&#39;s worden weergegeven. Een formulier met een groot aantal velden wordt traag geladen in de browser. U kunt de volgende optimalisaties uitvoeren op een XFA-formulier om de formulieren te optimaliseren met een groot aantal velden en pagina&#39;s:

* Evalueer het splitsen van de grote formulieren in meerdere formulieren. U kunt ook een formulierset gebruiken om alle kleinere formulieren te groeperen en weer te geven als één eenheid. Een formulierset laadt alleen de vereiste formulieren. Bovendien kunt u in een formulierset veelvoorkomende velden in verschillende formulieren configureren om gegevensbindingen te delen. Met gegevensbindingen kunnen gebruikers de algemene gegevens slechts eenmaal invullen. De gegevens worden automatisch ingevuld in volgende formulieren, wat tot aanzienlijke prestatieverbeteringen leidt. Zie voor meer informatie over formuliersets [Formulierset in AEM formulieren](https://helpx.adobe.com/aem-forms/6-3/formset-in-aem-forms.html).
* Overweeg secties te splitsen en elke sectie naar een andere pagina te verplaatsen. In HTML5-formulieren wordt elke pagina dynamisch geladen wanneer een pagina wordt opgevraagd. Alleen de geschoven pagina (de pagina die wordt weergegeven en de pagina&#39;s die eraan voorafgaan) wordt in het geheugen opgeslagen. De rest van de pagina&#39;s wordt op aanvraag geladen. Als u dus een sectie op een eigen pagina splitst en verplaatst, wordt de tijd die nodig is om een formulier te laden, verkort. U kunt de eerste pagina van het formulier ook gebruiken als bestemmingspagina. Het is gelijkaardig aan de inhoudstafel (TOC) van een boek. Een openingspagina van het formulier bevat alleen koppelingen naar de andere secties van het formulier. Hiermee wordt de laadtijd van de eerste pagina van het formulier aanzienlijk verkort en wordt de gebruikerservaring verbeterd.
* Voorwaardelijke secties standaard verborgen houden. Deze secties alleen zichtbaar maken als aan een bepaalde voorwaarde is voldaan. Hierdoor wordt de DOM tot een minimum beperkt. U kunt navigatie met tabs ook gebruiken om slechts één sectie tegelijk weer te geven.

## Minder is meer, verlaag het aantal pagina&#39;s {#less-is-more-reduce-the-number-of-pages}

HTML5-formulieren kunnen gegevensgestuurde velden (tabellen en subformulieren) bevatten. Met deze velden wordt de grootte van het formulier tijdens runtime vergroot. Een gegevensgestuurde tabel in een HTML5-formulier kan bijvoorbeeld duizenden rijen beslaan. Dergelijke tabellen kunnen de layout en prestaties nadelig beïnvloeden. Met de onderstaande optimalisaties kunt u de laadtijd van HTML5-formulieren met gegevensgestuurde velden verminderen:

* Gebruik XFA-scripting om gepagineerde navigatie tot stand te brengen om gegeven-gedreven gebieden (lijsten en subformulieren) te tonen. Bij gepagineerde navigatie worden alleen specifieke gegevens weergegeven op een pagina. Hierdoor wordt de verfbewerking in de browser beperkt tot de velden die tegelijkertijd worden weergegeven en is het gemakkelijker om in een formulier te navigeren. Bovendien zijn gebruikers op mobiele apparaten alleen geïnteresseerd in een subset gegevens. Het helpt u een geweldige gebruikerservaring te bieden en verkort de tijd die nodig is om de vereiste gegevens te laden. Je krijgt twee oplossingen voor de prijs van één.  Let er ook op dat gepagineerde navigatie niet beschikbaar is buiten het vak. U kunt XFA-scripts gebruiken om gepagineerde navigatie te ontwikkelen.

* Evalueer het samenvoegen van meerdere alleen-lezen kolommen in één kolom. Hiermee vermindert u het geheugen dat nodig is om het formulier weer te geven. Vermijd ook het weergeven van de kolommen waarvoor geen invoer van gebruikers nodig is.
* Evalueren door de gegevensgestuurde vorm in een [formulierset](https://helpx.adobe.com/aem-forms/6-3/formset-in-aem-forms.html), indien de bovenstaande suggesties niet veel verbeteringen opleveren. Als een tabel bijvoorbeeld meer dan 1000 rijen bevat, verplaatst u elke 100 rijen naar een ander formulier. Hiermee kunt u de laadtijd en prestaties van de formulieren verbeteren.  Een formulierset genereert een geconsolideerde verzendings-XML voor alle formulieren. Als u gegevens van elk formulier wilt onderscheiden, moet u verschillende basisgegevens gebruiken. Zie voor meer informatie [Formulierset in AEM Forms](https://helpx.adobe.com/aem-forms/6-3/formset-in-aem-forms.html).

## Macht van twee voor Document of Record (DOR) {#power-of-two-for-document-of-record-dor}

Een XFA-formulier kan een groot aantal secties bevatten die alleen zijn bestemd voor Document of Record (DOR). Om het aantal knooppunten te verminderen en de prestaties van een dergelijk formulier te verbeteren, kunt u verschillende exemplaren van het formulier bijhouden: een kopie om het formulier in te vullen en een andere kopie om het Document of Record te genereren op de server. In de kopie voor het invullen van het XFA-formulier worden alleen velden weergegeven die vereist zijn om gegevens vast te leggen. In het formulier Document of Record XFA genereren houdt u velden die alleen vereist zijn in de afgedrukte uitvoer van het formulier. Voordat u de voorgestelde aanpak kiest, moet u de prestatiewinst en de overhead voor het onderhoud evalueren.

## Aanbevolen leesbewerkingen  {#recommended-reads}

Met Adobe Experience Manager (AEM)-formulieren kunt u complexe transacties transformeren in eenvoudige, prachtige digitale ervaringen. Het vereist echter gezamenlijke inspanningen om efficiënte en productieve vormen te ontwikkelen. Naast HTML5 Forms zijn er enkele aanbevolen formuleringen voor algemene AEM aanbevolen procedures:

* [Aanbevolen werkwijzen voor implementeren en onderhouden van AEM](/help/sites-deploying/best-practices.md)
* [Aanbevolen procedures voor het ontwerpen van inhoud](/help/sites-authoring/best-practices.md)
* [Aanbevolen procedures voor het beheren van AEM](/help/sites-administering/administer-best-practices.md)
* [Aanbevolen werkwijzen voor het ontwikkelen van oplossingen](/help/sites-developing/best-practices.md)
* [Aanbevolen werkwijzen voor het werken met adaptieve formulieren](/help/forms/using/adaptive-forms-best-practices.md)
* [AEM Forms-server sluit fonts niet in op een dynamisch PDF-formulier](https://helpx.adobe.com/aem-forms/kb/aem-forms-server-does-not-embed-fonts-to-dynamic-pdf-form.html)

## Snelle referentiekaart {#quick-reference-card}

U kunt de volgende kaart afdrukken (klik op de kaart om een versie met hoge resolutie te downloaden) en deze voor een snelle referentie op uw bureau houden:
[![HTML5 Forms Best practices Snelle referentiekaart](do-not-localize/best-practices_reference_card.png)](assets/html5_forms_best_practices_reference_card.pdf)
