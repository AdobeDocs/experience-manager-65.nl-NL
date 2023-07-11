---
title: "Zelfstudie: Sjablonen maken"
seo-title: Create Print and Web templates for Interactive Communication
description: Afdruk- en websjablonen maken voor interactieve communicatie
seo-description: Create Print and Web templates for Interactive Communication
uuid: 22256a61-bcf6-4b02-9ee6-0ffb1cc20a6e
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 879ff6ca-e5f3-451d-acc2-f75142101ddd
docset: aem65
feature: Interactive Communication
exl-id: bef1f05e-aea2-433e-b3d5-0b7ad8163fa7
source-git-commit: e9f64722ba7df0a7f43aaf1005161483e04142f5
workflow-type: tm+mt
source-wordcount: '1793'
ht-degree: 0%

---

# Zelfstudie: Sjablonen maken{#tutorial-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Deze zelfstudie is een stap in de [Maak uw eerste interactieve communicatie](/help/forms/using/create-your-first-interactive-communication.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Om een Interactieve Mededeling tot stand te brengen, moet u malplaatjes beschikbaar op de AEM server voor de Kanalen van de Druk en van het Web hebben.

De sjablonen voor het kanaal Afdrukken worden gemaakt in Adobe Forms Designer en geüpload naar de AEM server. Deze malplaatjes zijn dan beschikbaar voor gebruik terwijl het creëren van een Interactieve Mededeling.

De malplaatjes voor het kanaal van het Web worden gecreeerd in AEM. Sjabloonauteurs en -beheerders kunnen websjablonen maken, bewerken en inschakelen. Zodra gecreeerd en toegelaten, zijn deze malplaatjes beschikbaar voor gebruik terwijl het creëren van een Interactieve Communicatie.

Dit leerprogramma begeleidt u door de stappen om malplaatjes voor de kanalen van de Druk en van het Web tot stand te brengen zodat zij voor gebruik terwijl het creëren van Interactieve Mededelingen beschikbaar zijn. Aan het einde van deze zelfstudie kunt u het volgende doen:

* XDP-sjablonen maken voor het afdrukkanaal met Adobe Forms Designer
* De XDP-sjablonen uploaden naar de AEM Forms-server
* Sjablonen voor het webkanaal maken en inschakelen

## Sjabloon maken voor afdrukkanaal {#create-template-for-print-channel}

Creeer en beheer malplaatje voor het kanaal van de Druk van Interactieve Communicatie gebruikend de volgende taken:

* [XDP-sjabloon maken met Forms Designer](../../forms/using/create-templates-print-web.md#create-xdp-template-using-forms-designer)
* [XDP-sjabloon uploaden naar de AEM Forms-server](../../forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server)
* [XDP-sjabloon maken voor layoutfragmenten](../../forms/using/create-templates-print-web.md#create-xdp-template-for-layout-fragments)

### XDP-sjabloon maken met Forms Designer {#create-xdp-template-using-forms-designer}

Op basis van de [use case](/help/forms/using/create-your-first-interactive-communication.md) en [anatomie](/help/forms/using/planning-interactive-communications.md), maakt u de volgende subformulieren in de XDP-sjabloon:

* Bill Details: Bevat een documentfragment
* Klantgegevens: Bevat een documentfragment
* Bill Summary: Bevat een documentfragment
* Overzicht: Bevat een documentfragment (subformulier Laden) en een diagram (subformulier Teksten)
* Gespecialiseerde Vraag: Bevat een tabel (layoutfragment)
* Nu betalen: Bevat een afbeelding
* Services voor toegevoegde waarde: Bevat een afbeelding

![create_print_template](assets/create_print_template.gif)

Deze subformulieren worden weergegeven als doelgebieden in de afdruksjabloon nadat het XDP-bestand naar de Forms-server is geüpload. Alle entiteiten zoals documentfragmenten, grafieken, lay-outfragmenten en afbeeldingen worden aan doelgebieden toegevoegd tijdens het maken van de interactieve communicatie.

Voer de volgende stappen uit om een XDP malplaatje voor het kanaal van de Druk tot stand te brengen:

1. Open Forms Designer en selecteer **Bestand** > **Nieuw** > **Een leeg formulier gebruiken** tikken **Volgende** en tikt u vervolgens op **Voltooien** om het formulier te openen voor het maken van een sjabloon.

   Zorg ervoor dat de **Objectbibliotheek** en **Object** opties worden geselecteerd in het menu **Venster** -menu.

1. Sleep de **Subformulier** uit de **Objectbibliotheek** op het formulier.
1. Selecteer het subformulier om de opties voor het subformulier weer te geven in het dialoogvenster **Object** in het rechterdeelvenster.
1. Selecteer **Subformulier** en selecteert u **Overlopen** van de **Inhoud** vervolgkeuzelijst. Sleep het linkereindpunt van het subformulier om de lengte aan te passen.
1. In de **Bindingen** tab:

   1. Opgeven **BillDetails** in de **Naam** veld.

   1. Selecteren **Geen gegevensbinding** van de **Gegevensbinding** vervolgkeuzelijst.

   ![Designer-subformulier](assets/forms_designer_subform_new.png)

1. Selecteer op dezelfde manier het basissubformulier en selecteer de optie **Subformulier** en selecteert u **Overlopen** van de **Inhoud** vervolgkeuzelijst. In de **Bindingen** tab:

   1. Opgeven **TelecaBill** in de **Naam** veld.

   1. Selecteren **Geen gegevensbinding** van de **Gegevensbinding** vervolgkeuzelijst.

   ![Subformulier voor afdruksjabloon](assets/root_subform_print_template_new.png)

1. Herhaal stap 2 tot en met 5 om de volgende subformulieren te maken:

   * BillDetails
   * CustomerDetails
   * BillSummary
   * Samenvatting - selecteer **Subformulier** en selecteert u **Geplaatst** van de **Inhoud** vervolgkeuzelijst voor dit subformulier. De volgende subformulieren invoegen in het dialoogvenster **Samenvatting** subformulier.

      * Heffingen
      * Grafieken

   * ItemCalls
   * Nu betalen
   * ValueAddedServices

   Als u tijd wilt besparen, kunt u ook bestaande subformulieren kopiëren en plakken om nieuwe subformulieren te maken.

   Als u de opdracht **Grafieken** subformulier rechts van het subformulier Heffingen, selecteert u het subformulier **Grafieken** subformulier in het linkerdeelvenster selecteert u de optie **Layout** en geeft een waarde op voor **AnkerX** veld. De waarde moet groter zijn dan de waarde voor de **Breedte** veld voor de **Heffingen** subformulier. Selecteer **Heffingen** subformulier en selecteer de **Layout** om de waarde van de optie **Breedte** veld.

1. Sleep de **Tekst** van het object **Objectbibliotheek** op het formulier en voer de **Bel XXXX voor abonnement** tekst in het vak.
1. Klik met de rechtermuisknop op het tekstobject in het linkerdeelvenster en selecteer **Naam object wijzigen** en voert u de naam van het tekstobject in als **Abonneren**.

   ![XDP-sjabloon](assets/print_xdp_template_subform_new.png)

1. Selecteren **Bestand** > **Opslaan als** om het bestand op te slaan op het lokale bestandssysteem:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef de naam op als **create_first_ic_print_template**.
   1. Selecteren **.xdp** van de **Opslaan als type** vervolgkeuzelijst.

   1. Tikken **Opslaan**.

### XDP-sjabloon uploaden naar de AEM Forms-server {#upload-xdp-template-to-the-aem-forms-server}

Nadat u een XDP-sjabloon hebt gemaakt met de Forms Designer, moet u de sjabloon uploaden naar de AEM Forms-server, zodat de sjabloon beschikbaar is voor gebruik tijdens het maken van de interactieve communicatie.

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tikken **Maken** > **Bestand uploaden**.

   Navigeer en selecteer de **create_first_ic_print_template** sjabloon (XDP) en tik **Openen** om de XDP-sjabloon te importeren naar de AEM Forms-server.

### XDP-sjabloon maken voor layoutfragmenten {#create-xdp-template-for-layout-fragments}

Als u een lay-outfragment wilt maken voor het afdrukkanaal van de interactieve communicatie, maakt u een XDP met Forms Designer en uploadt u deze naar de AEM Forms-server.

1. Open Forms Designer en selecteer **Bestand** > **Nieuw** > **Een leeg formulier gebruiken** tikken **Volgende** en tikt u vervolgens op **Voltooien** om het formulier te openen voor het maken van een sjabloon.

   Zorg ervoor dat de **Objectbibliotheek** en **Object** opties worden geselecteerd in het menu **Venster** -menu.

1. Sleep de **Tabel** uit de **Objectbibliotheek** op het formulier.
1. In het dialoogvenster Tabel invoegen:

   1. Geef het aantal kolommen op als **5**.
   1. Het aantal tekstrijen opgeven als **1**.
   1. Selecteer **Koptekstrij in tabel opnemen** selectievakje.
   1. Tab **OK**.

1. Tikken **+** in het linkerdeelvenster naast **Tabel** 1 en klik met de rechtermuisknop **Cel1** en selecteert u **Naam object wijzigen** tot **Datum**.

   Naam wijzigen **Cel2**, **Cel3**, **Cel4**, en **Cel5** tot **Tijd**, **Getal**, **Duur**, en **Heffingen** respectievelijk.

1. Klik op de tekstvelden Koptekst in het dialoogvenster **Designer-weergave** en hernoemen **Tijd**, **Getal**, **Duur**, en **Heffingen**.

   ![Lay-outfragment](assets/layout_fragment_print_new.png)

1. Selecteren **Rij 1** in het linkerdeelvenster en selecteer **Object** > **Binding** > **Rij herhalen voor elk gegevensitem**.

   ![Eigenschappen voor layoutfragment herhalen](assets/layout_fragment_print_repeat_new.png)

1. Sleep de **Tekstveld** uit de **Objectbibliotheek** aan de **Designer-weergave**.

   ![Tekstveld voor layoutfragment](assets/layout_fragment_print_text_field_new.png)

   Op dezelfde manier slepen en neerzetten **Tekstveld** aan de **Tijd**, **Getal**, **Duur**, en **Heffingen** rijen.

1. Selecteren **Bestand** > **Opslaan als** om het bestand op te slaan op het lokale bestandssysteem:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef de naam op als **table_lf**.
   1. Selecteren **.xdp** van de **Opslaan als type** vervolgkeuzelijst.

   1. Tikken **Opslaan**.

   Nadat u een XDP-sjabloon voor een lay-outfragment hebt gemaakt met de Forms Designer, moet u [uploaden](../../forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server) wordt naar de AEM Forms-server gestuurd, zodat de sjabloon beschikbaar is voor gebruik tijdens het maken van lay-outfragmenten.

## Sjabloon maken voor webkanaal {#create-template-for-web-channel}

Creeer en beheer malplaatje voor het kanaal van het Web van Interactieve Communicatie gebruikend de volgende taken:

* [Map maken voor sjablonen](../../forms/using/create-templates-print-web.md#create-folder-for-templates)
* [De sjabloon maken](../../forms/using/create-templates-print-web.md#create-the-template)
* [De sjabloon inschakelen](../../forms/using/create-templates-print-web.md#enable-the-template)
* [Knoppen inschakelen in Interactieve communicatie](../../forms/using/create-templates-print-web.md#enabling-buttons-in-interactive-communications)

### Map maken voor sjablonen {#create-folder-for-templates}

Als u een webkanaalsjabloon wilt maken, definieert u een map waarin u de gemaakte sjablonen kunt opslaan. Zodra u een malplaatje binnen die omslag creeert, laat het malplaatje toe om de vormengebruikers toe te staan om het kanaal van het Web van een Interactieve Communicatie tot stand te brengen die op het malplaatje wordt gebaseerd.

Voer de volgende stappen uit om een map voor de bewerkbare sjablonen te maken:

1. Tikken **Gereedschappen** ![hamerpictogram](assets/hammer-icon.svg) > **Configuratiebrowser**.
   * Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Tik op de pagina Configuration Browser (Configuratiebrowser) op **Maken**.
1. In de **Configuratie maken** dialoogvenster, opgeven **Create_First_IC_templates** als de titel voor de map, controleert u **Bewerkbare sjablonen** en tikken **Maken**.

   ![Websjablonen configureren](assets/create_first_ic_web_template_new.png)

   De **Create_First_IC_templates** map wordt gemaakt en wordt vermeld op het tabblad **Configuratiebrowser** pagina.

### De sjabloon maken {#create-the-template}

Op basis van de [use case](/help/forms/using/create-your-first-interactive-communication.md) en [anatomie](/help/forms/using/planning-interactive-communications.md)maakt u de volgende deelvensters in de websjabloon:

* Bill Details: Bevat een documentfragment
* Klantgegevens: Bevat een documentfragment
* Bill Summary: Bevat een documentfragment
* Overzicht van kosten: Bevat een documentfragment en een diagram (lay-out met twee kolommen)
* Gespecialiseerde Vraag: Bevat een tabel
* Nu betalen: Bevat een **Nu betalen** en een afbeelding
* Services voor toegevoegde waarde: Bevat een afbeelding en een **Abonneren** knop.

![create_web_template](assets/create_web_template.gif)

Alle entiteiten zoals documentfragmenten, grafieken, tabellen, afbeeldingen en knoppen worden toegevoegd tijdens het maken van de interactieve communicatie.

Voer de volgende stappen uit om een malplaatje voor het kanaal van het Web in te creëren **Create_First_IC_templates** map:

1. Navigeer naar de juiste sjabloonmap door **Gereedschappen** > **Sjablonen** > **Create_First_IC_templates** map.
1. Tikken **Maken**.
1. Op de **Sjabloontype kiezen** configuratiewizard, selecteren **Interactieve communicatie - Webkanaal** en tikken **Volgende**.
1. Op de **Sjabloondetails** configuratietovenaar, specificeer **Create_First_IC_Web_Template** als de sjabloontitel. Geef een optionele beschrijving op en tik op **Maken**.

   Een bevestigingsbericht dat **Create_First_IC_Web_Template** wordt weergegeven.

1. Tikken **Openen** om de sjabloon te openen in de sjablooneditor.
1. Selecteren **Oorspronkelijke inhoud** in de vervolgkeuzelijst naast de **Voorvertoning** optie.

   ![Sjablooneditor](assets/template_editor_initial_content_new.png)

1. Tikken **Hoofddeelvenster** en tik vervolgens op **+** om de lijst met componenten weer te geven die u aan de sjabloon kunt toevoegen.
1. Selecteren **Deelvenster** in de lijst om een deelvenster toe te voegen boven de **Hoofddeelvenster**.
1. Selecteer **Inhoud** in het linkerdeelvenster. Het nieuwe deelvenster dat u in stap 8 hebt toegevoegd, wordt weergegeven onder de **Hoofddeelvenster** in de inhoudsstructuur.

   ![Inhoudsstructuur](assets/content_tree_root_panel_new.png)

1. Selecteer het deelvenster en tik op ![configure_icon](assets/configure_icon.png) (Configureren).
1. In het deelvenster Eigenschappen:

   1. Opgeven **factureringsgegevens** in het veld Naam.
   1. Opgeven **Bill Details** in het veld Titel.
   1. Selecteren **1** van de **Aantal kolommen** vervolgkeuzelijst.

   1. Tikken ![Opslaan](/help/forms/using/assets/done_icon.png) om de eigenschappen op te slaan.

   De naam van het deelvenster wordt bijgewerkt naar **Bill Details** in de inhoudsstructuur.

1. Herhaal stap 7 - 11 om deelvensters met de volgende eigenschappen toe te voegen aan de sjabloon:

   | Naam | Titel | Aantal kolommen |
   |---|---|---|
   | klantgegevens | Klantgegevens | 1 |
   | billsummary | Bill Summary | 1 |
   | samenvattingskosten | Overzicht van heffingen | 2 |
   | gespecificeerde vraag | Gespecificeerde Vraag | 1 |
   | uitbetaling | Nu betalen | 2 |
   | vas | Services voor toegevoegde waarde | 1 |

   In de volgende afbeelding wordt de inhoudsstructuur weergegeven nadat alle deelvensters aan de sjabloon zijn toegevoegd:

   ![Inhoudsstructuur voor alle deelvensters](assets/content_tree_all_panels_new.png)

### De sjabloon inschakelen {#enable-the-template}

Zodra u het malplaatje van het Web hebt gecreeerd, moet u het toelaten om het malplaatje te gebruiken terwijl het creëren van de Interactieve Communicatie.

Voer de volgende stappen uit om het malplaatje van het Web toe te laten:

1. Tikken **Gereedschappen** ![hamerpictogram](assets/hammer-icon.svg) > **Sjablonen**.
1. Ga naar de **Create_First_IC_Web_Template** sjabloon, selecteert u deze en tikt u op **Inschakelen**.
1. Tab **Inschakelen** nogmaals ter bevestiging.

   Het malplaatje wordt toegelaten en zijn status wordt getoond zoals Toegelaten. U kunt dit malplaatje gebruiken terwijl het creëren van Interactieve Communicatie voor het kanaal van het Web.

### Knoppen inschakelen in Interactieve communicatie {#enabling-buttons-in-interactive-communications}

Op basis van het gebruiksgeval moet u de optie **Nu betalen** en **Abonneren** knoppen (adaptieve formuliercomponenten) in Interactieve communicatie. Voer de volgende stappen uit om het gebruik van deze knoppen in de interactieve communicatie mogelijk te maken:

1. Selecteren **Structuur** in de vervolgkeuzelijst naast de **Voorvertoning** optie.
1. Selecteer **Documentcontainer** hoofddeelvenster gebruiken met de inhoudsstructuur en tikken **Beleid** om de componenten te selecteren die voor gebruik in Interactieve Mededeling worden toegestaan.

   ![Beleid configureren](assets/structure_configure_policy_new.png)

1. In de **Toegestane componenten** tabblad van **Eigenschappen** sectie, selecteert u **Knop** van de **Adaptief formulier** componenten.

   ![Toegestane componenten](assets/allowed_components_af_new.png)

1. Tikken ![opslaan](assets/done_icon.png) om de eigenschappen op te slaan.
