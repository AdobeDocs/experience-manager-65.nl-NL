---
title: Een URL naar gedeelde elementen genereren
description: In dit artikel wordt beschreven hoe u elementen, mappen en verzamelingen in AEM Assets als een URL naar externe partijen kunt delen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Middelen delen via een koppeling {#asset-link-sharing}

Met Adobe Experience Manager (AEM) kunt u elementen, mappen en verzamelingen als een URL delen met leden van uw organisatie en externe entiteiten, waaronder partners en leveranciers. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij AEM Assets.

>[!NOTE]
>
>U vereist geeft ACL toestemming op de omslag of de activa uit die u als verbinding wilt delen.

## Assets delen {#sharelink}

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op de `/var/dam/share` locatie kunnen de koppelingen weergeven die met hen worden gedeeld.

>[!NOTE]
>
>Voordat u een koppeling met gebruikers deelt, moet u ervoor zorgen dat Day CQ Mail Service is geconfigureerd. Er treedt een fout op als u een koppeling probeert te delen zonder eerst de Day CQ Mail Service [te](/help/assets/link-sharing.md#configmailservice)configureren.

1. Selecteer in de gebruikersinterface Elementen het element dat u wilt delen als een koppeling.
1. Klik/tik op de werkbalk op Koppeling **** delen ![assets_share](assets/assets_share.png).

   Er wordt automatisch een elementkoppeling gemaakt in het veld Koppeling **** delen. Kopieer deze koppeling en deel deze met de gebruikers. De standaardvervaltijd voor de verbinding is één dag.

   ![Dialoogvenster met de koppeling Delen](assets/Link-sharing-dialog-box.png)

   *Afbeelding: Het dialoogvenster voor het delen van elementen als een koppeling.*

   Alternatief, ga te werk om stappen 3-7 van deze procedure uit te voeren om e-mailontvangers toe te voegen, de vervaltijd voor de verbinding te vormen, en het van de dialoog te verzenden.

   >[!NOTE]
   >
   >Als u koppelingen van uw AEM-auteur naar externe entiteiten wilt delen, dient u ervoor te zorgen dat alleen de volgende URL&#39;s (die worden gebruikt voor het delen van koppelingen) beschikbaar worden gemaakt voor `GET` aanvragen. Andere URL&#39;s blokkeren om de beveiliging van AEM-auteur te garanderen.
   >
   >* http://&lt;aem_server>:&lt;port>/linkshare.html
   * http://&lt;aem_server>:&lt;port>/linksharepreview.html
   * http://&lt;aem_server>:&lt;port>/linkexpired.html


   >[!NOTE]
   Als een gedeeld element naar een andere locatie wordt verplaatst, werkt de koppeling niet meer. Maak de koppeling opnieuw en deel deze opnieuw met de gebruikers.

1. Ga in de AEM-interface naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.

1. Open de **[!UICONTROL Configuratie van de Verbinding van CQ van de Dag External]** en wijzig de volgende eigenschappen op het gebied van **[!UICONTROL Domeinen]** met de waarden die tegen `local`, `author`, en `publish`worden vermeld. Geef voor de eigenschappen `local` en `author` de URL op voor respectievelijk de lokale instantie en de auteur. Zowel `local` als `author` eigenschappen hebben dezelfde waarde als u één instantie van de Auteur van de Manager van de Ervaring in werking stelt. Geef `publish`bijvoorbeeld de URL op voor het publicatieexemplaar van Experience Manager.

1. In the email address box of the **[!UICONTROL Link Sharing]** dialog, type the email ID of the user you want to share the link with. U kunt de koppeling ook delen met meerdere gebruikers.

   Als de gebruiker lid is van uw organisatie, selecteert u de e-mailid van de gebruiker in de voorgestelde e-mailadressen die worden weergegeven in de lijst onder het invoergebied. Voor een externe gebruiker typt u de volledige e-mailid en selecteert u deze in de lijst.

   Als u wilt dat e-mailberichten naar gebruikers kunnen worden verzonden, configureert u de SMTP-servergegevens in [Day CQ Mail Service](#configmailservice).

   ![Koppelingen naar elementen rechtstreeks delen via het dialoogvenster Koppelen](assets/Asset-Sharing-LinkShareDialog.png)

   *Afbeelding: Koppelingen naar elementen rechtstreeks delen via het dialoogvenster[!UICONTROL Delen]van koppeling.*

   >[!NOTE]
   Als u een e-mailadres invoert van een gebruiker die geen lid is van uw organisatie, wordt het woord [!UICONTROL Externe Gebruiker] vooraf voorzien van de e-mailid van de gebruiker.

1. Voer in het veld **[!UICONTROL Onderwerp]** een onderwerp in voor het element dat u wilt delen.

1. Voer in het veld **[!UICONTROL Bericht]** een optioneel bericht in.

1. Geef in het veld **[!UICONTROL Verlopen]** een vervaldatum en -tijd voor de koppeling op met de datumkiezer. De vervaldatum wordt standaard ingesteld voor een week vanaf de datum waarop u de koppeling deelt.

   ![Vervaldatum van gedeelde koppeling instellen](assets/Set-shared-link-expiration.png)

1. Als u gebruikers de oorspronkelijke afbeelding samen met de uitvoeringen wilt laten downloaden, selecteert u **[!UICONTROL Downloaden van origineel bestand]** toestaan.

   >[!NOTE]
   Standaard kunnen gebruikers alleen de uitvoeringen downloaden van het element dat u als koppeling deelt.

1. Klik op **[!UICONTROL Delen]**. Een bericht bevestigt dat de koppeling via e-mail met de gebruikers wordt gedeeld.
1. Als u het gedeelde element wilt weergeven, klikt of tikt u op de koppeling in het e-mailbericht dat naar de gebruiker is verzonden. Het gedeelde element wordt weergegeven op de pagina **[!UICONTROL Adobe Marketing Cloud]** .

   ![chlimage_1-260](assets/chlimage_1-545.png)

   Als u wilt schakelen naar de lijstweergave, klikt of tikt u op de layoutoptie op de werkbalk.

1. Als u een voorvertoning van de asset wilt genereren, klikt of tikt u op de gedeelde asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click/tap **[!UICONTROL Parent Folder]** to return to the parent folder.

   ![chlimage_1-261](assets/chlimage_1-546.png)

   >[!NOTE]
   AEM ondersteunt het genereren van een voorvertoning van elementen van deze MIME-typen: JPG, PNG, GIF, BMP, INDD, PDF en PPT. U kunt alleen de elementen van de andere MIME-typen downloaden.

1. Als u het gedeelde element wilt downloaden, tikt u op **[!UICONTROL Selecteren]** op de werkbalk, klikt of tikt u op het element en klikt of tikt u op **[!UICONTROL Downloaden]** op de werkbalk.

   ![chlimage_1-262](assets/chlimage_1-547.png)

1. Als u de elementen die u hebt gedeeld als koppelingen wilt weergeven, gaat u naar de interface Elementen en tikt u op het logo van Experience Manager. Kies **[!UICONTROL Navigatie]** in de lijst om het navigatievenster weer te geven.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. Als u een element niet meer wilt delen, selecteert u het en tikt u op Delen **[!UICONTROL opheffen]** of klikt u op de werkbalk. Hierna volgt een bevestigingsbericht. De vermelding voor het element wordt uit de lijst verwijderd.

## CQ-mailservice op dag configureren {#configmailservice}

1. Navigeer op de startpagina van Experience Manager naar **[!UICONTROL Extra]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.
1. Zoek vanuit de lijst met services de **[!UICONTROL Day CQ Mail Service]**.
1. Tap **[!UICONTROL Edit]** beside the service, and configure the following parameters for **[!UICONTROL Day CQ Mail Service]** with the details mentioned against their names:

   * hostnaam SMTP-server: hostnaam e-mailserver
   * SMTP-serverpoort: e-mailserverpoort
   * SMTP-gebruiker: gebruikersnaam e-mailserver
   * SMTP-wachtwoord: wachtwoord e-mailserver
   ![chlimage_1-263](assets/chlimage_1-548.png)

1. Klik op **[!UICONTROL Opslaan]** of tik op Opslaan.

## Maximale gegevensgrootte configureren {#maxdatasize}

Wanneer u elementen downloadt van de koppeling die wordt gedeeld met de functie voor het delen van koppelingen, comprimeert AEM de hiërarchie van elementen uit de gegevensopslagruimte en retourneert het element vervolgens in een ZIP-bestand. Bij gebrek aan beperkingen van de hoeveelheid gegevens die in een ZIP-bestand kan worden gecomprimeerd, worden enorme hoeveelheden gegevens gecomprimeerd, waardoor fouten in het geheugen in JVM worden veroorzaakt. Om het systeem van een potentiële ontkenning van de dienstaanval toe te schrijven aan deze situatie te beveiligen, vorm de maximumgrootte gebruikend de **[!UICONTROL Max (ongecomprimeerde)]** parameter van de Grootte van de Inhoud voor [!UICONTROL Dag CQ DAM Adhoc Servlet] van de Volmacht van het Aandeel van Activa in de Manager van de Configuratie. Als de niet-gecomprimeerde grootte van het element de geconfigureerde waarde overschrijdt, worden de verzoeken om het downloaden van het element afgewezen. De standaardwaarde is 100 MB.

1. Klik of tik op het AEM-logo en ga vervolgens naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.
1. Zoek in de webconsole de configuratie van de **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** .
1. Open de configuratie van **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** in de bewerkingsmodus en wijzig de waarde van de parameter **[!UICONTROL Max Content Size (niet-gecomprimeerd)]**.

   ![chlimage_1-264](assets/chlimage_1-549.png)

1. Sla de wijzigingen op.

## Beste werkwijzen en probleemoplossing {#bestpractices}

* Elementmappen of verzamelingen die een witruimte in hun naam bevatten, worden mogelijk niet gedeeld.
* Als gebruikers de gedeelde elementen niet kunnen downloaden, vraagt u de AEM-beheerder na welke [downloadlimieten](#maxdatasize) gelden.
* Als u geen e-mail met koppelingen naar gedeelde elementen kunt verzenden of als de andere gebruikers uw e-mail niet kunnen ontvangen, raadpleegt u uw AEM-beheerder als de [e-mailservice](#configmailservice) is geconfigureerd of niet.
* Als u geen elementen kunt delen via de functie voor het delen van koppelingen, controleert u of u de juiste machtigingen hebt. Zie [Elementen](#sharelink)delen.
