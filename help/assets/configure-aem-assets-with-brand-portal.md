---
title: AEM Assets configureren met Brand Portal
description: Leer hoe u AEM Assets met Brand Portal configureert voor het publiceren van middelen en verzamelingen naar Brand Portal.
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
docset: aem65
feature: Brand Portal
role: Admin
exl-id: ae33181c-9eec-421c-be55-4bd019de40b8
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 75c15b0f0e4de2ea7fff339ae46b88ce8f6af83f
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 3%

---


# AEM Assets configureren met Brand Portal {#configure-integration-65}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal) |
| AEM 6.5 | Dit artikel |

Met Adobe Experience Manager Assets Brand Portal kunt u goedgekeurde merkmiddelen van Adobe Experience Manager Assets naar Brand Portal publiceren en deze aan de Brand Portal-gebruikers distribueren.

AEM Assets is geconfigureerd met Brand Portal via Adobe Developer Console, dat een Adobe Identity Management Services (IMS)-accounttoken aanschaft voor toestemming van de Brand Portal-huurder.

>[!NOTE]
>
>Het configureren van AEM Assets met Brand Portal via Adobe Developer Console wordt ondersteund op AEM 6.5.4.0 en hoger.
>
<!--
>Earlier, Brand Portal was configured via legacy OAuth Gateway, which uses the JSON Web Token (JWT) exchange to obtain an IMS Access token for authorization. 
>
>Configuration via legacy OAuth Gateway is no longer supported from April 6, 2020, and is changed to Adobe Developer Console.
-->

>[!TIP]
>
>***slechts voor bestaande klanten***
>
>Adobe raadt u aan de bestaande OAuth Gateway-configuratie te blijven gebruiken. Als u problemen met erfenisconfiguratie OAuth van de Gateway tegenkomt, schrap de bestaande configuratie en creeer een configuratie door middel van Adobe Developer Console.

<!--
This help describes the following two use-cases:

* [New configuration](#configure-new-integration-65): If you are a new Brand Portal user and want to configure your AEM Assets Author instance with Brand Portal, you can create a configuration by way of the Adobe Developer Console. 
* [Upgrade configuration](#upgrade-integration-65): If you are an existing Brand Portal user having configuration on legacy OAuth Gateway, delete the existing configuration and create a configuration by way of Adobe Developer Console.
-->
De verstrekte informatie is gebaseerd op de veronderstelling dat iedereen die deze Hulp leest met de volgende technologieën vertrouwd is:

* Adobe Experience Manager- en AEM-pakketten installeren, configureren en beheren.

* Werken met Linux® en Microsoft® Windows.

## Vereisten {#prerequisites}

U hebt het volgende nodig om AEM Assets te configureren met Brand Portal:

* Een AEM Assets Author-instantie voor meer informatie met het nieuwste Service Pack
* URL Brand Portal-gebruiker
* Een gebruiker met systeembeheerdersrechten voor de IMS-organisatie van de Brand Portal-huurder

[AEM 6.5 downloaden en installeren](#aemquickstart)

[Download en installeer de nieuwste AEM Service Pack](#servicepack)

### AEM 6.5 downloaden en installeren {#aemquickstart}

Het wordt aanbevolen om AEM 6.5 te hebben om een AEM Author-instantie in te stellen. Als AEM niet actief is, kunt u het downloaden van de volgende locaties:

* Als u een bestaande klant van AEM bent, download AEM 6.5 van de [ Adobe Vergunnende website ](https://licensing.adobe.com).

* Als u een Adobe-partner bent, gebruikt u het Adobe Partner Training Program om AEM 6.5 aan te vragen.

Nadat u AEM downloadt, voor instructies aan opstelling een instantie van de Auteur van AEM, zie [ het opstellen en het handhaven ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/implementing/deploying/deploying/deploy#default-local-install).

### Download en installeer AEM latest Service Pack {#servicepack}

Voor gedetailleerde instructies, zie de huidige [ AEM 6.5 Nota&#39;s van de Versie van het Pak van de Dienst ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/release-notes/release-notes).

**contacteer de Klantenondersteuning van Adobe** als u niet het recentste pakket van AEM of Service Pack kunt vinden.

## Configuratie maken {#configure-new-integration-65}

>[!NOTE]
>
>U kunt vanaf juni 2024 geen nieuwe JWT-referenties maken. Voortaan worden alleen OAuth-referenties gemaakt. Zie meer bij het creëren van een configuratie OAuth.

Voor het configureren van AEM Assets met Brand Portal zijn configuraties vereist in zowel de AEM Assets Author-instantie als de Adobe Developer Console.

1. Maak in Adobe Developer Console een project voor uw Brand Portal-huurder (organisatie).
1. In Experience Manager Assets configureert u de Brand Portal-cloudservice met behulp van het IMS-account en het Brand Portal-eindpunt (organisatie-URL).
1. Test uw configuratie door middelen van Experience Manager Assets aan Brand Portal te publiceren.

<!--
1. In AEM Assets, create an IMS account and generate a public certificate (public key).
1. In Adobe Developer Console, create a project for your Brand Portal tenant (organization).
1. Under the project, configure an API using the public key to create a service account (JWT) connection.
1. Get the service account credentials and JWT payload information.
1. In AEM Assets, configure the IMS account using the service account credentials and JWT payload.
1. In AEM Assets, configure the Brand Portal cloud service using the IMS account and Brand Portal endpoint (organization URL).
1. Test your configuration by publishing an asset from AEM Assets to Brand Portal.
-->

>[!NOTE]
>
>Een AEM Assets Author-instantie mag slechts met één Brand Portal-huurder worden geconfigureerd.

Voer de volgende stappen in de vermelde reeks uit als u AEM Assets voor het eerst met Brand Portal configureert:

### Een nieuwe configuratie maken {#create-new-configuration}

Voer de volgende stappen in de opgegeven reeks uit om Experience Manager Assets met Brand Portal te configureren.

1. [De OAuth-referenties configureren in de Adobe Developer Console](#config-oauth)
1. [Een nieuwe Adobe IMS-integratie maken met OAuth](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-cloud-service)

#### De OAuth-referenties configureren in de Adobe Developer Console {#config-oauth}

[ vorm de geloofsbrieven OAuth in Adobe Developer Console ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/security/setting-up-ims-integrations-for-aem#credentials-in-the-developer-console) en selecteer Brand Portal API.

#### Nieuwe Adobe IMS-integratie maken met OAuth {#create-ims-account-configuration}

[ creeer een nieuwe Integratie van Adobe IMS gebruikend OAuth ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/security/setting-up-ims-integrations-for-aem#creating-oauth-configuration) en selecteer Brand Portal van drop-down.

#### Cloudservice configureren {#configure-cloud-service}

<!--
1. [Obtain a public certificate](#public-certificate)
1. [Create service account (JWT) connection](#createnewintegration) 
1. [Configure an IMS account](#create-ims-account-configuration)
1. [Configure cloud service](#configure-cloud-service)
1. [Test configuration](#test-integration)
-->
<!--
### Create IMS configuration {#create-ims-configuration}

The IMS configuration authenticates your AEM Assets Author instance with the Brand Portal tenant. 

IMS configuration includes two steps:

* [Obtain a public certificate](#public-certificate) 
* [Configure an IMS account](#create-ims-account-configuration)

### Obtain public certificate {#public-certificate}

The public key (certificate) authenticates your profile on Adobe Developer Console.

1. Log in to your AEM Assets Author instance. The default URL is `http://localhost:4502/aem/start.html`.

1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. In the Adobe IMS Configurations page, click **[!UICONTROL Create]**. It redirects to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page. By default, the **Certificate** tab opens.

1. Select **[!UICONTROL Adobe Brand Portal]** in the **[!UICONTROL Cloud Solution]** dropdown list.  

1. Select the **[!UICONTROL Create new certificate]** check box and specify an **alias** for the public key. The alias serves as the name of the public key. 

1. Click **[!UICONTROL Create certificate]**. Then, click **[!UICONTROL OK]** to generate the public key.

   ![Create Certificate](assets/ims-config2.png)

1. Click the **[!UICONTROL Download Public Key]** icon and save the public key (.crt) file on your machine. 

   The public key is used later to configure the API for your Brand Portal tenant and generate service account credentials in Adobe Developer Console.

   ![Download Certificate](assets/ims-config3.png)

1. Click **[!UICONTROL Next]**. 

   In the **Account** tab, an Adobe IMS account is created which requires the service account credentials that are generated in Adobe Developer Console. Keep this page open for now.

   Open a new tab and [create a service account (JWT) connection in Adobe Developer Console](#createnewintegration) so you can get the credentials and JWT payload for configuring the IMS account. 

### Create the service account (JWT) connection {#createnewintegration}

In Adobe Developer Console, projects and APIs are configured at the Brand Portal tenant (organization) level. Configuring an API creates a service account (JWT) connection. There are two methods to configure the API, by generating a key pair (private and public keys) or by uploading a public key. To configure AEM Assets with Brand Portal, you must generate a public key (certificate) in AEM Assets and create credentials in Adobe Developer Console by uploading the public key. These credentials are required to configure the IMS account in AEM Assets. Once the IMS account is configured, you can configure the Brand Portal cloud service in AEM Assets.

To create the service account credentials and JWT payload, do the following:

1. Log in to Adobe Developer Console with system administrator privileges on the IMS organization (Brand Portal tenant). The default URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Ensure that you have selected the correct IMS organization (Brand Portal tenant) from the drop-down (organization) list in the upper-right corner.

1. Click **[!UICONTROL Create new project]**. A blank project with a system-generated name is created for your organization. 

   Click **[!UICONTROL Edit project]** so you can update the **[!UICONTROL Project Title]** and **[!UICONTROL Description]**, and click **[!UICONTROL Save]**.
   
1. In the **[!UICONTROL Project overview]** tab, click **[!UICONTROL Add API]**.

1. In the **[!UICONTROL Add an API window]**, select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Next]**. 

   Ensure that you have access to the AEM Brand Portal service.

1. In the **[!UICONTROL Configure API]** window, click **[!UICONTROL Upload your public key]**. Then, click **[!UICONTROL Select a File]** and upload the public key (.crt file) that you have downloaded in the [obtain public certificate](#public-certificate) section. 

   Click **[!UICONTROL Next]**.

   ![Upload Public Key](assets/service-account3.png)

1. Verify the public key and click **[!UICONTROL Next]**.

1. Select **[!UICONTROL Assets Brand Portal]** as the default product profile and click **[!UICONTROL Save configured API]**. 
-->
<!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->
<!--
   ![Select Product Profile](assets/service-account4.png)

1. Once the API is configured, you are redirected to the API overview page. From the left navigation under **[!UICONTROL Credentials]**, click the **[!UICONTROL Service Account (JWT)]** option.

   >[!NOTE]
   >
   >You can view the credentials and perform actions such as generate JWT tokens, copy credential details, and retrieve client secret.

1. From the **[!UICONTROL Client Credentials]** tab, copy the **[!UICONTROL client ID]**. 

   Click **[!UICONTROL Retrieve Client Secret]** and copy the **[!UICONTROL client secret]**.

   ![Service Account Credentials](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]** information. 

You can now use the client ID (API key), client secret, and JWT payload to [configure the IMS account](#create-ims-account-configuration) in AEM Assets.

<!--
### Create Adobe I/O integration {#createnewintegration}

Adobe I/O integration generates API Key, Client Secret, and Payload (JWT) which is required in setting up the IMS Account configurations.

1. Login to Adobe Developer Console with system administrator privileges on the IMS organization of the Brand Portal tenant.

   Default URL: [https://console.adobe.io/](https://console.adobe.io/) 

1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create a new integration page opens. 
   
   Select your organization from the drop-down list.

   In **[!UICONTROL Experience Cloud]**, Select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Continue]**. 

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Create Integration](assets/create-new-integration2.png)

1. Specify a name and description for the integration. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Select the profile of your organization. 

   Or, select the default profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Create Integration]**. The integration is created.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information. 

   Copy the **[!UICONTROL API Key]** 
   
   Click **[!UICONTROL Retrieve Client Secret]** and copy the Client Secret key.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigate to **[!UICONTROL JWT]** tab, and copy the **[!UICONTROL JWT payload]**.

   The API Key, Client Secret key, and JWT payload information that is used to create IMS account configuration.
-->
<!--
### Configure the IMS account {#create-ims-account-configuration}

Ensure that you have already performed the following steps:

* [Obtain a public certificate](#public-certificate)
* [Create service account (JWT) connection](#createnewintegration)

To configure the IMS account: 

1. Open the IMS Configuration and navigate to the **[!UICONTROL Account]** tab. You kept the page open while [obtaining the public certificate](#public-certificate).

1. Specify a **[!UICONTROL Title]** for the IMS account.

   In the **[!UICONTROL Authorization Server]** field, specify the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/).  

   Specify client ID in the **[!UICONTROL API key]** field, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]** (JWT payload) that you have copied while [creating the service account (JWT) connection](#createnewintegration).

   Click **[!UICONTROL Create]**.

   The IMS account is configured. 

   ![IMS Account configuration](assets/create-new-integration6.png)
   
1. Select the IMS account configuration and click **[!UICONTROL Check Health]**.

   Click **[!UICONTROL Check]** in the dialog box. On successful configuration, a message appears that the *Token is retrieved successfully*.

   ![Healthy Configuration confirmation dialog](assets/create-new-integration5.png)

>[!CAUTION]
>
>You must have only one IMS configuration.
>
>Ensure that the IMS configuration passes the health check. If the configuration does not pass the health check, it is invalid. Delete it and create another valid configuration.
-->

1. Meld u aan bij uw AEM Assets Author-exemplaar.

1. Van **Hulpmiddelen** ![ ](assets/do-not-localize/tools.png) paneel van Hulpmiddelen, navigeer aan **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klik op **[!UICONTROL Create]** op de pagina Brand Portal Configurations.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de configuratie IMS die u terwijl [ het vormen van de rekening IMS ](#create-ims-account-configuration) hebt gecreeerd.

   Geef in het veld **[!UICONTROL Service URL]** de URL van de Brand Portal-huurder (organisatie) op.

   ![ het venster van de Configuratie van Brand Portal ](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save & Close]**. De cloudconfiguratie wordt gemaakt.

   Uw AEM Assets Author-instantie is nu geconfigureerd met de Brand Portal-huurder.

<!--

### Test and validate the configuration {#test-integration}

1. Log in to your AEM Assets cloud instance.

1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**.

   ![The Tools panel](assets/test-integration1.png)

1. In the Replication page, click **[!UICONTROL Agents on Author]**.

   ![Replication page](assets/test-integration2.png)

   You can see the four replication agents created for your Brand Portal tenant. 

   Locate the replication agents of your Brand Portal tenant and click the replication agent URL. 

   ![Assets replication configuration](assets/test-integration3.png)

   >[!NOTE]
   >
   >The replication agents work in parallel and share the job distribution equally, so that it increases the publishing speed by four times the original speed. After the cloud service is configured, additional configuration is not required to enable the replication agents that are activated by default to enable parallel publishing of multiple assets.

1. To verify the connection between AEM Assets and Brand Portal, click the **[!UICONTROL Test Connection]** icon.

   ![Verifying the assets replication settings](assets/test-integration4.png)

   A message appears that your *test package is successfully delivered*.

   ![Test confirmation output](assets/test-integration5.png)

1. Verify the test results on all four replication agents.


   >[!NOTE]
   >
   >Avoid disabling any of the replication agents, as it can cause the replication of the assets (running-in-queue) to fail.
   >
   >Ensure that all the four replication agents are configured to avoid timeout error. See [troubleshoot issues in parallel publishing to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html?lang=nl-NL#connection-timeout).
   >
   >Do not modify any autogenerated settings.

You can now:

* [Publish assets from AEM Assets to Brand Portal](../assets/brand-portal-publish-assets.md)
* [Publish assets from Brand Portal to AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=nl-NL) - Asset Sourcing in Brand Portal 
* [Publish folders from AEM Assets to Brand Portal](../assets/brand-portal-publish-folder.md)
* [Publish collections from AEM Assets to Brand Portal](../assets/brand-portal-publish-collection.md) 
* [Publish presets, schemas, and facets to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html?lang=nl-NL)
* [Publish tags to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html?lang=nl-NL)

See the [Brand Portal documentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=nl-NL) for more information.

-->
<!--
## Upgrade configuration {#upgrade-integration-65}

To upgrade your existing configurations to Adobe Developer Console, do the following steps, in the listed sequence : 

1. [Verify running jobs](#verify-jobs)
1. [Delete existing configurations](#delete-existing-configuration)
1. [Create configuration](#configure-new-integration-65)

### Verify running jobs {#verify-jobs}

Ensure that no publishing job is running on your AEM Assets Author instance before you make any edits. For that, you can verify the status of active jobs on all the four replication agents and ensure that the queues are idle.  

1. Log in to your AEM Assets Author instance.

1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Deployment Replication]**.

1. In the Replication page, click **[!UICONTROL Agents on Author]**.

   ![Replication agents for assets](assets/test-integration2.png)

1. Locate the replication agents of your Brand Portal tenant. 
   
   Ensure that the **Queue is Idle** for all the replication agents, and no publishing job is active. 

   ![Replication queue settings](assets/test-integration3.png)

### Delete existing configurations {#delete-existing-configuration}

Run the following checklist while deleting the existing configurations:

* Delete all four replication agents
* Delete Brand Portal cloud service
* Delete Mac user 

1. Log in to your AEM Assets Author instance and open CRX Lite as an administrator. The default URL is `http://localhost:4502/crx/de/index.jsp`.

1. Navigate to `/etc/replications/agents.author` and delete all the four replication agents of your Brand Portal tenant.

   ![Replication agent in CRXDE](assets/delete-replication-agent.png)

1. Navigate to `/etc/cloudservices/mediaportal` and delete the Brand Portal cloud service configuration.

   ![Detail of replication agent in CRXDE](assets/delete-cloud-service.png)

1. Navigate to `/home/users/mac` and delete the **Mac user** of your Brand Portal tenant.

   ![More detail of replication agent in CRXDE](assets/delete-mac-user.png)


You can now [create a configuration](#configure-new-integration-65) by way of the Adobe Developer Console on your AEM 6.5 Author instance. 
-->
