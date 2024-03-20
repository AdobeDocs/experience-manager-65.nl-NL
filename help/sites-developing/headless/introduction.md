---
title: Ontwikkeling zonder hoofd voor AEM 6.5 sites
description: Leer hoe AEM 6.5 krachtige mogelijkheden zonder kop, zoals Content Models, Content Fragments, en de GraphQL API samenwerken om u in staat te stellen uw ervaringen centraal te beheren en hen te dienen over kanalen.
exl-id: b6598bcf-b2ce-403a-87cf-6895fec8a91b
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Ontwikkeling zonder hoofd voor AEM 6.5 sites {#headless-development}

Leer hoe AEM 6.5 krachtige mogelijkheden zonder kop, zoals Content Models, Content Fragments, en de GraphQL API samenwerken om u in staat te stellen uw ervaringen centraal te beheren en hen te dienen over kanalen.

## Overzicht {#overview}

De implementatie zonder hoofd wordt steeds belangrijker om ervaringen aan uw publiek te kunnen bieden, waar ze zich ook bevinden en ongeacht het kanaal.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels en hybride oplossingen, en wordt de nadruk gelegd op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en hun levering over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![Implementatiemodellen AEM](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Dit document richt zich op het volledige implementatiemodel zonder kop van AEM. Nochtans, hoeft de kop versus de kop geen binaire keuze in AEM te zijn. U kunt de functies zonder koppen gebruiken om uw inhoud te beheren en aan verschillende eindpunten te leveren, terwijl u de auteurs van de inhoud ook in staat stelt toepassingen op één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [Hoofdletters en headless in AEM](/help/sites-developing/headful-headless.md) voor meer informatie .

## AEM 6.5 en zonder kop {#aem-headless}

AEM 6.5 is een flexibel instrument voor het model van de implementatie zonder kop door drie krachtige services aan te bieden:

1. Inhoudsmodellen
   * Inhoudsmodellen zijn een gestructureerde weergave van inhoud.
   * Deze worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   * Inhoudsmodellen dienen als basis voor inhoudsfragmenten.
1. Inhoudsfragmenten
   * Inhoudsfragmenten zijn instantiaties van inhoudsmodellen.
   * Deze worden gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * Ze worden opgeslagen in AEM Assets en beheerd in de interface voor middelenbeheer.
1. Inhoud-API voor levering
   * De AEM GraphQL API ondersteunt de levering van inhoudsfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * Directe levering van inhoud is ook mogelijk met de [JSON-export van Content Fragment Core Component.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)

## Uw eerste stappen met AEM zonder kop {#first-steps}

Er zijn verschillende bronnen beschikbaar waarmee u aan de slag kunt met AEM functies zonder kop. Ze zijn bedoeld voor verschillende gebruiksgevallen, maar bieden allemaal een stevig overzicht van AEM hoofdloze kenmerken.

| Bron | Beschrijving | Type | Publiek | Oost. Tijd |
|---|---|---|---|---|
| [Headless Developer Journey](/help/journey-headless/developer/overview.md) | **Voor gebruikers die nog niet zijn AEM en zonder kop** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door met uw eerste hoofdloze project te leven. | Hulplijn | Ontwikkelaars **nieuw tot AEM en zonder kop** | 1 uur |
| [Aan de slag met koploze gids](/help/sites-developing/headless/getting-started/introduction.md) | **Voor ervaren AEM** Voor een kort overzicht van de belangrijkste functies voor het AEM zonder kop, bekijkt u dit snelstartoverzicht. | Snel starten | Ontwikkelaars, beheerders **met AEM ervaring** | 20 minuten |
| [Aan de slag met AEM praktische zelfstudie zonder hoofd](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **Als u liever een praktische aanpak kiest en vertrouwd bent met AEM** Deze zelfstudie duikt rechtstreeks in het maken van een eenvoudig project zonder kop. | Zelfstudie | Ontwikkelaars | 2 uur |
| [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html) | Deze inning van middelen wordt zowel voor **new** en **ervaren** ontwikkelaars. | Inzameling van middelen | Ontwikkelaars | |
