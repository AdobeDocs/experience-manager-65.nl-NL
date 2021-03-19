---
title: '"Zelfstudie: Sjablonen maken"'
seo-title: Afdruk- en websjablonen maken voor interactieve communicatie
description: Afdruk- en websjablonen maken voor interactieve communicatie
seo-description: Afdruk- en websjablonen maken voor interactieve communicatie
uuid: 22256a61-bcf6-4b02-9ee6-0ffb1cc20a6e
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 879ff6ca-e5f3-451d-acc2-f75142101ddd
docset: aem65
feature: Interactieve communicatie
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 0%

---


# Zelfstudie: Sjablonen maken{#tutorial-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Deze zelfstudie is een stap in de serie [Maak uw eerste interactieve communicatiemodellen](/help/forms/using/create-your-first-interactive-communication.md). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

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

Op basis van de [use case](/help/forms/using/create-your-first-interactive-communication.md) en [anatomy](/help/forms/using/planning-interactive-communications.md) maakt u de volgende subformulieren in de XDP-sjabloon:

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

1. Open Forms Designer, selecteer **Bestand** > **Nieuw** > **Een leeg formulier gebruiken,** tikken **Volgende** en tik vervolgens op **Voltooien** om het formulier te openen voor het maken van een sjabloon.

   Zorg ervoor dat de opties **Objectbibliotheek** en **Object** zijn geselecteerd in het menu **Venster**.

1. Sleep de **Subform** component van **Objectbibliotheek** naar het formulier.
1. Selecteer het subformulier om de opties voor het subformulier weer te geven in het venster **Object** in het rechterdeelvenster.
1. Selecteer het tabblad **Subformulier** en selecteer **Overlopen** in de vervolgkeuzelijst **Inhoud**. Sleep het linkereindpunt van het subformulier om de lengte aan te passen.
1. Op het tabblad **Bindingen**:

   1. Geef **BillDetails** op in het veld **Naam**.

   1. Selecteer **Geen gegevensbinding** in de vervolgkeuzelijst **Gegevensbinding**.

   ![Designer-subformulier](assets/forms_designer_subform_new.png)

1. Selecteer op dezelfde manier het basissubformulier, selecteer het tabblad **Subformulier** en selecteer **Overlopen** in de vervolgkeuzelijst **Inhoud**. Op het tabblad **Bindingen**:

   1. Geef **TelecaBill** op in het veld **Naam**.

   1. Selecteer **Geen gegevensbinding** in de vervolgkeuzelijst **Gegevensbinding**.

   ![Subformulier voor afdruksjabloon](assets/root_subform_print_template_new.png)

1. Herhaal stap 2 tot en met 5 om de volgende subformulieren te maken:

   * BillDetails
   * CustomerDetails
   * BillSummary
   * Samenvatting - selecteer het **tabblad Subformulier** en selecteer **Geplaatst** in de vervolgkeuzelijst **Inhoud** voor dit subformulier. Voeg de volgende subformulieren in het subformulier **Summary** in.

      * Heffingen
      * Grafieken
   * ItemCalls
   * Nu betalen
   * ValueAddedServices

   Als u tijd wilt besparen, kunt u ook bestaande subformulieren kopiëren en plakken om nieuwe subformulieren te maken.

   Als u het subformulier **Tekens** rechts van het subformulier Laden wilt verplaatsen, selecteert u het subformulier **Tekens** in het linkerdeelvenster, selecteert u het tabblad **Lay-out** en geeft u een waarde op voor het veld **AnkerX**. De waarde moet groter zijn dan de waarde voor het veld **Breedte** voor het subformulier **Laden**. Selecteer het subformulier **Laden** en selecteer het tabblad **Lay-out** om de waarde van het veld **Breedte** weer te geven.

