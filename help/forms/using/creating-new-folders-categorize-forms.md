---
title: Nieuwe mappen maken om formulieren te categoriseren
seo-title: Nieuwe mappen maken om formulieren te categoriseren
description: Gebruik mappen om uw formuliersjablonen, PDF's, bronnen en aangepaste formulieren te ordenen.
seo-description: Gebruik mappen om uw formuliersjablonen, PDF's, bronnen en aangepaste formulieren te ordenen.
uuid: 63fcb807-c9cf-49ae-ad69-6b1187543470
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 2a8f4380-8d0f-4354-b2da-4e0c02a545e3
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---


# Nieuwe mappen maken om formulieren {#create-new-folders-to-categorize-forms} te categoriseren

U kunt uw elementen beter ordenen met behulp van mappen. Aangezien AEM Forms ondersteuning biedt voor verschillende typen elementen (formuliersjablonen, PDF&#39;s, documenten, bronnen en adaptieve formulieren, met verschillende metagegevens), kunt u mappen gebruiken om uw formulieren te categoriseren op basis van de gewenste criteria.

Met AEM Forms kunt u de titel van een map wijzigen. De titel is niet gelijk aan de naam van het knooppunt waaronder de map is opgeslagen in de opslagplaats. In plaats daarvan blijft de titel behouden als metagegevens voor de map. Als u de titel van een map wijzigt, heeft dit geen invloed op het pad van de middelen in de map.

## Een map {#create-a-folder} maken

U kunt op een van de volgende manieren een map maken in AEM Forms:

* Upload een ZIP-bestand met elementen in de gewenste mapstructuur (zie [XDP- en PDF-documenten ophalen in AEM Forms](/help/forms/using/get-xdp-pdf-documents-aem.md))

* Nieuwe lege map maken

1. Meld u aan bij de AEM Forms-gebruikersinterface op `https://<server>:<port>/aem/forms.html`.
1. Navigeer naar de locatie waaronder u een map wilt maken.
1. Klik op het pictogram ![aem6forms_add](assets/aem6forms_add.png) op de werkbalk en selecteer **[!UICONTROL Create Folder]**.

1. Voer de volgende gegevens in:

   * **Titel:** Naam weergeven voor map
   * **Naam:** *(verplicht)* De knooppuntnaam waaronder u de map in de opslagplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanuit de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Klik op **[!UICONTROL Submit].**

   Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutbericht weergeven door de muisaanwijzer op het foutpictogram ![aem6forms_error_alert](assets/aem6forms_error_alert.png) naast het naamveld te plaatsen.

### De maptitel {#edit-the-folder-title-br} bewerken

1. Selecteer de map waarvan u de titel wilt bewerken.
1. Klik op het pictogram ![aem6forms_edit](assets/aem6forms_edit.png) op de werkbalk.
1. Voer de nieuwe titel in. Het tekstveld wordt vooraf gevuld met de huidige waarde van de maptitel. U kunt de waarde wijzigen in een nieuwe waarde.
1. Klik op **[!UICONTROL Submit].**

