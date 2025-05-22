---
title: Nota's van de versie voor  [!DNL Adobe Experience Manager]  6.5
description: Vind versieinformatie, wat nieuw is, installeer hoe te, en een gedetailleerde veranderingslijst voor  [!DNL Adobe Experience Manager]  6.5.
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: ec388629ba8908ba52fc681e1d6aa5877f64f8b4
workflow-type: tm+mt
source-wordcount: '5180'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Nieuwste opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, May 29, 2025. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.23.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | donderdag 22 mei 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.23.0 {#what-is-included-in-aem-6523}

[!DNL Experience Manager] 6.5.23.0 bevat nieuwe functies, belangrijke verbeteringen die door de klant worden aangevraagd en opgeloste problemen. Het omvat ook prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 worden vrijgegeven. [ installeer dit Pak van de Dienst ](#install) op [!DNL Experience Manager] 6.5.

<!-- UPDATE FOR EACH NEW RELEASE -->

<!--
## Key features and enhancements

### Sites {#sites}

* A () -->

<!--
### [!DNL Assets]

* A ()
-->

<!--
### Forms {#forms-sp23}

Key features and enhancements in this release include the following:

#### New GA features in AEM Forms {#ga-aem-forms-sp23}

* A ()

#### New Beta features in AEM Forms {#beta-aem-forms-sp23}
-->

## Opgeloste problemen in Service Pack 23 {#fixed-issues}

<!-- 6.5.23.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-6523}

#### Toegankelijkheid {#sites-accessibility-6523}

* Canvassecties in AEM Editor-pagina&#39;s bieden nu ondersteuning voor volledige toetsenbordtoegankelijkheid. Gebruikers kunnen sectitels activeren en knoppen bewerken met alleen het toetsenbord, zonder de muisaanwijzer te hoeven aanwijzen. Deze update zorgt voor compatibiliteit met WCAG 2.1.1 en verbetert de bruikbaarheid in verschillende componenten, zoals Taser, Image, Carousel, Layout, Time Warp en Annotation-modals. (SITES-25256) <!-- 6.5 LTS SP1 -->
* Probleem met toegankelijkheid verholpen in de AEM Page Editor waarbij de toetsenbordfocus onverwachts wordt teruggezet naar het begin van de demografische werkbalk nadat knoppen zoals Persona, Kaart of Verlaten zijn geactiveerd. De geactiveerde knop blijft nu geactiveerd om consistente workflows voor toetsenbordnavigatie en schermlezers te ondersteunen. (SITES-25306)
* Probleem verholpen waarbij het probleem van de toegankelijkheid in de AEM Page Editor is verholpen waarbij canvaselementen in meerdere dialoogvensters en modals (bijvoorbeeld Asset rail of Layout preview) niet alleen met een toetsenbord konden worden gebruikt. Alle interactieve canvaselementen ondersteunen nu toetsenbordnavigatie, waarbij wordt voldaan aan WCAG 2.1-succescriterium 2.1.1 (SITE-25256)
* Probleem met toegankelijkheid verholpen in de gebruikersinterface Sites Admin, waarbij interactieve lijstitems in de pop-up Maken onjuiste ARIA-rollen gebruikten. Elementen die zich als koppelingen gedroegen, werden toegewezen aan `role="listitem"` in plaats van `role="menuitem"` , waardoor ARIA-ontwerppatronen werden overtreden en schermlezers werden verward. De updates zorgen ervoor dat alle lijstcomponenten juiste semantische rollen voor betere toetsenbord en hulptechnologie steun volgen. (SITES-24493)
* Probleem met koppeling van toegankelijkheidslabel voor paginatitel- en -tagvelden opgelost. De AEM-interface koppelt toegankelijkheidslabels nu correct aan de velden Titel en Paginatitel wanneer schermlezers worden gebruikt, zoals JAWS. Met deze correctie wordt een correcte aflezing van labels gegarandeerd en wordt de ADA-compatibiliteit verbeterd voor het maken van pagina&#39;s, eigenschappen en workflows verplaatsen. (SITES-27149)
* Probleem met toegankelijkheid verholpen met tabelidentificatie in het dialoogvenster met machtigingen. De machtigingstabel in AEM gebruikt nu de juiste ARIA-rollen en -kenmerken om ervoor te zorgen dat schermlezers, zoals JAWS, deze correct identificeren als een tabel. De oplossing verbetert de toegankelijkheidseisen en zorgt ervoor dat gebruikers nauwkeurige navigatie- en inhoudsmededelingen ontvangen. (SITES-27140)
* Het ontbrekende visuele label voor invoervelden voor opmerkingen in de tijdlijn is gecorrigeerd. Ontbrekende visuele labels voor invoervelden voor &quot;opmerkingen&quot; zijn gecorrigeerd in de tijdlijnsectie om de toegankelijkheid te verbeteren. De update zorgt ervoor dat schermlezers de veldlabels correct kunnen aankondigen. Deze ervaring verbetert de navigatie en verzending van formulieren voor alle gebruikers, in het bijzonder gebruikers die op ondersteunende hulpmiddelen vertrouwen. (SITES-26903)
* Toegankelijkheid met toetsenbord voor knop met ovaal in tijdlijnopmerkingen gecorrigeerd. Toetsenbordnavigatie ingeschakeld voor de elliptische knop (drie punten) naast opmerkingen onder de tijdlijnsectie. Gebruikers kunnen nu toegang krijgen tot de knop en communiceren met de Tab-toets, waardoor de toegankelijkheid voor gebruikers die alleen op het toetsenbord navigeren, wordt verbeterd. (SITES-26891)
* Verbeterde aankondigingen van NVDA/Narrator voor zoekresultaten in selectievalken. Het dialoogvenster Selectie openen is bijgewerkt om aan te kondigen of zoekresultaten worden gevonden bij gebruik van schermlezers, zoals NVDA of Narrator. Deze verbetering helpt gebruikers die op hulptechnologieën vertrouwen het resultaat van hun onderzoeksacties begrijpen zonder visuele bevestiging te hoeven. (SITES-26883)
* Correcte ARIA-rol voor weglatingspictogram naast veld voor invoer opmerking. Het pictogram met de ellips (drie punten) naast het invoerveld voor opmerkingen is bijgewerkt om de juiste ARIA-rol te gebruiken, zodat schermlezers het element nauwkeurig kunnen identificeren. Deze verbetering verbetert toegankelijkheids naleving en verbetert de ervaring voor gebruikers die zich op hulptechnologieën baseren. (SITES-26881)
* Ongeldige ARIA-kenmerken gecorrigeerd in Coral UI-componenten. Bijgewerkte Coral UI-componenten om ervoor te zorgen dat alle ARIA-kenmerken geldige waarden gebruiken, waardoor de compatibiliteit met toegankelijkheid wordt verbeterd. Er zijn vooral gevallen opgelost waarin ongeldige waarden zoals `aria-modal="dialog"` onjuist werden toegewezen. Dankzij deze verbetering kunnen schermlezers dialoogvensterelementen correct interpreteren, waardoor de toegankelijkheid voor gebruikers die op ondersteunende hulpmiddelen vertrouwen, wordt verbeterd. (SITES-26873)
* Verbeterde zichtbaarheid en knopinfo voor pictogrammen in opnieuw plaatsen. Verbeterde het opnieuw plaatsen gedrag om tooltips vertoning correct voor **Download** te verzekeren, **activa** opnieuw verwerken, en **uitcheckpictogrammen**. Gericht op een toegankelijkheidsprobleem waarbij pictogrammen en hun labels onzichtbaar werden toen de zoominstellingen van de viewport werden gewijzigd of gewijzigd. Deze correctie ondersteunt gebruikers met een laag gezichtsvermogen door de zichtbaarheid te behouden en correcte pictogrambeschrijvingen te bieden tijdens het opnieuw plaatsen. (SITES-26871)

#### Gebruikersinterface Admin{#sites-adminui-6523}

Correctie van Universal Editor URL Service-uitzondering met ontbrekende ExternalAlizer-eindpunten. De Universal Editor URL Service verwerkt nu ontbrekende eindpunten van auteurs, publiceren of lokale ExternalAlizer zonder uitzonderingen te genereren. Admin-gebruikers kunnen de Pagina-editor openen, zelfs als sommige Externalzer-configuraties onvolledig zijn. (SITES-28877) <!-- LTS -->

#### Klassieke interface{#sites-classicui-6523}

* Een probleem in de dialoogvensters Klassieke gebruikersinterface waarbij een knop wordt verborgen als een tekstgebied wordt verborgen en niet opnieuw wordt weergegeven als een gebruiker nogmaals klikt. De correctie zorgt ervoor dat het tekstgebied correct opnieuw verschijnt wanneer van een knevel voorzien, het verwachte gedrag herstelt en verstoringen aan de dynamische werkschema&#39;s van de dialoogdoos voorkomt. (SITES-30230)
* Oplossing voor defecte functionaliteit voor het zoeken van grafische elementen in de klassieke gebruikersinterface na de upgrade naar Service Pack 22. De zoekfunctie voor klassieke UI-afbeeldingselementen verwerkt nu correct namen van elementen met spaties of speciale tekens. Deze update zorgt ervoor dat de functie voor het zoeken naar elementen bestandsnamen correct codeert, zodat zoekfouten worden voorkomen en auteurs de afbeeldingselementen zonder fouten kunnen zoeken en selecteren. (SITES-29151)

#### [!DNL Content Fragments]{#sites-contentfragments-6523}

* Correctie van validatietestfout voor `DeleteVariationIT.testUpdateBasic`. De `DeleteVariationIT.testUpdateBasic` -test mislukt niet meer tijdens de validatieuitvoering van Service Pack. Met deze correctie wordt een ontbrekend teksttoewijzingsprobleem in de JSON-verwerkingslogica gecorrigeerd, zodat de stabiliteit van de test wordt gegarandeerd en onnodige testverstoringen worden voorkomen. (SITES-28022)
* AEM voorkomt nu prestatievermindering die wordt veroorzaakt door onjuist gevormde XMP-metagegevens in afbeeldingselementen. Assets die ongeldige of niet-compatibele XMP-eigenschapsnamen bevatten, zoals die met numerieke segmenten of ongekwalificeerde structuren, activeren niet langer herhaalde waarschuwingslogboeken tijdens de verwerking. Het systeem filtert problematische metagegevens uit om ervoor te zorgen dat de invoer en validatie van elementen zonder fouten zijn voltooid. (SITES-30683) &lt;!— AEM 6.5 LTS SP1>


<!-- #### [!DNL Content Fragments] - Admin{#sites-admin-6523}

* A () -->


#### [!DNL Content Fragments] - Fragmenteditor{#sites-fragments-editor-6523}

Andere auteurs kunnen nog steeds Content Fragments publiceren, zelfs wanneer een andere auteur ze uitcheckt. Dit is in strijd met het beoogde gedrag van de uitcheckfunctie. Deze correctie voorkomt dat andere gebruikers de publicatieknoppen in de ontwerpinterface zien of gebruiken wanneer een inhoudsfragment wordt uitgecheckt. (SITES-30578) <!-- LTS -->

#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-6523}

GraphQL QueryValidationError is opgelost met schema&#39;s voor inhoudsfragmenten. Als u de `cq-dam-cfm-graphql` -bundel vernieuwt, worden fouten in de schemavalidatie gecorrigeerd wanneer u verwijzingen naar inhoudsfragmenten gebruikt. De moeilijke situatie zorgt ervoor dat de vragen van GraphQL behoorlijk zonder handschemahergroepering of herpublicatie na pakketplaatsingen te vereisen functioneren. (SITES-27001) <!-- LTS -->


<!-- #### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6523}

* A () -->

<!-- #### [!DNL Content Fragments] - REST API{#sites-restapi-6523}

* A () -->


#### Component Console{#sites-component-console-6523}

Verbeteringen voor het laden van pagina&#39;s voor &quot;Actief gebruik van componenten&quot;. Hiermee optimaliseert u de pagina &quot;Componenten Live-gebruik&quot; in AEM om te voorkomen dat lege rijen verschijnen wanneer door grote gegevenssets wordt geschoven. Gebruikers die componenten met uitgebreide gebruiksverwijzingen laden, kunnen nu ononderbroken gegevens laden zonder onnodige tussenruimten of lege items. Deze ervaring verbetert paginanavigatie, nauwkeurigheid van bijhouden en beheerefficiëntie in de rapportage van het componentgebruik. (SITES-26454)

#### Core Backend{#sites-core-backend-6523}

* Probleem met de eigenschappenlijst van de Finder voor vaste inhoud veroorzaakt door ongeldige elementnamen. In de Inhoudszoeker worden elementnamen nu correct verwerkt met niet-coderbare tekens. De lijst met middelen in de Pagina-editor mislukt niet meer en genereert geen uitzonderingen wanneer er elementen met problematische namen optreden. (SITES-28722)
* Een probleem waarbij de component `SearchPathLimiter` overdreven logitems heeft gegenereerd door berichten op FOUT-niveau voor elke aanroep af te drukken. Dit gedrag begon na Service Pack 17 en leidde tot prestatieproblemen als gevolg van extreem hoge logvolumes. De moeilijke situatie vermindert het logboekniveau aan DEBUG, beduidend verminderend logboeklawaai en verbeterend systeem controle en kenmerkende efficiency. (SITES-29835)
* Bij onjuist opgemaakte XMP-metagegevens is een fout opgetreden tijdens het verwerken van afbeeldingselementen in de `ValidationDataServlet` . Deze correctie zorgt voor compatibele verwerking van metagegevens en voorkomt overbodige parsering van ongeldige eigenschappen. (SITE-30683) <!-- LTS -->


<!-- #### Core Components{#sites-core-components-6523}

* A () -->

<!-- #### Campaign integration{#sites-campaign-integration-6523}

* A () -->

<!-- #### Experience Fragments{#sites-experiencefragments-6523}

* A () -->

<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-6523}

