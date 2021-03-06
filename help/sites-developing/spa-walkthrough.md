---
title: SPA Inleiding en Analyse
seo-title: SPA Introduction and Walkthrough
description: Dit artikel introduceert de concepten SPA en loopt door het gebruiken van een basis SPA toepassing voor creatie, die toont hoe het op het onderliggende AEM SPA Redacteur betrekking heeft.
seo-description: This article introduces the concepts of a SPA and walks through using a basic SPA application for authoring, showing how it relates to the underlying AEM SPA Editor.
uuid: 4b0a9e53-3892-4d60-8bd3-7ff740d2f137
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
discoiquuid: 0478afcb-b029-4ce6-b3e6-cee4bb5408ce
docset: aem65
exl-id: 95990112-2afc-420a-a7c7-9613f40d4c4a
source-git-commit: d1b4cf87291f7e4a0670a21feca1ebf8dd5e0b5e
workflow-type: tm+mt
source-wordcount: '1968'
ht-degree: 0%

---

# SPA Inleiding en Analyse{#spa-introduction-and-walkthrough}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van dergelijke frameworks.

De SPA Editor biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel doorloopt het gebruiken van een basis SPA toepassing voor creatie en toont hoe het op het onderliggende AEM SPA Redacteur betrekking heeft.

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA kader gebaseerde cliënt-zijteruggeven (b.v. Reageren of Angular) vereisen.

## Inleiding {#introduction}

### Artikel {#article-objective}

Dit artikel introduceert de basisconcepten van SPA alvorens de lezer door een analyse van de SPA redacteur door een eenvoudige SPA toepassing te gebruiken te leiden om basisinhoud het uitgeven aan te tonen. Vervolgens duikt het neer in de constructie van de pagina en hoe de SPA toepassing zich verhoudt tot en communiceert met de AEM SPA Editor.

Het doel van deze inleiding en analyse is aan een AEM ontwikkelaar te tonen waarom SPA relevant zijn, hoe zij over het algemeen werken, hoe een SPA door de AEM Redacteur wordt behandeld SPA, en hoe het van een standaard AEM toepassing verschillend is.

De analyse is gebaseerd op standaard AEM functionaliteit en de steekproefWij.Retail app van het Dagboek. Aan de volgende eisen moet worden voldaan:

* [AEM versie 6.4 met servicepack 2 of hoger](/help/release-notes/release-notes.md)
* [Installeer de steekproefWij.Retail app van het Dagboek beschikbaar op GitHub hier.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)

>[!CAUTION]
>
>In dit document worden de [We.Retail Journal-app](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) uitsluitend voor demonstratiedoeleinden. Het mag niet worden gebruikt voor projectwerkzaamheden.
>
>Elk AEM project moet [Projectarchetype AEM](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html), die SPA projecten met React of Angular steunt en hefboomwerkingen de SPA SDK.

### Wat is een SPA? {#what-is-a-spa}

Een toepassing van één pagina (SPA) verschilt van een conventionele pagina in zoverre dat het cliënt-kant wordt teruggegeven en hoofdzakelijk JavaScript-gedreven is, die op Ajax vraag baseert om gegevens te laden en dynamisch de pagina bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die asynchroon worden geladen, afhankelijk van gebruikersinteractie met de pagina.

Hierdoor is het minder nodig pagina&#39;s te vernieuwen en wordt de gebruiker een ervaring geboden die naadloos, snel is en meer lijkt op een native app-ervaring.

Met de AEM SPA Editor kunnen front-end ontwikkelaars SPA maken die in een AEM site kunnen worden geïntegreerd, zodat de auteurs van de inhoud de SPA inhoud net zo gemakkelijk kunnen bewerken als elke andere AEM.

### Waarom een SPA? {#why-a-spa}

Door sneller, vloeiend en meer als een native toepassing te zijn, wordt een SPA een zeer aantrekkelijke ervaring, niet alleen voor de bezoeker van de webpagina, maar ook voor marketers en ontwikkelaars vanwege de aard van de manier waarop SPA werkt.

![screen_shot_2018-08-20at135550](assets/screen_shot_2018-08-20at135550.png)

**Bezoekers**

* Bezoekers willen native ervaringen als ze met inhoud werken.
* Er zijn duidelijke gegevens dat hoe sneller een pagina, hoe waarschijnlijker een conversie zal plaatsvinden.

**Marketers**

* Marketers willen rijke, native ervaringen bieden om bezoekers te dwingen om zich volledig met inhoud bezig te houden.
* Personalisatie kan deze ervaringen nog aantrekkelijker maken.

**Ontwikkelaars**

