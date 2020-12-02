---
title: '"Zelfstudie: Interactieve communicatie maken "'
seo-title: Creeer een Interactieve Communicatie voor Druk en Web
description: Een interactieve communicatie maken met alle bouwstenen
seo-description: Een interactieve communicatie maken met alle bouwstenen
uuid: 5ffaa86f-87c7-4673-8b41-63ec61421be2
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ac5d8d4f-fc13-4e8d-819c-c5db07fa6870
docset: aem65
translation-type: tm+mt
source-git-commit: bd70508b361ac8b62ebc0344538a18369a075f3e
workflow-type: tm+mt
source-wordcount: '2002'
ht-degree: 0%

---


# Zelfstudie: Interactieve communicatie {#tutorial-create-interactive-communication} maken

![09-stijl-uw-adaptief-vorm-klein](assets/09-style-your-adaptive-form-small.png)

Deze zelfstudie is een stap in de serie [Maak uw eerste interactieve communicatiemodellen](/help/forms/using/create-your-first-interactive-communication.md). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat u alle bouwstenen voor de webversie hebt gemaakt, zoals het formuliergegevensmodel, documentfragmenten, sjablonen en thema&#39;s, kunt u een interactieve communicatie maken.

De interactieve Mededelingen kunnen door twee kanalen worden geleverd: Afdrukken en web. U kunt ook een interactieve communicatie maken met Afdrukkanaal als master kanaal. De druk als master optie voor het kanaal van het Web verzekert de inhoud, de overerving, en de gegevensband van het kanaal van het Web wordt afgeleid uit het kanaal van de Druk. Het zorgt ook dat de veranderingen in het kanaal van de Druk worden aangebracht gesynchroniseerd in het kanaal van het Web. De interactieve auteurs van Communicatie worden, echter, toegestaan om de overerving voor specifieke componenten in het kanaal van het Web te breken.

Dit leerprogramma begeleidt u door de stappen om interactieve mededelingen voor de kanalen van de Druk en van het Web tot stand te brengen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* Interactieve communicatie maken voor het afdrukkanaal
* Interactieve communicatie voor het webkanaal maken
* Creeer Druk en Web Interactieve Mededelingen met Druk als Master

## Interactieve communicatie voor afdrukken en web maken zonder synchronisatie {#create-interactive-communications-for-print-and-web-with-no-synchronization}

### Interactieve communicatie maken voor afdrukkanaal {#create-interactive-communication-for-print-channel}

Hier volgt een lijst met bronnen die al in deze zelfstudie zijn gemaakt en die nodig zijn tijdens het maken van de interactieve communicatie voor het kanaal Afdrukken:

**Afdruksjabloon:** [maken_eerste_ic_print_sjabloon](../../forms/using/create-templates-print-web.md)

**Formuliergegevensmodel:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Documentfragmenten:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](../../forms/using/create-document-fragments.md)

**Lay-outfragmenten:** [tabel_lf](../../forms/using/create-templates-print-web.md)

**afbeeldingen:** PayNow en ValueAddedServices

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tik **Maken** en selecteer **Interactieve communicatie**. De **Create Interactive Communication** tovenaar wordt getoond.
1. Geef **create_first_ic** op in het veld **Title** en **Name**. Selecteer **FDM_Create_First_IC** als het Model van de Gegevens van het Vorm en tik **Volgende**.
1. In de **tovenaar van Kanalen**:

   1. Geef **create_first_ic_print_template** op als de afdruksjabloon en tik **Select**. Zorg ervoor dat het selectievakje **Afdrukken gebruiken als Master voor webkanaal** niet is ingeschakeld.

   1. Geef **Create_First_IC_templates** map > **Create_First_IC_Web_Template** op als websjabloon en tik **Select**.

   1. Tik **Maken**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Tik **Bewerken** om de interactieve communicatie in het rechterdeelvenster te openen.
1. Ga naar het tabblad **Middelen** en pas het filter toe om alleen de documentfragmenten in het linkerdeelvenster weer te geven.
1. Sleep de volgende documentfragmenten naar het doelgebied in de interactieve communicatie.

   | Documentfragment | Doelgebied |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Heffingen |

   ![Documentfragmenten voor interactieve communicatie](assets/create_first_ic_doc_fragments_new.png)