* A () -->


#### Lanceringen{#sites-launches-6523}

* Correctie van onjuiste weergave op de startdatum tussen 25 december en 31 december. In de gebruikersinterface van Launches worden nu datums tussen 25 en 31 december weergegeven met het juiste jaar. De moeilijke situatie zorgt ervoor dat de data niet meer verkeerd het volgende jaar tonen, vermijdend verwarring tijdens campagneplanning en planning. (SITES-28706)
* Oplossing voor een defecte AEM-opstartsjablonen na de upgrade naar Service Pack 22. AEM Launch-sjablonen worden nu correct geladen na een Service Pack 22-upgrade. Met deze correctie worden ongeldige gegevens in interne startconfiguraties gecorrigeerd, zodat gebruikers Starten kunnen weergeven, bewerken en maken zonder fouten of ontbrekende velden. (SITES-28504)


<!-- #### Link Checker{#sites-link-checker-6523}

* A () -->

<!-- #### MSM - Live Copies{#sites-msm-live-copies-6523}

* A () -->


#### Pagina-editor{#sites-pageeditor-6523}

* Probleem met laden van AssetPicker is opgelost bij lagere schermresoluties. De AssetPicker laadt nu elementen correct wanneer gebruikers met een lagere schermresolutie (1728×1117 of lager) schuiven. Gebruikers ervaren tijdens het schuiven geen ontbrekende elementen meer, waardoor het middelenbeheer over verschillende apparaatbreekpunten wordt verbeterd. (SITES-28065)
* Aankondiging van schermlezer voor vergrendelen en ontgrendelen van pagina&#39;s is opgelost. De Pagina-editor kondigt nu het bericht &quot;Info: De pagina is vergrendeld/ontgrendeld&quot; correct aan wanneer gebruikers de knop Vergrendelen/Ontgrendelen activeren. De oplossing verbetert de compatibiliteit met toegankelijkheid en zorgt ervoor dat schermlezers tijdens het bewerken van de pagina&#39;s dynamische updates ontvangen. (SITES-27143)
* Verbeterd gedrag voor toetsenbordfocus voor componentacties in AEM Authoring. Verbeterde toetsenbordnavigatie in het AEM-ontwerpgereedschap om ervoor te zorgen dat de focus blijft op de nieuw gemaakte of geselecteerde component na handelingen zoals Configureren, Verwijderen of Converteren. Eerder werd de focus naar de bovenkant van de pagina verschoven, wat problemen met toegankelijkheidseisen veroorzaakte. Deze update verbetert de gebruikerservaring voor gebruikers van toetsenbord en ondersteunende hulpmiddelen. Dit gebeurt door logische focusvoortgang te behouden binnen de bewerkingsworkflow. (SITES-26549)
* Verbeterde tabnavigatie in de dialoogvensters Auteur. Verbetert toetsenbordnavigatie in de dialoogvensters van de Auteur van AEM door gebruikers toe te staan vooruit van labels voorzien nadat het de Edit vakje van de Beschrijving bereikt. Eerder werd door focusovervulling in het veld Beschrijving verdere navigatie geblokkeerd zonder speciale toetsencombinaties te gebruiken. De update zorgt ervoor dat gebruikers probleemloos door velden kunnen navigeren met alleen de Tab-toets, waardoor de compatibiliteit met de toegankelijkheid en de gebruikerservaring worden verbeterd. (SITES-26524)
* Er is een regressie geïntroduceerd in AEM 6.5 Service Pack 22 waardoor gebruikers geen spaties konden opnemen in opstarthtels. De correctie herstelt de capaciteit om ruimten te gebruiken, toestaand teams om de namen van de Lancering flexibeler te bepalen en te organiseren, in lijn met verwacht gedrag. (SITES-29414)
* Probleem met vergroten/verkleinen voor componenten binnen lay-outcontainers is opgelost nadat handelingen zijn verborgen of verborgen. De Pagina-editor berekent nu correct kolomwaarden nadat een container voor lay-out is verborgen en verborgen. Gebruikers kunnen de grootte van componenten zonder fouten wijzigen en kolommen worden tijdens het wijzigen van de grootte correct weergegeven. (SITES-28463)
* Verplaatsing van de knop Vaste inhoudsstructuur in de Pagina-editor. De pagina-editor plaatst de configuratieknop van de inhoudsstructuur nu correct onder het bedoelde dialoogvenster Koptaser in plaats van onder de verkeerde sectie. Met deze correctie wordt de CSS voor het dialoogvenster Inhoudsstructuur bijgewerkt zodat `top:0` in plaats van `bottom:0` wordt gebruikt. De juiste plaatsing van de knop wordt gegarandeerd. (SITES-28448)


