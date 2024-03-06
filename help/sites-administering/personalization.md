---
title: Personalisatie
description: Leer over verpersoonlijking in Adobe Experience Manager om de gebruiker van een op maat gemaakte milieu te voorzien die dynamische inhoud toont.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 3a550a33-b54b-4217-b9a6-b5a7971276ee
source-git-commit: 518207a0d8a95ef17b0972855a58f124fb215c85
workflow-type: tm+mt
source-wordcount: '1696'
ht-degree: 0%

---

# Personalisatie {#personalization}

## Wat is personalisatie? {#what-is-personalization}

Er is een steeds groter volume aan inhoud beschikbaar vandaag, of het nu op Internet, Extranet, of Intranetwebsites is.

Bij personalisatie wordt de gebruiker voorzien van een op maat gemaakte omgeving waarin dynamische inhoud wordt weergegeven die op basis van de specifieke behoeften is geselecteerd. Hierbij wordt uitgegaan van vooraf gedefinieerde profielen, gebruikersselectie of interactief gebruikersgedrag.

Er zijn drie hoofdelementen betrokken bij personalisatie:

### Gebruikers {#users}

* Profielen hebben, zowel individueel als gegroepeerd. Deze profielen bevatten kenmerken (zoals taakbeschrijving, locatie en interesses) die kunnen worden gebruikt om de inhoud die ze kunnen zien aan te passen.
* Voer handelingen uit. Deze kunnen vervolgens worden geanalyseerd en vergeleken met gedragsregels om de inhoud die ze zien aan te passen.

### Inhoud {#content}

* Is wat de gebruiker wil zien. Voorkeurelijk inhoud van belang, en gebruik, aan hen voor het vervullen van hun taken.
* Kan worden gecategoriseerd en daarom aan gebruikers volgens vooraf bepaalde regels ter beschikking worden gesteld.
* Moet dynamisch zijn.

Met andere woorden, de inhoud moet in zekere zin afhankelijk zijn van de gebruiker. Als elke gebruiker de zelfde inhoud ziet, dan is de verpersoonlijking overtollig.

### Regels {#rules}

* Bepaal hoe verpersoonlijking eigenlijk gebeurt - welke inhoud de gebruiker kan zien, en wanneer.

Personalisatie kan een van de volgende zijn:

#### Expliciet {#explicit}

* Aanpassing: de gebruiker maakt selecties van een keuze uit inhoudsbronnen.

#### Impliciet {#implicit}

* Gebaseerde regels: bedrijfsmanagers bepalen specifieke regels voor acties die op specifieke profielen en/of gedrag worden gebaseerd.
* Eenvoudig filteren: selecties worden gemaakt op basis van vooraf gedefinieerde profielen op gebruikers- en/of groepsniveau.
* Filteren op samenwerking/aanbevelingen: gebruikersgedrag wordt geregistreerd volgens vooraf gedefinieerde regels. Deze regels zijn gebaseerd op gedrag dat wordt waargenomen met gelijkgestemde individuen. De verzamelde informatie wordt gebruikt om de informatie aan de gebruiker te maken, met name in de vorm van aanbevelingen.

## Hoe en wanneer kan Personalisatie worden gebruikt? {#how-and-when-can-personalization-be-used}

Personalisatie kan in veel gevallen worden gebruikt, bijvoorbeeld:

### Intranetpagina&#39;s {#intranet-pages}

* Inhoud kan worden aangeboden op basis van de locatie, afdeling en/of rol van een gebruiker - al gedefinieerd binnen een intern netwerk.
* Afhankelijk van de beschikbare keuze kan de gebruiker meer selecties maken.

### Specifieke, beperkte, doelgebruikersgroepen - Extra&#39;s {#extranets}

