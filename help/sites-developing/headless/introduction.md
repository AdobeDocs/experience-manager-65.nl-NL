---
title: Ontwikkeling zonder hoofd voor AEM 6.5 sites
description: Leer hoe AEM 6.5 krachtige mogelijkheden zonder kop, zoals Content Models, Content Fragments, en de GraphQL API samenwerken om u in staat te stellen uw ervaringen centraal te beheren en hen te dienen over kanalen.
exl-id: b6598bcf-b2ce-403a-87cf-6895fec8a91b
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Ontwikkeling zonder hoofd voor AEM 6.5 sites {#headless-development}

Leer hoe AEM 6.5 krachtige mogelijkheden zonder kop, zoals Content Models, Content Fragments, en de GraphQL API samenwerken om u in staat te stellen uw ervaringen centraal te beheren en hen te dienen over kanalen.

## Overzicht {#overview}

De implementatie zonder hoofd wordt steeds belangrijker om ervaringen aan uw publiek te kunnen bieden, waar ze zich ook bevinden en ongeacht het kanaal.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels en hybride oplossingen, en wordt de nadruk gelegd op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en hun levering over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![ AEM de Modellen van de Implementatie ](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Dit document richt zich op het volledige implementatiemodel zonder kop van AEM. Nochtans, hoeft de kop versus de kop geen binaire keuze in AEM te zijn. U kunt de functies zonder koppen gebruiken om uw inhoud te beheren en aan verschillende eindpunten te leveren, terwijl u de auteurs van de inhoud ook in staat stelt toepassingen op één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [ Kopieerbaar en Hoofdloos in AEM ](/help/sites-developing/headful-headless.md) voor meer informatie.

## AEM 6.5 en zonder kop {#aem-headless}

AEM 6.5 is een flexibel instrument voor het model van de implementatie zonder kop door drie krachtige services aan te bieden:

1. Inhoudsmodellen
   * Inhoudsmodellen zijn een gestructureerde weergave van inhoud.
   * Deze worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   * Inhoudsmodellen dienen als basis voor inhoudsfragmenten.
1. Inhoudsfragmenten
   * Inhoudsfragmenten zijn instantiaties van inhoudsmodellen.
   * Deze worden gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * Ze worden opgeslagen in AEM Assets en beheerd in de gebruikersinterface van Assets Admin.
1. Inhoud-API voor levering
   * De AEM GraphQL API ondersteunt de levering van inhoudsfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * De directe inhoudslevering is ook mogelijk met de [ uitvoer van JSON van de Component van de Component van het Fragment van de Inhoud.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)

## Uw eerste stappen met AEM zonder kop {#first-steps}

Er zijn verschillende bronnen beschikbaar waarmee u aan de slag kunt gaan met AEM functies zonder kop. Ze zijn bedoeld voor verschillende gebruiksgevallen, maar bieden allemaal een goed overzicht van AEM onbelangrijke kenmerken.

| Bron | Beschrijving | Type | Publiek | Oost. Tijd |
|---|---|---|---|---|
| [ Zwaardeloze Reis van de Ontwikkelaar ](/help/journey-headless/developer/overview.md) | **voor gebruikers nieuw aan AEM en headless** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door het gaan met uw eerste headless project leven. | Hulplijn | De ontwikkelaars **nieuw aan AEM en zonder kop** | 1 uur |
| [ Koploze Begonnen Gids ](/help/sites-developing/headless/getting-started/introduction.md) | **voor ervaren AEM gebruikers** die een korte samenvatting van de belangrijkste AEM zonder kop eigenschappen nodig hebben, controleer dit snelle beginoverzicht. | Snel starten | De ontwikkelaars, Beheerders **met AEM ervaring** | 20 minuten |
| [ Begonnen het worden met AEM Hoofdloze hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) | **als u een hands-on benadering verkiest en met AEM** vertrouwd bent, duikt dit leerprogramma direct in het creëren van een eenvoudig headless project. | Zelfstudie | Ontwikkelaars | 2 uur |
| [ AEM het Portaal van de Ontwikkelaar ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html) | Deze inzameling van middelen wordt verstrekt voor zowel **nieuwe** als **ervaren** ontwikkelaars. | Inzameling van middelen | Ontwikkelaars | |
