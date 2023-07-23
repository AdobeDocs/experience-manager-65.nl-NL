---
title: Document met record genereren voor adaptieve formulieren
seo-title: Generate Document of Record for adaptive forms
description: Verklaart hoe u een malplaatje voor een document van verslag (DoR) voor adaptieve vormen kunt produceren.
seo-description: Explains how you can generate a template for a document of record (DoR) for adaptive forms.
uuid: 2dc7e0de-fff9-43fa-9426-e9b047eb2595
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ce65cb5f-94ec-4423-9fa9-d617e9703091
docset: aem65
feature: Adaptive Forms
exl-id: 7240897f-6b3a-427a-abc6-66310c2998f3
source-git-commit: e7a3558ae04cd6816ed73589c67b0297f05adce2
workflow-type: tm+mt
source-wordcount: '3416'
ht-degree: 0%

---

# Document met record genereren voor adaptieve formulieren{#generate-document-of-record-for-adaptive-forms}

<span class="preview"> Adobe raadt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |


## Overzicht {#overview}

Nadat u een formulier hebt verzonden, willen uw klanten doorgaans de informatie die zij in het formulier hebben ingevuld, afdrukken of in documentindeling bewaren voor toekomstig gebruik. Dit wordt bedoeld als document van verslag.

In dit artikel wordt uitgelegd hoe u een recorddocument kunt genereren voor adaptieve formulieren.

>[!NOTE]
>
>Automatisch genereren van een recorddocument wordt niet ondersteund voor op XFA gebaseerde adaptieve formulieren. U kunt echter de XDP gebruiken om het adaptieve formulier te maken als een recorddocument.

## Adaptieve formuliertypen en hun recorddocumenten {#adaptive-form-types-and-their-documents-of-record}

Wanneer u een adaptief formulier maakt, kunt u een formuliermodel selecteren. U kunt kiezen uit de volgende opties:

* [Formuliersjablonen](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template)
Hiermee kunt u een XFA-sjabloon selecteren voor het aangepaste formulier. Als u een XFA-sjabloon selecteert, kunt u het bijbehorende XDP-bestand gebruiken voor een recorddocument, zoals hierboven beschreven.

* [XML-schema](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema)
Hiermee kunt u een XML-schemadefinitie selecteren voor het aangepaste formulier. Wanneer u een XML-schema selecteert voor het aangepaste formulier, kunt u:

   * Koppel een XFA-sjabloon voor een record. Zorg ervoor dat de gekoppelde XFA-sjabloon hetzelfde XML-schema gebruikt als het aangepaste formulier
   * Automatisch een recorddocument genereren

* Met Geen kunt u een adaptief formulier maken zonder een formuliermodel. Het recorddocument wordt automatisch gegenereerd voor het aangepaste formulier.

