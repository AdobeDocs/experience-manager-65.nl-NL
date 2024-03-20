---
title: Adobe Sign integreren met AEM Forms
description: Leer Adobe Sign configureren voor uw AEM Adaptive Forms. Adobe Sign verbetert de workflow en verwerkt de documenten voor juridische zaken, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms, Foundation Components, Acrobat Sign
exl-id: 52146038-1582-41b8-aee0-215d04bb91d7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1888'
ht-degree: 0%

---

# Integreren [!DNL Adobe Sign] met AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms.html?lang=en#adobe-acrobat-sign-for-government) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

Normaal [!DNL Adobe Acrobat Sign] en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Acrobat Sign] om de goedgekeurde aanvraag te markeren. AEM Forms steunt zowel Adobe Acrobat Sign als Adobe Acrobat Sign Solutions voor de regering. Afhankelijk van uw licentie en vereisten kunt u AEM Forms integreren in of verbinden met een van de twee oplossingen:

* [AEM Forms verbinden met Adobe Acrobat Sign](#adobe-sign)
* [Connect AEM Forms met Adobe Acrobat Sign Solutions for Government](#adobe-acrobat-sign-for-government)

## AEM Forms verbinden met Adobe Acrobat Sign {#adobe-sign}

Verbinding maken **[!DNL AEM Forms]** with **[!DNL Adobe Acrobat Sign]**, stelt u de software en accounts in die in de sectie Voorwaarden worden vermeld, en maakt u Adobe Sign verbinding met alle instanties van AEM Forms Author and Publish:

## Vereisten {#prerequisites}

U hebt de volgende integratie nodig: [!DNL Adobe Sign] met AEM [!DNL Forms]:

* Een actief [Adobe Sign Developer-account.](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* An [SSL ingeschakeld](/help/sites-administering/ssl-by-default.md) AEM [!DNL Forms] server.
* An [Adobe Sign API-toepassing](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Credentials (client-id en clientgeheim) van [!DNL Adobe Sign] API-toepassing
* Bij het aanpassen van de configuratie verwijdert u de bestaande [!DNL Adobe Sign] configuratie van zowel auteur- als publicatieinstanties.
* Gebruiken [identieke cryptosleutel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur- en publicatieinstanties.

## Configureren [!DNL Adobe Sign] met AEM [!DNL Forms] {#configure-adobe-sign-with-aem-forms}

Nadat de eerste vereisten op zijn plaats zijn, voer de volgende stappen uit om te vormen [!DNL Adobe Sign] met AEM [!DNL Forms] in de instantie Auteur:

1. Op AEM [!DNL Forms] auteurinstantie, navigeren aan **Gereedschappen** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, selecteert u **[!UICONTROL Create]**.
   * Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en selecteert u **[!UICONTROL Create]**. Er wordt een configuratiecontainer gemaakt.
1. Navigeren naar **Gereedschappen** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** en selecteer de configuratiecontainer u in de bovenstaande stap creeerde.

   >[!NOTE]
   >
   >U kunt stappen 1-4 uitvoeren om een configuratiecontainer te maken en een [!DNL Adobe Sign] in de container of de bestaande `global` map in **Gereedschappen** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]**. Als u de configuratie in de nieuwe configuratiecontainer creeert, zorg ervoor om de containernaam in te specificeren **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

   >[!NOTE]
   >
   Zorg ervoor dat URL van de Pagina van de Configuratie van Cloud Servicen met begint **HTTPS**. Zo niet, [SSL inschakelen](/help/sites-administering/ssl-by-default.md) voor AEM [!DNL Forms] server.


1. Tik op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Sign] configuratie AEM [!DNL Forms].
1. In de **[!UICONTROL General]** tabblad van het **[!UICONTROL Create Adobe Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie en tikken **[!UICONTROL Next]**. U kunt desgewenst een titel opgeven en naar een miniatuur voor de configuratie bladeren.
1. Nu kunt u **[!UICONTROL Select solution]** om [!DNL Adobe Acrobat Sign].

   ![Adobe Acrobat Sign Solutions](/help/forms/using/assets/adobe-sign-solution.png)

1. Kopieer de URL in het huidige browservenster naar een laptop en verwijder het onderdeel /`ui#/aem` via de URL. De gewijzigde URL wordt dan vereist om te vormen [!DNL Adobe Acrobat Sign] toepassing met [!DNL AEM Forms], in een latere stap. Tikken [!UICONTROL Next].

1. In de **[!UICONTROL Settings]** tab,
   * de **[!UICONTROL OAuth URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/public/oauth/v2`

     Bijvoorbeeld:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * de **[!UICONTROL Access token URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/oauth/v2/token`

     Bijvoorbeeld:
     `https://api.na1.echosign.com/oauth/v2/token`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   * Houd de **Adobe Acrobat Sign-configuratie maken** pagina geopend. Sluit het bestand niet. U kunt **Client-id** en **Clientgeheim** na het configureren van OAuth-instellingen voor de [!DNL Adobe Acrobat Sign] zoals beschreven in volgende stappen.
   * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie over Adobe Sign OAuth URL en Access Token URL.

1. OAuth-instellingen configureren voor de [!DNL Adobe Sign] toepassing:

   1. Open een browservenster en meld u aan bij [!DNL Adobe Sign] ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor AEM wordt geconfigureerd [!DNL Forms]en selecteert u **[!UICONTROL Configure OAuth for Application]**.
   1. De **[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** op een laptop.
   1. In de **[!UICONTROL Redirect URL]** voegt u de HTTPS-URL toe die u in de vorige stap hebt gekopieerd.
   1. De volgende OAuth-instellingen inschakelen voor de [!DNL Adobe Sign] toepassing en klik **[!UICONTROL Save]**.

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_write
   * workflow_read

   Voor geleidelijke informatie om montages OAuth voor te vormen [!DNL Adobe Sign] en verkrijgen de toetsen, zie [Auteursinstellingen voor de toepassing configureren](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) ontwikkelaarsdocumentatie.

   ![OAuth Config](assets/oauthconfig_new.png)

<!--
1. Go back to the **[!UICONTROL Create Adobe Sign Configuration]** page. In the **[!UICONTROL Settings]** tab, the **[!UICONTROL OAuth URL]** field mentions the  default URL. The format of the URL is:

   `https://<shard>/public/oAuth/v2`

   For example: 
   `https://secure.na1.echosign.com/public/oauth/v2`

   where:

   **na1** refers to the default database shard.

   You can modify the value for the database shard. Restart the server to be able to use the new value for the database shard.

   >[!NOTE]
   >
   >Ensure that your author and publish instance configurations point to the same shard. If you create multiple Adobe Sign configurations for an organization, ensure all the configurations utilize the same shard. -->

1. Ga terug naar de **[!UICONTROL Create Adobe Sign Configuration]** pagina. In de **[!UICONTROL Settings]** tabblad, geeft u de **Client-id** (ook toepassings-id genoemd) en **Clientgeheim**. Gebruik de [Client-id en clientgeheim van Adobe Sign-toepassing](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) gemaakt voor AEM Forms.

1. Selecteer de **[!UICONTROL Enable Adobe Sign for attachments also]** aan een aangepast formulier gekoppelde bestanden toevoegen aan de overeenkomstige [!DNL Adobe Sign] document verzonden voor ondertekening.

1. Selecteer **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Sign] toepassing.

   ![Adobe Acrobat Sign Cloud-configuratie gelukt](assets/adobe-sign-cloud-configuration-success.png)

1. Tikken **[!UICONTROL Create]** om de [!DNL Adobe Sign] configuratie.
1. Open AEM webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Openen **[!UICONTROL Forms Common Configuration Service].**
1. In de **[!UICONTROL Allow]** veld, **selecteren** Alle gebruikers - Alle gebruikers, anoniem of aangemeld, kunnen een voorbeeld van bijlagen bekijken, formulieren verifiëren en ondertekenen en op **[!UICONTROL Save].** Auteur-instantie is geconfigureerd voor gebruik [!DNL Adobe Sign].
1. Publiceer de configuratie.
1. Gebruiken [replicatie](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/replication.html) om identieke configuratie op overeenkomstige te creëren publiceer instanties.

Nu, [!DNL Adobe Sign] is geïntegreerd met AEM [!DNL Forms] en klaar voor gebruik in adaptieve vormen. Naar [Adobe Sign-service in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), geeft u de hierboven gemaakte configuratiecontainer op in adaptieve formuliereigenschappen.

>[!NOTE]
>
Als u de Adobe Sign-sandbox wilt configureren, kunt u dezelfde configuratiestappen volgen als in [Adobe Sign](#adobe-sign).

## Connect AEM Forms met Adobe Acrobat Sign Solutions for Government {#adobe-acrobat-sign-for-government}

Het verbinden van AEM Forms met Adobe Acrobat Sign Solutions voor de overheid is een proces dat uit meerdere stappen bestaat. Het gaat om:

* Omleidings-URL maken voor uw AEM
* De omleiding van URL en het bereik delen met Adobe Sign Solutions for Government-team
* Referenties ontvangen van het Adobe Sign-team
* Ontvangen gebruikersgegevens gebruiken om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

![adobe-acrobat-sign-govt-workflow](/help/forms/using/assets/adobe-acrobat-sign-govt-workflow.png)

### Voordat u begint {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Voordat u AEM Forms gaat verbinden met Adobe Acrobat Sign Solution,

* Zorg ervoor dat uw [Adobe Acrobat Sign Solutions for Government](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) account is ingericht.
* Uw AEM [!DNL Forms] servers zijn [SSL ingeschakeld](/help/sites-administering/ssl-by-default.md) .
* Uw AEM [!DNL Forms] servers gebruiken [identieke cryptosleutel](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur- en publicatieinstanties.

### AEM Forms verbinden met Adobe Acrobat Sign Solutions voor de overheid {#connect-adobe-acrobat-sign-for-government}

#### Een omleidings-URL voor uw AEM maken

1. Navigeer op uw AEM Forms-exemplaar naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Op de **[!UICONTROL Configuration Browser]** pagina, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** dialoogvenster, geeft u een **[!UICONTROL Title]** voor de configuratie, laat toe **[!UICONTROL Cloud Configurations]** en selecteert u **[!UICONTROL Create]**. Er wordt een configuratiecontainer gemaakt. Zorg ervoor dat de naam van de container/map geen ruimte bevat.

1. Navigeren naar **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde. Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het dialoogvenster **[!UICONTROL Configuration Container]** veld.
1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] in AEM Forms.
1. Kopieer de URL van het huidige browservenster naar een aantekenblok via de URL. Deze URL wordt `re-direct URL`. In de volgende sectie deelt u de opdracht `re-direct URL` en `Scopes` met Adobe Sign-team en aanvraagreferenties (client-id en clientgeheim).

>[!NOTE]
>
>
* A `re-direct URL` bevat een [Top-level](https://en.wikipedia.org/wiki/Top-level_domain) domein. Bijvoorbeeld: `https://adobe.com/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`
* Gebruik geen lokale URL als `re-direct URL`. Bijvoorbeeld: `https://localhost:4502/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`.


#### De omleiding van URL en bereik delen met het team van Adobe Sign en referenties ontvangen

Het Adobe Acrobat Sign for Government Solutions-team heeft `re-direct URL` en het bepaalde bereik dat voor uw Adobe Acrobat Sign-toepassing (hieronder vermeld) moet worden ingeschakeld om referenties te genereren (client-id en clientgeheim) waarmee u AEM Forms voor de overheid kunt verbinden met Adobe Acrobat Sign Solutions.

Deel de `scopes` (zie hieronder) en de `re-direct URL` gemaakt en genoteerd voor de laatste stap in de vorige sectie met uw Adobe Acrobat Sign for Government Solution-vertegenwoordiger [Adobe Professional Services-teamlid](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password).

**_Segmenten_**

* [!DNL agreement_read]
* [!DNL agreement_write]
* [!DNL agreement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

De vertegenwoordiger genereert en deelt referenties met u. In de volgende sectie gebruikt u de referenties (client-id en clientgeheim) om AEM Forms te verbinden met Adobe Acrobat Sign Solutions for Government.

#### Gebruik de ontvangen referenties om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

1. Open de `re-direct URL` in uw browser. U hebt de `re-direct URL` in de laatste stap van de [een omleidings-URL maken op uw AEM-instantie](#create-redirect-url) sectie.

1. In de **[!UICONTROL General]** tabblad van het **[!UICONTROL Create Adobe Sign Configuration]** pagina, geeft u een **[!UICONTROL Name]** voor de configuratie, en selecteer **[!UICONTROL Next]**. U kunt desgewenst een **[!UICONTROL Title]** en bladert u om een **[!UICONTROL Thumbnail]** voor de configuratie. Klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Settings]** tabblad van het **[!UICONTROL Create Adobe Sign Configuration]** pagina, voor de **[!UICONTROL Select solution]** selecteert u [!DNL Adobe Acrobat Sign Solutions for Government].

   ![Adobe Acrobat Sign Solutions for Government](/help/forms/using/assets/adobe-sign-for-govt.png)

1. In de **[!UICONTROL Email]** Geef het e-mailadres op dat aan uw Adobe Acrobat Sign Solutions for Government-account is gekoppeld.

1. In de **[!UICONTROL Settings]** tab,
   * de **[!UICONTROL OAuth URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * de **[!UICONTROL Access token URL]** bevat het veld de standaard-URL die het Adobe Sign-databasespoor bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   waarbij:

   **nl1** verwijst naar de standaard databasedeelt. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL  Adobe Acrobat Sign] Cloud Configurations verwijzen naar de [correcte Shard](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie met betrekking tot Adobe Sign Auth URL en Access Token URL.

1. Gebruik de gegevens die worden gedeeld door de vertegenwoordiger van Adobe Acrobat Sign for Government Solution ([Adobe Professional Services-teamlid]) in de vorige sectie als [**[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]**].

1. Selecteer de **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** aan een adaptief formulier gekoppelde bestanden toevoegen aan de corresponderende [!DNL Adobe Acrobat Sign] document verzonden voor ondertekening.

1. Selecteer **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Acrobat Sign] toepassing. Wanneer gevraagd om toegang te bevestigen voor `Adobe Acrobat Sign for Government Solutions` en klikt u op **[!UICONTROL Allow Access]**. Als de gegevens juist zijn en u [!DNL AEM Forms] om toegang te krijgen tot [!DNL Adobe Acrobat Sign] ontwikkelaarsaccount, een succesbericht dat lijkt op het volgende:

   ![Adobe Acrobat Sign Cloud-configuratie gelukt](/help/forms/using/assets/adobe-sign-cloud-configuration-success.png)

   Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt tijdens het maken van [!DNL Adobe Acrobat Sign] toepassing. Wanneer gevraagd om toegang te bevestigen voor `your account`en klik op **[!UICONTROL Allow Access]**.

1. Selecteren **[!UICONTROL Create]** om de configuratie te maken.
1. Open AEM webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Openen **[!UICONTROL Forms Common Configuration Service].**
1. In de **[!UICONTROL Allow]** veld, **selecteren** Alle gebruikers - Alle gebruikers, anoniem of aangemeld, kunnen een voorbeeld van bijlagen bekijken, formulieren verifiëren en ondertekenen en op **[!UICONTROL Save].** Auteur-instantie is geconfigureerd voor gebruik [!DNL Adobe Sign].

1. Publiceer de configuratie.
1. Gebruiken [replicatie](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/replication.html) om identieke configuratie op overeenkomstige te creëren publiceer instanties.

Nu kunt u [Adobe Acrobat Sign-velden toevoegen aan een adaptief formulier gebruiken](working-with-adobe-sign.md) of [AEM](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Zorg ervoor dat u de configuratiecontainer die voor de configuratie van de Cloud Service wordt gebruikt aan al Adaptive Forms toevoegt die voor wordt toegelaten [!DNL Adobe Acrobat Sign]. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.


## Configureren [!DNL Adobe Sign] planner om de ondertekeningsstatus te synchroniseren {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

An [!DNL Adobe Sign] Het ingeschakelde adaptieve formulier wordt alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. Standaard worden de [!DNL Adobe Sign] De planningsdiensten zijn gepland om (opiniepeiling) ondertekenaarreactie na om de 24 uur te controleren. U kunt het standaardinterval voor uw milieu veranderen. Voer de volgende stappen uit om het standaardinterval te wijzigen:

1. Aanmelden bij AEM [!DNL Forms] server met beheerdersreferenties en navigeer naar **Gereedschappen** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   U kunt ook de volgende URL openen in een browservenster:
   `https://[localhost]:'port'/system/console/configMgr`

1. Zoek en open de **[!UICONTROL Adobe Sign Configuration Service]** -optie. Geef een [uitsnijdexpressie](https://en.wikipedia.org/wiki/Cron#CRON_expression) in de **[!UICONTROL Status Update Scheduler Expression]** veld en klik op **[!UICONTROL Save]**. Bijvoorbeeld, om de configuratieservice dagelijks bij 00:00 te leiden am, specificeer `0 0 0 1/1 * ? *` in de **[!UICONTROL Status Update Scheduler Expression]** veld.

Standaardinterval voor synchronisatie van de status van [!DNL Adobe Sign] is nu gewijzigd.

## Verwante artikelen {#related-articles}

* [Adobe Sign in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md)
* [Adobe Sign met Form-Centric workflows](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)
* [Adobe Sign gebruiken met AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
