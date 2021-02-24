---
title: Functiepakket 18912 voor migratie van grote hoeveelheden bedrijfsmiddelen installeren
description: Met Feature Pack 18912 kunt u middelen bulksgewijs innemen via FTP, of middelen van Dynamic Media Classic migreren naar Dynamic Media op AEM. Dit optionele functiepakket is verkrijgbaar bij Adobe-ondersteuning.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
translation-type: tm+mt
source-git-commit: 18e62f8fb46de20e1668b2dcdcedf68fe4622b50
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Installeren van functiepak 18912 voor migratie van grote hoeveelheden bedrijfsmiddelen{#installing-feature-pack-for-bulk-asset-migration}

De installatie van functiepak 18912 is *optioneel*.

Met Feature Pack 18912 kunt u opgenomen middelen rechtstreeks in Dynamic Media - Scene7-modus opnemen via AEM via FTP, of elementen van Dynamic Media Classic migreren naar Dynamic Media - Scene7-modus bij AEM. Het functiepakket is beschikbaar bij [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Hoewel het voor u mogelijk is om het eigenschappak te gebruiken om activa op zich van de Klassiek van Dynamic Media aan Dynamic Media - wijze Scene 7 in AEM of bulkmiddel te migreren migrate activa gebruikend de eigenschap van FTP in Dynamic Media Classic, *niet* adviseert Adobe deze methode wegens de ingewikkeldheid in kwestie.
>
>Als dusdanig, worden de pakketten van de migratieeigenschap, zoals dit, *slechts* gesteund als deel van een migratieproject wanneer gedaan door [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Voordat u het functiepakket kunt installeren, moet u eerst een servicegebruiker maken en die informatie doorgeven aan de ondersteuning van Adobe.

Zie ook [Dynamic Media configureren - Scene7-modus](/help/assets/config-dms7.md).

**Om functiepak 18912 voor de migratie van bulkmiddelen te installeren**

1. Navigeer in uw AEM naar **[!UICONTROL Tools > Security > Users]** en selecteer **[!UICONTROL Create User]**. Deze servicegebruiker moet *lees-/schrijfrechten* hebben voor `/content/dam.`
1. Voer in de velden **[!UICONTROL ID]** en **[!UICONTROL Password]** een gebruikersnaam en wachtwoord in. bijvoorbeeld **FTP-gebruiker**. Deze naam wordt in de tijdlijn weergegeven als de gebruiker die het element heeft gemaakt. Wanneer een element wordt geüpload vanaf FTP, wordt een element beschouwd als gemaakt wanneer het naar de FTP-server wordt geüpload en naar AEM wordt geduwd.
1. Neem contact op met [Adobe Enterprise Customer Care for Experience Manager](https://experienceleague.adobe.com/?support-solution=General#support) om toegang te vragen tot functiepakket 18912 voor downloaden. U hebt mogelijk de volgende informatie nodig wanneer u contact opneemt met de ondersteuningsafdeling:

   * IP van de server adres voor uw instantie van de Auteur, met inbegrip van het havenaantal (door gebrek, is het havenaantal 4502.)
   * AEM de gebruikersbenaming en het wachtwoord van de dienstgebruiker van de vorige stap.

1. Adobe Enterprise Customer Care for AEM biedt u de FTP-referenties en toegang tot functiepakket 18912.
1. Wanneer u het functiepak 18912 ontvangt, installeer het.

   Zie [Werken met Pakketten](/help/sites-administering/package-manager.md) voor meer informatie bij het gebruiken van de Distributie van de Software en pakketten in AEM.
