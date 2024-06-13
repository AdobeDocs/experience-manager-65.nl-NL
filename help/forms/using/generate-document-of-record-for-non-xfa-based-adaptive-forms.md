---
title: Document met record genereren voor adaptieve formulieren
description: Verklaart hoe u document van verslag (DoR) voor adaptieve vormen kunt produceren.
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms, Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f8013aeedb79f900158df2291f7f641353bb4c05
workflow-type: tm+mt
source-wordcount: '4155'
ht-degree: 0%

---

# Document met record genereren voor adaptieve formulieren of adaptieve formulierfragmenten {#generate-document-of-record-for-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |


## Overzicht {#overview}

Nadat u een formulier hebt verzonden, willen uw klanten doorgaans de informatie die zij in het formulier hebben ingevuld, afdrukken of in documentindeling bewaren voor toekomstig gebruik. Dit wordt bedoeld als document van verslag.

In dit artikel wordt uitgelegd hoe u een recorddocument kunt genereren voor adaptief Forms- of adaptief formulierfragment.

>[!NOTE]
>
> De ondersteuning voor het aanpassen van uw fragmenten van het adaptieve formulier en de bijbehorende velden in de Adaptieve Form Editor is geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).


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
* Velden die op het moment van verzending zijn gemarkeerd, worden automatisch van een recorddocument uitgesloten. Er is geen extra inspanning nodig.
* Het bespaart tijd voor het ontwerpen van document van verslagmalplaatje.
* Hiermee kunt u verschillende stijlen en vormgeving proberen met verschillende basissjablonen en de beste stijl en vormgeving kiezen voor Document of Record. Stijlvormgeving is optioneel. Als u geen stijl opgeeft, worden systeemstijlen standaard ingesteld.
* Hiermee zorgt u ervoor dat elke wijziging in het formulier direct wordt doorgevoerd in het document met de record.

## Componenten die automatisch een recorddocument genereren {#components-to-automatically-generate-a-document-of-record}

Voor het genereren van een recorddocument voor adaptieve formulieren hebt u de volgende componenten nodig:

**Aangepast formulier** Aangepast formulier waarvoor u een document met records wilt genereren.

**Adaptief formulierfragment** Adaptief formulierfragment waarvoor u een document met records wilt genereren.

**Basissjabloon (aanbevolen)** XFA-sjabloon (XDP-bestand) gemaakt in AEM Designer. De malplaatje van de basis wordt gebruikt om het stileren en het brandmerken informatie voor document van verslagmalplaatje te specificeren.

