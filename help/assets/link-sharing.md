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

[!DNL Adobe Experience Manager Assets] kunt u elementen, mappen en verzamelingen als een URL delen met leden van uw organisatie en externe entiteiten, waaronder partners en leveranciers. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij [!DNL Assets].

>[!PREREQUISITES]
>
>* U vereist geeft ACL toestemming op de omslag of de activa uit die u als verbinding wilt delen.
>* Om e-mails naar de gebruikers te verzenden, configureert u de SMTP-servergegevens in [Day CQ Mail Service](#configmailservice).


## Assets delen {#sharelink}

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op `/var/dam/share`-locatie kunnen de koppelingen weergeven die met hen worden gedeeld.

1. Selecteer in de gebruikersinterface [!DNL Assets] het element dat u wilt delen als koppeling.
1. Klik op **[!UICONTROL Share Link]** ![pictogram Elementen delen](assets/do-not-localize/assets_share.png) op de werkbalk.

   De koppeling die wordt gemaakt nadat op [!UICONTROL Share] is geklikt, wordt vooraf weergegeven in het veld [!UICONTROL Share Link]. De standaardvervaltijd voor de verbinding is één dag.

   ![Dialoogvenster met de koppeling Delen](assets/Link-sharing-dialog-box.png)

   *Afbeelding: Het dialoogvenster voor het delen van elementen als een koppeling.*

   >[!NOTE]
   >
   >Als u verbindingen van uw [!DNL Experience Manager] plaatsing van de Auteur aan externe entiteiten wilt delen, zorg ervoor dat u slechts volgende URLs (die voor verbinding het delen worden gebruikt) voor `GET` verzoeken blootstelt slechts. Andere URL&#39;s blokkeren vanwege beveiligingsredenen.
   >
   >* `http://[aem_server]:[port]/linkshare.html`
   >* `http://[aem_server]:[port]/linksharepreview.html`
   >* `http://[aem_server]:[port]/linkexpired.html`


1. In [!DNL Experience Manager] interface, toegang **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

1. Open de **[!UICONTROL Day CQ Link Externalizer]** configuratie en wijzig de volgende eigenschappen in het **[!UICONTROL Domains]** gebied met de waarden die tegen `local`, `author`, en `publish` worden vermeld. Geef voor de eigenschappen `local` en `author` de URL op voor respectievelijk de lokale instantie en de instantie van de auteur. Zowel `local` als `author` eigenschappen hebben de zelfde waarde als u één enkele [!DNL Experience Manager] auteursinstantie in werking stelt. Geef voor Publicatie-instanties de URL op voor de publicatie-instantie [!DNL Experience Manager].

1. Typ in het vak E-mailadres van het dialoogvenster **[!UICONTROL Link Sharing]** de e-mail-id van de gebruiker met wie u de koppeling wilt delen. U kunt een of meer gebruikers toevoegen.

   ![Koppelingen naar elementen rechtstreeks delen via het dialoogvenster Koppelen](assets/Asset-Sharing-LinkShareDialog.png)

   *Afbeelding: Koppelingen naar elementen rechtstreeks vanuit het  [!UICONTROL Link Sharing] dialoogvenster delen.*

   >[!NOTE]
   >
   >Als u een e-mailadres opgeeft van een gebruiker die geen lid is van uw organisatie, wordt het woord [!UICONTROL External User] voorafgegaan door de e-mailid van de gebruiker.

1. Voer in het veld **[!UICONTROL Subject]** een onderwerpregel in.

1. Voer in het veld **[!UICONTROL Message]** een optioneel bericht in.

1. Geef in het veld **[!UICONTROL Expiration]** een vervaldatum en -tijd op waarop de koppeling moet stoppen met werken. De vervaldatum wordt standaard ingesteld voor een week vanaf de datum waarop u de koppeling deelt.

   ![Vervaldatum van gedeelde koppeling instellen](assets/Set-shared-link-expiration.png)

1. Selecteer **[!UICONTROL Allow download of original file]** als u wilt dat gebruikers het oorspronkelijke element samen met de uitvoeringen kunnen downloaden. Standaard kunnen gebruikers alleen de uitvoeringen downloaden van het element dat u als koppeling deelt.

1. Klik op **[!UICONTROL Share]**. Een bericht bevestigt dat de koppeling via e-mail met de gebruikers wordt gedeeld.

1. Klik op de koppeling in de e-mail die naar de gebruiker is verzonden om het gedeelde element weer te geven. Het gedeelde element wordt weergegeven op de pagina **[!UICONTROL Adobe Marketing Cloud]**.

   ![chlimage_1-260](assets/chlimage_1-545.png)

1. Klik op het gedeelde element om een voorvertoning van het element te genereren. Als u de voorvertoning wilt sluiten en wilt terugkeren naar de pagina **[!UICONTROL Marketing Cloud]**, klikt u op **[!UICONTROL Back]** op de werkbalk. Als u een map hebt gedeeld, klikt u op **[!UICONTROL Parent Folder]** om terug te keren naar de bovenliggende map.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   >
   >[!DNL Experience Manager] ondersteunt het genereren van een voorvertoning van alleen  [de ondersteunde bestandstypen](/help/assets/assets-formats.md). Als andere MIME-typen worden gedeeld, kunt u alleen de elementen downloaden en kunt u geen voorvertoning weergeven.

1. Als u het gedeelde element wilt downloaden, klikt u op **[!UICONTROL Select]** op de werkbalk, klikt u op het element en vervolgens op **[!UICONTROL Download]** op de werkbalk.

   ![chlimage_1-262](assets/chlimage_1-547.png)

1. Als u de elementen wilt weergeven die u als koppelingen hebt gedeeld, gaat u naar de [!DNL Assets]-gebruikersinterface en klikt u op het [!DNL Experience Manager]-logo. Choose **[!UICONTROL Navigation]**. Kies **[!UICONTROL Shared Links]** in het navigatievenster om een lijst met gedeelde elementen weer te geven.

1. Als u een element niet wilt delen, selecteert u het en klikt u op **[!UICONTROL Unshare]** op de werkbalk. Hierna volgt een bevestigingsbericht. De vermelding voor het element wordt uit de lijst verwijderd.

## CQ-mailservice op dag configureren {#configmailservice}

1. Navigeer op de startpagina [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Zoek in de lijst met services **[!UICONTROL Day CQ Mail Service]**.
1. Klik op **[!UICONTROL Edit]** naast de service en configureer de volgende parameters voor **[!UICONTROL Day CQ Mail Service]** met de details vermeld onder hun naam:

   * hostnaam SMTP-server: hostnaam e-mailserver
   * SMTP-serverpoort: e-mailserverpoort
   * SMTP-gebruiker: gebruikersnaam e-mailserver
   * SMTP-wachtwoord: wachtwoord e-mailserver

   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klik op **[!UICONTROL Save]**.

## Maximale gegevensgrootte {#maxdatasize} configureren

Wanneer u elementen downloadt van de koppeling die wordt gedeeld met de functie voor het delen van koppelingen, wordt de elementenhiërarchie van de opslagplaats gecomprimeerd en wordt het element vervolgens in een ZIP-bestand geretourneerd. [!DNL Experience Manager] Bij gebrek aan beperkingen van de hoeveelheid gegevens die in een ZIP-bestand kan worden gecomprimeerd, worden enorme hoeveelheden gegevens gecomprimeerd, waardoor fouten in het geheugen in JVM worden veroorzaakt. Om het systeem van een potentiële ontkenning van de dienstaanval wegens deze situatie te beveiligen, vorm de maximumgrootte gebruikend de **[!UICONTROL Max Content Size (uncompressed)]** parameter voor [!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet] in de Manager van de Configuratie. Als de niet-gecomprimeerde grootte van het element de geconfigureerde waarde overschrijdt, worden de verzoeken om het downloaden van het element afgewezen. De standaardwaarde is 100 MB.

1. Klik op het [!DNL Experience Manager]-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Van de Console van het Web, bepaal de plaats van de **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuratie.
1. Open de **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuratie in geef wijze uit, en wijzig de waarde van de **[!UICONTROL Max Content Size (uncompressed)]** parameter.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Sla de wijzigingen op.

## Aanbevolen procedures en problemen oplossen {#bestpractices}

* Elementmappen of verzamelingen die een witruimte in hun naam bevatten, worden mogelijk niet gedeeld.
* Als gebruikers de gedeelde elementen niet kunnen downloaden, vraagt u bij uw [!DNL Experience Manager]-beheerder wat de [downloadlimieten](#maxdatasize) zijn.
* Als u geen e-mail met koppelingen naar gedeelde elementen kunt verzenden of als de andere gebruikers uw e-mail niet kunnen ontvangen, raadpleegt u uw [!DNL Experience Manager]-beheerder als de [e-mailservice](#configmailservice) is geconfigureerd of niet.
* Als u geen elementen kunt delen via de functie voor het delen van koppelingen, controleert u of u de juiste machtigingen hebt. Zie [assets delen](#sharelink).
* Als een gedeeld element naar een andere locatie wordt verplaatst, werkt de koppeling niet meer. Maak de koppeling opnieuw en deel deze opnieuw met de gebruikers.
