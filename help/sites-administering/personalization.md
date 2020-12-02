---
title: Personalisatie
seo-title: Personalisatie
description: Meer informatie over personalisatie in AEM.
seo-description: Meer informatie over personalisatie in AEM.
uuid: 5790a3e0-f0ec-4785-b915-330a10dea30c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 03ebc494-8baa-4741-b8de-dac5ace743c8
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1684'
ht-degree: 0%

---


# Personalisatie{#personalization}

## Wat is personalisatie? {#what-is-personalization}

Er is een steeds groter volume aan inhoud beschikbaar vandaag, of het nu op Internet, Extranet, of Intranetwebsites is.

Personalisatie richt zich op het bieden van een op maat gemaakte omgeving waarin dynamische inhoud wordt weergegeven die op basis van hun specifieke behoeften is geselecteerd; Dit is op basis van vooraf gedefinieerde profielen, gebruikersselectie of interactief gebruikersgedrag.

Er zijn drie hoofdelementen betrokken bij personalisatie:

**Gebruikers**

* hebben profielen, zowel individueel als groep. Deze profielen bevatten kenmerken (zoals taakbeschrijving, locatie en interesses) die kunnen worden gebruikt om de inhoud die ze kunnen zien aan te passen.
* acties ondernemen. Deze kunnen vervolgens worden geanalyseerd en vergeleken met gedragsregels om de inhoud die ze zien aan te passen.

**Inhoud**

* is wat de gebruiker wil zien. Voorkeurelijk inhoud van belang en gebruik voor de vervulling van hun taken.
* kunnen worden ingedeeld en derhalve volgens vooraf gedefinieerde regels aan de gebruikers ter beschikking worden gesteld.moet dynamisch zijn; met andere woorden, de inhoud
* moet in zekere zin afhankelijk zijn van de gebruiker - als elke gebruiker dezelfde inhoud zou zien, dan zou personalisatie overtollig zijn.

**Regels**

* bepalen hoe verpersoonlijking eigenlijk gebeurt - welke inhoud de gebruiker kan zien, en wanneer.

Personalisatie kan:

**Expliciet**

* Aanpassing: waarbij de gebruiker selecties maakt van een keuze uit inhoudsbronnen.

**Impliciet**

* Gebaseerde regels: bedrijfsmanagers definiëren specifieke regels voor acties op basis van specifieke profielen en/of gedrag.
* Eenvoudig filteren: selecties worden gemaakt op basis van vooraf gedefinieerde profielen op gebruikers- en/of groepsniveau.
* Filteren op samenwerking/aanbevelingen: gebruikersgedrag wordt geregistreerd volgens vooraf gedefinieerde regels. Deze regels zijn gebaseerd op gedrag dat wordt waargenomen met gelijkgestemde individuen. De verzamelde informatie wordt gebruikt om de informatie aan de gebruiker te maken, met name in de vorm van aanbevelingen.

## Hoe en wanneer kan Personalisatie worden gebruikt? {#how-and-when-can-personalization-be-used}

Personalisatie kan in veel gevallen worden gebruikt, bijvoorbeeld:

**Intranetpagina&#39;s**

* Inhoud kan worden aangeboden op basis van de locatie, afdeling en/of rol van een gebruiker - al gedefinieerd binnen een intern netwerk.
* Afhankelijk van de beschikbare keuze kan de gebruiker meer selecties maken.

**Specifieke, beperkte, doelgebruikersgroepen (extranets)**

* De gebruikers vereisen login voor vergunning; dit wordt gekoppeld aan een profiel met informatie die nodig is voor personalisatie; eventueel nadere gegevens zoals de locatie, de relatie met het product, de gebruiksgeschiedenis, de budgettaire verantwoordelijkheden, enz.
* Dergelijke instanties kunnen zich uitstrekken over sites zoals:
* Bedrijven die websites aanbieden aan een zeer gespecialiseerde afdeling van hun markt, bijvoorbeeld een farmaceutische onderneming die een gespecialiseerde website voor artsen aanbiedt.
* Bedrijven die websites aanbieden waarmee hun klanten actuele account- en factureringsgegevens kunnen bekijken; bijvoorbeeld telefoonaanbieders.

**Website voor verkoop en distributie**

* Op verkoop- en distributiewebsites, zoals Amazon, kunnen een gebruikersprofiel, de verkoopgeschiedenis van de gebruiker en de browsergeschiedenis worden gecombineerd om suggesties te doen voor wat de gebruiker interesseert.

**Zoeken in websites**

* Veel van de belangrijkste websites van zoekprogramma&#39;s beschikken over zeer krachtige analytische instrumenten waarmee het gedrag van gebruikers, de zoektermen die ze gebruiken en de websites die ze bezoeken, worden vastgelegd. Dit wordt vervolgens gebruikt om de aangeboden inhoud aan te passen, met name wat betreft het weergeven van advertenties.

### Sterke punten van personalisatie en te overwegen punten {#strengths-of-personalization-and-points-to-consider}

De volgende redenen waarom personalisatie moet worden gebruikt:

* Een gebruiker kan een comfortabele, gerichte website ervaren.
* De verpersoonlijking kan worden gebruikt om toegang tot de recentste versie van inhoud automatisch te verspreiden.
* De functies voor sociale samenwerking zijn beschikbaar voor gebruikers om met elkaar te communiceren, zoals ze door hun profielen kunnen worden geïdentificeerd.
* Een gebruiker kan de inhoud krijgen die hij of zij nodig heeft om een bepaalde taak uit te voeren. Binnen het Intranet van een bedrijf kan dit een onschatbaar hulpmiddel verstrekken om informatie te verspreiden.
* Een gebruiker kan worden voorzien van de inhoud die hij of zij nodig heeft, waardoor hij of zij minder tijd nodig heeft om zoekbewerkingen uit te voeren.
* De inhoudprovider kan de inhoud sturen die door specifieke categorieën gebruikers moet worden bekeken.
* De regels kunnen worden bepaald om inhoud te leveren die op combinaties van zowel gebruikerskenmerken als gedrag wordt gebaseerd. Dit biedt een geavanceerd mechanisme voor het personaliseren van hun webervaring.

Houd rekening met het volgende wanneer u personalisatie gebruikt:

**Prestaties**

* Natuurlijk heeft de extra analyse en evaluatie gevolgen voor de prestaties. De gebruikte methoden zijn echter zeer geavanceerd en kunnen worden geoptimaliseerd om de impact tot een minimum te beperken.

**Toestemming**

* Voor personalisatie is een aanmeldingsmechanisme vereist, omdat de website de gebruiker moet kunnen identificeren.

**Caching**

* Caching is een aspect dat de gebruiker in termen van prestaties en nauwkeurigheid zal zien - hoe snel levert de website gepersonaliseerde inhoud, en is het altijd huidig.
* Het in cache plaatsen is een belangrijke overweging bij het configureren van de personalisatie en de tijd moet in acht worden genomen om ervoor te zorgen dat de juiste implementatie wordt gebruikt. Dit zal later nader worden besproken.

**Nauwkeurigheid van de regels**

* Personalisatie die wordt gerealiseerd door het gedrag van de gebruiker te volgen, of regels te plaatsen die op het profiel van de gebruiker worden gebaseerd, moet nauwkeurig en logisch zijn.
* Er is niets frustrerender voor de gebruiker dan het hebben van inhoud gedwongen op, of ontkend aan, hen wegens de onnauwkeurige logica van een regel.
* Daarom moeten de regels goed doordacht zijn - met de eisen van de gebruiker op de voorgrond. Dit kan veel moeite kosten en mag niet onderschat worden. het bepalen van de bedrijfsregels weegt vaak tegen de technische inspanning wanneer het uitvoeren van verpersoonlijking.

**Wanneer gebruiken**

* Zoals vele eigenschappen op het Web, zou de verpersoonlijking met zorg moeten worden gebruikt. Zal het gebruik ervan de gebruiker echt ten goede komen? moet altijd de eerste overweging zijn - of dat het gewenste doel met minder moeite met een andere methode kan worden bereikt. Personalisatie kan het risico lopen om een eigenschap te zijn die de gebruikers één keer (om te zien hoe het werkt) en slechts één keer vormen - aangezien het hen geen echte voordelen brengt.
* Personalisatie is alleen zinvol wanneer de inhoud dynamisch is, op een of andere manier afhankelijk van de gebruiker. Als alle gebruikers de zelfde inhoud zien, dan is de verpersoonlijking overtollig.

**Vertrouwelijkheid**

* Veel gebruikers maken zich zorgen over gegevensbescherming en beveiliging. Met name gegevens die worden opgehaald bij het volgen van hun gedrag bij surfen op het web.

## Personalisatie en toegang {#personalization-and-access}

Personalisatie moet los van toegangscontrole worden beschouwd, maar heeft wel een onderlinge relatie.

Personalisatie zelf leidt tot geen vorm van toegangscontrole. Het is gewoon een manier om te sturen wat de gebruiker ziet. het beperkt de gebruiker niet om tot andere inhoud toegang te hebben en zoals met om het even welke inhoud, moeten zij de correcte reeds toegewezen toegangscontroles hebben.

Nochtans, kan de toegangscontrole worden gebruikt om een vorm van verpersoonlijking tot stand te brengen. Als u een gebruiker toegang tot inhoud toestaat of ontkent, beïnvloedt dit onvermijdelijk de keus van inhoud die zij beschikbaar hebben - zo personaliserend hun Web-ervaring.

## Componenten beschikbaar voor personalisatie {#components-available-for-personalization}

Diverse componenten worden voorzien van AEM voor verpersoonlijking. Sommige gebruikers kunnen zich aanmelden en hun profielen bewerken, andere (zoals Mijn Gadgets) kunnen gebruikers een specifieke pagina configureren:

| Titel in Sidetrap | Doel |
|---|---|
| Veld voor gecontroleerd wachtwoord | Verzoekt om wachtwoord en bevestiging van wachtwoord. |
| Gecombineerde aanmelding | Hiermee kan de gebruiker zich aanmelden bij een bestaande account of zich aanmelden voor een nieuwe account. |
| Forms-adresveld | Een complex veld dat de invoer van een internationaal adres mogelijk maakt. |
| Forms beginnen | Hiermee wordt een formulierdefinitie gestart |
| Forms Captcha | Een veld dat bestaat uit een alfanumeriek woord dat automatisch wordt vernieuwd. De component captcha beschermt websites tegen bots. |
| Forms Checkbox-groep | Meerdere items die zijn ingedeeld in een lijst en worden voorafgegaan door selectievakjes. Gebruikers kunnen meerdere selectievakjes selecteren. |
| Forms-vervolgkeuzelijst | Meerdere items die zijn ingedeeld in een vervolgkeuzelijst. Met de schakeloptie Multi Selectable wordt opgegeven of verschillende elementen in de lijst kunnen worden geselecteerd. |
| Forms End | Hiermee wordt de formulierdefinitie beëindigd. |
| Forms-bestanden uploaden | An upload element that allows the user to upload a file to the server. |
| Verborgen Forms-veld | Dit veld wordt niet weergegeven aan de gebruiker. Het kan worden gebruikt om een waarde aan de cliënt en terug naar de server te vervoeren. Dit veld mag geen beperkingen hebben. |
| Forms-afbeeldingsknop | Een extra verzendknop voor het formulier dat als afbeelding wordt weergegeven. |
| Forms-wachtwoordveld | Hetzelfde als tekstveld, maar er is slechts één regel toegestaan en de tekstinvoer van de gebruiker is niet zichtbaar in het veld. |
| Forms-keuzerondje | Meerdere items die zijn ingedeeld in een lijst die wordt voorafgegaan door een keuzerondje. Gebruikers mogen slechts één keuzerondje selecteren. |
| Knop Forms verzenden | Een extra verzendknop voor het formulier waarvan de titel als tekst op de knop wordt weergegeven. |
| Forms-tekstveld | Tekstveld waarin gebruikers gegevens kunnen invoeren. |
| Mijn gadgets | Hiermee kunt u een van de beschikbare gadgets opnemen. |
| Profiel Avatar Photo | Hiermee wordt invoer van een Avatar-foto toegestaan. |
| Gedetailleerde naam profiel | Invoer van naamdetails, inclusief elementen zoals titel, middelnaam en achtervoegsel, indien vereist. |
| Weergavenaam profiel | Naam die moet worden weergegeven. |
| E-mailadres profiel | Invoer van een e-mailadres. |
| Profiel Geslacht | Hiermee kan het geslacht worden ingevoerd. |
| Primaire telefoonnummer van profiel | Hiermee wordt invoer van een telefoonnummer toegestaan. |
| Primaire URL profiel | Hiermee wordt invoer van een URL toegestaan. |
| Profiel algemene tekst, eigenschap | Profieleigenschappen. |
| Aanmelden | Hiermee kunt u een gebruikersnaam en wachtwoord opgeven wanneer u zich aanmeldt. |
| Afmelden | Hiermee wordt aangegeven welke gebruiker momenteel is aangemeld en krijgt u een koppeling naar het afmelden. |
| Cloud labelen | Een labelwolk om een grafisch weergegeven selectie van tags op uw website weer te geven |
| Teaser | Een stuk inhoud (gewoonlijk een beeld) die op een hoofdpagina wordt getoond om gebruikers tot de onderliggende inhoud &quot;te &quot;teweegbrengen&quot;. |

## Personalisatie en communautaire inhoud {#personalization-and-community-content}

Communautaire functies zoals blogs, forums en kalenders resulteren in het maken van inhoud van de gebruikersgemeenschap, die doorgaans UGC (door gebruikers gegenereerde inhoud) wordt genoemd. Wanneer UGC in een publicatiemilieu is ingegaan dat uit veelvoudige AEM instanties (a [publiceer landbouwbedrijf](/help/communities/topologies.md)) bestaat, is één belangrijke kwestie geweest hoe te om UGC over alle instanties te synchroniseren.

Met [AEM Communities 6.1](/help/communities/overview.md) uitbreiding, wordt dit probleem opgelost door een [gemeenschappelijke opslag voor UGC](/help/communities/working-with-srp.md) te gebruiken. Wat personalisatie betreft, bevatten de Community&#39;s [Sociale aanmelding](/help/communities/social-login.md) - de mogelijkheid voor bezoekers van de site om zich aan te melden bij Facebook en Twitter.

Zonder de uitbreiding van de Gemeenschappen zijn verschillende methodes om de kwestie van de consistentie van UGC te onderzoeken:

* Meerdere publicatieinstanties indien nodig synchroniseren
* de UGC van de publicatie-instantie naar de auteursomgeving verzenden, vanwaar deze op vergelijkbare wijze kan worden gepubliceerd als het publiceren van pagina-inhoud

De methode die wordt gebruikt om UGC-consistentie te bereiken in een publicatieomgeving die uit meerdere publicatie-instanties bestaat, moet zorgvuldig worden ontworpen en getest op prestaties en consistentie.
