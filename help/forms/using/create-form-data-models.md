---
title: Formuliergegevensmodel maken
description: Leer hoe te om modellen van vormgegevens met of zonder gevormde gegevensbronnen te creëren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
docset: aem65
feature: Form Data Model
exl-id: 7f5978c3-6c9f-4ce4-b0fb-660ac1d49244
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# Formuliergegevensmodel maken{#create-form-data-model}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models.html) |
| AEM 6,5 | Dit artikel |


![hoofdafbeelding](do-not-localize/data-integration.png)

AEM Forms-gegevensintegratie biedt een intuïtieve gebruikersinterface voor het maken van en werken met formuliergegevensmodellen. Een formuliergegevensmodel is gebaseerd op gegevensbronnen voor gegevensuitwisseling. U kunt echter wel een formuliergegevensmodel maken met of zonder gegevensbron. Er zijn twee benaderingen om van gegevensmodel afhankelijk van tot stand te brengen of u gegevensbronnen hebt gevormd:

* **Vooraf geconfigureerde gegevensbronnen gebruiken**: Als u gegevensbronnen hebt geconfigureerd zoals beschreven in [Gegevensbronnen configureren](../../forms/using/configure-data-sources.md)kunt u deze selecteren tijdens het maken van een formuliergegevensmodel. Hiermee worden alle gegevensmodelobjecten, eigenschappen en services van de geselecteerde gegevensbronnen beschikbaar gemaakt voor gebruik in het formuliergegevensmodel.

* **Zonder gegevensbronnen**: Als u geen gegevensbronnen hebt geconfigureerd voor uw formuliergegevensmodel, kunt u het nog steeds maken zonder gegevensbronnen. U kunt het gegevensmodel van het formulier gebruiken om adaptieve formulieren en interactieve communicatie te maken en deze te testen met behulp van voorbeeldgegevens. Wanneer gegevensbronnen beschikbaar zijn, kunt u het formuliergegevensmodel binden met gegevensbronnen, die automatisch worden weergegeven in de bijbehorende adaptieve formulieren en interactieve communicatie.

>[!NOTE]
>
>U moet lid zijn van beide **fdm-auteur** en **formuliergebruiker** groepen die in staat zijn om een formuliergegevensmodel te maken en ermee te werken. Neem contact op met de AEM beheerder om lid te worden van de groepen.

## Formuliergegevensmodel maken {#data-sources}

Zorg ervoor dat u de gegevensbronnen hebt geconfigureerd die u wilt gebruiken in het formuliergegevensmodel, zoals beschreven in [Gegevensbronnen configureren](../../forms/using/configure-data-sources.md). Ga als volgt te werk om een formuliergegevensmodel te maken op basis van geconfigureerde gegevensbronnen:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms > Data Integrations]**.
1. Selecteren **[!UICONTROL Create > Form Data Model]**.
1. In het dialoogvenster Formuliergegevensmodel maken:

   * Geef een naam op voor het gegevensmodel van het formulier.
   * (**Optioneel**) Geef een titel, beschrijving en codes op voor het formuliergegevensmodel.
   * (**Optioneel en alleen van toepassing als gegevensbronnen zijn geconfigureerd**) Selecteer het verdeelpictogram naast **[!UICONTROL Data Source Configuration]** en selecteer het configuratieknooppunt waar de wolkendiensten voor de gegevensbronnen u wilt gebruiken verblijven. Het beperkt de lijst van gegevensbronnen beschikbaar voor selectie op de volgende pagina tot degenen beschikbaar in de geselecteerde configuratieknoop. Alle JDBC-database- en AEM gegevensbronnen van gebruikersprofielen worden standaard weergegeven. Als u geen configuratieknooppunt selecteert, worden de gegevensbronnen van alle configuratieknooppunten vermeld.

   Selecteren **[!UICONTROL Next]**.

1. (**Alleen van toepassing als gegevensbronnen zijn geconfigureerd**) **[!UICONTROL Select Datasource]** het scherm maakt een lijst van beschikbare gegevensbronnen, als om het even welk. Selecteer gegevensbronnen die u wilt gebruiken in het formuliergegevensmodel.
1. Selecteren **[!UICONTROL Create]** en in het bevestigingsdialoogvenster selecteert u **[!UICONTROL Open]** om de formuliergegevensmodeleditor te openen.