* De gebruikers vereisen login voor vergunning; dit zal met een profiel worden verbonden dat informatie verstrekt die voor verpersoonlijking wordt vereist; misschien details zoals hun plaats, verhouding aan het product, gebruiksgeschiedenis, het begroten verantwoordelijkheden, etc.
* Dergelijke instanties kunnen zich uitstrekken over sites zoals:
* Bedrijven die websites aanbieden aan een zeer gespecialiseerde afdeling van hun markt, bijvoorbeeld een farmaceutische onderneming die een gespecialiseerde website voor artsen aanbiedt.
* Bedrijven die websites aanbieden waarmee hun klanten actuele account- en factureringsgegevens kunnen bekijken, bijvoorbeeld telefoonproviders.

### Website voor verkoop en distributie {#sales-site}

* Op verkoop- en distributiewebsites, zoals Amazon, kunnen een gebruikersprofiel, de verkoopgeschiedenis van de gebruiker en de browsergeschiedenis worden gecombineerd om suggesties te doen voor wat de gebruiker interesseert.

### Websites zoeken {#search-site}

* Veel van de belangrijkste websites van zoekprogramma&#39;s beschikken over zeer krachtige analytische instrumenten waarmee het gedrag van gebruikers, de zoektermen die ze gebruiken en de websites die ze bezoeken, worden vastgelegd. Dit wordt vervolgens gebruikt om de aangeboden inhoud aan te passen, met name met betrekking tot het weergeven van advertenties.

### Sterke punten van personalisatie en aandachtspunten {#strengths-of-personalization-and-points-to-consider}

De volgende redenen waarom personalisatie moet worden gebruikt:

* Een gebruiker kan een comfortabele, gerichte website ervaren.
* De verpersoonlijking kan worden gebruikt om toegang tot de recentste versie van inhoud automatisch te verspreiden.
* De functies voor sociale samenwerking zijn beschikbaar voor gebruikers om met elkaar te communiceren, zoals ze door hun profielen kunnen worden geïdentificeerd.
* Een gebruiker kan de inhoud krijgen die hij of zij nodig heeft om een bepaalde taak uit te voeren. Binnen het Intranet van een bedrijf kan dit een onschatbaar hulpmiddel verstrekken om informatie te verspreiden.
* Een gebruiker kan worden voorzien van de inhoud die hij of zij nodig heeft, waardoor hij of zij minder tijd nodig heeft om zoekbewerkingen uit te voeren.
* De inhoudprovider kan de inhoud sturen die door specifieke categorieën gebruikers moet worden bekeken.
* De regels kunnen worden bepaald om inhoud te leveren die op combinaties van zowel gebruikerskenmerken als gedrag wordt gebaseerd. Dit biedt een geavanceerd mechanisme voor het personaliseren van hun webervaring.

Houd rekening met het volgende wanneer u personalisatie gebruikt:

#### Prestaties {#performance}

* Natuurlijk heeft de extra analyse en evaluatie gevolgen voor de prestaties. De gebruikte methoden zijn echter zeer geavanceerd en kunnen worden geoptimaliseerd om de impact tot een minimum te beperken.

#### Toestemming {#authorization}

* Voor personalisatie is een aanmeldingsmechanisme vereist, omdat de website de gebruiker moet kunnen identificeren.

#### Caching {#caching}

* Caching is een aspect dat de gebruiker in termen van prestaties en nauwkeurigheid zal zien - hoe snel levert de website gepersonaliseerde inhoud, en is het altijd huidig.
* Het in cache plaatsen is een belangrijke overweging bij het configureren van de personalisatie en de tijd moet in acht worden genomen om ervoor te zorgen dat de juiste implementatie wordt gebruikt.

>[!TIP]
>
>Het effect van de aanpassing op prestaties en verwante in het voorgeheugen onderbrengende onderwerpen worden verder besproken in het document [Optimalisatie van prestaties.](/help/sites-deploying/configuring-performance.md)

#### Nauwkeurigheid van de regels {#accuracy}