1. Sleep en zet het **Text**-object van **Objectbibliotheek** naar het formulier en voer de **Dial XXXX in om een abonnement te nemen**-tekst in het vak.
1. Klik met de rechtermuisknop op het tekstobject in het linkerdeelvenster, selecteer **Naam van object wijzigen** en voer de naam van het tekstobject in als **Abonneren**.

   ![XDP-sjabloon](assets/print_xdp_template_subform_new.png)

1. Selecteer **Bestand** > **Opslaan als** om het bestand op te slaan op het lokale bestandssysteem:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef de naam op als **create_first_ic_print_template**.
   1. Selecteer **.xdp** in de vervolgkeuzelijst **Opslaan als type**.

   1. Tik **Opslaan**.

### XDP-sjabloon uploaden naar de AEM Forms-server {#upload-xdp-template-to-the-aem-forms-server}

Nadat u een XDP-sjabloon hebt gemaakt met de Forms Designer, moet u de sjabloon uploaden naar de AEM Forms-server, zodat de sjabloon beschikbaar is voor gebruik tijdens het maken van de interactieve communicatie.

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tik **Maken** > **Bestand uploaden**.

   Navigeer en selecteer **create_first_ic_print_template** sjabloon (XDP) en tik **Open** om de XDP sjabloon naar de AEM Forms server te importeren.

### XDP-sjabloon maken voor layoutfragmenten {#create-xdp-template-for-layout-fragments}

Als u een lay-outfragment wilt maken voor het afdrukkanaal van de interactieve communicatie, maakt u een XDP met Forms Designer en uploadt u deze naar de AEM Forms-server.

1. Open Forms Designer, selecteer **Bestand** > **Nieuw** > **Een leeg formulier gebruiken,** tikken **Volgende** en tik vervolgens op **Voltooien** om het formulier te openen voor het maken van een sjabloon.

   Zorg ervoor dat de opties **Objectbibliotheek** en **Object** zijn geselecteerd in het menu **Venster**.

1. Sleep de **Table** component van **Objectbibliotheek** naar het formulier.
1. In het dialoogvenster Tabel invoegen:

   1. Geef het aantal kolommen op als **5**.
   1. Geef het aantal tekstrijen op als **1**.
   1. Selecteer het selectievakje **Koptekstrij in tabel opnemen**.
   1. Tab **OK**.

1. Tik **+** in het linkerdeelvenster naast **Tabel** 1 en klik met de rechtermuisknop **Cell1** en selecteer **Naam van object wijzigen** in **Datum**.

   Wijzig op dezelfde manier **Cell2**, **Cell3**, **Cell4** en **Cell5** in **Time**, **Number**, **Duration a 13/> en** Laden **respectievelijk.**

1. Klik op de tekstvelden Koptekst in de **Designer-weergave** en wijzig de naam ervan in **Time**, **Number**, **Duur** en **Laden**.

   ![Lay-outfragment](assets/layout_fragment_print_new.png)

1. Selecteer **Rij 1** in het linkerdeelvenster en selecteer **Object** > **Binding** > **Rij herhalen voor elk gegevensitem**.

   ![Eigenschappen voor layoutfragment herhalen](assets/layout_fragment_print_repeat_new.png)

1. Sleep de **Tekstveld** component van **Objectbibliotheek** naar **Ontwerpweergave**.

   ![Tekstveld voor layoutfragment](assets/layout_fragment_print_text_field_new.png)

   Op dezelfde manier slepen en neerzetten **Tekstveld** component aan **Tijd**, **Aantal**, **Duur**, en **Lagen** rijen.

