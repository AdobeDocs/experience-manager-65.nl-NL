---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe te om slimme het etiketteren en verbeterde slimme het etiketteren in  [!DNL Adobe Experience Manager] te vormen, gebruikend de Slimme Dienst van de Inhoud.
role: Admin
feature: Tagging,Smart Tags
solution: Experience Manager, Experience Manager Assets
exl-id: 9caee314-697b-4a7b-b991-10352da17f2c
source-git-commit: ab9292c491cc9dfcd8f239ba279b1e0ae6d1560f
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 5%

---

# Problemen met slimme tags voor OAuth-gebruikersgegevens oplossen {#oauth-config}

Een open vergunningsconfiguratie wordt vereist om de toestemming aan de [!DNL Adobe Experience Manager] toepassing goed te keuren om met de Slimme Diensten van de Inhoud op een beveiligde manier in wisselwerking te staan.

>[!NOTE]
>
> U kunt vanaf juni 2024 geen nieuwe JWT-referenties maken. Voortaan worden alleen OAuth Server-to-Server-referenties gemaakt.
> De JWT-integratie gaat door tot januari 2025, alleen voor de bestaande AMS en on-premise gebruikers.

## OAuth-configuratie voor de nieuwe AMS-gebruikers {#oauth-config-existing-ams-users}

