---
title: Adobe-classificaties
seo-title: Adobe-classificaties
description: Meer informatie over Adobe Classifications.
seo-description: Meer informatie over Adobe Classifications.
uuid: 57fb59f4-da90-4fe7-a5b1-c3bd51159a16
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6787511a-2ce0-421a-bcfb-90d5f32ad35e
translation-type: tm+mt
source-git-commit: 4456b5366387c27810c407d6ac9e6c17fc290269

---


# Adobe-classificaties{#adobe-classifications}

Adobe Classifications exporteert classificatiegegevens op een geplande manier naar [Adobe Analytics](/help/sites-administering/adobeanalytics.md) . De exporter is een implementatie van een **com.adobe.cq.scheduled.exporter.Exporter**.

Om dit te vormen:

1. Selecteer met **Navigatie** eerst **Gereedschappen**, **Cloud Services** en daarna **Oudere Cloud Services**.
1. Blader naar **Adobe Analytics** en selecteer **Configurations** tonen.
1. Klik op de koppeling **[+]** naast de configuratie van Adobe Analytics.

1. In het dialoogvenster **Kader** maken:

   * Geef een **titel** op.
   * U kunt optioneel de **naam** opgeven voor het knooppunt dat de frameworkgegevens in de opslagplaats opslaat.
   * Classificaties **van Adobe Analytics selecteren**
   Klik op **Maken**.

   ![Dialoogvenster Framework maken](assets/aa-25.png)

1. Het dialoogvenster **Classificatieinstellingen** wordt geopend voor bewerking.

   ![Dialoogvenster Classificatieinstellingen](assets/aa-classifications-settings.png)

   Tot de eigenschappen behoren:

   | **Veld** | **Beschrijving** |
   |---|---|
   | Ingeschakeld | Selecteer **Ja** om de instellingen voor Adobe-classificaties in te schakelen. |
   | Overschrijven bij conflict | Selecteer **Ja** om eventuele gegevensbotsingen te overschrijven. Standaard is deze ingesteld op **Nee**. |
   | Verwerkt verwijderen | Indien ingesteld op **Ja**, worden verwerkte knooppunten verwijderd nadat deze zijn geëxporteerd. De standaardwaarde is **False**. |
   | Taakbeschrijving exporteren | Voer een beschrijving in voor de Adobe Classifications-taak. |
   | E-mailbericht | Voer een e-mailadres in voor de kennisgeving van Adobe Classifications. |
   | Rapportsuite | Voer de rapportsuite in waarop de importtaak moet worden uitgevoerd. |
   | Gegevensset | Voer de relatie-id van de gegevensset in om de importtaak uit te voeren waarvoor. |
   | Transformer | Selecteer een transformatorimplementatie in het keuzemenu. |
   | Gegevensbron | Navigeer naar het pad voor de gegevenscontainer. |
   | Export Plan | Selecteer het schema voor het exporteren. De standaardwaarde is elke 30 minuten. |

1. Klik op **OK** om uw instellingen op te slaan.

## Paginaformaat wijzigen {#modifying-page-size}

Records worden op pagina&#39;s verwerkt. Standaard worden in Adobe Classifications pagina&#39;s gemaakt met een paginaformaat van 1000.

Een pagina kan maximaal 25000 pagina&#39;s groot zijn, per definitie in Adobe-classificaties en kan worden gewijzigd vanaf de Felix-console. Tijdens het exporteren vergrendelt Adobe Classifications het bronknooppunt om gelijktijdige wijzigingen te voorkomen. Het knooppunt wordt ontgrendeld na exporteren, bij een fout of wanneer de sessie wordt gesloten.

Het paginaformaat wijzigen:

1. Navigeer naar de OSGI-console op **https://&lt;host>:&lt;port>/system/console/configMgr** en selecteer **Adobe AEM Classifications Exporter**.

   ![aa-26](assets/aa-26.png)

1. Werk het formaat **van de Pagina van de** Uitvoer zoals vereist bij, dan klik **sparen**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe Classifications werd voorheen SAINT Exporter genoemd.

Een exporteur kan een Transformer gebruiken om de exportgegevens om te zetten in een specifieke indeling. Voor Adobe Classifications is een subinterface beschikbaar `SAINTTransformer<String[]>` voor de implementatie van de Transformer-interface. Deze interface wordt gebruikt om het gegevenstype te beperken tot `String[]` dat door SAINT API wordt gebruikt en een tellerinterface te hebben om dergelijke diensten voor selectie te vinden.

In de standaardimplementatie SAINTDefaultTransformer, worden de kindmiddelen van de exporterbron behandeld als verslagen met bezitsnamen als sleutels en bezitswaarden als waarden. De kolom **Sleutel** wordt automatisch toegevoegd als eerste kolom - zijn waarde zal de knooppuntnaam zijn. Benoemde eigenschappen (die `:`) bevatten worden genegeerd.

*Nodestructuur:*

* id-classificatie `nt:unstructured`

   * 1 `nt:unstructured`

      * Product = Mijn productnaam (Koord)
      * Price = 120.90 (String)
      * Size = M (String)
      * Color = black (String)
      * Color^Code = 101 (String)

**SAINT-koptekst en -record:**

| **Sleutel** | **Product** | **Prijs** | **Grootte** | **Kleur** | **Kleur^code** |
|---|---|---|---|---|---|
| 1 | Mijn productnaam | 120.90 | M | zwart | 101 |

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
   <td>Markering om gegevensbotsingen te overschrijven. De standaardwaarde is <strong>false</strong>.</td>
  </tr>
  <tr>
   <td>controledivisies</td>
   <td>Markering om te controleren of de rapportsuite compatibel is. De standaardwaarde is <strong>true</strong>.</td>
  </tr>
  <tr>
   <td>gereduceerd</td>
   <td>Markering om de verwerkte knooppunten na het exporteren te verwijderen. De standaardwaarde is <strong>false</strong>.</td>
  </tr>
 </tbody>
</table>

## Exporteren van Adobe Classifications automatiseren {#automating-adobe-classifications-export}

U kunt uw eigen workflow maken, zodat bij nieuwe importbewerkingen de workflow wordt gestart voor het maken van de juiste en goed gestructureerde gegevens in **/var/export/** , zodat deze kunnen worden geëxporteerd naar Adobe Classifications.
