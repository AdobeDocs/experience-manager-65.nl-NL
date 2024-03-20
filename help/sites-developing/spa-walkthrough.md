---
title: SPA Inleiding en Analyse
description: Dit artikel introduceert de concepten van een SPA en loopt door het gebruiken van een basis SPA toepassing voor creatie, die toont hoe het op het onderliggende AEM SPA Redacteur betrekking heeft.
topic-tags: spa
content-type: reference
exl-id: 95990112-2afc-420a-a7c7-9613f40d4c4a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1945'
ht-degree: 0%

---


# SPA Inleiding en Analyse {#spa-introduction-and-walkthrough}

Toepassingen op één pagina (SPA) kunnen aantrekkelijke ervaringen bieden voor websitegebruikers. Ontwikkelaars willen sites kunnen maken met behulp van SPA frameworks en auteurs willen inhoud naadloos bewerken binnen AEM voor een site die is gebouwd met behulp van dergelijke frameworks.

De SPA Editor biedt een uitgebreide oplossing voor het ondersteunen van SPA binnen AEM. Dit artikel doorloopt het gebruiken van een basis SPA toepassing voor creatie en toont hoe het op het onderliggende AEM SPA Redacteur betrekking heeft.

>[!NOTE]
>
>De SPA Redacteur is de geadviseerde oplossing voor projecten die SPA op kader-gebaseerde cliënt-zijteruggeven (bijvoorbeeld, Reageren of Angular) vereisen.

## Inleiding {#introduction}

### Artikel {#article-objective}

Dit artikel introduceert de basisconcepten van SPA alvorens de lezer door een analyse van de SPA redacteur door een eenvoudige SPA toepassing te gebruiken te leiden om basisinhoud het uitgeven aan te tonen. Vervolgens duikt het neer in de constructie van de pagina en hoe de SPA toepassing zich verhoudt tot en communiceert met de AEM SPA Editor.

Het doel van deze inleiding en analyse is aan een AEM ontwikkelaar te tonen waarom SPA relevant zijn, hoe zij over het algemeen werken, hoe een SPA door de AEM Redacteur wordt behandeld SPA, en hoe het van een standaard AEM toepassing verschillend is.

## Vereisten {#requirements}

De analyse is gebaseerd op standaard AEM functionaliteit en de steekproefWKND SPA Project app. Om samen met deze analyse te volgen, moet u het volgende beschikbaar hebben.

* [AEM versie 6.5.4 of hoger](/help/release-notes/release-notes.md)
   * U moet beheerdersrechten voor het systeem hebben.
