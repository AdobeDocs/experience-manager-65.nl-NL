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
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 0%

---

# App-handlers buiten vak{#out-of-the-box-app-handlers}

{{ue-over-mobile}}

Zie de volgende richtlijnen voor het ontwikkelen van Content Sync Handlers:

* De managers moeten *com.day.cq.contentsync.handler.ContentUpdateHandler* uitvoeren (of direct of het uitbreiden van een klasse die doet)
* De managers kunnen *com.adobe.cq.mobile.platform.impl.contentsync.handler.AbstractSlingResourceUpdateHandler* uitbreiden
* Handler mag alleen true rapporteren als deze de cache ContentSync heeft bijgewerkt. Als u Waar onjuist rapporteert, AEM een update maken.
* De manager zou slechts het geheime voorgeheugen moeten bijwerken als de inhoud werkelijk veranderde. Schrijf niet naar de cache als een wit niet nodig is en vermijd het maken van een overbodige update.

## Buiten de handlers van de Doos {#out-of-the-box-handlers}

De volgende lijst bevat een lijst met apps die niet in de verpakking staan:

**mobileapppages** geeft app pagina&#39;s terug.

* ***type - Koord*** - mobileapppages
* ***weg - Koord*** - weg aan een pagina
* ***uitbreiding - Koord*** - Uitbreiding die in het verzoek zou moeten worden gebruikt. Voor pagina&#39;s is dit bijna altijd *html*, maar anderen zijn nog mogelijk.

* ***selecteur - Koord*** - Facultatieve selecteurs die door punt worden gescheiden. De gemeenschappelijke voorbeelden zijn *aanraking* voor het teruggeven van mobiele versies van een pagina.

* ***diep - Van Boole*** - Facultatief booleaans bezit dat bepaalt als de kindpagina&#39;s, eveneens zouden moeten worden omvat. De standaardwaarde is waar *.*

* ***includeImages - Van Boole*** - Facultatief booleaans bezit dat bepaalt als de beelden zouden moeten worden omvat. De standaardwaarde is waar **.

   * Standaard worden alleen afbeeldingscomponenten met een type basis/componenten/afbeelding als opname beschouwd.

* ***includeVideos - Van Boole*** - het facultatieve booleaanse bezit bepaalt als de video&#39;s zouden moeten worden omvat. De standaardwaarde is waar **.

* ***includeModifiedPagesOnly - Van Boole*** - als vals of weggelaten alle pagina&#39;s teruggeven en updates in het teruggeven controleren. Indien waar (true), is het basisverschil afhankelijk van wijzigingen in een pagina die als laatste is gewijzigd.
* ***+ rewrite (node)***
  ***- relativeParentPath - Koord*** - de weg om alle andere wegen met betrekking tot te schrijven.

>[!NOTE]
>
>Het middeltype van het beeld en de videocomponenten die door deze manager worden beïnvloed wordt geplaatst door de eigenschappen van *com.adobe.cq.mobile.platform.impl.contentsync.handler te vormen*.*MobilePagesUpdateHandler OSGi dienst*.

**mobilepageassets** verzamelt de activa van de toepassingspagina.

**mobilcontentList** maakt een lijst van de inhoud van ZIP ContentSync. Dit wordt gebruikt door de client-side js op het apparaat voor het uitvoeren van de eerste vereiste bestandskopie voor AEM apps.

Deze handler moet worden toegevoegd aan elke AEM ContentSync Config voor Apps.

* ***type - Koord - mobiele inhoudList***
* ***weg*** - Koord - houdt leeg, moet aanwezig zijn om als geldige manager worden gezien maar de weg wordt afgeleid om het huidige geheime voorgeheugen te zijn ContentSync. Deze waarde wordt genegeerd.
* ***targetRootDirectory* - &#x200B;** Koord - de prefix om aan wegen als doelwortel voor inhoudsupdate voor deze manager toe te voegen.
* ***orde - Lang* - &#x200B;** Orde voor ContentSync om deze manager uit te voeren. Dit aantal zou hoger dan alle andere managers zoals 100 moeten worden geplaatst. Deze moet worden uitgevoerd na traditionele inhoudshandlers.

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

**mobiel ContentPackageslisting** maakt een lijst van het AEM inhoudspakket in bepaalde app en serverURL om updateverzoeken aan te maken. Dit wordt gebruikt de cliënt zijjs op apparaat om inhoudsupdates te verzoeken

