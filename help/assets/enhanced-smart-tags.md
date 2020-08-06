---
title: Verbeterde slimme tags
description: Verbeterde slimme tags
contentOwner: AG
translation-type: tm+mt
source-git-commit: 892237699a4027e7dab406fd620cac220aa8b88b
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 8%

---


# Verbeterde slimme tags {#enhanced-smart-tags}

## Overzicht van verbeterde slimme tags {#overview-of-enhanced-smart-tags}

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar digitale activa van een bepaalde klasse te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u ze gemakkelijk herkennen en ophalen door zoekopdrachten op basis van tags.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren van digitale activa die op bedrijfstaxonomie worden gebaseerd hen op de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen.

Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer afbeeldingen van verschillende modellen worden doorzocht om een promotiecampagne te ontwerpen.

Als u wilt dat de Smart Content Service de juiste tags toepast, moet u deze trainen om uw taxonomie te herkennen. Als u de service wilt trainen, moet u eerst een set elementen en tags beheren die deze elementen het beste beschrijven. Pas deze tags toe op de middelen en voer een trainingsworkflow uit om de service te helpen leren.

Nadat een tag is opgeleid en gereed, kan de service deze tags nu toepassen op elementen via een workflow voor labelen.

Op de achtergrond gebruikt de Smart Content Service het Adobe Sensei AI-framework om het algoritme voor imageherkenning op te leiden voor uw tagstructuur en bedrijfskatonomie. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen.

Smart Content Service is een cloudservice die wordt gehost op Adobe I/O. Om het binnen te gebruiken [!DNL Adobe Experience Manager], moet de systeembeheerder uw [!DNL Experience Manager] plaatsing met Adobe I/O integreren.

Samenvattend, zijn hier de belangrijkste stappen om de Slimme Dienst van de Inhoud te gebruiken:

* Onboarding
* Elementen en labels controleren (taxonomidefinitie)
* De Smart Content Service trainen
* Automatisch labelen

![stroomschema](assets/flowchart.gif)

## Vereisten {#prerequisites}

Voordat u de service Slimme inhoud kunt gebruiken, moet u het volgende doen om een integratie in de Adobe I/O te maken:

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* De service Smart Content Service is ingeschakeld voor uw organisatie.

## Onboarding {#onboarding}

The Smart Content Service is available for purchase as an add-on to [!DNL Experience Manager]. Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar Adobe I/O.

De beheerder kan de verbinding volgen om de Slimme Dienst van de Inhoud met te integreren [!DNL Experience Manager]. Om de dienst met te integreren, zie [!DNL Experience Manager Assets]Vorm Slimme Markeringen [](config-smart-tagging.md).

Het instapproces is volledig wanneer de beheerder de dienst vormt en gebruikers binnen toevoegt [!DNL Experience Manager].

