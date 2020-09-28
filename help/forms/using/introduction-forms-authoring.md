---
title: Inleiding tot het ontwerpen van adaptieve formulieren
seo-title: Inleiding tot het ontwerpen van adaptieve formulieren
description: AEM Forms biedt gebruiksvriendelijke maar toch krachtige interface voor het ontwerpen van adaptieve formulieren. Deze sjabloon biedt een groot aantal componenten en gereedschappen waarmee u formulieren kunt maken.
seo-description: AEM Forms biedt gebruiksvriendelijke maar toch krachtige interface voor het ontwerpen van adaptieve formulieren. Deze sjabloon biedt een groot aantal componenten en gereedschappen waarmee u formulieren kunt maken.
uuid: 3b150507-41b9-47c2-a94c-f85b903b2274
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: introduction, author
discoiquuid: ba70921e-db7e-43f6-902c-1065d3b13aef
docset: aem65
translation-type: tm+mt
source-git-commit: d324586eb1d4fb809bf87641001b92a1941e6548
workflow-type: tm+mt
source-wordcount: '3067'
ht-degree: 0%

---


# Inleiding tot het ontwerpen van adaptieve formulieren {#introduction-to-authoring-adaptive-forms}

## Overzicht {#overview}

Met adaptieve formulieren kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een intuïtieve gebruikersinterface en kant-en-klare componenten voor het maken van en werken met adaptieve formulieren. U kunt desgewenst een adaptief formulier maken op basis van een formuliermodel of -schema of zonder formuliermodel. Het is belangrijk om zorgvuldig het formuliermodel te kiezen dat niet alleen aan uw vereisten voldoet, maar ook uw bestaande infrastructurele investeringen en middelen uitbreidt. U kunt uit de volgende opties kiezen om een adaptief formulier te maken:

* **Een formuliergegevensmodel gebruiken**
   [Met gegevensintegratie](../../forms/using/data-integration.md) kunt u entiteiten en services integreren van verschillende gegevensbronnen in een formuliergegevensmodel waarmee u adaptieve formulieren kunt maken. Kies een formuliergegevensmodel als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

* **Met een XDP-formuliersjabloon** is een ideaal formuliermodel als u investeert in XFA-formulieren of XDP-formulieren. Dit biedt een directe manier om uw XFA-formulieren om te zetten in adaptieve formulieren. Bestaande XFA-regels blijven behouden in de bijbehorende adaptieve formulieren. De resulterende adaptieve formulieren ondersteunen XFA-constructies, zoals validaties, gebeurtenissen, eigenschappen en patronen.

* **Het gebruiken van een Definitie van het Schema van XML (XSD) of een schema JSON van het Schema** XML en JSON- schema&#39;s vertegenwoordigen de structuur waarin het gegeven wordt geproduceerd of door het achterste deelsysteem in uw organisatie verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het aangepaste formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de browser Inhoud wanneer u adaptieve formulieren maakt.

* **Geen of geen formuliermodel** gebruiken Aangepaste formulieren die met deze optie zijn gemaakt, gebruiken geen formuliermodel. De XML-gegevens die op basis van dergelijke formulieren worden gegenereerd, hebben een vlakke structuur met velden en bijbehorende waarden.

Zie Een adaptief formulier [maken voor meer informatie over het maken van een adaptief formulier](../../forms/using/creating-adaptive-form.md).

## UI voor het schrijven van adaptieve formulieren {#adaptive-form-authoring-ui}

De interface voor het optimaliseren van aanrakingen voor het ontwerpen van adaptieve formulieren is intuïtief en biedt:

* Functionaliteit voor slepen en neerzetten
* Standaardformuliercomponenten
* Geïntegreerde opslagplaats voor middelen

Wanneer u een nieuw formulier maakt of een bestaand adaptief formulier bewerkt, gebruikt u de volgende interface-elementen:

