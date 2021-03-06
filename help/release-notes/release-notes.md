---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: '"[!DNL Adobe Experience Manager] 6.5 notities waarin de releasegegevens, de nieuwe functies, de installatie en gedetailleerde lijsten met wijzigingen worden beschreven."'
mini-toc-levels: 3
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 9f957175573eeb2b40d79a5087dc3034c56819cc
workflow-type: tm+mt
source-wordcount: '3718'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.13.0. |
| Type | Service Pack-release |
| Date | 26 mei 2022 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.13.0.zip) |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.13.0. {#what-is-included-in-aem}

[!DNL Experience Manager] 6.5.13.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 worden vrijgegeven. [Dit servicepack installeren](#install) op [!DNL Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.13.0 zijn:

* Gebruik onzichtbare CAPTCHA in een adaptieve vorm: U kunt nu een onzichtbare CAPTCHA gebruiken om de CAPTCHA-uitdaging alleen te tonen in het geval van een verdachte activiteit. Als geen verdachte activiteit wordt gevonden, wordt de uitdaging CAPTCHA niet getoond. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren. (NPR-38500)

* Extra ondersteuning voor het ophalen van antwoordheaders in de nabewerker van het formuliergegevensmodel voor REST-eindpunten. (NPR-38275)

* Bij het genereren van een adaptief formuliervertaalbestand is nu dezelfde reeks teksten als het gegenereerde XLIFF-bestand identiek aan de reeks componenten in het corresponderende adaptieve formulier. (NPR-37700)

* Wanneer u een adaptief formulier lokaliseert en zelfs een kleine wijziging aanbrengt in de tekst van de basistaal, ontbreekt de volledige vertaling voor alle andere talen. Het probleem is opgelost in [!DNL Experience Manager] 6.5.13.0. (NPR-37189)

* Verbeterde toegankelijkheid voor Forms:

   * Extra ondersteuning voor schermlezers om de koptekst en hoofdtekst van een tabel te herkennen als continue en verbonden entiteiten. Schermlezers kunnen hierdoor gemakkelijker door de tabellen navigeren. (NPR-37139)
   * Extra ondersteuning voor schermlezers om te stoppen met navigeren door de HTML-werkruimte totdat een dialoogvenster is geopend. (NPR-37134)
   * Mogelijkheid toegevoegd om schermtekst voor hyperlinks op te geven in Forms Designer.(NPR-36221)

De volgende opgeloste problemen, belangrijke functies en verbeteringen zijn geïntroduceerd in [!DNL Experience Manager] 6.5.13.0:

<!-- The following issues are fixed in [!DNL Experience Manager] 6.5.13.0: -->

## [!DNL Assets] {#assets-6513}

* Wanneer u probeert een alleen-lezen vervolgkeuzeveld te bewerken, wordt de vervolgkeuzelijst weer ingesteld op leeg. (NPR-38389)
* De gebruiker kan geen video (.mp4) activa opnemen als er geen audio in het videodossier is. De DAM Update Asset-workflow mislukt en geeft een foutbericht weer. (NPR-38116)
* Wanneer u de wizard Element verplaatsen gebruikt om een map met elementen te verplaatsen, mislukt de workflow en wordt een foutbericht weergegeven. (NPR-38061)
* De MPEG-transcoderingsworkflow mislukt voor FLV-videoprofiel. (CQ-4343249)
* Na bijwerken naar [!DNL Experience Manager] 6.5 SP10, werkt de redacteur van activa meta-gegevens niet behoorlijk. (CQ-4341359)
* Wanneer u een slimme verzameling opent die is opgeslagen met het zoekfilter dat is toegepast als Publiceren, verandert het zoekfilter automatisch in Niet gepubliceerd. (CQ-4341/191)
* Bij schakelen van taal in **[!UICONTROL User Preference]**, het etiket **[!UICONTROL Sort By]**, vervolgkeuzelijst en andere opties in de sorteeropties op de startpagina van Asset worden niet weergegeven in de geselecteerde taal. (CQ-4339306)
* Bij het toevoegen van een regel aan een vervolgkeuzelijst in **[!UICONTROL Metadata Schema]** de **[!UICONTROL Dependent On]** geeft niet het veldlabel van de vervolgkeuzelijst weer. (ACTIVA-9442)
* Vervolgkeuzelijst met metagegevens van elementen uitgeschakeld bevat geen waarden. (ACTIVA-8918)
* Bij weergave van het element met **[!UICONTROL More Details]** optie in **[!UICONTROL Column]** onjuiste annotaties worden weergegeven. (ACTIVA-8851)
* Wanneer u een dubbel element maakt met een andere versie, worden de uitvoeringen niet gegenereerd. (ACTIVA-8607)

* Een gebruiker die geen beheerder is, kan een element publiceren dat al is uitgecheckt door een andere gebruiker. (NPR-38128)
* Dimensionele viewer werkt niet op Chrome 97. (CQ-4340456)
* De knop voor het downloaden van middelen geeft geen volledig menu weer op de pagina met elementdetails. (CQ-4336703)
* Wanneer u Koppeling delen gebruikt, zijn sommige tekenreeksen in het venster voor het delen van koppelingen niet gelokaliseerd. (CQ-4330540)
* Wanneer u items toevoegt in Publicatie beheren, wordt de tekenreeks die het aantal geselecteerde items weerspiegelt, niet gelokaliseerd. (CQ-4330491)

### [!DNL Dynamic Media] {#dynamic-media-6513}

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Zero day exploit with the Java™ Spring Core Framework (CVE-2022-22963) impacting Experience Manager 6.5.12. (ASSETS-9031) -->
* Beveiligde voorvertoning op basis van token voor Dynamic Media-elementen op AEM-auteurs. (ACTIVA-4995)
* Wanneer u een voorinstelling voor afbeeldingen voor Dynamic Media maakt in [!DNL Experience Manager], is het toegestane maximum beperkt tot 2000x2000 pixels in de gebruikersinterface. Wanneer de waarde voor breedte of hoogte wordt verhoogd tot 2001 pixels, wordt de **[!UICONTROL Save]** wordt gedeactiveerd. (ACTIVA-5691)
* Gebruikers kunnen voorkomen dat bepaalde bestandsindelingen worden geüpload naar Dynamic Media. (ACTIVA-5693)
* Toegankelijkheid - Gebruikers met een visuele handicap die vertrouwen op schermlezers, worden beïnvloed als het Alt-kenmerk niet is geïmplementeerd op een afbeelding in de gebruikersinterface van de voorinstellingen voor afbeeldingen. (ACTIVA-9817)
* Toegankelijkheid - Schermlezers worden beïnvloed wanneer schermlezers in de modus Pijl-omlaag naar afbeeldingen zonder label verwijzen die zich bevinden in het segment Tijdlijn en op het tabblad Handelingen. (ACTIVA-5651)
* Toegankelijkheid - Schermlezers worden beïnvloed omdat schermlezers (NVDA/JAWS) de beschrijvende naam (E-mail verzenden) voor de knop &quot;E-mail verzenden&quot; in het dialoogvenster &quot;E-mailkoppeling&quot; in de videospeler niet vertellen terwijl ze navigeren met de modi (Bladeren/Cursor). (ACTIVA-5641)
* Toegankelijkheid - De toetsenbordfocus gaat niet naar de knop Opnieuw, die wordt weergegeven nadat de knop Ongedaan maken op de pagina van de Editor afbeeldingsset is geactiveerd, terwijl u navigeert met de TAB-toets op het toetsenbord. (ACTIVA-5582)
* Toegankelijkheid - Gebruikers die op schermlezers vertrouwen, krijgen invloed omdat het Alt-kenmerk niet wordt opgegeven voor een afbeelding in de afbeeldingsset die onder de kop Eigenschappen staat. (ACTIVA-5576)
* Toegankelijkheid - Schermlezers vertellen de koprol niet voor `Cannot save this set` tekst in de `Cannot save this set` waarschuwing, tijdens navigeren met sneltoets voor koptekst `H`en Pijl-omlaag. (ACTIVA-5569)
* Toegankelijkheid - Gebruikers die op schermlezers vertrouwen, worden beïnvloed om door de formulieren te navigeren. Ze vinden het moeilijk om de informatie over de formulierbesturingselementen te begrijpen als NVDA de labelinformatie voor de draaibesturingselementen voor &quot;Breedte en Hoogte&quot; niet doorvoert. Deze besturingselementen die aanwezig zijn onder de koptekst Responsieve uitsnijding van afbeelding tijdens het navigeren in de NVDA-formuliermodus &quot;F&quot;. (ACTIVA-5393)
* Nadat u een Dynamic Media-component aan een site hebt toegevoegd en de pagina hebt gepubliceerd, is het nieuwe Dynamic Media-element niet zichtbaar op de gepubliceerde pagina en kan het ook niet worden weergegeven op de pagina Voorbeeld. Dit probleem is opgetreden voor zowel afbeeldings- als video-elementen. (ACTIVA-9467)

## Handel {#commerce-6513}

* &quot;Iedereen&quot; heeft jcr:schrijven op `/content/usergenerated/etc/commerce/smartlists`. (NPR-35230)
* Lokale sortering van Commerce Products werkt niet meer. (CQ-4343750)
* Kan geen product snel publiceren vanaf de pagina met zoekresultaten nadat eigenschappen zijn gewijzigd. (CQ-4343318)

## CRX {#crx-6513}

* Kan een pakket niet downloaden als het speciale teken heeft `+` in de pakketnaam. (NPR-38102)

## [!DNL Forms] {#forms-65130}

<!-- * When you use the prefill service to fill an adaptive form that contains a fragment and the fragment contains a Text box that supports rich text, the form fails to submit, and the following error occurs:

  `[AF] [AEM-AF-901-004]: Encountered an internal error while submitting the form.` (NPR-38542) -->

* Het keuzerondje, het selectievakje en de onderdelen voor het uploaden van bestanden worden niet correct vertaald van het Duits naar het Engels. (NPR-38527)
* De PDF417-streepjescodering die wordt geproduceerd door [!DNL Experience Manager] Forms is ongeldig voor een groep keuzerondjes. (NPR-38525)
* De volgende fout treedt op bij het verzenden van een adaptief formulier.
   `WARN [10.172.114.236 [1650871578492] POST /lc/content/forms/af/public/DHS-3754-ENG/jcr:content/guideContainer.af.internalsubmit.jsp HTTP/1.1] com.adobe.aemds.guide.internal.impl.utils.SubmitDataCollector TemplateKey not found in merge json:cq:responsive` (NPR-38520)
* De optie Verborgen velden uitsluiten van document van record werkt niet. (NPR-38512)
* Na het toevoegen van de component van de Container van Forms aan een pagina van Plaatsen, kunnen de gebruikers niet aan een verschillende pagina van Plaatsen doorlopen en de pagina van Plaatsen hangt bij sommige gelegenheden. Het probleem verschijnt periodiek. (NPR-38506)
* Gebruikers ervaren overlappende tekst in Adaptief Forms na het toepassen [!DNL Experience Manager] 6.5 Service Pack 11. (NPR-38376, CQ-4342472)
* Gebruikers ondervinden een uitzondering wanneer ze adaptieve formulierdeelvensters verplaatsen naar een nieuwe responsieve indeling. (NPR-38369)
* Ondersteuning voor ECMASCRIPT 6 (ES6) is niet ingeschakeld voor de clientbibliotheek ` /libs/fd/expeditor/clientlibs/view`. (NPR-38358)
* Wanneer u een [!DNL Experience Manager] De workflow voor het verzenden van een e-mailbericht in het Hebreeuws bevat aan het einde van de gebruiker de vraagtekens (??) in plaats van de Hebreeuwse tekst (NPR-38296).
* Gebruikers worden willekeurig afgemeld van [!DNL Experience Manager] Publicatie-instanties en een adaptief formulier kunnen niet worden verzonden. Het probleem wordt weergegeven op [!DNL Experience Manager] instanties die Dispatcher gebruiken. (NPR-38285)
* Wanneer u de optie getFormDataString gebruikt in de regel van een Adobe Launch om de Adaptive Form-gegevens vast te leggen, worden geen Adaptive Forms-gegevens geretourneerd. (NPR-38283)
* [!DNL Experience Manager] 6.5 Forms-API die verouderd is voor java.acl.Group en de volgende foutberichten worden weergegeven in het bestand error.log:
   ` *WARN* [default task-36] org.apache.jackrabbit.oak.spi.security.principal.AclGroupDeprecation use of deprecated java.acl.Group-related API - this method is going to be removed in future Oak releases - see OAK-7358 for details` (NPR-38282)
* Forms dat in het Duits is gemaakt, vertaalt niet naar het Engels of een andere taal. (NPR-38280)
* Als u een gelokaliseerde versie van een adaptief formulier gebruikt, wordt het bijbehorende Document of Record (DoR) niet gelokaliseerd. (NPR-38235)
* Wanneer u de stap E-mail verzenden gebruikt om een bijlage samen met een e-mail te verzenden, behoudt de bijlage de naam die in de workflowstap is opgegeven niet. (NPR-38216)
* Wanneer een nieuwe versie van de brief wordt gepubliceerd, kunnen de gebruikers niet de ontwerp brieven voor vorige versies van de brieven openen. (NPR-38215, CQ-4342515)
* Bij het aanroepen van een eindpuntservicemethode van de AEM Forms JEE-service op een knop klikt die is geconfigureerd als een adaptieve formulierregel, mislukt de SOAP-service met onderstaande uitzondering:
   `ERROR* [0:0:0:0:0:0:0:1 [1624362360493] POST /content/forms/af/testsoapwsdl/jcr:content/guideContainer.af.dermis HTTP/1.1] com.adobe.aemds.guide.addon expeditor.servlet.ExpEditorServiceManager Error while making web service related call java.lang.Exception: createSOAPParam: JSONException`
* Als u com.adobe.fd.pdfutility.services.PDFUtilityService#convertPDFtoXDP gebruikt om een PDF naar XDP-indeling te converteren, wordt een ongeldig XDP-bestand geretourneerd. (NPR-38140, CQ-434/2099)
* Wanneer meerdere gebruikers Correspondentiebeheer gebruiken om verschillende letters te genereren, wordt bij voorvertoning een onjuiste letter weergegeven voor sommige gebruikers. (NPR-38134)
* De AEM Forms-component die is ingesloten in de SITES-pagina gebruikt het breedtekenmerk met waarde in % en is niet geldig volgens de W3C-HTML-validatie. Gebruikers ondervinden een fout bij het parseren tijdens het valideren van de HTML. (NPR-38124)
* Keuzerondjes en selectievakjes voor de meeste OOTB-thema&#39;s in adaptieve vormen maken geen deel uit van de tabvolgorde (NPR-38108)
* Wanneer een gebruiker HTML-tags aan de commentaarsectie toevoegt tijdens het uitvoeren van een workflow, worden de HTML-tags weergegeven. (NPR-37591)
* Bij het importeren en publiceren van een letter die een nieuw XDP-bestand bevat, wordt geen voorvertoning van de letters weergegeven in de instantie Publiceren. Als de letters echter een tweede keer worden geïmporteerd en gepubliceerd met hetzelfde CMP-bestand, wordt een voorvertoning van de letters weergegeven. (CQ-4343599)
* Een formulier met de eigenschap voor het voorbereiden van het gegevensproces is niet gerenderd in de HTML Workspace. (CQ-4343294)
* Voor statische PDF forms die zijn gemaakt met Forms 6.5 Designer, mislukt de toegankelijkheid van PDF bij een fout `Tab order entry in page with annotations not set to "S"`. (CQ-4343117)
* Kan een afbeelding niet converteren naar PDF met gebruik van de PDFG-service met OCR, nadat de patch AEMForms-6.5.0-0038 (log4jv2.16) is toegepast. (CQ-4342450)
* Er wordt een onjuiste waarde weergegeven voor de streepjescode SSCC-18. Forms-servers laten de waarde in het rechtergedeelte van de streepjescode weg. (CQ-4342400)
* Kan geen Microsoft® Word-bestand importeren naar Forms Designer. Fout aangetroffen door gebruiker `Word (version XP or onwards) could not be found on the machine`. (CQ-4342146)
* Als u in Forms 6.5 Designer een formulier opent dat is gemaakt met Forms 6.1 Designer en een tekstvak bewerkt, overschrijdt de alinea-afstand de opgegeven ruimte. Alle vorige instellingen van de ruimte worden verwijderd en het tekstvak moet handmatig opnieuw worden opgemaakt. (CQ-4341899)
* De gebruiker kan geen aangepaste tijd instellen in de planner voor het leegmaken van taken. (CQ-4339/192)
* De gebruiker kan geen configuratie onder eindpuntbeheer UI bijwerken en fout ontmoeten ` Uncaught ReferenceError: updateEndpoint_required is not defined`. (CQ-4331523)
* Voor ongeldige tags werkt een goede afhandeling van foutberichten niet zoals u had verwacht. (NPR-38106 en CQ-4337173)

>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.


## Graniet {#granite-6513}

* Het resultaat van Omnissearch wordt geretourneerd voor gebruikers zonder leesrechten. (NPR-38373)
* ES6 inschakelen voor `/libs/granite/configurations/clientlibs/confbrowser`. (NPR-38300)

## Integrations {#integrations-6513}

* De zittingen van de middeloplosser op de dienst van de Test en van het Doel van verouderde UserInfoServlet. (NPR-38112)

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * AEM‑OP‑13 ‑ HTTP Parameter Pollution in `com.day.cq.searchpromote.impl.servlet`. (NPR-38033) -->
<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Analytics 2.0 IMS support added to Experience Manager 6.5. (NPR-37914) -->

## eiken - indexering en vragen {#oak-6513}

* De eik-versie voor 6.5.13.0 wordt nu bijgewerkt naar 1.22.11. (NPR-38084) —>

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Create a CFP based on latest 6.5.12 and update Oak-related bundle versions. (NPR-38144) -->

## Platform {#platform-6513}

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * RTC : Universal XSS through cq-rewriter HtmlParser. (NPR-38064) -->
* Afhankelijkheid van upgrade `org.apache.httpcomponents.httpclient` in [!DNL Experience Manager] 6.5 (NPR-37999)
* Hoge Auteur laden vanwege suggesties voor padvelden. (CQ-4341826)
* De gebruiker moet de pagina verfrissen wanneer zij het project van de mening van de Kaart in de mening van de Kalender veranderen. (CQ-4340368)
* Tags gaan verloren vanwege beperkingen op de machtigingen. (CQ-4339543)
* Meerdere problemen die zijn gemeld met Zoeken en filteren in padselectie werken niet. (CQ-4339402)
* Stop met het gebruik van DTM op 6.5 - schakel over op Starten voor Omega Instrumentation en voeg steun Gainsight toe. (CQ-4337809)
* Beperk de zoekfunctie van padveldcomponenten op basis van de eigenschap pathfield filter die is ingesteld. (CQ-4309556)
* [!DNL Experience Manager] Platform 6.5: Oplossingen voor naamgeving van Chinese landinstellingen. (CQ-4308978)
* Schakel over naar Starten voor Omega Instrumentation. (NPR-38377)
* [!DNL Experience Manager] Platform 6.5: Oplossingen voor de naamgeving van Chinese landinstellingen. (CQ-4308978)

## Replicatie {#replication-6513}

* Publiceren van mislukte gebruikersknooppunten van auteur naar uitgever. (NPR-38005)

## [!DNL Sites] {#sites-6513}

### Beheer {#sites-admin-6513}

* Verbeter de regressie die met SP 12 wordt geïntroduceerd die een kwestie zou kunnen hebben veroorzaakt toen het bewegen van pagina&#39;s. (SITES-5298)

### Klassieke gebruikersinterface {#sites-classicui-6513}

* RTE: De bijgewerkte afbeelding is niet zichtbaar wanneer een nieuwe afbeelding boven op een bestaande afbeelding wordt gesleept. (NPR-38141)

<!-- version 2 of description above * Updated Image is not visible When a new image is dragged on top of an existing image the updated image is not visible in RTE - Classic UI. (NPR-38141) -->

### Contentfragmenten {#sites-contentfragments-6513}

* Ondersteuning voor het maken van modellen van inhoudsfragmenten in subconfiguraties. (NPR-38054)

<!-- version 2 of description above * The Configuration Manager now allows you to set the Content Fragment Model config on a sub-config folder. (NPR-38054) -->
* Verbeter de prestaties bij het gebruik van de validatie &#39;Uniek veld&#39; in het inhoudsfragmentmodel. (NPR-38142)

<!-- version 2 of description above * The unique field validation query is now fixed. (NPR-38142) -->
* Verbeter reactie-tijd wanneer het openen van de Redacteur van het Model van het Fragment van de Inhoud. Klanten met een groot aantal fragmenten in Elementen kunnen bij het openen fouten hebben gezien. (SITES-6284)

<!-- version 2 of description above * If the customer is trying to access the editor of the content fragment models, they get a query error because of too many fragments on the dam. (SITES-6284) -->
* Correctie van regressie die werd geïntroduceerd bij het bijwerken van 6.5.11 naar 6.5.12 die tot fouten van de Redacteur van het Model van het Fragmentmodel van de Inhoud zou kunnen hebben veroorzaakt. (SITES-5088 en SITES-4967)

<!-- version 2 of description above * Paths were getting deleted when AEM 6.5.12.0 was installed on existing 6.5.11.0 instance. (SITES-5088)
* Apple 6.5.10 system crashing when using CF model editor, due to erroneous feature toggle check. (SITES-4967) -->
* Verbeter lokalisatie van de gebruikersinterface van de Editor van het inhoudsfragmentmodel. (NPR-38126)

<!-- version 2 of description above * Some strings in the Content Fragment Model editor are not localized. (NPR-38126) -->
* Probleem verhelpen dat het sluiten van de Content Fragment Editor een fout kan veroorzaken wanneer de Auteur-server wordt gebruikt met Dispatcher. (NPR-38205)

<!-- version 2 of description above * Update of Content Fragment references is returning an invalid JSON response via Dispatcher. (NPR-38205) -->
* Probleem verhelpen dat het opslaan van een model niet mogelijk was toen de bevestiging op een gebied van RTE werd gebruikt. (NPR-38210)

<!--version 2 of description above * Content Fragment Model Rich Text Validation Prevents Blocks Saving a Content Fragment Model. (NPR-38210) -->
* Probleem met inhoudsfragment waarbij de Booleaanse eigenschap Veldtekst niet in de titel weergeeft in plaats van Eigenschapnaam. (NPR-38244)
* Fout bij het uitvoeren van een voortgezette query met een queryvariabele als Postman. (NPR-38251, NPR-38057)
<!--version 2 of description above * An unexpected error message is coming in Postman, when executing the graphQL persisted query having query variables. (NPR-38251) -->
* Component inhoudsfragment: De regressie in de optie &#39;greep koppen als alinea&#39;s&#39; die 6.5 SP7 was. (NPR-38055)

<!--version 2 of description above * After applying SP11 to the Publish instance of AEM 6.5.6, the display result of the Content Fragment set in the published page changes. (NPR-38055) -->
* Correctie van regressie die in 6.5.11 is geïntroduceerd en mogelijk fouten met het zoeken naar middelen heeft veroorzaakt. (SITES-4784)

<!--version 2 of description above * Adapt external index package to use selection Policy (fragment versus asset index). (SITES-4784) -->
* Gebruiken **[!UICONTROL Edit]** uit de zoekresultaten kan leiden tot `Not Found` fout. (NPR-37810)

<!--version 2 of description above * When editing Content Fragment from the Assets Search Rail results page, it throws 'Not Found' error. (NPR-37810) -->

### ContentHub {#sites-contenthub-6513}

* De modellen van de hub UI van de context geven niet behoorlijk terug zonder een harde pagina verfrist zich. (NPR-38212)

### E-maileditor {#sites-emaileditor-6513}

* Ondersteuning inschakelen voor komende release van E-mail Core Components [https://github.com/adobe/aem-core-email-components](https://github.com/adobe/aem-core-email-components). (NPR-38445 en NPR-38204)

<!-- version 2 of description above * Allow new email templated under campaign and ambit. (NPR-38445) * The "Approve for Adobe Campaign" workflow was only running for pages which are of type or extending the resource types: "mcm/neolane/components/newsletter", "mcm/campaign/components/newsletter" and "mcm/campaign/components/campaign_newsletterpage". (NPR-38204) -->

### Ervaringsfragmenten {#sites-experiencefragments-6513}

* Wanneer u de actie Navigeren naar pagina gebruikt in de verwijzingen voor een ervaringsfragment, wordt de verkeerde pagina geopend. (NPR-38062)
* Layout-eigenschappen die afkomstig zijn van XF-sjabloon worden niet waargenomen naast een pagina. (NPR-38214)
* Verbeterde prestaties van XF-referentieberekening. (NPR-38269)

<!-- version 2 of description above * Job queue configuration is incorrect - The OSGi configuration for the reference updater job queue has not been ported back to 6.5. This issue leads to jobs being run in the main queue, which has a higher priority and allows more jobs to run in parallel. This flow can lead to CPU exhaustion. (NPR-38269) -->

### Pagina-editor {#sites-pageeditor-6513}

* Verbeter ongedaan maken voor componenten die geen inlineEditing of dropTarget eigenschap in hebben `cq:editConfig`. (NPR-38361)

<!-- version 2 of the description above * When out of the box components that don't have inlineEditing or dropTarget feature in the _cq_editConfig file (navigation, breadcrumb, embed) are deleted > undeleted (by way of Undo), all configurations are lost and empty placeholder reappears. Component must be reconfigured from scratch. (NPR-38361) -->
* De vervolgkeuzelijst Stijlsysteem kan boven aan de pagina zijn geplaatst in plaats van in de context van de component - voor componenten die `cq:editConfig` &quot;afteredit: REFRESH_PAGE&quot;. Dit probleem is nu opgelost. (NPR-38384)

<!-- version 2 of description above* When selecting a style option on a component, the Styles box shifts to the upper left corner of the screen, rather than staying put below the style icon. Happens for components that have  cq:editConfig “afteredit: REFRESH_PAGE”. (NPR-38384) -->
* De tekstcomponent wordt verkeerd uitgelijnd wanneer deze wordt toegevoegd aan geneste lay-outcontainers. (NPR-38193)
* Een leeg stijllusje werd getoond wanneer er geen de config van het Systeem van de Stijl voor een component was; het lusje is nu verborgen wanneer geen config aanwezig is. (NPR-38218)
<!-- version 2 of description above * Style tab is blank on components without styles/policies. (NPR-38218) -->
* De eigenschap `useLegacyResponsiveBehaviour` werkt alleen wanneer dit is geverifieerd. (NPR-37996)
* Als u jquery-ui bijwerkte naar de laatste versie, is de Editor verbroken. (SITES-5647)

### Beveiliging {#sites-security-6513}

* De gebruikersinterface van Gebruikersgroepbeheer is er soms niet in geslaagd om gebruikers te verwijderen, met name in groepen met +20 gebruikers. (NPR-38041)

<!--version 2 of description above * Cannot remove users from user groups. (NPR-38041) -->

### SEO {#sites-seo-6513}

* De Sitemap Generator en de Canonical markering voegen steun voor URLs zonder .html toe. (CIF-2647)
* Voeg steun voor het verwijderen van alternatieve talen toe gebruikend de noindexconfiguratie. (CIF-2496)
* Voeg ondersteuning toe voor aangepaste URL&#39;s waarmee u de standaard canonieke URL kunt overschrijven voor pagina&#39;s met bijna identieke inhoud. (CIF-2747)

### SPA Editor en SDK {#sites-spa-sdk-6513}

* Vanaf 6.5.13, moet u niet meer de knoop van de containercomponent in JCR tot stand brengen alvorens uit te geven als Redacteur van de SPA. A `virtual container` wordt gemaakt voordat deze wordt opgeslagen via de SDK. (SITES-5762)

<!-- version 2 of description above * Virtual container support - Adding a child component to a virtual container that is not yet present in the database implies the creation of a node to represent the container in content structure. (SITES-5762) -->

### Sjablooneditor {#sites-templateeditor-6513}

* Verbeter de regressie dat het publiceren van een veranderde malplaatje niet alle gebiedsdelen publiceerde. (NPR-38274)

<!-- version 2 of description above * Template changes do not get published until you publish a page that uses that template. (NPR-38274) -->
* TemplatedResource valueMap moet diepe leesbewerkingen mogelijk maken volgens ValueMap API. (NPR-38439)

## Sling {#sling-6513}

<!-- OBSOLETE BASED ON CQDOC-19400 * Memory leak in `DiscoveryLiteDescriptor`. (NPR-38288) -->
* Bijwerken `sling-javax.activation` bundel met moeilijke situatie van SLING-8777. (NPR-38077)

<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * Security issues reported under `org.apache.sling.scripting.jst`. (NPR-38067) -->

## Vertaalprojecten {#translation-6513}

* Er worden meerdere keren gestart om te worden gemaakt voor pagina&#39;s waarnaar wordt verwezen/xf. (NPR-38263)
* Veranderd gedrag van het toevoegen van pagina&#39;s aan vertaalprojecten sinds Service Pack 10. Het vertaalproject bevat geen nieuw gemaakte pagina [ex: testpagina-Vrouwen-2] in de lijst, wanneer geselecteerd bovenliggend item van de nieuw gemaakte pagina [niet rechtstreeks de nieuwe pagina]. (NPR-38256)
* Toevoegen `cq:isTranslationLaunch` eigenschap in Launches created by Translation Project. (NPR-38224)
* Launch wordt gemaakt voor een pagina met een XF waarnaar wordt verwezen en die een element bevat. (NPR-38199)
* [!DNL Experience Manager] vertaalgeheugen bijwerken werkt niet. (NPR-38196)
* ES6 inschakelen voor `/libs/cq/gui/components/projects/admin/translation/job/addcontent/clientlibs.js`. (NPR-38306)
* Laatste 18n pakket voor vertalingen voor [!DNL Experience Manager] 6.5 (CQ-4339505)

## Gebruikersinterface {#ui-6513}

* Bijwerken naar `favicon.ico` die in de Experience Manager wordt gebruikt. (CQ-4315324)
* Wanneer u op startpagina > de sectie van Hulpmiddelen bent en klik [!DNL Experience Manager] pictogram, de [!DNL Experience Manager] Navigatievenster moet verschijnen. (NPR-38417)
* ES6 inschakelen voor `/libs/granite/ui/references/clientlibs/coral/references`. (NPR-38303)
* ES6 inschakelen voor `/libs/granite/datavisualization/clientlibs/d3-3.x`. (NPR-38302)
<!-- VULNERABILITY ISSUE - REMOVED AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * AEM‑OP‑09 ‑ Persistent cross‑site scripting selecting paths in templates. (NPR-38301) -->
* Datumkiezer in aanraak-UI wordt weergegeven in het Koreaans. (NPR-38079)
* Dialoogvenster Ontwerpen met meerdere velden, wanneer de velden opnieuw worden gerangschikt waarbij de selectiewaarde van het keuzerondje verloren gaat. (NPR-38063)

## WCM {#wcm-6513}

* [!DNL Experience Manager] MCM (Campagne) 6.5: Oplossingen voor naamgeving van Chinese landinstellingen. (CQ-4308973)
* Unclosed ResourceResolver in com.day.cq.wcm.workflow.impl.WcmWorkflowServiceImpl.autoSubmitPageAfterModification (NPR-38286)

## Installeren [!DNL Experience Manager] 6.5.13.0. {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback -->

* [!DNL Experience Manager] 6.5.13.0 vereist [!DNL Experience Manager] 6.5 Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.13.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.

>[!NOTE]
>
>Adobe raadt u niet aan de installatie van de [!DNL Experience Manager] 6.5.13.0-pakket.

### Installeer het de dienstpak op [!DNL Experience Manager] 6,5 {#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.13.0.zip).

1. Pakketbeheer openen en klikken **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem treedt meestal op in [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.13.0.

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>[!DNL Experience Manager] 6.5.13.0 ondersteunt geen Bootstrap-installatie.

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.13.0)` krachtens [!UICONTROL Installed Products].

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.2.2.3 of hoger (Webconsole gebruiken: `/system/console/bundles`).


### Installeren [!DNL Experience Manager] Forms-invoegtoepassing {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Overslaan als u dit niet gebruikt [!DNL Experience Manager] Forms. Oplossingen in [!DNL Experience Manager] Forms wordt één week na de geplande levering geleverd via een afzonderlijk invoegpakket [!DNL Experience Manager] Service Pack-release.

1. Controleer of u de [!DNL Experience Manager] Service Pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates).

### Installeren [!DNL Experience Manager] Forms op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Oplossingen in [!DNL Experience Manager] Forms op JEE wordt via een afzonderlijk installatieprogramma geleverd.

Voor informatie over het installeren van het cumulatieve installatieprogramma voor [!DNL Experience Manager] Forms op JEE en configuratie na implementatie, zie [releaseopmerkingen](jee-patch-installer-65.md).

>[!NOTE]
>
>Na installatie van het cumulatieve installatieprogramma voor [!DNL Experience Manager] Forms on JEE, installeer het nieuwste Forms add-on pakket, verwijder het Forms add-on pakket uit het `crx-repository\install` en start de server opnieuw op.

### UberJar {#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.13.0 is beschikbaar in de [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.13/)(https://).

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.13</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op de Centrale Bewaarplaats van de Adobe Openbare Maven bewaarplaats (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` tag.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Er is een alternatieve optie opgegeven.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integraties | De **[!UICONTROL AEM Cloud Services Opt-In]** het scherm is verouderd sinds [!DNL Experience Manager] en [!DNL Adobe Target] integratie wordt bijgewerkt in [!DNL Experience Manager] 6.5 De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O]. Het ondersteunt de groeiende rol van Adobe Launch naar instrument [!DNL Experience Manager] De optiewizard is functioneel niet relevant op pagina&#39;s voor analyse en personalisatie. | Systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O] integratie via de respectieve [!DNL Experience Manager] cloudservices. |
| Connectors | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen voor [!DNL Experience Manager] 6.5 | N.v.t. |

## Bekende problemen {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THE LIST.
 -->

<!-- VULNERABILITY ISSUE - REMOVED MAY 23, 2022 AND ADDED TO https://wiki.corp.adobe.com/display/DXContent/Security+and+Vulnerability+issues+for+SP+and+CFP+releases * If you are using Content Fragments and GraphQL, Adobe recommends that you install the following packages on top of 6.5.12.0:

  * [AEM 6.5.12 Sites HotFix-NPR-38144](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2Faem-service-pkg-6.5.12.0-NPR-38144-B0002.zip) (this hot fix replaces SP12, but can be installed on top of SP12) -->

* [Inhoudsfragment AEM met GraphQL Index Package 1.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.3.zip)

* Als [!DNL Microsoft® Windows Server 2019] ondersteunt niet [!DNL MySQL 5.7] en [!DNL JBoss® EAP 7.1], [!DNL Microsoft® Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL AEM Forms 6.5.10.0].

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] van 6.5 tot 6.5.10.0 versie, kunt u bekijken `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

* Wanneer u probeert inhoudsfragmenten of sites/pagina&#39;s te verplaatsen/verwijderen/publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.13.0:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.13.0](/help/release-notes/assets/65130_bundles.txt)

* [Lijst van inhoudspakketten opgenomen in Experience Manager 6.5.13.0](/help/release-notes/assets/65130_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de Adobe Klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

