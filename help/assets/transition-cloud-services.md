---
title: Vertaalcloudservices toepassen op mappen
description: Pas vertaalwolkendiensten op omslagen in Adobe Experience Manager toe.
role: Admin
feature: Translation
exl-id: f17a33d7-eb2f-406b-8d6c-a3bf564c8702
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 42%

---

# Vertaalcloudservices toepassen op mappen {#applying-translation-cloud-services-to-folders}

[!DNL Adobe Experience Manager] kunt u gebruikmaken van vertaalservices in de cloud van de door u gekozen vertaalprovider om ervoor te zorgen dat uw middelen op basis van uw vereisten worden vertaald.

U kunt de vertaalcloudservice rechtstreeks toepassen op de map met middelen, zodat u deze kunt gebruiken tijdens vertaalworkflows.

## Vertaalservices toepassen {#applying-the-translation-services}

Als u de vertaalcloud-services rechtstreeks toepast op uw map met middelen, hoeft u geen vertaalservices te configureren wanneer u vertaalworkflows maakt of bijwerkt.

1. Van de [!DNL Assets] -gebruikersinterface, selecteert u de map waarop u vertaalservices wilt toepassen.
1. Klik op de werkbalk op **[!UICONTROL Properties]** om de **[!UICONTROL Folder Properties]** pagina.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Ga naar het tabblad **[!UICONTROL Cloud Services]**.
1. Kies in de lijst Configuraties van Cloud Servicen de gewenste vertaalprovider. Als u bijvoorbeeld vertaalservices wilt gebruiken vanuit Microsoft, kiest u **[!UICONTROL Microsoft Translator]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Kies de connector voor de vertaalprovider.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Klik op de werkbalk op **[!UICONTROL Save]** en klik vervolgens op **[!UICONTROL OK]** om het dialoogvenster te sluiten. De vertaalservice wordt toegepast op de map.

## Aangepaste vertaalaansluiting toepassen  {#applying-custom-translation-connector}

Als u een aangepaste connector wilt toepassen voor de vertaalservices die u wilt gebruiken in vertaalworkflows. Om een aangepaste connector toe te passen installeert u eerst de connector vanaf Package Manager. Vervolgens configureert u de connector vanaf de Cloud Services-console. Nadat u de connector hebt geconfigureerd, is deze beschikbaar in de lijst met connectors op het tabblad Cloud Services die wordt beschreven in [De vertaalservices toepassen](transition-cloud-services.md#applying-the-translation-services). Nadat u de aangepaste connector hebt toegepast en vertaalworkflows hebt uitgevoerd, geeft de tegel **[!UICONTROL Translation Summary]** van het vertaalproject de connectordetails weer onder de koppen **[!UICONTROL Provider]** en **[!UICONTROL Method]**.

1. Installeer de connector via Package Manager.
1. Klik op de knop [!DNL Experience Manager] logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Zoek de connector die u onder de pagina **[!UICONTROL Third Party Services]** in de **[!UICONTROL Cloud Services]** hebt geïnstalleerd.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Klik op de knop **[!UICONTROL Configure now]** de koppeling openen **[!UICONTROL Create Configuration]** in.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Specificeer een titel en een naam voor de schakelaar, en klik dan **[!UICONTROL Create]**. De aangepaste connector is beschikbaar in de lijst met connectors op het tabblad **[!UICONTROL Cloud Services]** zoals beschreven in stap 5 van [De vertaalservices toepassen](#applying-the-translation-services).
1. Voer een vertaalworkflow uit die in [Vertaalprojecten maken](translation-projects.md) wordt beschreven nadat u de aangepaste connector hebt toegepast. Verifieer de details van de connector in de tegel **[!UICONTROL Translation Summary]** van het vertaalproject in de **[!UICONTROL Projects]**-console.

   ![chlimage_1-220](assets/chlimage_1-220.png)
