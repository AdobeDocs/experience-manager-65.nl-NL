---
title: Headless Development voor AEM 6.5 Sites
description: Leer hoe de krachtige mogelijkheden zonder kop van AEM 6.5, zoals Content Models, Content Fragments en de GraphQL API, samenwerken om u in staat te stellen uw ervaringen centraal te beheren en ze via verschillende kanalen te bedienen.
exl-id: b6598bcf-b2ce-403a-87cf-6895fec8a91b
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# Headless Development voor AEM 6.5 Sites {#headless-development}

Leer hoe de krachtige mogelijkheden zonder kop van AEM 6.5, zoals Content Models, Content Fragments en de GraphQL API, samenwerken om u in staat te stellen uw ervaringen centraal te beheren en ze via verschillende kanalen te bedienen.

## Overzicht {#overview}

De implementatie zonder hoofd wordt steeds belangrijker om ervaringen aan uw publiek te kunnen bieden, waar ze zich ook bevinden en ongeacht het kanaal.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels en hybride oplossingen, en wordt de nadruk gelegd op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en hun levering over het kanaal. Het is een modern en dynamisch ontwikkelingspatroon voor het implementeren van webervaringen.

![&#x200B; Modellen van de Implementatie van AEM &#x200B;](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

## Bezig met vergelijken van hoofdletters en hoofdletters {#headful-headless}

Dit document richt zich op het volledige implementatiemodel zonder kop van AEM. Maar kop versus kop hoeft geen binaire keuze te zijn in AEM. U kunt de functies zonder koppen gebruiken om uw inhoud te beheren en aan verschillende eindpunten te leveren, terwijl u de auteurs van de inhoud ook in staat stelt toepassingen op één pagina te bewerken. Alles in AEM.

>[!TIP]
>
>Zie het document [&#x200B; Kopieerbaar en Hoofdloos in AEM &#x200B;](/help/sites-developing/headful-headless.md) voor meer informatie.

## AEM 6.5 en headless {#aem-headless}

AEM 6.5 is een flexibel hulpmiddel voor het model van implementatie zonder kop door drie krachtige services aan te bieden:

1. Inhoudsmodellen
   * Inhoudsmodellen zijn een gestructureerde weergave van inhoud.
   * Deze worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model Editor.
   * Inhoudsmodellen dienen als basis voor inhoudsfragmenten.
1. Inhoudsfragmenten
   * Inhoudsfragmenten zijn instantiaties van inhoudsmodellen.
   * Deze worden gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   * Ze worden opgeslagen in AEM Assets en beheerd in de gebruikersinterface van Assets Admin.
1. Inhoud-API voor levering
   * De AEM GraphQL API ondersteunt de levering van inhoudsfragmenten.
   * De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   * De directe inhoudslevering is ook mogelijk met de [&#x200B; uitvoer van JSON van de Component van de Component van het Fragment van de Inhoud.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=nl-NL)

## Je eerste stappen met AEM Headless {#first-steps}

Er zijn verschillende bronnen beschikbaar waarmee u aan de slag kunt gaan met functies zonder koppen van AEM. Ze zijn bedoeld voor verschillende gebruiksgevallen, maar geven allemaal een goed overzicht van de AEM-functies zonder kop.

| Bron | Beschrijving | Type | Publiek | Oost. Tijd |
|---|---|---|---|---|
| [&#x200B; Zwaardeloze Reis van de Ontwikkelaar &#x200B;](/help/journey-headless/developer/overview.md) | **voor gebruikers nieuw aan AEM en headless** technologieën, begin hier voor een uitvoerige inleiding aan AEM en zijn headless eigenschappen van de theorie van headless door het gaan met uw eerste headless project leven. | Hulplijn | Ontwikkelaars **nieuw aan AEM en zonder kop** | 1 uur |
| [&#x200B; Koploze Begonnen Gids &#x200B;](/help/sites-developing/headless/getting-started/introduction.md) | **voor ervaren gebruikers van AEM** die een korte samenvatting van de belangrijkste eigenschappen van AEM nodig hebben, controleer dit snelle beginoverzicht. | Snel starten | De ontwikkelaars, Beheerders **met de ervaring van AEM** | 20 minuten |
| [&#x200B; Begonnen het worden met AEM Headless hands-on leerprogramma &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html?lang=nl-NL) | **als u een hands-on benadering verkiest en met AEM** vertrouwd bent, duikt dit leerprogramma direct in het creëren van een eenvoudig headless project. | Zelfstudie | Ontwikkelaars | 2 uur |
| [&#x200B; AEM Developer Portal &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL) | Deze inzameling van middelen wordt verstrekt voor zowel **nieuwe** als **ervaren** ontwikkelaars. | Inzameling van middelen | Ontwikkelaars | |
