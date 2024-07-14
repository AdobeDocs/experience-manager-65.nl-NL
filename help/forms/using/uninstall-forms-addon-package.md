---
title: Dit artikel bevat de instructie om het Forms-add-onpakket te verwijderen met CRX Package Manager.
description: Leer de stappen voor het verwijderen van het Forms-add-onpakket met CRX Package Manager.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: 2755e414ea23ebc1472e9c08d832eca93f28311b
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 1%

---


# AEM Forms Add-on Package verwijderen van AEM Instance

In dit artikel worden de stappen beschreven die nodig zijn om het AEM Forms-invoegpakket correct te verwijderen van een AEM Forms SDK-instantie. Voer de volgende stappen uit om ervoor te zorgen dat het Forms-add-on-pakket wordt verwijderd, zodat potentiële problemen met uw AEM worden voorkomen.

## Voorwaarde

Zorg ervoor dat u back-ups maakt om gegevensverlies te voorkomen.

## AEM Forms Add-on Package verwijderen

Voer de volgende stappen uit om het AEM Forms Add-on Package te verwijderen:

1. **desinstalleert het toe:voegen-op pakket van AEM Forms:**
   1. Navigeer naar de map `http://[host]:[port]/crx/de/index.jsp` .
   1. Zoek en verwijder de `AEM Forms add-on package` .

   ![ Uninstall pakket ](/help/forms/using/assets/uninstall-aem-forms-package.png)

1. **Schrap de inheemse omslag van CRXDE:**
   1. Navigeer naar de map `http://[host]:[port]/crx/de/index.jsp` .
   1. Ga naar de map `/libs/fd/native/install` en verwijder `native` in CRXDE.

      ![ Schrap inheemse knoop van CRX/de ](/help/forms/using/assets/native-install-folder-crxde.png)
   1. Sla de wijzigingen op.

1. **Einde SDK van AEM Forms:**
   1. Stop de AEM Forms SDK-instantie met de opdracht &#39;Ctrl + C&#39;.

1. **Controle voor het gesteente en installeert omslagen in crx-quickstart omslag**
   1. Navigeer naar de map `..author\crx-quickstart` in de AEM Forms SDK-instantie.
   1. Zoeken naar mappen met de naam `bedrock` en `install` .
Indien gevonden, zorg ervoor dat zij uit de `crx-quickstart` omslag in de instantie van de SDK van AEM Forms worden geschrapt.

   >[!NOTE]
   >
   > De map `bedrock` wordt automatisch opnieuw gemaakt wanneer u de AEM Forms SDK-instantie opnieuw start.

1. **begin de AEMInstantie opnieuw:**
   1. Zodra alle vorige stappen worden voltooid, [ nieuw begin de instantie van SDK van AEM Forms ](/help/forms/using/restart-aem-sdk.md).




