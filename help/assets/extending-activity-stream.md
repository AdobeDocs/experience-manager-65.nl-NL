---
title: Integreer [!DNL Assets] met activiteitsstroom
description: Beschrijft de opnamemogelijkheden van [!DNL Experience Manager] en hoe te om het te vormen om specifieke gebeurtenissen te registreren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 1%

---


# [!DNL Assets] integreren met activiteitsstroom {#integrating-assets-with-activity-stream}

[!DNL Adobe Experience Manager Assets] gebruikers voeren veel handelingen uit, zoals het maken, uploaden en verwijderen van elementen. Deze acties kunnen worden opgenomen zodat u een geschiedenis kunt verstrekken van wat door een gebruiker is gedaan. In deze sectie worden de opnamemogelijkheden van [!DNL Experience Manager] beschreven en hoe u [!DNL Experience Manager] configureert om specifieke gebeurtenissen op te nemen.

## Prestatieoverwegingen en standaardgedrag {#performance-considerations-and-default-behavior}

Deze integratie kan CPU- en schijfruimte in beslag nemen, bijvoorbeeld bij het importeren van grote hoeveelheden. Om deze redenen is de [!DNL Assets]-integratie met de activiteitsstroom standaard uitgeschakeld.

## Ondersteunde actiegebeurtenissen {#supported-action-events}

De volgende gebeurtenissen kunnen worden geconfigureerd om te worden opgenomen:

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
* Submiddel bijgewerkt (SUBASSET_UPDATED)
* Subelement verwijderd (SUBASSET_REMOVED)

## [!DNL Assets]-gebeurtenissen voor het opnemen van {#configuring-aem-assets-events-recording} configureren

De [Webconsole](/help/sites-deploying/configuring-osgi.md) biedt toegang tot de afstemming van de Gebeurtenisrecorder van Elementen. Ga als volgt te werk om de Gebeurtenisrecorder voor middelen te configureren:

1. Navigeer naar **[!UICONTROL Web Console]**

1. Klik op **[!UICONTROL Configuration]**.

1. Dubbelklik op **[!UICONTROL Day CQ DAM Event Recorder]**.

1. Vinkje **[!UICONTROL Enables this service]**.

1. Controleer welke **[!UICONTROL Event Types]** u in de stroom van de gebruikersactiviteit wilt worden geregistreerd.

1. Klik op **[!UICONTROL Save]**.

## Opgenomen gebeurtenissen {#reading-recorded-events} lezen

De opgenomen gebeurtenissen worden opgeslagen als activiteiten. U kunt deze programmatisch lezen met de [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
