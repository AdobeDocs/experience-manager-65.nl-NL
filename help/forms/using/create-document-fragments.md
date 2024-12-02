---
title: 'Zelfstudie: documentfragmenten maken'
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

![ 05-create-form-data-model-main_small ](assets/05-create-form-data-model-main_small.png)

Dit leerprogramma is een stap in [ creeer uw eerste Interactieve Communicatie ](/help/forms/using/create-your-first-interactive-communication.md) reeks. De Adobe raadt u aan de reeks in chronologische volgorde te volgen om de volledige Gebruikszaak van de zelfstudie te begrijpen, uit te voeren en te demonstreren.

Documentfragmenten zijn herbruikbare componenten van een correspondentie die worden gebruikt om een interactieve communicatie samen te stellen. De documentfragmenten zijn van de volgende typen:

* Tekst - Een tekstelement is een stuk inhoud dat bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn.
* List - List is een groep documentfragmenten, waaronder tekst, lijsten, voorwaarden en afbeeldingen.
* Voorwaarde - De Voorwaarden laten u toe om te bepalen welke inhoud inbegrepen in Interactieve Mededeling wordt gebaseerd op de gegevens die van het Model van de Gegevens van het Vorm worden ontvangen.

Dit leerprogramma begeleidt u door de stappen om veelvoudige die fragmenten tot stand te brengen van het tekstdocument op de anatomie in [ wordt verstrekt Plan de Interactieve Communicatie ](/help/forms/using/planning-interactive-communications.md) sectie die. Aan het einde van deze zelfstudie moet u het volgende kunnen doen:

* Documentfragmenten maken
* Variabelen maken
* Regels maken en toepassen

![ text_document_fragments ](assets/text_document_fragments.gif)

Hier volgt een lijst met documentfragmenten die in deze zelfstudie worden gemaakt:

* [Bill details](../../forms/using/create-document-fragments.md#step-create-bill-details-text-document-fragment)
* [Klantgegevens](../../forms/using/create-document-fragments.md#step-create-customer-details-text-document-fragment)
* [Overzicht van Bill](../../forms/using/create-document-fragments.md#step-create-bill-summary-text-document-fragment)
* [Overzicht van kosten](../../forms/using/create-document-fragments.md#step-create-summary-of-charges-text-document-fragment)

Elk documentfragment bevat velden met statische tekst, gegevens die zijn ontvangen van het formuliergegevensmodel en gegevens die zijn ingevoerd met de gebruikersinterface van de agent. Al deze gebieden zijn afgebeeld in het [ Plan de Interactieve Communicatie ](/help/forms/using/planning-interactive-communications.md) sectie.

Terwijl het creëren van documentfragmenten in dit leerprogramma, worden de variabelen gecreeerd voor gebieden die gegevens gebruikend de Agent UI ontvangen.

Het gebruik **FDM_Create_First_IC**, zoals die in [ wordt beschreven leidt het model van vormgegevens ](../../forms/using/create-form-data-model0.md) sectie, als model van vormgegevens om documentfragmenten in dit leerprogramma tot stand te brengen.

## Stap 1: Create Bill Details text Document Fragment {#step-create-bill-details-text-document-fragment}

Het fragment Document Bill Details bevat de volgende velden:

| Veld | Data Source |
|---|---|
| Factuurnummer | Gebruikersinterface van agent |
| Bill Period | Gebruikersinterface van agent |
| Bill Date | Gebruikersinterface van agent |
| Uw abonnement | Formuliergegevensmodel |

Ga als volgt te werk om variabelen voor velden te maken met de gebruikersinterface van de Agent als gegevensbron, statische tekst te maken en elementen van het formuliergegevensmodel in het documentfragment te gebruiken:

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]** .

1. Selecteer **creëren** > **Tekst**.
1. Geef de volgende informatie op:

   1. Ga **bill_details_first_ic** als naam op het **gebied van de Titel** in. De titel wordt auto-bevolkt op het **gebied van de Naam**.

   1. Selecteer **Model van de Gegevens van de Vorm** van de **sectie van het Model van Gegevens**.

   1. Selecteer **FDM_Create_First_IC** als model van vormgegevens en selecteer **Uitgezocht**.

   1. Selecteer **daarna**.

1. Selecteer het **lusje van Variabelen** in de linkerruit en selecteer **creeer**.
1. In **creeer Variabele** sectie:

   1. Ga **InvoiceNumber** als naam van de variabele in.
   1. Selecteer **Koord** als type.
   1. Selecteer **creeer**.

   ![ creeer variabele van het type van Koord ](assets/variable_create_string_new.png)

   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Billperiod: Het type String
   * BillDate: type Date

   ![ de Details van de Rekening ](assets/variable_bill_details_new.png)

1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Factuurnummer
   * Bill Period
   * Bill Date
   * Uw abonnement

   ![ Statische teksten ](assets/variable_bill_details_static_text_new.png)

1. Plaats de curseur naast het **Factuur Nr** gebied en klik de **InvoiceNumber** variabele van het **** lusje van Variabelen {in de linkerruit tweemaal.
1. Plaats de curseur naast het **gebied van de Periode van de Rekening** en klik de **Billperiod** variabele tweemaal.
1. Plaats de curseur naast het **gebied van de Datum van de Rekening** en klik de **Datum van de Rekening** variabele tweemaal.
1. Selecteer het **ModelVoorwerpen van Gegevens** lusje in de linkerruit.
1. Plaats de curseur naast het **Uw gebied van het Plan** en klik de **klant** > **klant** bezit tweemaal.

   ![ rekening_details_customerplan_fdm ](assets/bill_details_customerplan_fdm.png)

1. Klik **sparen** om het de tekstfragment van het Document van Details van de Rekening tot stand te brengen.

## Stap 2: Maak een tekstdocumentfragment voor klantgegevens {#step-create-customer-details-text-document-fragment}

Het fragment Document met klantgegevens bevat de volgende velden:

| Veld | Data Source |
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

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]** .
1. Selecteer **creëren** > **Tekst**.
1. Geef de volgende informatie op:

   1. Ga **customer_details_first_ic** als naam op het **gebied van de Titel** in. De titel wordt auto-bevolkt op het **gebied van de Naam**.

   1. Selecteer **Model van de Gegevens van de Vorm** van de **sectie van het Model van Gegevens**.

   1. Selecteer **FDM_Create_First_IC** als model van vormgegevens en selecteer **Uitgezocht**.

   1. Selecteer **daarna**.

1. Selecteer het **lusje van Variabelen** in de linkerruit en selecteer **creeer**.
1. In **creeer Variabele** sectie:

   1. Ga **Plaatsbepaling** als naam van de variabele in.
   1. Selecteer **Koord** als type.
   1. Selecteer **creeer**.

   Herhaal stap 4 en 5 om de volgende variabelen te maken:

   * Statecode: type Number
   * Numberconnecties: type Number

1. Selecteer het **ModelVoorwerpen van Gegevens** lusje, plaats de curseur in de juiste ruit, en klik de **klant** tweemaal > **naam** bezit.
1. De pers gaat binnen om de curseur aan de volgende lijn te bewegen en **klant** tweemaal te klikken > **adres** bezit.
1. Maak statische tekst voor de volgende velden met behulp van het rechterdeelvenster:

   * Mobiel nummer
   * Alternatief contactnummer
   * Plaats van levering
   * Relatie-nummer
   * Statuscode
   * Aantal verbindingen

   ![ de details van de Klant statische teksten ](assets/customer_details_static_text_new.png)

1. Plaats de curseur naast het **Mobiele gebied van het Aantal** en klik de **klant** > **mobiel** bezit tweemaal.
1. Plaats de curseur naast het **Afwisselende 1} gebied van het Aantal van het Contact {en klik het** klant** >** afwisselend enumber **bezit tweemaal.**
1. Plaats de curseur naast het **gebied van het Aantal van de Verhouding 0} {en klik de** klant **>** verhouding aantal **bezit tweemaal.**
1. Selecteer het **lusje van Variabelen**, plaats de curseur naast de **Plaats van het gebied van de Levering** en klik de **Placesupply** variabele tweemaal.
1. Plaats de curseur naast het **gebied van de Code van de Staat 0} en klik de** **variabele Statecode tweemaal.**
1. Plaats de curseur naast het **Aantal Verbindingen** gebied en klik de **variabele van Numberconnections** tweemaal.

   ![ de details van de Klant ](assets/customer_details_df2_new.png)

1. Klik **sparen** om het de tekstfragment van het Document van de Details van de Klant te creëren.

## Stap 3: Samenvattingstekstdocumentfragment maken {#step-create-bill-summary-text-document-fragment}

Het fragment Bill Summary Document bevat de volgende velden:

| Veld | Data Source |
|---|---|
| Vorig saldo | Gebruikersinterface van agent |
| Betalingen | Gebruikersinterface van agent |
| Aanpassingen | Gebruikersinterface van agent |
| Lopende factuurperiode | Formuliergegevensmodel |
| Te betalen bedrag | Gebruikersinterface van agent |
| Vervaldatum | Gebruikersinterface van agent |

Ga als volgt te werk om variabelen voor velden te maken met de gebruikersinterface van de Agent als gegevensbron, statische tekst te maken en elementen van het formuliergegevensmodel in het documentfragment te gebruiken:

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]** .
1. Selecteer **creëren** > **Tekst**.
1. Geef de volgende informatie op:

   1. Ga **bill_summary_first_ic** als naam op het **gebied van de Titel** in. De titel wordt auto-bevolkt op het **gebied van de Naam**.

   1. Selecteer **Model van de Gegevens van de Vorm** van de **sectie van het Model van Gegevens**.

   1. Selecteer **FDM_Create_First_IC** als model van vormgegevens en selecteer **Uitgezocht**.

   1. Selecteer **daarna**.

1. Selecteer het **lusje van Variabelen** in de linkerruit en selecteer **creeer**.
1. In **creeer Variabele** sectie:

   1. Ga **Previousbalance** als naam van de variabele in.
   1. Selecteer **Aantal** als type.
   1. Selecteer **creeer**.

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

   ![ de Samenvattende statische tekst van de Rekening ](assets/bill_summary_static_new.png)

1. Plaats de curseur naast het **Vorige gebied van het Saldo** en klik de **Previousbalance** variabele tweemaal.
1. Plaats de curseur naast het **gebied van Betalingen** en klik de **variabele van Betalingen** tweemaal.
1. Plaats de curseur naast het **gebied van Aanpassingen** en klik de **variabele van Aanpassingen** tweemaal.
1. Plaats de curseur naast het **Gelverschuldigd Bedrag** gebied en klik de **Gemate** variabele tweemaal.
1. Plaats de curseur naast het **Vereiste gebied van de Datum** en klik **duid** variabele tweemaal.
1. Selecteer het **ModelVoorwerpen van Gegevens** lusje, plaats de curseur naast het **gebied van de laden huidige factureringsperiode** in de juiste ruit, en klik de **rekeningen** tweemaal > **gebruiksheffingen** bezit.

   ![ Overzicht van de Rekening ](assets/bill_summary_static_variables_new.png)

1. Klik **sparen** om het de tekstfragment van het Document van de Details van de Klant te creëren.

## Stap 4: Samenvatting van ladingen maken tekstfragment Document {#step-create-summary-of-charges-text-document-fragment}

Het fragment Overzicht van ladingen Document bevat de volgende velden:

| Veld | Data Source |
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

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]** .
1. Selecteer **creëren** > **Tekst**.
1. Geef de volgende informatie op:

   1. Ga **summary_charges_first_ic** als naam op het **gebied van de Titel** in. De titel wordt automatisch ingevuld in het veld Naam.

   1. Selecteer **Model van de Gegevens van de Vorm** van de **sectie van het Model van Gegevens**.

   1. Selecteer **FDM_Create_First_IC** als model van vormgegevens en selecteer **Uitgezocht**.

   1. Selecteer **daarna**.

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

   ![ Summiere Tarieven ](assets/summary_charges_static_new.png)

