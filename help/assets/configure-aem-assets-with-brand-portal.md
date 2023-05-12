---
title: AEM Assets configureren met Brand Portal
seo-title: Configure AEM Assets with Brand Portal
description: Leer hoe u AEM Assets met Brand Portal configureert voor het publiceren van middelen en verzamelingen naar Brand Portal.
seo-description: Learn how to configure AEM Assets with Brand Portal for publishing assets and Collections to Brand Portal.
uuid: b95c046e-9988-444c-b50e-ff5ec8cafe14
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: dca5a2ac-1fc8-4251-b073-730fd6f49b1c
docset: aem65
feature: Brand Portal
role: Admin
exl-id: ae33181c-9eec-421c-be55-4bd019de40b8
hide: true
source-git-commit: 3d5e9ad8ee19756b05e5a77a3f748bc647fcf734
workflow-type: tm+mt
source-wordcount: '1959'
ht-degree: 10%

---

# AEM Assets configureren met Brand Portal {#configure-integration-65}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/configure-aem-assets-with-brand-portal.html?lang=en) |
| AEM 6,5 | Dit artikel |

Met Adobe Experience Manager Assets Brand Portal kunt u goedgekeurde merkmiddelen van Adobe Experience Manager Assets naar Brand Portal publiceren en deze aan Brand Portal-gebruikers distribueren.

AEM Assets is geconfigureerd met Brand Portal via Adobe Developer Console, die een Adobe Identity Management Services (IMS)-accounttoken aanschaft voor toestemming van de Brand Portal-huurder.

>[!NOTE]
>
>Het configureren van AEM Assets met Brand Portal via Adobe Developer Console wordt ondersteund op AEM 6.5.4.0 en hoger.
>
>Eerder, werd Brand Portal gevormd via erfenis OAuth Gateway, die JSON Web Token (JWT) uitwisseling gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning.
>
>Configuratie via verouderde OAuth Gateway wordt vanaf 6 april 2020 niet meer ondersteund en wordt gewijzigd in Adobe Developer Console.

>[!TIP]
>
>***Alleen voor bestaande klanten***
>
>Het wordt geadviseerd om de bestaande oudere configuratie van de Gateway te blijven gebruiken OAuth. In het geval, ontmoet u problemen met erfenisOAuth configuratie van de Gateway, schrapt de bestaande configuratie en creeert nieuwe configuratie via de Console van Adobe Developer.

In deze Help worden de volgende twee gebruiksgevallen beschreven:

* [Nieuwe configuratie](#configure-new-integration-65): Als u een nieuwe Brand Portal-gebruiker bent en uw AEM Assets-auteurinstantie met Brand Portal wilt configureren, kunt u configuratie maken via Adobe Developer Console.
* [Upgradeconfiguratie](#upgrade-integration-65): Als u een bestaande Brand Portal-gebruiker bent die configuratie heeft op een verouderde OAuth Gateway, verwijdert u de bestaande configuratie en maakt u een nieuwe configuratie via Adobe Developer Console.

De verstrekte informatie is gebaseerd op de veronderstelling dat iedereen die deze Hulp leest met de volgende technologieën vertrouwd is:

* Adobe Experience Manager- en AEM-pakketten installeren, configureren en beheren.

* Linux- en Microsoft Windows-besturingssystemen gebruiken.

## Vereisten {#prerequisites}

U hebt het volgende nodig om AEM Assets te configureren met Brand Portal:

* Een AEM Assets-auteur-exemplaar met de nieuwste Service Pack
* URL Brand Portal-gebruiker
* Een gebruiker met systeembeheerdersbevoegdheden op de IMS-organisatie van de Brand Portal-tenant

[Download en installeer AEM 6.5](#aemquickstart)

[Download en installeer de nieuwste AEM Service Pack](#servicepack)

### Download en installeer AEM 6.5 {#aemquickstart}

Het wordt aanbevolen om AEM 6.5 te hebben om een AEM instantie van de auteur in te stellen. Als u niet AEM, download het van de volgende plaatsen:

* Als u een bestaande AEM klant bent, downloadt u AEM 6.5 van [Adobe-website voor licentieverlening](https://licensing.adobe.com).

* Als u een partner van de Adobe bent, gebruik [Adobe Partner Training-programma](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) AEM 6.5.

Nadat u AEM hebt gedownload, vindt u instructies voor het instellen van een AEM instantie van de auteur [implementeren en onderhouden](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html#default-local-install).

### Download en installeer AEM nieuwste Service Pack {#servicepack}

Zie voor gedetailleerde instructies

* [Opmerkingen bij de release AEM 6.5 Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html)

**Contact opnemen met ondersteuning** als u het nieuwste AEM pakket of Service Pack niet kunt vinden.

## Configuratie maken {#configure-new-integration-65}

Voor het configureren van AEM Assets met Brand Portal zijn configuraties vereist in zowel de AEM Assets-auteurinstantie als de Adobe Developer Console.

1. In AEM Assets maakt u een IMS-account en genereert u een openbaar certificaat (openbare sleutel).
1. Maak in Adobe Developer Console een project voor uw Brand Portal-huurder (organisatie).
1. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening (JWT) tot stand te brengen.
1. Krijg de geloofsbrieven van de de dienstrekening en JWT payload informatie.
1. In AEM Assets configureert u de IMS-account met de gegevens van de serviceaccount en de JWT-payload.
1. In AEM Assets configureert u de Brand Portal-cloudservice met behulp van het IMS-account en het Brand Portal-eindpunt (organisatie-URL).
1. Test uw configuratie door middelen van AEM Assets aan Brand Portal te publiceren.

>[!NOTE]
>
>Een AEM Assets-auteur-instantie mag slechts met één Brand Portal-huurder worden geconfigureerd.

Voer de volgende stappen in de vermelde reeks uit als u AEM Assets voor het eerst met Brand Portal configureert:
1. [Openbaar certificaat verkrijgen](#public-certificate)
1. [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)
1. [IMS-account configureren](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)
1. [Configuratie testen](#test-integration)

### IMS-configuratie maken {#create-ims-configuration}

De configuratie IMS verifieert uw AEM Assets auteurinstantie met de huurder van Brand Portal.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-account configureren](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met de openbare sleutel (certificaat) wordt uw profiel geverifieerd op Adobe Developer Console.

1. Meld u aan bij de AEM Assets-auteur. De standaard-URL is `http://localhost:4502/aem/start.html`.

1. Van de **Gereedschappen** ![Gereedschappen](assets/do-not-localize/tools.png) deelvenster, navigeren naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Klik op de pagina Adobe IMS Configurations op **[!UICONTROL Create]**. Het zal worden omgeleid naar de **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina. Standaard worden de **Certificaat** wordt geopend.

1. Selecteren **[!UICONTROL Adobe Brand Portal]** in de **[!UICONTROL Cloud Solution]** vervolgkeuzelijst.

1. Selecteer **[!UICONTROL Create new certificate]** selectievakje en geef een **alias** voor de openbare sleutel. De alias fungeert als naam voor de openbare sleutel.

1. Klik op **[!UICONTROL Create certificate]**. Klik vervolgens op **[!UICONTROL OK]** om de openbare sleutel te produceren.

   ![Create Certificate](assets/ims-config2.png)

1. Klik op de knop **[!UICONTROL Download Public Key]** en sla het bestand met de openbare sleutel (.crt) op uw computer op.

   De openbare sleutel zal later worden gebruikt om API voor uw Brand Portal huurder te vormen en de geloofsbrieven van de de dienstrekening in de Console van Adobe Developer te produceren.

   ![Download Certificate](assets/ims-config3.png)

1. Klik op **[!UICONTROL Next]**.

   In de **Account** wordt een Adobe IMS-account gemaakt waarvoor de referenties van de serviceaccount zijn vereist die in Adobe Developer Console worden gegenereerd. Laat deze pagina voorlopig open.

   Open een nieuw tabblad en [een JWT-verbinding (Service Account) maken in Adobe Developer Console](#createnewintegration) om de referenties en JWT-lading op te halen voor het configureren van de IMS-account.

### Verbinding voor serviceaccount (JWT) maken {#createnewintegration}

In de Console van Adobe Developer, worden de projecten en APIs gevormd op het niveau van de huurder van Brand Portal (organisatie). Als u een API configureert, wordt een JWT-verbinding (Service Account) gemaakt. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. Als u AEM Assets wilt configureren met Brand Portal, moet u een openbare sleutel (certificaat) genereren in AEM Assets en referenties maken in Adobe Developer Console door de openbare sleutel te uploaden. Deze gegevens zijn vereist om de IMS-account in AEM Assets te configureren. Zodra de IMS-account is geconfigureerd, kunt u de Brand Portal-cloudservice in AEM Assets configureren.

Voer de volgende stappen uit om de geloofsbrieven van de de dienstrekening en lading van JWT te produceren:

1. Meld u aan bij Adobe Developer Console met systeembeheerdersrechten voor de IMS-organisatie (Brand Portal-huurder). De standaard-URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Zorg ervoor dat u de juiste IMS-organisatie (Brand Portal-huurder) hebt geselecteerd in de vervolgkeuzelijst (organisatie) in de rechterbovenhoek.

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project met een door het systeem gegenereerde naam gemaakt voor uw organisatie.

   Klikken **[!UICONTROL Edit project]** om de **[!UICONTROL Project Title]** en **[!UICONTROL Description]** en klik op **[!UICONTROL Save]**.

1. In de **[!UICONTROL Project overview]** tabblad, klikt u op **[!UICONTROL Add API]**.

1. In de **[!UICONTROL Add an API window]**, selecteert u **[!UICONTROL AEM Brand Portal]** en klik op **[!UICONTROL Next]**.

   Zorg ervoor dat u toegang hebt tot de AEM Brand Portal-service.

1. In de **[!UICONTROL Configure API]** venster, klikt u op **[!UICONTROL Upload your public key]**. Klik vervolgens op **[!UICONTROL Select a File]** en uploadt u de openbare sleutel (.crt-bestand) die u in het dialoogvenster [openbare verklaring verkrijgen](#public-certificate) sectie.

   Klik op **[!UICONTROL Next]**.

   ![Openbare sleutel uploaden](assets/service-account3.png)

1. De openbare sleutel controleren en klikken **[!UICONTROL Next]**.

1. Selecteren **[!UICONTROL Assets Brand Portal]** als het standaardproductprofiel en klik op **[!UICONTROL Save configured API]**.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Productprofiel selecteren](assets/service-account4.png)

1. Nadat de API is geconfigureerd, wordt u omgeleid naar de API-overzichtspagina. Vanaf de linkernavigatie onder **[!UICONTROL Credentials]**, klikt u op de knop **[!UICONTROL Service Account (JWT)]** optie.

   >[!NOTE]
   >
   >U kunt de geloofsbrieven bekijken en acties uitvoeren zoals produceren JWT tokens, exemplaar credentiedetails, terugwinnen cliëntgeheim, etc.

1. Van de **[!UICONTROL Client Credentials]** kopiëren **[!UICONTROL client ID]**.

   Klikken **[!UICONTROL Retrieve Client Secret]** en kopieert u de **[!UICONTROL client secret]**.

   ![Servicerekeningen](assets/service-account5.png)

1. Ga naar de **[!UICONTROL Generate JWT]** en kopieer de **[!UICONTROL JWT Payload]** informatie.

U kunt nu de client-id (API-sleutel), het clientgeheim en de JWT-payload gebruiken naar [IMS-account configureren](#create-ims-account-configuration) in AEM Assets.

<!--
### Create Adobe I/O integration {#createnewintegration}

Adobe I/O integration generates API Key, Client Secret, and Payload (JWT) which is required in setting up the IMS Account configurations.

1. Login to Adobe I/O Console with system administrator privileges on the IMS organization of the Brand Portal tenant.

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

   The API Key, Client Secret key, and JWT payload information will be used to create IMS account configuration.
-->

### IMS-account configureren {#create-ims-account-configuration}

Controleer of u de volgende stappen hebt uitgevoerd:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)

Voer de volgende stappen uit om de IMS-account te configureren.

1. Open de IMS-configuratie en navigeer naar de **[!UICONTROL Account]** tab. U hebt de pagina geopend gehouden terwijl [verkrijgen van het openbare certificaat](#public-certificate).

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   In de **[!UICONTROL Authorization Server]** -veld, geeft u de URL op: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/).

   Client-id opgeven in het dialoogvenster **[!UICONTROL API key]** veld, **[!UICONTROL Client Secret]**, en **[!UICONTROL Payload]** (JWT-lading) die u hebt gekopieerd terwijl [maken van de verbinding van de serviceaccount (JWT)](#createnewintegration).

   Klik op **[!UICONTROL Create]**.

   De IMS-account is geconfigureerd.

   ![IMS Account configuration](assets/create-new-integration6.png)

1. Selecteer de IMS-accountconfiguratie en klik op **[!UICONTROL Check Health]**.

   Klikken **[!UICONTROL Check]** in het dialoogvenster. Bij een geslaagde configuratie verschijnt het bericht dat de *Token is opgehaald*.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>U kunt slechts één IMS-configuratie hebben.
>
>Zorg ervoor dat de IMS-configuratie slaagt voor de statuscontrole. Als de configuratie niet slaagt voor de statuscontrole, is deze ongeldig. U moet deze dan verwijderen en een nieuwe, geldige configuratie maken.

### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de Brand Portal-cloudservice te configureren:

1. Meld u aan bij de AEM Assets-auteur.

1. Van de **Gereedschappen** ![Gereedschappen](assets/do-not-localize/tools.png) deelvenster, navigeren naar **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klik op de pagina Brand Portal Configurations op **[!UICONTROL Create]**.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de IMS-configuratie die u hebt gemaakt terwijl u [configureren van IMS-account](#create-ims-account-configuration).

   In de **[!UICONTROL Service URL]** -veld, geeft u de URL van uw Brand Portal-huurder (organisatie) op.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save & Close]**. De cloudconfiguratie wordt gemaakt.

   Uw AEM Assets-auteurinstantie is nu geconfigureerd met de Brand Portal-huurder.

### Configuratie testen {#test-integration}

Voer de volgende stappen uit om de configuratie te valideren:

1. Meld u aan bij uw AEM Assets-cloudinstantie.

1. Van de **Gereedschappen** ![Gereedschappen](assets/do-not-localize/tools.png) deelvenster, navigeren naar **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**.

   ![](assets/test-integration1.png)

1. Klik op de pagina Replicatie op **[!UICONTROL Agents on author]**.

   ![](assets/test-integration2.png)

   U kunt de vier replicatieagenten zien die voor uw huurder van Brand Portal worden gecreeerd.

   Bepaal de plaats van de replicatieagenten van uw Brand Portal huurder en klik op de replicatieagent URL.

   ![](assets/test-integration3.png)

   >[!NOTE]
   >
   >De replicatieagenten werken parallel en delen de baandistributie gelijk, daardoor verhogend de het publiceren snelheid met vier keer de originele snelheid. Nadat de wolkendienst wordt gevormd, wordt de extra configuratie niet vereist om de replicatieagenten toe te laten die door gebrek worden geactiveerd om parallelle publicatie van veelvoudige activa toe te laten.

1. Als u de verbinding tussen AEM Assets en Brand Portal wilt controleren, klikt u op de knop **[!UICONTROL Test Connection]** pictogram.

   ![](assets/test-integration4.png)

   Er verschijnt een bericht dat uw *testpakket is afgeleverd*.

   ![](assets/test-integration5.png)

1. Verifieer de testresultaten op alle vier replicatieagenten.


   >[!NOTE]
   >
   >Vermijd onbruikbaar makend om het even welke replicatieagenten, aangezien het de replicatie van de activa (in werking stellen-in-rij) kan veroorzaken om te ontbreken.
   >
   >Zorg ervoor dat alle vier replicatieagenten worden gevormd om onderbrekingsfout te vermijden. Zie [Problemen met parallelle publicatie naar Brand Portal oplossen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/troubleshoot-parallel-publishing.html#connection-timeout).
   >
   >Wijzig geen automatisch gegenereerde instellingen.

U kunt nu het volgende doen:

* [Assets publiceren van AEM Assets naar Brand Portal](../assets/brand-portal-publish-assets.md)
* [Elementen publiceren van Brand Portal naar AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) - Asset Souring in Brand Portal
* [Mappen publiceren van AEM Assets naar Brand Portal](../assets/brand-portal-publish-folder.md)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](../assets/brand-portal-publish-collection.md)
* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

Zie [Brand Portal-documentatie](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor meer informatie .


## Upgradeconfiguratie {#upgrade-integration-65}

Voer de volgende stappen in de vermelde reeks uit om uw bestaande configuraties bij te werken naar Adobe Developer Console:
1. [Werken met taken controleren](#verify-jobs)
1. [Bestaande configuraties verwijderen](#delete-existing-configuration)
1. [Configuratie maken](#configure-new-integration-65)

### Werken met taken controleren {#verify-jobs}

Zorg ervoor dat er geen publicatietaak wordt uitgevoerd op de AEM Assets-ontwerpinstantie voordat u wijzigingen aanbrengt. Voor dat, kunt u het statuut van actieve banen op alle vier replicatieagenten verifiëren en ervoor zorgen dat de rijen nutteloos zijn.

1. Meld u aan bij de AEM Assets-auteur.

1. Van de **Gereedschappen** ![Gereedschappen](assets/do-not-localize/tools.png) deelvenster, navigeren naar **[!UICONTROL Deployment]** > **[!UICONTROL Deployment Replication]**.

1. Klik op de pagina Replicatie op **[!UICONTROL Agents on author]**.

   ![](assets/test-integration2.png)

1. Bepaal de plaats van de replicatieagenten van uw huurder van Brand Portal.

   Zorg ervoor dat de **Wachtrij is inactief** voor alle replicatieagenten, is geen het publiceren baan actief.

   ![](assets/test-integration3.png)

### Bestaande configuraties verwijderen {#delete-existing-configuration}

U moet de volgende controlelijst in werking stellen terwijl het schrappen van de bestaande configuraties:
* Alle vier replicatieagents verwijderen
* Brand Portal-cloudservice verwijderen
* MAC-gebruiker verwijderen

1. Meld u aan bij de AEM Assets-auteur en open CRX Lite als beheerder. De standaard-URL is `http://localhost:4502/crx/de/index.jsp`.

1. Navigeren naar `/etc/replications/agents.author` en schrapt alle vier replicatieagenten van uw Brand Portal huurder.

   ![](assets/delete-replication-agent.png)

1. Navigeren naar `/etc/cloudservices/mediaportal` en verwijder de configuratie van de Brand Portal-cloudservice.

   ![](assets/delete-cloud-service.png)

1. Navigeren naar `/home/users/mac` en de **Mac-gebruiker** van je Brand Portal-huurder.

   ![](assets/delete-mac-user.png)


U kunt nu [configuratie maken](#configure-new-integration-65) via Adobe Developer Console op uw AEM 6.5-auteurexemplaar.



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->
