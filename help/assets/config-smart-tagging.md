---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe u slimme tags en verbeterde slimme tags configureert in [!DNL Adobe Experience Manager] met de Smart Content Service.
contentOwner: AG
role: Beheerder
feature: Tags,slimme tags
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 21%

---


# [!DNL Assets] voorbereiden voor slimme tags {#configure-asset-tagging-using-the-smart-content-service}

Voordat u met het labelen van uw middelen kunt beginnen met Smart Content Services, moet u [!DNL Experience Manager Assets] integreren met Adobe Developer Console om de slimme service van [!DNL Adobe Sensei] te benutten. Zodra gevormd treig de dienst gebruikend een paar beelden en een markering.

Controleer het volgende voordat u de Smart Content Service gebruikt:

* [Integreren met Adobe Developer Console](#integrate-adobe-io).
* [Train the Smart Content Service](#training-the-smart-content-service).

* Installeer het nieuwste [[!DNL Experience Manager] Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html).

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Wanneer u met de Console van de Ontwikkelaar van Adobe integreert, verifieert de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van de Console van de Ontwikkelaar van de Adobe alvorens uw verzoek aan de Slimme Dienst van de Inhoud door:sturen. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en de licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. Om een openbare sleutel te produceren, [creeer een Slimme Configuratie van de Dienst](#obtain-public-certificate) in [!DNL Experience Manager]. [Verkrijg een openbaar certificaat voor OAuth-integratie.](#obtain-public-certificate)

1. [Maak een integratie in Adobe Developer Console en upload de gegenereerde openbare sleutel.](#create-adobe-i-o-integration)

1. [Configureer uw ](#configure-smart-content-service) implementatie met behulp van de API-sleutel en andere gegevens uit de Adobe Developer Console.

1. [Test de configuratie](#validate-the-configuration).

1. Schakel desgewenst automatische labeling in bij het uploaden van elementen](#enable-smart-tagging-in-the-update-asset-workflow-optional).[

### Verkrijg openbaar certificaat door de Slimme configuratie van de Dienst van de Inhoud {#obtain-public-certificate} te creëren

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. Klik op **[!UICONTROL Configure Now]** onder **[!UICONTROL Assets Smart Tags]** op de pagina Cloud Services.

1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een titel en naam op voor de configuratie van slimme tags. Klik op **[!UICONTROL Create]**.

1. Gebruik de volgende waarden in het dialoogvenster **[!UICONTROL AEM Smart Content Service]**:

   **[!UICONTROL Service URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**:  `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Klik op **[!UICONTROL OK]**.

   ![Het dialoogvenster Experience Manager Smart Content Service om de contentservice-URL op te geven](assets/aem_scs.png)


   *Afbeelding: Het dialoogvenster Smart Content Service om de URL van de inhoudsservice te bieden*

   >[!NOTE]
   >
   >De URL die als [!UICONTROL Service URL] wordt opgegeven, is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt O.K. met de zelfde waarde van de [!UICONTROL Service URL] parameter. Zie [https://status.adobe.com](https://status.adobe.com) voor het algemene servicestatus en onderhoudsplan.

1. Klik **[!UICONTROL Download Public Certificate for OAuth Integration]**, en download het openbare certificaatdossier `AEM-SmartTags.crt`.

   ![Een voorstelling van de instellingen die voor de service voor slimme tags zijn gemaakt](assets/smart-tags-download-public-cert.png)


   *Afbeelding: Instellingen voor service voor slimme tags.*

#### Opnieuw configureren wanneer een certificaat verloopt {#certrenew}

Nadat een certificaat is verlopen, wordt het niet meer vertrouwd. U kunt een verlopen certificaat niet verlengen. Voer de volgende stappen uit om een certificaat toe te voegen.

1. Meld u als beheerder aan bij uw [!DNL Experience Manager]-implementatie. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]**-gebruiker. Klik op het tabblad **[!UICONTROL Keystore]**. 

1. Verwijder het bestaande **[!UICONTROL similaritysearch]**-sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Verwijder het bestaande zoekitem voor gelijkenis in Keystore om een beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)


   *Afbeelding: Verwijder het bestaande  `similaritysearch` item in het sleutelarchief om een beveiligingscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.

1. Open [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande Smart Content Services op de pagina **[!UICONTROL Integrations]**. Upload het nieuwe certificaat. Zie de instructies in [Integratie van de Adobe Developer Console maken](#create-adobe-i-o-integration) voor meer informatie.

### Integratie van Adobe-ontwikkelaarsconsole maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in de Adobe Developer Console voor [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID]-veld voor integratie van Adobe Developer Console), [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID] en [!UICONTROL CLIENT SECRET] voor [!UICONTROL Assets Smart Tagging Service Settings] van cloudconfiguratie in [!DNL Experience Manager].

1. Open [https://console.adobe.io](https://console.adobe.io/) in uw browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er wordt een [!UICONTROL Public key(s) uploaded successfully]-bericht weergegeven. Klik op **[!UICONTROL Next]**.

   [!UICONTROL Create a new Service Account (JWT) credential] De pagina toont de openbare sleutel voor de de dienstrekening.

1. Klik op **[!UICONTROL Next]**.

1. Ga naar de pagina **[!UICONTROL Select product profiles]** en selecteer **[!UICONTROL Smart Content Services]**. Klik op **[!UICONTROL Save configured API]**.

   De pagina die verschijnt biedt meer informatie over de configuratie. Laat deze pagina open om deze waarden in [!UICONTROL Assets Smart Tagging Service Settings] van de wolkenconfiguratie in [!DNL Experience Manager] te kopiëren en toe te voegen om slimme markeringen te vormen.

   ![Op het tabblad Overview kunt u de informatie bekijken die is opgegeven voor de integratie.](assets/integration_details.png)


   *Afbeelding: Gegevens over de integratie in de Adobe Developer Console*

### Smart Content Service {#configure-smart-content-service} configureren

Om de integratie te vormen, gebruik de waarden van [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], [!UICONTROL CLIENT SECRET], en [!UICONTROL CLIENT ID] gebieden van de integratie van de Console van de Ontwikkelaar van Adobe. Het creëren van een Slimme wolkenconfiguratie van Markeringen staat authentificatie van API verzoeken van de [!DNL Experience Manager] plaatsing toe.

1. Navigeer in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** om de [!UICONTROL Cloud Services]-console te openen.

1. Open onder **[!UICONTROL Assets Smart Tags]** de hierboven gemaakte configuratie. Klik op **[!UICONTROL Edit]** op de pagina met service-instellingen.

1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.

1. Voor de velden [!UICONTROL Api Key], [!UICONTROL Technical Account ID], [!UICONTROL Organization ID], en [!UICONTROL Client Secret], kopieer en gebruik de volgende waarden die in [de integratie van de Console van de Adobe worden geproduceerd ](#create-adobe-i-o-integration).

   | [!UICONTROL Assets Smart Tagging Service Settings] | [!DNL Adobe Developer Console] integratievelden |
   |--- |--- |
   | [!UICONTROL Api Key] | [!UICONTROL CLIENT ID] |
   | [!UICONTROL Technical Account ID] | [!UICONTROL TECHNICAL ACCOUNT ID] |
   | [!UICONTROL Organization ID] | [!UICONTROL ORGANIZATION ID] |
   | [!UICONTROL Client Secret] | [!UICONTROL CLIENT SECRET] |

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open uw [!DNL Experience Manager]-server op `https://[aem_server]:[port]`.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]**.

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Het opent **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Klik op `validateConfigs()`. Klik in het dialoogvenster **[!UICONTROL Validate Configurations]** op **[!UICONTROL Invoke]**.

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

### Slimme tags toepassen inschakelen in de [!UICONTROL DAM Update Asset]-workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.

1. Klik op **[!UICONTROL Edit]** op de werkbalk.

1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Afbeelding: Voeg de stap Slimme tag-elementen toe na de stap met de procesminiaturen in de  [!UICONTROL DAM Update Asset] workflow.*

1. Open de stap in de bewerkingsmodus. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen](assets/smart-tag-step-properties-workflow1.png)


   *Afbeelding: Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen*

1. Selecteer **[!UICONTROL Arguments]** op het tabblad **[!UICONTROL Ignore Errors]** als u de workflow wilt voltooien, zelfs als de stap voor automatische labeling mislukt.

   ![De DAM Update Asset-workflow configureren om een stap voor slimme tags toe te voegen en de voortgang van de handler te selecteren](assets/smart-tag-step-properties-workflow2.png)


   *Afbeelding: De DAM Update Asset-workflow configureren om een stap voor slimme tags toe te voegen en de voortgang van de handler te selecteren*

   Als u assets tijdens het uploaden wilt voorzien van een tag (ongeacht of slimme tags zijn ingeschakeld voor mappen), moet u de optie **[!UICONTROL Ignore Smart Tag Flag]** inschakelen.

   ![Workflow van DAM Update Asset configureren om stap Smart Tag toe te voegen en markering Smart Tag negeren te selecteren](assets/smart-tag-step-properties-workflow3.png)


   *Afbeelding: Configureer de DAM Update Asset-workflow om een stap met slimme tags toe te voegen en selecteer Slim label negeren.*

1. Klik op **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op.

## Train de Smart Content Service {#training-the-smart-content-service}

Als u wilt dat de Smart Content Service uw bedrijfskrionomie herkent, voert u deze uit op een reeks elementen die al tags bevatten die relevant zijn voor uw bedrijf. Om uw merkbeelden effectief te etiketteren, vereist de Slimme Dienst van de Inhoud dat de trainingsbeelden aan bepaalde richtlijnen voldoen. Na de training kan de service dezelfde taxonomie toepassen op een vergelijkbare set activa.

U kunt de service meerdere keren trainen om de service beter in staat te stellen relevante tags toe te passen. Voer na elke trainingscyclus een labelworkflow uit en controleer of uw elementen correct zijn gecodeerd.

U kunt de Slimme Dienst van de Inhoud periodiek of op vereiste basis trainen.

>[!NOTE]
>
>De trainingsworkflow wordt alleen uitgevoerd voor mappen.

### Richtlijnen voor training {#guidelines-for-training}

Voor de beste resultaten voldoen de afbeeldingen in de trainingsset aan de volgende richtlijnen:

**Hoeveelheid en grootte:** Minimaal 30 afbeeldingen per tag. Minimaal 500 pixels aan de langere zijde.

**Coherentie**: Afbeeldingen die voor een specifieke tag worden gebruikt, lijken visueel op elkaar.

Het is bijvoorbeeld geen goed idee om al deze afbeeldingen te labelen als `my-party` (voor training), omdat ze er anders uitzien.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coherence.png)

**Dekking**: Gebruik voldoende variatie in de afbeeldingen in de training. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat de Experience Manager leert zich te richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen.

Voor de tag *model-down-pose* neemt u bijvoorbeeld meer trainingsafbeeldingen op die lijken op de gemarkeerde afbeelding hieronder, zodat u vergelijkbare afbeeldingen tijdens het labelen nauwkeuriger kunt identificeren.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp).

Voor de tag *casual-shoe* is de tweede afbeelding bijvoorbeeld geen goede trainingskandidaat.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/distraction.png)

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Voeg bijvoorbeeld voor tags, zoals `raincoat` en `model-side-view`, beide tags toe aan het in aanmerking komende element voordat u dit opneemt voor training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>Of de Smart Content Service uw tags kan trainen en deze op andere afbeeldingen kan toepassen, hangt af van de kwaliteit van de afbeeldingen die u voor de training gebruikt. Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

### Periodieke training {#periodic-training}

U kunt de Slimme Dienst van de Inhoud toelaten om periodiek op de activa en bijbehorende markeringen binnen een omslag te trainen. Open de pagina [!UICONTROL Properties] van de elementenmap, selecteer **[!UICONTROL Enable Smart Tags]** onder het tabblad **[!UICONTROL Details]** en sla de wijzigingen op.

![enable_smart_tags](assets/enable_smart_tags.png)

Als deze optie voor een map is geselecteerd, wordt automatisch een trainingsworkflow uitgevoerd om de Smart Content Service te trainen voor de mappenelementen en de bijbehorende tags. [!DNL Experience Manager] Standaard wordt de trainingsworkflow wekelijks om 12:30 uur uitgevoerd op zaterdag.

### On-demand training {#on-demand-training}

U kunt de Slimme Dienst van de Inhoud wanneer vereist van de console van het Werkschema trainen.

1. Ga in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL Smart Tags Training]**-workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.
1. Blader in het dialoogvenster **[!UICONTROL Run Workflow]** naar de payload-map met de gecodeerde middelen voor het trainen van de service.
1. Geef een titel op voor de workflow en voeg een opmerking toe. Klik vervolgens op **[!UICONTROL Run]**. De elementen en tags worden ter training aangeboden.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Nadat de middelen in een map zijn verwerkt voor training, worden alleen de gewijzigde middelen verwerkt in volgende trainingscycli.

### Trainingsrapporten weergeven {#viewing-training-reports}

Om te controleren of de Slimme Dienst van de Inhoud op uw markeringen in de trainingsreeks activa wordt getraind, herzie het rapport van de opleidingswerkstroom van de console van Rapporten.

1. Ga in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. Klik op **[!UICONTROL Asset Reports]** op de pagina.**[!UICONTROL Create]**
1. Selecteer het **[!UICONTROL Smart Tags Training]** rapport, en klik dan **[!UICONTROL Next]** van de toolbar.
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
   * Tags worden ondersteund in de landinstellingen waarin [!DNL Experience Manager] wordt ondersteund. Zie [Opmerkingen bij de release Smart Content Services](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/smart-content-service-release-notes.html) voor een lijst met talen.

* Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u [!DNL Assets] Omnzoekopdracht (full-text zoekopdracht). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!MORELIKETHIS]
>
>* [Overzicht van slimme tags en hoe deze kunnen worden getraind](enhanced-smart-tags.md)
>* [Videozelfstudie over slimme tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html)

