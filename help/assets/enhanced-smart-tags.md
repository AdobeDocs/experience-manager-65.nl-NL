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


# Slimme tags {#enhanced-smart-tags} begrijpen, toepassen en beheren

Organisaties die met digitale middelen te maken hebben, maken steeds vaker gebruik van een door taxonomie gecontroleerde woordenlijst in metagegevens van bedrijfsmiddelen. In wezen, omvat het een lijst van sleutelwoorden die de werknemers, de partners, en de klanten algemeen gebruiken om naar digitale activa van een bepaalde klasse te verwijzen en te zoeken. Door elementen te labelen met een woordenschat die door de taxonomie wordt bepaald, kunt u ze gemakkelijk herkennen en ophalen door zoekopdrachten op basis van tags.

Vergeleken met natuurlijke taalwoordenboeken, helpt het etiketteren van digitale activa die op bedrijfstaxonomie worden gebaseerd hen op de zaken van een bedrijf te richten en zorgt ervoor dat de meest relevante activa in onderzoeken verschijnen.

Een autofabrikant kan bijvoorbeeld autoafbeeldingen labelen met modelnamen, zodat alleen relevante afbeeldingen worden weergegeven wanneer afbeeldingen van verschillende modellen worden doorzocht om een promotiecampagne te ontwerpen.

Als u wilt dat de Smart Content Service de juiste tags toepast, moet u deze trainen om uw taxonomie te herkennen. Als u de service wilt trainen, moet u eerst een set elementen en tags beheren die deze elementen het beste beschrijven. Pas deze tags toe op de middelen en voer een trainingsworkflow uit om de service te helpen leren.

Nadat een tag is opgeleid en gereed, kan de service deze tags nu toepassen op elementen via een workflow voor labelen.

Op de achtergrond gebruikt de Smart Content Service het Adobe Sensei AI-framework om het algoritme voor imageherkenning op te leiden voor uw tagstructuur en bedrijfskatonomie. Deze inhoudsinfo wordt vervolgens gebruikt om relevante tags toe te passen op een andere set elementen.

Smart Content Service is een cloudservice die wordt gehost op Adobe I/O. Om het in [!DNL Adobe Experience Manager] te gebruiken, moet de systeembeheerder uw [!DNL Experience Manager] plaatsing met Adobe I/O integreren.

Samenvattend, zijn hier de belangrijkste stappen om de Slimme Dienst van de Inhoud te gebruiken:

* Onboarding
* Elementen en labels controleren (taxonomidefinitie)
* De Smart Content Service trainen
* Automatisch labelen

![stroomschema](assets/flowchart.gif)

## Vereisten {#prerequisites}

Voordat u de Smart Content Service kunt gebruiken, moet u het volgende doen om een integratie te maken in Adobe I/O:

* Een Adobe ID-account met beheerdersrechten voor de organisatie.
* De service Smart Content Service is ingeschakeld voor uw organisatie.
* Het pakket Smart Content Services Base mag alleen worden toegevoegd aan een implementatie waarbij een [!DNL Sites] Base Package en [!DNL Assets] add-on zijn gelicentieerd.

## Onboarding {#onboarding}

De Smart Content Service kan worden aangeschaft als een invoegtoepassing voor [!DNL Experience Manager]. Nadat u de aankoop hebt gedaan, wordt een e-mail verzonden naar de beheerder van uw organisatie met een koppeling naar Adobe I/O.

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

Standaard worden bij het zoeken met [!DNL Experience Manager] de zoektermen gecombineerd met een `AND`-component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, wordt een extra `OR`-component toegevoegd om een zoekterm in de lijst te zoeken, past u slimme tags toe. U kunt bijvoorbeeld zoeken naar `woman running`. Elementen met alleen het trefwoord `woman` of `running` in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat is gelabeld met `woman` of `running` met behulp van slimme tags, wordt echter wel weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* elementen met de trefwoorden `woman` en `running` in de metagegevens.

