---
title: Dynamic Media Classic-functies (Scene7) toevoegen aan uw pagina
description: Adobe Dynamic Media Classic (Scene7) is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan Web, mobiel, e-mail en displays en drukwerk via internet.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: bc9c864b-8bc3-42b4-ba25-6c5108be4f65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '3409'
ht-degree: 0%

---

# Dynamic Media Classic-functies (Scene7) toevoegen aan uw pagina{#adding-scene-features-to-your-page}

[ Adobe Dynamic Media Classic (Scene7) ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/home.html?lang=nl-NL) is een ontvangen oplossing voor het beheren, verbeteren, publiceren, en het leveren van rijke media activa aan Web, mobiel, e-mail, en Internet-Verbonden vertoningen en druk.

U kunt Experience Manager-elementen die in Dynamic Media Classic (Scene7) zijn gepubliceerd, in verschillende viewers weergeven:

* Zoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale middelen rechtstreeks van Experience Manager aan Dynamic Media Classic (Scene7) publiceren en u kunt digitale activa van Dynamic Media Classic (Scene7) aan Experience Manager publiceren.

In dit document wordt beschreven hoe u digitale elementen kunt publiceren van Experience Manager naar Dynamic Media Classic (Scene7) en omgekeerd. Viewers worden ook in detail beschreven. Voor informatie bij het vormen van Experience Manager voor Dynamic Media Classic (Scene7), zie [ Integrating Dynamic Media Classic (Scene7) met Experience Manager ](/help/sites-administering/scene7.md).

Zie ook [ Afbeeldingskaarten ](/help/assets/image-maps.md) toevoegen.

