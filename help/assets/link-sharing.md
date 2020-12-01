---
title: Elementen delen via een koppeling
description: Elementen, mappen en verzamelingen delen als een URL.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1f6da1c69ea3b3c3f07e8ac10fd8e1e9c7208158
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 3%

---


# Middelen delen via een koppeling {#asset-link-sharing}

[!DNL Adobe Experience Manager Assets] kunt u elementen, mappen en verzamelingen als een URL delen met leden van uw organisatie en externe entiteiten, waaronder partners en leveranciers. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat ze zich eerst hoeven aan te melden bij [!DNL Assets].

>[!PREREQUISITES]
>
>* U vereist geeft ACL toestemming op de omslag of de activa uit die u als verbinding wilt delen.
>* Om e-mails naar de gebruikers te verzenden, vorm de SMTP serverdetails in de Dienst [van de Post van](#configmailservice)Dag CQ.


## Assets delen {#sharelink}

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op de `/var/dam/share` locatie kunnen de koppelingen weergeven die met hen worden gedeeld.

1. Selecteer in de [!DNL Assets] gebruikersinterface het element dat u wilt delen als koppeling.
1. Klik op het pictogram **[!UICONTROL Share Link]** Elementen ![](assets/do-not-localize/assets_share.png)delen op de werkbalk.

   De koppeling die na het klikken wordt gemaakt, [!UICONTROL Share] wordt vooraf in het [!UICONTROL Share Link] veld weergegeven. De standaardvervaltijd voor de verbinding is één dag.

   ![Dialoogvenster met de koppeling Delen](assets/Link-sharing-dialog-box.png)

   *Afbeelding: Het dialoogvenster voor het delen van elementen als een koppeling.*

   >[!NOTE]
   >
   >Als u koppelingen van de implementatie van uw [!DNL Experience Manager] auteur naar externe entiteiten wilt delen, moet u ervoor zorgen dat u alleen de volgende URL&#39;s (die worden gebruikt voor het delen van koppelingen) beschikbaar maakt voor `GET` aanvragen. Andere URL&#39;s blokkeren vanwege beveiligingsredenen.
   >
   >* `http://[aem_server]:[port]/linkshare.html`
   >* `http://[aem_server]:[port]/linksharepreview.html`
   >* `http://[aem_server]:[port]/linkexpired.html`


1. Ga in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

1. Open de **[!UICONTROL Day CQ Link Externalizer]** configuratie en wijzig de volgende eigenschappen op het **[!UICONTROL Domains]** gebied met de waarden die tegen `local`, `author`, en `publish`worden vermeld. Geef voor de eigenschappen `local` en `author` de URL op voor respectievelijk de lokale instantie en de auteur. Zowel `local` als `author` eigenschappen hebben dezelfde waarde als u één [!DNL Experience Manager] auteurinstantie uitvoert. Geef bij Publicatie-instanties de URL voor de [!DNL Experience Manager] publicatie-instantie op.

1. Typ in het vak E-mailadres van het dialoogvenster **[!UICONTROL Link Sharing]** de e-mail-id van de gebruiker met wie u de koppeling wilt delen. U kunt een of meer gebruikers toevoegen.

   ![Koppelingen naar elementen rechtstreeks delen via het dialoogvenster Koppelen](assets/Asset-Sharing-LinkShareDialog.png)

   *Afbeelding: Koppelingen naar elementen rechtstreeks vanuit het [!UICONTROL Link Sharing] dialoogvenster delen.*

   >[!NOTE]
   >
   >Als u een e-mailadres invoert van een gebruiker die geen lid is van uw organisatie, [!UICONTROL External User] worden de woorden vooraf voorzien van de e-mailid van de gebruiker.

1. Voer in het **[!UICONTROL Subject]** veld een onderwerpregel in.

1. Voer in het **[!UICONTROL Message]** veld een optioneel bericht in.

1. Geef in het **[!UICONTROL Expiration]** veld een vervaldatum en -tijd op waarop de koppeling moet stoppen. De vervaldatum wordt standaard ingesteld voor een week vanaf de datum waarop u de koppeling deelt.

   ![Vervaldatum van gedeelde koppeling instellen](assets/Set-shared-link-expiration.png)

1. Selecteer **[!UICONTROL Allow download of original file]**. Standaard kunnen gebruikers alleen de uitvoeringen downloaden van het element dat u als koppeling deelt.

1. Klik op **[!UICONTROL Share]**. Een bericht bevestigt dat de koppeling via e-mail met de gebruikers wordt gedeeld.

1. Klik op de koppeling in de e-mail die naar de gebruiker is verzonden om het gedeelde element weer te geven. Het gedeelde element wordt op de **[!UICONTROL Adobe Marketing Cloud]** pagina weergegeven.

   ![chlimage_1-260](assets/chlimage_1-545.png)

1. Klik op het gedeelde element om een voorvertoning van het element te genereren. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click **[!UICONTROL Parent Folder]** to return to the parent folder.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] ondersteunt het genereren van een voorvertoning van alleen [de ondersteunde bestandstypen](/help/assets/assets-formats.md). Als andere MIME-typen worden gedeeld, kunt u alleen de elementen downloaden en kunt u geen voorvertoning weergeven.