<!-- #### Replication{#sites-replication-6523}

* A () -->


#### RTF-editor{#sites-rte-6523}

Onverwachte `<br>` -tags corrigeren in de RTF-editor met de Plaintext-plakmodus. De rijke Redacteur van de Tekst behandelt nu correct besnoeiing-en-deegverrichtingen wanneer het gebruiken van plaintext `defaultPasteMode`. Met deze correctie wordt voorkomen dat onverwachte `<br>` -tags worden ingevoegd wanneer gebruikers tekst knippen en plakken in RTE-velden. Hierdoor wordt een schone opmaak gegarandeerd tijdens het bewerken van inhoud. (SITES-27780)

#### Universele editor {#sites-universal-editor-6523}

* Wanneer meerdere aanvragen met de queryparameter naar AEM worden verzonden, wordt het cookie met het inlogtoken mogelijk niet op tijd geretourneerd, wat kan leiden tot een mislukte aanmelding. (SITES-30659) <!-- LTS -->
* Om verenigbaarheid en steun met de managers van SAML te verzekeren, moet u het `service.ranking` bezit vormen zodat de `Query Token Auth` manager *vóór* de `SAML Auth` manager loopt. (SITES-29684)

### [!DNL Assets]{#assets-6523}

* De volgende kwesties komen op [!DNL AEM] op-Premise (6.5.22.0) pagina van de Navigatie na het selecteren van ![ Assets ](/help/assets/assets/Smock_Asset_18_N.svg)**[!UICONTROL Assets]**&#x200B;voor, navigerend aan **[!UICONTROL Search Adobe Stock]**&#x200B;omslag, en het selecteren van een voorraadbeeld:
   * De geselecteerde voorraadafbeelding kan geen licentie krijgen en worden opgeslagen omdat een leeg vervolgkeuzemenu wordt weergegeven wanneer u op **[!UICONTROL License & Save]** klikt.
   * Als u de Stock-afbeelding selecteert of de URL van de voorraadpagina opnieuw invoert, wordt de startpagina van [!DNL AEM] weergegeven, zodat de Adobe Stock-afbeelding niet toegankelijk is. (ASSETS-48687)
