---
title: Adobe Experience Manager Assets Home Page Experience
description: Pas de startpagina Experience Manager Assets aan voor een uitgebreide ervaring met welkomstschermen, waaronder een momentopname van recente activiteiten rond middelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 678e91699523c22a7048bd7b344fa539b849ae8b
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 1%

---


# Adobe Experience Manager Assets Home Page Experience {#aem-assets-home-page-experience}

Pas de homepage van de Middelen van de Adobe Experience Manager aan voor een rijke welkomstscherm ervaring, met inbegrip van een momentopname van recente activiteiten rond activa.

De homepage van activa verstrekt een rijke en gepersonaliseerde ervaring van het welkomstscherm, die een momentopname van recente activiteiten, zoals activa omvat die onlangs werden bekeken of geupload.

De startpagina Middelen is standaard uitgeschakeld. Voer de volgende stappen uit om het in te schakelen:

1. Open Experience Manager Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Day CQ DAM Event Recorder]** service.
1. Selecteer de optie **[!UICONTROL Enable this service]** om opname van activiteiten in te schakelen.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Selecteer in de **[!UICONTROL Event Types]** lijst de gebeurtenissen die moeten worden opgenomen en sla de wijzigingen op.

   >[!CAUTION]
   >
   >Als u de weergaveopties voor het element, de bekeken projecten en de weergegeven verzamelingen inschakelt, wordt het aantal opgenomen gebeurtenissen aanzienlijk verhoogd.

1. Open de **[!UICONTROL DAM Asset Home Page Feature Flag]** dienst van de Manager van de Configuratie `https://[aem_server]:[port]/system/console/configMgr`.
1. Selecteer de `isEnabled.name` optie om de functie Homepage van middelen in te schakelen. Sla de wijzigingen op.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Open het **[!UICONTROL User Preferences]** dialoogvenster en selecteer **[!UICONTROL Enable Assets Home Page]**. Sla de wijzigingen op.

   ![De elementenstartpagina inschakelen in het dialoogvenster Gebruikersvoorkeuren](assets/Annotation-color.png)

Nadat u de elementenstartpagina hebt ingeschakeld, navigeert u vanuit de navigatiepagina naar de gebruikersinterface Middelen of opent u deze rechtstreeks via de URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam`.

![ervaringskoppeling configureren in de gebruikersinterface voor middelen](assets/config-experience-link.png)

Klik op het pictogram **[!UICONTROL Click here to configure your experience link]** om uw gebruikersnaam, achtergrondafbeelding en profielafbeelding toe te voegen.

De pagina Middelen Home bevat de volgende secties:

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

**Activiteit**: Onder deze sectie geeft de **[!UICONTROL My Activity]** widget recente activiteiten weer die door de aangemelde gebruiker zijn uitgevoerd met elementen (waaronder elementen zonder vertoningen), zoals het uploaden van middelen, downloads, het maken van elementen, bewerkingen, opmerkingen, annotaties en shares.

**Recent**: De **[!UICONTROL Recently Viewed]** widget onder deze sectie toont onlangs betreden entiteiten door de het programma geopende gebruiker, met inbegrip van omslagen, inzamelingen, en projecten.

**Detecteren**: De **[!UICONTROL New]** widget in deze sectie geeft de elementen en uitvoeringen weer die onlangs zijn geüpload naar de implementatie van Elementen.

Om het zuiveren van de gegevens van de gebruikersactiviteit toe te laten, laat **[!UICONTROL DAM Event Purge Service]** van de Manager van de Configuratie toe. Nadat u deze dienst toelaat, worden de activiteiten van de het programma geopende gebruiker die een gespecificeerd aantal overschrijden geschrapt door het systeem.

Het welkomstscherm biedt eenvoudige navigatiehulpmiddelen, zoals pictogrammen op de werkbalk, voor toegang tot mappen, verzamelingen en catalogi.

>[!NOTE]
>
>Als u de [!UICONTROL Day CQ DAM Event Recorder] en [!UICONTROL DAM Event Purge] services inschakelt, worden meer schrijfbewerkingen naar JCR uitgevoerd en wordt het zoeken naar indexering versneld, waardoor de belasting op de Experience Manager-server aanzienlijk toeneemt. De extra belasting op de Experience Manager-server kan van invloed zijn op de prestaties.

>[!CAUTION]
>
>Het vangen, het filtreren, en het zuiveren gebruikersactiviteiten die voor de homepage van Activa worden vereist leggen een overheadkosten op prestaties. Daarom moeten beheerders de startpagina effectief configureren voor doelgebruikers.
>
>Adobe raadt beheerders en gebruikers die bulkbewerkingen uitvoeren aan de functie Startpagina van bedrijfsmiddelen niet te gebruiken om te voorkomen dat gebruikers meer gaan werken. Bovendien kunnen beheerders opnameactiviteiten voor specifieke gebruikers uitsluiten door deze te configureren [!UICONTROL Day CQ DAM Event Recorder] van [!UICONTROL Configuration Manager].
>
>Als u deze functie gebruikt, raadt Adobe u aan de laadfrequentie te laten bepalen op basis van het laden van de server.
