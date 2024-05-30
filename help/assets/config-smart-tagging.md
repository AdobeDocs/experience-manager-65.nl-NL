---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe u slimme tags en verbeterde slimme tags kunt configureren in [!DNL Adobe Experience Manager], met de Smart Content Service.
contentOwner: AG
role: Admin
feature: Tagging,Smart Tags
exl-id: 9f68804f-ba15-4f83-ab1b-c249424b1396
solution: Experience Manager, Experience Manager Assets
source-git-commit: 17a8dc53d77dfbc3dc3a4dc2f2176eaba3e1cb7c
workflow-type: tm+mt
source-wordcount: '2152'
ht-degree: 16%

---

# Voorbereiden [!DNL Assets] voor slimme tags {#configure-asset-tagging-using-the-smart-content-service}

Voordat u met het labelen van uw elementen kunt beginnen met gebruik van Smart Content Services, moet u eerst [!DNL Experience Manager Assets] met Adobe Developer Console voor gebruik van intelligente service van [!DNL Adobe Sensei]. Zodra gevormd treig de dienst gebruikend een paar beelden en een markering.

>[!NOTE]
>
>* Smart Content Services is niet meer beschikbaar voor nieuwe [!DNL Experience Manager Assets] Klanten op locatie. Bestaande klanten op locatie, die deze mogelijkheid al hebben ingeschakeld, kunnen Smart Content Services blijven gebruiken.
>* Smart Content Services is beschikbaar voor bestaande [!DNL Experience Manager Assets] Managed Services-klanten die deze mogelijkheid al hebben ingeschakeld.
>* Nieuw [!DNL Experience Manager Assets] Managed Services-klanten kunnen de instructies in dit artikel volgen om Smart Content Services in te stellen.

Controleer het volgende voordat u de Smart Content Service gebruikt:

* [Integreren met Adobe Developer Console](#integrate-adobe-io).
* [De Smart Content Service trainen](#training-the-smart-content-service).

* De nieuwste [[!DNL Experience Manager] Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html).

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Wanneer u met Adobe Developer Console integreert, [!DNL Experience Manager] -server verifieert uw servicegegevens met de Adobe Developer Console-gateway voordat uw aanvraag naar de Smart Content Service wordt doorgestuurd. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en de licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. Een openbare sleutel genereren [Een Smart Content Service maken](#obtain-public-certificate) configuratie in [!DNL Experience Manager]. [Verkrijg een openbaar certificaat voor OAuth-integratie.](#obtain-public-certificate)

1. [Maak een integratie in Adobe Developer Console en upload de gegenereerde openbare sleutel.](#create-adobe-i-o-integration)

1. [Uw implementatie configureren](#configure-smart-content-service) met de API-sleutel en andere gegevens uit Adobe Developer Console.

1. [Test de configuratie](#validate-the-configuration).

1. Optioneel [automatisch labelen inschakelen bij het uploaden van elementen](#enable-smart-tagging-in-the-update-asset-workflow-optional).

### Verkrijg openbaar certificaat door de Slimme configuratie van de Dienst van de Inhoud te creëren {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

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

   ![Het dialoogvenster Experience Manager Smart Content Service om de contentservice-URL op te geven](assets/aem_scs.png)


   *Afbeelding: Het dialoogvenster Slimme inhoudsservice om de URL van de inhoudsservice op te geven*

   >[!NOTE]
   >
   >De opgegeven URL [!UICONTROL Service URL] is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt OK met dezelfde waarde als de [!UICONTROL Service URL] parameter. Voor het algemene de dienststatus en onderhoudsplan, zie [https://status.adobe.com](https://status.adobe.com).

1. Klikken **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt`.

   ![Een voorstelling van de instellingen die voor de service voor slimme tags zijn gemaakt](assets/smart-tags-download-public-cert.png)


   *Afbeelding: Instellingen voor service voor slimme tags.*

#### Opnieuw configureren wanneer een certificaat verloopt {#certrenew}

Nadat een certificaat is verlopen, wordt het niet meer vertrouwd. U kunt een verlopen certificaat niet vernieuwen. Voer de volgende stappen uit om een certificaat toe te voegen.

1. Meld u als beheerder aan bij uw [!DNL Experience Manager]-implementatie. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]**-gebruiker. Klikken **[!UICONTROL Keystore]** tab.

1. Verwijder het bestaande **[!UICONTROL similaritysearch]**-sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Verwijder het bestaande zoekitem voor gelijkenis in Keystore om een beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)


   *Afbeelding: De bestaande verwijderen `similaritysearch` vermelding in sleutelarchief om een beveiligingscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.

1. Toegang [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande Smart Content Services op de **[!UICONTROL Integrations]** pagina. Upload het nieuwe certificaat. Zie de instructies in [Integratie met Adobe Developer Console maken](#create-adobe-i-o-integration).

### Integratie met Adobe Developer Console maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID] gebied van de integratie van Adobe Developer Console), [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], en [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] van cloudconfiguratie in [!DNL Experience Manager].

1. Open [https://console.adobe.io](https://console.adobe.io/) in uw browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er wordt een [!UICONTROL Public key(s) uploaded successfully]-bericht weergegeven. Klik op **[!UICONTROL Next]**.

   [!UICONTROL Create a new Service Account (JWT) credential] De pagina toont de openbare sleutel voor de de dienstrekening.

1. Klik op **[!UICONTROL Next]**.

1. Op de **[!UICONTROL Select product profiles]** pagina, selecteert u **[!UICONTROL Smart Content Services]**. Klik op **[!UICONTROL Save configured API]**.

   De pagina die verschijnt biedt meer informatie over de configuratie. Laat deze pagina open om deze waarden te kopiëren en toe te voegen in [!UICONTROL Assets Smart Tagging Service Settings] van cloudconfiguratie in [!DNL Experience Manager] slimme tags configureren.

   ![Op het tabblad Overview kunt u de informatie bekijken die is opgegeven voor de integratie.](assets/integration_details.png)


   *Afbeelding: integratiegegevens in Adobe Developer Console*

### Slimme-inhoudsservice configureren {#configure-smart-content-service}

>[!CAUTION]
>
>Eerder zijn configuraties die zijn gemaakt met JWT Credentials onderhevig aan afschrijving in de Adobe Developer Console. U kunt na 3 juni 2024 geen nieuwe JWT-referenties maken. Dergelijke configuraties kunnen niet meer worden gemaakt of bijgewerkt, maar kunnen worden gemigreerd naar OAuth-configuraties.
> Zie [IMS-integratie instellen voor AEM](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service)
>Zie [Stappen om OAuth voor op-premise gebruikers te vormen](#config-oauth-onprem)
> Zie [Problemen met slimme tags voor OAuth-gebruikersgegevens oplossen](#config-smart-tagging.md)

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

### OAuth voor gebruikers op locatie configureren {#config-oauth-onprem}

#### Vereisten {#prereqs-config-oauth-onprem}

Een vergunningswerkingsgebied is een koord OAuth dat de volgende eerste vereisten bevat:

* Maak een nieuwe OAuth-integratie in het dialoogvenster [Ontwerpconsole](https://developer.adobe.com/console/user/servicesandapis) gebruiken `ClientID`, `ClientSecretID`, en `OrgID`.
* De volgende bestanden toevoegen aan dit pad `/apps/system/config in crx/de`:
   * `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`
   * `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`

#### OAuth voor gebruikers op locatie configureren {#steps-config-oauth-onprem}

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
6. Verwijder de oude configuratie voor `"Access Token provider name: adobe-ims-similaritysearch"` in `/system/console/configMgr`.
7. Start de console opnieuw.

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Toegang tot uw [!DNL Experience Manager] server op `https://[aem_server]:[port]`.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klikken **[!UICONTROL Main]>[!UICONTROL JMX]**.

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Klik op `validateConfigs()`. In de **[!UICONTROL Validate Configurations]** dialoogvenster, klikt u op **[!UICONTROL Invoke]**.

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

### Slimme tags toepassen inschakelen in het dialoogvenster [!UICONTROL DAM Update Asset] workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. In [!DNL Experience Manager], ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.

1. Klik op **[!UICONTROL Edit]** op de werkbalk.

1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Afbeelding: Voeg de stap Slim tagelement toe na de stap met de procesminiaturen in het dialoogvenster [!UICONTROL DAM Update Asset] workflow.*

1. Open de stap in de bewerkingsmodus. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen](assets/smart-tag-step-properties-workflow1.png)


   *Afbeelding: de workflow voor DAM-updategegevens configureren en stap voor slimme tags toevoegen*

1. In de **[!UICONTROL Arguments]** tab, selecteert u **[!UICONTROL Ignore Errors]** als u wilt dat de workflow wordt voltooid, zelfs als de stap voor automatisch labelen mislukt.

   ![De DAM Update Asset-workflow configureren om een stap voor slimme tags toe te voegen en de voortgang van de handler te selecteren](assets/smart-tag-step-properties-workflow2.png)


   *Figuur: Vorm DAM de werkschema van de Activa van de Update om slimme markeringsstap toe te voegen en manager te selecteren vooruit*

   Als u assets tijdens het uploaden wilt voorzien van een tag (ongeacht of slimme tags zijn ingeschakeld voor mappen), moet u de optie **[!UICONTROL Ignore Smart Tag Flag]** inschakelen.

   ![Workflow van DAM Update Asset configureren om stap Smart Tag toe te voegen en markering Smart Tag negeren te selecteren](assets/smart-tag-step-properties-workflow3.png)


   *Afbeelding: Configureer de DAM Update Asset-workflow om een stap voor slimme tags toe te voegen en selecteer Slim label negeren.*

1. Klikken **[!UICONTROL OK]** om de processtap te sluiten en vervolgens de workflow op te slaan.

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

**Coherentie**: Afbeeldingen die voor een specifieke tag worden gebruikt, lijken visueel op elkaar.

Het is bijvoorbeeld geen goed idee om al deze afbeeldingen van tags te voorzien `my-party` (voor training) omdat ze niet op elkaar lijken.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coherence.png)

**Dekking**: Gebruik voldoende variatie in de afbeeldingen in de training. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat de Experience Manager leert zich te richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen.

Bijvoorbeeld voor de tag *model-down-pose* neemt u meer trainingsafbeeldingen op die lijken op de gemarkeerde afbeelding hieronder, zodat u vergelijkbare afbeeldingen tijdens het labelen nauwkeuriger kunt identificeren.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp).

Bijvoorbeeld voor de tag *casual-shoe* Het tweede imago is geen goede kandidaat voor opleiding.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/distraction.png)

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Bijvoorbeeld voor tags, zoals `raincoat` en `model-side-view`voegt u beide tags toe aan het in aanmerking komende element voordat u dit opneemt voor training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>Of de Smart Content Service uw tags kan trainen en deze op andere afbeeldingen kan toepassen, hangt af van de kwaliteit van de afbeeldingen die u voor de training gebruikt. Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

### Periodieke training {#periodic-training}

U kunt de Slimme Dienst van de Inhoud toelaten om periodiek op de activa en bijbehorende markeringen binnen een omslag te trainen. Open de [!UICONTROL Properties] pagina met uw middelenmap, selecteert u **[!UICONTROL Enable Smart Tags]** onder de **[!UICONTROL Details]** en slaat u de wijzigingen op.

![enable_smart_tags](assets/enable_smart_tags.png)

Zodra deze optie voor een omslag wordt geselecteerd, [!DNL Experience Manager] voert automatisch een trainingsworkflow uit om de Smart Content Service te trainen op de mappenelementen en de bijbehorende tags. Standaard wordt de trainingsworkflow wekelijks om 12:30 uur uitgevoerd op zaterdag.

### Opleiding op aanvraag {#on-demand-training}

U kunt de Slimme Dienst van de Inhoud wanneer vereist van de console van het Werkschema trainen.

1. In [!DNL Experience Manager] interface, ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Van de **[!UICONTROL Workflow Models]** pagina, selecteert u de **[!UICONTROL Smart Tags Training]** workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.
1. In de **[!UICONTROL Run Workflow]** , bladert u naar de payload-map met de gelabelde middelen voor het trainen van de service.
1. Geef een titel op voor de workflow en voeg een opmerking toe. Klik vervolgens op **[!UICONTROL Run]**. De elementen en tags worden ter training aangeboden.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Nadat de middelen in een map zijn verwerkt voor training, worden alleen de gewijzigde middelen verwerkt in volgende trainingscycli.

### Trainingsrapporten weergeven {#viewing-training-reports}

Om te controleren of de Slimme Dienst van de Inhoud op uw markeringen in de trainingsreeks activa wordt getraind, herzie het rapport van de opleidingswerkstroom van de console van Rapporten.

1. In [!DNL Experience Manager] interface, ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. In de **[!UICONTROL Asset Reports]** pagina, klikt u **[!UICONTROL Create]**.
1. Selecteer de **[!UICONTROL Smart Tags Training]** rapport, en klik dan **[!UICONTROL Next]** op de werkbalk.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk.
1. Bekijk de details van het rapport.

   Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de Smart Content Service is getraind voor de tag. Een gele kleur geeft aan dat de service niet volledig is getraind voor een bepaalde tag. Voeg in dit geval meer afbeeldingen met de desbetreffende tag toe en voer de trainingsworkflow uit om de service volledig op de tag te trainen.

   Als dit rapport uw tags niet bevat, voert u de trainingsworkflow voor deze tags opnieuw uit.

1. Om het rapport te downloaden, selecteer het van de lijst, en klik **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een Microsoft Excel-spreadsheet.

## Beperkingen {#limitations}

* Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de Smart Content Service heeft de volgende beperkingen:

   * Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
   * Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
   * Tags worden ondersteund in de landinstellingen die [!DNL Experience Manager] wordt ondersteund in.

* Als u wilt zoeken naar elementen met slimme tags (normaal of verbeterd), gebruikt u de opdracht [!DNL Assets] Omnissearch (full-text zoekopdracht). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!MORELIKETHIS]
>
>* [Overzicht en hoe u slimme tags kunt trainen](enhanced-smart-tags.md)
>* [Problemen met slimme tags voor OAuth-gebruikersgegevens oplossen](config-smart-tagging.md)
>* [Videozelfstudie over slimme tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html)
