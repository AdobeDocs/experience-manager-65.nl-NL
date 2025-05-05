---
title: Installeren van functiepak 18912 voor migratie van grote bedrijfsmiddelen
description: Met Feature Pack 18912 kunt u middelen bulksgewijs innemen via FTP, of elementen van Dynamic Media Classic migreren naar Dynamic Media op Adobe Experience Manager. Dit optionele functiepakket is beschikbaar via ondersteuning voor Adoben.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
docset: aem65
feature: Asset Management
role: User, Admin
exl-id: 53ea2cf7-d633-4ab9-a869-ce76eb1c01e5
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Installeren van functiepak 18912 voor migratie van grote bedrijfsmiddelen{#installing-feature-pack-for-bulk-asset-migration}

De installatie van eigenschappak 18912 is facultatief **.

Met Feature Pack 18912 kunt u opgenomen elementen via FTP rechtstreeks in Dynamic Media - Scene7-modus op Adobe Experience Manager in bulk plaatsen. U kunt ook middelen migreren van Dynamic Media Classic naar de Scene7-modus op Experience Manager. Het eigenschappak is beschikbaar bij [ Adobe Professional Services ](https://business.adobe.com/customers/consulting-services/main.html).

>[!IMPORTANT]
>
>Het is mogelijk dat u het functiepakket gebruikt voor het bulken van uw eigen middelen van Dynamic Media Classic naar Dynamic Media - Scene7 modus in Experience Manager. Het is ook mogelijk om migratieactiva in bulk te migreren gebruikend de eigenschap van FTP in Dynamic Media Classic. Nochtans, adviseert de Adobe *niet* dat u één van beiden van deze methodes toe te schrijven aan de betrokken ingewikkeldheid gebruikt.
>
>Als dusdanig, wordt dit pak van de migratieeigenschap *slechts* gesteund als deel van een migratieproject wanneer gedaan door [ Adobe Professional Services ](https://business.adobe.com/customers/consulting-services/main.html).

Alvorens u het eigenschappak installeert, creeer een de dienstgebruiker en verstrek die informatie aan de steun van de Adobe.

Zie ook [ vormen Dynamic Media - de wijze van Scene7 ](/help/assets/config-dms7.md).

**om eigenschappak 18912 voor bulkactiva migratie te installeren:**

1. Navigeer in de instantie Experience Manager naar **[!UICONTROL Tool]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** en selecteer **[!UICONTROL Create User]** . Deze de dienstgebruiker moet *toestemmingen `/content/dam.` lezen/schrijven* hebben.
1. Op de **[!UICONTROL ID]** en **[!UICONTROL Password]** gebieden, ga een gebruikersnaam en wachtwoord in; bijvoorbeeld, **Gebruiker van FTP**. Deze naam wordt in de tijdlijn weergegeven als de gebruiker die het element heeft gemaakt. Wanneer een element wordt geüpload vanaf FTP, wordt een element beschouwd als gemaakt wanneer het naar de FTP-server wordt geüpload en naar de Experience Manager wordt geduwd.
1. De Steun van de Klant van de Adobe van het contact [ voor Experience Manager ](https://experienceleague.adobe.com/nl?support-solution=General#support) om toegang tot eigenschappak 18912 voor het downloaden te verzoeken. U hebt mogelijk de volgende informatie nodig wanneer u contact opneemt met de ondersteuningsafdeling:

   * IP van de server adres voor uw instantie van de Auteur, met inbegrip van het havenaantal (door gebrek, is het havenaantal 4502.)
   * Gebruikersnaam en wachtwoord van de Experience Manager-service uit de vorige stap.

1. De Klantenondersteuning van de Adobe voor Experience Manager biedt u de FTP-referenties en toegang tot functiepak 18912.
1. Wanneer u het functiepak 18912 ontvangt, installeer het.

   Zie [ hoe te met Pakketten ](/help/sites-administering/package-manager.md) voor meer informatie werken bij het gebruiken van de Distributie van de Software en de pakketten in Experience Manager.
