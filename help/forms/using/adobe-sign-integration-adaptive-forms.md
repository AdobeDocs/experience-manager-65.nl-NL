---
title: Adobe-ondertekening integreren met AEM-formulieren
seo-title: Adobe-ondertekening integreren met AEM-formulieren
description: Leer hoe u Adobe Sign for AEM Forms configureert
seo-description: Leer hoe u Adobe Sign for AEM Forms configureert
uuid: e5049775-fb6c-4228-9823-e6a2811460da
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 1f28b257-5419-4a21-a54a-b20bf35530ac
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Adobe-ondertekening integreren met AEM-formulieren{#integrate-adobe-sign-with-aem-forms}

Met Adobe Sign kunnen workflows voor e-handtekeningen worden gebruikt voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard Adobe-scenario voor ondertekenen en aanpassen van formulieren vult een gebruiker een adaptief formulier in om een **aanvraag voor een service** in te dienen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt Adobe Sign om de goedgekeurde toepassing te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign met AEM Forms integreren.

Als u Adobe Sign with AEM Forms wilt gebruiken, configureert u Adobe Sign in AEM Cloud Services:

## Vereisten {#prerequisites}

U hebt het volgende nodig om Adobe Sign with AEM Forms te integreren:

* Een actieve [Adobe Sign-ontwikkelaarsaccount.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Een AEM Forms-server met [SSL ingeschakeld](/help/sites-administering/ssl-by-default.md) .
* Een API-toepassing [voor](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md)ondertekening door Adobe.
* Referenties (client-id en clientgeheim) van de Adobe Sign API-toepassing.

## Adobe-ondertekening met AEM-formulieren configureren {#configure-adobe-sign-with-aem-forms}

Nadat aan de voorwaarden is voldaan, voert u de volgende stappen uit om Adobe Sign with AEM Forms in de Author-instantie te configureren:

1. Navigeer in de auteur van AEM Forms naar **Gereedschappen** ![](assets/hammer.png) > **Algemeen** > **Configuratiebrowser**.
1. Tik op de pagina **[!UICONTROL Configuration Browser]** op **[!UICONTROL Create]**.
1. Geef in het dialoogvenster **[!UICONTROL Configuratie]** maken een **[!UICONTROL titel]** op voor de configuratie, schakel **[!UICONTROL Cloudconfiguraties]** in en tik op **[!UICONTROL Maken]**. Er wordt een configuratiecontainer voor cloudservices gemaakt.
1. Ga naar **Gereedschappen** ![](assets/hammer.png) > **Cloud Services** > **Adobe Sign** en selecteer de configuratiecontainer die u in de bovenstaande stap hebt gemaakt.

   >[!NOTE]
   >
   >Zorg ervoor dat de URL van de configuratiepagina voor cloudservices begint met **HTTPS**. Als dat niet het geval is, [schakelt u SSL](/help/sites-administering/ssl-by-default.md) in voor de AEM Forms-server.

1. Tik op de configuratiepagina op **[!UICONTROL Maken]** om de Adobe-ondertekeningsconfiguratie in AEM Forms te maken.
1. Geef op het tabblad **[!UICONTROL Algemeen]** van de pagina Configuratie **[!UICONTROL Adobe-ondertekening]** maken een **naam** op voor de configuratie en tik op **Volgende**. U kunt desgewenst een titel opgeven en naar een miniatuur voor de configuratie bladeren.

   Kopieer de URL in het huidige browservenster. Adobe Sign application with AEM Forms is vereist.

1. Configureer overige instellingen voor de Adobe-toepassing voor ondertekenen:

   1. Open een browservenster en meld u aan bij de Adobe Sign-ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor AEM-formulieren is geconfigureerd en tik op OAuth configureren voor toepassing.
   1. Voeg in het vak URL **** omleiden de eerder gekopieerde HTTPS-URL toe en klik op **Opslaan**.
   1. Schakel de volgende OAuth-instellingen in voor de toepassing Adobe Sign en klik op **Opslaan**.
   * samenvoeging_read
   * samenvoeging_write
   * aggregatie_verzenden
   * widget_write
   * workflow_read
   Voor geleidelijke informatie om montages OAuth voor een toepassing van het Teken van Adobe te vormen en de sleutels te verkrijgen, zie de montages van de Auth van de [Vorm voor de documentatie van de toepassingsontwikkelaar](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobeio/adobeio-documentation/master/sign/gstarted/configure_oauth.md) .

   ![OAuth Config](assets/oauthconfig_new.png)

1. Ga terug naar de pagina **Adobe Sign Configuration** . Op het tabblad **[!UICONTROL Instellingen]** vermeldt het veld **[!UICONTROL OAuth URL]** de volgende standaard-URL:

   https://secure.na1.echosign.com/public/oauth

   waarbij:

   **na1** verwijst naar het standaard gegevensbestandaandeel.

   U kunt de waarde voor het delen van de database wijzigen. Start de server opnieuw om de nieuwe waarde voor de databaseschijf te kunnen gebruiken.

1. Geef de **client-id** (ook toepassings-id genoemd) en het **clientgeheim** op. Schakel de optie Adobe-ondertekening **inschakelen voor bijlagen ook** in om bestanden die zijn gekoppeld aan een adaptief formulier, toe te voegen aan het corresponderende Adobe-document dat is verzonden voor ondertekening.

   Tik op **[!UICONTROL Verbinding maken met Adobe-ondertekening]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van een Adobe Sign-toepassing.

   Tik op **[!UICONTROL Maken]** om de Adobe-ondertekeningsconfiguratie te maken.

1. Open AEM-webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Open **Forms Common Configuration Service.**
1. In het veld **Toestaan** **selecteert** u Alle gebruikers. Alle gebruikers, anoniem of aangemeld, kunnen een voorbeeld van bijlagen bekijken, formulieren verifiëren en ondertekenen en op **Opslaan klikken.** De instantie Auteur is geconfigureerd voor gebruik van Adobe Sign.
1. Meld u aan bij de instantie [Publiceren](/help/sites-deploying/deploy.md) en open de volgende URL:

   `https://<server-name>:<port>/libs/granite/configurations/content/view.html/conf`

1. Herhaal stap 1 tot en met 12 om Adobe Sign with AEM Forms te configureren. Gebruik dezelfde titel voor configuratie (zoals opgegeven in stap 3) en dezelfde naam (zoals opgegeven in stap 6) om de instellingen te repliceren die op de instantie Auteur zijn geconfigureerd.

   Adobe Sign is nu geïntegreerd met AEM Forms en klaar voor gebruik in adaptieve formulieren. Als u de Adobe Sign-service in een adaptieve vorm [wilt](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)gebruiken, geeft u de hierboven gemaakte configuratiecontainer op in adaptieve formuliereigenschappen.

## Adobe-ondertekeningsplanner configureren om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Een adaptief formulier dat geschikt is voor ondertekening door Adobe wordt alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. Standaard wordt de respons van de ondertekenaar van de Adobe Sign Scheduler-services na elke 24 uur gecontroleerd. U kunt het standaardinterval voor uw milieu veranderen. Voer de volgende stappen uit om het standaardinterval te wijzigen:

1. Meld u met beheerdersreferenties aan de AEM Forms-server aan en navigeer naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.

   U kunt ook de volgende URL openen in een browservenster:
   `https://[localhost]:'port'/system/console/configMgr`

1. Zoek en open de optie **Adobe Sign Configuration Service** . Geef een [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) op in het veld **Uitdrukking planner voor** statusupdate en klik op **Opslaan**. Bijvoorbeeld, om de configuratieservice dagelijks om 00:00 uur in werking te stellen, specificeer `0 0 0 1/1 * ? *` op het gebied van de Uitdrukking van de Planner van de Update van de **Status** .

Het standaardinterval voor het synchroniseren van de status van Adobe Sign is nu gewijzigd.

## Verwante artikelen {#related-articles}

* [Adobe Sign in een adaptief formulier gebruiken](../../forms/using/working-with-adobe-sign.md)
* [Adobe-ondertekening gebruiken met AEM-formulieren (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Adobe-ondertekening integreren met AEM-formulieren](../../forms/using/adobe-sign-integration-adaptive-forms.md)

