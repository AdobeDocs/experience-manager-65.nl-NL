---
title: "Zelfstudie: interactieve communicatie maken "
description: Een interactieve communicatie maken met alle bouwstenen
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: aaacee66-6bbe-498b-91b1-3a9545ff1aeb
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Zelfstudie: interactieve communicatie maken {#tutorial-create-interactive-communication}

![09-stijl-uw-adaptief-vorm-klein](assets/09-style-your-adaptive-form-small.png)

Deze zelfstudie is een stap in de [Maak uw eerste interactieve communicatie](/help/forms/using/create-your-first-interactive-communication.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat u alle bouwstenen voor de webversie hebt gemaakt, zoals het formuliergegevensmodel, documentfragmenten, sjablonen en thema&#39;s, kunt u een interactieve communicatie maken.

De interactieve Mededelingen kunnen door twee kanalen worden geleverd: Druk en Web. U kunt ook een interactieve communicatie maken met Afdrukkanaal als stramien. De druk als hoofdoptie voor het kanaal van het Web verzekert de inhoud, de overerving, en de gegevensband van het kanaal van het Web wordt afgeleid uit het kanaal van de Druk. Het zorgt ook dat de veranderingen in het kanaal van de Druk worden aangebracht gesynchroniseerd in het kanaal van het Web. De interactieve auteurs van Communicatie worden, echter, toegestaan om de overerving voor specifieke componenten in het kanaal van het Web te breken.

Dit leerprogramma begeleidt u door de stappen om interactieve mededelingen voor de kanalen van de Druk en van het Web tot stand te brengen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* Interactieve communicatie maken voor het afdrukkanaal
* Interactieve communicatie voor het webkanaal maken
* Interactieve communicatie voor afdrukken en web maken met Afdrukken als origineel

## Interactieve communicatie voor afdrukken en web maken zonder synchronisatie {#create-interactive-communications-for-print-and-web-with-no-synchronization}

### Interactieve communicatie maken voor het afdrukkanaal {#create-interactive-communication-for-print-channel}

Hier volgt een lijst met bronnen die al in deze zelfstudie zijn gemaakt en die nodig zijn tijdens het maken van de interactieve communicatie voor het kanaal Afdrukken:

**Afdruksjabloon:** [create_first_ic_print_template](../../forms/using/create-templates-print-web.md)

**Formuliergegevensmodel:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Documentfragmenten:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](../../forms/using/create-document-fragments.md)

**Layoutfragmenten:** [table_lf](../../forms/using/create-templates-print-web.md)

**Afbeeldingen:** PayNow en ValueAddedServices

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **Maken** en selecteert u **Interactieve communicatie**. De **Interactieve communicatie maken** wordt weergegeven.
1. Opgeven **create_first_ic** in de **Titel** en de **Naam** veld. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Volgende**.
1. In de **Kanalen** wizard:

   1. Opgeven **create_first_ic_print_template** als de sjabloon Afdrukken en selecteer **Selecteren**. Zorg ervoor dat de **Afdrukken als origineel voor webkanaal gebruiken** selectievakje is niet ingeschakeld.

   1. Opgeven **Create_First_IC_templates** map > **Create_First_IC_Web_Template** als het malplaatje van het Web en selecteer **Selecteren**.

   1. Selecteren **Maken**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Selecteren **Bewerken** om de Interactieve Communicatie in de juiste ruit te openen.
1. Ga naar de **Activa** en pas het filter toe om alleen de documentfragmenten in het linkervenster weer te geven.
1. Sleep de volgende documentfragmenten naar het doelgebied in de interactieve communicatie.

   | Documentfragment | Doelgebied |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Heffingen |

   ![Documentfragmenten voor interactieve communicatie](assets/create_first_ic_doc_fragments_new.png)

1. Selecteren **Grafieken** doelgebied en selecteer **+** om een **Diagram** component.
1. Selecteer de component van de Grafiek en selecteer ![configure_icon](assets/configure_icon.png) (Configureren). De grafiekeigenschappen worden weergegeven in het linkerdeelvenster:

   1. Geef een naam op voor het diagram.
   1. Selecteren **Schijf** van de **Type diagram** vervolgkeuzelijst.
   1. Selecteer de **calltype** eigenschap van de **oproepen** objecttype gegevensmodel in het dialoogvenster **X-as** sectie. Selecteren ![done_icon](assets/done_icon.png).
   1. Selecteren **Frequentie** van de **Functie** vervolgkeuzelijst.
   1. Selecteer de **calltype** eigenschap van de **oproepen** objecttype gegevensmodel in het dialoogvenster **Y-as** sectie. Selecteren ![done_icon](assets/done_icon.png).
   1. Selecteren ![done_icon](assets/done_icon.png) om de eigenschappen van het diagram op te slaan.

1. Ga naar de **Activa** en pas het filter toe om alleen de layoutfragmenten in het linkerdeelvenster weer te geven. Sleep de **table_lf** lay-outfragment naar de **Gespecificeerde Vraag** doelgebied.
1. Selecteer het tekstveld in het dialoogvenster **Datum** kolom en selecteer ![configure_icon](assets/configure_icon.png) (Configureren).
1. Selecteren **Gegevensmodelobject** van de **Bindingstype** vervolgkeuzelijst en selecteer **oproepen** > **calldate**. Selecteren ![done_icon](assets/done_icon.png) twee keer om de eigenschappen op te slaan.

   Op dezelfde manier binding maken met **calltime**, **callnumber**, **callduration**, en **opvragingskosten** voor tekstvelden in het dialoogvenster **Tijd**, **Getal**, **Duur**, en **Heffingen** kolommen.

1. Selecteren **Nu betalen** doelgebied en selecteer **+** om een **Afbeelding** component.
1. Selecteer de component Image en selecteer ![configure_icon](assets/configure_icon.png) (Configureren). De eigenschappen van de afbeelding worden weergegeven in het linkervenster:

   1. Opgeven **Nu betalen** als de naam van de afbeelding in het dialoogvenster **Naam** veld.
   1. Selecteren **Uploaden** selecteert u de afbeelding die op het lokale bestandssysteem is opgeslagen en selecteert u **Openen**.
   1. Selecteren ![done_icon](assets/done_icon.png) om de eigenschappen van de afbeelding op te slaan.

1. De stappen 13 en 14 herhalen om toe te voegen **ValueAddedServices** aan de **ValueAddedServices** doelgebied.

### Interactieve communicatie voor webkanaal maken {#create-interactive-communication-for-web-channel}

Hier volgt een lijst met bronnen die al in deze zelfstudie zijn gemaakt en die nodig zijn tijdens het maken van de interactieve communicatie voor het webkanaal:

**Websjabloon:** [Create_First_IC_Web_Template](../../forms/using/create-templates-print-web.md)

**Formuliergegevensmodel:** [FDM_Create_First_IC](../../forms/using/create-form-data-model0.md)

**Documentfragmenten:** [bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic](../../forms/using/create-document-fragments.md)

**Afbeeldingen:** PayNowWeb en ValueAddedServicesWeb

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **Maken** en selecteert u **Interactieve communicatie**. De **Interactieve communicatie maken** wordt weergegeven.
1. Opgeven **create_first_ic** in de **Titel** en de **Naam** veld. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Volgende**.
1. In de **Kanalen** wizard:

   1. Opgeven **create_first_ic_print_template** als de sjabloon Afdrukken en selecteer **Selecteren**. Zorg ervoor dat de **Afdrukken als origineel voor webkanaal gebruiken** selectievakje is niet ingeschakeld.

   1. Opgeven **Create_First_IC_templates** map > **Create_First_IC_Web_Template** als het malplaatje van het Web en selecteer **Selecteren**.

   1. Selecteren **Maken**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Selecteren **Bewerken** om de Interactieve Communicatie in de juiste ruit te openen.
1. Selecteer de **Kanalen** van het linkerpaneel en selecteer **Web**.
1. Ga naar de **Activa** en pas het filter toe om alleen de documentfragmenten in het linkervenster weer te geven.
1. Sleep de volgende documentfragmenten naar het doelgebied in de interactieve communicatie.

   | Documentfragment | Doelgebied |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Heffingen |

1. Selecteren **Overzicht van heffingen** doelgebied en selecteer **+** om een **Diagram** component.
1. Selecteer de component van de Grafiek en selecteer ![configure_icon](assets/configure_icon.png) (Configureren). De grafiekeigenschappen worden weergegeven in het linkerdeelvenster:

   1. Geef een naam op voor het diagram.
   1. Selecteren **Schijf** van de **Type diagram** vervolgkeuzelijst.

   1. Selecteer de **calltype** eigenschap van de **oproepen** objecttype gegevensmodel in het dialoogvenster **X-as** sectie. Selecteren ![done_icon](assets/done_icon.png).

   1. Selecteren **Frequentie** van de **Functie** vervolgkeuzelijst.

   1. Selecteer de **calltype** eigenschap van de **oproepen** objecttype gegevensmodel in het dialoogvenster **Y-as** sectie. Selecteren ![done_icon](assets/done_icon.png).

   1. Selecteren ![done_icon](assets/done_icon.png) om de eigenschappen van het diagram op te slaan.

1. Selecteer de **Gegevensbronnen** van het linkervenster en sleep-en-daling **oproepen** gegevensmodelobject naar het **Gespecificeerde Vraag** doelgebied. Alle eigenschappen in het dialoogvenster **oproepen** gegevensmodelobject wordt weergegeven als tabelkolommen in het dialoogvenster **Gespecificeerde Vraag** doelgebied in het rechterdeelvenster.

   Gebaseerd op het gebruiksgeval, vereist u de Datum van de Vraag, de Tijd van de Vraag, het Aantal van de Vraag, de Duur van de Vraag, en de kolommen van de Heffingen van de Vraag in de lijst.

   ![Tabel voor interactieve communicatie](assets/table_ic_web_new.png)

1. Selecteren **Mobilenum** tabelkolomkop en selecteer **Meer opties** > **Kolom verwijderen**. Verwijder op dezelfde manier de **Calltype** kolom.
1. Selecteer de **Bijschrift** tabelkolomkop en selecteer ![bewerken](assets/edit.png) (Bewerken) om de naam van de tekst te wijzigen in **Aanroepingsdatum**. Wijzig de naam van de andere kolomkoppen in de tabel.
1. Voeg op basis van het geval van gebruik een **Nu betalen** in de interactieve communicatie die de gebruiker een optie biedt om de betaling uit te voeren door op de knop te klikken. Voer de volgende stappen uit om de knop in te voegen:

   1. Selecteren **Nu betalen** doelgebied en selecteer **+** om een **Tekst** component.

   1. Selecteer de tekstcomponent en selecteer ![bewerken](assets/edit.png) (Bewerken).
   1. De naam van de tekst wijzigen in **Nu betalen**.
   1. Selecteer de tekst en selecteer het pictogram Hyperlink.
   1. Geef de betalings-URL op in het dialoogvenster **Pad** veld.
   1. Selecteren **Nieuw tabblad** van **Doel** vervolgkeuzelijst.

   1. Selecteren ![done_icon](assets/done_icon.png) om de eigenschappen van de hyperlink op te slaan.

1. Selecteren **Stijl** in de vervolgkeuzelijst naast de **Voorvertoning** -optie.

   ![Stijlmodus selecteren voor interactieve communicatie](assets/select_style_ic_web_new.png)

1. Maak de hyperlinktekst zodanig op dat deze als een knop in de interactieve communicatie wordt weergegeven. Ga hierbij als volgt te werk:

   1. Selecteer de tekstcomponent en selecteer ![bewerken](assets/edit.png) (Bewerken).
   1. In de **Rand** sectie, specificeren **1,5 px** als **Randbreedte**, selecteert u **Effen** als **Randstijl** en geeft **46 px** als **Straal rand**.

   1. Selecteer Rood als achtergrondkleur voor de knop in het menu **Achtergrond** sectie.
   1. In de **Marge** veld voor **Dimensionen en positie** selecteert u de **Gelijktijdig bewerken** en stelt de **Rechts** marge als **450 px**. De velden Boven, Onder en Links worden ingesteld als leeg.

   ![Hyperlink invoegen in interactieve communicatie](assets/ic_web_hyperlink_new.png)

1. Selecteren **Nu betalen** doelgebied en selecteer **+** om een **Afbeelding** component.
1. Selecteer de component Image en selecteer ![configure_icon](assets/configure_icon.png) (Configureren). De eigenschappen van de afbeelding worden weergegeven in het linkervenster:

   1. Opgeven **Nu betalen** als de naam van de afbeelding in het dialoogvenster **Naam** veld.

   1. Selecteren **Uploaden**, selecteert u de **PayNowWeb** afbeelding opgeslagen in het lokale bestandssysteem en selecteer **Openen**.

   1. Selecteren ![done_icon](assets/done_icon.png) om de eigenschappen van de afbeelding op te slaan.

1. Voeg op basis van het geval van gebruik een **Abonneren** in de Interactieve Mededeling die de gebruiker een optie verstrekt om aan de diensten van de toegevoegde waarde in te schrijven door de knoop te klikken.

   Herhaal stap 13 - 17 om een **Abonneren** aan de **Services voor toegevoegde waarde** doelgebied en voeg de **ValueAddedServicesWeb** afbeelding.

## Interactieve communicatie voor afdrukken en web maken met automatische synchronisatie {#create-interactive-communications-for-print-and-web-with-auto-synchronization}

U kunt ook een interactieve communicatie maken door automatische synchronisatie tussen Afdrukken en Webkanalen in te schakelen. Als u automatische synchronisatie wilt inschakelen, selecteert u de optie Afdrukken als stramien tijdens het maken van de interactieve communicatie. Als u de optie Afdrukken als stramien selecteert, wordt de inhoud, overerving en gegevensbinding van het webkanaal afgeleid van het kanaal Afdrukken. Het zorgt ook dat de veranderingen in het kanaal van de Druk worden aangebracht weerspiegeld in het kanaal van het Web.

Voer de volgende stappen uit om de inhoud van het Kanaal van het Web af te leiden gebruikend het kanaal van de Druk:

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **Maken** en selecteert u **Interactieve communicatie**. De **Interactieve communicatie maken** wordt weergegeven.
1. Opgeven **create_first_ic** in de **Titel** en de **Naam** veld. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Volgende**.
1. In de **Kanalen** wizard:

   1. Opgeven **create_first_ic_print_template** als de sjabloon Afdrukken en selecteer **Selecteren**.

   1. Selecteer de **Afdrukken als origineel voor webkanaal gebruiken** selectievakje.
   1. Opgeven **Create_First_IC_templates** map > **Create_First_IC_Web_Template** als het malplaatje van het Web en selecteer **Selecteren**.

   1. Selecteren **Maken**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Selecteren **Bewerken** om de Interactieve Communicatie in de juiste ruit te openen.
1. Voer stap 6 - 15 uit van [Interactieve communicatie maken voor het afdrukkanaal](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-print-channel) sectie.
1. Selecteer de **Kanalen** van het linkerpaneel en selecteer **Web** om automatisch inhoud voor het webkanaal te genereren via het kanaal Afdrukken.
1. Als de **Afdrukken als origineel voor webkanaal gebruiken** Schakel het selectievakje in in stap 4. De inhoud en bindingen worden automatisch gegenereerd voor het webkanaal via het kanaal Afdrukken.

   De inhoud van het afdrukkanaal wordt ingevoegd onder de inhoud van de webkanaalsjabloon. Als u de inhoud van het webkanaal wilt wijzigen die automatisch is gegenereerd via het kanaal Afdrukken, kunt u de overerving voor elk doelgebied annuleren.

   Houd de muisaanwijzer boven het desbetreffende doelgebied in het webkanaal en selecteer ![cancelovererving](assets/cancelinheritance.png) (Overerving annuleren) en vervolgens in het dialoogvenster **Overerving annuleren** dialoogvenster, selecteren **Ja**.

   ![Overerving annuleren](assets/cancel_inheritance_web_channel_new.png)

   Als u de overerving van een component hebt geannuleerd, kunt u deze opnieuw inschakelen. Als u overerving weer wilt inschakelen, plaatst u de cursor boven de grens van het desbetreffende doelgebied, dat de component omvat, en selecteert u ![reenableerbaarheid](assets/reenableinheritance.png).

1. Selecteer de **Inhoud** in het linkerdeelvenster.
1. Sleep de automatisch gegenereerde webkanaalinhoud naar de bestaande deelvensters in de websjabloon met de inhoudsstructuur. Hieronder volgt een lijst met onderdelen die opnieuw moeten worden gerangschikt:

   * De component van Details van de rekening aan het paneel van Details van de Rekening
   * Customer Details component naar het deelvenster Customer Details
   * De Samenvattingscomponent van de Rekening aan het paneel van de Overzicht van de Rekening
   * Samenvatting van de component van Laden aan Samenvatting van het paneel van Laden
   * Het fragment van de lay-out (lijst) aan het Gespecialiseerde paneel van Vraag

   ![Webinhoud-structuur](assets/ic_web_content_tree_new.png)

1. Herhaal stap 13 - 18 van [Interactieve communicatie voor webkanaal maken](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-web-channel) om de **Nu betalen** en **Abonneren** hyperlinks in het kanaal van het Web van de Interactieve Mededeling.
