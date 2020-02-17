---
title: Vertaalcloudservices toepassen op mappen
description: Vertaalcloudservices toepassen op mappen
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Vertaalcloudservices toepassen op mappen {#applying-translation-cloud-services-to-folders}

Met Adobe Experience Manager (AEM) kunt u vertaalservices in de cloud gebruiken van het vertaalbureau van uw keuze om ervoor te zorgen dat uw middelen op basis van uw vereisten worden vertaald.

U kunt de vertaalcloudservice rechtstreeks toepassen op de map met middelen, zodat u deze kunt gebruiken tijdens vertaalworkflows.

## Vertaalservices toepassen {#applying-the-translation-services}

Als u de vertaalcloud-services rechtstreeks toepast op uw map met middelen, hoeft u geen vertaalservices te configureren wanneer u vertaalworkflows maakt of bijwerkt.

1. Selecteer in de gebruikersinterface Middelen de map waarop u vertaalservices wilt toepassen.
1. Klik/tik op het pictogram **[!UICONTROL Eigenschappen]** op de werkbalk om de pagina **[!UICONTROL Eigenschappen]** van map weer te geven.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Navigeer naar het tabblad **[!UICONTROL Cloud Services]** .
1. Kies in de lijst Cloud Service Configurations de gewenste vertaalprovider. Als u bijvoorbeeld vertaalservices wilt gebruiken vanuit Microsoft, kiest u **[!UICONTROL Microsoft Translator]**.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Kies de connector voor de vertaalprovider.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Klik in de werkbalk op **[!UICONTROL Opslaan]** of tik op Opslaan en klik vervolgens op **[!UICONTROL OK]** om het dialoogvenster te sluiten. De vertaalservice wordt toegepast op de map.

## Aangepaste vertaalaansluiting toepassen {#applying-custom-translation-connector}

Als u een aangepaste aansluiting wilt toepassen voor de vertaalservices die u wilt gebruiken in vertaalworkflows. Om een douaneverbinding toe te passen, installeer eerst de schakelaar van de Manager van het Pakket. Dan, vorm de schakelaar van de console van de Diensten van de Wolk. Nadat u de aansluiting hebt geconfigureerd, is deze beschikbaar in de lijst met connectors op het tabblad Cloud Services die wordt beschreven in [De vertaalservices](transition-cloud-services.md#applying-the-translation-services)toepassen. Nadat u de douaneverbinding en de looppas vertaalwerkschema&#39;s toepast, toont de **[!UICONTROL Vertaling Summiere]** tegel van het vertaalproject de schakelaardetails onder de hoofden **[!UICONTROL Leverancier]** en **[!UICONTROL Methode]**.

1. Installeer de connector via Package Manager.
1. Klik op of tik op het AEM-logo en navigeer naar **[!UICONTROL Extra > Implementatie > Cloud Services]**.
1. Zoek de connector die u onder Services **[!UICONTROL van]** derden hebt geïnstalleerd op de pagina **[!UICONTROL Cloud Services]** .

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Klik/tik de **[!UICONTROL Configure nu]** verbinding om de **[!UICONTROL Create dialoog van de Configuratie]** te openen.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Geef een titel en een naam voor de aansluiting op en klik op **[!UICONTROL Maken]**. De aangepaste aansluiting is beschikbaar in de lijst met connectors op het tabblad **[!UICONTROL Cloud Services]** die wordt beschreven in stap 5 van de [toepassing van de vertaalservices](#applying-the-translation-services).
1. Voer een vertaalworkflow uit die in [Vertaalprojecten](translation-projects.md) maken wordt beschreven nadat u de aangepaste connector hebt toegepast. Verifieer de details van de schakelaar in de **[!UICONTROL Vertaal Summiere]** tegel van het vertaalproject in de console van **[!UICONTROL Projecten]** .

   ![chlimage_1-220](assets/chlimage_1-220.png)
