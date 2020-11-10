---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe u slimme tags en verbeterde slimme tags kunt configureren in [!DNL Adobe Experience Manager]de Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 23%

---


# Voorbereiden [!DNL Assets] op slimme tags {#configure-asset-tagging-using-the-smart-content-service}

Voordat u met het labelen van uw middelen begint met Smart Content Services, dient u uw bestanden te integreren [!DNL Experience ManageR Assets] met de Adobe Developer Console om de slimme service van [!DNL Adobe Sensei]te gebruiken. Zodra gevormd treig de dienst gebruikend een paar beelden en een markering.

Controleer het volgende voordat u de Smart Content Service gebruikt:

* [Integreren met Adobe Developer Console](#integrate-adobe-io).
* [Train the Smart Content Service](#training-the-smart-content-service).

   <!-- TBD: This link will update soon after the new articles goes live on docs.adobe.com. Change it when new URL is available.
  -->

* Installeer het nieuwste servicepakket voor [Experience Managers](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html).

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Wanneer u met de Console van de Ontwikkelaar van Adobe integreert, verklaart de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van de Console van de Ontwikkelaar van Adobe voor het door:sturen van uw verzoek aan de Slimme Dienst van de Inhoud voor authentiek. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en de licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. [Creeer een Slimme configuratie van de Dienst](#obtain-public-certificate) van de Inhoud binnen [!DNL Experience Manager] om een openbare sleutel te produceren. [Verkrijg een openbaar certificaat voor OAuth-integratie.](#obtain-public-certificate)

1. [Maak een integratie in Adobe Developer Console en upload de gegenereerde openbare sleutel.](#create-adobe-i-o-integration)

1. [Configureer uw implementatie](#configure-smart-content-service) met behulp van de API-sleutel en andere gegevens uit de Adobe Developer Console.

1. [Test de configuratie](#validate-the-configuration).

1. Optionally, [enable auto-tagging on asset upload](#enable-smart-tagging-in-the-update-asset-workflow-optional).

### Configuratie van Smart Content Service maken om een openbaar certificaat te verkrijgen {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe Developer Console.

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. In the Cloud Services page, click **[!UICONTROL Configure Now]** under **[!UICONTROL Assets Smart Tags]**.

1. Geef in het **[!UICONTROL Create Configuration]** dialoogvenster een titel en naam op voor de configuratie Slimme tags. Klik op **[!UICONTROL Create]**.

1. Gebruik de volgende waarden in het **[!UICONTROL AEM Smart Content Service]** dialoogvenster:

   **[!UICONTROL Service URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Authorization Server]**: `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Klik op **[!UICONTROL OK]**.

   ![Het dialoogvenster Experience Manager Smart Content Service om de contentservice-URL op te geven](assets/aem_scs.png)


   *Afbeelding: Het dialoogvenster Smart Content Service om de URL van de inhoudsservice te bieden*

   >[!NOTE]
   >
   >De URL die wordt opgegeven als [!UICONTROL Service URL] is niet toegankelijk via de browser en genereert een fout van 404. De configuratie werkt OK met dezelfde waarde als de [!UICONTROL Service URL] parameter. Voor het algemene de dienststatus en onderhoudsplan, zie [https://status.adobe.com](https://status.adobe.com).

1. Klik **[!UICONTROL Download Public Certificate for OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt`.

   ![Een voorstelling van de instellingen die voor de service voor slimme tags zijn gemaakt](assets/smart-tags-download-public-cert.png)


   *Afbeelding: Instellingen voor service voor slimme tags*

#### Reconfigure when a certificate expires {#certrenew}

Nadat een certificaat is verlopen, wordt het niet meer vertrouwd. U kunt een verlopen certificaat niet verlengen. Voer de onderstaande stappen uit om een nieuw certificaat toe te voegen.

1. Meld u als beheerder aan bij uw [!DNL Experience Manager]-implementatie. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]**-gebruiker. Klik op het tabblad **[!UICONTROL Keystore]**. 

1. Verwijder het bestaande **[!UICONTROL similaritysearch]**-sleutelarchief met het verlopen certificaat. Klik op **[!UICONTROL Save & Close]**.

   ![Verwijder het bestaande zoekitem voor gelijkenis in Keystore om een nieuw beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)


   *Afbeelding: Verwijder de bestaande `similaritysearch`-vermelding in het sleutelarchief om een nieuw beveiligingscertificaat toe te voegen.*

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**. Klik op **[!UICONTROL Asset Smart Tags]** > **[!UICONTROL Show Configuration]** > **[!UICONTROL Available Configurations]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op **[!UICONTROL Download Public Certificate for OAuth Integration]**.

1. Ga naar [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande Smart Content Services op de **[!UICONTROL Integrations]** pagina. Upload het nieuwe certificaat. For more information, see the instructions in [Create Adobe Developer Console integration](#create-adobe-i-o-integration).

### Integratie van Adobe Developer Console maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in de Adobe Developer Console om deze te verkrijgen [!UICONTROL API Key] (gegenereerd op [!UICONTROL CLIENT ID] gebied van de integratie van de Adobe Developer Console), [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID]en [!UICONTROL CLIENT SECRET] voor [!UICONTROL Assets Smart Tagging Service Settings] de configuratie van de cloud in [!DNL Experience Manager].

1. Open [https://console.adobe.io](https://console.adobe.io/) in uw browser. Selecteer het gewenste account en verifieer dat de bijbehorende organisatierol is ingesteld op systeembeheerder.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Upload your public key]**. Geef het certificaatbestand op dat u hebt gedownload van [!DNL Experience Manager]. Er wordt een [!UICONTROL Public key(s) uploaded successfully]-bericht weergegeven. Klik op **[!UICONTROL Next]**.

   De pagina [!UICONTROL Create a new Service Account (JWT) credential] toont de openbare sleutel voor het serviceaccount dat u zojuist hebt geconfigureerd. 

1. Klik op **[!UICONTROL Next]**.

1. Ga naar de pagina **[!UICONTROL Select product profiles]** en selecteer **[!UICONTROL Smart Content Services]**. Klik op **[!UICONTROL Save configured API]**.

   De pagina die verschijnt biedt meer informatie over de configuratie. Zorg dat deze pagina geopend blijft en kopieer en voeg deze waarden toe in [!UICONTROL Assets Smart Tagging Service Settings] de cloudconfiguratie [!DNL Experience Manager] om slimme tags te configureren.

   ![Op het tabblad Overview kunt u de informatie bekijken die is opgegeven voor de integratie.](assets/integration_details.png)


   *Afbeelding: Gegevens over de integratie in de Adobe Developer Console*

### Smart Content Service configureren {#configure-smart-content-service}

To configure the integration, use the values of [!UICONTROL TECHNICAL ACCOUNT ID], [!UICONTROL ORGANIZATION ID], [!UICONTROL CLIENT SECRET], and [!UICONTROL CLIENT ID] fields from the Adobe Developer Console integration. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] implementatie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager], naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Legacy Cloud Services]** om de [!UICONTROL Cloud Services] console te openen.

1. Open onder de **[!UICONTROL Assets Smart Tags]** sectie de configuratie die hierboven is gemaakt. Klik op de pagina met service-instellingen **[!UICONTROL Edit]**.

1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]**.

1. Voor de gebieden [!UICONTROL Api Key], [!UICONTROL Technical Account ID], [!UICONTROL Organization ID], en [!UICONTROL Client Secret], kopieer en gebruik de volgende waarden die in de integratie [van de Console van de Ontwikkelaar van](#create-adobe-i-o-integration)Adobe worden geproduceerd.

   | [!UICONTROL Assets Smart Tagging Service Settings] | [!DNL Adobe Developer Console] integratievelden |
   |--- |--- |
   | [!UICONTROL Api Key] | [!UICONTROL CLIENT ID] |
   | [!UICONTROL Technical Account ID] | [!UICONTROL TECHNICAL ACCOUNT ID] |
   | [!UICONTROL Organization ID] | [!UICONTROL ORGANIZATION ID] |
   | [!UICONTROL Client Secret] | [!UICONTROL CLIENT SECRET] |

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open uw [!DNL Experience Manager] server op `https://[aem_server]:[port]`.

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]**.

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl`. Het wordt geopend **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.

1. Klik op `validateConfigs()`. In the **[!UICONTROL Validate Configurations]** dialog, click **[!UICONTROL Invoke]**.

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

### Slimme tags toepassen inschakelen in de [!UICONTROL DAM Update Asset] workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.

1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.

1. Klik op **[!UICONTROL Edit]** op de werkbalk.

1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

   *Afbeelding: Voeg de stap Slimme tag-elementen toe na de stap met de procesminiaturen in de [!UICONTROL DAM Update Asset] workflow.*

1. Open de stap in de bewerkingsmodus. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen](assets/smart-tag-step-properties-workflow1.png)


   *Afbeelding: Workflow van DAM-updatemiddelen configureren en stap voor slimme tags toevoegen*

1. In the **[!UICONTROL Arguments]** tab, select **[!UICONTROL Ignore Errors]** if you want the workflow to complete even if the automatic tagging step fails.

   ![De DAM Update Asset-workflow configureren om een stap voor slimme tags toe te voegen en de voortgang van de handler te selecteren](assets/smart-tag-step-properties-workflow2.png)


   *Afbeelding: De DAM Update Asset-workflow configureren om een stap voor slimme tags toe te voegen en de voortgang van de handler te selecteren*

   Als u assets tijdens het uploaden wilt voorzien van een tag (ongeacht of slimme tags zijn ingeschakeld voor mappen), moet u de optie **[!UICONTROL Ignore Smart Tag Flag]** inschakelen.

   ![Workflow van DAM Update Asset configureren om stap Smart Tag toe te voegen en markering Smart Tag negeren te selecteren](assets/smart-tag-step-properties-workflow3.png)


   *Afbeelding: Workflow van DAM Update Asset configureren om stap Smart Tag toe te voegen en markering Smart Tag negeren te selecteren*

1. Klik op **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op.

## De Smart Content Service trainen {#training-the-smart-content-service}

Als u wilt dat de Smart Content Service uw bedrijfskrionomie herkent, voert u deze uit op een reeks elementen die al tags bevatten die relevant zijn voor uw bedrijf. Om uw merkbeelden effectief te etiketteren, vereist de Slimme Dienst van de Inhoud dat de trainingsbeelden aan bepaalde richtlijnen voldoen. Na de training kan de service dezelfde taxonomie toepassen op een vergelijkbare set activa.

U kunt de service meerdere keren trainen om de service beter in staat te stellen relevante tags toe te passen. Voer na elke trainingscyclus een labelworkflow uit en controleer of uw elementen correct zijn gecodeerd.

U kunt de Slimme Dienst van de Inhoud periodiek of op vereiste basis trainen.

>[!NOTE]
>
>De trainingsworkflow wordt alleen uitgevoerd voor mappen.

### Richtsnoeren voor opleiding {#guidelines-for-training}

Voor de beste resultaten moeten de afbeeldingen in de trainingsset voldoen aan de volgende richtlijnen:

**Hoeveelheid en grootte:** Minimaal 30 afbeeldingen per tag. Minimaal 500 pixels aan de langere zijde.

**Coherentie**: Afbeeldingen voor een tag moeten visueel op elkaar lijken.

Het is bijvoorbeeld geen goed idee om al deze afbeeldingen als `my-party` (voor training) te labelen, omdat ze er anders uitzien.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coherence.png)

**Dekking**: De beelden in de training moeten voldoende uiteenlopend zijn. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat de Experience Manager leert zich te richten op de juiste dingen. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen.

Neem voor het vervolgkeuzemodel ** van het label bijvoorbeeld meer trainingsafbeeldingen op, vergelijkbaar met de gemarkeerde afbeelding hieronder, zodat de service vergelijkbare afbeeldingen nauwkeuriger kan identificeren tijdens het labelen.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/coverage_1.png)

**Vervorming/obstructie**: De dienst rijdt beter op beelden die minder afleiding hebben (vooraanstaande achtergronden, niet-verwante begeleiding, zoals voorwerpen/personen met het hoofdonderwerp).

Voor de tag *casual-shoe* is de tweede afbeelding bijvoorbeeld geen goede trainingskandidaat.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/distraction.png)

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. For example, for tags, such as `raincoat` and `model-side-view`, add both the tags on the eligible asset before including it for training.

![Illustratieve afbeeldingen ter illustratie van de richtlijnen voor training](/help/assets/assets/do-not-localize/completeness.png)

>[!NOTE]
>
>Of de Smart Content Service uw tags kan trainen en deze op andere afbeeldingen kan toepassen, hangt af van de kwaliteit van de afbeeldingen die u voor de training gebruikt. Voor de beste resultaten raadt Adobe u aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

### Periodieke training {#periodic-training}

U kunt de Slimme Dienst van de Inhoud toelaten om periodiek op de activa en bijbehorende markeringen binnen een omslag te trainen. Open de [!UICONTROL Properties] pagina van uw elementenmap, selecteer deze **[!UICONTROL Enable Smart Tags]** onder het **[!UICONTROL Details]** tabblad en sla de wijzigingen op.

![enable_smart_tags](assets/enable_smart_tags.png)

Als deze optie voor een map is geselecteerd, [!DNL Experience Manager] wordt automatisch een trainingsworkflow uitgevoerd om de Smart Content Service te trainen op de mappenelementen en de bijbehorende tags. Standaard wordt de trainingsworkflow wekelijks om 12:30 uur uitgevoerd op zaterdag.

### Opleiding op aanvraag {#on-demand-training}

U kunt de Slimme Dienst van de Inhoud wanneer vereist van de console van het Werkschema trainen.

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL Smart Tags Training]** workflow and then click **[!UICONTROL Start Workflow]** from the toolbar.
1. Blader in het **[!UICONTROL Run Workflow]** dialoogvenster naar de payload-map met de gecodeerde elementen voor het trainen van de service.
1. Geef een titel op voor de workflow en voeg een opmerking toe. Klik vervolgens op **[!UICONTROL Run]**. De elementen en tags worden ter training aangeboden.

   ![workflow_dialog](assets/workflow_dialog.png)

>[!NOTE]
>
>Nadat de middelen in een map zijn verwerkt voor training, worden alleen de gewijzigde middelen verwerkt in volgende trainingscycli.

### Trainingsrapporten weergeven {#viewing-training-reports}

Om te controleren of de Slimme Dienst van de Inhoud op uw markeringen in de trainingsreeks activa wordt getraind, herzie het rapport van de opleidingswerkstroom van de console van Rapporten.

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]**.
1. In the **[!UICONTROL Asset Reports]** page, click **[!UICONTROL Create]**.
1. Select the **[!UICONTROL Smart Tags Training]** report, and then click **[!UICONTROL Next]** from the toolbar.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Then, click **[!UICONTROL Create]** from the toolbar.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op de werkbalk om het rapport weer te geven. **[!UICONTROL View]**
1. Bekijk de details van het rapport.

   Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de Smart Content Service is getraind voor de tag. Een gele kleur geeft aan dat de service niet volledig is getraind voor een bepaalde tag. Voeg in dit geval meer afbeeldingen met de desbetreffende tag toe en voer de trainingsworkflow uit om de service volledig op de tag te trainen.

   Als dit rapport uw tags niet bevat, voert u de trainingsworkflow voor deze tags opnieuw uit.

1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** de werkbalk. Het rapport wordt gedownload als een Microsoft Excel-spreadsheet.

## Beperkingen {#limitations}

* Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de Smart Content Service heeft de volgende beperkingen:

   * Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
   * Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
   * Tags worden ondersteund in de landinstellingen die worden ondersteund in. [!DNL Experience Manager] Zie Opmerkingen bij de release [Smart Content Services voor een lijst met talen](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/smart-content-service-release-notes.html).

* Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u de optie [!DNL Assets] Zoeken (full-text zoeken). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!MORELIKETHIS]
>
>* [Overzicht van slimme tags en hoe deze kunnen worden getraind](enhanced-smart-tags.md)
>* [Videozelfstudie over slimme tags](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html)

