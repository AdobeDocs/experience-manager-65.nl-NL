---
title: Dit artikel bevat de instructie om het Forms-add-on-pakket met behulp van CRX Package Manager te verwijderen.
description: Leer de stappen voor het verwijderen van het Forms-invoegpakket met behulp van CRX Package Manager.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 975f1f580404ea1f2940aec5981f5668dced4b95
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 1%

---


# AEM Forms Add-on Package verwijderen van AEM Instance

In dit artikel worden de stappen beschreven die nodig zijn om het AEM Forms-invoegpakket correct te verwijderen van een AEM Forms SDK-instantie. Ga als volgt te werk om ervoor te zorgen dat het invoegpakket voor Forms wordt verwijderd, zodat potentiële problemen met uw AEM worden voorkomen.

## Voorwaarden

Zorg ervoor dat u een back-up maakt van formulieren en gegevens om gegevensverlies te voorkomen.

## AEM Forms Add-on Package verwijderen

Voer de volgende stappen uit om het AEM Forms Add-on Package te verwijderen:

1. **Verwijder het AEM Forms Add-on-pakket:**
   1. Ga naar de `http://[host]:[port]/crx/de/index.jsp`.
   1. Zoek en verwijder de `AEM Forms add-on package`.

   ![Pakket verwijderen](/help/forms/using/assets/uninstall-aem-forms-package.png)

1. **De native map verwijderen uit CRXDE:**
   1. Ga naar de `http://[host]:[port]/crx/de/index.jsp`.
   1. Ga naar `/libs/fd/native/install` en verwijderen `native` in CRXDE.

      ![Native knooppunt verwijderen uit CRX/de](/help/forms/using/assets/native-install-folder-crxde.png)
   1. Sla de wijzigingen op.

1. **Stop de SDK van AEM Forms:**
   1. Stop de AEM Forms SDK-instantie met de opdracht &#39;Ctrl + C&#39;.

1. **Controleren op de vaste schijf en mappen installeren in de map crx-quickstart**
   1. Navigeren naar `..author\crx-quickstart` in de AEM Forms SDK-instantie.
   1. Naar benoemde mappen zoeken `bedrock` en `install`.
Indien gevonden, zorg ervoor dat zij uit worden geschrapt `crx-quickstart` in de AEM Forms SDK-instantie.

   >[!NOTE]
   >
   > De `bedrock` wordt automatisch opnieuw een map gemaakt wanneer u de AEM Forms SDK-instantie opnieuw start.

1. **Start de AEM opnieuw:**
   1. Zodra alle vorige stappen zijn voltooid, [de AEM Forms SDK-instantie opnieuw starten](/help/forms/using/restart-aem-sdk.md).




