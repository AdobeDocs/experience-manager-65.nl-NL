---
title: '[!DNL Adobe Experience Manager] 6.5 de vorige de versienota''s van het de dienstpak'
description: Opmerkingen bij de release voor [!DNL Adobe Experience Manager] 6.5-servicepacks
contentOwner: AK
mini-toc-levels: 2
exl-id: aeed49a0-c7c2-44da-b0b8-ba9f6b6f7101
source-git-commit: 97d0b0d85276c733b487a8f3c5095bc4feb7e08d
workflow-type: tm+mt
source-wordcount: '22693'
ht-degree: 0%

---

# Hotfixes en de Pakken van de Eigenschap inbegrepen in de vorige de dienstpakken {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## [!DNL Adobe Experience Manager] 6.5.9.0. {#experience-manager-6590}

[!DNL Adobe Experience Manager] 6.5.9.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het servicepack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste eigenschappen en de verhogingen die in [!DNL Adobe Experience Manager] 6.5.9.0 worden geïntroduceerd zijn:

* [!DNL Experience Manager Sites] Met de Dynamic Media Foundation-component kunt u de optimalisatie voor apparaten met een hogere resolutie nu in- of uitschakelen wanneer u responsieve voorinstelling voor afbeeldingen of Slim uitsnijden gebruikt.

* Om de prestaties te verbeteren, wordt de `hidden=false` voorwaarde verplaatst van vraag JCR naar [!UICONTROL QueryBuilder] beoordelaar. [!DNL Experience Manager] controleert of een verborgen map niet wordt weergegeven om te controleren of een verborgen voorspelling werkt na de wijziging.

* Mogelijkheid om verwijderde pagina&#39;s en boomstructuur op een [!DNL Experience Manager Sites]-pagina te herstellen.

* Steun voor een nieuwe gebruiker om het toegangstoken te verfrissen gebruikend verfrist token voor de dienst van de brievenbusconfiguratie.

