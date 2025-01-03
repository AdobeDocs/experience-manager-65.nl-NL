---
title: De tekenset wijzigen
description: U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd. Leer hoe u de tekenset kunt wijzigen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 9ff75d98-54ad-425d-912f-d5a7501bf564
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# De tekenset wijzigen {#change-the-character-set}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd.

1. Klik in de beheerconsole op **[!UICONTROL Services > output]** .
1. Selecteer onder Internationalisatie een tekenset in de lijst Tekenset. Deze instelling is afhankelijk van de `TransformationFormat` en `PrintFormat` die via de API zijn opgegeven. Als u een andere tekenset dan de vermelde wilt opgeven, selecteert u Aangepast en geeft u een coderingswaarde op in het vak dat wordt weergegeven.

   Als `TransformationFormat` PDF en PDF/A of `PrintFormat` PCL, PostScript, Zebra-label, IPL, DPL, TPCL, GenericColorPCL of GenericPSLevel3 is, worden alleen specifieke tekensets ondersteund.

   De tekenset moet een geldige canonieke naam zijn. De standaardwaarde is ISO-8859-1.

1. Klik op **[!UICONTROL Save]**.
