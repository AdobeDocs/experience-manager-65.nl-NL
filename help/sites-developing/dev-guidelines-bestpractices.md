---
title: AEM ontwikkeling - Richtsnoeren en beste praktijken
description: Richtsnoeren en beste praktijken voor de ontwikkeling van AEM
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 8eef7e4d-a6f2-4b87-a995-0761447283c6
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 0%

---

# AEM ontwikkeling - Richtsnoeren en beste praktijken{#aem-development-guidelines-and-best-practices}

## Richtlijnen voor het gebruik van sjablonen en componenten {#guidelines-for-using-templates-and-components}

Adobe Experience Manager (AEM)-componenten en -sjablonen vormen een krachtige toolkit. Ze kunnen door ontwikkelaars worden gebruikt om zakelijke gebruikers, editors en beheerders van websites de functionaliteit te bieden om hun websites aan te passen aan veranderende bedrijfsbehoeften (inhouds-behendigheid). Dit alles met behoud van de uniforme lay-out van de sites (merkbescherming).

Een typische uitdaging voor een persoon verantwoordelijk voor een website, of een reeks websites (bijvoorbeeld in een bijkantoor van een globale onderneming), is een nieuw type van inhoudspresentatie op hun websites te introduceren.

Laten we ervan uitgaan dat er een nieuwsbrief moet worden toegevoegd aan de websites, waarin uittreksels uit andere artikelen staan die al zijn gepubliceerd. De pagina moet hetzelfde ontwerp en dezelfde structuur hebben als de rest van de website.

De aanbevolen manier om een dergelijke uitdaging aan te gaan is:

* U kunt een bestaande sjabloon opnieuw gebruiken, zodat u een paginatype kunt maken. De sjabloon definieert grofweg de paginastructuur (navigatie-elementen, deelvensters, enzovoort), die verder wordt verfijnd door het ontwerp (CSS, afbeeldingen).
* Gebruik het paragraafsysteem (parsys/iparsys) op de nieuwe pagina&#39;s.
* Bepaal toegangsrecht tot de wijze van het Ontwerp van de paragraafsystemen, zodat slechts de gemachtigde mensen (gewoonlijk de beheerder) hen kunnen veranderen.
* Definieer de componenten die zijn toegestaan in het opgegeven alineasysteem, zodat editors de vereiste componenten op de pagina kunnen plaatsen. In dit geval kan het een component List zijn, die een subboomstructuur van pagina&#39;s kan doorlopen en de informatie kan ophalen volgens vooraf gedefinieerde regels.
* Editors voegen en configureren de toegestane componenten toe op de pagina&#39;s waarvoor ze verantwoordelijk zijn, om de gevraagde functionaliteit (informatie) aan het bedrijf te leveren.

Dit illustreert hoe deze benadering de bijdragende gebruikers en beheerders van de website machtigt om snel aan bedrijfsbehoeften te antwoorden, zonder de betrokkenheid van ontwikkelingsteams te vereisen. Alternatieve methodes, zoals het creëren van een malplaatje, zijn gewoonlijk een dure oefening, die een veranderingsbeheersproces en betrokkenheid van het ontwikkelingsteam vereist. Dit maakt het hele proces langer en kostbaar.

De ontwikkelaars van op AEM gebaseerde systemen moeten daarom gebruik maken van:

* sjablonen en toegangsbeheer voor het ontwerpen van alineasystemen voor uniformiteit en merkbescherming
* alineasysteem, met inbegrip van de configuratieopties voor flexibiliteit.

De volgende algemene regels voor ontwikkelaars zijn zinvol voor de meest gebruikelijke projecten:

* Houd het aantal sjablonen laag - zo laag als het aantal fundamenteel verschillende paginastructuren op de websites.
* Verstrek de noodzakelijke flexibiliteit en configuratiemogelijkheden aan uw douanecomponenten.
* Maximaliseer gebruik van de macht en de flexibiliteit van het de paragraafsysteem van de AEM - parsys &amp; iparsys componenten.

### Componenten en andere elementen aanpassen {#customizing-components-and-other-elements}

Wanneer u uw eigen componenten maakt of een bestaande component aanpast, is het vaak het eenvoudigst (en veiligst) om bestaande definities opnieuw te gebruiken. Dezelfde beginselen gelden ook voor andere elementen binnen AEM, bijvoorbeeld de fouthandler.

Dit kan worden gedaan door de bestaande definitie te kopiëren en te bedekken. Met andere woorden, het kopiëren van de definitie van `/libs` naar `/apps/<your-project>` . Deze nieuwe definitie, in `/apps`, kan volgens uw vereisten worden bijgewerkt.

