---
title: Vorm activa het etiketteren gebruikend de Slimme Dienst van de Inhoud.
description: Leer hoe u slimme tags en verbeterde slimme tags kunt configureren in [!DNL Adobe Experience Manager]de Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 29cf202b2522b4e624960e8b911f77ec7f291e24
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 37%

---


# Asset tagging configureren met behulp van de Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Met Adobe Developer Console kunt u [!DNL Adobe Experience Manager] de service Slimme inhoud integreren. Gebruik deze configuratie om tot de Slimme Dienst van de Inhoud van binnen toegang te hebben [!DNL Experience Manager].

Het artikel detailleert de volgende zeer belangrijke taken uit die worden vereist om de Slimme Dienst van de Inhoud te vormen. At the back end, the [!DNL Experience Manager] server authenticates your service credentials with the Adobe Developer Console gateway before forwarding your request to the Smart Content Service.

1. Create a Smart Content Service configuration in [!DNL Experience Manager] to generate a public key. [Verkrijg een openbaar certificaat voor OAuth-integratie.](#obtain-public-certificate)
1. [Maak een integratie in Adobe Developer Console en upload de gegenereerde openbare sleutel.](#create-adobe-i-o-integration)
1. [Configureer uw implementatie](#configure-smart-content-service) met behulp van de API-sleutel en andere gegevens uit de Adobe Developer Console.
1. [Test de configuratie](#validate-the-configuration).
1. Optionally, [enable auto-tagging on asset upload](#enable-smart-tagging-in-the-update-asset-workflow-optional).

## Vereisten {#prerequisites}

Voordat u de Smart Content Service kunt gebruiken, moet u het volgende doen om een integratie te maken in de Adobe Developer Console:

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* De service Smart Content Service is ingeschakeld voor uw organisatie.

Om Verbeterde Slimme Markeringen toe te laten, naast bovenstaand, installeer ook het recentste de dienstpak [van](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)AEM.

## Openbaar certificaat verkrijgen {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. In the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.
1. Geef in het **[!UICONTROL Create Configuration]** dialoogvenster een titel en naam op voor de configuratie Slimme tags. Klik op **[!UICONTROL Create]**.
1. Gebruik de volgende waarden in het **[!UICONTROL AEM Smart Content Service]** dialoogvenster:

   **[!UICONTROL Service URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**: `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Klik op **[!UICONTROL OK]**.

   ![Het dialoogvenster Experience Manager Smart Content Service om de URL van de inhoudsservice te bieden](assets/aem_scs.png)

   >[!NOTE]
   >
   >De URL die wordt opgegeven als [!UICONTROL Service URL] is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt OK met dezelfde waarde als de [!UICONTROL Service URL] parameter. Voor het algemene de dienststatus en onderhoudsplan, zie [https://status.adobe.com](https://status.adobe.com).

1. Klik **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt`.

   ![Een voorstelling van de instellingen die voor de service voor slimme tags zijn gemaakt](assets/smart-tags-download-public-cert.png)

### Reconfigure when a certificate expires {#certrenew}

Nadat een certificaat is verlopen, wordt het niet meer vertrouwd. U kunt een verlopen certificaat niet verlengen. Voer de onderstaande stappen uit om een nieuw certificaat toe te voegen.

1. Meld u als beheerder aan bij uw [!DNL Experience Manager]-implementatie. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]**-gebruiker. Klik op het tabblad **[!UICONTROL Keystore]**.
1. Verwijder het bestaande **[!UICONTROL similaritysearch]**-sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Verwijder het bestaande zoekitem voor gelijkenis in Keystore om een nieuw beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)

   *Afbeelding: Verwijder de bestaande`similaritysearch`-vermelding in het sleutelarchief om een nieuw beveiligingscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.
1. Ga naar [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande Smart Content Services op de **[!UICONTROL Integrations]** pagina. Upload het nieuwe certificaat. For more information, see the instructions in [Create Adobe Developer Console integration](#create-adobe-i-o-integration).

## Adobe Developer Console-integratie maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om API-sleutel, technische account-id, organisatie-id en clientgeheim te genereren.

1. Open [https://console.adobe.io](https://console.adobe.io/) in uw browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.
1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.
1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er wordt een [!UICONTROL Public key(s) uploaded successfully]-bericht weergegeven. Klik op **[!UICONTROL Next]**.
1. De pagina [!UICONTROL Create a new Service Account (JWT) credential] toont de openbare sleutel voor het serviceaccount dat u zojuist hebt geconfigureerd. Klik op **[!UICONTROL Next]**.
1. Ga naar de pagina **[!UICONTROL Select product profiles]** en selecteer **[!UICONTROL Smart Content Services]**. Klik op **[!UICONTROL Save configured API]**. De pagina die verschijnt biedt meer informatie over de configuratie. Houd deze pagina open om de waarden te kopiëren en toe te voegen in Experience Manager voor de verdere configuratie van Smart Tags in [!DNL Experience Manager].

   ![Op het tabblad Overview kunt u de informatie bekijken die is opgegeven voor de integratie.](assets/integration_details.png)

## Smart Content Service configureren {#configure-smart-content-service}

Als u de integratie wilt configureren, gebruikt u de waarden Technical Account ID, Organization ID, Client Secret, Authorization Server en API-sleutelvelden van de integratie met de Adobe Developer Console. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] implementatie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager], naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** om de [!UICONTROL Cloud Services] console te openen.
1. Open onder de **[!UICONTROL Assets Smart Tags]** sectie de configuratie die hierboven is gemaakt. Klik op de pagina met service-instellingen **[!UICONTROL Edit]**.
1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.
1. Voor de velden **[!UICONTROL API Key]**, **[!UICONTROL Technical Account Id]**, **[!UICONTROL Organization Id]** en **[!UICONTROL Client Secret]** gebruikt u de hierboven gegenereerde waarden.

## De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open uw [!DNL Experience Manager] server op `https://[aem_server]:[port]`.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]**.
1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Het wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.
1. Klik op `validateConfigs()`. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**. De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

## Slimme tags toepassen inschakelen in de [!UICONTROL DAM Update Asset] workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.
1. Klik op **[!UICONTROL Edit]** op de werkbalk.
1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Afbeelding: Voeg de stap Slimme tag-elementen toe na de stap met de procesminiaturen in de[!UICONTROL DAM Update Asset]workflow.*

1. Open de stap in de bewerkingsmodus. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen](assets/smart-tag-step-properties-workflow1.png)

1. In the **[!UICONTROL Arguments]** tab, select **[!UICONTROL Ignore Errors]** if you want the workflow to complete even if the automatic tagging step fails.

   Als u assets tijdens het uploaden wilt voorzien van een tag (ongeacht of slimme tags zijn ingeschakeld voor mappen), moet u de optie **[!UICONTROL Ignore Smart Tag Flag]** inschakelen.

   ![Workflow van DAM Update Asset configureren om stap Smart Tag toe te voegen en markering Smart Tag negeren te selecteren](assets/smart-tag-step-properties-workflow2.png)

1. Klik op **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op.

>[!MORELIKETHIS]
>
>* [Slimme tags beheren](managing-smart-tags.md)
>* [Overzicht van slimme tags en hoe deze kunnen worden getraind](enhanced-smart-tags.md)
>* [Richtlijnen en regels voor de opleiding van de Smart Content Service](smart-tags-training-guidelines.md)
>* [Videozelfstudie over het configureren van slimme tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)

