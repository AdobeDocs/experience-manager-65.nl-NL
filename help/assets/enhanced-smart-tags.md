---
title: Verbeterde slimme tags
description: Verbeterde slimme tags
contentOwner: AG
feature: Smart Tags, Search
role: User
exl-id: 5eff4a0f-30b1-4753-ad0b-002656eed972
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 5aff321eb52c97e076c225b67c35e9c6d3371154
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# Slimme tags begrijpen, toepassen en beheren {#enhanced-smart-tags}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/smart-tags.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar digitale activa van een bepaalde klasse te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt gecontroleerd, worden de elementen gemakkelijk geïdentificeerd en opgehaald.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren van digitale activa die op bedrijfstaxonomie worden gebaseerd hen op de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen.

Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer afbeeldingen van verschillende modellen worden doorzocht om een promotiecampagne te ontwerpen.

Als u wilt dat de Smart Content Service de juiste tags toepast, moet u deze trainen om uw taxonomie te herkennen. Als u de service wilt trainen, moet u eerst een set elementen en tags beheren die deze elementen het beste beschrijven. Om de dienst te helpen leren, pas deze markeringen op de activa toe en stel een opleidingswerkschema in werking.

Nadat een tag is opgeleid en gereed, kan de service deze tags nu toepassen op elementen via een workflow voor labelen.

Op de achtergrond gebruikt de Smart Content Service het Adobe Sensei AI-framework om het algoritme voor imageherkenning op te leiden voor uw tagstructuur en bedrijfskatonomie. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen.

Smart Content Service is een cloudservice die wordt gehost op [!DNL Adobe Developer Console] . Als u deze toepassing wilt gebruiken in [!DNL Adobe Experience Manager] , moet de systeembeheerder de [!DNL Experience Manager] implementatie integreren met [!DNL Adobe Developer Console] .

Samenvattend, zijn hier de belangrijkste stappen om de Slimme Dienst van de Inhoud te gebruiken:

* Onboarding
* Elementen en labels controleren (taxonomidefinitie)
* De Smart Content Service trainen
* Automatisch labelen

![ Stroomschema ](assets/flowchart.gif)

## Vereisten en ondersteunde indelingen {#prerequisites}

Voordat u de service Slimme inhoud kunt gebruiken, moet u het volgende doen om een integratie te maken op [!DNL Adobe Developer Console] :

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* Schakel de service Smart Content Service voor uw organisatie in.
* Als u Smart Content Services Base Package wilt toevoegen aan een implementatie, moet u [!DNL Adobe Experience Manager Sites] Base Package en [!DNL Assets] add-on licentie geven.

De service past slimme tags toe op elementen van de volgende MIME-typen:

* `image/jpeg`
* `image/tiff`
* `image/png`
* `image/bmp`
* `image/gif`
* `image/pjpeg`
* `image/x-portable-anymap`
* `image/x-portable-bitmap`
* `image/x-portable-graymap`
* `image/x-portable-pixmap`
* `image/x-rgb`
* `image/x-xbitmap`
* `image/x-xpixmap`
* `image/x-icon`
* `image/photoshop`
* `image/x-photoshop`
* `image/psd`
* `image/vnd.adobe.photoshop`

De service past slimme tags toe op elementuitvoeringen van de volgende MIME-typen:

* `image/jpeg`
* `image/pjpeg`
* `image/png`

## Onboarding {#onboarding}

De service Slimme inhoud kan worden aangeschaft als invoegtoepassing voor [!DNL Experience Manager] . Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar [!DNL Adobe I/O] .

De beheerder kan de koppeling volgen om de service Slimme inhoud te integreren met [!DNL Experience Manager] . Om de dienst met [!DNL Experience Manager Assets] te integreren, zie [ Slimme Markeringen ](config-smart-tagging.md) vormen.

Het instapproces is voltooid wanneer de beheerder de service configureert en gebruikers toevoegt in [!DNL Experience Manager] .

## Elementen en tags controleren {#reviewing-assets-and-tags}

Nadat u aan boord bent, is het eerste wat u wilt doen een reeks markeringen identificeren die deze beelden in de context van uw zaken het best beschrijven.