1. Tik **Teken** doelgebied en tik **+** om een **Diagram**-component toe te voegen.
1. Tik op de component Chart en selecteer ![configure_icon](assets/configure_icon.png) (Configure). De grafiekeigenschappen worden weergegeven in het linkerdeelvenster:

   1. Geef een naam op voor het diagram.
   1. Selecteer **Schijf** van **Grafiektype** drop-down lijst.
   1. Selecteer **calltype** bezit van **vraag** het type van gegevensmodelvoorwerp in **X-as** sectie. Tik ![done_icon](assets/done_icon.png).
   1. Selecteer **Frequentie** in de vervolgkeuzelijst **Functie**.
   1. Selecteer **calltype** bezit van **vraag** het type van gegevensmodelvoorwerp in **Y-as** sectie. Tik ![done_icon](assets/done_icon.png).
   1. Tik ![done_icon](assets/done_icon.png) om de diagrameigenschappen op te slaan.

1. Ga naar het **tabblad Middelen** en pas het filter toe om alleen de layoutfragmenten in het linkerdeelvenster weer te geven. Sleep het **table_lf** lay-outfragment aan **Gespecialiseerde Vraag** doelgebied.
1. Selecteer het tekstveld in de kolom **Datum** en tik ![configure_icon](assets/configure_icon.png) (Configure).
1. Selecteer **Gegevensmodelobject** in de vervolgkeuzelijst **Bindend type** en selecteer **call** > **calldate**. Tik tweemaal op ![done_icon](assets/done_icon.png) om de eigenschappen op te slaan.

   Op dezelfde manier creeer band met **calltime**, **callnumber**, **callduration**, en **callcharges** voor tekstgebieden in **Time**, **Number**, **Duur**, respectievelijk **Laden** kolommen.

1. Tik **PayNow** doelgebied en tik **+** om een **Image**-component toe te voegen.
1. Tik op de component Image en selecteer ![configure_icon](assets/configure_icon.png) (Configure). De eigenschappen van de afbeelding worden weergegeven in het linkervenster:

   1. Geef **PayNow** op als de naam van de afbeelding in het veld **Naam**.
   1. Tik **Upload**, selecteer de afbeelding die is opgeslagen op het lokale bestandssysteem en tik **Open**.
   1. Tik ![done_icon](assets/done_icon.png) om de afbeeldingseigenschappen op te slaan.

1. Herhaal stap 13 en 14 om **ValueAddedServices**-afbeelding toe te voegen aan het doelgebied **ValueAddedServices**.

### Interactieve communicatie maken voor webkanaal {#create-interactive-communication-for-web-channel}

Hier volgt een lijst met bronnen die al in deze zelfstudie zijn gemaakt en die nodig zijn tijdens het maken van de interactieve communicatie voor het webkanaal:

**Websjabloon:** [Create_First_IC_Web_Template](../../forms/using/create-templates-print-web.md)

**Formuliergegevensmodel:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Documentfragmenten:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](../../forms/using/create-document-fragments.md)

**Afbeeldingen:** PayNowWeb en ValueAddedServicesWeb

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tik **Maken** en selecteer **Interactieve communicatie**. De **Create Interactive Communication** tovenaar wordt getoond.
1. Geef **create_first_ic** op in het veld **Title** en **Name**. Selecteer **FDM_Create_First_IC** als het Model van de Gegevens van het Vorm en tik **Volgende**.
1. In de **tovenaar van Kanalen**:

   1. Geef **create_first_ic_print_template** op als de afdruksjabloon en tik **Select**. Zorg ervoor dat het selectievakje **Afdrukken gebruiken als Master voor webkanaal** niet is ingeschakeld.

   1. Geef **Create_First_IC_templates** map > **Create_First_IC_Web_Template** op als websjabloon en tik **Select**.

   1. Tik **Maken**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Tik **Bewerken** om de interactieve communicatie in het rechterdeelvenster te openen.
1. Tik op het tabblad **Kanalen** in het linkerdeelvenster en tik op **Web**.
1. Ga naar het tabblad **Middelen** en pas het filter toe om alleen de documentfragmenten in het linkerdeelvenster weer te geven.
1. Sleep de volgende documentfragmenten naar het doelgebied in de interactieve communicatie.

   | Documentfragment | Doelgebied |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Heffingen |

