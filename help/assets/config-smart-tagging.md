---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe te om slimme het etiketteren en verbeterde slimme het etiketteren in  [!DNL Adobe Experience Manager] te vormen, gebruikend de Slimme Dienst van de Inhoud.
role: Admin
feature: Tagging,Smart Tags
exl-id: 9f68804f-ba15-4f83-ab1b-c249424b1396
solution: Experience Manager, Experience Manager Assets
source-git-commit: 5b4153f83d725c307e23ea10c4ea151911d4d390
workflow-type: tm+mt
source-wordcount: '1914'
ht-degree: 12%

---

# [!DNL Assets] voorbereiden voor slimme tags {#configure-asset-tagging-using-the-smart-content-service}

Voordat u met het labelen van uw middelen begint met Smart Content Services, moet u [!DNL Experience Manager Assets] integreren met Adobe Developer Console om de slimme service van [!DNL Adobe Sensei] te gebruiken. Als de service eenmaal is geconfigureerd, kunt u de service trainen met enkele afbeeldingen en een tag.

<!--
>[!NOTE]
>
>* Smart Content Services is no longer available to new [!DNL Experience Manager Assets] On-Premise customers. Existing On-Premise customers, who already have this capability enabled, can continue using Smart Content Services.
>* Smart Content Services is available for existing [!DNL Experience Manager Assets] Managed Services customers, who already have this capability enabled.
>* New Experience Manager Assets Managed Services customers can follow the instructions mentioned in this article to set up Smart Content Services.
>* For Service Pack 20 and older, you need to perform the workaround steps for SCS to support Oauth integration. See [Troubleshooting smart tags for OAuth credentials](config-oauth.md).
>* To support the Oauth integration on Service Pack 21, you need to install the [Hotfix for SP 21](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fproduct%2Fassets%2Fcq-6.5.0-hotfix-40772-1.2.zip). 
>* For Existing SCS configuration, the process is the same as setting up a new OAuth integration. Any legacy configuration will be automatically cleaned up.
-->

Controleer het volgende voordat u de Smart Content Service gebruikt:

* [ integreer met Adobe Developer Console ](#integrate-adobe-io).
* [ Lijn de Slimme Dienst van de Inhoud ](#training-the-smart-content-service).

* Installeer het recentste [[!DNL Experience Manager]  Pak van de Dienst ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html).

## SCS upgrade ter ondersteuning van Oauth voor Adobe Managed Services {#scs-upgrade-oauth-managed-services}

**Nieuwe Gebruikers**

Installeer Service Pack 21. Om Oauth integratie op Service Pack 21 te steunen, moet u [ Hotfix voor Service Pack 21 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fproduct%2Fassets%2Fcq-6.5.0-hotfix-40772-1.2.zip) installeren.

Volg de instructies in dit artikel aan opstellings de Slimme Diensten van de Inhoud.

**Bestaande gebruikers**

Als u aan Service Pack 21 hebt bevorderd, installeer [ Hotfix voor SP 21 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fproduct%2Fassets%2Fcq-6.5.0-hotfix-40772-1.2.zip) om Oauth integratie te steunen. Elke bestaande configuratie wordt automatisch verwijderd. Volg de instructies in dit artikel aan opstellings de Slimme Diensten van de Inhoud.

Voor Service Pack 20 en ouder, moet u de tijdelijke stappen voor SCS uitvoeren om Oauth integratie te steunen. Zie [ het Oplossen van problemen slimme markeringen voor geloofsbrieven OAuth ](config-oauth.md).

## SCS verbetering om Oauth voor Op-premise gebruikers te steunen {#scs-upgrade-oauth-on-premise}

**Nieuwe Gebruikers**

Smart Content Services is niet meer beschikbaar voor nieuwe [!DNL Experience Manager Assets] gebruikers op locatie.

**Bestaande gebruikers**

Bestaande gebruikers op locatie die deze mogelijkheid al hebben ingeschakeld, kunnen services voor slimme inhoud blijven gebruiken.

Als u aan Service Pack 21 hebt bevorderd, installeer [ Hotfix voor SP 21 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fproduct%2Fassets%2Fcq-6.5.0-hotfix-40772-1.2.zip) om Oauth integratie te steunen. Elke bestaande configuratie wordt automatisch verwijderd. Volg de instructies in dit artikel aan opstellings de Slimme Diensten van de Inhoud.

Voor Service Pack 20 en ouder, moet u de tijdelijke stappen voor SCS uitvoeren om Oauth integratie te steunen. Zie [ het Oplossen van problemen slimme markeringen voor geloofsbrieven OAuth ](config-oauth.md).


## Integreren met Adobe Developer Console {#integrate-adobe-io}

Wanneer u met Adobe Developer Console integreert, verifieert de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van Adobe Developer Console alvorens uw verzoek aan de Slimme Dienst van de Inhoud door:sturen. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en de licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. Creeer een integratie in [ Adobe Developer Console ](#create-adobe-io-integration).

1. Creeer [ IMS technische rekeningsconfiguratie ](#create-ims-account-config) gebruikend de API sleutel en andere geloofsbrieven van Adobe Developer Console.

1. [ vorm de Slimme Dienst van de Inhoud ](#configure-smart-content-service).

1. [Test de configuratie](#validate-the-configuration).

<!--
To configure the Smart Content Service, follow these top-level steps:

1. To generate a public key, [Create a Smart Content Service] (#obtain-public-certificate) configuration in [!DNL Experience Manager]. 

1. Optionally, [enable auto-tagging on asset upload](#enable-smart-tagging-in-the-update-asset-workflow-optional).

   <!--1. [Obtain public certificate](#obtain-public-certificate) for OAuth integration.
   1. [Create an integration in Adobe Developer Console](#create-adobe-i-o-integration) and upload the generated public key.

   1. [Configure your deployment](#configure-smart-content-service) using the API key and other credentials from Adobe Developer Console.

   1. [Test the configuration](#validate-the-configuration).-->

### Adobe Developer Console-integratie maken {#create-adobe-io-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID] field of Adobe Developer Console integration), [!UICONTROL ORGANIZATION ID] en [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] van de cloudconfiguratie te verkrijgen in [!DNL Experience Manager] .

1. Toegang [ https://developer.adobe.com ](https://developer.adobe.com/) in browser. Selecteer de aangewezen rekening en verifieer dat de bijbehorende organisatorische rol systeem **beheerder** is.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL OAuth Server-to-Server]**. Klik op **[!UICONTROL Next]** .
Raadpleeg de documentatie bij Developer Console voor meer informatie over het uitvoeren van deze configuratie, afhankelijk van uw vereisten:

   * Overzicht:
      * [ Server aan de authentificatie van de Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

   * Een nieuwe OAuth-referentie maken:
      * [ OAuth Server-aan-Server de gids van de credentieimplementatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

   * Een bestaande JWT-referentie migreren naar een OAuth-referentie:
      * [ migrerend van de Rekening van de Dienst (JWT) credential aan OAuth Server-aan-Server credential ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)


1. Selecteer **[!UICONTROL Smart Content Services]** op de pagina **[!UICONTROL Select product profiles]** . Klik op **[!UICONTROL Save configured API]**.

   De pagina die verschijnt biedt meer informatie over de configuratie. Zorg dat deze pagina geopend blijft en kopieer deze waarden in [!UICONTROL Assets Smart Tagging Service Settings] van de cloudconfiguratie in [!DNL Experience Manager] om slimme tags te configureren.

   ![ Referentie OAuth in Developer Console ](assets/ims-configuration-developer-console.png)

### Configuratie van technische IMS-account maken {#create-ims-account-config}

U moet de configuratie van de technische IMS-account maken met de onderstaande stappen:

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Klik op **[!UICONTROL Create]**.

1. Gebruik de volgende waarden in het dialoogvenster Configuratie technische account van IMS:

   ![ het venster van de Configuratie van Adobe IMS ](assets/adobe-ims-config.png)

   | Veld | Beschrijving |
   | -------- | ---------------------------- |
   | Cloudoplossing | Kies **[!UICONTROL Smart Tags]** in de vervolgkeuzelijst. |
   | Titel | Voeg een titel toe van de configurerende IMS-account. |
   | Autorisatieserver | Toevoegen `https://ims-na1.adobelogin.com` |
   | Client-id | Te verstrekken door [ console van Adobe Developer ](https://developer.adobe.com/console/). |
   | Clientgeheim | Te verstrekken door [ console van Adobe Developer ](https://developer.adobe.com/console/). |
   | Scope | Te verstrekken door [ console van Adobe Developer ](https://developer.adobe.com/console/). |
   | Org-id | Te verstrekken door [ console van Adobe Developer ](https://developer.adobe.com/console/). |

1. Selecteer de configuratie die u hebt gemaakt en klik op **[!UICONTROL Check Health]** .

1. Bevestig het dialoogvenster Gezondheid controleren en klik op Sluiten als de configuratie gezond is.

### Een nieuwe configuratie maken {#configure-smart-content-service}

<!--
>[!CAUTION]
>
>Previously, configurations that were made with JWT Credentials are now subject to deprecation in the Adobe Developer Console. You cannot create new JWT credentials after June 3, 2024. Such configurations can no longer be created or updated, but can be migrated to OAuth configurations.
> See [Setting up IMS integrations for AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service)
>See [Steps to configure OAuth for on-premise users](#config-oauth-onprem)
> See [Troubleshooting smart tags for OAuth credentials](#config-smart-tagging.md)
-->

Als u de integratie wilt configureren, gebruikt u de waarden van de velden [!UICONTROL TECHNICAL ACCOUNT ID] , [!UICONTROL ORGANIZATION ID] , [!UICONTROL CLIENT SECRET] en [!UICONTROL CLIENT ID] van de Adobe Developer Console-integratie. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] -implementatie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Smart Tag]** om het dialoogvenster [!UICONTROL Smart Tag Configurations] te openen.

1. Klik op **[!UICONTROL Create]** om een nieuwe configuratie te maken. Anders klikt u op **[!UICONTROL Properties]** om de bestaande configuratie bij te werken.

1. Vul de volgende velden in:

   ![ Slimme Configuratie van Markeringen ](assets/smart-tags-config.png)

   | Veld | Beschrijving |
   | -------- | ---------------------------- |
   | Titel | Voeg een titel toe van de configurerende IMS-account. |
   | Gekoppelde Adobe IMS-configuratie | Kies configuratie in de keuzelijst. |
   | Service-URL | `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`. Bijvoorbeeld `https://smartcontent.adobe.io/apac` . U kunt `na` , `emea` of `apac` opgeven als de gebieden waar de auteur van de Experience Manager wordt gehost. |

   >[!NOTE]
   >
   >Als de Experience Manager Beheerde Dienst vóór September 01, 2022 provisioned is, gebruik de volgende Dienst URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

1. Klik op **[!UICONTROL Save & Close]**.

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open de [!DNL Experience Manager] -server op `https://[aem_server]:[port]` .

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]** .

<!--
1. Click `com.day.cq.dam.similaritysearch.internal.impl`. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.-->

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl (SCS)`.

   ![ het venster van het Boon ](assets/mbean.png)

1. Klik op `validateConfigs()`. Klik in het dialoogvenster **[!UICONTROL Validate Configurations]** op **[!UICONTROL Invoke]** .

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

<!--
### Obtain public certificate by creating Smart Content Service configuration {#obtain-public-certificate}

A public certificate lets you authenticate your profile on Adobe Developer Console.

1. In the [!DNL Experience Manager] user interface, access **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. In the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.

1. In the **[!UICONTROL Create Configuration]** dialog, specify a title and name for the Smart Tags configuration. Click **[!UICONTROL Create]**.

1. In the **[!UICONTROL AEM Smart Content Service]** dialog, use the following values:

   **[!UICONTROL Service URL]**: `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`

   For example, `https://smartcontent.adobe.io/apac`. You can specify `na`, `emea`, or, `apac` as the regions where your Experience Manager author instance is hosted. 

   >[!NOTE]
   >
   >If the Experience Manager Managed Service is provisioned before September 01, 2022, use the following Service URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**: `https://ims-na1.adobelogin.com`

   Leave the other fields blank for now (to be provided later). Click **[!UICONTROL OK]**.

   ![Experience Manager Smart Content Service dialog to provide content service URL](assets/aem_scs.png)


   *Figure: Smart Content Service dialog to provide content service URL*

   >[!NOTE]
   >
   >The URL provided as [!UICONTROL Service URL] is not accessible via browser and generates a 404 error. The configuration works OK with the same value of the [!UICONTROL Service URL] parameter. For the overall service status and maintenance schedule, see [https://status.adobe.com](https://status.adobe.com).

1. Click **[!UICONTROL Download Public Certificate for OAuth Integration]**, and download the public certificate file `AEM-SmartTags.crt`.

   ![A representation of the settings created for the smart tagging service](assets/smart-tags-download-public-cert.png)


   *Figure: Settings for smart tagging service.*

#### Reconfigure when a certificate expires {#certrenew}

After a certificate expires, it is no longer trusted. You cannot renew an expired certificate. To add a certificate, follow these steps.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Click **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Locate and click **[!UICONTROL dam-update-service]** user. Click **[!UICONTROL Keystore]** tab.

1. Delete the existing **[!UICONTROL similaritysearch]** keystore with the expired certificate. Click **[!UICONTROL Save & Close]**.

   ![Delete the existing similarity search entry in Keystore to add a security certificate](assets/smarttags_delete_similaritysearch_keystore.png)


   *Figure: Delete the existing `similaritysearch` entry in Keystore to add a security certificate.*

1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Click **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Click the required configuration.  

1. To download a public certificate, click **[!UICONTROL Download Public Certificate for OAuth Integration]**.

1. Access [https://console.adobe.io](https://console.adobe.io) and navigate to the existing Smart Content Services on the **[!UICONTROL Integrations]** page. Upload the new certificate. For more information, see the instructions in [Create Adobe Developer Console integration](#create-adobe-i-o-integration).

### Create Adobe Developer Console integration {#create-adobe-i-o-integration}

To use Smart Content Service APIs, create an integration in Adobe Developer Console to obtain [!UICONTROL API Key] (generated in [!UICONTROL CLIENT ID] field of Adobe Developer Console integration), [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], and [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] of cloud configuration in [!DNL Experience Manager].

1. Access [https://console.adobe.io](https://console.adobe.io/) in a browser. Select the appropriate account and verify that the associated organization role is system administrator.

1. Create a project with any desired name. Click **[!UICONTROL Add API]**.

1. On the **[!UICONTROL Add an API]** page, select **[!UICONTROL Experience Cloud]** and select **[!UICONTROL Smart Content]**. Click **[!UICONTROL Next]**.

1. Select **[!UICONTROL Upload your public key]**. Provide the certificate file downloaded from [!DNL Experience Manager]. A message [!UICONTROL Public key(s) uploaded successfully] is displayed. Click **[!UICONTROL Next]**.

   [!UICONTROL Create a new Service Account (JWT) credential] page displays the public key for the service account.

1. Click **[!UICONTROL Next]**.

1. On the **[!UICONTROL Select product profiles]** page, select **[!UICONTROL Smart Content Services]**. Click **[!UICONTROL Save configured API]**.

   A page displays more information about the configuration. Keep this page open to copy and add these values in [!UICONTROL Assets Smart Tagging Service Settings] of cloud configuration in [!DNL Experience Manager] to configure smart tags.

   ![In the Overview tab, you can review the information provided for integration.](assets/integration_details.png)


   *Figure: Details of integration in Adobe Developer Console*

### Configure Smart Content Service {#configure-smart-content-service}

>[!CAUTION]
>
>Previously, configurations that were made with JWT Credentials are now subject to deprecation in the Adobe Developer Console. You cannot create new JWT credentials after June 3, 2024. Such configurations can no longer be created or updated, but can be migrated to OAuth configurations.
> See [Setting up IMS integrations for AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service)
>See [Steps to configure OAuth for on-premise users](#config-oauth-onprem)
> See [Troubleshooting smart tags for OAuth credentials](#config-smart-tagging.md)

To configure the integration, use the values of [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], [!UICONTROL CLIENT SECRET], and [!UICONTROL CLIENT ID] fields from the Adobe Developer Console integration. Creating a Smart Tags cloud configuration allows authentication of API requests from the [!DNL Experience Manager] deployment.

1. In [!DNL Experience Manager], navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** to open the [!UICONTROL Cloud Services] console.

1. Under the **[!UICONTROL Assets Smart Tags]**, open the configuration created above. On the service settings page, click **[!UICONTROL Edit]**.

1. In the **[!UICONTROL AEM Smart Content Service]** dialog, use the pre-populated values for the **[!UICONTROL Service URL]** and **[!UICONTROL Authorization Server]** fields.

1. For the fields [!UICONTROL Api Key], [!UICONTROL Technical Account ID], [!UICONTROL Organization ID], and [!UICONTROL Client Secret], copy and use the following values generated in [Adobe Developer Console integration](#create-adobe-i-o-integration).

   | [!UICONTROL Assets Smart Tagging Service Settings] | [!DNL Adobe Developer Console] integration fields |
   |--- |--- |
   | [!UICONTROL Api Key] | [!UICONTROL CLIENT ID] |
   | [!UICONTROL Technical Account ID] | [!UICONTROL TECHNICAL ACCOUNT ID] |
   | [!UICONTROL Organization ID] | [!UICONTROL ORGANIZATION ID] |
   | [!UICONTROL Client Secret] | [!UICONTROL CLIENT SECRET] |

### Configure OAuth for on-premise users {#config-oauth-onprem}

#### Prerequisites {#prereqs-config-oauth-onprem}

An authorization scope is an OAuth string that contains the following prerequisites:

* Create a new OAuth integration in the [Developer Console](https://developer.adobe.com/console/user/servicesandapis) using `ClientID`, `ClientSecretID`, and `OrgID`.
* Add the following files at this path `/apps/system/config in crx/de`:
   * `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`
   * `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`

#### Configure OAuth for on-premise users {#steps-config-oauth-onprem}

1. Add or update the below properties in `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`:

   * `auth.token.provider.authorization.grants="client_credentials"`
   * `auth.token.provider.orgId="<OrgID>"`
   * `auth.token.provider.default.claims=("\"iss\"\ :\ \"<OrgID>\"")`
   * `auth.token.provider.scope="read_pc.dma_smart_content,\ openid,\ AdobeID,\ additional_info.projectedProductContext"`
     `auth.token.validator.type="adobe-ims-similaritysearch"`
   * Update the `auth.token.provider.client.id` with the Client ID of the new OAuth configuration.
   * Update `auth.access.token.request` to `"https://ims-na1.adobelogin.com/ims/token/v3"`
2. Rename the file to `com.adobe.granite.auth.oauth.accesstoken.provider-<randomnumber>.config`.
3. Perform the steps below in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`:
   * Update the property auth.ims.client.secret with the Client Secret from the new OAuth integration.
   * Rename the file to `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl-<randomnumber>.config`
4. Save all the changes in content repository development console, for example, CRXDE.
5. Navigate to `/system/console/configMgr` and replace the OSGi configuration from `.<randomnumber>` to `-<randomnumber>`.
6. Delete the old configuration for `"Access Token provider name: adobe-ims-similaritysearch"` in `/system/console/configMgr`.
7. Restart the console.

### Validate the configuration {#validate-the-configuration}

After you have completed the configuration, you can use a JMX MBean to validate the configuration. To validate, follow these steps.

1. Access your [!DNL Experience Manager] server at `https://[aem_server]:[port]`.

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** to open the OSGi console. Click **[!UICONTROL Main] > [!UICONTROL JMX]**.

1. Click `com.day.cq.dam.similaritysearch.internal.impl`. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Click `validateConfigs()`. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

The validation results are displayed in the same dialog.
-->

### Slimme tags toepassen inschakelen in de [!UICONTROL DAM Update Asset] -workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .

1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.

1. Klik op **[!UICONTROL Edit]** op de werkbalk.

1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

1. Open de eigenschappen van de stap om de details te wijzigen. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![ vorm het werkschema van de Activa van de Update DAM en voeg slimme markeringsstap ](assets/smart-tag-step-properties-workflow1.png) toe

1. Selecteer op het tabblad **[!UICONTROL Arguments]** de optie **[!UICONTROL Ignore Errors]** als u de workflow wilt voltooien, zelfs als de stap Automatisch labelen is mislukt.

   Als u bovendien elementen wilt labelen terwijl ze worden geüpload, ongeacht of slimme tags zijn ingeschakeld voor mappen, selecteert u **[!UICONTROL Ignore Smart Tag Flag]** .

   ![ vorm het werkschema van de Activa van de Update DAM om slimme markeringsstap toe te voegen en manager vooruit te selecteren ](assets/smart-tag-step-properties-workflow2.png)

1. Klik gedaan ![ gereed pictogram ](assets/do-not-localize/check-ok-done-icon.png) om de processtap te sluiten.

1. Klik op **[!UICONTROL Sync]** om de workflow op te slaan.

## De Smart Content Service trainen {#training-the-smart-content-service}

Als u wilt dat de Smart Content Service uw bedrijfskrionomie herkent, voert u deze uit op een reeks elementen die al tags bevatten die relevant zijn voor uw bedrijf. Om uw merkbeelden effectief te etiketteren, vereist de Slimme Dienst van de Inhoud dat de trainingsbeelden aan bepaalde richtlijnen voldoen. Na de training kan de service dezelfde taxonomie toepassen op een vergelijkbare set activa.

U kunt de service meerdere keren trainen om de service beter in staat te stellen relevante tags toe te passen. Voer na elke trainingscyclus een labelworkflow uit en controleer of uw elementen correct zijn gecodeerd.

U kunt de Slimme Dienst van de Inhoud periodiek of op vereiste basis trainen.

>[!NOTE]
>
>De trainingsworkflow wordt alleen uitgevoerd voor mappen.

### Richtsnoeren voor opleiding {#guidelines-for-training}

Voor de beste resultaten voldoen de afbeeldingen in de trainingsset aan de volgende richtlijnen:

**Hoeveelheid en grootte:** Minimaal 30 afbeeldingen per tag. Minimaal 500 pixels aan de langere zijde.

**Samenhang**: De beelden die voor een specifieke markering worden gebruikt zijn visueel gelijkaardig.

Het is bijvoorbeeld geen goed idee om al deze afbeeldingen als `my-party` te labelen (voor training) omdat ze er anders uitzien.

![ Illustratieve beelden om de richtlijnen voor opleiding ](/help/assets/assets/do-not-localize/coherence.png) te illustreren

**Dekking**: Gebruik voldoende verscheidenheid in de beelden in de opleiding. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat de Experience Manager leert zich te richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen.

Bijvoorbeeld, voor de markering *model-onderstel*, omvat meer opleidingsbeelden gelijkend op het benadrukte beeld hieronder voor de dienst om gelijkaardige beelden nauwkeuriger tijdens het etiketteren te identificeren.

![ Illustratieve beelden om de richtlijnen voor opleiding ](/help/assets/assets/do-not-localize/coverage_1.png) te illustreren

**Vervorming/belemmering**: De de diensttreinen beter op beelden die minder afleiding (duidelijke achtergronden, niet verwante accompanimenten, zoals voorwerpen/personen met het belangrijkste onderwerp) hebben.

Bijvoorbeeld, voor de markering *casual-shoe*, is het tweede beeld geen goede opleidingskandidaat.

![ Illustratieve beelden om de richtlijnen voor opleiding ](/help/assets/assets/do-not-localize/distraction.png) te illustreren

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Voeg bijvoorbeeld voor tags, zoals `raincoat` en `model-side-view`, beide tags toe aan het in aanmerking komende element voordat u dit opneemt voor training.

![ Illustratieve beelden om de richtlijnen voor opleiding ](/help/assets/assets/do-not-localize/completeness.png) te illustreren

>[!NOTE]
>
>Of de Smart Content Service uw tags kan trainen en deze op andere afbeeldingen kan toepassen, hangt af van de kwaliteit van de afbeeldingen die u voor de training gebruikt. Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

### Periodieke training {#periodic-training}

U kunt de Slimme Dienst van de Inhoud toelaten om periodiek op de activa en bijbehorende markeringen binnen een omslag te trainen. Open de pagina [!UICONTROL Properties] van de elementmap, selecteer **[!UICONTROL Enable Smart Tags]** onder het tabblad **[!UICONTROL Details]** en sla de wijzigingen op.

![ enable_smart_tags ](assets/enable_smart_tags.png)

Als deze optie voor een map is geselecteerd, voert [!DNL Experience Manager] automatisch een trainingsworkflow uit om de Smart Content Service op te leiden voor de mappenelementen en hun tags. Standaard wordt de trainingsworkflow wekelijks om 12:30 uur uitgevoerd op zaterdag.

### Opleiding op aanvraag {#on-demand-training}

U kunt de Slimme Dienst van de Inhoud wanneer vereist van de console van het Werkschema trainen.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL Smart Tags Training]** workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.
1. Blader in het dialoogvenster **[!UICONTROL Run Workflow]** naar de payload-map met de gecodeerde elementen voor training voor de service.
1. Geef een titel op voor de workflow en voeg een opmerking toe. Klik vervolgens op **[!UICONTROL Run]** . De elementen en tags worden ter training aangeboden.

   ![ workflow_dialog ](assets/workflow_dialog.png)

>[!NOTE]
>
>Nadat de middelen in een map zijn verwerkt voor training, worden alleen de gewijzigde middelen verwerkt in volgende trainingscycli.

### Trainingsrapporten weergeven {#viewing-training-reports}

Om te controleren of de Slimme Dienst van de Inhoud op uw markeringen in de trainingsreeks activa wordt getraind, herzie het rapport van de opleidingswerkstroom van de console van Rapporten.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]** .
1. Klik op **[!UICONTROL Create]** op de pagina **[!UICONTROL Asset Reports]** .
1. Selecteer het rapport **[!UICONTROL Smart Tags Training]** en klik vervolgens op **[!UICONTROL Next]** op de werkbalk.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk om het rapport weer te geven.
1. Bekijk de details van het rapport.

   Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de Smart Content Service is getraind voor de tag. Een gele kleur geeft aan dat de service niet volledig is getraind voor een bepaalde tag. Voeg in dit geval meer afbeeldingen met de desbetreffende tag toe en voer de trainingsworkflow uit om de service volledig op de tag te trainen.

   Als dit rapport uw tags niet bevat, voert u de trainingsworkflow voor deze tags opnieuw uit.

1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een Microsoft Excel-spreadsheet.

## Beperkingen {#limitations}

* Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de Smart Content Service heeft de volgende beperkingen:

   * Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
   * Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
   * Tags worden ondersteund in de landinstellingen waarin [!DNL Experience Manager] wordt ondersteund.

* Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u [!DNL Assets] Omnzoekopdracht (full-text zoekopdracht). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!MORELIKETHIS]
>
>* [ Overzicht en hoe te om Slimme Markeringen ](enhanced-smart-tags.md) te trainen
>* [ het Oplossen van problemen slimme markeringen voor geloofsbrieven OAuth ](config-oauth.md)
>* [ Videozelfstudie over slimme markeringen ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html)