Wanneer u een formuliermodel selecteert, configureert u het document met records met de opties die beschikbaar zijn onder Document of Record Template Configuration. Zie [Document met recordsjabloonconfiguratie](#document-of-record-template-configuration).

## Automatisch gegenereerd document van record {#automatically-generated-document-of-record}

Met een document met records kunnen uw klanten een kopie van het verzonden formulier bewaren voor afdrukdoeleinden. Wanneer u automatisch een document met records genereert, wordt het document met records telkens wanneer u het formulier wijzigt, onmiddellijk bijgewerkt. U verwijdert bijvoorbeeld het leeftijdsveld voor klanten die de Verenigde Staten van Amerika als hun land selecteren. Wanneer dergelijke klanten een document van verslag produceren, is het leeftijdsgebied niet zichtbaar aan hen in het document van verslag.

Automatisch gegenereerde recorddocumenten hebben de volgende voordelen:

* Het zorgt voor gegevensbinding.
* Velden die op het moment van verzending zijn gemarkeerd, worden automatisch van een record uitgesloten. Er is geen extra inspanning nodig.
* Het bespaart tijd voor het ontwerpen van document van verslagmalplaatje.
* Hiermee kunt u verschillende stijlen en vormgeving proberen met verschillende basissjablonen en de beste stijl en vormgeving kiezen voor Document of Record. Stijlvormgeving is optioneel. Als u geen stijl opgeeft, worden systeemstijlen standaard ingesteld.
* Hiermee zorgt u ervoor dat elke wijziging in het formulier direct wordt doorgevoerd in het document met de record.

## Componenten die automatisch een recorddocument genereren {#components-to-automatically-generate-a-document-of-record}

Voor het genereren van een recorddocument voor adaptieve formulieren hebt u de volgende componenten nodig:

**Aangepast formulier** Aangepast formulier waarvoor u een document met records wilt genereren.

**Basissjabloon (aanbevolen)** XFA-sjabloon (XDP-bestand) gemaakt in AEM Designer. De malplaatje van de basis wordt gebruikt om het stileren en het brandmerken informatie voor document van verslagmalplaatje te specificeren.

Zie [Basissjabloon van een record](#base-template-of-a-document-of-record)

>[!NOTE]
>
>De basissjabloon van een document met record wordt ook wel de meta-sjabloon van een document met record genoemd.

**Document met recordsjabloon** XFA-sjabloon (XDP-bestand) gegenereerd op basis van een adaptief formulier.

Zie [Document met recordsjabloonconfiguratie](#document-of-record-template-configuration).

**Formuliergegevens** Informatie die door een gebruiker in het adaptieve formulier wordt ingevuld. Het samenvoegt met het document van verslagmalplaatje om het document van verslag te produceren.

## Toewijzing van adaptieve formulierelementen {#mapping-of-adaptive-form-elements}

In de volgende secties wordt beschreven hoe adaptieve formulierelementen worden weergegeven in een recorddocument.

### Velden {#fields}

<table>
 <tbody>
  <tr>
   <th>Aangepast formulieronderdeel</th>
   <th>Overeenkomende XFA-component</th>
   <th>Standaard opgenomen in document van recordsjabloon?</th>
   <th>Notities</th>
  </tr>
  <tr>
   <td>Knop</td>
   <td>Knop</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Selectievakje</td>
   <td>Selectievakje</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumkiezer</td>
   <td>Datum-/tijdveld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Vervolgkeuzelijst</td>
   <td>Vervolgkeuzelijst</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Krabbelhandtekening</td>
   <td>Krabbelen op handtekening</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Numeriek vak</td>
   <td>Numeriek veld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Wachtwoordvak</td>
   <td>Wachtwoordveld</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Keuzerondje</td>
   <td>Keuzerondje</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Tekstvak</td>
   <td>Tekstveld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Knop Opnieuw instellen</td>
   <td>Knop Opnieuw instellen</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Verzenden, knop</td>
   <td><p>Knop E-mail verzenden</p> <p>Knop HTTP verzenden</p> </td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Voorwaarden en bepalingen</td>
   <td> </td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Bestandsbijlage</td>
   <td> </td>
   <td>false</td>
   <td>Niet beschikbaar in document van recordsjabloon. Alleen beschikbaar in document van record via bijlagen.</td>
  </tr>
 </tbody>
</table>

### Containers {#containers}

<table>
 <tbody>
  <tr>
   <th>Aangepast formulieronderdeel</th>
   <th>Overeenkomende XFA-component</th>
   <th>Notities</th>
  </tr>
  <tr>
   <td>Deelvenster<br /> </td>
   <td>Subformulier<br /> </td>
   <td>Herhalbaar deelvenster verwijst naar herhaalbaar subformulier.</td>
  </tr>
 </tbody>
</table>

### Statische componenten {#static-components}

| Aangepast formulieronderdeel | Overeenkomende XFA-component | Notities |
|---|---|---|
| Afbeelding | Afbeelding | De gebonden of niet-gebonden componenten TextDraw en Image worden altijd in het recorddocument weergegeven voor een adaptief formulier op basis van XSD, tenzij ze worden uitgesloten met behulp van het document met recordinstellingen. |
| Tekst | Tekst |

>[!NOTE]
>
>In de klassieke UI krijgt u verschillende tabbladen voor het bewerken van veldeigenschappen.

### Tabellen {#tables}

De tabelcomponenten voor adaptieve formulieren, zoals koptekst, voettekst en rijtoewijzing, voor de overeenkomstige XFA-componenten. U kunt herhaalbare deelvensters toewijzen aan tabellen in een document met records.

## Basissjabloon van een record {#base-template-of-a-document-of-record}

De basissjabloon biedt opmaak- en weergavegegevens voor documenten met een record. Hiermee kunt u de standaardweergave van automatisch gegenereerd document met record aanpassen. U wilt bijvoorbeeld het bedrijfslogo in de koptekst en copyrightinformatie in de voettekst van het document met de record plaatsen. De master pagina van het basissjabloon wordt gebruikt als een master pagina voor het document met een recordsjabloon. De master pagina kan informatie bevatten, zoals paginakoptekst, voettekst en paginanummer, die u kunt toepassen op het recorddocument. U kunt dergelijke informatie op document van verslag toepassen gebruikend basissjabloon voor auto het produceren van document van verslag. Met een basissjabloon kunt u de standaardeigenschappen van velden wijzigen.

Volg deze [Basissjabloonconventies](#base-template-conventions) wanneer u basissjabloon ontwerpt.

## Basissjabloonconventies {#base-template-conventions}

Een basissjabloon wordt gebruikt om de kop-, voettekst-, opmaak- en vormgeving van een recorddocument te definiëren. De kop- en voettekst kunnen informatie bevatten zoals het bedrijfslogo en de copyrighttekst. De eerste master pagina in de basissjabloon wordt gekopieerd en gebruikt als een master pagina voor het recorddocument. Deze pagina bevat koptekst, voettekst, paginanummer of andere informatie die op alle pagina&#39;s in het recorddocument moet worden weergegeven. Als u een basissjabloon gebruikt dat niet voldoet aan de conventies voor basissjablonen, wordt de eerste master pagina van de basissjabloon nog steeds gebruikt in het document met een recordsjabloon. U wordt ten zeerste aangeraden de basissjabloon te ontwerpen volgens de conventies en deze te gebruiken voor het automatisch genereren van een document met record.

**Master paginaconventies**

* In het basissjabloon moet u het basissubformulier een naam geven `AF_METATEMPLATE` en de master pagina als `AF_MASTERPAGE`.

* De master pagina met de naam `AF_MASTERPAGE` die zich onder `AF_METATEMPLATE` het basissubformulier krijgt de voorkeur voor het ophalen van koptekst-, voettekst- en opmaakgegevens.

* Indien `AF_MASTERPAGE` is afwezig, wordt de eerste master pagina gebruikt die in het basissjabloon aanwezig is.

**Opmaakconventies voor velden**

* Als u stijl wilt toepassen op de velden in het document met records, bevat de basissjabloon velden in het dialoogvenster `AF_FIELDSSUBFORM` subfrom under the `AF_METATEMPLATE` basissubformulier.

* De eigenschappen van deze velden worden toegepast op de velden in het recorddocument. Deze velden moeten `AF_<name of field in all caps>_XFO` naamgevingsconventie. De veldnaam voor het selectievakje moet bijvoorbeeld `AF_CHECKBOX_XFO`.

Ga als volgt te werk in AEM Designer om een basissjabloon te maken.

1. Klikken **Bestand > Nieuw**.
1. Selecteer **Op basis van een sjabloon** optie.

1. Selecteer **Forms - Document of Record** categorie.
1. Selecteren **DoR-basissjabloon**.
1. Klikken **Volgende** en verstrekt de vereiste informatie.

1. (Optioneel) Wijzig de opmaak en weergave van velden die u wilt toepassen op de velden in het document met records.
1. Sla het formulier op.

U kunt het opgeslagen formulier nu gebruiken als een basissjabloon voor een recorddocument.
Wijzig of verwijder geen scripts in de basissjabloon.

**Basissjabloon wijzigen**

* Als u geen opmaak toepast op velden in de basissjabloon, is het aan te raden deze velden uit de basissjabloon te verwijderen, zodat alle upgrades naar de basissjabloon automatisch worden opgehaald.
* Verwijder scripts niet tijdens het wijzigen van een basissjabloon, voeg ze toe of wijzig ze niet.

>[!NOTE]
>
>Ontwerp het basissjabloon met conventies en volg de bovenstaande stappen strikt.

## Document met recordsjabloonconfiguratie {#document-of-record-template-configuration}

Configureer het document met de recordsjabloon van uw formulier, zodat uw klanten een afdrukvriendelijke kopie van het verzonden formulier kunnen downloaden. Een XDP-bestand fungeert als het document van een recordsjabloon. Het document van recordgebruikers dat wordt gedownload, wordt opgemaakt volgens de indeling die is opgegeven in het XDP-bestand.

Voer de volgende stappen uit om een document van verslag voor adaptieve vormen te vormen:

1. Klik in AEM instantie van de auteur op **Forms > Forms en Documenten.**
1. Selecteer een formulier en klik op **Eigenschappen weergeven**.
1. Tik in het venster Eigenschappen op **Formuliermodel**.
U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.

   >[!NOTE]
   >
   >Selecteer op het tabblad Formuliermodel de optie **Schema** of **Geen** van de **Selecteren uit** vervolgkeuzelijst. **[!UICONTROL Document of record is not supported for XFA-based or adaptive forms with Form Template as form model.]**

1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel een van de volgende opties.

   **Geen** Selecteer deze optie als u geen document van verslag voor de vorm wilt vormen.

   **Formuliersjabloon koppelen als Document of Record-sjabloon** Selecteer deze optie als u een XDP-bestand hebt dat u als sjabloon voor het recorddocument wilt gebruiken. Als u deze optie selecteert, worden alle XDP-bestanden weergegeven die beschikbaar zijn in de AEM Forms-opslagplaats. Selecteer het juiste bestand.

   Het geselecteerde XDP-bestand wordt gekoppeld aan het adaptieve formulier.

   **Document van record genereren** Selecteer deze optie als u een XDP-bestand wilt gebruiken als een basissjabloon voor het definiëren van de opmaak en weergave voor het document met records. Als u deze optie selecteert, worden alle XDP-bestanden weergegeven die beschikbaar zijn in de AEM Forms-opslagplaats. Selecteer het juiste bestand.

   >[!NOTE]
   >
   >Zorg ervoor dat het schema dat wordt gebruikt om een adaptief formulier en schema (gegevensschema) van XFA-formulieren te maken, hetzelfde zijn als:
   >
   >
   >
   >    * Het adaptieve formulier is gebaseerd op een schema
   >    * U gebruikt **Formuliersjabloon koppelen als Document of Record-sjabloon** optie voor recorddocument
   >
   >

1. Klikken **Gereed.**

## De brandinggegevens in het document van de record aanpassen {#customize-the-branding-information-in-document-of-record}

Tijdens het genereren van een recorddocument kunt u de brandinggegevens voor het recorddocument wijzigen op het tabblad Document of Record. Het tabblad Document of Record bevat opties zoals logo, weergave, lay-out, koptekst en voettekst, disclaimer en of u niet het selectievakje en keuzerondjes wilt inschakelen of niet.

Als u de brandinggegevens die u opgeeft op het tabblad Document of Record wilt lokaliseren, moet u ervoor zorgen dat de landinstelling van de browser correct is ingesteld. Voer de volgende stappen uit als u de brandinggegevens van een recorddocument wilt aanpassen:

1. Selecteer een deelvenster (hoofddeelvenster) in het document met records en tik vervolgens op ![vormen](assets/configure.png).
1. Tikken ![dortab](/help/forms/using/assets/dortab.png). Het tabblad Document of Record wordt weergegeven.
1. Selecteer de standaardsjabloon of een aangepaste sjabloon voor het weergeven van het document met records. Als u de standaardsjabloon selecteert, wordt een miniatuurvoorvertoning van het recorddocument weergegeven onder de vervolgkeuzelijst Sjabloon.

   ![brandingsjabloon](/help/forms/using/assets/brandingtemplate.png)

   Als u een aangepaste sjabloon wilt selecteren, bladert u door een selectie van een XDP op uw AEM Forms-server. Als u een sjabloon wilt gebruiken die nog niet op uw AEM Forms-server staat, moet u de XDP eerst uploaden naar uw AEM Forms-server.

1. Afhankelijk van het feit of u een standaardsjabloon of een aangepaste sjabloon selecteert, worden sommige of alle volgende eigenschappen weergegeven op het tabblad Document van record. Geef deze op de juiste manier op:

   * **Logoafbeelding**: U kunt kiezen of u de afbeelding met het logo in het adaptieve formulier wilt gebruiken, een afbeelding kiezen in DAM of een afbeelding uploaden vanaf uw computer.
   * **Formuliertitel**
   * **Koptekst**
   * **Label voor afwijzing**
   * **Disclaimer**
   * **Disclaimtekst**
   * **Accentkleur**: De kleur waarin koptekst en scheidingslijnen worden gerenderd in het document of de record PDF
   * **Lettertypefamilie**: Lettertypefamilie van de tekst in het document van record PDF
   * **Geef voor de componenten Selectievakje en Keuzerondje alleen de geselecteerde waarden weer**
   * **Scheidingsteken voor meerdere geselecteerde waarden**
   * **Formulierobjecten opnemen die niet aan het gegevensmodel zijn gebonden**
   * **Verborgen velden uitsluiten van het recorddocument**
   * **Beschrijving van deelvensters verbergen**

   Als de aangepaste XDP-sjabloon die u selecteert meerdere master pagina&#39;s bevat, worden de eigenschappen voor deze pagina&#39;s weergegeven in het dialoogvenster **[!UICONTROL content]** van de **[!UICONTROL Document of Record]** tab.

   ![Master pagina-eigenschappen](assets/master-page-properties.png)

   Tot de master pagina-eigenschappen behoren Logo Image, Header Text, Form Title, Disclaimer Label en Disclaimer Text. U kunt adaptieve formulier- of XDP-sjablooneigenschappen toepassen op het Document of Record. AEM Forms past de sjablooneigenschappen standaard toe op het Document of Record. U kunt ook aangepaste waarden definiëren voor de master pagina-eigenschappen. Ga voor informatie over het toepassen van meerdere master pagina&#39;s in een document met records naar [Meerdere master pagina&#39;s toepassen op een document met records](#apply-multiple-master-pages-dor).

   >[!NOTE]
   >
   >Als u een adaptieve formuliersjabloon gebruikt die is gemaakt met een versie van Designer die ouder is dan versie 6.3, zodat de eigenschappen Accent Color en Font Family werken, moet u ervoor zorgen dat het volgende aanwezig is in uw adaptieve formuliersjabloon onder het basissubformulier:

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Tik op Gereed om de wijzigingen in de branding op te slaan.

## Tabel- en kolomindelingen voor deelvensters in document van record {#table-and-column-layouts-for-panels-in-document-of-record}

Het aangepaste formulier kan lang zijn en meerdere formuliervelden bevatten. U wilt een document met records mogelijk niet opslaan als een exacte kopie van het aangepaste formulier. U kunt nu een tabel- of kolomindeling kiezen om een of meer adaptieve formulierdeelvensters op te slaan in het document met de recordindeling PDF.

Voordat u een recorddocument genereert, kiest u in de instellingen van een deelvenster de optie Indeling voor het document van record voor dat deelvenster als tabel of kolom. De velden in het deelvenster worden op basis van de indeling in het recorddocument ingedeeld.

![Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records](assets/dortablelayout.png)

Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records

![Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records](assets/dorcolumnlayout.png)

Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records

## Document met recordinstellingen {#document-of-record-settings}

Met documenten met recordinstellingen kunt u opties kiezen die u wilt opnemen in het document met records. Een bank accepteert bijvoorbeeld naam, leeftijd, socialezekerheidsnummer en telefoonnummer in een formulier. Het formulier genereert een bankrekeningnummer en filiaalgegevens. U kunt ervoor kiezen alleen de naam, het socialezekerheidsnummer, de bankrekening en de filiaalgegevens in een document met gegevens weer te geven.

Het document met recordinstellingen van een component is beschikbaar onder de eigenschappen. Als u toegang wilt krijgen tot de eigenschappen van een component, selecteert u de component en klikt u op ![cmppr](assets/cmppr.png) in de overlay. De eigenschappen worden vermeld in de zijbalk en u kunt de volgende instellingen erin vinden.

**Instellingen op veldniveau**

* **Uitsluiten van document van record**: Als u de eigenschap true instelt, wordt het veld van het recorddocument uitgesloten. Dit is een scriptbare eigenschap met de naam `excludeFromDoR`. Het gedrag hangt af van **Velden uitsluiten van DoR indien verborgen** eigenschap op formulierniveau.

* **Deelvenster weergeven als tabel:** Als u de eigenschap instelt, wordt het deelvenster weergegeven als een tabel in een document met record als het deelvenster minder dan 6 velden bevat. Alleen van toepassing op het deelvenster.
* **Titel van document of record uitsluiten:** Als u de eigenschap instelt, wordt de titel van het deelvenster/de tabel uitgesloten van het recorddocument. Alleen van toepassing op het deelvenster en de tabel.
* **Beschrijving uitsluiten van document van record:** Als u de eigenschap instelt, wordt de beschrijving van het deelvenster/de tabel niet opgenomen in het recorddocument. Alleen van toepassing op het deelvenster en de tabel.
* **[!UICONTROL Pagination]** > **[!UICONTROL Place]**: Hiermee bepaalt u waar u het deelvenster wilt plaatsen.
   * **[!UICONTROL Place]** > **[!UICONTROL Following Previous]**: Hiermee plaatst u het deelvenster achter het vorige object in het bovenliggende deelvenster.
   * **[!UICONTROL Place]** > **[!UICONTROL In Content Area]** > Naam van inhoudsgebied: Plaatst het deelvenster in het opgegeven inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Next Content Area]**: Hiermee plaatst u het deelvenster boven aan het volgende inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Content Area]** > Naam van inhoudsgebied: Plaatst het deelvenster boven aan het opgegeven inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL On Page]** > Naam van master pagina: Plaatst het deelvenster op de opgegeven pagina. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Next Page]**: Hiermee plaatst u het deelvenster boven aan de volgende pagina. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Page]** > Naam van master pagina: Plaatst het deelvenster boven aan de pagina wanneer de opgegeven pagina wordt weergegeven. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
