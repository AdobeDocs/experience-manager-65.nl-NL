---
title: AEM ontwikkeling - Richtsnoeren en beste praktijken
seo-title: AEM Development - Guidelines and Best Practices
description: Richtsnoeren en beste praktijken voor de ontwikkeling van AEM
seo-description: Guidelines and best practices for developing on AEM
uuid: a67de085-4441-4a1d-bec3-2f27892a67ff
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b4cf0ffc-973a-473b-80c8-7f530d111435
exl-id: 8eef7e4d-a6f2-4b87-a995-0761447283c6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 0%

---

# AEM ontwikkeling - Richtsnoeren en beste praktijken{#aem-development-guidelines-and-best-practices}

## Richtlijnen voor het gebruik van sjablonen en componenten {#guidelines-for-using-templates-and-components}

AEM componenten en sjablonen vormen een zeer krachtige toolkit. Ze kunnen door ontwikkelaars worden gebruikt om zakelijke gebruikers, editors en beheerders van websites de functionaliteit te bieden om hun websites aan te passen aan veranderende bedrijfsbehoeften (inhouds-behendigheid) terwijl de uniforme lay-out van de sites behouden blijft (merkbescherming).

Een typische uitdaging voor een persoon verantwoordelijk voor een website, of reeks websites (bijvoorbeeld in een bijkantoor van een globale onderneming), is een nieuw type van inhoudspresentatie op hun websites te introduceren.

Laten we ervan uitgaan dat er een nieuwsbrief moet worden toegevoegd aan de websites, waarin uittreksels uit andere artikelen staan die al zijn gepubliceerd. De pagina moet hetzelfde ontwerp en dezelfde structuur hebben als de rest van de website.

De aanbevolen manier om een dergelijke uitdaging aan te gaan is:

* Een bestaande sjabloon opnieuw gebruiken om een nieuw type pagina te maken. De sjabloon definieert grofweg de paginastructuur (navigatie-elementen, deelvensters, enzovoort), die verder wordt verfijnd door het ontwerp (CSS, afbeeldingen).
* Gebruik het paragraafsysteem (parsys/iparsys) op de nieuwe pagina&#39;s.
* Bepaal toegangsrecht tot de wijze van het Ontwerp van de paragraafsystemen, zodat slechts de gemachtigde mensen (gewoonlijk de beheerder) hen kunnen veranderen.
* Definieer de componenten die zijn toegestaan in het opgegeven alineasysteem, zodat editors de vereiste componenten op de pagina kunnen plaatsen. In ons geval kan het een lijstcomponent zijn, die een subboomstructuur van pagina&#39;s kan doorlopen en de informatie volgens vooraf bepaalde regels kan halen.
* De redacteurs voegen en vormen de toegestane componenten, op de pagina&#39;s toe zij voor verantwoordelijk zijn, om de gevraagde functionaliteit (informatie) aan de zaken te leveren.

Dit illustreert hoe deze benadering de bijdragende gebruikers en beheerders van de website machtigt om snel aan bedrijfsbehoeften te antwoorden, zonder de betrokkenheid van ontwikkelingsteams te vereisen. Alternatieve methodes, zoals het creëren van een nieuw malplaatje, zijn gewoonlijk een dure oefening, die een veranderingsbeheersproces en betrokkenheid van het ontwikkelingsteam vereist. Dit maakt het hele proces veel langer en kostbaar.

De ontwikkelaars van op AEM gebaseerde systemen moeten daarom gebruik maken van:

* sjablonen en toegangsbeheer voor het ontwerpen van alineasystemen voor uniformiteit en merkbescherming
* alineasysteem, inclusief configuratieopties voor flexibiliteit.

De volgende algemene regels voor ontwikkelaars zijn in de meeste gebruikelijke projecten zinvol:

* Houd het aantal sjablonen laag - zo laag als het aantal fundamenteel verschillende paginastructuren op de websites.
* Verstrek noodzakelijke flexibiliteit en configuratiemogelijkheden aan uw douanecomponenten.
* Maximaliseer gebruik van de macht en de flexibiliteit van AEM paragraafsysteem - parsys &amp; iparsys componenten.

### Componenten en andere elementen aanpassen {#customizing-components-and-other-elements}

Wanneer u uw eigen componenten maakt of een bestaande component aanpast, is het vaak het eenvoudigst (en veiligst) om bestaande definities opnieuw te gebruiken. Dezelfde beginselen gelden ook voor andere elementen binnen AEM, bijvoorbeeld de fouthandler.

Dit kan worden gedaan door de bestaande definitie te kopiëren en te bedekken. Met andere woorden, het kopiëren van de definitie uit `/libs` tot `/apps/<your-project>`. Deze nieuwe definitie, in `/apps`, kan worden bijgewerkt naar wens.

