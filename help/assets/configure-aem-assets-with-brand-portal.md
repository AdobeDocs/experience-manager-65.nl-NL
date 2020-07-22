---
title: AEM Assets configureren met Brand Portal
seo-title: AEM Assets configureren met Brand Portal
description: Leer hoe u AEM Assets configureert met Brand Portal voor het publiceren van middelen en verzamelingen naar Brand Portal.
seo-description: Leer hoe u AEM Assets configureert met Brand Portal voor het publiceren van middelen en verzamelingen naar Brand Portal.
uuid: b95c046e-9988-444c-b50e-ff5ec8cafe14
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: dca5a2ac-1fc8-4251-b073-730fd6f49b1c
docset: aem65
translation-type: tm+mt
source-git-commit: 91caca39b0b6c5c0c98b58be02f518901a3d90e3
workflow-type: tm+mt
source-wordcount: '1943'
ht-degree: 14%

---


# AEM Assets configureren met Brand Portal {#configure-integration-65}

Adobe Experience Manager-elementen (AEM) worden geconfigureerd met het Brand Portal via de Adobe Developer Console, die een IMS-token aanschaft voor goedkeuring door uw Pandhouder.

>[!NOTE]
>
>Het configureren van AEM Assets met Brand Portal via Adobe Developer Console wordt ondersteund op AEM 6.5.4.0 en hoger.
>
>Eerder, werd het Portaal van het Merk gevormd in Klassieke UI via Verouderde Gateway OAuth, die de het symbolenuitwisseling van JWT gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning.
>
>Configuratie via verouderde OAuth wordt vanaf 6 april 2020 niet meer ondersteund en wordt gewijzigd in configuratie via Adobe Developer Console.


>[!TIP]
>
>***Alleen voor bestaande klanten***
>
>Het wordt geadviseerd om bestaande oudere configuratie van de Gateway te blijven gebruiken OAuth. Als er problemen optreden met de oudere OAuth Gateway-configuratie, verwijdert u de bestaande configuratie en maakt u een nieuwe configuratie via Adobe Developer Console.



