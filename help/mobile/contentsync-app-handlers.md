---
title: App-handlers buiten vak
seo-title: App-handlers buiten vak
description: Volg deze pagina voor meer informatie over de handlers voor Adobe PhoneGap Enterprise met AEM.
seo-description: Volg deze pagina voor meer informatie over de handlers voor Adobe PhoneGap Enterprise met AEM.
uuid: 436038cb-fb76-4bb5-ae79-5d4043b81dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fec86f03-f81e-460a-9f84-d6304c95128c
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---


# Out of the Box App Handlers{#out-of-the-box-app-handlers}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Zie de volgende richtlijnen voor het ontwikkelen van Content Sync Handlers:

* Handlers moeten *com.day.cq.contentsync.handler.ContentUpdateHandler* implementeren (rechtstreeks of een klasse uitbreiden die dat doet)
* Handlers kunnen *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler* uitbreiden
* Handler mag alleen true rapporteren als deze de cache ContentSync heeft bijgewerkt. Als u Waar onjuist rapporteert, AEM een update maken.
* De manager zou slechts het geheime voorgeheugen moeten bijwerken als de inhoud werkelijk veranderde. Schrijf niet naar de cache als een wit niet nodig is en vermijd het maken van updates.

## Buiten de handlers van de Doos {#out-of-the-box-handlers}

De volgende lijst bevat een lijst met apps die niet in de verpakking staan:

**** mobileapppagesRenders app pages.

* ***type - String***  - mobileapppages
* ***path - String***  - path to a page
* ***extension - String***  - Extension, die moet worden gebruikt in de aanvraag. Voor pagina&#39;s is dit bijna altijd *html*, maar andere zijn nog mogelijk.

* ***kiezer - String***  - Optionele kiezers, gescheiden door punt. Algemene voorbeelden zijn *touch* voor het renderen van mobiele versies van een pagina.

* ***deep - Boolean***  - Optionele booleaanse eigenschap die bepaalt of onderliggende pagina&#39;s ook moeten worden opgenomen. De standaardwaarde is *true.*

* ***includeImages - Boolean***  - Optionele Booleaanse eigenschap die bepaalt of afbeeldingen moeten worden opgenomen. De standaardwaarde is *true*.

   * Standaard worden alleen afbeeldingscomponenten met een type basis/componenten/afbeelding als opname beschouwd.

* ***includeVideos - Boolean***  - De optionele booleaanse eigenschap bepaalt of video&#39;s moeten worden opgenomen. De standaardwaarde is *true*.

* ***includeModifiedPagesOnly - Boolean***  - Als de waarde false of weggelaten is, worden alle pagina&#39;s gerenderd en worden updates in de rendering gecontroleerd. Indien waar (true), is het basisverschil afhankelijk van wijzigingen in een pagina die als laatste is gewijzigd.
* ***+ rewrite (knooppunt)***
   ***- relativeParentPath - String***  - de weg om alle andere wegen met betrekking tot te schrijven.

>[!NOTE]
>
>Het middeltype van beeld en videocomponenten die door deze manager worden beïnvloed wordt geplaatst door de eigenschappen van *com.adobe.cq.mobile.platform.impl.contentsync.handler* te vormen.*MobilePagesUpdateHandler OSGi-service*.

**** mobilepageassetsHiermee worden app-pagina-elementen verzameld.

**** mobileContentListList the content of the ContentSync zip. Dit wordt gebruikt door de client-side js op het apparaat voor het uitvoeren van de eerste vereiste bestandskopie voor AEM apps.

Deze handler moet worden toegevoegd aan elke AEM ContentSync Config voor Apps.

* ***type - String - mobileContentListing***
* ***path***  - String - keep empty, must be present to be seen as a valid handler but path is afgeleid to be the current ContentSync cache. Deze waarde wordt genegeerd.
* ***targetRootDirectory* -**String - het voorvoegsel dat aan paden moet worden toegevoegd als doelhoofdmap voor inhoudsupdate voor deze handler.
* ***order - Long* -**Order for ContentSync om deze handler uit te voeren. Dit aantal zou hoger dan alle andere managers zoals 100 moeten worden geplaatst. Deze moet worden uitgevoerd na traditionele inhoudshandlers.

```xml
{
  "files": [
    "config.xml",
    "res/screens/ios/screen-ipad-portrait-2x.png",
    "res/screens/ios/screen-ipad-landscape.png",
    "res/screens/ios/screen-iphone-portrait-2x.png",
    "res/screens/ios/screen-iphone-landscape.png",
    "res/screens/ios/screen-iphone-portrait.png",
    "apps/weretail-app/components/splash-page/clientlibs.css",
    ...
    "pge-content-packages.json"
  ],
  "count": 382,
  "lastModified": 1422902754733
}
```