1. Als u het gedeelde element wilt downloaden, klikt u **[!UICONTROL Select]** op de werkbalk, klikt u op het element en vervolgens klikt u **[!UICONTROL Download]** op de werkbalk.

   ![chlimage_1-262](assets/chlimage_1-547.png)

1. Als u de elementen die u hebt gedeeld als koppelingen wilt weergeven, gaat u naar de [!DNL Assets] gebruikersinterface en klikt u op het [!DNL Experience Manager] logo. Choose **[!UICONTROL Navigation]**. In the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.

1. Als u een element niet wilt delen, selecteert u het en klikt u op **[!UICONTROL Unshare]** de werkbalk. Hierna volgt een bevestigingsbericht. De vermelding voor het element wordt uit de lijst verwijderd.

## CQ-mailservice op dag configureren {#configmailservice}

1. Navigeer op de [!DNL Experience Manager] startpagina naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Van de lijst van de diensten, bepaal de plaats **[!UICONTROL Day CQ Mail Service]**.
1. Click **[!UICONTROL Edit]** beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * hostnaam SMTP-server: hostnaam e-mailserver
   * SMTP-serverpoort: e-mailserverpoort
   * SMTP-gebruiker: gebruikersnaam e-mailserver
   * SMTP-wachtwoord: wachtwoord e-mailserver

   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klik op **[!UICONTROL Save]**.

## Maximale gegevensgrootte configureren {#maxdatasize}

Wanneer u elementen downloadt van de koppeling die wordt gedeeld met de functie voor het delen van koppelingen, [!DNL Experience Manager] wordt de hiërarchie van elementen gecomprimeerd vanuit de opslagplaats en wordt het element vervolgens geretourneerd in een ZIP-bestand. Bij gebrek aan beperkingen van de hoeveelheid gegevens die in een ZIP-bestand kan worden gecomprimeerd, worden enorme hoeveelheden gegevens gecomprimeerd, waardoor fouten in het geheugen in JVM worden veroorzaakt. Om het systeem van een potentiële ontkenning van de dienstaanval toe te schrijven aan deze situatie te beveiligen, vorm de maximumgrootte gebruikend de **[!UICONTROL Max Content Size (uncompressed)]** parameter voor [!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet] in de Manager van de Configuratie. Als de niet-gecomprimeerde grootte van het element de geconfigureerde waarde overschrijdt, worden de verzoeken om het downloaden van het element afgewezen. De standaardwaarde is 100 MB.

1. Click the [!DNL Experience Manager] logo and then go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Van de Console van het Web, bepaal de plaats van de **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuratie.
1. Open de **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuratie in geef wijze uit, en wijzig de waarde van de **[!UICONTROL Max Content Size (uncompressed)]** parameter.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Sla de wijzigingen op.

## Beste werkwijzen en probleemoplossing {#bestpractices}

* Elementmappen of verzamelingen die een witruimte in hun naam bevatten, worden mogelijk niet gedeeld.
* Als gebruikers de gedeelde elementen niet kunnen downloaden, moet u bij de [!DNL Experience Manager] beheerder nagaan wat de [downloadlimiet](#maxdatasize) is.
* Als u geen e-mail met koppelingen naar gedeelde elementen kunt verzenden of als de andere gebruikers uw e-mail niet kunnen ontvangen, raadpleegt u uw [!DNL Experience Manager] beheerder of de [e-mailservice](#configmailservice) is geconfigureerd of niet.
* Als u geen elementen kunt delen via de functie voor het delen van koppelingen, controleert u of u de juiste machtigingen hebt. Zie [Elementen](#sharelink)delen.
* Als een gedeeld element naar een andere locatie wordt verplaatst, werkt de koppeling niet meer. Maak de koppeling opnieuw en deel deze opnieuw met de gebruikers.
