---
title: MIME-type van activa detecteren met Apache Tika
description: Schakel Apache Tika in om AEM Assets te helpen het MIME-type van elementen van de inhoudsstroom te detecteren tijdens het uploaden in plaats van de bestandsextensie.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# MIME-type van activa detecteren met Apache Tika {#detecting-mime-type-of-assets-using-apache-tika}

Normaliter wordt in Adobe Experience Manager (AEM) het MIME-type van middelen gedetecteerd dat u uploadt vanuit de bestandsextensie.

Als u Apache Tika gebruikt om activa te uploaden, ontdekt AEM Middelen hun MIME type van de inhoudsstroom tijdens het uploaden verrichting in plaats van de dossieruitbreiding.

Deze functie is standaard uitgeschakeld. Om de eigenschap toe te laten, vorm de dienst van het Type **[!UICONTROL van MIME van]** Dag CQ DAM van de Manager [!UICONTROL van de]Configuratie.

>[!NOTE]
>
>MIME-typedetectie met behulp van de Apache Tika-bibliotheek is een hulpbronnenintensieve bewerking.

1. Om de Webconsole van de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Zoek in de lijst met services de **[!UICONTROL Day CQ DAM Mime Type Service]** op en tik op **[!UICONTROL Bewerken]** naast deze service om deze in de modus Bewerken te openen.

1. Selecteer de optie MIME **[!UICONTROL detecteren uit inhoud]** om het parseren van geüploade elementen in staat te stellen hun MIME-type te bepalen terwijl bestandsextensies worden genegeerd. Deze optie is standaard uitgeschakeld.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klik op **[!UICONTROL Opslaan]** of tik op Opslaan om de wijzigingen op te slaan.