>[!NOTE]
>
>Zie [&#x200B; Gebruikend Bedekkingen &#x200B;](/help/sites-developing/overlays.md) voor meer details.

Bijvoorbeeld:

* [Een component aanpassen](/help/sites-developing/components.md)

  Hiervoor moest een componentdefinitie worden bedekt:

   * Maak een componentmap in `/apps/<website-name>/components/<MyComponent>` door een bestaande component te kopiëren:

      * Bijvoorbeeld om het de componentenexemplaar van de Tekst aan te passen:

         * Van `/libs/foundation/components/text`
         * tot `/apps/myProject/components/text`

* [Pagina&#39;s aanpassen die worden weergegeven door de fouthandler](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

  In dit geval wordt een servlet bedekt:

   * Kopieer een of meer standaardscripts in de opslagplaats:

      * Van `/libs/sling/servlet/errorhandler/`
      * tot `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>**&#x200B;** verander niets in de `/libs` weg.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>Voor configuratie en andere wijzigingen:
>
>1. het item kopiëren in `/libs` naar `/apps`
>1. om het even welke veranderingen aanbrengen binnen `/apps`

## Wanneer moeten JCR-query&#39;s worden gebruikt en wanneer moeten deze niet worden gebruikt? {#when-to-use-jcr-queries-and-when-not-to-use-them}

JCR-query&#39;s zijn een krachtig hulpmiddel als ze correct worden uitgevoerd. Zij zijn geschikt voor:

* echte eindgebruikervragen, zoals fullText onderzoeken op inhoud.
* gevallen waarin gestructureerde inhoud moet worden gevonden in de gehele gegevensopslagruimte.

  In dergelijke gevallen, zorg ervoor dat de vragen slechts wanneer vereist lopen. Bijvoorbeeld bij componentactivering of cachevalidatie (in tegenstelling tot bijvoorbeeld Workflows Stappen, Gebeurtenishandlers die worden geactiveerd bij inhoudswijzigingen en Filters).

Gebruik nooit JCR-query&#39;s voor pure rendering-aanvragen. JCR-query&#39;s zijn bijvoorbeeld niet geschikt voor het volgende:

* renderingnavigatie
* een overzicht maken van de 10 meest recente nieuwsartikelen
* het tonen van tellingen van inhoudspunten

Gebruik voor het renderen van inhoud navigatie-toegang tot de inhoudsstructuur in plaats van een JCR-query uit te voeren.

>[!NOTE]
>
>Als u de [&#x200B; Bouwer van de Vraag &#x200B;](/help/sites-developing/querybuilder-api.md) gebruikt, gebruikt u JCR Vragen, aangezien de Bouwer van de Vraag JCR Vragen onder de kap produceert.
>

## Beveiligingsoverwegingen {#security-considerations}

>[!NOTE]
>
>Het is ook nuttig om naar [&#x200B; veiligheidscontrolelijst &#x200B;](/help/sites-administering/security-checklist.md) te verwijzen.

### JCR-sessies (Repository) {#jcr-repository-sessions}

Gebruik de gebruikerssessie, niet de beheersessie. Dit betekent dat u het volgende moet gebruiken:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Protect tegen XSS (Cross-Site Scripting) {#protect-against-cross-site-scripting-xss}

Met XSS (Cross-site scripting) kunnen aanvallers code injecteren in webpagina&#39;s die door andere gebruikers worden weergegeven. Deze kwetsbaarheid op het gebied van beveiliging kan door kwaadaardige webgebruikers worden misbruikt om toegangsbesturingselementen te omzeilen.

AEM past het beginsel toe van het filtreren van alle gebruiker-geleverde inhoud op output. Het voorkomen van XSS krijgt de hoogste prioriteit tijdens zowel ontwikkeling als testen.

Ook, kan een firewall van de Webtoepassing, zoals [&#x200B; mod_security voor Apache &#x200B;](https://modsecurity.org), betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder onontdekte dwars-plaats scripting aanvallen beschermen.

>[!CAUTION]
>
>De voorbeeldcode van AEM kan niet zelf tegen dergelijke aanvallen beschermen en baseert zich over het algemeen op verzoek het filtreren door een firewall van de Webtoepassing.

Het XSS API-taakblad bevat informatie waarvan u moet weten dat u de XSS-API kunt gebruiken en een AEM-app veiliger kunt maken. U kunt het hier downloaden:

Het XSSAPI-controleblad.

[Bestand ophalen](assets/xss_cheat_sheet_2016.pdf)

### Communicatie beveiligen voor vertrouwelijke informatie {#securing-communication-for-confidential-information}

Bij elke internettoepassing moet u ervoor zorgen dat bij het vervoer van vertrouwelijke informatie

* verkeer wordt beveiligd via SSL
* Indien van toepassing wordt HTTP-POST gebruikt

Dit geldt voor informatie die vertrouwelijk is voor het systeem (zoals configuratie of administratieve toegang) en informatie die vertrouwelijk is voor de gebruikers (zoals hun persoonlijke gegevens).

## Specifieke ontwikkelingstaken {#distinct-development-tasks}

### Foutpagina&#39;s aanpassen {#customizing-error-pages}

Foutpagina&#39;s kunnen voor AEM worden aangepast. Dit is aan te raden, zodat de instantie geen bewegingssporen weergeeft bij interne serverfouten.

Zie [&#x200B; Aanpassen van de Pagina&#39;s van de Fout die door de Handler van de Fout &#x200B;](/help/sites-developing/customizing-errorhandler-pages.md) voor volledige details worden getoond.

### Bestanden openen in het Java™-proces {#open-files-in-the-java-process}

Omdat AEM tot vele dossiers kan toegang hebben, wordt het geadviseerd dat het aantal [&#x200B; open dossiers voor een proces Java™ &#x200B;](/help/sites-deploying/configuring.md#open-files-in-the-java-process) uitdrukkelijk voor AEM worden gevormd.

Om dit probleem tot een minimum te beperken, moet bij de ontwikkeling ervoor worden gezorgd dat geopende bestanden correct worden gesloten wanneer dat (zinvol) mogelijk is.