* Problemen tijdens het beheren van mappen als de naam van de map een `/` bevat in de naam op de navigatiepagina [!DNL AEM] Op locatie (6.5.22.0 ). (ASSETS-46740)
* Op [!DNL AEM] 6.5, laadt de pagina van elementdetails niet van ![ de mening van de Inzameling ](/help/assets/assets/Smock_Collection_18_N.svg)**[!UICONTROL Collections]**&#x200B;toe te schrijven aan hoog geheugengebruik. (ASSETS-46738)
* Problemen met integratie met [!DNL InDesign] als `Day CQ DAM Mime Type OSGI` Service identificeren [!DNL InDesign] bestanden onjuist als `x-adobe-indesign` in plaats van `x-indesign` . (ASSETS-45953)
* [!DNL AEM 6.5.21] -sessilek komt overeen met de workflowstap uit de box **[!UICONTROL Scheduled publish to Brand Portal]** . (ASSETS-44104)
* **[!UICONTROL Out of Memory (OOM)]** fouten worden in [!DNL AEM] weergegeven bij het verwerken en publiceren van afbeeldingen. Dit probleem is veroorzaakt door vervangen methoden in workflows, zoals **[!DNL Dam Asset update]** en **[!DNL Dynamic Media: Reprocess assets]** . (ASSETS-43343)
* Nadat u een kleine wijziging hebt aangebracht, zoals het bijwerken van de titel, opent u de **[!DNL Connected Assets configuration]** opnieuw op de lokale instantie Sites en slaat u deze opnieuw op. De externe instantie verliest vervolgens de verbinding met de lokale instantie. Dit heeft tot gevolg dat er geen communicatie tot stand kan worden gebracht met de lokale instantie Sites. (ASSETS-44484)
* Wanneer in [!DNL AEM 6.5.21] een element in de lijstweergave wordt geüpload en een tweede upload wordt uitgevoerd, geeft [!DNL AEM] een **[!UICONTROL 0 of NaN assets uploaded]** -fout weer. (ASSETS-44124)

#### [!DNL Dynamic Media]{#assets-dm-6523}

Een eigenschap metadata (`jcr:content/metadata/dam:scene7SmartCropStatus`) toegevoegd aan elementen voor het identificeren van mislukte generaties Slim uitsnijden. Maakt efficiënt zoeken, filteren en herverwerken van middelen met SmartCrop-problemen mogelijk via handmatige of geautomatiseerde workflows. (ASSETS-46237)

#### [!DNL Dynamic Media] - Hybride modus {#assets-dm-hybrid-6523}

##### Dynamische media - hybride invoegtoepassing (AEM 6.5.23 en hoger)

Vanaf AEM 6.5 Service Pack 23 is er een nieuw invoegpakket beschikbaar voor Dynamic Media - Hybride modus. Dit pakket bevat de `cq-scene7-imaging` -bundel die specifiek compatibel is met de modus Dynamische media - Hybride uitvoering.

**Zeer belangrijke inbegrepen moeilijke situatie**

Probleem verholpen met Dynamic Media - hybride implementaties waarbij updates van de parameter `catalog.expiration` onder `/conf/global/settings/dam/dm/imageserver` niet werden weerspiegeld op de URL&#39;s van de server of auteur, ondanks dat replicatie zonder fouten is gelukt. De update zorgt voor consistente vervalwaarden tussen CRX/DE, de serverreactie en openbare bezorgings-URL&#39;s. Het verbetert op zijn beurt het cachegedrag en de betrouwbaarheid van afbeeldingstransformaties. (ASSETS-44837)

**Belangrijke overwegingen**

* De `cq-scene7-imaging` bundel in de basisAEM 6.5.23 (en recenter) installatie is *niet compatibel* met Dynamische Media - Hybride looppaswijze.
* Het installeren van Service Pack 23 (en recenter) alleen werkt *niet automatisch* bestaande `cq-scene7-imaging` bundel op de instanties van AEM bij die voor Dynamische Media - Hybride (`-r dynamicmedia` looppaswijze) worden gevormd.

**wanneer om het Hybride toe:voegen-op pakket te installeren**

* Bij een rechtstreekse upgrade naar AEM 6.5.23 (en hoger) vanaf AEM 6.5.19 of eerder.
* Als u oplossingen nodig hebt die specifiek zijn voor de functie Dynamische media - Hybride.
* Bij de implementatie van een nieuwe Dynamic Media - Hybride-instantie rechtstreeks van AEM 6.5 GA (algemene beschikbaarheid) naar Service Pack 23 (en hoger).

**Download Hybride toe:voegen-op pakket**

Het Hybrid Add-on-pakket is beschikbaar op Software Distribution en is openbaar toegankelijk wanneer AEM 6.5.23 op donderdag 22 mei 2025 officieel vrijgeeft.