* Ontwikkelaars willen een duidelijke scheiding tussen inhoud en presentatie.
* Schone scheiding maakt het systeem uitbreidbaarder en maakt een onafhankelijke ontwikkeling aan de voorzijde mogelijk.

### Hoe werkt een SPA? {#how-does-a-spa-work}

Het primaire idee achter een SPA is dat de vraag en de afhankelijkheid van een server worden verminderd om vertragingen te minimaliseren die door servervraag worden veroorzaakt zodat de SPA de ontvankelijkheid van een inheemse toepassing benadert.

In een traditionele, opeenvolgende webpagina worden alleen de gegevens geladen die nodig zijn voor de directe pagina. Dit betekent dat wanneer de bezoeker naar een andere pagina gaat, de server om de extra bronnen wordt gevraagd. Aanvullende aanroepen kunnen nodig zijn omdat de bezoeker werkt met elementen op de pagina. Deze veelvoudige vraag kan een gevoel van vertraging of vertraging geven aangezien de pagina met de verzoeken van de bezoeker moet inhalen.

![screen_shot_2018-08-20at140449](assets/screen_shot_2018-08-20at140449.png)

Voor een vloeiendere ervaring, die nadert wat een bezoeker van mobiele, native apps verwacht, laadt een SPA alle noodzakelijke gegevens voor de bezoeker bij de eerste lading. Hoewel dit een beetje langer kan duren, elimineert het dan de behoefte aan extra servervraag.

Door het pagina-element op de client weer te geven, reageert het pagina-element sneller en zijn de interactie met de pagina door de bezoeker direct. Eventuele aanvullende gegevens worden asynchroon aangeroepen om de snelheid van de pagina te maximaliseren.

>[!NOTE]
>
>Raadpleeg het artikel voor technische details over hoe SPA werken in AEM [Aan de slag met SPA in AEM](/help/sites-developing/spa-getting-started-react.md).
>
>Raadpleeg het artikel voor meer informatie over het ontwerp, de architectuur en de technische workflow van de SPA Editor [Overzicht SPA Editor](/help/sites-developing/spa-overview.md).

## Ervaring voor het bewerken van inhoud met SPA {#content-editing-experience-with-spa}

Wanneer een SPA is gemaakt om de AEM SPA Editor te gebruiken, merkt de auteur van de inhoud op dat er geen verschil is bij het bewerken en maken van inhoud. Er is algemene AEM beschikbaar en er zijn geen wijzigingen in de workflow van de auteur vereist.

>[!NOTE]
>
>De analyse is gebaseerd op standaard AEM functionaliteit en de steekproefWij.Retail app van het Dagboek. Aan de volgende eisen moet worden voldaan:
>
>* [AEM versie 6.4 met servicepack 2](/help/release-notes/release-notes.md)
>* [Installeer de steekproefWij.Retail app van het Dagboek beschikbaar op GitHub hier.](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal)

>


