---
title: Segmentatie configureren
description: Leer hoe te om segmentatie voor AEM Campagne te vormen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 6d759907-8796-4749-bd80-306ec7f2c819
solution: Experience Manager, Experience Manager Sites
feature: Administering,Personalization
role: Admin
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---


# Segmentatie configureren {#configuring-segmentation}

>[!NOTE]
>
>Dit document behandelt de configuratie van segmentatie zoals die met de Context van de Cliënt wordt gebruikt. Om segmenten met ContextHub te vormen gebruikend aanraking UI, zie [&#x200B; het Vormen Segmentatie met ContextHub &#x200B;](/help/sites-administering/segmentation.md).

Segmentering is een belangrijke overweging bij het maken van een campagne. Zie [&#x200B; verklarende woordenlijst van de Segmentatie &#x200B;](/help/sites-authoring/segmentation-overview.md) voor informatie over hoe de segmentatie en zeer belangrijke termijnen werkt.

Afhankelijk van de informatie die u reeds over uw plaatsbezoekers en de doelstellingen hebt verzameld u wilt bereiken, moet u de segmenten en de strategieën bepalen nodig voor uw gerichte inhoud.

Deze segmenten worden vervolgens gebruikt om een bezoeker specifieke inhoud te bieden. Deze inhoud wordt gehandhaafd in de [&#x200B; Campagnes &#x200B;](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md) sectie van de website. De hier gedefinieerde taserpagina&#39;s kunnen als taseralinea&#39;s op elke pagina worden opgenomen en definiëren voor welk bezoekerssegment de gespecialiseerde inhoud van toepassing is.

Met AEM kunt u eenvoudig segmenten, theers en campagnes maken en bijwerken. Ook kunt u de resultaten van uw definities controleren.

De **Redacteur van het Segment** laat u gemakkelijk een segment bepalen:

![&#x200B; het venster van de Redacteur van het Segment &#x200B;](assets/segmenteditor.png)

U kunt **uitgeven** elk segment om a **Titel**, **Beschrijving** en **factor van de Verhoging** te specificeren. Gebruikend sidekick kunt u **EN** en **OF** containers toevoegen om de **Logica van het Segment** te bepalen, dan de vereiste **Begeleidingen van het Segment** toe te voegen om de selectiecriteria te bepalen.

## Verhoging van factor {#boost-factor}

Elk segment heeft a **&#x200B;**&#x200B;parameter van de Verhoging die als wegingsfactor wordt gebruikt; een hoger aantal wijst erop dat het segment in voorkeur aan een segment met een lager aantal zal worden geselecteerd.

* Minimumwaarde: `0`
* Maximumwaarde: `1000000`

## Segmentlogica {#segment-logic}

De volgende logische containers zijn beschikbaar uit-van-de-doos en laten u de logica van uw segmentselectie construeren. Ze kunnen van het hulpwerktuig naar de editor worden gesleept:

<table>
 <tbody>
  <tr>
   <td> EN Container <br /> </td>
   <td> De booleaanse operator AND.<br /> </td>
  </tr>
  <tr>
   <td> OF Container <br /> </td>
   <td> De Booleaanse operator OR.</td>
  </tr>
 </tbody>
</table>

## Segmentsporen {#segment-traits}

De volgende segmentkenmerken zijn beschikbaar buiten het vak; ze kunnen van het hulpstuk naar de editor worden gesleept:

<table>
 <tbody>
  <tr>
   <td> IP-bereik <br /> </td>
   <td>Bepaalt een waaier van IP adressen die de bezoeker kan hebben.<br /> </td>
  </tr>
  <tr>
   <td> Paginahits <br /> </td>
   <td>Hoe vaak is de pagina aangevraagd. <br /> </td>
  </tr>
  <tr>
   <td> Pagina-eigenschap <br /> </td>
   <td>Om het even welk bezit van de bezochte pagina.<br /> </td>
  </tr>
  <tr>
   <td> Referral-trefwoorden <br /> </td>
   <td>Trefwoorden die overeenkomen met gegevens van de verwijzende website. <br /> </td>
  </tr>
  <tr>
   <td> Script</td>
   <td>Te evalueren JavaScript-expressie.<br /> </td>
  </tr>
  <tr>
   <td> Segmentverwijzing <br /> </td>
   <td>Verwijzing naar een andere segmentdefinitie.<br /> </td>
  </tr>
  <tr>
   <td> Cloud labelen <br /> </td>
   <td>Tags die moeten overeenkomen met de tags van de bezochte pagina's.<br /> </td>
  </tr>
  <tr>
   <td> Leeftijd gebruiker <br /> </td>
   <td>Zoals overgenomen uit het gebruikersprofiel.<br /> </td>
  </tr>
  <tr>
   <td> Eigenschap gebruiker <br /> </td>
   <td>Alle andere informatie die beschikbaar is in het gebruikersprofiel. </td>
  </tr>
 </tbody>
</table>

U kunt deze eigenschappen combineren gebruikend de booleaanse exploitanten OF EN (zie [&#x200B; Creërend een Nieuw Segment &#x200B;](#creating-a-new-segment)) om het nauwkeurige scenario te bepalen voor het selecteren van dit segment.

Wanneer de volledige verklaring aan waar evalueert dan heeft dit segment opgelost. Als er veelvoudige toepasselijke segmenten zijn, dan wordt de **[1&rbrace; factor van de Verhoging &lbrace;ook gebruikt.](/help/sites-administering/campaign-segmentation.md#boost-factor)**

>[!CAUTION]
>
>De segmentredacteur controleert geen cirkelverwijzingen. Zo verwijst segment A bijvoorbeeld naar een ander segment B, dat op zijn beurt naar segment A verwijst. Zorg ervoor dat de segmenten geen cirkelverwijzingen bevatten.

>[!NOTE]
>
>Eigenschappen met het achtervoegsel **_i18n** worden geplaatst door een manuscript dat een deel van UI clientlib van de verpersoonlijking is. Alle UI-gerelateerde clientlibs worden alleen op de auteur geladen omdat de gebruikersinterface niet nodig is bij publiceren.
>
>Daarom wanneer het creëren van een segment met dergelijke eigenschappen is het normaal noodzakelijk om op **browserFamily** voor instantie in plaats van **browserFamily_i18n** te vertrouwen.

### Een nieuw segment maken {#creating-a-new-segment}

Het nieuwe segment definiëren:

1. In het spoor, kies **Hulpmiddelen > Verrichtingen > Configuratie**.
1. Klik op de **pagina van de Segmentatie** in de linkerruit, en navigeer aan de vereiste plaats.
1. Creeer a [&#x200B; nieuwe pagina &#x200B;](/help/sites-authoring/editing-content.md#creatinganewpage) gebruikend het **malplaatje van het Segment**.
1. Open de nieuwe pagina om de segmenteditor weer te geven:

   ![&#x200B; de eerste stap van het creëren van een segment in de Redacteur van het Segment &#x200B;](assets/screen_shot_2012-02-02at101726am.png)

1. Gebruik of sidekick of contextmenu (gewoonlijk klik met de rechtermuisknop aan muisknoop, dan uitgezocht **Nieuw...** om het venster van de Component van het Tussenvoegsel te openen) om het segmentspoor te vinden u wenst. Dan sleep het aan de **Redacteur van het Segment** het in het gebrek **EN** container zal verschijnen.
1. Dubbelklik op de nieuwe eigenschap om de specifieke parameters te bewerken, bijvoorbeeld de muispositie:

   ![&#x200B; Uitgevend een component in de Redacteur van het Segment &#x200B;](assets/screen_shot_2012-02-02at103135am.png)

1. Klik **O.K.** om uw definitie te bewaren:
1. U kunt **&#x200B;**&#x200B;de segmentdefinitie uitgeven om het a **Titel**, **Beschrijving** en **[factor van de Verhoging](#boost-factor)** te geven:

   ![&#x200B; Uitgevend de segmentmontages in de Redacteur van het Segment &#x200B;](assets/screen_shot_2012-02-02at103547am.png)

1. Voeg desgewenst meer kenmerken toe. U kunt booleaanse uitdrukkingen formuleren gebruikend **EN de Container** en **OF de componenten van de Container** die onder **Logica van het Segment** worden gevonden. Met de segmentredacteur kunt u eigenschappen of containers schrappen niet meer nodig, of hen slepen aan nieuwe posities binnen de verklaring.

### AND en OR-containers gebruiken {#using-and-and-or-containers}

U kunt complexe segmenten in AEM samenstellen. Het helpt om zich van een paar basispunten bewust te zijn:

* Het hoogste niveau van de definitie is altijd de EN container die aanvankelijk wordt gecreeerd; dit kan niet worden veranderd, maar heeft geen effect op de rest van uw segmentdefinitie.
* Zorg ervoor dat het nesten van de container zinvol is. De containers kunnen als steunen van uw booleaanse uitdrukking worden bekeken.

In het volgende voorbeeld worden bezoekers geselecteerd die:

Mannelijk en tussen 16 en 65 jaar

OF

Vrouwen tussen 16 en 62 jaar

Aangezien de belangrijkste exploitant OF is moet u met een **OF Container** beginnen. Binnen dit hebt u 2 EN verklaringen, voor elk van deze hebt u een **EN Container** nodig, waarin u de individuele eigenschappen kunt toevoegen.

![&#x200B; een voorbeeld van EN EN OF exploitanten in de Redacteur van het Segment &#x200B;](assets/screen_shot_2012-02-02at105145am.png)

## De toepassing van een segment testen {#testing-the-application-of-a-segment}

Zodra het segment is bepaald, kunnen de potentiële resultaten met de hulp van de **[Context van de Cliënt](/help/sites-administering/client-context.md)** worden getest:

1. Selecteer het segment dat u wilt testen.
1. Pers **[CTRL-alt-C](/help/sites-authoring/page-authoring.md#keyboardshortcuts)** om de **[Context van de Cliënt](/help/sites-administering/client-context.md)** te openen, die de gegevens toont die zijn verzameld. Voor testende doeleinden kunt u **bepaalde waarden uitgeven, of** laden **een ander profiel om het effect daar te zien.**

1. Afhankelijk van de gedefinieerde kenmerken komen de gegevens die beschikbaar zijn voor de huidige pagina mogelijk niet overeen met de segmentdefinitie. De status van de overeenkomst wordt onder de definitie weergegeven.

Een eenvoudige segmentdefinitie kan bijvoorbeeld gebaseerd zijn op de leeftijd en het geslacht van de gebruiker. Wanneer u een specifiek profiel laadt, wordt getoond dat het segment is opgelost:

![&#x200B; Gebruikend het venster van de Context van de Cliënt om een EN segmentatieverrichting &#x200B;](assets/screen_shot_2012-02-02at105926am.png) te testen

Of niet:

![&#x200B; Gebruikend het venster van de Context van de Cliënt om een NOT segmenteringsverrichting &#x200B;](assets/screen_shot_2012-02-02at110019am.png) te testen

>[!NOTE]
>
>Alle kenmerken worden onmiddellijk opgelost, maar de meeste wijzigingen worden alleen toegepast wanneer de pagina opnieuw wordt geladen. Wijzigingen in de muispositie zijn direct zichtbaar, zodat u ze kunt testen.

Dergelijke tests kunnen ook op inhoudspagina&#39;s en in combinatie met **de componenten van het Taser** worden uitgevoerd.

Bij de muisaanwijzer op een teasalinea worden de toegepaste segmenten weergegeven, ongeacht of deze momenteel zijn opgelost en waarom de huidige teaser-instantie is geselecteerd:

![&#x200B; een voorbeeldmuis over van een segment &#x200B;](assets/chlimage_1-47.png)

### Uw segment gebruiken {#using-your-segment}

De segmenten worden momenteel gebruikt binnen [&#x200B; Campagnes &#x200B;](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md). Ze worden gebruikt om de werkelijke inhoud te sturen die door specifieke doelgroepen wordt gezien. Zie [&#x200B; Begrip Segmenten &#x200B;](/help/sites-authoring/segmentation-overview.md) voor meer informatie.
