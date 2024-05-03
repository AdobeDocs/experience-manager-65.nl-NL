---
title: "Lesbestand: documentfragmenten maken"
description: Documentfragmenten maken voor interactieve communicatie
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 81429735-cd52-4621-8dc2-10dd89df3052
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1641'
ht-degree: 0%

---

# Zelfstudie: documentfragmenten maken{#tutorial-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Deze zelfstudie is een stap in de [Maak uw eerste interactieve communicatie](/help/forms/using/create-your-first-interactive-communication.md) reeks. De Adobe raadt u aan de reeks in chronologische volgorde te volgen om de volledige Gebruikszaak van de zelfstudie te begrijpen, uit te voeren en te demonstreren.

Documentfragmenten zijn herbruikbare componenten van een correspondentie die worden gebruikt om een interactieve communicatie samen te stellen. De documentfragmenten zijn van de volgende typen:

* Tekst - Een tekstelement is een stuk inhoud dat bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn.
* List - List is een groep documentfragmenten, waaronder tekst, lijsten, voorwaarden en afbeeldingen.
* Voorwaarde - De Voorwaarden laten u toe om te bepalen welke inhoud inbegrepen in Interactieve Mededeling wordt gebaseerd op de gegevens die van het Model van de Gegevens van het Vorm worden ontvangen.

In deze zelfstudie worden de stappen doorlopen waarmee u meerdere tekstdocumentfragmenten kunt maken op basis van de anatomie die in [De interactieve communicatie plannen](/help/forms/using/planning-interactive-communications.md) sectie. Aan het einde van deze zelfstudie moet u het volgende kunnen doen:

* Documentfragmenten maken
* Variabelen maken
* Regels maken en toepassen

![text_document_fragments](assets/text_document_fragments.gif)

Hier volgt een lijst met documentfragmenten die in deze zelfstudie worden gemaakt:

* [Bill details](../../forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [Klantgegevens](../../forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [Overzicht van Bill](../../forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [Overzicht van kosten](../../forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

Elk documentfragment bevat velden met statische tekst, gegevens die zijn ontvangen van het formuliergegevensmodel en gegevens die zijn ingevoerd met de gebruikersinterface van de agent. Al deze velden zijn weergegeven in het dialoogvenster [De interactieve communicatie plannen](/help/forms/using/planning-interactive-communications.md) sectie.

Terwijl het creëren van documentfragmenten in dit leerprogramma, worden de variabelen gecreeerd voor gebieden die gegevens gebruikend de Agent UI ontvangen.

Gebruiken **FDM_Create_First_IC**, zoals beschreven in de [Formuliergegevensmodel maken](../../forms/using/create-form-data-model0.md) als het formuliergegevensmodel voor het maken van documentfragmenten in deze zelfstudie.

## Stap 1: Create Bill Details text Document Fragment {#step-create-bill-details-text-document-fragment}

Het fragment Document Bill Details bevat de volgende velden:

| Veld | Gegevensbron |
|---|---|
| Factuurnummer | Gebruikersinterface van agent |
| Bill Period | Gebruikersinterface van agent |
| Bill Date | Gebruikersinterface van agent |
| Uw abonnement | Formuliergegevensmodel |

Ga als volgt te werk om variabelen voor velden te maken met de gebruikersinterface van de Agent als gegevensbron, statische tekst te maken en elementen van het formuliergegevensmodel in het documentfragment te gebruiken:

1. Selecteren **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.

1. Selecteren **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Enter **bill_details_first_ic** als de naam in het dialoogvenster **Titel** veld. De titel wordt automatisch ingevuld in het dialoogvenster **Naam** veld.

   1. Selecteren **Formuliergegevensmodel** van de **Gegevensmodel** sectie.

   1. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Selecteren**.

   1. Selecteren **Volgende**.

1. Selecteer de **Variabelen** in het linkerdeelvenster en selecteert u **Maken**.
1. In de **Variabele maken** sectie:

   1. Enter **Factuurnummer** als de naam van de variabele.
   1. Selecteren **String** als het type.
   1. Selecteren **Maken**.

   ![Een variabele van het type String maken](assets/variable_create_string_new.png)

   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Billperiod: Het type String
   * BillDate: type Date

   ![Bill Details](assets/variable_bill_details_new.png)

1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Factuurnummer
   * Bill Period
   * Bill Date
   * Uw abonnement

   ![Statische tekst](assets/variable_bill_details_static_text_new.png)

1. Plaats de cursor naast de **Factuurnummer** en dubbelklik op de knop **InvoiceNumber** variabele uit de **Variabelen** in het linkerdeelvenster.
1. Plaats de cursor naast de **Bill Period** en dubbelklik op de knop **Billperiod** variabele.
1. Plaats de cursor naast de **Bill Date** en dubbelklik op de knop **Bill Date** variabele.
1. Selecteer de **Gegevensmodelobjecten** in het linkerdeelvenster.
1. Plaats de cursor naast de **Uw abonnement** en dubbelklik op de knop **klant** > **klantplan** eigenschap.

   ![bill_details_customerplan_fdm](assets/bill_details_customerplan_fdm.png)

1. Klikken **Opslaan** om het tekstdocumentfragment Bill Details te maken.

## Stap 2: Maak een tekstdocumentfragment voor klantgegevens {#step-create-customer-details-text-document-fragment}

Het fragment Document met klantgegevens bevat de volgende velden:

| Veld | Gegevensbron |
|---|---|
| Naam klant | Formuliergegevensmodel |
| Adres | Formuliergegevensmodel |
| Plaats van levering | Gebruikersinterface van agent |
| Statuscode | Gebruikersinterface van agent |
| Mobiel nummer | Formuliergegevensmodel |
| Alternatief contactnummer | Formuliergegevensmodel |
| Relatie-nummer | Formuliergegevensmodel |
| Aantal verbindingen | Gebruikersinterface van agent |

Ga als volgt te werk om variabelen voor velden te maken met de gebruikersinterface van de Agent als gegevensbron, statische tekst te maken en elementen van het formuliergegevensmodel in het documentfragment te gebruiken:

1. Selecteren **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Selecteren **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Enter **customer_details_first_ic** als de naam in het dialoogvenster **Titel** veld. De titel wordt automatisch ingevuld in het dialoogvenster **Naam** veld.

   1. Selecteren **Formuliergegevensmodel** van de **Gegevensmodel** sectie.

   1. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Selecteren**.

   1. Selecteren **Volgende**.

1. Selecteer de **Variabelen** in het linkerdeelvenster en selecteert u **Maken**.
1. In de **Variabele maken** sectie:

   1. Enter **Plaatslevering** als de naam van de variabele.
   1. Selecteren **String** als het type.
   1. Selecteren **Maken**.

   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Statecode: type Number
   * Numberconnecties: type Number

1. Selecteer de **Gegevensmodelobjecten** , plaatst u de cursor in het rechterdeelvenster en dubbelklikt u op de knop **klant** > **name** eigenschap.
1. Druk op Enter om de cursor naar de volgende regel te verplaatsen en dubbelklik op de knop **klant** > **adres** eigenschap.
1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Mobiel nummer
   * Alternatief contactnummer
   * Plaats van levering
   * Relatie-nummer
   * Statuscode
   * Aantal verbindingen

   ![Klantgegevens statische tekst](assets/customer_details_static_text_new.png)

1. Plaats de cursor naast de **Mobiel nummer** en dubbelklik op de knop **klant** > **mobilenum** eigenschap.
1. Plaats de cursor naast de **Alternatief contactnummer** veld en dubbelklik op de** klant** > **alternatemobilenumber** eigenschap.
1. Plaats de cursor naast de **Relatie-nummer** en dubbelklik op de knop **klant** > **relatienummer** eigenschap.
1. Selecteer de **Variabelen** tab, plaats de cursor naast de **Plaats van levering** en dubbelklik op de knop **Plaatslevering** variabele.
1. Plaats de cursor naast de **Statuscode** en dubbelklik op de knop **Statecode** variabele.
1. Plaats de cursor naast de **Aantal verbindingen** en dubbelklik op de knop **Numberverbindingen** variabele.

   ![Klantgegevens](assets/customer_details_df2_new.png)

1. Klikken **Opslaan** om het tekstdocumentfragment Klantgegevens te maken.

## Stap 3: Samenvattingstekstdocumentfragment maken {#step-create-bill-summary-text-document-fragment}

Het fragment Bill Summary Document bevat de volgende velden:

| Veld | Gegevensbron |
|---|---|
| Vorig saldo | Gebruikersinterface van agent |
| Betalingen | Gebruikersinterface van agent |
| Aanpassingen | Gebruikersinterface van agent |
| Lopende factuurperiode | Formuliergegevensmodel |
| Te betalen bedrag | Gebruikersinterface van agent |
| Vervaldatum | Gebruikersinterface van agent |

Ga als volgt te werk om variabelen voor velden te maken met de gebruikersinterface van de Agent als gegevensbron, statische tekst te maken en elementen van het formuliergegevensmodel in het documentfragment te gebruiken:

1. Selecteren **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Selecteren **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Enter **bill_summary_first_ic** als de naam in het dialoogvenster **Titel** veld. De titel wordt automatisch ingevuld in het dialoogvenster **Naam** veld.

   1. Selecteren **Formuliergegevensmodel** van de **Gegevensmodel** sectie.

   1. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Selecteren**.

   1. Selecteren **Volgende**.

1. Selecteer de **Variabelen** in het linkerdeelvenster en selecteert u **Maken**.
1. In de **Variabele maken** sectie:

   1. Enter **Vorige balans** als de naam van de variabele.
   1. Selecteren **Getal** als type.
   1. Selecteren **Maken**.

   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Betalingen: Number-type
   * Adjustments: Number type
   * Bedrag: type Number
   * Duedate: Het type Date

1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Vorig saldo
   * Betalingen
   * Aanpassingen
   * Lopende factuurperiode
   * Te betalen bedrag
   * Vervaldatum
   * Te late betalingskosten na de vervaldatum zijn $ 20

   ![Statische tekst van Bill Summary](assets/bill_summary_static_new.png)

1. Plaats de cursor naast de **Vorig saldo** en dubbelklik op de knop **Vorige balans** variabele.
1. Plaats de cursor naast de **Betalingen** en dubbelklik op de knop **Betalingen** variabele.
1. Plaats de cursor naast de **Aanpassingen** en dubbelklik op de knop **Aanpassingen** variabele.
1. Plaats de cursor naast de **Te betalen bedrag** en dubbelklik op de knop **Bedrag** variabele.
1. Plaats de cursor naast de **Vervaldatum** en dubbelklik op de knop **Duedate** variabele.
1. Selecteer de **Gegevensmodelobjecten** tab, plaats de cursor naast de **Lopende factuurperiode** in het rechterdeelvenster en dubbelklik op het pictogram **biljet** > **gebruikskosten** eigenschap.

   ![Overzicht van Bill](assets/bill_summary_static_variables_new.png)

1. Klikken **Opslaan** om het tekstdocumentfragment Klantgegevens te maken.

## Stap 4: Samenvatting van ladingen maken tekstfragment Document {#step-create-summary-of-charges-text-document-fragment}

Het fragment Overzicht van ladingen Document bevat de volgende velden:

| Veld | Gegevensbron |
|---|---|
| Oproepkosten | Formuliergegevensmodel |
| Kosten voor conferentiegesprek | Formuliergegevensmodel |
| SMS-kosten | Formuliergegevensmodel |
| Mobiele internetkosten | Formuliergegevensmodel |
| Nationale roamingkosten | Formuliergegevensmodel |
| Internationale roamingkosten | Formuliergegevensmodel |
| Kosten voor toegevoegde services | Formuliergegevensmodel |
| Totale kosten | Formuliergegevensmodel |
| TOTAAL BETAALBAAR | Formuliergegevensmodel |

Ga als volgt te werk om statische tekst te maken en elementen van het formuliergegevensmodel in het documentfragment te gebruiken:

1. Selecteren **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Selecteren **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Enter **summary_charges_first_ic** als de naam in het dialoogvenster **Titel** veld. De titel wordt automatisch ingevuld in het veld Naam.

   1. Selecteren **Formuliergegevensmodel** van de **Gegevensmodel** sectie.

   1. Selecteren **FDM_Create_First_IC** als het formuliergegevensmodel en selecteer **Selecteren**.

   1. Selecteren **Volgende**.

1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Oproepkosten
   * Kosten voor conferentiegesprek
   * SMS-kosten
   * Mobiele internetkosten
   * Nationale roamingkosten
   * Internationale roamingkosten
   * Kosten voor toegevoegde services
   * Totale kosten
   * TOTAAL BETAALBAAR

   ![Samenvattingskosten](assets/summary_charges_static_new.png)

1. Selecteer de **Gegevensmodelobjecten** tab.
1. Plaats de cursor naast de **Oproepkosten** en dubbelklik op de knop **biljet** > **opvragingskosten** eigenschap.
1. Plaats de cursor naast de **Kosten voor conferentiegesprek** en dubbelklik op de knop **biljet** > **samenvattingskosten** eigenschap.
1. Plaats de cursor naast de **SMS-kosten** en dubbelklik op de knop **biljet** > **schaarste** eigenschap.
1. Plaats de cursor naast de **Mobiele internetkosten** en dubbelklik op de knop **biljet** > **onderlinge verbinding** eigenschap.
1. Plaats de cursor naast de **Nationale roamingkosten** en dubbelklik op de knop **biljet** > **landelijk** eigenschap.
1. Plaats de cursor naast de **Internationale roamingkosten** en dubbelklik op de knop **biljet** > **roamingintnl** eigenschap.
1. Plaats de cursor naast de **Kosten voor toegevoegde services** en dubbelklik op de knop **biljet** > **vas** eigenschap.
1. Plaats de cursor naast de **Totale kosten** en dubbelklik op de knop **biljet** > **gebruikskosten** eigenschap.
1. Plaats de cursor naast de **TOTAAL BETAALBAAR** en dubbelklik op de knop **biljet** > **gebruikskosten** eigenschap.

   ![Overzicht van heffingen](assets/summary_charges_static_fdm_new.png)

1. Selecteer de tekst in het dialoogvenster **Kosten voor toegevoegde services** rij en selecteer **Regel maken** om een voorwaarde tot stand te brengen die waarop de rij in Interactieve Mededeling wordt getoond:
1. Op de **Regel maken** pop-upvenster:

   1. Selecteren **Gegevensmodellen en variabelen** en vervolgens **biljet** > **opvragingskosten**.

   1. Selecteren **is kleiner dan** als de operator.
   1. Selecteren **Getal** en voer de waarde in als **60**.

   Gebaseerd op deze voorwaarde, wordt de rij van de Heffingen van de Diensten van de Waarde Toegevoegde getoond slechts als de waarde voor het gebied van de Heffingen van de Vraag minder dan 60 is.

   ![create_rules_caption](assets/create_rules_caption.gif)

1. Klikken **Opslaan** Hiermee maakt u de samenvatting van ladingstekstfragmenten.
