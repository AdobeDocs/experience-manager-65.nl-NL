---
title: AEM Assets Home Page Experience
description: Pas de startpagina van AEM Assets aan voor een uitgebreide ervaring met welkomstschermen, waaronder een momentopname van recente activiteiten rond middelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# AEM Assets Home Page Experience {#aem-assets-home-page-experience}

Pas de Adobe Experience Manager (AEM)-middelenstartpagina aan voor een uitgebreide welkomstscherm, inclusief een momentopname van recente activiteiten rond middelen.

De startpagina van AEM Assets biedt een rijke en gepersonaliseerde ervaring met welkomstschermen, die een momentopname bevat van recente activiteiten, zoals elementen die onlangs zijn weergegeven of geüpload.

De startpagina Middelen is standaard uitgeschakeld. Voer de volgende stappen uit om het in te schakelen:

1. Open AEM Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL DAM DAM-service Gebeurtenisrecorder]** op de dag.
1. Selecteer **[!UICONTROL Enable this service]** om activiteitenopname in te schakelen.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Selecteer in de lijst **[!UICONTROL Gebeurtenistypen]** de gebeurtenissen die moeten worden opgenomen en sla de wijzigingen op.

   >[!CAUTION]
   >
   >Als u de weergaveopties voor het element, de bekeken projecten en de weergegeven verzamelingen inschakelt, wordt het aantal opgenomen gebeurtenissen aanzienlijk verhoogd.

1. Open de service **[!UICONTROL DAM Asset Home Page Feature Flag]** van Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Selecteer de `isEnabled.name` optie om de functie Homepage van middelen in te schakelen. Sla de wijzigingen op.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Open het dialoogvenster **[!UICONTROL Gebruikersvoorkeuren]** en selecteer Startpagina **[!UICONTROL voor elementen]** inschakelen. Sla de wijzigingen op.

   ![De elementenstartpagina inschakelen in het dialoogvenster Gebruikersvoorkeuren](assets/Annotation-color.png)

Nadat u de elementenstartpagina hebt ingeschakeld, navigeert u vanuit de navigatiepagina naar de gebruikersinterface Middelen of opent u deze rechtstreeks via de URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam`.

![ervaringskoppeling configureren in de gebruikersinterface voor middelen](assets/config-experience-link.png)

Klik hier **[!UICONTROL Klik om uw ervaringskoppeling]** te configureren en uw gebruikersnaam, achtergrondafbeelding en profielafbeelding toe te voegen.

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

**Activiteit**: Onder deze sectie geeft de widget **[!UICONTROL Mijn activiteiten]** recente activiteiten weer die door de aangemelde gebruiker zijn uitgevoerd met elementen (waaronder elementen zonder vertoningen), zoals het uploaden van middelen, downloads, het maken van elementen, bewerkingen, opmerkingen, annotaties en shares.

**Recent**: De **[!UICONTROL onlangs Bekeken]** widget onder deze sectie toont onlangs betreden entiteiten door de het programma geopende gebruiker, met inbegrip van omslagen, inzamelingen, en projecten.

**Detecteren**: De **[!UICONTROL nieuwe]** widget in deze sectie geeft de elementen en vertoningen weer die onlangs naar de instantie AEM Assets zijn geüpload.

Om het zuiveren van de gegevens van de gebruikersactiviteit toe te laten, laat de **[!UICONTROL Dienst]** van de Weigering van de Gebeurtenis DAM van de Manager van de Configuratie toe. Nadat u deze dienst toelaat, worden de activiteiten van de het programma geopende gebruiker die een gespecificeerd aantal overschrijden geschrapt door het systeem.

Het welkomstscherm biedt eenvoudige navigatiehulpmiddelen, zoals pictogrammen op de werkbalk, voor toegang tot mappen, verzamelingen en catalogi.

>[!NOTE]
>
>Als u de services [!UICONTROL Day CQ DAM Event Recorder] en [!UICONTROL DAM Event Purge] inschakelt, nemen schrijfbewerkingen naar JCR toe en wordt de zoekindex aanzienlijk verhoogd, waardoor de belasting op de AEM-server aanzienlijk toeneemt. De extra belasting op de AEM-server kan van invloed zijn op de prestaties.

>[!CAUTION]
>
>Het vangen, het filtreren, en het zuiveren gebruikersactiviteiten die voor de homepage van Activa worden vereist leggen een overheadkosten op prestaties. Daarom moeten beheerders de startpagina effectief configureren voor doelgebruikers.
>
>Adobe raadt beheerders en gebruikers die bulkbewerkingen uitvoeren aan de functie Startpagina van bedrijfsmiddelen niet te gebruiken om te voorkomen dat gebruikers meer gaan werken. Daarnaast kunnen beheerders opnameactiviteiten voor specifieke gebruikers uitsluiten door CQ DAM-gebeurtenisrecorder [!UICONTROL op] dag te configureren in [!UICONTROL Configuratiebeheer].
>
>Als u deze functie gebruikt, raadt Adobe u aan de laadfrequentie te laten bepalen op basis van het laden van de server.
