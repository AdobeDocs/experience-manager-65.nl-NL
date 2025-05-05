---
title: Inleiding tot het ontwerpen van adaptieve formulieren
description: AEM Forms biedt gebruiksvriendelijke maar toch krachtige interface voor het ontwerpen van adaptieve formulieren. Deze sjabloon biedt een groot aantal componenten en gereedschappen waarmee u formulieren kunt maken.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: introduction, author
docset: aem65
feature: Adaptive Forms
exl-id: 935b734c-6fb1-45e8-8515-e98c8b85286c
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '3086'
ht-degree: 0%

---

# Inleiding tot het ontwerpen van adaptieve formulieren {#introduction-to-authoring-adaptive-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/introduction-forms-authoring.html) |
| AEM 6,5 | Dit artikel |


## Overzicht {#overview}

Met adaptieve formulieren kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een intuïtieve gebruikersinterface en kant-en-klare componenten voor het maken van en werken met adaptieve formulieren. U kunt desgewenst een adaptief formulier maken op basis van een formuliermodel of -schema of zonder formuliermodel. Het is belangrijk om zorgvuldig het formuliermodel te kiezen dat niet alleen aan uw vereisten voldoet, maar ook uw bestaande infrastructurele investeringen en middelen uitbreidt. U kunt uit de volgende opties kiezen om een adaptief formulier te maken:

* **Gebruikend een model van vormgegevens**
  [ de integratie van Gegevens ](../../forms/using/data-integration.md) laat u entiteiten en de diensten van verschillende gegevensbronnen in aan een model integreren van vormgegevens dat u kunt gebruiken om adaptieve vormen tot stand te brengen. Kies een formuliergegevensmodel als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.

* **Gebruikend een Malplaatje van de Vorm XDP**
Het is een ideaal formuliermodel als u investeert in XFA-gebaseerde of XDP-formulieren. Dit biedt een directe manier om uw XFA-formulieren om te zetten in adaptieve formulieren. Bestaande XFA-regels blijven behouden in de bijbehorende adaptieve formulieren. De resulterende adaptieve formulieren ondersteunen XFA-constructies, zoals validaties, gebeurtenissen, eigenschappen en patronen.

* **Gebruikend een Definitie van het Schema van XML (XSD) of een Schema JSON**
De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het aangepaste formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de browser Inhoud wanneer u adaptieve formulieren maakt.

* **Gebruikend niets of zonder een vormmodel**
Voor adaptieve formulieren die met deze optie worden gemaakt, wordt geen formuliermodel gebruikt. De XML-gegevens die op basis van dergelijke formulieren worden gegenereerd, hebben een vlakke structuur met velden en bijbehorende waarden.

Voor meer informatie over het creëren van een adaptieve vorm, zie [ Creërend een adaptieve vorm ](../../forms/using/creating-adaptive-form.md).

## UI voor het schrijven van adaptieve formulieren {#adaptive-form-authoring-ui}

De interface voor het optimaliseren van aanrakingen voor het ontwerpen van adaptieve formulieren is intuïtief en biedt:

* Functionaliteit voor slepen en neerzetten
* Standaardformuliercomponenten
* Geïntegreerde opslagplaats voor middelen

Wanneer u een bestaand adaptief formulier maakt of bewerkt, gebruikt u de volgende UI-elementen:

* [Zijbalk](#sidebar)
* [Pagina, werkbalk](#page-toolbar)
* [Component, werkbalk](#component-toolbar)
* [Aangepaste formulierpagina](#af-page)

![ Aanpassings vorm authoring UI ](assets/formeditor.png)

**A.** Sidebar **B.** de toolbar van de Pagina **C.** Aangepaste vormpagina

### Zijbalk {#sidebar}

Met de zijbalk kunt u

* Zie formulierinhoud zoals deelvensters, componenten, velden en indeling.
* Eigenschappen van componenten bewerken.
* Zoek, bekijk en gebruik middelen in uw AEM DAM-opslagplaats (Digital Asset Management).
* Voeg componenten toe aan uw formulier.

![ Sidebar ](assets/sidebar-comps.png)

**A.** browser van de Inhoud **B.** browser van Eigenschappen **C.** browser van Assets **D.** Browser van Componenten

<!--Click to enlarge

](assets/sidebar-comps-1.png) -->

De zijbalk bestaat uit de volgende browsers:

* **browser van de Inhoud**
In de inhoudbrowser kunt u zien

   * **Objecten van de Vorm**
Hiermee geeft u de objecthiërarchie van het formulier weer. Auteurs kunnen naar specifieke formuliercomponenten navigeren door op dat element te tikken in de formulierobjectstructuur. Auteur kan objecten zoeken en opnieuw rangschikken vanuit deze structuur.

   * **Modelvoorwerpen van Gegevens**
Hiermee kunt u de hiërarchie van het formuliermodel bekijken.
Hiermee kunt u formuliermodelelementen naar het aangepaste formulier slepen en neerzetten. De toegevoegde elementen worden automatisch geconverteerd naar formuliercomponenten met behoud van hun oorspronkelijke eigenschappen. U kunt gegevensmodelobjecten zien wanneer uw formulier gebruikmaakt van een XML-schema, JSON-schema of XDP-sjabloon.

* **browser van Eigenschappen**

  Hiermee kunt u de eigenschappen van een component bewerken. De eigenschappen worden gewijzigd op basis van een component. Eigenschappen van de adaptieve formuliercontainer weergeven:

  Selecteer een component, dan uitgezocht ![ gebied-niveau ](assets/field-level.png) > **[!UICONTROL Adaptive Form Container]**, en selecteer dan ![ cmp ](assets/cmppr.png).

* **browser van Assets**

  Hiermee kunt u verschillende typen inhoud segmenteren, zoals afbeeldingen, documenten, pagina&#39;s, films, enzovoort.

* **browser van Componenten**

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
   <td>Voegt CAPTCHA-validatie toe met de Google reCAPTCHA-service. Voor details, zie <a href="../../forms/using/captcha-adaptive-forms.md" target="_blank"> Gebruikend CAPTCHA in adaptieve vormen </a>.</td>
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
   <td>Hiermee voegt u een kalenderveld toe waarin u een datum kunt selecteren.</td>
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
   <td><p>Hiermee voegt u een veld toe waarin u het e-mailadres kunt vastleggen. De component Email valideert standaard e-mailadressen met de volgende reguliere expressie.</p> <p><code>^[a-zA-Z0-9.!#$%&amp;'*+/=?^_&grave;{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$</code></p> </td>
  </tr>
  <tr>
   <td>Bestandsbijlage</td>
   <td><p>Hiermee voegt u een knop toe waarmee gebruikers door ondersteunende documenten kunnen bladeren en deze aan een formulier kunnen toevoegen. U kunt meerdere bestanden koppelen aan een component Bestandsbijlage. U kunt **[!UICONTROL Maximum File Size] &#x200B;** en **&#x200B; [!UICONTROL Supported File Types] &#x200B;** voor de gehechtheid in eigenschappen browser van de component ook specificeren. </p> <p><strong> Opmerking: </strong><ul> <li> De component biedt geen ondersteuning voor het koppelen van bestanden waarvan de bestandsnaam begint met tekens (.) en die de tekens \ / : * ? bevatten " &lt; &gt; | ; % $ of speciale bestandsnamen die zijn gereserveerd voor Windows-besturingssystemen zoals null, prn, con, lpt of com. </li> <li> Als u meerdere bestanden wilt koppelen aan een bestandsbijlage die is geopend in de Apple Safari-browser, selecteert u de bestanden één voor één en voegt u ze toe. U kunt niet meerdere bestanden tegelijk selecteren en koppelen.</li> <li>De component Bestandsbijlage ondersteunt een vooraf gedefinieerde set bestandsindelingen in adaptieve formulieren die zijn ingeschakeld voor Adobe Sign. Voor meer informatie, zie <a href="https://helpx.adobe.com/document-cloud/help/supported-file-formats-fill-sign.html#main-pars_text"> Gesteunde dossierformaten </a>. </li></ul></p> </td>
  </tr>
  <tr>
   <td>Lijst met bestandsbijlagen</td>
   <td>Hiermee voegt u een veld toe met alle bijlagen die zijn geüpload met de component Bestandsbijlage.</td>
  </tr>
  <tr>
   <td>Koptekst <br /> </td>
   <td>Voegt de paginakop toe die typisch embleem van een onderneming, titel van de vorm, en samenvatting omvat.<br /> </td>
  </tr>
  <tr>
   <td>Voettekst</td>
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
   <td><p>Hiermee voegt u een deelvenster of subdeelvenster toe.</p> <p>U kunt een paneelcomponent van de ouderpaneeltoolbar ook toevoegen gebruikend <span class="uicontrol"> toevoegt het Comité van het Kind</code> knop. Op dezelfde manier kunt u een paneel-specifieke toolbar toevoegen gebruikend <span class="uicontrol"> toevoegt Toolbar van het Comité</code> knop. U kunt de positie van de paneelwerkbalk configureren met behulp van het dialoogvenster Deelvenster bewerken.</p> </td>
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
   <td>Hier kunt u statische tekst opgeven.</td>
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
     <li>Type International wordt gevalideerd door <code>^[+][0-9]{0,14}$</code> .</li>
     <li>Type USPhoneNumber wordt gevalideerd door <code>{'+1 ('999') '999-9999}</code> .</li>
     <li>Type UKPhoneNumber wordt gevalideerd door <code>text{'+'99 999 999 9999}</code> .</li>
     <li>Aangepast type biedt geen standaard validatiepatroon. Het neemt de waarde van het laatste geselecteerde type van telefoonaantal. U kunt ook uw eigen aangepaste validatiepatroon opgeven.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Voorwaarden en bepalingen <br /> </td>
   <td>Hiermee voegt u een veld toe waarin auteurs de voorwaarden kunnen opgeven die gebruikers kunnen bekijken voordat ze het formulier invullen.</td>
  </tr>
  <tr>
   <td>Tekstvak </td>
   <td><p>Voegt een tekstvak toe waarin een gebruiker de vereiste informatie kan opgeven. </p> <p>Standaard accepteert de component Tekstvak alleen onbewerkte tekst. U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Een tekstcomponent met RTF-functionaliteit biedt opties voor het toevoegen van kopteksten, het wijzigen van tekenstijlen (vet, cursief, onderstrepen van tekens), het maken van geordende en ongeordende lijsten, het wijzigen van de tekstachtergrond en tekstkleur en het toevoegen van hyperlinks. Om rijke tekst voor een tekstvakje toe te laten, laat <strong> toe staat RTF </strong> optie in de componenteneigenschappen toe.</p> </td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Hiermee geeft u een titel op voor het adaptieve formulier.</td>
  </tr>
  <tr>
   <td>Stap verifiëren</td>
   <td><p>Hiermee voegt u een tijdelijke aanduiding toe waarmee het ingevulde formulier wordt weergegeven ter verificatie door de gebruiker.</p> <p><strong> Nota </strong>: De adaptieve vorm die de Verify component bevat steunt geen anonieme gebruikers. Het wordt ook afgeraden de component Verify te gebruiken in een adaptief formulierfragment.</p> </td>
  </tr>
 </tbody>
</table>

#### Aanbevolen procedures voor het werken met componenten {#best-practices}

U kunt de volgende tips en trucs gebruiken bij het werken met adaptieve formuliercomponenten:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Om de eigenschappen van een component te vormen, selecteer de component en selecteer ![ cmp ](assets/cmppr.png) om de componenteneigenschappen in browser van Eigenschappen te openen.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u ![ cmp ](assets/cmppr.png) selecteert, kunt u de naam van de component veranderen door de **[!UICONTROL Element Name]** gebiedswaarde in eigenschappen browser te veranderen. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.

* U kunt de eigenschap Titel van een adaptieve formuliercomponent inline wijzigen in de formuliereditor zonder de browser Eigenschappen te openen, zolang de titel maar zichtbaar is op het formulier. Daartoe:

   1. Selecteer deze optie om een component te selecteren die een eigenschap **[!UICONTROL Title]** heeft en waarvan de eigenschap **[!UICONTROL Hide title]** is uitgeschakeld.

   1. Selecteer ![ name_6_3_edit ](assets/aem_6_3_edit.png) om de titel editable te maken.

   1. Wijzig de titel en selecteer de Return-toets of selecteer een willekeurige locatie buiten de component om de wijzigingen op te slaan. Selecteer de sleutel van Esc om de veranderingen te verwerpen.

* Sommige adaptieve formuliercomponenten, zoals E-mail en Telefoon, bevatten validatiepatronen die niet in de verpakking staan. U kunt echter aangepaste validatie opgeven door het veld **[!UICONTROL Validation Pattern]** onder de accordeon Patronen bij te werken in de componenteigenschappen. Zie de componentbeschrijvingen in de bovenstaande tabel voor meer informatie over standaardvalidaties.

* Adaptieve formuliervelden, zoals Numeriek vak en E-mail, kunnen zo worden geconfigureerd dat ze ook speciale HTML5-invoertypen bevatten. Wanneer deze velden de focus hebben op mobiele apparaten en tablets, worden op het toetsenblok specifieke alfabet, getallen en tekens vóór weergegeven die doorgaans worden gebruikt voor het invoeren van informatie in de velden. Het helpt gebruikers informatie snel ingaan zonder het moeten tussen karakterreeksen op het toetsenbord van een knevel voorzien. Als u gespecialiseerde invoer voor een component wilt toestaan, schakelt u het selectievakje **[!UICONTROL Use HTML Type Number]** in de componenteigenschappen in.

* U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Als u tekst met opmaak wilt inschakelen voor een tekstvak, schakelt u het selectievakje **[!UICONTROL Allow Rich Text]** in de eigenschappen van de component in.

* U kunt de componenten van het Doos van de Tekst, E-mail, en van de Telefoon aan autofill waarden voor gebieden zoals naam, adres, creditcard, telefoon, en e-mail van de informatie toelaten die in browser autofill montages wordt opgeslagen. Selecteer **[!UICONTROL Enable Autofill]** in de componenteigenschappen en selecteer een **[!UICONTROL Autofill Attribute]** om deze functie in te schakelen. Wanneer een gebruiker een adaptief formulier invult, worden de waarden voorgesteld vanuit het profiel Automatisch vullen in de browser of op basis van de waarden die eerder door de gebruiker zijn ingevuld. Automatisch vullen werkt alleen als de instellingen voor automatisch vullen in de browser van de gebruiker zijn ingeschakeld.

* Geef waarden op voor keuzerondjes en selectievakjes in de indeling `{value}={text}` in componenteigenschappen.
* Met de component Bestandsbijlage kan een gebruiker standaard slechts één bestand bijvoegen. U kunt de componenteigenschappen echter configureren om meerdere bijlagen te ondersteunen. Als een gebruiker meerdere bestanden met dezelfde bestandsnaam bijvoegt, kunnen er bovendien problemen optreden in de bijlagen. Daarom wordt aanbevolen een unieke id te koppelen voor elke verzonden bijlage bij het verzenden van het formulier. Daartoe:

   1. Navigeer op uw AEM Forms-server naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** .
   1. Zoeken en selecteren **[!UICONTROL Adaptive Forms Configuration Service]** .
   1. Schakel **[!UICONTROL Make File Names Unique]** in het dialoogvenster Adaptive Forms Configuration Service in. Standaard is dit uitgeschakeld.

* Om gebruikers toe te laten om een PDF vast te maken gebruikend browser Safari, zorg ervoor dat **application/pdf** aan het Ondersteunde bezit van de Types van Dossier van de component van de gehechtheid van het Dossier wordt toegevoegd. De adaptieve vormen die met vorige versie van AEM Forms worden gecreeerd kunnen **.pdf** in plaats van **application/pdf** in het Ondersteunde bezit van de Types van Dossier bevatten.

Voor meer beste praktijken rond adaptieve vormen, zie [ Beste praktijken voor het werken met adaptieve vormen ](/help/forms/using/adaptive-forms-best-practices.md).

>[!NOTE]
>
>Adaptieve formuliercomponenten bieden geen ondersteuning voor RTL-talen (van rechts naar links). Bijvoorbeeld Hebreeuws.

### Pagina, werkbalk {#page-toolbar}

De pagina-werkbalk boven in het scherm bevat opties waarmee u een voorbeeld van het formulier kunt bekijken, de eigenschappen van het formulier kunt wijzigen en de indeling van het formulier kunt bewerken. U kunt een voorbeeld van het formulier bekijken wanneer u het maakt en de wijzigingen daarop aanbrengen. In de paginabooltoolbar, ziet u:

* **Knevel Zijpaneel** ![ knevel-zij-paneel ](assets/toggle-side-panel.png): Laat u Zijbalk tonen of verbergen.

* **de informatie van de Pagina** ![ thema-opties ](assets/theme-options.png): Laat u paginaeigenschappen bekijken, publiceren/unpublish een vorm, een vormwerkschema beginnen, en de vorm in klassieke UI openen.

* **Emulator** ![ heerser ](assets/ruler.png): Laat u het blik van uw vorm voor verschillende vertoningsgrootte zoals tabletten en telefoons emuleren.

* **geeft** uit: Laat u andere wijzen zoals: **[!UICONTROL Edit]**, **[!UICONTROL Style]**, **[!UICONTROL Developer]**, en **[!UICONTROL Design]** selecteren.

   * **geeft** uit: Laat u de eigenschappen van de vorm en zijn componenten uitgeven. U kunt bijvoorbeeld een component toevoegen, een afbeelding neerzetten en verplichte velden opgeven.
   * **Stijl**: Laat u de verschijning van componenten van uw vorm opmaken. In de stijlmodus kunt u bijvoorbeeld een deelvenster selecteren en de achtergrondkleur ervan opgeven.

   * **Ontwikkelaar**: Laat een ontwikkelaar aan:

      * Ontdek waaruit de formulieren bestaan.
      * Foutopsporing waar en wanneer gebeurt, wat weer helpt om problemen op te lossen.

   * **Ontwerp**. Hiermee kunt u aangepaste componenten, of componenten buiten het vak die niet in het zijpaneel staan, in- of uitschakelen.

* **Voorproef**: Laat u voorproef hoe de vorm kijkt wanneer u het publiceert.

### Component, werkbalk {#component-toolbar}

![ de toolbar van de Component in de aanraking UI ](assets/component-toolbar.png)

Wanneer u een component selecteert, ziet u een werkbalk waarin u de component kunt bewerken. U krijgt opties om, eigenschappen van de componenten te snijden te kleven, te bewegen en te specificeren. U kunt kiezen uit de volgende opties:

A.**vormt**: Wanneer u **[!UICONTROL Configure]** selecteert, zijn de componenteneigenschappen zichtbaar in sidebar. Als u deze eigenschappen configureert, kunt u de ervaring voor het vastleggen van gegevens aanpassen. U kunt de elementnaam van de component wijzigen en de labeltekst opgeven in het veld Titel van de component. Met elementnaam kunt u waarden vastleggen die gebruikers invoeren met de component. In de componenteigenschappen geeft u het gedrag van de component op en beheert u de gebruikersinvoer. Configureer eigenschappen in de zijbalk om gebruikersgegevens vast te leggen en te gebruiken voor verdere verwerking. Met eigenschappen voor adaptieve formuliercontainers kunt u clientbibliotheken, indelingen, thema&#39;s, Document of Record-instellingen, opslaginstellingen, verzendinstellingen en metagegevensinstellingen opgeven.

B.**Exemplaar**: U kunt de exemplaaroptie gebruiken om een component te kopiëren en het in andere plaatsen in de vorm te kleven. Wanneer u een component plakt, krijgt de geplakte component een nieuwe elementnaam maar behoudt deze de eigenschappen van de gekopieerde component.

C.**Besnoeiing**: U kunt de besnoeiingsoptie gebruiken om een component van één plaats aan een andere in de adaptieve vorm te bewegen.

D. **Schrapping**: Laat u de component van de vorm schrappen.

E. **Tussenvoegsel**: Laat u een component boven de geselecteerde component opnemen.

F. **Deeg**: Laat u de component kleven u knipt of gebruikend de hierboven beschreven opties kopieerde.

G. **geeft regels** uit: Laat u de regelredacteur openen. Voor meer informatie, zie [ Redacteur van de Regel ](../../forms/using/rule-editor.md).

H. **Groep**: Laat u veelvoudige componenten selecteren als u, meer dan één component samen knippen kopiëren of wilt kleven.

I. **Ouder**: Laat u de ouder van een component selecteren. Een tekstveld bevindt zich bijvoorbeeld binnen een subsectie, die zich in een sectie bevindt. De sectie bevindt zich in het hoofddeelvenster van de hulplijn en de adaptieve formuliercontainer is het bovenliggende element van een hoofddeelvenster van de hulplijn. Voor een component, kunt u alle opties zien met hiërarchie gesorteerd onderaan-op.

Als u bijvoorbeeld **[!UICONTROL Parent]** voor een tekstvak selecteert, kunt u zien:

* Onderafdeling
* Sectie
* guideRootPanel
* Container voor adaptieve vorm

J. **anderen**: Verstrekt meer opties om met de geselecteerde component te werken.

* SOM-expressie weergeven
* Een deelvenster opslaan als fragment (alleen voor deelvensters)
* Onderliggend deelvenster toevoegen (alleen voor deelvensters)
* Deelvensterwerkbalk toevoegen (alleen voor deelvensters)
* Vervangen (niet voor deelvensters)

### Aangepaste formulierpagina {#af-page}

De aangepaste formulierpagina is het daadwerkelijke formulier. Dit is net als elke andere WCM-pagina die is gemodelleerd als de WCM `cq:Page` -component. In de volgende afbeelding ziet u de inhoudsstructuur van een adaptief formulier.

![ de structuur van de inhoud van een adaptieve vormWCM pagina ](assets/afstructure.png)

De inhoudsstructuur bevat doorgaans de volgende primaire componenten:

* **guideContainer**: De wortel van een adaptieve vorm, die als **[!UICONTROL Start of adaptive form]** in de adaptieve vorm UI duidelijk is. In deze component kunt u het volgende opgeven:

   * *Mobiele Lay-out van de adaptieve vorm*: Bepaalt de verschijning van de vorm op mobiele apparaten.
   * *Dank u pagina*: Bepaalt de pagina waar de gebruiker na het voorleggen van de vorm opnieuw gericht wordt.
   * *legt Actie* voor: Bepaalt hoe de vorm op de server wordt verwerkt zodra de gebruiker de vorm voorlegt.
   * *het Stileren*: Specificeert de weg aan het CSS dossier wordt gebruikt om de verschijning van de vorm aan te passen die.

* **rootPanel:** het wortelpaneel van een adaptieve vorm. Het kan subdeelvensters onder de puntenknoop bevatten. Aan elk deelvenster, inclusief het hoofddeelvenster, kan een lay-out zijn gekoppeld. De indeling van het deelvenster bepaalt hoe het formulier wordt opgemaakt. In de schermindeling Accordeon worden de items ervan bijvoorbeeld ingedeeld als Accordion-stappen.

* **toolbar:** een adaptieve vormcontainer heeft een bijbehorende globale toolbar, die aan de vorm globaal is. Deze werkbalk kan worden toegevoegd met de handeling **[!UICONTROL Add Toolbar]** op de bewerkbalk. Hiermee kunnen auteurs handelingen toevoegen, zoals Verzenden, Opslaan, Herstellen enzovoort.

* **activa:** Deze knoop bevat extra informatie die voor vorm creatie wordt gebruikt. Bijvoorbeeld details van het formuliermodel, lokalisatiedetails, enzovoort).
