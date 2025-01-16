---
title: SPA Inleiding en Analyse
description: Dit artikel introduceert de concepten van een SPA en loopt door het gebruiken van een basis SPA toepassing voor creatie, die toont hoe het op het onderliggende AEM SPA Redacteur betrekking heeft.
topic-tags: spa
content-type: reference
exl-id: 95990112-2afc-420a-a7c7-9613f40d4c4a
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
source-git-commit: 6d961456e0e1f7a26121da9be493308a62c53e04
workflow-type: tm+mt
source-wordcount: '1925'
ht-degree: 0%

---


# SPA Inleiding en Analyse {#spa-introduction-and-walkthrough}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van dergelijke frameworks.

De SPA Editor biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel doorloopt het gebruiken van een basis SPA toepassing voor creatie en toont hoe het op het onderliggende AEM SPA Redacteur betrekking heeft.

{{ue-over-spa}}

## Inleiding {#introduction}

### Artikel {#article-objective}

Dit artikel introduceert de basisconcepten van SPA alvorens de lezer door een analyse van de SPA redacteur door een eenvoudige SPA toepassing te gebruiken te leiden om basisinhoud het uitgeven aan te tonen. Vervolgens duikt het neer in de constructie van de pagina en hoe de SPA toepassing zich verhoudt tot en communiceert met de AEM SPA Editor.

Het doel van deze inleiding en analyse is aan een AEM ontwikkelaar te tonen waarom SPA relevant zijn, hoe zij over het algemeen werken, hoe een SPA door de AEM Redacteur wordt behandeld SPA, en hoe het van een standaard AEM toepassing verschillend is.

## Vereisten {#requirements}

De analyse is gebaseerd op standaard AEM functionaliteit en de steekproefWKND SPA Project app. Om samen met deze analyse te volgen, moet u het volgende beschikbaar hebben.

* [AEM versie 6.5.4 of hoger](/help/release-notes/release-notes.md)
   * U moet beheerdersrechten voor het systeem hebben.
