---
title: Adobe-classificaties
description: Leer hoe u classificaties van Adoben kunt gebruiken om classificatiegegevens naar Adobe Analytics te exporteren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 0e675ce8-ba3b-481d-949e-0c85c97054d2
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Adobe-classificaties{#adobe-classifications}

De classificaties van de Adobe voeren classificatiegegevens naar [ Adobe Analytics ](/help/sites-administering/adobeanalytics.md) op een geplande manier uit. Exporter is een implementatie van a **com.adobe.cq.scheduled.exporter.Exporter**.

Om dit te vormen:

1. Gebruikend **Navigatie**, uitgezochte **Hulpmiddelen**, **Cloud Servicen**, toen **Oudere Cloud Servicen**.
1. De rol aan **Adobe Analytics** en selecteert **toont Configuraties**.
1. Klik de **[+]** verbinding naast uw configuratie van Adobe Analytics.

1. In **creeer Kader** dialoog:

   * Specificeer a **Titel**.
   * Naar keuze kunt u de **Naam** specificeren, voor de knoop die de kaderdetails in de bewaarplaats opslaat.
   * Selecteer **Classificaties van Adobe Analytics**

   En klik **creeer**.

   ![ creeer de dialoog van het Kader ](assets/aa-25.png)

1. De **dialoog van de Montages van Classificaties** opent voor het uitgeven.

   ![ de dialoog van de Montages van Classificaties ](assets/aa-classifications-settings.png)

   Tot de eigenschappen behoren:

   | **Gebied** | **Beschrijving** |
   |---|---|
   | Ingeschakeld | Selecteer **ja** om de montages van de Classificaties van de Adobe toe te laten. |
   | Overschrijven bij conflict | Selecteer **ja** om het even welke gegevensbotsingen te beschrijven. Door gebrek, wordt dit geplaatst aan **Nr**. |
   | Verwerkt verwijderen | Als de reeks aan **ja**, verwerkte knopen schrapt nadat zij worden uitgevoerd. Het gebrek is **Vals**. |
   | Taakbeschrijving exporteren | Voer een beschrijving in voor de taak Classificaties Adoben. |
   | E-mailbericht | Voer een e-mailadres in voor berichten over Adoben van classificaties. |
   | Rapportsuite | Voer de rapportsuite in waarop de importtaak moet worden uitgevoerd. |
   | Gegevensset | Voer de relatie-id van de gegevensset in om de importtaak uit te voeren waarvoor. |
   | Transformer | Selecteer een transformatorimplementatie in het keuzemenu. |
   | Data Source | Navigeer naar het pad voor de gegevenscontainer. |
   | Export Plan | Selecteer het schema voor het exporteren. De standaardwaarde is elke 30 minuten. |

1. Klik **O.K.** om uw montages te bewaren.

## Paginaformaat wijzigen {#modifying-page-size}

Records worden op pagina&#39;s verwerkt. Standaard worden met Adobe classificaties pagina&#39;s gemaakt met een paginaformaat van 1000.

Een pagina kan maximaal 25000 pagina&#39;s groot zijn, per definitie in classificaties van Adoben en kan worden gewijzigd vanaf de Felix-console. Tijdens de uitvoer, vergrendelt de Classificaties van de Adobe de bronknoop om gezamenlijke wijzigingen te verhinderen. Het knooppunt wordt ontgrendeld na exporteren, bij een fout of wanneer de sessie wordt gesloten.

Het paginaformaat wijzigen:

1. Navigeer aan de console OSGI in **https://&lt;host>:&lt;port>/system/console/configMgr** en selecteer **Adobe AEM de Exporter van Classificaties**.

   ![ a-26 ](assets/aa-26.png)

1. Werk de **Grootte van de Pagina van de Uitvoer** zoals vereist bij, dan klik **sparen**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe Classifications was voorheen bekend als de SAINT Exporter.

Een exporteur kan een Transformer gebruiken om de exportgegevens om te zetten in een specifieke indeling. Voor classificaties van de Adobe, is een subinterface `SAINTTransformer<String[]>` die de interface van Transformer uitvoert verstrekt. Deze interface wordt gebruikt om het gegevenstype te beperken tot `String[]` dat wordt gebruikt door de SAINT API en om een markeringsinterface te hebben om dergelijke services voor selectie te zoeken.

In de standaardimplementatie SAINTDefaultTransformer, worden de kindmiddelen van de exporterbron behandeld als verslagen met bezitsnamen als sleutels en bezitswaarden als waarden. De **Zeer belangrijke** kolom wordt automatisch toegevoegd als eerste kolom - zijn waarde zal de knoopnaam zijn. Benoemde eigenschappen (die `:` bevatten) worden genegeerd.

*structuur van de Knoop:*

* id-classificatie `nt:unstructured`

   * 1 `nt:unstructured`

      * Product = Mijn productnaam (Koord)
      * Price = 120.90 (String)
      * Size = M (String)
      * Color = black (String)
      * Color^Code = 101 (String)

**SAINT Kopbal &amp; Verslag:**

| **Sleutel** | **Product** | **Prijs** | **Grootte** | **Kleur** | **kleur^Code** |
|---|---|---|---|---|---|
| 1 | Mijn productnaam | 120,90 | M | zwart | 101 |

Tot de eigenschappen behoren:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschappenpad</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>transformator</td>
   <td>Een klassenaam van een SAINTTransformer-implementatie</td>
  </tr>
  <tr>
   <td>email</td>
   <td>E-mailadres voor melding.</td>
  </tr>
  <tr>
   <td>reportsuites</td>
   <td>ID's van suite rapporteren waarin de importtaak moet worden uitgevoerd. </td>
  </tr>
  <tr>
   <td>gegevensset</td>
   <td>Dataset relatie-id om de importtaak uit te voeren voor. </td>
  </tr>
  <tr>
   <td>beschrijving</td>
   <td>Taakbeschrijving. <br /> </td>
  </tr>
  <tr>
   <td>overschrijven</td>
   <td>Markering om gegevensbotsingen te overschrijven. Het gebrek is <strong> vals </strong>.</td>
  </tr>
  <tr>
   <td>controleafdelingen</td>
   <td>Markering om te controleren of de rapportsuite compatibel is. Het gebrek is waar <strong> </strong>.</td>
  </tr>
  <tr>
   <td>gereduceerd</td>
   <td>Markering om de verwerkte knooppunten na het exporteren te verwijderen. Het gebrek is <strong> vals </strong>.</td>
  </tr>
 </tbody>
</table>

## Exporteren van Adobe classificaties automatiseren {#automating-adobe-classifications-export}

U kunt uw eigen werkschema tot stand brengen, zodat om het even welke nieuwe invoer de werkschema lanceert om aangewezen, en correct gestructureerd, gegevens in **te creëren/var/export/** zodat het naar de Classificaties van de Adobe kan worden uitgevoerd.
