---
title: Formuliergegevensmodel maken
seo-title: Formuliergegevensmodel maken
description: Leer hoe te om modellen van vormgegevens met of zonder gevormde gegevensbronnen tot stand te brengen.
seo-description: Leer hoe te om modellen van vormgegevens met of zonder gevormde gegevensbronnen tot stand te brengen.
uuid: 5a94f733-0c08-41bb-983f-e7d34816d8fb
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
discoiquuid: 7c392909-ff84-4411-b44f-16f99dffac54
docset: aem65
translation-type: tm+mt
source-git-commit: 3226edb575de3d9f8bff53f5ca81e2957f37c544

---


# Formuliergegevensmodel maken{#create-form-data-model}

![](do-not-localize/data-integeration.png)

De gegevensintegratie van AEM Forms biedt een intuïtieve gebruikersinterface voor het maken van en werken met modellen van formuliergegevens. Een formuliergegevensmodel is gebaseerd op gegevensbronnen voor gegevensuitwisseling; u kunt echter wel een formuliergegevensmodel maken met of zonder gegevensbron. Er zijn twee benaderingen om van gegevensmodel afhankelijk van tot stand te brengen of u gegevensbronnen hebt gevormd:

* **Vooraf geconfigureerde gegevensbronnen** gebruiken: Als u gegevensbronnen hebt geconfigureerd zoals wordt beschreven in Gegevensbronnen [](../../forms/using/configure-data-sources.md)configureren, kunt u deze selecteren tijdens het maken van een formuliergegevensmodel. Hiermee worden alle gegevensmodelobjecten, eigenschappen en services van de geselecteerde gegevensbronnen beschikbaar gemaakt voor gebruik in het formuliergegevensmodel.

* **Zonder gegevensbronnen**: Als u geen gegevensbronnen hebt geconfigureerd voor uw formuliergegevensmodel, kunt u het nog steeds maken zonder gegevensbronnen. U kunt het gegevensmodel van het formulier gebruiken om adaptieve formulieren en interactieve communicatie te maken en deze te testen met behulp van voorbeeldgegevens. Wanneer gegevensbronnen beschikbaar zijn, kunt u het formuliergegevensmodel binden met gegevensbronnen, die automatisch worden weergegeven in de bijbehorende adaptieve formulieren en interactieve communicatie.

>[!NOTE]
>
>U moet lid zijn van zowel **fdm-auteur** als **formulieren-gebruiker** groepen om formuliergegevensmodel te kunnen maken en ermee te kunnen werken. Neem contact op met de AEM-beheerder om lid te worden van de groepen.

## Formuliergegevensmodel maken {#data-sources}

Zorg ervoor dat u de gegevensbronnen hebt geconfigureerd die u wilt gebruiken in het formuliergegevensmodel, zoals beschreven in Gegevensbronnen [](../../forms/using/configure-data-sources.md)configureren. Ga als volgt te werk om een formuliergegevensmodel te maken op basis van geconfigureerde gegevensbronnen:

1. Navigeer in de auteur van AEM naar **[!UICONTROL Formulieren > Gegevensintegratie]**.
1. Tik op **[!UICONTROL Maken > Formuliergegevensmodel]**.
1. In het dialoogvenster Formuliergegevensmodel maken:

   * Geef een naam op voor het gegevensmodel van het formulier.
   * (**Optioneel**) Geef een titel, beschrijving en codes op voor het formuliergegevensmodel.
   * (**Optioneel en alleen van toepassing als gegevensbronnen zijn geconfigureerd**) Tik op het tikpictogram naast het veld **[!UICONTROL Gegevensbronconfiguratie]** en selecteer het configuratieknooppunt waar de cloudservices voor de gegevensbronnen die u wilt gebruiken zich bevinden. Het beperkt de lijst van gegevensbronnen beschikbaar voor selectie op de volgende pagina tot degenen beschikbaar in de geselecteerde configuratieknooppunt. Alle gegevensbronnen van JDBC-databases en AEM-gebruikersprofielen worden standaard weergegeven. Als u geen configuratieknooppunt selecteert, worden de gegevensbronnen van alle configuratieknooppunten vermeld.
   Tik op **[!UICONTROL Volgende]**.

1. (**Toepasselijk slechts als de gegevensbronnen worden gevormd**) het **[!UICONTROL Uitgezochte scherm van de Gegevensbron]** maakt een lijst van beschikbare gegevensbronnen, als om het even welk. Selecteer gegevensbronnen die u wilt gebruiken in het formuliergegevensmodel.
1. Tik op **[!UICONTROL Maken]** en tik in het bevestigingsvenster op **[!UICONTROL Openen]** om de formuliergegevensmodeleditor te openen.

