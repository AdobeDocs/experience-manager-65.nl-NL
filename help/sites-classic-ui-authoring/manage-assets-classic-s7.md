---
title: Dynamic Media Classic (Scene7)-functies aan uw pagina toevoegen
description: Adobe Dynamic Media Classic (Scene7) is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan Web, mobiele apparaten, e-mail en displays en drukwerk via internet.
uuid: dc463e2d-a452-490e-88af-f79bdaa3b089
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: dc0191d0-f181-4e1e-b3f4-73427aa22073
docset: aem65
exl-id: bc9c864b-8bc3-42b4-ba25-6c5108be4f65
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '3371'
ht-degree: 0%

---

# Dynamic Media Classic (Scene7)-functies aan uw pagina toevoegen{#adding-scene-features-to-your-page}

[Adobe Dynamic Media Classic (Scene7) ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/home.html) is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan Web, mobiel, e-mail en displays en drukwerk via internet.

U kunt Experience Manager-elementen die zijn gepubliceerd in Dynamic Media Classic (Scene7), in verschillende viewers weergeven:

* In-/uitzoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale middelen rechtstreeks van Experience Manager aan Dynamic Media Classic (Scene7) publiceren en u kunt digitale activa van Dynamic Media Classic (Scene7) aan Experience Manager publiceren.

In dit document wordt beschreven hoe u digitale elementen kunt publiceren van Experience Manager naar Dynamic Media Classic (Scene7) en omgekeerd. Viewers worden ook in detail beschreven. Zie [Dynamic Media Classic (Scene7) integreren met Experience Manager](/help/sites-administering/scene7.md) voor informatie over het configureren van Experience Manager voor Dynamic Media Classic (Scene7).

Zie ook [Afbeeldingskaarten toevoegen](/help/assets/image-maps.md).

Raadpleeg de volgende secties voor meer informatie over het gebruik van videocomponenten met Experience Manager:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Als Dynamic Media Classic (Scene7)-elementen niet correct worden weergegeven, moet u ervoor zorgen dat Dynamic Media [uitgeschakeld](/help/assets/config-dynamic.md#disabling-dynamic-media) is en de pagina vervolgens vernieuwen.

## Handmatig publiceren naar Dynamic Media Classic (Scene7) van middelen {#manually-publishing-to-scene-from-assets}

U kunt digitale middelen naar Dynamic Media Classic (Scene7) publiceren vanuit de middelenconsole in de klassieke gebruikersinterface of rechtstreeks vanuit het middel.

>[!NOTE]
>
>Experience Manager publiceert asynchroon naar Dynamic Media Classic (Scene7). Nadat u **[!UICONTROL Publish]** hebt geselecteerd, kan het enkele seconden duren voordat uw element naar Dynamic Media Classic (Scene7) wordt gepubliceerd.


### Publiceren vanaf de middelenconsole {#publishing-from-the-assets-console}

U kunt vanuit de middelenconsole publiceren naar Dynamic Media Classic (Scene7) als de middelen zich in een Dynamic Media Classic (Scene7)-doelmap bevinden.

1. Selecteer **[!UICONTROL Digital Assets]** in de klassieke UI van de Experience Manager om toegang te krijgen tot het beheer van digitale elementen.

1. Selecteer het element (of de elementen) of de map in de doelmap die u naar Dynamic Media Classic (Scene7) wilt publiceren, klik met de rechtermuisknop en selecteer **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]**. U kunt ook **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** selecteren in het menu **[!UICONTROL Tools]**.

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. Ga naar Dynamic Media Classic (Scene7) en bevestig dat de middelen beschikbaar zijn.

   >[!NOTE]
   >
   >Als de elementen zich niet in een gesynchroniseerde Dynamic Media Classic (Scene7)-map bevinden, is **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** in beide menu&#39;s zichtbaar maar uitgeschakeld.

### Publiceren vanuit een element {#publishing-from-an-asset}

