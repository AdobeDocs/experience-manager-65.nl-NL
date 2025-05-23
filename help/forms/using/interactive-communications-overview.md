---
title: Interactieve communicatie - overzicht
description: Dit artikel bevat een overzicht, voorbeelden van gebruiksgevallen, de workflow voor het maken van ontwerpen en verschillen tussen interactieve communicatie en brief.
contentOwner: gtalwar
topic-tags: interactive-communications, introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6cfbeec0-0be3-48b2-a4bb-fd19c69c92c7
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 3%

---


# Interactieve communicatie - overzicht {#interactive-communications-overview}

Dit artikel bevat een overzicht, voorbeelden van gebruiksgevallen, de workflow voor het maken van ontwerpen en verschillen tussen interactieve communicatie en brief.

![ held-beeld ](do-not-localize/correspondence-management.png)

De interactieve Mededelingen centraliseert en beheert de verwezenlijking, de assemblage, en de levering van veilige, gepersonaliseerde, en interactieve correspondentie zoals bedrijfscorrespondentie, documenten, verklaringen, voordeelberichten, marketing brievenpost, rekeningen, en welkomstkits.

## Belangrijkste mogelijkheden {#key-capabilities}

Hier volgen de belangrijkste mogelijkheden van interactieve communicatie:

- De integratie van buiten-de-doos met het model van vormgegevens om gemakkelijke en gestroomlijnde toegang tot achterste eindgegevensbestanden en andere systemen van CRM, zoals de Dynamica van MS® toe te laten
- Geïntegreerde ontwerpinterface voor afdrukken en webkanalen met de mogelijkheid om webkanaal automatisch te genereren via het afdrukkanaal
- Grafieken om informatie in gemakkelijk te begrijpen visuele formaten in druk en Web te presenteren
- Documentfragmenten ondersteunen regeleditor en formuliergegevensmodel
- De gebruikersinterface van de agent toont druk en Webvoorproef van Interactieve Communicatie
- Met slepen en neerzetten kunt u snel afdrukken- en webkanalen maken

## Interactieve communicatie maken {#interactive-communication-creation}

![ interactive_communication-01 ](assets/interactive_communication-01.jpg)

### Workflow {#workflow}

Om een Interactieve Mededeling tot stand te brengen, heb de [ bouwstenen ](#buildingblocks) voor Interactieve Communicatie klaar en voltooi dan de volgende stappen:

1. Kies om [ tot een Interactieve Communicatie ](/help/forms/using/create-interactive-communication.md) te leiden.

1. Specificeer het [ model van vormgegevens ](/help/forms/using/data-integration.md), de prefill dienst, en [ druk en Webkanaalmalplaatjes ](/help/forms/using/web-channel-print-channel.md). U kunt het webkanaal genereren via het afdrukkanaal.

1. Gebruikend de [ belemmering-en-dalingsinterface ](/help/forms/using/introduction-interactive-communication-authoring.md), voeg documentfragmenten, beelden, componenten aan druk en Webkanaal van de Interactieve Mededeling toe zoals vereist.
1. Vorm de eigenschappen voor de opgenomen componenten, zoals het volgende:

   1. [Afbeeldingen](/help/forms/using/create-interactive-communication.md#step2)
   1. [ Lijsten ](/help/forms/using/create-interactive-communication.md#tables) (met inbegrip van de Fragmenten van de Lay-out)
   1. [Grafieken](/help/forms/using/chart-component-interactive-communications.md)
   1. [Documentfragmenten](/help/forms/using/create-interactive-communication.md#document-fragment-properties)

1. Een voorvertoning weergeven van afdruk- en webkanalen en, indien nodig, Interactieve communicatie.
1. De agent gebruikt de Agent UI om [ de Interactieve Communicatie ](/help/forms/using/prepare-send-interactive-communication.md) voor te bereiden om het naar het ontvanger/postproces te verzenden.

### Bouwstenen {#buildingblocks}

Hieronder vindt u de bouwstenen die nodig zijn voor het maken van interactieve communicatie:

- [Formuliergegevensmodel](/help/forms/using/data-integration.md)
- [Afdruk- en webkanaalsjablonen](/help/forms/using/web-channel-print-channel.md)
- [Documentfragmenten](/help/forms/using/document-fragments.md)
- Afbeeldingen
- [ Thema&#39;s ](/help/forms/using/themes.md) voor het kanaal van het Web

## Interactieve communicatie Vs Correspondentenbeheer {#interactive-communications-vs-correspondence-management}

De interactieve Communicatie is het gebrek en geadviseerde benadering om klantenmededelingen tot stand te brengen. Om de brieven te blijven gebruiken die in AEM 6.3 Forms en AEM 6.2 Forms creëren, moet u een verenigbaarheidspakket [&#128279;](/help/forms/using/compatibility-package.md) installeren.  Hier volgt een vergelijking tussen de mogelijkheden van interactieve communicatie en de letters.

<table>
 <tbody>
  <tr>
   <td><strong>Capaciteit</strong></td>
   <td><strong>Interactieve communicatie</strong></td>
   <td><strong>Letter</strong></td>
  </tr>
  <tr>
   <td>Uitvoer</td>
   <td>Afdrukken en web</td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Schema</td>
   <td>Formuliergegevensmodel </td>
   <td>Gegevenswoordenboek </td>
  </tr>
  <tr>
   <td>Lokalisatie</td>
   <td>Niet ondersteund in formuliergegevensmodel</td>
   <td>Ondersteund in gegevenswoordenboek</td>
  </tr>
  <tr>
   <td>Regeleditor</td>
   <td>
    <ul>
     <li>De redacteur van de de steunregel van de tekst en van de voorwaarde voor het creëren van gealigneerde voorwaarden</li>
     <li>De interactieve Communicatie redacteur steunt toepassing van regels op componenten van het Webkanaal</li>
    </ul> </td>
   <td>Geen interface voor maken van voorwaardelijke expressie</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Interface voor slepen en neerzetten maken van afdrukken en webkanaal</td>
   <td>Geen mechanisme voor slepen en neerzetten </td>
  </tr>
  <tr>
   <td>Grafieken</td>
   <td>Grafieken die worden ondersteund in afdrukken en webkanaal</td>
   <td>Niet ondersteund</td>
  </tr>
  <tr>
   <td>Thema's</td>
   <td>Gebruikt thema's om webkanaal op te maken</td>
   <td>Onderwerpen worden niet ondersteund</td>
  </tr>
   <tr>
   <td>Concepten</td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
   <tr>
   <td>Indieningen</td>
   <td>Ondersteund</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
  <tr>
   <td>Controle</td>
   <td>Niet ondersteund</td>
   <td>Ondersteund</td>
  </tr>
   <tr>
   <td>Versioning</td>
   <td>Niet ondersteund</td>
   <td>Ondersteund</td>
  </tr>
   <td>Batchverwerking</td>
   <td>Ondersteund </td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td>Handtekening agent</td>
   <td>Niet ondersteund</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td>Externe functies</td>
   <td>Niet ondersteund</td>
   <td>Ondersteund</td>
  </tr>
 </tbody>
</table>