Laten we de verschillende componenten van de gebruikersinterface van de formuliergegevensmodel bekijken.

![Een formuliergegevensmodel met drie gegevensbronnen: een RESTful-service, een AEM-gebruikersprofiel en een RDBMS](assets/fdm-ui.png)

**A. Gegevensbronnen** Maakt een lijst van gegevensbronnen in een model van vormgegevens. Breid een gegevensbron uit om zijn voorwerpen en de diensten van het gegevensmodel te bekijken.

**B. Vernieuw de Definities** van de Gegevensbron Vetst om het even welke veranderingen in gegevensbrondefinities van gevormde gegevensbronnen en werkt hen op het Bronlusje van Gegevens van de modelredacteur van vormgegevens bij.

**C. Model** inhoudsgebied waar toegevoegde gegevensmodelvoorwerpen verschijnen.

**D. Het gebied van de Inhoud van de diensten** waar de toegevoegde gegevensbronverrichtingen of de diensten verschijnen.

**E. Gereedschappen op de werkbalk** voor het werken met het formuliergegevensmodel. Op de werkbalk ziet u meer opties, afhankelijk van het geselecteerde object in het formuliergegevensmodel.

**F. Hiermee voegt u geselecteerde** gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

Zie [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md)voor meer informatie over de formuliergegevensmodeleditor en hoe u ermee kunt werken om het formuliergegevensmodel te bewerken en te configureren.

## Gegevensbronnen bijwerken {#update}

Ga als volgt te werk om gegevensbronnen toe te voegen aan of bij te werken naar een bestaand formuliergegevensmodel.

1. Ga naar **[!UICONTROL Formulieren > Gegevensintegratie]**, selecteer het formuliergegevensmodel waarin u gegevensbronnen wilt toevoegen of bijwerken en tik op **[!UICONTROL Eigenschappen]**.
1. Ga in de eigenschappen van het formuliergegevensmodel naar het tabblad Bron **** bijwerken.

   Op het tabblad Bron bijwerken:

   * Tik op het bladerpictogram in het veld Configuratie **[!UICONTROL met]** behoud van context en selecteer een configuratieknooppunt waar de cloudconfiguratie voor de gegevensbron die u wilt toevoegen zich bevindt. Als u geen knoop selecteert, worden de wolkenconfiguraties die slechts in de `global` knoop verblijven vermeld wanneer u **[!UICONTROL Add Bronnen]** tikt.

   * Als u een nieuwe gegevensbron wilt toevoegen, tikt u op Bronnen **** toevoegen en selecteert u de gegevensbronnen die u aan het formuliergegevensmodel wilt toevoegen. Alle gegevensbronnen binnen gevormd `global` en de geselecteerde configuratieknooppunt, als om het even welk, worden getoond.

   * Tik op het pictogram **[!UICONTROL Bewerken]** voor de gegevensbron en selecteer een gegevensbron in de lijst met beschikbare gegevensbronnen om een bestaande gegevensbron te vervangen door een andere gegevensbron van hetzelfde type.
   * Tik op het pictogram **[!UICONTROL Verwijderen]** om een bestaande gegevensbron te verwijderen. Het pictogram Verwijderen is uitgeschakeld als een gegevensmodelobject in de gegevensbron wordt toegevoegd aan het formuliergegevensmodel.
   ![fdm-eigenschappen](assets/fdm-properties.png)

1. Tik op **[!UICONTROL Opslaan en sluiten]** om de updates op te slaan.

>[!NOTE]
>
>Nadat u nieuwe gegevensbronnen hebt toegevoegd of bestaande gegevensbronnen hebt bijgewerkt in een formuliergegevensmodel, zorgt u ervoor dat u de bindingsverwijzingen naar behoren bijwerkt in adaptieve formulieren en interactieve communicatie die gebruikmaken van het bijgewerkte formuliergegevensmodel.

## Volgende stappen {#next-steps}

U hebt nu een formuliergegevensmodel waaraan gegevensbronnen zijn toegevoegd. Vervolgens kunt u het gegevensmodel van het formulier bewerken om gegevensmodelobjecten en -services toe te voegen en te configureren, koppelingen tussen gegevensmodelobjecten toe te voegen, eigenschappen te bewerken, aangepaste gegevensmodelobjecten en -eigenschappen toe te voegen, voorbeeldgegevens te genereren, enzovoort.

Zie [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md)voor meer informatie.