* [Zijbalk](#sidebar)
* [Pagina, werkbalk](#page-toolbar)
* [Component, werkbalk](#component-toolbar)
* [Aangepaste formulierpagina](#af-page)

![UI voor het schrijven van adaptieve formulieren](assets/formeditor.png)

**A.** Zijbalk **B.** Pagina, werkbalk **C.** Aangepaste formulierpagina

### Zijbalk {#sidebar}

Met de zijbalk kunt u

* Zie formulierinhoud zoals deelvensters, componenten, velden en indeling.
* Eigenschappen van componenten bewerken.
* Zoek, bekijk en gebruik middelen in uw AEM DAM-opslagplaats (Digital Asset Management).
* Voeg componenten toe aan uw formulier.

![Zijbalk](assets/sidebar-comps.png)

**A.** Inhoudsbrowser **B.** Eigenschappen browser **C.** Middelen browser **D.** Browser voor componenten

<!--Click to enlarge

](assets/sidebar-comps-1.png) -->

De zijbalk bestaat uit de volgende browsers:

* **De inhoudbrowser** In de inhoudbrowser kunt u de volgende informatie bekijken:

   * **Formulierobjecten** tonen de objecthiërarchie van het formulier. Auteurs kunnen naar specifieke formuliercomponenten navigeren door op dat element te tikken in de formulierobjectstructuur. Auteur kan objecten zoeken en opnieuw rangschikken vanuit deze structuur.

   * **Met gegevensmodelobjecten**kunt u de hiërarchie van het formuliermodel bekijken.
Hiermee kunt u formuliermodelelementen naar het aangepaste formulier slepen en neerzetten. De toegevoegde elementen worden automatisch geconverteerd naar formuliercomponenten met behoud van hun oorspronkelijke eigenschappen. U kunt gegevensmodelobjecten zien wanneer uw formulier gebruikmaakt van een XML-schema, JSON-schema of XDP-sjabloon.

* **Eigenschappenbrowser**

   Hiermee kunt u de eigenschappen van een component bewerken. De eigenschappen veranderen afhankelijk van een component. Eigenschappen van de adaptieve formuliercontainer weergeven:

   Selecteer een component, tik vervolgens op ![veldniveau](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]**, en tik vervolgens op ![cmr](assets/cmppr.png).

* **Bandenbrowser**

   Hiermee kunt u verschillende typen inhoud segmenteren, zoals afbeeldingen, documenten, pagina&#39;s, films, enzovoort.

* **Browser voor componenten**

   Bevat componenten die u kunt gebruiken om een adaptief formulier te maken. U kunt componenten van het aangepaste formulier naar het aangepaste formulier slepen om formulierelementen toe te voegen en toegevoegde elementen configureren volgens de vereisten. In de volgende tabel worden de componenten beschreven die in de componentbrowser worden weergegeven.

<table>
 <tbody>
  <tr>
   <th><strong>Component</strong></th>
   <th><strong>Functionaliteit</strong></th>
  </tr>
  <tr>
   <td>Adobe Sign Block</td>
   <td>Voegt een blok tekst met plaatsaanduidingen toe voor velden die moeten worden ingevuld tijdens het ondertekenen met Adobe Sign.</td>
  </tr>
  <tr>
   <td>Knop</td>
   <td>Voegt een knoop toe, die u kunt vormen om acties uit te voeren, zoals sparen, terugstellen, volgende gaan, vorige gaan, etc.</td>
  </tr>
  <tr>
   <td>Captcha</td>
   <td>Voegt CAPTCHA-validatie toe met Google reCAPTCHA-service. Zie CAPTCHA <a href="../../forms/using/captcha-adaptive-forms.md" target="_blank">gebruiken in adaptieve vormen</a>voor meer informatie.</td>
  </tr>
  <tr>
   <td>Diagram</td>
   <td>Hiermee voegt u een grafiek toe die u kunt gebruiken in adaptieve formulieren en documenten voor een visuele weergave van tweedimensionale gegevens in herhaalbare deelvensters en tabelrijen.</td>
  </tr>
  <tr>
   <td>Selectievakje</td>
   <td>Hiermee wordt een selectievakje toegevoegd.</td>
  </tr>
  <tr>
   <td>Datuminvoerveld</td>
   <td>Gebruik de component Datuminvoerveld in het formulier, zodat klanten dag, maand en jaar afzonderlijk in drie vakken kunnen invullen. U kunt de vormgeving van de component aanpassen en de datumnotatie wijzigen. U kunt uw klanten bijvoorbeeld datums laten invoeren in de notatie MM/DD/JJJJ of DD/MM/JJJJ.</td>
  </tr>
  <tr>
   <td>Datumkiezer</td>
   <td>Hiermee voegt u een kalender-veld toe waarin een datum wordt gekozen.</td>
  </tr>
  <tr>
   <td>Documentfragment</td>
   <td>Hiermee kunt u herbruikbare componenten van een correspondentie toevoegen.</td>
  </tr>
  <tr>
   <td>Fragmentgroep document</td>
   <td>Hiermee kunt u een groep gerelateerde documentfragmenten toevoegen die u in een lettertypesjabloon als één eenheid kunt gebruiken.</td>
  </tr>
  <tr>
   <td>Vervolgkeuzelijst</td>
   <td>Hiermee voegt u een vervolgkeuzelijst toe: één of meerdere selecties</td>
  </tr>
  <tr>
   <td>E-mail</td>
   <td><p>Hiermee voegt u een veld toe waarin u het e-mailadres kunt vastleggen. De component Email valideert standaard e-mailadressen met de volgende reguliere expressie.</p> <p><code>^[a-zA-Z0-9.!#$%&amp;’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$</code></p> </td>
  </tr>
  <tr>
   <td>Bestandsbijlage</td>
   <td><p>Hiermee voegt u een knop toe waarmee gebruikers door ondersteunende documenten kunnen bladeren en deze aan een formulier kunnen toevoegen. U kunt meerdere bestanden koppelen aan een component Bestandsbijlage.</p> <p><strong> Opmerking: </strong><ul> <li> Als u meerdere bestanden wilt koppelen aan een bestandsbijlage die is geopend in de Apple Safari-browser, selecteert u de bestanden één voor één en voegt u ze toe. U kunt niet meerdere bestanden tegelijk selecteren en koppelen.</li> <li>De component Bestandsbijlage ondersteunt een vooraf gedefinieerde set bestandsindelingen in adaptieve formulieren die zijn ingeschakeld voor Adobe Sign. Zie <a href="https://helpx.adobe.com/document-cloud/help/supported-file-formats-fill-sign.html#main-pars_text">Ondersteunde bestandsindelingen</a>voor meer informatie. </li> </ul></p> </td>
  </tr>
  <tr>
   <td>Lijst met bestandsbijlagen</td>
   <td>Hiermee voegt u een veld toe met alle bijlagen die zijn geüpload met de component Bestandsbijlage.</td>
  </tr>
  <tr>
   <td>Voettekst<br /> </td>
   <td>Hiermee voegt u de koptekst van de pagina toe, die doorgaans het logo van een bedrijf, de titel van het formulier en het overzicht bevat.<br /> </td>
  </tr>
  <tr>
   <td>Koptekst</td>
   <td>Hiermee voegt u de voettekst van de pagina toe die meestal copyrightinformatie en koppelingen naar andere pagina's bevat. </td>
  </tr>
  <tr>
   <td>Afbeelding</td>
   <td>Hiermee kunt u een afbeelding invoegen.</td>
  </tr>
  <tr>
   <td>Afbeeldingskeuze</td>
   <td>Hiermee kunnen uw klanten een afbeelding selecteren die informatie verschaft. U kunt de informatie gebruiken om de gepersonaliseerde diensten aan uw klanten te verlenen.</td>
  </tr>
  <tr>
   <td>Volgende knop</td>
   <td>Hiermee voegt u een knop toe waarmee u naar het volgende venster in een formulier kunt navigeren.</td>
  </tr>
  <tr>
   <td>Numeriek vak</td>
   <td>Hiermee wordt een veld toegevoegd voor het vastleggen van numerieke waarden</td>
  </tr>
  <tr>
   <td>Numerieke stap</td>
   <td>Gebruik Numerieke Stepper in uw formulier om uw klanten een numerieke waarde te laten invoeren die ze op basis van een vooraf gedefinieerde stap kunnen verhogen of verlagen.</td>
  </tr>
  <tr>
   <td>Deelvenster</td>
   <td><p>Hiermee voegt u een deelvenster of subdeelvenster toe.</p> <p>U kunt ook een deelvenstercomponent toevoegen vanaf de werkbalk van het bovenliggende deelvenster met de knop Deelvenster <span class="uicontrol"></code> toevoegen. U kunt ook een paneelspecifieke werkbalk toevoegen met de knop Werkbalk <span class="uicontrol">van deelvenster</code> toevoegen. U kunt de positie van de paneelwerkbalk configureren met behulp van het dialoogvenster Deelvenster bewerken.</code></code></p> </td>
  </tr>
  <tr>
   <td>Wachtwoordvak</td>
   <td>Hiermee voegt u een veld toe waarin u een wachtwoord kunt vastleggen.</td>
  </tr>
  <tr>
   <td>Vorige knop</td>
   <td>Hiermee voegt u een knop toe die gebruikers nodig hebben om terug te gaan naar de vorige pagina of het vorige deelvenster.</td>
  </tr>
  <tr>
   <td>Keuzerondje</td>
   <td>Hiermee voegt u keuzerondjes toe.</td>
  </tr>
  <tr>
   <td>Knop Opnieuw instellen</td>
   <td>Hiermee voegt u een knop toe waarmee u formuliervelden opnieuw kunt instellen.</td>
  </tr>
  <tr>
   <td>Knop Opslaan</td>
   <td>Hiermee voegt u een knop toe om formuliergegevens op te slaan.</td>
  </tr>
  <tr>
   <td>Krabbelhandtekening</td>
   <td>Hiermee voegt u een veld voor het vastleggen van scripthandtekeningen toe.</td>
  </tr>
  <tr>
   <td>Scheidingsteken</td>
   <td>Hiermee schakelt u visuele segregatie van deelvensters in het formulier in.</td>
  </tr>
  <tr>
   <td>Handtekeningstap</td>
   <td>Hiermee geeft u de informatie weer die in het formulier en de handtekeningvelden is opgegeven, zodat de gebruiker het formulier kan verifiëren en ondertekenen.</td>
  </tr>
  <tr>
   <td>Tekst</td>
   <td>Hiermee kunt u statische tekst opgeven.</td>
  </tr>
  <tr>
   <td>Verzendknop</td>
   <td>Voegt een verzendknop toe om het formulier naar de geconfigureerde verzendactie te verzenden.</td>
  </tr>
  <tr>
   <td>Samenvattingsstap</td>
   <td>Hiermee verzendt u het formulier en de samenvattingstekst die de auteurs opgeven nadat het formulier is verzonden. </td>
  </tr>
  <tr>
   <td>Overschakelen</td>
   <td>Voegt een schakelaar toe die een knevel uitvoert of laat/onbruikbaar maakt actie toe. U kunt niet meer dan twee opties in de component van de Schakelaar toevoegen. Aangezien een schakelaar slechts twee waarden kan hebben: Aan of Uit, verplicht is niet van toepassing. Er wordt minstens één waarde opgeslagen, ongeacht de gebruikersinvoer. <br /> </td>
  </tr>
  <tr>
   <td>Tabel</td>
   <td>Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. </td>
  </tr>
  <tr>
   <td>Telefoon</td>
   <td><p>Hiermee voegt u een veld toe waarin u het telefoonnummer kunt vastleggen. De component van de Telefoon staat auteurs toe om één van de volgende types van telefoonaantal te vormen. Elk type is gekoppeld aan een standaardreguliere expressie voor validatie.</p>
    <ul>
     <li>Type International wordt gevalideerd door <code>^[+][0-9]{0,14}$</code>.</li>
     <li>Het type USPhoneNumber wordt gevalideerd door <code>{'+1 ('999') '999-9999}</code>.</li>
     <li>Type UKPhoneNumber wordt gevalideerd door <code>text{'+'99 999 999 9999}</code>.</li>
     <li>Aangepast type biedt geen standaard validatiepatroon. Het neemt de waarde van het laatste geselecteerde type van telefoonaantal. U kunt ook uw eigen aangepaste validatiepatroon opgeven.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Voorwaarden en bepalingen<br /> </td>
   <td>Hiermee voegt u een veld toe waarin auteurs de voorwaarden kunnen opgeven die gebruikers kunnen bekijken voordat ze het formulier invullen.</td>
  </tr>
  <tr>
   <td>Tekstvak </td>
   <td><p>Voegt een tekstvak toe waarin een gebruiker de vereiste informatie kan opgeven. </p> <p>Standaard accepteert de component Tekstvak alleen onbewerkte tekst. U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Een tekstcomponent met RTF-functionaliteit biedt opties voor het toevoegen van kopteksten, het wijzigen van tekenstijlen (vet, cursief, onderstrepen van tekens), het maken van geordende en ongeordende lijsten, het wijzigen van de tekstachtergrond en tekstkleur en het toevoegen van hyperlinks. Als u RTF-tekst voor een tekstvak wilt inschakelen, schakelt u de optie RTF<strong> -tekst</strong> toestaan in de componenteigenschappen in.</p> </td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Hiermee geeft u een titel voor het aangepaste formulier op.</td>
  </tr>
  <tr>
   <td>Stap verifiëren</td>
   <td><p>Hiermee voegt u een tijdelijke aanduiding toe waarmee het ingevulde formulier wordt weergegeven ter verificatie door de gebruiker.</p> <p><strong>Opmerking</strong>: Het adaptieve formulier met de component Verify ondersteunt geen anonieme gebruikers. Het wordt ook afgeraden de component Verify te gebruiken in een adaptief formulierfragment.</p> </td>
  </tr>
 </tbody>
</table>

#### Aanbevolen procedures voor het werken met componenten {#best-practices}

U kunt de volgende tips en trucs gebruiken bij het werken met adaptieve formuliercomponenten:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Tik op de component en tik op ![cmp](assets/cmppr.png) om de eigenschappen van een component te configureren. Open vervolgens de eigenschappen van de component in de eigenschappenbrowser.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u op ![cmp](assets/cmppr.png)tikt, kunt u de naam van de component wijzigen door de waarde van het **[!UICONTROL Element Name]** veld te wijzigen in de eigenschappenbrowser. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.

* U kunt de eigenschap Titel van een adaptieve formuliercomponent inline wijzigen in de formuliereditor zonder de browser Eigenschappen te openen, zolang de titel maar zichtbaar is op het formulier. Daartoe:

   1. Tik om een component te selecteren die een **[!UICONTROL Title]** eigenschap heeft en waarvan de **[!UICONTROL Hide title]** eigenschap is uitgeschakeld.

   1. Tik op ![naam_6_3_bewerken](assets/aem_6_3_edit.png) om de titel bewerkbaar te maken.

   1. Wijzig de titel en tik op de Return-toets of tik ergens buiten de component om de wijzigingen op te slaan. Tik op Esc om de wijzigingen te verwijderen.

* Sommige adaptieve formuliercomponenten, zoals E-mail en Telefoon, bevatten validatiepatronen die niet in de verpakking staan. U kunt echter aangepaste validatie opgeven door het **[!UICONTROL Validation Pattern]** veld onder de accordeon Patronen bij te werken in de componenteigenschappen. Zie de componentbeschrijvingen in de bovenstaande tabel voor meer informatie over standaardvalidaties.

* Adaptieve formuliervelden, zoals Numeriek vak en E-mail, kunnen zo worden geconfigureerd dat ze speciale HTML5-invoertypen bevatten. Wanneer deze velden de focus hebben op mobiele apparaten en tablets, worden op het toetsenblok specifieke alfabet, getallen en tekens vóór weergegeven die doorgaans worden gebruikt voor het invoeren van informatie in de velden. Het helpt gebruikers informatie snel ingaan zonder het moeten tussen karakterreeksen op het toetsenbord van een knevel voorzien. Als u gespecialiseerde invoer voor een component wilt toestaan, schakelt u het **[!UICONTROL Use HTML Type Number]** selectievakje in de componenteigenschappen in.

* U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Als u tekst met opmaak wilt inschakelen voor een tekstvak, schakelt u het **[!UICONTROL Allow Rich Text]** selectievakje in de eigenschappen van de component in.

* U kunt de componenten van het Doos van de Tekst, E-mail, en van de Telefoon aan autofill waarden voor gebieden zoals naam, adres, creditcard, telefoon, en e-mail van de informatie toelaten die in browser autofill montages wordt opgeslagen. Selecteer deze functie **[!UICONTROL Enable Autofill]** in de componenteigenschappen en selecteer een **[!UICONTROL Autofill Attribute]**. Wanneer een gebruiker een adaptief formulier invult, worden de waarden voorgesteld vanuit het profiel Automatisch vullen in de browser of op basis van de waarden die eerder door de gebruiker zijn ingevuld. Automatisch vullen werkt alleen als de instellingen voor automatisch vullen in de browser van de gebruiker zijn ingeschakeld.

* Geef waarden voor keuzerondjes en selectievakjes op in de `{value}={text}` indeling in componenteigenschappen.
* Met de component Bestandsbijlage kan een gebruiker standaard slechts één bestand bijvoegen. U kunt de componenteigenschappen echter configureren om meerdere bijlagen te ondersteunen. Als een gebruiker meerdere bestanden met dezelfde bestandsnaam bijvoegt, kunnen er bovendien problemen optreden in de bijlagen. Daarom wordt aanbevolen een unieke id te koppelen voor elke verzonden bijlage bij het verzenden van het formulier. Daartoe:

   1. Navigeer op uw AEM Forms-server naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
   1. Zoeken en tikken **[!UICONTROL Adaptive Forms Configuration Service]**.
   1. Schakel in het dialoogvenster Adaptive Forms Configuration Service de optie **[!UICONTROL Make File Names Unique]**. Standaard is dit uitgeschakeld.

* Als u gebruikers wilt toestaan een PDF toe te voegen met een Safari-browser, zorgt u ervoor dat **application/pdf** wordt toegevoegd aan de eigenschap Ondersteunde bestandstypen van de component Bestandsbijlage. Adaptieve formulieren die zijn gemaakt met de vorige AEM Forms-versie bevatten mogelijk **.pdf** in plaats van **application/pdf** in de eigenschap Ondersteunde bestandstypen.

Zie [Aanbevolen werkwijzen voor het werken met adaptieve formulieren](/help/forms/using/adaptive-forms-best-practices.md)voor meer tips over het werken met adaptieve formulieren.

>[!NOTE]
>
>Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.

### Pagina, werkbalk {#page-toolbar}

De pagina-werkbalk boven in het scherm bevat opties waarmee u een voorbeeld van het formulier kunt bekijken, de eigenschappen van het formulier kunt wijzigen en de indeling van het formulier kunt bewerken. U kunt een voorbeeld van het formulier bekijken wanneer u het maakt en wijzigingen aanbrengen. In de paginabooltoolbar, ziet u:

* **Zijpaneel** in-/ ![uitschakelen](assets/toggle-side-panel.png): Hiermee kunt u Zijbalk tonen of verbergen.

* **Pagina-informatie** ![thema-opties](assets/theme-options.png): Hiermee kunt u pagina-eigenschappen weergeven, een formulier publiceren/publiceren, een formulierwerkstroom starten en het formulier openen in een klassieke gebruikersinterface.

* **Emulatorliniaal**![](assets/ruler.png): Hiermee kunt u het uiterlijk van een formulier emuleren voor verschillende weergavegrootten, zoals tablets en telefoons.

* **Bewerken**: Hiermee kunt u andere modi selecteren, zoals: **[!UICONTROL Edit]**, **[!UICONTROL Style]**, **[!UICONTROL Developer]** en **[!UICONTROL Design]**.

   * **Bewerken**: Hiermee kunt u de eigenschappen van het formulier en de componenten ervan bewerken. U kunt bijvoorbeeld een component toevoegen, een afbeelding neerzetten en verplichte velden opgeven.
   * **Stijl**: Hiermee kunt u de vormgeving van componenten van het formulier opmaken. In de stijlmodus kunt u bijvoorbeeld een deelvenster selecteren en de achtergrondkleur ervan opgeven.

   * **Ontwikkelaar**: Hiermee kan een ontwikkelaar:

      * Ontdek waaruit de formulieren bestaan.
      * Foutopsporing waar en wanneer gebeurt, wat weer helpt om problemen op te lossen.
   * **Ontwerp**. Hiermee kunt u aangepaste componenten, of componenten buiten het vak die niet in het zijpaneel staan, in- of uitschakelen.


* **Voorvertoning**: Hiermee kunt u een voorbeeld bekijken van de weergave van het formulier wanneer u het publiceert.

### Component, werkbalk {#component-toolbar}

![Component-werkbalk in de aanraakinterface](assets/component-toolbar.png)

Wanneer u een component selecteert, ziet u een werkbalk waarin u de component kunt bewerken. U krijgt opties om, eigenschappen van de componenten te snijden te kleven, te bewegen en te specificeren. U kunt kiezen uit de volgende opties:

A.**Configureren**: Wanneer u tikt **[!UICONTROL Configure]**, zijn componenteigenschappen zichtbaar in de zijbalk. Als u deze eigenschappen configureert, kunt u de ervaring voor het vastleggen van gegevens aanpassen. U kunt de elementnaam van de component wijzigen en de labeltekst opgeven in het veld Titel van de component. Met elementnaam kunt u waarden vastleggen die gebruikers invoeren met de component. In de componenteigenschappen geeft u het gedrag van de component op en beheert u de gebruikersinvoer. Configureer eigenschappen in de zijbalk om gebruikersgegevens vast te leggen en te gebruiken voor verdere verwerking. Met eigenschappen voor adaptieve formuliercontainers kunt u clientbibliotheken, indelingen, thema&#39;s, Document of Record-instellingen, opslaginstellingen, verzendinstellingen en metagegevensinstellingen opgeven.

B.**Kopiëren**: Met de optie Kopiëren kunt u een component kopiëren en op andere plaatsen in het formulier plakken. Wanneer u een component plakt, krijgt de geplakte component een nieuwe elementnaam maar behoudt deze de eigenschappen van de gekopieerde component.

C.**Knippen**: Met de optie Knippen kunt u een component in het aangepaste formulier van de ene naar de andere plaats verplaatsen.

D. **Verwijderen**: Hiermee kunt u de component uit het formulier verwijderen.

E. **Invoegen**: Hiermee kunt u een component invoegen boven de geselecteerde component.

F. **Plakken**: Hiermee kunt u de component die u hebt geknipt of gekopieerd, plakken met de hierboven beschreven opties.

G. **Regels** bewerken: Hiermee opent u de regeleditor. Zie [Regeleditor](../../forms/using/rule-editor.md)voor meer informatie.

H. **Groep**: Hiermee kunt u meerdere componenten selecteren als u meerdere componenten tegelijk wilt knippen, kopiëren of plakken.

I. **Bovenliggend element**: Hiermee kunt u het bovenliggende element van een component selecteren. Een tekstveld bevindt zich bijvoorbeeld binnen een subsectie, die zich in een sectie bevindt. De sectie bevindt zich in het hoofddeelvenster van de hulplijn en de adaptieve formuliercontainer is het bovenliggende element van een hoofddeelvenster van de hulplijn. Voor een component, kunt u alle opties zien met hiërarchie gesorteerd onderaan-op.

Als u bijvoorbeeld tikt **[!UICONTROL Parent]** voor een tekstvak, kunt u zien:

* Onderafdeling
* Sectie
* guideRootPanel
* Container voor adaptieve vorm

J. **Overige**: Biedt meer opties voor het werken met de geselecteerde component.

* SOM-expressie weergeven
* Een deelvenster opslaan als fragment (alleen voor deelvensters)
* Onderliggend deelvenster toevoegen (alleen voor deelvensters)
* Deelvensterwerkbalk toevoegen (alleen voor deelvensters)
* Vervangen (niet voor deelvensters)

### Aangepaste formulierpagina {#af-page}

De aangepaste formulierpagina is het daadwerkelijke formulier. Het is net als elke andere WCM-pagina die als WCM- `cq:Page` component is gemodelleerd. In de volgende afbeelding ziet u de inhoudsstructuur van een adaptief formulier.

![Inhoudsstructuur van een aangepaste WCM-pagina](assets/afstructure.png)

De inhoudsstructuur bevat doorgaans de volgende primaire componenten:

* **guideContainer**: De basis van een adaptief formulier, gemarkeerd als **[!UICONTROL Start of adaptive form]** in de gebruikersinterface van het adaptieve formulier. In deze component kunt u het volgende opgeven:

   * *Mobiele lay-out van het adaptieve formulier*: Hiermee definieert u de weergave van het formulier op mobiele apparaten.
   * *Bedankt, pagina*: Hiermee definieert u de pagina waarop de gebruiker na het verzenden van het formulier wordt omgeleid.
   * *Handeling* verzenden: Hiermee bepaalt u hoe het formulier op de server wordt verwerkt wanneer de gebruiker het formulier verzendt.
   * *Stijlen*: Hiermee geeft u het pad op naar het CSS-bestand dat wordt gebruikt om de weergave van het formulier aan te passen.

* **rootPanel:** Het hoofddeelvenster van een adaptief formulier. Het kan subdeelvensters onder de puntenknoop bevatten. Aan elk deelvenster, inclusief het hoofddeelvenster, kan een lay-out zijn gekoppeld. De indeling van het deelvenster bepaalt de indeling van het formulier. In de schermindeling Accordeon worden de items ervan bijvoorbeeld ingedeeld als Accordion-stappen.

* **werkbalk:** Een adaptieve formuliercontainer heeft een bijbehorende algemene werkbalk, die algemeen is voor het formulier. Deze werkbalk kan worden toegevoegd met de **[!UICONTROL Add Toolbar]** handeling in de bewerkbalk, waarmee auteurs handelingen kunnen toevoegen, zoals Verzenden, Opslaan, Herstellen enzovoort.

* **activa:** Dit knooppunt bevat aanvullende informatie die wordt gebruikt voor het ontwerpen van formulieren. Bijvoorbeeld details van het formuliermodel, lokalisatiedetails, enzovoort).

