---
title: De tekenset wijzigen
seo-title: De tekenset wijzigen
description: U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd. Leer hoe u de tekenset kunt wijzigen.
seo-description: U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd. Leer hoe u de tekenset kunt wijzigen.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# De tekenset {#change-the-character-set} wijzigen

U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd.

1. Klik in de beheerconsole op **[!UICONTROL Services > output]**.
1. Selecteer onder Internationalisatie een tekenset in de lijst Tekenset. Deze instelling is afhankelijk van de `TransformationFormat` en `PrintFormat` die via de API zijn opgegeven. Als u een andere tekenset dan de vermelde wilt opgeven, selecteert u Aangepast en geeft u een coderingswaarde op in het vak dat wordt weergegeven.

   Als `TransformationFormat` PDF en PDF/A of `PrintFormat` PCL, PostScript, Zebra-label, IPL, DPL, TPCL, GenericColorPCL of GenericPSLevel3 is, worden alleen specifieke tekensets ondersteund.

   De tekenset moet een geldige canonieke naam zijn. De standaardwaarde is ISO-8859-1.

1. Klik op **[!UICONTROL Save]**.

