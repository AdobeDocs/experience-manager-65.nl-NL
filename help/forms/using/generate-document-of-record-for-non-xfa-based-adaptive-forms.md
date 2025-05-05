---
title: Document met record genereren voor adaptieve formulieren
description: Verklaart hoe u document van verslag (DoR) voor adaptieve vormen kunt produceren.
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 7240897f-6b3a-427a-abc6-66310c2998f3
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '4155'
ht-degree: 0%

---

# Document met record genereren voor adaptieve formulieren of adaptieve formulierfragmenten {#generate-document-of-record-for-adaptive-forms}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=nl-NL) |
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

* [ Malplaatjes van de Vorm ](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template)
Hiermee kunt u een XFA-sjabloon selecteren voor het aangepaste formulier. Als u een XFA-sjabloon selecteert, kunt u het bijbehorende XDP-bestand gebruiken voor een recorddocument, zoals hierboven beschreven.

* [ Schema van XML ](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema)
Hiermee kunt u een XML-schemadefinitie selecteren voor het aangepaste formulier. Wanneer u een XML-schema selecteert voor het aangepaste formulier, kunt u:

   * Koppel een XFA-sjabloon voor een record. Zorg ervoor dat de gekoppelde XFA-sjabloon hetzelfde XML-schema gebruikt als het aangepaste formulier
   * Automatisch een recorddocument genereren

* Geen
Hiermee kunt u een adaptief formulier maken zonder een formuliermodel. Het recorddocument wordt automatisch gegenereerd voor het aangepaste formulier.

