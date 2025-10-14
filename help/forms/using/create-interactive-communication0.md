---
title: 'Zelfstudie: interactieve communicatie maken '
description: Een interactieve communicatie maken met alle bouwstenen
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: aaacee66-6bbe-498b-91b1-3a9545ff1aeb
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Zelfstudie: interactieve communicatie maken {#tutorial-create-interactive-communication}

![&#x200B; 09-stijl-uw-adaptief-vorm-klein &#x200B;](assets/09-style-your-adaptive-form-small.png)

Dit leerprogramma is een stap in [&#x200B; creeer uw eerste Interactieve Communicatie &#x200B;](/help/forms/using/create-your-first-interactive-communication.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat u alle bouwstenen voor de webversie hebt gemaakt, zoals het formuliergegevensmodel, documentfragmenten, sjablonen en thema&#39;s, kunt u een interactieve communicatie maken.

De interactieve Mededelingen kunnen door twee kanalen worden geleverd: Druk en Web. U kunt ook een interactieve communicatie maken met Afdrukkanaal als stramien. De druk als hoofdoptie voor het kanaal van het Web verzekert de inhoud, de overerving, en de gegevensband van het kanaal van het Web wordt afgeleid uit het kanaal van de Druk. Het zorgt ook dat de veranderingen in het kanaal van de Druk worden aangebracht gesynchroniseerd in het kanaal van het Web. De interactieve auteurs van Communicatie worden, echter, toegestaan om de overerving voor specifieke componenten in het kanaal van het Web te breken.

Dit leerprogramma begeleidt u door de stappen om interactieve mededelingen voor de kanalen van de Druk en van het Web tot stand te brengen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* Interactieve communicatie maken voor het afdrukkanaal
* Interactieve communicatie voor het webkanaal maken
* Interactieve communicatie voor afdrukken en web maken met Afdrukken als origineel

## Interactieve communicatie voor afdrukken en web maken zonder synchronisatie {#create-interactive-communications-for-print-and-web-with-no-synchronization}

### Interactieve communicatie maken voor het afdrukkanaal {#create-interactive-communication-for-print-channel}

Hier volgt een lijst met bronnen die al in deze zelfstudie zijn gemaakt en die nodig zijn tijdens het maken van de interactieve communicatie voor het kanaal Afdrukken:

**malplaatje van de Druk:** [&#x200B; create_first_ic_print_template &#x200B;](../../forms/using/create-templates-print-web.md)

**Model van de Gegevens van de Vorm:** [&#x200B; FDM_Create_First_IC &#x200B;](../../forms/using/create-form-data-model0.md)

**Fragments van het Document:** [&#x200B; bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic &#x200B;](../../forms/using/create-document-fragments.md)

**Fragmenten van de Lay-out:** [&#x200B; table_lf &#x200B;](../../forms/using/create-templates-print-web.md)

**Beelden:** PayNow en ValueAddedServices

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **creeer** en selecteer **Interactieve Communicatie**. **creeer Interactieve Communicatie** tovenaar wordt getoond.
1. Specificeer **create_first_ic** in de **Titel** en het **gebied van de Naam**. Selecteer **FDM_Create_First_IC** als Model van de Gegevens van de Vorm en selecteer **daarna**.
1. In de **tovenaar van Kanalen**:

   1. Specificeer **create_first_ic_print_template** als malplaatje van de Druk en selecteer **Uitgezocht**. Zorg ervoor dat het **Gebruik Druk als Meester voor het Kanaal van het Web** checkbox niet wordt geselecteerd.

   1. Specificeer **Create_First_IC_templates** omslag > **Create_First_IC_Web_Template** als malplaatje van het Web en selecteer **Uitgezocht**.

   1. Selecteer **creeer**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Selecteer **uitgeven** om de Interactieve Mededeling in de juiste ruit te openen.
1. Ga naar het **Assets** lusje en pas de filter toe om slechts de documentfragmenten in de linkerruit te tonen.
1. Sleep de volgende documentfragmenten naar het doelgebied in de interactieve communicatie.

   | Documentfragment | Doelgebied |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Heffingen |

   ![&#x200B; de fragmenten van het Document voor Interactieve Mededelingen &#x200B;](assets/create_first_ic_doc_fragments_new.png)

1. Selecteer **doelgebied van Grafieken 1&rbrace;, en selecteer** + **om de component van de a** Grafiek **toe te voegen.**
1. Selecteer de component van de Grafiek en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm). De grafiekeigenschappen worden weergegeven in het linkerdeelvenster:

   1. Geef een naam op voor het diagram.
   1. Selecteer **Schijf** van de **drop-down lijst van het Type van Grafiek**.
   1. Selecteer het **calltype** bezit van het **vraag** type van gegevensmodel in de **x-as** sectie. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png).
   1. Selecteer **Frequentie** van de **drop-down lijst van de Functie**.
   1. Selecteer het **calltype** bezit van het **vraag** type van gegevensmodel in de **y-as** sectie. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png).
   1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de grafiekeigenschappen te bewaren.

1. Ga naar het **Assets** lusje en pas de filter toe om slechts de lay-outfragmenten in de linkerruit te tonen. Sleep-en-daling het **table_lf** lay-outfragment aan het **Gespecialiseerde Vraag** doelgebied.
1. Selecteer het Gebied van de Tekst in de **kolom van de Datum** &lbrace;en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm).
1. Selecteer **ModelVoorwerp van Gegevens** van de **Bindende drop-down lijst van het Type** en selecteer **vraag** > **calldate**. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) tweemaal om de eigenschappen te bewaren.

   Op dezelfde manier creeer band met **calltime**, **callnumber**, **callduration**, en **callloads** voor tekstgebieden in de **Tijd**, **Aantal**, **Duur**, en **lading** kolommen.

1. Selecteer **PayNow** doelgebied, en selecteer **+** om een **component van het Beeld** toe te voegen.
1. Selecteer de component van het Beeld en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm). De eigenschappen van de afbeelding worden weergegeven in het linkervenster:

   1. Specificeer **PayNow** als naam van het beeld op het **3&rbrace; gebied van de Naam &lbrace;.**
   1. Selecteer **uploaden**, selecteer het beeld dat op het lokale dossiersysteem wordt bewaard, en selecteer **Open**.
   1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de beeldeigenschappen te bewaren.

1. Herhaal stappen 13 en 14 om **beeld ValueAddedServices** aan het **&#x200B;**&#x200B;doelgebied toe te voegen ValueAddedServices.

### Interactieve communicatie voor webkanaal maken {#create-interactive-communication-for-web-channel}

Hier volgt een lijst met bronnen die al in deze zelfstudie zijn gemaakt en die nodig zijn tijdens het maken van de interactieve communicatie voor het webkanaal:

**malplaatje van het Web:** [&#x200B; Create_First_IC_Web_Template &#x200B;](../../forms/using/create-templates-print-web.md)

**Model van de Gegevens van de Vorm:** [&#x200B; FDM_Create_First_IC &#x200B;](../../forms/using/create-form-data-model0.md)

**Fragments van het Document:** [&#x200B; bill_details_first_ic, customer_details_first_ic, bill_summary_first_ic, summary_charges_first_ic &#x200B;](../../forms/using/create-document-fragments.md)

**Beelden:** PayNowWeb en ValueAddedServicesWeb

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **creeer** en selecteer **Interactieve Communicatie**. **creeer Interactieve Communicatie** tovenaar wordt getoond.
1. Specificeer **create_first_ic** in de **Titel** en het **gebied van de Naam**. Selecteer **FDM_Create_First_IC** als Model van de Gegevens van de Vorm en selecteer **daarna**.
1. In de **tovenaar van Kanalen**:

   1. Specificeer **create_first_ic_print_template** als malplaatje van de Druk en selecteer **Uitgezocht**. Zorg ervoor dat het **Gebruik Druk als Meester voor het Kanaal van het Web** checkbox niet wordt geselecteerd.

   1. Specificeer **Create_First_IC_templates** omslag > **Create_First_IC_Web_Template** als malplaatje van het Web en selecteer **Uitgezocht**.

   1. Selecteer **creeer**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Selecteer **uitgeven** om de Interactieve Mededeling in de juiste ruit te openen.
1. Selecteer het **lusje van Kanalen** van de linkerruit en selecteer **Web**.
1. Ga naar het **Assets** lusje en pas de filter toe om slechts de documentfragmenten in de linkerruit te tonen.
1. Sleep de volgende documentfragmenten naar het doelgebied in de interactieve communicatie.

   | Documentfragment | Doelgebied |
   |---|---|
   | bill_details_first_ic | BillDetails |
   | customer_details_first_ic | CustomerDetails |
   | bill_summary_first_ic | BillSummary |
   | summary_charges_first_interactive_communication | Heffingen |

1. Selecteer **Samenvatting van de Tarieven** doelgebied, en selecteer **+** om de component van de a **Grafiek** toe te voegen.
1. Selecteer de component van de Grafiek en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm). De grafiekeigenschappen worden weergegeven in het linkerdeelvenster:

   1. Geef een naam op voor het diagram.
   1. Selecteer **Schijf** van de **drop-down lijst van het Type van Grafiek**.

   1. Selecteer het **calltype** bezit van het **vraag** type van gegevensmodel in de **x-as** sectie. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png).

   1. Selecteer **Frequentie** van de **drop-down lijst van de Functie**.

   1. Selecteer het **calltype** bezit van het **vraag** type van gegevensmodel in de **y-as** sectie. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png).

   1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de grafiekeigenschappen te bewaren.

1. Selecteer het **Bronnen van Gegevens** lusje van de linkerruit en belemmering-en-daling het **voorwerp van het vraag** gegevensmodel aan het **Getoonde Vraag** doelgebied. Alle eigenschappen in het **vraag** gegevensmodelvoorwerp wordt getoond als lijstkolommen in het **Gespecialiseerde het doelgebied van Vraag** in de juiste ruit.

   Gebaseerd op het gebruiksgeval, vereist u de Datum van de Vraag, de Tijd van de Vraag, het Aantal van de Vraag, de Duur van de Vraag, en de kolommen van de Heffingen van de Vraag in de lijst.

   ![&#x200B; Lijst voor Interactieve Communicatie &#x200B;](assets/table_ic_web_new.png)

1. Selecteer **Mobilenum** de kolomrubriek van de lijst en selecteer **Meer opties** > **kolom van de Schrapping**. Op dezelfde manier schrap **Calltype** kolom.
1. Selecteer de **de kolomrubriek van de 0&rbrace; Bijgestelde** lijst en selecteer ![&#x200B; uitgeven &#x200B;](assets/edit.png) (geef uit) om de tekst anders te noemen aan **Datum van de Vraag**. Wijzig de naam van de andere kolomkoppen in de tabel.
1. Gebaseerd op het gebruiksgeval, neem a **nu betalen** knoop in de Interactieve Mededeling op die de gebruiker een optie verstrekt om de betaling te maken door de knoop te klikken. Voer de volgende stappen uit om de knop in te voegen:

   1. Selecteer **nu betalen** doelgebied, en selecteren **+** om de component van de a **Tekst** toe te voegen.

   1. Selecteer de tekstcomponent en selecteer ![&#x200B; uitgeven &#x200B;](assets/edit.png) (geef uit).
   1. Wijzig de naam van de tekst aan **nu betalen**.
   1. Selecteer de tekst en selecteer het pictogram Hyperlink.
   1. Specificeer betalings URL op het **gebied van de Weg**.
   1. Selecteer **Nieuw Lusje** van **drop-down lijst van het Doel**.

   1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de hyperlinkeigenschappen te bewaren.

1. Selecteer **Stijl** van de drop-down lijst naast de **optie van de Voorproef**.

   ![&#x200B; Uitgezochte wijze van de Stijl voor Interactieve Communicatie &#x200B;](assets/select_style_ic_web_new.png)

1. Maak de hyperlinktekst zodanig op dat deze als een knop in de interactieve communicatie wordt weergegeven. Ga hierbij als volgt te werk:

   1. Selecteer de tekstcomponent en selecteer ![&#x200B; uitgeven &#x200B;](assets/edit.png) (geef uit).
   1. In de **sectie 0&rbrace; Grens &lbrace;, specificeer** 1.5px **als** Breedte van de Grens **, selecteer** Ononderbroken **als** Stijl van de Grens **, en specificeer** 46px **als** Straal van de Grens **.**

   1. Selecteer Rood als achtergrondkleur voor de knoop van de **Achtergrond** sectie.
   1. Op het **gebied van de Marge** voor **Dimensionen &amp; de sectie van de Positie**, uitgezocht gelijktijdig **uitgeven** pictogram, en plaats de **juiste** marge als **450px**. De velden Boven, Onder en Links worden ingesteld als leeg.

   ![&#x200B; hyperlink van het Tussenvoegsel in Interactieve Mededeling &#x200B;](assets/ic_web_hyperlink_new.png)

1. Selecteer **nu betalen** doelgebied, en selecteren **+** om een **component van het Beeld** toe te voegen.
1. Selecteer de component van het Beeld en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm). De eigenschappen van de afbeelding worden weergegeven in het linkervenster:

   1. Specificeer **PayNow** als naam van het beeld op het **3&rbrace; gebied van de Naam &lbrace;.**

   1. Selecteer **uploaden**, selecteer het **&#x200B;**&#x200B;beeld PayNowWeb dat op het lokale dossiersysteem wordt bewaard, en selecteer **Open**.

   1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de beeldeigenschappen te bewaren.

1. Gebaseerd op het gebruiksgeval, neem a **in Abonneren** knoop in de Interactieve Mededeling die de gebruiker een optie verstrekt om aan de diensten van de toegevoegde waarde in te tekenen door de knoop te klikken.

   Herhaal stappen 13 - 17 om a **toe te voegen onderteken** knoop aan de **Waarde Toegevoegde het doelgebied van de Diensten** en voeg het **&#x200B;**&#x200B;beeld ValueAddedServicesWeb toe.

## Interactieve communicatie voor afdrukken en web maken met automatische synchronisatie {#create-interactive-communications-for-print-and-web-with-auto-synchronization}

U kunt ook een interactieve communicatie maken door automatische synchronisatie tussen Afdrukken en Webkanalen in te schakelen. Als u automatische synchronisatie wilt inschakelen, selecteert u de optie Afdrukken als stramien tijdens het maken van de interactieve communicatie. Als u de optie Afdrukken als stramien selecteert, wordt de inhoud, overerving en gegevensbinding van het webkanaal afgeleid van het kanaal Afdrukken. Het zorgt ook dat de veranderingen in het kanaal van de Druk worden aangebracht weerspiegeld in het kanaal van het Web.

Voer de volgende stappen uit om de inhoud van het Kanaal van het Web af te leiden gebruikend het kanaal van de Druk:

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **creeer** en selecteer **Interactieve Communicatie**. **creeer Interactieve Communicatie** tovenaar wordt getoond.
1. Specificeer **create_first_ic** in de **Titel** en het **gebied van de Naam**. Selecteer **FDM_Create_First_IC** als Model van de Gegevens van de Vorm en selecteer **daarna**.
1. In de **tovenaar van Kanalen**:

   1. Specificeer **create_first_ic_print_template** als malplaatje van de Druk en selecteer **Uitgezocht**.

   1. Selecteer het **Gebruik Druk als Meester voor het Kanaal van het Web** checkbox.
   1. Specificeer **Create_First_IC_templates** omslag > **Create_First_IC_Web_Template** als malplaatje van het Web en selecteer **Uitgezocht**.

   1. Selecteer **creeer**.

   Er wordt een bevestigingsbericht weergegeven dat de interactieve communicatie is gemaakt.

1. Selecteer **uitgeven** om de Interactieve Mededeling in de juiste ruit te openen.
1. Voer stappen 6 uit - 15 van [&#x200B; creëren Interactieve Communicatie voor het kanaal van de Druk &#x200B;](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-print-channel) sectie.
1. Selecteer het **lusje van Kanalen** van de linkerruit en selecteer **Web** om inhoud voor het kanaal van het Web van het kanaal van de Druk auto-produceren.
1. Aangezien het **Gebruik Druk als Meester voor Kanaal van het Web** checkbox in stap 4 wordt geselecteerd, worden de inhoud en de banden auto-geproduceerd voor het kanaal van het Web van het kanaal van de Druk.

   De inhoud van het afdrukkanaal wordt ingevoegd onder de inhoud van de webkanaalsjabloon. Als u de inhoud van het webkanaal wilt wijzigen die automatisch is gegenereerd via het kanaal Afdrukken, kunt u de overerving voor elk doelgebied annuleren.

   Beweeg over het relevante doelgebied in het Webkanaal en selecteer ![&#x200B; annuleringserving &#x200B;](assets/cancelinheritance.png) (Cancel Overerving) en dan in de **annuleert Overerving** dialoog, uitgezochte **ja**.

   ![&#x200B; annuleert overerving &#x200B;](assets/cancel_inheritance_web_channel_new.png)

   Als u de overerving van een component hebt geannuleerd, kunt u deze opnieuw inschakelen. Om overerving re-toe te laten, houd over de grens van het relevante doelgebied, dat de component omvat, en selecteer ![&#x200B; reenableinheritance &#x200B;](assets/reenableinheritance.png) opnieuw in.

1. Selecteer het **lusje van de Inhoud** in de linkerruit.
1. Sleep de automatisch gegenereerde webkanaalinhoud naar de bestaande deelvensters in de websjabloon met de inhoudsstructuur. Hieronder volgt een lijst met onderdelen die opnieuw moeten worden gerangschikt:

   * De component van Details van de rekening aan het paneel van Details van de Rekening
   * Customer Details component naar het deelvenster Customer Details
   * De Samenvattingscomponent van de Rekening aan het paneel van de Overzicht van de Rekening
   * Samenvatting van de component van Laden aan Samenvatting van het paneel van Laden
   * Het fragment van de lay-out (lijst) aan het Gespecialiseerde paneel van Vraag

   ![&#x200B; de inhoudsboom van het Web &#x200B;](assets/ic_web_content_tree_new.png)

1. Herhaal stappen 13 - 18 van [&#x200B; creëren Interactieve Mededeling voor het kanaal van het Web &#x200B;](../../forms/using/create-interactive-communication0.md#create-interactive-communication-for-web-channel) om **nu te nemen betaal** en **onderteken** hyperlinks in het kanaal van het Web van de Interactieve Mededeling.