De manager zou op AEM App Shell ContentSync Config (knoop met pge-type=app-instance) moeten worden gebruikt

* ***type - Koord - mobiel ContentPackageslisting***
* ***weg &#x200B;**-**Koord*** - Weg aan app shell (knoop met pge-type=app-instantie).
* ***targetRootDirectory - Koord*** - de prefix om aan wegen als doelwortel voor inhoudsupdate voor deze manager toe te voegen.
* ***orde - Lang* - &#x200B;** Orde voor ContentSync om deze manager uit te voeren. Dit aantal zou hoger dan alle andere managers zoals 100 moeten worden geplaatst. Deze moet worden uitgevoerd na traditionele inhoudshandlers.

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

**widgetconfig** omvat bijgewerkte config.xml die om het even welke die uitgeeft via het Centrum van het Bevel met verstrekt config.xml samenvoegt. Als deze handler geen toepassingsdetails bevat die via de beheerinterface zijn gewijzigd, worden deze niet in de cache opgenomen.

Deze manager zou op een AEM moeten worden gebruikt App Shell ContentSync config (knoop met pge-type= [ app-instantie ]).

* **&#x200B; *type - Koord* - &#x200B;** widgetconfig
* ***weg &#x200B;**-**Koord*** - Weg aan om het even welke app shell kindknoop (knoop met pge-type= [ app-instantie ]).
* ***targetRootDirectory - Koord*** - de prefix om aan wegen als doelwortel voor inhoudsupdate voor deze manager toe te voegen.
* ***targetIconDirectory - Koord*** - de folder om de pictogrammen voor app te plaatsen

**mobileADBMobileConfigJSON** omvat het dossier ADBMobileConfig.JSON als de cloudservice van AMS werd gevormd.

Dit wordt tijdens het compileren gebruikt om de insteekmodule van AMS voor analytische steun te vormen.

De manager zou op AEM App Shell ContentSync Config (knoop met pge-type=app-instance) moeten worden gebruikt

* ***type - Koord*** - mobileADBMobileConfigJSON
* ***weg - Koord*** - Weg aan app shell (knoop met pge-type=app-instantie of RT die /libs/mobileapps/core/components/instantie uitbreidt)
* ***targetRootDirectory - Koord*** - de prefix om aan wegen als doelwortel voor inhoudsupdate voor deze manager toe te voegen

**meldingenconfig** trekt berichtconfiguraties uit die op apparaat worden vereist. De eigenschappen worden geëxtraheerd uit de respectievelijke cloudserviceconfiguratie van de pushservice die aan de app is gekoppeld.

De niet AEM eigenschappen in jcr van de clouddienst:inhoudsknoop worden gehaald en aan het {**JSON- dossier 0} pge-notifications-config.json voor opneming in de wortel van de toepassingsinhoud toegevoegd www.**

AEM eigenschappen zijn de eigenschappen met naamruimte &quot;cq&quot;, &quot;sling&quot; of &quot;jcr&quot;. Andere eigenschappen kunnen worden uitgesloten via de eigenschap &quot;excludeProperties&quot; op het knooppunt voor het configureren van de inhoud.

* ***type - Koord*** - berichtenconfig
* ***excludeProperties - Koord[]*** - uit te sluiten eigenschappen

**contentSyncconfigcontent** verzamelt inhoud van een bestaande config ContentSync.

* ***type - Koord*** - contentsyncconfigcontent
* ***weg - Koord*** - Weg aan één van:

   * een andere ContentSync config
   * aan een Pakket van de Inhoud (zal zijn phonegap-exportTemplate bezit gebruiken om zijn config ContentSync te vinden)
   * aan een Mobiele Middel (app-inhoud zal onder dat middel worden gevonden en, als die inhoudspakketten een pge-includeInBuild bezit hebben dat waar is, phonegap-exportTemplate wordt gebruikt om zijn config ContentSync te vinden)

* ***autoCreateFirstUpdateBeforeImport - Van Boole*** - als waar, creeer een aanvankelijke **update** in het doel config alvorens in te voeren als eens niet reeds bestaat