>[!NOTE]
>
>Zie [!DNL Experience Manager] Slimme tags [als u versie](https://helpx.adobe.com/experience-manager/6-3/assets/using/touch-ui-smart-tags.html)6.3 of lager gebruikt en coderingsservice voor uw elementen nodig hebt. Slimme tags maken geen gebruik van de nieuwste AI-mogelijkheden en zijn daarom minder nauwkeurig dan de verbeterde service voor slimme tags.

## Elementen en tags controleren {#reviewing-assets-and-tags}

Nadat u aan boord wordt genomen, is het eerste wat u wilt doen een reeks markeringen identificeren die deze beelden in de context van uw zaken het best beschrijven.

Hierna kunt u afbeeldingen bekijken om een set afbeeldingen te identificeren die het beste bij uw product passen voor een bepaalde zakelijke behoefte. Zorg ervoor dat de elementen in de beheerde set voldoen aan de trainingsrichtlijnen [voor](smart-tags-training-guidelines.md)Smart Content Service.

Voeg de elementen toe aan een map en pas de tags toe op elk element vanaf de eigenschappenpagina. Voer vervolgens de trainingsworkflow uit op deze map. Met de gekromde set elementen kan de Smart Content Service effectief meer elementen trainen met behulp van uw taxonomidefinities.

>[!NOTE]
>
>1. Opleiding is een onherroepelijk proces. Adobe raadt u aan de tags in de gekromde set elementen te controleren voordat u de Smart Content Service op de tags informeert.
>1. Zie de trainingsrichtlijnen voor [](smart-tags-training-guidelines.md)Smart Content Service voordat u gaat trainen voor een tag.
>1. Wanneer u de Slimme Dienst van de Inhoud voor het eerst opleidt, adviseert Adobe dat u het op minstens twee verschillende markeringen opleidt.


## De Smart Content Service trainen {#training-the-smart-content-service}

Als u wilt dat de Smart Content Service uw bedrijfskrionomie herkent, voert u deze uit op een reeks elementen die al tags bevatten die relevant zijn voor uw bedrijf. Na de training kan de service dezelfde taxonomie toepassen op een vergelijkbare set activa.

U kunt de service meerdere keren trainen om de service beter in staat te stellen relevante tags toe te passen. Voer na elke trainingscyclus een labelworkflow uit en controleer of uw elementen correct zijn gecodeerd.

U kunt de Slimme Dienst van de Inhoud periodiek of op vereiste basis trainen.

>[!NOTE]
>
>De trainingsworkflow wordt alleen uitgevoerd voor mappen.

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

## Elementen automatisch labelen {#tagging-assets-automatically}

Nadat u de Slimme Dienst van de Inhoud hebt opgeleid, kunt u het etiketteren werkschema teweegbrengen om aangewezen markeringen op een verschillende reeks gelijkaardige activa automatisch toe te passen.

U kunt de tagwerkstroom periodiek of telkens wanneer dat nodig is uitvoeren.

>[!NOTE]
>
>De tagwerkstroom wordt zowel op elementen als op mappen uitgevoerd.

### Periodieke tags {#periodic-tagging}

U kunt de Slimme Dienst van de Inhoud toelaten om activa binnen een omslag periodiek te etiketteren. Open de eigenschappenpagina van de elementenmap, selecteer deze **[!UICONTROL Enable Smart Tags]** onder het **[!UICONTROL Details]** tabblad en sla de wijzigingen op.

Als deze optie voor een map is geselecteerd, worden de middelen in de map automatisch gelabeld door de Smart Content Service. Standaard wordt de tagwerkstroom elke dag om 12.00 uur uitgevoerd.

### Tags op aanvraag {#on-demand-tagging}

U kunt de tagwerkstroom activeren door uw elementen direct te labelen:

* Workflowconsole
* Tijdlijn

>[!NOTE]
>
>Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.

#### Elementen labelen vanaf de workflowconsole {#tagging-assets-from-the-workflow-console}

1. In [!DNL Experience Manager] interface, go to **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL DAM Smart Tags Assets]** workflow and then click **[!UICONTROL Start Workflow]** from the toolbar.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Blader in het **[!UICONTROL Run Workflow]** dialoogvenster naar de payload-map met elementen waarop u de tags automatisch wilt toepassen.
1. Geef een titel voor de workflow en een optionele opmerking op. Klik op **[!UICONTROL Run]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gelabeld. Zie Slimme tags [beheren voor meer informatie](managing-smart-tags.md).

#### Elementen labelen vanaf de tijdlijn {#tagging-assets-from-the-timeline}

1. Selecteer in de [!DNL Assets] gebruikersinterface de map met elementen of specifieke elementen waarop u slimme tags wilt toepassen.
1. Open vanuit de linkerbovenhoek de **[!UICONTROL Timeline]** aanwijzer.
1. Open acties onder aan de linkerzijbalk en klik op **[!UICONTROL Start Workflow]**.

   ![start_workflow](assets/start_workflow.png)

1. Selecteer de **[!UICONTROL DAM Smart Tag Assets]** workflow en geef een titel op voor de workflow.
1. Klik op **[!UICONTROL Start]**. De workflow past de labels toe op elementen. Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gelabeld. Zie Slimme tags [beheren voor meer informatie](managing-smart-tags.md).

>[!NOTE]
>
>In de volgende coderingscycli worden alleen de gewijzigde elementen opnieuw gecodeerd met nieuw opgeleide tags. Zelfs ongewijzigde elementen worden echter gecodeerd als de ruimte tussen de laatste en huidige coderingscycli voor de coderingsworkflow meer dan 24 uur bedraagt. Voor workflows met periodieke labels worden ongewijzigde elementen gecodeerd wanneer de tijdruimte langer is dan zes maanden.
