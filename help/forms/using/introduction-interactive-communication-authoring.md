---
title: Inleiding tot Interactive Communication authoring UI
seo-title: Een inleiding aan de diverse elementen van de gebruikersinterface u aan auteur Interactieve Communicatie kunt gebruiken
description: Een inleiding aan de diverse elementen van de gebruikersinterface u aan auteur Interactieve Communicatie kunt gebruiken
seo-description: Een inleiding aan de diverse elementen van de gebruikersinterface u aan auteur Interactieve Communicatie kunt gebruiken
uuid: e8c5b1e8-b2bb-46b4-b42e-1f343192641a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications
discoiquuid: 5855d21b-340c-4139-aabe-c3a534cedb98
docset: aem65
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Inleiding tot Interactive Communication authoring UI{#introduction-to-interactive-communication-authoring-ui}

De gebruikersinterface voor creatie [Interactieve Communicatie](/help/forms/using/interactive-communications-overview.md) is intuïtief en verstrekt het volgende voor auteursdruk en Webkanaal van de Interactieve Mededeling:

* WYSIWYG-documenteditor voor slepen en neerzetten
* Geïntegreerde opslagplaats voor middelen - de activa die aan worden geupload en op de server worden gecreeerd zijn beschikbaar in de browser van Activa van Interactive Communication auteursinterface

Wanneer u een nieuwe [creeert of een bestaande Interactieve Communicatie](../../forms/using/create-interactive-communication.md)uitgeeft, gebruikt u de volgende gebruikersinterfaceelementen:

* [Zijbalk](#sidebar)
* [Pagina, werkbalk](#page-toolbar)
* [Component, werkbalk](#component-toolbar)
* Inhoudsgebied

![gebruikersinterface voor interactieve communicatie ontwerpen](assets/form-editor.png)

**A.** Zijbalk **B.** Pagina, werkbalk **C.** Inhoudsgebied

## Zijbalk {#sidebar}

![Zijbalk](assets/sidebar-comps-2.png)

**A.** Kanaalbrowser **B.** Inhoudsbrowser **C.** Eigenschappen browser **D.** Middelenbrowser **E.** Browser van componenten **F.** Browser van Gegevensbronnen - het Model van Gegevens **G.** Browser voor gegevensbronnen - stramieninhoud

<!-- Click to enlarge

![sidebar-comps-3](assets/sidebar-comps-3.png)-->

De zijbalk bevat het volgende:

* **Kanaalbrowser**

Met de kanaalbrowser kunt u schakelen tussen de afdruk- en webkanalen van de interactieve communicatie. Op basis van het kanaal dat u in de kanaalbrowser hebt geselecteerd, worden de opties weergegeven in browsers zoals Inhoud en Componenten.

* **De inhoudbrowser** In de inhoudbrowser kunt u de objecthiërarchie van het document voor het geselecteerde kanaal zien. Auteurs kunnen naar een bepaalde component navigeren door op dat element te tikken in de documentobjectenstructuur. Auteurs kunnen objecten zoeken in het webkanaal en ze opnieuw rangschikken vanuit deze structuur.

* **Eigenschappenbrowser**

   Hiermee kunt u de eigenschappen van een component bewerken. De eigenschappen veranderen afhankelijk van de component. Als u bijvoorbeeld de eigenschappen van de documentcontainer wilt zien:
Selecteer een component, tik vervolgens op ![veldniveau](assets/field-level.png) > **Documentcontainer** en tik vervolgens op ![cmp](assets/cmppr.png).

* **De browser** Middelen segregeert verschillende soorten inhoud zoals lay-outfragmenten, beelden, documenten, pagina&#39;s, video&#39;s. Auteurs kunnen elementen naar de interactieve communicatie slepen.

* **De browser** van componenten omvat componenten die u kunt gebruiken om de druk en Webkanalen van een document te bouwen. U kunt componenten aan de Interactieve Mededeling slepen om elementen toe te voegen, en toegevoegde element te vormen zoals aan de vereisten. In de volgende tabel worden de componenten beschreven die in de browser Components worden weergegeven voor afdrukken en webkanalen:

| **Component** | **Afdrukkanaal** | **Webkanaal** | **Functionaliteit** |
|---|---|---|---|
| Diagram | ✓ | ✓ | Hiermee voegt u een grafiek toe die u in een interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzamelitem van een formuliergegevensmodel. |
| Documentfragment | ✓ | ✓ | Staat u toe om een herbruikbare component, een tekst, een lijst, of een voorwaarde, aan een Interactieve Communicatie toe te voegen. De herbruikbare component die u toevoegt aan een interactieve communicatie kan gebaseerd zijn op een formuliergegevensmodel of geen formuliergegevensmodel. |
| Afbeelding | ✓ | ✓ | Hiermee kunt u een afbeelding invoegen. |
| Deelvenster | - | ✓ | De component van het Comité is placeholder voor het groeperen van andere componenten samen en controleert hoe een groep componenten in een Interactieve Mededeling worden uiteengezet. Met een deelvenstercomponent kunt u ook een groep componenten herhaalbaar maken voor de eindgebruiker, bijvoorbeeld in meerdere items die nodig zijn om de gegevens van het onderwijs in te vullen. Het is ook een goede praktijk om een paneel elk voor een lusje van een Interactieve Communicatie met veelvoudige lusjes te gebruiken. |
| Tabel | * | ✓ | Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. |
| Doelgebied | ** | ✓ | Hiermee voegt u een doelgebied in een webkanaal in om de webkanaalspecifieke componenten te ordenen. |
| Tekst | - | ✓ | Hiermee voegt u tekst toe aan het webkanaal van een interactieve communicatie. Tekst kan formuliergegevensmodelobjecten gebruiken om de inhoud dynamisch te maken. |

* Gebruik Layoutfragmenten in het kanaal Afdrukken om tabellen toe te voegen.

** In het kanaal Afdrukken zijn de doelgebieden vooraf gedefinieerd in de XDP/afdruksjabloon. U kunt geen nieuwe doelgebieden toevoegen gebruikend Interactieve Communicatie auteursUI.

* **Browser** van de Gegevensbronnen van Gegevensbronnen van Gegevensbronnen Browser toont de beschikbare gegevensbronnen in het model van vormgegevens u terwijl het creëren van de Interactieve Mededeling selecteerde.

### Belangrijke punten voor het werken met componenten {#key-points-for-working-with-components}

De belangrijkste punten wanneer het werken met interactieve communicatie componenten zijn als volgt:

* Elke component heeft bijbehorende eigenschappen die de weergave en functionaliteit ervan bepalen. Tik op de component en tik op ![cmp](assets/cmppr.png) om de eigenschappen van een component te configureren. Open vervolgens de eigenschappen van de component in de eigenschappenbrowser.
* Een component wordt geïdentificeerd met zijn elementnaam. Wanneer u op ![cmp](assets/cmppr.png)tikt, kunt u de naam van de component wijzigen door de waarde van het veld Elementnaam te wijzigen in de eigenschappenbrowser. Het veld Elementnaam accepteert alleen letters, cijfers, koppeltekens (-) en onderstrepingstekens (_). Andere speciale tekens zijn niet toegestaan en de elementnaam moet met een letter beginnen.
* U kunt het bezit van de Titel van een Interactieve Component van de Communicatie inline in de redacteur wijzigen zonder browser van Eigenschappen te openen zolang de titel op Interactieve Mededeling zichtbaar is. Daartoe:

   1. Tik om een component te selecteren die een eigenschap Titel heeft en waarvan de eigenschap Titel verbergen is uitgeschakeld.
   1. Tik op ![naam_6_3_bewerken](assets/aem_6_3_edit.png) om de titel bewerkbaar te maken.

   1. Wijzig de titel en tik op de Return-toets of tik ergens buiten de component om de wijzigingen op te slaan. Tik op Esc om de wijzigingen te verwijderen.

## Component, werkbalk {#component-toolbar}

![Componentwerkbalklabels](do-not-localize/component_toolbar_labels_new.png)

Wanneer u een component selecteert, ziet u een werkbalk waarmee u ermee kunt werken. U krijgt opties om, eigenschappen van de componenten te snijden te kleven, te bewegen en te specificeren. U kunt kiezen uit de volgende opties:

A.**Configureren**: Wanneer u op **Configureren** tikt, zijn componenteigenschappen zichtbaar in de zijbalk.

B.Regels **** bewerken: Wanneer u op Regels bewerken tikt, wordt de Regeleditor weergegeven waarin u regels voor de geselecteerde component kunt bewerken en maken. In de Regeleditor kunt u ook andere formulierobjecten (componenten) selecteren en regels voor die formulierobjecten bewerken/maken.

C.**Kopiëren**: Met de kopieeroptie kunt u een component kopiëren en op andere plaatsen in de interactieve communicatie plakken.

D.**Knippen**: U kunt de besnoeiingsoptie gebruiken om een component van één plaats aan een andere in de Interactieve Communicatie te bewegen.

E. **Verwijderen**: Hiermee kunt u de component uit de interactieve communicatie verwijderen.

F. Component **** invoegen: Hiermee kunt u een component invoegen boven de geselecteerde component.

G. **Plakken**: Hiermee kunt u de component die u hebt geknipt of gekopieerd, plakken met de hierboven beschreven opties.

H. **Groep**: Hiermee kunt u meerdere componenten selecteren als u meerdere componenten tegelijk wilt knippen, kopiëren of plakken.

I. **Bovenliggend element**: Hiermee kunt u het bovenliggende element van een component selecteren.

J. SOM-expressie **weergeven:** Hiermee kunt u de [SOM-expressie](../../forms/using/using-som-expressions-adaptive-forms.md) voor de component weergeven.

K: Objecten **groeperen in deelvenster:** Hiermee kunt u de componenten in een deelvenster groeperen en tegelijkertijd bewerkingen op die componenten uitvoeren. Zie Objecten [groeperen in deelvenster](create-interactive-communication.md#groupobjectspanel)voor meer informatie.

L. Deelvenster **Onderliggend element** toevoegen (alleen voor deelvensters): Hiermee kunt u een onderliggend deelvenster aan het deelvenster toevoegen.

M: Werkbalk **Deelvenster** toevoegen (alleen voor deelvensters):Hiermee kunt u de werkbalk voor de component Deelvenster toevoegen. U kunt vervolgens verdere handelingen uitvoeren op de werkbalk.

Daarnaast kunt u met de optie **Vervangen** op de werkbalk de bestaande component vervangen door een alternatieve component. De optie is niet beschikbaar voor de component Panel.

## Pagina, werkbalk {#page-toolbar}

De werkbalk Pagina bovenaan biedt opties waarmee u een voorvertoning van de interactieve communicatie kunt weergeven en de eigenschappen van de communicatie kunt wijzigen. U kunt een voorvertoning van de interactieve communicatie weergeven wanneer u deze ontwerpt en wijzigingen daarop aanbrengen. In de paginabooltoolbar, ziet u:

* Zijpaneel in-/ ![uitschakelen](assets/toggle-side-panel.png): Hiermee kunt u Zijbalk tonen of verbergen.
* Pagina-informatie ![pagina](assets/pageinformationad.png): Hiermee kunt u pagina-eigenschappen weergeven.
* Emulatorliniaal ![](assets/ruler.png): Hiermee kunt u het uiterlijk van uw interactieve communicatie emuleren voor verschillende weergavegrootten, zoals tablets en telefoons.
* Bewerken: Hiermee kunt u andere modi selecteren, zoals: Bewerken, Stijl, Ontwikkelaar en Ontwerp.

   * Bewerken: Hiermee kunt u de eigenschappen van de interactieve communicatie en de bijbehorende componenten bewerken. U kunt bijvoorbeeld een component toevoegen, een afbeelding neerzetten en verplichte velden opgeven.
   * Stijl: Hiermee kunt u de vormgeving van componenten van uw interactieve communicatie opmaken. In de stijlmodus kunt u bijvoorbeeld een deelvenster selecteren en de achtergrondkleur ervan opgeven.
   * Ontwikkelaar: Hiermee kan een ontwikkelaar:

      * Ontdek waar Interactieve communicatie uit bestaat.
      * Foutopsporing waar en wanneer gebeurt, wat weer helpt om problemen op te lossen.
   * Doel: Hiermee kunt u aangepaste componenten, of componenten buiten het vak die niet in het zijpaneel staan, in- of uitschakelen.


* Voorvertoning: Hiermee kunt u een voorvertoning weergeven van de Interactieve communicatie wanneer u deze publiceert.

