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
source-git-commit: f0038c1f88ea0047cbaae4fe49456a665aa67f10
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 0%

---


# Adobe Sign integreren met AEM Forms{#integrate-adobe-sign-with-aem-forms}

Adobe Sign maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard Adobe Sign- en adaptief formulierscenario vult een gebruiker een adaptief formulier in om **een service aan te vragen**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. De serviceprovider controleert de toepassing en gebruikt Adobe Sign om de goedgekeurde toepassing te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign integreren met AEM Forms.

Als u Adobe Sign met AEM Forms wilt gebruiken, configureert u Adobe Sign in AEM Cloud Services:

## Vereisten {#prerequisites}

U hebt het volgende nodig om Adobe Sign te integreren met AEM Forms:

* Een actieve [Adobe Sign-ontwikkelaarsaccount.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* Een [SSL ingeschakeld](/help/sites-administering/ssl-by-default.md) AEM Forms-server.
* An [Adobe Sign API application](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Referenties (client-id en clientgeheim) van Adobe Sign API-toepassing.
* Als u de configuratie opnieuw configureert, verwijdert u de bestaande Adobe Sign-configuratie uit zowel auteur- als publicatieinstanties.
* Gebruik [identieke crypto key](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur en publiceer instanties.

## Adobe Sign configureren met AEM Forms {#configure-adobe-sign-with-aem-forms}

Voer de volgende stappen uit om Adobe Sign met AEM Forms in de Author-instantie te configureren nadat u aan de voorwaarden hebt voldaan:

1. Navigeer in AEM Forms-auteurinstantie naar **Tools** ![hammer](assets/hammer.png) > **Algemeen** > **Configuratiebrowser**.
1. Tik op de pagina **[!UICONTROL Configuration Browser]** op **[!UICONTROL Create]**.
   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** op voor de configuratie, schakel **[!UICONTROL Cloud Configurations]** in en tik **[!UICONTROL Create]**. Er wordt een configuratiecontainer voor cloudservices gemaakt.
1. Navigeer naar **Tools** ![hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign** en selecteer de configuratiecontainer die u in de bovenstaande stap hebt gemaakt.

   >[!NOTE]
   >
   >U kunt of stappen 1-4 uitvoeren om een nieuwe configuratiecontainer tot stand te brengen en een configuratie van Adobe Sign in de container tot stand te brengen of de bestaande `global` omslag in **Tools** ![hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign** te gebruiken. Als u de configuratie maakt in de nieuwe configuratiecontainer, moet u de naam van de container opgeven in het veld **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

   >[!NOTE]
   Zorg ervoor dat de URL van de configuratiepagina voor cloudservices begint met **HTTPS**. Als dat niet het geval is, [schakel SSL](/help/sites-administering/ssl-by-default.md) voor de AEM Forms-server in.

1. Tik op **[!UICONTROL Create]** op de configuratiepagina om Adobe Sign-configuratie te maken in AEM Forms.
1. Geef op het tabblad **[!UICONTROL General]** van de pagina **[!UICONTROL Create Adobe Sign Configuration]** een **Naam** op voor de configuratie en tik **Volgende**. U kunt desgewenst een titel opgeven en naar een miniatuur voor de configuratie bladeren.

1. Kopieer de URL in het huidige browservenster naar een laptop. Het is vereist om Adobe Sign-toepassing te configureren met AEM Forms.

1. Configureer OAuth-instellingen voor de Adobe Sign-toepassing:

   1. Open een browservenster en meld u aan bij de Adobe Sign-ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor AEM Forms is geconfigureerd en tik op OAuth configureren voor toepassing.
   1. Voeg in het vak **URL omleiden** de HTTPS-URL toe die in de vorige stap is gekopieerd en klik op **Opslaan**.
   1. Schakel de volgende OAuth-instellingen voor de Adobe Sign-toepassing in en klik op **Opslaan**.
   * samenvoeging_read
   * samenvoeging_write
   * aggregatie_verzenden
   * widget_write
   * workflow_read

   Voor geleidelijke informatie om montages OAuth voor een toepassing van Adobe Sign te vormen en de sleutels te verkrijgen, zie [montages van Auth voor de toepassing ](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaarsdocumentatie vormen.

   ![OAuth Config](assets/oauthconfig_new.png)

1. Ga terug naar **Adobe Sign Configuration** pagina. Op het tabblad **[!UICONTROL Settings]** vermeldt het veld **[!UICONTROL OAuth URL]** de volgende standaard-URL:

   https://secure.na1.echosign.com/public/oauth

   waarbij:

   **na1** verwijst naar het standaard gegevensbestandaandeel.

   U kunt de waarde voor het delen van de database wijzigen. Start de server opnieuw om de nieuwe waarde voor de databaseschijf te kunnen gebruiken.

1. Geef de **Client ID** (ook wel toepassings-id genoemd) en **Client Secret** op. Selecteer de optie **Adobe Sign ook inschakelen voor bijlagen** om bestanden die zijn gekoppeld aan een adaptief formulier, toe te voegen aan het corresponderende Adobe Sign-document dat ter ondertekening is verzonden.

   Tik op **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van een Adobe Sign-toepassing.

   Tik **[!UICONTROL Create]** om de Adobe Sign-configuratie te maken.

1. Open AEM webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Open **Forms Common Configuration Service.**
1. In het **Allow** veld **select** Alle gebruikers - Alle gebruikers, anoniem of aangemeld, kunnen een voorbeeld van bijlagen bekijken, formulieren controleren en ondertekenen en op **Opslaan klikken.** Author-instantie is geconfigureerd voor gebruik van Adobe Sign.
1. Publiceer de configuratie.
1. Gebruik [replicatie](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/replication.html) om identieke configuratie op overeenkomstige te creëren publiceer instanties.

Adobe Sign is nu geïntegreerd met AEM Forms en klaar voor gebruik in adaptieve formulieren. Als u de Adobe Sign-service in een adaptieve vorm wilt [gebruiken, geeft u de hierboven gemaakte configuratiecontainer op in adaptieve formuliereigenschappen.](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)



## Adobe Sign-planner configureren om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Een adaptief formulier dat geschikt is voor Adobe Sign wordt alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. Standaard is de Adobe Sign Scheduler-service gepland om na elke 24 uur de respons van de ondertekenaar van de (opiniepeiling)gegevens te controleren. U kunt het standaardinterval voor uw milieu veranderen. Voer de volgende stappen uit om het standaardinterval te wijzigen:

1. Meld u met beheerdersgegevens aan bij de AEM Forms-server en navigeer naar **Tools** > **Operations** > **Webconsole**.

   U kunt ook de volgende URL openen in een browservenster:
   `https://[localhost]:'port'/system/console/configMgr`

1. Zoek en open de **Adobe Sign Configuration Service**-optie. Geef een [expressie voor uitsnijden](https://en.wikipedia.org/wiki/Cron#CRON_expression) op in het veld **Uitdrukking voor statusupdate-planner** en klik op **Opslaan**. Als u bijvoorbeeld de configuratieservice dagelijks om 00:00 uur wilt uitvoeren, geeft u `0 0 0 1/1 * ? *` op in het veld **Uitdrukking planner voor statusupdate**.

Het standaardinterval voor het synchroniseren van de status van Adobe Sign is nu gewijzigd.

## Verwante artikelen {#related-articles}

* [Adobe Sign in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md)
* [Adobe Sign gebruiken met AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)