* **[!UICONTROL Pagination]** > **[!UICONTROL After]**: Hiermee bepaalt u welk gebied moet worden gevuld nadat een deelvenster is geplaatst. De volgende velden zijn beschikbaar in het dialoogvenster **[!UICONTROL After]** sectie:
   * **[!UICONTROL After]** > **[!UICONTROL Continue Filling Parent]**: Hiermee gaat u door met het samenvoegen van gegevens voor alle objecten die nog in het bovenliggende deelvenster moeten worden ingevuld.
   * **[!UICONTROL After]** > **[!UICONTROL Go to Next Content Area]**: Hiermee begint u het volgende inhoudsgebied te vullen nadat u het deelvenster hebt geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Content Area]** > Naam van inhoudsgebied: Hiermee wordt het vullen van het opgegeven inhoudsgebied gestart nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Next Page]**: Hiermee wordt het vullen van de volgende pagina gestart nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Page]** > Naam van pagina: Hiermee wordt het vullen van de opgegeven pagina gestart nadat het deelvenster is geplaatst.
* **[!UICONTROL Pagination]** > **[!UICONTROL Overflow]**: Hiermee stelt u een overloop in voor een deelvenster of een tabel die meerdere pagina&#39;s beslaat. De volgende velden zijn beschikbaar in het dialoogvenster **[!UICONTROL Overflow]** sectie:
   * **[!UICONTROL Overflow]** > **[!UICONTROL None]**: Hiermee wordt het vullen van de volgende pagina gestart. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
   * **[!UICONTROL Overflow]** > **[!UICONTROL Go to Content Area]** > Naam van inhoudsgebied: Hiermee wordt het vullen van het opgegeven inhoudsgebied gestart.
   * **[!UICONTROL Overflow]** > **[!UICONTROL Go To Page]** > Naam van pagina: Hiermee wordt het vullen van de opgegeven pagina gestart.