Raadpleeg de volgende secties voor meer informatie over het gebruik van videocomponenten met Experience Manager:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Als de activa van Dynamic Media Classic (Scene7) niet behoorlijk tonen, zorg ervoor dat Dynamic Media [ gehandicapt ](/help/assets/config-dynamic.md#disabling-dynamic-media) is en vernieuw dan de pagina.

## Handmatig publiceren naar Dynamic Media Classic (Scene7) vanuit Assets {#manually-publishing-to-scene-from-assets}

U kunt digitale middelen naar Dynamic Media Classic (Scene7) publiceren vanuit de Assets-console in de klassieke gebruikersinterface of rechtstreeks vanuit het middel.

>[!NOTE]
>
>Experience Manager publiceert asynchroon naar Dynamic Media Classic (Scene7). Nadat u **[!UICONTROL Publish]** hebt geselecteerd, kan het enkele seconden duren voordat uw element naar Dynamic Media Classic (Scene7) wordt gepubliceerd.
>

### Publiceren vanaf de Assets-console {#publishing-from-the-assets-console}

U kunt vanuit de Assets-console publiceren naar Dynamic Media Classic (Scene7) als de middelen zich in een doelmap van Dynamic Media Classic (Scene7) bevinden.

1. Selecteer in de klassieke UI van de Experience Manager de optie **[!UICONTROL Digital Assets]** voor toegang tot het beheer van digitale elementen.

1. Selecteer het element (of de elementen) of de map in de doelmap die u naar Dynamic Media Classic (Scene7) wilt publiceren, klik met de rechtermuisknop en selecteer **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** . U kunt ook **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** selecteren in het menu **[!UICONTROL Tools]** .

   ![ chlimage_1-48 ](assets/chlimage_1-48.png)

1. Ga naar Dynamic Media Classic (Scene7) en bevestig dat de middelen beschikbaar zijn.

   >[!NOTE]
   >
   >Als de elementen zich niet in een gesynchroniseerde Dynamic Media Classic (Scene7)-map bevinden, is **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** in beide menu&#39;s zichtbaar maar uitgeschakeld.

### Publish van een middel {#publishing-from-an-asset}

U kunt een element handmatig publiceren zolang dat element zich in de gesynchroniseerde Dynamic Media Classic-map (Scene7) bevindt.

>[!NOTE]
>
>Als het element niet in de gesynchroniseerde map van Dynamic Media Classic (Scene7) staat, wordt de koppeling naar **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** niet weergegeven.

Publiceren naar Dynamic Media Classic (Scene7) rechtstreeks vanaf een digitaal middel:

1. Selecteer in Experience Manager **[!UICONTROL Digital Assets]** voor toegang tot het beheer van digitale elementen.

1. Dubbelklik om een element te openen.

1. Selecteer **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** in het deelvenster Elementdetails.

   ![ screen_shot_2012-02-22at34828pm ](assets/screen_shot_2012-02-22at34828pm.png)

1. De koppeling verandert in **[!UICONTROL Publishing ...]** en vervolgens in **[!UICONTROL Published]** . Ga naar Dynamic Media Classic (Scene7) en bevestig dat het middel beschikbaar is.

   >[!NOTE]
   >
   >Als het element niet correct wordt gepubliceerd naar Dynamic Media Classic (Scene7), verandert de koppeling in **[!UICONTROL Publishing Failed]** . Als het element al is gepubliceerd naar Dynamic Media Classic (Scene7), wordt **[!UICONTROL Re-Publish to Dynamic Media Classic (Scene7)]** weergegeven op de koppeling. Met Herpublicatie kunt u elementen in de Experience Manager wijzigen en opnieuw publiceren.

### Publish-middelen van buiten de CQ-doelmap {#publishing-assets-from-outside-the-cq-target-folder}

Adobe raadt u aan elementen alleen naar Dynamic Media Classic (Scene7) te publiceren vanuit middelen in de doelmap Dynamic Media Classic (Scene7). Als u echter elementen moet uploaden vanuit een map buiten de doelmap, kunt u dat nog steeds doen door ze te uploaden naar een map op aanvraag in Dynamic Media Classic (Scene7). Configureer eerst de cloudconfiguratie voor de pagina waarop u het element wilt weergeven. Vervolgens voegt u een Dynamic Media Classic-component (Scene7) aan de pagina toe en sleept u een element naar de component. Nadat de pagina-eigenschappen voor die pagina zijn ingesteld, wordt een **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** -koppeling weergegeven die bij selectie het uploaden naar Dynamic Media Classic (Scene7) activeert.

>[!NOTE]
>
>Assets in de map op aanvraag wordt niet weergegeven in de Inhoudsbrowser van Dynamic Media Classic (Scene7).

**om activa van buiten de CQ doelomslag te publiceren:**

1. Selecteer **[!UICONTROL Websites]** in Experience Manager in de klassieke gebruikersinterface en navigeer naar de webpagina die u een digitaal element wilt toevoegen dat nog niet naar Dynamic Media Classic (Scene7) is gepubliceerd. (Normale regels voor paginaovererving zijn van toepassing.)

1. Selecteer in het zijpaneel het pictogram **[!UICONTROL Page]** en selecteer **[!UICONTROL Page Properties]** .

1. Selecteer **[!UICONTROL Cloud Services]** .
1. Selecteer **[!UICONTROL Add services]** .
1. Selecteer **[!UICONTROL Dynamic Media Classic (Scene7)]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic (Scene7)]** de gewenste configuratie en selecteer **[!UICONTROL OK]** .

   ![ chlimage_1-49 ](assets/chlimage_1-49.png)

1. Voeg op de webpagina een Dynamic Media Classic-component (Scene7) toe aan de gewenste locatie op de pagina.
1. Sleep een digitaal element vanuit de zoeker naar de component. Er wordt een koppeling naar **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]** weergegeven.

   >[!NOTE]
   >
   >Als het digitale element zich in de CQ-doelmap bevindt, wordt er geen koppeling naar **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]** weergegeven. De elementen worden in de component geplaatst.

   ![ chlimage_1-50 ](assets/chlimage_1-50.png)

