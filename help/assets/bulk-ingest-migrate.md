---
title: Functiepakket 18912 voor migratie van grote hoeveelheden bedrijfsmiddelen installeren
description: Met Feature Pack 18912 kunt u elementen via FTP bulksgewijs toevoegen of elementen van Dynamic Media Classic migreren naar Dynamic Media op AEM. Dit optionele functiepakket is beschikbaar bij de ondersteuning van Adobe.
uuid: 45c2f5f8-4368-4d7b-a43e-fe96cfb272fd
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: 5d5eebe4-46c9-4028-9354-c5f27944fcdc
docset: aem65
translation-type: tm+mt
source-git-commit: d6ae8bffa2d9d59f5656b9344d8826128f12885c
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---


# Functiepakket 18912 voor migratie van grote hoeveelheden bedrijfsmiddelen installeren{#installing-feature-pack-for-bulk-asset-migration}

De installatie van functiepak 18912 is *optioneel*.

Het pak van de eigenschap 18912 laat u of bulkingest activa direct in Dynamic Media - wijze Scene7 op AEM door middel van FTP, of migrate activa van Dynamic Media Klassiek in Dynamic Media - wijze Scene7 op AEM. Het functiepakket is beschikbaar bij [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Hoewel het voor u mogelijk is om het eigenschappak te gebruiken om activa op zich te bulken van Dynamic Media Klassiek aan Dynamic Media - wijze Scene 7 in AEM of bulkmigreren activa gebruikend de eigenschap van FTP in Dynamic Media Classic, adviseert Adobe deze methode *niet* wegens de ingewikkeldheid in kwestie.
>
>Migratiefunctiepakketten, zoals deze, worden daarom *alleen* ondersteund als onderdeel van een migratieproject als dit gebeurt via [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Voordat u het functiepakket kunt installeren, moet u eerst een servicegebruiker maken en die informatie doorgeven aan de ondersteuning van Adobe.

Zie ook het [Vormen Dynamic Media - wijze](/help/assets/config-dms7.md)Scene7.

**Om functiepak 18912 voor de migratie van bulkmiddelen te installeren**

1. Navigeer in uw AEM-instantie naar **[!UICONTROL Tools > Security > Users]** en selecteer **[!UICONTROL Create User]**. Deze servicegebruiker moet over *lees-/schrijfmachtigingen* beschikken om `/content/dam.`
1. Voer in de velden **[!UICONTROL ID]** en **[!UICONTROL Password]** velden een gebruikersnaam en wachtwoord in. bijvoorbeeld **FTP-gebruiker**. Deze naam wordt in de tijdlijn weergegeven als de gebruiker die het element heeft gemaakt. Wanneer een element wordt geüpload vanaf FTP, wordt een element beschouwd als gemaakt wanneer het naar de FTP-server wordt geüpload en naar AEM wordt geduwd.
1. Neem contact op met de klantenservice van [Adobe Enterprise voor Experience Manager](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) om toegang te vragen tot het functiepakket 18912 voor downloaden. U hebt mogelijk de volgende informatie nodig wanneer u contact opneemt met de ondersteuningsafdeling:

   * IP van de server adres voor uw instantie van de Auteur, met inbegrip van het havenaantal (door gebrek, is het havenaantal 4502.)
   * Gebruikersnaam en wachtwoord voor AEM-service uit de vorige stap.

1. De klantenservice van Adobe Enterprise voor AEM biedt u de FTP-referenties en toegang tot het functiepakket 18912.
1. Wanneer u het functiepak 18912 ontvangt, installeer het.

   Zie [hoe te met Pakketten](/help/sites-administering/package-manager.md) voor meer informatie te werken bij het gebruiken van de Distributie van de Software en de pakketten in AEM.
