---
title: Thema's maken en gebruiken
description: Met thema's kunt u een adaptief formulier of interactieve communicatie stileren en een visuele identiteit geven. U kunt een thema delen op elk gewenst aantal adaptieve formulieren of interactieve communicatie.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop, interactive-communications
content-strategy: max-2018
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 93c360a8-a9d9-4c4b-b7e2-2c44eaf4604c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '6086'
ht-degree: 0%

---

# Thema&#39;s maken en gebruiken {#creating-and-using-themes}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/themes.html) |
| AEM 6,5 | Dit artikel |

## Inleiding {#introduction}

U kunt thema&#39;s maken en toepassen om een adaptief formulier of interactieve communicatie te stileren. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. Thema&#39;s worden onafhankelijk beheerd zonder verwijzing naar een adaptieve vorm of interactieve communicatie.

U kunt:

* Een thema maken
* Een bestaand thema bewerken en kopiëren
* Een bestaand thema downloaden en uploaden naar de AEM Forms-server
* Afhankelijkheden voor een thema beheren

## Een thema maken, downloaden of uploaden {#creating-downloading-or-uploading-a-theme}

Met AEM Forms kunt u thema&#39;s maken, downloaden of uploaden. Net als andere elementen, zoals formulieren, documenten en letters, wordt een thema gemaakt. Het thema wordt opgeslagen als een afzonderlijke entiteit, compleet met meta-eigenschappen zoals formulieren. Thema&#39;s die een afzonderlijke entiteit zijn, maken hergebruik in meerdere adaptieve vormen en interactieve communicatie mogelijk. U kunt een thema ook naar een andere AEM Forms-instantie verplaatsen en opnieuw gebruiken.

### Een thema maken {#creating-a-theme}

Voer de volgende stappen uit om een thema te maken:

1. Klik **Adobe Experience Manager**, klik **Forms**, en klik dan **Thema&#39;s**.

1. In de pagina van Thema&#39;s, klik **creeer > Thema**.
Er wordt een wizard gestart om een thema te maken.

1. In het Basis lusje van de Create tovenaar van het Thema, verstrek **Titel** en **Naam** van het thema. Dit zijn verplichte velden.

1. Op het tabblad Geavanceerd krijgt u twee velden:

   * **Clientlib Plaats**: Plaats in de bewaarplaats die de clientlibs voor het thema opslaat.

   * **Clientlib Categorie**: Verstrekt een tekstgebied om cliëntlib categorienaam voor het thema in te gaan.

1. Klik **creeer** en klik dan **uitgeven** om het thema in de Redacteur van het Thema te openen, of klik **Gedaan** om aan de themapagina terug te keren.

### Een thema downloaden {#downloading-a-theme}

U kunt thema&#39;s exporteren als ZIP-bestand en deze gebruiken in andere projecten of AEM. Een thema downloaden:

1. Klik **Adobe Experience Manager**, klik **Forms**, en klik dan **Thema&#39;s**.

1. In de pagina van Thema&#39;s, **selecteer** een thema, en klik **Download**. Er wordt een dialoogvenster weergegeven met de details van het thema.

1. Klik **Download**. Het thema wordt gedownload als een ZIP-bestand.

>[!NOTE]
>
>Als u een thema downloadt waaraan een adaptief formulier is gekoppeld en het bijbehorende adaptieve formulier is gebaseerd op een aangepaste sjabloon, downloadt u ook de aangepaste sjabloon. Wanneer u het gedownloade thema en het aangepaste formulier uploadt naar een AEM Forms-server, kunt u ook de gerelateerde aangepaste sjabloon uploaden.

### Een thema uploaden {#uploading-a-theme}

U kunt gemaakte thema&#39;s gebruiken met voorinstellingen voor stijlen voor uw project. U kunt themapakketten die anderen maken, importeren door deze te uploaden naar uw project.

Een thema uploaden:

1. Klik **Adobe Experience Manager**, klik **Forms**, en klik dan **Thema&#39;s**.

1. In de pagina van Thema&#39;s, klik **creëren > Dossier uploadt**.
1. In het Dossier uploadt herinnering, doorblader en selecteer een themapakket op uw computer en klik **uploadt**.
Het geüploade thema is beschikbaar op de themapagina.

## Metagegevens van een thema {#metadata-of-a-theme}

Lijst met meta-eigenschappen van een thema (bevindt zich op de pagina met eigenschappen van een thema).