**** mobileContentPackage slistingHiermee wordt het AEM inhoudspakket in een bepaalde app weergegeven, evenals de serverURL waarnaar updateaanvragen moeten worden ingediend. Dit wordt gebruikt de cliënt zijjs op apparaat om inhoudsupdates te verzoeken

De manager zou op AEM App Shell ContentSync Config (knoop met pge-type=app-instance) moeten worden gebruikt

* ***type - String - mobileContentPackageSlisting***
* ***path **-**String*** - Path to an app shell (node with pge-type=app-instance).
* ***targetRootDirectory - String***  - het voorvoegsel dat aan paden moet worden toegevoegd als doelhoofdmap voor inhoudsupdate voor deze handler.
* ***order - Long* -**Order for ContentSync om deze handler uit te voeren. Dit aantal zou hoger dan alle andere managers zoals 100 moeten worden geplaatst. Deze moet worden uitgevoerd na traditionele inhoudshandlers.

>[!NOTE]
>
>Het volgende codeblok is geen exacte implementatie en moet worden gebruikt als een referentievoorbeeld:

```xml
{
  "content": [
    {
      "name": "en",
      "title": "We Retail Mobile App - English",
      "type": "CONTENT",
      "path": "/content/phonegap/weretail-outdoors/en",
      "updatePath": "/content/phonegap/weretail/en/jcr:content/pge-app/app-config"
    },
    {
      "name": "shell",
      "title": "We Retail Mobile App",
      "type": "INSTANCE",
      "path": "/content/phonegap/weretail-outdoors/shell",
      "updatePath": "/content/phonegap/weretail/shell/jcr:content/pge-app/app-config"
    }
  ],
  "serverURL": "http://localhost:4503/"
}
```

**** widgetconfigIncludes een bijgewerkte config.xml die om het even welke die veranderingen samenvoegt via het Centrum van het Bevel met verstrekte config.xml worden aangebracht. Als deze handler geen toepassingsdetails bevat die via de beheerinterface zijn gewijzigd, worden deze niet in de cache opgenomen.

Deze manager zou op een AEMApp Shell ContentSync config (knoop met pge-type=[app-instance]) moeten worden gebruikt.

* ***type - String* - **widgetconfig
* ***path **-**String*** - Path to any app shell child node (node with pge-type=[app-instance]).
* ***targetRootDirectory - String***  - het voorvoegsel dat aan paden moet worden toegevoegd als doelhoofdmap voor inhoudsupdate voor deze handler.
* ***targetIconDirectory - String***  - de map waarin de pictogrammen voor de app worden geplaatst

**** mobileADBMobileConfigJSONInomvat het ADBMobileConfig.JSON- dossier als de cloudservice van AMS werd gevormd.

Dit wordt tijdens het compileren gebruikt om de insteekmodule van AMS voor analytische steun te vormen.

De manager zou op AEM App Shell ContentSync Config (knoop met pge-type=app-instance) moeten worden gebruikt

* ***type - String***  - mobileADBMobileConfigJSON
* ***path - String***  - Path to an app shell (node met pge-type=app-instance of een RT die /libs/mobileapps/core/components/instance uitbreidt)
* ***targetRootDirectory - String***  - het voorvoegsel dat aan paden moet worden toegevoegd als doelhoofdmap voor inhoudsupdate voor deze handler

**Meldingen** configExtrats berichtconfiguraties die op apparaat worden vereist. De eigenschappen worden geëxtraheerd uit de respectievelijke cloudserviceconfiguratie van de pushservice die aan de app is gekoppeld.

Niet-AEM eigenschappen in het Jcr:content-knooppunt van de cloudservice worden geëxtraheerd en toegevoegd aan het JSON-bestand **pge-notifications-config.json** voor opname in de www-hoofdmap van de inhoud van de app.

AEM eigenschappen zijn de eigenschappen met naamruimte &quot;cq&quot;, &quot;sling&quot; of &quot;jcr&quot;. Andere eigenschappen kunnen worden uitgesloten via de eigenschap &quot;excludeProperties&quot; op het knooppunt voor het configureren van de inhoud.

* ***type - String***  - notificationsconfig
* ***excludeProperties - String[]***  - eigenschappen die moeten worden uitgesloten

**** contentSyncconfigcontentCollects inhoud van een bestaande ContentSync config.

* ***type - String***  - contentSyncconfigcontent
* ***path - String***  - Path to one of:

   * een andere ContentSync config
   * aan een Pakket van de Inhoud (zal zijn phonegap-exportTemplate bezit gebruiken om zijn config ContentSync te vinden)
   * aan een Mobiele Middel (app-inhoud zal onder dat middel worden gevonden en, als die inhoudspakketten een pge-includeInBuild bezit hebben dat waar is, phonegap-exportTemplate zal worden gebruikt om zijn config ContentSync te vinden)