Voor informatie over het toepassen van pagina-einden en het toepassen van meerdere master pagina&#39;s in een document met records raadpleegt u [Pagina-einde toepassen in een document van record](#apply-page-breaks-in-dor) en [Meerdere master pagina&#39;s toepassen op een document met records](#apply-multiple-master-pages-dor).

**Instellingen voor formulierniveau**

* **Inclusief niet-gebonden velden in DoR:** Als u de eigenschap instelt, worden niet-gebonden velden van het op schema gebaseerde adaptieve formulier in het document of record opgenomen. Standaard is dit waar.
* **Velden uitsluiten van DoR indien verborgen:** De eigenschap instellen om de verborgen velden uit te sluiten [!UICONTROL Document of Record] bij het indienen van het formulier. Wanneer u [Revalidate op server](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), worden de verborgen velden opnieuw berekend voordat deze worden uitgesloten van de [!UICONTROL Document of Record].

## Een pagina-einde toepassen in een document van record {#apply-page-breaks-in-dor}

U kunt pagina-einden in een Document van Verslag toepassen gebruikend veelvoudige methodes.

Een pagina-einde toepassen op een document met records:

1. Tik op het deelvenster en selecteer ![Configureren](/help/forms/using/assets/configure.png)
1. Uitbreiden **[!UICONTROL Document of Record]** om de eigenschappen weer te geven.

