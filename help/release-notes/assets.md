---
title: Opmerkingen bij de release AEM Assets
description: De nieuwe mogelijkheden en verbeteringen voor Adobe Experience Manager 6.5-middelen.
uuid: f785029d-e0fd-494f-b215-7b4caca4e806
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 1ab34a42-2f0e-4b05-a7b6-2fc8dca07ef5
docset: aem65
translation-type: tm+mt
source-git-commit: 95d9ed8a0ccfa7651b83058d337511dd6b15665f

---


# Opmerkingen bij de release AEM Assets{#aem-assets-release-notes}

Hier volgen de belangrijkste kenmerken en hooglichten van de AEM 6.5 Assets-release.

## Integratie met Adobe Creative Cloud en creatieve workflows {#integration-with-adobe-creative-cloud-and-creative-workflows}

AEM biedt verschillende manieren om te integreren met Adobe Creative Cloud en middelen te delen voor gebruik in workflows waarbij de creatieve en marketingteams of de zakelijke teams nauw samenwerken. AEM 6.5 blijft de integratie verbeteren en stroomlijnt deze verder om meer kansen aan het licht te brengen en de bestaande methoden te stroomlijnen.

Lees verder om de specifieke mogelijkheden en integratie van AEM 6.5 te kennen die u kunt gebruiken om uw gebruiksscenario&#39;s voor snelheid van inhoud het best te steunen.

### Adobe-elementkoppeling {#aal}

Adobe Asset Link versterkt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud. Creatieven hebben toegang tot inhoud die is opgeslagen in Adobe Experience Manager Assets (AEM Assets), zonder de apps te verlaten waarmee ze het meest vertrouwd zijn. Met het deelvenster in de app in Photoshop-, Illustrator- en InDesign-toepassingen kunt u op naadloze wijze door middelen bladeren, ze zoeken, uitchecken en inchecken.

