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

De gebruikersinterface voor ontwerpen [Interactieve communicatie](/help/forms/using/interactive-communications-overview.md) is intuïtief en biedt de volgende mogelijkheden voor het ontwerpen van afdrukken en het webkanaal van de interactieve communicatie:

* WYSIWYG-documenteditor voor slepen en neerzetten
* Geïntegreerde opslagplaats voor middelen - de activa die aan worden geupload en op de server worden gecreeerd zijn beschikbaar in de browser van Activa van Interactive Communication auteursinterface

Wanneer u [een bestaande interactieve communicatie maken of bewerken](../../forms/using/create-interactive-communication.md)gebruikt u de volgende gebruikersinterface-elementen:

* [Zijbalk](#sidebar)
* [Pagina, werkbalk](#page-toolbar)
* [Component, werkbalk](#component-toolbar)
* Inhoudsgebied

![gebruikersinterface voor interactieve communicatie ontwerpen](assets/form-editor.png)

**A.** Zijbalk **B.** Pagina, werkbalk **C.** Inhoud

## Zijbalk {#sidebar}

![Zijbalk](assets/sidebar-comps-2.png)

**A.** Kanaalbrowser **B.** Inhoudsbrowser **C.** Eigenschappenbrowser **D.** Middelenbrowser **E.** Browser voor componenten **F.** Browser van Gegevensbronnen - het Model van Gegevens **G.** Browser voor gegevensbronnen - stramieninhoud

<!-- Click to enlarge

![sidebar-comps-3](assets/sidebar-comps-3.png)-->

De zijbalk bevat het volgende:

* **Kanaalbrowser**

Met de kanaalbrowser kunt u schakelen tussen de afdruk- en webkanalen van de interactieve communicatie. Op basis van het kanaal dat u in de kanaalbrowser hebt geselecteerd, worden de opties weergegeven in browsers zoals Inhoud en Componenten.

* **Inhoudsbrowser**
In de inhoudbrowser, kunt u objecten hiërarchie van het document voor het geselecteerde kanaal zien. Auteurs kunnen naar een bepaalde component navigeren door op dat element te tikken in de documentobjectenstructuur. Auteurs kunnen objecten zoeken in het webkanaal en ze opnieuw rangschikken vanuit deze structuur.

* **Eigenschappenbrowser**

  Hiermee kunt u de eigenschappen van een component bewerken. De eigenschappen veranderen afhankelijk van de component. Als u bijvoorbeeld de eigenschappen van de documentcontainer wilt zien: selecteer een component en selecteer vervolgens ![op veldniveau](assets/field-level.png) > **Documentcontainer** en selecteer vervolgens ![cmppr](assets/cmppr.png).

* **Bandenbrowser**
Hiermee kunt u verschillende typen inhoud segmenteren, zoals lay-outfragmenten, afbeeldingen, documenten, pagina&#39;s, video&#39;s. Auteurs kunnen elementen naar de interactieve communicatie slepen.

* **Browser voor componenten**
Bevat componenten die u kunt gebruiken om de afdruk- en webkanalen van een document samen te stellen. U kunt componenten aan de Interactieve Mededeling slepen om elementen toe te voegen, en toegevoegde element te vormen zoals aan de vereisten. In de volgende tabel worden de componenten beschreven die in de browser Components worden weergegeven voor afdrukken en webkanalen:

| **Component** | **Afdrukkanaal** | **Webkanaal** | **Functionaliteit** |
|---|---|---|---|
| Diagram | ✓ | ✓ | Hiermee voegt u een grafiek toe die u in een interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzamelitem van een formuliergegevensmodel. |
| Documentfragment | ✓ | ✓ | Hiermee kunt u een herbruikbare component, tekst, lijst of voorwaarde toevoegen aan een interactieve communicatie. De herbruikbare component die u toevoegt aan een interactieve communicatie kan gebaseerd zijn op een formuliergegevensmodel of geen formuliergegevensmodel. |
| Afbeelding | ✓ | ✓ | Hiermee kunt u een afbeelding invoegen. |
| Deelvenster | - | ✓ | De component van het Comité is placeholder voor het groeperen van andere componenten samen en controleert hoe een groep componenten in een Interactieve Mededeling worden uiteengezet. Met een deelvenstercomponent kunt u ook een groep componenten herhaalbaar maken voor de eindgebruiker, bijvoorbeeld in meerdere items die nodig zijn om de gegevens van het onderwijs in te vullen. Het is ook een goede praktijk om een paneel elk voor een lusje van een Interactieve Communicatie met veelvoudige lusjes te gebruiken. |
| Tabel | &#42; | ✓ | Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. |
| Doelgebied | &#42;&#42; | ✓ | Hiermee voegt u een doelgebied in een webkanaal in om de webkanaalspecifieke componenten te ordenen. |
| Tekst | - | ✓ | Hiermee voegt u tekst toe aan het webkanaal van een interactieve communicatie. Tekst kan objecten van het formuliergegevensmodel gebruiken om de inhoud dynamisch te maken. |

&#42; Gebruik Layoutfragmenten in het kanaal Afdrukken om tabellen toe te voegen.

&#42;&#42; In het kanaal van de Druk, zijn de doelgebieden vooraf bepaald in het XDP/drukmalplaatje. U kunt geen nieuwe doelgebieden toevoegen gebruikend Interactieve Communicatie auteursUI.

* **Browser gegevensbronnen**
Browser van Gegevensbronnen toont de beschikbare gegevensbronnen in het model van vormgegevens u terwijl het creëren van de Interactieve Communicatie selecteerde.

### Belangrijke punten voor het werken met componenten {#key-points-for-working-with-components}

De belangrijkste punten wanneer het werken met interactieve communicatie componenten zijn als volgt:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Selecteer de component en selecteer ![cmppr](assets/cmppr.png) om de componenteigenschappen in de browser van Eigenschappen te openen.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u ![cmppr](assets/cmppr.png)kunt u de naam van de component wijzigen door de waarde van het veld Elementnaam te wijzigen in de eigenschappenbrowser. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.
* U kunt het bezit van de Titel van een Interactieve Component van de Communicatie inline in de redacteur wijzigen zonder browser van Eigenschappen te openen zolang de titel op Interactieve Mededeling zichtbaar is. Daartoe:

   1. Selecteer deze optie om een component te selecteren die een eigenschap Titel heeft en waarvan de eigenschap Titel verbergen is uitgeschakeld.
   1. Selecteren ![aem_6_3_edit](assets/aem_6_3_edit.png) om de titel bewerkbaar te maken.

   1. Wijzig de titel en selecteer de Return-toets of selecteer een willekeurige locatie buiten de component om de wijzigingen op te slaan. Selecteer de sleutel van Esc om de veranderingen te verwerpen.

## Component, werkbalk {#component-toolbar}

![Componentwerkbalklabels](do-not-localize/component_toolbar_labels_new.png)

Wanneer u een component selecteert, ziet u een werkbalk waarmee u ermee kunt werken. U krijgt opties om, eigenschappen van de componenten te snijden te kleven, te bewegen en te specificeren. U kunt kiezen uit de volgende opties:

A.**Configureren**: Wanneer u **Configureren**, zijn componenteigenschappen zichtbaar in de zijbalk.

B.**Regels bewerken**: Wanneer u Regels bewerken selecteert, wordt de Regeleditor weergegeven waarin u regels voor de geselecteerde component kunt bewerken en maken. In de Regeleditor kunt u ook andere formulierobjecten (componenten) selecteren en regels voor die formulierobjecten bewerken/maken.

C.**Kopiëren**: U kunt de kopieeroptie gebruiken om een component te kopiëren en het in andere plaatsen in de Interactieve Mededeling te kleven.

D.**Knippen**: U kunt de knipoptie gebruiken om een component van één plaats aan een andere in de Interactieve Mededeling te bewegen.

E. **Verwijderen**: Hiermee kunt u de component uit de interactieve communicatie verwijderen.

F. **Component invoegen**: Hiermee kunt u een component invoegen boven de geselecteerde component.

G. **Plakken**: Hiermee kunt u de component die u hebt geknipt of gekopieerd, plakken met de hierboven beschreven opties.

H. **Groep**: Hiermee kunt u meerdere componenten selecteren als u meerdere componenten tegelijk wilt knippen, kopiëren of plakken.

I. **Bovenliggend**: Hiermee kunt u het bovenliggende element van een component selecteren.

J. **SOM-expressie weergeven:** Hiermee kunt u de [SOM-expressie](../../forms/using/using-som-expressions-adaptive-forms.md) voor de component.

K: **Objecten groeperen in deelvenster:** Hiermee kunt u de componenten in een deelvenster groeperen en tegelijkertijd bewerkingen op die componenten uitvoeren. Zie voor meer informatie [Objecten groeperen in deelvenster](create-interactive-communication.md#groupobjectspanel).

L. **Deelvenster Onderliggend element toevoegen** (alleen voor deelvensters): hiermee kunt u een onderliggend deelvenster aan het deelvenster toevoegen.

M: **Werkbalk Deelvenster toevoegen** (alleen voor deelvensters):Hiermee kunt u de werkbalk voor de component Panel toevoegen. U kunt vervolgens verdere handelingen uitvoeren op de werkbalk.

Bovendien **Vervangen** kunt u de bestaande component vervangen door een alternatieve component op de werkbalk. De optie is niet beschikbaar voor de component Panel.

## Pagina, werkbalk {#page-toolbar}

De werkbalk Pagina bovenaan biedt opties waarmee u een voorvertoning van de interactieve communicatie kunt weergeven en de eigenschappen van de communicatie kunt wijzigen. U kunt een voorvertoning van de interactieve communicatie weergeven wanneer u deze ontwerpt en wijzigingen daarop aanbrengen. In de paginabooltoolbar, ziet u:

* Zijpaneel in-/uitschakelen ![schakelen tussen zijpaneel](assets/toggle-side-panel.png): Hiermee kunt u Zijbalk tonen of verbergen.
* Pagina-informatie ![pageinformationad](assets/pageinformationad.png): Hiermee kunt u pagina-eigenschappen weergeven.
* Emulator ![liniaal](assets/ruler.png): Hiermee kunt u het uiterlijk van uw interactieve communicatie emuleren voor verschillende weergavegrootten, zoals tablets en telefoons.
* Bewerken: hiermee kunt u andere modi selecteren, zoals Bewerken, Stijl, Ontwikkelaar en Ontwerp.

   * Bewerken: hiermee kunt u de eigenschappen van de interactieve communicatie en de bijbehorende componenten bewerken. U kunt bijvoorbeeld een component toevoegen, een afbeelding neerzetten en verplichte velden opgeven.
   * Stijl: laat u de verschijning van componenten van uw Interactieve Communicatie opmaken. In de stijlmodus kunt u bijvoorbeeld een deelvenster selecteren en de achtergrondkleur ervan opgeven.
   * Ontwikkelaar: laat een ontwikkelaar het volgende doen:

      * Ontdek waar Interactieve communicatie uit bestaat.
      * Foutopsporing waar en wanneer gebeurt, wat weer helpt om problemen op te lossen.

   * Doel: Hiermee kunt u aangepaste componenten, of componenten buiten het vak die niet in de zijbalk worden vermeld, in- of uitschakelen.

* Voorbeeld: hiermee kunt u een voorvertoning weergeven van de Interactieve communicatie wanneer u deze publiceert.