* elementen die zijn gelabeld met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. overeenkomend met `woman running` in de verschillende metagegevensvelden.
1. overeenkomsten van `woman running` in slimme markeringen.
1. overeenkomende met `woman` of `running` in slimme tags.

>[!CAUTION]
>
>Als de Lucene-indexering uit [!DNL Adobe Experience Manager] is uitgevoerd, werkt de zoekopdracht op basis van slimme tags niet zoals verwacht.

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

   Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gelabeld.

#### Elementen labelen vanaf de tijdlijn {#tagging-assets-from-the-timeline}

1. Selecteer in de gebruikersinterface [!DNL Assets] de map met elementen of specifieke elementen waarop u slimme tags wilt toepassen.
1. Open in de linkerbovenhoek de **[!UICONTROL Timeline]**.
1. Open handelingen onder aan de linkerzijbalk en klik op **[!UICONTROL Start Workflow]**.

   ![start_workflow](assets/start_workflow.png)

1. Selecteer de **[!UICONTROL DAM Smart Tag Assets]** workflow en geef een titel op voor de workflow.
1. Klik op **[!UICONTROL Start]**. De workflow past de labels toe op elementen. Navigeer naar de map met middelen en controleer de tags om te controleren of de Smart Content Service uw elementen correct heeft gelabeld.

>[!NOTE]
>
>In de volgende coderingscycli worden alleen de gewijzigde elementen opnieuw gecodeerd met nieuw opgeleide tags. Zelfs ongewijzigde elementen worden echter gecodeerd als de ruimte tussen de laatste en huidige coderingscycli voor de coderingsworkflow meer dan 24 uur bedraagt. Voor workflows met periodieke labels worden ongewijzigde elementen gecodeerd wanneer de tijdruimte langer is dan zes maanden.

## De toegepaste slimme tags {#manage-smart-tags} krommen of verkleinen

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkafbeeldingen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags naar afbeeldingen verder verfijnen door ervoor te zorgen dat de afbeelding in de zoekresultaten wordt weergegeven voor de meest relevante tags. In feite wordt hiermee de kans dat niet-verwante afbeeldingen in zoekresultaten worden weergegeven, verkleind.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie ervan voor een afbeelding te vergroten. Door een tag voor een afbeelding te promoten, neemt de kans toe dat de afbeelding in de zoekresultaten wordt weergegeven wanneer een zoekopdracht op basis van de desbetreffende tag wordt uitgevoerd.

1. Zoek in het vak Onderzoek naar elementen op basis van een tag.
1. Inspect de zoekresultaten om een afbeelding te identificeren die je niet relevant vindt voor je zoekopdracht.
1. Selecteer de afbeelding en klik op **[!UICONTROL Manage Tags]** op de werkbalk.
1. Controleer de tags op de pagina **[!UICONTROL Manage Tags]**. Als u niet wilt dat de afbeelding wordt doorzocht op basis van een specifiek label, selecteert u het label en klikt u op **[!UICONTROL Delete]** op de werkbalk. U kunt ook op `x`-symbool naast een tag klikken.
1. Als u een hogere rangorde aan een tag wilt toewijzen, selecteert u de tag en klikt u op **[!UICONTROL Promote]** op de werkbalk. De tag die u promoot, wordt verplaatst naar de sectie **[!UICONTROL Tags]**.
1. Klik **[!UICONTROL Save]** en klik dan **[!UICONTROL OK]**
1. Navigeer naar de pagina **[!UICONTROL Properties]** voor de afbeelding. Let erop dat de code die u hebt bevorderd relevanter wordt toegewezen en eerder in de zoekresultaten wordt weergegeven.

## Tips en beperkingen {#tips-best-practices-limitations}

* Het gebruik van Smart Content Services is beperkt tot maximaal 2 miljoen getagde afbeeldingen per jaar. Alle gedupliceerde afbeeldingen die zijn verwerkt en getagd, worden allemaal geteld als een gecodeerde afbeelding.
* Als u de labelworkflow uitvoert vanuit de tijdlijn, kunt u tags toepassen op maximaal 15 elementen tegelijk.