1. In de **[!UICONTROL Pagination]** sectie, tikken ![Map](/help/forms/using/assets/folder-icon.png) in de **[!UICONTROL Place]** veld.
1. Tikken **[!UICONTROL Top of Next page]** en tikken **[!UICONTROL Select]**. U kunt ook tikken **[!UICONTROL Top of Page]** selecteert u de master pagina en tikt u op **[!UICONTROL Select]** om het pagina-einde toe te passen.
1. Tikken ![Opslaan](/help/forms/using/assets/save_icon.png) om de eigenschappen op te slaan.

Het geselecteerde deelvenster gaat naar de volgende pagina.

## Meerdere master pagina&#39;s toepassen op een document met records {#apply-multiple-master-pages-dor}

Als de aangepaste XDP-sjabloon die u selecteert meerdere master pagina&#39;s bevat, worden de eigenschappen voor deze pagina&#39;s weergegeven in het dialoogvenster [!UICONTROL content] van de [!UICONTROL Document of Record] tab. Zie voor meer informatie [De brandinggegevens in het document van de record aanpassen](#customize-the-branding-information-in-document-of-record).

U kunt meerdere master pagina&#39;s toepassen op een Document of Record door verschillende master pagina&#39;s toe te passen op de onderdelen van een adaptief formulier. Gebruik de [Paginering](#document-of-record-settings) van de eigenschappen Document of Record om meerdere master pagina&#39;s toe te passen.

