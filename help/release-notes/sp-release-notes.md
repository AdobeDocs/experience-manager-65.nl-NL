---
title: '[!DNL Experience Manager] Opmerkingen bij de release van 6.5 servicepack'
description: Opmerkingen bij de release specifiek voor  [!DNL Adobe Experience Manager] 6.5 servicepack 9
docset: aem65
mini-toc-levels: 1
exl-id: 28a5ed58-b024-4dde-a849-0b3edc7b8472
source-git-commit: 0ed031e8be43633caf6d9916542b6650e3dfd327
workflow-type: tm+mt
source-wordcount: '3797'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] Opmerkingen bij de release van 6.5 servicepack  {#aem-service-pack-release-notes}

## Informatie {#release-information} opheffen

| Producten | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.9.0. |
| Type | Service Pack-release |
| Date | 27 mei 2021 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.9-1.0.zip) |

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5.9.0 {#what-s-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.9.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het servicepack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste eigenschappen en de verhogingen die in [!DNL Adobe Experience Manager] 6.5.9.0 worden geïntroduceerd zijn:

* [!DNL Experience Manager Sites] Met de Dynamic Media Foundation-component kunt u nu optimalisatie voor apparaten met een hogere resolutie in- of uitschakelen wanneer u responsieve voorinstelling voor afbeeldingen of Slim uitsnijden gebruikt.

* Om prestaties te verbeteren, wordt de verborgen=false voorwaarde verplaatst van vraag JCR naar beoordelaar QueryBuilder. Om te verifiëren dat een verborgen predikaat na de verandering werkt, controleert de Experience Manager dat om het even welke verborgen omslag niet op de interface wordt getoond.

* Mogelijkheid om verwijderde pagina&#39;s en boomstructuur op een [!DNL Experience Manager Sites]-pagina te herstellen.

* Steun voor een nieuwe gebruiker om het toegangstoken te verfrissen gebruikend verfrist token voor de dienst van de brievenbusconfiguratie.

* [Steun voor SMTP XOAUTH2](/help/sites-administering/notification.md#setting-up-oauth) mechanisme voor de dienst van de postconfiguratie.

* Ondersteuning voor [!DNL MongoDB] versies 4.2 en 4.4.

* Namen die betrekking hebben op Hongkong, Macau en Taiwan worden bijgewerkt volgens de nieuwe naamconventies voor Chinese landinstellingen en regio&#39;s.

* Verbeterde toegankelijkheid in [!DNL Experience Manager] [Middelen](#assets-accessibility-6590) en [Dynamic Media](#accessibility-dm-6590).

* Dankzij de functie Smart Imaging DPR (Device Pixel Ratio) en de optimalisatie van de netwerkbandbreedte kunt u op efficiënte wijze beelden van de beste kwaliteit leveren. op apparaten met hoge resolutievertoningen en beperkte netwerkbandbreedte. Zie [Veelgestelde vragen over slimme beeldverwerking](/help/assets/imaging-faq.md) voor meer informatie.

   >[!NOTE]
   >
   >De releasetijdlijn voor de bovenstaande verbeteringen voor Smart Imaging is:
   >
   >* Noord-Amerika 24 mei 2021 in NA,
      >
      >
   * Europa, het Midden-Oosten en Afrika 25 juni 2021,
      >
      >
   * Azië-Stille Oceaan 19 juli 2021.


* Introductie van ondersteuning voor AVIF-afbeeldingsindeling van de volgende generatie in Dynamic Media-levering (fmt URL-modifier). Zie [api fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html) voor beeldbewerking en rendering.

   >[!NOTE]
   >
   >De releasetijdlijn voor AVIF-ondersteuning is:
   >
   >* Noord-Amerika 10 mei 2021,
      >
      >
   * Europa, het Midden-Oosten en Afrika 24 mei 2021,
      >
      >
   * Azië-Stille Oceaan 24 juni 2021.


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
>Vanaf Service Pack 9 kunnen klanten [!DNL Experience Manager] hun [!DNL Experience Manager] toepassingen ontwikkelen en gebruiken met distributies van de [!DNL Azul Zulu] builds van OpenJDK, standaarden-compatibel met Java SE.
>Adobe biedt ook ondersteuning voor de [!DNL Azul Zulu] JDK&#39;s aan klanten van [!DNL Experience Manager].
>U kunt de relevante versies van [!DNL Azul Zulu] JDKs van [de Distributie van de Software van Adobe downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
>De gebruiksrechten voor de Oracle Java-technologie, zoals die door Adobe wordt gedistribueerd, lopen eind december 2022 af. [!DNL Experience Manager] klanten worden aangemoedigd om uiterlijk op deze datum het gebruik voor de  [!DNL Azul Zulu] JDK&#39;s te plannen en uit te voeren. Raadpleeg de bijbehorende [Veelgestelde vragen](https://experienceleague.adobe.com/docs/experience-manager-65/assets/adobe-azul-openjdk-license-agreement.pdf?lang=en) voor meer informatie over het gebruik van de [!DNL Oracle Java]-technologie en [!DNL Azul Zulu]-technologie.

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.9.0-release.

### [!DNL Sites] {#sites-6590}

* Gepubliceerde pagina&#39;s waarvoor de eigenschap Verificatievereiste is ingeschakeld, leiden niet om naar de aanmeldingspagina en retourneren het 404-foutbericht (NPR-36354).

* Wanneer u een hyperlink maakt, werkt de optie voor het doorzoeken van een koppeling niet in de tekstcomponent (NPR-35849).

* Er wordt een transversale query geactiveerd bij het gebruik van de `com.day.cq.wcm.commons.ReferenceSearch`-API. Het beïnvloedt prestaties van [!DNL Experience Manager] server (NPR-36407).

* De geneste lay-outcontainer binnen een andere resized lay-outcontainer toont een onjuist aantal kolommen voor zijn kindcomponenten, die in deze componenten resulteren die niet aan het net worden gericht (NPR-36359).

* External Link Checker geeft geldige externe koppelingen weer als ongeldige koppelingen (NPR-36289).

* Nadat u de referenties een tijdje hebt weergegeven, wordt in het venster Referenties een foutbericht weergegeven (NPR-36167).

* Wanneer het bewegen van een component, automatisch gecreeerd parsys, heeft niet de `sling:resourceType` knoop (NPR-36165).

* Wanneer het proberen om een livecopy (terwijl het gebruiken van uitloopvormen [!UICONTROL Activate on Blueprint activation] en [!UICONTROL De-activate on Blueprint activation]) te synchroniseren als een component in de master livecopy wordt geschrapt, ontbreekt de synchronisatie en `NullPointerException` wordt geregistreerd (NPR-36127).

* Wanneer een gebruiker ad-hoctekst typt voor tag (tag die niet op het systeem aanwezig is) en op Enter drukt, wordt de tag onder het veld weergegeven, maar wanneer het inhoudsfragment wordt opgeslagen en opnieuw geopend, verdwijnt de ad-hoctag (NPR-36132).

* De status van asynchrone bewerkingen (NPR-36104) wordt niet weergegeven in Postvak In.

* Er wordt een dubbele component gemaakt na het herstellen van de overerving (NPR-36000).

* Wanneer het gebruiken van `RemoteContentRenderingService`, omvat het verzoek aan `RemoteContentRendererRequestHandler.getRequest` altijd de wortelpagina voor `ComponentExporter`, maar omvat niet de gevraagde pagina als het niet inbegrepen met het wortelmodel is dat op de traversale diepte en het filtreren optiesreeks wordt gebaseerd. Het verzoek moet altijd de gevraagde pagina omvatten zodat de SPA genoeg informatie heeft om een antwoord terug te geven (NPR-35961).

* onTime/offTime-items activeren/deactiveren niet op de verwachte onTime/offTime (NPR-35936).

* Wanneer u een pagina publiceert die een fragment van de Ervaring bevat dat geen `cq:lastModified` bezit, komt `NullPointerException` voor (NPR-35914).

* Wanneer u probeert de grootte van een component in een container te wijzigen, is het niet mogelijk de oorspronkelijke grootte te herstellen. Wanneer de grootte van de container van de component wordt verkleind, is het niet mogelijk de grootte terug te zetten naar het origineel (NPR-35809).

* In het dialoogvenster Uitrollen, dat in de editor of vanuit het Live Copy-overzicht wordt geactiveerd, zijn de statuspictogrammen voor losgekoppelde, geschorste of niet gemaakte pagina&#39;s onjuist (NPR-35691).

* Op pagina&#39;s uitrollen van beheer voor meerdere sites hebben de eigenschappen master het selectievakje Uitrollout-pagina en subpagina&#39;s negeren (NPR-35634).

* De functie Herstelboomstructuur, beschikbaar in de klassieke gebruikersinterface, ontbreekt in Touch-gebruikersinterface (CQ-4315352, CQ-4309415).

* Problemen tijdens het herstellen van overerving en het implementeren van de pagina op een [!DNL Experience Manager Sites]-pagina (NPR-36033).

### [!DNL Assets] {#assets-6590}

[!DNL Adobe Experience Manager] In 6.5.9.0 worden de volgende problemen  [!DNL Assets] opgelost.

* De tags die zijn gemaakt vanuit een element voor tagselectie in een formulier [!UICONTROL Folder Metadata Schema], worden niet opgeslagen (NPR-36119).

* Wanneer een kleine ellips wordt gebruikt om elementen van notities te voorzien, overlapt de ellips met het nummer van de annotatie in de afdrukversie (NPR-36114).

* In de kolomweergave veroorzaakt [!DNL Experience Manager] in sommige gevallen geen dubbele conflict tussen elementen wanneer een dubbel element wordt geüpload (NPR-36048).

* Het dialoogvenster Koppeling delen wordt niet gesloten als het wordt geopend en er geen wijzigingen worden aangebracht (NPR-36030).

* Wanneer er meerdere elementen zijn geselecteerd om de eigenschappen bij te werken, treedt soms een fout op of worden eigenschappen van een niet-geselecteerd element bijgewerkt (NPR-36002).

* Wanneer bij het uploaden van middelen witruimten worden toegevoegd aan het begin of einde van namen van elementbestanden, met resterende tekens die gelijk zijn aan de naam van een bestaand element in de gegevensopslagruimte, wordt het bestaande element vervangen zonder dat een fout wordt geregistreerd (NPR-36001).

* Wanneer video wordt afgespeeld op de pagina met elementdetails, werken de opties voor afspelen en pauzeren niet (NPR-35999).

* Wanneer het unpublishing van activa in bulk, Brand Portal een fout veroorzaakt die erop wijst dat het verzoek URI te lang is (NPR-35954).

* Wanneer een element met lange annotatietekst wordt afgedrukt, wordt de annotatietekst bijgesneden, zelfs als er ruimte beschikbaar is (NPR-35948).

* De optie om naar de volgende pagina te gaan is uitgeschakeld wanneer u de pagina selecteert in de weergave Sjablonen op de pagina Catalogus maken (CQ-4315462).

* Wanneer de werkstroom voor het bijwerken van elementen wordt gestart voor het video-element, wordt de pagina herhaaldelijk vernieuwd (CQ-4313375).

* DAM-mappen kunnen niet worden verwijderd of verplaatst en er wordt een uitzondering vastgelegd (NPR-35942).

#### Verbeteringen in elementen {#assets-enhancements}

* Introduceerde de optie [!UICONTROL None] in kaart, kolom, en inzichten mening om activa in de orde te sorteren zij in de knoop JCR (NPR-36356) worden opgeslagen.

* Er wordt een optie toegevoegd om de e-mailid in kleine letters toe te voegen in API-reactie van Adobe Experience Manager (CQ-4317704).

#### Verbeterde toegankelijkheid in elementen {#assets-accessibility-6590}

[!DNL Adobe Experience Manager] 6.5.9.0  [!DNL Assets] biedt de volgende toegankelijkheidsverbeteringen.

Het contrast (met de achtergrond) van de volgende tekst en pictogrammen is verbeterd, zodat gebruikers met een beperkt gezichtsvermogen en kleurperceptie deze kunnen begrijpen:

* titel van het element op pagina [!UICONTROL Properties] (NPR-35967).
* sterrenclassificatiepictogrammen in secties [!UICONTROL Rating] op verschillende plaatsen (NPR-36009).
* tekst op het middel en de omslagkaartmening (NPR-35966).
* plaatsaanduidingstekst in de weergave [!UICONTROL Timeline] (NPR-35965).
* namen van activa in de resultaten van de activazoekopdracht (NPR-35964).
* plaatsaanduidingstekst in het dialoogvenster [!UICONTROL Link Sharing] (NPR-35963).
* [!UICONTROL Metadata],  [!UICONTROL Status]en  [!UICONTROL Other] tekst met  [!UICONTROL List] optie in het  [!UICONTROL View Settings] dialoogvenster (NPR-35910).
* [!UICONTROL Location] en  [!UICONTROL Type to search] plaatsaanduidingsteksten in de wereldwijde zoekactie (NPR-35909).
* pictogrammen uit- en samenvouwen onder [!UICONTROL Content Tree] (NPR-35908).
* de [!UICONTROL Assets]-tekst op de pagina waarop mappen met elementen worden weergegeven (NPR-35905).
* tekst in [!UICONTROL Asset Metadata], [!UICONTROL Usage Statistics] binnen [!UICONTROL Overview] optie op de pagina met elementdetails (NPR-35904).
* tekst voor sneltoetsen voor opties [!UICONTROL properties] en [!UICONTROL edit] op de pagina met elementdetails (NPR-35904).

### [!DNL Dynamic Media] {#dynamic-media-6590}

Adobe Experience Manager 6.5.9.0 Assets verhelpt de volgende problemen in [!DNL Dynamic Media]:

* Custom ViewerPresets en CSS worden niet gerepliceerd naar [!DNL Dynamic Media] wanneer [!DNL Dynamic Media] selectief wordt geactiveerd en door [default](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/config-dm.html?lang=en#troubleshoot-dm-config) (NPR-36232) wordt uitgeschakeld.

* Wanneer u video-uitvoeringen wilt voorvertonen op de pagina met elementdetails, worden de video&#39;s traag geladen (CQ-4320122).

* Browserpagina reageert niet en wordt trager wanneer meer dan 200 elementen worden geüpload terwijl Duplicate Asset Detector is ingeschakeld (CQ-4319633).

* Wanneer een panoramisch afbeeldingselement wordt toegevoegd aan het panoramische mediacomponent op een pagina, wordt een niet-afgevangen referentiefout vastgelegd (CQ-4317666).

* Wanneer de interactieve media viewer wordt geïmplementeerd met Experience Fragment, wordt het Experience Fragment niet geopend bij de uitgever en wordt een fout vastgelegd (CQ-4317655).

* De optie Publiceren naar Dynamic Media is niet beschikbaar in Snel publiceren in de weergave Metaeditor (CQ-4317199).

* Siteauteurs met de machtiging Alleen-lezen kunnen de functie voor slim uitsnijden voor elementen gebruiken en de slimme bijgesneden uitvoeringen bewerken. Gebruikers met de machtiging Alleen-lezen mogen echter de eigenschappen van elementen niet kunnen bewerken in de instantie Sites Dev (CQ-4316450).

* Videoannotaties werken niet voor mappaden [!DNL where Dynamic] De mediaconfiguratie is niet ingeschakeld, zelfs niet als de [!DNL Experience Manager]-instantie is ingesteld in de modus [!DNL Dynamic Media] (CQ-4314950).

* Wanneer de titel van het element dubbel-byte, multi-byte, hoge ASCII, Cyrillisch, surrogaat paar, Hebreeuws, Arabisch, en GB18030 karakters heeft, dan bij het publiceren aan Dynamic Media heeft de activa titel een vraagteken (?) (CQ-4311872).

#### Verbeterde toegankelijkheid in Dynamic Media {#accessibility-dm-6590}

[!DNL Adobe Experience Manager] 6.5.9.0  [!DNL Assets] biedt de volgende toegankelijkheidsverbeteringen in  [!DNL Dynamic Media].

* Wanneer u het dialoogvenster opent om elementen toe te voegen met de toetsenbordtoetsen in de Image Set Editor:
   * schermlezers vertellen dat het dialoogvenster wordt geopend.
   * wanneer het dialoogvenster wordt geopend, wordt de focus van het toetsenbord verplaatst.
   * toetsenbordfocus gaat terug naar de optie Element toevoegen wanneer het dialoogvenster wordt gesloten (CQ-4312134).

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

### Omzettingsprojecten {#translation-6590}

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

* Bij het filtreren van spam, verbruikt het systeem 100% van de heapruimte Java waardoor de server van de Experience Manager (NPR-36316, NPR-36493) onbruikbaar wordt.
* In forums worden de gegevens van de JCR-sessies afkomstig van `SearchCommentSocialComponentListProvider` uitgelekt (NPR-36235).
* Het openen van een specifiek postbusbericht weerspiegelt alle berichten met onjuiste paginering en andere kwesties (NPR-35917).

### [!DNL Brand Portal] {#brandportal-6590}

* De markering voor de functie Asset Sourcing wordt automatisch ingeschakeld bij het configureren van [!DNL Experience Manager Assets] met [!DNL Brand Portal] (NPR-36010).

### [!DNL Forms] {#forms-6590}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het  [!DNL Experience Manager] Service Pack vrij.
>* U kunt nu toepassingen ontwikkelen en gebruiken met [!DNL Azul Zulu] builds van [!DNL OpenJDK] voor [!DNL Experience Manager Forms] op OSGi-implementaties.


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

* Wanneer u het REST-eindpunt van een [!DNL Experience Manager Forms]-service op JBoss aanroept, geeft [!DNL Experience Manager] het volgende foutbericht weer (NPR-36305):

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

## 6.5.9.0 installeren {#install}

**Instellingsvereisten en meer informatie**

* Experience Manager 6.5.9.0 vereist Experience Manager 6.5. Zie [upgrade documentation](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer Experience Manager 6.5.9.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.

>[!NOTE]
>
>Adobe raadt u niet aan het [!DNL Adobe Experience Manager] 6.5.9.0-pakket te verwijderen of te verwijderen.

### Installeren van het servicepack {#install-service-pack}

Voer de volgende stappen uit om het servicepack te installeren op een [!DNL Adobe Experience Manager] 6.5-exemplaar:

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (dit is het geval wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt ook aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager]-exemplaar.

1. Download het servicepakket van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.9-1.0.zip).

1. Open Package Manager en klik **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie [Pakketbeheer](/help/sites-administering/package-manager.md) voor meer informatie.

1. Selecteer het pakket en klik **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit gebeurt gewoonlijk op [!DNL Safari] maar kan periodiek op om het even welke browser gebeuren.

**Automatische installatie**

Er zijn twee manieren om [!DNL Experience Manager] 6.5.9.0 op een werkende instantie automatisch te installeren:

A. Plaats het pakket in de map `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik [HTTP API van de Manager van het Pakket](/help/sites-administering/package-manager.md#package-share). Gebruik `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Adobe Experience Manager 6.5.9.0 biedt geen ondersteuning voor Bootstrap-installatie.

**De installatie valideren**

1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks `Adobe Experience Manager (6.5.9.0)` weergegeven onder [!UICONTROL Installed Products].

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De bundel OSGi `org.apache.jackrabbit.oak-core` is versie 1.22.3 of later (de Console van het Gebruik: `/system/console/bundles`).

Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md) voor meer informatie over de platforms die zijn gecertificeerd voor deze release.

### Adobe Experience Manager Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Sla over als u Experience Manager Forms niet gebruikt. Correcties in Experience Manager Forms worden één week na de geplande [!DNL Experience Manager] Service Pack-release geleverd via een afzonderlijk add-on pakket.

1. Controleer of u het Adobe Experience Manager Service Pack hebt geïnstalleerd.
1. Download het overeenkomstige Forms add-on pakket dat u vindt op [AEM Forms releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#forms-updates) voor uw besturingssysteem.
1. Installeer het invoegpakket voor Forms zoals beschreven in [AEM Forms-invoegpakketten installeren](../forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

>[!NOTE]
>
>AEM 6.5.9.0 bevat een nieuwe versie van [AEM Forms-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#aem-65-forms-releases). Als u een oudere versie van het AEM Forms Compatibility Package gebruikt en een update naar AEM 6.5.9.0 uitvoert, installeert u de nieuwste versie van het pakket na de installatie van het Forms Add-on Package.

### Adobe Experience Manager Forms installeren op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Correcties in Adobe Experience Manager Forms op JEE worden via een afzonderlijk installatieprogramma geleverd.

Raadpleeg de [releaseopmerkingen](jee-patch-installer-65.md) voor informatie over de installatie van het cumulatieve installatieprogramma voor Experience Manager Forms in JEE en de configuratie na de implementatie.

>[!NOTE]
>
>Nadat u het cumulatieve installatieprogramma voor Experience Manager Forms in JEE hebt geïnstalleerd, installeert u het nieuwste Forms-invoegpakket, verwijdert u het Forms-invoegpakket uit de map `crx-repository\install` en start u de server opnieuw.

### UberJar {#uber-jar}

UberJar voor Experience Manager 6.5.9.0 is beschikbaar in [Maven Centrale bewaarplaats](https://repo1.maven.org/maven2/com/adobe/aem/uber-jar/6.5.9/).

Om UberJar in een Geweven project te gebruiken, zie [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en omvat de volgende gebiedsdeel in uw projectPOM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.9</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Maven Central Repository in plaats van Adobe Public Maven repository (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als waarde, voor de tag `dependency`.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Een alternatieve optie wordt gewoonlijk verstrekt.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | Het scherm **[!UICONTROL AEM Cloud Services Opt-In]** is verouderd. Met de Experience Manager en de integratie van Adobe Target die in Experience Manager 6.5 wordt bijgewerkt om de Standaard API van Adobe Target te steunen, die authentificatie via Adobe IMS en [!DNL Adobe I/O] gebruikt, en de groeiende rol van de Lancering van Adobe voor het van instrumenten voorzien van Experience Manager pagina&#39;s voor analyse en verpersoonlijking, is de opt-in tovenaar functioneel irrelevant geworden. | Configureer systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O]-integratie via de respectievelijke [!DNL Experience Manager]-cloudservices. |
| Connectors | De Adobe JCR-connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013 is afgekeurd voor Experience Manager 6.5. | N.v.t. |

## Bekende problemen {#known-issues}

* Als u uw [!DNL Experience Manager] instantie van versie 6.5 aan versie 6.5.9.0 bevordert, kunt u `RRD4JReporter` uitzonderingen in het `error.log` dossier bekijken. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een eerder servicepakket installeert op [!DNL Experience Manager] 6.5, wordt de runtimekopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) verwijderd.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Als de naam van een map in de hiërarchie wordt gewijzigd in [!DNL Assets] en een geneste map met een element wordt gepubliceerd naar [!DNL Brand Portal], wordt de titel van de map niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van formulieren mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.9.0:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.9.0](assets/6590_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.9.0](assets/6590_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* Zie [hoe u contact opneemt met de klantenservice van Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Opmerkingen bij de release 6.5](/help/release-notes/release-notes.md)
* [[!DNL Experience Manager] productpagina](https://www.adobe.com/marketing/experience-manager.html)
* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

