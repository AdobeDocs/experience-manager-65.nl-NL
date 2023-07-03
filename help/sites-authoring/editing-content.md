---
title: De inhoud van pagina's bewerken
description: Nadat u de pagina hebt gemaakt, kunt u de inhoud bewerken om de gewenste updates uit te voeren.
uuid: 5b4f0a8f-5196-42ea-8413-203783a0b77b
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: f92ed674-5865-4a53-8c3a-369536861f14
docset: aem65
exl-id: d5cf4478-51e4-4ca8-b3f8-6d7caed7d515
source-git-commit: d9155cdac183acbdd190da552512a1e9bcc43d64
workflow-type: tm+mt
source-wordcount: '3082'
ht-degree: 5%

---

# Paginacontent bewerken{#editing-page-content}

Nadat u de pagina hebt gemaakt (nieuw of als onderdeel van een opstart of live kopie), kunt u de inhoud bewerken en de gewenste updates uitvoeren.

Inhoud wordt toegevoegd met [componenten](/help/sites-authoring/default-components-console.md) (van toepassing op het inhoudstype) dat naar de pagina kan worden gesleept. Deze kunnen vervolgens worden bewerkt, verplaatst of verwijderd.

>[!NOTE]
>
>Uw account heeft [passende toegangsrechten](/help/sites-administering/security.md) en [machtigingen](/help/sites-administering/security.md#permissions) om pagina&#39;s te bewerken.
>
>Als u om het even welke problemen ontmoet wij adviseren u uw systeembeheerder contacteert.

>[!NOTE]
>
>Als uw pagina en/of sjabloon op de juiste wijze is ingesteld, kunt u [responsieve indeling](/help/sites-authoring/responsive-layout.md) bij het bewerken.

>[!NOTE]
>
>Wanneer in **Bewerken** in de modus, zijn koppelingen in de inhoud zichtbaar, maar **niet toegankelijk**. Gebruiken [Voorvertoningsmodus](#previewingpagestouchoptimizedui) als u wilt navigeren met de koppelingen in de inhoud.

## Werkbalk Pagina {#page-toolbar}

De paginawerkbalk biedt toegang tot de juiste functionaliteit, afhankelijk van de paginaconfiguratie.

![screen_shot_2018-03-22at111338](assets/screen_shot_2018-03-22at111338.png)

De werkbalk biedt toegang tot een groot aantal opties. Afhankelijk van uw huidige context en configuratie zijn sommige opties mogelijk niet beschikbaar.

* **Zijpaneel in-/uitschakelen**

  Hiermee opent/sluit u het zijpaneel, dat de [Middelenbrowser](/help/sites-authoring/author-environment-tools.md#assets-browser), [Componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser), en [Inhoudsstructuur](/help/sites-authoring/author-environment-tools.md#content-tree).

  ![Zijpaneel in-/uitschakelen](do-not-localize/screen_shot_2018-03-22at111425.png)

* **Pagina-informatie**

  Biedt toegang tot de [Pagina-informatie](/help/sites-authoring/author-environment-tools.md#page-information) menu met paginagegevens en handelingen die op de pagina kunnen worden uitgevoerd, zoals het weergeven en bewerken van pagina-informatie, het weergeven van pagina-eigenschappen en het publiceren/ongedaan maken van de publicatie van de pagina.

  ![Pagina-informatie](do-not-localize/screen_shot_2018-03-22at111437.png)

* **Emulator**

  Hiermee schakelt u het [emulator, werkbalk](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate), die wordt gebruikt om het uiterlijk van de pagina op een ander apparaat na te bootsen. Dit wordt automatisch in- en uitgeschakeld in de lay-outmodus.

  ![Emulator](do-not-localize/screen_shot_2018-03-22at111442.png)

* **ContextHub**

  Hiermee opent u de [contexthub](/help/sites-authoring/ch-previewing.md). Alleen beschikbaar in de modus Voorbeeld.

  ![screen_shot_2018-03-22at111543](assets/screen_shot_2018-03-22at111543.png)

* **Paginatitel**

  Dit is puur informatief.

  ![screen_shot_2018-03-22at111554](assets/screen_shot_2018-03-22at111554.png)

* **Modus selecteren**

  Geeft de huidige [mode](/help/sites-authoring/author-environment-tools.md#page-modes) en kunt u een andere modus selecteren, zoals bewerken, lay-out, tijdverdraaiing of doelversie.

  ![chlimage_1-120](assets/chlimage_1-120.png)

* **Voorvertoning**

  Inschakelen [voorbeeldmodus](/help/sites-authoring/editing-content.md#preview-mode). Hiermee wordt de pagina weergegeven zoals deze wordt weergegeven bij publicatie.

  ![chlimage_1-121](assets/chlimage_1-121.png)

* **Annoteren**

  Hiermee kunt u [annotaties](/help/sites-authoring/annotations.md) naar de pagina wanneer een pagina wordt gecontroleerd. Na de eerste annotatie schakelt het pictogram over naar een getal dat het aantal annotaties op de pagina aangeeft.

  ![Annoteren](do-not-localize/screen_shot_2018-03-22at111638.png)

### Statusmelding {#status-notification}

Als een pagina deel uitmaakt van een [werkstroom](/help/sites-authoring/workflows.md) Voor meerdere workflows wordt deze informatie weergegeven in een berichtenbalk boven aan het scherm wanneer u de pagina bewerkt.

![screen_shot_2018-03-22at111739](assets/screen_shot_2018-03-22at111739.png)

>[!NOTE]
>
>De statusbalk is alleen zichtbaar voor gebruikersaccounts met de juiste rechten.

In het bericht wordt de workflow weergegeven die op de pagina wordt uitgevoerd. Als de gebruiker betrokken is bij de huidige workflowstap, kunt u [de workflowstatus beïnvloeden](/help/sites-authoring/workflows-participating.md) en meer informatie over de workflow vindt u onder andere :

* **Voltooid** - Opent de **Voltooid werkitem** dialoogvenster

* **Delegeren** - Opent de **Voltooid werkitem** dialoogvenster

* **Details weergeven** - Opent de **Details** venster van de workflow

Workflowstappen uitvoeren en delegeren via de berichtenbalk werkt op dezelfde manier als wanneer [deelnemen aan workflows](/help/sites-authoring/workflows-participating.md) in het vak Melding.

Als de pagina aan veelvoudige werkschema&#39;s onderworpen is, wordt het aantal werkschema&#39;s getoond aan het rechtereind van het bericht samen met pijlknopen om u toe te staan om door de werkschema&#39;s te scrollen.

![chlimage_1-122](assets/chlimage_1-122.png)

## Tijdelijke aanduiding voor onderdeel {#component-placeholder}

De tijdelijke aanduiding van de component is een indicator waarmee wordt aangegeven waar een component wordt geplaatst wanneer u deze neerzet - boven de component waarover u momenteel heft.

* Bij het toevoegen van een nieuwe component aan de pagina (slepen vanuit de componentbrowser):

  ![screen_shot_2018-03-22at111928](assets/screen_shot_2018-03-22at111928.png)

* Bij het verplaatsen van een bestaande component:

  ![screen_shot_2018-03-22at112445](assets/screen_shot_2018-03-22at112445.png)

## Een component invoegen {#inserting-a-component}

### Een component invoegen vanuit de Componentbrowser {#inserting-a-component-from-the-components-browser}

U kunt een nieuwe component toevoegen door de [componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser). De [tijdelijke aanduiding voor onderdeel](#component-placeholder) toont u waar de component zal worden geplaatst:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-authoring/author-environment-tools.md#page-modes).
1. Open de [componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser).
1. Sleep de vereiste component naar de [vereiste positie](#component-placeholder).

1. [Bewerken](#editmovecopypastedelete) de component.

>[!NOTE]
>
>Op een mobiel apparaat vult de componentbrowser het volledige scherm. Nadat u een component hebt gesleept, wordt de pagina in de browser weer weergegeven, zodat u de component kunt plaatsen.

### Een component invoegen vanuit het alineasysteem {#inserting-a-component-from-the-paragraph-system}

U kunt een nieuwe component toevoegen door de **Componenten hierheen slepen** vak van het alineasysteem:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-authoring/author-environment-tools.md#page-modes).
1. Er zijn twee manieren om een nieuwe component in het alineasysteem te selecteren en toe te voegen:

   * Selecteer **Component invoegen** van de werkbalk van een bestaande component of van de **Componenten hierheen slepen** doos.

   ![screen_shot_2018-03-22at112536](assets/screen_shot_2018-03-22at112536.png)

   * Als u zich op een desktopapparaat bevindt, kunt u dubbelklikken op de knop **Componenten hierheen slepen** doos.

   De **Nieuwe component invoegen** wordt geopend zodat u de gewenste component kunt selecteren:

   ![screen_shot_2018-03-22at112650](assets/screen_shot_2018-03-22at112650.png)

1. De geselecteerde component wordt onder aan de pagina toegevoegd. [Bewerken](#editmovecopypastedelete) de component naar wens.

### Een component invoegen met de middelenbrowser {#inserting-a-component-using-the-assets-browser}

U kunt ook een nieuwe component aan de pagina toevoegen door een element van de [middelenbrowser](/help/sites-authoring/author-environment-tools.md#assets-browser). Hiermee wordt automatisch een nieuwe component van het juiste type gemaakt (en die het element bevat).

Dit is geldig voor de volgende elementtypen (sommige zijn afhankelijk van het pagina-/alineasysteem):

<table>
 <tbody>
  <tr>
   <th><strong>Elementtype</strong></th>
   <th><strong>Resulterend componenttype</strong></th>
  </tr>
  <tr>
   <td>Afbeelding</td>
   <td>Afbeelding</td>
  </tr>
  <tr>
   <td>Document</td>
   <td>Downloaden</td>
  </tr>
  <tr>
   <td>Product</td>
   <td>Product</td>
  </tr>
  <tr>
   <td>Video</td>
   <td>Flash</td>
  </tr>
  <tr>
   <td>Inhoudsfragment</td>
   <td>Inhoudsfragment<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Dit gedrag kan voor uw installatie worden gevormd. Zie [Een alineasysteem configureren, zodat een componentinstantie wordt gemaakt wanneer u een element sleept](/help/sites-developing/developing-components.md#configuring-a-paragraph-system-so-that-dragging-an-asset-creates-a-component-instance) voor nadere bijzonderheden.

Een component maken door een van de bovenstaande elementtypen te slepen:

1. Zorg ervoor dat de pagina zich bevindt in [**Bewerken** mode](/help/sites-authoring/author-environment-tools.md#page-modes).
1. Open de [middelenbrowser](/help/sites-authoring/author-environment-tools.md#assets-browser).
1. Sleep het vereiste element naar de gewenste positie. De [tijdelijke aanduiding voor onderdeel](#component-placeholder) Hiermee kunt u zien waar de component wordt geplaatst.

   Een component die geschikt is voor het type element, wordt op de vereiste locatie gemaakt. De component bevat het geselecteerde element.

1. [Bewerken](#editmovecopypastedelete) de component, indien vereist.

>[!NOTE]
>
>Op een mobiel apparaat vult de middelenbrowser het volledige scherm. Nadat u een element hebt gesleept, wordt de pagina in de browser weergegeven, zodat u het element kunt plaatsen.

Als u bij het bladeren in de elementen opmerkt dat u snel een wijziging in een element moet aanbrengen, kunt u het dialoogvenster [middeleneditor](/help/assets/manage-assets.md) rechtstreeks vanuit de browser door op het pictogram Bewerken naast de naam van het element te klikken.

![screen_shot_2018-03-22at112735](assets/screen_shot_2018-03-22at112735.png)

## Bewerken/configureren/kopiëren/knippen/verwijderen/plakken {#edit-configure-copy-cut-delete-paste}

Als u een component selecteert, wordt de werkbalk geopend. Dit verleent toegang tot diverse acties die op de component kunnen worden uitgevoerd.

De acties die de gebruiker daadwerkelijk kan uitvoeren, worden op de juiste wijze weergegeven en niet alle acties worden hier beschreven.

![screen_shot_2018-03-22at112909](assets/screen_shot_2018-03-22at112909.png)

* **Bewerken**

  [Afhankelijk van het componenttype](/help/sites-authoring/default-components.md) op die manier kunt u [de inhoud van de component bewerken](#edit-content). Er wordt vaak een werkbalk weergegeven.

  ![Bewerken](do-not-localize/screen_shot_2018-03-22at112936.png)

* **Configureren**

  [Afhankelijk van het componenttype](/help/sites-authoring/default-components.md) hierdoor kunt u de eigenschappen van de component bewerken en configureren. Vaak wordt een dialoogvenster geopend.

  ![Configureren](do-not-localize/screen_shot_2018-03-22at112955.png)

* **Kopiëren**

  Hiermee wordt de component naar het klembord gekopieerd. Na de plakactie, zal de originele component blijven.

  ![Kopiëren](do-not-localize/screen_shot_2018-03-22at113000.png)

* **Knippen**

  Hiermee wordt de component naar het klembord gekopieerd. Na de plakhandeling wordt de oorspronkelijke component verwijderd.

  ![screen_shot_2018-03-22at113007](assets/screen_shot_2018-03-22at113007.png)

* **Verwijderen**

  Hiermee verwijdert u de component van de pagina met uw bevestiging.

  ![Verwijderen](do-not-localize/screen_shot_2018-03-22at113012.png)

* **Component invoegen**

  Hiermee wordt het dialoogvenster geopend voor [een nieuwe component toevoegen](/help/sites-authoring/editing-content.md#inserting-a-component-from-the-paragraph-system).

  ![Component invoegen](do-not-localize/screen_shot_2018-03-22at113017.png)

* **Plakken**

  Hiermee wordt de component van het klembord naar de pagina geplakt. Of het origineel overblijft, hangt af van het feit of u de kopie of het knipsel hebt gebruikt.

   * U kunt op dezelfde pagina of op een andere pagina plakken.
   * Het geplakte item wordt boven het item geplakt waar u de plakactie selecteert.
   * De handeling Pate wordt alleen weergegeven als er inhoud op het klembord staat.

  ![screen_shot_2018-03-22at113553](assets/screen_shot_2018-03-22at113553.png)

  >[!NOTE]
  >
  >Als u plakt naar een andere pagina die al was geopend vóór de knip-/kopieerbewerking, moet u de pagina vernieuwen om de geplakte inhoud te zien.

* **Groep**

  Hierdoor kunt u meerdere componenten tegelijk selecteren. Hetzelfde kan worden bereikt op een desktopapparaat met een **Ctrl+klikken** of **Command+klikken**.

  ![Groep](do-not-localize/screen_shot_2018-03-22at113240.png)

* **Bovenliggend**

  Hiermee kunt u de bovenliggende component van de geselecteerde component selecteren.

  ![screen_shot_2018-03-22at113028](assets/screen_shot_2018-03-22at113028.png)

* **Layout**

  Hierdoor kunt u de [layout](/help/sites-authoring/editing-content.md#edit-component-layout) van de geselecteerde component. Dit geldt alleen voor de geselecteerde component en activeert de component [Lay-outmodus](/help/sites-authoring/author-environment-tools.md#page-modes) voor de gehele pagina.

  ![Layout](do-not-localize/screen_shot_2018-03-22at113044.png)

* **Omzetten in een ervaringsfragmentvariatie**

  Zo kunt u een nieuwe [ervaren, fragment](/help/sites-authoring/experience-fragments.md) van de geselecteerde component of voeg het aan een bestaand ervaringsfragment toe.

  ![Omzetten in ervaringsfragmentvariatie](do-not-localize/screen_shot_2018-03-22at113033.png)

## Bewerken (inhoud) {#edit-content}

Er zijn twee methoden om inhoud toe te voegen en/of te bewerken in componenten:

* Open de [dialoogvenster voor bewerking](#component-edit-dialog).
* [Middelen slepen en neerzetten](#draganddropintocomponent) vanuit de middelenbrowser om rechtstreeks inhoud toe te voegen.

### Dialoogvenster Component Edit {#component-edit-dialog}

U kunt een component openen om de content te bewerken met het pictogram [Bewerken (potlood) van de werkbalk van de component](#edit-configure-copy-cut-delete-paste).

De exacte bewerkingsopties zijn afhankelijk van de component. Voor sommige componenten [alle acties zijn alleen beschikbaar in de modus Volledig scherm](#edit-content-full-screen-mode). Bijvoorbeeld:

* [Tekstcomponent](/help/sites-authoring/rich-text-editor.md#main-pars-title-24)

  ![screen_shot_2018-03-22at120215](assets/screen_shot_2018-03-22at120215.png)

* Afbeeldingscomponent

  ![screen_shot_2018-03-22at120252](assets/screen_shot_2018-03-22at120252.png)

  >[!NOTE]
  >
  >Bewerken werkt niet op een lege afbeeldingscomponent.
  >
  >
  >U moet [een afbeelding slepen of uploaden (met Configureren)](/help/sites-authoring/default-components-foundation.md#image) voordat u kunt beginnen met bewerken.

* Afbeeldingscomponent - volledig scherm

  [Door de volledige-schermmodus te openen](/help/sites-authoring/editing-content.md#edit-content-full-screen-mode) voor de afbeeldingscomponent kunt u meer ruimte vrijmaken voor het bewerken van de afbeelding en kunt u extra bewerkingsopties weergeven, zoals **Kaart starten** en **Zoomen opnieuw instellen**. Bovendien kunt u op het volledige scherm voorinstellingen voor bijsnijden selecteren.

  ![screen_shot_2018-03-22at120529](assets/screen_shot_2018-03-22at120529.png)

* Onderdelen die zijn vervaardigd uit meer dan één basisonderdeel, zoals de [Component voor tekst- en afbeeldingsbasis](/help/sites-authoring/default-components-foundation.md#text-image)Vraag u eerst om te bevestigen welke set bewerkingsopties u wilt:

  ![chlimage_1-123](assets/chlimage_1-123.png)

### Elementen naar component slepen en neerzetten {#drag-and-drop-assets-into-component}

Voor specifieke componenttypen kunt u elementen van de elementenbrowser rechtstreeks naar de component slepen om de inhoud bij te werken:

| **Elementtype** | **Componenttype** |
|---|---|
| Afbeelding | Afbeelding |
| Document | Downloaden |
| Product | Product |
| Video | Flash |
| Inhoudsfragment | Inhoudsfragment |

## Modus Volledig scherm bewerken (inhoud) {#edit-content-full-screen-mode}

Voor alle componenten kunt u de modus Volledig scherm openen (en afsluiten):

![Modus Volledig scherm bewerken](do-not-localize/chlimage_1-20.png)

De **Tekst** component:

![screen_shot_2018-03-22at121616](assets/screen_shot_2018-03-22at121616.png)

>[!NOTE]
>
>Voor sommige componenten zijn er meer opties beschikbaar voor de modus Volledig scherm dan voor de standaard, op locatie verkrijgbare editor.

## Een component verplaatsen {#moving-a-component}

Een alineacomponent verplaatsen:

1. Selecteer de alinea die u wilt verplaatsen met Tik en houd de muisknop ingedrukt of klik en houd de muisknop ingedrukt.
1. Sleep de alinea naar de nieuwe locatie. AEM geeft aan waar de alinea kan worden gedeponeerd. Zet het neer op de gewenste plaats.

   ![screen_shot_2018-03-22at121821](assets/screen_shot_2018-03-22at121821.png)

1. Uw alinea wordt verplaatst.

>[!NOTE]
>
>U kunt ook [Knippen en plakken](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste) om een component te verplaatsen.

## Componentindeling bewerken {#edit-component-layout}

In plaats van herhaaldelijk over te schakelen van de bewerkingsmodus naar [de lay-outmodus](/help/sites-authoring/responsive-layout.md) om een component aan te passen, kunt u de actie **Lay-out** selecteren zodat een component de lay-out van die component kan wijzigen en tijd kan besparen door de bewerkingsmodus niet te verlaten.

1. Wanneer in **Bewerken** wijze van de plaatsenconsole, die een component selecteert openbaart de toolbar van de component.

   ![screen_shot_2018-03-22at133756](assets/screen_shot_2018-03-22at133756.png)

   Klik of tik op **Layout** actie om de lay-out van de component aan te passen.

   ![Component, werkbalk](do-not-localize/chlimage_1-21.png)

1. Nadat de handeling Lay-out is geselecteerd:

   * De formaatgrepen voor de componentweergave.
   * De emulatorwerkbalk wordt boven in het scherm weergegeven.
   * De acties van de lay-out in plaats van de standaard geeft acties uit tonen op de componententoolbar.

   ![screen_shot_2018-03-22at133843](assets/screen_shot_2018-03-22at133843.png)

   U kunt nu de lay-out van de component wijzigen zoals u zou doen binnen [lay-outmodus](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode).

1. Klik op de knop **Sluiten** in het actiemenu van de component om het wijzigen van de lay-out van de component op te houden. De werkbalk van de component keert terug naar de normale bewerkingsstatus.

   ![Sluiten](do-not-localize/screen_shot_2018-03-22at133920.png)

>[!NOTE]
>
>De actie Lay-out is beperkt in werkingsgebied tot de geselecteerde component. Als u bijvoorbeeld de lay-out van een component bewerkt en vervolgens op een andere component klikt, verdwijnt de werkbalk voor standaardbewerking (niet de layoutwerkbalk) voor de zojuist geselecteerde component en de formaatgrepen en de emulatorwerkbalk.
>
>Als u de algemene lay-out van de pagina moet bewerken, wat van invloed is op meerdere componenten, schakelt u over naar de [lay-outmodus](/help/sites-authoring/responsive-layout.md).

## Overgenomen componenten {#inherited-components}

Overerfde componenten kunnen het product van diverse scenario&#39;s zijn, die omvatten:

* [Beheer van meerdere sites](/help/sites-administering/msm.md)
* [Starten](/help/sites-authoring/launches.md) (indien gebaseerd op live kopie).
* Specifieke componenten, zoals het Overgenomen alineasysteem in Geometrixx.

U kunt de overerving annuleren (en vervolgens opnieuw inschakelen). Afhankelijk van de component, kan dit beschikbaar zijn bij:

* **Live kopie**

  De componentwerkbalk als de component zich op een pagina bevindt die deel uitmaakt van een live kopie of introductie (op basis van een live kopie). Bijvoorbeeld:

  ![screen_shot_2018-03-22at134339](assets/screen_shot_2018-03-22at134339.png)

  De optie Overerving annuleren is beschikbaar:

  ![Overerving annuleren](do-not-localize/screen_shot_2018-03-22at134406.png)

  Of herstel overname indien reeds geannuleerd:

  ![Herhaalbare overerving](do-not-localize/screen_shot_2018-03-22at134417.png)

  De actie Uitvoer is ook beschikbaar in de blauwdruk of Live Copy-bron:

  ![Uitrol](do-not-localize/screen_shot_2018-03-22at134516.png)

* **Een overerfd alineasysteem**

  Het configuratiedialoogvenster. Bijvoorbeeld, zoals met het Overgenomen Systeem van de Paragraaf:

  ![chlimage_1-124](assets/chlimage_1-124.png)

## De paginasjabloon bewerken {#editing-the-page-template}

Als de pagina is gebaseerd op een [bewerkbare sjabloon](/help/sites-authoring/templates.md#editable-and-static-templates)kunt u eenvoudig overschakelen op [sjablooneditor](/help/sites-authoring/templates.md#editing-templates-template-authors) door **Sjabloon bewerken** in de [Menu Paginagegevens](/help/sites-authoring/author-environment-tools.md#page-information).

Als de pagina is gebaseerd op een [statische sjabloon](/help/sites-authoring/templates.md#editable-and-static-templates)kunt u overschakelen op [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) met de [paginamodus selecteren](/help/sites-authoring/author-environment-tools.md#page-modes) op de werkbalk om componenten voor gebruik op de pagina in of uit te schakelen.

U kunt gemakkelijk zien op welke sjabloon de pagina is gebaseerd wanneer u de pagina selecteert in de [kolomweergave](/help/sites-authoring/basic-handling.md#column-view) of de [lijstweergave](/help/sites-authoring/basic-handling.md#list-view).

## Status van live kopiëren {#live-copy-status}

De [De paginamodus Actieve kopie](/help/sites-authoring/author-environment-tools.md#page-modes) Hiermee kunt u snel een overzicht geven van de status van de live kopie en van de onderdelen die u wel of niet wilt overnemen:

* Groene rand: Overgenomen
* Roze rand: Overerving is geannuleerd

Bijvoorbeeld:

![screen_shot_2018-03-22at134820](assets/screen_shot_2018-03-22at134820.png)

## Annotaties toevoegen {#adding-annotations}

[Annotaties](/help/sites-authoring/annotations.md) revisoren en andere auteurs feedback geven over uw inhoud. Ze worden vaak gebruikt voor controle- en validatiedoeleinden.

## Pagina&#39;s voorvertonen {#previewing-pages}

Er zijn twee opties voor het voorvertonen van een pagina:

* [Voorvertoningsmodus](#preview-mode) - een snelle voorvertoning op locatie

* [Weergeven als gepubliceerd](#view-as-published) - een volledige voorvertoning waarmee de pagina in een nieuw tabblad wordt geopend

>[!NOTE]
>
>* Koppelingen in de inhoud zijn zichtbaar, maar niet toegankelijk in de bewerkingsmodus.
>* Gebruik een van de voorvertoningsopties als u door de koppelingen wilt navigeren.
>* Gebruik de [sneltoets](/help/sites-authoring/keyboard-shortcuts.md) `Ctrl-Shift-M` om te schakelen tussen de voorvertoning en de laatst geselecteerde modus.
>

>[!NOTE]
>
>Het WCM-moduscookie wordt ingesteld voor beide opties.

### Voorvertoningsmodus {#preview-mode}

Wanneer u inhoud bewerkt, kunt u een voorvertoning van de pagina weergeven met behulp van de voorvertoning [mode](/help/sites-authoring/author-environment-tools.md#page-modes). Deze modus:

* Hiermee verbergt u verschillende bewerkingsmechanismen waarmee u snel kunt zien hoe de pagina er bij het publiceren uitziet.
* Hiermee kunt u navigeren met koppelingen.
* doet **niet** Vernieuw de pagina-inhoud.

Tijdens het ontwerpen is de voorvertoningsmodus beschikbaar met het pictogram rechtsboven in de pagina-editor:

![chlimage_1-125](assets/chlimage_1-125.png)

### Weergeven als gepubliceerd {#view-as-published}

De **Weergeven als gepubliceerd** Deze optie is beschikbaar via de [Pagina-informatie](/help/sites-authoring/author-environment-tools.md#page-information) -menu. Hierdoor wordt de pagina op een nieuw tabblad geopend, wordt de inhoud vernieuwd en wordt de pagina precies zo weergegeven als in de publicatieomgeving.

## Een pagina vergrendelen {#locking-a-page}

AEM kunt u een pagina vergrendelen, zodat niemand anders de inhoud kan wijzigen. Dit is handig wanneer u veel bewerkingen uitvoert op een bepaalde pagina of wanneer u een pagina even wilt stilzetten.

Een pagina kan worden vergrendeld vanuit:

* **Sites** console

   1. Selecteer de pagina met [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
   1. Selecteer het vergrendelingspictogram.

  ![screen_shot_2018-03-22at134928](assets/screen_shot_2018-03-22at134928.png)

* **Pagina-editor**

   1. Selecteer **Pagina-informatie** om het menu te openen.
   1. Selecteer **Pagina vergrendelen** optie.

Nadat de weergave op de console is vergrendeld, wordt de informatie bijgewerkt en wanneer u een vergrendelingssymbool bewerkt, wordt deze weergegeven op de werkbalk.

![screen_shot_2018-03-22at135010](assets/screen_shot_2018-03-22at135010.png)

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer [gebruiker beleven](/help/sites-administering/security.md#impersonating-another-user). Een pagina die op deze manier is vergrendeld, kan echter alleen dan worden ontgrendeld door de gebruiker die zich heeft laten verpersoonlijken of door de beheerder.
>
>De pagina&#39;s kunnen niet worden ontgrendeld door zich als de gebruiker voor te doen die de pagina heeft vergrendeld.

## Een pagina ontgrendelen {#unlocking-a-page}

Het ontgrendelen van een pagina lijkt veel op [de pagina vergrendelen](#locking-a-page). Nadat de pagina is vergrendeld, worden de vergrendelingsopties vervangen door ontgrendelingsacties.

In het menu Pagina-informatie wordt **Ontgrendelen** als optie weergegeven en het pictogram Vergrendelen in de Sites-console wordt vervangen door een pictogram **Ontgrendelen**.

![screen_shot_2018-03-22at134942](assets/screen_shot_2018-03-22at134942.png)

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer [gebruiker beleven](/help/sites-administering/security.md#impersonating-another-user). Een pagina die op deze manier is vergrendeld, kan echter alleen dan worden ontgrendeld door de gebruiker die zich heeft laten verpersoonlijken of door de beheerder.
>
>De pagina&#39;s kunnen niet worden ontgrendeld door zich als de gebruiker voor te doen die de pagina heeft vergrendeld.

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren {#undoing-and-redoing-page-edits}

Met de volgende pictogrammen kunt u een handeling ongedaan maken of opnieuw uitvoeren. Deze worden in voorkomend geval weergegeven op de werkbalk:

![Ongedaan maken en Opnieuw](do-not-localize/screen_shot_2018-03-23at093614.png)

>[!NOTE]
>
>De [sneltoets](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) `Ctrl-Z` is ook beschikbaar voor het ongedaan maken van paginabewerkingsacties.
>
>De sneltoets `Ctrl-Y` is ook beschikbaar om paginabewerkingsacties opnieuw uit te voeren.

>[!NOTE]
>
>Zie [Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie](#undoing-and-redoing-page-edits-the-theory) voor de volledige details van wat mogelijk is wanneer het ongedaan maken van en het opnieuw doen van paginaedetingen.

## Paginabewerkingen ongedaan maken en opnieuw uitvoeren - De theorie {#undoing-and-redoing-page-edits-the-theory}

>[!NOTE]
>
>Uw systeembeheerder kan [Verschillende aspecten van de functies Ongedaan maken/Opnieuw configureren](/help/sites-administering/config-undo.md) volgens de vereisten voor uw exemplaar.

AEM slaat een geschiedenis van acties op die u uitvoert en de opeenvolging waarin u hen uitvoerde zodat u veelvoudige acties in de orde ongedaan kunt maken dat u hen uitvoerde evenals hen opnieuw doet om één of meerdere acties indien nodig opnieuw toe te passen.

Als een element op de inhoudspagina wordt geselecteerd (zoals een tekstcomponent), dan is het ongedaan maken en opnieuw bevel op het geselecteerde punt van toepassing.

Het gedrag van de opdrachten Ongedaan maken en Opnieuw is vergelijkbaar met dat van andere softwareprogramma&#39;s. Gebruik de opdrachten om de recente status van uw webpagina te herstellen terwijl u beslissingen neemt over de inhoud. Als u bijvoorbeeld een tekstalinea naar een andere locatie op de pagina verplaatst, kunt u de opdracht Ongedaan maken gebruiken om de alinea terug te verplaatsen. Als u vervolgens besluit dat de vorige positie beter was, gebruikt u de opdracht Opnieuw uitvoeren om de bewerking Ongedaan maken ongedaan te maken.

>[!NOTE]
>
>U kunt:
>
>* Voer handelingen opnieuw uit zolang u geen paginabewerking hebt uitgevoerd nadat u Ongedaan maken hebt gebruikt.
>* U kunt maximaal 20 bewerkingen ongedaan maken (standaardinstelling).
>* Ook gebruiken [Sneltoetsen](/help/sites-authoring/page-authoring-keyboard-shortcuts.md) voor ongedaan maken en opnieuw uitvoeren.
>

U kunt de volgende typen paginawijzigingen ongedaan maken en opnieuw uitvoeren:

* Alinea&#39;s toevoegen, bewerken, verwijderen en verplaatsen
* Lokaal bewerken van alinea-inhoud
* Items op een pagina kopiëren, knippen en plakken

Formuliervelden die door formuliercomponenten worden gerenderd, mogen geen waarden hebben die zijn opgegeven tijdens het ontwerpen van pagina&#39;s. De opdrachten Ongedaan maken en Opnieuw hebben daarom geen invloed op wijzigingen die u aanbrengt in de waarden van die typen componenten. U kunt bijvoorbeeld het selecteren van een waarde in een vervolgkeuzelijst niet ongedaan maken.

>[!NOTE]
>
>Er zijn speciale machtigingen vereist voor het ongedaan maken en opnieuw uitvoeren van wijzigingen in bestanden en afbeeldingen.

>[!NOTE]
>
>De geschiedenis van wijzigingen in bestanden en afbeeldingen duurt minimaal tien uur. Na deze tijd is het ongedaan maken van de wijzigingen echter niet gegarandeerd. De beheerder kan de standaardtijd van tien uur wijzigen.