Wanneer u een formuliermodel selecteert, configureert u het document met records met de opties die beschikbaar zijn onder Document of Record Template Configuration. Zie [ Document van de Configuratie van het Malplaatje van het Verslag ](#document-of-record-template-configuration).

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

**Aangepaste vorm** Aangepaste vorm waarvoor u een document van verslag wilt produceren.

**Aangepast vormfragment** Aangepast vormfragment waarvoor u een document van verslag wilt produceren.

**malplaatje van de Basis (geadviseerd)** malplaatje XFA (XDP dossier) dat in AEM Designer wordt gecreeerd. De malplaatje van de basis wordt gebruikt om het stileren en het brandmerken informatie voor document van verslagmalplaatje te specificeren.

Zie [ malplaatje van de Basis van een document van verslag ](#base-template-of-a-document-of-record)

>[!NOTE]
>
>De basissjabloon van een document met record wordt ook wel de meta-sjabloon van een document met record genoemd.

**Document van verslagmalplaatje** XFA malplaatje (XDP dossier) dat van een adaptieve vorm wordt geproduceerd.

Zie [ Document van de Configuratie van het Malplaatje van het Verslag ](#document-of-record-template-configuration).

**gegevens van de Vorm** Informatie die in door een gebruiker in de adaptieve vorm wordt gevuld. Het samenvoegt met het document van verslagmalplaatje om het document van verslag te produceren.

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
   <td>Deelvenster <br /> </td>
   <td>Subform<br /> </td>
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

Ben zeker u volgt [ de overeenkomsten van het het malplaatjesjabloon van de Basis ](#base-template-conventions) wanneer u basissjabloon ontwerpt.

## Basissjabloonconventies {#base-template-conventions}

Een basissjabloon wordt gebruikt om de kop-, voettekst-, opmaak- en vormgeving van een recorddocument te definiëren. De kop- en voettekst kunnen informatie bevatten zoals het bedrijfslogo en de copyrighttekst. De eerste basispagina in de basissjabloon wordt gekopieerd en gebruikt als een basispagina voor het recorddocument, die koptekst, voettekst, paginanummer of andere informatie bevat die op alle pagina&#39;s in het recorddocument moet worden weergegeven. Als u een basissjabloon gebruikt dat niet voldoet aan de conventies voor basissjablonen, wordt de eerste basispagina van het basissjabloon nog steeds gebruikt in het document met een recordsjabloon. U wordt ten zeerste aangeraden de basissjabloon te ontwerpen volgens de conventies en deze te gebruiken voor het automatisch genereren van een document met record.

**Hoofdpaginaovereenkomsten**

* In de basissjabloon moet u het basissubformulier een naam geven `AF_METATEMPLATE` en de basispagina een naam geven als `AF_MASTERPAGE` .

* De basispagina met de naam `AF_MASTERPAGE` die zich onder het `AF_METATEMPLATE` basissubformulier bevindt, krijgt de voorkeur voor het ophalen van koptekst-, voettekst- en opmaakgegevens.

* Als `AF_MASTERPAGE` niet aanwezig is, wordt de eerste basispagina in de basissjabloon gebruikt.

**het Stijlen overeenkomsten voor gebieden**

* Als u stijl wilt toepassen op de velden in het document van de record, bevat de basissjabloon velden in het subformulier `AF_FIELDSSUBFORM` onder het `AF_METATEMPLATE` basissubformulier.

* De eigenschappen van deze velden worden toegepast op de velden in het recorddocument. Deze velden moeten de naamgevingsconventie `AF_<name of field in all caps>_XFO` volgen. De veldnaam voor het selectievakje moet bijvoorbeeld `AF_CHECKBOX_XFO` zijn.

Ga als volgt te werk in AEM Designer om een basissjabloon te maken.

1. Klik **Dossier > Nieuw**.
1. Selecteer **Gebaseerd op een malplaatje** optie.

1. Selecteer **Forms - Document van de categorie van het Verslag**.
1. Selecteer **het Malplaatje van de Basis DoR**.
1. Klik **daarna** en verstrek de vereiste informatie.

1. (Optioneel) Wijzig de opmaak en weergave van velden die u wilt toepassen op de velden in het document met records.
1. Sla het formulier op.

U kunt het opgeslagen formulier nu gebruiken als een basissjabloon voor een recorddocument.
Wijzig of verwijder geen scripts in de basissjabloon.

**wijzigend basissjabloon**

* Als u geen opmaak toepast op velden in de basissjabloon, is het raadzaam deze velden uit de basissjabloon te verwijderen, zodat alle upgrades naar de basissjabloon automatisch worden opgehaald.
* Verwijder scripts niet tijdens het wijzigen van een basissjabloon, voeg ze toe of wijzig ze niet.

>[!NOTE]
>
>Ontwerp het basissjabloon met conventies en volg de bovenstaande stappen strikt.

## Document met recordsjabloonconfiguratie {#document-of-record-template-configuration}

Configureer het document met de recordsjabloon van uw formulier, zodat uw klanten een afdrukvriendelijke kopie van het verzonden formulier kunnen downloaden. Een XDP-bestand fungeert als het document van een recordsjabloon. Het document van recordgebruikers dat wordt gedownload, wordt opgemaakt volgens de indeling die is opgegeven in het XDP-bestand.

Voer de volgende stappen uit om een document van verslag voor adaptieve vormen te vormen:

1. In AEM auteursinstantie, klik **Forms > Forms en Documenten.**
1. Selecteer een vorm, en klik **Eigenschappen van de Mening**.
1. In het venster van Eigenschappen, uitgezochte **Model van de Vorm**.
U kunt ook een formuliermodel selecteren wanneer u een formulier maakt.

   >[!NOTE]
   >
   >In het modellusje van de Vorm, zorg ervoor dat u **Schema** of **niets** van **selecteert Uitgezocht van** drop-down. **[!UICONTROL Document of record is not supported for XFA-based or adaptive forms with Form Template as form model.]**

1. Selecteer in het gedeelte Document of Record Template Configuration van het tabblad Formuliermodel een van de volgende opties:

   **niets** selecteer deze optie als u geen document van verslag voor de vorm wilt vormen.

   **associeerde het Malplaatje van de Vorm als Document van het Malplaatje van het Verslag** selecteer deze optie als u een XDP dossier hebt dat u als malplaatje voor het document van verslag wilt gebruiken. Als u deze optie selecteert, worden alle XDP-bestanden weergegeven die beschikbaar zijn in de AEM Forms-opslagplaats. Selecteer het juiste bestand.

   Het geselecteerde XDP-bestand wordt gekoppeld aan het adaptieve formulier.

   **produceer Document van Verslag** selecteer deze optie om een XDP dossier als basismalplaatje te gebruiken voor het bepalen van het stileren en de verschijning voor het document van verslag. Als u deze optie selecteert, worden alle XDP-bestanden weergegeven die beschikbaar zijn in de AEM Forms-opslagplaats. Selecteer het juiste bestand.

   >[!NOTE]
   >
   >Zorg ervoor dat het schema dat wordt gebruikt om een adaptief formulier en schema (gegevensschema) van XFA-formulieren te maken, hetzelfde zijn als:
   >
   >
   >
   >    * Het adaptieve formulier is gebaseerd op een schema
   >    * U gebruikt **het Malplaatje van de Vorm als Document van het Malplaatje van het Verslag** optie voor document van verslag
   >
   >

1. Klik **Gereed.**

## De brandinggegevens in het document van de record aanpassen {#customize-the-branding-information-in-document-of-record}

Tijdens het genereren van een recorddocument kunt u de brandinggegevens voor het recorddocument wijzigen op het tabblad Document of Record. Het tabblad Document of Record bevat opties zoals logo, weergave, lay-out, koptekst en voettekst, disclaimer en of u niet het selectievakje en keuzerondjes wilt inschakelen of niet.

Als u de brandinggegevens die u opgeeft op het tabblad Document of Record wilt lokaliseren, moet u ervoor zorgen dat de landinstelling van de browser correct is ingesteld. Voer de volgende stappen uit als u de brandinggegevens van een recorddocument wilt aanpassen:

1. Selecteer een paneel (wortelpaneel) in het document van verslag en selecteer dan ![ vormen ](assets/configure.png).
1. Selecteer ![ dortab ](/help/forms/using/assets/dortab.png). Het tabblad Document of Record wordt weergegeven.
1. Selecteer de standaardsjabloon of een aangepaste sjabloon voor het weergeven van het document met records. Als u de standaardsjabloon selecteert, wordt een miniatuurvoorvertoning van het recorddocument weergegeven onder de vervolgkeuzelijst Sjabloon.

   ![ brandingtemplate ](/help/forms/using/assets/brandingtemplateupdate.png)

   Als u een aangepaste sjabloon wilt selecteren, bladert u naar een geselecteerde XDP op uw AEM Forms-server. Als u een sjabloon wilt gebruiken die nog niet op uw AEM Forms-server staat, moet u de XDP eerst uploaden naar uw AEM Forms-server.

### Eigenschappen basispagina (#master-page-properties)

Afhankelijk van het feit of u een standaardsjabloon of een aangepaste sjabloon selecteert, worden sommige of alle volgende eigenschappen van de basispagina weergegeven op het tabblad Document van record, zoals in de bovenstaande afbeelding wordt getoond. Geef deze op de juiste manier op:

* **Beeld van het Logo**: U kunt of verkiezen om het logobeeld van de adaptieve vorm te gebruiken, één van DAM te kiezen, of één van uw computer te uploaden.
* **Titel van de Vorm**
* **Tekst van de Kopbal**
* **Etiket van de Schrapping**
* **Disclaimer**
* **Tekst van de Disclaimer**

  <!--
    * **Accent Color**: The color in which header text and separator lines are rendered in the document or record PDF
    * **Font Family**: Font family of the text in the document of record PDF
    * **For Check Box and Radio Button components, show only the selected values**
    * **Separator for multiple selected value(s)**
    * **Include form objects that are not bound to data model**
    * **Exclude hidden fields from the document of record**
    * **Hide description of panels**
    -->

  Als de aangepaste XDP-sjabloon die u selecteert meerdere stramienpagina&#39;s bevat, worden de eigenschappen van die pagina&#39;s weergegeven in de **[!UICONTROL content]** -sectie van het tabblad **[!UICONTROL Document of Record]** .

  ![ Hoofdpagina Eigenschappen ](assets/master-page-properties.png)

  Tot de eigenschappen van de basispagina behoren Logo Image, Header Text, Form Title, Disclaimer Label en Disclaimer Text. U kunt adaptieve formulier- of XDP-sjablooneigenschappen toepassen op het Document of Record. AEM Forms past de sjablooneigenschappen standaard toe op het Document of Record. U kunt ook aangepaste waarden definiëren voor de eigenschappen van de basispagina. Voor informatie over hoe te om veelvoudige hoofdpagina&#39;s in een Document van Verslag toe te passen, zie [ veelvoudige hoofdpagina&#39;s op een Document van Verslag ](#apply-multiple-master-pages-dor) toepassen.

  >[!NOTE]
  >
  >Als u een adaptief formuliersjabloon gebruikt dat is gemaakt met een versie van Designer ouder dan 6.3, zodat de eigenschappen Accentkleur en Lettertypefamilie werken, moet u ervoor zorgen dat het volgende aanwezig is in uw adaptieve formuliersjabloon onder het basissubformulier:

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

![ Gebieden in een paneel dat in een lijstlay-out in het document van verslag ](assets/dortablelayout.png) wordt teruggegeven

Velden in een deelvenster die zijn gerenderd in een tabelindeling in het document met records

![ Gebieden in een paneel dat in een kolomlay-out in het document van verslag ](assets/dorcolumnlayout.png) wordt teruggegeven

Velden in een deelvenster die zijn gerenderd in een kolomindeling in het document met records

## Document met recordinstellingen {#document-of-record-settings}

Met documenten met recordinstellingen kunt u opties kiezen die u wilt opnemen in het document met records. Een bank accepteert bijvoorbeeld naam, leeftijd, socialezekerheidsnummer en telefoonnummer in een formulier. Het formulier genereert een bankrekeningnummer en filiaalgegevens. U kunt ervoor kiezen alleen de naam, het socialezekerheidsnummer, de bankrekening en de filiaalgegevens in een document met gegevens weer te geven.

Het document met recordinstellingen van een component is beschikbaar onder de eigenschappen. Om tot de eigenschappen toegang te hebben een component, selecteer de component en klik ![ cmp ](assets/cmppr.png) in de bekleding. De eigenschappen worden vermeld in de zijbalk en u kunt de volgende instellingen erin vinden.

**het niveaumontages van het Gebied**

* **sluit van Document van Verslag** uit: Het plaatsen van het bezit waar sluit het gebied van verslag uit. Dit is een scripteigenschap met de naam `excludeFromDoR` . Zijn gedrag hangt van **gebieden van DoR uit als verborgen** bezit van het vormniveau.

* **het paneel van de Vertoning als lijst:** plaatsend het paneel van bezitsvertoningen als lijst in document van verslag als het paneel minder dan 6 gebieden in het heeft. Alleen van toepassing op het deelvenster.
* **sluit titel van Document van Verslag uit:** het plaatsen van het bezit sluit titel van het paneel/de lijst van document uit. Alleen van toepassing op deelvenster en tabel.
* **sluit beschrijving van Document van Verslag uit:** het plaatsen van het bezit sluit beschrijving van het paneel/de lijst van document uit. Alleen van toepassing op deelvenster en tabel.
* **[!UICONTROL Pagination]** > **[!UICONTROL Place]** : hiermee bepaalt u waar u het deelvenster wilt plaatsen.
   * **[!UICONTROL Place]** > **[!UICONTROL Following Previous]** : plaatst het deelvenster achter het vorige object in het bovenliggende deelvenster.
   * **[!UICONTROL Place]** > **[!UICONTROL In Content Area]** > Naam van inhoudsgebied: plaatst het deelvenster in het opgegeven inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Next Content Area]** : plaatst het deelvenster boven aan het volgende inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Content Area]** > Naam van inhoudsgebied: plaatst het deelvenster boven aan het opgegeven inhoudsgebied.
   * **[!UICONTROL Place]** > **[!UICONTROL On Page]** > Naam van stramienpagina: plaatst het deelvenster op de opgegeven pagina. Als een pagina-einde niet automatisch wordt ingevoegd, voegt [!DNL AEM Forms] een pagina-einde toe.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Next Page]** : plaatst het deelvenster boven aan de volgende pagina. Als een pagina-einde niet automatisch wordt ingevoegd, voegt [!DNL AEM Forms] een pagina-einde toe.
   * **[!UICONTROL Place]** > **[!UICONTROL Top of Page]** > Naam van stramienpagina: plaatst het deelvenster boven aan de pagina wanneer de opgegeven pagina wordt weergegeven. Als een pagina-einde niet automatisch wordt ingevoegd, voegt [!DNL AEM Forms] een pagina-einde toe.
* **[!UICONTROL Pagination]** > **[!UICONTROL After]** : hiermee bepaalt u welk gebied moet worden gevuld nadat een deelvenster is geplaatst. De volgende velden zijn beschikbaar in de sectie **[!UICONTROL After]** :
   * **[!UICONTROL After]** > **[!UICONTROL Continue Filling Parent]** : gaat door met het samenvoegen van gegevens voor alle objecten die nog in het bovenliggende deelvenster moeten worden ingevuld.
   * **[!UICONTROL After]** > **[!UICONTROL Go to Next Content Area]** : hiermee wordt het vullen van het volgende inhoudsgebied gestart nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Content Area]** > Naam van inhoudsgebied: begint het opgegeven inhoudsgebied te vullen nadat u het deelvenster hebt geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Next Page]** : hiermee wordt het vullen van de volgende pagina gestart nadat het deelvenster is geplaatst.
   * **[!UICONTROL After]** > **[!UICONTROL Go To Page]** > Naam van pagina: hiermee wordt het vullen van de opgegeven pagina gestart nadat het deelvenster is geplaatst.
