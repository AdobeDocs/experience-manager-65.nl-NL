---
title: Verbeterde slimme tags
description: Verbeterde slimme tags
contentOwner: AG
translation-type: tm+mt
source-git-commit: 788a66d5732f0a120de6b80da69e9cf81f998667
workflow-type: tm+mt
source-wordcount: '1561'
ht-degree: 1%

---


# Slimme tags {#enhanced-smart-tags} begrijpen, toepassen en beheren

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van door taxonomie gecontroleerde woordenschat in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar digitale activa van een bepaalde klasse te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt gecontroleerd, worden de elementen gemakkelijk geïdentificeerd en opgehaald.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren van digitale activa die op bedrijfstaxonomie worden gebaseerd hen op de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen.

Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer afbeeldingen van verschillende modellen worden doorzocht om een promotiecampagne te ontwerpen.

Als u wilt dat de Smart Content Service de juiste tags toepast, moet u deze trainen om uw taxonomie te herkennen. Als u de service wilt trainen, moet u eerst een set elementen en tags beheren die deze elementen het beste beschrijven. Om de dienst te helpen leren, pas deze markeringen op de activa toe en stel een opleidingswerkschema in werking.

Nadat een tag is opgeleid en gereed, kan de service deze tags nu toepassen op elementen via een workflow voor labelen.

Op de achtergrond gebruikt de Smart Content Service het Adobe Sensei AI-framework om het algoritme voor imageherkenning op te leiden voor uw tagstructuur en bedrijfskatonomie. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen.

Smart Content Service is een cloudservice die wordt gehost op [!DNL Adobe Developer Console]. Om het in [!DNL Adobe Experience Manager] te gebruiken, moet de systeembeheerder uw [!DNL Experience Manager] plaatsing met [!DNL Adobe Developer Console] integreren.

Samenvattend, zijn hier de belangrijkste stappen om de Slimme Dienst van de Inhoud te gebruiken:

* Onboarding
* Elementen en labels controleren (taxonomidefinitie)
* De Smart Content Service trainen
* Automatisch labelen

![Stroomdiagram](assets/flowchart.gif)

## Vereisten en ondersteunde indelingen {#prerequisites}

Voordat u de service Slimme inhoud kunt gebruiken, moet u het volgende doen om een integratie te maken op [!DNL Adobe Developer Console]:

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* Schakel de service Smart Content Service voor uw organisatie in.
* Om het Slimme Pakket van de Basis van de Diensten van de Inhoud aan een plaatsing toe te voegen, vergunning [!DNL Adobe Experience Manager Sites] het Pakket van de Basis en [!DNL Assets] toe:voegen-on.

De service past slimme tags toe op elementen van de volgende MIME-typen:

* image/jpeg
* image/tiff
* image/png
* image/bmp
* image/gif
* image/pjpeg
* image/x-portable-anymap
* image/x-portable-bitmap
* image/x-portable-graymap
* image/x-portable-pixmap
* image/x-rgb
* image/x-xbitmap
* image/x-xpixmap
* image/x-icon
* image/photoshop
* image/x-photoshop
* image/psd
* image/vnd.adobe.photoshop

De service past slimme tags toe op elementuitvoeringen van de volgende MIME-typen:

* image/jpeg
* image/pjpeg
* image/png

## Onboarding {#onboarding}

De Smart Content Service kan worden aangeschaft als een invoegtoepassing voor [!DNL Experience Manager]. Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar [!DNL Adobe I/O].

De beheerder kan de verbinding volgen om de Slimme Dienst van de Inhoud met [!DNL Experience Manager] te integreren. Zie [Slimme tags configureren](config-smart-tagging.md) om de service te integreren met [!DNL Experience Manager Assets].

Het instapproces is voltooid wanneer de beheerder de service configureert en gebruikers toevoegt in [!DNL Experience Manager].

