---
title: Teasers en strategieën
seo-title: Teasers en strategieën
description: Campagnes gebruiken vaak theaters als een mechanisme om een specifiek segment van de bezoekersbevolking door te zetten tot inhoud die op hun belangen is gericht. Een of meer theaters zijn gedefinieerd voor een specifieke campagne.
seo-description: Campagnes gebruiken vaak theaters als een mechanisme om een specifiek segment van de bezoekersbevolking door te zetten tot inhoud die op hun belangen is gericht. Een of meer theaters zijn gedefinieerd voor een specifieke campagne.
uuid: c78ec858-4b0a-48d5-99b2-5ddd9e15183d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 7f378b94-5233-4358-8d93-a7b3386df00b
docset: aem65
translation-type: tm+mt
source-git-commit: dc1985c25c797f7b994f30195d0586f867f9b3ee

---


# Teasers en strategieën{#teasers-and-strategies}

Campagnes gebruiken vaak theaters als een mechanisme om een specifiek segment van de bezoekersbevolking door te zetten tot inhoud die op hun belangen is gericht. Een of meer theaters zijn gedefinieerd voor een specifieke campagne.

>[!NOTE]
>
>De component Teaser is afgekeurd in AEM 6.2. Gebruik in plaats hiervan de [doelcomponent](/help/sites-authoring/content-targeting-touch.md) .

* **Merkpagina** &#39;s worden opgeslagen in de sectie Campagnes van de website. Een merk bevat de afzonderlijke campagnes.
* **Campagnepagina** &#39;s worden opgeslagen in de sectie Campagnes van de website. Elke campagne heeft een afzonderlijke pagina waarop de teasdefinities staan. De container, of overzichtspagina, bevat ook bepaalde informatie en statistieken over de afzonderlijke laserpagina&#39;s.

Teasers binnen AEM bestaan uit verschillende onderdelen:

* **De teaspagina** &#39;s worden opgeslagen onder de aangewezen campagnepagina en houden de definities van de teasparagrafen beschikbaar voor elke specifieke campagne. Deze definities worden gebruikt bij de weergave van de laseralinea&#39;s; inclusief variaties in de inhoud, het segment dat moet worden gebruikt voor het selecteren van een variatie- en versterkingsfactor.
* De component **** Taser is beschikbaar in het vak en u kunt een instantie van de specifieke tasalinea in een inhoudspagina maken. U kunt de lasercomponent van het hulpstuk slepen, dan uw teasdefinitie specificeren om uw eigen teasparagraaf tot stand te brengen. **** Opmerking:De component Teaser is afgekeurd in AEM 6.2. Gebruik in plaats hiervan de [doelcomponent](/help/sites-authoring/content-targeting-touch.md) .
* **Taseralinea** &#39;s zijn de werkelijke instanties van het gummetje in een inhoudspagina. Deze maken een deel van de bezoekers bekend met inhoud die op hun belangen is toegespitst.
* Pagina&#39;s die de inhoud van de campagne bevatten, hebben de focus op een specifiek bezoekerssegment. Doorgaans leiden de laseralinea&#39;s de bezoeker naar dergelijke pagina&#39;s.

## Strategieën {#strategies}

Wanneer u een laseralinea toevoegt aan een pagina, moet u de **strategie** definiëren.

Dit is voor het geval dat verscheidene tellers voor selectie beschikbaar zijn aangezien hun toegewezen segmenten allen met succes oplossen. De **Strategie** specificeert dan een extra criteria die worden gebruikt om het getoonde meetapparaat te selecteren:

