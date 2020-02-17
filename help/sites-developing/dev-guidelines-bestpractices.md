---
title: AEM-ontwikkeling - Richtlijnen en beste praktijken
seo-title: AEM-ontwikkeling - Richtlijnen en beste praktijken
description: Richtlijnen en beste praktijken voor ontwikkeling op AEM
seo-description: Richtlijnen en beste praktijken voor ontwikkeling op AEM
uuid: a67de085-4441-4a1d-bec3-2f27892a67ff
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b4cf0ffc-973a-473b-80c8-7f530d111435
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM-ontwikkeling - Richtlijnen en beste praktijken{#aem-development-guidelines-and-best-practices}

## Richtlijnen voor het gebruik van sjablonen en componenten {#guidelines-for-using-templates-and-components}

AEM-componenten en -sjablonen vormen een zeer krachtige toolkit. Ze kunnen door ontwikkelaars worden gebruikt om zakelijke gebruikers, editors en beheerders van websites de functionaliteit te bieden om hun websites aan te passen aan veranderende bedrijfsbehoeften (inhouds-behendigheid) terwijl de uniforme lay-out van de sites behouden blijft (merkbescherming).

Een typische uitdaging voor een persoon verantwoordelijk voor een website, of reeks websites (bijvoorbeeld in een bijkantoor van een globale onderneming), is een nieuw type van inhoudspresentatie op hun websites te introduceren.

Laten we ervan uitgaan dat er een nieuwsbrief moet worden toegevoegd aan de websites, waarin uittreksels uit andere artikelen staan die al zijn gepubliceerd. De pagina moet hetzelfde ontwerp en dezelfde structuur hebben als de rest van de website.

De aanbevolen manier om een dergelijke uitdaging aan te gaan is:

* Een bestaande sjabloon opnieuw gebruiken om een nieuw type pagina te maken. De sjabloon definieert grofweg de paginastructuur (navigatie-elementen, deelvensters, enzovoort), die verder wordt verfijnd door het ontwerp (CSS, afbeeldingen).
* Gebruik het paragraafsysteem (parsys/iparsys) op de nieuwe pagina&#39;s.
* Bepaal toegangsrecht tot de wijze van het Ontwerp van de paragraafsystemen, zodat slechts de gemachtigde mensen (gewoonlijk de beheerder) hen kunnen veranderen.
* Definieer de componenten die zijn toegestaan in het opgegeven alineasysteem, zodat editors de vereiste componenten op de pagina kunnen plaatsen. In ons geval kan het een lijstcomponent zijn, die een subboomstructuur van pagina&#39;s kan doorlopen en de informatie volgens vooraf bepaalde regels kan halen.
* De redacteurs voegen en vormen de toegestane componenten, op de pagina&#39;s toe zij voor verantwoordelijk zijn, om de gevraagde functionaliteit (informatie) aan de zaken te leveren.

Dit illustreert hoe deze benadering de bijdragende gebruikers en beheerders van de website machtigt om snel aan bedrijfsbehoeften te antwoorden, zonder de betrokkenheid van ontwikkelingsteams te vereisen. Alternatieve methodes, zoals het creëren van een nieuw malplaatje, zijn gewoonlijk een dure oefening, die een veranderingsbeheersproces en betrokkenheid van het ontwikkelingsteam vereist. Dit maakt het hele proces veel langer en kostbaar.

De ontwikkelaars van op AEM gebaseerde systemen moeten daarom gebruikmaken van:

* sjablonen en toegangsbeheer voor het ontwerpen van alineasystemen voor uniformiteit en merkbescherming
* alineasysteem, inclusief configuratieopties voor flexibiliteit.

De volgende algemene regels voor ontwikkelaars zijn in de meeste gebruikelijke projecten zinvol:

* Houd het aantal sjablonen laag - zo laag als het aantal fundamenteel verschillende paginastructuren op de websites.
* Verstrek noodzakelijke flexibiliteit en configuratiemogelijkheden aan uw douanecomponenten.
* Maximaliseer gebruik van de macht en de flexibiliteit van AEM paragraafsysteem - parsys &amp; iparsys componenten.

### Componenten en andere elementen aanpassen {#customizing-components-and-other-elements}

Wanneer u uw eigen componenten maakt of een bestaande component aanpast, is het vaak het eenvoudigst (en veiligst) om bestaande definities opnieuw te gebruiken. Dezelfde beginselen gelden ook voor andere elementen binnen AEM, bijvoorbeeld de fouthandler.

Dit kan worden gedaan door de bestaande definitie te kopiëren en te bedekken. Met andere woorden, het kopiëren van de definitie van `/libs` naar `/apps/<your-project>`. Deze nieuwe definitie in `/apps`, kan volgens uw vereisten worden bijgewerkt.

>[!NOTE]
>
>Zie Bedekkingen [gebruiken](/help/sites-developing/overlays.md) voor meer informatie.

Bijvoorbeeld:

* [Een component aanpassen](/help/sites-developing/components.md)

   Hiervoor moest een componentdefinitie worden bedekt:

   * Maak een nieuwe componentmap in `/apps/<website-name>/components/<MyComponent>` door een bestaande component te kopiëren:

      * Bijvoorbeeld om het de componentenexemplaar van de Tekst aan te passen:

         * from `/libs/foundation/components/text`
         * to `/apps/myProject/components/text`

* [Pagina&#39;s aanpassen die worden weergegeven door de fouthandler](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

   In dit geval wordt een servlet bedekt:

   * Kopieer het standaardscript of de standaardscripts in de gegevensopslagruimte:

      * from `/libs/sling/servlet/errorhandler/`
      * to `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>U **mag niets** wijzigen in het `/libs` pad.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>Voor configuratie en andere wijzigingen:
>
>1. het item kopiëren in `/libs` naar `/apps`
>1. wijzigingen aanbrengen in `/apps`


## Wanneer moeten JCR-query&#39;s worden gebruikt en wanneer moeten deze niet worden gebruikt? {#when-to-use-jcr-queries-and-when-not-to-use-them}

JCR-query&#39;s zijn een krachtig hulpmiddel als ze correct worden uitgevoerd. Zij zijn geschikt voor:

* echte eindgebruikervragen, zoals fullText onderzoeken op inhoud.
* gevallen waarin gestructureerde inhoud moet worden gevonden in de gehele gegevensopslagruimte.

   In dergelijke gevallen moet u ervoor zorgen dat query&#39;s alleen worden uitgevoerd wanneer dit absoluut vereist is, bijvoorbeeld bij componentactivering of cachevalidatie (in tegenstelling tot bijvoorbeeld Workflows Stappen, Gebeurtenishandlers die worden geactiveerd bij inhoudswijzigingen, Filters, enz.).

JCR-query&#39;s mogen nooit worden gebruikt voor pure renderingaanvragen. JCR-query&#39;s zijn bijvoorbeeld niet geschikt voor

* renderingnavigatie
* een overzicht maken van de 10 meest recente nieuwsartikelen
* het tonen van tellingen van inhoudspunten

Gebruik voor het renderen van inhoud navigatie-toegang tot de inhoudsstructuur in plaats van een JCR-query uit te voeren.

>[!NOTE]
>
>Als u de [Bouwer](/help/sites-developing/querybuilder-api.md)van de Vraag gebruikt, gebruikt u Vragen JCR, aangezien de Bouwer van de Vraag JCR Vragen onder de kap produceert.


## Beveiligingsoverwegingen {#security-considerations}

>[!NOTE]
>
>Het is ook nuttig om naar de [veiligheidscontrolelijst](/help/sites-administering/security-checklist.md)te verwijzen.

### JCR-sessies (Repository) {#jcr-repository-sessions}

Gebruik de gebruikerssessie, niet de beheersessie. Dit betekent dat u het volgende moet gebruiken:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Beveiligen tegen XSS (Cross-Site Scripting) {#protect-against-cross-site-scripting-xss}

Met XSS (Cross-site scripting) kunnen aanvallers code injecteren in webpagina&#39;s die door andere gebruikers worden weergegeven. Deze kwetsbaarheid op het gebied van beveiliging kan door kwaadaardige webgebruikers worden misbruikt om toegangsbesturingselementen te omzeilen.

AEM past het beginsel toe om alle gebruiker-geleverde inhoud op output te filtreren. Het voorkomen van XSS krijgt de hoogste prioriteit tijdens zowel ontwikkeling als testen.

Bovendien, kan een firewall van de Webtoepassing, zoals [mod_security voor Apache](https://modsecurity.org), betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder niet ontdekte dwars-plaats scripting aanvallen beschermen.

>[!CAUTION]
>
>De voorbeeldcode die bij AEM wordt verstrekt kan niet zelf tegen dergelijke aanvallen beschermen en baseert zich over het algemeen op verzoek het filtreren door een firewall van de Webtoepassing.

Het XSS API-opmaakmodel bevat informatie die u moet weten om de XSS API te kunnen gebruiken en een AEM-toepassing veiliger te maken. U kunt het hier downloaden:

Het XSSAPI-controleblad.

[Bestand ophalen](assets/xss_cheat_sheet_2016.pdf)

### Communicatie beveiligen voor vertrouwelijke informatie {#securing-communication-for-confidential-information}

Bij elke internettoepassing moet u ervoor zorgen dat bij het vervoer van vertrouwelijke informatie

* verkeer wordt beveiligd via SSL
* HTTP POST wordt gebruikt indien van toepassing

Dit geldt voor informatie die vertrouwelijk is voor het systeem (zoals configuratie of administratieve toegang) en voor informatie die vertrouwelijk is voor de gebruikers (zoals hun persoonlijke gegevens).

## Afzonderlijke ontwikkelingstaken {#distinct-development-tasks}

### Foutpagina&#39;s aanpassen {#customizing-error-pages}

Foutpagina&#39;s kunnen voor AEM worden aangepast. Dit is aan te raden, zodat de instantie geen bewegingssporen weergeeft bij interne serverfouten.

Zie [Aanpassen van de Pagina&#39;s van de Fout die door de Handler](/help/sites-developing/customizing-errorhandler-pages.md) van de Fout voor volledige details wordt getoond.

### Bestanden openen in het Java-proces {#open-files-in-the-java-process}

Omdat AEM tot een groot aantal dossiers kan toegang hebben, wordt geadviseerd dat het aantal [open dossiers voor een proces](/help/sites-deploying/configuring.md#open-files-in-the-java-process) van Java uitdrukkelijk voor AEM wordt gevormd.

Om dit probleem tot een minimum te beperken, moet de ontwikkeling ervoor zorgen dat geopende bestanden zo snel (zinvol) mogelijk correct worden gesloten.
