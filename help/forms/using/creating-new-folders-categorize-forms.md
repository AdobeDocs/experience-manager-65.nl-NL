---
title: Nieuwe mappen maken om formulieren te categoriseren
seo-title: Create new folders to categorize forms
description: Gebruik mappen om uw formuliersjablonen, PDF, bronnen en aangepaste formulieren te ordenen.
seo-description: Use folders to organize your form templates, PDFs, resources, and adaptive forms.
uuid: 63fcb807-c9cf-49ae-ad69-6b1187543470
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 2a8f4380-8d0f-4354-b2da-4e0c02a545e3
role: Admin
exl-id: f8af1ac3-6a95-4f91-8979-6b41a7e02ca4
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Nieuwe mappen maken om formulieren te categoriseren {#create-new-folders-to-categorize-forms}

U kunt uw elementen beter ordenen met behulp van mappen. Aangezien AEM Forms ondersteuning biedt voor verschillende typen elementen (formuliersjablonen, PDF, documenten, bronnen en adaptieve formulieren, met verschillende metagegevens), kunt u mappen gebruiken om uw formulieren te categoriseren op basis van de gewenste criteria.

Met AEM Forms kunt u de titel van een map wijzigen. De titel is niet gelijk aan de naam van het knooppunt waaronder de map is opgeslagen in de opslagplaats. In plaats daarvan blijft de titel behouden als metagegevens voor de map. Als u de titel van een map wijzigt, heeft dit geen invloed op het pad van de middelen in de map.

## Een map maken {#create-a-folder}

U kunt op een van de volgende manieren een map maken in AEM Forms:

* Upload een ZIP-bestand met elementen in de gewenste mapstructuur (zie [XDP- en PDF-documenten ophalen in AEM Forms](/help/forms/using/get-xdp-pdf-documents-aem.md))

* Lege map maken

1. Meld u aan bij de gebruikersinterface van AEM Forms op `https://<server>:<port>/aem/forms.html`.
1. Navigeer naar de locatie waaronder u een map wilt maken.
1. Klik op de knop ![aem6forms_add](assets/aem6forms_add.png) op de werkbalk en selecteer vervolgens **[!UICONTROL Create Folder]**.

1. Voer de volgende gegevens in:

   * **Titel:** Naam voor de map weergeven
   * **Naam:** *(Verplicht)* De knooppuntnaam waaronder u de map in de opslagplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanuit de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Klik op **[!UICONTROL Submit].**

   Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutbericht weergeven door de muisaanwijzer op de fout te plaatsen ![aem6forms_error_alert](assets/aem6forms_error_alert.png) pictogram dat naast het naamveld wordt weergegeven.

### De maptitel bewerken {#edit-the-folder-title-br}

1. Selecteer de map waarvan u de titel wilt bewerken.
1. Klik op Bewerken ![aem6forms_edit](assets/aem6forms_edit.png) in de werkbalk.
1. Voer de nieuwe titel in. Het tekstveld wordt vooraf gevuld met de huidige waarde van de maptitel. U kunt de waarde wijzigen in een nieuwe waarde.
1. Klik op **[!UICONTROL Submit].**
