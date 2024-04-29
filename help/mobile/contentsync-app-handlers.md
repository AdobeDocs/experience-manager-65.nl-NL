---
title: App-handlers buiten vak
description: Volg deze pagina voor meer informatie over de handlers voor Adobe PhoneGap Enterprise met AEM.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: e2ddf5d1-0f5b-4f3b-9666-0f388915730e
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1408'
ht-degree: 0%

---

# App-handlers buiten vak{#out-of-the-box-app-handlers}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Zie de volgende richtlijnen voor het ontwikkelen van Content Sync Handlers:

* Handlers moeten implementeren *com.day.cq.contentsync.handler.ContentUpdateHandler* (rechtstreeks of door een klasse uit te breiden die dit doet)
* Handlers kunnen *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler*
* Handler mag alleen true rapporteren als deze de cache ContentSync heeft bijgewerkt. Als u Waar onjuist rapporteert, AEM een update maken.
* De manager zou slechts het geheime voorgeheugen moeten bijwerken als de inhoud werkelijk veranderde. Schrijf niet naar de cache als een wit niet nodig is en vermijd het maken van een overbodige update.

## Buiten de handlers van de Doos {#out-of-the-box-handlers}

De volgende lijst bevat een lijst met apps die niet in de verpakking staan:

**mobiele appages** Hiermee worden app-pagina&#39;s weergegeven.

* ***type - String*** - mobiele appages
* ***path - String*** - pad naar een pagina
* ***extension - String*** - Uitbreiding die in het verzoek moet worden gebruikt. Voor pagina&#39;s is dit bijna altijd *html*, maar andere zijn nog mogelijk.

* ***selector - String*** - Optionele kiezers, gescheiden door punt. Algemene voorbeelden zijn *tikken* voor het weergeven van mobiele versies van een pagina.

* ***deep - Boolean*** - Optionele booleaanse eigenschap die bepaalt of onderliggende pagina&#39;s ook moeten worden opgenomen. De standaardwaarde is *true.*

* ***includeImages - Boolean*** - Optionele booleaanse eigenschap die bepaalt of afbeeldingen moeten worden opgenomen. De standaardwaarde is *true*.

   * Standaard worden alleen afbeeldingscomponenten met een type basis/componenten/afbeelding als opname beschouwd.

* ***includeVideos - Boolean*** - Optionele booleaanse eigenschappen bepalen of video&#39;s moeten worden opgenomen. De standaardwaarde is *true*.

* ***includeModifiedPagesOnly - Boolean*** - Als de waarde false of weggelaten is, worden alle pagina&#39;s gerenderd en worden updates voor de rendering gecontroleerd. Indien waar (true), is het basisverschil afhankelijk van wijzigingen in een pagina die als laatste is gewijzigd.
* ***+ rewrite (knooppunt)***
  ***- relativeParentPath - String*** - het pad waarnaar alle andere paden moeten worden geschreven.

>[!NOTE]
>
>Het middeltype van het beeld en de videocomponenten die door deze manager worden beïnvloed wordt geplaatst door de eigenschappen van te vormen *com.adobe.cq.mobile.platform.impl.contentsync.handler*.*MobilePagesUpdateHandler OSGi-service*.

**mobilepageassets** Verzamelt app page-elementen.

**mobiele inhoud** Hiermee wordt de inhoud van het ZIP-bestand voor ContentSync weergegeven. Dit wordt gebruikt door de client-side js op het apparaat voor het uitvoeren van de eerste vereiste bestandskopie voor AEM apps.

Deze handler moet worden toegevoegd aan elke AEM ContentSync Config voor Apps.

* ***type - String - mobileContentList***
* ***pad*** - Tekenreeks - leeg houden, moet aanwezig zijn om te worden beschouwd als een geldige handler, maar het pad wordt geïnterpreteerd als de huidige cache van ContentSync. Deze waarde wordt genegeerd.
* ***targetRootDirectory* -**Tekenreeks - het voorvoegsel dat aan paden moet worden toegevoegd als doelbasis voor de update van de inhoud voor deze handler.
* ***bestelling - lang* -**Order for ContentSync om deze handler uit te voeren. Dit aantal zou hoger dan alle andere managers zoals 100 moeten worden geplaatst. Deze moet worden uitgevoerd na traditionele inhoudshandlers.

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