* [ de steekproefWKND SPA Project beschikbaar op GitHub ](https://github.com/adobe/aem-guides-wknd-spa)
   * Download de [ recentste versie van React app.](https://github.com/adobe/aem-guides-wknd-spa/releases) De naam van de URL is vergelijkbaar met die van `wknd-spa-react.all.classic-X.Y.Z-SNAPSHOT.zip` .
   * Download de [ recentste steekproefbeelden ](https://github.com/adobe/aem-guides-wknd-spa/releases) voor app. Deze krijgt een naam die lijkt op `wknd-spa-sample-images-X.Y.Z.zip` .
   * [ het pakketmanager van het Gebruik ](/help/sites-administering/package-manager.md) om de pakketten te installeren aangezien u een ander pakket in AEM.
   * Voor deze analyse hoeft de app niet te worden geïnstalleerd met Maven.

>[!CAUTION]
>
>Dit document gebruikt [ app van het Project van de SPUL WKND ](https://github.com/adobe/aem-guides-wknd-spa) voor demonstratiedoeleinden slechts. Niet gebruiken voor projectwerk.
>
>Om het even welk AEM project zou het [ AEM Archetype van het Project moeten gebruiken, ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) dat SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

### Wat is een SPA? {#what-is-a-spa}

Een toepassing van één pagina (SPA) verschilt van een conventionele pagina in die zin dat deze op client wordt weergegeven en vooral door JavaScript wordt aangedreven, afhankelijk van Ajax-aanroepen om gegevens te laden en de pagina dynamisch bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die asynchroon worden geladen, afhankelijk van gebruikersinteractie met de pagina.

Hierdoor is het minder nodig pagina&#39;s te vernieuwen en wordt de gebruiker een ervaring geboden die naadloos, snel is en meer lijkt op een native app-ervaring.

Met de AEM SPA Editor kunnen front-end ontwikkelaars SPA maken die in een AEM site kunnen worden geïntegreerd, zodat de auteurs van de inhoud de SPA inhoud net zo gemakkelijk kunnen bewerken als elke andere AEM.

### Waarom een SPA? {#why-a-spa}

Door sneller, vloeiend en meer als een native toepassing te zijn, wordt een SPA een zeer aantrekkelijke ervaring, niet alleen voor de bezoeker van de webpagina, maar ook voor marketers en ontwikkelaars vanwege de aard van de manier waarop SPA werkt.

![ screen_shot_2018-08-20at135550 ](assets/screen_shot_2018-08-20at135550.png)

**Bezoekers**

* Bezoekers willen native ervaringen als ze met inhoud werken.
* Er zijn duidelijke gegevens dat hoe sneller een pagina, hoe waarschijnlijker een conversie zal plaatsvinden.

**Marketers**

* Marketers willen rijke, native ervaringen bieden om bezoekers te dwingen om zich volledig met inhoud bezig te houden.
* Personalization kan deze ervaringen nog aantrekkelijker maken.

**Ontwikkelaars**

* Ontwikkelaars willen een duidelijke scheiding tussen inhoud en presentatie.
* Schone scheiding maakt het systeem meer uitbreidbaar en maakt een onafhankelijke ontwikkeling aan de voorzijde mogelijk.

### Hoe werkt een SPA? {#how-does-a-spa-work}

Het primaire idee achter een SPA is dat de vraag en de afhankelijkheid van een server worden verminderd om vertragingen te minimaliseren die door servervraag worden veroorzaakt zodat de SPA de ontvankelijkheid van een inheemse toepassing benadert.

In een traditionele, opeenvolgende webpagina worden alleen de gegevens geladen die nodig zijn voor de directe pagina. Dit betekent dat wanneer de bezoeker naar een andere pagina gaat, de server om de extra bronnen wordt gevraagd. Aanvullende aanroepen kunnen nodig zijn omdat de bezoeker werkt met elementen op de pagina. Deze veelvoudige vraag kan een gevoel van vertraging of vertraging geven aangezien de pagina met de verzoeken van de bezoeker moet inhalen.

![ screen_shot_2018-08-20at140449 ](assets/screen_shot_2018-08-20at140449.png)

Voor een vloeiendere ervaring, die nadert wat een bezoeker van mobiele, native apps verwacht, laadt een SPA alle noodzakelijke gegevens voor de bezoeker bij de eerste lading. Hoewel dit een beetje langer kan duren, elimineert het dan de behoefte aan extra servervraag.

Door het pagina-element op de client weer te geven, reageert het pagina-element sneller en zijn de interactie met de pagina door de bezoeker direct. Eventuele aanvullende gegevens worden asynchroon aangeroepen om de snelheid van de pagina te maximaliseren.

>[!NOTE]
>
>Voor technische details op hoe SPA werk in AEM, zie het artikel [ Begonnen het worden met SPA in AEM ](/help/sites-developing/spa-getting-started-react.md).
>
>Voor een dichtere blik bij het ontwerp, de architectuur, en het technische werkschema van de SPA Redacteur, zie het artikel [ SPA het Overzicht van de Redacteur ](/help/sites-developing/spa-overview.md).

## Ervaring voor het bewerken van inhoud met SPA {#content-editing-experience-with-spa}

Wanneer een SPA is gemaakt om de AEM SPA Editor te gebruiken, merkt de auteur van de inhoud op dat er geen verschil is bij het bewerken en maken van inhoud. Er is algemene AEM beschikbaar en er zijn geen wijzigingen in de workflow van de auteur vereist.

1. Bewerk de WKND SPA Project-app in AEM.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

   ![ Stap 1 ](assets/spa-walkthrough-step-1.png)

1. Selecteer een koptekstcomponent. Een werkbalk ziet er net zo uit als een andere component. Selecteer **uitgeven**.

   ![ Stap 2 ](assets/spa-walkthrough-step-2.png)

1. Bewerk de inhoud als normaal binnen AEM. De wijzigingen blijven bestaan.

   ![ Stap 3 ](assets/spa-walkthrough-step-3.png)

   >[!NOTE]
   >
   >Zie het [ SPA Overzicht van de Redacteur ](spa-overview.md#requirements-limitations) voor verdere informatie over op zijn plaats tekstredacteur en SPA.

1. Met de Assets-browser kunt u een nieuwe afbeelding naar een afbeeldingscomponent slepen en neerzetten.

   ![ Stap 4 ](assets/spa-walkthrough-step-4.png)

1. De wijziging wordt doorgevoerd.

   ![ Stap 5 ](assets/spa-walkthrough-step-5.png)

Extra ontwerpgereedschappen, zoals het slepen en neerzetten van aanvullende componenten op de pagina, het opnieuw rangschikken van componenten en het wijzigen van de layout, worden ondersteund zoals in elke andere toepassing dan SPA.

>[!NOTE]
>
>De SPA Editor wijzigt het DOM van de toepassing niet. De SPA zelf is verantwoordelijk voor het DOM.
>
>Om te zien hoe dit werkt, ga op de volgende sectie van dit artikel [ SPA Apps en AEM SPA Redacteur ](#spa-apps-and-the-aem-spa-editor) verder.

## Apps en de AEM SPA Editor SPA {#spa-apps-and-the-aem-spa-editor}

Door te ervaren hoe een SPA zich gedraagt voor de eindgebruiker en vervolgens de SPA pagina te inspecteren, kunt u beter begrijpen hoe een SAP-app werkt met de SPA Editor in AEM.

### Een SPA toepassing gebruiken {#using-an-spa-application}

1. Laad de toepassing van het SPA van WKND of op publiceer server of gebruikend de optie **Mening zoals Gepubliceerd** van het **menu van de Informatie van de Pagina** in de paginaredacteur.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![ Stap 1 ](assets/spa-walkthrough-step-1-1.png)

   Neem nota van de paginastructuur met inbegrip van navigatie aan kindpagina&#39;s, weer widget, en artikelen.

1. Navigeer naar een onderliggende pagina met behulp van het menu en controleer of de pagina direct wordt geladen zonder dat een pagina moet worden vernieuwd.

   ![ Stap 2 ](assets/spa-walkthrough-step-1-2.png)

1. Open de ingebouwde ontwikkelaarsgereedschappen van uw browser en controleer de netwerkactiviteit terwijl u door de onderliggende pagina&#39;s navigeert.

   ![ Stap 3 ](assets/spa-walkthrough-step-1-3.png)

   Er is erg weinig verkeer wanneer u van pagina naar pagina gaat in de app. De pagina wordt niet opnieuw geladen en alleen de nieuwe afbeeldingen worden aangevraagd.

   De SPA beheert de inhoud en het verpletteren volledig op de cliëntkant.

Dus als de pagina niet opnieuw wordt geladen wanneer u door de onderliggende pagina&#39;s navigeert, hoe wordt deze geladen?

De volgende sectie, [ die een Toepassing van de SPA laadt, ](#loading-an-spa-application) graaft dieper in de mechanica van het laden van de SPA en hoe de inhoud synchroon en asynchroon kan worden geladen.

### Een SPA laden {#loading-an-spa-application}

1. Als niet reeds geladen, laad WKND SPA Project app of op publiceer server of gebruikend de optie **Mening zoals Gepubliceerd** van het **menu van de Informatie van de Pagina** in de paginaredacteur.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![ Stap 1 ](assets/spa-walkthrough-step-1-1.png)

1. Gebruik het ingebouwde gereedschap van uw browser om de bron van de pagina weer te geven.
1. De inhoud van de bron is uiterst beperkt.

   * De pagina heeft geen inhoud in de hoofdtekst. Het bestaat voornamelijk uit stijlpagina&#39;s en een aanroep naar verschillende scripts, zoals `clientlib-react.min.js` .
   * Deze scripts vormen de belangrijkste stuurprogramma&#39;s voor deze toepassing en zijn verantwoordelijk voor het renderen van alle inhoud.

1. Gebruik de ingebouwde gereedschappen van uw browser om de pagina te inspecteren. Zie de inhoud van de DOM volledig geladen.

   ![ Stap 4 ](assets/spa-walkthrough-step-1-4.png)

1. Schakelaar aan het **lusje van het Netwerk** van de ontwikkelaarshulpmiddelen en laad de pagina opnieuw.

   Afbeeldingsverzoeken worden genegeerd. De primaire bronnen die voor de pagina worden geladen, zijn de pagina zelf, CSS, de React JavaScript, de afhankelijkheden en JSON-gegevens voor de pagina.

   ![ Stap 5 ](assets/spa-walkthrough-step-1-5.png)

1. Laad de `react.model.json` op een nieuw tabblad.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.model.json`

   ![ Stap 6 ](assets/spa-walkthrough-step-1-6.png)

   De AEM SPARedacteur gebruikt [ AEM de Diensten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) om de volledige inhoud van de pagina als model te leveren JSON.

   Door specifieke interfaces uit te voeren, verstrekken de Modellen van het Sling de informatie noodzakelijk aan de SPA. De levering van de JSON-gegevens wordt omlaag gedelegeerd aan elke component (van pagina, alinea, component, enzovoort).

   Elke component kiest wat het blootstelt en hoe het (server-kant met HTML of cliënt-kant met React) wordt teruggegeven. Dit artikel richt zich op client-side rendering met React.

1. Het model kan pagina&#39;s ook groeperen zodat ze synchroon worden geladen, waardoor het aantal pagina&#39;s dat opnieuw moet worden geladen, afneemt.

   In het voorbeeld van de WKND SPA Project-app worden de pagina&#39;s `home` , `page-1` , `page-2` en `page-3` synchroon geladen, aangezien bezoekers doorgaans alle pagina&#39;s bezoeken.

   Dit gedrag is niet verplicht en is volledig definieerbaar.

   ![ Stap 7 ](assets/spa-walkthrough-step-1-7.png)

1. Om dit verschil in gedrag te bekijken, laad de pagina opnieuw en ontruim de netwerkactiviteit van de ontwikkelaarshulpmiddelen. Navigeer naar `page-1` in het paginamenu en controleer of de enige netwerkactiviteit een aanvraag is voor de afbeelding van `page-1` . `page-1` zelf hoeft niet te worden geladen.

   ![ Stap 8 ](assets/spa-walkthrough-step-1-8.png)

### Interactie met de SPA Editor {#interaction-with-the-spa-editor}

Met behulp van de voorbeeldtoepassing WKND SPA Project is het duidelijk hoe de app zich gedraagt en wordt geladen wanneer deze wordt gepubliceerd, met behulp van inhoudsservices voor het leveren van JSON-inhoud en het asynchroon laden van bronnen.

Voor de auteur van de inhoud is het maken van inhoud met een SPA-editor bovendien naadloos in AEM.

In de volgende sectie zullen wij het contract onderzoeken dat de SPARedacteur toestaat om componenten binnen de SPA met AEM componenten te verbinden en deze naadloze het uitgeven ervaring te bereiken.

1. Laad de toepassing van het SPA van WKND in de redacteur en schakelaar aan **wijze van de Voorproef**.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

1. Controleer de inhoud van de pagina met de ingebouwde ontwikkelaarsgereedschappen van uw browser. Selecteer met het selectiegereedschap een bewerkbare component op de pagina en bekijk de details van het element.

   De component heeft een nieuw gegevenskenmerk `data-cq-data-path` .

   ![ Stap 2 ](assets/spa-walkthrough-step-2-2.png)

   Bijvoorbeeld

   `data-cq-data-path="/content/wknd-spa-react/us/en/home/jcr:content/root/responsivegrid/text`

   Met dit pad kunt u het contextconfiguratieobject van elke component ophalen en koppelen.

   Dit is het enige prijsverhogingsattribuut dat voor de redacteur wordt vereist om dit als editable component binnen de SPA te erkennen. Gebaseerd op dit attribuut, zal de SPA Redacteur bepalen welke editable configuratie met de component wordt geassocieerd, zodat het correcte kader, de toolbar, etc., wordt geladen.

   Bepaalde specifieke klassenamen worden ook toegevoegd voor het markeren van plaatsaanduidingen en voor het slepen en neerzetten van elementen.

   >[!NOTE]
   >
   >Dit is een gedragswijziging van gerenderde pagina&#39;s op de server in AEM, waarbij voor elke bewerkbare component een element `cq` wordt ingevoegd.
   >
   >
   >Deze benadering in SPA verwijdert de behoefte om douaneelementen te injecteren, die slechts een extra gegevensattribuut baseren, die de prijsverhoging voor de frontend ontwikkelaar eenvoudiger maken.

## Volgende stappen {#next-steps}

Nu u de SPA het uitgeven ervaring in AEM begrijpt en hoe een SPA op de SPA Redacteur betrekking heeft, neem een diepgaande duik in het begrijpen van hoe een SPA wordt gebouwd.

* [ Begonnen het Worden met SPA in AEM ](/help/sites-developing/spa-getting-started-react.md) toont hoe een basis SPA wordt gebouwd om met de SPA Redacteur in AEM te werken
* [ SPA het Overzicht van de Redacteur ](/help/sites-developing/spa-overview.md) gaat in meer diepte in het communicatie model tussen AEM en de SPA.
* [ het ontwikkelen SPA voor AEM ](/help/sites-developing/spa-architecture.md) beschrijft hoe te om front-end ontwikkelaars in dienst te nemen om een SPA voor AEM te ontwikkelen en hoe SPA met AEM architectuur in wisselwerking staan.