1. Selecteer **Bestand** > **Opslaan als** om het bestand op te slaan op het lokale bestandssysteem:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef de naam op als **table_lf**.
   1. Selecteer **.xdp** in de vervolgkeuzelijst **Opslaan als type**.

   1. Tik **Opslaan**.
   Nadat u een XDP-sjabloon voor een lay-outfragment hebt gemaakt met de Forms Designer, moet u de sjabloon [uploaden](../../forms/using/create-templates-print-web.md#upload-xdp-template-to-the-aem-forms-server) naar de AEM Forms-server, zodat de sjabloon beschikbaar is voor gebruik tijdens het maken van lay-outfragmenten.

## Sjabloon maken voor webkanaal {#create-template-for-web-channel}

Creeer en beheer malplaatje voor het kanaal van het Web van Interactieve Communicatie gebruikend de volgende taken:

* [Map maken voor sjablonen](../../forms/using/create-templates-print-web.md#create-folder-for-templates)
* [De sjabloon maken](../../forms/using/create-templates-print-web.md#create-the-template)
* [De sjabloon inschakelen](../../forms/using/create-templates-print-web.md#enable-the-template)
* [Knoppen inschakelen in Interactieve communicatie](../../forms/using/create-templates-print-web.md#enabling-buttons-in-interactive-communications)

### Map maken voor sjablonen {#create-folder-for-templates}

Als u een webkanaalsjabloon wilt maken, definieert u een map waarin u de gemaakte sjablonen kunt opslaan. Zodra u een malplaatje binnen die omslag creeert, laat het malplaatje toe om de vormengebruikers toe te staan om het kanaal van het Web van een Interactieve Communicatie tot stand te brengen die op het malplaatje wordt gebaseerd.

Voer de volgende stappen uit om een map voor de bewerkbare sjablonen te maken:

1. Tik **Gereedschappen** ![hamerpictogram](assets/hammer-icon.svg) > **Configuratiebrowser**.
   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Tik op **Create** in de pagina Configuration Browser.
1. Geef in het dialoogvenster **Configuratie maken** **Eerste_IC_templates** op als titel voor de map, schakel **Bewerkbare sjablonen** in en tik **Maken**.

   ![Websjablonen configureren](assets/create_first_ic_web_template_new.png)

   De map **Create_First_IC_templates** wordt gemaakt en vermeld op de pagina **Configuration Browser**.

### De sjabloon {#create-the-template} maken

Gebaseerd op [use case](/help/forms/using/create-your-first-interactive-communication.md) en [anatomy](/help/forms/using/planning-interactive-communications.md), creeer de volgende panelen in het malplaatje van het Web:

* Bill Details: Bevat een documentfragment
* Klantgegevens: Bevat een documentfragment
* Bill Summary: Bevat een documentfragment
* Overzicht van kosten: Bevat een documentfragment en een diagram (lay-out met twee kolommen)
* Gespecialiseerde Vraag: Bevat een tabel
* Nu betalen: Bevat een **Nu betalen**-knop en een afbeelding
* Services voor toegevoegde waarde: Bevat een afbeelding en een **Abonneren**-knop.

![create_web_template](assets/create_web_template.gif)

Alle entiteiten zoals documentfragmenten, grafieken, tabellen, afbeeldingen en knoppen worden toegevoegd tijdens het maken van de interactieve communicatie.

Voer de volgende stappen uit om een malplaatje voor het kanaal van het Web in **Create_First_IC_templates** omslag tot stand te brengen:

1. Navigeer naar de juiste sjabloonmap door **Tools** > **Templates** > **Create_First_IC_templates** te selecteren.
1. Tik **Maken**.
1. Selecteer **Interactieve communicatie - Webkanaal** en tik **Volgende** in de configuratietovenaar **Sjabloontype**.
1. Voor **Sjabloondetails** configuratietovenaar, specificeer **Create_First_IC_Web_Template** als malplaatjetitel. Geef een optionele beschrijving op en tik **Maken**.

   Een bevestigingsbericht dat **Create_First_IC_Web_Template** wordt getoond.

1. Tik **Open** om de sjabloon in de sjablooneditor te openen.
1. Selecteer **Eerste inhoud** in de vervolgkeuzelijst naast de optie **Voorvertoning**.

   ![Sjablooneditor](assets/template_editor_initial_content_new.png)

1. Tik op **Hoofdvenster** en tik op **+** om de lijst met componenten weer te geven die u aan de sjabloon kunt toevoegen.
1. Selecteer **Deelvenster** in de lijst om een deelvenster toe te voegen boven **Hoofddeelvenster**.
1. Selecteer het tabblad **Inhoud** in het linkerdeelvenster. Het nieuwe deelvenster dat in stap 8 is toegevoegd, wordt weergegeven onder **Hoofdvenster** in de inhoudsstructuur.

   ![Inhoudsstructuur](assets/content_tree_root_panel_new.png)

1. Selecteer het paneel en tik ![configure_icon](assets/configure_icon.png) (Configure).
1. In het deelvenster Eigenschappen:

   1. Geef **billdetails** op in het veld Naam.
   1. Geef **Bill Details** op in het veld Titel.
   1. Selecteer **1** in de vervolgkeuzelijst **Aantal kolommen**.

   1. Tik ![](/help/forms/using/assets/done_icon.png) om de eigenschappen op te slaan.

   De naam van het deelvenster wordt bijgewerkt naar **Bill Details** in de inhoudsstructuur.

1. Herhaal stap 7 - 11 om deelvensters met de volgende eigenschappen toe te voegen aan de sjabloon:

   | Naam | Titel | Aantal kolommen |
   |---|---|---|
   | klantgegevens | Klantgegevens | 1 |
   | billsummary | Bill Summary | 3 |
   | samenvattingskosten | Overzicht van heffingen | 2 |
   | gespecificeerde vraag | Gespecificeerde Vraag | 3 |
   | uitbetaling | Nu betalen | 2 |
   | vas | Services voor toegevoegde waarde | 3 |

   In de volgende afbeelding wordt de inhoudsstructuur weergegeven nadat alle deelvensters aan de sjabloon zijn toegevoegd:

   ![Inhoudsstructuur voor alle deelvensters](assets/content_tree_all_panels_new.png)

### De sjabloon {#enable-the-template} inschakelen

Zodra u het malplaatje van het Web hebt gecreeerd, moet u het toelaten om het malplaatje te gebruiken terwijl het creëren van de Interactieve Communicatie.

Voer de volgende stappen uit om het malplaatje van het Web toe te laten:

1. Tik **Gereedschappen** ![hamerpictogram](assets/hammer-icon.svg) > **Sjablonen**.
1. Navigeer naar de sjabloon **Create_First_IC_Web_Template**, selecteer deze en tik **Enable**.
1. Tab **Schakel** opnieuw in om te bevestigen.

   Het malplaatje wordt toegelaten en zijn status wordt getoond zoals Toegelaten. U kunt dit malplaatje gebruiken terwijl het creëren van Interactieve Communicatie voor het kanaal van het Web.

### Knoppen inschakelen in interactieve communicatie {#enabling-buttons-in-interactive-communications}

Gebaseerd op het gebruiksgeval, moet u **Nu betalen** en **Abonneren** knopen (adaptieve vormcomponenten) in Interactieve Mededeling omvatten. Voer de volgende stappen uit om het gebruik van deze knoppen in de interactieve communicatie mogelijk te maken:

1. Selecteer **Structuur** in de vervolgkeuzelijst naast de optie **Voorvertoning**.
1. Selecteer het **Hoofddeelvenster Documentcontainer** met de inhoudsstructuur en tik **Beleid** om de componenten te selecteren die zijn toegestaan voor gebruik in Interactieve communicatie.

   ![Beleid configureren](assets/structure_configure_policy_new.png)

1. Selecteer **Knop** op het tabblad **Eigenschappen** van de **Adaptief formulier**-componenten.****

   ![Toegestane componenten](assets/allowed_components_af_new.png)

1. Tik ![done_icon](assets/done_icon.png) om de eigenschappen op te slaan.