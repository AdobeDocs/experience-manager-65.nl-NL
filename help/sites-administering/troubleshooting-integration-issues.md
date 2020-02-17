---
title: Problemen met integratie oplossen
seo-title: Problemen met integratie oplossen
description: Leer hoe u integratieproblemen kunt oplossen.
seo-description: Leer hoe u integratieproblemen kunt oplossen.
uuid: fe080e58-a855-4308-a611-f72eb47ba82d
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 422ee332-23ae-46bd-8394-a4e0915beaa2
translation-type: tm+mt
source-git-commit: 2fc35bfd93585a586cb1d4e3299261611db49ba6

---


# Problemen met integratie oplossen{#troubleshooting-integration-issues}

## Algemene tips voor probleemoplossing {#general-troubleshooting-tips}

### Geen JavaScript-fouten opsporen {#ensure-there-are-no-javascript-errors}

Controleer of er fouten worden weergegeven in de JavaScript-console van de browser. Onverwerkte fouten kunnen voorkomen dat de volgende code correct wordt uitgevoerd. Als er fouten optreden, controleert u welk script de fout veroorzaakt en op welk gebied. Het pad naar het script kan aangeven tot welke functionaliteit het script behoort.

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

Voor extra details over registreren, zie het [Registreren](/help/sites-deploying/configure-logging.md) en het [Werken met de Verslagen van de Controle en de pagina&#39;s van de Dossiers](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) van het Logboek.

## Problemen met analytische integratie {#analytics-integration-issues}

### De rapportimportmodule leidt tot een hoog CPU-/geheugengebruik {#the-report-importer-causes-high-cpu-memory-usage}

De rapportimportmodule veroorzaakt een hoog CPU-/geheugengebruik of veroorzaakt `OutOfMemoryError` uitzonderingen.

#### Oplossing {#solution}

U kunt het volgende proberen om dit probleem op te lossen:

* Zorg ervoor dat er geen grote hoeveelheid geregistreerde PollingImporters is (zie de sectie &quot;Sluiting duurt lang toe te schrijven aan PollingImporter&quot; hieronder).
* De Importeurs van het Rapport van de looppas op een bepaald tijdstip van de dag door CRON uitdrukkingen voor de `ManagedPollingImporter` configuraties in de console [te gebruiken](/help/sites-deploying/configuring-osgi.md)OSGi.

Lees het volgende artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html)voor meer informatie over het maken van services voor het importeren van aangepaste gegevens in AEM.

### Het afsluiten duurt lang vanwege de PollingImporter {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analyses zijn ontworpen met het oog op een overervingsmechanisme. Gewoonlijk schakelt u Analytics voor een site in door een verwijzing naar een analytische configuratie toe te voegen op het tabblad [Cloud Services](/help/sites-developing/extending-cloud-config.md) voor pagina-eigenschappen. De configuratie wordt dan automatisch overgeërfd aan alle subpagina&#39;s zonder de behoefte om het opnieuw te verwijzen tenzij een pagina een verschillende configuratie vereist. Wanneer u een verwijzing naar een site toevoegt, worden automatisch meerdere knooppunten (12 voor AEM 6.3 en eerder of 6 voor AEM 6.4 en hoger) gemaakt van het type `cq;PollConfig` dat PollingImporters instantieert die worden gebruikt om analysegegevens in AEM te importeren. Dientengevolge:

* Veel pagina&#39;s die verwijzen naar Analytics leiden tot een grote hoeveelheid PollingImporters.
* Bovendien, leidt het kopiëren en het kleven van pagina&#39;s met een verwijzing naar een configuratie van Analytics tot een verdubbeling van zijn PollingImporters.

#### Oplossing {#solution-1}

Ten eerste, zou het analyseren van [error.log](/help/sites-deploying/configure-logging.md) u wat inzicht in de hoeveelheid actieve of geregistreerde PollingImporters kunnen geven. Bijvoorbeeld:

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

Lees het volgende artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html)voor meer informatie over het maken van services voor het importeren van aangepaste gegevens in AEM.

## DTM-problemen (verouderd) {#dtm-legacy-issues}

### De DTM-scripttag wordt niet weergegeven in de paginabron {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

De [DTM](/help/sites-administering/dtm.md) -scripttag wordt niet correct op de pagina opgenomen, ook al wordt naar de configuratie verwezen op het tabblad [Cloud Services](/help/sites-developing/extending-cloud-config.md) voor pagina-eigenschappen.

#### Oplossing {#solution-2}

U kunt het volgende proberen om het probleem op te lossen:

* Zorg ervoor dat gecodeerde eigenschappen kunnen worden gedecodeerd (gebruik een andere automatisch gegenereerde sleutel voor elke AEM-instantie). Lees voor meer informatie ook [Encryption Support for Configuration Properties](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Publiceer de configuraties in `/etc/cloudservices/dynamictagmanagement`
* Controle ACLs op `/etc/cloudservices`. ACLs zou moeten zijn:

   * toestaan; jcr:read; webservice-support-servicelibfinder
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/default/&amp;ast;
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/default
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/public/&amp;ast;
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/public

Voor meer informatie over het beheren van ACLs, lees de pagina van het Beleid van de [Gebruiker en van de Veiligheid](/help/sites-administering/security.md#permissions-in-aem) .

## Problemen met doelintegratie {#target-integration-issues}

### Gerichte inhoud niet zichtbaar in de modus Voorbeeld bij gebruik van aangepaste paginacomponenten {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dit probleem treedt op omdat aangepaste paginacomponenten niet de juiste JSP- of clientbibliotheken bevatten die de DTM-integratie van het doel afhandelen.

#### Oplossing {#solution-3}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de aangepaste `headlibs.jsp` (indien van toepassing `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`) het volgende bevat:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Zorg ervoor dat de aangepaste `head.html` (indien aanwezig `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **geen** specifieke integratiekoppen bevatten, zoals in het onderstaande voorbeeld:

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

De `servicelibs.jsp` functie voegt de vereiste analytische JavaScript-objecten toe en laadt de aan de website gekoppelde cloudservice-bibliotheken. Voor de service Doel worden de bibliotheken geladen via de `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

De set bibliotheken die worden geladen, is afhankelijk van het type doelclientbibliotheek ( `mbox.js` of `at.js`) dat wordt gebruikt in de doelconfiguratie.

Als u DTM gebruikt om bibliotheken te leveren `mbox.js` of te `at.js` laden voordat de inhoud wordt gerenderd. Als u Tagbeheersystemen gebruikt die deze bibliotheken asynchroon laden, kunnen er problemen optreden bij het uitvoeren van de doelspecifieke JavaScript-code.

Lees voor meer informatie de pagina [Ontwikkelen voor gerichte inhoud](/help/sites-developing/target.md#understanding-the-target-component) .

### De fout &quot;Ontbrekende ID van de Reeks van het Rapport in initialisatie AppMeturement&quot;wordt getoond in de browser console {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dit probleem kan optreden wanneer Adobe Analytics met DTM op de website wordt geïmplementeerd en aangepaste code wordt gebruikt. De oorzaak gebruikt het object `s = new AppMeasurement()` om het `s` object te instantiëren.

#### Oplossing {#solution-4}

Gebruik `s_gi` in plaats van de `new AppMeasurement` instantiemethode. Bijvoorbeeld:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Er wordt willekeurig een standaardvoorstel weergegeven in plaats van de juiste aanbieding {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dit probleem kan meerdere oorzaken hebben:

* Het asynchroon laden van doelclientbibliotheken ( `mbox.js` of `at.js`) met behulp van systemen voor tagbeheer van derden kan willekeurig een doeleinde maken. De doelbibliotheken moeten synchroon in de paginakop worden geladen. Dit is altijd het geval wanneer de bibliotheken van AEM worden geleverd.

* Twee doelclientbibliotheken ( `at.js`) tegelijk laden, bijvoorbeeld één met DTM en één met de doelconfiguratie in AEM. Dit kan tot klassen voor de `adobe.target` definitie leiden als de `at.js` versies verschillen.

#### Oplossing {#solution-5}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de klantcode die de DTM-achtige bibliotheken laadt (die op hun beurt de doelbibliotheken laden) synchroon wordt uitgevoerd in de [paginakop](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* als de site zodanig is geconfigureerd dat DTM wordt gebruikt voor het leveren van Target-bibliotheken, zorgt u ervoor dat de optie **Clientlib die door DTM** wordt geleverd, wordt gecontroleerd in de [doelconfiguratie](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) voor de site.

### Een standaardaanbieding wordt altijd getoond in plaats van correcte aanbieding wanneer het gebruiken van AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Uit het vak is AEM 6.2 en 6.3 niet compatibel met AT.js versie 1.3.0+. Met AT.js versie 1.3.0 die parameterbevestiging voor zijn APIs introduceert, `adobe.target.applyOffer()` vereist een &quot;mbox&quot;parameter die niet door de `atjs-itegration.js` code wordt verstrekt.

#### Oplossing {#solution-6}

U lost dit probleem op door het `atjs-itegration.js` veld in het parameterobject `"mbox": mboxName` `adobe.target.applyOffer()` als volgt te bewerken en toe te voegen:

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

Dit probleem is waarschijnlijk een probleem met de configuratie-provisioning van de [A4T Analytics Cloud](/help/sites-administering/target-configuring.md) .

#### Oplossing {#solution-7}

U moet controleren of A4T correct is ingeschakeld voor uw Target-account door de volgende verificatieaanvraag naar AEM uit te voeren:

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

Als het antwoord de regel bevat, kunt u contact opnemen met de `a4tEnabled:false`klantenservice [](https://helpx.adobe.com/contact.html) van Adobe om uw account correct te kunnen instellen.

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