Verwijs naar [ configuratie van de slimme inhoudsdiensten ](#integrate-adobe-io) voor de configuratie van de diensten OAuth voor een nieuwe gebruiker. Zodra gedaan, volg deze [ stappen ](#prereqs-config-oauth-onprem).

>[!NOTE]
>
>Indien vereist, kunt u een steunkaartje na het [ steunproces ](https://experienceleague.adobe.com/?lang=en&amp;support-tab=home#support) voorleggen.

## OAuth-configuratie voor de bestaande AMS-gebruikers {#oauth-config-new-ams-users}

Voordat u een van de stappen in deze methode uitvoert, moet u het volgende implementeren:

### Vereisten {#prereqs-config-oauth-onprem}

Een configuratie OAuth vereist de volgende eerste vereisten:

* Creeer een nieuwe integratie OAuth in [ Developer Console ](https://developer.adobe.com/console/user/servicesandapis). Gebruik de eigenschappen `ClientID` , `ClientSecret` , `OrgID` en andere eigenschappen in de onderstaande stappen:
* De volgende bestanden zijn te vinden op dit pad `/apps/system/config in crx/de` :
   * `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`
   * `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`

### OAuth-configuratie voor de bestaande AMS- en On prem-gebruikers {#steps-config-oauth-onprem}

De hieronder stappen kunnen door systeemadmin in **CRXDE** worden uitgevoerd. De klant van AMS kan uit aan de vertegenwoordiger van de Adobe bereiken of een steunkaartje na het [ steunproces voorleggen ](https://experienceleague.adobe.com/?lang=en&amp;support-tab=home#support).

1. Voeg de onderstaande eigenschappen toe of werk deze bij in `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config` :

   * `auth.token.provider.authorization.grants="client_credentials"`
   * `auth.token.provider.orgId="<OrgID>"`
   * `auth.token.provider.default.claims=("\"iss\"\ :\ \"<OrgID>\"")`
   * `auth.token.provider.scope="read_pc.dma_smart_content,\ openid,\ AdobeID,\ additional_info.projectedProductContext"`
     `auth.token.validator.type="adobe-ims-similaritysearch"`
   * Werk `auth.token.provider.client.id` met Cliënt identiteitskaart van de nieuwe configuratie OAuth bij.
   * `auth.access.token.request` bijwerken naar `"https://ims-na1.adobelogin.com/ims/token/v3"`
1. Wijzig de naam van het bestand in `com.adobe.granite.auth.oauth.accesstoken.provider-<randomnumber>.config` .

   >[!IMPORTANT]
   >
   >Vervang punt (.) door afbreekstreepje (-) als voorvoegsel naar `<randomnumber>` .

1. Voer de onderstaande stappen uit in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config` :
   * Werk het bezit auth.ims.client.geheime met het Geheim van de Cliënt van de nieuwe integratie OAuth bij.
   * Naam van bestand wijzigen in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl-<randomnumber>.config`
1. Sla alle wijzigingen op in de ontwikkelingsconsole van de inhoudsopslagplaats, bijvoorbeeld CRXDE.
<!--
1. Navigate to `/system/console/configMgr` and replace the OSGi configuration from `.<randomnumber>` to `-<randomnumber>`.
1. Delete the old OSGi configuration for `"Access Token provider name: adobe-ims-similaritysearch"` in `/system/console/configMgr`.
-->
1. In `System/console/configMgr` kunt u zowel oudere als nieuwe configuratiebestanden zien. Verwijder de oudere configuraties voor de naam `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl` en de provider van toegangstoken `adobe-ims-similaritysearch` . Zorg ervoor dat de bijgewerkte configuratie slechts op zijn plaats is, eerder dan de oudere configuraties.
1. Start de console opnieuw.

## De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open de [!DNL Experience Manager] -server op `https://[aem_server]:[port]` .

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]** .

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Deze wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]** .

1. Klik op `validateConfigs()`. Klik in het dialoogvenster **[!UICONTROL Validate Configurations]** op **[!UICONTROL Invoke]** .

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

>[!NOTE]
>
>Als de fout `unsupported_grant_type` optreedt, installeert u de hotfix voor graniet. Verwijs naar [ migratie van de Rekening van de Dienst (JWT) naar de geloofsbrieven van Server-aan-Server van OAuth ](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24660).

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Als nieuwe gebruiker, wanneer u met Adobe Developer Console integreert, verifieert de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van Adobe Developer Console alvorens uw verzoek aan de Slimme Dienst van de Inhoud door:sturen. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en een licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

<!--![Experience Manager Smart Content Service dialog to provide content service URL](assets/config-oauth.png)-->

1. Om een openbare sleutel te produceren, [ creeer een Slimme 1} configuratie van de Dienst van de Inhoud {in [!DNL Experience Manager]. ](#oauth-config) [ Download een openbaar certificaat ](#oauth-config) voor integratie OAuth.

1. *[niet toepasselijk als u een bestaande gebruiker]* [ bent creeer een integratie in Adobe Developer Console ](#create-adobe-i-o-integration).

1. [ vorm uw plaatsing ](#configure-smart-content-service) gebruikend de API sleutel en andere geloofsbrieven van Adobe Developer Console.

1. [Test de configuratie](#validate-the-configuration).

## Download een openbaar certificaat door de Configuratie van de Dienst van de Slimme Inhoud te creëren {#download-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op de Adobe Developer Console.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. Klik op de pagina Cloud Servicen op **[!UICONTROL Configure Now]** onder **[!UICONTROL Assets Smart Tags]** .

1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een titel en naam op voor de configuratie van slimme tags. Klik op **[!UICONTROL Create]**.

1. Gebruik de volgende waarden in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** :

   **[!UICONTROL Service URL]**: `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`

   Bijvoorbeeld `https://smartcontent.adobe.io/apac` . U kunt `na` , `emea` of `apac` opgeven als de gebieden waar de auteur van de Experience Manager wordt gehost.

   >[!NOTE]
   >
   >Als de Experience Manager Beheerde Dienst vóór September 01, 2022 provisioned is, gebruik de volgende Dienst URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**: `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Klik op **[!UICONTROL OK]**.

   ![ Experience Manager de Slimme dialoog van de Dienst van de Inhoud om de inhoudsdienst URL ](assets/aem_scs12.png) te verstrekken

   *Cijfer: De slimme dialoog van de Dienst van de Inhoud om de inhoudsdienst URL* te verstrekken

   >[!NOTE]
   >
   >De URL die als [!UICONTROL Service URL] wordt opgegeven, is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt OK met dezelfde waarde als de parameter [!UICONTROL Service URL] . Voor het algemene de dienststatus en onderhoudsprogramma, zie [ https://status.adobe.com ](https://status.adobe.com).

1. Klik op **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt` . Bovendien hoeft u dit certificaat niet meer te uploaden naar de Adobe Developer-console.

   ![ een vertegenwoordiging van de montages die voor de slimme het etiketteren dienst ](assets/smart-tags-download-public-cert1.png) worden gecreeerd

   *Cijfer: Montages voor de slimme het etiketteren dienst.*

## Adobe Developer Console-integratie maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID] field of Adobe Developer Console integration), [!UICONTROL TECHNICAL ACCOUNT ID] , [!UICONTROL ORGANIZATION ID] en [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] of cloud configuration in [!DNL Experience Manager] te verkrijgen.

1. Toegang [ https://developer.adobe.com/console/ ](https://developer.adobe.com/console/) in browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Kies de verificatiemethode **[!UICONTROL OAuth Server-to-Server]** .

1. Voeg de **[!UICONTROL Credential Name]** desgewenst toe of wijzig deze. Klik op **[!UICONTROL Next]**.

1. Selecteer het productprofiel **[!UICONTROL Smart Content Services]** . Klik op **[!UICONTROL Save Configured API]**. De OAuth API wordt toegevoegd aan de verbonden geloofsbrieven voor verder gebruik. U kunt de [!UICONTROL API key (Client ID)] of [!UICONTROL Generate access token] ervan kopiëren.
<!--
1. On the **[!UICONTROL Select product profiles]** page, select **[!UICONTROL Smart Content Services]**. Click **[!UICONTROL Save configured API]**.

   A page displays more information about the configuration. Keep this page open to copy and add these values in [!UICONTROL Assets Smart Tagging Service Settings] of cloud configuration in [!DNL Experience Manager] to configure smart tags.

   ![In the Overview tab, you can review the information provided for integration.](assets/integration_details.png)


   *Figure: Details of integration in Adobe Developer Console*
-->

![ oauth config ](assets/oauth-config.png)
*Cijfer: Gevormde OAuth Server-aan-Server in Adobe Developer Console*

## Slimme-inhoudsservice configureren {#configure-smart-content-service}

Als u de integratie wilt configureren, gebruikt u de waarden van de velden [!UICONTROL TECHNICAL ACCOUNT ID] , [!UICONTROL ORGANIZATION ID] , [!UICONTROL CLIENT SECRET] en [!UICONTROL CLIENT ID] van de Adobe Developer Console-integratie. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] -implementatie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** om de [!UICONTROL Cloud Services] -console te openen.

1. Open onder **[!UICONTROL Assets Smart Tags]** de configuratie die hierboven is gemaakt. Klik op **[!UICONTROL Edit]** op de pagina met service-instellingen.

1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.

1. Voor de gebieden [!UICONTROL Api Key], [!UICONTROL Technical Account ID], [!UICONTROL Organization ID], en [!UICONTROL Client Secret], kopieer en gebruik de volgende waarden die in [ worden geproduceerd de integratie van Adobe Developer Console ](#create-adobe-i-o-integration).

   | [!UICONTROL Assets Smart Tagging Service Settings] | [!DNL Adobe Developer Console] integratievelden |
   |--- |--- |
   | [!UICONTROL Api Key] | [!UICONTROL CLIENT ID] |
   | [!UICONTROL Technical Account ID] | [!UICONTROL TECHNICAL ACCOUNT ID] |
   | [!UICONTROL Organization ID] | [!UICONTROL ORGANIZATION ID] |
   | [!UICONTROL Client Secret] | [!UICONTROL CLIENT SECRET] |

>[!MORELIKETHIS]
>
>* [ Overzicht en hoe te om Slimme Markeringen ](enhanced-smart-tags.md) te trainen
>* [ vorm slimme het etiketteren ](config-smart-tagging.md)
>* [ Videozelfstudie over slimme markeringen ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html)