U kunt een element handmatig publiceren zolang dat element zich in de gesynchroniseerde Dynamic Media Classic-map (Scene7) bevindt.

>[!NOTE]
>
>Als het element niet in de gesynchroniseerde Dynamic Media Classic (Scene7)-map staat, wordt de koppeling naar **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** niet weergegeven.

Publiceren naar Dynamic Media Classic (Scene7) rechtstreeks vanuit een digitaal middel:

1. Selecteer **[!UICONTROL Digital Assets]** in Experience Manager om toegang te krijgen tot het beheer van digitale elementen.

1. Dubbelklik om een element te openen.

1. Selecteer **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** in het deelvenster Elementdetails.

   ![screen_shot_2012-02-22at34828pm](assets/screen_shot_2012-02-22at34828pm.png)

1. De koppeling verandert in **[!UICONTROL Publishing ...]** en vervolgens **[!UICONTROL Published]**. Ga naar Dynamic Media Classic (Scene7) en bevestig dat het middel beschikbaar is.

   >[!NOTE]
   >
   >Als het element niet correct wordt gepubliceerd naar Dynamic Media Classic (Scene7), verandert de koppeling in **[!UICONTROL Publishing Failed]**. Als het middel reeds aan Dynamic Media Classic (Scene7) is gepubliceerd, leest de verbinding **[!UICONTROL Re-Publish to Dynamic Media Classic (Scene7)]**. Met Herpublicatie kunt u elementen in de Experience Manager wijzigen en opnieuw publiceren.

### Elementen publiceren van buiten de CQ-doelmap {#publishing-assets-from-outside-the-cq-target-folder}

Adobe raadt u aan elementen alleen vanuit de doelmap Dynamic Media Classic (Scene7) naar Dynamic Media Classic (Scene7) te publiceren. Als u echter elementen moet uploaden vanuit een map buiten de doelmap, kunt u dat nog steeds doen door ze te uploaden naar een map op aanvraag in Dynamic Media Classic (Scene7). Configureer eerst de cloudconfiguratie voor de pagina waarop u het element wilt weergeven. Vervolgens voegt u een Dynamic Media Classic-component (Scene7) toe aan de pagina en sleept u een element naar de component. Nadat de pagina-eigenschappen voor die pagina zijn ingesteld, wordt een **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]**-koppeling weergegeven die bij selectie het uploaden naar Dynamic Media Classic (Scene7) activeert.

>[!NOTE]
>
>Elementen in de map op aanvraag worden niet weergegeven in de Dynamic Media Classic (Scene7) Content Browser.

**Elementen publiceren van buiten de CQ-doelmap:**

1. Selecteer **[!UICONTROL Websites]** in Experience Manager in de klassieke UI en navigeer naar de webpagina die u een digitaal element wilt toevoegen aan dat nog niet is gepubliceerd naar Dynamic Media Classic (Scene7). (Normale regels voor paginaovererving zijn van toepassing.)

1. Selecteer in de assistent het pictogram **[!UICONTROL Page]** en selecteer **[!UICONTROL Page Properties]**.