* [Steun voor SMTP XOAUTH2](/help/sites-administering/notification.md#setting-up-oauth) mechanisme voor de dienst van de postconfiguratie.

* Ondersteuning voor [!DNL MongoDB] versies 4.2 en 4.4.

* Namen die betrekking hebben op Hongkong, Macau en Taiwan worden bijgewerkt volgens de nieuwe naamconventies voor Chinese landinstellingen en regio&#39;s.

* Verbeterde toegankelijkheid in [!DNL Experience Manager] [[!DNL Assets]](#assets-accessibility-6590) en [[!DNL Dynamic Media]](#accessibility-dm-6590).

* Met de functie Smart Imaging DPR (Device Pixel Ratio) en de optimalisatie van de netwerkbandbreedte kunt u afbeeldingen van de beste kwaliteit efficiënt leveren. op apparaten met vertoningen met hoge resolutie en beperkte netwerkbandbreedte. Zie [Veelgestelde vragen over intelligente beeldverwerking](/help/assets/imaging-faq.md) voor meer informatie en tijdlijn.

* [!DNL Dynamic Media] levering (`fmt` URL-optie) ondersteunt de volgende generatie afbeeldingsindeling AVIF (AV1-afbeeldingsindeling). Zie [API fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html) voor beeldweergave en rendering voor meer informatie en tijdlijn.

* Mogelijkheid om een meldingsbericht per e-mail naar een groep te verzenden met de workflowstap [!UICONTROL Assign Task].

* Capaciteit om een Interactief Communicatie ontwerp terug te winnen na het wijzigen van de bron Interactieve Communicatie.

* Stel een aangepaste domeinnaam in voor het laden, renderen en valideren van de reCAPTCHA-service in [!DNL Experience Manager Forms].

* Verbeteringen van invoergegevens voor [!UICONTROL Invoke Form Data Model Service]-workflowstap.

* Mogelijkheid om meerdere master pagina&#39;s te gebruiken in een Document of Record-sjabloon in [!DNL Experience Manager Forms].

* Pagina-einden in Document of Record worden ondersteund in [!DNL Experience Manager Forms].

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.7.

Voor een volledige lijst van eigenschappen en verhogingen die in [!DNL Experience Manager] 6.5.9.0 worden geïntroduceerd, zie [nieuw in  [!DNL Adobe Experience Manager] 6.5 Service Pack 9](new-features-latest-service-pack.md).

>[!NOTE]
>
>Vanaf Service Pack 9 kunnen klanten [!DNL Experience Manager] hun [!DNL Experience Manager] toepassingen ontwikkelen en gebruiken met distributies van de [!DNL Azul Zulu] builds van OpenJDK, standaarden-compatibel met Java™ SE.
>Adobe biedt ook ondersteuning voor de [!DNL Azul Zulu] JDK&#39;s aan klanten van [!DNL Experience Manager].
>U kunt de relevante versies van [!DNL Azul Zulu] JDKs van [de Distributie van de Software van Adobe downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
>De gebruiksrechten voor de Oracle Java™-technologie, zoals die door Adobe wordt gedistribueerd, lopen eind december 2022 af. [!DNL Experience Manager] klanten worden aangemoedigd om uiterlijk op deze datum het gebruik voor de  [!DNL Azul Zulu] JDK&#39;s te plannen en uit te voeren. Raadpleeg de bijbehorende [Veelgestelde vragen](https://experienceleague.adobe.com/docs/experience-manager-65/assets/adobe-azul-openjdk-license-agreement.pdf) voor meer informatie over het gebruik van de [!DNL Oracle Java™]-technologie en [!DNL Azul Zulu]-technologie.

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.9.0-release.

### [!DNL Sites] {#sites-6590}

* Gepubliceerde pagina&#39;s waarvoor de eigenschap Verificatievereiste is ingeschakeld, leiden niet om naar de aanmeldingspagina en retourneren het 404-foutbericht (NPR-36354).

* Wanneer u een hyperlink maakt, werkt de optie voor het doorzoeken van een koppeling niet in de tekstcomponent (NPR-35849).

* Er wordt een transversale query geactiveerd bij het gebruik van de `com.day.cq.wcm.commons.ReferenceSearch`-API. Het beïnvloedt prestaties van [!DNL Experience Manager] server (NPR-36407).

* De geneste lay-outcontainer binnen een andere resized lay-outcontainer toont een onjuist aantal kolommen voor zijn kindcomponenten, die in deze componenten resulteren die niet aan het net worden gericht (NPR-36359).

* Externe Linkchecker geeft geldige externe koppelingen weer als ongeldige koppelingen (NPR-36289).

* Nadat u de referenties een tijdje hebt weergegeven, wordt in het venster Referenties een foutbericht weergegeven (NPR-36167).

* Wanneer het bewegen van een component, automatisch gecreeerd parsys, heeft niet de `sling:resourceType` knoop (NPR-36165).

* Wanneer het proberen om een livecopy (terwijl het gebruiken van uitloopvormen [!UICONTROL Activate on Blueprint activation] en [!UICONTROL De-activate on Blueprint activation]) te synchroniseren als een component in de master livecopy wordt geschrapt, ontbreekt de synchronisatie en `NullPointerException` wordt geregistreerd (NPR-36127).

* Wanneer een gebruiker in geïmproviseerde tekst typt voor tag (tag die niet op het systeem aanwezig is) en op Enter drukt, wordt de tag onder het veld weergegeven, maar wanneer het inhoudsfragment wordt opgeslagen en opnieuw geopend, verdwijnt de geïmproviseerde tag (NPR-36132).

* De status van asynchrone bewerkingen (NPR-36104) wordt niet weergegeven in Postvak In.

* Er wordt een dubbele component gemaakt na het herstellen van de overerving (NPR-36000).

* Wanneer het gebruiken van `RemoteContentRenderingService`, omvat het verzoek aan `RemoteContentRendererRequestHandler.getRequest` altijd de wortelpagina voor `ComponentExporter`, maar omvat niet de gevraagde pagina als het niet inbegrepen met het wortelmodel is dat op de traversale diepte en het filtreren optiesreeks wordt gebaseerd. Het verzoek moet altijd de gevraagde pagina omvatten zodat de SPA genoeg informatie heeft om een antwoord terug te geven (NPR-35961).

* onTime/offTime-items activeren/deactiveren niet op de verwachte onTime/offTime (NPR-35936).

* Wanneer u een pagina publiceert die een fragment van de Ervaring bevat dat geen `cq:lastModified` bezit, komt `NullPointerException` voor (NPR-35914).

* Wanneer u probeert de grootte van een component in een container te wijzigen, is het niet mogelijk de oorspronkelijke grootte te herstellen. Wanneer de grootte van de container van de component wordt verkleind, is het niet mogelijk de grootte terug te zetten naar het origineel (NPR-35809).

* In het rollout dialoogvenster, dat in de redacteur of van het Levende Overzicht van het Exemplaar wordt teweeggebracht, zijn de statuspictogrammen voor losgemaakte, geschorste of niet gecreeerde pagina&#39;s verkeerd (NPR-35691).

* Op pagina&#39;s uitrollen van beheer voor meerdere sites hebben de eigenschappen master het selectievakje Uitrollout-pagina en subpagina&#39;s negeren (NPR-35634).

* De functie Herstelboomstructuur, beschikbaar in de klassieke gebruikersinterface, ontbreekt in Touch-gebruikersinterface (CQ-4315352, CQ-4309415).

* Problemen tijdens het herstellen van overerving en het implementeren van de pagina op een [!DNL Experience Manager Sites]-pagina (NPR-36033).

### [!DNL Assets] {#assets-6590}

De volgende verbeteringen in de gebruikerservaring worden uitgevoerd in [!DNL Assets]:

* Als u elementen wilt weergeven die niet zijn gesorteerd op basis van een van de parameters [!UICONTROL Create], [!UICONTROL Modify] of [!UICONTROL Name], biedt [!DNL Adobe Experience Manager] een optie [!UICONTROL None] binnen [!UICONTROL Sort by] opties. De optie [!UICONTROL None] zorgt ervoor dat de elementen in de gebruikersinterface van Elementen (in Kaart, Kolom, en mening) in de zelfde orde zijn zoals zij in knoop JCR (NPR-36356) bestaan.

* Als u de e-mailid in kleine letters wilt weergeven in de ACS API-respons van [!DNL Adobe Experience Manager], wordt een optionele instelling geïntroduceerd. aangezien de [!DNL Adobe Asset Link]-gebruikers geen middelen konden inchecken als hun id niet alle tekens in kleine letters bevatte. Het [!DNL Adobe Asset Link] paneel verbruikt de reactie van ACS API van [!DNL Adobe Experience Manager] (CQ-4317704).

De volgende toegankelijkheidsverbeteringen zijn beschikbaar in [!DNL Assets] als onderdeel van servicepack 9:

Het contrast (met de achtergrond) van de volgende tekst en pictogrammen is verbeterd, zodat gebruikers met een beperkt gezichtsvermogen en kleurperceptie deze kunnen begrijpen:

* Titel van element op pagina [!UICONTROL Properties] (NPR-35967).
* Sterrenclassificatiepictogrammen in [!UICONTROL Rating]-secties op verschillende plaatsen (NPR-36009).
* Tekst op het middel en de omslagmening van de Kaart (NPR-35966).
* Plaatsaanduidingstekst in de weergave [!UICONTROL Timeline] (NPR-35965).
* Namen van activa in de zoekresultaten van activa (NPR-35964).
* Plaatsaanduidingstekst in het dialoogvenster [!UICONTROL Link Sharing] (NPR-35963).
* [!UICONTROL Metadata],  [!UICONTROL Status]en  [!UICONTROL Other] tekst met  [!UICONTROL List] optie in het  [!UICONTROL View Settings] dialoogvenster (NPR-35910).
* [!UICONTROL Location] en  [!UICONTROL Type to search] plaatsaanduidingsteksten in de wereldwijde zoekactie (NPR-35909).
* Pictogrammen uitvouwen en samenvouwen onder [!UICONTROL Content Tree] (NPR-35908).
* De [!UICONTROL Assets]-tekst op de pagina waarop mappen met elementen worden weergegeven (NPR-35905).
* Tekst in [!UICONTROL Asset Metadata], [!UICONTROL Usage Statistics] binnen [!UICONTROL Overview] optie in de pagina met elementdetails (NPR-35904).
* Tekst voor sneltoetsen voor opties [!UICONTROL properties] en [!UICONTROL edit] op de pagina met elementdetails (NPR-35904).

De volgende insectenmoeilijke situaties zijn beschikbaar in [!DNL Assets] als deel van de dienstpak 9:

* De tags die zijn gemaakt vanuit een element voor tagselectie in een formulier [!UICONTROL Folder Metadata Schema], worden niet opgeslagen (NPR-36119).

* Wanneer een kleine ellips wordt gebruikt om elementen van notities te voorzien, overlapt de ellips met het nummer van de annotatie in de afdrukversie (NPR-36114).

* Soms, in de mening van de Kolom, [!DNL Experience Manager] veroorzaakt geen dubbel activaconflict wanneer een dubbel middel wordt geupload (NPR-36048).

* Het dialoogvenster Koppeling delen wordt niet gesloten als het wordt geopend en er geen wijzigingen worden aangebracht (NPR-36030).

* Wanneer er meerdere elementen zijn geselecteerd om de eigenschappen bij te werken, treedt soms een fout op of worden eigenschappen van een niet-geselecteerd element bijgewerkt (NPR-36002).

* Wanneer bij het uploaden van middelen witruimten worden toegevoegd aan het begin of einde van namen van elementbestanden, met resterende tekens die gelijk zijn aan de naam van een bestaand element in de gegevensopslagruimte, wordt het bestaande element vervangen zonder dat een fout wordt geregistreerd (NPR-36001).

* Wanneer video wordt afgespeeld op de pagina met elementdetails, werken de opties voor afspelen en pauzeren niet (NPR-35999).

* Wanneer het unpublishing van activa in bulk, Brand Portal een fout veroorzaakt die erop wijst dat het verzoek URI te lang is (NPR-35954).

* Wanneer een element met lange annotatietekst wordt afgedrukt, wordt de annotatietekst bijgesneden, zelfs als er ruimte beschikbaar is (NPR-35948).

* De optie om naar de volgende pagina te gaan is uitgeschakeld wanneer u de pagina selecteert in de weergave Sjablonen op de pagina Catalogus maken (CQ-4315462).

* Wanneer de werkstroom voor het bijwerken van elementen wordt gestart voor het video-element, wordt de pagina herhaaldelijk vernieuwd (CQ-4313375).

* DAM-mappen kunnen niet worden verwijderd of verplaatst en er wordt een uitzondering vastgelegd (NPR-35942).

### [!DNL Dynamic Media] {#dynamic-media-6590}

In [!DNL Adobe Experience Manager] 6.5.9.0 zijn de volgende toegankelijkheidsverbeteringen beschikbaar in [!DNL Dynamic Media]:

* Wanneer u het dialoogvenster opent om elementen toe te voegen met behulp van toetsenbordtoetsen in de [!UICONTROL Image Set]-editor:
   * Schermlezers vertellen dat het dialoogvenster wordt geopend.
   * De toetsenbordfocus wordt naar het dialoogvenster verplaatst wanneer het wordt geopend.
   * De toetsenbordfocus gaat terug naar de optie Element toevoegen wanneer het dialoogvenster wordt gesloten (CQ-4312134).

* U kunt nu Hotspots op elementen toevoegen en bewerken met de sneltoetsen in de Hotspot-editor (CQ-4305965).

* U kunt hyperlink nu op hotspot plaatsen via Hotspot-beheer met behulp van toetsenbordtoetsen. De focus van de schermlezer gaat nu naar het veld om het URL-pad te bewerken en de optie voor het dialoogvenster Selectie openen (CQ-4290735).

* Het contrast (met de achtergrond) van tekst en besturingselementen op de pagina van de Editor voor de afbeeldingsset is verbeterd, zodat gebruikers met een beperkte gezichtsscherpte en kleurperceptie deze kunnen begrijpen (CQ-4290733).

* U kunt nu naar opties voor het delen van elementen navigeren in de Viewer Preset Editor en de uitgevouwen deeloptie samenvouwen met de toetsenbordtoetsen (CQ-4290724).

* U kunt nu met toetsenbordtoetsen navigeren en knopinfo weergeven in de informatiepictogrammen en waarschuwingspictogrammen op de tabbladen Standaard en Geavanceerd van de pagina Video coderen bewerken (CQ-4290722).

* Schermlezers vertellen nu de instructies voor verschillende velden op het tabblad Weergave en op het tabblad Gedrag in de Viewer Preset Editor (CQ-4290721).

* Wanneer u in de modus Formulier door de pagina Voorinstelling afbeelding bewerken navigeert, worden het doel en de namen van de verschillende velden en besturingselementen in schermlezers vermeld (CQ-4290717).

* Bij het navigeren door de detailpagina met elementen beschrijven schermlezers nu het doel van verschillende opties in Viewers (CQ-4290716).

* Contrast (met achtergrond) van de plaatsaanduidingstekst De optie Alle uitvoeringen in uitvoeringen van de pagina met elementdetails is verbeterd, zodat gebruikers met een beperkt gezichtsvermogen en kleurperceptie deze kunnen begrijpen (CQ-4290713).

* De visuele asterisk om verplicht gebied te betekenen wordt nu verstrekt op het gebied van de Titel van activa in de Redacteur van de Reeks van het Beeld, en de schermlezers kondigen de vereiste informatie voor het gebied aan (CQ-4290712).

* Schermlezers hebben nu toegang tot de pagina met elementdetails voor verschillende interactieve opties in Viewers (CQ-4290708) en kunnen het doel van deze opties nu vertellen.

Adobe Experience Manager 6.5.9.0 Assets verhelpt de volgende problemen in [!DNL Dynamic Media]:

* Custom ViewerPresets en CSS worden niet gerepliceerd naar [!DNL Dynamic Media] wanneer [!DNL Dynamic Media] selectief wordt geactiveerd en door [default](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/config-dm.html#troubleshoot-dm-config) (NPR-36232) wordt uitgeschakeld.

* Wanneer u video-uitvoeringen wilt voorvertonen op de pagina met elementdetails, worden de video&#39;s traag geladen (CQ-4320122).

* Browserpagina reageert niet en wordt trager wanneer meer dan 200 elementen worden geüpload terwijl Duplicate Asset Detector is ingeschakeld (CQ-4319633).

* Wanneer een panoramisch afbeeldingselement wordt toegevoegd aan het panoramische mediacomponent op een pagina, wordt een niet-afgevangen referentiefout vastgelegd (CQ-4317666).

* Wanneer de interactieve media viewer wordt geïmplementeerd met Experience Fragment, wordt het Experience Fragment niet geopend bij de uitgever en wordt een fout vastgelegd (CQ-4317655).

* [!UICONTROL Publish to Dynamic Media] is niet beschikbaar in de  [!UICONTROL Quick Publish] opties op de  [!UICONTROL Properties] pagina (CQ-4317199).

* Siteauteurs met de machtiging Alleen-lezen kunnen de functie voor slim uitsnijden gebruiken voor elementen en de slimme bijgesneden uitvoeringen bewerken (CQ-4316450).

* Video-annotaties werken niet voor mappaden waarbij [!DNL Dynamic Media]-configuratie niet is ingeschakeld, zelfs als de [!DNL Experience Manager]-instantie is ingesteld in de modus [!DNL Dynamic Media] (CQ-4314950).

* Wanneer de titel van het element dubbel-byte, multi-byte, hoge ASCII, Cyrillisch, surrogaat paar, Hebreeuws, Arabisch, en GB18030 karakters heeft, dan bij het publiceren aan Dynamic Media heeft de activa titel een vraagteken (?) (CQ-4311872).

>Bekende problemen met het afspelen van video in Dynamic Media *alleen op Experience Manager 6.5.9.0*:
>
>* 

   <!-- CQDOC-18116 -->You cannot play video renditions from the asset's Details page on Experience Manager - Dynamic Media running in hybrid mode.
>* 

   <!-- CQDOC-18116 -->You cannot stream videos on Experience Manager - Dynamic Media running in hybrid mode.


### Platform {#platform-6590}

* Wanneer u een miniatuur voor een blauwdruk genereert en de wijzigingen in de live kopie doorvoert, werkt de overerving voor sommige velden niet (CQ-4319517).

* Wanneer u een map maakt, selecteert u de eigenschap Bestelbaar en voegt u meer dan 20 elementen aan de map toe. Als u alle elementen in de map selecteert, wordt een onjuist aantal weergegeven (CQ-4316243).

* Wanneer u een pagina vernieuwt, geeft het sorteren van mappen of elementen niet de juiste resultaten weer (CQ-4316200).

* Handlebars JavaScript bibliotheek wordt bevorderd aan v4.7.7 (NPR-36375).

* Aangepaste bundels worden niet bijgewerkt wanneer u een nieuw codepakket installeert met Package Manager (NPR-35949).

* Een `resourceresolver` Het groeperen van bundel veroorzaakt `Sling:alias` vraag om te ontbreken (NPR-35335).

* Het contextpad wordt verwijderd bij het instellen van SSL in Experience Manager (NPR-35294).

* De uitzondering `SegmentNotFound` wordt geretourneerd na een langdurige sessie (NPR-36405).

### Integrations {#integrations-6590}

* Kan pagina-eigenschappen niet opslaan met overerving ingeschakeld voor Cloud Services-ervaringsfragmenten (NPR-36107).

* De paginering en lazy loading van de IMS-gebruikersinterface geven geen geschikte resultaten weer (NPR-36046).

* Wanneer u een configuratie van het Doel A4T creeert en de rapporteringsbron als [!DNL Adobe Analytics] selecteert, zijn er geen Adobe Target-Toegelaten rapportreeksen beschikbaar in dropdown lijst (NPR-36006).

### Projecten {#projects-6590}

* Kan de eigenschappen van een project niet opslaan omdat het JCR-pad naar het project niet is opgelost door een extra slash (`/`) die aan het projectpad is toegevoegd (NPR-36191).

### Schermen {#screens-6590}

* [!DNL Experience Manager Screens] spelers kunnen niet voor authentiek verklaren als een douane twee-factor authentificatiemanager wordt gebruikt (NPR-35854).

### Handel {#commerce-6590}

* De wizard [!UICONTROL Commerce Catalog] kan niet meer dan 40 items laden in de kolomweergave (CQ-4318379).

### Vertaalprojecten {#translation-6590}

* De opties voor bijwerken of overschrijven worden niet weergegeven wanneer een `es` wordt omgezet in `es_es`-pagina (NPR-36170).

* Wanneer de optie Automatisch goedkeuren is geselecteerd voor een project met menselijke vertaling, wordt de taakstatus weergegeven als `Unknown` (NPR-35981).

* Wanneer u een pagina vertaalt, wordt het referentiepad van [!DNL Experience Fragments] niet bijgewerkt naar het referentiepad [!DNL Experience Fragment] (NPR-35911).

* Wanneer u wijzigingen aanbrengt in de bovenliggende en onderliggende pagina&#39;s en de bovenliggende pagina ter vertaling verzendt, worden de onderliggende pagina&#39;s ook onjuist vertaald (NPR-35896).

* Wanneer er meerdere gezamenlijke vertaalprojecten voor een geselecteerde pagina zijn, koppelt de optie [!UICONTROL Go To Projects] niet aan het meest recente vertaalproject (NPR-35454).

* Wanneer u elementen publiceert naar [!DNL Dynamic Media], geeft [!DNL Experience Manager] een onjuist bericht weer voor ongepubliceerde tags (CQ-4315914, CQ-4315913).

* Als u een verwijderde taak opent, wordt een onjuist bericht weergegeven in [!DNL Experience Manager] (CQ-4315910).

### Workflow {#workflow-6590}

* Wanneer u op Handelingen Voltooien, Delegeren of Openen klikt voor items die beschikbaar zijn in Inbox, is er geen visuele aanwijzing voor het voltooien van deze handelingen (NPR-36317).

### [!DNL Communities] {#communities-6590}

* Bij spamfiltering verbruikt het systeem 100% van de Java™ heap-ruimte, waardoor de Experience Manager server niet reageert (NPR-36316, NPR-36493).
* In forums worden de gegevens van de JCR-sessies afkomstig van `SearchCommentSocialComponentListProvider` uitgelekt (NPR-36235).
* Het openen van een specifiek postbusbericht weerspiegelt alle berichten met onjuiste paginering en andere kwesties (NPR-35917).

### [!DNL Brand Portal] {#brandportal-6590}

* De markering voor de functie Asset Sourcing wordt automatisch ingeschakeld bij het configureren van [!DNL Experience Manager Assets] met [!DNL Brand Portal] (NPR-36010).

### [!DNL Forms] {#forms-6590}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het  [!DNL Experience Manager] Service Pack vrij.


**Adaptieve Forms**

* Problemen met taalinitialisatie in [!DNL Experience Manager Forms] 6.5.7.0 bij het genereren van meerdere vertaalwoordenboeken (NPR-36439).
* Als u een bijlage toevoegt aan een adaptief formulierfragment en het formulier verzendt, wordt het volgende foutbericht weergegeven in [!DNL Experience Manager Forms] (NPR-36195):

   ```TXT
    POST /content/forms/af/attachmentissue/jcr:content/guideContainer.af.submit.jsp HTTP/1.1] com.adobe.aemds.guide.servlet.GuideSubmitServlet [AF] Invalid file name or mime type for file resulted in submission failure
   ```

* Wanneer u menselijke vertaling gebruikt om een woordenboek bij te werken en dan een voorbeeld van een adaptief formulier te bekijken, worden de wijzigingen niet weergegeven (NPR-36035).

**Interactieve communicatie**

* Wanneer u een afbeelding uploadt via het Interactieve communicatiekanaal Afdrukken en deze bewerkt, is de afbeelding niet meer zichtbaar (NPR-36518).

* Bij het bewerken van een tekstelement en het vullen van een plaatsaanduiding worden alle interactieve elementen verwijderd uit het navigatiegebied (NPR-35991).

**Workflow**

* Wanneer u het REST-eindpunt van een [!DNL Experience Manager Forms]-service op JBoss® aanroept, geeft [!DNL Experience Manager] het volgende foutbericht weer (NPR-36305):

   ```TXT
   Invalid input. The maximum length of 2000 characters was exceeded.
   ```

**BackendIntegration**

* Kan een formuliergegevensmodel niet opslaan terwijl het Leesservice-argument wordt gebonden aan een letterlijke waarde die een streepje bevat (NPR-36366).

**Documentbeveiliging**

* Wanneer u certificering en HSM instelt voor GlobalSign, [!DNL Experience Manager Forms] geeft de foutberichten `Unsuported Algorithm` en `Invalid TSA Certificate` weer terwijl een tijdstempel wordt toegevoegd aan LTV (NPR-36026, NPR-36025).

**Document Services**

* Updates voor [!DNL Gibson]-bibliotheek voor integratie met [!DNL Experience Manager Forms] (NPR-36211).

**Foundation JEE**

* Wanneer u Eindpuntbeheer op AdminUI selecteert, [!DNL Experience Manager Forms] toont het `endpoint registry failure` foutenbericht (CQ-4320249).

Zie [[!DNL Experience Manager] pagina met beveiligingsbulletins](https://helpx.adobe.com/security/products/experience-manager.html) voor informatie over beveiligingsupdates.

### Bekende problemen in Experience Manager 6.5.9.0 {#known-issues-6590}

* Als u uw [!DNL Experience Manager] instantie van versie 6.5 aan versie 6.5.10.0 bevordert, kunt u `RRD4JReporter` uitzonderingen in het `error.log` dossier bekijken. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een eerder servicepakket installeert op [!DNL Experience Manager] 6.5, wordt de runtimekopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) verwijderd.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam van een map in een hiërarchie in [!DNL Assets] wijzigen en een geneste map publiceren naar [!DNL Brand Portal]. De titel van de map wordt echter pas bijgewerkt in [!DNL Brand Portal] als de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van formulieren mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## [!DNL Adobe Experience Manager] 6.5.8.0. {#experience-manager-6580}

[!DNL Adobe Experience Manager] 6.5.8.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het servicepack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste eigenschappen en de verhogingen die in [!DNL Adobe Experience Manager] 6.5.8.0 worden geïntroduceerd zijn:

<!-- TBD:
* Using the Connected Assets functionality, it is now possible to connect up to 3 [!DNL Sites] instances with 1 [!DNL Assets] instances. The configuration user interface now allows the administrators to provide the details of these [!DNL Sites] instances. -->

* Wanneer u [Functionaliteit voor verbonden elementen](/help/assets/use-assets-across-connected-assets-instances.md) gebruikt, kunt u nu een lijst weergeven met alle [!DNL Sites] pagina&#39;s die het element gebruiken. Deze verwijzingen naar een element zijn beschikbaar op de pagina [!UICONTROL Properties] van een element. Op deze manier kunnen beheerders, marketers en bibliothecarissen een volledig overzicht van het gebruik van bedrijfsmiddelen krijgen, zodat ze het bedrijfsmerk beter kunnen bijhouden, beheren en het merk consistenter zijn.

* Als u een element verwijdert waarnaar in een webpagina wordt verwezen, wordt [!DNL Experience Manager] [een waarschuwing ](/help/assets/use-assets-across-connected-assets-instances.md#asset-usage-references) weergegeven. U kunt een element waarnaar wordt verwezen, forceren verwijderen of de verwijzingen controleren en wijzigen die op de pagina [!DNL Properties] van het element worden weergegeven. Als u op de referenties klikt, worden de lokale en externe [!DNL Sites] pagina&#39;s geopend.

* De pagina&#39;s van Live Copy die beschikbaar zijn voor rollout sorteren met de eigenschappen [!UICONTROL Name], [!UICONTROL Last modified date,] en [!UICONTROL Last rollout date].

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.2.6. <!-- TBD: Mention the version -->

Voor een volledige lijst van eigenschappen en verhogingen die in [!DNL Experience Manager] 6.5.8.0 worden geïntroduceerd, zie [nieuw in  [!DNL Adobe Experience Manager] 6.5 Service Pack 8](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.8.0-release.

### [!DNL Sites] {#sites-6580}

* Wanneer een pagina naar een blauwdruk wordt verplaatst, wordt de bestemming van koppelingen niet bijgewerkt (NPR-35724).
* Op Tizen gebaseerde speler kan niet worden geverifieerd voor bepaalde browsers. Het probleem treedt op bij browsers die het kenmerk samesite=none niet ondersteunen (NPR-35589).
* Een niet-vergrendelde responsieve container geeft geen toegestane onderdelen weer (NPR-35565).
* Wanneer u een live kopie van een zojuist toegevoegde pagina maakt, maakt de master taal twee kopieën voor elk domein (NPR-35545).
* Deadlock in de SCR Registratie van de Component wanneer vele draden wegens `org.apache.felix.scr.impl.ComponentRegistry` tijdopnemer worden geblokkeerd. Als gevolg hiervan reageert [!DNL Experience Manager] niet langer voor onbepaalde tijd (GRANITE-33125,FELIX-6252).
* Wanneer u een specifiek middel in de zijspoorstaaf zoekt, bevat het resultaat sommige niet-gezochte activa (NPR-35524).
* Wanneer u SSL voor een instantie van de Experience Manager toelaat, wordt de contextweg verwijderd (NPR-35477).
* Wanneer u een lijst creeert, voeg wat tekst als eerste element toe, voeg een lijst als tweede element toe, en voeg een lijst binnen de lijst toe, vervormt de ouderlijst (NPR-35465).
* Wanneer u verschillende plug-ins gebruikt op opeenvolgende lijstitems, wordt een extra <br>-tag toegevoegd aan de lijstitems (NPR-35464).
* Wanneer een lijst tussen twee paragrafen wordt geplaatst, kunt u geen lijst aan de lijst (NPR-35356) toevoegen.
* Wanneer u een AEM instantieverbetering van AEM 6.3 tot AEM 6.5 begint, duurt de verbeteringsinstantie langer om (NPR-35323) te beginnen.
* Wanneer u een AEM element dupliceert dat een haakje () bevat. in de naam, ontbreekt de replicatie (GRANITE-27004, NPR-35315).
* Wanneer u koppen toevoegt aan een RTF-editor, is de alineaknop uitgeschakeld (NPR-35256).
* Wanneer u een punt aan een bestaande lijst toevoegt, schrapt het het opvouwen of knevellijst (NPR-35206).
* Als de optie Pagina uitrollen is geselecteerd, wordt een dialoogvenster weergegeven met alle beschikbare live kopieën en wordt de functie automatisch uitrollen uitgevoerd. De live kopieën van pagina&#39;s worden zonder tussenkomst van de gebruiker naar alle geografische gebieden uitgerold (NPR-35138).
* Wanneer u de optie Inclusief onderliggende pagina&#39;s gebruikt, worden niet alle pagina&#39;s vermeld met de optie Publicatie beheren. Er worden slechts 22 pagina&#39;s vermeld (NPR-35086).
* Wanneer een beleid wordt uitgegeven, behoudt de tekstcomponent niet de beleidsveranderingen (NPR-35070).
* Wanneer u een aantal items in een genummerde lijst inspringt, behouden alle items hetzelfde nummer, maar de nummering moet beginnen bij 1 voor items met dezelfde inspringing (CQ-4313011).
* Wanneer minificatie is ingeschakeld, kunt u geen enkele pagina of component bewerken. De kwesties begonnen na het installeren AEM 6.5 Service Pack 7 (CQ-4311133).
* Universeel zoek- en assetfilters retourneren irrelevant of geen resultaten (CQ-4312322, NPR-35793).
* Wanneer meerdere pagina&#39;s tegelijk toegang krijgen tot een clientbibliotheek, kan de HTML-bibliotheekbeheerder de clientbibliotheek niet laden. Dit leidt tot een onjuiste weergave van pagina&#39;s (NPR-35538).
* Het contextpad wordt automatisch verwijderd wanneer u een SSL instelt in [!DNL Experience Manager] (NPR-35294).
* De manager van het pakket registreert geen gebruikers na het klikken van de Logout optie (NPR-35160).

### [!DNL Assets] {#assets-6580}

[!DNL Adobe Experience Manager] 6.5.8.0  [!DNL Assets] verhelpt de volgende problemen en biedt de volgende verbeteringen.

* Na het herstellen van een vorige versie van activa, wordt de gebeurtenis DamEvent.Type RESTORED niet teweeggebracht in de console OSGi (NPR-35789).
* `IndexWriter.merge` veroorzaakt  `OutOfMemoryError` fout aangezien de slimme etiketteringsfunctionaliteit grote  `/oak:index/lucene` en  `/oak:index/ntBaseLucene` indexen (NPR-35651) leidt.
* Er wordt een foutbericht weergegeven wanneer u een tekstmap [!UICONTROL Asset Contribution] met multibyte-tekens in de naam probeert op te slaan (NPR-35605).
* Wanneer trapsgewijze subtypevelden voor metagegevens worden gebruikt, treedt de fout &#39;Dit veld invullen&#39; op (NPR-35643).
* Wanneer een bestaand element wordt gesleept in de [!DNL Assets]-gebruikersinterface en er wordt een nieuwe versie gemaakt, zijn de wijzigingen in de metagegevens niet blijvend (NPR-34940).
* Wanneer het creëren van regels in de redacteur van het meta-gegevensschema voor een trapsgewijs menu, herhaalt de [!UICONTROL Dependant On] optie de zelfde naam (NPR-35596).
* Het zoeken op basis van gelijkenis werkt niet nadat u [!UICONTROL Assets Admin Search Rail] (NPR-35588) hebt bewerkt.
* Als u vanuit een map de zoekopdracht naar elementen opent in de linkertrack door op [!UICONTROL Filter] te klikken, werkt het filter in [!UICONTROL Status] > [!UICONTROL Checkout] > [!UICONTROL Checked out] niet (NPR-35530).
* Als u probeert alle slimme tags van een element te verwijderen en de wijzigingen op te slaan, worden de tags niet verwijderd. De gebruikersinterface geeft echter aan dat de wijzigingen worden opgeslagen (NPR-35519).
* Gebruikers kunnen elementen in de lijstweergave niet opnieuw rangschikken of sorteren in een bestelbare map (NPR-35516).
* Als u het standaardmetagegevensschema bewerkt, verandert het tagveld op de pagina [!UICONTROL Properties] van het element in een tekstveld. Door de wijziging kunnen onbewuste gebruikers tags op aanvraag toevoegen en worden de tags als een tekenreeks opgeslagen in de opslagplaats (NPR-35478).
* Als u tijdens het downloaden van een element een naam opgeeft die geen geldig e-mailadres heeft, is de downloadoptie niet beschikbaar. Als er echter een andere optie in het dialoogvenster Downloaden is geselecteerd, wordt de knop ingeschakeld, maar wordt geen e-mail verzonden (NPR-35365).
* Gebruikers kunnen hun middelen niet inchecken nadat ze de middelen in [!DNL Adobe InDesign] hebben bewerkt en een fout over een gebrek aan machtigingen ontvangen (NPR-35341).
* Handlebars JavaScript bibliotheek wordt bevorderd aan v4.7.6 (NPR-35333).
* De interface van de metagegevenseditor werkt niet meer zoals u had verwacht wanneer u begint met het bewerken van bulkmetagegevens en items deselecteert totdat één item geselecteerd blijft (NPR-35144).
* De globale navigatie opent niet de correcte console wanneer geklikt binnen `assets.html` pagina (CQ-4312311).
* [!DNL Assets] geeft geen RGB-uitvoering weer voor een element met RGB-uitvoering (CQ-4310190).
* De optie [!UICONTROL Relate] in het menu wordt niet correct weergegeven op de pagina [!UICONTROL Properties] (CQ-4310188).
* Als filetype filter voor documenten wordt gebruikt om activa te zoeken en een Slimme Inzameling tot stand te brengen, wordt de filter niet toegepast wanneer de inzameling wordt betreden. In plaats daarvan worden alle typen elementen weergegeven in de zoekopdracht (NPR-35759).
* U kunt geen activa in een Lichtbak van [!DNL Assets] gebruikersinterface (NPR-35901) slepen en toevoegen.
* Wanneer een nieuwe versie van een bestaand element wordt gemaakt nadat het naamconflict is opgelost, worden de metagegevens van het oorspronkelijke element overschreven (CQ-4313594).
* Wanneer u het zoeken van elementen filtert met een zoekfilter of voorspeld, een element opent om het te bekijken of te bewerken en teruggaat naar de pagina met zoekresultaten, werkt het filter niet. Alle gezochte activa zijn vermeld ongefilterd (NPR-35913).

#### [!DNL Dynamic Media] {#dynamic-media-6580}

* De optie URL voor de voorinstelling van een RESS-afbeelding wordt ingeschakeld op de pagina met elementdetails. Nu zijn zowel URL- als RESS-opties beschikbaar op de pagina met elementdetails wanneer de RESS-voorinstelling is geselecteerd in de sectie met dynamische uitvoeringen. (CQ-4311241)
* Interactieve mediacomponent - interactieve video werkt niet als de gebruiker [!DNL Experience Manager] met selectieve publicatieconfiguratie heeft (CQ-4311054).
* Als u middelen over omslagen beweegt, is de synchronisatie tussen [!DNL Experience Manager] en [!DNL Dynamic Media–Scene7] via API zeer langzaam (CQ-4310001).
* Bij gebruik van Omnissearch neemt de grootte van de logs aanzienlijk toe (CQ-4309153).
* Wanneer selectieve synchronisatie is ingeschakeld en een element wordt gekopieerd (niet verplaatst) naar een synchronisatiemap, wordt het niet gesynchroniseerd zoals u had verwacht (CQ-4307122).
* Voor geüploade elementen die automatisch naar DM worden gepubliceerd, wordt de status niet weergegeven bij AEM. Bovendien wordt in de statuskolom Dynamic Media Publish niet de juiste gepubliceerde status weergegeven (CQ-4306415).
* Als een element wordt gepubliceerd op [!DNL Experience Manager] en bij activering wordt ingesteld om naar [!DNL Dynamic Media] te publiceren, wordt de metagegevenswaarde `scene7FileStatus` niet naar behoren bijgewerkt (CQ-4308269).
* Als u het videoprofiel bewerkt, worden de hoogte- en bitsnelheidwaarden die zijn ingesteld voor de videovoorinstelling niet weergegeven in [!DNL Experience Manager]. De velden worden leeg weergegeven (CQ-4311828).

### [!DNL Commerce] {#commerce-6580}

* Kan geen aangepaste tag maken voor alle producten in de handel (CQ-4310682).

* De update van de verwijzing van het productelement veroorzaakt replicatiedraden om in de wachtstand te zijn tot de draad ProductAssetListener zijn verplichtingen aan JCR voltooit (NPR-35269).

### Platform {#platform-6580}

* Wanneer u een component van de Mening van het Lusje van het Koraal zonder lusjes gebruikt en dan een validator van de Stichting teweegbrengt, komt de volgende fout voor (NPR-35636):

   ```TXT
    Uncaught TypeError: Cannot set property 'invalid' of undefined
     at enable (foundation.js:10703)
     at foundation.js:10710
   ```

* SCD door:sturen replicatie ontbreekt voor de gebeurtenissen van de Schrapping voor knopen die een komma in de naam (NPR-35191) omvatten.

* Nadat u aan AEM 6.5.7 bevordert, beginnen de bouwstijlen te ontbreken. De reden hiervoor is dat een oude versie of geen cola van de nakker is ingebed in de uber-jar (GRANITE-33006).

### Gebruikersinterface {#ui-6580}

* Wanneer u van de mening van de Kaart aan de mening van de Lijst voor documenten in een omslag in de console van Activa overschakelt, werkt het sorteren niet geschikt (NPR-35842).

* Wanneer u tekst in een tekstcomponent hyperlinkt, geeft de zoekfunctie niet de juiste resultaten weer (NPR-35849).

* Wanneer geen waarde wordt verstrekt aan een verborgen gebied dat wordt gemerkt vereist, verhindert het u een component (NPR-35219) op te slaan.

### Integraties {#integrations-6580}

* Wanneer u verschillende waarden voor IMS huurder ID en de code van de Cliënt van het Doel gebruikt, [!DNL Experience Manager] kan niet integreren met [!DNL Adobe Target] (NPR-35342).

### Vertaalprojecten {#translation-6580}

* Problemen bij het exporteren of importeren van een vertaaltaak in [!DNL Experience Manager] (NPR-35259).

### Campagne {#campaign-6580}

* Wanneer u een campagnepagina maakt met een out-of-the-box-sjabloon in Touch UI en het tabblad E-mail opent in het dialoogvenster met pagina-eigenschappen, blijft de variabele voor de personalisatie van het onderwerp en de tekstvelden uitgeschakeld (CQ-4312388).

### [!DNL Communities] {#communities-6580}

* Bij het toevoegen van een paginastructuur aan een communautaire groep, wordt de [!UICONTROL Group] titel in de broodkruimel veranderd in de titel van eerste [!UICONTROL Page] (NPR-35803).
* In tegenstelling tot moderatoren is een standaardlid van de community geen toegang tot een ontwerppost (NPR-35339) en kan het deze niet bewerken.
* Verbroken toegangscontrole en ontkenning van service met `DSRPReindexServlet` die de site van de gemeenschappen omlaag brengt tot de indexering is voltooid (NPR-35591).
* Als u [!UICONTROL All Users] uit het veld [!UICONTROL Administrators] verwijdert, worden deze niet daadwerkelijk uit het achterste gedeelte verwijderd (NPR-35592, NPR-35611).
* De component [!UICONTROL Compose Message] retourneert geen resultaat wanneer de ingevoerde tekst gedeeltelijk overeenkomt (NPR-35666).

* Het kan zijn dat de prestaties enigszins worden beïnvloed en vertraagd wanneer u probeert tags toe te voegen aan een nieuwe blog door **[!UICONTROL Add Tags]** te selecteren. Installeer [cqTagLucene-0.0.1.zip hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/cqTagLucene-0.0.1.zip) om de prestaties te verbeteren.

### [!DNL Brand Portal] {#brandportal-6580}

* Als u een lid toevoegt aan een [!UICONTROL Asset Contribution]-typemap, wordt het bijschrift [!UICONTROL Add User or Group] weergegeven in de gebruikersinterface, hoewel alleen actieve Brand Portal-gebruikers worden ondersteund en niet groepen (NPR-35332).

### [!DNL Forms] {#forms-6580}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het  [!DNL Experience Manager] Service Pack vrij.

**Adaptieve Forms**

* Wanneer u een tabel met een herhaalbare rij invoegt in een herhaalbaar paneel dat meerdere instanties in een adaptieve vorm heeft, wordt de tabel altijd toegevoegd aan de eerste instantie van het paneel (NPR-35635).

* Wanneer de tabfocus de component CAPTCHA opnieuw bereikt nadat deze eenmaal is geverifieerd in een adaptieve vorm, geeft [!DNL Experience Manager Forms] het foutbericht `Provide Captcha phrase to proceed` weer (NPR-35539).

**Interactieve communicatie**

* Wanneer u een vertaald formulier verzendt, worden de verzendberichten in het Engels weergegeven en niet in de juiste taal vertaald (NPR-35808).

* Wanneer u een hide-voorwaarde opneemt in de bijgevoegde XDP- of documentfragmenten, kan de interactieve communicatie niet worden geladen (NPR-35745).

**Correspondentenbeheer**

* Wanneer u een letter bewerkt, duurt het langer om de modules met voorwaarden te laden (NPR-35325).

* Wanneer u in het linkernavigatievenster een element selecteert dat niet in een letter is opgenomen en vervolgens het volgende element selecteert, wordt de blauwe markering niet uit het eerder geselecteerde element verwijderd (NPR-35851).

* Wanneer u tekstvelden in een letter bewerkt, wordt [!DNL Experience Manager Forms] het foutbericht `Text Edit Failed` weergegeven (CQ-4313770).

**Workflow**

* Wanneer u een adaptief formulier probeert te openen op een [!DNL Experience Manager Forms] mobiele toepassing voor iOS, stopt de toepassing met reageren (CQ-4314825).

* Het tabblad [!UICONTROL To-do] in de HTML-werkruimte geeft HTML-tekens weer (NPR-35298).

**XMLFM**

* Wanneer u een XML-document genereert met de uitvoerservice, treedt de fout `OutputServiceException` op voor sommige XML-bestanden (CQ-4311341, CQ-4313893).

* Wanneer u superscript-eigenschap toepast op het eerste teken van het opsommingsteken, wordt de grootte van het opsommingsteken kleiner (CQ-4306476).

* De PDF forms die worden gegenereerd met de uitvoerservice omvatten geen randen (CQ-4312564).

**Designer**

* Wanneer u een XDP-bestand opent in [!DNL Experience Manager Forms] Designer, wordt een bestand designer.log gegenereerd in dezelfde map als het XDP-bestand (CQ-4309427, CQ-4310865).

**HTML5 Forms**

* Wanneer u een selectievakje in adaptieve vorm in [!DNL Safari] webbrowser selecteert voor [!DNL iOS 14.1 or 14.2], worden geen extra velden weergegeven (NPR-35652).

**Forms Management**

* Geen bevestigingsbericht om aan te geven dat XDP-bestanden in bulk zijn geüpload naar CRX-opslagplaats (NPR-35546).

**Documentbeveiliging**

* Meerdere problemen gerapporteerd voor de optie [!UICONTROL Edit Policy] op AdminUI (NPR-35747).

### Bekende problemen in Experience Manager 6.5.8.0 {#known-issues-6580}

* Als u uw [!DNL Experience Manager] instantie van versie 6.5 aan versie 6.5.8.0 bevordert, kunt u `RRD4JReporter` uitzonderingen in het `error.log` dossier bekijken. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een eerder servicepakket installeert op [!DNL Experience Manager] 6.5, wordt de runtimekopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) verwijderd.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Neem contact op met de klantenservice van Adobe als u problemen ondervindt bij het bewerken en maken van trapsgewijze regels in [!UICONTROL Folder Metadata Schema Forms Editor] en [!UICONTROL Metadata Schema Forms Editor] via het dialoogvenster [!UICONTROL Define Rule]. De regels die al zijn gemaakt en opgeslagen, werken zoals u had verwacht.

* Als de naam van een map in de hiërarchie wordt gewijzigd in [!DNL Experience Manager Assets] en de geneste map met een element wordt gepubliceerd naar [!DNL Brand Portal], wordt de titel van de map niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* Als de wizard [!UICONTROL Connected assets configuration] na de installatie een foutbericht van 404 retourneert, installeert u de pakketten `cq-remotedam-client-ui-content` en `cq-remotedam-client-ui-components` handmatig opnieuw met de Package Manager.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van formulieren mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## [!DNL Adobe Experience Manager] 6.5.7.0. {#experience-manager-6570}

[!DNL Adobe Experience Manager] 6.5.7.0 is een belangrijke update die nieuwe eigenschappen, zeer belangrijke klant gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen omvat, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het Service Pack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste eigenschappen en de verhogingen die in [!DNL Adobe Experience Manager] 6.5.7.0 worden geïntroduceerd omvatten:

* Als u de pagina uitvoert, worden de pagina verplaatst en MSM-rollouts als asynchrone bewerkingen uitgevoerd, zodat de runtime minder wordt belast met de prestaties.

* Gebruikers kunnen digitale elementen sorteren in de Kaart- en kolomweergave.

* [!DNL Assets] en  [!DNL Dynamic Media] bieden meerdere toegankelijkheidsverbeteringen. De verbeteringen hebben betrekking op toetsenbordnavigatie, het gebruik van schermlezers en het inschakelen van gebruikers om vergelijkbare ondersteunende hulpmiddelen (AT) te gebruiken. Zie [[!DNL Assets] verbeteringen](#assets-6570) en [[!DNL Dynamic Media] verbeteringen](#dynamic-media-6570).

* [Het gegevensmodel van de vormHTTP- cliëntconfiguratie ](../../help/forms/using/configure-data-sources.md#fdm-http-client-configuration) om prestaties te optimaliseren.

* [Beschikbaarheid van de optie Herstellen voor elke ](../../help/forms/using/resize-using-layout-mode.md#resize-components) component in de modus Lay-out

* [!DNL Experience Manager] 6.5 Service Pack 7 Forms verbetert de prestaties voor:

   * De veldwaarden op de server valideren wanneer u een adaptief formulier verzendt.

   * Een PDF-formulier converteren naar een adaptief formulier met [!DNL Automated Forms Conversion service].

* Ondersteuning voor [!DNL Microsoft SQL Server] 2019 in [!DNL Experience Manager Forms].

* Steun voor [!DNL Microsoft] SQL Server 2016 altijd op beschikbaarheidsgroepen voor Hoge Beschikbaarheid voor plaatsingen OSGi.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.22.5.

Voor een volledige lijst van eigenschappen en verhogingen die in [!DNL Experience Manager] 6.5.7.0 worden geïntroduceerd, zie [Nieuw in  [!DNL Adobe Experience Manager] 6.5 Service Pack 7](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.7.0.

### [!DNL Sites] {#sites-6570}

* Wanneer u de optie [!UICONTROL Timewrap] voor een pagina opent, de optie van de de zijspoorstaaf van de Chronologie open houdt, en aan [!UICONTROL Sites] console navigeert, komt de `Failed to Load` fout (NPR-34951) voor.

* Met de optie [!UICONTROL Timewrap] worden geen afbeeldingen voor het geselecteerde datum- en tijdbereik weergegeven (NPR-34951).

* Wanneer een filter `getHeader()` van een pagina roept die een tevreden Fragment bevat, komt de `java.lang.AbstractMethodError` fout voor (NPR-34942).

* Wanneer het pad van een pagina meerdere subtekenreeksen voor inhoud bevat, kunnen voorvertoningen niet worden weergegeven en mislukt de functie Vergelijken van versie ook (NPR-34740).

* Wanneer u een numerieke waarde instelt voor de eigenschap `String` type label van een component, kunt u de component verwijderen en de verwijderbewerking ongedaan maken. Na het ongedaan maken van de verwijdering verandert de eigenschap label echter van `String` in `Long` (NPR-34739).

* De volgende uitzondering geldt bij het toevoegen van een ervaringsfragment dat is gebaseerd op een sjabloon met een vergrendelde indeling aan een pagina (NPR-34632):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.apache.sling.api.SlingException: Cannot get DefaultSlingScript: org.mozilla.javascript.EcmaError: TypeError: Cannot call method "getChildren" of null
   ```

* Wanneer u een map verplaatst, veroorzaakt dit traversale problemen en treedt de volgende fout op (NPR-34554):

   ```TXT
   org.apache.sling.api.SlingException: Cannot get DefaultSlingScript. org.apache.jackrabbit.oak.query.RuntimeNodeTraversalException: The query read or traversed more than 100000 nodes. To avoid affecting other tasks, processing was stopped
   ```

* Wanneer nieuwe elementen worden gemaakt, gepubliceerd en naar een nieuwe locatie worden verplaatst, wordt de `Request to complete move operation`-workflow gemaakt en wordt de status Afgebroken weergegeven. Als u een nieuw element uploadt en een `move`-bewerking uitvoert, wordt de `Request to complete move operation`-workflow in de wachtrij geplaatst (NPR-34543).

* Wanneer u een fragment van de Ervaring van [!DNL Experience Manager] 6.5.2 milieu naar [!DNL Target] Standaard uitvoert, ontbreekt de API vraag omdat het werkruimtebezit niet beschikbaar voor [!DNL Target] Standaard (NPR-34557) is.

* Gebruikers kunnen geen pagina&#39;s publiceren via de optie [!UICONTROL manage publication] omdat de optie [!UICONTROL Publish] verdwijnt (NPR-34542).

* Wanneer u bepaalde stijlen aan de tekst toevoegt, wordt een `<div>`-label aan de tekst toegevoegd en kan de stijl niet meer op de tekst worden toegepast (NPR-34531).

* Wanneer u een item in een pop-upmenu selecteert en de vereiste bestanden bijwerkt, is het niet toegestaan dialoogvensterwaarden op te slaan omdat het andere menu een leeg vereist veld heeft (NPR-34529).

* Wanneer u een pagina maakt op basis van een aangepaste sjabloon en deze verplaatst binnen de hiërarchie van de blauwdruk, worden componenten die eerder van de pagina zijn verwijderd, weergegeven op de pagina in de hiërarchie van de live kopie (NPR-34527).

* Wanneer een artikelstijl op een inhoud is toegepast, kan deze niet worden verwijderd (NPR-34486).

* Alle live kopieën en kopieën van een Experience Fragment verwijzen naar dezelfde [!DNL Adobe Target] aanbieding-id (NPR-34469).

* Lijstitems met opsommingstekens worden naast de genummerde lijst weergegeven (NPR-34455).

* De optie Vergelijken met bron geeft het verschil tussen de bronpagina en de bewerkte versie van een pagina niet aan (NPR-34285).

* Wanneer u een pagina schrapt, zijn de versiedetails niet configureerbaar (NPR-34159).

* Wanneer een gebruiker de [!UICONTROL Open Selection] dialoogdoos selecteert, beweegt de toetsenbordnadruk zich aan de verborgen controle op de pagina (CQ-4307779, CQ-4293601).

* Wanneer u een gepubliceerde map op de Auteur verplaatst, worden de mappaden niet overeenkomstig bijgewerkt in de instantie Publiceren (CQ-4305144).

* Wanneer een gebruiker de `Enter`-toets op de optie [!UICONTROL Select All] selecteert, wordt de toetsenbordfocus niet verplaatst naar de optie [!UICONTROL Create Control] (CQ-4293599).

* Wanneer u de `Esc` sleutel selecteert, wordt de nadruk niet hersteld aan de oudercontrole (CQ-4293593, CQ-4293590).

* Verbeterde WCAG-compatibiliteit voor UI- en Core-componenten [!DNL Sites] (CQ-4293448).

* [!UICONTROL Zoom] en  [!UICONTROL Scale] functies zijn uitgeschakeld voor de  [!DNL Sites Editor] pagina (CQ-4282353).

* Nadat u de optie Rechtsom roteren hebt gebruikt, houdt de schermlezer op met commentaar voor de huidige rotatie- of spiegelstatus (CQ-4282128).

* De knoppen Gereed en Annuleren in het dialoogvenster Configureren bevatten veel tabstops (CQ-4274601).

* Het verplaatsen van pagina&#39;s met een vergelijkbare naam op hetzelfde niveau is niet toegestaan (NPR-35041).

* Nadat u de optie Wissen (x) hebt geselecteerd, wordt de toetsenbordfocus niet verplaatst naar het veld [!UICONTROL Filter] (CQ-4293581).

* Wanneer u een upgrade uitvoert naar [!DNL Experience Manager] 6.5.6.0, verandert het gedrag van het overgeërfde alineasysteem en werkt het niet correct (NPR-35117).

* Toetsenbordgebruikers kunnen de tabfocus niet in de juiste volgorde verplaatsen nadat ze de sectie [!UICONTROL Action] op een pagina [!DNL AEM Sites] hebben geselecteerd (CQ-4307786).

* Nadat u een optie hebt geselecteerd in de vervolgkeuzelijst met koppelingsdoelen van de RTE-werkbalk tijdens het bewerken van een inhoudsfragment, wordt het dialoogvenster met de auteur van het inhoudsfragment geflickeerd (CQ-4305532).

* Keyboard-gebruikers kunnen de opties in de vervolgkeuzelijst [!UICONTROL Add Component] niet selecteren met de pijl-omlaag (CQ-4295097).

* De tabfocus verschuift niet in de juiste volgorde wanneer u een datum selecteert in het menu Kalender op het tabblad [!UICONTROL Assets] van een pagina [!DNL Sites] (CQ-4293600).

* De tabfocus verschuift niet naar de volgende of vorige opties voor toetsenbordgebruikers nadat de beschikbare opties voor Koppeling of Tekst zijn verwijderd tijdens het bewerken van een sitepagina (CQ-4293597).

* Toetsenbordgebruikers kunnen de tabfocus niet terugzetten op Meer opties in de sectie [!UICONTROL Actions] nadat ze de beschikbare opties hebben bekeken en op `Esc` hebben gedrukt (CQ-4293592).

* Wanneer u de optie [!UICONTROL Rotate] voor een afbeelding in de modus [!UICONTROL Edit] activeert, wordt de tabfocus in plaats van te blijven roteren verplaatst naar de optie [!UICONTROL Redo] voor de toetsenbordgebruikers (CQ-4293587).

* In het [!UICONTROL Open Selection] dialoogvenster dat beschikbaar is op het tabblad [!UICONTROL Link and Actions], wordt de tabfocus verplaatst naar verborgen elementen op de pagina na de optie [!UICONTROL Cancel] (CQ-4293579).

* Wanneer gebruikers van het toetsenbord een afbeelding bewerken, naar de optie [!UICONTROL Finish] navigeren en op Enter drukken, kondigen schermlezers de voltooiing niet aan (CQ-4282351).

* De opties Omhoog en Omlaag in het dialoogvenster [!UICONTROL Link and Actions] zijn niet beschikbaar voor schermlezers en toetsenbordgebruikers (CQ-4281120).

* Keyboard-gebruikers kunnen de tabfocus niet herstellen nadat ze naar de optie Close (X) op de pagina [!UICONTROL Properties] zijn genavigeerd (CQ-4293581, NPR-34653).

### [!DNL Assets] {#assets-6570}

[!DNL Adobe Experience Manager] 6.5.7.0  [!DNL Assets] verhelpt de volgende problemen en biedt de volgende verbeteringen.

* De volgende verbeteringen zijn aangebracht voor de toegankelijkheid in [!DNL Experience Manager Assets] in deze release. Zie [toegankelijkheidsfuncties in [!DNL Assets]](/help/assets/accessibility.md) voor meer informatie.

   * Wanneer u met een toetsenbord door de tijdlijn navigeert, kan de `Esc`-toets de optie [!UICONTROL Show All] samenvouwen zonder de focus te verliezen (CQ-4293598).
   * Wanneer u navigeert met de Tab-toets op het toetsenbord, behoudt het tagveld de focus nadat u de laatste tag uit de toegevoegde tags hebt verwijderd (NPR-35109).
   * [!DNL Experience Manager] De componenten bevatten nu de juiste informatie voor de naam, rol en waarde die door schermlezers moeten worden gebruikt (NPR-34255).
   * Nadat u de keuzelijst Type/Grootte, keuzelijst Koppeling, keuzelijst Taal of Tekstbewerking hebt verwijderd, keert de toetsenbordfocus terug naar de volgende of vorige gebruikersinterface-elementen of naar een relevanter gebruikersinterface-element (CQ-4293585).
   * Als u de aanwijzer op opties plaatst, worden er tips zoals Selecteren en Downloaden weergegeven. Gebruikers die een schermvergroting gebruiken, zien de miniaturen van het bestand mogelijk niet vanwege deze tips. Nu is het mogelijk om de focus te behouden nadat u de optie hebt verwijderd met de `Escape`-toets. (CQ-4293554).
   * Wanneer u een rastercel selecteert uit het raster dat aanwezig is op de pagina, wordt de focus verplaatst naar de actiebalk die wordt weergegeven op het scherm (CQ-4282127).
   * Visuele gebruikers kunnen onderscheid maken tussen normale tekst en een koppeling, aangezien visuele aanwijzingen (onderstreping en chevron-pictogram) worden weergegeven voor koppelingen naar alle oplossingen op [!DNL Experience Manager] homepage (CQ-4282072).

* De volgende gebruikerservaring wordt verbeterd in [!DNL Assets]:

   * Het sorteren van elementen in kaart- en kolomweergave inschakelen (NPR-35097).

* Als na de upgrade naar 6.5 een JSON-bestand wordt gegenereerd met de HTTP-API voor Middelen, zijn er problemen met de codering die in het bestand wordt gebruikt (NPR-35129).

* Gebruikers van een groep die niet de machtiging heeft gekregen om verzamelingen te maken (de optie Verzameling maken is niet beschikbaar), kunnen nog steeds verzamelingen maken door rechtstreeks toegang te krijgen tot de URL `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/collections/createcollectionwizard.html/content/dam/collections?contentPath=/content/dam/collections` (NPR-35115).

* Wanneer gesorteerd op naam, worden de gezochte activa gesorteerd op case-sensitive manier. Hierdoor worden twee aparte gesorteerde lijsten gemaakt op basis van de trapsgewijze lijsten die op geordende wijze in de zoekresultaten worden weergegeven (NPR-35068).

* Wanneer een tevreden Fragment in de redacteur wordt geopend, worden de waarschuwingsberichten (`Invalid value specified for a metadata property`) het programma geopend in foutenlogboeken (NPR-35012).

* Gebruikers zonder beheerdersrechten kunnen verlopen middelen bewerken met de bureaubladtoepassing [Experience Manager]. (NPR-34993).

* Wanneer hetzelfde element in de gebruikersinterface van Elementen wordt gesleept en een nieuwe versie wordt gemaakt, zijn de wijzigingen in de metagegevens niet blijvend (NPR-34940).

* Bij het bewerken van verzamelingen kan een gebruiker de titel van de verzameling verwijderen en de wijzigingen opslaan (NPR-34889).

* Wanneer u een gedupliceerde afbeelding uploadt, wordt een verwijderingsoptie weergegeven. Als u Verwijderen selecteert, kunnen de afbeeldingen worden geüpload. DAM Update Asset workflow wordt ook geactiveerd (NPR-34744).

* Wanneer u [!DNL Adobe Asset Link] gebruikt met [!DNL Adobe InDesign], bevatten de zoekresultaten geen mappen en verzamelingen, maar bevatten deze alleen elementen (NPR-34699, CQ-4303666).

* Als u de aanwijzer op de kaartweergave plaatst, schuift het scherm als gevolg van (automatische) focus op de snelle acties die beschikbaar zijn op de kaart (NPR-34514).

* Als u de eigenschappen van meerdere elementen bulksgewijs bewerkt, wordt de weergave van de grote editor gesloten en wordt de hoofdpagina [!DNL Assets] omgeleid. [!UICONTROL Save] Dit gedrag is hetzelfde als het gedrag van de optie [!UICONTROL Save & Close] en wordt niet verwacht (NPR-34546).

* De slimme verzameling bevat na het opslaan niet de juiste instelling voor de gebruikersinterface. De vraag wordt bewaard behoorlijk maar de interface toont altijd de laatste toegevoegde predikaat van de Optie (NPR-34539).

* Wanneer u elementen toevoegt aan [!DNL Experience Manager], worden de metagegevens zonder naamruimte niet geïmporteerd (NPR-34530).

* Wanneer u middelen naar een map sleept om deze te verplaatsen, wordt in de gebruikersinterface ook de optie [!UICONTROL Drop in Lightbox] en [!UICONTROL Drop in Collection] weergegeven. Zelfs als de verplaatsingsbewerking wordt geannuleerd, worden in de gebruikersinterface de laatste twee opties weergegeven (NPR-34526).

* Het symbool `%>` wordt weergegeven op de verzamelingspagina (NPR-34499).

* In de kolomweergave worden dubbele map- en elementnamen weergegeven wanneer naar boven en naar beneden wordt geschoven voordat alle elementen worden weergegeven (NPR-34464).[!DNL Assets]

* Als u direct na het maken van een openbare map een privémap maakt, worden in de openbare map de instellingen voor de privémap gebruikt (NPR-34415).

* In de kaartweergave worden de kaarten niet in alfabetische volgorde weergegeven en kunnen kaarten niet alfabetisch worden gesorteerd (NPR-34234).

* Bij het opnieuw openen van trapsgewijze regels blijven de opties niet behouden in de gebruikersinterface (CQ-4301452).

#### [!DNL Dynamic Media] {#dynamic-media-6570}

* De volgende verbeteringen worden uitgevoerd voor toegankelijkheid in [!DNL Dynamic Media] (CQ-4290306). Zie [toegankelijkheidsfuncties in [!DNL Dynamic Media]](/help/assets/accessibility-dm.md) voor meer informatie.

   * Schermlezers (JAWS, Narrator) vertellen de naam, rol en status van de menu-items in de menuoptie Grootte insluiten (CQ-4290927).
   * Gebruikers kunnen in het dialoogvenster E-mailkoppeling navigeren met de `Tab`-toets (CQ-4290926).
   * De workflow voor het maken van videocoderingsprofielen is gebruiksvriendelijker gezien de schermlezerverbetering (CQ-4290623, CQ-4290622).
   * Wanneer u navigeert met de `Tab`-toets, gaat de focus naar de juiste gebruikersinterface-elementen in de workflow om een interactieve video te maken (CQ-4290621, CQ-4290620, CQ-4290619).
   * De pagina Publiceren, Asset-pagina bewerken, Smart Crops bewerken en de pagina Editor afbeeldingsset zijn verbeterd en voldoen nu aan de webstandaarden. Gebruikers van ondersteunende technologie (AT) kunnen nu gemakkelijk door deze pagina&#39;s navigeren en acties uitvoeren zoals het bijsnijden van afbeeldingen (CQ-4290617, CQ-4290616, CQ-4290613, CQ-4290612, CQ-49) 0610, CQ-4290614).
   * Gebruikers kunnen nu beter navigeren met een toetsenbord (CQ-4290615).
   * Gebruikers van het toetsenbord en de schermlezer kunnen de uitsnijdfunctionaliteit gebruiken (CQ-4290609).
   * Gebruikers met het toetsenbord kunnen de hotspots beter beheren (CQ-4290604, CQ-4290603).

* Externe afbeeldingen kunnen niet worden bewerkt in [!DNL Experience Manager] als de bedrijfsnaam en mapnaam gelijk zijn (NPR-31340).

* De z-indexvolgorde is onjuist wanneer u de uitvoer probeert voor te vertonen nadat u een hotspot aan een [!DNL Dynamic Media]-afbeelding hebt toegevoegd of nadat u een [!DNL Dynamic Media]-video of [!DNL Experience Fragment] met een afbeelding hebt bewerkt (CQ-4307267).

* [!DNL Dynamic Media] sync mislukt wanneer gemengde mediasets opnieuw worden verwerkt (CQ-4307184).

* Als een element wordt verplaatst naar een map waarin automatische synchronisatie naar [!DNL Dynamic Media] is geconfigureerd, wordt het element niet gesynchroniseerd (CQ-4307122).

* [!DNL Dynamic Media] video wordt niet afgespeeld op iOS-apparaten met de native HTML5-videobesturingselementen (CQ-4306977, CQ-4306727).

* Kan geen afbeeldingen downloaden waarop SmartCrop is toegepast (CQ-4304558).

* Kan mappen niet selectief publiceren naar Dynamic Media (CQ-4304526).

* Als u de publicatie van een videobestand opheft vanuit [!DNL Experience Manager], wordt de publicatie van de Adaptive Video Set niet ongedaan gemaakt op basis van een geconfigureerde Scene7-implementatie (CQ-4304405).

* Als u een panoramisch afbeeldingselement toevoegt aan een panoramisch mediacomponent en de pagina vernieuwt, treedt de fout `Uncaught ReferenceError: $ is not defined` op (CQ-4302810).

* In [!UICONTROL Viewer Presets Editor], wanneer het uitgeven [!UICONTROL PanoramicImage/PanoramicImage_VR] vooraf ingesteld, in `PanoramicView` component, is het `PANORAMICVIEW_AUTOROTATE` bepalingsetiket niet beschikbaar (CQ-4302443).

* Videobijschriften worden niet weergegeven als de video niet de eerste is in een MixedMediaSet (CQ-4298161).

* HTML5 eCatalog Viewer op mobiele apparaten met iPhones kan de pagina&#39;s niet draaien of de pagina&#39;s omdraaien (CQ-4296611).

* Wanneer u stalen op een mobiel apparaat schuift, schuiven de stalen naar rechts en uit het zichtbare gebied gedurende een paar seconden voordat u weer in beeld bladert (CQ-4296439).

* Wanneer een Voorinstelling voor viewer Master record wordt gemaakt, worden de CSS en de illustraties niet gepubliceerd en wordt alleen de voorinstelling voor viewers gepubliceerd (CQ-4262205).

* Wanneer u een ervaringsfragment probeert te koppelen voor een bepaalde hotspot in de [!UICONTROL Interactive Video/Images]-component, wordt het geselecteerde pad van het ervaringsfragment niet weergegeven. In plaats daarvan wordt een lege waarde vanuit het padveld geretourneerd (NPR-35146, CQ-4298136).

* Kan geen voorvertoning van een ervaringsfragment weergeven in de IVV Editor (CQ-4308560).

* Wanneer u een hotspot aan een afbeelding toevoegt en een ervaringsfragment selecteert, is het niet mogelijk om de submappen en de varianten van het ervaringsfragment te selecteren (CQ-4307455).

* De niet-afbeeldingselementen worden niet weergegeven zoals gepubliceerd na het uploaden (CQ-4306415).

#### [!DNL Experience Manager] 3D-elementen {#three-d-assets-6570}

* `DAM CQ MIME Type` de dienst past onjuiste MIME types op 3D activa toe die tot onjuiste teruggave leiden (NPR-34731).

### [!DNL Commerce] {#commerce-6570}

* De gebruikersinterface voor het verzamelen van handelsproducten bevat niet meer dan 15 producten binnen een collectie (NPR-34502).

### Platform {#platform-6570}

* Een HTTP-sessie via HTTPS wordt niet ongeldig gemaakt (NPR-35083).
* Een `NullPointerException` wordt geretourneerd wanneer dagelijkse of wekelijkse onderhoudstaken vanuit een gebruikersinterface worden gestart (NPR-34953).
* De W3C-validator rapporteert waarschuwingen voor compatibele JavaScript-bestanden uit de clientbibliotheek (NPR-34898).
* De functie `AudienceOmniSearchHandler` gebruikt een afgekeurde index (NPR-34870).
* Afmelden bij Experience Manager wist de cookies niet (NPR-34743).
* De functie `findByTitle` van de API `TagManager` werkt niet als de tagnaam een speciaal teken bevat (NPR-34357).
* Het proces voor het importeren van het synchronisatiepakket van de gebruiker mislukt (NPR-34399).
* Toegevoegde ondersteuning voor `ariaLabel`- en `ariaLabelledby`-eigenschappen aan de `Coral.Masonry`-component (GRANITE-29962).
* De Dispatcher-cache wordt niet vernieuwd voor pagina&#39;s met inhoudsfragmenten nadat de nieuwste kerncomponentpakketten zijn geïnstalleerd (CQ-4306788).
* Gelokaliseerde labelnamen met aanhalingstekens (`"`) worden niet correct weergegeven in de gebruikersinterface (CQ-4305439).

### Gebruikersinterface {#ui-6570}

* Het veld [!UICONTROL Link to] in componenteigenschappen geeft automatisch aangevulde suggesties weer die niet overeenkomen met de opgegeven tekenreeks (NPR-34865).

* AEM geeft het volgende foutbericht weer wanneer u een dagelijks onderhoudvenster plant dat tussen twee dagen wordt verdeeld (NPR-35280):

   ```TXT
   ERROR The start time must precede (be less than) the end time
   ```

### Integraties {#integrations-6570}

* Het bewerken van een bestaande [!DNL Adobe Launch]-configuratie mislukt (NPR-35045).
* Kan [!DNL Experience Fragments] niet exporteren naar [!DNL Adobe Target] bij gebruik van IMS-configuratie en [!DNL Adobe Target Standard]-omgeving (NPR-34555).
* De optie [!UICONTROL Create] wordt op de pagina [!UICONTROL Audiences] weergegeven bij het navigeren van een map naar de pagina [!UICONTROL Audiences] (NPR-35151).

### Sling {#sling-6570}

* De standaardlogin gezondheidscontrole bevestigt de geloofsbrieven van een gebruiker die niet bestaat (NPR-34686).

### Vertaalprojecten {#translation-6570}

* Bij het annuleren van een vertaalproject in [!DNL Experience Manager] wordt het verzoek om het te annuleren niet verzonden naar de vertaalprovider (NPR-34433).

### [!DNL Communities] {#communities-6570}

* Alle gevallen van onbillijke terminologie in het product worden vervangen door aanvaarde equivalenten (NPR-34311).
* [!DNL Google+] wordt verwijderd uit de lijst van opties voor sociale media (NPR-33877).

### [!DNL Brand Portal] {#brandportal-6570}

* De gebruikersinterface reageert niet bij het selecteren van de elementen in [!UICONTROL List View] (NPR-34728).

### [!DNL Forms] {#forms-6570}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het  [!DNL Experience Manager] Service Pack vrij.

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor  [!DNL Forms]. Zij worden geleverd gebruikend een afzonderlijk [!DNL Forms] toe:voegen-op pakket. Bovendien wordt een cumulatief installatieprogramma vrijgegeven dat moeilijke situaties voor [!DNL Experience Manager Forms] op JEE omvat. Zie [AEM Forms-invoegtoepassing installeren](#install-aem-forms-add-on-package) en [AEM Forms installeren op JEE](#install-aem-forms-jee-installer) voor meer informatie.

**Adaptieve Forms**

* Kan een adaptief formulier niet bewerken met de klassieke gebruikersinterface nadat [!DNL Experience Manager] Service Pack 6 (NPR-35126) is toegepast.

* Als u een PDF converteert naar een adaptief formulier, kunt u geen waarde instellen voor een genest deelvenster met een formuliergegevensmodel in de indeling met tabbladen. Daarnaast zijn er problemen wanneer u een waarde voor Keuzerondjesgroepen dynamisch instelt met een statische array met behulp van de code-editor (NPR-35062).

* Wanneer u Japanse tekens in een adaptieve vorm in een tekstveldcomponent invoert, kunt u meer tekens opgeven dan de maximale limiet van 35 tekens (NPR-35039).

* Het adaptieve formulier geeft ongewenste parameters weer, zoals `owner` en `status`, op de pagina **[!UICONTROL Thank you]** die wordt weergegeven na het verzenden van het formulier (NPR-34989).

* In het dialoogvenster [!UICONTROL File Selection] voor de component [!UICONTROL Attachment] worden de niet-ondersteunde bestandstypen ook weergegeven voor selectie. Dit leidt tot een fout tijdens het verzenden van het adaptieve formulier (NPR-34970).

* Wanneer u een adaptief formulier invoegt op een [!DNL Experience Manager Sites]-pagina die tekst vóór het formulier bevat, wordt de cursorfocus direct verplaatst naar het formulier in plaats van naar de tekst vóór het formulier (NPR-34947).

* [!UICONTROL Preview with Data] het vooraf invullen van een adaptief formulier met een XML-bestand met  [!DNL Experience Manager] 6.2-gegevens werkt niet correct (NPR-35087).

* Wanneer u het gegevenswoordenboek voor een adaptief formulier bijwerkt, wordt het formulier niet vertaald omdat het adaptieve formulier in de cache opgeslagen waarden retourneert (NPR-34845).

* Het laden van fragmenten in adaptieve vorm duurt langer omdat de cache ongeldig wordt (NPR-34567).

* Tabnavigatie werkt niet correct voor schermlezers in adaptieve vorm (NPR-34544).

**Correspondentenbeheer**

* Kan waarden voor XML-labels met numerieke gegevens, waaronder floattype, niet opslaan als concept (NPR-35050).

* Wanneer u de activa van ES3 migreert, omvatten de activa twee niet-editable wanbetalingsvoorwaarden (NPR-34972).

* Wanneer u een gegevenswoordenboek in een letter bewerkt, worden in de sectie [!UICONTROL Lent Content] draaiende rechthoeken weergegeven in plaats van nuttige informatie (NPR-34853).

**Interactieve communicatie**

* De naam van de rollout configuratie voor Interactieve Communicatie, beschikbaar na het installeren van [!DNL Forms] toe:voegen-op pakket, dupliceert de standaard naam van de rollout configuratie (NPR-34976).

**Documentbeveiliging**

* Wanneer u een nieuw document beveiligingsbeleid opslaat, geeft Experience Manager Forms het foutbericht `Relative validity period is required` weer (NPR-34679).

* Documentbeveiliging kan PDF 2.0-document (CQ-4305851) niet beveiligen.

Voor informatie over veiligheidsupdates, zie [pagina van de veiligheidsbulletins van de Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## [!DNL Adobe Experience Manager] 6.5.6.0. {#experience-manager-6560}

Adobe Experience Manager 6.5.6.0 is een belangrijke update die nieuwe functies, de belangrijkste door de klant gevraagde verbeteringen en prestaties, stabiliteit en beveiligingsverbeteringen bevat die worden vrijgegeven sinds de algemene beschikbaarheid van de 6.5-release in **April 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

De belangrijkste functies en verbeteringen die in Adobe Experience Manager 6.5.6.0 zijn geïntroduceerd, zijn:

* Publiceer selectief elementen naar of [!DNL Experience Manager] of [!DNL Dynamic Media] met [!UICONTROL Quick Publish] of [!UICONTROL Manage Publication] wizard.

* Gebruik de [!DNL Dynamic Media] gebruikersinterface om inhoud in cache van CDN (Content Delivery Network) ongeldig te maken.

* Het publiceren van de mappen voor middelenbijdrage van Brand Portal naar Experience Manager Assets wordt nu ook ondersteund via proxyserver.

* De automatisch gegenereerde groepen privémappen worden nu opgeschoond wanneer de privémap in [!DNL Experience Manager Assets] wordt verwijderd.

* De beschrijvingen van modifiers in video [!UICONTROL Viewer] vooraf ingestelde redacteur is bijgewerkt in [!DNL Dynamic Media].

* Een nieuw bedrijf wordt het plaatsen verstrekt om de status van [!DNL Dynamic Media] schakelaar te weerspiegelen.

* De standaardopties voor `test` en `aiprocess` worden bijgewerkt naar `Thumbnail`, van `Rasterize` eerder in Dynamic Media, om ervoor te zorgen dat gebruikers alleen miniaturen moeten maken en de pagina-extractie en uitname van trefwoorden moeten overslaan.

* [Een adaptief formulier vooraf invullen op de client](../../help/forms/using/prepopulate-adaptive-form-fields.md#prefill-at-client).

* [Integratie van formuliergegevensmodellen met RESTful-API&#39;s op een server met 2-wegs SSL-implementatie](../../help/forms/using/configure-data-sources.md).

* [Verbeterd in cache plaatsen voor vertaalde adaptieve formulierpagina](../../help/forms/using/configure-adaptive-forms-cache.md)&#39;s.

* Ondersteuning voor [Adobe Sign Text Tags in Automatede form conversion Service](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html).

* Ondersteuning voor [conversie van gekleurde formulieren naar adaptieve formulieren](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms.html) met [!DNL Automated Forms Conversion service].

* Steun voor SMB 2 en SMB 3 protocollen.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.2.2.4.

Voor een volledige lijst van eigenschappen en verhogingen die in Experience Manager 6.5.6.0 worden geïntroduceerd, zie [Nieuw in Adobe Experience Manager 6.5 Service Pack 6](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.6.0-release.

### [!DNL Sites] {#sites-6560}

* Selecteer een project in [!DNL Sites] of [!DNL Screens] en klik op [!UICONTROL Management Publications]. Gebruikers kunnen vanwege gebruikersinterfacefouten niet verder navigeren in de wizard [!UICONTROL Manage Publication]. Met name de optie [!UICONTROL Publish] werkt niet (NPR-34099).
* De positie van iParsys (Overerfd Systeem van de Paragraaf) wordt niet teruggekeerd aan zijn originele standaardpositie na het schrappen van [!UICONTROL Cancel Inheritance] of [!UICONTROL Disable Inheritance] opties (NPR-34097).
* Als `RolloutConfigManagerFactoryImpl` geen rollout config kan laden, probeert het niet om de ontbrekende vormen te laden. Het keert de caching configuraties (NPR-34092) terug.
* In de kerncomponent Text wordt na het gebruik van de HTML-bronbewerkingsoptie de klasse uit de tag `em` verwijderd (NPR-34081).
* Na het upgraden van Experience Manager 6.3.3 naar Experience Manager 6.5.3 duurt het uitrolproces veel langer en mislukt de uitrol met een time-outfout (NPR-34049).
* De `htmlwriter` codeert de kenmerkwaarden niet. De opmaak die aanwezig is in de XF-opmaak wordt geëxporteerd met gedecodeerde kenmerkwaarden (namelijk `"` in plaats van `&#34`). Het veroorzaakt kwesties op de kant van het Doel met Visuele Composer van de Ervaring die uitgevoerde XF (NPR-34048) gebruikt.
* Wanneer het bewegen van pagina&#39;s in [!DNL Experience Manager Sites], verbeter het registreren om de fout van de versieverwezenlijking met reden (NPR-34014) te vangen.
* Als in [!DNL Rich Text Editor] alle tekst wordt verwijderd, wordt het alinealabel ook verwijderd (NPR-33976).
* Wanneer de pagina `siteadmin` (in Klassieke UI) wordt geopend of verfrist, zijn de opties in `New` menu gehandicapt (NPR-33949).

   ![Screenshot om het probleem van het ontbreken van een menu in de klassieke gebruikersinterface te illustreren](assets/33949_missing_menu.png)

* Een [!DNL Content Fragment] kan niet als `TemplatedResource` worden gebruikt aangezien het in `ContentFragmentUsePojo` (NPR-33911) ontbreekt.
* Synchrone en asynchrone verplaatsingsbewerkingen kunnen leiden tot fouten als gevolg van gelijktijdige overdrachten. Verplaatsingsbewerkingen voor pagina&#39;s zijn beperkt tot alleen asynchrone verplaatsing. Hiermee wordt gelijktijdige verplaatsing van pagina&#39;s voorkomen (NPR-33875).
* [!UICONTROL Manage Publication] bewerking voor het repliceren van inhoud van de instantie Auteur naar instantie Publiceren mislukt en genereert een JavaScript-fout (NPR-33872).
* Wanneer u meerdere pagina&#39;s of middelen hebt geselecteerd om versies te maken, wordt de nieuwe versie alleen gemaakt voor de laatst geselecteerde pagina of het laatst geselecteerde element (NPR-33866).
* Verplaats een pagina met een blauwdruk met live kopieën naar een andere map. Wanneer u de afbeelding naar de oorspronkelijke map verplaatst, mislukt de verplaatsing zonder fout (NPR-33864).
* Wanneer de beweging actie wordt gebruikt om een Web-pagina in [!DNL Sites] Console anders te noemen, toont het twee overlappende dialogen bij de laatste stap van de tovenaar (NPR-33831).

   ![Screenshot ter illustratie van NPR-33831-probleem van overlappend dialoogvenster voor verplaatsen](assets/33831_rename_dialog.png)

* De eigenschappen `cq:acLinks` en `cq:acUUID` voor [!DNL Adobe Campaign] op de kopie worden tijdens kopieer- en plakbewerking verwijderd (NPR-33794).
* Wanneer het proberen van een rollout op een kindpagina van een losgemaakte levende ouder exemplaar, [!DNL Experience Manager] produceert een ongeldige wijzeruitzondering (NPR-33676).
* De [!DNL RTE] componenten in een lay-outcontainer zijn niet zichtbaar wanneer de lay-outcontainer wordt gekopieerd en opnieuw op de pagina gekleefd. De [!DNL RTE]-componenten kunnen niet worden bewerkt, maar worden wel weergegeven bij het vernieuwen van een pagina (NPR-33662).
* Wanneer u de grootte van een lay-outcomponent wijzigt voor verschillende (middelgrote en grote) onderbrekingspunten, gedraagt de lay-out zich niet zoals verwacht (NPR-33608).
* In de inline bewerkingsmodus van [!DNL RTE] werkt het slepen van een afbeelding niet voor de component Text (NPR-33602).
* Het is mogelijk om een component op een blauwdrukpagina met dezelfde naam als de paginanaam te maken. Tijdens rollout is `_msm_moved` achtervoegd om de naam van de component te wijzigen. De component wordt verplaatst naar het einde van [!UICONTROL Paragraph System] (NPR-33535).
* Wanneer offTime of onTime op vele pagina&#39;s of activa wordt geplaatst, is het middel-intensief en vertraagt het systeem tijdens opstarten en sluiting (NPR-33482).
* Een gebruiker met CRUD toestemmingen op `/content/experience-fragment` kan geen omslag schrappen (NPR-33436).
* U kunt [!UICONTROL HTML & JSON] als optie voor [!UICONTROL Adobe Target export format] op een ouderomslag in [!DNL Experience Fragments] sectie selecteren. Dezelfde eigenschappen worden weergegeven in een interface met aanraakfuncties voor de submappen van deze bovenliggende map. In CRXDE wordt voor `cq:adobeTargetExportFormat` echter alleen HTML weergegeven in plaats van `html,json` (NPR-33423) weer te geven.
* Publiceren of Publiceren ongedaan maken van een pagina-alias wordt niet ondersteund. Verwijder de optie die anders lijkt te zijn (NPR-33415).
* Een specifieke tag kan van de ene locatie naar de andere worden verplaatst in [!DNL Experience Manager]. Deze kan ook op verschillende pagina&#39;s worden toegepast vóór en na het verplaatsen. Wanneer u de eigenschappen van de pagina&#39;s bewerkt, wordt de tag niet weergegeven voor bewerking, ook al is de tag gelijk (NPR-33353).
* Een paginasjabloon wordt niet correct weergegeven wanneer een lay-outcontainer wordt verwijderd uit een sjabloon die meerdere lay-outcontainers bevat (NPR-33347).
* Probeer in de sjablooneditor een sjabloon te verwijderen die door meer dan 100000 pagina&#39;s onder `/content/` wordt gebruikt. Er wordt een fout weergegeven zonder foutbericht (NPR-33312).
* Omleiding naar pagina [!DNL Experience Manager] met anker werkt niet op instantie Auteur omdat `PageRedirectServlets` een querytekenreeks na een URL-fragment of een anker plaatst (NPR-34288).
* Als u een merk maakt onder `/content/campaign`, resulteert dit in een structuur die het niet mogelijk maakt campagnes te maken. [!UICONTROL Create Brand] blijft het nieuwe merk onveranderd  [!UICONTROL Offers and Activities] omdat er geen  [!UICONTROL Create] optie is (NPR-34113).
* U kunt de [!DNL Live Copy] van een pagina onderbreken en de overerving wordt verbroken zoals in de Editor-modus wordt getoond. In de pagina-eigenschappen geeft het pictogram dat overerving vertegenwoordigt onjuist aan dat de overerving bestaat en niet wordt verbroken (NPR-34017).
* Pagina&#39;s met veel verwijzingen kunnen niet asynchroon worden verplaatst en soms mislukt de verplaatsingsbewerking (CQ-4297969).
* Een webpagina met het teken `/` in de URL reageert niet tijdens het ontwerpen. Wanneer een component tijdens het ontwerpen wordt toegevoegd, neemt het CPU-gebruik toe en reageert de browser niet meer (CQ-4295749).
* In de modus Bladeren wordt een waarde die u in het menu Type/Grootte hebt geselecteerd, niet door NVDA van commentaar voorzien. De visuele focus is niet op het geselecteerde element. Gebruikers die op een schermlezer vertrouwen, kunnen de modus Bladeren niet gebruiken (CQ-4294993).
* Gebruikers die een webpagina maken, kunnen [!UICONTROL Content Page]-sjabloon selecteren. Op het tabblad [!UICONTROL Social Media] selecteren gebruikers een [!UICONTROL Preferred XF variation]. Gebruikers kunnen geen toetsenbordtoetsen gebruiken om een Experience Fragment in de NVDA-bladermodus te selecteren (CQ-4292669).
* De handbalkbibliotheek is bijgewerkt naar versie 4.7.3 (NPR-34484) met meer beveiliging.
* Meerdere cross-site scripting instances in [!DNL Experience Manager Sites] componenten (NPR-33925).
* Het veld Mapnaam bij het maken van een nieuwe map is kwetsbaar voor opgeslagen cross-site scripting (GRANITE-30094).
* De zoekresultaten op de pagina[!UICONTROL  Welcome] en de padvoltooiingssjabloon zijn kwetsbaar voor cross-site scripting (NPR-33719, NPR-33718).
* Als u een binaire eigenschap maakt op een ongestructureerd knooppunt, wordt naar andere sites cross-site scripting uitgevoerd op het dialoogvenster voor binaire eigenschappen (NPR-33717).
* Xxx-site scripting bij gebruik van [!UICONTROL Access Control Test] optie op de CRX DE interface (NPR-33716).
* Gebruikersinvoer wordt niet op de juiste wijze gecodeerd voor verschillende componenten bij het verzenden van informatie naar de client (NPR-33695).
* Scripts voor andere sites in de kalenderweergave voor Experience Manager Inbox (NPR-33545).
* Een URL die eindigt met `childrenlist.html` geeft een HTML-pagina weer in plaats van een 404-reactie. Dergelijke URL&#39;s zijn kwetsbaar voor cross-site scripting (NPR-33441).


### [!DNL Assets] {#assets-6560}

**Toegankelijkheidsverbeteringen in Experience Manager-elementen**

* Met de toetsenbordtoetsen kunnen gebruikers nu toegang krijgen tot de interactieve gebruikersinterfaceopties in de lijst met elementen van [!UICONTROL References] (NPR-34115).

* De schermlezer kondigt nu de bedoelde actie aan van de voorspelling op de zoekpagina (NPR-34104).

* De pagina met zoekresultaten en de pagina met zoekresultaten hebben nu meer informatieve titels voor een beter begrip van schermlezers (NPR-34093).

* Schermlezers kondigen nu de opties aan om de geselecteerde labels op het tabblad [!UICONTROL Basic] van de pagina Middelen [!UICONTROL Properties] (NPR-33972) te verwijderen.

* De elementen in elke rij in de lijstweergave worden nu door schermlezers aangekondigd als de elementen van dezelfde rij (NPR-33932).

* Wanneer de gebruiker navigeert met de `Tab`-toets, wordt nu de sluitoptie in de voorvertoning van de versie gebruikt (NPR-33863).

* De focus van de gebruiker wordt nu naar het zoekpictogram verplaatst nadat het onderzoek is gesloten (NPR-33705).

* De opties voor de gebruikersinterface die u kunt activeren, hebben nu een prominentere visuele focus met verbeterd contrast wanneer u navigeert met behulp van toetsenbordtoetsen. De gebruikers van het toetsenbord kunnen de gebieden met focus identificeren (NPR-33542).

* De sleepfunctionaliteit met het toetsenbord werkt nu in de bladermodus van schermlezers (CQ-4296326).[!UICONTROL Metadata Schema Editor]

* In het dialoogvenster voor het delen van koppelingen navigeert u in de bladermodus door een schermlezer.

   * De tabelinformatie wordt niet van commentaar voorzien zodra het dialoogvenster is geladen.

   * Kan naar alle vermelde automatische suggesties navigeren.

   * Vermeldt de weergegeven automatische suggesties voor de [!UICONTROL Add Email Address/Search] (CQ-4294232).

* Als u de toets `Esc` gebruikt om de snelactiepictogrammen uit de kaartweergave te verwijderen, wordt de toetsenbordfocus niet langer van het laatste item met focus verwijderd (CQ-4293554).

* Voor interactieve opties in de gebruikersinterface worden nu het doel van de pictogrammen door de schermlezer aangegeven in plaats van de letterlijke namen (CQ-4272943).

* De toetsenbordfocus wordt nu met succes verplaatst naar de opties [!UICONTROL Flyout], [!UICONTROL InlineZoom], [!UICONTROL Shoppable_Banner], [!UICONTROL Zoom_dark], [!UICONTROL Zoom_light], [!UICONTROL ZoomVertical_dark] en [!UICONTROL ZoomVertical_light] bij het navigeren met behulp van de Tab-toets in de elementdetails [!UICONTROL Viewers] in [!DNL Dynamic Media] (CQ-4290605).

* [!UICONTROL Save & Close] op de  [!UICONTROL Properties] elementpagina kan nu worden geopend met behulp van toetsenbordtoetsen (NPR-34107).

* Foutberichten als gevolg van onjuiste combinaties van gebruikersnaam en wachtwoord op de aanmeldingspagina worden nu door schermlezers gemeld wanneer de fout optreedt (NPR-33722).

* In de koptekstsectie [!DNL Experience Manager] kondigt de schermlezer nu bij navigatie in de bladermodus aan:

   * Suggesties die automatisch worden bewerkt in [!UICONTROL Type to search] in Omnsearch.

   * De toestand zoals deze is uitgevouwen of samengevouwen voor de opties [!UICONTROL Solutions], [!UICONTROL Help], [!UICONTROL Inbox] en [!UICONTROL User].

   * Het [!UICONTROL Searching Help] statusbericht dat wordt weergegeven wanneer de gebruiker een zoektekenreeks invoert in [!UICONTROL Search for Help] veld onder [!UICONTROL Help] optie.

   ![Menu Help in koptekst](assets/Help_aem_header.png)

   *Afbeelding:  [!UICONTROL Search for Help] in  [!UICONTROL Help] menu.*

   * Het foutbericht als in het veld [!UICONTROL Impersonate as] onder [!UICONTROL User] de optie een onjuiste waarde is ingevoerd en de focus correct naar het tekstveld wordt verplaatst (NPR-33804).

   ![Menu Gebruiker in koptekst](assets/User_aem_header.png)

   *Afbeelding:  [!UICONTROL Impersonate as] veld in  [!UICONTROL User] menu in koptekst.*

* De gebruiker kan nu de focus wijzigen met het toetsenbord binnen:

   * [!UICONTROL Search/Add Email Address] in het  [!UICONTROL Link Sharing] dialoogvenster.

   * [!UICONTROL Add User or Group] veld  [!UICONTROL Closed User Group] op het  [!UICONTROL Permissions] tabblad Map  [!UICONTROL Properties] (NPR-34452).

**In Experience Manager Assets opgeloste emissies**

[!DNL Adobe Experience Manager] 6.5.6.0  [!DNL Assets] biedt oplossingen voor de volgende problemen:

* Annotaties worden niet gemarkeerd wanneer deze worden geselecteerd in de tijdlijn van het element (CQ-4302422).

* Voorvertoning van marketingonderpandselementen (zoals brochure, Flyer en Business card) die zijn gemaakt met de sjabloon [!DNL Adobe InDesign] geeft geen regeleinden en alinea-einden weer (NPR-34268).

* Het uitnemen van tekst en dus het zoeken naar de geüploade PDF-bestanden in volledige tekst werkt niet (NPR-34164). Start de [!DNL sAdobe Experience Manager]-implementatie opnieuw nadat u Service Pack 6 hebt geïnstalleerd om dit probleem op te lossen.

* In de tijdlijn van elementen die uit meerdere pagina&#39;s bestaan, worden annotaties weergegeven die op alle subelementen zijn toegepast wanneer u in het element bladert in de tijdlijnweergave, in plaats van de annotaties weer te geven die specifiek zijn voor de specifieke subelementen (NPR-34100).

* De omslagen van activa worden niet gepubliceerd gebruikend [!UICONTROL Manage Publication] optie als de omslagen middelen in JavaScript, CSS, of JSON dossierformaten (NPR-34090) bevatten.

* Wanneer u de selectie of het verwijderen van de toegepaste tags of filters in Omnsearch opheft, wordt de zoekquery meerdere keren uitgevoerd. Dit leidt tot een langere zoektijd (NPR-34078).

* In de kaartweergave wanneer een workflow (op een middel in een map) wordt uitgevoerd of in behandeling is, wordt de pagina opnieuw geladen totdat de workflow is voltooid of beëindigd. Auteurs kunnen dan ook niet werken met die middelen in de map waarvoor ze moeten schuiven (NPR-33986).

* Als de gebruiker een gepubliceerd element naar een nieuwe locatie verplaatst, wordt het element opnieuw gepubliceerd, zelfs als de optie [!UICONTROL Republish] is uitgeschakeld. Dit leidt tot vele zwevende elementen die op de publicatie-instantie liggen. Het standaardgedrag is echter dat de publicatie van een gepubliceerd element automatisch wordt ongedaan gemaakt door de verplaatsingsbewerking. dit element wordt opnieuw gepubliceerd als de auteur de optie [!UICONTROL Republish] selecteert wanneer het element wordt verplaatst (NPR-33934).

* De pagina [!UICONTROL Move Assets] voor elementen in verzamelingen laadt niet alle HTML-inhoud, zoals de optie [!UICONTROL Adjust/ Republish]. Daarom kunnen gebruikers de verplaatsingsbewerking niet voltooien (NPR-33860).

* Als u een element verplaatst en speciale tekens toevoegt in de naam en de titel van de verplaatste elementen, wordt een extra map (met dezelfde naam) gemaakt op de nieuwe locatie van het element (NPR-33826).

* [!UICONTROL Download] wordt uitgeschakeld wanneer de  [!UICONTROL Email] optie wordt geselecteerd in het  [!UICONTROL Download] dialoogvenster (NPR-33730).

* De fout &quot;Request-URI too long&quot; wordt waargenomen bij het uitvoeren van bulkbewerkingen op elementen, zoals het bewerken van bulkmetagegevens (NPR-33723).

* Er wordt een JavaScript-fout waargenomen en gebruikers kunnen de keuzes die in [!UICONTROL Dropdown] veld worden gegenereerd door [!UICONTROL Add through JSON path] functionaliteit in [!UICONTROL Folder Metadata Schema Form Editor] niet selecteren of verwijderen als het geüploade JSON-bestand spatie of speciale tekens in waarde heeft (NPR-33712).

* De statische rendities van elementen worden niet bijgewerkt wanneer element wordt bijgewerkt met de optie [!UICONTROL Open] in [!DNL desktop app] of [!DNL Adobe Asset Link] en worden weer gesynchroniseerd naar [!DNL Adobe Experience Manager] (CQ-4296279).

* In de kolomweergave verplaatst de verplaatsingsbewerking van een set elementen ook de elementen die zijn geselecteerd voordat de optie [!UICONTROL Filter] voor deze elementen wordt gebruikt. Als u de optie [!UICONTROL Filter] gebruikt, wordt de selectie van de vorige selectie opgeheven (NPR-34018).

* Backslashes worden toegevoegd vóór speciale tekens in zoeksuggesties voor elementen, die speciale tekens in hun naam hebben (NPR-33834).

* Bij het maken van regels voor vervolgkeuzelijsten in [!UICONTROL Folder Metadata Schema Form] kan de gebruiker geen waarden selecteren uit de kolom [!UICONTROL Field Choices] (CQ-4297530).

* De runtime kopie van het aangepaste workflowmodel voor middelen (gemaakt in `/var/workflow/models/dam`) wordt verwijderd wanneer u [!DNL Experience Manager] 6.5 Service Pack 5 of een eerdere versie installeert op [!DNL Experience Manager] 6.5 (NPR-34532). Als u de runtimekopie wilt ophalen, synchroniseert u de ontwerptijdkopie van het workflowmodel met de runtimekopie met de HTTP-API:
   `<designModelPath>/jcr:content.generate.json`.

**In Dynamic Media opgeloste problemen**

* Als de gebruiker de coderingsinstellingen definieert in bewerkingen nadat het videoprofiel is gemaakt, worden de instellingen voor slimme uitsnijdingen verwijderd uit videoprofielen (CQ-4299177).

* Elementen flikkeren bij het laden van de pagina wanneer de gebruiker schakelt tussen opties voor de zijliniaal (bijvoorbeeld [!UICONTROL Overview], [!UICONTROL Timeline], [!UICONTROL Viewers]) op de pagina met elementdetails (NPR-34235).

* De volgende problemen worden waargenomen bij het opnieuw verwerken van de taak:

   * Taak-id ontbreekt in taakgreep die wordt geretourneerd door herverwerkingstaak.

   * Alleen bestandsnaam en niet volledig pad worden opnieuw verwerkt in taak voor videologboeken.

   * Herverwerkingstaak heeft geen optie om het elementtype als statisch in te stellen.

   * `ExcludeFromAVS` geen optie is opgegeven (CQ-4298401).

* De functie Slim uitsnijden mislukt met een fout wanneer een afbeeldingsprofiel wordt toegevoegd aan een map met meerdere (bijvoorbeeld 11) hoogte-breedteverhoudingen (NPR-34082).

* De workflow met DAM-updatemiddelen wordt geactiveerd wanneer de gebruiker op [!UICONTROL Workflow Archive]-pagina op [!UICONTROL Workflow]-tabblad naar [!UICONTROL Tools] schuift in [!DNL Adobe Experience Manager] geconfigureerd met Dynamic Media Scene7 (CQ-4299727).

* Symbolen op het tabblad [!UICONTROL Behavior] van [!UICONTROL Viewer Preset Editor] zijn niet gelokaliseerd (CQ-4299026).

* In de hoofdweergave wordt de afbeelding in een onjuiste lay-out weergegeven die niet in de viewer past, als de viewer in de responsieve modus staat (CQ-4298293).

* Wijzigingen in voorinstellingen voor afbeeldingen in [!UICONTROL Adobe Experience Manager] synchroniseren niet naar Scene7 Publishing System (CQ-4299713).

### [!DNL Commerce] {#commerce-6560}

* Koppelingen naar activa van producten worden niet geheroriënteerd wanneer activa worden verplaatst (NPR-34098).

### Platform {#platform-6560}

* Kan logboeken niet downloaden met het hulpprogramma Diagnosis op een geüpgrade Experience Manager-instantie (NPR-34336).
* De verbetering ontbreekt met een fout toe te schrijven aan gebiedsdelen op een specifieke versie van `cq-wcm-api` stichtingspakket (CQ-4300520).
* De standaardwaarden voor de **[!UICONTROL Connect Timeout]** en **[!UICONTROL Socket Timeout]** montages voor de configuratie Default Agent (publiceren) worden niet gespecificeerd (NPR-33707).
* Updates van de toewijzingsconfiguratie onder `/etc/map.publish` weerspiegelen niet op de sitepagina&#39;s (NPR-34015).
* [De API-referentiedocumentatie ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/package-summary.html) bevat niet de documentatie voor het  `com.day.cq.tagging` pakket (CQ-4295864).

### Gebruikersinterface {#ui-6560}

* In de interface van de browser Offloading worden niet alle taakonderwerpen weergegeven (NPR-34308).
* De [Browser van de Configuratie](/help/sites-administering/configurations.md) interface toont niet alle configuraties (NPR-33644).
* Wanneer u op de `Esc`-toets drukt terwijl u naar gebruikers zoekt om zich te laten nadoen, wordt het dialoogvenster **[!UICONTROL User]** gesloten in plaats van de gebruikerslijst (NPR-34084).

### Integraties {#integrations-6560}

* Activiteiten met lange namen worden niet gesynchroniseerd met [!DNL Adobe Target] (NPR-34254).

* Wanneer u een eigenschap selecteert terwijl u een nieuwe configuratie voor het starten van de Adobe maakt, wordt het volgende foutbericht weergegeven (NPR-33947):

   ```javascript
   GET http://hostname:Port/libs/cq/dtm-reactor/content/configurations/createcloudconfigwizard/jcr:content/body/items/form/items/wizard/items/general/items/fixedcolumns/items/container/items/general/items/property/data.html?query=&start=0&end=25&imsConfigurationId=Adobe%20Launch&companyId=&_charset_=utf-8 400 (Bad Request)
   ```

### Omzettingsprojecten {#translation-6560}

* Er wordt geen vertaalproject gemaakt als het `authorizableID` van de gebruiker speciale tekens bevat (NPR-33828).

### Sling {#sling-6560}

* Health Check en Pattern Detector hebben overlappende functionaliteit. Hierdoor wordt de gezondheidscontrole uit het product verwijderd (NPR-33928).

### WCM {#wcm-6560}

* Elementaire componenten - Wanneer u een component met een basisafbeelding aan een pagina toevoegt en naar een afbeelding verwijst, werkt de bewerking `Undo` niet (NPR-34516).

* Kan de bewerking Pagina verplaatsen niet gebruiken (CQ-4303028).

### [!DNL Communities] {#communities-6560}

* Bij het delen van een artikel op sociale media is de optie Google+ verouderd (NPR-33877).

* Lid van de Gemeenschap kan groepsmalplaatje of andere montages van de Functie van de Groep niet wijzigen (NPR-33530).

* Hyperlink-tags op afbeeldingen worden niet correct gegenereerd in een forumbericht (NPR-33464).

* Toegankelijkheidsproblemen worden geïdentificeerd in de communautaire toewijzingsfunctie (NPR-33442).

* De bestaande gebruikers van een communautaire groep die via admin console wordt toegevoegd worden verwijderd uit de gebruikerslijst op om het even welke wijziging in de communautaire groepsconsole (NPR-34315).

* De `TagFilterServlet` lekt potentieel gevoelige gegevens (NPR-33868).

<!--
* Tag filters are vulnerable to sensitive information disclosure (NPR-33868).
-->

### [!DNL Forms] {#forms-6560}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor  [!DNL Forms]. Zij worden geleverd gebruikend een afzonderlijk [!DNL Forms] toe:voegen-op pakket. Bovendien wordt een cumulatief installatieprogramma vrijgegeven dat moeilijke situaties voor [!DNL Experience Manager Forms] op JEE omvat. Zie [AEM Forms-invoegtoepassing installeren](#install-aem-forms-add-on-package) en [AEM Forms installeren op JEE](#install-aem-forms-jee-installer) voor meer informatie.

Na installatie van het [!DNL Experience Manager Forms] 6.5.6.0-invoegpakket:

* Stop de instantie [!DNL Experience Manager Forms].

* Verwijder `bcpkix-1.51`, `bcmail-1.51` en `bcprov-1.51` JAR-bestanden uit de map `crx-repository\launchpad\ext`.

* Schrap` sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider` bezit van het `sling.properties` dossier.

* Start de instantie [!DNL Experience Manager Forms] opnieuw.

**Adaptieve Forms**

* Als er een ontbrekend adaptief formulierfragment is, kan het adaptieve formulier niet worden weergegeven (NPR-34302).

* In de beschrijving van Help-inhoud voor adaptieve formuliervelden wordt een alinea-HTML-tag weergegeven (NPR-34116).

* Wanneer u de eigenschap **[!UICONTROL Revalidate on Server]** selecteert, kan het adaptieve formulier niet worden verzonden (NPR-33876).

* De verzendactie **[!UICONTROL Submit to REST endpoint]** werkt niet voor een adaptieve vorm (CQ-4299044).

* Toegankelijkheid: Wanneer u een adaptief formulier probeert te verzenden zonder een bijlage voor een verplicht veld te uploaden, wordt de focus niet automatisch naar het bijlageveld (CQ-4298065).

* Wanneer u rijen toevoegt aan een adaptieve vorm, geven de **[!UICONTROL Add to top]** en **[!UICONTROL Add to bottom]** opties geen aangewezen resultaten (CQ-4297511).

* Het script [!UICONTROL Value Commit] wordt onjuist geactiveerd, wat resulteert in gegevensverlies in een adaptieve vorm (CQ-4296874).

* De Datumkiezer werkt niet correct voor gelokaliseerde adaptieve formulieren (NPR-34333).

* Als de bestandsnaam een onderstrepingsteken of een spatie bevat, kunt u het bestand niet aan een adaptief formulier koppelen (CQ-4301001).

* Wanneer een genest herhaalbaar deelvenster meer voorvallen heeft dan het bovenliggende deelvenster, wordt het geneste herhaalbare deelvenster niet voorafgegaan (NPR-33666).

* Aangepaste formulieren hebben enkele open resourceoplossers. Deze leiden tot mislukte indiening. Het probleem doet zich af en toe voor (CQ-4299407).

* Wanneer u de veldconfiguratie voor het eerst opent, wordt het eigenschappenpictogram niet weergegeven (CQ-4296284).

* Gebruikers kunnen metagegevens voor verzending bewerken, zoals `afPath`, `afSubmissionTime` en `signers`, wanneer zij een adaptief formulier indienen. Om het probleem op te lossen, worden de metagegevenswaarden verwijderd uit de formulierverzendgegevens op de client. Gebruikers kunnen het object `FormSubmitInfo` gebruiken om deze waarden op te halen van de server (NPR-33654).

* Gebruikersinvoer wordt niet op de juiste wijze gecodeerd voor [!DNL Forms]-componenten bij het verzenden van informatie naar de client (NPR-33611).

**Workflow**

* Wanneer een werkstroomfiatteur een gehechtheid uploadt, wordt de gehechtheid anders genoemd aan `undefined` (NPR-33699).

* [!DNL Experience Manager] De werkstroom leegmaken mislukt en geeft het volgende foutbericht weer (NPR-33575):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* [!DNL Experience Manager Forms] app voor het  [!DNL Windows] stoppen met reageren na het verzenden van een formulier (NPR-34409).

* Als u AEM Service Pack installeert, wordt de lijst **Aan** met items niet weergegeven als koppelingen. De tekst voor de **To Do**-items bevat HTML-tags (NPR-34317).

**Interactieve communicatie**

* Wanneer u een tekstdocumentfragment met geneste herhaalbare componenten opneemt, kan de interactieve communicatie niet worden opgeslagen (NPR-34095).

**Correspondentenbeheer**

* Wanneer u een fragment van het tekstdocument wijzigt dat de waarden van het gegevenswoordenboek omvat, houdt UI van de Agent op antwoordend (NPR-33930).

* Inhoud kopiëren en plakken van een [!DNL Microsoft Word]-document naar een tekstdocumentfragment in een letter resulteert in opmaakproblemen (NPR-33536).

**Document Services**

* Wanneer u een PDF-bestand genereert op basis van een XDP-bestand met Output- en Forms-services, resulteert dit in ontbrekende en overlappende tekst (NPR-34237, CQ-4299331).

* Wanneer u een HTML-bestand naar PDF converteert, kan het `MaxReuseCount`-kenmerk niet worden geconfigureerd (NPR-33470).

* Wanneer u een PDF-bestand downloadt dat interactieve functies voor extensies voor Readers bevat, kunt u geen bijlage aan het PDF-bestand toevoegen met [!DNL Adobe Reader] (NPR-33729).

**Documentbeveiliging**

* Kan de ondertekeningsbewerking met op HSM gebaseerde certificaten niet uitvoeren in een PDF-bestand nadat [!DNL Experience Manager] Service Pack (NPR-34310) is geïnstalleerd.

**Designer**

* Kan XForms niet openen in Designer versie 6.5.x (CQ-4295322).

* Wanneer u Designer opent, wordt in het welkomstscherm een onjuist jaar weergegeven (CQ-4295289).

* Wanneer u [!DNL Acrobat DC] op de server installeert, is de optie **[!UICONTROL Distribute Form]** inactief (CQ-4296304).

Voor informatie over veiligheidsupdates, zie [pagina van de veiligheidsbulletins van de Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## [!DNL Adobe Experience Manager] 6.5.5.0. {#experience-manager-6550}

Adobe Experience Manager 6.5.5.0 is een belangrijke update die nieuwe functies, de belangrijkste door de klant gevraagde verbeteringen en prestaties, stabiliteit en beveiligingsverbeteringen bevat die beschikbaar zijn sinds de algemene beschikbaarheid van de 6.5-release in **April 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.5.0 zijn:

* Anonieme toegang tot CRXDE Lite is niet toegestaan. In plaats daarvan worden de gebruikers naar het aanmeldingsscherm geleid. Zie [Ontwikkelen met CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

* Pas de kolomnamen aan die in [!DNL Adobe Experience Manager] Inbox worden getoond.

* Verbeterde toegankelijkheid op diverse gebieden in het Beheer van de Inhoud van het Web van de Experience Manager (WCM) zoals de Redacteur van de Pagina, de Componenten van de Kern, RTE, en Admin gebruikersinterface.

* Sla een [!DNL Interactive Communication] op als concept.

* Ondersteuning voor [!DNL Oracle WebLogic 12] voor Experience Manager Forms op JEE.

* Verbeterde uitzonderingsbehandeling in [!DNL Adobe Experience Manager Assets] gebruikersinterfacestroom.

* Om publicatie-URL voor Dynamic Media Scene7 op te halen, wordt een nieuwe methode `getRemoteAssetPublishURL` toegevoegd aan `com.day.cq.dam.api.s7dam.scene7.ImageUrlApi`-interface.

* [Toegankelijkheidsverbeteringen ](#assets-6550) in overeenstemming  [!DNL Adobe Experience Manager Assets] met de Web Content Accessibility Guidelines (WCAG).

* Integratie met delen van pakket is verwijderd uit Adobe Experience Manager.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.22.3.

Voor een volledige lijst van eigenschappen, zeer belangrijke hoogtepunten, zeer belangrijke eigenschappen die in Experience Manager 6.5 Service Pack 5 worden geïntroduceerd, zie [Nieuw in Adobe Experience Manager 6.5 Service Pack 5](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.5.0-release.

### [!DNL Sites] {#sites-6550}

* Sites van Experience Managers biedt een optie om een pagina te publiceren of de publicatie ervan ongedaan te maken. De optie werkt niet (NPR-33415).
* Wanneer een lay-outcontainer wordt verwijderd uit een sjabloon met meerdere sjablonen, wordt de sjabloon niet correct weergegeven (NPR-33347).
* Wanneer een pagina van de Plaatsen van de Experience Manager deel van een grote inhoudset met veelvoudige levende-exemplaren uitmaakt, kan de de geschiedenisvoorproef van de paginaversie niet laden (NPR-33311).
* Wanneer u het bevel van de Beweging gebruikt om een pagina van de Plaatsen van de Experience Manager anders te noemen, wordt de paginatitel niet bijgewerkt (NPR-33264).
* Wanneer u pagina&#39;s door de kolommening beweegt, verdwijnen de kolommen (NPR-33216).
* Wanneer de naam van een lokale component in een taalkopie identiek is aan de naam van een component in het concept en de component uit blauwdruk wordt opgerold, wordt de term `_msm_moved` niet toegevoegd aan de naam van de lokale component (NPR-33208).
* De server van de Omleiding van de Pagina voegt .html aan een Experience ManagerPlaatsen URL toe waar ResourceType niet `cq:Page` (NPR-33176) is.
* Wanneer u een substructuur plakt, is er geen optie om te bepalen of corresponderende subpagina&#39;s moeten worden geplakt (NPR-33149).
* Het aantal resultaten in levend gebruik van een component is beperkt tot nummer 49 (NPR-33058).
* Wanneer u een inhoudsfragment baseert op een schema en het een verplicht tekstgebied of een weggebied bevat, kan het inhoudsfragment niet opslaan (NPR-33007).
* Wanneer u een douanecomponent creeert gebruikend de standaardcomponent van het Fragment van de Ervaring en het in de pagina&#39;s van de Plaatsen van de Experience Manager gebruikt, toont de Experience Manager geen verwijzingen (gebruik) voor de douanecomponent (NPR-32852).
* Wanneer u de naam van een map wijzigt met een groot aantal verwijzingen, worden veel verwijzingen naar de map niet bijgewerkt (NPR-32765).
* Wanneer u de optie voor bronbewerking inschakelt, wordt deze beschikbaar voor inlineopties voor volledig scherm, maar blijft deze beschikbaar voor opties voor het bewerken van het dialoogvenster en het volledige scherm van de RTF-editor (NPR-32763).
* Als u een veld met meerdere velden hebt en een vereist veld (zoals een vervolgkeuzelijst of een padveld) in de pagina-eigenschappen van een blauwdruk bevat, worden de pagina-eigenschappen van de live kopie niet opgeslagen (NPR-32751) wanneer een pagina die een dergelijk veld bevat, wordt opgerold.
* Schermlezers kunnen niet door de kopstructuur van een pagina navigeren. Bovendien heeft het tabblad Componenten het verkeerde label (NPR-32648).
* Wanneer de paginering begint, laadt de Plukker van de Fragmenten van de Ervaring niet alle punten (NPR-32605).
* Auteurmachtigingen voor het lezen, wijzigen, maken en verwijderen van live kopieën worden ingetrokken. Elke auteur moest lees- en wijzigingstoestemmingen uitdrukkelijk verstrekken om pagina&#39;s binnen een Blauwdruk (NPR-32550) te bewegen.
* Inhoudsauteurs kunnen de functie Starten niet maken voor een pagina die is geïntegreerd met Adobe Analytics (NPR-32548).
* Wanneer een gebruiker de overerving met synchronisatie hervat, synchroniseert de live kopie van de bovenliggende pagina niet met de blauwdruk en geeft deze een onjuiste status weer (NPR-32500).
* Het laden van de pagina Sites-editor voor Experience Managers duurt meer dan 15 seconden (NPR-32413).
* In bepaalde velden wordt de optie Overerving annuleren niet weergegeven (NPR-32362).
* Wanneer u een pad selecteert voor een ervaringsfragmentcomponent en het selectievakje Dialoogvenster Selectie openen inschakelt, wordt niet naar het geselecteerde pad genavigeerd in de padbrowser (NPR-32308).
* Wanneer u van Experience Manager 6.2 aan Experience Manager 6.5 bevordert, toont de component Parsys van statische malplaatjes niet correct. De hoogte van de component Parsys wordt geplaatst aan 0 en de componenten binnen het zijn niet zichtbaar (NPR-33663).
* Wanneer een gebruiker een Layout Container op dezelfde pagina kopieert en plakt, worden componenten in een Layout Container niet weergegeven (NPR-33648).
* Met de health check van de verzender wordt `Invalid cookie header` waarschuwingsbericht weergegeven in de logbestanden (NPR-33629).
* Gereflecteerde XSS in PreferencesServlet (NPR-33438).
* Anonieme gebruikers hebben toegang tot CRXDE Lite-functies (GRANITE-27790).

### [!DNL Assets] {#assets-6550}

>[!IMPORTANT]
>
>Windows-gebruikers van [!DNL Experience Manager desktop app] wordt aangeraden een upgrade uit te voeren naar [desktop app versie 2.0.3.2](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html#what-is-new) om toegang te krijgen tot de DAM-opslagruimte op [!DNL Adobe Experience Manager 6.5.5.0]-instantie. Omdat ze problemen kunnen ondervinden bij het openen van de DAM-opslagplaats op [!DNL Adobe Experience Manager] 6.5.5.0-exemplaar met de bureaubladtoepassing versie 2.0.2.

**Toegankelijkheidsverbeteringen in Experience Manager-elementen**

* Het is nu mogelijk om toetsenbordfocus op [!UICONTROL Comments] lijst en klikbare optie naar [!UICONTROL Create] versiecommentaren onder [!UICONTROL Create new version] in [!UICONTROL Timeline] paneel van activa (NPR-33424) te brengen.

* Het is nu mogelijk om [!UICONTROL View Settings] optie voor activa te bereiken en montages in [!UICONTROL View Settings] dialoog te veranderen gebruikend toetsenbordsleutels (NPR-33420).

* De keuzelijst met keuzelijsten met invoervak (in verschillende velden op verschillende pagina&#39;s) bevat nu items als een lijst met opties die door schermlezers kunnen worden aangekondigd (NPR-33516).

* De sorteerfunctionaliteit van sorteerbare koppen (in lijstweergave, [!UICONTROL Timeline] weergave en [!UICONTROL Manage Publication] pagina) wordt nu door schermlezers aangekondigd en de sorteerbesturingselementen op kolomkoppen zijn toegankelijk via het toetsenbord (NPR-32979).

* De klikbare elementen zoals commentaarkaarten, versie-updates, combodozen, en chevron pictogrammen van menu&#39;s kunnen nu worden geconcentreerd op en met het gebruiken van een toetsenbord (NPR-33514) in wisselwerking staan.

* Functionaliteit (of doel van de handeling) van inzichtspictogrammen (voor gebruik, indrukken en klikken) op [!UICONTROL Insights View] worden nu correct aangekondigd door schermlezers (NPR-33513).

* Alleen-lezen formuliervelden (bijvoorbeeld uitgeschakelde velden op [!UICONTROL Basic tab] element [!UICONTROL Properties]) kunnen nu met het toetsenbord worden geactiveerd (NPR-33493, CQ-4273031).

* Labels in verschillende invoervelden zijn nu permanente labels (dus toegankelijk) en niet alleen plaatsaanduidingslabels, die zijn verdwenen bij het invoeren van tekst (NPR-33475).

* Verschillende kopniveaus (zoals paginatitels en sectiekoppen) worden nu gezien als koppen met verschillende niveaus voor schermlezers (NPR-33471).

* Interactieve elementen in de gebruikersinterface, zoals koppelingen en opties (op koptekst- en zoomopties van de elementenpagina, mapnavigatie), zijn nu toegankelijk via een toetsenbord (NPR-33468, CQ-4271412).

* De voortgangsindicatoren [!UICONTROL Options], [!UICONTROL Scope] en [!UICONTROL Workflows] op [!UICONTROL Manage Publication] pagina worden nu correct gelezen door schermlezers als voortgangsindicatoren in plaats van tabs (NPR-33416).

* De kleur van sterrenbeoordelingspictogrammen (zoals in de sectie [!UICONTROL Rating] van [!UICONTROL Advanced] tab in element [!UICONTROL Properties] of in de kaartweergave) wordt gewijzigd, zodat het juiste contrast zichtbaar is voor gebruikers met een beperkt gezichtsveld en zonder kleurperceptie (NPR-33414).

* U kunt de pijl-omhoog naast het veld [!UICONTROL Comment] op de pagina met informatie over elementen nu openen met de toetsenbordtoetsen (NPR-33397).

* De uitgevouwen en samengevouwen status van het [!UICONTROL Tags]-dialoogvenster over de middelen [!UICONTROL Properties] en de linkerspoornavigatie (in de gebruikersinterface voor middelen) worden nu correct door schermlezers aangekondigd (NPR-33396).

* De titels van alle gebrowste pagina&#39;s op [!DNL Adobe Experience Manager] Elementen zijn nu uniek (NPR-33343).

* Bij het navigeren door boomstructuur worden verschillende elementen van het besturingselement voor de structuurweergave nu correct aangekondigd door schermlezers (NPR-33304).

* Verschillende versies van elementen in de [!UICONTROL Timeline]-weergave op de pagina met informatie over elementen zijn nu toegankelijk via de toetsenbordtoetsen (NPR-33283).

* Namen van zoeksuggesties die worden weergegeven in de keuzelijst Omnzoekopdracht worden nu door schermlezers aangekondigd wanneer ze de zoekfunctie gebruiken (NPR-33280).

* Klikbare elementen en [!UICONTROL Go to link] in [!UICONTROL References rail] worden nu door schermlezers aangekondigd als klikbare elementen (NPR-33278).

* Informatie over de tabelstructuur (zoals rij 1, cel 1, tabel) van het dialoogvenster [!UICONTROL Share Link] wordt niet meer door schermlezers aangekondigd wanneer het dialoogvenster wordt geopend (NPR-33268).

* Het doel van verschillende keuzelijstelementen (zoals het veld Pad en de optie om het dialoogvenster Selectie te openen op het tabblad Standaard van Eigenschappen van element) worden nu correct aangekondigd door schermlezers (NPR-33235).

* De informatie dat de rijen in de lijst van de lijstmening selecteerbaar zijn wordt nu meegedeeld aan de gebruikers van de schermlezer wanneer toetsenbordnadruk op hen is. Wanneer een aanwijzer op de rijen wordt geplaatst, geven de schermlezers de informatie aan (NPR-33234).

* Opties (met [!UICONTROL x]) om elke geselecteerde tag onder het veld [!UICONTROL Tags] op het tabblad [!UICONTROL Basic] van [!UICONTROL Properties] te verwijderen, zijn nu toegankelijk voor schermlezers (NPR-33206).

* Datumkiezer voor kalenderdatums kan nu worden geactiveerd en geactiveerd met het toetsenbord van schermlezers en gebruikers van waargenomen toetsenborden (NPR-33200).

* Als u schakelt tussen de lijstweergave en de kaartweergave, wordt de functionaliteit (van het aanpassen van weergaven) nu correct weergegeven voor schermlezers (NPR-33069).

* Het menu in de linkerrail is nu toegankelijk. Functionaliteit en doel van het uitbreiden van het menu worden door schermlezers op de juiste wijze aangekondigd (NPR-33068).

* De keuzelijst en veel andere gebruikersinterface-elementen zijn nu toegankelijk voor gebruikers met een niet-visuele schermlezer. De volgende informatie hierover wordt door schermlezers aangekondigd (NPR-33040):

   * of gebruikersinvoer op een element is vereist voordat het formulier wordt verzonden.
   * of een element niet bewerkbaar is.
   * of een widget is geselecteerd of niet.

* De optie om filterzijbalk te openen kan nu met het toetsenbord worden geopend (NPR-32842, CQ-4273018).

* Het besturingselement voor selectievakjes in de kolomkop van de lijstweergave is nu toegankelijk en het doel van het gebruik van het besturingselement wordt door schermlezers aangekondigd (NPR-32722, NPR-33005).

* Labels voor uren (HH) en minuten (mm) velden in de datumkiezer voor de kalenderdatum zijn nu permanente labels in plaats van plaatsaanduidingslabels en verdwijnen niet wanneer de gebruiker tekst in deze velden invoert (NPR-32720).

* De koppelingstekst van berichten (die wordt weergegeven nadat op het belpictogram is geklikt) wordt nu aangekondigd voor gebruikers van schermlezers die met Tab toegang krijgen tot elke koppeling (NPR-32645).

* [!UICONTROL Select],  [!UICONTROL Download],  [!UICONTROL Properties]en  [!UICONTROL More Actions] opties op assetkaarten in  [!UICONTROL Insights View] zijn nu toegankelijk via het toetsenbord (NPR-32609).

* Visueel verborgen inhoud (zoals de inhoud van de menubalk van de header op zoekresultaten) wordt niet meer aangekondigd door schermlezers wanneer deze toegang krijgen met het toetsenbord (NPR-32606).

* Het doel van de etiketten op besturingselementen om naar volgende en vorige maanden in een kalenderdatumkiezer te gaan, worden nu door schermlezers bekendgemaakt (NPR-32604).

* Sterrenclassificatiepictogrammen zijn nu brandbaar en kunnen worden geactiveerd met behulp van toetsenbordtoetsen (NPR-32513).

* Functionaliteit voor het regelen van het videovolume is nu toegankelijk via de Tab-toets (om de volumeschuifregelaar te activeren) en de pijltoetsen (om het volume aan te passen) op het toetsenbord (NPR-32065).

* Het doel van ondergrens ([!UICONTROL From]) en bovengrens ([!UICONTROL To]) inputgebieden van de filter van de Grootte van het Dossier wordt nu aangekondigd aan gebruikers van de niet-waargenomen het schermlezer (NPR-32064).

* Het menu [!UICONTROL Languages] in het formulier [!UICONTROL Create and Translate] is nu toegankelijk voor schermlezers in de modus Bladeren (CQ-4293906).

* Het deelvenster [!UICONTROL References] is nu toegankelijk met de volgende verbeteringen (NPR-33261, CQ-4293798):

   * In de bladermodus wordt de focus van schermlezers niet meer verplaatst naar verborgen bewerkingsvelden met meerdere regels onder de secties [!UICONTROL Site References], [!UICONTROL Asset References], [!UICONTROL Copies] en [!UICONTROL Form References].

   * Schermlezers geven nu de rol van [!UICONTROL Site References]- en [!UICONTROL Language Copies]-elementen aan.

   * De focus van schermlezers in de modus Bladeren verschuift in een betekenisvolle volgorde naar verschillende elementen.

* [!UICONTROL Metadata Schema Editor] De pagina en de elementen ervan zijn nu toegankelijk met het toetsenbord en zijn gebruiksvriendelijk voor schermlezers (CQ-4290962, CQ-4272953).

* Het doel van het symbool `X` om de geselecteerde labels te verwijderen wordt nu door schermlezers aangekondigd samen met het aantal geselecteerde tags (CQ-4273017).

* Om verwarring te voorkomen voor niet-zichtbare gebruikers die een schermlezer gebruiken, worden decoratieve pictogrammen en afbeeldingen nu genegeerd door schermlezers (CQ-4272944).

**In Experience Manager Assets opgeloste emissies**

[!DNL Adobe Experience Manager] 6.5.5.0 Middelen bieden oplossingen voor de volgende problemen:

* [!UICONTROL Start] optie op  [!UICONTROL Create Workflow] dialoog voor activa in een inzameling wordt onbruikbaar gemaakt, daardoor verhinderend werkschema om worden teweeggebracht (NPR-32471).

* Bij het gebruiken van het cascading popup in meta-gegevensschema&#39;s, bij het selecteren van en het bewaren van een drop-down optie die een apostrof (van de kinddrop-down) bevat, verdwijnt de geselecteerde apostrof optie na het heropenen van activa [!UICONTROL Properties] (NPR-32649).

* [!UICONTROL Assets Insights Sync Job] stopt en mislukt als er ongeldige items worden aangetroffen (aan de zijde Analytics) in plaats van naar de volgende vermelding te gaan (NPR-32674).

* Gyroscoop werkt niet omdat bewegingssensoren standaard zijn uitgeschakeld in mobiele browsers in panoramische viewer (CQ-4272937).

* [!UICONTROL Connected Assets Configuration] De wizard werkt niet met een fout van 404 bij de installatie van versie 6.5.3 op 6.5.1 (NPR-32730).

* Tijdens het XMP terugschrijven proces, veranderen alle eigenschappen van de meta-gegevens van douanenamespace de prefix van douanespaconruimte in ns2 in tegenstelling tot het namespaceprefix die wordt gevormd (NPR-32748).

* Lazy loading wordt niet geactiveerd en er worden slechts 100 assets weergegeven bij het selecteren om de taken te bekijken vanuit de berichten in het Postvak IN (NPR-32750).

* `NullPointerException` wordt waargenomen omdat voorkeuren voor ontbrekende knooppunten ontbreken in het nieuwe gebruikersprofiel (SAML/SSO). Deze fout verhindert nieuw het programma geopende gebruikers om [!DNL Adobe Experience Manager Stock] integratie (NPR-32777) te gebruiken.

* Traversale waarschuwingen worden waargenomen in logboeken bij het openen van een slimme verzameling die meer dan 10.000 activa bevat (NPR-32980).

* Namen van middelen worden gewijzigd in kleine letters wanneer u middelen van de ene map naar de andere verplaatst in [!DNL Adobe Experience Manager] en werkt op de Dynamic Media Scene7-runmode (NPR-32995).

* Een doorzocht middel kan niet worden geschrapt nadat aan zijn eigenschappen van de onderzoeksresultaten navigeert en dan naar onderzoeksresultaten teruggaat om het te schrappen (NPR-32998).

* [!UICONTROL Next] blijft uitgeschakeld bij het selecteren van een doelmap in de  [!UICONTROL Move Assets] interface (NPR-33356).

* [!UICONTROL Next] Deze optie is niet ingeschakeld bij het selecteren van het bovenliggende knooppunt (waar één onderliggende map zichtbaar is) en het selecteren van de onderliggende map (NPR-33275).

* De controle binnen en de controle uit toestemmingen worden onbruikbaar gemaakt op de Verbinding van Activa van Adobe (AAL) voor gebruikers met schrappingstoestemming, zelfs als andere toestemmingen zoals lezen, creëren, of wijzigen worden verleend (NPR-33272).

* Smart Crop-uitvoeringen zijn niet beschikbaar in het dialoogvenster voor het downloaden van bestanden (NPR-33167).

* Uitzondering wordt waargenomen in logboeken bij het openen van uitvoeringen per spoor voor een PDF onder een map met profiel voor slimme uitsnijdingen (CQ-4294201).

* Voorinstellingen voor afbeeldingen publiceren niet als [!UICONTROL Dynamic Media sync mode] standaard is uitgeschakeld in de Experience Manager met de Dynamic Media Scene7-runmode (CQ-4294200).

* De verwerking van bedrijfsmiddelen tijdens bulkupload blijft vastzitten en de werkstroominstantie toont vastgelopen instanties van update DAM-middelen (CQ-4293916).

* Het creëren van een configuratie van Dynamic Media op Experience Manager werkt, maar op het gebruikersinterface gebeurt niets bij het selecteren van sparen (CQ-4292442).

* Voorvertoning van F4V-video-elementen werkt niet in progressief afspelen op Safari/Mac (CQ-4289844).

* Er wordt een extra map gemaakt bij het slim uitsnijden van middelen die zich in een bovenliggende map bevinden met een punt `.`-teken in de naam (CQ-4289337).

* De miniatuur wordt verbroken en de videoverwerkingsbanner wordt niet weergegeven wanneer een video wordt gekopieerd (CQ-4284125).

* In de DIG-viewer worden in Firefox voor sommige modellen met lege cameraweergaven ten onrechte lege miniaturen weergegeven (CQ-4283447).

* De prestatieproblemen die zijn vastgelegd in 6.5.5.0 zijn (CQ-4279206):

   * Het uploaden van grote binaire bestanden naar Dynamic Media Image Processing-servers duurt te lang.

   * De tijd van de miniatuurgeneratie bij Experience Manager neemt toe vanwege de Dynamic Media Scene7-architectuur.

* Migratieproblemen met Dynamic Media Scene7 mislukken voor klanten met een groot aantal middelen (CQ-4279206).

* De lay-out van video 360-viewer wordt verbroken wanneer `setVideo` wordt gebruikt en de video wordt omlaag verplaatst bij gebruik van `video= modifier` (CQ-4263201).

* Er wordt een foutbericht weergegeven tijdens de installatie van het SDL-pakket van de Experience Manager (NPR-33175).

* SSRF-kwetsbaarheid in Experience Manager (NPR-33435).

### Platform {#platform-6550}

* Het filter [!DNL Sling] wordt niet aangeroepen als het kaartitem `sling:match` onder `/etc/maps` (NPR-33362) wordt gemaakt.
* Experience Manager loopt vast als gevolg van een segmentatiefout met [!DNL Apache Lucene] (NPR-32988).
* [!DNL Jackson] kernpakket ontbreekt in het Experience Manager uberjar-bestand (NPR-32848).
* CRXDE Lite laadt geen inhoud voor gebruikers zonder lees toestemming op `jcr:primaryType` bezit voor een knoop (NPR-32611).
* [!DNL Granite] De planner van de onderhoudstaak herinitialiseert te vaak tijdens de plaatsingen van de Experience Manager (CQ-4294627).
* Wanneer een SQL-query lang wordt uitgevoerd, bijvoorbeeld 7 uur, stopt de Experience Manager met reageren (NPR-33044).

### Gebruikersinterface {#ui-6550}

* Selectie van keuzerondjes blijft niet behouden in een multiveld (NPR-33309).
* Lazy loading limit werkt niet voor de lijstweergave (NPR-33124).
* De resultatenpagina van het onderzoek toont geen bericht als er geen gelijken (NPR-32974) zijn.
* Het filter van Onderzoek keert alle gelijken onder `/content` knoop terug die de geselecteerde plaats (NPR-32849) negeert.

### Integraties {#integrations-6550}

* De interne cache wordt gewist wanneer een pagina met een Adobe Target-component wordt gepubliceerd (NPR-33162).
* Integratie met Adobe Target werkt niet op [!DNL Windows Internet Explorer] 11 (NPR-33111).
* Bij het configureren van Adobe Target worden de velden [!UICONTROL Company] en [!UICONTROL Report Suite] niet weergegeven bij het selecteren van een rapportbron (NPR-32502).
* Wanneer u [!DNL Experience Fragments] exporteert met [!DNL Adobe I/O], worden metagegevens zoals een bronproduct niet geëxporteerd naar Adobe Target (NPR-32159).
* Erkende IMS-gebruikers in de lokale beheergroep van Experience Managers kunnen geen IMS-configuraties maken of wijzigen (NPR-33045).
* Op de pagina Startconfiguraties van Adobe worden niet alle records weergegeven (NPR-33011).
* Gebruikers in een groep van inhoudsauteurs kunnen vanwege een JavaScript-fout de eigenschappen van een Adobe Target-component niet bewerken (NPR-32996).
* Xxx-site scripting voor JSON (NPR-32744).

### Omzettingsprojecten {#translation-6550}

* Vertaalde tags worden niet geïmporteerd in de Experience Manager van vertaalservices van derden (NPR-33154).
* Op de pagina voor vertaalconfiguratie wordt een onjuiste vertaalprovider weergegeven dan de provider die wordt gebruikt voor de vertaling (NPR-32971).
* Als u een ervaringsfragmentmap toevoegt aan een bestaand vertaalproject, wordt een nieuw project gemaakt (NPR-32843).
* Een `NullPointerException` fout wordt gezien in de logboeken op het runnen van een vertaalbaan (NPR-32628).

### WCM {#wcm-6550}

* Pagina-editor - De Pagina-editor [!DNL Sites] staat gebruikers met alleen het toetsenbord niet toe om naar de hoofdinhoud te gaan in plaats van de tabfocus door alle opties in de koptekst te verplaatsen (CQ-4293883).
* Pagina-editor - Deelvensters die de component Well gebruiken en opgeslagen gegevens bevatten, worden niet weergegeven vanwege updates in [!DNL Chrome]- en [!DNL Firefox]-versies (CQ-4292995).
* MSM - Als u een component van de pagina verwijdert, wordt de component niet verwijderd uit de gepubliceerde versie van de pagina (CQ-4292360).

### [!DNL Brand Portal] {#assets-brand-portal-6550}

* Als u een gepubliceerd metagegevensschema verwijdert uit [!DNL Brand Portal], treedt er een fout op (CQ-4292063).
* Als een beheerder [!DNL Experience Manager Assets] 6.5.4 met Brand Portal via de Console van de Ontwikkelaar van de Adobe configureert, kan [!DNL Brand Portal] gebruiker niet de activa van een bijdrageomslag van [!DNL Brand Portal] aan [!DNL Experience Manager] (NPR-33046) publiceren.
* Dubbele replicatie van de bovenliggende mappen die conflicten veroorzaken (NPR-33001).

### [!DNL Communities] {#communities-6550}

* Kan een kaart in moderatieconsole niet verwijderen met de snelmenuoptie (NPR-33117).
* Er treedt een fout op bij de toegang tot de pagina [!UICONTROL Activity Stream] (NPR-33146).
* Groepen die op een instantie van de auteur worden verwijderd, worden niet uit alle publicatie-instanties verwijderd (NPR-33199).
* Auteurs worden na het maken van een nieuwe groep niet omgeleid naar de sectie [!UICONTROL Community Group] op [!DNL Internet Explorer] 11 (NPR-33205).
* De toegang tot van een bericht in Experience Manager Inbox verandert niet de status van het bericht aan Gelezen (NPR-32764).
* Als u een [!DNL Communities]-groep bewerkt en de miniatuurafbeelding wijzigt, wordt de groepminiatuurafbeelding niet bijgewerkt (NPR-32599).
* Een gebruiker kan geen e-mail naar een andere gebruiker in een gemeenschap (NPR-32598) verzenden.
* Een verzonden blog wordt pas weergegeven wanneer de gebruiker de pagina vernieuwt (NPR-32391).
* Tijdens het maken van een versie van meldingen en abonnementen op door gebruikers gegenereerde inhoud (UGC) wordt een onjuiste id van de bronpagina opgeslagen (CQ-4279355, CQ-4289703).
* Probleem met scripts die verwijzen naar andere sites (NPR-33203).

### Workflow {#workflow-6550}

* De optie [!UICONTROL Timeline] in de linkerspoorstaaf neemt meer tijd om te laden dan verwacht (NPR-32851).
* Nadat u een Experience Manager-instantie opnieuw hebt gestart, bevat de e-mail voor de overzichtstaak voor een verzameling een onjuiste payload-koppeling (NPR-32774).

### [!DNL Forms] {#forms-6550}

>[!NOTE]
>
>Experience Manager Service Pack bevat geen oplossingen voor [!DNL Forms]. Ze worden geleverd met een apart Forms-add-onpakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor AEM Forms op JEE bevat. Zie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer) voor meer informatie.

* Correspondentenbeheer: De volgorde van de activa in een doelgebied verandert na indiening van een brief (NPR-33359, NPR-33153).
* Adaptieve Forms: Wanneer een gebruiker een adaptief formulier bewerkt, werkt de optie [!UICONTROL Start Workflow] in het menu [!UICONTROL Page Information] niet (NPR-33004).
* Adaptieve Forms: De gebruiker kan geen adaptief formulier opslaan met meer dan één bijlage (NPR-32997).
* Adaptieve Forms: Als u de indeling van het deelvenster wijzigt in een adaptief formulier, treedt er een fout op (CQ-4293880).
* Adaptieve Forms: Een nieuwe regel aan een tekenreeks in een woordenboek voor adaptieve formulieren voegt `&#xa;` tekens toe aan het woordenboek (NPR-33266).
* Adaptieve toegankelijkheid voor Forms: Wanneer een gebruiker een adaptief formulier weergeeft als HTML-formulier, kan het veld [!UICONTROL Scribble Signature] de tabfocus niet behouden (NPR-33159).
* Adaptieve toegankelijkheid voor Forms: De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, zijn niet gekoppeld aan een `aria-describedBy`-kenmerk (NPR-33071).
* Adaptieve toegankelijkheid voor Forms: Velden die verplicht zijn gemarkeerd in een adaptief formulier, hebben niet het verplichte kenmerk ingesteld op Waar in het ARIA-toegankelijkheidsschema (NPR-33070).
* PDFG-service: Wanneer een gebruiker een tekstbestand naar een PDF converteert, worden Japanse tekens niet correct weergegeven (NPR-33238).
* PDFG-service: `CreatePDF`-bewerking kan een PDF-bestand niet converteren naar PDF OCR-indeling (NPR-32994).
* PDFG-service: PDF-conversie mislukt voor de 200e instantie van een [!DNL OpenOffice]-document (NPR-32766).
* BackendIntegration: De verzoeken van het het gegevensmodel van de vorm ontbreken aangezien verfrist teken wegens onjuiste inactieve staat (NPR-33169) verloopt.
* Designer: Schermlezers voeren de tabvolgorde uit op basis van de standaard geografische volgorde in plaats van de aangepaste tabvolgorde die is gedefinieerd in het XDP-bestand (NPR-32160).
* Designer: Als de optie Tags toevoegen is ingeschakeld, verdwijnt de rand van het subformulier in de gegenereerde PDF-uitvoer (NPR-32778).
* Opgeslagen XSS met GuideSOMProviderServlet (NPR-32700).

## Adobe Experience Manager 6.5.4.0 {#experience-manager-6540}

Adobe Experience Manager 6.5.4.0 is een belangrijke update die nieuwe functies bevat, belangrijke door de klant gevraagde verbeteringen en prestaties, stabiliteit en verbeteringen op het gebied van beveiliging, die zijn uitgebracht sinds de algemene beschikbaarheid van de 6.5-release in **April 2019**. Deze kan boven op Adobe Experience Manager 6.5 worden geïnstalleerd.

Enkele belangrijke functies en verbeteringen die zijn geïntroduceerd in Adobe Experience Manager 6.5.4.0 zijn:

* Adobe Experience Manager Assets is nu geconfigureerd met Brand Portal via [!DNL Adobe I/O] Console.

* Er is nu een nieuwe [Afdrukbare uitvoerstap genereren](../forms/using/aem-forms-workflow-step-reference.md) beschikbaar voor Adobe Experience Manager Forms-workflows.

* [Ondersteuning voor meerdere kolommen ](../forms/using/resize-using-layout-mode.md) voor de lay-outmodus voor adaptieve formulieren en interactieve communicatie.

* Ondersteuning voor [RTF-tekst](../forms/using/designing-form-template.md) in HTML5-formulieren.

* [Toegankelijkheidsverbeteringen ](new-features-latest-service-pack.md#accessibility-enhancements) in Experience Manager Assets.

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.8.

* U kunt selectieve inhoudsubstructuren nu synchroniseren naar *Dynamic Media - Scene7-modus* in plaats van alle beschikbare substructuren op `content/dam`.

* Integratie van formuliergegevensmodellen met SOAP-webservice ondersteunt nu keuzegroepen of kenmerken voor elementen.

* De invoer of de output van de ZEEP en complexe gegevensstructuren steunen nu Dynamische Vervanging van de Groep.

Zie [Nieuwe functies in Adobe Experience Manager 6.5 Service Packs](new-features-latest-service-pack.md) voor een complete lijst met functies en belangrijke kenmerken die zijn geïntroduceerd in de nieuwste servicepacks.

### Sites {#sites-fixes}

* Wanneer een URL van een Adobe Experience Manager Sites-pagina een dubbele punt (`:`) of percentagesymbool (`%`) bevat, stopt de browser met reageren en CPU-gebruikspieken (NPR-32369, NPR-31918).

* Wanneer een pagina van de Plaatsen van de Experience Manager voor het uitgeven wordt geopend en een component wordt gekopieerd, blijft de deegactie niet beschikbaar voor sommige placeholders (NPR-32317).

* Wanneer de wizard Publicatie beheren wordt geopend, wordt een ervaringsfragment dat is gekoppeld aan een kerncomponent niet weergegeven in de lijsten met gepubliceerde referenties (NPR-32233).

* Het overzicht van live kopieën in Touch UI duurt veel langer dan de klassieke interface die wordt weergegeven (NPR-32149).

* Wanneer de server-tijd en machine-tijd in verschillende tijdzones zijn, toont de geplande publicatietijd servertijd in Touch UI, terwijl in Klassieke UI, machinetijd wordt getoond (NPR-32077).

* Sites van Experience Managers kunnen geen pagina openen met een achtervoegsel in de URL (NPR-32072).

* Wanneer een gebruiker een inhoudsfragment bewerkt, wordt een verwijderde variant van het inhoudsfragment hersteld (NPR-32062).

* Gebruikers mogen een inhoudsfragment opslaan zonder informatie op te geven in de vereiste velden (NPR-31988).

* kernel.js en ui.js worden niet vooraf in acht genomen of in cache geplaatst. Het leidt tot extra tijd bij het teruggeven van pagina&#39;s (NPR-31891).

* Wanneer PageEventAuditListener wordt toegelaten, breidt de lengte van toe verbindt rij. Het beïnvloedt de prestaties van vele verrichtingen zoals bulkpublicaties, navigatie, bulkactivabeweging (NPR-31890).

* Wanneer de Fragmenten van de Ervaring worden gesleept, wordt de hoge reactietijd waargenomen (NPR-31878).

* Wanneer u de component van de Belemmering hier optie in ontvankelijke placeholder van het net selecteert, wordt een verzoek van de GET verzonden en het verzoek resulteert in fout HTTP 403 (NPR-31845).

* Wanneer u de inhoud binnen dezelfde map verplaatst, is de optie Pagina verplaatsen uitgeschakeld (NPR-31840).

* In de bewerkbare sjabloonstructuurmodus worden in de lijst met toegestane componenten in de lay-outcontainer onjuiste resultaten weergegeven. Alleen componenten met een dialoogvenster voor ontwerpen worden weergegeven in de lay-outcontainer (NPR-31816).

* Wanneer een pagina alleen-lezen toestemmingen voor een gebruiker heeft, is de Open eigenschappen optie zichtbaar in sites.html maar niet in editor.html (NPR-31770).

* Wanneer een gebruiker op de knop Maken klikt, is de pagina-optie niet beschikbaar (NPR-31756).

* Kan de campagne niet synchroniseren in Adobe-campagne met OOTB (Out of the box)-ontwerpimportcomponent (NPR-31728).

* Wanneer u een lijst met opsommingstekens probeert te wijzigen in een genummerde lijst, worden alleen de eerste twee items van de lijst gewijzigd (NPR-31636).

* Wanneer een pagina niet-geschreven is en het onderliggende knooppunt is geselecteerd, wordt in het dialoogvenster Selecteren nog steeds het eerste knooppunt weergegeven. Wanneer de pagina is geschreven en de gebruiker doorbladert, richt de pagina zich aan de wortelknoop in plaats van de authored knoop (NPR-31618).

* Het dialoogvenster Weergaveconfiguratie werkt niet correct voor de workflowfunctie voor het aanpassen van postvakken (NPR-32503 en NPR-32492).

* Er wordt een foutbericht weergegeven tijdens het weergeven van workflowinformatie met Inbox (CQ-4282168).

### Assets {#assets-6540-enhancements}

* De knop waarmee de workflow voor het verzamelen van elementen wordt geactiveerd, is uitgeschakeld (NPR-32471).

* Een map zonder naam wordt gemaakt in SPS (Scene7 Publishing System) en een element van de ene map naar de andere verplaatst in Experience Manager met de Dynamic Media Scene7-configuratie (NPR-32440).

* De handeling voor het verplaatsen van alle elementen (met de opdracht Alles selecteren en vervolgens verplaatsen) naar een map met gepubliceerde elementen mislukt bij fout (NPR-32366).

* Het genereren van uitvoeringen voor elementen met ${extension} mislukt (NPR-32294).

* URL&#39;s met versiegeschiedenis worden weergegeven onder Veld Verwijzing naar op de eigenschappenpagina voor elementen (NPR-31889).

* ZIP-bestand dat is gedownload van DAM, kan niet worden geopend met WinZip (NPR-32293).

* Oorspronkelijke machtigingen van een map worden bijgewerkt wanneer Mapinstellingen worden geopend om de maptitel of miniatuurafbeelding te wijzigen en vervolgens worden opgeslagen (NPR-32292).

* Het kalenderpictogram voor activering dat is gepland, wordt niet weergegeven in de kolom Status (in de klassieke gebruikersinterface van de DAM-lijst met activa) voor elementen waarvan de activering voor een latere datum en tijd is gepland (NPR-32291).

* Het maken van fragmenten met behulp van fragmentsjablonen geeft een fout op bij het zoeken naar verzamelingen tijdens het maken van fragmenten (NPR-32290).

* Meerdere zoekquery&#39;s worden geactiveerd wanneer meerdere tags zijn geselecteerd met het zoekfilter (NPR-32143).

* In de gebruikersinterface van Experience Manager Assets worden afgebroken bestandsnamen weergegeven wanneer elementen met meer dan 50 tekens in de bestandsnaam zijn geüpload (NPR-32054).

* Alle selectievakjes in het deelvenster Filter worden gewist wanneer het eerste en het tweede selectievakje worden gewist, terwijl op niveau twee selectievakjes in de boomstructuur van het selectievakje in Adobe Stock zijn ingeschakeld (NPR-31919).

* Bestanden en mapzoekopdrachten met Omnsearch-facetten geven uitzondering (NPR-31872).

* Veldmarkering voor verplichte veldselectie in de metagegevenseditor wordt niet verwijderd, zelfs niet nadat het vereiste veld is geselecteerd, wanneer de afhankelijkheidsregels zijn ingesteld in het corresponderende metagegevensschema (NPR-31834).

* Volledige namen van bladniveautags (uit de taghiërarchie) worden niet weergegeven op de pagina Eigenschappen van element (NPR-31820).

* Het gebruik van de opdracht back van de pagina Eigenschappen van element op de Safari-browser geeft een fout (NPR-31753).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* Op de elementendetailpagina van PDF-elementen worden geen actieknoppen weergegeven, behalve naar de knoppen Verzameling en Vertoning toevoegen in Experience Manager die worden uitgevoerd in de Dynamic Media Scene7-uitvoeringsmodus (CQ-4286705).

* Het duurt te lang om de batchupload van Scene7 te doorlopen (CQ-4286445).

* Met de knop Opslaan wordt de externe set niet geïmporteerd als de gebruiker geen wijzigingen heeft aangebracht in de Set Editor in de Dynamic Media Client (CQ-4285690).

* Miniatuur van 3D-elementen is niet informatief wanneer een ondersteund 3D-model in de Experience Manager wordt opgenomen (CQ-4283701).

* De onverwerkte status van de voorinstelling van de viewer voor SmartCrop wordt twee keer weergegeven op de bannertekst naast de naam van de voorinstelling (CQ-4283517).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in 3D-viewer, wordt weergegeven op de detailpagina van het element (CQ-4283309).

* De Carousel Editor wordt niet geopend in IE 11 in de modus Dynamic Media Hybrid Experience Manager (CQ-4255590).

* De toetsenbordfocus blijft vastzitten in de vervolgkeuzelijst E-mail in het dialoogvenster Downloaden, in Chrome- en Safari-browsers (NPR-32067).

* Het selectievakje Alle inhoud synchroniseren is standaard niet ingeschakeld wanneer wordt geprobeerd om DM-cloud config op Experience Manager toe te voegen (CQ-4288533).

### Foundation-UI {#foundation-ui-6540}

* Bij het zoeken van elementen met het deelvenster Filter wordt de muiscontrole verplaatst naar het vorige filterveld in plaats van in het bestaande filterveld te blijven (NPR-32538).

* Tags voor Platforms: Als u tags zoekt door in de tagvelden te typen, worden tags buiten de hoofdgrenzen weergegeven en wordt de eigenschap `rootPath` van tagvelden niet gerespecteerd (NPR-31895).

* UI Platform: Browsereinden van het pad als een ongeldig pad is toegevoegd in het tekstveld (NPR-31884).

* Melding wordt verborgen achter een plakmenu op paginaselectie (NPR-31628).

### Platform {#platform-sling-6540}

* (HTL) Onderstrepingstekens vervangen dubbele punten in de padsectie van URL (NPR-32231).

### Projecten {#projects-6540}

* De knop Maken is niet zichtbaar voor de gebruiker, zelfs niet als de gebruiker toestemming heeft om een project te maken in de submap (NPR-31832).

### Projectomzetting {#projects-translation-6540}

* Wanneer de optie Snijruimten bijsnijden is geactiveerd in `Apache Sling JSP Script Handler` (NPR-32154), wordt de interface van het vertaalproject verbroken.

* Fout in UI en Null-puntuitzondering in foutenlogboeken wordt waargenomen wanneer om het even welke te vertalen markering aan een vertaalproject (NPR-31896) wordt toegevoegd.

### Integraties {#integrations-6540}

* Het genereren van een URL-bibliotheek met opstarthandleidingen is alleen gebaseerd op de waarden `path` en `library_name` van de API voor opstarten en is niet gebaseerd op de waarde `library_path` (NPR-31550).

* Er wordt een foutbericht weergegeven tijdens het verwerken van aan LiveFyre gerelateerde items (FYR-12420).

* ReportSuitesServlet is kwetsbaar voor SSRF (NPR-32156).

### WCM-sjablooneditor {#wcm-template-editor-6540}

* In de bewerkbare sjabloonstructuurmodus wordt de lijst met toegestane componenten in de lay-outcontainer niet weergegeven met de koppelingsknopcomponent (CQ-4282099).

### WCM Pagina-editor {#wcm-page-editor-6540}

* Er is een fout opgetreden bij het selecteren van een overlay en het selecteren van responsieve rastersleepcomponenten hier (CQ-4283342).

### Campagne gericht {#campaign-targeting-6540}

* De configuratie van de doelcloud mislukt als de fout get-boxes is mislukt (CQ-4279880).

### Brand Portal {#assets-brand-portal-6540}

* Brand Portal-gebruikers kunnen bij de upgrade naar [!DNL Adobe I/O] op Experience Manager 6.5.4 (CQDOC-15655) geen middelen voor de map met bijdragen publiceren naar [!DNL Assets]. Voor een directe oplossing voor Experience Manager 6.5.4, wordt het geadviseerd [hotfix](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/hotfix/cq-6.5.0-hotfix-33041) te downloaden en op uw auteursinstantie te installeren.

* Pop-upwaarden van het metagegevensschema zijn niet zichtbaar in de elementeigenschappen (CQ-4283287).

* In het subschema Metagegevens worden geen tabbladen weergegeven op basis van MIME-typen in de eigenschappen van elementen (CQ-4283288).

* Als u het schema voor metagegevens niet publiceert, wordt een foutbericht weergegeven, maar wordt het schema op de achtergrond verwijderd.

* Voorvertoningsafbeelding wordt niet weergegeven voor een gepubliceerd element (CQ-4285886).

* De gebruiker kan activa publiceren of unpublish die enig citaat in de naam bevatten (CQ-4272686).

* De voorwaarden worden niet weergegeven tijdens het downloaden van meerdere middelen (CQ-4281224).

* Kleine beveiligingskwetsbaarheden verholpen.

### Gemeenschappen {#communities-6540}

* Het formulier Lid maken wordt weergegeven als een lege pagina (NPR-31997).

* De gebruiker kan het Analytics-rapport over de auteurinstantie (NPR-30913) niet bekijken.

### eikenindexering en vragen {#oak-indexing-6540}

* MS Word- en MS Excel-documenten met JPEG-afbeeldingen kunnen niet worden geparseerd en er is een fout opgetreden bij het parseren van een klasse die niet is gevonden (NPR-31952).

### Forms {#forms-6540}

>[!NOTE]
>
>Experience Manager Service Pack omvat geen moeilijke situaties voor Experience Manager Forms. Ze worden geleverd met een apart Forms-add-onpakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor Adobe Experience Manager Forms op JEE bevat. Zie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer) voor meer informatie.

* Correspondentenbeheer: Letters geven extra tekens weer na verzending naar workflows voor postprocessen (NPR-32626).

* Correspondentenbeheer: Bij letters wordt een tijdelijke aanduiding voor een vervolgkeuzelijst weergegeven als een tekstonderdeel na verzending naar workflows na verwerking (NPR-32539).

* Correspondentenbeheer: De standaardwaarden die in de lettertypesjabloon worden gedefinieerd, worden niet weergegeven in de voorvertoningsmodus (NPR-32511).

* Mobiele Forms: De knop Verzenden wordt weergegeven als vergroot tijdens het renderen van een XDP-formulier in een HTML-versie (NPR-32514).

* Documentservices: Problemen met URL-toegang voor Letters en enkele andere pagina&#39;s na toepassing van Service Pack 2 (NPR-32508, NPR-32509).

* Documentservices: Als het aantal transacties op een server een specifieke limiet overschrijdt, mislukt de conversie van HTML naar PDF en worden de instellingen voor het bestandstype verwijderd van de [!DNL Forms]-server (NPR-32204).

* Adaptieve Forms: Browser het hulpmiddel van de toegankelijkheid meldt mislukkingen in adaptieve vormen overeenkomstig de richtlijnen van niveau AA van WCAG2 (NPR-32312, NPR-32309, CQ-4285439).

* Adaptieve Forms: Het hulpmiddel van de de browser van Chrome rapporteert een beste praktijkmislukking (NPR-32310).

* Adaptieve Forms: Vertaalproblemen tijdens het configureren van een adaptief formulier dat is ingesloten op de pagina Sites van Experience Manager (NPR-32168).

* Workbench: Er wordt een foutbericht weergegeven wanneer de bewerking PDF-eigenschappen ophalen voor de PDF Utilities-service (NPR-32150) wordt gebruikt.

* Documentbeveiliging: Een beveiligd PDF-bestand kan niet offline worden geopend met de optie DisableGlobalOfflineSynchronizationData ingesteld op True (NPR-32078).

* Designer: Als de coderingsoptie is ingeschakeld, verdwijnt de subformulierrand in de gegenereerde PDF-uitvoer (NPR-32547, NPR-31983, NPR-31950).

* Designer: Als een tabel samengevoegde cellen bevat, mislukt de toegankelijkheidstest voor het PDF-uitvoerbestand dat is geconverteerd van een XDP-formulier met de uitvoerservice (CQ-4285372).

* Foundation JEE: Als een Experience Manager Forms-server wordt losgekoppeld van een cluster, wordt door cacheproblemen voorkomen dat deze opnieuw verbinding maakt met de server (NPR-32412).

## Adobe Experience Manager 6.5.3.0 {#experience-manager-6530}

[!DNL Adobe Experience Manager] 6.5.3.0 is een belangrijke release die prestatievermogen, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn vrijgegeven sinds de algemene beschikbaarheid van de 6.5-release in  **april 2019**. Het kan bovenop [!DNL Adobe Experience Manager] 6.5 worden geïnstalleerd.

Enkele belangrijke kenmerken van deze Service Pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.6.

* [!DNL Experience Manager Assets] ondersteunt nu ZIP-archieven die zijn gemaakt met het Deflate64-algoritme.

* Er is een nieuwe kolom voor de gemaakte datum toegevoegd aan de DAM-lijstweergave en de zoekresultaten voor elementen in de lijstweergave. Deze kolom kan worden gesorteerd.

* Asset sorting based on Name column is enabled in de mening van de Lijst.

* [!DNL Dynamic Media] ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen.

* [!DNL Dynamic Media] ondersteunt Smart Imaging.

* Mogelijkheid om [uit-van-Office](../forms/using/configure-out-of-office-settings.md) voorkeur in [!DNL Experience Manager] werkschema&#39;s te plaatsen.

* Mogelijkheid om [Inbox- of Inbox-items](../forms/using/configure-shared-queues-osgi.md) te delen met andere gebruikers in [!DNL Experience Manager]-workflows.

* Mogelijkheid om [Interactieve Mededelingen op een wijze van de Partij ](../forms/using/generate-multiple-interactive-communication-using-batch-api.md) te produceren.

* Bijgewerkte versie van jQuery die in ContextHub aan 3.4.1 wordt gebundeld.

### Activa {#assets-6530-enhancements}

**Verbeteringen voor producten**

* [!DNL Experience Manager Assets] ondersteunt nu ZIP-archieven die zijn gemaakt met het Deflate64-algoritme (NPR-27573).

* De nieuwe kolom voor gemaakte datum, die sorteerbaar is, wordt toegevoegd in de DAM-lijstweergave en in de resultaten voor het zoeken naar middelen in de lijstweergave (NPR-31312).

* In de lijstmening, kunnen de gebruikers de lijst van activa sorteren gebruikend [!UICONTROL Name] kolom (NPR-31299).

* De GLB-, GLTF-, OBJ- en STL-bestanden kunnen worden voorvertoond op de pagina [!UICONTROL Asset Details] in DAM (CQ-4282277).

* `ReplicationOnModifyListener` De gebeurtenis wordt geactiveerd voor segmentknooppunten tijdens het uploaden naar een segment in  [!DNL Dynamic Media] (CQ-4281279).

* [!DNL Dynamic Media] ondersteunt nu SmartCrop-video-elementen. Slim uitsnijden is een door computers aangedreven functie die een video bijsnijdt terwijl het frame wordt verplaatst om het brandpunt van de scène te volgen (CQ-4278995).

* [!DNL Dynamic Media] ondersteunt Smart Imaging (CQ-4222249).

* De onderzoek of doorbladert mening wordt geplaatst als standaardmening in de plukker van de Stichting als de vraagparameters in verzoek worden overgegaan (NPR-31601).

**Oplossingen**

* Metagegevens voor sommige PDF-documenten worden niet bijgewerkt en in de PDF opgeslagen wanneer de titel wordt gewijzigd (NPR-31629).

* Het delen van elementen werkt niet voor elementen die een plusteken (`+`) in de bestandsnaam hebben (NPR-31547).

* Bewerkingen in het standaardzoekformulier Middelen Admin Search Rail werken niet zoals verwacht (NPR-31502).

* Suggesties worden niet weergegeven wanneer u OmnZoeken op middelen gebruikt om middelen te zoeken (NPR-31496).

* Verwijzingen naar activa binnen verzamelingen worden niet bijgewerkt wanneer de betreffende activa naar een andere locatie worden verplaatst, in gevallen waarin naar dezelfde activa wordt verwezen door verschillende inzamelingen door verschillende gebruikers (NPR-31486).

* Er worden dubbele IPTC-tags toegevoegd aan metagegevens van elementen (NPR-31328).

* Het aantal zoekresultaten wordt niet op de juiste wijze bijgewerkt wanneer een zoekopdracht wordt gestart vanaf de filterrail (NPR-31316).

* Alle selectievakjes worden gewist wanneer de selectie van de selectievakjes van het tweede niveau in het filter Bestandstype wordt opgeheven en de tekst in de zoekbalk is niet synchroon met de geselecteerde of gedeselecteerde eigenschappen (NPR-31287).

* Niet alle leden (gebruikers/groepen) kunnen worden verwijderd uit de sectie Leden van een map. wanneer wordt geprobeerd om alle gebruikers te verwijderen, wordt de aangemelde gebruiker toegevoegd aan de lijst (NPR-31171).

* Elementen met het plusteken (`+`) in de bestandsnaam kunnen niet worden verwijderd (NPR-31162).

* Het keuzemenu Maken, dat in het bovenste menu zichtbaar is wanneer u een map selecteert, geeft &#39;Map&#39; niet weer als een optie voor maken (NPR-30877).

* De selectie van de omslag leidt tot > FileUpload actiepunt ontbreekt wanneer ACL voor ontkent `jcr:removeChildNodes` en `jcr:removeNode` op weg wordt toegepast voor een gebruiker (NPR-30840).

* De DAM-workflows worden in de status &#39;stale&#39; gezet wanneer bepaalde MP4-middelen worden geüpload, waardoor alle resterende workflows in de status &#39;stale&#39; gaan (NPR-30662).

* Er is een fout ten gevolge van onvoldoende geheugen opgetreden wanneer grote PDF-bestanden (met meerdere gigabytes) naar DAM worden geüpload en de bijbehorende subbestanden worden verwerkt (NPR-30614).

* Bulkverplaatsing van activa mislukt en geeft een waarschuwingsbericht weer (NPR-30610).

* Elementnamen worden in kleine letters gewijzigd wanneer middelen van de ene map naar de andere worden verplaatst in [!DNL Experience Manager] en worden uitgevoerd in [!DNL Dynamic Media]-Scene7-modus (NPR-31630).

* Er is een fout opgetreden tijdens het bewerken van een externe imageset voor de afbeelding die zich bevindt in de map met dezelfde naam als de bedrijfsnaam van Scene7 (NPR-31340).

* [!DNL Dynamic Media] activa met referenties worden niet gepubliceerd (NPR-31180).

* Het uploaden van [!DNL Dynamic Media]7-Scene7 mode naar [!DNL Dynamic Media Classic] duurt te lang om te voltooien (NPR-31048).

* Hotspot die aan een afbeeldingselement is toegevoegd, is niet zichtbaar via de Interactive Image Viewer op de pagina met elementdetails (NPR-30979).

* Er worden enorme slingerbanen gecreëerd en de verwerkingsbanner wordt opnieuw weergegeven wanneer acties op activa in [!DNL Experience manager Assets] worden doorgegeven aan Scene7 (NPR-30947).

* Conflict doet zich voor bij het maken van Taalkopie van middelen en middelen wordt niet geüpload naar Scene7 (NPR-30932).

* Dynamische uitvoeringen die worden gedownload van [!DNL Experience Manager] en die worden uitgevoerd in [!DNL Dynamic Media]-hybride modus, worden verbroken (het gaat om tekstype met de inhoud &#39;kan afbeelding niet vinden&#39; in plaats van het type afbeeldingsinhoud) (NPR-30876).

* [!DNL Dynamic Media] De workflow Video coderen genereert geen miniatuur voor de video die in Adobe Experience Manager van  [!DNL Dynamic Media Classic] de modus  [!DNL Dynamic Media]-Scene7 wordt gemigreerd (CQ-428/2011).

* IpsApiException werd waargenomen terwijl het migreren van activa van één geval aan een andere gebruikend verschillende het bedrijfs identiteitskaart van Scene7 (CQ-4280548).

* De miniatuur van 3D-middelen is niet informatief wanneer een ondersteund 3D-model wordt opgenomen in [!DNL Experience Manager] (CQ-4283701).

* Schuifknoppen worden weergegeven in de viewer als een 3D-element maar weinig cameraweergaven heeft (CQ-4283322).

* Onjuiste containerhoogte van een geüpload 3D-model, voorvertoond in DimensionalViewer op de pagina Asset Details (CQ-4283309).

* Video&#39;s kunnen niet worden afgespeeld met SmartCropVideoViewer in Internet Explorer 11 en Safari (CQ-4281422).

* Het gebruik van de verplaatsingsknop om meerdere elementen van de ene map naar de andere te verplaatsen, mislukt in [!DNL Experience Manager] dat wordt uitgevoerd op [!DNL Dynamic Media]-Scene7 runmode (CQ-4280384).

* Vervormde video wordt weergegeven op de elementdetails wanneer het MIME-type niet MP4 is (CQ-4279704).

* Video&#39;s die onlangs in mappen met videoprofiel zijn opgenomen, worden nog steeds verwerkt nadat het coderingspercentage is voltooid tot 100% (CQ-4279389).

* Als u elementen uit een map verplaatst, ontstaan er veel slingertaken (Scene7 API-aanroepen) die bij voorkeur vereist zijn (CQ-4278664).

* Namen van de imageset worden in Scene7 gewijzigd in kleine letters, wanneer imageset (of mediaset) wordt gemaakt en benoemd met de juiste naamgevingsconventie in DAM (CQ-4281112).

* Scene7 Migrator-sets publiceren de status onjuist (CQ-4263492).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker in Content Fragments (CQ-4282898).

* PDF-bestanden zijn niet geïndexeerd en de inhoud in deze bestanden kan niet worden doorzocht (CQ-4278916).

* Een fout &quot;Groep niet vermeld door de plukker van de gebruiker: onwaar naar verwacht gelijk aan true&quot; wordt waargenomen bij het toevoegen van een gesloten gebruikersgroep met verschillende `principalName` en `authorizableId` (CQ-4278177).

* De Mening van de Kolom UI van activa toont alle wegen ongeacht de de dampwortel van specifieke huurder weg (CQ-4278175).

* Het zoeken door de kiezer van middelen werkt niet zoals verwacht (CQ-4275886).

* Workflows voor uitvoering ontbreken (CQ-4271928).

* DAM Event Purge verwijdert de meest recente (`maxSavedActivities`) gebeurtenisgegevens en bevat de gegevens die eerder zijn gemaakt (NPR-31336).

* De resultatenpagina Touch UI-zoekopdracht (uitgevoerd via Omnissearch) wordt automatisch naar boven geschoven en verliest de schuifpositie van de gebruiker (NPR-31307).

* De actiebalk en het aantal elementen worden niet bijgewerkt wanneer u alle items selecteert en vervolgens de selectie van bepaalde items (mappen/afzonderlijke elementen) in Touch UI (NPR-31118) opheft.

* Een uitzondering wordt weergegeven in [!DNL Experience Manager] tijdens het opiniepeilen voor taakdetails van een element (CQ-4283569).

### Sites

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links naar taalkopieën weergegeven in plaats van LiveCopy-koppelingen (NPR-30980).
* Voor een nieuwe blauwdruk, als het aantal verslagen meer dan 40 is, slechts worden de eerste 40 verslagen getoond. Blauwdruk geeft lege regels weer voor de rest van de records (NPR-31182).
* Wanneer een gebruiker Japanse of Koreaanse karakters in het beschrijvingsbezit van een menu toevoegt, toont het menu vervormde karakters voor Japans en Koreaans taaltekst (NPR-31331).
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem (NPR-30879).
* Buiten het vak, de basislijn van de Rich Text Editor (RTE). past inline font-size toe op elementen, onverwacht (NPR-31284).
* Wanneer een gebruiker de linkerspoorgebieden concentreert en een toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het de inhoud van het paginageditor klembord in plaats van de inhoud die van de linkerspoorgebieden wordt gekopieerd (NPR-31172).
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden (NPR-30882).
* De `ResponsiveGridExporter`-API retourneert geen `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter`-interface. Het `com.day.cq.wcm.foundation.model.impl`-pakket wordt gedeclareerd als een privépakket (NPR-31398).

<!-- Review: NPR-31398 has fixVersion as 6530. However, it is mentioned twice in 6530 and 6520 as fixed. 
Remove one mention of this fix.
-->

* Wanneer een pagina die bepaalde fragmenten uit de ervaring bevat, wordt geopend in een niet-bewerkingsmodus (in Auteur zonder het voorvoegsel `editor.html` en `wcmmode=disabled`, of in Publisher)., eindigt de aanvraag in de HTTP-statusfoutcode `500` (NPR-30743).
* Gebruikers kunnen hun wachtwoord niet wijzigen en toegang krijgen tot hun profielpagina (NPR-31161).

### Zoeken en gebruikersinterface {#ui-interface-and-search}

* Wanneer u op een pagina met zoekresultaten overschakelt van de kaartweergave naar de lijstweergave, is er een vertraging voordat de pagina kan worden geschoven (NPR-31286).

* Het selectievakje [!UICONTROL Select All] is verborgen in de lijstweergave in [!DNL Sites] gebruikersinterface (NPR-31614).

* Het aantal [!UICONTROL Select All] op een pagina met zoekresultaten is onjuist (NPR-31120).

* In de metagegevenseditor worden tags weergegeven die niet bestaan (NPR-31119).

### Vertaling {#translation}

* Er worden twee kalenderpop-ups weergegeven bij het selecteren van de optie Einddatum in een vertaaltaak (NPR-31270).

### Platform

* De Mime typeoptie in de console van het Web werkt niet (NPR-31108).

* Clientcertificaat wordt niet geaccepteerd bij het configureren van Single Sign-On (NPR-31165).

* Updates in de configuratie van de buffergrootte voor de op Jetty-Gebaseerde dienst van HTTP worden niet bewaard (NPR-30925).

* QueryBuilder steunt nu orde `fn:name()` in xpath vragen (NPR-31322).

* Er wordt een dubbele activeringsstructuur gemaakt bij een upgrade van [!DNL Experience Manager] 6.3 (NPR-31513).

* Door:sturen verzoeken bewaren antwoordkopballen niet die tijdens het verbinden authentificatie (NPR-30013) worden geplaatst.

* Zoeken in de kiezercomponenten werkt niet (NPR-31692).

* Er wordt een fout weergegeven bij het koppelen van een ZIP-bestand aan een [!DNL Experience Manager Communities]-bericht vanwege verschillende versies van Apache POI en Apache Tika-bundel (NPR-31018).

* De bundel `org.apache.sling.distribution.api` is verborgen in de configuratiemanager en daarom niet beschikbaar aan douanesbundels (NPR-31720).

### Projecten

* Schakelen tussen kalenderweergaven werkt niet (NPR-31271).

### Brand Portal {#assets-brand-portal-6530}

**Verbeteringen voor producten**

* Workflow voor het importeren van bronnen in [!DNL Experience Manager Assets] is gewijzigd om alleen de nieuw gemaakte elementen op te halen van [!DNL Brand Portal] naar [!DNL Experience Manager] en slaat de elementen over die al in de map NEW bestaan om replicatie te voorkomen (CQ-4278527).

**Oplossingen**

* Er wordt een onjuist pictogram weergegeven bij het maken van een nieuwe map voor bijdragen in de functie voor het zoeken naar middelen (CQ-4282825).
* Bij het maken van een nieuwe Contribute-map worden een of beide submappen (NEW en SHARED) niet weergegeven in de map Contribution (CQ-4282424).
* Het systeem genereert een uitzondering als de gebruiker de map Contribution opnieuw probeert te publiceren van [!DNL Experience Manager] naar [!DNL Brand Portal] nadat hij nieuwe elementen in de map Contribution heeft ontvangen vanuit [!DNL Brand Portal] end (CQ-4279740).
* Het is niet toegestaan om een Contribute-map te maken in een map met bijdragen (geneste map) om complexiteit te voorkomen (CQ-4278391).
* Het systeem genereert een uitzondering bij het uploaden van de [!DNL Brand Portal] gebruikerslijst (.csv- dossier) die uit [!DNL Experience Manager] Admin Console wordt ingevoerd. Alleen de velden E-mail, Voornaam en Achternaam in het CSV-bestand zijn verplicht (CQ-4278390).

### Gemeenschappen {#communities-6530}

**Oplossingen**

* Snelle koppelingen voor het beheer van groepen (groepen Openen/Bewerken/Publiceren/Verwijderen) zijn niet zichtbaar voor de communautaire beheerders (beheer van groep/site) (NPR-31627).
* Een verzonden blog wordt alleen weergegeven als de pagina handmatig wordt vernieuwd of opnieuw wordt geladen (NPR-31599).
* De JCR-query die wordt gebruikt door de functie &quot;Misions&quot; is hoofdlettergevoelig en het duurt te lang om resultaten te retourneren (NPR-31475).
* [!DNL Experience Manager] 6.5 Het bestand UberJar genereert een uitzondering, er ontbreekt een  `cq-social-translation` bundel in  [!DNL Experience Manager] 6.5 UberJar-bestand (NPR-31186).
* Jackson Databind-bibliotheken bijgewerkt naar versie 2.9.9.3 om nieuwe kwetsbaarheden te verhelpen (NPR-30967).
* Activiteiten en aanmeldingstitels zijn inconsistent (NPR-30941).
* Paginering werkt niet correct in [!DNL Communities] Blogs (NPR-30914).
* Rapporten over analysemogelijkheden worden niet gevuld in de auteur- omgeving van [!DNL Experience Manager]. Er wordt een lege pagina weergegeven (NPR-30913).

### Eik {#oak}

* De indexupdates van Lucene die auteurserver veroorzaken om te vertragen (NPR-31548).

### Forms {#forms-6530}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor  [!DNL Experience Manager Forms]. Ze worden geleverd met een apart Forms-add-onpakket. Bovendien wordt een cumulatief installatieprogramma vrijgegeven dat moeilijke situaties voor [!DNL Experience Manager Forms] op JEE omvat. Zie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer) voor meer informatie.

#### Forms-invoegtoepassing {#forms-add-on-package-6530}

**Adaptieve Forms**

* Tekenreeksen bevatten de woordenboeksleutel bij het lokaliseren van adaptieve formulieren (NPR-31110).

**Interactieve communicatie**

* **MissingNode.toString()** retourneert onjuiste resultaten nadat Jackson-bibliotheken zijn bijgewerkt naar 2.10.0 (NPR-31549).

* Teksteditor verwijdert willekeurig spatietekens uit de tekst die uit Microsoft Word is gekopieerd (NPR-31113).

**Correspondentenbeheer**

* Bijschriften en knopinfo worden niet weergegeven tijdens het migreren van letters van LiveCycle ES4SP1 naar [!DNL Experience Manager] 6.5 (NPR-31615).

* **De opmaak van TextFlow wordt niet meer** ondersteund voor foutberichten wanneer letters worden opgeslagen als concepten (NPR-30463).

**Workflow**

* OSGi-workflow mislukt als gevolg van 100% CPU-gebruik (NPR-31233).

**HTML5 Forms**

* Als u HTML5-voorbeeld van een XDP-formulier genereert, wordt een flikkering weergegeven terwijl exemplaren van een subformulier worden toegevoegd (NPR-30909).

#### Forms op JEE-installatieprogramma {#forms-jee-installer-6530}

**Forms - Document Services**

* De de Webdienst van de ZEEP die MTOM in een .NET project gebruikt toont uitzonderingen voor AssemblerServiceClient aanhaalt en methodes HtmlToPDF2 (NPR-4281771).

* Beveiligingskwetsbaarheid 2012-5784 en 2014-3596 gevonden met AXIS 1.4 jar, en verhelpt deze bij [AXIS1.4.1 jar](https://helpx.adobe.com/aem-forms/quick-fixes/6-5/jee-patch-0014.html) (NPR-31015).

**Foundation JEE**

* De configuratie van de actie laadt niet de procesnamen voor het aanhalen van een Forms Workflow voorlegt actie (NPR-31478).

### Inclusief functiepakketten {#feature-packs-included-6530}

>[!NOTE]
>
>Voor [!DNL Experience Manager Forms]-klanten is het van essentieel belang om [!DNL Experience Manager Forms] add-onpakket te installeren nadat u een [!DNL Experience Manager] Service Pack, Cumulative Fix Pack of Feature Pack hebt geïnstalleerd.

#### Forms - Foundation JEE {#forms-foundation-jee-feature}

* [!DNL Experience Manager] Forms-steun voor Oracle 18c (NPR-29155).

## Adobe Experience Manager 6.5.2.0 {#experience-manager-6520}

[!DNL Adobe Experience Manager] 6.5.2.0 is een belangrijke release die prestatievermogen, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn geïntroduceerd sinds de algemene beschikbaarheid van  [!DNL Adobe Experience Manager] 6.5 in  **april 2019**. Het kan bovenop [!DNL Experience Manager] 6.5 worden geïnstalleerd.

Enkele belangrijke kenmerken van deze Service Pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.3.
* Er is een configuratie-eigenschap toegevoegd waarmee u Experience Fragments rechtstreeks kunt exporteren naar door de gebruiker gedefinieerde werkruimten voor [!DNL Adobe Target].
* Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visueel zoeken](../assets/search-assets.md#visualsearch).

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Zie [Gekoppelde elementen gebruiken](../assets/use-assets-across-connected-assets-instances.md).

* Filters van het type Document verbeteren met meer types MIME om multi-getaxeerde opties te steunen.
* Introduceerde een externe workflow voor herverwerking voor ondersteuning van meerdere bronnen.
* Geoptimaliseerde [!DNL Dynamic Media] prestaties door standaard activafilters voor replicatie te gebruiken.
* Opties voor het bewerken van middelen voor uitsnijden en roteren zijn hersteld voor DMS7.
* Een optie geïmplementeerd om een video te dempen tijdens het laden in VideoPlayer.
* Repareren om ervoor te zorgen dat de de kolommening van Activa slechts huurdersspecifieke inhoud toont.
* Oplossing voor wijzigingen in stijlaccordeon in zoekresultaten.

### Activa

**Verbeteringen voor producten**

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Hotfix voor CQ-4270245. Zie [Gekoppelde elementen gebruiken](/help/assets/use-assets-across-connected-assets-instances.md).

* [!DNL Experience Manager Assets] gebruikers kunnen visueel vergelijkbare afbeeldingen zoeken. [!DNL Experience Manager] geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visueel zoeken](../assets/search-assets.md#visualsearch).

**Oplossingen**

* Elementpaden in URL&#39;s en mapmetagegevens die door de ACS-API worden gegenereerd, worden niet via URL gecodeerd. GRANITE-26198: Hotfix voor CQ-4271814
* Het uitpakken van een archief met een map met een procentteken (%) in de naam kan niet worden geopend via de [!DNL Experience Manager Assets]-interface. NPR-29989: Hotfix voor CQ-4270467
* Aanraakinterface: Tijdens de wizard Publiceren beheren worden verwijzingen toegevoegd na de pagina in de hoofdtekst van het postverzoek, waardoor alle elementen na de pagina worden gepubliceerd. Wanneer de pagina wordt weergegeven, worden sommige elementen in de publicatieinstantie overgeslagen. NPR-29985: Hotfix voor CQ-4270724
* De functie Niet-gerelateerd element Element werkt niet voor gerelateerde elementen die speciale tekens (tekens die door URI worden gecodeerd) in de naam hebben. NPR-30387: Hotfix voor CQ-4274446
* Wanneer u een inhoudsfragment bewerkt, wordt de versie gemaakt met de verkeerde gebruiker.
* Mislukking tijdens het creëren van inzamelingen op het Gebaseerde systeem van de Aannemer. NPR-30114: Hotfix voor CQ-4272948
* De de kolommening van activa UI respecteert niet de de damwortel van de huidige huurder maar de toegang tot van alle paden van de huurdersdam. NPR-30636: Hotfix voor CQ-4275481
* Mogelijke XSS-aanval (cross-site scripting) via een beperkt waarschuwingsvenster voor bestanden, aangezien de geïnjecteerde afbeelding zichtbaar is. NPR-30617: Hotfix voor CQ-4270133
* MultiTenant: Bij huurders die mapeigenschappen opslaan, wordt zowel een melding met de succesmelding als een foutbericht weergegeven waarin de handeling wordt beschreven. &quot;Kan de eigenschappen niet bewerken. Onvoldoende rechten.&quot; dat leidt tot verwarring . NPR-30545: Hotfix voor CQ-4275333
* In het dialoogvenster Asset Selector is het selecteren van elementen niet toegestaan. De bron kan daarom niet worden bijgewerkt met de desbetreffende functie voor bronvervanging. NPR-30502: Hotfix voor CQ-4275029
* [!UICONTROL DAM Update Asset] workflow - In de status Gestreefd bij het uploaden van grote MP4-bestanden. NPR-30480: Hotfix voor CQ-4271352
* De functie Revisietaak maken werkt niet omdat de payload null is en alle volgende aan een revisie gerelateerde handelingen mislukken. NPR-30468: Hotfix voor CQ-4274263
* Verbindingsprobleem met Adobe Smart Tag via Datapower. NPR-30026: Hotfix voor CQ-4269457
* In de kolomweergave van elementen wordt een fout gegenereerd wanneer wordt geprobeerd de filters te openen zonder rails. NPR-30501: Hotfix voor CQ-4273862
* Wanneer u groepen toevoegt die via LDAP zijn gesynchroniseerd in de CUG-eigenschappen (Closed User Group) van een map Asset, wordt de groep niet opgeslagen en opgehaald. NPR-30615: Hotfix voor CQ-4274689
* De de onderzoeksstijl en richtingsgebieden van het filter passen niet de autocompleted waarde op de onderzoeksvraag toe. NPR-30620: Hotfix voor CQ-4275724
* Koppeling voor het delen van middelen van een map met spatie en &quot;&amp;&quot;-teken in de naam geeft lege grijze kaarten voor bepaalde elementen weer. NPR-30557: Hotfix voor CQ-4270187
* Het metagegevensschema van mappen detecteert het gegevenstype niet automatisch en maakt dus geen gerelateerde TypeHint in de vorm van het verzenden van formulieren. NPR-30599: Hotfix voor CQ-4275227
* Opties voor het bewerken van elementen uitsnijden en roteren zijn uitgeschakeld in de DMS7-ontwerpinterface. NPR-30118: Hotfix voor CQ-4273221
* De eigenschap van de Verbinding van het aandeel werkt niet aan [!DNL Experience Manager] instantie met configuratie DMS7. NPR-30080, NPR-30492: Hotfix voor CQ-4273651
* Wanneer u de component [!DNL Dynamic Media]-Scene7 aan de pagina toevoegt en vervolgens de pagina publiceert, wordt niet elke keer de configuratie dmscene7 geactiveerd. NPR-30641: Hotfix voor CQ-4275962
* Er is een IPSJobJournal toegevoegd in [!DNL Experience Manager] om slechts één IPS-taak (Intrusion Prevention Systems) per verwerkingsprofiel te maken. NPR-30490: Hotfix voor CQ-4273614
* [!DNL Dynamic Media]: Toegevoegde standaardfilters om uit te sluiten dat elementen worden gerepliceerd naar het  [!DNL Experience Manager] publicatieknooppunt. NPR-30538: Hotfix voor CQ-4274678
* Introduceerde een externe werkstroom van het Herproces voor multi-middelsteun om omslag als lading toe te staan. De werkstroom heeft twee stappen - verwerkt activa zonder handvatten via meta-gegevenskaart aan volgende stap opnieuw en uploadt alle activa zonder activa handvat aan S7 in één enkele IPS baan. Voor meer details, zie het Vormen [!DNL Dynamic Media] Cloud Services. NPR-30489: Hotfix voor CQ-4272903
* Het uploaden van onjuiste CSV na correcte CSV wipes uit correcte CSV. Hotfix voor CQ-4277694, CQ-4277814
* Het onjuiste pictogram dat specifiek is voor de bijdragemappen die moeten worden verwijderd. Hotfix voor CQ-4277580
* Als u een gebruiker selecteert in de gebruikerskiezer op het tabblad Asset Contribution, wordt de naam van de gebruiker niet weergegeven in de tabel en wordt in het dialoogvenster Gebruikers verwijderen op de eigenschappenpagina een onjuiste tekst weergegeven. Hotfix voor CQ-4277875
* Medewerkers kunnen niet vanuit de gebruikerskiezer worden toegevoegd aan de map Asset Contributor door een gebruiker te selecteren en op Toevoegen te klikken. Hotfix voor CQ-4277824, CQ-4278087
* Zoeken in kleine letters werkt niet in de gebruikerskiezer. Hotfix voor CQ-4277958, CQ-4277930
* Niet-beheerders kunnen elementen publiceren in een nieuwe map in de map Asset Contribution. Hotfix voor CQ-4278200
* de gebruiker van de dam (niet-admin) heeft geen optie om contribuanten aan de omslag van de inbreng van Activa toe te voegen. Hotfix voor CQ-4278192
* De knop Maken is zichtbaar in de map Asset Contribution. Hotfix voor CQ-4277560
* Als u zoekquery sorteert op relevantie, worden [!DNL InDesign]-documenten samen met [!DNL InDesign]-sjablonen geretourneerd. Hotfix voor CQ-4273864
* Als de gebruiker een e-mailadres in hoofdletters heeft, kunnen gebruikers niet inchecken voor de elementen die eerder zijn uitgecheckt. Hotfix voor CQ-4276575
* De bewerking Verwijderen is alleen van toepassing op voorinstellingen die zijn geselecteerd. Als de lijst na de bewerking automatisch wordt vernieuwd op het scherm, worden andere voorinstellingen weergegeven die al zijn vernieuwd. Hotfix voor CQ-4261461
* Als u [!DNL Dynamic Media]-Cloud Services configureert in [!DNL Dynamic Media]-hybride modus, resulteert dit in meerdere lege rapportsuites die zijn gemaakt in [!DNL Analytics] en zonder rapportsuite-id die is opgeslagen in [!DNL Experience Manager]. Dit leidt tot het dupliceren van rapportsuite. Hotfix voor CQ-4249780
* Naam van bewerking in [!DNL Experience Manager]-element wijzigen in gedupliceerde naam kan niet worden gesynchroniseerd met Scene7. Hotfix voor CQ-4276763
* Door de gebruiker gegenereerde inhoud wordt onjuist weergegeven in het deelvenster met zoekfilters. Hotfix voor CQ-4273875
* De optie Vergelijkbare zoeken is niet beschikbaar voor TIFF-afbeeldingen. Hotfix voor CQ-4278238
* Geïmplementeerde optie om video te dempen bij het laden in VideoPlayer. Hotfix voor CQ-4266465
* Viewers - VideoViewer: poster=none werkt onjuist als een externe video wordt gebruikt. Hotfix voor CQ-4265536
* Het pictogram Wachten is zichtbaar tijdens het afspelen van video in IE11- en MS Edge-browsers. Hotfix voor CQ-4251539
* 3.8 SDK- en 5.13 README-bestanden voor viewers worden niet bijgewerkt en bevatten informatie uit eerdere releases. Hotfix voor CQ-4273737
* Inhoudsfragment wordt versieeerd, zelfs voordat de wijzigingen worden opgeslagen. NPR-30616: Hotfix voor CQ-4273088
* Vervang Asset#getMetadata(String) door Asset#getMetadataValueFromJcr(String) in het miniatuurproces. NPR-30491: Hotfix voor CQ-4273067
* Bij het uploaden van jpg wordt het bericht op meerdere plaatsen weergegeven: &quot;ReplicateOnModifyWorker Replicating UPDATED&quot; voor elk element, waardoor de prestaties afnemen.
* Als u het ZIP-archief uitpakt met de functie Archiveren uitpakken, ontstaan er problemen met mappen waarvan de naam een percentage (%) in de titel bevat. NPR-29990: Hotfix voor CQ-4270467

### Sites {#sites-6520}

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links naar taalkopieën weergegeven in plaats van LiveCopy-koppelingen (NPR-30980).
* Voor een nieuwe blauwdruk worden alleen de eerste 40 records weergegeven als het aantal records groter is dan 40. Met Blueprint worden lege regels weergegeven voor de rest van de records (NPR-31182).
* Plug-in Rich Text Editor (RTE) van de tekstcomponent geeft vervormde tekens voor Japanse en Koreaanse tekst weer (NPR-31331).
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem (NPR-30879).
* De RTE (Rich Text Editor) is een onverwacht gealigneerde tekengrootte van buiten het vak en past deze onverwacht toe op elementen (NPR-31284).
* Wanneer een gebruiker de linkerspoorgebieden concentreert en toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het inhoud van pagina redacteurs klembord in plaats van de inhoud die van linkerspoorgebieden wordt gekopieerd (NPR-31172).
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden (NPR-30882).
* De `ResponsiveGridExporter`-API retourneert geen `com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter`-interface. Het `com.day.cq.wcm.foundation.model.impl`-pakket wordt gedeclareerd als een privépakket (NPR-31398).
* Wanneer een pagina met bepaalde fragmenten van de Ervaring in niet redacteurswijze (of in Auteur zonder `editor.html` prefix en `wcmmode=disabled`, of in Uitgever) wordt geopend, beëindigt het verzoek in de code van de HTTP- statusfout 500 (NPR-30743).

### WCM - Pagina-editor {#wcm-page-editor-6520}

**Verbeteringen voor producten**

* `EnhanceDocument` Typ filters met meer MIME-typen ter ondersteuning van multigetaxeerde opties. Hotfix voor CQ-4270694

### Beheer van inhoudsfragmenten {#content-fragment-management-6520}

* De query die wordt gebruikt door de gebruikersinterface van Content Fragment-modellen is erg langzaam en resulteert uiteindelijk in een fout. Hotfix voor CQ-4270807

### UI - Foundation {#ui-foundation}

* Sneltoetsen die voorkomen dat de gebruiker &#39;m,&#39; &#39;p,&#39; &#39;e&#39; gebruikt in specifieke gebruikersinterfaces. NPR-30355: Hotfix voor GRANITE-26346
* Als u [!DNL Experience Manager Assets] zoekinterface sluit, wordt de linkerrail niet opnieuw ingesteld op Content selectie, waardoor de gebruiker de filterrail niet de tweede keer kan openen. NPR-30509: Hotfix voor CQ-4274716
* Omgeving met meerdere gebruikers: [!DNL Experience Manager Assets] UI top navigation is not available and throwing JavaScript error. NPR-30104: Hotfix voor GRANITE-26344

### Vertaling {#translation-6520}

* Probleem met vertaling - Slechts een paar componenten worden vertaald met behulp van Machine Translation. NPR-30079: Hotfix voor CQ-4273764

### Platform {#platform-6520}

* [!DNL Experience Manager] De standaard afzender van de Post kan geen post naar een verre server SMTP over TLS v1.2 verzenden. NPR-30476: Hotfix voor GRANITE-26605

### Projecten {#projects-6520}

* dam:folderThumbnailPaths de waarden worden niet vernieuwd en tonen oude duimnagels zelfs na het schrappen van de activa binnen de omslag. NPR-30424: Hotfix voor CQ-4273667
* Als u de optie &quot;verplaatsen&quot; voltooit, blijven de titel en de naam van het element ongewijzigd. NPR-30647: Hotfix voor CQ-4276265

### Gemeenschappen {#communities-6520}

* Diagnostiek voor gebruikerssynchronisatie is volledig verbroken en werkt niet. NPR-30004, NPR-29943: Hotfix voor CQ-4270287, CQ-4271348

### Sling {#sling}

* De bijgewerkte instantie van 6.3.3.2 tot 6.5 resulteert in dubbele configuraties OSGi. NPR-30130: Hotfix voor CQ-4274016

### Integratie

* De aangepaste inhoud wordt pas correct weergegeven op de publicatieversie als de instantie opnieuw is gestart. NPR-30377: Hotfix voor CQ-4273706
* Wanneer u Starten op een website configureert, wordt voor het bibliotheekadres een schuine streep (/) toegevoegd, zodat u telkens handmatig kunt ingrijpen. NPR-30694: Hotfix voor CQ-4275501

### Forms {#forms-6520}

>[!NOTE]
>
>[!DNL Experience Manager] Service Pack bevat geen oplossingen voor  [!DNL Experience Manager Forms]. Zij worden geleverd gebruikend een afzonderlijk [!DNL Forms] toe:voegen-op pakket. Bovendien wordt een cumulatief installatieprogramma vrijgegeven dat moeilijke situaties voor [!DNL Experience Manager Forms] op JEE omvat. Zie [Experience Manager Forms-invoegtoepassing installeren](/help/release-notes/sp-release-notes.md#install-aem-forms-add-on-package) en [Experience Manager Forms installeren op JEE](/help/release-notes/sp-release-notes.md#install-aem-forms-jee-installer) voor meer informatie.

De belangrijkste hoogtepunten voor [!DNL Experience Manager] 6.5.2.0 vormen zijn:

* Instelling &#39;Auto&#39; toegevoegd aan `RenderAtClient` in `PDFFormRenderOptions` API voor [!DNL Experience Manager] Forms OSGi.

#### Forms-invoegtoepassing

**Back-end integratie**

* Kan het formuliergegevensmodel niet configureren met een door AWS gehoste taakgebalanceerde URL. NPR-30123: Hotfix voor CQ-4273359
* Tijdens het creëren van het Model van de Gegevens van de Vorm (FDM) met de Taal van de Definitie van de Dienst van het Web (WSDL), is het foutenbericht `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` teruggekeerd: NPR-30477: Hotfix voor CQ-4272921

**Correspondentenbeheer**

* De vertoning van de &quot;van de Correspondentie UI van de Making (CCR UI) ontbreekt periodiek met hieronder fout in console:
   `- Uncaught Error: variable [object Object]is already known the letter`- NPR-30127

**Interactieve communicatie**

* Een veld dat is gemarkeerd als vereist in het formuliergegevensmodel, wordt weergegeven als vereist in de interface Correspondentie maken (CCR UI). NPR-30623: Hotfix voor CQ-4274902

**Forms - Workflow**

* Niet-toegewezen uitvoervariabelen op Gecontroleerde mappen zorgen ervoor dat de activering mislukt. Hotfix voor CQ-4264451

**HTML5 Forms**

* Wanneer de douanecode of het project voor de tweede keer wordt opgesteld, geeft de pagina niet terug en de volgende fout komt voor:

   `org.apache.sling.scripting.sightly.SightlyException.`

   NPR-30539: Hotfix voor CQ-4272509

* Wanneer u in de modus Bladeren een HTML5-formulier leest met toegang tot niet-visuele desktops, wordt in de Chrome-browser vóór elke SVG (Scalable Vector Graphic) in het formulierontwerp &quot;graphic&quot; gelezen. NPR-30449: Hotfix voor CQ-4274732

#### Forms JEE-installatieprogramma

**Forms - Documentbeveiliging**

* Het toepassen van een handtekening met tijdstempel mislukt vanwege een fout: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Inroepfout. NPR-30820: Hotfix voor CQ-4275852

**Forms - Document Services**

* Als &quot;SubmitURL&quot;een ampersand (&amp;) bevat, worden de ontledingsfouten gezien in het logboek wanneer het verzoek van de POST aan `renderpdf` servlet wordt gemaakt. NPR-30865: Hotfix voor CQ-4278232

**Forms - Foundation JEE**

* De HTMLtoPDF-service geeft maxReuseCount niet weer in de JMX-console. NPR-30134, NPR-30304: Hotfix voor CQ-4273763
* Als u een verbinding met een webservice toevoegt of bewerkt door webservices op te roepen vanuit Workbench, treedt er een fout op: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. [!DNL Experience Manager Forms] NPR-30105: Hotfix voor CQ-4273217

### Inclusief functiepakketten

>[!NOTE]
>
>Voor [!DNL Experience Manager Forms]-klanten is het van essentieel belang om [!DNL Experience Manager Forms] add-onpakket te installeren nadat u een [!DNL Experience Manager] Service Pack, Cumulative Fix Pack of Feature Pack hebt geïnstalleerd.

#### Sites {#sites-feature-packs-included}

* Er is een configuratie-eigenschap toegevoegd waarmee u Experience Fragments rechtstreeks kunt exporteren naar door de gebruiker gedefinieerde werkruimten voor [!DNL Adobe Target]. NPR-29189: Hotfix voor CQ-4249782

#### Forms - Document Services {#forms-document-services-1}

* Instelling &#39;Auto&#39; toegevoegd aan `RenderAtClient` in `PDFFormRenderOptions` API voor [!DNL Experience Manager Forms] OSGi. NPR-30759: Hotfix voor CQ-4278193

## Adobe Experience Manager 6.5.1.0 {#experience-manager-6510}

[!DNL Adobe Experience Manager] 6.5.1.0 is een belangrijke release die prestatievermogen, stabiliteit, beveiliging en belangrijke correcties en verbeteringen voor klanten bevat die zijn geïntroduceerd sinds de algemene beschikbaarheid van  [!DNL Adobe Experience Manager] 6.5 in  *april 2019.* Het kan bovenop  [!DNL Experience Manager] 6.5 worden geïnstalleerd.

Enkele belangrijke kenmerken van deze Service Pack-release zijn:

* De opname van de status dynamic-UI in het bijhouden van gebeurtenissen als aangepaste kenmerken ingeschakeld.
* Inclusief ondersteuning voor de levering van video-elementen van 360 graden in de modus [!DNL Dynamic Media]-Scene7.
* De functie *Japanse tekstomloop* is ingeschakeld via de stijlplug-in van de Rich Text Editor. Zie [Japanse tekstomloop configureren](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap) voor meer informatie

### Activa

* Bijgewerkte interface DAM DMGateway voor S3 multipart steun. NPR-29740: Hotfix voor CQ-4226303
* In de voorvertoning van uitvoeringen wordt `Only empty tenantId is currently supported`-fout gegenereerd na de upgrade naar [!DNL Experience Manager] 6.5. NPR-29986: Hotfix voor CQ-4272353
* Dialoogvenster Verwijderen is niet zichtbaar om het verwijderen van taken toe te staan. NPR-29720: Hotfix voor CQ-4271074
* Nadat een elementtitel aan de eigenschappenpagina is toegevoegd en een gebruiker de pagina probeert te sluiten, wordt [!DNL Experience Manager] de eigenschappenpagina weer geopend. NPR-29627: Hotfix voor CQ-4264929
* VersioningTimelineEventProvider moet een hoofdversie leveren samen met het knooppunt van het type nt: versie. Hotfix voor GRANITE-26063
* Implementeerde de mogelijkheid om 360 sferische video&#39;s te uploaden en af te spelen in de DM-Scene7-modus. [!DNL Experience Manager] Hotfix voor CQ-4265131
* Met Live kopie wordt een onjuiste status opgehaald als de bron wordt bewerkt. Hotfix voor CQ-4265451
* Ondersteuning voor beheer van meerdere sites ingeschakeld voor [!DNL Experience Manager Assets]. Hotfix voor CQ-4271453, CQ-4268621, CQ-4257491
* [!DNL Experience Manager] een extra item voor de huidige versie van het element in de tijdlijngeschiedenis weer te geven, waarbij de laatste incheckopmerking van  [!DNL Adobe Asset Link]wordt weergegeven. Hotfix voor CQ-4262864
* In de tijdlijn van het inhoudsfragment wordt een foutbericht weergegeven wanneer eigenschappen ontbreken. Hotfix voor CQ-4272560
* Dit is een probleem met Scene7-videospeler wanneer deze wordt uitgevouwen tot volledig scherm. Hotfix voor CQ-4266700
* ZoomVerticalViewer: Panknoppen mogen niet worden weergegeven als één afbeeldingselement wordt gebruikt. Hotfix voor CQ-4264795
* Wanneer u een onderliggende node in de live kopie verwijdert, moet de liveRelationship worden losgekoppeld. Hotfix voor CQ-4270395
* Het meta-gegevensschema bevat slechts punten van de globale configuratie en mist degenen van de actieve huurder. De URL-waarde van het formPath wordt weer ingesteld op de standaardwaarde, zelfs als deze wordt gewijzigd. NPR-29945: Hotfix voor CQ-4262898
* Publiceren van voorinstellingen voor afbeeldingen naar [!DNL Brand Portal] mislukt met 500 foutcode. NPR-29510: Hotfix voor CQ-4268659

### Sites

* Lege eigenschappen en meerdere eigenschappen verspreiden zich niet van blauwdruk tijdens de rollout. Actieve kopie herstellen met blauwdruk werkt niet voor componenten. NPR-29253: Hotfix voor CQ-4264928, CQ-4264926, CQ-4267722
* CoralUI, wanneer gebruikt met `Multifield`, slaat `fileReferenceParameter` op componentenniveau in plaats van multifield niveau op. NPR-29537: Hotfix voor CQ-4266129
* Verbetering van tekstcomponent [!DNL Experience Manager] en teksteditor naar Japans. NPR-29785: Hotfix voor CQ-4265090
* De pagina die wordt teruggezet met Timewarp, moet naar het correcte beeld op het tijdstip van versioning verwijzen. NPR-29431: Hotfix voor CQ-4262638
* An issue with the inheritance of Style System nodes from parent to child. NPR-29516: Hotfix voor CQ-4270330
* Een foutbericht tijdens het instellen van het sociaal posten naar [!DNL Facebook]-verificatie. NPR-29211: Hotfix voor CQ-4266630
* De weergegeven miniatuur op Inhoudsfragment toont de interne kalenderrepresentatie voor het veld Datum en tijd. NPR-29531: Hotfix voor CQ-4269362
* De knoppen worden niet weergegeven wanneer u het tabblad met machtigingen opent in de implementatie van Coral2. Hotfix voor CQ-4269419

### Handel

* RestrictionViolationException, when running lazy content migration for e-commerce. NPR-29247: Hotfix voor CQ-4264383

### Beheer van inhoudsfragmenten

* Parseerfout bij het openen van een inhoudsfragment met de tekens `($)` en accolade openen `({)`. Hotfix voor CQ-4270266

### Ervaringsfragmenten

* Exporteer [!DNL Experience Manager] Experience Fragments naar [!DNL Adobe Target]. Hotfix voor CQ-4265469
* De uitvoer van de Fragmenten van de ervaring naar doel ontbreekt met slimme beeld. Hotfix voor CQ-4269606

* De gebruiker raakt een doodlopende weg wanneer het proberen om de Fragmenten van de Ervaring door Onderzoek in kaartmening te bewegen. Hotfix voor CQ-4263848

### WCM - Pagina-editor

* Gespiegeld XSS (Cross-site scripting) bij gebruik van een ongeldige kiezer. Hotfix voor CQ-4270397

### Replicatie

* Door de gebruiker opgegeven gegevens worden niet beschermd bij uitvoer in de `cq/replication/components/agent`-component, wat resulteert in een opgeslagen XSS-kwetsbaarheid (Cross-site scripting). Hotfix voor CQ-4266263

### Workflow

* Het veld Kalenderkiezer van deelnemer in dialoogvenster is verbroken. NPR-29727: Hotfix voor CQ-4270423

### WCM - SPA Editor

* Toegelaten het halen van pre-teruggegeven inhoud van een ver eindpunt. Hotfix voor CQ-4270238
* Waarschuwingen in logbestanden bij het openen van een SPA Sjabloonpagina die op de server wordt weergegeven. Hotfix voor CQ-4270238

### WCM - MSM

* Als u een upgrade uitvoert naar [!DNL Experience Manager] 6.4.3, duurt het lang voordat u de functie voor beheer van meerdere sites kunt uitvoeren. Hotfix voor CQ-4271410

### Integratie

* BrightEdge-referenties zijn mislukt vanwege een verbindingsfout. NPR-29168: Hotfix voor CQ-4265872

* Een uitzonderingsbericht wordt getoond wanneer het proberen om [!DNL Experience Manager] lanceringsconfiguratie uit te geven en te bewaren. NPR-29176: Hotfix voor CQ-4265782/CQ-4266153

### Gebruikersinterface

* Toegevoegde ondersteuning voor het bijhouden van dynamische UI-statussen als aangepaste kenmerken bij het bijhouden van bepaalde gebeurtenissen in de API voor het bijhouden van stichtingen. Hotfix voor GRANITE-26283
* Kan de functie voor bijhouden niet instellen op de verzendknop. Hotfix voor GRANITE-26326
* De wizard kan de functie voor bijhouden niet instellen op de verzendknop. NPR-29995, NPR-30025: Hotfix voor CQ-4264289

### Gemeenschappen

* Kan geen nieuwe badges uitlijnen in de vervolgkeuzelijst op de pagina voor het lidprofiel. NPR-29381: Hotfix voor CQ-4267987
* Bezoekers en leden zonder moderatorrechten kunnen niet-goedgekeurde/hangende berichten zien door de URL te plakken. NPR-29724: Hotfix voor CQ-4271124, CQ-4271441
* Hoge responstijd tot 40-50 seconden wordt waargenomen bij het aanmelden bij de gebruiker voor de Gemeenschap. NPR-29677: Hotfix voor CQ-4269444

### Replicatie

* De component van de Agent van de replicatie is vatbaar voor een kwetsbaarheid die gevoelige informatie aan onbevoegde gebruikers openbaart. NPR-29611: Hotfix voor GRANITE-25070

* Sessielek tijdens OAuth voor elke replicatie naar [!DNL Brand Portal]. NPR-30001: Hotfix voor GRANITE-26196

### Projecten

* Publiceer [!DNL Experience Manager Assets] van [!DNL Experience Manager] Auteur /content/dam/mac folder naar [!DNL Brand Portal] werkt niet. NPR-29819: Hotfix voor CQ-4271118

### Platform

* HtmlLibraryManager verwijdert alle inhoud van crx-quickstart bij cachevalidatie. NPR-29863: Hotfix voor GRANITE-26197

### Felix

* Gegevens over geheugengebruik worden niet weergegeven in de systeemconsole bij gebruik van Java11\. NPR-29669

### Forms

De belangrijkste hoogtepunten voor [!DNL Experience Manager Forms] 6.5.1.0 zijn:

* Alleen OSGi: Een nieuw kenmerk `PAGECOUNT` toegevoegd in Output en Forms Service.

* Alleen OSGI: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met Forms Service.
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers.
* Ondersteuning ingeschakeld voor ADFS v3.0 for Dynamics on-premise integratie.

#### Forms-invoegtoepassing

**Backend-integratie**

* Fout bij het ophalen van de beveiligde Web Service Definition Language (WSDL). NPR-29944: Hotfix voor CQ-4270777
* Wanneer [!DNL Experience Manager Forms] is geïnstalleerd op IBM WebSphere, mislukt het maken van een formuliergegevensmodel op basis van SOAP. Hotfix voor CQ-4251134
* Toegelaten steun voor de Actieve Diensten van de Federatie van de Folder (ADFS) v3.0 voor de Integratie van de Dynamiek van Microsoft op-gebouw. Hotfix voor CQ-4270586
* Als de titel van een gegevensbron wordt gewijzigd, wordt de bijgewerkte titel niet weergegeven in het formuliergegevensmodel. Hotfix voor CQ-4265599
* Als de naam van een entiteit of kenmerk afbreekstreepjes of spaties bevat, worden dergelijke entiteiten en kenmerken niet door expressies geëvalueerd. Hotfix voor CQ-4225129

* Er wordt een onjuiste uitvoer waargenomen wanneer een dubbele punt aanwezig is in de primitieve uitvoer van de tekenreeks. Hotfix voor CQ-4260825

* Zelfs als er geen inhoud wordt verwacht van de REST API-uitvoer, genereert de aanroepbewerking van het formuliergegevensmodel een fout. Hotfix voor CQ-4268828

**Adaptieve Forms**

* Unable to add new instance in Adaptive Form Fragment during lazy loading. NPR-29818: Hotfix voor CQ-4269875
* Verify component registreert of toont geen fout voor Document van de malplaatjes van het Verslag. Hotfix voor CQ-4272999
* Toegevoegde ondersteuning voor het uitschakelen van de lay-outeditor voor Adaptive Forms. Hotfix voor CQ-4270810
* De stap Verifiëren voor Adaptive Forms is hersteld in [!DNL Experience Manager] 6.5. Hotfix voor CQ-4269583

* Fout bij validatie van adaptieve formuliervelden: [!DNL Adobe Sign] wordt verbroken. Hotfix voor CQ-4269463
* Wanneer een [!DNL Experience Manager Forms]-instantie meer dan 20 adaptieve formulierfragmenten heeft en de naam van alle formulierfragmenten begint met dezelfde tekenreeks, retourneert de zoekopdracht niet of alleen naar recente 20 gemaakte fragmenten. Hotfix voor CQ-4264414, CQ-4264914

* Prestatieproblemen wanneer de adaptieve Forms-toepassing wordt gebruikt met een grote dataset. . Hotfix voor CQ-4235310

* Wanneer betreden door anonieme rekening op een publicatie instantie, ontbreekt GuideRuntime manuscript om te laden. Hotfix voor CQ-4268679

**Forms - Interactieve communicatie**

* De interactieve Communicatie malplaatje maakt geen lijst van kopbal en footer componenten in toegestane componentenlijst. Hotfix voor CQ-4237895
* Wanneer u een interactieve sjabloon voor communicatie-afdrukken maakt die een afbeeldingsveld bevat, wordt de titel van het diagram ingesteld op leeg. Hotfix voor CQ-4264772
* De lijnkleur van een diagram wordt, wanneer deze wordt verwijderd, ingesteld op ongedefinieerd. Hotfix voor CQ-4264762
* Wijzigingen in de lay-outlaag die zijn aangebracht op documentfragment, verdwijnen bij het uitvoeren van de wijzigingen en blijven synchroon. Hotfix voor CQ-4266054
* Het formuliergegevensmodelelement in een documentfragment dat aan een tekstveld is gebonden, geeft geen overervingspictogram weer en staat binding toe. Hotfix voor CQ-4261089
* De printerkanaal-render-API heeft geen optie om gegevens als parameter door te geven in de API. Hotfix voor CQ-4263540
* De montages van de agent zijn niet zichtbaar aangezien Editable door de controledoos van de Agent wordt ongecontroleerd wanneer het bindingstype van het Fragment van de Tekst in niets/het ModelVoorwerp van Gegevens voor het gebied van het Koord/variabele wordt veranderd. Hotfix voor CQ-4261953
* Voor de voorlegging van de UI van de Agent, slaat het resulterende dossier van Webgegevens informatie voor erving-geannuleerde niet gebonden gebieden op. Hotfix voor CQ-4265621

**Forms - Workflow**

* Wanneer een formulier opnieuw wordt verzonden vanuit de Postvak UIT de app voor adaptieve formulieren, gaan er gegevens verloren. NPR-28345: Hotfix voor CQ-4260929
* Documenten worden niet gesloten tijdens het opslaan voor niet-variabele gevallen. Hotfix voor CQ-4269784
* De adaptieve Forms-app heeft de ondersteuning voor Microsoft Windows 8.1 ingetrokken. Hotfix voor CQ-4265274
* Wanneer een afbeelding van meer dan 2 MB als een bijlage op veldniveau aan een formulier wordt gekoppeld in de Android-versie van de app [!DNL Experience Manager Forms], loopt de app vast. Hotfix voor CQ-4265578

* Toegelaten pre-populatieopties voor Interactieve Communicatie Kanaal van de Druk in Assign taak. Hotfix voor CQ-4265577
* De gebruikers kunnen geen gedeelde taak bekijken tot zij lid van de groep worden waaraan de taak wordt toegewezen. Hotfix voor CQ-4248733
* Het opslaan of verzenden van JEE-toepassingen in de app Adaptief formulier is geblokkeerd in Windows. Hotfix voor CQ-4268704
* Het formuliergegevensmodel dat is gekoppeld aan de variabele van het formuliergegevensmodel is niet zichtbaar. Hotfix voor CQ-4266554
* Geen ondersteuning voor de statusvariabele van het documentteken met variabele ondersteuning. Hotfix voor CQ-4266312
* Verzending vanuit werkruimte mislukt met een umlaut-teken. Hotfix voor CQ-4263172
* Als de workflow tijdens een upgrade wordt geopend voor bewerking, wordt in de gebruikersinterface van de controlemap (UI) een fout weergegeven in plaats van de naam van de workflow. Hotfix voor CQ-4238579

**Forms - Beheer**

* Wanneer een andere extensie dan xsd of schema.json wordt geüpload, vindt uploaden niet plaats en wordt er geen foutbericht gegenereerd. Hotfix voor CQ-4266716

**Forms - Correspondentenbeheer**

* [!DNL Experience Manager Forms] 6.5 de Create Correspondence UI (CCR UI) kan geen correspondentie openen die met  [!DNL Experience Manager Forms] 6.3 wordt gecreeerd. Hotfix voor CQ-4266392
* De functie Som in XDP werkt niet als het DDE gegevenstype van type aantal is. Hotfix voor CQ-4227403
* Letters voor de invalidatielogica voor de cache in het geheugen die moeten worden bijgewerkt, omdat de laatste gewijzigde tijd van een element niet wordt bijgewerkt wanneer een element wordt gepubliceerd. Hotfix voor CQ-4250465
* Kan documentfragment, DD &amp; letters niet publiceren. Hotfix voor CQ-4272893

#### Forms JEE-installatieprogramma

**PDF Generator**

* CAD-bestanden naar PDF-conversie mislukken met 64-bits JDK. NPR-29924, NPR-29925: Hotfix voor CQ-4272113
* De naam van PhantomJS is vervangen door WebToPDF voor conversie van HTML naar PDF. NPR-29933: Hotfix voor CQ-4234545
* Er wordt een fout gegenereerd bij het converteren van het ZIP-bestand naar PDF. Hotfix voor CQ-4268628

**Forms - Designer**

* Wanneer een volledige toegankelijkheidscontrole wordt uitgevoerd op het statische PDF-bestand dat is gemaakt met [!DNL Experience Manager Forms Designer], mislukt de controle van de primaire taal omdat het taalkenmerk ontbreekt. Hotfix voor CQ-4272923, CQ-4271002

**Forms - Documentbeveiliging**

* Digital Signature with Hardware Security Module (HSM) werkt niet op OSGi Linux op Java 11 en Java 8\. NPR-29838: Hotfix voor CQ-4270441
* Digital Signature with Hardware Security Module (HSM) werkt niet op JEE Linux en op alle ondersteunde toepassingsservers, zoals JBoss en Websphere. NPR-29839: Hotfix voor CQ-4266721
* Als u de handtekeningen in een PDF verifieert met behulp van PDF Advanced Electronic Signatures (PAdES), wordt InvalidOperationException gegenereerd. NPR-29842: Hotfix voor CQ-4244837
* Extra ondersteuning voor documentbeveiliging voor Office 2019\. Hotfix voor CQ-4254369, CQ-4259764

**Forms - Document Services**

* PDF kan niet worden geconverteerd naar PDF/A-1b met formulierveld heeft geen weergavewoordenboek. NPR-29940: Hotfix voor CQ-4269618

* OSGi: Kan het aantal pagina&#39;s dat tijdens de rendering wordt gegenereerd, niet bepalen. NPR-28922: Hotfix voor CQ-4270870
* Ondersteuning ingeschakeld voor statische PDF-bestanden met gebruik van Forms Service in [!DNL Experience Manager Forms OSGi]. NPR-28572: Hotfix voor CQ-4270869
* Kan de machtigingen voor XMLForm.exe niet wijzigen. NPR-29828, NPR-29237: Hotfix voor Q-4267080
* In de statische PDF die wordt gemaakt door de uitvoermodule van de [!DNL Experience Manager Forms]-server, wordt het taalkenmerk/de taaltag niet ingevuld met de taal van het gemaakte document. NPR-27332: Hotfix voor CQ-4271002

**Forms - Foundation JEE**

* Niet-beschikbare pdfg_srt in definitieve artefacten veroorzaakt het installatieprogramma om te ontbreken. NPR-29854: Hotfix voor CQ-4270137
* LCBackupMode.sh werkt niet. NPR-29840: Hotfix voor CQ-4269424
* De UDP havenverwijzing zou uit gebruikersinterface (UI) voor WebSphere moeten worden verwijderd. Hotfix voor CQ-4264782

### Inclusief functiepakketten

#### Activa - opgenomen

* Ondersteuning voor beheer van meerdere sites ingeschakeld voor [!DNL Experience Manager Assets]. Zie [Elementen opnieuw gebruiken met MSM voor Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/reuse-assets-using-msm.html) voor meer informatie. NPR-29199: Hotfix voor CQ-4259922

#### Sites - inbegrepen

* Exporteer [!DNL Experience Manager] Experience Fragments naar [!DNL Adobe Target]. Zie [The Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML) voor meer informatie. Hotfix voor CQ-4265469

#### Forms - Document Services - inbegrepen

* Alleen OSGi: Een nieuw kenmerk PAGECOUNT toegevoegd in Output en Forms Service. NPR-28922: Hotfix voor CQ-4270870
* Alleen OSGi: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met Forms Service. NPR-28572: Hotfix voor CQ-4270869
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers. NPR-29237: Hotfix voor CQ-4267080

### OSGi-bundels en inhoudspakketten

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.1.0

Lijst van OSGi-bundels opgenomen in [!DNL Experience Manager] 6.5.1.0

[Bestand ophalen](assets/6_5-bundle-list.txt)

Lijst met inhoudspakketten die zijn opgenomen in [!DNL Experience Manager] 6.5.1.0

[Bestand ophalen](assets/6_5-content-package-list.txt)
