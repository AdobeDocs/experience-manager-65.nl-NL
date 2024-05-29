---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe u slimme tags en verbeterde slimme tags kunt configureren in [!DNL Adobe Experience Manager], met de Smart Content Service.
role: Admin
feature: Tagging,Smart Tags
solution: Experience Manager, Experience Manager Assets
source-git-commit: 109a608db0724050f6e505394da9138855ba992e
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 6%

---

# Problemen met slimme tags voor OAuth-gebruikersgegevens oplossen {#oauth-config}

Een open vergunningsconfiguratie wordt vereist om de toestemming aan te nemen [!DNL Adobe Experience Manager] toepassing om op een beveiligde manier te communiceren met Smart Content Services.

>[!NOTE]
>
> U kunt vanaf juni 2024 geen nieuwe JWT-referenties maken. Voortaan worden alleen OAuth Server-to-Server-referenties gemaakt.
> De JWT-integratie gaat door tot januari 2025, alleen voor de bestaande AMS en on-premise gebruikers.

## OAuth-configuratie voor de nieuwe AMS-gebruikers {#oauth-config-existing-ams-users}

Zie [configuratie van services voor slimme inhoud](#integrate-adobe-io) voor de configuratie van de diensten OAuth voor een nieuwe gebruiker. Volg deze [stappen](#prereqs-config-oauth-onprem).

>[!NOTE]
>
>Indien nodig kunt u een ondersteuningsticket verzenden na de [supportproces](https://experienceleague.adobe.com/?lang=en&amp;support-tab=home#support).

## OAuth-configuratie voor de bestaande AMS-gebruikers {#oauth-config-new-ams-users}

Voordat u een van de stappen in deze methode uitvoert, moet u het volgende implementeren:

### Vereisten {#prereqs-config-oauth-onprem}

Een configuratie OAuth vereist de volgende eerste vereisten:

* Maak een nieuwe OAuth-integratie in het dialoogvenster [Ontwerpconsole](https://developer.adobe.com/console/user/servicesandapis). Gebruik de `ClientID`, `ClientSecret`, `OrgID`en andere eigenschappen in de onderstaande stappen:
* De volgende bestanden zijn te vinden op dit pad `/apps/system/config in crx/de`:
   * `com.**adobe**.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`
   * `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`

### OAuth voor gebruikers op locatie configureren {#steps-config-oauth-onprem}

1. Hieronder vindt u eigenschappen toevoegen of bijwerken in `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`:

   * `auth.token.provider.authorization.grants="client_credentials"`
   * `auth.token.provider.orgId="<OrgID>"`
   * `auth.token.provider.default.claims=("\"iss\"\ :\ \"<OrgID>\"")`
   * `auth.token.provider.scope="read_pc.dma_smart_content,\ openid,\ AdobeID,\ additional_info.projectedProductContext"`
     `auth.token.validator.type="adobe-ims-similaritysearch"`
   * Werk de `auth.token.provider.client.id` met identiteitskaart van de Cliënt van de nieuwe configuratie OAuth.
   * Bijwerken `auth.access.token.request` tot `"https://ims-na1.adobelogin.com/ims/token/v3"`
2. De naam van het bestand wijzigen in `com.adobe.granite.auth.oauth.accesstoken.provider-<randomnumber>.config`.
3. Voer de onderstaande stappen uit in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`:
   * Werk het bezit auth.ims.client.geheime met het Geheim van de Cliënt van de nieuwe integratie OAuth bij.
   * De naam van het bestand wijzigen in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl-<randomnumber>.config`
4. Sla alle wijzigingen op in de ontwikkelingsconsole van de inhoudsopslagplaats, bijvoorbeeld CRXDE.
5. Navigeren naar `/system/console/configMgr` en vervang de OSGi-configuratie vanuit `.<randomnumber>` tot `-<randomnumber>`.
6. Verwijder de oude OSGi-configuratie voor `"Access Token provider name: adobe-ims-similaritysearch"` in `/system/console/configMgr`.
7. Start de console opnieuw.

## De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Toegang tot uw [!DNL Experience Manager] server op `https://[aem_server]:[port]`.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klikken **[!UICONTROL Main]>[!UICONTROL JMX]**.

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Klik op `validateConfigs()`. In de **[!UICONTROL Validate Configurations]** dialoogvenster, klikt u op **[!UICONTROL Invoke]**.

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Als nieuwe gebruiker, wanneer u met de Console van Adobe Developer integreert, [!DNL Experience Manager] -server verifieert uw servicegegevens met de Adobe Developer Console-gateway voordat uw aanvraag naar de Smart Content Service wordt doorgestuurd. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en een licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. Een openbare sleutel genereren [Creëer de Slimme Dienst van de Inhoud](#obtain-public-certificate) configuratie in [!DNL Experience Manager]. [Een openbaar certificaat downloaden](#obtain-public-certificate) voor OAuth-integratie.

1. *[Niet van toepassing als u een bestaande gebruiker bent]* [Een integratie maken in Adobe Developer Console](#create-adobe-i-o-integration).

1. [Uw implementatie configureren](#configure-smart-content-service) met de API-sleutel en andere gegevens uit Adobe Developer Console.

1. [Test de configuratie](#validate-the-configuration).

## Download een openbaar certificaat door de Configuratie van de Dienst van de Slimme Inhoud te creëren {#download-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op de Adobe Developer-console.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. Klik op de pagina Cloud Servicen op **[!UICONTROL Configure Now]** krachtens **[!UICONTROL Assets Smart Tags]**.

1. In de **[!UICONTROL Create Configuration]** geeft u een titel en naam op voor de configuratie Slimme tags. Klik op **[!UICONTROL Create]**.

1. In de **[!UICONTROL AEM Smart Content Service]** gebruikt u de volgende waarden:

   **[!UICONTROL Service URL]**: `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`

   Bijvoorbeeld: `https://smartcontent.adobe.io/apac`. U kunt `na`, `emea`, of `apac` als de gebieden waar uw Experience Manager auteur-instantie wordt gehost.

   >[!NOTE]
   >
   >Als de Experience Manager Beheerde Dienst vóór September 01, 2022 provisioned is, gebruik de volgende Dienst URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**: `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Klik op **[!UICONTROL OK]**.

   ![Het dialoogvenster Experience Manager Smart Content Service om de contentservice-URL op te geven](assets/aem_scs12.png)

   *Afbeelding: Het dialoogvenster Slimme inhoudsservice om de URL van de inhoudsservice op te geven*

   >[!NOTE]
   >
   >De opgegeven URL [!UICONTROL Service URL] is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt OK met dezelfde waarde als de [!UICONTROL Service URL] parameter. Voor het algemene de dienststatus en onderhoudsplan, zie [https://status.adobe.com](https://status.adobe.com).

1. Klikken **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt`. Bovendien hoeft u dit certificaat niet meer te uploaden naar de Adobe Developer Console.

   ![Een voorstelling van de instellingen die voor de service voor slimme tags zijn gemaakt](assets/smart-tags-download-public-cert1.png)

   *Afbeelding: Instellingen voor service voor slimme tags.*

## Integratie met Adobe Developer Console maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID] gebied van de integratie van Adobe Developer Console), [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], en [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] van cloudconfiguratie in [!DNL Experience Manager].

1. Toegang [https://developer.adobe.com/console/](https://developer.adobe.com/console/) in een browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Kies de optie **[!UICONTROL OAuth Server-to-Server]** verificatiemethode.

1. Voeg/wijzig toe **[!UICONTROL Credential Name]** zoals vereist. Klik op **[!UICONTROL Next]**.

1. Selecteer het productprofiel **[!UICONTROL Smart Content Services]**. Klik op **[!UICONTROL Save Configured API]**. De OAuth API wordt toegevoegd onder de aangesloten geloofsbrieven voor verder gebruik. U kunt de [!UICONTROL API key (Client ID)] of [!UICONTROL Generate access token] van het.
<!--
1. On the **[!UICONTROL Select product profiles]** page, select **[!UICONTROL Smart Content Services]**. Click **[!UICONTROL Save configured API]**.

   A page displays more information about the configuration. Keep this page open to copy and add these values in [!UICONTROL Assets Smart Tagging Service Settings] of cloud configuration in [!DNL Experience Manager] to configure smart tags.

   ![In the Overview tab, you can review the information provided for integration.](assets/integration_details.png)


   *Figure: Details of integration in Adobe Developer Console*
-->

![oauth config](assets/oauth-config.png)
*Afbeelding: OAuth Server-to-Server geconfigureerd in Adobe Developer Console*

## Slimme-inhoudsservice configureren {#configure-smart-content-service}

Om de integratie te vormen, gebruik de waarden van [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], [!UICONTROL CLIENT SECRET], en [!UICONTROL CLIENT ID] velden van de integratie met Adobe Developer Console. Het creëren van een Slimme wolkenconfiguratie van Markeringen staat authentificatie van API verzoeken van toe [!DNL Experience Manager] implementatie.

1. In [!DNL Experience Manager], navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** om de [!UICONTROL Cloud Services] console.

1. Onder de **[!UICONTROL Assets Smart Tags]**, opent u de hierboven gemaakte configuratie. Klik op de pagina met service-instellingen op **[!UICONTROL Edit]**.

1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.

1. Voor de velden [!UICONTROL Api Key], [!UICONTROL Technical Account ID], [!UICONTROL Organization ID], en [!UICONTROL Client Secret]kopieert en gebruikt u de volgende waarden die zijn gegenereerd in [Integratie met Adobe Developer Console](#create-adobe-i-o-integration).

   | [!UICONTROL Assets Smart Tagging Service Settings] | [!DNL Adobe Developer Console] integratievelden |
   |--- |--- |
   | [!UICONTROL Api Key] | [!UICONTROL CLIENT ID] |
   | [!UICONTROL Technical Account ID] | [!UICONTROL TECHNICAL ACCOUNT ID] |
   | [!UICONTROL Organization ID] | [!UICONTROL ORGANIZATION ID] |
   | [!UICONTROL Client Secret] | [!UICONTROL CLIENT SECRET] |

>[!MORELIKETHIS]
>
>* [Overzicht en hoe u slimme tags kunt trainen](enhanced-smart-tags.md)
>* [Slimme tags configureren](config-smart-tagging.md)
>* [Videozelfstudie over slimme tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html)