**mobileContentpackageslisting** Hiermee geeft u het AEM inhoudspakket in een bepaalde app en de serverURL weer waarnaar updateaanvragen moeten worden ingediend. Dit wordt gebruikt de cliënt zijjs op apparaat om inhoudsupdates te verzoeken

De manager zou op AEM App Shell ContentSync Config (knoop met pge-type=app-instance) moeten worden gebruikt

* ***type - String - mobileContentPackageSlisting***
* ***pad **-**String*** - Pad naar een app-shell (knooppunt met paginatype=app-instance).
* ***targetRootDirectory - String*** - Het voorvoegsel dat aan paden moet worden toegevoegd als doelbasis voor de update van de inhoud voor deze handler.
* ***bestelling - lang* -**Opdracht voor ContentSync om deze handler uit te voeren. Dit aantal zou hoger dan alle andere managers zoals 100 moeten worden geplaatst. Deze moet worden uitgevoerd na traditionele inhoudshandlers.

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

**widgetconfig** Omvat bijgewerkte config.xml die om het even welke die veranderingen samenvoegt via het Centrum van het Bevel met verstrekte config.xml worden aangebracht. Als deze handler geen toepassingsdetails bevat die via de beheerinterface zijn gewijzigd, worden deze niet in de cache opgenomen.

Deze manager zou op een AEM moeten worden gebruikt App Shell ContentSync config (knoop met pge-type=[app-instance]).

* ***type - String* - **widgetconfig
* ***pad **-**String*** - Pad naar elk onderliggend knooppunt van de app-shell (knooppunt met paginatype=[app-instance]).
* ***targetRootDirectory - String*** - Het voorvoegsel dat aan paden moet worden toegevoegd als doelbasis voor de update van de inhoud voor deze handler.
* ***targetIconDirectory - String*** - de map waarin de pictogrammen voor de app worden geplaatst

**mobileADBMobileConfigJSON** Neem het bestand ADBMobileConfig.JSON op als de AMS-cloudservice is geconfigureerd.

Dit wordt tijdens het compileren gebruikt om de insteekmodule van AMS voor analytische steun te vormen.

De manager zou op AEM App Shell ContentSync Config (knoop met pge-type=app-instance) moeten worden gebruikt

* ***type - String*** - mobileADBMobileConfigJSON
* ***path - String*** - Pad naar een app-shell (knooppunt met paginatype=app-instance of RT dat /libs/mobileapps/core/components/instance uitbreidt)
* ***targetRootDirectory - String*** - het voorvoegsel dat aan paden moet worden toegevoegd als doelbasis voor het bijwerken van de inhoud voor deze handler

**meldingenconfig** Extraheert berichtconfiguraties die op het apparaat zijn vereist. De eigenschappen worden geëxtraheerd uit de respectievelijke cloudserviceconfiguratie van de pushservice die aan de app is gekoppeld.

Niet-AEM eigenschappen in het Jcr:content-knooppunt van de cloudservice worden geëxtraheerd en toegevoegd aan het **pge-notifications-config.json** JSON-bestand voor opname in de www-hoofdmap van de inhoud van de app.

AEM eigenschappen zijn de eigenschappen met naamruimte &quot;cq&quot;, &quot;sling&quot; of &quot;jcr&quot;. Andere eigenschappen kunnen worden uitgesloten via de eigenschap &quot;excludeProperties&quot; op het knooppunt voor het configureren van de inhoud.

* ***type - String*** - meldingen, config
* ***excludeProperties - String[]*** - eigenschappen die moeten worden uitgesloten

**contentSyncconfigcontent** Verzamelt inhoud van een bestaande config ContentSync.

* ***type - String*** - contentSyncconfigcontent
* ***path - String*** - Pad naar een van de volgende:

   * een andere ContentSync config
   * aan een Pakket van de Inhoud (zal zijn phonegap-exportTemplate bezit gebruiken om zijn config ContentSync te vinden)
   * aan een Mobiele Middel (app-inhoud zal onder dat middel worden gevonden en, als die inhoudspakketten een pge-includeInBuild bezit hebben dat waar is, phonegap-exportTemplate wordt gebruikt om zijn config ContentSync te vinden)

* ***autoCreateFirstUpdateBeforeImport - Boolean*** - indien waar (true), een eerste **update** in het doel config alvorens in te voeren als eens niet reeds bestaat

