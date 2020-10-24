---
title: Verbeterde slimme tags
description: Verbeterde slimme tags
contentOwner: AG
translation-type: tm+mt
source-git-commit: e124025295f29d6f3999dc52467301d48bceee75
workflow-type: tm+mt
source-wordcount: '1489'
ht-degree: 1%

---


# Slimme tags begrijpen, toepassen en beheren {#enhanced-smart-tags}

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
* Het slimme Pakket van de Diensten van de Basis van de Inhoud kan slechts aan een plaatsing worden toegevoegd waar een [!DNL Sites] Pakket van de Basis en [!DNL Assets] toe:voegen-on vergunning hebben gekregen.

## Onboarding {#onboarding}

The Smart Content Service is available for purchase as an add-on to [!DNL Experience Manager]. Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar Adobe I/O.

De beheerder kan de verbinding volgen om de Slimme Dienst van de Inhoud met te integreren [!DNL Experience Manager]. Om de dienst met te integreren, zie [!DNL Experience Manager Assets]Vorm Slimme Markeringen [](config-smart-tagging.md).

Het instapproces is volledig wanneer de beheerder de dienst vormt en gebruikers binnen toevoegt [!DNL Experience Manager].

>[!NOTE]
>
>Zie [!DNL Experience Manager] Slimme tags [als u versie](https://helpx.adobe.com/experience-manager/6-3/assets/using/touch-ui-smart-tags.html)6.3 of lager gebruikt en coderingsservice voor uw elementen nodig hebt. Slimme tags maken geen gebruik van de nieuwste AI-mogelijkheden en zijn daarom minder nauwkeurig dan de verbeterde service voor slimme tags.

## Elementen en tags controleren {#reviewing-assets-and-tags}

Nadat u aan boord bent, is het eerste wat u wilt doen een reeks markeringen identificeren die deze beelden in de context van uw zaken het best beschrijven.

Hierna kunt u afbeeldingen bekijken om een set afbeeldingen te identificeren die het beste bij uw product passen voor een bepaalde zakelijke behoefte. Zorg ervoor dat de elementen in de beheerde set voldoen aan de trainingsrichtlijnen [voor](/help/assets/config-smart-tagging.md#training-the-smart-content-service)Smart Content Service.

Voeg de elementen toe aan een map en pas de tags toe op elk element vanaf de eigenschappenpagina. Voer vervolgens de trainingsworkflow uit op deze map. Met de gekromde set elementen kan de Smart Content Service effectief meer elementen trainen met behulp van uw taxonomidefinities.

>[!NOTE]
>
>1. Opleiding is een onherroepelijk proces. Adobe raadt u aan de tags in de gekromde set elementen te controleren voordat u de Smart Content Service op de tags informeert.
>1. Zie de trainingsrichtlijnen voor [](/help/assets/config-smart-tagging.md#training-the-smart-content-service)Smart Content Service voordat u gaat trainen voor een tag.
>1. Wanneer u de Slimme Dienst van de Inhoud voor het eerst opleidt, adviseert Adobe dat u het op minstens twee verschillende markeringen opleidt.


## De [!DNL Experience Manager] zoekresultaten begrijpen met slimme tags {#understandsearch}

Standaard combineert [!DNL Experience Manager] zoeken de zoektermen met een `AND` component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, voegt u een extra `OR` component toe om te zoeken naar zoektermen in de lijst, worden slimme tags toegepast. For example, consider searching for `woman running`. Elementen met alleen `woman` of alleen `running` trefwoorden in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat is gelabeld met slimme tags `woman` `running` of met slimme tags, wordt echter weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* elementen met `woman` en `running` trefwoorden in de metagegevens.

* elementen die zijn gelabeld met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. komt overeen met `woman running` de waarden in de verschillende metagegevensvelden.
1. overeenkomende waarden `woman running` in slimme tags.
1. overeenkomende met `woman` of van `running` in slimme tags.

>[!CAUTION]
>
>Als het indexeren van Lucene uit [!DNL Adobe Experience Manager] toen wordt gedaan werkt het onderzoek dat op slimme markeringen wordt gebaseerd niet zoals verwacht.

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

U kunt de tagwerkstroom vanuit de workflowconsole of vanuit de tijdlijn activeren om uw elementen ogenblikkelijk te labelen.

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

   Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gelabeld.

#### Elementen labelen vanaf de tijdlijn {#tagging-assets-from-the-timeline}

1. Selecteer in de [!DNL Assets] gebruikersinterface de map met elementen of specifieke elementen waarop u slimme tags wilt toepassen.
1. Open vanuit de linkerbovenhoek de **[!UICONTROL Timeline]** aanwijzer.
1. Open acties onder aan de linkerzijbalk en klik op **[!UICONTROL Start Workflow]**.

   ![start_workflow](assets/start_workflow.png)

1. Selecteer de **[!UICONTROL DAM Smart Tag Assets]** workflow en geef een titel op voor de workflow.
1. Klik op **[!UICONTROL Start]**. De workflow past de labels toe op elementen. Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gelabeld.

>[!NOTE]
>
>In de volgende coderingscycli worden alleen de gewijzigde elementen opnieuw gecodeerd met nieuw opgeleide tags. Zelfs ongewijzigde elementen worden echter gecodeerd als de ruimte tussen de laatste en huidige coderingscycli voor de coderingsworkflow meer dan 24 uur bedraagt. Voor workflows met periodieke labels worden ongewijzigde elementen gecodeerd wanneer de tijdruimte langer is dan zes maanden.

## De toegepaste slimme tags curven of matigen {#manage-smart-tags}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkafbeeldingen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags naar afbeeldingen verder verfijnen door ervoor te zorgen dat de afbeelding in de zoekresultaten wordt weergegeven voor de meest relevante tags. In feite wordt hiermee de kans dat niet-verwante afbeeldingen in zoekresultaten worden weergegeven, verkleind.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie ervan voor een afbeelding te vergroten. Door een tag voor een afbeelding te promoten, neemt de kans toe dat de afbeelding in de zoekresultaten wordt weergegeven wanneer een zoekopdracht op basis van de desbetreffende tag wordt uitgevoerd.

1. Zoek in het vak Onderzoek naar elementen op basis van een tag.
1. Inspect de zoekresultaten om een afbeelding te identificeren die je niet relevant vindt voor je zoekopdracht.
1. Select the image, and click **[!UICONTROL Manage Tags]** from the toolbar.
1. Controleer de tags op de **[!UICONTROL Manage Tags]** pagina. Als u niet wilt dat de afbeelding wordt doorzocht op basis van een specifiek label, selecteert u het label en klikt u vervolgens op **[!UICONTROL Delete]** de werkbalk. U kunt ook op het `x` symbool naast een tag klikken.
1. Als u een hogere rang aan een tag wilt toewijzen, selecteert u de tag en klikt u **[!UICONTROL Promote]** op de werkbalk. De tag die u promoot, wordt verplaatst naar de **[!UICONTROL Tags]** sectie.
1. Click **[!UICONTROL Save]** and then click **[!UICONTROL OK]**
1. Navigeer naar de **[!UICONTROL Properties]** pagina voor de afbeelding. Let erop dat de code die u hebt bevorderd relevanter wordt toegewezen en eerder in de zoekresultaten wordt weergegeven.

## Tips en beperkingen {#tips-best-practices-limitations}

* Het gebruik van Smart Content Services is beperkt tot maximaal 2 miljoen getagde afbeeldingen per jaar. Alle gedupliceerde afbeeldingen die zijn verwerkt en getagd, worden allemaal geteld als een gecodeerde afbeelding.
* Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.
