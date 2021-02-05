---
title: Adobe Sign integreren met AEM Forms
seo-title: Adobe Sign integreren met AEM Forms
description: Leer hoe u Adobe Sign for AEM Forms configureert
seo-description: Leer hoe u Adobe Sign for AEM Forms configureert
uuid: e5049775-fb6c-4228-9823-e6a2811460da
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 1f28b257-5419-4a21-a54a-b20bf35530ac
docset: aem65
translation-type: tm+mt
source-git-commit: fd9ee8e4eb35bd5d303d7bbdd9660a94c54925ff
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---


# [!DNL Adobe Sign] integreren met AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard [!DNL Adobe Sign]- en adaptief-formulierscenario vult een gebruiker een adaptief formulier in om **een service aan te vragen**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Sign] om de goedgekeurde toepassing te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u [!DNL Adobe Sign] integreren met AEM [!DNL Forms].

Als u [!DNL Adobe Sign] wilt gebruiken met AEM [!DNL Forms], configureert u [!DNL Adobe Sign] in AEM Cloud Services:

## Vereisten {#prerequisites}

U hebt het volgende nodig om [!DNL Adobe Sign] te integreren met AEM [!DNL Forms]:

* Een actieve [Adobe Sign-ontwikkelaarsaccount.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Een [SSL ingeschakeld](/help/sites-administering/ssl-by-default.md) AEM [!DNL Forms] server.
* An [Adobe Sign API application](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Referenties (client-id en clientgeheim) van [!DNL Adobe Sign] API-toepassing.
* Bij het opnieuw vormen, verwijder de bestaande [!DNL Adobe Sign] configuratie uit zowel auteur als publiceer instanties.
* Gebruik [identieke crypto key](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur en publiceer instanties.

## [!DNL Adobe Sign] configureren met AEM [!DNL Forms] {#configure-adobe-sign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit om [!DNL Adobe Sign] met AEM [!DNL Forms] op de instantie van de Auteur te vormen:

1. Navigeer op AEM [!DNL Forms] auteurinstantie naar **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Tik op de pagina **[!UICONTROL Configuration Browser]** op **[!UICONTROL Create]**.
   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** op voor de configuratie, schakel **[!UICONTROL Cloud Configurations]** in en tik **[!UICONTROL Create]**. Er wordt een configuratiecontainer voor cloudservices gemaakt.
1. Navigeer naar **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** en selecteer de configuratiecontainer die u in de bovenstaande stap hebt gemaakt.

   >[!NOTE]
   >
   >U kunt of stappen 1-4 uitvoeren om een nieuwe configuratiecontainer tot stand te brengen en een [!DNL Adobe Sign] configuratie in de container tot stand te brengen of de bestaande `global` omslag in **Tools** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** te gebruiken. Als u de configuratie maakt in de nieuwe configuratiecontainer, moet u de naam van de container opgeven in het veld **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

   >[!NOTE]
   Zorg ervoor dat de URL van de configuratiepagina voor cloudservices begint met **HTTPS**. Zo niet, [schakel SSL](/help/sites-administering/ssl-by-default.md) in voor AEM [!DNL Forms]-server.

1. Tik op de configuratiepagina op **[!UICONTROL Create]** om [!DNL Adobe Sign]-configuratie te maken in AEM [!DNL Forms].
1. Geef op het tabblad **[!UICONTROL General]** van de pagina **[!UICONTROL Create Adobe Sign Configuration]** een **[!UICONTROL Name]** op voor de configuratie en tik **[!UICONTROL Next]**. U kunt desgewenst een titel opgeven en naar een miniatuur voor de configuratie bladeren.

1. Kopieer de URL in het huidige browservenster naar een laptop. Het is vereist om [!DNL Adobe Sign] toepassing met AEM[!DNL Forms] te vormen.

1. Configureer OAuth-instellingen voor de toepassing [!DNL Adobe Sign]:

   1. Open een browservenster en meld u aan bij de [!DNL Adobe Sign]-ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor AEM [!DNL Forms] wordt geconfigureerd en tik **[!UICONTROL Configure OAuth for Application]**.
   1. Kopieer de **[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** naar een laptop.
   1. Voeg in het tekstvak **[!UICONTROL Redirect URL]** de HTTPS-URL toe die u in de vorige stap hebt gekopieerd.
   1. Schakel de volgende OAuth-instellingen in voor de toepassing [!DNL Adobe Sign] en klik op **[!UICONTROL Save]**.
   * samenvoeging_read
   * samenvoeging_write
   * aggregatie_verzenden
   * widget_write
   * workflow_read

   Voor geleidelijke informatie om montages OAuth voor een [!DNL Adobe Sign] toepassing te vormen en de sleutels te verkrijgen, zie [montages van Auth voor de toepassing ](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaardocumentatie vormen.

   ![OAuth Config](assets/oauthconfig_new.png)

1. Ga terug naar de **[!UICONTROL Create Adobe Sign Configuration]** pagina. Op het tabblad **[!UICONTROL Settings]** vermeldt het veld **[!UICONTROL OAuth URL]** de volgende standaard-URL:

   https://secure.na1.echosign.com/public/oauth

   waarbij:

   **na1** verwijst naar het standaard gegevensbestandaandeel.

   U kunt de waarde voor het delen van de database wijzigen. Start de server opnieuw om de nieuwe waarde voor de databaseschijf te kunnen gebruiken.

   >[!NOTE]
   Zorg ervoor dat de auteur en de publicatie van instantieconfiguraties naar hetzelfde niveau verwijzen. Als u meerdere Adobe Sign-configuraties voor een organisatie maakt, moet u ervoor zorgen dat alle configuraties hetzelfde segment gebruiken.

1. Geef de **Client ID** (ook wel toepassings-id genoemd) op en **Client Secret** gekopieerd in stap 8. Selecteer de optie **[!UICONTROL Enable Adobe Sign for attachments also]** om bestanden die aan een adaptief formulier zijn gekoppeld, toe te voegen aan het corresponderende [!DNL Adobe Sign]-document dat ter ondertekening is verzonden.

   Tik op **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van de [!DNL Adobe Sign]-toepassing.

   Tik **[!UICONTROL Create]** om de [!DNL Adobe Sign] configuratie tot stand te brengen.

1. Open AEM webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Open **[!UICONTROL Forms Common Configuration Service].**
1. In het **[!UICONTROL Allow]** gebied, **select** Alle gebruikers - Alle gebruikers, anoniem of het programma geopend, kunnen voorproef gehechtheid, vormen verifiëren en ondertekenen, en **[!UICONTROL Save]klikken.** De instantie van de auteur wordt gevormd om te gebruiken  [!DNL Adobe Sign].
1. Publiceer de configuratie.
1. Gebruik [replicatie](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/replication.html) om identieke configuratie op overeenkomstige te creëren publiceer instanties.

[!DNL Adobe Sign] is nu geïntegreerd met AEM [!DNL Forms] en klaar voor gebruik in adaptieve formulieren. Als u de Adobe Sign-service in een adaptieve vorm wilt [gebruiken, geeft u de hierboven gemaakte configuratiecontainer op in adaptieve formuliereigenschappen.](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)



## Configureer [!DNL Adobe Sign]-planner om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Een adaptief formulier met [!DNL Adobe Sign] wordt alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. Standaard wordt de respons van de ondertekenaar van de [!DNL Adobe Sign]-planningsservices na elke 24 uur gecontroleerd. U kunt het standaardinterval voor uw milieu veranderen. Voer de volgende stappen uit om het standaardinterval te wijzigen:

1. Meld u aan bij AEM [!DNL Forms]-server met beheerdersreferenties en navigeer naar **Extra** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   U kunt ook de volgende URL openen in een browservenster:
   `https://[localhost]:'port'/system/console/configMgr`

1. Zoek en open de optie **[!UICONTROL Adobe Sign Configuration Service]**. Geef een [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) op in het veld **[!UICONTROL Status Update Scheduler Expression]** en klik op **[!UICONTROL Save]**. Als u bijvoorbeeld de configuratieservice dagelijks om 00:00 uur wilt uitvoeren, geeft u `0 0 0 1/1 * ? *` op in het veld **[!UICONTROL Status Update Scheduler Expression]**.

Het standaardinterval voor het synchroniseren van de status van [!DNL Adobe Sign] is nu gewijzigd.

## Verwante artikelen {#related-articles}

* [Adobe Sign in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md)
* [Adobe Sign gebruiken met AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)


