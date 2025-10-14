---
title: Formuliergegevensmodel maken
description: Leer hoe te om modellen van vormgegevens met of zonder gevormde gegevensbronnen te creëren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
docset: aem65
feature: Form Data Model
exl-id: 7f5978c3-6c9f-4ce4-b0fb-660ac1d49244
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# Formuliergegevensmodel maken{#create-form-data-model}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


![&#x200B; held-beeld &#x200B;](do-not-localize/data-integration.png)

AEM Forms-gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Een formuliergegevensmodel is gebaseerd op gegevensbronnen voor gegevensuitwisseling. U kunt echter wel een formuliergegevensmodel maken met of zonder gegevensbron. Er zijn twee benaderingen om van gegevensmodel afhankelijk van tot stand te brengen of u gegevensbronnen hebt gevormd:

* **Gebruikend preconfigured gegevensbronnen**: Als u gegevensbronnen zoals die in [&#x200B; worden beschreven vormt gegevensbronnen &#x200B;](../../forms/using/configure-data-sources.md), kunt u hen selecteren terwijl het creëren van een model van vormgegevens. Hiermee worden alle gegevensmodelobjecten, eigenschappen en services van de geselecteerde gegevensbronnen beschikbaar gemaakt voor gebruik in het formuliergegevensmodel.

* **Zonder gegevensbronnen**: Als u geen gegevensbronnen voor uw model van vormgegevens hebt gevormd, kunt u het zonder gegevensbronnen nog tot stand brengen. U kunt het gegevensmodel van het formulier gebruiken om adaptieve formulieren en interactieve communicatie te maken en deze te testen met behulp van voorbeeldgegevens. Wanneer gegevensbronnen beschikbaar zijn, kunt u het formuliergegevensmodel binden met gegevensbronnen, die automatisch worden weergegeven in de bijbehorende adaptieve formulieren en interactieve communicatie.

>[!NOTE]
>
>U moet een lid van zowel **fdm-auteur** en **vormen-gebruiker** groepen zijn om met het model van vormgegevens te kunnen tot stand brengen en werken. Neem contact op met de AEM beheerder om lid te worden van de groepen.

## Formuliergegevensmodel maken {#data-sources}

Zorg ervoor dat u de gegevensbronnen hebt gevormd u in het model van vormgegevens wilt gebruiken zoals die in [&#x200B; worden beschreven vormt gegevensbronnen &#x200B;](../../forms/using/configure-data-sources.md). Ga als volgt te werk om een formuliergegevensmodel te maken op basis van geconfigureerde gegevensbronnen:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms > Data Integrations]** .
1. Selecteer **[!UICONTROL Create > Form Data Model]** .
1. In het dialoogvenster Formuliergegevensmodel maken:

   * Geef een naam op voor het gegevensmodel van het formulier.
   * (**Facultatieve**) specificeer titel, beschrijving, en markeringen voor het model van vormgegevens.
   * (**Facultatief en van toepassing slechts als de gegevensbronnen** worden gevormd) selecteer het tikpictogram naast het **[!UICONTROL Data Source Configuration]** gebied en selecteer de configuratieknoop waar de wolkendiensten voor de gegevensbronnen u wilt gebruiken verblijven. Het beperkt de lijst van gegevensbronnen beschikbaar voor selectie op de volgende pagina tot degenen beschikbaar in de geselecteerde configuratieknoop. Alle JDBC-database- en AEM gegevensbronnen van gebruikersprofielen worden standaard weergegeven. Als u geen configuratieknooppunt selecteert, worden de gegevensbronnen van alle configuratieknooppunten vermeld.

   Selecteer **[!UICONTROL Next]** .

1. (**van toepassing slechts als de gegevensbronnen** worden gevormd) het **[!UICONTROL Select Datasource]** scherm maakt een lijst van beschikbare gegevensbronnen, als om het even welk. Selecteer gegevensbronnen die u wilt gebruiken in het formuliergegevensmodel.
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Open]** in het bevestigingsvenster om de formuliergegevensmodeleditor te openen.

Laten we de verschillende componenten van de gebruikersinterface van de formuliergegevensmodel bekijken.

![&#x200B; het model van vormgegevens van A met drie gegevensbronnen - de dienst RESTful, AEM gebruikersprofiel, en een RDBMS &#x200B;](assets/fdm-ui.png)

**A. Gegevensbronnen** Maakt een lijst van gegevensbronnen in een model van vormgegevens. Breid een gegevensbron uit om zijn voorwerpen en de diensten van het gegevensmodel te bekijken.

**B. Vernieuw de Definities van Gegevens Source** vangt om het even welke veranderingen in gegevensbrondefinities van gevormde gegevensbronnen en werkt hen op het lusje van Gegevensbronnen van de modelredacteur van vormgegevens bij.

**C. Model** Inhoudsgebied waarin objecten voor toegevoegd gegevensmodel worden weergegeven.

**D. De diensten** gebied van de Inhoud waar de toegevoegde gegevensbronverrichtingen of de diensten verschijnen.

**E. De toolbar** Hulpmiddelen om met het model van vormgegevens te werken. Op de werkbalk ziet u meer opties, afhankelijk van het geselecteerde object in het formuliergegevensmodel.

**F. Voeg Geselecteerde** toe voegt geselecteerde voorwerpen en de diensten van het gegevensmodel aan het model van vormgegevens toe.

Voor meer informatie over de modelredacteur van vormgegevens en hoe u met het kunt werken om het model van vormgegevens uit te geven en te vormen, zie [&#x200B; Werk met het model van vormgegevens &#x200B;](../../forms/using/work-with-form-data-model.md).

## Gegevensbronnen bijwerken {#update}

Ga als volgt te werk om gegevensbronnen toe te voegen aan of bij te werken naar een bestaand formuliergegevensmodel.

1. Ga naar **[!UICONTROL Forms > Data Integrations]** en selecteer het formuliergegevensmodel waarin u gegevensbronnen wilt toevoegen of bijwerken. Selecteer vervolgens **[!UICONTROL Properties]** .
1. Ga in de eigenschappen van het formuliergegevensmodel naar het tabblad **[!UICONTROL Update Source]** .

   Op het tabblad Source bijwerken:

   * Selecteer het bladerpictogram in het **[!UICONTROL Context-Aware Configuration]** gebied en selecteer een configuratieknooppunt waar de wolkenconfiguratie voor de gegevensbron u wilt toevoegen verblijft. Als u geen knooppunt selecteert, worden cloudconfiguraties die alleen in het knooppunt `global` staan, weergegeven wanneer u **[!UICONTROL Add Sources]** selecteert.

   * Als u een nieuwe gegevensbron wilt toevoegen, selecteert u **[!UICONTROL Add Sources]** en selecteert u de gegevensbronnen die u aan het formuliergegevensmodel wilt toevoegen. Alle gegevensbronnen die zijn geconfigureerd in `global` en het geselecteerde configuratieknooppunt, indien aanwezig, worden weergegeven.

   * Als u een bestaande gegevensbron wilt vervangen door een andere gegevensbron van hetzelfde type, selecteert u het pictogram **[!UICONTROL Edit]** voor de gegevensbron en kiest u een van de beschikbare gegevensbronnen in de lijst.
   * Als u een bestaande gegevensbron wilt verwijderen, selecteert u het pictogram **[!UICONTROL Delete]** voor de gegevensbron. Het pictogram Verwijderen is uitgeschakeld als een gegevensmodelobject in de gegevensbron wordt toegevoegd aan het formuliergegevensmodel.

   ![&#x200B; fdm-eigenschappen &#x200B;](assets/fdm-properties.png)

1. Selecteer **[!UICONTROL Save & Close]** om de updates op te slaan.

>[!NOTE]
>
>Nadat u nieuwe gegevensbronnen hebt toegevoegd of bestaande gegevensbronnen hebt bijgewerkt in een formuliergegevensmodel, zorgt u ervoor dat u de bindingsverwijzingen naar behoren bijwerkt in adaptieve formulieren en interactieve communicatie die gebruikmaken van het bijgewerkte formuliergegevensmodel.

## Volgende stappen {#next-steps}

U hebt nu een formuliergegevensmodel waaraan gegevensbronnen zijn toegevoegd. Vervolgens kunt u het gegevensmodel van het formulier bewerken om gegevensmodelobjecten en -services toe te voegen en te configureren, koppelingen tussen gegevensmodelobjecten toe te voegen, eigenschappen te bewerken, aangepaste gegevensmodelobjecten en -eigenschappen toe te voegen, voorbeeldgegevens te genereren, enzovoort.

Voor meer informatie, zie [&#x200B; Werk met model van vormgegevens &#x200B;](../../forms/using/work-with-form-data-model.md).