Zie [Basissjabloon van een record](#base-template-of-a-document-of-record)

>[!NOTE]
>
>De basissjabloon van een document met record wordt ook wel de meta-sjabloon van een document met record genoemd.

**Document met recordsjabloon** XFA-sjabloon (XDP-bestand) gegenereerd uit een adaptief formulier.

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

De basissjabloon biedt opmaak- en weergavegegevens voor documenten met een record. Hiermee kunt u de standaardweergave van automatisch gegenereerd document met record aanpassen. U wilt bijvoorbeeld het bedrijfslogo in de koptekst en copyrightinformatie in de voettekst van het document met de record plaatsen. De basispagina van het basissjabloon wordt gebruikt als een basispagina voor documenten met een recordsjabloon. De stramienpagina kan informatie bevatten, zoals paginakoptekst, voettekst en paginanummer, die u kunt toepassen op het recorddocument. U kunt dergelijke informatie op document van verslag toepassen gebruikend basissjabloon voor auto het produceren van document van verslag. Met een basissjabloon kunt u de standaardeigenschappen van velden wijzigen.

Zorg ervoor dat u volgt [Basissjabloonconventies](#base-template-conventions) wanneer u basissjabloon ontwerpt.

## Basissjabloonconventies {#base-template-conventions}

Een basissjabloon wordt gebruikt om de kop-, voettekst-, opmaak- en vormgeving van een recorddocument te definiëren. De kop- en voettekst kunnen informatie bevatten zoals het bedrijfslogo en de copyrighttekst. De eerste basispagina in de basissjabloon wordt gekopieerd en gebruikt als een basispagina voor het recorddocument, die koptekst, voettekst, paginanummer of andere informatie bevat die op alle pagina&#39;s in het recorddocument moet worden weergegeven. Als u een basissjabloon gebruikt dat niet voldoet aan de conventies voor basissjablonen, wordt de eerste basispagina van het basissjabloon nog steeds gebruikt in het document met een recordsjabloon. U wordt ten zeerste aangeraden de basissjabloon te ontwerpen volgens de conventies en deze te gebruiken voor het automatisch genereren van een document met record.

**Hoofdpaginaconventies**

* In het basissjabloon moet u het basissubformulier een naam geven `AF_METATEMPLATE` en de basispagina als `AF_MASTERPAGE`.

* De stramienpagina met de naam `AF_MASTERPAGE` die zich onder `AF_METATEMPLATE` het basissubformulier krijgt de voorkeur voor het ophalen van koptekst-, voettekst- en opmaakgegevens.

* Indien `AF_MASTERPAGE` ontbreekt, wordt de eerste basispagina gebruikt die in het basissjabloon aanwezig is.

**Opmaakconventies voor velden**

* Als u een stijl wilt toepassen op de velden in het document met records, bevat de basissjabloon velden in het dialoogvenster `AF_FIELDSSUBFORM` subfrom under the `AF_METATEMPLATE` basissubformulier.

* De eigenschappen van deze velden worden toegepast op de velden in het recorddocument. Deze velden moeten `AF_<name of field in all caps>_XFO` naamgevingsconventie. De veldnaam voor het selectievakje moet bijvoorbeeld `AF_CHECKBOX_XFO`.

Ga als volgt te werk in AEM Designer om een basissjabloon te maken.

1. Klikken **Bestand > Nieuw**.
1. Selecteer de **Op basis van een sjabloon** -optie.

1. Selecteer de **Forms - Document of Record** categorie.
1. Selecteren **DoR-basissjabloon**.
1. Klikken **Volgende** en verstrekt de vereiste informatie.

1. (Optioneel) Wijzig de opmaak en weergave van velden die u wilt toepassen op de velden in het document met records.
1. Sla het formulier op.

U kunt het opgeslagen formulier nu gebruiken als een basissjabloon voor een recorddocument.
Wijzig of verwijder geen scripts in de basissjabloon.

**Basissjabloon wijzigen**

* Als u geen opmaak toepast op velden in de basissjabloon, is het raadzaam deze velden uit de basissjabloon te verwijderen, zodat alle upgrades naar de basissjabloon automatisch worden opgehaald.
* Verwijder scripts niet tijdens het wijzigen van een basissjabloon, voeg ze toe of wijzig ze niet.

>[!NOTE]
>
>Ontwerp het basissjabloon met conventies en volg de bovenstaande stappen strikt.

## Document met recordsjabloonconfiguratie {#document-of-record-template-configuration}

Configureer het document met de recordsjabloon van uw formulier, zodat uw klanten een afdrukvriendelijke kopie van het verzonden formulier kunnen downloaden. Een XDP-bestand fungeert als het document van een recordsjabloon. Het document van recordgebruikers dat wordt gedownload, wordt opgemaakt volgens de indeling die is opgegeven in het XDP-bestand.

Voer de volgende stappen uit om een document van verslag voor adaptieve vormen te vormen:

1. Klik in AEM auteurinstantie op **Forms > Forms en Documenten.**
1. Selecteer een formulier en klik op **Eigenschappen weergeven**.
1. Selecteer in het venster Eigenschappen de optie **Formuliermodel**.
U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.

   >[!NOTE]
   >
   >Selecteer op het tabblad Formuliermodel de optie **Schema** of **Geen** van de **Selecteren uit** vervolgkeuzelijst. **[!UICONTROL Document of record is not supported for XFA-based or adaptive forms with Form Template as form model.]**

1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel een van de volgende opties:

   **Geen** Selecteer deze optie als u het document met records voor het formulier niet wilt configureren.

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

1. Selecteer een deelvenster (hoofddeelvenster) in het recorddocument en selecteer vervolgens ![vormen](assets/configure.png).
1. Selecteren ![dortab](/help/forms/using/assets/dortab.png). Het tabblad Document of Record wordt weergegeven.
1. Selecteer de standaardsjabloon of een aangepaste sjabloon voor het weergeven van het document met records. Als u de standaardsjabloon selecteert, wordt een miniatuurvoorvertoning van het recorddocument weergegeven onder de vervolgkeuzelijst Sjabloon.

   ![brandingsjabloon](/help/forms/using/assets/brandingtemplateupdate.png)

   Als u een aangepaste sjabloon wilt selecteren, bladert u naar een geselecteerde XDP op uw AEM Forms-server. Als u een sjabloon wilt gebruiken die nog niet op uw AEM Forms-server staat, moet u de XDP eerst uploaden naar uw AEM Forms-server.

### Eigenschappen basispagina (#master-page-properties)

Afhankelijk van het feit of u een standaardsjabloon of een aangepaste sjabloon selecteert, worden sommige of alle volgende eigenschappen van de basispagina weergegeven op het tabblad Document van record, zoals in de bovenstaande afbeelding wordt getoond. Geef deze op de juiste manier op:

* **Logoafbeelding**: U kunt kiezen of u het logo wilt gebruiken in het adaptieve formulier, een afbeelding kiezen in DAM of een afbeelding uploaden vanaf uw computer.
* **Formuliertitel**
* **Koptekst**
* **Label voor afwijzing**
* **Disclaimer**
* **Disclaimtekst**

  <!--
    * **Accent Color**: The color in which header text and separator lines are rendered in the document or record PDF
    * **Font Family**: Font family of the text in the document of record PDF
    * **For Check Box and Radio Button components, show only the selected values**
    * **Separator for multiple selected value(s)**
    * **Include form objects that are not bound to data model**
    * **Exclude hidden fields from the document of record**
    * **Hide description of panels**
    -->

  Als de aangepaste XDP-sjabloon die u selecteert meerdere stramienpagina&#39;s bevat, worden de eigenschappen voor deze pagina&#39;s weergegeven in het dialoogvenster **[!UICONTROL content]** van de **[!UICONTROL Document of Record]** tab.

  ![Eigenschappen basispagina](assets/master-page-properties.png)

  Tot de eigenschappen van de basispagina behoren Logo Image, Header Text, Form Title, Disclaimer Label en Disclaimer Text. U kunt adaptieve formulier- of XDP-sjablooneigenschappen toepassen op het Document of Record. AEM Forms past de sjablooneigenschappen standaard toe op het Document of Record. U kunt ook aangepaste waarden definiëren voor de eigenschappen van de basispagina. Ga voor informatie over het toepassen van meerdere stramienpagina&#39;s in een document met records naar [Meerdere stramienpagina&#39;s toepassen op een document met records](#apply-multiple-master-pages-dor).

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

1. Selecteer Gereed om de wijzigingen in de branding op te slaan.

## Tabel- en kolomindelingen voor deelvensters in document van record {#table-and-column-layouts-for-panels-in-document-of-record}

Het aangepaste formulier kan lang zijn en meerdere formuliervelden bevatten. U wilt een document met records mogelijk niet opslaan als een exacte kopie van het aangepaste formulier. U kunt nu een tabel- of kolomindeling kiezen om een of meer adaptieve formulierdeelvensters op te slaan in het document met de recordindeling PDF.

Voordat u een recorddocument genereert, kiest u in de instellingen van een deelvenster de optie Lay-out voor het document van record voor dat deelvenster als tabel of kolom. De velden in het deelvenster worden op basis van de indeling in het recorddocument ingedeeld.

![Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records](assets/dortablelayout.png)

Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records

![Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records](assets/dorcolumnlayout.png)

Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records

## Document met recordinstellingen {#document-of-record-settings}

Met documenten met recordinstellingen kunt u opties kiezen die u wilt opnemen in het document met records. Een bank accepteert bijvoorbeeld naam, leeftijd, socialezekerheidsnummer en telefoonnummer in een formulier. Het formulier genereert een bankrekeningnummer en filiaalgegevens. U kunt ervoor kiezen alleen de naam, het socialezekerheidsnummer, de bankrekening en de filiaalgegevens in een document met gegevens weer te geven.

Het document met recordinstellingen van een component is beschikbaar onder de eigenschappen. Als u de eigenschappen van een component wilt openen, selecteert u de component en klikt u op ![cmppr](assets/cmppr.png) in de overlay. De eigenschappen worden vermeld in de zijbalk en u kunt de volgende instellingen erin vinden.

**Instellingen op veldniveau**

* **Uitsluiten van document van record**: Als u de eigenschap true instelt, wordt het veld uitgesloten van het recorddocument. Dit is een scriptbare eigenschap met de naam `excludeFromDoR`. Het gedrag hangt af van **Velden uitsluiten van DoR indien verborgen** eigenschap op formulierniveau.

* **Deelvenster weergeven als tabel:** Als u de eigenschap instelt, wordt het deelvenster weergegeven als een tabel in een document met record als het deelvenster minder dan 6 velden bevat. Alleen van toepassing op het deelvenster.
* **Titel van record uitsluiten:** Als u de eigenschap instelt, wordt de titel van het deelvenster/de tabel uitgesloten van het recorddocument. Alleen van toepassing op deelvenster en tabel.
* **Omschrijving uitsluiten van document van record:** Als u de eigenschap instelt, wordt de beschrijving van het deelvenster/de tabel niet opgenomen in het recorddocument. Alleen van toepassing op deelvenster en tabel.
* **[!UICONTROL Pagination]** > **[!UICONTROL Place]**: hiermee bepaalt u waar u het deelvenster wilt plaatsen.
   * **[!UICONTROL Place]** > **[!UICONTROL Following Previous]**: Hiermee plaatst u het deelvenster achter het vorige object in het bovenliggende deelvenster.
   * **[!UICONTROL Place]** > **[!UICONTROL In Content Area]** > Naam van inhoudsgebied: plaatst het deelvenster in het opgegeven inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Next Content Area]**: Hiermee plaatst u het deelvenster boven aan het volgende inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Content Area]** > Naam van inhoudsgebied: plaatst het deelvenster boven aan het opgegeven inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL On Page]** > Naam van stramienpagina: plaatst het deelvenster op de opgegeven pagina. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Next Page]**: Hiermee plaatst u het deelvenster boven aan de volgende pagina. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Page]** > Naam van stramienpagina: plaatst het deelvenster boven aan de pagina wanneer de opgegeven pagina wordt weergegeven. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