* ***autoFillBeforeImport - Van Boole*** - als waar, update/vul het doel config alvorens in te voeren
* ***configSuffix - Koord*** - een koord aan de weg toe te voegen die op het &quot;phonegap-exportTemplate&quot;bezit van app-inhoud wordt vermeld. Hiermee kunt u verschillende exportsjablonen onderscheiden. Bijvoorbeeld, kan dit bezit aan **&quot;- dev &quot;** worden geplaatst om erop te wijzen dat *&quot;/.../.../appconfig-dev&quot;* zou moeten worden gebruikt (in tegenstelling tot *&quot;/.../.../appconfig&quot;*).

**app-activa** omvat alle activa verbonden aan een toepassingsinstantie. Deze handler bevat alle elementen die zijn gevonden onder het opgegeven pad, samen met alle elementen waarnaar wordt verwezen door de eigenschap appAssetPath van een app-instantie.

* ***type - Koord*** - app-activa

* ***weg &#x200B;**-**Koord*** - weg aan een plaats onder een toepassingsinstantie waar app de activa worden opgeslagen

**mobileappoffers** Een nieuwe manager van de inhoudssynchronisatie is geïntroduceerd voor het gebruiksgeval van Personalization om gerichte inhoud terug te geven. De handler &#39;mobileappoffers&#39; weet hoe de gekoppelde doelaanbiedingen die door de auteur van de inhoud zijn gemaakt, moeten worden weergegeven. De handler mobileappoffers breidt de handler voor abstracte pagina&#39;s bijwerken uit, zodat veel eigenschappen vergelijkbaar zijn. De details van de handler mobileappoffers hebben de volgende eigenschappen.

De handler mobileappsoffers breidt de handler mobileappspages uit en voegt de volgende eigenschappen toe:

* ***locationRoot - Koord*** - specificeer de plaats van de mobiele toepassing
* ***includePageTypes - Koord*** - gebreken om cq/personalization/components/teaserpage en cq/personalization/components/offerproxy te steunen
* ***selecteur - Koord*** - zou aan tandt moeten worden geplaatst
* ***weg - Koord*** - de weg aan het merk van de campagne

**mobileappconfig** De mobileappconfig manager van de inhoudssynchronisatie verstrekt een manier om JSON- gegevens in MobileAppsConfig.json te injecteren. Als ontwikkelaars van een providerklasse een provider-klasse willen registreren, voegen zij hun MobileAppsInfoProvider-klasse toe aan de lijst met providers. De handler doorloopt de lijst met MobileAppsInfoProviders en stelt de provider in staat gegevens te injecteren in het resulterende JSON-bestand. De lijst met eigenschappen die door deze handler worden ondersteund, is:

* ***weg &#x200B;**-**Koord*** - de weg aan een knoop van de toepassingsinstantie met pge-type=app-instance of RT die /libs/mobileapps/core/components/instance uitbreidt
* ***leveranciers - Koord*** `[]` - de lijst van volledig - gekwalificeerde MobileAppsInfoProviders
* ***targetRootDirectory - Koord*** - de folder waar te om het MobileAppsConfig.json- dossier te schrijven aan.
* **fileName - Koord** - facultatieve naam van het dossier om JSON aan te schrijven, gebreken aan MobileAppsConfig.json

Het is mogelijk om veelvoudige mobileappconfig managers te hebben die elk met een unieke reeks leveranciers worden gevormd die aan verschillende JSON- dossiers schrijven.

### Handlers voor het synchroniseren van inhoud testen {#testing-content-sync-handlers}

**Stappen voor het Controle van Integriteit** Duidelijk geheim voorgeheugen

* Cache wissen
* Uw handler uitvoeren (cache bijgewerkt)
* Voer uw manager opnieuw in (het geheime voorgeheugen zou niet moeten worden bijgewerkt)

**Stappen voor het Zuiveren**

* Uw configuratie uitvoeren
* Uw configuratie of revisie exporteren op apparaat
* Als het teruggeven ontbreekt controle voor ontbrekende *stijlen/activa/bibliotheken* of controle voor slechte wegen aan *stijlen/activa/bibliotheken*

**Logging** laat ContentSync toe Debug registreren via configuraties OSGI logger op pakket `com.day.cq.contentsync` Dit zal u laten volgen welke managers in werking stelden en of zij het geheime voorgeheugen bijwerkten en het bijwerken van het geheime voorgeheugen rapporteerden.

## Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwerpen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)

>[!NOTE]
>
>Om met de toepassingsontwikkeling van AEM Mobile te beginnen, klik [&#x200B; hier &#x200B;](/help/mobile/getting-started-aem-mobile.md).
