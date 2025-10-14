---
title: Problemen met integratie oplossen
description: Leer hoe u problemen kunt oplossen bij de integratie met Adobe Experience Manager.
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 11b0023e-34bd-4dfe-8173-5466db9fbe34
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---

# Problemen met integratie oplossen{#troubleshooting-integration-issues}

## Algemene tips voor probleemoplossing {#general-troubleshooting-tips}

### Zorg ervoor dat er geen JavaScript-fouten zijn {#ensure-there-are-no-javascript-errors}

Controleer of de JavaScript-console van de browser fouten weergeeft. Onverwerkte fouten kunnen voorkomen dat de volgende code correct wordt uitgevoerd. Als er fouten optreden, controleert u welk script de fout veroorzaakt en op welk gebied. Het pad naar het script kan aangeven tot welke functionaliteit het script behoort.

### Aanmelden op componentniveau {#logging-on-component-level}

In sommige gevallen is het handig om aanvullende instructies op componentniveau toe te voegen. Aangezien de component wordt teruggegeven, kunt u een tijdelijke prijsverhoging toevoegen om veranderlijke waarden te tonen die u zouden kunnen helpen potentiële problemen identificeren. Bijvoorbeeld:

```
<%
log.info("myVariable={}", myVariable);
%>

<!--
<%= myJspVariable %>
-->

<!--
${ myHtlVariable }
-->
```