* **[!UICONTROL Pagination]** > **[!UICONTROL After]**: Hiermee bepaalt u welk gebied moet worden gevuld nadat een deelvenster is geplaatst. De volgende velden zijn beschikbaar in het dialoogvenster **[!UICONTROL After]** sectie:
   * **[!UICONTROL After]** > **[!UICONTROL Continue Filling Parent]**: Hiermee gaat u door met het samenvoegen van gegevens voor alle objecten die nog in het bovenliggende deelvenster moeten worden ingevuld.
   * **[!UICONTROL After]** > **[!UICONTROL Go to Next Content Area]**: Het volgende inhoudsgebied wordt gevuld nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Content Area]** > Naam van inhoudsgebied: begint het opgegeven inhoudsgebied te vullen nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Next Page]**: Hiermee wordt het vullen van de volgende pagina gestart nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Page]** > Naam van pagina: begint de opgegeven pagina te vullen nadat het deelvenster is geplaatst.
* **[!UICONTROL Pagination]** > **[!UICONTROL Overflow]**: Hiermee stelt u een overloop in voor een deelvenster of een tabel die meerdere pagina&#39;s beslaat. De volgende velden zijn beschikbaar in de **[!UICONTROL Overflow]** sectie:
   * **[!UICONTROL Overflow]** > **[!UICONTROL None]**: Hiermee wordt het vullen van de volgende pagina gestart. Als een pagina-einde niet automatisch wordt ingevoegd, [!DNL AEM Forms] voegt een pagina-einde toe.
   * **[!UICONTROL Overflow]** > **[!UICONTROL Go to Content Area]** > Naam van inhoudsgebied: begint het opgegeven inhoudsgebied te vullen.
   * **[!UICONTROL Overflow]** > **[!UICONTROL Go To Page]** > Naam van pagina: begint de opgegeven pagina te vullen.

  >[!NOTE]
  >
  > Pagineringseigenschap is niet beschikbaar voor adaptieve formulierfragmenten.