1. Selecteer de **Modelvoorwerpen van Gegevens** tabel.
1. Plaats de curseur naast het **gebied van de Heffingen van de Vraag** en klik de **rekeningen** > **callladings** bezit tweemaal.
1. Plaats de curseur naast het **gebied van de Vraag van de 1} Conferentie laden van de Vraag en klik de** rekeningen **>** confcallladings **bezit tweemaal.**
1. Plaats de curseur naast het **gebied van de Heffingen van SMS** en dubbelklik de **rekeningen** > **smaakten** bezit.
1. Plaats de curseur naast het **gebied van de Tarieven van 0} Mobiel Internet en klik de** rekeningen **>** onderlinge verbindings van netwerkenlasten **bezit tweemaal.**
1. Plaats de curseur naast het **Nationale Roaming Charges** gebied en klik de **rekeningen** > **roamingnational** bezit tweemaal.
1. Plaats de curseur naast het **Internationale Roaming Charges** gebied en klik de **rekeningen** > **roamingintnl** bezit tweemaal.
1. Plaats de curseur naast de **Waarde Toegevoegde het gebied van de Lasten van de Diensten** en dubbelklik de **rekeningen** > **vas** bezit.
1. Plaats de curseur naast het **Volledige gebied van Heffingen** en klik de **rekeningen** > **gebruiksheffingen** bezit tweemaal.
1. Plaats de curseur naast het **TOTALE BETAALBARE** gebied en klik de **rekeningen** > **gebruiksheffingen** bezit tweemaal.

   ![ Samenvatting van Tarieven ](assets/summary_charges_static_fdm_new.png)

1. Selecteer de tekst in de **rij van de Diensten van de Waarde Toegevoegde** en uitgezocht **creeer Regel** om een voorwaarde tot stand te brengen die op wordt gebaseerd waarop de rij in de Interactieve Mededeling wordt getoond:
1. Op **creeer regel** pop-up venster:

   1. Selecteer **Modellen van Gegevens en Variabelen** en dan **rekeningen** > **callloads**.

   1. Selecteer **is minder dan** als exploitant.
   1. Selecteer **Aantal** en ga de waarde als **60** in.

   Gebaseerd op deze voorwaarde, wordt de rij van de Heffingen van de Diensten van de Waarde Toegevoegde getoond slechts als de waarde voor het gebied van de Heffingen van de Vraag minder dan 60 is.

   ![ create_rules_caption ](assets/create_rules_caption.gif)

1. Klik **sparen** om de Samenvatting van het Fragment van het Document van de ladingstekst tot stand te brengen.