* Personalisatie die wordt gerealiseerd door het gedrag van de gebruiker te volgen, of regels te plaatsen die op het profiel van de gebruiker worden gebaseerd, moet nauwkeurig en logisch zijn.
* Er is niets frustrerender voor de gebruiker dan het hebben van inhoud gedwongen op, of ontkend aan, hen wegens de onnauwkeurige logica van een regel.
* Daarom moeten de regels goed doordacht zijn - met de eisen van de gebruiker op de voorgrond. Dit kan veel moeite kosten en mag niet onderschat worden; het definiëren van de bedrijfsregels weegt vaak zwaarder dan de technische inspanning bij het implementeren van personalisatie.

#### Wanneer gebruiken {#when-to-use}

* Zoals vele eigenschappen op het Web, zou de verpersoonlijking met zorg moeten worden gebruikt. Zal het gebruik ervan de gebruiker echt ten goede komen? moet altijd de eerste overweging zijn - of dat het gewenste doel met minder moeite met een andere methode kan worden bereikt. Personalisatie kan het risico lopen om een eigenschap te zijn die de gebruikers één keer (om te zien hoe het werkt) en slechts één keer vormen - aangezien het hen geen echte voordelen brengt.
* Personalisatie is alleen zinvol wanneer de inhoud dynamisch is, op een of andere manier afhankelijk van de gebruiker. Als alle gebruikers de zelfde inhoud zien, dan is de verpersoonlijking overtollig.

#### Vertrouwelijkheid {#confidentiality}

* Veel gebruikers maken zich zorgen over gegevensbescherming en beveiliging. Met name gegevens die worden opgehaald bij het volgen van hun gedrag bij surfen op het web.

## Personalisatie en toegang {#personalization-and-access}

Personalisatie moet los van toegangscontrole worden beschouwd, maar heeft wel een onderlinge relatie.

Personalisatie zelf leidt tot geen vorm van toegangscontrole. Het is eenvoudig een manier om te sturen wat de gebruiker ziet; het beperkt de gebruiker niet om tot andere inhoud toegang te hebben en zoals met om het even welke inhoud, moeten zij de correcte toegangscontroles reeds toegewezen hebben.

Nochtans, kan de toegangscontrole worden gebruikt om een vorm van verpersoonlijking tot stand te brengen. Als u een gebruiker toegang tot inhoud toestaat of ontkent, beïnvloedt dit onvermijdelijk de keus van inhoud die zij beschikbaar hebben - zo personaliserend hun Web-ervaring.

## Componenten beschikbaar voor personalisatie {#components-available-for-personalization}

Diverse componenten worden voorzien van AEM voor verpersoonlijking. Sommige gebruikers kunnen zich aanmelden en hun profielen bewerken, andere (zoals Mijn Gadgets) kunnen gebruikers een specifieke pagina configureren:

| Titel in Sidekick | Doel |
|---|---|
| Veld voor gecontroleerd wachtwoord | Verzoekt om wachtwoord en bevestiging van wachtwoord. |
| Gecombineerde aanmelding | Hiermee kan de gebruiker zich aanmelden bij een bestaande account of zich aanmelden voor een nieuwe account. |
| Forms-adresveld | Een complex veld waarmee een internationaal adres kan worden ingevoerd. |
| Forms beginnen | Hiermee wordt een formulierdefinitie gestart |
| Forms Captcha | Een veld dat bestaat uit een alfanumeriek woord dat automatisch wordt vernieuwd. De component captcha beschermt websites tegen bots. |
| Forms Checkbox-groep | Meerdere items die zijn ingedeeld in een lijst en worden voorafgegaan door selectievakjes. Gebruikers kunnen meerdere selectievakjes selecteren. |
| Forms-vervolgkeuzelijst | Meerdere items die zijn ingedeeld in een vervolgkeuzelijst. Met de schakeloptie Multi Selectable wordt opgegeven of verschillende elementen in de lijst kunnen worden geselecteerd. |
| Forms End | Hiermee wordt de formulierdefinitie beëindigd. |
| Forms-bestanden uploaden | An upload element that allows the user to upload a file to the server. |
| Verborgen Forms-veld | Dit veld wordt niet weergegeven aan de gebruiker. Het kan worden gebruikt om een waarde aan de cliënt en terug naar de server te vervoeren. Dit veld mag geen beperkingen hebben. |
| Forms-afbeeldingsknop | Een extra verzendknop voor het formulier dat als afbeelding wordt weergegeven. |
| Forms-wachtwoordveld | Hetzelfde als tekstveld, maar er is slechts één regel toegestaan en de tekstinvoer van de gebruiker is niet zichtbaar in het veld. |
| Forms-keuzerondje | Meerdere items die zijn ingedeeld in een lijst voorafgegaan door een keuzerondje. Gebruikers mogen slechts één keuzerondje selecteren. |
| Knop Forms verzenden | Een extra verzendknop voor het formulier waarvan de titel als tekst op de knop wordt weergegeven. |
| Forms-tekstveld | Tekstveld waarin gebruikers gegevens kunnen invoeren. |
| Mijn gadgets | Hiermee kunt u een van de beschikbare gadgets opnemen. |
| Profiel Avatar Photo | Hiermee wordt invoer van een Avatar-foto toegestaan. |
| Gedetailleerde naam profiel | Invoer van naamdetails, met inbegrip van elementen zoals titel, middelnaam en achtervoegsel indien nodig. |
| Weergavenaam profiel | Naam die moet worden weergegeven. |
| E-mailadres profiel | Invoer van een e-mailadres. |
| Profiel Geslacht | Hiermee kan het geslacht worden ingevoerd. |
| Primair telefoonnummer profiel | Hiermee wordt invoer van een telefoonnummer toegestaan. |
| Primaire URL profiel | Hiermee wordt invoer van een URL toegestaan. |
| Profiel algemene tekst, eigenschap | Profieleigenschappen. |
| Aanmelden | Hiermee kunt u een gebruikersnaam en wachtwoord opgeven wanneer u zich aanmeldt. |
| Afmelden | Hiermee wordt aangegeven welke gebruiker momenteel is aangemeld en krijgt u een koppeling naar het afmelden. |
| Cloud labelen | Een labelcloud waarmee een grafisch weergegeven selectie van tags op uw website wordt getoond |
| Teaser | Een stuk inhoud (gewoonlijk een beeld) die op een hoofdpagina wordt getoond om gebruikers tot de onderliggende inhoud &quot;te &quot;teweegbrengen&quot;. |

## Personalisatie en community-inhoud {#personalization-and-community-content}

Communautaire functies zoals blogs, forums en kalenders resulteren in het maken van inhoud van de gebruikersgemeenschap, die doorgaans UGC (door gebruikers gegenereerde inhoud) wordt genoemd. Wanneer UGC wordt ingevoerd in een publicatieomgeving die uit meerdere AEM bestaat (a [publicatiebedrijf](/help/communities/topologies.md)), was één belangrijke kwestie hoe te om UGC over alle instanties te synchroniseren.

Met [AEM Communities 6.1](/help/communities/overview.md) dit probleem is opgelost door een [gemeenschappelijke opslag voor UGC](/help/communities/working-with-srp.md). Wat personalisatie betreft, omvatten de Gemeenschappen [Sociale aanmelding](/help/communities/social-login.md) - de mogelijkheid voor bezoekers van de site om zich aan te melden bij Facebook en Twitter.

Zonder de uitbreiding van de Gemeenschappen zijn verschillende methodes om de kwestie van de consistentie van UGC te onderzoeken:

* Meerdere publicatie-instanties indien nodig synchroniseren
* De UGC vanuit de publicatie-instantie naar de auteursomgeving verzenden, vanwaar deze op vergelijkbare wijze kan worden gepubliceerd als pagina-inhoud

De methode die wordt gebruikt om UGC-consistentie te bereiken in een publicatieomgeving die uit meerdere publicatie-instanties bestaat, moet zorgvuldig worden ontworpen en getest op prestaties en consistentie.