Voor extra details over het registreren, zie [&#x200B; het Registreren &#x200B;](/help/sites-deploying/configure-logging.md) en [&#x200B; het Werken met de Verslagen van de Controle en de pagina&#39;s van de Dossiers van het Logboek &#x200B;](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

## Problemen met analytische integratie {#analytics-integration-issues}

### De rapportimportmodule leidt tot een hoog CPU-/geheugengebruik {#the-report-importer-causes-high-cpu-memory-usage}

De rapportimportmodule veroorzaakt een hoog CPU-/geheugengebruik of veroorzaakt `OutOfMemoryError` -uitzonderingen.

#### Oplossing {#solution}

U kunt het volgende proberen om dit probleem op te lossen:

* Zorg ervoor dat er geen grote hoeveelheid geregistreerde PollingImporters is (zie de sectie &quot;Sluiting duurt lang toe te schrijven aan PollingImporter&quot; hieronder).
* De Importeurs van het Rapport van de looppas op een bepaald tijdstip van de dag door CRON uitdrukkingen voor de `ManagedPollingImporter` configuraties in de [&#x200B; console OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) te gebruiken.

Voor extra details over het creëren van de diensten van de douanegegevensimporteur in AEM, lees het volgende artikel [&#x200B; https://helpx.adobe.com/experience-manager/using/polling.html &#x200B;](https://helpx.adobe.com/experience-manager/using/polling.html).

### Het afsluiten duurt lang vanwege de PollingImporter {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analyses zijn ontworpen met het oog op een overervingsmechanisme. Gewoonlijk, laat u Analytics voor een plaats toe door een verwijzing naar een configuratie van Analytics binnen de pagina eigenschappen [&#x200B; Cloud Servicen &#x200B;](/help/sites-developing/extending-cloud-config.md) tabel toe te voegen. De configuratie wordt dan automatisch overgeërfd aan alle subpagina&#39;s zonder de behoefte om het opnieuw te verwijzen tenzij een pagina een verschillende configuratie vereist. Als u een verwijzing naar een site toevoegt, worden ook automatisch meerdere knooppunten gemaakt (12 voor AEM 6.3 en lager of 6 voor AEM 6.4)   en hoger) van het type `cq;PollConfig` dat PollingImporters instantieert die worden gebruikt om analysegegevens in AEM te importeren. Dientengevolge:

* Veel pagina&#39;s die verwijzen naar Analytics leiden tot een grote hoeveelheid PollingImporters.
* Bovendien, leidt het kopiëren en het kleven van pagina&#39;s met een verwijzing naar een configuratie van Analytics tot een verdubbeling van zijn PollingImporters.

#### Oplossing {#solution-1}

Ten eerste, zou het analyseren van [&#x200B; error.log &#x200B;](/help/sites-deploying/configure-logging.md) u wat inzicht over de hoeveelheid actieve of geregistreerde PollingImporters kunnen geven. Bijvoorbeeld:

```
# Count PollingImporter entries
$ sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\),interval.*/\1/p" error.log | wc -l
86415
# Count PollingImporter entries for last30days
$ sed -n "s/.*(aem-analytics-integration-last30Days).*target=\(.*\),interval.*/\1/p" error.log | wc -l
14531
# Count unique paths of PollingImporter registrations
sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\)\/jcr:content.*/\1/p" error.log | sort | uniq -c
28115
```

Ten tweede, zorg ervoor dat slechts top-pagina&#39;s (hoog in de hiërarchie) een analytische configuratie hebben van verwijzingen voorzien.

Voor extra details over het creëren van de diensten van de douanegegevensimporteur in AEM, lees het volgende artikel [&#x200B; https://helpx.adobe.com/experience-manager/using/polling.html &#x200B;](https://helpx.adobe.com/experience-manager/using/polling.html).

## DTM-problemen (verouderd) {#dtm-legacy-issues}

### De DTM-scripttag wordt niet weergegeven in de paginabron {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

De [&#x200B; DTM &#x200B;](/help/sites-administering/dtm.md) manuscriptmarkering is niet behoorlijk inbegrepen in de pagina alhoewel de configuratie in de pagina eigenschappen [&#x200B; Cloud Servicen &#x200B;](/help/sites-developing/extending-cloud-config.md) tabel van  van verwijzingen is voorzien.

#### Oplossing {#solution-2}

U kunt het volgende proberen om het probleem op te lossen:

* Zorg ervoor dat gecodeerde eigenschappen kunnen worden gedecodeerd (gebruik een andere automatisch gegenereerde sleutel voor elke AEM). Voor extra details, lees ook [&#x200B; Steun van de Encryptie voor de Eigenschappen van de Configuratie &#x200B;](/help/sites-administering/encryption-support-for-configuration-properties.md).
* De configuraties in `/etc/cloudservices/dynamictagmanagement` opnieuw publiceren
* Controleer ACLs op `/etc/cloudservices`. ACLs zou moeten zijn:

   * allow; jcr:read; webservice-support-servicelibfinder
   * allow; jcr:read; all; `rep:glob:`&ast;`/defaults/`&ast;
   * allow; jcr:read; all; `rep:glob:`&ast;`/defaults`
   * allow; jcr:read; all; `rep:glob:`&ast;`/public/`&ast;
   * allow; jcr:read; all; `rep:glob:`&ast;`/public`

Voor meer informatie over het beheren van ACLs, lees het [&#x200B; Beleid van de Gebruiker en de pagina van de Veiligheid &#x200B;](/help/sites-administering/security.md#permissions-in-aem).

## Problemen met doelintegratie {#target-integration-issues}

### Gerichte inhoud niet zichtbaar in de modus Voorbeeld bij gebruik van aangepaste pagina-componenten {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dit probleem treedt op omdat aangepaste paginacomponenten niet de juiste JSP- of clientbibliotheken bevatten die de DTM-integratie van het doel afhandelen.

#### Oplossing {#solution-3}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de aangepaste instructie `headlibs.jsp` (indien van toepassing `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp` ) het volgende bevat:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Zorg ervoor douane `head.html` (als om het even welk `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **niet** selectief specifieke integratiekoplampen zoals het hieronder voorbeeld omvat:

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

In `servicelibs.jsp` worden de vereiste JavaScript-analyseobjecten toegevoegd en worden de aan de website gekoppelde cloudservicebibliotheken geladen. Voor de service Doel worden de bibliotheken geladen via de map `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

De set bibliotheken die worden geladen, is afhankelijk van het type doelclientbibliotheek ( `mbox.js` of `at.js` ) dat in de doelconfiguratie wordt gebruikt.

Wanneer u DTM gebruikt voor levering `mbox.js` of `at.js` , moet u ervoor zorgen dat de bibliotheken zijn geladen voordat de inhoud wordt gerenderd. Het gebruik van Tag Management Systems dat deze bibliotheken asynchroon laadt, kan problemen veroorzaken bij het uitvoeren van de specifieke JavaScript-doelcode.

Voor extra informatie, lees het [&#x200B; Ontwikkelen voor de gerichte inhoud &#x200B;](/help/sites-developing/target.md#understanding-the-target-component) pagina.

### De fout &quot;Ontbrekende ID van de Reeks van het Rapport in de initialisering van het AppMeasurement&quot;wordt getoond in de browser console {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dit probleem kan optreden wanneer Adobe Analytics op de website wordt geïmplementeerd met DTM en aangepaste code gebruikt. De oorzaak gebruikt `s = new AppMeasurement()` om het `s` -object te instantiëren.

#### Oplossing {#solution-4}

Gebruik `s_gi` in plaats van de `new AppMeasurement` -instantiemethode. Bijvoorbeeld:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Er wordt willekeurig een standaardvoorstel weergegeven in plaats van de juiste aanbieding {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dit probleem kan meerdere oorzaken hebben:

* Het asynchroon laden van doelclientbibliotheken ( `mbox.js` of `at.js` ) met Tag Management Systems van derden kan willekeurig een doeleinde maken. De doelbibliotheken moeten synchroon in de paginakop worden geladen. Dit geldt altijd wanneer de bibliotheken worden geleverd vanuit AEM.

* Twee doelclientbibliotheken ( `at.js`) tegelijk laden, bijvoorbeeld één met DTM en één met de doelconfiguratie in AEM. Dit kan tot klassen voor de `adobe.target` definitie leiden als de `at.js` versies verschillen.

#### Oplossing {#solution-5}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor de klantencode die de DTM-als bibliotheken laadt (die beurtelings de bibliotheken van het Doel laden) synchroon in het [&#x200B; paginakop &#x200B;](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages) wordt uitgevoerd.
* als de plaats wordt gevormd om DTM te gebruiken om de bibliotheken van het Doel te leveren ervoor zorgen dat de **Clientlib die door DTM** optie wordt geleverd in de [&#x200B; configuratie van het Doel &#x200B;](https://helpx.adobe.com/nl/experience-manager/6-3/sites/administering/using/target-configuring.html) voor de plaats wordt gecontroleerd.

### Een standaardaanbieding wordt altijd getoond in plaats van correcte aanbieding wanneer het gebruiken van AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Uit het vak AEM 6.2 en 6.3 is niet compatibel met AT.js versie 1.3.0+. Met AT.js versie 1.3.0 die parameterbevestiging voor zijn APIs introduceert, `adobe.target.applyOffer()` vereist een &quot;mbox&quot;parameter die niet door de `atjs-itegration.js` code wordt verstrekt.

#### Oplossing {#solution-6}

U lost dit probleem op door `atjs-itegration.js` te bewerken en het veld `"mbox": mboxName` in het parameterobject voor `adobe.target.applyOffer()` als volgt toe te voegen:

```
adobe.target.getOffer({
    "mbox": mboxName,
    "params": params,
    "success": function (response) {
        adobe.target.applyOffer({
            "mbox": mboxName, //<--- ADDED PARAM
            "selector": "#" + mboxName,
            "offer": response
        })
    },
```

### De pagina van Doelstellingen &amp; van Montages toont niet de sectie van Rapporteringsbronnen {#the-goals-settings-page-does-not-show-the-reporting-sources-section}

Deze kwestie is zeer waarschijnlijk een [&#x200B; A4T Analytics Cloud 1&rbrace; leveringskwestie van de Configuratie van de Configuratie.](/help/sites-administering/target-configuring.md)

#### Oplossing {#solution-7}

U moet controleren of A4T correct is ingeschakeld voor uw Target-account door het volgende verificatieverzoek aan AEM uit te voeren:

```
http://localhost:4502/etc/cloudservices/testandtarget/<YOUR-CONFIG>/jcr:content.a4t.json

{
    "a4tEnabled": true,
    "sharedsecret": "SECRET",
    "proxyUrl": "/libs/cq/contentinsight/content/proxy.reportingservices.json",
    "active": "true",
    "pageName": "",
    "url": "https://api5.omniture.com/rs/0.5/",
    "username": "USER@DOMAIN"
}
```

Als de reactie de lijn `a4tEnabled:false` bevat, de Zorg van de Klant van de Adobe [&#128279;](https://helpx.adobe.com/nl/contact.html) om uw rekening te krijgen die correct wordt voorzien.

### Nuttige doel-API&#39;s {#helpful-target-apis}

Hieronder ziet u twee doel-API&#39;s die nuttig kunnen zijn bij het oplossen van problemen met betrekking tot het doel:

* Wint het eindpunt van het Doel voor een bepaalde cliëntcode terug

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json

{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* Profiel van een client ophalen

```
https://admin<N>.testandtarget.omniture.com/admin/rest/v1/clients/<CLIENT>?email=<EMAIL>&password=<PASSWORD>

Response for N=4, CLIENT-dayintegrationintern
{
    "clientCode": "dayintegrationintern",
    "companyName": "Day Integration - Internal",
    "omnitureCompanyId": "Day Integration Internal",
    "softTraxId": -1,
    "address1": "XYZ",
    "city": "San Francisco",
    "state": "ca",
    "zip": "94107",
    "country": "UNITED STATES",
    "locale": "de_DE",
    "timeZone": "Europe/Berlin",
    "phone": "XX-XX-XXXX",
    "serviceLevel": "Up to 100,000",
    "privileges": [
        "a4t",
        "hosts",
        "TnT-SC-integration",
        "mvt",
        "steps",
        "testing-campaigns",
        "view-snapshot",
        "on-site-editor",
        "optimizing-campaign",
        "third-party-id-support",
        "landing-page-campaigns",
        "segment",
        "rest-create-user",
        "advanced-targeting",
        "mobile-device-targeting",
        "beta",
        "geolocation"
    ]
}
```