* **[!UICONTROL Pagination]** > **[!UICONTROL Overflow]** : stelt een overloop in voor een deelvenster of een tabel die meerdere pagina&#39;s beslaat. De volgende velden zijn beschikbaar in de sectie **[!UICONTROL Overflow]** :
   * **[!UICONTROL Overflow]** > **[!UICONTROL None]** : begint de volgende pagina te vullen. Als een pagina-einde niet automatisch wordt ingevoegd, voegt [!DNL AEM Forms] een pagina-einde toe.
   * **[!UICONTROL Overflow]** > **[!UICONTROL Go to Content Area]** > Naam van inhoudsgebied: begint het opgegeven inhoudsgebied te vullen.
   * **[!UICONTROL Overflow]** > **[!UICONTROL Go To Page]** > Naam van pagina: begint de opgegeven pagina te vullen.

  >[!NOTE]
  >
  > Pagineringseigenschap is niet beschikbaar voor adaptieve formulierfragmenten.

Voor informatie over hoe te om pagina onderbrekingen toe te passen en veelvoudige hoofdpagina&#39;s in een Document van Verslag toe te passen, zie [ paginauze in een Document van Verslag toepassen ](#apply-page-breaks-in-dor) en [ veelvoudige hoofdpagina&#39;s op een Document van Verslag ](#apply-multiple-master-pages-dor) toepassen.