1. Selecteer **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]**. Als de activa niet worden gepubliceerd, publiceert Experience Manager de activa aan Dynamic Media Classic (Scene7). Nadat het element is geüpload, vindt u het in de map op aanvraag. Standaard bevindt de map op aanvraag zich in de map **[!UICONTROL name_of_the_company/CQ5_adhoc]** . U kunt [ de omslag vormen op bestelling, indien nodig ](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Als het element zich niet in een gesynchroniseerde Dynamic Media Classic (Scene7)-map bevindt en er geen Dynamic Media Classic (Scene7)-cloudconfiguratie is gekoppeld aan de huidige pagina, mislukt het uploaden.

## Dynamic Media Classic (Scene7)-componenten {#scene-components}

De volgende Dynamic Media Classic (Scene7)-componenten zijn beschikbaar in de Experience Manager:

* Zoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat ze in de ontwerpmodus beschikbaar zijn gemaakt, kunt u de componenten net als alle andere Experience Managers aan de pagina toevoegen. Assets die nog niet naar Dynamic Media Classic (Scene7) zijn gepubliceerd, worden naar Dynamic Media Classic (Scene7) gepubliceerd als deze zich in een gesynchroniseerde map of op een pagina of met een Dynamic Media Classic (Scene7) Cloud Configuration bevindt.

>[!NOTE]
>
>Als u aangepaste S7-viewers maakt en ontwikkelt en de Inhoudszoeker gebruikt, moet u de parameter `allowfullscreen` expliciet toevoegen.

### Eindbericht voor Flash Viewers {#flash-viewers-end-of-life-notice}

Met ingang van 31 januari 2017 heeft Adobe Dynamic Media Classic (Scene7) de ondersteuning voor het viewerplatform voor Flash officieel beëindigd.

### Een Dynamic Media Classic-component (Scene7) aan een pagina toevoegen {#adding-a-scene-component-to-a-page}

Het toevoegen van een Dynamic Media Classic-component (Scene7) aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. Dynamic Media Classic (Scene7)-componenten worden in de volgende secties uitgebreid beschreven.

Een Dynamic Media Classic-component (Scene7)/viewer toevoegen aan een pagina in de klassieke gebruikersinterface:

1. Open in Experience Manager de pagina waaraan u de Dynamic Media Classic-component (Scene7) wilt toevoegen.

1. Als geen componenten van Dynamic Media Classic (Scene7) beschikbaar zijn, selecteer de heerser in sidekick om **wijze van het Ontwerp** in te gaan, **[!UICONTROL Edit]** parsys te selecteren, en alle **[!UICONTROL Dynamic Media Classic (Scene7)]** componenten te selecteren om hen beschikbaar te maken.

1. Terugkeer aan **geef** wijze uit door het potlood in sidekick te selecteren.

1. Sleep een component van de **[!UICONTROL Dynamic Media Classic (Scene7)]** groep in het hulpstuk op de pagina in de gewenste plaats.

1. Selecteer * **[!UICONTROL Edit]** zodat u de component kunt openen.

1. Bewerk de component naar wens en selecteer **[!UICONTROL OK]** om de wijzigingen op te slaan.

### Interactieve weergaven toevoegen aan een responsieve website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw elementen betekent dat uw elementen worden aangepast op basis van de locatie waar ze worden weergegeven. Bij een responsief ontwerp kunnen dezelfde elementen effectief op meerdere apparaten worden weergegeven.

Een interactieve kijkervaring toevoegen aan een responsieve site in de klassieke gebruikersinterface:

1. Login aan Experience Manager, en zorg ervoor dat u [ gevormde Cloud Servicen van Adobe Dynamic Media Classic (Scene7) ](/help/sites-administering/scene7.md#configuring-scene-integration) hebt en dat de componenten van Dynamic Media Classic (Scene7) beschikbaar zijn.

   >[!NOTE]
   >
   >Als Dynamic Media Classic (Scene7) WCM-componenten niet beschikbaar zijn, moet u deze inschakelen via de ontwerpmodus.

1. In een website waarvoor de Dynamic Media Classic (Scene7)-componenten zijn ingeschakeld, sleept u een **[!UICONTROL Image]** -viewer naar de pagina.
1. Bewerk de component en pas de onderbrekingspunten aan op het tabblad **[!UICONTROL Dynamic Media Classic (Scene7) Settings]** .

   ![ chlimage_1-51 ](assets/chlimage_1-51.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Instellingen die voor alle Dynamic Media Classic (Scene7)-componenten gelden {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle componenten van Dynamic Media Classic (Scene7):

* **Verwijzing van het Dossier** - doorblader aan een dossier dat u wilt van verwijzingen voorzien. De bestandsverwijzing toont de element-URL en niet noodzakelijkerwijs de volledige Dynamic Media Classic (Scene7)-URL, inclusief de URL-opdrachten en -parameters. U kunt in dit veld geen Dynamic Media Classic (Scene7) URL-opdrachten en -parameters toevoegen. In plaats daarvan, moeten zij door de overeenkomstige functionaliteit in de component worden toegevoegd.
* **Breedte** - laat u de breedte plaatsen.
* **Hoogte** - laat u de hoogte plaatsen.

U plaatst deze configuratieopties door (het tweemaal klikken) een component van Dynamic Media Classic (Scene7) te openen, bijvoorbeeld, wanneer u a **&#x200B;**&#x200B;component van het Gezoem opent:

![ chlimage_1-52 ](assets/chlimage_1-52.png)

### Zoomen {#zoom}

De HTML5 component van het Gezoem toont een groter beeld wanneer u + knoop drukt.

Het element heeft onderaan zoomgereedschappen. Selecteer **[!UICONTROL +]** om te vergroten. Selecteer **[!UICONTROL -]** om te reduceren. Als u de zoompijl **[!UICONTROL x]** of de zoompijl opnieuw instelt, wordt de afbeelding weer op de oorspronkelijke grootte ingesteld die was geïmporteerd als. Selecteer de diagonale pijlen zodat u deze op volledig scherm kunt weergeven. Selecteer **[!UICONTROL Edit]** zodat u de component kunt configureren. Met deze component, kunt u [ montages gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic vormen ](#settings-common-to-all-scene-components).

![ Beeld van Tipbloemen binnen de component van het Gezoem HTML5.](do-not-localize/chlimage_1-3.png)

### Flyout {#flyout}

In de HTML5 Flyout-component wordt het element weergegeven als een gesplitst scherm, waarbij het element in de opgegeven grootte wordt geplaatst en rechts het zoomgedeelte wordt weergegeven. Selecteer **[!UICONTROL Edit]** zodat u de component kunt configureren. Met deze component, kunt u [ montages gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic vormen ](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Als uw Flyout-component een aangepaste grootte gebruikt, wordt die aangepaste grootte gebruikt en wordt de responsieve instelling van de component uitgeschakeld.
>
>Als de component Flyout de standaardgrootte gebruikt, zoals die in de ontwerpweergave is ingesteld, wordt de standaardgrootte gebruikt. De component wordt uitgerekt om de grootte van de paginalay-out aan te passen met responsieve instelling van de component ingeschakeld. Houd er echter rekening mee dat er een beperking geldt voor de responsieve installatie van de component. Wanneer u de component Flyout met ontvankelijke opstelling gebruikt, zou u het niet met volledige paginalrek moeten gebruiken. Anders kan de Flyout de rechterrand van de pagina overschrijden.

![ chlimage_1-53 ](assets/chlimage_1-53.png)

### Afbeelding {#image}

Met de Dynamic Media Classic (Scene7) Image-component kunt u Dynamic Media Classic-functionaliteit (Scene7) aan uw afbeeldingen toevoegen, zoals wijzigingstoetsen voor Dynamic Media Classic (Scene7), voorinstellingen voor afbeeldingen of viewers en verscherpen. De Dynamic Media Classic (Scene7)-afbeeldingscomponent is vergelijkbaar met andere afbeeldingscomponenten in Experience Manager met speciale Dynamic Media Classic-functionaliteit (Scene7). In dit voorbeeld is op de afbeelding de optie Dynamic Media Classic (Scene7) URL `&op_invert=1` toegepast.

![ Beeld van een gebied binnen de het beeldcomponent van Dynamic Media Classic (Scène 7) ](do-not-localize/chlimage_1-4.png)

**Titel, de Tekst van Alt** - op het Geavanceerde lusje, voeg een titel aan het beeld en alt tekst voor die gebruikers toe die grafiek hebben uitgezet.

**URL, Open in** - u kunt activa van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![ chlimage_1-54 ](assets/chlimage_1-54.png)

**vooraf ingestelde Kijker** - selecteer een bestaande vooraf ingestelde kijker van het drop-down menu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**de Configuratie van Dynamic Media Classic (Scene7)** - selecteer de configuratie van Dynamic Media Classic (Scene7) die u wilt gebruiken om actieve beeldvoorinstellingen van SPS te halen.

**vooraf ingesteld Beeld** - selecteer een bestaand beeld vooraf ingesteld van het drop-down menu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**Formaat van de Output** - selecteer het outputformaat van het beeld, bijvoorbeeld, jpeg. Afhankelijk van de uitvoerindeling die u selecteert, hebt u mogelijk aanvullende configuratieopties. Zie Aanbevolen werkwijzen voor voorinstellingen afbeelding.

**Verscherpen** - selecteer hoe u het beeld wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in de aanbevolen werkwijzen voor voorinstellingen van afbeeldingen en in de aanbevolen werkwijzen voor Verscherpen.

**de Modifiers URL** - u kunt beeldgevolgen veranderen door extra S7 beeldbevelen te leveren. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de opdrachtverwijzing.

**Onderbrekingspunten** - als uw website ontvankelijk is, wilt u de breekpunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s (,).

### Afbeeldingssjabloon {#image-template}

Dynamic Media Classic (Scene7) Image Templates (Afbeeldingssjablonen) zijn gelaagde Photoshop-inhoud die is geïmporteerd naar Dynamic Media Classic (Scene7), waar de parameters voor inhoud en eigenschappen zijn bepaald op basis van variabiliteit. Met de component **[!UICONTROL Image template]** kunt u afbeeldingen importeren en de tekst dynamisch in Experience Manager wijzigen. Daarnaast kunt u de component **[!UICONTROL Image template]** zo configureren dat waarden van de clientcontext worden gebruikt, dat elke gebruiker de afbeelding op een gepersonaliseerde manier ervaart.

Selecteer **[!UICONTROL Edit]** - om de component te configureren. U kunt [ montages vormen gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic ](/help/sites-administering/scene7.md#settingscommontoallscene7components) en andere montages die in deze sectie worden beschreven.

![ chlimage_1-55 ](assets/chlimage_1-55.png)

**Verwijzing van het Dossier, Breedte, Hoogte** - zie [ montages gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic ](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Dynamic Media Classic (Scene7) URL-opdrachten en -parameters kunnen niet rechtstreeks aan de URL van de bestandsverwijzing worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de gebruikersinterface van de component in het deelvenster **[!UICONTROL Parameter]** .

**Titel, de Tekst van Alt** - in het lusje van het Malplaatje van het Beeld van Dynamic Media Classic (Scene7), voeg een titel aan het beeld en alt tekst voor die gebruikers toe die grafiek hebben uitgezet.

**URL, Open in** - u kunt activa van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![ chlimage_1-56 ](assets/chlimage_1-56.png)

**het Comité van de Parameter** - wanneer het invoeren van een beeld, worden de parameters pre-bevolkt met informatie van het beeld. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![ chlimage_1-57 ](assets/chlimage_1-57.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en selecteert u **[!UICONTROL OK]** . In dit voorbeeld, is de **Prijs** nu $50 en het verschepen is 99 cent.

![ chlimage_1-58 ](assets/chlimage_1-58.png)

De tekst in de afbeelding verandert. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te selecteren.

![ chlimage_1-59 ](assets/chlimage_1-59.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld aan een clientcontextwaarde wilt koppelen, selecteert u **[!UICONTROL Select]** om het contextmenu van de client te openen, selecteert u de clientcontext en selecteert u **[!UICONTROL OK]** . In dit voorbeeld verandert de naam op basis van de koppeling van de naam met de opgemaakte naam in het profiel.

![ chlimage_1-60 ](assets/chlimage_1-60.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te selecteren.

![ chlimage_1-61 ](assets/chlimage_1-61.png)

#### Een koppeling maken van de Dynamic Media Classic (Scene7)-afbeeldingssjabloon {#making-the-scene-image-template-a-link}

U kunt van de Dynamic Media Classic (Scene7) beeldmalplaatjecomponent een klikbare verbinding maken.

1. Selecteer **[!UICONTROL Edit]** op de pagina met de Dynamic Media Classic (Scene7)-afbeeldingssjablooncomponent.
1. Voer in het veld **[!UICONTROL URL]** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt geklikt. Selecteer in het veld **[!UICONTROL Open in]** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![ chlimage_1-62 ](assets/chlimage_1-62.png)

1. Selecteer **[!UICONTROL OK]** .

### Video-component {#video-component}

De Dynamic Media Classic (Scene7) **[!UICONTROL Video]** -component (beschikbaar in de sectie Dynamic Media Classic (Scene7) van het hulpwerkgebied) gebruikt apparaat- en bandbreedtedetectie om de juiste video voor elk scherm te leveren. Deze component is een HTML5-videospeler; het is één viewer die met meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [ Video ](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) voor meer informatie over hoe de video&#39;s met de integratie van Dynamic Media Classic (Scene7) werken. Bovendien zie hoe [ de **video** component van Dynamic Media Classic (Scene7) met de stichting **video** component ](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) vergelijkt.

![ chlimage_1-63 ](assets/chlimage_1-63.png)

### Bekende beperkingen voor de video-component {#known-limitations-for-the-video-component}

Adobe DAM en WCM tonen als een primaire bronvideo wordt geupload. Deze proxy-elementen worden niet weergegeven:

* Dynamic Media Classic (Scene7) gecodeerde uitvoeringen
* Dynamic Media Classic (Scene7) adaptieve videosets

Wanneer u een adaptieve videoset gebruikt met de Dynamic Media Classic (Scene7)-videocomponent, moet het formaat van de component worden aangepast aan de afmetingen van de video.

## Dynamic Media Classic (Scene7)-inhoudbrowser {#scene-content-browser}

Met de Dynamic Media Classic (Scene7)-inhoudbrowser kunt u inhoud uit Dynamic Media Classic (Scene7) rechtstreeks in Experience Manager weergeven. Om tot inhoudbrowser, in de Vinder van de Inhoud toegang te hebben, selecteer **Dynamic Media Classic (Scene7)** in het aanraking-geoptimaliseerde gebruikersinterface of het **S7** pictogram in het klassieke gebruikersinterface. De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, toont de Experience Manager door gebrek de [ standaardconfiguratie ](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties rechtstreeks selecteren in de Dynamic Media Classic-inhoudbrowser (Scene7) in het keuzemenu.

>[!NOTE]
>
>* Assets in de map op aanvraag wordt niet weergegeven in de Dynamic Media Classic-inhoudbrowser (Scene7).
>* Wanneer [ Veilige Voorproef ](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) wordt toegelaten, zowel gepubliceerde als unpublished activa op Dynamic Media Classic (Scene7) verschijnen in Dynamic Media Classic (Scene7) inhoudsbrowser.
>* Als u **[!UICONTROL Dynamic Media Classic (Scene7)]** of het **[!UICONTROL S7]** pictogram niet als optie in inhoudbrowser ziet, moet u [ Dynamic Media Classic (Scene7) vormen om met Experience Manager ](/help/sites-administering/scene7.md) te werken.
>* Voor video ondersteunt de Dynamic Media Classic (Scene7)-inhoudbrowser:
>   * Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>   * Eén MP4-video
>   * Single F4V-video

### Bladeren door inhoud {#browsing-content-in-the-classic-ui}

Blader door inhoud in Dynamic Media Classic (Scene7) door de tab **[!UICONTROL S7]** te selecteren.

U kunt de configuratie veranderen u toegang hebt door de configuratie te selecteren. De mappen veranderen afhankelijk van de geselecteerde configuratie.

![ chlimage_1-64 ](assets/chlimage_1-64.png)

Net als bij de zoekfunctie voor inhoud voor Assets kunt u zoeken naar elementen en resultaten filteren. Nochtans, in tegenstelling tot de vinder van Assets, wanneer het ingaan van een sleutelwoord in het **S7** lusje, begint het dossier - naam **met** het koord dat u inging, eerder dan **bevattend** het sleutelwoord in het dossier - naam.

Elementen worden standaard weergegeven op bestandsnaam. U kunt resultaten echter ook filteren op elementtype.

>[!NOTE]
>
>Voor video ondersteunt de Dynamic Media Classic (Scene7)-inhoudbrowser van WCM:
>
>* Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>* Eén MP4-video
>* Single F4V-video
>

### Zoeken naar Dynamic Media Classic (Scene7)-elementen met de inhoudbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar Dynamic Media Classic (Scene7)-elementen lijkt op het zoeken naar Experience Manager-elementen. De uitzondering is dat wanneer u zoekt, u eigenlijk een verre mening van de activa in het systeem van Dynamic Media Classic (Scene7) ziet, eerder dan hen direct in Experience Manager in te voeren.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**ga sleutelwoorden** in - u kunt activa door naam zoeken. Wanneer u de trefwoorden zoekt, geeft u op waar de bestandsnaam mee begint. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Selecteer `Enter` nadat u de term hebt getypt om het element te zoeken.

![ chlimage_1-65 ](assets/chlimage_1-65.png)

**Omslag/weg** - de naam van de omslag is gebaseerd op de configuratie die u selecteerde. U kunt tot lagere niveaus boren door het omslagpictogram te selecteren en subfolder te selecteren, dan het controleteken te selecteren om het te selecteren.

Als u een sleutelwoord ingaat en een omslag selecteert, zoekt de Experience Manager die omslag en om het even welke subfolders. Als u bij het zoeken echter geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

Standaard zoekt de Experience Manager naar de geselecteerde map en naar alle submappen.

![ chlimage_1-66 ](assets/chlimage_1-66.png)

**Type van Activa** - selecteer Dynamic Media Classic (Scene7) om Dynamic Media Classic (Scene7) inhoud te doorbladeren. Deze optie is alleen beschikbaar als Dynamic Media Classic (Scene7) is geconfigureerd.

![ chlimage_1-67 ](assets/chlimage_1-67.png)

**Configuratie** - als u meer dan één configuratie van Dynamic Media Classic (Scene7) die in Cloud Servicen wordt bepaald hebt, kunt u het hier selecteren. Hierdoor wordt de map gewijzigd op basis van de gekozen configuratie.

![ chlimage_1-68 ](assets/chlimage_1-68.png)

**type van Activa** - binnen browser van Dynamic Media Classic (Scene7), kunt u resultaten filtreren om het even welke volgend te omvatten: beelden, malplaatjes, video&#39;s, en adaptieve videoreeksen. Als u geen elementtype selecteert, zoekt Experience Manager standaard naar alle elementtypen.

![ chlimage_1-69 ](assets/chlimage_1-69.png)

>[!NOTE]
>
>* In klassieke UI, kunt u ook naar **Flash** en **FXG** zoeken. Filteren voor deze twee termen in de interface met geoptimaliseerde aanrakingen wordt niet ondersteund.
>
>* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen &#42; .mp4) en de gecodeerde uitvoering.
>* Wanneer u in een adaptieve videoset zoekt, zoekt u in de map en in alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, doorzoekt Experience Manager de submappen niet.
>

**Status van Publish** - u kunt voor activa filtreren die op publicatiestatus worden gebaseerd: Niet gepubliceerd of Gepubliceerd. Als u geen Publish-status selecteert, zoekt de Experience Manager standaard naar alle publicatiestatus.

![ chlimage_1-70 ](assets/chlimage_1-70.png)
