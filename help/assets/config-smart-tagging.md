---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe te om slimme het etiketteren en verbeterde slimme het etiketteren in  [!DNL Adobe Experience Manager] te vormen, gebruikend de Slimme Dienst van de Inhoud.
contentOwner: AG
role: Admin
feature: Tagging,Smart Tags
exl-id: 9f68804f-ba15-4f83-ab1b-c249424b1396
solution: Experience Manager, Experience Manager Assets
source-git-commit: 5aff321eb52c97e076c225b67c35e9c6d3371154
workflow-type: tm+mt
source-wordcount: '2152'
ht-degree: 16%

---

# [!DNL Assets] voorbereiden voor slimme tags {#configure-asset-tagging-using-the-smart-content-service}

Voordat u met het labelen van uw middelen begint met Smart Content Services, moet u [!DNL Experience Manager Assets] integreren met Adobe Developer Console om de slimme service van [!DNL Adobe Sensei] te gebruiken. Zodra gevormd treig de dienst gebruikend een paar beelden en een markering.

>[!NOTE]
>
>* Smart Content Services is niet meer beschikbaar voor nieuwe klanten van [!DNL Experience Manager Assets] On-Premise. Bestaande klanten op locatie, die deze mogelijkheid al hebben ingeschakeld, kunnen Smart Content Services blijven gebruiken.
>* Smart Content Services is beschikbaar voor bestaande [!DNL Experience Manager Assets] Managed Services-klanten die deze mogelijkheid al hebben ingeschakeld.
>* Nieuwe [!DNL Experience Manager Assets] Managed Services-klanten kunnen de instructies in dit artikel volgen om Smart Content Services in te stellen.

Controleer het volgende voordat u de Smart Content Service gebruikt:

* [ integreer met Adobe Developer Console ](#integrate-adobe-io).
* [ Lijn de Slimme Dienst van de Inhoud ](#training-the-smart-content-service).

* Installeer het recentste [[!DNL Experience Manager]  Pak van de Dienst ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html).

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Wanneer u met Adobe Developer Console integreert, verifieert de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van Adobe Developer Console alvorens uw verzoek aan de Slimme Dienst van de Inhoud door:sturen. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en de licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. Om een openbare sleutel te produceren, [ creeer een Slimme 1} configuratie van de Dienst van de Inhoud {in [!DNL Experience Manager]. ](#obtain-public-certificate) [Verkrijg een openbaar certificaat voor OAuth-integratie.](#obtain-public-certificate)

1. [Maak een integratie in Adobe Developer Console en upload de gegenereerde openbare sleutel.](#create-adobe-i-o-integration)

1. [ vorm uw plaatsing ](#configure-smart-content-service) gebruikend de API sleutel en andere geloofsbrieven van Adobe Developer Console.

1. [Test de configuratie](#validate-the-configuration).

1. Naar keuze, [ laat auto-etiketteren op activa toe uploadt ](#enable-smart-tagging-in-the-update-asset-workflow-optional).

### Verkrijg openbaar certificaat door de Slimme configuratie van de Dienst van de Inhoud te creëren {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

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

   ![ Experience Manager de Slimme dialoog van de Dienst van de Inhoud om de inhoudsdienst URL ](assets/aem_scs.png) te verstrekken


   *Cijfer: De slimme dialoog van de Dienst van de Inhoud om de inhoudsdienst URL* te verstrekken

   >[!NOTE]
   >
   >De URL die als [!UICONTROL Service URL] wordt opgegeven, is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt OK met dezelfde waarde als de parameter [!UICONTROL Service URL] . Voor het algemene de dienststatus en onderhoudsprogramma, zie [ https://status.adobe.com ](https://status.adobe.com).

1. Klik op **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt` .

   ![ een vertegenwoordiging van de montages die voor de slimme het etiketteren dienst ](assets/smart-tags-download-public-cert.png) worden gecreeerd


   *Cijfer: Montages voor de slimme het etiketteren dienst.*

#### Opnieuw configureren wanneer een certificaat verloopt {#certrenew}

Nadat een certificaat is verlopen, wordt het niet meer vertrouwd. U kunt een verlopen certificaat niet vernieuwen. Voer de volgende stappen uit om een certificaat toe te voegen.

1. Meld u als beheerder aan bij uw [!DNL Experience Manager]-implementatie. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]**-gebruiker. Klik op **[!UICONTROL Keystore]** tab.

1. Verwijder het bestaande **[!UICONTROL similaritysearch]**-sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![ Schrap de bestaande ingang van het gelijkheidsonderzoek in Keystore om een veiligheidscertificaat toe te voegen ](assets/smarttags_delete_similaritysearch_keystore.png)


   *Cijfer: Schrap de bestaande `similaritysearch` ingang in Keystore om een veiligheidscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.

1. Toegang [ https://console.adobe.io ](https://console.adobe.io) en navigeer aan de bestaande Slimme Diensten van de Inhoud op de **[!UICONTROL Integrations]** pagina. Upload het nieuwe certificaat. Voor meer informatie, zie de instructies in [ de integratie van Adobe Developer Console ](#create-adobe-i-o-integration) creëren.

### Adobe Developer Console-integratie maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID] field of Adobe Developer Console integration), [!UICONTROL TECHNICAL ACCOUNT ID] , [!UICONTROL ORGANIZATION ID] en [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] of cloud configuration in [!DNL Experience Manager] te verkrijgen.

1. Open [https://console.adobe.io](https://console.adobe.io/) in uw browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er wordt een [!UICONTROL Public key(s) uploaded successfully]-bericht weergegeven. Klik op **[!UICONTROL Next]**.

   Op de pagina [!UICONTROL Create a new Service Account (JWT) credential] wordt de openbare sleutel voor het serviceaccount weergegeven.

1. Klik op **[!UICONTROL Next]**.

1. Selecteer op de pagina **[!UICONTROL Select product profiles]** de optie **[!UICONTROL Smart Content Services]** . Klik op **[!UICONTROL Save configured API]**.

   De pagina die verschijnt biedt meer informatie over de configuratie. Zorg dat deze pagina geopend blijft en kopieer deze waarden in [!UICONTROL Assets Smart Tagging Service Settings] van de cloudconfiguratie in [!DNL Experience Manager] om slimme tags te configureren.

   ![Op het tabblad Overview kunt u de informatie bekijken die is opgegeven voor de integratie.](assets/integration_details.png)


   *Cijfer: Details van integratie in Adobe Developer Console*

### Slimme-inhoudsservice configureren {#configure-smart-content-service}

>[!CAUTION]
>
>Eerder zijn configuraties die zijn gemaakt met JWT Credentials onderhevig aan afschrijving in de Adobe Developer Console. U kunt na 3 juni 2024 geen nieuwe JWT-referenties maken. Dergelijke configuraties kunnen niet meer worden gemaakt of bijgewerkt, maar kunnen worden gemigreerd naar OAuth-configuraties.
> Zie [ de integratie van IMS van de Opstelling voor AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service)
>Zie [ Stappen om OAuth voor op-premise gebruikers ](#config-oauth-onprem) te vormen
> Zie [ het Oplossen van problemen slimme markeringen voor geloofsbrieven OAuth ](#config-smart-tagging.md)

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

### OAuth voor gebruikers op locatie configureren {#config-oauth-onprem}

#### Vereisten {#prereqs-config-oauth-onprem}

Een vergunningswerkingsgebied is een koord OAuth dat de volgende eerste vereisten bevat:

* Creeer een nieuwe integratie OAuth in [ Developer Console ](https://developer.adobe.com/console/user/servicesandapis) gebruikend `ClientID`, `ClientSecretID`, en `OrgID`.
* Voeg de volgende bestanden toe op dit pad `/apps/system/config in crx/de` :
   * `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config`
   * `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config`

#### OAuth voor gebruikers op locatie configureren {#steps-config-oauth-onprem}

1. Voeg de onderstaande eigenschappen toe of werk deze bij in `com.adobe.granite.auth.oauth.accesstoken.provider.<randomnumbers>.config` :

   * `auth.token.provider.authorization.grants="client_credentials"`
   * `auth.token.provider.orgId="<OrgID>"`
   * `auth.token.provider.default.claims=("\"iss\"\ :\ \"<OrgID>\"")`
   * `auth.token.provider.scope="read_pc.dma_smart_content,\ openid,\ AdobeID,\ additional_info.projectedProductContext"`
     `auth.token.validator.type="adobe-ims-similaritysearch"`
   * Werk `auth.token.provider.client.id` met Cliënt identiteitskaart van de nieuwe configuratie OAuth bij.
   * `auth.access.token.request` bijwerken naar `"https://ims-na1.adobelogin.com/ims/token/v3"`
2. Wijzig de naam van het bestand in `com.adobe.granite.auth.oauth.accesstoken.provider-<randomnumber>.config` .
3. Voer de onderstaande stappen uit in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl.<randomnumber>.config` :
   * Werk het bezit auth.ims.client.geheime met het Geheim van de Cliënt van de nieuwe integratie OAuth bij.
   * Naam van bestand wijzigen in `com.adobe.granite.auth.ims.impl.IMSAccessTokenRequestCustomizerImpl-<randomnumber>.config`
4. Sla alle wijzigingen op in de ontwikkelingsconsole van de inhoudsopslagplaats, bijvoorbeeld CRXDE.
5. Navigeer naar `/system/console/configMgr` en vervang de OSGi-configuratie van `.<randomnumber>` tot `-<randomnumber>` .
6. Verwijder de oude configuratie voor `"Access Token provider name: adobe-ims-similaritysearch"` in `/system/console/configMgr` .
7. Start de console opnieuw.

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open de [!DNL Experience Manager] -server op `https://[aem_server]:[port]` .

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]** .

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Deze wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]** .

1. Klik op `validateConfigs()`. Klik in het dialoogvenster **[!UICONTROL Validate Configurations]** op **[!UICONTROL Invoke]** .

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

### Slimme tags toepassen inschakelen in de [!UICONTROL DAM Update Asset] -workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .

1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.

1. Klik op **[!UICONTROL Edit]** op de werkbalk.

1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Cijfer: Voeg slimme stap van de markeringsactiva na de stap van de procesduimnagel in het [!UICONTROL DAM Update Asset] werkschema toe.*

1. Open de stap in de bewerkingsmodus. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![ vorm het werkschema van de Activa van de Update DAM en voeg slimme markeringsstap ](assets/smart-tag-step-properties-workflow1.png) toe


   *Figuur: Vorm het werkschema van de Activa van de Update DAM en voeg slimme markeringsstap* toe

1. Selecteer op het tabblad **[!UICONTROL Arguments]** de optie **[!UICONTROL Ignore Errors]** als u de workflow wilt voltooien, zelfs als de stap Automatisch labelen is mislukt.

   ![ vorm het werkschema van de Activa van de Update DAM om slimme markeringsstap toe te voegen en manager vooruit te selecteren ](assets/smart-tag-step-properties-workflow2.png)


   *Cijfer: Vorm het werkschema van de Activa van de Update DAM om slimme markeringsstap toe te voegen en manager vooruit te selecteren*

   Als u assets tijdens het uploaden wilt voorzien van een tag (ongeacht of slimme tags zijn ingeschakeld voor mappen), moet u de optie **[!UICONTROL Ignore Smart Tag Flag]** inschakelen.

   ![ vorm het werkschema van de Activa van de Update DAM om slimme markeringsstap toe te voegen en de uitgezochte Slimme markering van de Markering te negeren ](assets/smart-tag-step-properties-workflow3.png)


   *Cijfer: Vorm het werkschema van de Activa van de Update DAM om slimme markeringsstap toe te voegen en de uitgezochte markering van de Slimme Markering te negeren.*

1. Klik op **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op.

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