Voor informatie over het toepassen van pagina-einden en het toepassen van meerdere stramienpagina&#39;s in een document met records raadpleegt u [Pagina-einde toepassen in een document van record](#apply-page-breaks-in-dor) en [Meerdere stramienpagina&#39;s toepassen op een document met records](#apply-multiple-master-pages-dor).

**Instellingen voor formulierniveau**

* **[!UICONTROL BASIC]**
   * **Template:** U kunt de sjabloon Standaard of Aangepast selecteren.
     ![alt-tekst](image.png)
   * **Accentkleur:** U kunt de sjabloonkleur van het dialoogvenster [!UICONTROL Document of Record].
   * **Fontfamilie:** Selecteer een lettertype voor het dialoogvenster [!UICONTROL Document of Record] teksten.
   * **Inclusief niet-gebonden velden in DoR:** Als u de eigenschap instelt, worden niet-gebonden velden van het op schema gebaseerde adaptieve formulier opgenomen in [!UICONTROL Document of Record]. Standaard is dit waar.
   * **Velden uitsluiten van DoR indien verborgen:** De eigenschap instellen om de verborgen velden uit te sluiten [!UICONTROL Document of Record] bij het indienen van het formulier. Wanneer u [Revalidate op server](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), worden de verborgen velden opnieuw gecompileerd voordat deze worden uitgesloten van de [!UICONTROL Document of Record]
