---
title: Elementen integreren met activiteitsstroom
description: Beschrijft de opnamemogelijkheden van AEM en hoe te om AEM te vormen om specifieke gebeurtenissen te registreren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Elementen integreren met activiteitsstroom {#integrating-assets-with-activity-stream}

Gebruikers van Adobe Experience Manager (AEM) kunnen een groot aantal handelingen uitvoeren, zoals het maken, uploaden en verwijderen van middelen. Deze acties kunnen worden opgenomen zodat u een geschiedenis kunt verstrekken van wat door een gebruiker is gedaan. In deze sectie worden de opnamemogelijkheden van AEM beschreven en wordt beschreven hoe u AEM kunt configureren om specifieke gebeurtenissen op te nemen.

## Prestatieoverwegingen en standaardgedrag {#performance-considerations-and-default-behavior}

Deze integratie kan CPU- en schijfruimte in beslag nemen, bijvoorbeeld bij het importeren van grote hoeveelheden. Om deze redenen is de integratie van AEM-middelen met de activiteitsstroom standaard uitgeschakeld.

## Ondersteunde handelingsgebeurtenissen {#supported-action-events}

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

## AEM Assets-opname configureren {#configuring-aem-assets-events-recording}

De [webconsole](/help/sites-deploying/configuring-osgi.md) biedt toegang tot de afstemming van de gebeurtenisopnamen van AEM Assets. Ga als volgt te werk om de gebeurtenisrecorder voor AEM-elementen te configureren:

1. Naar de **[!UICONTROL webconsole navigeren]**

1. Klik op **[!UICONTROL Configuratie]**.

1. Dubbelklik op **[!UICONTROL Dag CQ DAM-gebeurtenisrecorder]**.

1. Schakel **[!UICONTROL deze service]** in.

1. Controleer welke **[!UICONTROL gebeurtenistypen]** u in de stroom van de gebruikersactiviteit wilt worden geregistreerd.

1. Click **[!UICONTROL Save]**.

## Opgenomen gebeurtenissen lezen {#reading-recorded-events}

De opgenomen gebeurtenissen worden opgeslagen als activiteiten. U kunt deze programmatisch lezen met de [ActivityManager-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/activitystreams/ActivityManager.html).