* ***autoFillBeforeImport - Boolean*** - Indien waar (true), werkt u de doelconfiguratie bij of vult u deze voordat u gaat importeren
* ***configSuffix - String*** - een tekenreeks die moet worden toegevoegd aan het pad dat wordt aangegeven met de eigenschap &quot;phonegap-exportTemplate&quot; van app-content. Hiermee kunt u verschillende exportsjablonen onderscheiden. Deze eigenschap kan bijvoorbeeld worden ingesteld op **&quot;-dev&quot;** aangeven dat *&quot;/../../../appconfig-dev&quot;* dient te worden gebruikt (in tegenstelling tot *&quot;/../../../appconfig&quot;*).

**app-assets** Bevat alle elementen die aan een app-instantie zijn gekoppeld. Deze handler bevat alle elementen die zijn gevonden onder het opgegeven pad, samen met alle elementen waarnaar wordt verwezen door de eigenschap appAssetPath van een app-instantie.

* ***type - String*** - app-assets

* ***pad **-**String*** - pad naar een locatie onder een app-instantie waar app-middelen zijn opgeslagen

**mobileappoffers** Er is een nieuwe handler voor inhoudssynchronisatie geïntroduceerd voor het gebruik van Aanpassing voor het renderen van doelinhoud. De handler &#39;mobileappoffers&#39; weet hoe de gekoppelde doelaanbiedingen die door de auteur van de inhoud zijn gemaakt, moeten worden weergegeven. De handler mobileappoffers breidt de handler voor abstracte pagina&#39;s bijwerken uit, zodat veel eigenschappen vergelijkbaar zijn. De details van de handler mobileappoffers hebben de volgende eigenschappen.

De handler mobileappsoffers breidt de handler mobileappspages uit en voegt de volgende eigenschappen toe:

* ***locationRoot - String*** - geef de locatie van de mobiele toepassing op
* ***includePageTypes - String*** - standaardinstellingen ter ondersteuning van cq/personalization/components/teaserpage en cq/personalization/components/offerproxy
* ***selector - String*** - moet worden ingesteld op tandaard
* ***path - String***- de weg naar het merk van de campagne

**mobileappconfig** De handler voor het synchroniseren van inhoud met mobileappconfig biedt een manier om JSON-gegevens te injecteren in de MobileAppsConfig.json. Als ontwikkelaars van een providerklasse een provider-klasse willen registreren, voegen zij hun MobileAppsInfoProvider-klasse toe aan de lijst met providers. De handler doorloopt de lijst met MobileAppsInfoProviders en stelt de provider in staat gegevens te injecteren in het resulterende JSON-bestand. De lijst met eigenschappen die door deze handler worden ondersteund, is:

* ***pad **-**String*** - het pad naar een appinstantie-knooppunt met pge-type=app-instance of een RT die /libs/mobileapps/core/components/instance uitbreidt
* ***providers - String*** `[]` - de lijst met volledig gekwalificeerde MobileAppsInfoProviders
* ***targetRootDirectory - String*** - de map waarnaar het bestand MobileAppsConfig.json moet worden geschreven.
* **fileName - String** - optionele naam van het bestand waarnaar de JSON moet worden geschreven, standaard ingesteld op MobileAppsConfig.json

Het is mogelijk om veelvoudige mobileappconfig managers te hebben die elk met een unieke reeks leveranciers worden gevormd die aan verschillende JSON- dossiers schrijven.

### Handlers voor het synchroniseren van inhoud testen {#testing-content-sync-handlers}

**Stappen voor het controleren van de integriteit** Cache wissen

* Cache wissen
* Uw handler uitvoeren (cache bijgewerkt)
* Voer uw manager opnieuw in (het geheime voorgeheugen zou niet moeten worden bijgewerkt)

**Stappen voor foutopsporing**

* Uw configuratie uitvoeren
* Uw configuratie of revisie exporteren op apparaat
* Als rendering mislukt, controleert u op ontbrekende items *stijlen/middelen/bibliotheken* of controleer op ongeldige paden naar *stijlen/middelen/bibliotheken*

**Logboekregistratie** Enable ContentSync Debug Logboekregistratie via OSGI logger configuraties on package `com.day.cq.contentsync` Dit zal u laten volgen welke managers in werking stelden en of zij het geheime voorgeheugen bijwerkten en het bijwerken van het geheime voorgeheugen rapporteerden.

## Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwerpen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Om aan de slag te gaan met de ontwikkeling van AEM Mobile-apps klikt u op [hier](/help/mobile/getting-started-aem-mobile.md).
