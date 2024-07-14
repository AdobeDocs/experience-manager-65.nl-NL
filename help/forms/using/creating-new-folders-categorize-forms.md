---
title: Nieuwe mappen maken om formulieren te categoriseren
description: Gebruik mappen om uw formuliersjablonen, PDF, bronnen en aangepaste formulieren te ordenen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin,User
exl-id: f8af1ac3-6a95-4f91-8979-6b41a7e02ca4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Nieuwe mappen maken om formulieren te categoriseren {#create-new-folders-to-categorize-forms}

U kunt uw elementen beter ordenen met behulp van mappen. Aangezien AEM Forms ondersteuning biedt voor verschillende typen elementen (formuliersjablonen, PDF, documenten, bronnen en adaptieve formulieren, met verschillende metagegevens), kunt u mappen gebruiken om uw formulieren te categoriseren op basis van de gewenste criteria.

Met AEM Forms kunt u de titel van een map wijzigen. De titel is niet gelijk aan de naam van het knooppunt waaronder de map is opgeslagen in de opslagplaats. In plaats daarvan blijft de titel behouden als metagegevens voor de map. Als u de titel van een map wijzigt, heeft dit geen invloed op het pad van de middelen in de map.

## Een map maken {#create-a-folder}

U kunt op een van de volgende manieren een map maken in AEM Forms:

* Upload een dossier van het PIT dat activa in de gewenste omslagstructuur (zie, [ het Krijgen van documenten XDP en PDF in AEM Forms ](/help/forms/using/get-xdp-pdf-documents-aem.md) bevat)

* Lege map maken

1. Meld u aan bij de gebruikersinterface van AEM Forms op `https://<server>:<port>/aem/forms.html` .
1. Navigeer naar de locatie waaronder u een map wilt maken.
1. Klik ![ aem6forms_add ](assets/aem6forms_add.png) pictogram in de toolbar en selecteer dan **[!UICONTROL Create Folder]**.

1. Voer de volgende gegevens in:

   * **Titel:** de naam van de vertoning voor de omslag
   * **Naam:** *(Verplicht)* De knoopnaam waaronder u de omslag in de bewaarplaats wilt opslaan

   >[!NOTE]
   >
   >Standaard wordt de waarde van het naamveld automatisch ingevuld vanuit de titel. De naam mag alleen alfanumerieke tekens bevatten of speciale tekens voor het koppelteken (-) en het onderstrepingsteken (_). Eventuele andere speciale tekens die in de titel worden ingevoerd, worden automatisch vervangen door een afbreekstreepje en u wordt gevraagd de nieuwe naam te bevestigen. U kunt doorgaan met de voorgestelde naam of deze verder bewerken.

1. Klik op **[!UICONTROL Submit].**

   Er wordt een nieuwe map met de door u gedefinieerde titel weergegeven op de huidige locatie in de lijst met elementen.

   Als een map met de opgegeven naam bestaat, mislukt het verzenden met een fout. U kunt het foutenbericht bekijken door over het fout ![ aem6forms_error_alert ](assets/aem6forms_error_alert.png) pictogram te bewegen dat naast het naamgebied verschijnt.

### De maptitel bewerken {#edit-the-folder-title-br}

1. Selecteer de map waarvan u de titel wilt bewerken.
1. Klik uitgeven ![ aem6forms_edit ](assets/aem6forms_edit.png) pictogram in de toolbar.
1. Voer de nieuwe titel in. Het tekstveld wordt vooraf gevuld met de huidige waarde van de maptitel. U kunt de waarde wijzigen in een nieuwe waarde.
1. Klik op **[!UICONTROL Submit].**