1. Bewerk de app We.Retail Journal in AEM.

   `https://localhost:4502/editor.html/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at142533](assets/screen_shot_2018-06-07at142533.png)

1. Selecteer een koptekstcomponent. Een werkbalk ziet er net zo uit als een andere component. Selecteren **Bewerken**.

   ![screen_shot_2018-06-07at142937](assets/screen_shot_2018-06-07at142937.png)

1. Bewerk de inhoud als normaal binnen AEM en houd er rekening mee dat de wijzigingen zich blijven voordoen.

   ![screen_shot_2018-06-07at143419](assets/screen_shot_2018-06-07at143419.png)

   >[!NOTE]
   >Zie de [Overzicht SPA Editor](spa-overview.md#requirements-limitations) voor meer informatie over de bestaande teksteditor en SPA.

1. Met de middelenbrowser kunt u een nieuwe afbeelding naar een afbeeldingscomponent slepen en neerzetten.

   ![screen_shot_2018-06-07at143530](assets/screen_shot_2018-06-07at143530.png)

1. De wijziging wordt doorgevoerd.

   ![screen_shot_2018-06-07at143732](assets/screen_shot_2018-06-07at143732.png)

Extra ontwerpgereedschappen, zoals het slepen en neerzetten van aanvullende componenten op de pagina, het opnieuw rangschikken van componenten en het wijzigen van de layout, worden ondersteund zoals in elke andere toepassing dan SPA.

>[!NOTE]
>
>De SPA Editor wijzigt het DOM van de toepassing niet. De SPA zelf is verantwoordelijk voor het DOM.
>
>Ga naar de volgende sectie van dit artikel om te zien hoe dit werkt [Apps en de AEM SPA Editor SPA](/help/sites-developing/spa-walkthrough.md#spa-apps-and-the-aem-spa-editor).

## Apps en de AEM SPA Editor SPA {#spa-apps-and-the-aem-spa-editor}

Door te ervaren hoe een SPA zich gedraagt voor de eindgebruiker en vervolgens de SPA pagina te inspecteren, kunt u beter begrijpen hoe een SAP-app werkt met de SPA Editor in AEM.

### Een SPA toepassing gebruiken {#using-an-spa-application}

1. Laad de toepassing van het Dagboek Wij.Retail of op de publicatieserver of gebruikend de optie **Weergeven als gepubliceerd** van de **Pagina-informatie** in de pagina-editor.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-08at102650](assets/screen_shot_2018-06-08at102650.png)

   Neem nota van de paginastructuur met inbegrip van navigatie aan kindpagina&#39;s, weer widget, en artikelen.

1. Navigeer naar een onderliggende pagina met behulp van het menu en controleer of de pagina direct wordt geladen zonder dat een pagina moet worden vernieuwd.

   ![screen_shot_2018-06-08at102815](assets/screen_shot_2018-06-08at102815.png)

1. Open de ingebouwde ontwikkelaarsgereedschappen van uw browser en controleer de netwerkactiviteit terwijl u door de onderliggende pagina&#39;s navigeert.

   ![screen_shot_2018-06-08at103922](assets/screen_shot_2018-06-08at103922.png)

   Er is erg weinig verkeer wanneer u van pagina naar pagina gaat in de app. De pagina wordt niet opnieuw geladen en alleen de nieuwe afbeeldingen worden aangevraagd.

   De SPA beheert de inhoud en het verpletteren volledig op de cliëntkant.

Dus als de pagina niet opnieuw wordt geladen wanneer u door de onderliggende pagina&#39;s navigeert, hoe wordt deze geladen?

de volgende afdeling, [Een SPA laden](/help/sites-developing/spa-walkthrough.md#loading-an-spa-application), gaat dieper in de mechanica van het laden van de SPA en hoe de inhoud synchroon en asynchroon kan worden geladen.

### Een SPA laden {#loading-an-spa-application}

1. Als niet reeds geladen, laad de toepassing van het Dagboek Wij.Retail of op de publicatieserver of gebruikend de optie **Weergeven als gepubliceerd** van de **Pagina-informatie** in de pagina-editor.

   `/content/we-retail-journal/react.html`

   ![screen_shot_2018-06-07at144736](assets/screen_shot_2018-06-07at144736.png)

1. Gebruik het ingebouwde gereedschap van uw browser om de bron van de pagina weer te geven.
1. De inhoud van de bron is uiterst beperkt.

   ```
   <!DOCTYPE HTML>
   <html lang="en-CH">
       <head>
       <meta charset="UTF-8">
       <title>We.Retail Journal</title>
   
       <meta name="template" content="we-retail-react-template"/>
   
   <link rel="stylesheet" href="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.css" type="text/css">
   
   <link rel="stylesheet" href="/libs/wcm/foundation/components/page/responsive.css" type="text/css">
   
   </head>
       <body class="page basicpage">
   
   <div id="page"></div>
   
   <script type="text/javascript" src="/etc.clientlibs/we-retail-journal/react/clientlibs/we-retail-journal-react.js"></script>
   
       </body>
   </html>
   ```

   De pagina heeft geen inhoud in de hoofdtekst. Het bestaat hoofdzakelijk uit stijlbladen en een vraag aan een manuscript van de Reactie, `we-retail-journal-react.js`.

   Dit React-script is het belangrijkste stuurprogramma voor deze toepassing en is verantwoordelijk voor het renderen van alle inhoud.

1. Gebruik de ingebouwde gereedschappen van uw browser om de pagina te inspecteren. Zie de inhoud van de DOM volledig geladen.

   ![screen_shot_2018-06-07at151848](assets/screen_shot_2018-06-07at151848.png)

1. Ga naar het tabblad Netwerk in de Inspecteur en laad de pagina opnieuw.

   Afbeeldingsverzoeken negeren. De primaire bronnen die voor de pagina worden geladen, zijn de pagina zelf, CSS, het React JavaScript, de afhankelijkheden en JSON-gegevens voor de pagina.

   ![screen_shot_2018-06-07at152155](assets/screen_shot_2018-06-07at152155.png)

1. Laad de `react.model.json` op een nieuw tabblad.

   `/content/we-retail-journal/react.model.json`

   ![screen_shot_2018-06-07at152636](assets/screen_shot_2018-06-07at152636.png)

   De AEM SPA Editor gebruikt [AEM Content Services](/help/assets/content-fragments/content-fragments.md) om de volledige inhoud van de pagina als JSON-model te leveren.

   Door specifieke interfaces uit te voeren, verstrekken de Modellen van het Sling de informatie noodzakelijk aan de SPA. De levering van de JSON-gegevens wordt naar beneden gedelegeerd aan elke component (van pagina, alinea, component, enz.).

   Elke component kiest wat het blootstelt en hoe het (server-kant met HTML of cliënt-kant met React) wordt teruggegeven. Natuurlijk richt dit artikel zich op client-side rendering met React.

1. Het model kan pagina&#39;s ook groeperen zodat ze synchroon worden geladen, waardoor het aantal pagina&#39;s dat opnieuw moet worden geladen, afneemt.

   In het voorbeeld van We.Retail Journal: `home`, `blog`, en `aboutus` De pagina&#39;s worden synchroon geladen, aangezien bezoekers doorgaans al deze pagina&#39;s bezoeken. De `weather` De pagina wordt asynchroon geladen, omdat bezoekers deze minder waarschijnlijk bezoeken.

   Dit gedrag is niet verplicht en is volledig definieerbaar.

   ![screen_shot_2018-06-07at153945](assets/screen_shot_2018-06-07at153945.png)

1. Als u dit verschil in gedrag wilt weergeven, laadt u de pagina opnieuw en wist u de netwerkactiviteit van de inspecteur. Navigeer naar de blog en over de webpagina&#39;s in het paginamenu en controleer of er geen netwerkactiviteiten zijn gerapporteerd.

   Navigeer naar de weerpagina en controleer of de `weather.model.json` wordt asynchroon aangeroepen.

   ![screen_shot_2018-06-07at155738](assets/screen_shot_2018-06-07at155738.png)

### Interactie met de SPA Editor {#interaction-with-the-spa-editor}

Met behulp van de voorbeeldtoepassing We.Retail Journal is het duidelijk hoe de app zich gedraagt en wordt geladen wanneer deze wordt gepubliceerd, waarbij gebruik wordt gemaakt van contentservices voor het leveren van JSON-inhoud en het asynchroon laden van bronnen.

Voor de auteur van de inhoud is het maken van inhoud met een SPA-editor bovendien naadloos in AEM.

In de volgende sectie zullen wij het contract onderzoeken dat de SPARedacteur toestaat om componenten binnen de SPA met AEM componenten te verbinden en deze naadloze het uitgeven ervaring te bereiken.

1. Laad de toepassing van het Dagboek Wij.Retail in de redacteur en schakelaar aan **Voorvertoning** in.

   `https://localhost:4502/editor.html/content/we-retail-journal/react.html`