1. Tik **Overzicht van laden** doelgebied en tik **+** om een **Chart**-component toe te voegen.
1. Tik op de component Chart en selecteer ![configure_icon](assets/configure_icon.png) (Configure). De grafiekeigenschappen worden weergegeven in het linkerdeelvenster:

   1. Geef een naam op voor het diagram.
   1. Selecteer **Schijf** van **Grafiektype** drop-down lijst.

   1. Selecteer **calltype** bezit van **vraag** het type van gegevensmodelvoorwerp in **X-as** sectie. Tik ![done_icon](assets/done_icon.png).

   1. Selecteer **Frequentie** in de vervolgkeuzelijst **Functie**.

   1. Selecteer **calltype** bezit van **vraag** het type van gegevensmodelvoorwerp in **Y-as** sectie. Tik ![done_icon](assets/done_icon.png).

   1. Tik ![done_icon](assets/done_icon.png) om de diagrameigenschappen op te slaan.

1. Selecteer **Gegevensbronnen** lusje van de linkerruit en belemmering-en-dalings **vraag** gegevensmodelvoorwerp aan **Gespecialiseerde Vraag** doelgebied. Alle eigenschappen in **call** gegevensmodelvoorwerp worden getoond als lijstkolommen in **Gespecialiseerde Vraag** doelgebied in de juiste ruit.

   Gebaseerd op het gebruiksgeval, vereist u de Datum van de Vraag, de Tijd van de Vraag, het Aantal van de Vraag, de Duur van de Vraag, en de kolommen van de Heffingen van de Vraag in de lijst.

   ![Tabel voor interactieve communicatie](assets/table_ic_web_new.png)

1. Selecteer **Mobilenum** kolomkop in de tabel en selecteer **Meer opties** > **Kolom** verwijderen. Op dezelfde manier schrap **Calltype** kolom.
1. Selecteer **Calldate** de kolomrubriek van de lijstkolom en tik ![geef](assets/edit.png) (geef uit) om de tekst anders te noemen in **Vraag Datum**. Wijzig de naam van de andere kolomkoppen in de tabel.
1. Gebaseerd op het gebruiksgeval, neem een **betaling nu** knoop in de Interactieve Mededeling op die de gebruiker een optie verstrekt om de betaling te maken door de knoop te klikken. Voer de volgende stappen uit om de knop in te voegen:

   1. Tik **Nu betalen** doelgebied en tik **+** om een **component Text** toe te voegen.

   1. Tik op de tekstcomponent en tik ![edit](assets/edit.png) (Edit).
   1. Wijzig de naam van de tekst in **Nu betalen**.
   1. Selecteer de tekst en tik op het hyperlinkpictogram.
   1. Geef de URL van de betaling op in het veld **Pad**.
   1. Selecteer **Nieuw tabblad** in de vervolgkeuzelijst **Doel**.

   1. Tik ![done_icon](assets/done_icon.png) om de hyperlinkeigenschappen op te slaan.

1. Selecteer **Stijl** in de vervolgkeuzelijst naast de optie **Voorvertoning**.

   ![Stijlmodus selecteren voor interactieve communicatie](assets/select_style_ic_web_new.png)

1. Maak de hyperlinktekst zodanig op dat deze als een knop in de interactieve communicatie wordt weergegeven. Ga hierbij als volgt te werk:

   1. Tik op de tekstcomponent en selecteer ![edit](assets/edit.png) (Edit).
   1. Geef in de sectie **Border** **1,5px** op als **Border Width**, selecteer **Solid** als **Border Style** en geef **46px** op als &lt;a 12/>Grensstraal **.**

   1. Selecteer Rood als achtergrondkleur voor de knop in de sectie **Achtergrond**.
   1. Tik in het veld **Marge** voor de sectie **Dimension &amp; Position** op het pictogram **gelijktijdig bewerken** en stel de marge **Right** in op **450px**. De velden Boven, Onder en Links worden ingesteld als leeg.

   ![Hyperlink invoegen in interactieve communicatie](assets/ic_web_hyperlink_new.png)

1. Tik **Nu betalen** doelgebied en tik **+** om een **Image**-component toe te voegen.
1. Tik op de component Image en selecteer ![configure_icon](assets/configure_icon.png) (Configure). De eigenschappen van de afbeelding worden weergegeven in het linkervenster:

   1. Geef **PayNow** op als de naam van de afbeelding in het veld **Naam**.

   1. Tik op **Uploaden**, selecteer de **PayNowWeb**-afbeelding die is opgeslagen op het lokale bestandssysteem en tik op **Open**.

   1. Tik ![done_icon](assets/done_icon.png) om de afbeeldingseigenschappen op te slaan.