**het niveau van de Vorm montages**

* **[!UICONTROL BASIC]**
   * **Malplaatje:** u kunt het malplaatjeGebrek of Douane selecteren.

     ![ alt tekst ](image.png)
   * **de Kleur van de Actie:** u kunt de malplaatjeKleur van [!UICONTROL Document of Record] vooraf bepalen.
   * **Familie van de Doopvont:** selecteer het type van Doopvont voor de [!UICONTROL Document of Record] teksten.
   * **omvat ongebonden gebieden in DoR:** het plaatsen van het bezit omvat ongebonden gebieden van Schema gebaseerde adaptieve vorm in [!UICONTROL Document of Record]. Standaard is dit waar.
   * **sluit gebieden van DoR uit als verborgen:** plaats het bezit om de verborgen gebieden van [!UICONTROL Document of Record] bij vormvoorlegging uit te sluiten. Wanneer u [ toelaat verwerk op server ](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form) opnieuw, compileert de server de verborgen gebieden alvorens die gebieden van [!UICONTROL Document of Record] uit te sluiten
* **[!UICONTROL FORM FIELD PROPERTIES]**
   * Als u de optie **voor de component van de Doos van de Controle en van de Keuzerondje tikt, slechts de geselecteerde waarde(n)** toont, zal het output van DoR met slechts geselecteerde waarde(n) produceren.
   * U kunt Scheidingsteken selecteren voor meerdere geselecteerde waarden of u kunt een ander scheidingsteken kiezen.
   * Uitlijning opties
      * verticaal
      * Horizontaal
      * Hetzelfde als adaptief formulier

     >[!NOTE]
     > Verticale en horizontale uitlijning is alleen van toepassing voor     Keuzerondje en selectievakje