In deze Help worden de volgende twee gebruiksgevallen beschreven:
* [Nieuwe configuratie](#configure-new-integration-65): Als u een nieuwe gebruiker van het Merk Portal bent en uw AEM Assets auteurinstantie met het Portaal van het Merk wilt vormen, kunt u nieuwe configuratie op de Console van de Ontwikkelaar van Adobe tot stand brengen.
* [Configuratie](#upgrade-integration-65)upgrade: Als u een bestaande gebruiker van het Portaal van het Merk met uw AEM Assets auteurinstantie bent die met het Portaal van het Merk op erfenisOAuth Gateway wordt gevormd, wordt het geadviseerd om de bestaande configuraties te schrappen en nieuwe configuratie op de Console van de Ontwikkelaar van Adobe tot stand te brengen.

De verstrekte informatie is gebaseerd op de veronderstelling dat iedereen die deze Hulp leest met de volgende technologieën vertrouwd is:

* Adobe Experience Manager- en AEM-pakketten installeren, configureren en beheren.

* Linux- en Microsoft Windows-besturingssystemen gebruiken.

## Vereisten {#prerequisites}

U hebt het volgende nodig om AEM Assets te configureren met Brand Portal:

* Een up-to-run AEM Assets auteur-instantie met het nieuwste Service Pack.
* URL van Brand Portal-tenant.
* Een gebruiker met systeembeheerdersbevoegdheden op de IMS-organisatie van de Brand Portal-tenant.


[AEM 6.5 downloaden en installeren](#aemquickstart)

[De nieuwste AEM Service Pack downloaden en installeren](#servicepack)

### AEM 6.5 downloaden en installeren {#aemquickstart}

Het wordt aanbevolen AEM 6.5 te hebben om een instantie van AEM-auteur in te stellen. Als AEM niet actief is, kunt u het downloaden van de volgende locaties:

* Als u een bestaande AEM-klant bent, downloadt u AEM 6.5 van de [Adobe-licentiewebsite](http://licensing.adobe.com).

* Als u een Adobe-partner bent, gebruikt u het [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) om AEM 6.5 aan te vragen.

Nadat u AEM hebt gedownload, raadpleegt u het [implementeren en onderhouden](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall)van instructies voor het instellen van een AEM-auteurinstantie.

### Download en installeer de nieuwste AEM Service Pack {#servicepack}

Zie voor gedetailleerde instructies

* [Opmerkingen bij de release AEM 6.5 Service Pack](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html)

**Neem contact op met de klantenservice** als u het nieuwste AEM-pakket of Service Pack niet kunt vinden.

## Configuratie maken {#configure-new-integration-65}

Voor het configureren van AEM Assets met Brand Portal zijn configuraties vereist in zowel de auteur-instantie van AEM Assets als in de Adobe Developer Console.

1. Maak in de auteur van AEM Assets een IMS-account en genereer een openbaar certificaat (openbare sleutel).

1. In de Console van de Ontwikkelaar van Adobe, creeer een project voor uw Poorthuurder van het Merk (organisatie).

1. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening (JWT) tot stand te brengen.

1. Krijg de geloofsbrieven van de de dienstrekening en JWT payload informatie.

1. In de auteursinstantie van AEM Assets, vorm de rekening IMS gebruikend de geloofsbrieven van de de dienstrekening en JWT lading.

1. In de auteur van AEM Assets, vorm de Poortwolkendienst van het Merk gebruikend de rekening IMS en het Poorteindpunt van het Merk (organisatie URL).

1. Test de configuratie door activa van de auteursinstantie van AEM Assets aan het Portaal van het Merk te publiceren.


>[!NOTE]
>
>Een Brand Portal-huurder mag slechts met één AEM Assets-auteur worden geconfigureerd.
>
>Vorm geen Poorthuurder van het Merk met veelvoudige de auteur van AEM Assets instanties.



Voer de volgende stappen in de vermelde opeenvolging uit als u AEM Assets met het Portaal van het Merk voor het eerst vormt:
1. [Openbaar certificaat verkrijgen](#public-certificate)
1. [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)
1. [IMS-account configureren](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)
1. [Configuratie testen](#test-integration)

### IMS-configuratie maken {#create-ims-configuration}

IMS-configuratie verifieert uw Brand Portal-tenant met de AEM Assets-auteurinstantie.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-account configureren](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

1. Meld u aan bij de auteur-instantie van uw AEM Assets. De standaard-URL is
   `http:// localhost:4502/aem/start.html`
1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

   ![Gebruikersinterface voor Adobe IMS-accountconfiguratie](assets/ims-config1.png)

1. Klik op de pagina Adobe IMS Configurations **[!UICONTROL Create]**.

1. U wordt omgeleid naar de **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina. By default, the **Certificate** tab opens.

   Selecteer de cloudoplossing **[!UICONTROL Adobe Brand Portal]**.

1. Schakel het selectievakje **[!UICONTROL Create new certificate]** in en geef een **alias** op voor het certificaat. De alias fungeert als naam voor het dialoogvenster.

1. Klik op **[!UICONTROL Create certificate]**. Klik vervolgens **[!UICONTROL OK]** in het dialoogvenster om het openbare certificaat te genereren.

   ![Create Certificate](assets/ims-config2.png)

1. Click **[!UICONTROL Download Public Key]** and save the certificate (.crt) file on your machine.

   Het certificaatbestand wordt in verdere stappen gebruikt om de API voor uw Brand Portal-gebruiker te configureren en de referenties van de serviceaccount te genereren in Adobe Developer Console.

   ![Download Certificate](assets/ims-config3.png)

1. Klik op **[!UICONTROL Next]**.

   Op het tabblad **Account** maakt u de Adobe IMS-account, maar hiervoor hebt u de verificatiegegevens van de serviceaccount nodig die zijn gegenereerd in Adobe Developer Console. Laat deze pagina voorlopig open.

   Open een nieuw tabblad en [maak een JWT-verbinding (Service Account) in Adobe Developer Console](#createnewintegration) om de referenties en JWT-lading voor het configureren van de IMS-account op te halen.

### Verbinding voor serviceaccount (JWT) maken {#createnewintegration}

In de Console van de Ontwikkelaar van Adobe, worden de projecten en APIs gevormd op organisatie (de huurder van het Portaal van het Merk) niveau. Als u een API configureert, wordt er een JWT-verbinding (Service Account) gemaakt in de Adobe Developer Console. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. Als u een auteur-instantie van een AEM Assets wilt configureren met Brand Portal, moet u een openbaar certificaat (openbare sleutel) genereren in de auteur-instantie van een AEM Assets en referenties maken in Adobe Developer Console door de openbare sleutel te uploaden. Deze openbare sleutel wordt gebruikt om API voor de geselecteerde organisatie van het Portaal van het Merk te vormen en produceert de geloofsbrieven en JWT nuttige lading voor de de dienstrekening. Deze geloofsbrieven worden verder gebruikt om de rekening IMS in de auteursinstantie van AEM Assets te vormen. Zodra de rekening IMS wordt gevormd, kunt u de de wolkendienst van het Portaal van de Merk in de auteursinstantie van AEM Assets vormen.

Voer de volgende stappen uit om de geloofsbrieven van de de dienstrekening en lading van JWT te produceren:

1. Meld u aan bij de Adobe Developer Console met systeembeheerdersrechten voor de IMS-organisatie (Brand Portal-gebruiker). De standaard-URL is

   [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui)


   >[!NOTE]
   >
   >Zorg ervoor dat u de juiste IMS-organisatie (Brand Portal-huurder) hebt geselecteerd in het vervolgkeuzemenu (organisatielijst) in de rechterbovenhoek.

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project gemaakt voor uw organisatie.

   Klik **[!UICONTROL Edit project]** om het **[!UICONTROL Project Title]** en **[!UICONTROL Description]** bij te werken, en klik **[!UICONTROL Save]**.

   ![Project maken](assets/service-account1.png)

1. Klik op het tabblad Projectoverzicht op **[!UICONTROL Add API]**.

   ![API toevoegen](assets/service-account2.png)

1. Selecteer in het venster Een API toevoegen de optie **[!UICONTROL AEM Brand Portal]** en klik **[!UICONTROL Next]**.

   Zorg ervoor dat u toegang hebt tot de AEM Brand Portal-service.

1. Klik in het venster API configureren op **[!UICONTROL Upload your public key]**. Klik vervolgens op het openbare certificaat (.crt-bestand) dat u hebt gedownload in de **[!UICONTROL Select a File]** sectie voor het verkrijgen van het openbare certificaat [](#public-certificate) en upload deze.

   Klik op **[!UICONTROL Next]**.

   ![Openbare sleutel uploaden](assets/service-account3.png)

1. Controleer het openbare certificaat en klik op **[!UICONTROL Next]**.

1. Select the default product profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Save configuration]**.

   ![Productprofiel selecteren](assets/service-account4.png)

1. Als de API is geconfigureerd, wordt u omgeleid naar het API-overzicht. Klik in de linkernavigatie onder **[!UICONTROL Credentials]** op **[!UICONTROL Service Account (JWT)]**.

   >[!NOTE]
   >
   >U kunt de geloofsbrieven bekijken en andere acties uitvoeren (produceren de tokens van JWT, kopiëren credentiedetails, terugwinnen cliëntgeheim, etc.) zoals nodig.

1. Kopieer het **[!UICONTROL Client Credentials]** tabblad **[!UICONTROL client ID]**.

   Klik **[!UICONTROL Retrieve Client Secret]** en kopieer het **[!UICONTROL client secret]**.

   ![Servicerekeningen](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]**.

U kunt nu de client-id (API-sleutel), het clientgeheim en de JWT-payload gebruiken om de IMS-account [te](#create-ims-account-configuration) configureren in de AEM Assets-cloud-instantie.

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

### IMS-accountconfiguratie maken {#create-ims-account-configuration}

Controleer of u de volgende stappen hebt uitgevoerd:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)

Voer de volgende stappen uit om de rekening te vormen IMS die u in [verkrijgen openbaar certificaat](#public-certificate)hebt gecreeerd.

1. Open de IMS-configuratie en navigeer naar het **[!UICONTROL Accounts]** tabblad. U hebt de pagina geopend gehouden tijdens het [verkrijgen van een openbaar certificaat](#public-certificate).

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   Voer in **[!UICONTROL Authorization Server]** de volgende URL in: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Plak de client-id in de API-sleutel, het clientgeheim en de JWT-payload die u hebt gekopieerd tijdens het [maken van de JWT-verbinding](#createnewintegration).

   Klik op **[!UICONTROL Create]**.

   De IMS-account is geconfigureerd.

   ![IMS Account configuration](assets/create-new-integration6.png)


1. Selecteer de IMS-configuratie en klik op **[!UICONTROL Check Health]**.

   Klik **[!UICONTROL Check]** in het dialoogvenster. Bij een geslaagde configuratie wordt het bericht weergegeven dat het *token is opgehaald*.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>U kunt slechts één IMS-configuratie hebben. Maak geen meerdere IMS-configuraties.
>
>Zorg ervoor dat de IMS-configuratie slaagt voor de statuscontrole. Als de configuratie niet slaagt voor de statuscontrole, is deze ongeldig. U moet deze dan verwijderen en een nieuwe, geldige configuratie maken.



### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de Brand Portal-cloudservice te maken:

1. Meld u aan bij de auteur-instantie van uw AEM Assets.

1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klik op de pagina Merkorportaalconfiguraties **[!UICONTROL Create]**.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de IMS-configuratie die u hebt gemaakt tijdens het [configureren van de IMS-account](#create-ims-account-configuration).

   In the **[!UICONTROL Service URL]**, enter your Brand Portal tenant (organization) URL.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save and Close]**. De cloudconfiguratie wordt gemaakt. Uw de auteur van AEM Assets instantie wordt nu gevormd met de huurder van het Portaal van het Merk.

### Configuratie testen {#test-integration}

Voer de volgende stappen uit om de configuratie te valideren:

1. Meld u aan bij de cloud-instantie van uw AEM Assets.

1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**.

   ![](assets/test-integration1.png)

1. Klik op de pagina Replicatie **[!UICONTROL Agents on author]**.

   ![](assets/test-integration2.png)

1. Vier replicatieagenten worden gecreeerd voor elke huurder.

   Bepaal de plaats van de replicatieagenten van uw huurder van het Portaal van het Merk.

   Klik op de URL van de replicatieagent.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >De replicatieagenten werken parallel en delen de baandistributie gelijk, daardoor verhogend de het publiceren snelheid met vier keer de originele snelheid. Nadat de wolkendienst wordt gevormd, wordt de extra configuratie niet vereist om de replicatieagenten toe te laten die door gebrek worden geactiveerd om parallelle publicatie van veelvoudige activa toe te laten.


1. Klik op **[!UICONTROL Test Connection]** om de verbinding tussen AEM Assets en Brand Portal te controleren.

   ![](assets/test-integration4.png)

   Onder aan de pagina wordt een bericht weergegeven dat het testpakket is geleverd.

   ![](assets/test-integration5.png)

1. Verifieer de testresultaten op alle vier replicatieagenten één voor één.


   >[!NOTE]
   >
   >Vermijd het onbruikbaar maken van om het even welke replicatieagenten. Hierdoor kan de replicatie van sommige elementen mislukken.

De auteur-instantie van uw AEM Assets is geconfigureerd met Brand Portal. U kunt nu:

* [Assets publiceren van AEM Assets naar Brand Portal](../assets/brand-portal-publish-assets.md)
* [Mappen publiceren van AEM Assets naar Brand Portal](../assets/brand-portal-publish-folder.md)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](../assets/brand-portal-publish-collection.md)
* [Configureer Asset Sourcing](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) , zodat de gebruikers van het Brand Portal elementen kunnen leveren en publiceren naar AEM Assets.

## Upgradeconfiguratie {#upgrade-integration-65}

Voer de volgende stappen in de vermelde opeenvolging uit om bestaande configuraties te bevorderen:
1. [Werken met taken controleren](#verify-jobs)
1. [Bestaande configuraties verwijderen](#delete-existing-configuration)
1. [Configuratie maken](#configure-new-integration-65)

### Werken met taken controleren {#verify-jobs}

Zorg ervoor dat er geen publicatietaak wordt uitgevoerd op de ontwerpinstantie van de AEM Assets voordat u wijzigingen aanbrengt. Voor dat, kunt u alle vier replicatieagenten verifiëren en ervoor zorgen dat de rijen leeg zijn.

1. Meld u aan bij de auteur-instantie van uw AEM Assets.

1. From the **Tools** ![Tools](assets/do-not-localize/tools.png) panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Deployment Replication]**.

1. Klik op de pagina Replicatie **[!UICONTROL Agents on author]**.

   ![](assets/test-integration2.png)

1. Bepaal de plaats van de replicatieagenten van uw huurder van het Portaal van het Merk.

   Zorg ervoor dat de **Rij voor alle replicatieagenten inactief** is, is geen het publiceren baan actief.

   ![](assets/test-integration3.png)

### Bestaande configuraties verwijderen {#delete-existing-configuration}

U moet de volgende controle-lijst in werking stellen terwijl het schrappen van de bestaande configuraties.
* Alle vier replicatieagents verwijderen
* Cloudservice verwijderen
* MAC-gebruiker verwijderen

1. Meld u aan bij de auteur-instantie van uw AEM Assets en open CRX Lite als beheerder. De standaard-URL is

   `http:// localhost:4502/crx/de/index.jsp`

1. Navigeer aan en schrap alle vier replicatieagenten van uw Poorthuurder van het Merk. `/etc/replications/agents.author`

   ![](assets/delete-replication-agent.png)

1. Navigeer naar de configuratie `/etc/cloudservices/mediaportal` van de **** Cloud Service en verwijder deze.

   ![](assets/delete-cloud-service.png)

1. Navigeer aan `/home/users/mac` en schrap de gebruiker **van** MAC van uw Poorthuurder van het Merk.

   ![](assets/delete-mac-user.png)


U kunt nu configuratie [](#configure-new-integration-65) maken via Adobe Developer Console op uw auteur-exemplaar van AEM 6.5.



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->