<table>
 <tbody>
  <tr>
   <th><p><strong>ID</strong></p> <p> </p> </th>
   <th><strong>Naam</strong></th>
   <th><strong>Kan worden bewerkt</strong></th>
   <th><strong>Beschrijving van eigenschap</strong></th>
  </tr>
  <tr>
   <td>1.</td>
   <td>Titel</td>
   <td>Ja</td>
   <td>Naam van thema weergeven.</td>
  </tr>
  <tr>
   <td>2.</td>
   <td>Beschrijving</td>
   <td>Ja</td>
   <td>Beschrijving van het thema.</td>
  </tr>
  <tr>
   <td>3.</td>
   <td>Type</td>
   <td>Nee</td>
   <td>
    <ul>
     <li>Type element.</li>
     <li>Waarde is altijd thema.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>4.</td>
   <td>Gemaakt</td>
   <td>Nee</td>
   <td>Aanmaakdatum thema</td>
  </tr>
  <tr>
   <td>5.</td>
   <td>Naam auteur</td>
   <td>Ja</td>
   <td>Auteur van het thema. Berekend op het moment dat het thema werd gemaakt.</td>
  </tr>
  <tr>
   <td>6.</td>
   <td>Laatste wijzigingsdatum</td>
   <td>Nee</td>
   <td>Datum waarop het thema voor het laatst is gewijzigd.</td>
  </tr>
  <tr>
   <td>7.</td>
   <td>Status</td>
   <td>Nee</td>
   <td>Status van het thema (Gewijzigd/gepubliceerd).</td>
  </tr>
  <tr>
   <td>8.</td>
   <td>Publish On Time</td>
   <td>Ja</td>
   <td>Tijd om het thema automatisch te publiceren.</td>
  </tr>
  <tr>
   <td>9.</td>
   <td>Publish Off Time</td>
   <td>Ja</td>
   <td>Tijd om de publicatie van het thema automatisch ongedaan te maken.</td>
  </tr>
  <tr>
   <td>10.</td>
   <td>Tags</td>
   <td>Ja</td>
   <td>Een label dat aan het thema is gekoppeld om het zoeken te verbeteren.</td>
  </tr>
  <tr>
   <td>11.</td>
   <td>Verwijzingen</td>
   <td>Koppelingen</td>
   <td>
    <ul>
     <li>Bevat sectie 'Verwezen door'. Hier worden formulieren weergegeven die het thema gebruiken.</li>
     <li>Omdat het thema niet naar andere elementen verwijst, is er geen sectie 'Verwijzingen'.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>12.</td>
   <td>Clientlib-locatie</td>
   <td>Ja</td>
   <td>
    <ul>
     <li>Het door de gebruiker gedefinieerde opslagpad binnen '/etc' waar de clientlibs die overeenkomen met dit thema, worden opgeslagen.</li>
     <li>Standaardwaarde - '/etc/clientlibs/fd/themes' + relatief pad van themaelement.</li>
     <li>Als de locatie niet bestaat, wordt de maphiërarchie automatisch gegenereerd.</li>
     <li>Wanneer deze waarde wordt gewijzigd, wordt de clientlib-knooppuntstructuur verplaatst naar de nieuwe ingevoerde locatie.<br /> <em> <strong> Nota:</strong> als u standaardcliëntlib plaats verandert, in de bewaarplaats CRXDE toewijzen <code>crx:replicate</code>, <code>rep:write</code>, <code>rep:glob:*</code>, <code>rep:itemNames::</code> <code>js.txt</code>, <code>jcr:read</code> aan <code>forms-users</code> en <code>crx:replicate</code>, <code>jcr:read</code> aan <code>fd-service</code> in de nieuwe plaats. Koppel ook een andere ACL door <code>deny jcr:addChildNodes</code> voor <code>forms-user</code></em> toe te voegen</li>
    </ul> </td>
  </tr>
  <tr>
   <td>13.</td>
   <td>Naam van categorie Clientlib</td>
   <td>Ja</td>
   <td>
    <ul>
     <li>De door de gebruiker gedefinieerde clientlib-categorienaam voor dit thema.</li>
     <li>Er wordt een fout weergegeven als de naam al wordt gebruikt door een ander bestaand thema.</li>
     <li>Standaardwaarde - berekend op basis van themalocatie.</li>
     <li>Wanneer deze waarde wordt gewijzigd, wordt de categorienaam bijgewerkt op de overeenkomstige cliëntlib knoop. Het bijwerken van de Naam van de Categorie van Clientlib in de Jsp- dossiers wordt niet vereist omdat de naam van de cliëntlib- categorie door verwijzing wordt gebruikt.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Over de Thema-editor {#about-the-theme-editor}

AEM Forms wordt geleverd met Thema Editor. Het is een handige interface voor zakelijke gebruikers en webontwerpers/ontwikkelaars die functies biedt die vereist zijn om de opmaak van verschillende adaptieve formulieren en interactieve communicatie-elementen eenvoudig op te geven. Wanneer u een thema maakt, wordt het opgeslagen als een afzonderlijke entiteit, zoals formulieren, interactieve communicatie, letters, documentfragmenten en gegevenswoordenboeken.

In de Thema-editor kunt u stijlen van de componenten die in een thema zijn opgemaakt, aanpassen. U kunt de weergave van een formulier of interactieve communicatie op een apparaat aanpassen.

De Thema-editor bestaat uit twee deelvensters:

* **Canvas** - verschijnt op de rechterkant. Het toont een voorbeeld van een adaptief formulier of interactieve communicatie waarin alle opmaakwijzigingen direct worden weerspiegeld. U kunt ook rechtstreeks objecten op het canvas selecteren om de bijbehorende stijlen op te zoeken en deze stijlen te bewerken. Een liniaal voor apparaatresolutie bovenaan bestuurt het canvas. Als u een onderbrekingspunt van de resolutie selecteert in de liniaal, wordt een voorbeeld van het voorbeeldformulier of de interactieve communicatie voor de desbetreffende resolutie weergegeven. Canvas wordt besproken in detail [ hieronder ](../../forms/using/themes.md#using-canvas).

* **Sidebar** - verschijnt op de linkerkant. Het heeft de volgende punten:

   * **Selecteur:** toont de component die voor het stileren wordt geselecteerd, en zijn eigenschappen die u kunt stileren. De kiezer vertegenwoordigt alle componenten van een type. Als u een tekstvakcomponent in een thema voor het stileren selecteert, erven alle tekstvakjes in uw formulier of interactieve mededeling de stijl. Met kiezers kunt u een algemene component of een specifieke component voor opmaak selecteren. Een veldcomponent is bijvoorbeeld een algemeen onderdeel en een tekstvak is een specifiek onderdeel.

     **het Stijlen generische component:**
Een veld kan een numeriek veld zijn, zoals leeftijd, of een veld in een tekstvak, zoals een adres.
Wanneer u een veld opmaakt, worden alle velden opgemaakt, zoals pagina, naam en adres.

     **het stileren van specifieke component**:
Een specifieke component is van invloed op objecten van de specifieke categorie. Wanneer u de stijl van de numerieke vakcomponent in het thema toepast, overerft alleen het object van het numerieke vak de stijl.

     Een tekstveld zoals een adres is bijvoorbeeld langer en een numeriek veld van een vak, zoals de leeftijd, is korter. U kunt een numeriek veld selecteren, de lengte ervan verkleinen en op het formulier toepassen. De breedte van alle velden van numerieke vakken wordt verkleind in het formulier.

     Wanneer u alle veldcomponenten met een specifieke achtergrondkleur aanpast, nemen alle velden, zoals leeftijd, naam en adres, de achtergrondkleur over. Wanneer u een numeriek vak selecteert, zoals de leeftijd, en de breedte en breedte van alle numerieke vakken zoals de leeftijd verkleint, wordt het aantal personen in een familie verminderd. De breedte van tekstvakken wordt niet gewijzigd.

   * **Staat:** laat u stijlen van een voorwerp in een specifieke staat aanpassen. U kunt bijvoorbeeld opgeven hoe een object eruitziet als het zich in de standaardtoestand, de standaardfocus, de uitgeschakelde toestand, de aanwijsstatus of de foutstatus bevindt.
   * **de Categorieën van het Bezit:** het stileren eigenschappen zijn verdeeld in diverse categorieën. Bijvoorbeeld Dimension en positie, tekst, achtergrond, rand en effecten. Onder elke categorie geeft u opmaakgegevens op. Onder Achtergrond kunt u bijvoorbeeld Achtergrondkleur en Afbeelding en Verloop opgeven.

   * **Geavanceerd:** laat u douane CSS aan een voorwerp toevoegen, dat de eigenschappen met voeten treedt visuele controles bepalen als er een overlapping is.

   * **CSS van de Mening**: Laat u CSS van de geselecteerde component bekijken

  In de Sidebar is onder aan de zijbalk ook een pijl aanwezig. Wanneer u de pijl klikt, krijgt u twee meer opties: **Simuleer Succes** en **Simuleer Fout.** Deze opties, samen met de hierboven beschreven opties worden besproken in detail [ hieronder ](../../forms/using/themes.md#using-rail).

[![ de redacteur van het thema met de spoorstaaf en Gemarkeerd Canvas.](assets/themes.png)](assets/themes-1.png) **A.** Sidebar **B.** Canvas

### Stijlcomponenten {#styling-components}

U kunt een thema gebruiken in meerdere adaptieve formulieren en interactieve communicatie, waarmee u de componentopmaak importeert die u in het thema hebt opgegeven. U kunt diverse componenten opmaken, zoals titels, beschrijving, deelvensters, velden, pictogrammen en tekstvakken. Gebruik widgets om componenteigenschappen in een thema te configureren. Eerdere kennis van CSS of LESS is niet vereist maar gewenst, hoewel u met de sectie CSS-overschrijvingen CSS-code kunt schrijven of aangepaste kiezers kunt opgeven. De sectie CSS overschrijven wordt weergegeven wanneer u een component in de zijbalk selecteert.

![ Stylable componenten in sidebar ](assets/stylable-components.png)

Opties in het zijpaneel waarmee u verschillende componenten kunt selecteren en opmaken.

Als u op de knop Bewerken klikt op een component in het zijpaneel, wordt de component in Canvas geselecteerd en kunt u de component opmaken met de opties in het zijpaneel.

Bepaalde componenten, zoals tekstvak, numeriek vak, keuzerondje en selectievakje, zijn gecategoriseerd onder algemene componenten, zoals Veld. U wilt bijvoorbeeld de opmaak van keuzerondjes aanpassen. Om radioknopen voor het stileren te selecteren, uitgezochte **Gebied > Widget > Keuzerondje**.

Klik **UITBREIDEN ALLES** in sidebar aan mening, selecteren, en stijl gecategoriseerde componenten die niet op voorgrond zichtbaar zijn.

### Lay-outs van het deelvenster Stijlen {#styling-panel-layouts-br}

Thema&#39;s in AEM Forms ondersteunen het opmaken van elementen in de lay-out van deelvensters in uw formulieren en interactieve communicatie. Het opmaken van elementen in lay-outs buiten de box en aangepaste lay-outs wordt ondersteund.

Voorbeelden van deelvensters buiten het vak zijn:

* Tabs links
* Bovenaan tabs
* Accordeon
* Responsief
* Wizard
* Mobiele lay-out

   * Titels van deelvensters in koptekst
   * Zonder deelvenstertitels in koptekst

De kiezers variëren voor elke lay-out.
Aangepaste lay-outs opmaken in de Thema-editor is:

* Componenten definiëren voor een lay-out die kan worden vormgegeven, en CSS-kiezers voor unieke identificatie van deze componenten
* CSS-eigenschappen definiëren die op deze componenten kunnen worden toegepast
* Definieer de opmaak voor deze componenten interactief vanuit de gebruikersinterface

### Verschillende stijlen voor verschillende schermgrootten {#different-styles-for-different-screen-sizes-br}

Bureaublad- en mobiele lay-outs kunnen enigszins of geheel verschillende stijlen hebben. Voor mobiele apparaten hebben tablets en telefoons dezelfde lay-outs, behalve voor componentformaten.

Onderbrekingspunten van de Thema-editor gebruiken om alternatieve opmaak voor verschillende schermgrootten te definiëren. U kunt een basisapparaat of een basisresolutie selecteren waarop u het thema begint te maken en de variaties in stijlen voor andere resoluties worden automatisch gegenereerd. U kunt de opmaak van alle resoluties expliciet wijzigen.

>[!NOTE]
>
>Het thema wordt eerst gemaakt met een formulier of interactieve communicatie en wordt vervolgens toegepast op verschillende formulieren of interactieve communicatie. De breekpunten die worden gebruikt bij het maken van thema&#39;s, kunnen afwijken van het formulier of de interactieve communicatie waarop het thema wordt toegepast. De CSS-mediaquery&#39;s zijn gebaseerd op het formulier of de interactieve communicatie die wordt gebruikt bij het maken van thema&#39;s, en niet op het formulier of de interactieve communicatie waarop het thema wordt toegepast.

### Contextwijzigingen in opmaakeigenschappen in zijbalk bij het selecteren van objecten {#styling-properties-context-changes-in-sidebar-on-selecting-objects}

Wanneer u een component op het canvas selecteert, worden de opmaakeigenschappen van de component weergegeven in het zijpaneel. Selecteer het objecttype en de objectstatus en geef de objectstijl op.

### Onlangs gebruikte stijlen in de Thema-editor {#recently-used-styles-in-theme-editor}

In de themaeditor worden maximaal 10 stijlen opgeslagen die op een component zijn toegepast. U kunt de stijlen in de cache gebruiken met een andere component van een thema. Onlangs gebruikte stijlen zijn direct onder de geselecteerde component in het zijpaneel beschikbaar als een keuzelijst. In eerste instantie is de lijst met onlangs gebruikte stijlen leeg.

![ activa-bibliotheek ](assets/asset-library.png)

Terwijl u een component opmaakt, worden de stijlen in de cache opgeslagen en in het lijstvak weergegeven. In dit voorbeeld wordt het label van het tekstvak opgemaakt om de tekengrootte en -kleur te wijzigen. U kunt vergelijkbare stappen volgen voor het kiezen van een afbeelding of het wijzigen van kleuren om een component op te maken. U kunt zien hoe de stijl in de cache wordt geplaatst en in het lijstvak wordt weergegeven wanneer de opmaak van het veldlabel wordt gewijzigd.

![ de doopvontstijl caching voor een component beschikbaar voor een andere ](assets/font-style-cached.png)

In dit voorbeeld wordt de stijl voor het veldlabel gewijzigd. Wanneer de optie Beschrijving van responsief deelvenster is geselecteerd als stijl, wordt een lijstitem toegevoegd aan de elementenbibliotheek. Het item in de elementenbibliotheek kan worden gebruikt om de stijl voor de beschrijving van het deelvenster Responsief te wijzigen.

Wanneer een stijl in de activabibliotheek wordt toegevoegd, is het beschikbaar voor andere thema&#39;s en op de [ stijlwijze ](../../forms/using/inline-style-adaptive-forms.md) van de vormredacteur of interactieve communicatie redacteur UI. Als u de stijlmodus van de gebruikersinterface van de formuliereditor of de interactieve communicatie-editor gebruikt om een component op te maken, wordt de stijl in het cachegeheugen opgeslagen en is deze beschikbaar in thema&#39;s.

Met de plusknop in de elementenbibliotheek kunt u de stijl permanent opslaan met een naam die u opgeeft. Met de plusknop slaat u de stijl op, zelfs als u niet op de knop Opslaan in het zijpaneel klikt om de stijl toe te passen op een component. De plus knoop om een stijl voor later gebruik te bewaren is niet beschikbaar op de stijlwijze.

![ Verstrekt een naam van de douanestijl voor activa bibliotheek ](assets/custom-style-name.png)

Wanneer u een aangepaste naam voor een stijl opgeeft, is de stijl gekoppeld aan een thema en is deze niet meer beschikbaar voor andere thema&#39;s. Een opgeslagen stijl verwijderen:

1. Op de toolbar CANVAS, klik **![ thema-opties ](assets/theme-options.png) >** leiden Stijlen **.**
1. In het Manage dialoog van Stijlen, selecteer een bewaarde stijl, klik **Schrapping**.

   ![ Schrap de bewaarde stijl ](assets/manage-styles.png)

### Wijzigingen live voorvertonen, opslaan en negeren {#live-preview-save-and-discard-changes}

Wijzigingen in de opmaak worden direct weerspiegeld in het formulier of de interactieve communicatie die op het canvas is geladen. Met Live voorvertoning kunt u interactief de invloed van de opmaak definiëren en bekijken. Wanneer u het stileren van een component verandert, wordt de **Gereed** knoop toegelaten in sidebar. Om veranderingen te behouden, gebruik de **Gereed** knoop.

>[!NOTE]
>
>Wanneer een ongeldig teken in een veld wordt ingevoerd, verandert de kleur van de veldgrens in rood en wordt een foutbericht weergegeven in de linkerbovenhoek van het scherm. Als u bijvoorbeeld alfabeten invoert in een tekstvak waarin numerieke tekens worden geaccepteerd als invoer, is de kleur van de grens van het invoervak veranderd in rood. U kunt een dergelijk thema niet opslaan zonder de fout op te lossen die bovenaan wordt weergegeven.

### Thema met een ander adaptief formulier of interactieve communicatie {#theme-with-another-adaptive-form-or-interactive-communication}

Wanneer u een thema maakt, wordt dit gemaakt met een formulier dat wordt geleverd bij de Thema-editor. U biedt stijlen voor componenten in dit formulier. In plaats van het formulier dat bij de Thema-editor wordt geleverd, kunt u een formulier of interactieve communicatie van uw keuze selecteren om de opmaak te bepalen en een voorbeeld van de resultaten te bekijken.

Het huidige formulier of de interactieve communicatie in het Thema Editor Canvas vervangen:

1. In het paneel van de EDITOR van het THEMA, klik **![ thema-opties ](assets/theme-options.png) >** vormen **van de Opties van het Thema.**

1. Op het Algemene lusje, doorblader en selecteer een vorm of interactieve mededeling voor het **Aangepaste 1&rbrace; gebied van de Vorm/van het Document.**

### Opnieuw/Ongedaan maken {#redo-undo}

U kunt de ongewenste wijzigingen die per ongeluk optreden, ongedaan maken of opnieuw uitvoeren. Gebruik de knoppen Opnieuw uitvoeren/Ongedaan maken op het canvas.

![ herhaal en maak acties ](assets/redo_undo_new.png) ongedaan

Knoppen Ongedaan maken/Opnieuw uitvoeren in Canvas

De knoppen voor Opnieuw/Ongedaan maken verschijnen wanneer u een component opmaakt in de Thema-editor.

## De Thema-editor gebruiken {#using-the-theme-editor}

Met de Thema-editor kunt u een thema bewerken dat u hebt gemaakt of geüpload. Navigeer aan **Forms &amp; Documenten > Thema&#39;s**, en selecteer een thema en open het. Het thema wordt geopend in de Thema-editor.

Zoals hierboven is beschreven, heeft de Thema-editor twee deelvensters: Sidebar en Canvas.
![ thema-redacteur ](assets/theme-editor.png)

De successtatusopmaak van de widgetcomponent Tekstvak aanpassen in de Thema-editor. Component wordt geselecteerd in Canvas, en zijn staat wordt geselecteerd in sidebar. De opmaakopties in de zijbalk worden gebruikt om de vormgeving van een component aan te passen.

### Canvas gebruiken {#using-canvas}

Het thema wordt gemaakt met het formulier dat u wilt uitvouwen of met een formulier of interactieve communicatie van uw keuze. Op het canvas ziet u een voorbeeld van het formulier of de interactieve communicatie die wordt gebruikt voor het maken van het thema met aanpassingen die in het thema zijn opgegeven. De liniaal boven het formulier wordt gebruikt om de indeling te bepalen op basis van de grootte van de weergave van het apparaat.

In de werkbalk Canvas ziet u:

* **Knevel Zijpaneel** ![ knevel-zij-paneel ](assets/toggle-side-panel.png): Laat u sidebar tonen of verbergen.
* **de Opties van het Thema** ![ thema-opties ](assets/theme-options.png): Verstrekt drie opties

   * Configureren: biedt opties voor het selecteren van het voorbeeldformulier of de interactieve communicatie, de basisclientlib en de Adobe Fonts-configuratie.
   * Thema CSS weergeven: genereert CSS voor het geselecteerde thema.
   * Stijlen beheren: biedt opties voor het beheer van tekst- en afbeeldingsstijlen
   * Help: hiermee wordt een rondleiding door de Thema-editor uitgevoerd voor afbeeldingen.

* **Emulator** ![ heerser ](assets/ruler.png): Emuleert de blik van uw thema voor verschillende vertoningsgrootte. Een weergavegrootte wordt beschouwd als een onderbrekingspunt in de emulator. U kunt een onderbrekingspunt selecteren en een stijl voor het specificeren. Desktop en Tablet zijn bijvoorbeeld twee breekpunten. U kunt verschillende stijlen opgeven voor elk onderbrekingspunt.

Wanneer u een component selecteert in het canvas, ziet u de componentwerkbalk er bovenop. Met de componentwerkbalk kunt u componenten selecteren of overschakelen op algemene componenten. U selecteert bijvoorbeeld een numeriek tekstvak in een deelvenster. De werkbalk van de component bevat de volgende opties:

* **Numerieke Widget van de Doos**: Laat u de component selecteren om zijn blik in sidebar aan te passen.
* **Widget van het Gebied**: Laat u de generische component voor het stileren selecteren. In dit voorbeeld worden alle tekstinvoercomponenten (tekstvak/numeriek vak/numerieke stepper/datum-invoer) geselecteerd voor opmaak.

* ![ gebied-niveau ](assets/field-level.png): Laat u op generische component voor het stileren schakelen. Als u een numeriek vak selecteert en dit pictogram selecteert, wordt de veldcomponent geselecteerd. Als u een veldcomponent selecteert en dit pictogram selecteert, wordt het deelvenster geselecteerd. Als u op dit pictogram blijft tikken om het te selecteren, selecteert u uiteindelijk de lay-out voor opmaak.

>[!NOTE]
>
>Welke opties beschikbaar zijn op de werkbalk van de component, is afhankelijk van de component die u selecteert.

![ de toolbar van de Component ](assets/overlay.png)

De werkbalk Component op het numerieke vak in Canvas

### Zijbalk gebruiken {#using-rail}

Het zijpaneel in de themaeditor bevat opties waarmee u stijlen voor componenten in een thema kunt aanpassen en kiezers kunt gebruiken. Met kiezers kunt u een groep componenten of afzonderlijke componenten selecteren en u kunt zoeken naar kiezers in het zijpaneel. U kunt kiezers schrijven voor aangepaste componenten.

Wanneer u een component selecteert op het canvas of op de zijbalk van de kiezer, worden in het zijpaneel alle opties weergegeven waarmee u stijlen kunt aanpassen.
Hieronder ziet u de opties die in het zijpaneel worden weergegeven wanneer u een component selecteert:

* Staat
* Eigenschappenblad
* Fout/succes simuleren

#### Staat {#state}

Een status is een indicator van gebruikersinteractie met een component. Wanneer een gebruiker bijvoorbeeld onjuiste gegevens in een tekstvak invoert, verandert de status van het tekstvak in een foutstatus. Met de Thema-editor kunt u stijlen voor een bepaalde status opgeven.

De opties voor het aanpassen van statusstijlen variëren voor verschillende componenten.

#### Eigenschappenblad {#property-sheet}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Gebruiken</strong></td>
  </tr>
  <tr>
   <td><p>Dimensionen en positie</p> </td>
   <td><p>Hiermee kunt u de uitlijning, grootte, positionering en plaatsing van componenten in het thema opmaken. </p> <p>De opties zijn weergave-instellingen, opvulling, marge, breedte, hoogte en Z-index.</p> <p>U kunt de modus Lay-out ook gebruiken om de breedte van componenten te definiëren met behulp van een eenvoudige interface voor slepen en neerzetten. Voor meer informatie, zie {de wijze van de Lay-out van het 0} Gebruik om componenten </a> te resize.<a href="../../forms/using/resize-using-layout-mode.md"></p> </td>
  </tr>
  <tr>
   <td><p>Tekst</p> </td>
   <td><p>Hiermee kunt u de tekststijlen in de component van het thema aanpassen.</p> <p>U wilt bijvoorbeeld instellen hoe de tekst die u in het tekstvak invoert, eruitziet.</p> <p>U kunt lettertypefamilie, dikte, kleur, grootte, regelhoogte, tekstuitlijning, letterspatiëring, tekstinspringing, onderstrepen, cursief, teksttransformatie, verticaal uitlijnen, basislijn en richting kiezen. </p> </td>
  </tr>
  <tr>
   <td><p>Achtergrond </p> </td>
   <td><p>Hiermee kunt u de achtergrond van de component vullen met een afbeelding of kleur. </p> </td>
  </tr>
  <tr>
   <td><p>Rand</p> </td>
   <td><p>Hiermee kunt u kiezen hoe de rand van de component eruitziet. U wilt bijvoorbeeld dat het tekstvak een diepe, rode, dikke rand heeft met een stippellijn. </p> <p>De opties zijn breedte, stijl, straal en kleur van de rand.</p> </td>
  </tr>
  <tr>
   <td><p>Effecten</p> </td>
   <td><p>Hiermee kunt u speciale effecten aan de componenten toevoegen, zoals dekking, overvloeimodus en schaduwen. </p> </td>
  </tr>
  <tr>
   <td><p>Geavanceerd</p> </td>
   <td><p>Hiermee kunt u het volgende toevoegen:</p>
    <ul>
     <li>Eigenschappen voor <code>::before</code> - en <code>::after</code> pseudo-elementen om inhoud toe te voegen na of vóór de standaardinhoud in de kiezer en de inhoud op te maken.<br /> zie <a href="https://www.w3schools.com/css/css_pseudo_elements.asp" target="_blank"> CSS pseudo-elementen </a>.</li>
     <li>Aangepaste CSS-code inline naar een component schrijven en aangepaste kiezers schrijven. </li>
    </ul> <p>Wanneer u een aangepaste CSS-code toevoegt, wordt hiermee de aanpassing genegeerd die u hebt toegevoegd met de opties in de zijbalk. </p> </td>
  </tr>
 </tbody>
</table>

#### Fout/succes simuleren {#simulate-error-success}

De opties Fout simuleren en Succes zijn beschikbaar onder aan het zijpaneel. U kunt ze zien met een tonen/verbergen-pijl die onder aan het zijpaneel zichtbaar is. Met de Thema-editor kunt u verschillende toestanden van een component opmaken.

U voegt bijvoorbeeld een numeriek veld aan het formulier toe en u geeft de opmaak op in de themaeditor. Wanneer een gebruiker een alfanumerieke waarde in het veld typt, moet u de achtergrondkleur van het tekstvak wijzigen. U selecteert het numerieke veld in het thema en gebruikt de statusoptie in het zijpaneel. U selecteert de staat van de Fout in sidebar, en verander de achtergrondkleur in rood. Als u een voorvertoning van het gedrag wilt weergeven, kunt u de optie Fout simuleren gebruiken die beschikbaar is in de zijbalk. De opties Simulatiefout en Succes worden hieronder gedetailleerd beschreven:

* **Simuleer Succes**:
Hiermee kunt u zien hoe een component eruitziet als u de stijl voor de successtatus opgeeft. In een formulier stellen klanten bijvoorbeeld een wachtwoord in. Gebruikers kunnen een wachtwoord instellen op basis van de richtlijnen die u opgeeft. Wanneer een gebruiker een wachtwoord typt dat voldoet aan alle richtlijnen die u opgeeft, wordt het tekstvak groen. Als het tekstvak groen wordt, is de status geslaagd. U kunt stijlen voor een component in successtaat specificeren, en zijn verschijning simuleren gebruikend de Simulate optie van het Succes.

* **Simuleer Fout**:
Hiermee kunt u zien hoe een component eruitziet als u de opmaak voor de foutstatus opgeeft. In een formulier stellen klanten bijvoorbeeld een wachtwoord in. Gebruikers kunnen een wachtwoord instellen op basis van de richtlijnen die u opgeeft. Wanneer een gebruiker een wachtwoord typt dat niet aan alle richtlijnen voldoet, wordt het tekstvak rood. Als het tekstvak rood wordt, treedt er een fout op. U kunt stijlen voor een component in foutenstaat specificeren, en zijn verschijning simuleren gebruikend de Simulate optie van de Fout.

### Een component opmaken {#styling-a-component}

In uw formulier hebt u bijvoorbeeld twee typen tekstvakken: een tekstvak waarin alleen numerieke waarden kunnen worden ingevoerd en een tekstvak waarin alfanumerieke waarden kunnen worden ingevuld. U kunt de opmaak aanpassen voor het tekstvak waarin alleen numerieke waarden kunnen worden ingevoerd (een numeriek vak).

Voer de volgende stappen uit om de opmaak voor een bepaalde component aan te passen (een numeriek vak in dit voorbeeld):

1. Selecteer in de Thema-editor het numerieke vak op het canvas.
1. Wanneer u het numerieke vak selecteert, ziet u de werkbalk met de componenten met drie opties:

   * **Numerieke Widget van de Doos**
   * **Widget van het Gebied** ![ gebied-niveau ](assets/field-level.png)

1. Selecteer **Numerieke Widget van de Doos**.
1. De titel van het zijpaneel verandert in de widget Numerieke vak en bevat opties waarmee u de vormgeving kunt aanpassen.
De optie van het Dimension en van de Positie van het gebruik **&#x200B;**&#x200B;in sidebar om grootte van de component aan te passen. Zorg ervoor dat de Staat **Gebrek** is.

In plaats van het selecteren van **Numerieke Widget van de Doos**, uitgezochte **Widget van het Gebied** in de componententoolbar, en voer de stappen hierboven uit. Wanneer u afmetingen voor **optie van Widget van het Gebied** selecteert, hebben alle tekstvakjes behalve de numerieke doos de zelfde grootte.

### Velden voor een bepaalde status opmaken {#styling-fields-given-state}

Met de componentwerkbalk kunt u ook de opmaak van componenten voor de verschillende werkstaten opgeven. Als een component bijvoorbeeld is uitgeschakeld, is deze uitgeschakeld. Veelgebruikte staten van een component die u in themaredacteur kunt opmaken zijn: Gebrek, Nadruk, Gehandicapten, Fout, Succes, en Hover. U kunt een component in het canvas selecteren en de optie Staat in het zijpaneel gebruiken om het uiterlijk aan te passen.

Voer de volgende stappen uit om de opmaak van een component in een specifieke status aan te passen:

1. Selecteer een component in het canvas en selecteer de gewenste optie op de werkbalk van de component.
In de zijbalk ziet u opties waarmee u de opmaak van de component kunt aanpassen.
1. Selecteer een staat in de zijbalk. Bijvoorbeeld de status Fout.
1. De opties van het gebruik zoals **Grens, Achtergrond** in sidebar om aan te passen hoe de component kijkt.
1. Gebruik de **Simuleer de optie van de Fout** bij de bodem van sidebar om te zien hoe het stileren in het uitgeven kijkt.

Wanneer u de opmaak van een component aanpast nadat u de status ervan hebt opgegeven, wordt de aanpassing alleen voor de component weergegeven voor de opgegeven status. Als u bijvoorbeeld de opmaak voor de component aanpast wanneer de aanwijsstatus is geselecteerd. De aanpassing wordt weergegeven voor de component wanneer u de aanwijzer over de component beweegt in het gegenereerde formulier of de interactieve communicatie waarop u het thema toepast.

Gebruik de modus Voorbeeld om gedrag van andere staten dan fout en succes te simuleren. Om de wijze van de Voorproef te gebruiken, klik **Voorproef** op de paginagtoolbar.

### Lay-outs voor kleinere schermen opmaken {#styling-layouts-for-smaller-displays}

Gebruik de liniaal in Canvas om onderbrekingspunten te selecteren voor apparaten met kleinere beeldschermen. Klik mededinger ![ heerser ](assets/ruler.png) in Canvas aan meningsheerser en breekpunten. Met de onderbrekingspunten kunt u een voorbeeld bekijken van een formulier of interactieve communicatie voor weergavegrootten die betrekking hebben op verschillende apparaten, zoals telefoons en tablets. Meerdere weergavegrootten worden ondersteund in de Thema-editor.

U kunt als volgt componenten voor verschillende onderbrekingspunten opmaken:

1. Selecteer op het canvas een onderbrekingspunt boven de liniaal.
Een onderbrekingspunt vertegenwoordigt een mobiel apparaat en zijn vertoningsgrootte.
1. Met de zijbalk kunt u de opmaak van formulieren of interactieve communicatiecomponenten in het thema voor de geselecteerde weergavegrootte aanpassen.
1. Zorg ervoor dat de aanpassing wordt opgeslagen.

U kunt formulieren of interactieve communicatiecomponenten opmaken voor meerdere apparaten. Formulier- en interactieve communicatiecomponenten voor desktops en mobiele apparaten kunnen geheel verschillende stijlen hebben.

### Weblettertypen in een thema gebruiken {#using-web-fonts-in-a-theme}

U kunt nu lettertypen gebruiken die beschikbaar zijn in een webservice in een adaptief formulier of interactieve communicatie. Uit-van-de-doos, [ Adobe Fonts ](https://fonts.adobe.com/), de dienst van de het Webdoopvont van de Adobe, is beschikbaar als configuratie. Om Adobe Fonts te gebruiken, creeer een uitrusting, voeg doopvonten in het toe, en verkrijg identiteitskaart van het Kit van [ Adobe Fonts ](https://fonts.adobe.com/).

Voer de volgende stappen uit om Adobe Fonts in AEM te configureren:

1. In de auteursinstantie, klik ![ adobeexperienceManager ](assets/adobeexperiencemanager.png) Adobe Experience Manager > Hulpmiddelen ![ hamer ](assets/hammer.png) > Plaatsing > Cloud Servicen.
1. Voor de **Cloud Servicen** pagina, navigeer aan en open de **Adobe Fonts** optie. Open de configuratiemap, en klik **creëren**.
1. Op **creeer de dialoog van de Configuratie**, specificeer een titel voor de configuratie en klik **creeer**.

   U wordt opnieuw gericht aan de configuratiepagina.

1. In de Edit dialoog van de Component die verschijnt, verstrek uw identiteitskaart van het Bewerken en klik **O.K.**.

Voer de volgende stappen uit om een thema te vormen om de configuratie van Adobe Fonts te gebruiken:

1. Open een thema in de themaeditor voor de auteurinstantie.
1. In de themaredacteur, navigeer aan **de Opties van het Thema** ![ thema-opties ](assets/theme-options.png) > **vormen**.
1. In **het gebied van de Configuratie van Adobe Fonts**, selecteer een uitrusting, en klik **sparen**.

   U ziet nu dat de lettertypen zijn toegevoegd aan de eigenschap font-family van het thema.

### Lettertypen weergeven en selecteren in themaeditor {#listing-and-selecting-fonts-in-theme-editor}

U kunt de dienst van de themaconfiguratie gebruiken om meer doopvonten aan de themaredacteur toe te voegen. Voer de volgende stappen uit om lettertypen toe te voegen:

1. Meld u aan bij AEM webconsole met beheerdersrechten. URL voor de AEM webconsole is `https://'[server]:[port]'/system/console/configMgr` .
1. Open **de Aangepaste Dienst van de Configuratie van het Thema van de Vorm**.

   ![ thema-config ](assets/theme-config.png)

1. Klik +, specificeer de naam van de doopvont, en klik **sparen**. Het lettertype wordt toegevoegd en is beschikbaar in de themaeditor.

#### Lettertypen selecteren in themaeditor {#selecting-fonts-in-theme-editor}

U kunt de knop + gebruiken om een lettertype toe te voegen. Wanneer u een lettertype toevoegt, wordt dit weergegeven in het zijpaneel.

![ Nieuwe doopvont die in de themaredacteur ](assets/theme-font.png) wordt vermeld

Naast de optie voor themaconfiguratie kunt u ook uw lettertype uit de themaeditor zelf toevoegen. Typ het lettertype dat u wilt gebruiken in het veld Lettertypefamilie onder het zijpaneel en druk op de toets Enter op het toetsenbord.

![ het Typen en het selecteren doopvont in themaredacteur ](assets/font-selection.png)

Wanneer u een lettertype selecteert, wordt dit toegevoegd onder de lijst van lettertypefamilies. Met de optie Masker in de themaeditor kunt u de weergegeven lettertypen in- of uitschakelen.

![ multi-doopvonten ](assets/multi-fonts.jpg)

U ziet de wijziging in het lettertype van de component.

Het veld Lettertypefamilie ondersteunt meerdere lettertypen. Wanneer u een lettertype typt, zoekt de browser ernaar en past deze toe op de geselecteerde component. Als de browser geen lettertype kan vinden, zoekt het naar een lettertype dat er naast ligt in de familie. U kunt beginnen met het typen van het specifieke lettertype dat u zoekt. Als u niet het lettertype vindt dat u wilt gebruiken, kunt u een algemeen lettertype in de familie typen en dit gebruiken.

#### Maskerstijlen die zijn toegepast in de themaeditor {#mask-styles-applied-in-theme-editor}

U kunt stijlen maskeren die in een thema zijn toegepast. In de sidebar van de themaredacteur, kunt u ![ gebruiken toggle_eye ](assets/toggle_eye.png) pictogram om een toegepaste stijl onbruikbaar te maken. Als u bijvoorbeeld de afmetingen van een component in een formulier of interactieve communicatie wijzigt, kunt u deze uitschakelen met de maskerknop links van een eigenschap. Wanneer u een thema opslaat, blijven de geselecteerde maskeringsopties behouden.

![ optie van het Masker beschikbaar in sidebar van de themageditor ](assets/mask-styles.png)

In het onderstaande voorbeeld ziet u gemaskeerde en niet-gemaskerde stijlen in een thema.

![ Gemaskeerde en unmasked stijlen ](assets/mask2.png)

## Een thema toepassen op een formulier of interactieve communicatie {#applying-a-theme-to-a-form-or-interactive-communication-br}

Een thema toepassen op een adaptief formulier:

1. Open het formulier in de bewerkingsmodus. Om een vorm op te openen geef wijze uit, selecteer een vorm en klik **Open**.
1. Op geef wijze uit, selecteer een component, dan klik ![ gebied-niveau ](assets/field-level.png) > **Aangepaste Container van de Vorm**, en klik dan ![ cmp ](assets/cmppr.png).

   U kunt eigenschappen van het formulier bewerken in de zijbalk.

1. In sidebar, klik **het Stileren**.
1. Selecteer uw thema van het **Aangepaste Thema van de Vorm** drop-down en klik **Gereed** ![ controle-knoop ](assets/check-button.png).

Een thema toepassen op een interactieve communicatie:

1. Open de interactieve communicatie in de bewerkingsmodus. Om een interactieve mededeling op uit te geven wijze te openen, selecteer een vorm en klik **Open**.
1. Op geef wijze uit, selecteer een component, dan klik ![ gebied-niveau ](assets/field-level.png) > **de Container van het Document**, en klik dan ![ cmp ](assets/cmppr.png).

   U kunt eigenschappen van het formulier bewerken in de zijbalk.

1. In sidebar, onder **Basis**, selecteer uw thema van het **thema** drop-down en klik **Gereed** ![ controle-knoop ](assets/check-button.png)

### Het thema van een formulier tijdens runtime wijzigen {#change-theme-of-a-form-at-runtime}

Met een thema kunt u verschillende onderdelen van een formulier opmaken. Met de eigenschap `themeOverride` kunt u het thema van een formulier dynamisch wijzigen. Een typische URL van een formulier is:

`https://<server>:<port>/content/forms/af/test.html`

U kunt de parameter themeOverride gebruiken om een thema op runtime toe te passen.

`https://<server>:<port>/content/forms/af/test.html?themeOverride=/content/dam/formsanddocuments-themes/simpleEnrollmentTheme`

Met de optie `themeOverride` kunt u een pad naar een thema opgeven. Het wijzigt het thema van het formulier en vernieuwt het formulier met bijgewerkte stijlen.

## Specifieke weergave ophalen met thema&#39;s {#specific-af-appearance}

Met AEM Forms zijn er, samen met het standaard canvasthema voor buitengebruik, veel andere thema&#39;s. Als u een formulier of interactieve communicatie met andere thema&#39;s wilt ontwerpen, alsmede aanvullende wijzigingen, kopieert u het thema uit de map Themabibliotheek. Plak de gekopieerde thema&#39;s buiten de map Themabibliotheek en bewerk het gekopieerde thema op basis van de gewenste wijzigingen.

Voer de volgende stappen uit om een thema te kopiëren:

1. In auteursinstantie, navigeer aan **Adobe Experience Manager > Forms > Thema&#39;s**.
1. Open de map Themabibliotheek.
1. In de omslag van de Bibliotheek van het Thema, houd wijzer over het overeenkomstige uit-van-de-doos thema en selecteer **Exemplaar**.
1. Plak het gekopieerde thema buiten de map Themabibliotheek.
1. Pas het gekopieerde thema aan.

Nadat u het thema hebt aangepast, past u het toe op uw formulier of interactieve communicatie.

>[!NOTE]
>
>Wijzig de thema&#39;s in de map Themabibliotheek niet. Deze map bevat systeemthema&#39;s. Wijzigingen die u in deze thema&#39;s hebt aangebracht, worden overschreven wanneer u een nieuwere versie of hotfix van AEM Forms installeert.

## Gevolgen voor andere adaptieve gevallen van formuliergebruik {#impact-on-other-adaptive-form-use-cases}

* **Publish/unpublish een vorm:** Bij het publiceren van een vorm, wordt het thema toegepast op ook gepubliceerd (als het niet reeds wordt gepubliceerd)
* **de Invoer/de Uitvoer een vorm:** bij het invoeren of het uitvoeren van een vorm, wordt zijn bijbehorend thema ook automatisch ingevoerd of uitgevoerd.
* **Verwijzingen van een vorm:** Verwijst sectie in vormverwijzingen bevat een extra ingang voor het thema.
* **Laatste wijzigingstijd van een vorm:** Bijgewerkt wanneer het bijbehorende thema wordt veranderd.
* **het Testen A/B:** u kunt een verschillend thema op twee versies van de vorm in het testen A/B toepassen. De informatie over de twee thema&#39;s wordt afzonderlijk opgeslagen op de twee hulplijncontainers.

## CSS-generatiereeks {#css-generation-sequence}

Wanneer u weergave-CSS selecteert, verzamelt de Thema-editor alle opmaakgegevens en wordt een CSS gemaakt. Het verzamelt informatie in de volgende orde:

1. Stijl die in de basisclientbibliotheek van het thema wordt gedefinieerd.
1. Door gebruiker gedefinieerde stijl, opgegeven met gebruik van de eigenschappen in de zijbalk.
1. CSS-stijl opgegeven met de optie CSS overschrijven.

De achtergrondkleur van een tekstvak is bijvoorbeeld blauw in de basisclientbibliotheek. U wijzigt de afbeelding in roze met de eigenschappen in de zijbalk. Wanneer u CSS genereert, ziet u de achtergrondkleur van het tekstvak roze. Nadat de achtergrondkleur is gewijzigd met de eigenschappen, gebruikt een andere auteur de CSS-overschrijvingsoptie om het tekstvak voor de achtergrondkleur als wit te wijzigen. Wanneer u CSS genereert, ziet u achtergrondkleur als wit in de gegenereerde CSS.

## Foutopsporingsstijlen {#debugging-styles}

Wanneer u stijlen voor componenten opgeeft in de Thema-editor, wordt een CSS gegenereerd. Wanneer u een generische component opmaakt, worden ook meerdere componenten in de component opgemaakt. Wanneer u bijvoorbeeld een veld opmaakt, worden het tekstvak en het label ook opgemaakt. Wanneer u het tekstvak binnen het veld opmaakt, krijgt het een eigen CSS. Als u fouten wilt opsporen in de CSS die voor het veld en de component is gegenereerd, biedt de Thema-editor opties waarmee u CSS kunt weergeven.

De gegenereerde CSS kunt u met de volgende opties zien:

* **CSS van de Mening** optie in sidebar: Wanneer u een component in het Thema selecteert, kunt u de WEERGAVE CSS optie in sidebar zien. De gegenereerde CSS wordt weergegeven, inclusief CSS voor `::before` - en `::after` pseudo-elementen.
* **optie van het Thema van 0&rbrace; Mening CSS &lbrace;in de canvastoolbar: In de Toolbar van het Canvas, klik ![ thema-opties ](assets/theme-options.png) >** het Thema CSS van de Mening **.** U kunt het volledige thema CSS zien die van de eigenschappen wordt geproduceerd u in de Redacteur van het Thema bepaalt.

## Problemen oplossen, aanbevelingen en aanbevolen procedures {#troubleshooting-recommendations-and-best-practices}

* **vermijdend activa van een ander Thema**

  Wanneer u een thema bewerkt, kunt u door elementen (zoals afbeeldingen) bladeren en elementen uit andere thema&#39;s toevoegen. U bewerkt bijvoorbeeld de achtergrond van een pagina. Bijvoorbeeld, wanneer u **Pagina** ![ uitgezocht geef-knoop ](assets/edit-button.png) > **Achtergrond** > **voegt** toe > **Beeld**, ziet u een dialoog die u laat doorbladeren en beelden in ander thema toevoegen.

* U kunt problemen met uw huidige thema oplossen als een element wordt toegevoegd uit een ander thema en het andere thema wordt verplaatst of verwijderd. U wordt aangeraden te voorkomen dat u bladeren en elementen uit andere thema&#39;s toevoegt.
* **Gebruikend basis clientlib, themaredacteur, en gealigneerd het stileren**

   * **Clilib van de Basis**:

     De basisclientbibliotheek bevat opmaakgegevens. Stijlinformatie in bibliotheken aan de clientzijde in thema&#39;s gebruiken.

      1. Navigeer aan **Experience Manager > Forms > Thema&#39;s**.
      1. In de pagina van Thema&#39;s, selecteer een thema en klik **Eigenschappen van de Mening**.
      1. In de pagina van Eigenschappen die opent, klik **Geavanceerd**.
      1. Blader op het tabblad Geavanceerd in het veld Clientlib-locatie naar de clientbibliotheek die u wilt gebruiken en selecteer deze.
      1. Klik **sparen**.

     De stijl die u opgeeft in de clientbibliotheek, wordt geïmporteerd in het thema dat deze stijl gebruikt. U geeft bijvoorbeeld de opmaak op voor tekstvak, numeriek vak en voor de clientbibliotheek. Wanneer u de clientbibliotheek in het thema importeert, wordt de stijl voor het tekstvak, het numerieke vak en de switch geïmporteerd. Vervolgens kunt u andere componenten opmaken met behulp van de themaeditor.
U kunt ook een thema maken, er kopieën van maken en vervolgens de opmaak wijzigen die in de gekopieerde thema&#39;s wordt geboden voor vergelijkbare gebruiksdoeleinden.
Zie [ Worden specifieke verschijning gebruikend Thema&#39;s ](#specific-af-appearance)

   * **Redacteur van het Thema:**

     Met de Thema-editor kunt u thema&#39;s maken om uw formulier of interactieve communicatie op te maken. U kunt de opmaak van componenten in een thema opgeven, zodat u de weergave in meerdere formulieren of interactieve communicatie die u ontwikkelt consistent kunt houden. Het wordt aanbevolen om opmaakgegevens op te geven in een thema en het thema vervolgens toe te passen op een formulier.

   * **Inline het stileren:**

     Als u met een formulier werkt, kunt u de stijlmodus gebruiken in de vorm van een formulier of de interactieve multikanaaleditor voor communicatie. Als u de stijl van een formuliercomponent wijzigt, overschrijft u de stijl die in het thema is opgegeven. Als u het stileren voor bepaalde componenten van een bepaalde vorm wilt veranderen, zie [ Inline het stileren van componenten ](../../forms/using/inline-style-adaptive-forms.md).

* **Gebruikend cliënt-zijbibliotheken**

  Als u cliëntbibliotheken wilt tot stand brengen om het stileren informatie in te voeren, zie [ Gebruikend de Bibliotheken van de Kant van de Cliënt ](/help/sites-developing/clientlibs.md). Nadat u een clientbibliotheek hebt gemaakt, kunt u deze in uw thema importeren aan de hand van de bovenstaande stappen.

* **Veranderend de lay-outbreedte van het containerpaneel**

  Het wordt niet aanbevolen de lay-outbreedte van het containervenster te wijzigen. Wanneer u de breedte van een containerdeelvenster opgeeft, wordt het statisch en wordt het niet aangepast aan verschillende weergaven.

* **wanneer om vormredacteur of themaredacteur voor het werken met kopbal en footer te gebruiken**

  Gebruik de themaeditor als u koptekst en voettekst wilt opmaken met opmaakopties zoals lettertypestijl, achtergrond en transparantie.
Gebruik de opties voor de formuliereditor als u informatie wilt opgeven, zoals een logoafbeelding, een bedrijfsnaam in de koptekst en copyrightinformatie in de voettekst.