1. Selecteer **[!UICONTROL Cloud Services]**.
1. Selecteer **[!UICONTROL Add services]**.
1. Selecteer **[!UICONTROL Dynamic Media Classic (Scene7)]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic (Scene7)]** de gewenste configuratie en selecteer **[!UICONTROL OK]**.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Voeg op de webpagina een Dynamic Media Classic-component (Scene7) toe aan de gewenste locatie op de pagina.
1. Sleep een digitaal element vanuit de zoeker naar de component. Er wordt een koppeling naar **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]** weergegeven.

   >[!NOTE]
   >
   >Als het digitale element zich in de CQ-doelmap bevindt, wordt geen koppeling naar **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]** weergegeven. De elementen worden in de component geplaatst.

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. Selecteer **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]**. Als de activa niet worden gepubliceerd, publiceert Experience Manager de activa aan Dynamic Media Classic (Scene7). Nadat het element is geüpload, vindt u het in de map op aanvraag. Standaard bevindt de map op aanvraag zich in de map **[!UICONTROL name_of_the_company/CQ5_adhoc]**. U kunt [de omslag op bestelling vormen, indien nodig](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Als het element zich niet in een gesynchroniseerde Dynamic Media Classic (Scene7)-map bevindt en er geen Dynamic Media Classic (Scene7)-cloudconfiguratie is gekoppeld aan de huidige pagina, mislukt het uploaden.

## Dynamic Media Classic (Scene7)-componenten {#scene-components}

De volgende Dynamic Media Classic (Scene7)-componenten zijn beschikbaar in de Experience Manager:

* In-/uitzoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat ze in de ontwerpmodus beschikbaar zijn gemaakt, kunt u de componenten net als alle andere Experience Managers aan de pagina toevoegen. Elementen die nog niet naar Dynamic Media Classic (Scene7) zijn gepubliceerd, worden naar Dynamic Media Classic (Scene7) gepubliceerd als ze zich in een gesynchroniseerde map of op een pagina bevinden, of met een Dynamic Media Classic (Scene7) Cloud Configuration.

>[!NOTE]
>
>Als u de kijkers van douane S7 en het gebruiken van de Vinder van de Inhoud creeert en ontwikkelt, moet u uitdrukkelijk de `allowfullscreen` parameter toevoegen.

### Kennisgeving over de gebruiksduur van Flash-viewers {#flash-viewers-end-of-life-notice}

Met ingang van 31 januari 2017 heeft Adobe Dynamic Media Classic (Scene7) officieel de ondersteuning voor het Flash-viewerplatform beëindigd.

### Een klassieke Dynamic Media-component (Scene7) aan een pagina toevoegen {#adding-a-scene-component-to-a-page}

Het toevoegen van een Dynamic Media Klassieke (Scene7) component aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. Dynamic Media Classic (Scene7)-componenten worden in de volgende secties uitgebreid beschreven.

Een Dynamic Media Classic (Scene7)-component/viewer toevoegen aan een pagina in de klassieke gebruikersinterface:

1. Open in Experience Manager de pagina waaraan u de Klassieke Dynamic Media-component (Scene7) wilt toevoegen.

1. Als er geen Klassieke Dynamic Media-componenten (Scene7) beschikbaar zijn, selecteert u de liniaal in het hulpwerkgebied om de modus **Design** in te voeren, selecteert u **[!UICONTROL Edit]** parsys en selecteert u alle **[!UICONTROL Dynamic Media Classic (Scene7)]** componenten om deze beschikbaar te maken.

1. Ga terug naar **Bewerk** modus door het potlood te selecteren in het hulpstuk.

1. Sleep een component van de **[!UICONTROL Dynamic Media Classic (Scene7)]** groep in het hulpstuk op de pagina in de gewenste plaats.

1. Selecteer ***[!UICONTROL Edit]** zodat u de component kunt openen.

1. Bewerk de component naar wens en selecteer **[!UICONTROL OK]** om de wijzigingen op te slaan.

### Interactieve weergaven toevoegen aan een responsieve website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw elementen betekent dat uw elementen worden aangepast op basis van de locatie waar ze worden weergegeven. Bij een responsief ontwerp kunnen dezelfde elementen effectief op meerdere apparaten worden weergegeven.

Een interactieve kijkervaring toevoegen aan een responsieve site in de klassieke gebruikersinterface:

1. Meld u aan bij de Experience Manager en controleer of u [geconfigureerde Adobe Dynamic Media Classic (Scene7)-Cloud Services](/help/sites-administering/scene7.md#configuring-scene-integration) hebt en of Dynamic Media Classic (Scene7)-componenten beschikbaar zijn.

   >[!NOTE]
   >
   >Als Dynamic Media Classic (Scene7) WCM-componenten niet beschikbaar zijn, moet u deze inschakelen via de ontwerpmodus.

1. In een website waarvoor de Dynamic Media Classic (Scene7)-componenten zijn ingeschakeld, sleept u een **[!UICONTROL Image]**-viewer naar de pagina.
1. Bewerk de component en pas de onderbrekingspunten aan op het tabblad **[!UICONTROL Dynamic Media Classic (Scene7) Settings]**.

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Instellingen die voor alle Dynamic Media Classic (Scene7)-componenten gelden {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle Klassieke (Scene7) componenten van Dynamic Media:

* **Bestandsverwijzing** - Blader naar een bestand waarnaar u wilt verwijzen. De bestandsverwijzing toont de element-URL en niet noodzakelijkerwijs de volledige Dynamic Media Classic (Scene7)-URL inclusief de URL-opdrachten en -parameters. U kunt in dit veld geen Dynamic Media Classic (Scene7) URL-opdrachten en -parameters toevoegen. In plaats daarvan, moeten zij door de overeenkomstige functionaliteit in de component worden toegevoegd.
* **Breedte**  - Hiermee kunt u de breedte instellen.
* **Hoogte**  - Hiermee kunt u de hoogte instellen.

U stelt deze configuratieopties in door een Dynamic Media Classic (Scene7)-component te openen (dubbelklikken), bijvoorbeeld wanneer u een **Zoom**-component opent:

![chlimage_1-52](assets/chlimage_1-52.png)

### In-/uitzoomen {#zoom}

De component HTML5 Zoom geeft een grotere afbeelding weer wanneer u op de knop + drukt.

Het element heeft onderaan zoomgereedschappen. Selecteer **[!UICONTROL +]** om te vergroten. Selecteer **[!UICONTROL -]** om te verminderen. Als u **[!UICONTROL x]** of de zoompijl opnieuw instellen selecteert, wordt de oorspronkelijke grootte van de afbeelding hersteld. Selecteer de diagonale pijlen zodat u deze op volledig scherm kunt weergeven. Selecteer **[!UICONTROL Edit]** zodat u de component kunt vormen. Met deze component kunt u [instellingen configureren die hetzelfde zijn voor alle Dynamic Media Classic (Scene7)-componenten](#settings-common-to-all-scene-components).

![](do-not-localize/chlimage_1-3.png)

### Flyout {#flyout}

In de HTML5 Flyout-component wordt het element weergegeven als gesplitst scherm. het element in de opgegeven grootte laten staan; rechts wordt het zoomgedeelte weergegeven. Selecteer **[!UICONTROL Edit]** zodat u de component kunt vormen. Met deze component kunt u [instellingen configureren die hetzelfde zijn voor alle Dynamic Media Classic (Scene7)-componenten](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Als uw Flyout-component een aangepaste grootte gebruikt, wordt die aangepaste grootte gebruikt en wordt de responsieve instelling van de component uitgeschakeld.
>
>Als de component Flyout de standaardgrootte gebruikt, zoals die in de ontwerpweergave is ingesteld, wordt de standaardgrootte gebruikt. De component wordt uitgerekt om de grootte van de paginalay-out aan te passen met responsieve instelling van de component ingeschakeld. Houd er echter rekening mee dat er een beperking geldt voor de responsieve instelling van de component. Wanneer u de component Flyout met ontvankelijke opstelling gebruikt, zou u het niet met volledige paginalrek moeten gebruiken. Anders kan de Flyout de rechterrand van de pagina overschrijden.

![chlimage_1-53](assets/chlimage_1-53.png)

### Afbeelding {#image}

Met de Dynamic Media Klassieke (Scene7) afbeeldingscomponent kunt u Dynamic Media Classic (Scene7)-functionaliteit toevoegen aan uw afbeeldingen, zoals Dynamic Media Classic (Scene7)-wijzigingstoetsen, voorinstellingen voor afbeeldingen of viewers en verscherpen. De Dynamic Media Classic (Scene7) afbeeldingscomponent is vergelijkbaar met andere afbeeldingscomponenten in Experience Manager met speciale Dynamic Media Classic (Scene7)-functionaliteit. In dit voorbeeld is op de afbeelding de optie Dynamic Media Classic (Scene7) URL toegepast, `&op_invert=1`.

![](do-not-localize/chlimage_1-4.png)

**Titel, Alt-tekst**  - Voeg op het tabblad Geavanceerd een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**URL, Openen in**  - U kunt een middel van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-54](assets/chlimage_1-54.png)

**Viewer-voorinstelling**  - Selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**Configuratie**  Dynamic Media Classic (Scene7) - Selecteer de Klassieke (Scene7) configuratie van Dynamic Media u wilt gebruiken om actieve beeldvoorinstellingen van SPS te halen.

**Voorinstelling**  afbeelding - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**Uitvoerindeling**  - Selecteer de uitvoerindeling van de afbeelding, bijvoorbeeld jpeg. Afhankelijk van de uitvoerindeling die u selecteert, hebt u mogelijk aanvullende configuratieopties. Zie Aanbevolen werkwijzen voor voorinstellingen afbeelding.

**Verscherpen**  - Selecteer hoe u de afbeelding wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in de aanbevolen werkwijzen voor voorinstellingen van afbeeldingen en in de aanbevolen werkwijzen voor Verscherpen.

**URL Modifiers**  - U kunt beeldgevolgen veranderen door extra S7 beeldbevelen te verstrekken. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de opdrachtverwijzing.

**Onderbrekingspunten**  - Als uw website reageert, wilt u de onderbrekingspunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s (,).

### Afbeeldingssjabloon {#image-template}

Dynamic Media Classic (Scene7) afbeeldingssjablonen zijn gelaagde Photoshop-inhoud die is geïmporteerd naar Dynamic Media Classic (Scene7), waar inhoud en eigenschappen zijn geparametereerd voor variabiliteit. Met de component **[!UICONTROL Image template]** kunt u afbeeldingen importeren en de tekst dynamisch in Experience Manager wijzigen. Bovendien kunt u de **[!UICONTROL Image template]** component vormen om waarden van cliëntcontext te gebruiken, zodat elke gebruiker het beeld op een gepersonaliseerde manier ervaart.

Selecteer **[!UICONTROL Edit]** - om de component te vormen. U kunt [instellingen configureren die hetzelfde zijn voor alle Dynamic Media Classic (Scene7)-componenten](/help/sites-administering/scene7.md#settingscommontoallscene7components) en andere instellingen die in deze sectie worden beschreven.

![chlimage_1-55](assets/chlimage_1-55.png)

**Bestandsverwijzing, Breedte, Hoogte**  - Zie de  [instellingen die gelden voor alle Dynamic Media Classic (Scene7)-componenten](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Dynamic Media Classic (Scene7) URL-opdrachten en -parameters kunnen niet rechtstreeks aan de URL van de bestandsverwijzing worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de interface van de component in het **[!UICONTROL Parameter]**-deelvenster.

**Titel, Alt-tekst**  - Voeg op het tabblad Dynamic Media Classic (Scene7) Afbeeldingssjabloon een titel toe aan de afbeelding en alternatieve tekst voor gebruikers die afbeeldingen hebben uitgeschakeld.

**URL, Openen in**  - U kunt een middel van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![chlimage_1-56](assets/chlimage_1-56.png)

**Deelvenster**  Parameter - Bij het importeren van een afbeelding worden de parameters vooraf gevuld met informatie uit de afbeelding. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![chlimage_1-57](assets/chlimage_1-57.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en selecteert u **[!UICONTROL OK]**. In dit voorbeeld is **Price** nu $50 en is de verzending 99 cent.

![chlimage_1-58](assets/chlimage_1-58.png)

De tekst in de afbeelding verandert. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te selecteren.

![chlimage_1-59](assets/chlimage_1-59.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld aan een clientcontextwaarde wilt koppelen, selecteert u **[!UICONTROL Select]** om het contextmenu van de client te openen, selecteert u de clientcontext en selecteert u **[!UICONTROL OK]**. In dit voorbeeld verandert de naam op basis van de koppeling van de naam met de opgemaakte naam in het profiel.

![chlimage_1-60](assets/chlimage_1-60.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te selecteren.

![chlimage_1-61](assets/chlimage_1-61.png)

#### Een koppeling maken van de Dynamic Media Classic (Scene7)-afbeeldingssjabloon {#making-the-scene-image-template-a-link}

U kunt van de Dynamic Media Classic (Scene7)-afbeeldingssjablooncomponent een klikbare koppeling maken.

1. Selecteer **[!UICONTROL Edit]** op de pagina met de Dynamic Media Classic (Scene7)-afbeeldingssjablooncomponent.
1. Voer in het veld **[!UICONTROL URL]** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt geklikt. Selecteer in het veld **[!UICONTROL Open in]** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Selecteer **[!UICONTROL OK]**.

### Video-component {#video-component}

De Dynamic Media Classic (Scene7) **[!UICONTROL Video]**-component (beschikbaar in de sectie Dynamic Media Classic (Scene7) van het hulpapparaat) gebruikt apparaat- en bandbreedtedetectie voor de juiste video voor elk scherm. Deze component is een HTML5-videospeler; het is één viewer die via meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) voor meer informatie over hoe video&#39;s werken met de integratie van Dynamic Media Classic (Scene7). Zie ook hoe [de **Dynamic Media Klassieke (Scene7) video** component zich verhoudt tot de basis **video** component](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md).

![chlimage_1-63](assets/chlimage_1-63.png)

### Bekende beperkingen voor de video-component {#known-limitations-for-the-video-component}

Adobe DAM en WCM laten zien of een primaire bronvideo is geüpload. Deze proxy-elementen worden niet weergegeven:

* Dynamic Media Classic (Scene7) gecodeerde uitvoeringen
* Dynamic Media Classic (Scene7) adaptieve videosets

Wanneer u een adaptieve videoset gebruikt met de Dynamic Media Classic (Scene7)-videocomponent, moet het formaat van de component worden aangepast aan de afmetingen van de video.

## Dynamic Media Classic-inhoudbrowser (Scene7) {#scene-content-browser}

Met de Dynamic Media Classic-inhoudbrowser (Scene7) kunt u inhoud van Dynamic Media Classic (Scene7) rechtstreeks in de Experience Manager weergeven. Als u de inhoudbrowser wilt openen, selecteert u **Dynamic Media Classic (Scene7)** in de gebruikersinterface met geoptimaliseerde aanrakingen of het pictogram **S7** in de klassieke gebruikersinterface. De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, toont de Experience Manager door gebrek [standaardconfiguratie](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties rechtstreeks selecteren in de Dynamic Media Classic (Scene7)-inhoudbrowser in het keuzemenu.

>[!NOTE]
>
>* Middelen in de map op aanvraag worden niet weergegeven in de Dynamic Media Classic-inhoudbrowser (Scene7).
>* Wanneer [Beveiligde voorvertoning is ingeschakeld](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene), worden zowel gepubliceerde als niet-gepubliceerde elementen op Dynamic Media Classic (Scene7) wel weergegeven in de Dynamic Media Classic (Scene7)-inhoudbrowser.
>* Als u **[!UICONTROL Dynamic Media Classic (Scene7)]** of het **[!UICONTROL S7]** pictogram niet als optie in inhoudbrowser ziet, moet u [Dynamic Media Klassiek (Scene7) vormen om met Experience Manager](/help/sites-administering/scene7.md) te werken.
>* De Dynamic Media Classic (Scene7)-inhoudbrowser ondersteunt voor video:
   >   * Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
   >   * Eén MP4-video
   >   * Single F4V-video


### Bladeren door inhoud {#browsing-content-in-the-classic-ui}

Blader door inhoud in Dynamic Media Classic (Scene7) door het tabblad **[!UICONTROL S7]** te selecteren.

U kunt de configuratie veranderen u toegang hebt door de configuratie te selecteren. De mappen veranderen, afhankelijk van de configuratie die u selecteert.

![chlimage_1-64](assets/chlimage_1-64.png)

Net als bij de zoekfunctie voor inhoud naar Middelen kunt u zoeken naar elementen en resultaten filteren. Nochtans, in tegenstelling tot de Finder van Activa, wanneer het ingaan van een sleutelwoord op **S7** tabel, begint het dossier - naam **met** het koord dat u inging, eerder dan **bevattend** het sleutelwoord in het dossier - naam.

Elementen worden standaard weergegeven op bestandsnaam. U kunt resultaten echter ook filteren op elementtype.

>[!NOTE]
>
>De Dynamic Media Classic (Scene7)-inhoudbrowser van WCM ondersteunt voor video:
>
>* Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>* Eén MP4-video
>* Single F4V-video

>



### Zoeken naar Dynamic Media Classic (Scene7)-middelen met de inhoudbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar Dynamic Media Classic (Scene7)-elementen lijkt op het zoeken naar Experience Managers. De uitzondering is dat wanneer u zoekt u eigenlijk een verre mening van de activa in het Klassieke systeem van Dynamic Media (Scene7) ziet, eerder dan hen direct in Experience Manager in te voeren.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**Trefwoorden**  invoeren - U kunt elementen zoeken op naam. Wanneer u de trefwoorden zoekt, geeft u op waar de bestandsnaam mee begint. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Zorg ervoor dat u Enter selecteert nadat u de term hebt getypt om het element te zoeken.

![chlimage_1-65](assets/chlimage_1-65.png)

**Map/pad**  - De naam van de map is gebaseerd op de configuratie die u hebt geselecteerd. U kunt tot lagere niveaus boren door het omslagpictogram te selecteren en subfolder te selecteren, dan het controleteken te selecteren om het te selecteren.

Als u een sleutelwoord ingaat en een omslag selecteert, zoekt de Experience Manager die omslag en om het even welke subfolders. Als u bij het zoeken echter geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

Standaard zoekt de Experience Manager naar de geselecteerde map en naar alle submappen.

![chlimage_1-66](assets/chlimage_1-66.png)

**Type element** : selecteer Dynamic Media Classic (Scene7) om door de inhoud van Dynamic Media Classic (Scene7) te bladeren. Deze optie is alleen beschikbaar als Dynamic Media Classic (Scene7) is geconfigureerd.

![chlimage_1-67](assets/chlimage_1-67.png)

**Configuratie**  - Als u meer dan één Classic (Scene7) configuratie hebt die in Cloud Services wordt bepaald, kunt u het hier selecteren. Hierdoor wordt de map gewijzigd op basis van de configuratie die u hebt gekozen.

![chlimage_1-68](assets/chlimage_1-68.png)

**Type**  element - In de Dynamic Media Classic-browser (Scene7) kunt u de resultaten filteren en de volgende items opnemen: afbeeldingen, sjablonen, video&#39;s en adaptieve videosets. Als u geen elementtype selecteert, zoekt Experience Manager standaard naar alle elementtypen.

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>* In klassieke UI, kunt u ook naar **Flash** en **FXG** zoeken. Filteren voor deze twee termen in de interface met geoptimaliseerde aanrakingen wordt niet ondersteund.
   >
   >
* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen *.mp4) en de gecodeerde uitvoering.
* Wanneer u in een adaptieve videoset zoekt, zoekt u in de map en in alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, doorzoekt Experience Manager de submappen niet.



**Status**  publiceren - U kunt filteren op elementen die zijn gebaseerd op de publicatiestatus: Niet gepubliceerd of gepubliceerd. Als u geen publicatiestatus selecteert, zoekt de Experience Manager standaard naar alle publicatiestatussen.

![chlimage_1-70](assets/chlimage_1-70.png)
