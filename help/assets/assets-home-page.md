---
title: "[!DNL Assets] Home Page experience"
description: Personaliseer [!DNL Experience Manager Assets] De homepage voor een rijke het ontvangen het schermervaring, met inbegrip van een momentopname van recente activiteiten rond activa.
contentOwner: AG
feature: Asset Management
role: Admin, User
exl-id: 042bd959-256a-4794-a34d-0848a6b8840d
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 1%

---

# [!DNL Adobe Experience Manager Assets] Introductiepagina {#aem-assets-home-page-experience}

Personaliseer [!DNL Adobe Experience Manager Assets] homepage voor een rijke welkomstscherm ervaring, met inbegrip van een momentopname van recente activiteiten rond activa.

[!DNL Assets] de homepage verstrekt een rijke en gepersonaliseerde ervaring van het welkomstscherm, die een momentopname van recente activiteiten, zoals activa omvat die onlangs werden bekeken of geupload.

De [!DNL Assets] de startpagina is standaard uitgeschakeld. Voer de volgende stappen uit om het in te schakelen:

1. Openen [!DNL Experience Manager] Configuratiebeheer `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Day CQ DAM Event Recorder]** service.
1. Selecteer de **[!UICONTROL Enable this service]** om het opnemen van activiteiten in te schakelen.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Van de **[!UICONTROL Event Types]** selecteert u de gebeurtenissen die moeten worden opgenomen en slaat u de wijzigingen op.

   >[!CAUTION]
   >
   >Als u de weergaveopties voor het element, de bekeken projecten en de weergegeven verzamelingen inschakelt, wordt het aantal opgenomen gebeurtenissen aanzienlijk verhoogd.

1. Open de **[!UICONTROL DAM Asset Home Page Feature Flag]** service van Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Selecteer de `isEnabled.name` om de [!DNL Assets] Functie voor startpagina. Sla de wijzigingen op.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Open de **[!UICONTROL User Preferences]** en selecteert u **[!UICONTROL Enable Assets Home Page]**. Sla de wijzigingen op.

   ![De elementenstartpagina inschakelen in het dialoogvenster Gebruikersvoorkeuren](assets/Annotation-color.png)

Nadat u het dialoogvenster [!DNL Assets] Startpagina, navigeer naar de [!DNL Assets] gebruikersinterface vanaf de navigatiepagina of rechtstreeks via de URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam`.

![ervaringskoppeling configureren in de gebruikersinterface voor middelen](assets/config-experience-link.png)

Klik op de knop **[!UICONTROL Click here to configure your experience link]** om uw gebruikersnaam, achtergrondafbeelding en profielafbeelding toe te voegen.

De [!DNL Assets] De startpagina bevat de volgende secties:

* Welkomstsectie
* Widget-sectie

**Welkomstsectie**

Als uw profiel bestaat, wordt in de welkomstsectie een welkomstbericht weergegeven dat aan u is gericht. Bovendien worden uw profielfoto en een welkomstafbeelding weergegeven (indien al geconfigureerd).

Als uw profiel onvolledig is, geeft de welkomstsectie een algemeen welkomstbericht en een tijdelijke aanduiding voor uw profielafbeelding weer.

**Widget-sectie**

Deze sectie verschijnt onder de welkomstsectie en toont buiten-de-dooswidgets onder de volgende secties:

* Activiteit
* Recent
* Discover

**Activiteit**: In deze sectie wordt de **[!UICONTROL My Activity]** De widget geeft recente activiteiten weer die door de aangemelde gebruiker zijn uitgevoerd met elementen (waaronder elementen zonder vertoningen), zoals het uploaden van middelen, downloads, het maken van elementen, bewerkingen, opmerkingen, annotaties en shares.

**Recent**: De **[!UICONTROL Recently Viewed]** widget onder deze sectie toont onlangs betreden entiteiten door de het programma geopende gebruiker, met inbegrip van omslagen, inzamelingen, en projecten.

**Discover**: De **[!UICONTROL New]** widget in deze sectie geeft de elementen en vertoningen weer die onlangs zijn geüpload naar de [!DNL Assets] implementatie.

Schakel de optie **[!UICONTROL DAM Event Purge Service]** in Configuratiebeheer. Nadat u deze dienst toelaat, worden de activiteiten van de het programma geopende gebruiker die een gespecificeerd aantal overschrijden geschrapt door het systeem.

Het welkomstscherm biedt eenvoudige navigatiehulpmiddelen, zoals pictogrammen op de werkbalk, voor toegang tot mappen, verzamelingen en catalogi.

>[!NOTE]
>
>Het inschakelen van de [!UICONTROL Day CQ DAM Event Recorder] en [!UICONTROL DAM Event Purge] de diensten verhogen schrijven verrichtingen aan JCR en onderzoek indexeert, die beduidend de lading op de [!DNL Experience Manager] server. De extra belasting op de [!DNL Experience Manager] kan de prestaties van de server beïnvloeden.

>[!CAUTION]
>
>Vastleggen, filteren en leegmaken van gebruikersactiviteiten vereist voor [!DNL Assets] de homepage legt een overheadkosten op prestaties op. Daarom moeten beheerders de startpagina effectief configureren voor doelgebruikers.
>
>Adobe raadt beheerders en gebruikers die bulkbewerkingen uitvoeren aan de functie Startpagina van bedrijfsmiddelen niet te gebruiken om te voorkomen dat gebruikers meer gaan werken. Daarnaast kunnen beheerders opnameactiviteiten voor specifieke gebruikers uitsluiten door [!UICONTROL Day CQ DAM Event Recorder] van [!UICONTROL Configuration Manager].
>
>Als u deze functie gebruikt, wordt u door de Adobe aangeraden de laadfrequentie te bepalen op basis van het laden van de server.