* **[!UICONTROL FORM FIELD PROPERTIES]**
   * Als u de optie inschakelt **Geef voor de component Selectievakje en Keuzerondje alleen de geselecteerde waarde(n) weer**, wordt alleen DoR-uitvoer gegenereerd met een of meer geselecteerde waarden.
   * U kunt Scheidingsteken selecteren voor meerdere geselecteerde waarden of u kunt een ander scheidingsteken kiezen.
   * Uitlijning opties
      * verticaal
      * Horizontaal
      * Hetzelfde als adaptief formulier
     >[!NOTE]
     > De verticale en horizontale uitlijning is alleen van toepassing op keuzerondjes en selectievakje
* **[!UICONTROL MASTER PAGE PROPERTIES]** Klik voor meer informatie over [Eigenschappen van basispagina](#master-page-properties-master-page-properties)

## Een pagina-einde toepassen in een document van record {#apply-page-breaks-in-dor}

U kunt pagina-einden in een Document van Verslag toepassen gebruikend veelvoudige methodes.

Een pagina-einde toepassen op een document met records:

1. Selecteer het deelvenster en selecteer ![Configureren](/help/forms/using/assets/configure.png)
1. Uitbreiden **[!UICONTROL Document of Record]** om de eigenschappen weer te geven.

1. In de **[!UICONTROL Pagination]** sectie, selecteert u ![Map](/help/forms/using/assets/folder-icon.png) in de **[!UICONTROL Place]** veld.
1. Selecteren **[!UICONTROL Top of Next page]** en selecteert u **[!UICONTROL Select]**. U kunt ook **[!UICONTROL Top of Page]** selecteert u de basispagina en selecteert u **[!UICONTROL Select]** om het pagina-einde toe te passen.
1. Selecteren ![Opslaan](/help/forms/using/assets/save_icon.png) om de eigenschappen op te slaan.

Het geselecteerde deelvenster gaat naar de volgende pagina.

## Meerdere stramienpagina&#39;s toepassen op een document met records {#apply-multiple-master-pages-dor}

Als de aangepaste XDP-sjabloon die u selecteert meerdere stramienpagina&#39;s bevat, worden de eigenschappen voor deze pagina&#39;s weergegeven in het dialoogvenster [!UICONTROL content] van de [!UICONTROL Document of Record] tab. Zie voor meer informatie [De brandinggegevens in het document van de record aanpassen](#customize-the-branding-information-in-document-of-record).

U kunt meerdere basispagina&#39;s toepassen op een Document of Record door verschillende basispagina&#39;s toe te passen op de componenten van een adaptief formulier. Gebruik de [Paginering](#document-of-record-settings) van de eigenschappen Document of Record om meerdere basispagina&#39;s toe te passen.

Hieronder ziet u hoe u meerdere stramienpagina&#39;s kunt toepassen op een document met records: u uploadt een XDP-sjabloon met vier stramienpagina&#39;s naar de [!DNL AEM Forms] server. [!DNL AEM Forms] Hiermee past u de sjablooneigenschappen standaard toe op het document of record. [!DNL AEM Forms] Hiermee past u ook de eerste eigenschappen van de basispagina in de sjabloon toe op het document of record.

Voer de volgende stappen uit om de eigenschappen van de tweede basispagina toe te passen op een deelvenster en de derde basispagina op de volgende deelvensters:

1. Selecteer het deelvenster om de tweede basispagina toe te passen en selecteer ![Configureren](assets/cmppr.png).
1. In de **[!UICONTROL Pagination]** sectie, selecteert u ![Map](/help/forms/using/assets/folder-icon.png) in de **[!UICONTROL Place]** veld.
1. Selecteren **[!UICONTROL On page]** selecteert u de tweede basispagina en selecteert u **[!UICONTROL Select]**.
AEM Forms past de tweede basispagina toe op het deelvenster en alle volgende deelvensters in het adaptieve formulier.
1. In de **[!UICONTROL Pagination]** sectie, selecteert u ![Map](/help/forms/using/assets/folder-icon.png) in de **[!UICONTROL After]** veld.
1. Selecteren **[!UICONTROL Go To page]**, selecteert u de derde basispagina en selecteert u **[!UICONTROL Select]**.
1. Selecteren ![Opslaan](/help/forms/using/assets/save_icon.png) om de eigenschappen op te slaan.
AEM Forms past de derde basispagina toe op het deelvenster en alle volgende deelvensters in het adaptieve formulier.

>[!NOTE]
>
> U kunt geen meerdere basispagina&#39;s toepassen op een document of record voor een adaptief formulierfragment.

## Belangrijke overwegingen bij het werken met een document {#key-considerations-when-working-with-document-of-record}

Houd rekening met de volgende overwegingen en beperkingen wanneer u werkt aan een document of record voor adaptieve formulieren.

* Document met recordsjablonen ondersteunt geen RTF-bestanden. Alle RTF-tekst in het statische adaptieve formulier of in de informatie die door de eindgebruiker is ingevuld, wordt daarom als onbewerkte tekst weergegeven in het document met de record.
* Documentfragmenten in een adaptieve vorm worden niet weergegeven in het recorddocument. Aangepaste formulierfragmenten worden echter ondersteund.
* Inhoudbinding in document van record die is gegenereerd voor een adaptief formulier op basis van een XML-schema, wordt niet ondersteund.
* De gelokaliseerde versie van document van verslag wordt gecreeerd op bestelling voor een scène wanneer de gebruiker om de teruggave van het document van verslag verzoekt. De lokalisatie van een recorddocument vindt plaats in combinatie met de lokalisatie van het adaptieve formulier. Zie voor meer informatie over lokalisatie van documenten met registratie en adaptieve formulieren [Aangepaste formulieren en recorddocumenten lokaliseren met AEM vertaalworkflow](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).

## Een aangepast XCI-bestand gebruiken

Met behulp van een XCI-bestand kunt u verschillende eigenschappen van een document instellen. <!-- Forms as a Cloud Service has a master XCI file.--> U kunt een aangepast XCI-bestand gebruiken om een of meer standaardeigenschappen te overschrijven die in het bestaande XCI-bestand zijn opgegeven. U kunt bijvoorbeeld een lettertype insluiten in een document of een gelabelde eigenschap inschakelen voor alle documenten. In de volgende tabel worden de XCI-opties aangegeven:

| XCI, optie | Beschrijving |
|--- |--- |
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Voor informatie over dit woordenboek raadpleegt u de [PDF Referentiehandleiding](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Voor informatie over dit woordenboek raadpleegt u de [PDF Referentiehandleiding](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/layout | Hiermee bepaalt u of de uitvoer één deelvenster is of gepagineerd. |
| config/present/pdf/compression/level | Hiermee geeft u de mate van compressie op die moet worden gebruikt bij het genereren van een PDF-document. |
| config/present/pdf/fontInfo/embed | Bepaalt het insluiten van lettertypen in het uitvoerdocument. |
| config/present/pdf/scriptModel | Bepaalt of XFA-specifieke informatie wordt opgenomen in het PDF-uitvoerdocument. |
| config/present/common/data/adjustData | Bepaalt of de XFA-toepassing de gegevens na het samenvoegen aanpast. |
| config/present/pdf/renderPolicy | Bepaalt of het genereren van pagina-inhoud wordt uitgevoerd op de server of uitgesteld aan de client. |
| config/present/common/locale | Geeft de standaardlandinstelling aan die in het uitvoerdocument wordt gebruikt. |
| config/present/destination | Wanneer deze elementen zich in een huidig element bevinden, geeft u de uitvoerindeling op. Wanneer deze zich in een element openAction bevindt, geeft dit de handeling op die moet worden uitgevoerd wanneer het document wordt geopend in een interactieve client. |
| config/present/output/type | Hiermee geeft u het type compressie op dat u wilt toepassen op een bestand of het type uitvoer dat u wilt maken. |
| config/present/common/temp/uri | Hier geeft u de URI van het formulier op. |
| config/present/common/template/base | Hiermee wordt een basislocatie voor URI&#39;s in het formulierontwerp opgegeven. Wanneer dit element ontbreekt of leeg is, wordt de locatie van het formulierontwerp als basis gebruikt. |
| config/present/common/log/to | Controls the location that log data or output data is written to. |
| config/present/output/to | Controls the location that log data or output data is written to. |
| config/present/script/currentPage | Hiermee geeft u de eerste pagina op wanneer het document wordt geopend. |
| config/present/script/exclude | Informeert Forms as a Cloud Service welke gebeurtenissen moeten worden genegeerd. |
| config/present/pdf/linearized | Controls whether the output PDF document is linearized. |
| config/present/script/runScripts | Hiermee bepaalt u welke set scripts Forms as a Cloud Service uitvoert. |
| config/present/pdf/tagged | Controls the include of tags into the output PDF document. Codes, in de context van PDF, zijn aanvullende informatie die in een document is opgenomen om de logische structuur van het document zichtbaar te maken. Tags zijn handig voor toegankelijkheidshulpmiddelen en voor het opnieuw opmaken. Een paginanummer kan bijvoorbeeld als een artefact worden gecodeerd, zodat een schermlezer het niet in het midden van de tekst activeert. Hoewel codes een document nuttiger maken, verhogen zij ook de grootte van het document en de verwerkingstijd om het tot stand te brengen. |
| config/present/pdf/fontInfo/alwaysEmbed | Hiermee geeft u een lettertype op dat in het uitvoerdocument wordt ingesloten. |
| config/present/pdf/fontInfo/neverEmbed | Hiermee geeft u een lettertype op dat nooit in het uitvoerdocument mag worden ingesloten. |
| config/present/pdf/pdfa/part | Hier geeft u het versienummer op van de PDF/A-specificatie waarmee het document compatibel is. |
| config/present/pdf/pdfa/amd | Geeft het wijzigingsniveau van de specificatie PDF/A aan. |
| config/present/pdf/pdfa/conformance | Hiermee wordt het compatibiliteitsniveau opgegeven met de PDF/A-specificatie. |
| config/present/pdf/version | Hiermee wordt de versie van het te genereren PDF-document opgegeven |
| config/present/pdf/version/map | Geeft de terugvalfonts voor het document aan |


<!--

### Use a custom XCI file in your AEM Forms environment

  1. Add the custom XCI file to your development project.
  1. Specify the following inline property:(/help/implementing/deploying/configuring-osgi.md)
  1. Deploy the project to your AEM Forms environment. <!--Cloud Service environment
  
-->

### Een aangepast XCI-bestand gebruiken in uw lokale Forms-ontwikkelomgeving

1. Upload het XCI-bestand naar uw lokale ontwikkelomgeving.
1. Openen <!--Cloud Service SDK--> configuratiebeheer. <!--The default URL is: <http://localhost:4502/system/console/configMgr>.-->
1. Zoek en open de **[!UICONTROL Adaptive Forms and Interactive Communication Web Channel]** configuratie.
1. Geef het pad van het XCI-bestand op en klik op **[!UICONTROL Save]**.