* ***autoCreateFirstUpdateBeforeImport - Boolean***  - indien waar (true), maakt u een eerste  **** update in de target-config voordat u gaat importeren als deze nog niet bestaat

* ***autoFillBeforeImport - Boolean***  - indien waar (true), werk de doelconfiguratie bij of vul deze in voordat u gaat importeren
* ***configSuffix - String***  - een tekenreeks die wordt toegevoegd aan het pad dat wordt aangegeven in de eigenschap &quot;phonegap-exportTemplate&quot; van app-content. Hiermee kunt u verschillende exportsjablonen onderscheiden. Deze eigenschap kan bijvoorbeeld worden ingesteld op **&quot;-dev&quot;** om aan te geven dat *&quot;/../../../appconfig-dev&quot;* moet worden gebruikt (in tegenstelling tot *&quot;/../../../appconfig&quot;*).

**app-** assetsBevat alle elementen die aan een app-instantie zijn gekoppeld. Deze handler bevat alle elementen die zijn gevonden onder het opgegeven pad, samen met alle elementen waarnaar wordt verwezen door de eigenschap appAssetPath van een app-instantie.

* ***type - String***  - app-assets

* ***path **-**String*** - path to a location under an app instance where app assets.

**** mobileappoffersEr is een nieuwe handler voor contentsynchronisatie geïntroduceerd voor het gebruik van personalisatie om doelinhoud te renderen. De handler &#39;mobileappoffers&#39; weet hoe de gekoppelde doelaanbiedingen die door de auteur van de inhoud zijn gemaakt, moeten worden weergegeven. De handler mobileappoffers breidt de handler voor abstracte pagina&#39;s bijwerken uit, zodat veel eigenschappen vergelijkbaar zijn. De details van de handler mobileappoffers hebben de volgende eigenschappen.

De handler mobileappsoffers breidt de handler mobileappspages uit en voegt de volgende eigenschappen toe:

* ***locationRoot - String***  - specificeer de locatie van de mobiele toepassing
* ***includePageTypes - String*** - defaults to support cq/personalization/components/teaserpage and cq/personalization/components/offerproxy
* ***kiezer - Tekenreeks***  - moet op tandt worden ingesteld
* ***path - String*** - the path to the campagne&#39;s brand

**** mobileappconfigDe handler voor het synchroniseren van inhoud met mobileappconfig biedt een manier om JSON-gegevens te injecteren in de MobileAppsConfig.json. Als ontwikkelaars van een providerklasse een provider-klasse willen registreren, voegen zij hun MobileAppsInfoProvider-klasse toe aan de lijst met providers. De handler doorloopt de lijst met MobileAppsInfoProviders en stelt de provider in staat gegevens te injecteren in het resulterende JSON-bestand. De lijst met eigenschappen die deze handler ondersteunt, is:

* ***path **-**String*** - the path to an app instance node with pge-type=app-instance or a RT that extends /libs/mobileapps/core/components/instance
* ***providers - String*** `[]`  - de lijst met volledig gekwalificeerde MobileAppsInfoProviders
* ***targetRootDirectory - String***  - de map waarnaar het bestand MobileAppsConfig.json moet worden geschreven.
* **fileName - String**  - optional name of the file to write the JSON to, defaults to MobileAppsConfig.json

Het is mogelijk om veelvoudige mobileappconfig managers te hebben die elk met een unieke reeks leveranciers worden gevormd die aan verschillende JSON- dossiers schrijven.

### Handlers voor het synchroniseren van inhoud testen {#testing-content-sync-handlers}

**Stappen voor het controleren van de cache** IntegrityClear

* Cache wissen
* Uw handler uitvoeren (cache bijgewerkt)
* Voer uw manager opnieuw in (het geheime voorgeheugen zou niet moeten worden bijgewerkt)

**Stappen voor foutopsporing**

* Uw configuratie uitvoeren
* Uw configuratie of revisie exporteren op apparaat
* Als de rendering mislukt, controleert u op ontbrekende *stijlen/assets/libs* of controleert u op slechte paden naar *stijlen/assets/libs*

**** LoggingEnable ContentSync Debug registreren via configuraties OSGI logger op pakket  `com.day.cq.contentsync` Dit zal u toestaan om te volgen welke managers in werking stelden en of zij het geheime voorgeheugen bijwerkten en het bijwerken van het geheime voorgeheugen rapporteerden.

## Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwerpen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Klik [hier](/help/mobile/getting-started-aem-mobile.md) om aan de slag te gaan met de ontwikkeling van AEM Mobile-apps.

