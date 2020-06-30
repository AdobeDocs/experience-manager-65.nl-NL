---
title: Vorm activa het etiketteren gebruikend de Slimme Dienst van de Inhoud.
description: Leer hoe u slimme tags en verbeterde slimme tags kunt configureren in [!DNL Adobe Experience Manager] met gebruik van de Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: dfac819018e85e0e8221bfcc57bc1eaf43b7ff25
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 8%

---


# Asset tagging configureren met behulp van de Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

Met Adobe Developer Console kunt u [!DNL Adobe Experience Manager] de service Slimme inhoud integreren. Gebruik deze configuratie om tot de Slimme Dienst van de Inhoud van binnen toegang te hebben [!DNL Experience Manager].

Het artikel detailleert de volgende zeer belangrijke taken uit die worden vereist om de Slimme Dienst van de Inhoud te vormen. Aan de achterkant verifieert de [!DNL Experience Manager] server uw servicegegevens met de Adobe Developer Console-gateway voordat uw verzoek naar de Smart Content Service wordt doorgestuurd.

1. Creeer een Slimme configuratie van de Dienst van de Inhoud binnen [!DNL Experience Manager] om een openbare sleutel te produceren. [Overheidscertificaat](#obtain-public-certificate) verkrijgen voor OAuth-integratie.
1. [Maak een integratie in Adobe Developer Console](#create-adobe-i-o-integration) en upload de gegenereerde openbare sleutel.
1. [Configureer uw implementatie](#configure-smart-content-service) met behulp van de API-sleutel en andere gegevens uit de Adobe Developer Console.
1. [Test de configuratie](#validate-the-configuration).
1. Schakel eventueel automatische labeling [in bij het uploaden](#enable-smart-tagging-in-the-update-asset-workflow-optional)van elementen.

## Vereisten {#prerequisites}

Voordat u de Smart Content Service kunt gebruiken, moet u het volgende doen om een integratie te maken in de Adobe Developer Console:

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* De service Smart Content Service is ingeschakeld voor uw organisatie.

Om Verbeterde Slimme Markeringen toe te laten, naast bovenstaand, installeer ook het recentste de dienstpak [van](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)AEM.

## Openbaar certificaat verkrijgen {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

1. Ga in de [!DNL Experience Manager] gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

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

### Opnieuw configureren wanneer een certificaat verloopt {#certrenew}

Nadat een certificaat is verlopen, wordt het niet meer vertrouwd. U kunt een verlopen certificaat niet vernieuwen. Voer de volgende stappen uit om een nieuw certificaat toe te voegen.

1. Log in your [!DNL Experience Manager] deployment as an administrator. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]** Gebruiker. Klik op **[!UICONTROL Keystore]** tabblad.
1. Verwijder het bestaande **[!UICONTROL similaritysearch]** sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Verwijder het bestaande zoekitem voor gelijkenis in Keystore om een nieuw beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)

   *Afbeelding: Verwijder het bestaande`similaritysearch`item in het sleutelarchief om een nieuw beveiligingscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.
1. Ga naar [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande Smart Content Services op de **[!UICONTROL Integrations]** pagina. Upload het nieuwe certificaat. Zie de instructies in de integratie [van Adobe Developer Console](#create-adobe-i-o-integration)maken voor meer informatie.

## Adobe Developer Console-integratie maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om API-sleutel, technische account-id, organisatie-id en clientgeheim te genereren.

1. Ga naar [https://console.adobe.io](https://console.adobe.io/) in een browser. Selecteer de aangewezen rekening en verifieer dat de bijbehorende organisatierol systeembeheerder is.
1. Maak een project met de gewenste naam. Klik op **[!UICONTROL Add API]**.
1. Selecteer op de **[!UICONTROL Add an API]** pagina **[!UICONTROL Experience Cloud]** en selecteer **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er [!UICONTROL Public key(s) uploaded successfully] wordt een bericht weergegeven. Klik op **[!UICONTROL Next]**.
1. [!UICONTROL Create a new Service Account (JWT) credential] De pagina toont de openbare sleutel voor de de dienstrekening enkel gevormd. Klik op **[!UICONTROL Next]**.
1. Selecteer op de **[!UICONTROL Select product profiles]** pagina **[!UICONTROL Smart Content Services]**. Klik **[!UICONTROL Save configured API]**. Op een pagina wordt meer informatie over de configuratie weergegeven. Laat deze pagina open om deze waarden in Experience Manager te kopiëren en toe te voegen wanneer u Slimme tags verder configureert in [!DNL Experience Manager].

   ![Op het tabblad Overzicht kunt u de informatie bekijken die voor integratie is opgegeven.](assets/integration_details.png)

## Smart Content Service configureren {#configure-smart-content-service}

Als u de integratie wilt configureren, gebruikt u de waarden Technical Account ID, Organization ID, Client Secret, Authorization Server en API-sleutelvelden van de integratie met de Adobe Developer Console. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] implementatie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager]naar **[!UICONTROL Tools > Cloud Service > Legacy Cloud Services]** om de [!UICONTROL Cloud Services] console te openen.
1. Open onder de **[!UICONTROL Assets Smart Tags]** sectie de configuratie die hierboven is gemaakt. Klik op de pagina met service-instellingen **[!UICONTROL Edit]**.
1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.
1. Voor de velden **[!UICONTROL API Key]**, **[!UICONTROL Technical Account Id]**, **[!UICONTROL Organization Id]** en **[!UICONTROL Client Secret]** gebruikt u de hierboven gegenereerde waarden.

## De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open uw [!DNL Experience Manager] server op `https://[aem_server]:[port]`.
1. Ga naar **[!UICONTROL Tools > Operations > Web Console]** om de console te openen OSGi. Klik op **[!UICONTROL Main > JMX]**.
1. Klik op **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Het wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.
1. Klik op **[!UICONTROL validateConfigs()]**. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

   Het validatieresultaat wordt in hetzelfde dialoogvenster weergegeven.

## Slimme tags toepassen inschakelen in de DAM Update Asset-workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga [!DNL Experience Manager]naar **[!UICONTROL Tools > Workflow > Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.
1. Klik op **[!UICONTROL Edit]** de werkbalk.
1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Slim tagelement toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Afbeelding: Voeg de stap Slimme tag-elementen toe na de stap met de procesminiaturen in de[!UICONTROL DAM Update Asset]workflow.*

1. Open de stap in de bewerkingsmodus. Zorg er onder **[!UICONTROL Advanced Settings]** dat de **[!UICONTROL Handler Advance]** optie is geselecteerd.

   ![Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen](assets/smart-tag-step-properties-workflow1.png)

1. In the **[!UICONTROL Arguments]** tab, select **[!UICONTROL Ignore Errors]** if you want the workflow to complete even if the automatic tagging step fails.

   ![De DAM Update Asset-workflow configureren om een stap voor slimme tags toe te voegen en de voortgang van de handler te selecteren](assets/smart-tag-step-properties-workflow2.png)

   Als u elementen wilt labelen wanneer ze worden geüpload, ongeacht of slimme tags zijn ingeschakeld in mappen, selecteert u **[!UICONTROL Ignore Smart Tag Flag]**.

   ![Workflow van DAM Update Asset configureren om stap Smart Tag toe te voegen en markering Smart Tag negeren te selecteren](assets/smart-tag-step-properties-workflow3.png)

1. Klik **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op.

>[!MORELIKETHIS]
>
>* [Slimme tags beheren](managing-smart-tags.md)
>* [Overzicht van slimme tags en hoe deze kunnen worden getraind](enhanced-smart-tags.md)
>* [Richtlijnen en regels voor de opleiding van de Smart Content Service](smart-tags-training-guidelines.md)
>* [Videozelfstudie over het configureren van slimme tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)

