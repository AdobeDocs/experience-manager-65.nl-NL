---
title: De testcase definiëren
description: Uw testgevallen moeten gebaseerd zijn op de gebruiksgevallen en de gedetailleerde specificaties van de eisen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
exl-id: c09cde0d-401c-437f-9ec8-a0530c1312d5
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# De testcase definiëren{#defining-your-test-cases}

Uw testgevallen moeten zijn gebaseerd op:

**Gevallen van het Gebruik**

* Deze definiëren de vereiste functionaliteit in termen van de interactie tussen de actoren (rollen die bepaalde handelingen initiëren) en het systeem.
* De gebruiksscenario&#39;s moeten door de klant worden gedefinieerd.

**Gedetailleerde Specificatie van Vereisten**

* Alle functionele en prestatie-eisen moeten worden getest.

De tests moeten duidelijk omschrijven:

* Vereisten; deze kunnen specifieke systemen, configuraties, of testervaring behandelen.
* Te volgen stappen, op een passend detailniveau.
* Verwachte resultaten.
* Duidelijke criteria voor slagen of zakken.

Het vooruitzicht om testgevallen te automatiseren is aantrekkelijk omdat het herhalende taken elimineert.

## Handmatige en geautomatiseerde tests {#manual-versus-automated-tests}

Het automatiseren van testgevallen is echter een belangrijke investering, dus moeten bepaalde aspecten in overweging worden genomen:

* Vereis tijd, inspanning, en ervaring aan opstelling en vorm.
* Als browser wordt gebaseerd, is er een verhoogd risico op problemen wanneer browser updates worden geïnstalleerd; het vereisen van verdere tijd om te verbeteren.
* Alleen haalbaar voor grote projecten.
* Goed als er meerdere releases worden gegenereerd voor tests of in het langetermijnreleaseplan.

## Specifieke aspecten testen {#testing-specific-aspects}

Bij het testen van AEM zijn enkele specifieke details van bijzonder belang:

**Auteur en de Milieu&#39;s van Publish**

Hoewel behandeld in [ Milieu ](/help/sites-developing/the-basics.md#environments), is het de moeite waard het benadrukken van een beslissende factor van AEM betreffende het testen.

AEM twee toepassingen:

* het *milieu van de Auteur*
Met deze instantie kunnen auteurs inhoud invoeren en publiceren.
Dit heeft een kleine (er), voorspelbare reeks gebruikers, voor wie specifieke functionaliteit en prestaties cruciaal zijn.

* het *milieu van Publish*
Dit exemplaar presenteert de website in zijn gepubliceerde vorm voor toegang van bezoekers.
Dit heeft gewoonlijk een grotere reeks gebruikers, waar het volume van verkeer niet altijd 100% voorspelbaar is. Prestaties zijn nog steeds van cruciaal belang - bij het beantwoorden van verzoeken. Overweeg ook caching en lading-in evenwicht brengen.

Alhoewel dezelfde software als dusdanig:

* verschillende doeleinden dienen
* verschillende eisen inzake functionaliteit en prestaties hebben
* zijn verschillend gevormd
* afzonderlijk worden afgebeeld
* elk heeft zijn eigen reeks goedkeuringstests

Met andere woorden, zij moeten afzonderlijk en met verschillende testgevallen worden getest.

**Personalization**

Wanneer het testen van verpersoonlijking elk individueel gebruiksgeval zou moeten worden herhaald gebruikend veelvoudige gebruikersrekeningen om gedrag te bewijzen.

Schakel het in cache plaatsen ook in voor het juiste gedrag.

**Dispatcher**

De meeste projecten installeren de Dispatcher voor caching en lading het in evenwicht brengen.

Testen is moeilijk (caching vindt plaats op verschillende niveaus en op verschillende locaties) en moet gebeuren op basis van een zwarte doos. De belangrijkste aspecten waarop u wilt testen zijn:

* **Nauwkeurigheid**
Hiermee zorgt u ervoor dat de bijgewerkte inhoud door de websitebezoeker wordt bekeken.

* **Continuïteit**
Zorg ervoor dat de website nog steeds beschikbaar is wanneer één server wordt afgesloten.

* **Clusters**
Wordt gebruikt om het volgende op te geven:

   * **Failover**
Als één server uitvalt, nemen andere servers in de cluster de verwerking over.

   * **Prestaties**
Het in evenwicht brengen van de lading met volledige failover verhoogt de prestaties van een cluster.
Wanneer gebruikt voor een klantenproject moet de cluster worden getest om correcte verrichting van de configuratie te bevestigen.

## Software van derden testen {#testing-third-party-software}

Eventuele software van derden die aan AEM is gekoppeld, wordt vermeld in de gedetailleerde specificaties voor de vereisten.

Eventuele vereiste tests (afhankelijk van het vastgestelde bereik) moeten worden geanalyseerd en er moet een schone test worden uitgevoerd.