1. Gebaseerd op het gebruiksgeval, neem een **Abonneren** knoop in de Interactieve Mededeling op die de gebruiker een optie verstrekt om aan de diensten op toegevoegde waarde in te tekenen door de knoop te klikken.

   Herhaal stap 13 - 17 om een **Abonneren** knoop aan **Value Added Services** doelgebied toe te voegen en **ValueAddedServicesWeb** beeld toe te voegen.

## Interactieve communicatie maken voor afdrukken en web met automatische synchronisatie {#create-interactive-communications-for-print-and-web-with-auto-synchronization}

U kunt ook een interactieve communicatie maken door automatische synchronisatie tussen Afdrukken en Webkanalen in te schakelen. Als u automatische synchronisatie wilt inschakelen, selecteert u de optie Afdrukken als master tijdens het maken van de interactieve communicatie. Als u de optie Afdrukken als master selecteert, worden de inhoud, overerving en gegevensbinding van het webkanaal afgeleid van het kanaal Afdrukken. Het zorgt ook dat de veranderingen in het kanaal van de Druk worden aangebracht weerspiegeld in het kanaal van het Web.

Voer de volgende stappen uit om de inhoud van het Kanaal van het Web af te leiden gebruikend het kanaal van de Druk:

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tik **Maken** en selecteer **Interactieve communicatie**. De **Create Interactive Communication** tovenaar wordt getoond.
1. Geef **create_first_ic** op in het veld **Title** en **Name**. Selecteer **FDM_Create_First_IC** als het Model van de Gegevens van het Vorm en tik **Volgende**.
1. In de **tovenaar van Kanalen**:

   1. Geef **create_first_ic_print_template** op als de afdruksjabloon en tik **Select**.

   1. Schakel het selectievakje **Afdrukken gebruiken als Master voor webkanaal** in.
   1. Geef **Create_First_IC_templates** map > **Create_First_IC_Web_Template** op als websjabloon en tik **Select**.

   1. Tik **Maken**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Tik **Bewerken** om de interactieve communicatie in het rechterdeelvenster te openen.
1. Voer stap 6 - 15 van [Interactieve communicatie voor het kanaal van de Druk ](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-print-channel) sectie uit.
1. Tik op het tabblad **Kanalen** in het linkerdeelvenster en tik **Web** om automatisch inhoud voor het webkanaal te genereren via het kanaal Afdrukken.
1. Aangezien **Afdrukken als Master voor het Kanaal van het Web** in stap 4 wordt geselecteerd, worden de inhoud en de banden auto-geproduceerd voor het kanaal van het Web van het kanaal van de Druk.

   De inhoud van het afdrukkanaal wordt ingevoegd onder de inhoud van de webkanaalsjabloon. Als u de inhoud van het webkanaal wilt wijzigen die automatisch is gegenereerd via het kanaal Afdrukken, kunt u de overerving voor elk doelgebied annuleren.

   Houd de cursor boven het desbetreffende doelgebied in het webkanaal en selecteer ![cancelinheritance](assets/cancelinheritance.png) (Overerving annuleren) en tik vervolgens in het dialoogvenster **Overerving annuleren** op **Yes**.

   ![Overerving annuleren](assets/cancel_inheritance_web_channel_new.png)

   Als u de overerving van een component hebt geannuleerd, kunt u deze opnieuw inschakelen. Als u overerving weer wilt inschakelen, plaatst u de cursor boven de grens van het desbetreffende doelgebied, dat de component omvat, en tikt u op ![opnieuw in te schakelen overerving](assets/reenableinheritance.png).

1. Selecteer het tabblad **Inhoud** in het linkerdeelvenster.
1. Sleep de automatisch gegenereerde webkanaalinhoud naar de bestaande deelvensters in de websjabloon met de inhoudsstructuur. Hieronder volgt een lijst met onderdelen die opnieuw moeten worden gerangschikt:

   * De component van Details van de rekening aan het paneel van Details van de Rekening
   * Customer Details component naar het deelvenster Customer Details
   * De Samenvattingscomponent van de Rekening aan het paneel van de Samenvatting van de Rekening
   * Samenvatting van de component van Heffingen aan Samenvatting van het paneel van Heffingen
   * Het fragment van de lay-out (lijst) aan het Gespecialiseerde paneel van Vraag

   ![Webinhoud-structuur](assets/ic_web_content_tree_new.png)

1. Herhaal stap 13 - 18 van [Interactieve communicatie voor het Kanaal van het Web creëren](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-web-channel) om **Nu betalen** en **Abonneren** hyperlinks in het Kanaal van het Web van de Interactieve Mededeling op te nemen.

