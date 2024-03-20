---
title: Integreren [!DNL Assets] met activiteitsstroom
description: Beschrijft de opnamemogelijkheden van [!DNL Experience Manager] en hoe te om het te vormen om specifieke gebeurtenissen te registreren.
contentOwner: AG
role: Developer
feature: Asset Management
exl-id: 2a08a7c1-8be9-42d1-9983-f9c8b12ea4e8
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Integreren [!DNL Assets] met activiteitsstroom {#integrating-assets-with-activity-stream}

[!DNL Adobe Experience Manager Assets] gebruikers voeren veel handelingen uit, zoals het maken, uploaden en verwijderen van elementen. Deze acties kunnen worden opgenomen zodat u een geschiedenis kunt verstrekken van wat door een gebruiker is gedaan. In deze sectie worden de opnamemogelijkheden van [!DNL Experience Manager] en configureren [!DNL Experience Manager] om specifieke gebeurtenissen op te nemen.

## Prestatieoverwegingen en standaardgedrag {#performance-considerations-and-default-behavior}

Deze integratie kan CPU- en schijfruimte in beslag nemen, bijvoorbeeld bij het importeren van grote hoeveelheden. Om deze redenen [!DNL Assets] integratie met de activiteitsstroom is standaard uitgeschakeld.

## Ondersteunde handelingsgebeurtenissen {#supported-action-events}

U kunt de volgende gebeurtenissen configureren die moeten worden opgenomen:

* Licentie geaccepteerd (AANVAARD)
* Gemaakte activa (ASSET_CREATED)
* Verplaatst element (ASSET_MOVED)
* Element verwijderd (ASSET_REMOVED)
* Vergunning geweigerd (AFGEWEZEN)
* Gedownload element (GEDOWNLOAD)
* Geversioneerd element (VERSIONED)
* Herstelbare versie van element
* Metagegevens van element bijgewerkt (METADATA_UPDATED)
* Element gepubliceerd naar extern systeem (PUBLISHED_EXTERNAL)
* Oorspronkelijk bijgewerkt element (ORIGINAL_UPDATED)
* Vertoning van element bijgewerkt (RENDITION_UPDATED)
* Vertoning van element verwijderd (RENDITION_REMOVED)
* Subelement bijgewerkt (SUBASSET_UPDATED)
* Subelement verwijderd (SUBASSET_REMOVED)

## Configureren [!DNL Assets] gebeurtenissen opnemen {#configuring-aem-assets-events-recording}

De [Webconsole](/help/sites-deploying/configuring-osgi.md) biedt toegang tot de afstemming van de Elements Event Recorder. Ga als volgt te werk om de Gebeurtenisrecorder voor middelen te configureren:

1. Ga naar de **[!UICONTROL Web Console]**

1. Klik op **[!UICONTROL Configuration]**.

1. Dubbelklikken **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Controleren **[!UICONTROL Enables this service]**.

1. Controleren welke **[!UICONTROL Event Types]** die u wilt opnemen in de gebruikersactiviteitsstroom.

1. Klik op **[!UICONTROL Save]**.

## Opgenomen gebeurtenissen lezen {#reading-recorded-events}

De opgenomen gebeurtenissen worden opgeslagen als activiteiten. U kunt ze programmatisch lezen met de opdracht [ActivityManager-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