* **De klikstreaming Score**, is gebaseerd op de markeringen en de verwante markeringstreffers die binnen de cliëntcontext van de bezoeker worden gehouden (toon hoe vaak een bezoeker op pagina&#39;s heeft geklikt die de respectieve markering bevatten). De snelheden voor tags die op de teaspagina zijn gedefinieerd, worden vergeleken.
* **Willekeurig**, voor &quot;willekeurige&quot; selectie; Gebruikt de willekeurige factor die voor een pagina wordt gegenereerd, dit is te zien bij de [clientcontext](/help/sites-administering/client-context.md).
* **Eerst** in de lijst van opgeloste segmenten. De volgorde is die van de trapsgewijze elementen op de pagina met de campagneccontainer.

De [factor](/help/sites-administering/campaign-segmentation.md#boost-factor) Verhogen van het segment heeft ook een effect op de selectie. Dit is een wegingsfactor die aan een segmentdefinitie wordt toegevoegd om de relatieve waarschijnlijkheid van selectie te vergroten/verkleinen.

Het proces en de onderlinge relaties van de verschillende selectiecriteria kunnen het best worden geïllustreerd met een voorbeeld (een methode die ook kan worden gebruikt om ervoor te zorgen dat uw theers het vereiste publiek zullen bereiken).

Als de volgende segmenten reeds zijn gecreeerd en hun respectieve Factor van de Verhoging toegewezen:

| Segment | Verhoging factor |
|---|---|
| S1 | 0 |
| S2 | 0 |
| S3 | 10 |
| S4 | 30 |
| S5 | 0 |
| S6 | 100 |

En wij gebruiken de volgende teasdefinities:

<table>
 <tbody>
  <tr>
   <td>Campagne</td>
   <td>Teaser</td>
   <td>Toegewezen segment</td>
   <td>Toegewezen labels </td>
  </tr>
  <tr>
   <td>C1</td>
   <td>T1</td>
   <td>S1, S2</td>
   <td>Zakelijk, marketing</td>
  </tr>
  <tr>
   <td>C1</td>
   <td>T2 </td>
   <td>S1</td>
   <td><br /> </td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T3</td>
   <td>S3, S4</td>
   <td><br /> </td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T4</td>
   <td>S2, S5</td>
   <td><br /> </td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T5</td>
   <td>S1, S2, S6</td>
   <td>Marketing</td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T6</td>
   <td>S6</td>
   <td>Zakelijk<br /> </td>
  </tr>
 </tbody>
</table>

Als we dit vervolgens toepassen op een bezoeker waar:

* **S1**, **S2** en **S6** slagen erin

* de tag **marketing** heeft 3 hits
* de tag **business** heeft 6 treffers

We zien het resultaat:

* succes van overeenkomst - los om het even welke segmenten die aan het meetapparaat worden toegewezen met succes voor de huidige bezoeker op?
* versterkingsfactor - de hoogste versterkingsfactor van alle toepasselijke segmenten
* clickstream-score - het cumulatieve totaal voor alle toepasselijke tagtreffers

die worden berekend voordat de passende strategie wordt toegepast:

<table>
 <tbody>
  <tr>
   <td>Campagne</td>
   <td>Teaser</td>
   <td>Toegewezen segment</td>
   <td>Tags </td>
   <td>Succesvolle overeenkomst?</td>
   <td>Resulterende boostfactor</td>
   <td>Resulterende Clickstream-score </td>
  </tr>
  <tr>
   <td>C1</td>
   <td>T1</td>
   <td>S1, S2</td>
   <td>Zakelijk, marketing</td>
   <td>Ja</td>
   <td>0</td>
   <td>9</td>
  </tr>
  <tr>
   <td>C1</td>
   <td>T2 </td>
   <td>S1</td>
   <td><br /> </td>
   <td>Ja</td>
   <td>0</td>
   <td><br /> </td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T3</td>
   <td>S3, S4</td>
   <td><br /> </td>
   <td>Nee</td>
   <td><br /> </td>
   <td><br /> </td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T4</td>
   <td>S2, S5</td>
   <td><br /> </td>
   <td>Ja<br /> </td>
   <td>0<br /> </td>
   <td><br /> </td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T5</td>
   <td>S1, S2, S6</td>
   <td>Marketing</td>
   <td>Ja</td>
   <td>100</td>
   <td>3</td>
  </tr>
  <tr>
   <td>C1 </td>
   <td>T6</td>
   <td>S6</td>
   <td>Zakelijk</td>
   <td>Ja</td>
   <td>100</td>
   <td>6 </td>
  </tr>
 </tbody>
</table>

Deze waarden worden gebruikt om de taser(s) te bepalen die de bezoeker ziet, afhankelijk van de **strategie** die op de teasalinea wordt toegepast:

<table>
 <tbody>
  <tr>
   <td>Strategie</td>
   <td>Resulterende taser</td>
   <td>Opmerkingen</td>
  </tr>
  <tr>
   <td>Eerste</td>
   <td>T5</td>
   <td>Alleen T5 en T6 worden beschouwd als de segmenten die ze allemaal oplossen <i>en hebben</i> de hoogste stimulerende factor. De geretourneerde lijst staat in de volgorde T5, T6. zodat T5 wordt geselecteerd en getoond.</td>
  </tr>
  <tr>
   <td>Willekeurig</td>
   <td>T5 of T6</td>
   <td>Beide teasers hebben segmenten die alle oplossen en de zelfde verhogingsfactor. Daarom worden de twee theelmeters in gelijke verhouding weergegeven.</td>
  </tr>
  <tr>
   <td>Clikstream score</td>
   <td>T6</td>
   <td><p>Segmenten voor T1, T4, T5 en T6 worden allemaal opgelost voor de bezoeker. De hogere stimulerende factoren van T5 en T6 sluiten vervolgens T1 en T4 uit. Tot slot resulteert de hogere Score van de ClikStream van T6 in het selecteren van dit.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Als er na de bovenstaande resolutietechnieken meerdere teasers beschikbaar zijn voor selectie, wordt met een interne selectie (willekeurig) één teaser voor weergave geselecteerd.
>
>Als de strategie bijvoorbeeld Clickstream Score was en T5 dezelfde Clickstream Score had als T6 (d.w.z. 6 in plaats van 3), zou de interne selectie (willekeurig) worden gebruikt om een van deze twee te selecteren.

Taserpagina&#39;s/alinea&#39;s worden gebruikt om bepaalde bezoekerssegmenten te sturen naar inhoud die op hun belangen is toegespitst. Zij kunnen een waaier van opties voor de bezoeker voorstellen om van te kiezen, of slechts één teaser paragraaf tonen die op het specifieke bezoekerssegment gebaseerd is; zo kan de getoonde laseralinea afhankelijk zijn van de leeftijd van de bezoeker .

Een laserpagina is doorgaans een tijdelijke actie die een bepaalde periode duurt, totdat deze wordt vervangen door de volgende laserpagina.

Nadat u uw merk en campagne hebt gemaakt, kunt u uw taservaring maken en instellen.

### Een aanraakpunt voor uw taser maken {#creating-a-touchpoint-for-your-teaser}

>[!NOTE]
>
>De component Teaser is afgekeurd in AEM 6.2. Gebruik in plaats hiervan de [doelcomponent](/help/sites-authoring/content-targeting-touch.md) .

1. Navigeer naar de inhoudspagina waar u de tasalinea wilt plaatsen die tot uw campagnepagina zal leiden.
1. Voeg een **Taser** -component (beschikbaar in de sectie **Personalisatie** van sidekick) toe op de gewenste positie. Wanneer eerst gecreeerd zal het tonen dat de campagneweg nog niet wordt gevormd:

   ![chlimage_1](assets/chlimage_1.png)

1. Bewerk de lasercomponent om het volgende toe te voegen:

   * **Pad** naar campagnepad naar de campagnepagina die de afzonderlijke teaspagina bevat; De segmenten bepalen precies welke teaser wordt getoond.

   * **[Strategie](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#strategies)**Methode die voor selectie wordt gebruikt wanneer de veelvoudige segmenten met succes oplossen.
   ![chlimage_1-1](assets/chlimage_1-1.png)

1. Klik op **OK** om op te slaan. Afhankelijk van de segmenten die u hebt ingesteld op het taser en het profiel van de gebruiker die u momenteel als gebruiker bent aangemeld, wordt de juiste inhoud weergegeven:

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. Plaats de muisaanwijzer op de alinea met het gereedschap Taser om het pictogram van het vraagteken weer te geven (rechteronderhoek van de component). Klik op deze optie om de toegepaste segmenten weer te geven en of deze momenteel worden omgezet.

   ![chlimage_1-3](assets/chlimage_1-3.png)

### Teaseroverzicht {#teaser-overview}

Naast de campagneweergave in de MCM bevat de campagnepagina ook informatie over de bijbehorende traders:

1. Open vanuit de **websiteconsole** de campagnepagina. bijvoorbeeld:

   `https://localhost:4502/content/campaigns/geometrixx-outdoors/storefront/summer.html`

   Hier ziet u een overzicht van de definities van de teaser en de weergavestatistieken:

   ![chlimage_1-4](assets/chlimage_1-4.png)