* **[!UICONTROL MASTER PAGE PROPERTIES]** klik voor meer informatie over [ eigenschappen van de Hoofdpagina ](#master-page-properties-master-page-properties)

## Een pagina-einde toepassen in een document van record {#apply-page-breaks-in-dor}

U kunt pagina-einden in een Document van Verslag toepassen gebruikend veelvoudige methodes.

Een pagina-einde toepassen op een document met records:

1. Selecteer het paneel en selecteer ![ vormen ](/help/forms/using/assets/configure.png)
1. Vouw **[!UICONTROL Document of Record]** uit om de eigenschappen weer te geven.

1. In de **[!UICONTROL Pagination]** sectie, uitgezochte ![ Omslag ](/help/forms/using/assets/folder-icon.png) op het **[!UICONTROL Place]** gebied.
1. Selecteer **[!UICONTROL Top of Next page]** en selecteer **[!UICONTROL Select]** . U kunt ook **[!UICONTROL Top of Page]** selecteren, de stramienpagina selecteren en **[!UICONTROL Select]** selecteren om het pagina-einde toe te passen.
1. Selecteer ![ sparen ](/help/forms/using/assets/save_icon.png) om de eigenschappen te bewaren.

Het geselecteerde deelvenster gaat naar de volgende pagina.

## Meerdere stramienpagina&#39;s toepassen op een document met records {#apply-multiple-master-pages-dor}

Als de aangepaste XDP-sjabloon die u selecteert meerdere stramienpagina&#39;s bevat, worden de eigenschappen van die pagina&#39;s weergegeven in de [!UICONTROL content] -sectie van het tabblad [!UICONTROL Document of Record] . Voor meer informatie, zie [ de branding informatie in document van verslag ](#customize-the-branding-information-in-document-of-record) aanpassen.

U kunt meerdere basispagina&#39;s toepassen op een Document of Record door verschillende basispagina&#39;s toe te passen op de componenten van een adaptief formulier. Gebruik de [ sectie van de Paginering ](#document-of-record-settings) van het Document van de eigenschappen van het Verslag om veelvoudige hoofdpagina&#39;s toe te passen.

Hieronder ziet u hoe u meerdere stramienpagina&#39;s kunt toepassen op een document met records:
U uploadt een XDP-sjabloon met vier stramienpagina&#39;s naar de [!DNL AEM Forms] -server. [!DNL AEM Forms] past de sjablooneigenschappen standaard toe op het document of record. [!DNL AEM Forms] past ook de eerste eigenschappen van de basispagina in de sjabloon toe op het Document of Record.

Voer de volgende stappen uit om de eigenschappen van de tweede basispagina toe te passen op een deelvenster en de derde basispagina op de volgende deelvensters:

1. Selecteer het paneel om de tweede hoofdpagina toe te passen en ![ te selecteren vorm ](assets/cmppr.png).
1. In de **[!UICONTROL Pagination]** sectie, uitgezochte ![ Omslag ](/help/forms/using/assets/folder-icon.png) op het **[!UICONTROL Place]** gebied.
1. Selecteer **[!UICONTROL On page]** , selecteer de tweede basispagina en selecteer **[!UICONTROL Select]** .
AEM Forms past de tweede basispagina toe op het deelvenster en alle volgende deelvensters in het adaptieve formulier.
1. In de **[!UICONTROL Pagination]** sectie, uitgezochte ![ Omslag ](/help/forms/using/assets/folder-icon.png) op het **[!UICONTROL After]** gebied.
1. Selecteer **[!UICONTROL Go To page]** , selecteer de derde basispagina en selecteer **[!UICONTROL Select]** .
1. Selecteer ![ sparen ](/help/forms/using/assets/save_icon.png) om de eigenschappen te bewaren.
AEM Forms past de derde basispagina toe op het deelvenster en alle volgende deelvensters in het adaptieve formulier.

>[!NOTE]
>
> U kunt geen meerdere basispagina&#39;s toepassen op een document of record voor een adaptief formulierfragment.

## Belangrijke overwegingen bij het werken met een document {#key-considerations-when-working-with-document-of-record}

Houd rekening met de volgende overwegingen en beperkingen wanneer u werkt aan een document of record voor adaptieve formulieren.

* Document met recordsjablonen ondersteunt geen RTF-bestanden. Alle RTF-tekst in het statische adaptieve formulier of in de informatie die door de eindgebruiker is ingevuld, wordt daarom als onbewerkte tekst weergegeven in het document met de record.
* Documentfragmenten in een adaptieve vorm worden niet weergegeven in het recorddocument. Aangepaste formulierfragmenten worden echter ondersteund.
* Inhoudbinding in document van record die is gegenereerd voor een adaptief formulier op basis van een XML-schema, wordt niet ondersteund.
* De gelokaliseerde versie van document van verslag wordt gecreeerd op bestelling voor een scène wanneer de gebruiker om de teruggave van het document van verslag verzoekt. De lokalisatie van een recorddocument vindt plaats in combinatie met de lokalisatie van het adaptieve formulier. Voor meer informatie over localisatie van document van verslag en adaptieve vormen zie [ Gebruikend AEM vertaalwerkschema om adaptieve vormen en document van verslag ](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md) te lokaliseren.

## Een aangepast XCI-bestand gebruiken

Met behulp van een XCI-bestand kunt u verschillende eigenschappen van een document instellen. <!-- Forms as a Cloud Service has a master XCI file.--> U kunt een aangepast XCI-bestand gebruiken om een of meer standaardeigenschappen te overschrijven die in het bestaande XCI-bestand zijn opgegeven. U kunt bijvoorbeeld een lettertype insluiten in een document of een gelabelde eigenschap inschakelen voor alle documenten. In de volgende tabel worden de XCI-opties aangegeven:

| XCI, optie | Beschrijving |
|--- |--- |
| config/present/pdf/creator | Hiermee wordt de maker van het document geïdentificeerd met het item Maker in het documentgegevenswoordenboek. Voor informatie over dit woordenboek, zie de [ gids van de Verwijzing van de PDF ](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
| config/present/pdf/producer | Hiermee wordt de documentproducent geïdentificeerd met behulp van het Producent-item in het documentinformatiewoordenboek. Voor informatie over dit woordenboek, zie de [ gids van de Verwijzing van de PDF ](https://opensource.adobe.com/dc-acrobat-sdk-docs/acrobatsdk/). |
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
1. Open het configuratiebeheer van <!--Cloud Service SDK--> . <!--The default URL is: <http://localhost:4502/system/console/configMgr>.-->
1. Zoek en open de **[!UICONTROL Adaptive Forms and Interactive Communication Web Channel]** -configuratie.
1. Geef het pad van het XCI-bestand op en klik op **[!UICONTROL Save]** .