Laten we de verschillende componenten van de gebruikersinterface van de formuliergegevensmodel bekijken.

![Een formuliergegevensmodel met drie gegevensbronnen: een RESTful-service, AEM gebruikersprofiel en een RDBMS](assets/fdm-ui.png)

**A. Gegevensbronnen** Hier worden gegevensbronnen in een formuliergegevensmodel weergegeven. Breid een gegevensbron uit om zijn voorwerpen en de diensten van het gegevensmodel te bekijken.

**B. Definities van gegevensbron vernieuwen** Krijgt om het even welke veranderingen in gegevensbrondefinities van gevormde gegevensbronnen en werkt hen op het Bronlusje van Gegevens van de modelredacteur van vormgegevens bij.

**C. Model** Inhoudsgebied waar objecten van een toegevoegd gegevensmodel worden weergegeven.

**D. Diensten** Inhoudsgebied waar bewerkingen of services met toegevoegde gegevensbron worden weergegeven.

**E. Werkbalk** Gereedschappen voor het werken met het formuliergegevensmodel. Op de werkbalk ziet u meer opties, afhankelijk van het geselecteerde object in het formuliergegevensmodel.

**F. Geselecteerde toevoegen** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

Zie voor meer informatie over de formuliergegevensmodeleditor en hoe u ermee kunt werken om het formuliergegevensmodel te bewerken en te configureren [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md).

## Gegevensbronnen bijwerken {#update}

Ga als volgt te werk om gegevensbronnen toe te voegen aan of bij te werken naar een bestaand formuliergegevensmodel.

1. Ga naar **[!UICONTROL Forms > Data Integrations]** selecteert u het formuliergegevensmodel waarin u gegevensbronnen wilt toevoegen of bijwerken en selecteert u **[!UICONTROL Properties]**.
1. Ga in de eigenschappen van het formuliergegevensmodel naar **[!UICONTROL Update Source]** tab.

   Op het tabblad Bron bijwerken:

   * Selecteer het bladerpictogram in het dialoogvenster **[!UICONTROL Context-Aware Configuration]** en selecteer een configuratienode waar de wolkenconfiguratie voor de gegevensbron u wilt toevoegen verblijft. Als u geen knooppunt selecteert, blijven cloudconfiguraties alleen in de `global` knooppunt wordt weergegeven wanneer u **[!UICONTROL Add Sources]**.

   * Selecteer **[!UICONTROL Add Sources]** en selecteert u de gegevensbronnen die u aan het formuliergegevensmodel wilt toevoegen. Alle gegevensbronnen geconfigureerd in `global` en het geselecteerde configuratieknooppunt, als om het even welk, wordt getoond.

   * Als u een bestaande gegevensbron wilt vervangen door een andere gegevensbron van hetzelfde type, selecteert u de **[!UICONTROL Edit]** pictogram voor de gegevensbron en selecteer uit de lijst van beschikbare gegevensbronnen.
   * Als u een bestaande gegevensbron wilt verwijderen, selecteert u de **[!UICONTROL Delete]** pictogram voor de gegevensbron. Het pictogram Verwijderen is uitgeschakeld als een gegevensmodelobject in de gegevensbron wordt toegevoegd aan het formuliergegevensmodel.

   ![fdm-eigenschappen](assets/fdm-properties.png)

1. Selecteren **[!UICONTROL Save & Close]** om de updates op te slaan.

>[!NOTE]
>
>Nadat u nieuwe gegevensbronnen hebt toegevoegd of bestaande gegevensbronnen hebt bijgewerkt in een formuliergegevensmodel, zorgt u ervoor dat u de bindingsverwijzingen naar behoren bijwerkt in adaptieve formulieren en interactieve communicatie die gebruikmaken van het bijgewerkte formuliergegevensmodel.

## Volgende stappen {#next-steps}

U hebt nu een formuliergegevensmodel waaraan gegevensbronnen zijn toegevoegd. Vervolgens kunt u het gegevensmodel van het formulier bewerken om gegevensmodelobjecten en -services toe te voegen en te configureren, koppelingen tussen gegevensmodelobjecten toe te voegen, eigenschappen te bewerken, aangepaste gegevensmodelobjecten en -eigenschappen toe te voegen, voorbeeldgegevens te genereren, enzovoort.

Zie voor meer informatie [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md).
