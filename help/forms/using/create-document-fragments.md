---
title: '"Zelfstudie: Documentfragmenten maken"'
seo-title: Documentfragmenten maken voor interactieve communicatie
description: Documentfragmenten maken voor interactieve communicatie
seo-description: Documentfragmenten maken voor interactieve communicatie
uuid: 677d717e-e92e-434e-8266-6fbbf94f3867
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8ae97a21-83af-4615-9be3-61e2f8065081
docset: aem65
translation-type: tm+mt
source-git-commit: e545fc5e2ea139bd8ebb7f84138ba68e03d71d19

---


# Zelfstudie: Documentfragmenten maken{#tutorial-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Deze zelfstudie is een stap in de [eerste interactieve communicatiereeks](/help/forms/using/create-your-first-interactive-communication.md) maken. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Documentfragmenten zijn herbruikbare componenten van een correspondentie die worden gebruikt om een interactieve communicatie samen te stellen. De documentfragmenten zijn van de volgende typen:

* Tekst - Een tekstelement is een stuk inhoud dat bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn.
* List - List is een groep documentfragmenten, waaronder tekst, lijsten, voorwaarden en afbeeldingen.
* Voorwaarde - De Voorwaarden laten u toe om te bepalen welke inhoud inbegrepen in Interactieve Mededeling wordt gebaseerd op de gegevens die van het Model van de Gegevens van het Vorm worden ontvangen.

Deze zelfstudie begeleidt u door de stappen om meerdere tekstdocumentfragmenten te maken op basis van de anatomie die in de sectie Interactieve communicatie [in](/help/forms/using/planning-interactive-communications.md) Plan is opgenomen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* Documentfragmenten maken
* Variabelen maken
* Regels maken en toepassen

![text_document_fragments](assets/text_document_fragments.gif)

Hier volgt een lijst met documentfragmenten die in deze zelfstudie worden gemaakt:

* [Details van facturering](../../forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [Klantgegevens](../../forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [Overzicht van Bill](../../forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [Overzicht van kosten](../../forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

Elk documentfragment bevat velden met statische tekst, gegevens die zijn ontvangen van het formuliergegevensmodel en gegevens die zijn ingevoerd met de gebruikersinterface van de agent. Al deze gebieden zijn getoond in het [Plan de Interactieve sectie van de Communicatie](/help/forms/using/planning-interactive-communications.md) .

Terwijl het creëren van documentfragmenten in dit leerprogramma, worden de variabelen gecreeerd voor gebieden die gegevens gebruikend de Agent UI ontvangen.

Gebruik **FDM_Create_First_IC**, zoals beschreven in de sectie [Formuliergegevensmodel](../../forms/using/create-form-data-model0.md) maken, als het formuliergegevensmodel om documentfragmenten in deze zelfstudie te maken.

## Stap 1: Tekstdocumentfragment Bill Details maken {#step-create-bill-details-text-document-fragment}

Het documentfragment Bill Details bevat de volgende velden:

| Veld | Gegevensbron |
|---|---|
| Factuurnummer | Gebruikersinterface van agent |
| Bill Period | Gebruikersinterface van agent |
| Bill Date | Gebruikersinterface van agent |
| Uw abonnement | Formuliergegevensmodel |

Voer de volgende stappen uit om variabelen voor gebieden met Agent UI als gegevensbron tot stand te brengen, statische teksten tot stand te brengen, en de modelelementen van het de vormgegevensmodel in het documentfragment te gebruiken:

1. Selecteer **[!UICONTROL Formulieren]** > **[!UICONTROL Documentfragmenten]**.

1. Selecteer **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Voer **bill_details_first_ic** in als naam in het veld **Titel** . De titel wordt automatisch ingevuld in het veld **Naam** .

   1. Selecteer **Formuliergegevensmodel** in de sectie **Gegevensmodel** .

   1. Selecteer **FDM_Create_First_IC** als het formuliergegevensmodel en tik op **Selecteren**.

   1. Tik op **Volgende**.

1. Selecteer het tabblad **Variabelen** in het linkerdeelvenster en tik op **Maken**.
1. In de sectie Variabele **maken** :

   1. Voer **Factuurnummer** in als de naam van de variabele.
   1. Selecteer **String** als type.
   1. Tik op **Maken**.
   ![Een variabele van het type String maken](assets/variable_create_string_new.png)

   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Billperiod: Het type String
   * BillDate: Het type Date
   ![Bill Details](assets/variable_bill_details_new.png)

1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Factuurnummer
   * Bill Period
   * Bill Date
   * Uw abonnement
   ![Statische tekst](assets/variable_bill_details_static_text_new.png)

1. Plaats de curseur naast het gebied van **Factuur Geen** en klik de variabele **InvoiceNumber** van het lusje van **Variabelen** in de linkerruit tweemaal.
1. Plaats de curseur naast het gebied van de Periode **van de** Rekening en klik de variabele **Billperiod** tweemaal.
1. Plaats de curseur naast het gebied van de Datum **van de** Rekening en klik de variabele van de Datum **van de** Rekening tweemaal.
1. Selecteer het tabblad **Gegevensmodelobjecten** in het linkerdeelvenster.
1. Plaats de curseur naast het **Uw gebied van het Plan** en klik de **klant** > **customerplan** bezit tweemaal.

   ![bill_details_customerplan_fdm](assets/bill_details_customerplan_fdm.png)

1. Klik op **Opslaan** om het tekstdocumentfragment Bill Details te maken.

## Stap 2: Tekstdocumentfragment voor klantgegevens maken {#step-create-customer-details-text-document-fragment}

Het documentfragment Customer Details bevat de volgende velden:

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

Voer de volgende stappen uit om variabelen voor gebieden met Agent UI als gegevensbron tot stand te brengen, statische teksten tot stand te brengen, en de modelelementen van het de vormgegevensmodel in het documentfragment te gebruiken:

1. Selecteer **[!UICONTROL Formulieren]** > **[!UICONTROL Documentfragmenten]**.
1. Selecteer **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Voer **customer_details_first_ic** in als naam in het veld **Titel** . De titel wordt automatisch ingevuld in het veld **Naam** .

   1. Selecteer **Formuliergegevensmodel** in de sectie **Gegevensmodel** .

   1. Selecteer **FDM_Create_First_IC** als het formuliergegevensmodel en tik op **Selecteren**.

   1. Tik op **Volgende**.

1. Selecteer het tabblad **Variabelen** in het linkerdeelvenster en tik op **Maken**.
1. In de sectie Variabele **maken** :

   1. Voer **Placesupply** in als de naam van de variabele.
   1. Selecteer **String** als type.
   1. Tik op **Maken**.
   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Statcode: Het type Number
   * Nummerverbindingen: Het type Number


1. Selecteer het tabblad **Gegevensmodelobjecten** , plaats de cursor in het rechterdeelvenster en dubbelklik op de eigenschap **klant** > **name** .
1. Druk op Enter om de cursor naar de volgende regel te verplaatsen en dubbelklik op de eigenschap **klant** > **address** .
1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Mobiel nummer
   * Alternatief contactnummer
   * Plaats van levering
   * Relatie-nummer
   * Statuscode
   * Aantal verbindingen
   ![Klantgegevens statische tekst](assets/customer_details_static_text_new.png)

1. Plaats de cursor naast het veld **Mobiel nummer** en dubbelklik op de eigenschap **klant** > **mobile** .
1. Plaats de cursor naast het veld **Alternatief contactnummer** en dubbelklik op de eigenschap** customer** > **alternobilenumber** .
1. Plaats de curseur naast het gebied van het Aantal **van de** Verhouding en klik het **klant** > **bezit van het** relatienummer tweemaal.
1. Selecteer het tabblad **Variabelen** , plaats de cursor naast het veld **Plaats van levering** en dubbelklik op de variabele **Plaatsing** .
1. Plaats de curseur naast het gebied van de Code **van de** Staat en klik de variabele **Statecode** tweemaal.
1. Plaats de cursor naast het veld **Aantal verbindingen** en dubbelklik op de variabele **Numberconnecties** .

   ![Klantgegevens](assets/customer_details_df2_new.png)

1. Klik op **Opslaan** om het tekstdocumentfragment Klantgegevens te maken.

## Stap 3: Samenvattingstekstdocumentfragment van Bill maken {#step-create-bill-summary-text-document-fragment}

Het fragment Bill Summary-document bevat de volgende velden:

| Veld | Gegevensbron |
|---|---|
| Vorig saldo | Gebruikersinterface van agent |
| Betalingen | Gebruikersinterface van agent |
| Aanpassingen | Gebruikersinterface van agent |
| Lopende factuurperiode | Formuliergegevensmodel |
| Te betalen bedrag | Gebruikersinterface van agent |
| Vervaldatum | Gebruikersinterface van agent |

Voer de volgende stappen uit om variabelen voor gebieden met Agent UI als gegevensbron tot stand te brengen, statische teksten tot stand te brengen, en de modelelementen van het de vormgegevensmodel in het documentfragment te gebruiken:

1. Selecteer **[!UICONTROL Formulieren]** > **[!UICONTROL Documentfragmenten]**.
1. Selecteer **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Voer **bill_summary_first_ic** in als naam in het veld **Titel** . De titel wordt automatisch ingevuld in het veld **Naam** .

   1. Selecteer **Formuliergegevensmodel** in de sectie **Gegevensmodel** .

   1. Selecteer **FDM_Create_First_IC** als het formuliergegevensmodel en tik op **Selecteren**.

   1. Tik op **Volgende**.

1. Selecteer het tabblad **Variabelen** in het linkerdeelvenster en tik op **Maken**.
1. In de sectie Variabele **maken** :

   1. Voer **Vorige balans** in als naam voor de variabele.
   1. Selecteer **Getal** als type.
   1. Tik op **Maken**.
   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Betalingen: Het type Number
   * Aanpassingen: Het type Number
   * Bedrag: Het type Number
   * Duur: Het type Date


1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Vorig saldo
   * Betalingen
   * Aanpassingen
   * Lopende factuurperiode
   * Te betalen bedrag
   * Vervaldatum
   * Betalingskosten na vervaldatum zijn $ 20
   ![Statische tekst Bill Summary](assets/bill_summary_static_new.png)

1. Plaats de cursor naast het veld **Vorige balans** en dubbelklik op de variabele **Vorige balans** .
1. Plaats de cursor naast het veld **Betalingen** en dubbelklik op de variabele **Betalingen** .
1. Plaats de cursor naast het veld **Aanpassingen** en dubbelklik op de variabele **Aanpassingen** .
1. Plaats de cursor naast het veld **Bedrag verschuldigd** en dubbelklik op de variabele **Bedrag** .
1. Plaats de cursor naast het veld **Einddatum** en dubbelklik op de variabele **Vervolgdatum** .
1. Selecteer het tabblad **Gegevensmodelobjecten** , plaats de cursor naast het veld **Laden voor huidige factuurperiode** in het rechtervenster en dubbelklik op de eigenschap **facturen** > **gebruiksrechten** .

   ![Overzicht van Bill](assets/bill_summary_static_variables_new.png)

1. Klik op **Opslaan** om het tekstdocumentfragment Klantgegevens te maken.

## Stap 4: Samenvatting maken van tekstdocumentfragment met ladingen {#step-create-summary-of-charges-text-document-fragment}

Het fragment Overzicht van ladingen bevat de volgende velden:

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

Voer de volgende stappen uit om statische tekst te maken en formuliergegevensmodelelementen in het documentfragment te gebruiken:

1. Selecteer **[!UICONTROL Formulieren]** > **[!UICONTROL Documentfragmenten]**.
1. Selecteer **Maken** > **Tekst**.
1. Geef de volgende informatie op:

   1. Voer in het veld **Titel** de naam **** summary_charges_first_ic in. De titel wordt automatisch ingevuld in het veld Naam.

   1. Selecteer **Formuliergegevensmodel** in de sectie **Gegevensmodel** .

   1. Selecteer **FDM_Create_First_IC** als het formuliergegevensmodel en tik op **Selecteren**.

   1. Tik op **Volgende**.

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

1. Selecteer het tabblad Objecten **gegevensmodel** .
1. Plaats de curseur naast het gebied van de Heffingen **van de** Vraag en klik de **rekeningen** > **callladingsbezit** tweemaal.
1. Plaats de curseur naast het gebied van de Heffingen **van de Vraag van de** Conferentie en klik de **rekeningen** > **confcallladings** bezit tweemaal.
1. Plaats de cursor naast het veld **SMS-kosten** en dubbelklik op de eigenschap **Bill** > **smrages** .
1. Plaats de curseur naast het **Mobiele gebied van de Tarieven** van Internet en klik de **rekeningen** > **onderlinge verbindings van netwerkenbezit** tweemaal.
1. Plaats de cursor naast het veld **Nationale roamingkosten** en dubbelklik op de **facturen** > **roamingnationale** eigenschap.
1. Plaats de cursor naast het veld **Internationale zwervende kosten** en dubbelklik op de **facturen** > **roamingintleigenschap** .
1. Plaats de curseur naast het gebied van de Kosten **van de Diensten van de** Waarde Toegevoegde en klik de **rekeningen** > **vasbezit** tweemaal.
1. Plaats de cursor naast het veld **Totale kosten** en dubbelklik op de eigenschap **facturen** > **gebruiksrechten** .
1. Plaats de cursor naast het veld **TOTAAL BETAALBAAR** en dubbelklik op de eigenschap **factureren** > **gebruiksheffingen** .

   ![Overzicht van heffingen](assets/summary_charges_static_fdm_new.png)

1. Selecteer de tekst in de **Waarde toegevoegde de rij van de Laden** van de Diensten en tik **Create Regel** om een voorwaarde tot stand te brengen die waarop de rij in Interactieve Mededeling wordt getoond:
1. In het pop-upvenster Regel **** maken:

   1. Selecteer **Gegevensmodellen en Variabelen** en dan **rekeningen** > **callloads**.

   1. Selecteren **is kleiner dan** de operator.
   1. Selecteer **Aantal** en ga de waarde als **60** in.
   Gebaseerd op deze voorwaarde, wordt de rij van de Heffingen van de Diensten van de Waarde Toegevoegde getoond slechts als de waarde voor het gebied van de Heffingen van de Vraag minder dan 60 is.

   ![create_rules_caption](assets/create_rules_caption.gif)

1. Klik op **Opslaan** om het fragment Overzicht van ladingen voor het tekstdocument te maken.