Hierna kunt u afbeeldingen bekijken om een set afbeeldingen te identificeren die het beste bij uw product passen voor een bepaalde zakelijke behoefte. Zorg ervoor dat de activa in uw gebogen reeks met [ Slimme de opleidingsrichtlijnen van de Dienst van de Inhoud ](/help/assets/config-smart-tagging.md#training-the-smart-content-service) in overeenstemming zijn.

Voeg de elementen toe aan een map en pas de tags toe op elk element vanaf de eigenschappenpagina. Voer vervolgens de trainingsworkflow uit op deze map. Met de gekromde set elementen kan de Smart Content Service effectief meer elementen trainen met behulp van uw taxonomidefinities.

>[!NOTE]
>
>1. Opleiding is een onherroepelijk proces. Adobe raadt u aan de tags in de gekromde set elementen te controleren voordat u de Smart Content Service op de tags informeert.
>1. Vóór opleiding voor een markering, zie [ Slimme de opleidingsrichtlijnen van de Dienst van de Inhoud ](/help/assets/config-smart-tagging.md#training-the-smart-content-service).
>1. Wanneer u de Slimme Dienst van de Inhoud voor het eerst opleidt, adviseert de Adobe dat u het op minstens twee verschillende markeringen opleidt.

## [!DNL Experience Manager] Zoekresultaten met slimme tags begrijpen {#understandsearch}

Standaard worden in [!DNL Experience Manager] zoektermen gecombineerd met een `AND` -component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, voegt u een extra `OR` -component toe om te zoeken naar zoektermen die betrekking hebben op slimme tags. Zoek bijvoorbeeld naar `woman running` . Assets met alleen het trefwoord `woman` of alleen het trefwoord `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. In een dergelijke zoekopdracht wordt echter een element weergegeven dat is gelabeld met `woman` of `running` met slimme tags. De zoekresultaten zijn dus een combinatie van:

* Assets met `woman` en `running` trefwoorden in de metagegevens.

* Assets smart wordt getagd met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. Komt overeen met `woman running` in de verschillende metagegevensvelden.
1. Komt overeen met `woman running` in slimme tags.
1. Komt overeen met `woman` of `running` in slimme tags.

>[!CAUTION]
>
>Als de Lucene-indexering uit [!DNL Adobe Experience Manager] is uitgevoerd, werkt de zoekopdracht op basis van slimme tags niet zoals u had verwacht.

## Elementen automatisch labelen {#tagging-assets-automatically}

Nadat u de Slimme Dienst van de Inhoud hebt opgeleid, kunt u het etiketteren werkschema teweegbrengen om aangewezen markeringen op een verschillende reeks gelijkaardige activa automatisch toe te passen.

U kunt de tagwerkstroom periodiek of telkens wanneer dat nodig is uitvoeren.

>[!NOTE]
>
>De tagwerkstroom wordt zowel op elementen als op mappen uitgevoerd.

### Periodieke tags {#periodic-tagging}

U kunt de Slimme Dienst van de Inhoud toelaten om activa binnen een omslag periodiek te etiketteren. Open de eigenschappenpagina van de elementenmap, selecteer **[!UICONTROL Enable Smart Tags]** onder het tabblad **[!UICONTROL Details]** en sla de wijzigingen op.

Als deze optie voor een map is geselecteerd, worden de middelen in de map automatisch gelabeld door de Smart Content Service. Standaard wordt de tagwerkstroom elke dag om 12.00 uur uitgevoerd.

### Tags op aanvraag {#on-demand-tagging}

U kunt de tagwerkstroom vanuit de workflowconsole of vanuit de tijdlijn activeren om uw elementen ogenblikkelijk te labelen.

>[!NOTE]
>
>Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.

#### Elementen labelen vanaf de workflowconsole {#tagging-assets-from-the-workflow-console}

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL DAM Smart Tags Assets]** workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.

   ![ dam_smart_tag_workflow ](assets/dam_smart_tag_workflow.png)

1. Blader in het dialoogvenster **[!UICONTROL Run Workflow]** naar de payload-map met elementen waarop u de tags automatisch wilt toepassen.
1. Geef een titel voor de workflow en een optionele opmerking op. Klik op **[!UICONTROL Run]**.

   ![ tagging_dialog ](assets/tagging_dialog.png)

   Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gecodeerd.

#### Elementen labelen vanaf de tijdlijn {#tagging-assets-from-the-timeline}

1. Selecteer in de gebruikersinterface van [!DNL Assets] de map met elementen of specifieke elementen waarop u slimme tags wilt toepassen.
1. Open vanuit de linkerbovenhoek de **[!UICONTROL Timeline]** .
1. Open handelingen onder aan de linkerzijbalk en klik op **[!UICONTROL Start Workflow]** .

   ![ start_workflow ](assets/start_workflow.png)

1. Selecteer de **[!UICONTROL DAM Smart Tag Assets]** -workflow en geef een titel op voor de workflow.
1. Klik op **[!UICONTROL Start]**. De workflow past labels toe op de elementen. Als u wilt controleren of de Smart Content Service uw elementen correct heeft gelabeld, navigeert u naar de map met middelen en controleert u de tags.

>[!NOTE]
>
>In de volgende coderingscycli worden alleen de gewijzigde elementen opnieuw gecodeerd met zojuist opgeleide tags. Zelfs ongewijzigde elementen worden echter gecodeerd als de ruimte tussen de laatste en huidige coderingscycli voor de coderingsworkflow meer dan 24 uur bedraagt. Voor workflows voor periodieke labeling worden ongewijzigde elementen gecodeerd wanneer het tijdsverschil langer is dan zes maanden.

## De toegepaste slimme tags curven of matigen {#manage-smart-tags}

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkafbeeldingen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags naar afbeeldingen verder verfijnen door ervoor te zorgen dat de afbeelding in de zoekresultaten wordt weergegeven voor de meest relevante tags. In feite wordt hiermee de kans dat niet-verwante afbeeldingen in zoekresultaten worden weergegeven, verkleind.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie ervan voor een afbeelding te vergroten. Als u een tag voor een afbeelding promoot, neemt de kans toe dat de afbeelding in de zoekresultaten wordt weergegeven wanneer de desbetreffende tag wordt doorzocht.

1. Zoek in het zoekvak naar elementen op basis van een tag als een trefwoord.
1. Als u een afbeelding wilt identificeren die u niet relevant vindt voor uw zoekopdracht, bekijkt u de zoekresultaten.
1. Selecteer de afbeelding en klik op **[!UICONTROL Manage Tags]** op de werkbalk.
1. Controleer de tags op de pagina **[!UICONTROL Manage Tags]** . Als u niet wilt dat de afbeelding wordt doorzocht op basis van een specifiek label, selecteert u het label en klikt u op **[!UICONTROL Delete]** op de werkbalk. U kunt ook op het symbool `x` klikken dat naast een tag wordt weergegeven.
1. Als u een hogere rang aan een tag wilt toewijzen, selecteert u de tag en klikt u op **[!UICONTROL Promote]** in de werkbalk. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]** .
1. Klik op **[!UICONTROL Save]** en klik vervolgens op **[!UICONTROL OK]**
1. Navigeer naar de pagina **[!UICONTROL Properties]** voor de afbeelding. Let erop dat de code die u hebt bevorderd relevanter wordt toegewezen en eerder in de zoekresultaten wordt weergegeven.

## Tips en beperkingen {#tips-best-practices-limitations}

* Gebruik de meest geschikte afbeeldingen om het model op te leiden. De training kan niet worden teruggezet of het trainingsmodel kan niet worden verwijderd. De nauwkeurigheid van de tags is afhankelijk van de huidige training, dus doe dit zorgvuldig.
* Het gebruik van Smart Content Services is beperkt tot maximaal 2 miljoen getagde afbeeldingen per jaar. Alle gedupliceerde afbeeldingen die zijn verwerkt en getagd, worden allemaal geteld als een gecodeerde afbeelding.
* Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.
* Slimme tags werken alleen voor PNG- en JPG-afbeeldingsindelingen. Dus ondersteunde elementen met uitvoeringen die in deze twee indelingen zijn gemaakt, worden gelabeld met slimme tags.

>[!MORELIKETHIS]
>
>* [ Overzicht en hoe te om Slimme Markeringen ](enhanced-smart-tags.md) te trainen
>* [ vorm slimme het etiketteren ](config-smart-tagging.md)
>* [ het Oplossen van problemen slimme markeringen voor geloofsbrieven OAuth ](config-oauth.md)
>* [ Videozelfstudie over slimme markeringen ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html?lang=nl-NL)
