---
title: Installeren van functiepak 18912 voor migratie van grote bedrijfsmiddelen
description: Met Feature Pack 18912 kunt u middelen bulksgewijs innemen via FTP, of elementen van Dynamic Media Classic migreren naar Dynamic Media op Adobe Experience Manager. Dit optionele functiepakket is verkrijgbaar bij Adobe-ondersteuning.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
feature: Beheer van bedrijfsmiddelen
role: User, Admin
exl-id: 53ea2cf7-d633-4ab9-a869-ce76eb1c01e5
source-git-commit: 471f9e99078a1e0af60024d439afd42ae77cba8c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Installeren van functiepak 18912 voor migratie van grote bedrijfsmiddelen{#installing-feature-pack-for-bulk-asset-migration}

De installatie van functiepak 18912 is *optioneel*.

Met Feature Pack 18912 kunt u opgenomen elementen via FTP rechtstreeks in Dynamic Media - Scene7-modus op Adobe Experience Manager in bulk plaatsen. U kunt ook elementen migreren van Dynamic Media Classic naar de modus Dynamic Media - Scene7 op Experience Manager. Het functiepakket is beschikbaar bij [Adobe Professional Services](https://business.adobe.com/customers/consulting-services/main.html).

>[!IMPORTANT]
>
>U kunt het functiepakket gebruiken om uw eigen middelen in Experience Manager in bulk te migreren van Dynamic Media Classic naar Dynamic Media-Scene7. Het is ook mogelijk om migrate middelen in bulk te plaatsen gebruikend de eigenschap van FTP in Dynamic Media Classic. Nochtans, adviseert Adobe *not* dat u één van beide methodes wegens de ingewikkeldheid in kwestie gebruikt.
>
>Als dusdanig, is dit migratie eigenschappak *slechts* gesteund als deel van een migratieproject wanneer gedaan door [Adobe Professional Services](https://business.adobe.com/customers/consulting-services/main.html).

Alvorens u het eigenschappak installeert, creeer een de dienstgebruiker en verstrek die informatie aan de steun van Adobe.

Zie ook [Dynamic Media configureren - Scene7-modus](/help/assets/config-dms7.md).

**Om functiepak 18912 voor migratie van bulkmiddelen te installeren:**

1. Navigeer in uw Experience Manager-instantie naar **[!UICONTROL Tool]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** en selecteer **[!UICONTROL Create User]**. Deze servicegebruiker moet *lees-/schrijfrechten* hebben voor `/content/dam.`
1. Voer in de velden **[!UICONTROL ID]** en **[!UICONTROL Password]** een gebruikersnaam en wachtwoord in. bijvoorbeeld **FTP-gebruiker**. Deze naam wordt in de tijdlijn weergegeven als de gebruiker die het element heeft gemaakt. Wanneer een element wordt geüpload vanaf FTP, wordt een element beschouwd als gemaakt wanneer het naar de FTP-server wordt geüpload en naar de Experience Manager wordt geduwd.
1. Neem contact op met [Adobe Enterprise Customer Care for Experience Manager](https://experienceleague.adobe.com/?support-solution=General#support) om toegang te vragen tot functiepakket 18912 voor downloaden. U hebt mogelijk de volgende informatie nodig wanneer u contact opneemt met de ondersteuningsafdeling:

   * IP van de server adres voor uw instantie van de Auteur, met inbegrip van het havenaantal (door gebrek, is het havenaantal 4502.)
   * Gebruikersnaam en wachtwoord van de Experience Manager-service uit de vorige stap.

1. Adobe Enterprise Customer Care for Experience Manager biedt u de FTP-referenties en toegang tot functiepakket 18912.
1. Wanneer u het functiepak 18912 ontvangt, installeer het.

   Zie [Werken met Pakketten](/help/sites-administering/package-manager.md) voor meer informatie bij het gebruiken van de Distributie van de Software en de pakketten in Experience Manager.