1. Controleer de inhoud van de pagina met de ingebouwde ontwikkelaarsgereedschappen van uw browser. Selecteer met het selectiegereedschap een bewerkbare component op de pagina en bekijk de details van het element.

   De component heeft een nieuw gegevenskenmerk `data-cq-data-path`.

   ![screen_shot_2018-06-08at095124](assets/screen_shot_2018-06-08at095124.png)

   Bijvoorbeeld

   `data-cq-data-path="root/responsivegrid/paragraph_1`

   Met deze paden kunnen het contextconfiguratieobject van elke component worden opgehaald en gekoppeld.

   Dit is het enige prijsverhogingsattribuut dat voor de redacteur wordt vereist om dit als editable component binnen de SPA te erkennen. Op basis van dit kenmerk bepaalt de SPA Editor welke bewerkbare configuratie aan de component is gekoppeld, zodat het juiste frame, de juiste werkbalk, enzovoort. is geladen.

   Bepaalde specifieke klassenamen worden ook toegevoegd voor het markeren van plaatsaanduidingen en voor het slepen en neerzetten van elementen.

   >[!NOTE]
   >
   >Dit is een gedragswijziging van gerenderde pagina&#39;s op de server in AEM, waar een `cq` element ingevoegd voor elke bewerkbare component.
   >
   >
   >Deze benadering in SPA verwijdert de behoefte om douaneelementen te injecteren, die slechts een extra gegevensattribuut baseren, die de prijsverhoging voor de frontend ontwikkelaar eenvoudiger maken.

## Volgende stappen {#next-steps}

Nu u de SPA het uitgeven ervaring in AEM begrijpt en hoe een SPA op de SPA Redacteur betrekking heeft, neem een diepgaande duik in het begrijpen van hoe een SPA wordt gebouwd.

* [Aan de slag met SPA in AEM](/help/sites-developing/spa-getting-started-react.md) toont hoe een basis SPA wordt gebouwd om met de SPARedacteur in AEM te werken
* [Overzicht SPA Editor](/help/sites-developing/spa-overview.md) gaat dieper in het communicatie model tussen AEM en de SPA.
* [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md) beschrijft hoe te om front-end ontwikkelaars in dienst te nemen om een SPA voor AEM te ontwikkelen evenals hoe SPA met AEM architectuur in wisselwerking staan.
