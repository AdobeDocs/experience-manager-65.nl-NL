---
title: De tekenset wijzigen
seo-title: Change the character set
description: U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd. Leer hoe u de tekenset kunt wijzigen.
seo-description: You can specify the character set used to encode the output stream. Learn how you can change the character set.
uuid: ecb0c3ff-368c-4553-80e4-aa35fc15af62
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 811b31f8-5465-4fb2-b1f9-513936041771
exl-id: 9ff75d98-54ad-425d-912f-d5a7501bf564
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---

# De tekenset wijzigen {#change-the-character-set}

U kunt de tekenset opgeven waarmee de uitvoerstream wordt gecodeerd.

1. Klik in de beheerconsole op **[!UICONTROL Services > output]**.
1. Selecteer onder Internationalisatie een tekenset in de lijst Tekenset. Deze instelling is afhankelijk van de instelling `TransformationFormat` en `PrintFormat` opgegeven via de API. Als u een andere tekenset dan de vermelde wilt opgeven, selecteert u Aangepast en geeft u een coderingswaarde op in het vak dat wordt weergegeven.

   Indien `TransformationFormat` is PDF en PDF/A of `PrintFormat` PCL, PostScript, Zebra-label, IPL, DPL, TPCL, GenericColorPCL of GenericPSLevel3, worden alleen specifieke tekensets ondersteund.

   De tekenset moet een geldige canonieke naam zijn. De standaardwaarde is ISO-8859-1.

1. Klik op **[!UICONTROL Save]**.