Hieronder ziet u hoe u meerdere master pagina&#39;s kunt toepassen op een document met records: U uploadt een XDP-sjabloon met vier master pagina&#39;s naar de [!DNL AEM Forms] server. [!DNL AEM Forms] Hiermee past u de sjablooneigenschappen standaard toe op het document of record. [!DNL AEM Forms] Hiermee past u ook de eerste master pagina-eigenschappen in de sjabloon toe op het Document of Record.

Voer de volgende stappen uit om de tweede master pagina-eigenschappen toe te passen op een deelvenster en de derde master pagina-eigenschappen op de volgende deelvensters:

1. Tik op het deelvenster om de tweede master pagina toe te passen en selecteer ![Configureren](assets/cmppr.png).
1. In de **[!UICONTROL Pagination]** sectie, tikken ![Map](/help/forms/using/assets/folder-icon.png) in de **[!UICONTROL Place]** veld.
1. Tikken **[!UICONTROL On page]**, selecteert u de tweede master pagina en tikt u op **[!UICONTROL Select]**.
AEM Forms past de tweede master pagina toe op het deelvenster en alle volgende deelvensters in het adaptieve formulier.
1. In de **[!UICONTROL Pagination]** sectie, tikken ![Map](/help/forms/using/assets/folder-icon.png) in de **[!UICONTROL After]** veld.
1. Tikken **[!UICONTROL Go To page]**, selecteert u de derde master pagina en tikt u op **[!UICONTROL Select]**.
1. Tikken ![Opslaan](/help/forms/using/assets/save_icon.png) om de eigenschappen op te slaan.
AEM Forms past de derde master pagina toe op het deelvenster en alle volgende deelvensters in het adaptieve formulier.


## Belangrijke overwegingen bij het werken met een document {#key-considerations-when-working-with-document-of-record}

Houd rekening met de volgende overwegingen en beperkingen wanneer u werkt aan een document of record voor adaptieve formulieren.

* Document met recordsjablonen ondersteunt geen RTF-bestanden. Alle RTF-tekst in het statische adaptieve formulier of in de informatie die door de eindgebruiker is ingevuld, wordt daarom als onbewerkte tekst weergegeven in het document met de record.
* Documentfragmenten in een adaptieve vorm worden niet weergegeven in het recorddocument. Aangepaste formulierfragmenten worden echter ondersteund.
* Inhoudbinding in document van record die is gegenereerd voor een adaptief formulier op basis van een XML-schema, wordt niet ondersteund.
* De gelokaliseerde versie van document van verslag wordt gecreeerd op bestelling voor een scène wanneer de gebruiker om de teruggave van het document van verslag verzoekt. De lokalisatie van een recorddocument vindt plaats in combinatie met de lokalisatie van het adaptieve formulier. Zie voor meer informatie over lokalisatie van documenten met registratie en adaptieve formulieren [Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).