Adobe Asset Link maakt deel uit van [Creative Cloud voor ondernemingen](https://www.adobe.com/creativecloud/business/enterprise.html) . Zie [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)voor meer informatie, waaronder de noodzakelijke configuratie van uw AEM-implementatie.

![Photoshop voor middelenzoekopdracht](assets/asset_search_photoshop.png)

### Adobe Stock-integratie {#stock}

Uw organisatie kan haar Adobe Stock Enterprise Plan binnen AEM Assets gebruiken om ervoor te zorgen dat de vergunning gegeven activa voor uw creatieve en marketing projecten globaal beschikbaar zijn. U kunt snel Adobe Stock-middelen vinden, voorvertonen en in licentie geven die in AEM zijn opgeslagen, met behulp van de krachtige DAM-mogelijkheden van AEM.

De voorraadservice van Adobe biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten.

Zie Adobe Stock Assets [gebruiken in AEM Assets](/help/assets/aem-assets-adobe-stock.md)voor meer informatie.

![Adobe Stock-afbeelding voorvertonen en een licentie aanvragen vanuit AEM Assets](assets/stock_image_preview_license_options.png)

Adobe Stock-afbeelding voorvertonen en een licentie aanvragen vanuit AEM Assets

![De gelicentieerde Adobe Stock-afbeeldingen zoeken en filteren in AEM](assets/aem-search-filters2.jpg)

De gelicentieerde Adobe Stock-afbeeldingen zoeken en filteren in AEM

### Dynamische referenties in Adobe InDesign {#dynamic-references-in-indesign}

De AEM-elementen die in Adobe InDesign-bestanden worden gebruikt, zijn dynamisch. De verwijzingen worden automatisch bijgewerkt als de elementen waarnaar wordt verwezen, in de JCR-hiërarchie worden verplaatst. Zie Samengestelde elementen [beheren voor meer informatie](/help/assets/managing-linked-subassets.md).

## Merk Portal-mogelijkheden {#brand-portal-capabilities}

Met AEM Assets Brand Portal kunt u de goedgekeurde bedrijfsmiddelen eenvoudig verwerven, effectief beheren en veilig distribueren aan externe leveranciers/agentschappen en interne zakelijke gebruikers op verschillende apparaten. Het helpt de efficiëntie van het delen van bedrijfsmiddelen te verbeteren, versnelt de tijd tot aan de markt voor bedrijfsmiddelen en voorkomt het risico van niet-conform gebruik en ongeoorloofde toegang.

Zie [Nieuwe functies in Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/using/whats-new.html)voor meer informatie.

## Verbonden elementen {#connectedassets}

In grote ondernemingen kan de infrastructuur die nodig is om websites te maken, worden gedistribueerd. Soms bevinden de mogelijkheden voor het maken van websites en de vereiste digitale middelen zich in verschillende silo&#39;s.

AEM Sites biedt mogelijkheden om webpagina&#39;s te maken en AEM Assets is het Digital Asset Management (DAM)-systeem dat de vereiste middelen voor websites levert. AEM biedt nu ondersteuning voor het bovenstaande gebruiksscenario door de integratie van AEM-sites en AEM-middelen.

Zie Elementen [gebruiken van een Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)voor meer informatie.

![DAM-elementen slepen en neerzetten vanuit een AEM-instantie op de pagina Sites op een andere AEM-instantie](assets/connected-assets-drag-and-drop-only.gif)

DAM-elementen slepen en neerzetten vanuit een AEM-instantie op de pagina Sites op een andere AEM-instantie

##  Dynamische media {#dynamic-media}

Dynamische media biedt verbeterde mogelijkheden voor het schrijven en leveren van rijke media in AEM Assets om geavanceerde ervaringen te creëren die meeslepend en gepersonaliseerd zijn. Door één hoofdmiddel van hoge kwaliteit te uploaden en onze geavanceerde cloudrendering en viewers te gebruiken, kunt u elke combinatie van uitvoeringen ter plekke aanbieden ter ondersteuning van de mediastrategie van uw organisatie.

Zie Opmerkingen bij de release [Dynamische media voor meer informatie over de nieuwe functies van Dynamische media](https://marketing.adobe.com/resources/help/en_US/s7/release_notes/).

### 360 Video-ondersteuning {#video-support}

Beheer uw 360-videobestanden rechtstreeks in AEM met gebruik van de meest geavanceerde viewers van Dynamic Media om VR-ervaringen te bieden aan desktops, mobiele apparaten en VR-headsets. Zie [360-video](/help/assets/360-video.md)gebruiken voor meer informatie.

### Aangepaste videominiaturen {#custom-video-thumbnails}

U kunt de miniaturen voor uw video-elementen nu aanpassen met frames uit de video zelf of andere inhoud die is opgeslagen in de DAM. Zie [Informatie over videominiaturen](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-scene-mode)voor aanvullende instructies.

### Verbeteringen voor toegankelijkheid {#accessibility-enhancements}

Dynamische mediaviewers bieden nu ondersteuning voor verbeterde toegankelijkheidsfuncties, zoals ondersteuning voor apparaatondersteuning, schermlezers en Alt-tekst. Zie Opmerkingen bij de release van [Dynamic Media-viewers voor meer informatie](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/index.html).

## Verbeterde zoekervaring {#search-experience-enhancement}

Vanaf AEM 6.5 kunnen marketers de gewenste middelen sneller ontdekken vanaf de pagina met zoekresultaten. De zoekfacetten worden met het aantal elementen bijgewerkt, zelfs voordat het zoekfilter wordt toegepast. Door het verwachte aantal op het filter te zien, kunnen gebruikers efficiënt door de zoekresultaten navigeren. Zie Elementen [zoeken in AEM](../assets/search-assets.md)voor meer informatie.

![Het aantal elementen weergeven zonder zoekresultaten te filteren in zoekfacetten](/help/assets/assets/asset_search_results_in_facets_filters.png)

Zie het aantal elementen zonder zoekresultaten te filteren in zoekfacetten.

## Verbetering van bruikbaarheid {#usability-enhancement}

U kunt nu alle elementen in een map selecteren of vanuit een zoekresultaat in één keer. Hiermee kunt u meerdere elementen snel beheren. Met het selectievakje worden alle elementen geselecteerd die in het scenario passen, zoals een zoekresultaat en niet alleen de elementen die zichtbaar zijn in de AEM-interface.

![Met de optie Alles selecteren kunt u alle elementen met één klik selecteren.](assets/select-all-in-aem-assets.gif)

Met de optie Alles selecteren kunt u alle elementen met één klik selecteren.

## Verbeteringen in metagegevens {#metadata-enhancements}

Met elementen kunt u metagegevensschema&#39;s maken voor de mappen met elementen, waarmee de lay-out en de metagegevens worden gedefinieerd die op de pagina&#39;s met mapeigenschappen worden weergegeven. U kunt nu een schema voor mapmetagegevens toewijzen aan een bestaande map of bij het maken van een nieuwe map. Zie [Metagegevensschema](/help/assets/folder-metadata-schema.md)van map voor meer informatie.

Als u trapsgewijze metagegevens opgeeft, kunnen de opties tijdens de runtime uit een JSON-bestand worden geladen, bijvoorbeeld in plaats van handmatig in het formulier te typen. Zie [Trapsgewijze metagegevens](/help/assets/cascading-metadata.md)voor meer informatie.

## Verbeteringen rapporteren {#reporting-enhancements}

De Content Fragments en link shares zijn nu opgenomen in het rapport Gedownloade middelen. Zie [Elementenrapporten](/help/assets/asset-reports.md)voor meer informatie.