>[!NOTE]
>
>Zie [Slimme tags](https://helpx.adobe.com/experience-manager/6-3/assets/using/touch-ui-smart-tags.html) als u [!DNL Experience Manager] 6.3 of een eerdere versie gebruikt en coderingsservice voor uw elementen nodig hebt. Slimme tags maken geen gebruik van de nieuwste AI-mogelijkheden en zijn daarom minder nauwkeurig dan de verbeterde service voor slimme tags.

## Elementen en tags controleren {#reviewing-assets-and-tags}

Nadat u aan boord bent, is het eerste wat u wilt doen een reeks markeringen identificeren die deze beelden in de context van uw zaken het best beschrijven.

Hierna kunt u afbeeldingen bekijken om een set afbeeldingen te identificeren die het beste bij uw product passen voor een bepaalde zakelijke behoefte. Zorg ervoor dat de elementen in uw gekromde set voldoen aan [trainingsrichtlijnen voor Smart Content Service](/help/assets/config-smart-tagging.md#training-the-smart-content-service).

Voeg de elementen toe aan een map en pas de tags toe op elk element vanaf de eigenschappenpagina. Voer vervolgens de trainingsworkflow uit op deze map. Met de gekromde set elementen kan de Smart Content Service effectief meer elementen trainen met behulp van uw taxonomidefinities.

>[!NOTE]
>
>1. Opleiding is een onherroepelijk proces. Adobe raadt u aan de tags in de gekromde set elementen te controleren voordat u de Smart Content Service op de tags informeert.
>1. Zie [Richtlijnen voor training voor Smart Content Service](/help/assets/config-smart-tagging.md#training-the-smart-content-service) voor training voor een tag.
>1. Wanneer u de Slimme Dienst van de Inhoud voor het eerst opleidt, adviseert Adobe dat u het op minstens twee verschillende markeringen opleidt.


## [!DNL Experience Manager] zoekresultaten begrijpen met slimme tags {#understandsearch}

Standaard worden bij het zoeken met [!DNL Experience Manager] de zoektermen gecombineerd met een `AND`-component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, voegt u een extra `OR`-component toe om een zoekterm te zoeken die verwant is aan de slimme tags. U kunt bijvoorbeeld zoeken naar `woman running`. Elementen met alleen het trefwoord `woman` of `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat is gelabeld met `woman` of `running` met behulp van slimme tags, wordt echter wel weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* Middelen met de trefwoorden `woman` en `running` in de metagegevens.

* Elementen die zijn getagd met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. Komt overeen met `woman running` in de verschillende metagegevensvelden.
1. Komt overeen met `woman running` in slimme tags.
1. Komt overeen met `woman` of `running` in slimme tags.

>[!CAUTION]
>
>Als het indexeren van Lucene uit [!DNL Adobe Experience Manager] wordt gedaan, dan werkt het onderzoek dat op slimme markeringen wordt gebaseerd niet zoals verwacht.

## Elementen automatisch labelen {#tagging-assets-automatically}

Nadat u de Slimme Dienst van de Inhoud hebt opgeleid, kunt u het etiketteren werkschema teweegbrengen om aangewezen markeringen op een verschillende reeks gelijkaardige activa automatisch toe te passen.

U kunt de tagwerkstroom periodiek of telkens wanneer dat nodig is uitvoeren.

>[!NOTE]
>
>De tagwerkstroom wordt zowel op elementen als op mappen uitgevoerd.

### Periodieke labels {#periodic-tagging}

U kunt de Slimme Dienst van de Inhoud toelaten om activa binnen een omslag periodiek te etiketteren. Open de eigenschappenpagina van de elementenmap, selecteer **[!UICONTROL Enable Smart Tags]** onder het tabblad **[!UICONTROL Details]** en sla de wijzigingen op.

Als deze optie voor een map is geselecteerd, worden de middelen in de map automatisch gelabeld door de Smart Content Service. Standaard wordt de tagwerkstroom elke dag om 12.00 uur uitgevoerd.

### Tags op aanvraag {#on-demand-tagging}

U kunt de tagwerkstroom vanuit de workflowconsole of vanuit de tijdlijn activeren om uw elementen ogenblikkelijk te labelen.

>[!NOTE]
>
>Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.

#### Elementen labelen vanaf de workflowconsole {#tagging-assets-from-the-workflow-console}

1. Ga in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL DAM Smart Tags Assets]**-workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Blader in het dialoogvenster **[!UICONTROL Run Workflow]** naar de payload-map met elementen waarop u de tags automatisch wilt toepassen.
1. Geef een titel voor de workflow en een optionele opmerking op. Klik op **[!UICONTROL Run]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gecodeerd.

#### Elementen labelen vanaf de tijdlijn {#tagging-assets-from-the-timeline}

1. Selecteer in de gebruikersinterface [!DNL Assets] de map met elementen of specifieke elementen waarop u slimme tags wilt toepassen.
1. Open in de linkerbovenhoek de **[!UICONTROL Timeline]**.
1. Open handelingen onder aan de linkerzijbalk en klik op **[!UICONTROL Start Workflow]**.

   ![start_workflow](assets/start_workflow.png)

1. Selecteer de **[!UICONTROL DAM Smart Tag Assets]** workflow en geef een titel op voor de workflow.
1. Klik op **[!UICONTROL Start]**. De workflow past labels toe op de elementen. Als u wilt controleren of de Smart Content Service uw elementen correct heeft gelabeld, navigeert u naar de map met middelen en controleert u de tags.

>[!NOTE]
>
>In de volgende coderingscycli worden alleen de gewijzigde elementen opnieuw gecodeerd met zojuist opgeleide tags. Zelfs ongewijzigde elementen worden echter gecodeerd als de ruimte tussen de laatste en huidige coderingscycli voor de coderingsworkflow meer dan 24 uur bedraagt. Voor workflows voor periodieke labeling worden ongewijzigde elementen gecodeerd wanneer het tijdsverschil langer is dan zes maanden.

## De toegepaste slimme tags {#manage-smart-tags} krommen of verkleinen

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkafbeeldingen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags naar afbeeldingen verder verfijnen door ervoor te zorgen dat de afbeelding in de zoekresultaten wordt weergegeven voor de meest relevante tags. In feite wordt hiermee de kans dat niet-verwante afbeeldingen in zoekresultaten worden weergegeven, verkleind.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie ervan voor een afbeelding te vergroten. Als u een tag voor een afbeelding promoot, neemt de kans toe dat de afbeelding in de zoekresultaten wordt weergegeven wanneer de desbetreffende tag wordt doorzocht.

1. Zoek in het zoekvak naar elementen op basis van een tag als een trefwoord.
1. Als u een afbeelding wilt identificeren die u niet relevant vindt voor uw zoekopdracht, bekijkt u de zoekresultaten.
1. Selecteer de afbeelding en klik op **[!UICONTROL Manage Tags]** op de werkbalk.
1. Reviseer de tags op de pagina **[!UICONTROL Manage Tags]**. Als u niet wilt dat de afbeelding wordt doorzocht op basis van een specifiek label, selecteert u het label en klikt u op **[!UICONTROL Delete]** op de werkbalk. U kunt ook op `x`-symbool naast een tag klikken.
1. Als u een hogere rangorde aan een tag wilt toewijzen, selecteert u de tag en klikt u op **[!UICONTROL Promote]** op de werkbalk. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]**.
1. Klik **[!UICONTROL Save]** en klik dan **[!UICONTROL OK]**
1. Navigeer naar de pagina **[!UICONTROL Properties]** voor de afbeelding. Let erop dat de code die u hebt bevorderd relevanter wordt toegewezen en eerder in de zoekresultaten wordt weergegeven.

## Tips en beperkingen {#tips-best-practices-limitations}

* Het gebruik van Smart Content Services is beperkt tot maximaal 2 miljoen getagde afbeeldingen per jaar. Alle gedupliceerde afbeeldingen die zijn verwerkt en getagd, worden allemaal geteld als een gecodeerde afbeelding.
* Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.
* Slimme tags werken alleen voor PNG- en JPG-afbeeldingsindelingen. Dus ondersteunde elementen met uitvoeringen die in deze twee indelingen zijn gemaakt, worden gelabeld met slimme tags.
