---
title: Inleiding tot Interactive Communication authoring UI
description: Een inleiding aan de diverse elementen van de gebruikersinterface u aan auteur Interactieve Communicatie kunt gebruiken
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications
docset: aem65
feature: Interactive Communication
exl-id: 3d15a723-df6c-4b4a-992e-a6636f4cf3dc
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 0%

---

# Inleiding tot Interactive Communication authoring UI{#introduction-to-interactive-communication-authoring-ui}

Het gebruikersinterface voor creatie [&#x200B; Interactieve Communicatie &#x200B;](/help/forms/using/interactive-communications-overview.md) is intuïtief en verstrekt het volgende voor auteursdruk en Webkanaal van de Interactieve Mededeling:

* WYSIWYG-documenteditor voor slepen en neerzetten
* Geïntegreerde opslagplaats voor middelen - de activa die aan worden geupload en op de server worden gecreeerd zijn beschikbaar in de browser van Activa van Interactive Communication auteursinterface

Wanneer u [&#x200B; creeert of een bestaande Interactieve Mededeling &#x200B;](../../forms/using/create-interactive-communication.md) uitgeeft, gebruikt u de volgende elementen van het gebruikersinterface:

* [Zijbalk](#sidebar)
* [Pagina, werkbalk](#page-toolbar)
* [Component, werkbalk](#component-toolbar)
* Inhoudsgebied

![&#x200B; interactieve mededeling auteursgebruikersinterface &#x200B;](assets/form-editor.png)

**A.** Sidebar **B.** de toolbar van de Pagina **C.** Inhoudsgebied

## Zijbalk {#sidebar}

![&#x200B; Sidebar &#x200B;](assets/sidebar-comps-2.png)

**A.** browser van het Kanaal **B.** browser van de Inhoud **C.** browser van Eigenschappen **D.** browser van Activa **E.** browser van Componenten 10&rbrace; F.**browser van Gegevensbronnen - het Model van Gegevens** G.**Browser van Gegevensbronnen - HoofdInhoud**

<!-- Click to enlarge

![sidebar-comps-3](assets/sidebar-comps-3.png)-->

De zijbalk bevat het volgende:

* **browser van het Kanaal**

Met de kanaalbrowser kunt u schakelen tussen de afdruk- en webkanalen van de interactieve communicatie. Op basis van het kanaal dat u in de kanaalbrowser hebt geselecteerd, worden de opties weergegeven in browsers zoals Inhoud en Componenten.

* **browser van de Inhoud**
In de inhoudbrowser, kunt u objecten hiërarchie van het document voor het geselecteerde kanaal zien. Auteurs kunnen naar een bepaalde component navigeren door op dat element te tikken in de documentobjectenstructuur. Auteurs kunnen objecten zoeken in het webkanaal en ze opnieuw rangschikken vanuit deze structuur.

* **browser van Eigenschappen**

  Hiermee kunt u de eigenschappen van een component bewerken. De eigenschappen veranderen afhankelijk van de component. Als u bijvoorbeeld de eigenschappen van de documentcontainer wilt zien:
Selecteer een component, dan uitgezocht ![&#x200B; gebied-niveau &#x200B;](assets/field-level.png) > **de Container van het Document**, en selecteer dan ![&#x200B; cmp &#x200B;](assets/cmppr.png).

* **browser van Assets**
Hiermee kunt u verschillende typen inhoud segmenteren, zoals lay-outfragmenten, afbeeldingen, documenten, pagina&#39;s, video&#39;s. Auteurs kunnen elementen naar de interactieve communicatie slepen.

* **browser van Componenten**
Bevat componenten die u kunt gebruiken om de afdruk- en webkanalen van een document samen te stellen. U kunt componenten aan de Interactieve Mededeling slepen om elementen toe te voegen, en toegevoegde element te vormen zoals aan de vereisten. In de volgende tabel worden de componenten beschreven die in de browser Components worden weergegeven voor afdrukken en webkanalen:

| **Component** | **Kanaal van de Druk** | **Kanaal van 0&rbrace; Web** | **Functionaliteit** |
|---|---|---|---|
| Diagram | ✓ | ✓ | Hiermee voegt u een grafiek toe die u in een interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzamelitem van een formuliergegevensmodel. |
| Documentfragment | ✓ | ✓ | Hiermee kunt u een herbruikbare component, tekst, lijst of voorwaarde toevoegen aan een interactieve communicatie. De herbruikbare component die u toevoegt aan een interactieve communicatie kan gebaseerd zijn op een formuliergegevensmodel of geen formuliergegevensmodel. |
| Afbeelding | ✓ | ✓ | Hiermee kunt u een afbeelding invoegen. |
| Deelvenster | - | ✓ | De component van het Comité is placeholder voor het groeperen van andere componenten samen en controleert hoe een groep componenten in een Interactieve Mededeling worden uiteengezet. Met een deelvenstercomponent kunt u ook een groep componenten herhaalbaar maken voor de eindgebruiker, bijvoorbeeld in meerdere items die nodig zijn om de gegevens van het onderwijs in te vullen. Het is ook een goede praktijk om een paneel elk voor een lusje van een Interactieve Communicatie met veelvoudige lusjes te gebruiken. |
| Tabel | &#42; | ✓ | Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. |
| Doelgebied | &#42;&#42; | ✓ | Hiermee voegt u een doelgebied in een webkanaal in om de webkanaalspecifieke componenten te ordenen. |
| Tekst | - | ✓ | Hiermee voegt u tekst toe aan het webkanaal van een interactieve communicatie. Tekst kan objecten van het formuliergegevensmodel gebruiken om de inhoud dynamisch te maken. |

&#42; Gebruik Lay-outfragmenten in het kanaal Afdrukken om tabellen toe te voegen.

&#42;&#42; In het kanaal Afdrukken zijn de doelgebieden vooraf gedefinieerd in de XDP/afdruksjabloon. U kunt geen nieuwe doelgebieden toevoegen gebruikend Interactieve Communicatie auteursUI.

* **Browser van Gegevensbronnen**
Browser van Gegevensbronnen toont de beschikbare gegevensbronnen in het model van vormgegevens u terwijl het creëren van de Interactieve Communicatie selecteerde.

### Belangrijke punten voor het werken met componenten {#key-points-for-working-with-components}

De belangrijkste punten wanneer het werken met interactieve communicatie componenten zijn als volgt:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Om de eigenschappen van een component te vormen, selecteer de component en selecteer ![&#x200B; cmp &#x200B;](assets/cmppr.png) om de componenteneigenschappen in browser van Eigenschappen te openen.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u ![&#x200B; cmp &#x200B;](assets/cmppr.png) selecteert, kunt u de naam van de component veranderen door de het gebiedswaarde van de Naam van het Element in eigenschappen browser te veranderen. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.
* U kunt het bezit van de Titel van een Interactieve Component van de Communicatie inline in de redacteur wijzigen zonder browser van Eigenschappen te openen zolang de titel op Interactieve Mededeling zichtbaar is. Daartoe:

   1. Selecteer deze optie om een component te selecteren die een eigenschap Titel heeft en waarvan de eigenschap Titel verbergen is uitgeschakeld.
   1. Selecteer ![&#x200B; name_6_3_edit &#x200B;](assets/aem_6_3_edit.png) om de titel editable te maken.

   1. Wijzig de titel en selecteer de Return-toets of selecteer een willekeurige locatie buiten de component om de wijzigingen op te slaan. Selecteer de sleutel van Esc om de veranderingen te verwerpen.

## Component, werkbalk {#component-toolbar}

![&#x200B; de toolbaretiketten van de Component &#x200B;](do-not-localize/component_toolbar_labels_new.png)

Wanneer u een component selecteert, ziet u een werkbalk waarmee u ermee kunt werken. U krijgt opties om, eigenschappen van de componenten te snijden te kleven, te bewegen en te specificeren. U kunt kiezen uit de volgende opties:

A.**vormt**: Wanneer u **&#x200B;**&#x200B;selecteert, zijn de componenteneigenschappen zichtbaar in sidebar.

B. **geeft Regels** uit: Wanneer u uitgezocht geef Regels uit, verschijnt de Redacteur van de Regel waarin u regels voor de geselecteerde component kunt uitgeven en creëren. In de Regeleditor kunt u ook andere formulierobjecten (componenten) selecteren en regels voor die formulierobjecten bewerken/maken.

C.**Exemplaar**: U kunt de exemplaaroptie gebruiken om een component te kopiëren en het in andere plaatsen in de Interactieve Mededeling te kleven.

D.**Besnoeiing**: U kunt de besnoeiingsoptie gebruiken om een component van één plaats aan een andere in de Interactieve Mededeling te bewegen.

E. **Schrapping**: Laat u de component van de Interactieve Mededeling schrappen.

F. **Component van het Tussenvoegsel**: Laat u een component boven de geselecteerde component opnemen.

G. **Deeg**: Laat u de component kleven u knipt of gebruikend de hierboven beschreven opties kopieerde.

H. **Groep**: Laat u veelvoudige componenten selecteren als u, meer dan één component samen knippen kopiëren of wilt kleven.

I. **Ouder**: Laat u de ouder van een component selecteren.

J. **Uitdrukking SOM van de Mening:** laat u de [&#x200B; uitdrukking SOM &#x200B;](../../forms/using/using-som-expressions-adaptive-forms.md) voor de component bekijken.

K: **de voorwerpen van de Groep in Comité:** laat u de componenten in een paneel groeperen om verrichtingen op die componenten gelijktijdig kunnen uitvoeren. Voor details, zie [&#x200B; voorwerpen van de Groep in Comité &#x200B;](create-interactive-communication.md#groupobjectspanel).

L. **voegt het Comité van het Kind** toe (voor panelen slechts): Laat u een kindpaneel aan het paneel toevoegen.

M: **voegt Toolbar van het Comité** (voor panelen slechts) toe:Laat u Toolbar voor de component van het Comité toevoegen. U kunt vervolgens verdere handelingen uitvoeren op de werkbalk.

Bovendien **vervangt** optie op de toolbar laat u de bestaande component met een afwisselende component vervangen. De optie is niet beschikbaar voor de component Panel.

## Pagina, werkbalk {#page-toolbar}

De werkbalk Pagina bovenaan biedt opties waarmee u een voorvertoning van de interactieve communicatie kunt weergeven en de eigenschappen van de communicatie kunt wijzigen. U kunt een voorvertoning van de interactieve communicatie weergeven wanneer u deze ontwerpt en wijzigingen daarop aanbrengen. In de paginabooltoolbar, ziet u:

* Knevel zijComité ![&#x200B; knevel-zij-paneel &#x200B;](assets/toggle-side-panel.png): Laat u Zijbalk tonen of verbergen.
* De informatie van de pagina ![&#x200B; pageinformationad &#x200B;](assets/pageinformationad.png): Laat u paginaeigenschappen bekijken.
* Emulator ![&#x200B; heerser &#x200B;](assets/ruler.png): Laat u het blik van uw Interactieve Mededeling voor verschillende vertoningsgrootte zoals tabletten en telefoons emuleren.
* Bewerken: hiermee kunt u andere modi selecteren, zoals Bewerken, Stijl, Ontwikkelaar en Ontwerp.

   * Bewerken: hiermee kunt u de eigenschappen van de interactieve communicatie en de bijbehorende componenten bewerken. U kunt bijvoorbeeld een component toevoegen, een afbeelding neerzetten en verplichte velden opgeven.
   * Stijl: laat u de verschijning van componenten van uw Interactieve Communicatie opmaken. In de stijlmodus kunt u bijvoorbeeld een deelvenster selecteren en de achtergrondkleur ervan opgeven.
   * Ontwikkelaar: laat een ontwikkelaar het volgende doen:

      * Ontdek waar Interactieve communicatie uit bestaat.
      * Foutopsporing waar en wanneer gebeurt, wat weer helpt om problemen op te lossen.

   * Doel: Hiermee kunt u aangepaste componenten, of componenten buiten het vak die niet in de zijbalk worden vermeld, in- of uitschakelen.

* Voorbeeld: hiermee kunt u een voorvertoning weergeven van de Interactieve communicatie wanneer u deze publiceert.