* [De steekproefWKND SPA Project beschikbaar op GitHub](https://github.com/adobe/aem-guides-wknd-spa)
   * Download de [nieuwste versie van de React-app.](https://github.com/adobe/aem-guides-wknd-spa/releases) De naam van de functie is vergelijkbaar met `wknd-spa-react.all.classic-X.Y.Z-SNAPSHOT.zip`.
   * Download de [nieuwste voorbeeldafbeeldingen](https://github.com/adobe/aem-guides-wknd-spa/releases) voor de app. De naam van de functie is vergelijkbaar met `wknd-spa-sample-images-X.Y.Z.zip`.
   * [Pakketbeheer gebruiken](/help/sites-administering/package-manager.md) om de pakketten te installeren zoals u een ander pakket in AEM.
   * Voor deze analyse hoeft de app niet te worden geïnstalleerd met Maven.

>[!CAUTION]
>
>In dit document worden de [WKND Spa Project-app](https://github.com/adobe/aem-guides-wknd-spa) uitsluitend voor demonstratiedoeleinden. Niet gebruiken voor projectwerk.
>
>Voor elk AEM project moet het [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) die SPA projecten gebruikend React of Angular steunt en SPA SDK gebruikt.

### Wat is een SPA? {#what-is-a-spa}

Een toepassing van één pagina (SPA) verschilt van een conventionele pagina in die zin dat deze wordt weergegeven op de client en voornamelijk wordt aangedreven door JavaScript. Hierbij wordt uitgegaan van Ajax-aanroepen om gegevens te laden en de pagina dynamisch bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die asynchroon worden geladen, afhankelijk van gebruikersinteractie met de pagina.

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
* Schone scheiding maakt het systeem meer uitbreidbaar en maakt een onafhankelijke ontwikkeling aan de voorzijde mogelijk.

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

1. Bewerk de WKND SPA Project-app in AEM.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

   ![Stap 1](assets/spa-walkthrough-step-1.png)

1. Selecteer een koptekstcomponent. Een werkbalk ziet er net zo uit als een andere component. Selecteren **Bewerken**.

   ![Stap 2](assets/spa-walkthrough-step-2.png)

1. Bewerk de inhoud als normaal binnen AEM. De wijzigingen blijven bestaan.

   ![Stap 3](assets/spa-walkthrough-step-3.png)

   >[!NOTE]
   >
   >Zie de [Overzicht SPA Editor](spa-overview.md#requirements-limitations) voor meer informatie over de bestaande teksteditor en SPA.

1. Met de middelenbrowser kunt u een nieuwe afbeelding naar een afbeeldingscomponent slepen en neerzetten.

   ![Stap 4](assets/spa-walkthrough-step-4.png)

1. De wijziging wordt doorgevoerd.

   ![Stap 5](assets/spa-walkthrough-step-5.png)

Extra ontwerpgereedschappen, zoals het slepen en neerzetten van aanvullende componenten op de pagina, het opnieuw rangschikken van componenten en het wijzigen van de layout, worden ondersteund zoals in elke andere toepassing dan SPA.

>[!NOTE]
>
>De SPA Editor wijzigt het DOM van de toepassing niet. De SPA zelf is verantwoordelijk voor het DOM.
>
>Ga naar de volgende sectie van dit artikel om te zien hoe dit werkt [Apps en de AEM SPA Editor SPA](#spa-apps-and-the-aem-spa-editor).

## Apps en de AEM SPA Editor SPA {#spa-apps-and-the-aem-spa-editor}

Door te ervaren hoe een SPA zich gedraagt voor de eindgebruiker en vervolgens de SPA pagina te inspecteren, kunt u beter begrijpen hoe een SAP-app werkt met de SPA Editor in AEM.

### Een SPA toepassing gebruiken {#using-an-spa-application}

1. Laad de WKND SPA-projecttoepassing op de publicatieserver of met de optie **Weergeven als gepubliceerd** van de **Pagina-informatie** in de pagina-editor.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![Stap 1](assets/spa-walkthrough-step-1-1.png)

   Neem nota van de paginastructuur met inbegrip van navigatie aan kindpagina&#39;s, weer widget, en artikelen.

1. Navigeer naar een onderliggende pagina met behulp van het menu en controleer of de pagina direct wordt geladen zonder dat een pagina moet worden vernieuwd.

   ![Stap 2](assets/spa-walkthrough-step-1-2.png)

1. Open de ingebouwde ontwikkelaarsgereedschappen van uw browser en controleer de netwerkactiviteit terwijl u door de onderliggende pagina&#39;s navigeert.

   ![Stap 3](assets/spa-walkthrough-step-1-3.png)

   Er is erg weinig verkeer wanneer u van pagina naar pagina gaat in de app. De pagina wordt niet opnieuw geladen en alleen de nieuwe afbeeldingen worden aangevraagd.

   De SPA beheert de inhoud en het verpletteren volledig op de cliëntkant.

Dus als de pagina niet opnieuw wordt geladen wanneer u door de onderliggende pagina&#39;s navigeert, hoe wordt deze geladen?

de volgende afdeling, [Een SPA toepassing laden,](#loading-an-spa-application) graaft dieper in de mechanica van het laden van de SPA en hoe inhoud synchroon en asynchroon kan worden geladen.

### Een SPA laden {#loading-an-spa-application}

1. Laad, indien nog niet geladen, de WKND SPA Project-app op de publicatieserver of met de optie **Weergeven als gepubliceerd** van de **Pagina-informatie** in de pagina-editor.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.html`

   ![Stap 1](assets/spa-walkthrough-step-1-1.png)

1. Gebruik het ingebouwde gereedschap van uw browser om de bron van de pagina weer te geven.
1. De inhoud van de bron is uiterst beperkt.

   * De pagina heeft geen inhoud in de hoofdtekst. Het bestaat voornamelijk uit stijlpagina&#39;s en een aanroep naar verschillende scripts, zoals `clientlib-react.min.js`.
   * Deze scripts vormen de belangrijkste stuurprogramma&#39;s voor deze toepassing en zijn verantwoordelijk voor het renderen van alle inhoud.

1. Gebruik de ingebouwde gereedschappen van uw browser om de pagina te inspecteren. Zie de inhoud van de DOM volledig geladen.

   ![Stap 4](assets/spa-walkthrough-step-1-4.png)

1. Schakel over naar de **Netwerk** van de ontwikkelaarsgereedschappen en laad de pagina opnieuw.

   Afbeeldingsverzoeken worden genegeerd. De primaire bronnen die voor de pagina worden geladen, zijn de pagina zelf, CSS, de React JavaScript, de afhankelijkheden en JSON-gegevens voor de pagina.

   ![Stap 5](assets/spa-walkthrough-step-1-5.png)

1. Laad de `react.model.json` op een nieuw tabblad.

   `http://<host>:<port>/content/wknd-spa-react/us/en/home.model.json`

   ![Stap 6](assets/spa-walkthrough-step-1-6.png)

   De AEM SPA Editor gebruikt [AEM Content Services](/help/assets/content-fragments/content-fragments.md) om de volledige inhoud van de pagina als JSON-model te leveren.

   Door specifieke interfaces uit te voeren, verstrekken de Modellen van het Sling de informatie noodzakelijk aan de SPA. De levering van de JSON-gegevens wordt omlaag gedelegeerd aan elke component (van pagina, alinea, component, enzovoort).

   Elke component kiest wat het blootstelt en hoe het (server-kant met HTML of cliënt-kant met React) wordt teruggegeven. Dit artikel richt zich op client-side rendering met React.

1. Het model kan pagina&#39;s ook groeperen zodat ze synchroon worden geladen, waardoor het aantal pagina&#39;s dat opnieuw moet worden geladen, afneemt.

   In het voorbeeld van de WKND-SPA Project-app `home`, `page-1`, `page-2`, en `page-3` De pagina&#39;s worden synchroon geladen, aangezien bezoekers doorgaans al deze pagina&#39;s bezoeken.

   Dit gedrag is niet verplicht en is volledig definieerbaar.

   ![Stap 7](assets/spa-walkthrough-step-1-7.png)

1. Om dit verschil in gedrag te bekijken, laad de pagina opnieuw en ontruim de netwerkactiviteit van de ontwikkelaarshulpmiddelen. Navigeren naar `page-1` in het paginamenu en controleer of de enige netwerkactiviteit een verzoek is om het image van `page-1`. `page-1` zelf hoeft niet te worden geladen.

   ![Stap 8](assets/spa-walkthrough-step-1-8.png)

### Interactie met de SPA Editor {#interaction-with-the-spa-editor}

Met behulp van de voorbeeldtoepassing WKND SPA Project is het duidelijk hoe de app zich gedraagt en wordt geladen wanneer deze wordt gepubliceerd, met behulp van inhoudsservices voor het leveren van JSON-inhoud en het asynchroon laden van bronnen.

Voor de auteur van de inhoud is het maken van inhoud met een SPA-editor bovendien naadloos in AEM.

In de volgende sectie zullen wij het contract onderzoeken dat de SPARedacteur toestaat om componenten binnen de SPA met AEM componenten te verbinden en deze naadloze het uitgeven ervaring te bereiken.

1. Laad de WKND SPA toepassing van het Project in de redacteur en schakelaar aan **Voorvertoning** -modus.

   `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`

1. Controleer de inhoud van de pagina met de ingebouwde ontwikkelaarsgereedschappen van uw browser. Selecteer met het selectiegereedschap een bewerkbare component op de pagina en bekijk de details van het element.

   De component heeft een nieuw gegevenskenmerk `data-cq-data-path`.

   ![Stap 2](assets/spa-walkthrough-step-2-2.png)

   Bijvoorbeeld

   `data-cq-data-path="/content/wknd-spa-react/us/en/home/jcr:content/root/responsivegrid/text`

   Met dit pad kunt u het contextconfiguratieobject van elke component ophalen en koppelen.

   Dit is het enige prijsverhogingsattribuut dat voor de redacteur wordt vereist om dit als editable component binnen de SPA te erkennen. Gebaseerd op dit attribuut, zal de SPA Redacteur bepalen welke editable configuratie met de component wordt geassocieerd, zodat het correcte kader, de toolbar, etc., wordt geladen.

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
* [SPA ontwikkelen voor AEM](/help/sites-developing/spa-architecture.md) beschrijft hoe te om front-end ontwikkelaars in dienst te nemen om een SPA voor AEM te ontwikkelen en hoe SPA met AEM architectuur in wisselwerking staan.
