---
title: Adobe Sign integreren met AEM Forms
seo-title: Integrate Adobe Sign with AEM Forms
description: Leer hoe u Adobe Sign for AEM Forms configureert
seo-description: Learn how to configure Adobe Sign for AEM Forms
uuid: e5049775-fb6c-4228-9823-e6a2811460da
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 1f28b257-5419-4a21-a54a-b20bf35530ac
docset: aem65
feature: Adaptive Forms, Acrobat Sign
exl-id: 52146038-1582-41b8-aee0-215d04bb91d7
source-git-commit: 28d092a7713438c27213766f0bb702b699305b88
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 0%

---

# Integreren [!DNL Adobe Sign] met AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

Normaal [!DNL Adobe Sign] en adaptieve formulieren, vult een gebruiker een adaptief formulier aan **een dienst aanvragen**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Sign] om de goedgekeurde aanvraag te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u [!DNL Adobe Sign] met AEM [!DNL Forms].

Te gebruiken [!DNL Adobe Sign] met AEM [!DNL Forms], configureren [!DNL Adobe Sign] in AEM Cloud Services:

## Vereisten {#prerequisites}

U hebt het volgende nodig om te integreren [!DNL Adobe Sign] met AEM [!DNL Forms]:

* Een actief [Adobe Sign Developer-account.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* An [SSL ingeschakeld](/help/sites-administering/ssl-by-default.md) AEM [!DNL Forms] server.
* An [Adobe Sign API-toepassing](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credentials (client-id en clientgeheim) van [!DNL Adobe Sign] API-toepassing.
* Bij het aanpassen van de configuratie verwijdert u de bestaande [!DNL Adobe Sign] configuratie van zowel auteur- als publicatieinstanties.
* Gebruiken [identieke cryptosleutel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur- en publicatieinstanties.

## Configureren [!DNL Adobe Sign] met AEM [!DNL Forms] {#configure-adobe-sign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit om te vormen [!DNL Adobe Sign] met AEM [!DNL Forms] in de instantie Auteur:

1. Op AEM [!DNL Forms] auteurinstantie, navigeren aan **Gereedschappen** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, tikken **[!UICONTROL Create]**.
   * Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en tikken **[!UICONTROL Create]**. Er wordt een configuratiecontainer voor cloudservices gemaakt.
1. Navigeren naar **Gereedschappen** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** en selecteert u de configuratiecontainer die u in de bovenstaande stap hebt gemaakt.

   >[!NOTE]
   >
   >U kunt stappen 1-4 uitvoeren om een nieuwe configuratiecontainer te maken en een [!DNL Adobe Sign] in de container of gebruik de bestaande `global` map in **Gereedschappen** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]**. Als u de configuratie in de nieuwe configuratiecontainer creeert, zorg ervoor om de containernaam in te specificeren **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

   >[!NOTE]
   Zorg ervoor dat de URL van de configuratiepagina voor cloudservices begint met **HTTPS**. Zo niet, [SSL inschakelen](/help/sites-administering/ssl-by-default.md) voor AEM [!DNL Forms] server.

1. Tik op de configuratiepagina op **[!UICONTROL Create]** om [!DNL Adobe Sign] configuratie in AEM [!DNL Forms].
1. In de **[!UICONTROL General]** tabblad van het dialoogvenster **[!UICONTROL Create Adobe Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie en tikken **[!UICONTROL Next]**. U kunt desgewenst een titel opgeven en naar een miniatuur voor de configuratie bladeren.

1. Kopieer de URL in het huidige browservenster naar een laptop. Het is vereist om te configureren [!DNL Adobe Sign] toepassing met AEM[!DNL Forms].

1. In de **[!UICONTROL Settings]** de **[!UICONTROL OAuth URL]** bevat de standaard-URL. De opmaak van de URL is:

   `https://<shard>/public/oAuth/v2`

   Bijvoorbeeld:
   `https://secure.na1.echosign.com/public/oauth/v2`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   Als u een andere [!DNL Adobe Sign] configuratie voor een Adobe Experience Manager-functie of -component, moet u ervoor zorgen dat alle [!DNL Adobe Sign] Cloud Configurations verwijzen naar hetzelfde segment.

   >[!NOTE]
   De **Adobe Sign-configuratie maken** pagina geopend. Sluit het bestand niet. U kunt **Client-id** en **Clientgeheim** na het configureren van OAuth-instellingen voor de [!DNL Adobe Sign] zoals beschreven in volgende stappen.


1. OAuth-instellingen configureren voor de [!DNL Adobe Sign] toepassing:

   1. Open een browservenster en meld u aan bij [!DNL Adobe Sign] ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor AEM wordt geconfigureerd [!DNL Forms]en tikken **[!UICONTROL Configure OAuth for Application]**.
   1. Kopieer de **[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** op een laptop.
   1. In de **[!UICONTROL Redirect URL]** voegt u de HTTPS-URL toe die u in de vorige stap hebt gekopieerd.
   1. De volgende OAuth-instellingen inschakelen voor de [!DNL Adobe Sign] toepassing en klik **[!UICONTROL Save]**.
   * samenvoeging_read
   * samenvoeging_write
   * aggregatie_verzenden
   * widget_write
   * workflow_read

   Voor geleidelijke informatie om montages OAuth voor te vormen [!DNL Adobe Sign] en verkrijgen de toetsen, zie [Auteursinstellingen voor de toepassing configureren](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaarsdocumentatie.

   ![OAuth Config](assets/oauthconfig_new.png)

1. Ga terug naar de **[!UICONTROL Create Adobe Sign Configuration]** pagina. In de **[!UICONTROL Settings]** de **[!UICONTROL OAuth URL]** in het veld wordt de standaard-URL vermeld. De opmaak van de URL is:

   `https://<shard>/public/oAuth/v2`

   Bijvoorbeeld:
   `https://secure.na1.echosign.com/public/oauth/v2`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt.

   U kunt de waarde voor het delen van de database wijzigen. Start de server opnieuw om de nieuwe waarde voor de databaseschijf te kunnen gebruiken.

   >[!NOTE]
   Zorg ervoor dat de auteur en de publicatie van instantieconfiguraties naar hetzelfde niveau verwijzen. Als u meerdere Adobe Sign-configuraties voor een organisatie maakt, moet u ervoor zorgen dat alle configuraties hetzelfde segment gebruiken.

1. Ga terug naar de **[!UICONTROL Create Adobe Sign Configuration]** pagina. In de **[!UICONTROL Settings]** tabblad, geeft u de **Client-id** (ook toepassings-id genoemd) en **Clientgeheim**. Gebruik de [Client-id en clientgeheim van Adobe Sign-toepassing](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) gemaakt voor AEM Forms.

1. Selecteer **[!UICONTROL Enable Adobe Sign for attachments also]** aan een aangepast formulier gekoppelde bestanden toevoegen aan de overeenkomstige [!DNL Adobe Sign] document verzonden voor ondertekening.

1. Tik op **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Sign] toepassing.

1. Tikken **[!UICONTROL Create]** om de [!DNL Adobe Sign] configuratie.

1. Open AEM webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Open **[!UICONTROL Forms Common Configuration Service].**
1. In de **[!UICONTROL Allow]** veld, **selecteren** Alle gebruikers - Alle gebruikers, anoniem of aangemeld, kunnen een voorbeeld van bijlagen bekijken, formulieren verifiëren en ondertekenen en op **[!UICONTROL Save].** Auteur-instantie is geconfigureerd voor gebruik [!DNL Adobe Sign].
1. Publiceer de configuratie.
1. Gebruiken [replicatie](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/configuring/replication.html) om identieke configuratie op overeenkomstige te creëren publiceer instanties.

Nu, [!DNL Adobe Sign] is geïntegreerd met AEM [!DNL Forms] en klaar voor gebruik in adaptieve vormen. Naar [Adobe Sign-service in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geeft u de hierboven gemaakte configuratiecontainer op in adaptieve formuliereigenschappen.



## Configureren [!DNL Adobe Sign] planner om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

An [!DNL Adobe Sign] Het ingeschakelde adaptieve formulier wordt alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. Standaard worden de [!DNL Adobe Sign] De planningsdiensten zijn gepland om (opiniepeiling) ondertekenaarreactie na om de 24 uur te controleren. U kunt het standaardinterval voor uw milieu veranderen. Voer de volgende stappen uit om het standaardinterval te wijzigen:

1. Aanmelden bij AEM [!DNL Forms] server met beheerdersreferenties en navigeer naar **Gereedschappen** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   U kunt ook de volgende URL openen in een browservenster:
   `https://[localhost]:'port'/system/console/configMgr`

1. Zoek en open de **[!UICONTROL Adobe Sign Configuration Service]** optie. Geef een [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) in de **[!UICONTROL Status Update Scheduler Expression]** veld en klik op **[!UICONTROL Save]**. Bijvoorbeeld, om de configuratieservice dagelijks bij 00:00 am in werking te stellen, specificeer `0 0 0 1/1 * ? *` in de **[!UICONTROL Status Update Scheduler Expression]** veld.

Standaardinterval voor synchronisatie van de status van [!DNL Adobe Sign] is nu gewijzigd.

## Verwante artikelen {#related-articles}

* [Adobe Sign in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md)
* [Adobe Sign gebruiken met AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