[ Download Dynamische Media - Hybride toe:voegen-op pakket ](https://author-p11553-e21065.adobeaemcloud.com/ui#/aem/assetdetails.html/content/dam/aem/public/adobe/packages/cq650/hotfix/cq-dam-delivery-65-hybrid-addon-1.0.zip).


### [!DNL Forms]{#forms-6523}

Correcties in [!DNL Experience Manager] Forms worden één week na de geplande releasedatum van [!DNL Experience Manager] Service Pack via een afzonderlijk invoegpakket geleverd. In dit geval is de invoegtoepassing AEM 6.5.23.0 Forms gepland voor donderdag 29 mei 2025. Er wordt een lijst met Forms-correcties en -verbeteringen toegevoegd aan deze sectie na de release.

#### Forms Captcha {#forms-captcha-6523}

* Verbeterde reCAPTCHA-waarschuwingen in Adaptive Forms door het bijwerken van de verzendfoutcodes naar 400. Ook, verfijnde logboekalarm om tussen onderbrekingen, verlopen, en beide mislukkingen van de ontdekkingsopsporing te onderscheiden, die het verbeteren van het oplossen van problemennauwkeurigheid en systeemwaarneming verbeteren. (FORMS-19240)
* Een niet-gesloten `ResourceResolver` -instantie in `ReCaptchaConfigurationServiceImpl` gesloten om mogelijke bronlekken te voorkomen en de stabiliteit van het systeem te verbeteren bij gebruik van reCAPTCHA-integratie in AEM Forms. (FORMS-19242)
* Verbeterde CAPTCHA-configuratieverwerking voor AEM Forms door ervoor te zorgen dat de juiste configuratie aan elk formulier wordt gekoppeld wanneer er meerdere items in de map `/conf/global` aanwezig zijn. Voorkomt onbedoeld gebruik van onjuiste CAPTCHA-instellingen wanneer de configuratiecontainer niet expliciet is geselecteerd. (FORMS-19239)


<!--
#### XMLFM {#forms-xmlfm-6523}

* A () -->

<!--
#### [!DNL Adaptive Forms] {#adaptive-forms-6523}

* A () -->

<!--
#### [!DNL Forms Designer] {#forms-designer-6523}

* A () -->


### Stichting {#foundation-6523}

* Probleem verholpen met Coral Alert Banners waarbij de tekstkleur wit in plaats van zwart wordt weergegeven na de upgrade naar Service Pack 21. Hiermee zorgt u ervoor dat de juiste opmaak wordt toegepast om het juiste contrast en de leesbaarheid van waarschuwingsberichten in de interface te behouden. (NPR-42359)
* Toegevoegde steun voor integratie OAuth in Slimme configuratie van Markeringen om zich aan de verval van JWT (het Token van het Web JSON) te richten. Zorgt voor voortdurende functionaliteit van functies voor slimme tags met behulp van bijgewerkte verificatiemethoden. (NPR-42296)

#### Apache Felix {#foundation-apachefelix-6523}

Oplossing voor een NullPointerException die voorkwam toen het uploaden van dossiers van de privé sleutel aan een binair-type bezitsgebied in CRX, die verenigbaarheid herstelde die door Service Pack 16 aanwezig was. Schakelt veilige workflows voor het uploaden van sleutelbestanden in AEM Managed Services in zonder serverfouten of onderbrekingen in de certificaatvernieuwingsprocessen. (CQ-4359178)


<!--
#### Campaign{#foundation-campaign-6523}

* A () -->

<!--
#### Cloud Services{#foundation-cloudservices-6523}

* A () -->

<!--
#### Communities {#foundation-communities-6523}

* A () -->

<!--
#### Content distribution{#foundation-content-distribution-6523}

* A () -->

<!--
#### CRX {#foundation-crx-6523}

* A () -->


#### Graniet{#foundation-granite-6523}

* Oplossing voor OSGi-afhankelijkheidscycli tussen Apache Sling-scriptservices die vertragingen of fouten veroorzaakten bij het laden van HTML-pagina&#39;s na de upgrade naar Service Pack 21. Bijgewerkte verwijzingen naar interne services om cyclische afhankelijkheden met `SightlyScriptingEngineFactory` en verwante componenten te voorkomen, waardoor de betrouwbaarheid en het opstartgedrag van de scriptengine worden verbeterd. (GRANITE-56808)
* De bijgewerkte Manuscripten van het Gebruik JS in Apache Sling om slechts op bestelling in plaats van ongeduldig bij opstarten te laden, die draadgeschil elimineert en het risico vermindert dat publiceer servers onder lading niet reageren. Deze verandering verbetert serverstabiliteit en reactietijden tijdens hoog-verkeersscenario&#39;s door middelvergrendeling te verhinderen die door vroege manuscriptresolutie wordt veroorzaakt. (GRANITE-56611)
* Correctie van een probleem in AEM Omnzoeker waarbij plaatsaanduidingen voor invoervelden onjuist als labels worden weergegeven, wat tot visuele verwarring leidt. Zorgt voor een juiste weergave van plaatsaanduidingen in filtervelden, zodat een consistent en toegankelijk formuliergedrag behouden blijft. (GRANITE-51791)
* Oplossing voor een serverfout die is geactiveerd wanneer u meer dan 30 CFM&#39;s (Content Fragment Models) selecteert met referenties voor meerdere velden in de modeleditor voor inhoudsfragmenten. Verbeterde de component van de filtersuggestie om POST verrichtingen te steunen. Hierdoor kunnen grote referentiesets correct worden verwerkt tijdens het maken van inhoudsfragmenten en kan de stabiliteit van modelconfiguraties met een hoog volume worden verbeterd. (GRANITE-57164)
* Oplossing voor een probleem in CFM&#39;s waarbij het klikken dicht bij een selectievakje de status onbedoeld in- en uitschakelde. Bijgewerkte stijlen om de activering van de klik te beperken tot het element van het checkbox, onbedoelde gebruikersinteractie te verhinderen en vormbruikbaarheid en toegankelijkheid te verbeteren. (GRANITE-52384)


<!--
#### Integrations{#foundation-integrations-6523}

* A () -->


#### Jetty{#foundation-jetty-6523}

Oplossing voor een probleem waarbij API-aanroepen door SNI-validatie via HTTPS werden geblokkeerd voor AEM-klanten die Dispatcher SSL-configuraties met aangepaste hostheaders gebruikten. Introduceert een optie om SNI-validatie uit te schakelen als onderdeel van de Jetty-configuratie, waardoor compatibiliteit met specifieke reverse-proxyinstellingen mogelijk is, waar `mod_proxy` niet mogelijk is. (NPR-42614)


<!--
#### Localization{#foundation-localization-6523}

* A () -->

<!--
#### Oak {#foundation-oak-6523}

* A () -->


#### Platform{#foundation-platform-6523}

* Het samenvoegen van tags is nu opgelost doordat de samengevoegde tagwaarde altijd correct wordt weergegeven in de verschillende elementen, ongeacht of tags inline zijn gemaakt of via de methode voor het maken van de standaardtag. Hiermee voorkomt u dat restwaarden van `EN:title` -velden de weergave van samengevoegde tags overschrijven. (CQ-4358812)
* Correctie van herhaalde codering van ampersand-tekens in tagwaarden in het dialoogvenster voor het bewerken van tags. Hiermee voorkomt u dat extra &#39;&amp;&#39;-entiteiten bij elke keer opslaan worden toegevoegd, zodat de waarden van de tags schoon en consistent blijven voor alle bewerkingen en weergavefouten in geschreven inhoud worden voorkomen. (CQ-4359048)
* Oplossing voor een `ClassCastException` -fout die voorkomt dat e-mailberichten worden verzonden bij het verzenden van een adaptief formulier in AEM 6.5 via WebSphere®. De oplossing maakt een geslaagde e-mailverzending mogelijk door de compatibiliteit tussen `com.sun.mail.handlers.text_plain` en `java.activation.DataContentHandler` te garanderen, uitgelijnd op de configuratie van de e-mailhandler die door WebSphere®-omgevingen wordt verwacht. (NPR-42500)
* Verbeterde foutafhandeling in Package Manager door ervoor te zorgen dat AEM een duidelijk bericht krijgt wanneer de installatie mislukt en de foutreactie anders leeg is. Deze oplossing voorkomt stille fouten en hulpmiddelen bij snellere foutopsporing tijdens de implementatie van pakketten. (NPR-42375)

<!--
#### Security{#foundation-security-6523}

* A -->

<!--
#### Sling{#foundation-sling-6523}

* A () -->


#### Vertaling{#foundation-translation-6523}

Vaste een NullPointerException (NPE) kwestie teweeggebracht toen het bijwerken van de Fragmenten van de Inhoud in werkschema&#39;s gebruikend {het Exemplaar van de Taal van 0} Update **.** Deze correctie zorgt ervoor dat werkstromen geen ontbroken staat ingaan of blijven vastzitten in een lopende staat wanneer het uitgeven van inhoud verbonden aan vertaalverwijzingen. (NPR-42115)

#### Gebruikersinterface{#foundation-ui-6523}

Voegt ontbrekende `title` attributen aan Koraal UI dialoogvakknopen zoals **toe Gedaan** en **annuleert** in component geeft dialoogdozen uit om toegankelijkheid te verbeteren en geautomatiseerde bevestiging toe te laten. Zorgt ervoor dat de knopen verwachte attributen over prijsverhogingsteruggave behouden, die mislukkingen in op selenium-Gebaseerde tests UI verhinderen. (NPR-42412)

#### WCM{#foundation-wcm-6523}

Vaste een kwestie die pagina&#39;s verhindert aan vertaalbanen worden toegevoegd wanneer het gebruiken van **Exemplaar van de Taal van de Update** in milieu&#39;s met Service Pack 19 of later. Zorgt ervoor dat de vertaalworkflows doorgaan zoals u had verwacht, zodat de pagina&#39;s zonder handmatige tussenkomst correct tussen de taalkopieën kunnen worden overgedragen. (CQ-4357929)

#### Workflow{#foundation-workflow-6523}

Oplossing voor een probleem in `EmailNotificationServiceProcessor` waar de methode `getSegmentId` retourneert `null` na hotfix-implementatie, waardoor e-mailtriggers mislukken tijdens workflowverwerking. Hiermee herstelt u de correcte logica voor de resolutie van segment-id&#39;s door ervoor te zorgen dat de processor de vereiste `SegmentInfo` -waarden ophaalt ter ondersteuning van workflows voor e-mailmeldingen over AEM-instanties. (CQ-4359755)


## Installeren [!DNL Experience Manager] 6.5.23.0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.23.0 requires [!DNL Experience Manager] 6.5. Zie [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het Pak van de Dienst is beschikbaar op de Distributie van de Software van Adobe [&#128279;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer [!DNL Experience Manager] 6.5.23.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe raadt u niet aan het pakket [!DNL Experience Manager] 6.5.23.0 te verwijderen of te verwijderen. Daarom moet u, voordat u het pakket installeert, een back-up van de `crx-repository` maken voor het geval u deze moet terugdraaien. <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- FORMS For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->

### Het Service Pack installeren op [!DNL Experience Manager] 6.5{#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van de [!DNL Experience Manager] -instantie.

1. Download het Sack van de Dienst van [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.23.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Open Package Manager en selecteer vervolgens **[!UICONTROL Upload Package]** om het pakket te uploaden. Om meer te weten, zie [ Manager van het Pakket ](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]** .

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [ de Opslag van Gegevens van Amazon S3 ](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>Het dialoogvakje op de Manager UI van het Pakket eindigt soms tijdens de installatie van het Pak van de Dienst. Adobe raadt u aan te wachten totdat de foutenlogboeken zich stabiliseren voordat u de implementatie opent. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installatie succesvol is. Dit probleem doet zich doorgaans voor in de [!DNL Safari] -browser, maar kan soms ook in elke browser optreden.

**Automatische installatie**

Er zijn twee verschillende methoden die u kunt gebruiken om [!DNL Experience Manager] 6.5.23.0 te installeren. <!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in de map `../crx-quickstart/install` wanneer de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik [ HTTP API van de Manager van het Pakket ](/help/sites-administering/package-manager.md#package-share). Gebruik `cmd=install&recursive=true` om de geneste pakketten te installeren.

>[!NOTE]
>
>Experience Manager 6.5.23.0 biedt geen ondersteuning voor Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

**bevestigt de installatie**

Om de platforms te kennen die om met deze versie worden verklaard te werken, zie de [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager (6.5.23.0)` onder [!UICONTROL Installed Products] . <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-bundels staan **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de OSGi-console (Webconsole gebruiken: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.20 of hoger (Webconsole gebruiken: `/system/console/bundles` ). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE. CHECK WITH SAMEER DHAWAN -->

### Service Pack installeren voor [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Voor instructies om het Service Pack op Experience Manager Forms te installeren, zie [ de installatieinstructies van het Pak van de Dienst van Experience Manager Forms ](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>De Adaptieve eigenschap van Forms, beschikbaar in [ AEM 6.5 QuickStart ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/implementing/deploying/deploying/deploy), wordt ontworpen voor exploratie en evaluatiedoeleinden slechts. Voor productiegebruik is het van essentieel belang een geldige licentie voor AEM Forms te verkrijgen, aangezien voor de adaptieve Forms-functionaliteit een correcte licentie vereist is.

### GraphQL-indexpakket installeren voor Experience Manager-inhoudsfragmenten{#install-aem-graphql-index-add-on-package}

De klanten die GraphQL gebruiken moeten het [ Fragment van de Inhoud van Experience Manager met het Pakket van de Index van GraphQL 1.1.1 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip) installeren.

Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

### UberJar{#uber-jar}

UberJar voor [!DNL Experience Manager] 6.5.23.0 is beschikbaar in de [ Gemaakt Centrale bewaarplaats ](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.22/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [ hoe te om UberJar ](/help/sites-developing/ht-projects-maven.md) te gebruiken en de volgende gebiedsdeel in uw projectPOM te omvatten: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.23</version>
  <scope>provided</scope>          
  </dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Centrale Bewaarplaats van de Bewaarplaats van Adobe Public Maven (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar` . Er is dus geen `classifier` , met `apis` als waarde, voor de tag `dependency` .



## Verouderde en verwijderde functies{#removed-deprecated-features}

Zie [ Vervangen en verwijderde eigenschappen ](/help/release-notes/deprecated-removed-features.md/) voor een gedetailleerde lijst van alle eigenschappen afgekeurd of verwijderd voor AEM 6.5.

### SPA-editor {#spa-editor}

[ de Redacteur van het KUUROORD ](/help/sites-developing/spa-overview.md) is afgekeurd voor nieuwe projecten die met versie 6.5.23 van AEM 6.5 beginnen. De redacteur van het KUUROORD blijft gesteund voor bestaande projecten, maar zou niet voor nieuwe projecten moeten worden gebruikt.

De voorkeurseditors voor het beheer van inhoud zonder kop in AEM zijn nu:

* [ de Universele Redacteur ](/help/sites-developing/universal-editor/introduction.md) voor het visuele uitgeven.
* [ de Redacteur van het Fragment van de Inhoud ](/help/sites-developing/universal-editor/introduction.md) voor op vorm-gebaseerde het uitgeven.

## Bekende problemen{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

* **Verwant aan Oak**
Van Service Pack 13 en hierboven, is het volgende foutenlogboek begonnen te verschijnen dat het persistentiegeheime voorgeheugen beïnvloedt:

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.0.202/5]
  at org.h2.mvstore.DataUtils.newMVStoreException(DataUtils.java:1004)
      at org.h2.mvstore.MVStore.getUnsupportedWriteFormatException(MVStore.java:1059)
      at org.h2.mvstore.MVStore.readStoreHeader(MVStore.java:878)
      at org.h2.mvstore.MVStore.<init>(MVStore.java:455)
      at org.h2.mvstore.MVStore$Builder.open(MVStore.java:4052)
      at org.h2.mvstore.db.Store.<init>(Store.java:129)
  ```

  of

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.1.214/5].
  ```

  U kunt deze uitzondering als volgt oplossen:

   1. De volgende twee mappen verwijderen uit `crx-quickstart/repository/`

      * `cache`
      * `diff-cache`

   1. Installeer het Service Pack of start Experience Manager as a Cloud Service opnieuw.
Er worden automatisch nieuwe mappen van `cache` en `diff-cache` gemaakt en er is geen uitzondering meer die gerelateerd is aan `mvstore` in de `error.log` .

* Werk uw GraphQL-query&#39;s bij die mogelijk een aangepaste API-naam voor uw inhoudsmodel hebben gebruikt om in plaats daarvan de standaardnaam van het inhoudsmodel te gebruiken.

* Een GraphQL-query kan de `damAssetLucene` index gebruiken in plaats van de `fragments` index. Deze handeling kan resulteren in GraphQL-query&#39;s die mislukken of die lang duren.

  `damAssetLucene` moet zijn geconfigureerd om de volgende twee eigenschappen op te nemen onder `/indexRules/dam:Asset/properties` om het probleem op te lossen:

   * `contentFragment`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/contentFragment"`
      * `propertyIndex="{Boolean}true"`
      * `type="Boolean"`
   * `model`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/data/cq:model"`
      * `ordered="{Boolean}true"`
      * `propertyIndex="{Boolean}true"`
      * `type="String"`

  Nadat de indexdefinitie is gewijzigd, is opnieuw indexeren vereist (`reindex` = `true`).

  Na deze stappen zouden de vragen van GraphQL sneller moeten presteren.

* Wanneer u probeert inhoudsfragmenten, sites of pagina&#39;s te verplaatsen, te verwijderen of te publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald. De achtergrondquery is mislukt. De functionaliteit werkt dus niet.
U zorgt voor een correcte bewerking door de volgende eigenschappen toe te voegen aan het indexdefinitieknooppunt `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Als u uw [!DNL Experience Manager] -instantie upgradet van 6.5.0 tot 6.5.4 naar het meest recente Service Pack op Java™ 11, ziet u `RRD4JReporter` uitzonderingen in het `error.log` -bestand. Start de instantie van [!DNL Experience Manager] opnieuw om de uitzonderingen te stoppen. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Gebruikers kunnen de naam van een map in een hiërarchie in [!DNL Assets] wijzigen en een geneste map publiceren naar [!DNL Brand Portal] . De titel van de map wordt echter pas bijgewerkt in [!DNL Brand Portal] als de hoofdmap opnieuw wordt gepubliceerd.

* De volgende fouten en waarschuwingsberichten kunnen worden weergegeven tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] met de Target Standard API (IMS-verificatie), leidt het exporteren van Experience Fragments naar Target tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Er zijn geen onderhoudsvensters gevonden in `granite/operations/maintenance` .
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` : er zijn geen onderhoudsvensters gevonden in `granite/operations/maintenance` .
   * De hotspot in een interactieve afbeelding voor dynamische media is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : time-out die wacht tot de registerwijziging niet is geregistreerd.

* Vanaf AEM 6.5.15 heeft de Rhino JavaScript Engine die door de ```org.apache.servicemix.bundles.rhino``` -bundel wordt geleverd, een nieuw hoistinggedrag. De manuscripten die de strikte wijze (```use strict;```) gebruiken moeten hun correcte variabelen verklaren. Anders worden ze niet uitgevoerd en wordt er een runtimefout gegenereerd.

* Als u labelen van verwant kant-en-klare inhoud via een officieel updatepakket installeert, wordt de standaardinstelling van de eigenschap languages van het knooppunt `/content/cq:tags` hersteld. Deze actie is waar voor de Packs van de Dienst, de Pakketten van de Dienst van de Veiligheid, de Uitgebreide Packs van de Eigenschap, de Cumulatieve Packs van de Eigenschap, de flarden, etc. Daarom is het noodzakelijk om het uit de eigenschappen vóór installatie toe te voegen.

### Bekend probleem voor AEM Sites {#known-issues-aem-sites-6523}

* Voorvertoning van inhoudfragmenten mislukt als gevolg van DoS-beveiliging voor een grote boomstructuur met fragmenten. Zie het [ KB- artikel over Standaard de configuratieopties van de Vraag van GraphQL van de Uitvoerder ](https://experienceleague.adobe.com/nl/docs/experience-cloud-kcs/kbarticles/ka-23945) (SITES-17934)



### Bekende problemen voor AEM Forms {#known-issues-aem-forms-6523}

* Als de HTML naar PDF-conversie mislukt op een SUSE® Linux® (SLES 15 SP6 en hoger)-server met de volgende fout:

  ```Auto configuration failed 4143511872:error:0E079065:configuration file routines:DEF_LOAD_BIO:missing equal sign:conf_def.c:362:line 57```
Stel vervolgens de volgende omgevingsvariabele in en start de server opnieuw:
  `OPENSSL_CONF=/etc/ssl`

* Nadat u AEM Forms JEE Service Pack 21 (6.5.21.0) hebt geïnstalleerd, voert u de volgende stappen uit om het probleem op te lossen als u dubbele vermeldingen van Geode jars `(geode-*-1.15.1.jar and geode-*-1.15.1.2.jar)` onder de map `<AEM_Forms_Installation>/lib/caching/lib` (FORMS-14926) vindt:

   1. Stop de locators, als zij lopen.
   1. Stop de AEM-server.
   1. Ga naar de `<AEM_Forms_Installation>/lib/caching/lib` .
   1. Verwijder alle Geode-patchbestanden behalve `geode-*-1.15.1.2.jar` . Bevestig dat alleen de Geode-jars met `version 1.15.1.2` aanwezig zijn.
   1. Open de opdrachtprompt in de beheerdermodus.
   1. Installeer de Geode-patch met het `geode-*-1.15.1.2.jar` -bestand.

* Als een gebruiker een voorvertoning probeert te bekijken van een conceptbrief met opgeslagen XML-gegevens, blijft deze voor bepaalde letters vastzitten in de status `Loading` . Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (FORMS-14521)

* Na de upgrade naar AEM Forms Service Pack 6.5.21.0 voert de `PaperCapture` -service geen OCR-bewerkingen (Optical Character Recognition) uit op PDF&#39;s. De service genereert geen uitvoer in de vorm van een PDF- of logbestand. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (CQDOC-21680)

* Toen gebruikers van AEM 6.5 Forms Service Pack 18 of 19 aan Service Pack 20 of 21 bevorderden, ontmoetten zij een fout van de JSP compilatie. Door deze fout konden ze geen aangepaste formulieren openen of maken. Het veroorzaakte ook problemen met andere interfaces van AEM. Die interfaces omvatten de Redacteur van de Pagina, UI van AEM Forms, de redacteur van het Werkschema, en het Overzicht UI van het Systeem. (FORMS-15256)

  Voer de volgende stappen uit om een dergelijk probleem op te lossen:
   1. Navigeer naar de map `/libs/fd/aemforms/install/` in CRXDE.
   1. Verwijder de bundel met de naam `com.adobe.granite.ui.commons-5.10.26.jar` .
   1. Start de AEM-server opnieuw.

* Na het bijwerken aan AEM Forms Service Pack 20 (6.5.20.0) met Forms toe:voegen-On, configuraties die zich op de erfenisDienst van Adobe Analytics Cloud baseren gebruikend op referentie-gebaseerde authentificatieophouden werkend. Hierdoor konden de analyseregels niet correct worden uitgevoerd. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (FORMS-15428)

* Wanneer een gebruiker AEM Forms Service Pack 20 (6.5.20.0) op de JEE server bijwerkt en PDFs gebruikend de outputdiensten produceert, geven PDFs met toegankelijkheidskwesties terug. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (LC-3922112)
* Wanneer een gebruiker gecodeerde PDF&#39;s genereert met de uitvoerservice op JEE, wordt &quot;Onjuiste structuurwaarschuwing&quot; weergegeven. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (LC-392/2038)
* Wanneer een formulier wordt verzonden op AEM Forms JEE, worden de instanties van een herhalend XML-element verwijderd uit de gegevens. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (LC-392/2017)
* Wanneer een gebruiker in een Linux®-omgeving een adaptief formulier (op JEE) rendert in HTML, wordt het formulier niet correct weergegeven. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (LC-3921957)
* Wanneer een gebruiker een XTG-bestand in PostScript-indeling converteert met de Output Service op AEM Forms JEE, mislukt dit met de fout: `AEM_OUT_001_003: Unexpected Exception: PAExecute Failure: XFA_RENDER_FAILURE` . Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (LC-3921720)
* Na upgrade naar AEM Forms Service Pack 18 (6.5.18.0) op de JEE-server, kan een gebruiker een formulier verzenden waardoor HTML5 of PDF forms en XMLFM niet vastlopen. Om hotfix te downloaden en te installeren, verwijs naar [ Hotfixes van Adobe Experience Manager Forms ](/help/release-notes/aem-forms-hotfix.md#hotfix-for-adaptive-forms) artikel. (LC-3921718)
* In de Voorproef van de Druk van de Interactieve Communicatie Agent UI, wordt het muntsymbool (zoals het dollarteken $) inconsistent getoond voor alle gebiedswaarden. Deze wordt weergegeven voor waarden tot en met 999, maar ontbreekt voor waarden van 1000 en hoger. (FORMS-16557)
* Eventuele wijzigingen in de XDP van geneste lay-outfragmenten in een interactieve communicatie worden niet weerspiegeld in de IC-editor. (FORMS-16575)
* In de Voorproef van de Druk van de Interactieve Communicatie Agent UI, worden sommige berekende waarden niet correct getoond. (FORMS-16603)
* Wanneer de brief in de Voorproef van de Druk wordt bekeken, wordt de inhoud veranderd. Dat wil zeggen dat sommige spaties verdwijnen en dat bepaalde letters worden vervangen door `x` . (FORMS-15681)
* Wanneer een gebruiker een instantie WebLogic 14c vormt, ontbreekt de dienst PDFG in AEM Forms Service Pack 21 (6.5.21.0) op JEE die op JBoss® loopt toe te schrijven aan klasseconflicten die de bibliotheek SLF4J impliceren. De fout wordt als volgt weergegeven (CQDOC-22178):

  ```java
  Caused by: java.lang.LinkageError: loader constraint violation: when resolving method "org.slf4j.impl.StaticLoggerBinder.getLoggerFactory()Lorg/slf4j/ILoggerFactory;"
  the class loader org.ungoverned.moduleloader.ModuleClassLoader @404a2f79 (instance of org.ungoverned.moduleloader.ModuleClassLoader, child of 'deployment.adobe-livecycle-jboss.ear'
  @7e313f80 org.jboss.modules.ModuleClassLoader) of the current class, org/slf4j/LoggerFactory, and the class loader 'org.slf4j.impl@1.1.0.Final-redhat-00001' @506ab52
  (instance of org.jboss.modules.ModuleClassLoader, child of 'app' jdk.internal.loader.ClassLoaders$AppClassLoader) for the method's defining class, org/slf4j/impl/StaticLoggerBinder,
  have different Class objects for the type org/slf4j/ILoggerFactory used in the signature
  ```



## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in deze [!DNL Experience Manager] 6.5 versie van het Service Pack:

* [ Lijst van bundels OSGi inbegrepen in Experience Manager 6.5.23.0](/help/release-notes/assets/65230-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [ Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.23.0](/help/release-notes/assets/65230-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->



## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Neem contact op met uw Adobe-accountmanager als u een klant bent en toegang nodig hebt.

* [ download van het Product bij licensing.adobe.com ](https://licensing.adobe.com/)
* [ de Klantenondersteuning van Adobe van het Contact ](https://experienceleague.adobe.com/nl/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager]  productpagina ](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager]  6.5 documentatie ](https://experienceleague.adobe.com/nl/docs/experience-manager-65)
>* [ Abonneren aan de updates van het de prioritaire product van Adobe ](https://www.adobe.com/subscription/priority-product-update.html)