>[!NOTE]
>
>Zie [Bedekkingen gebruiken](/help/sites-developing/overlays.md) voor meer informatie .

Bijvoorbeeld:

* [Een component aanpassen](/help/sites-developing/components.md)

   Hiervoor moest een componentdefinitie worden bedekt:

   * Een nieuwe componentmap maken in `/apps/<website-name>/components/<MyComponent>` door een bestaande component te kopiëren:

      * Bijvoorbeeld om het de componentenexemplaar van de Tekst aan te passen:

         * Van `/libs/foundation/components/text`
         * tot `/apps/myProject/components/text`

* [Pagina&#39;s aanpassen die worden weergegeven door de fouthandler](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

   In dit geval wordt een servlet bedekt:

   * Kopieer het standaardscript of de standaardscripts in de gegevensopslagruimte:

      * Van `/libs/sling/servlet/errorhandler/`
      * tot `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>U **mogen** om het even wat in `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>Voor configuratie en andere wijzigingen:
>
>1. het item kopiëren in `/libs` tot `/apps`
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
>Als u het [Query Builder](/help/sites-developing/querybuilder-api.md)U kunt ook JCR-query&#39;s gebruiken terwijl de Query Builder JCR-query&#39;s onder de kap genereert.

## Beveiligingsoverwegingen {#security-considerations}

>[!NOTE]
>
>Het is ook de moeite waard te verwijzen naar de [beveiligingscontrolelijst](/help/sites-administering/security-checklist.md).

### JCR-sessies (Repository) {#jcr-repository-sessions}

Gebruik de gebruikerssessie, niet de beheersessie. Dit betekent dat u het volgende moet gebruiken:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Protect tegen XSS (Cross-Site Scripting) {#protect-against-cross-site-scripting-xss}

Met XSS (Cross-site scripting) kunnen aanvallers code injecteren in webpagina&#39;s die door andere gebruikers worden weergegeven. Deze kwetsbaarheid op het gebied van beveiliging kan door kwaadaardige webgebruikers worden misbruikt om toegangsbesturingselementen te omzeilen.

AEM past het beginsel toe van het filtreren van alle gebruiker-geleverde inhoud op output. Het voorkomen van XSS krijgt de hoogste prioriteit tijdens zowel ontwikkeling als testen.

Daarnaast is er een webtoepassingsfirewall, zoals [mod_security voor Apache](https://modsecurity.org), kan betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder onontdekte dwars-plaats scripting aanvallen beschermen.

>[!CAUTION]
>
>De voorbeeldcode van AEM kan niet zelf tegen dergelijke aanvallen beschermen en baseert zich over het algemeen op verzoek het filtreren door een firewall van de Webtoepassing.

Het XSS API-taakblad bevat informatie die u moet weten om de XSS API te kunnen gebruiken en een AEM app veiliger te maken. U kunt het hier downloaden:

Het XSSAPI-controleblad.

[Bestand ophalen](assets/xss_cheat_sheet_2016.pdf)

### Communicatie beveiligen voor vertrouwelijke informatie {#securing-communication-for-confidential-information}

Bij elke internettoepassing moet u ervoor zorgen dat bij het vervoer van vertrouwelijke informatie

* verkeer wordt beveiligd via SSL
* Indien van toepassing wordt HTTP-POST gebruikt

Dit geldt voor informatie die vertrouwelijk is voor het systeem (zoals configuratie of administratieve toegang) en voor informatie die vertrouwelijk is voor de gebruikers (zoals hun persoonlijke gegevens).

## Afzonderlijke ontwikkelingstaken {#distinct-development-tasks}

### Foutpagina&#39;s aanpassen {#customizing-error-pages}

Foutpagina&#39;s kunnen voor AEM worden aangepast. Dit is aan te raden, zodat de instantie geen bewegingssporen weergeeft bij interne serverfouten.

Zie [Foutpagina&#39;s aanpassen die worden weergegeven door de foutafhandeling](/help/sites-developing/customizing-errorhandler-pages.md) voor volledige informatie.

### Bestanden openen in het Java-proces {#open-files-in-the-java-process}

Omdat AEM toegang heeft tot een groot aantal bestanden, wordt aanbevolen het aantal [bestanden openen voor een Java-proces](/help/sites-deploying/configuring.md#open-files-in-the-java-process) uitdrukkelijk worden gevormd voor AEM.

Om dit probleem tot een minimum te beperken, moet de ontwikkeling ervoor zorgen dat geopende bestanden zo snel (zinvol) mogelijk correct worden gesloten.
