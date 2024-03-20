---
title: Problemen met integratie oplossen
description: Leer hoe u problemen kunt oplossen bij de integratie met Adobe Experience Manager.
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 11b0023e-34bd-4dfe-8173-5466db9fbe34
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%

---

# Problemen met integratie oplossen{#troubleshooting-integration-issues}

## Algemene tips voor probleemoplossing {#general-troubleshooting-tips}

### Geen JavaScript-fouten opsporen {#ensure-there-are-no-javascript-errors}

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

Voor extra details over registreren, zie [Logboekregistratie](/help/sites-deploying/configure-logging.md) en [Werken met auditrecords en logbestanden](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) pagina&#39;s.

## Problemen met analytische integratie {#analytics-integration-issues}

### De rapportimportmodule leidt tot een hoog CPU-/geheugengebruik {#the-report-importer-causes-high-cpu-memory-usage}

De rapportimportmodule veroorzaakt een hoog CPU/geheugengebruik of veroorzaakt `OutOfMemoryError` uitzonderingen.

#### Oplossing {#solution}

U kunt het volgende proberen om dit probleem op te lossen:

* Zorg ervoor dat er geen grote hoeveelheid geregistreerde PollingImporters is (zie de sectie &quot;Sluiting duurt lang toe te schrijven aan PollingImporter&quot; hieronder).
* Voer Rapportimporteurs op een bepaald tijdstip van de dag uit met CRON-expressies voor de `ManagedPollingImporter` in de [OSGi-console](/help/sites-deploying/configuring-osgi.md).

Lees het volgende artikel voor meer informatie over het maken van aangepaste services voor het importeren van gegevens in AEM [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

### Het afsluiten duurt lang vanwege de PollingImporter {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analyses zijn ontworpen met het oog op een overervingsmechanisme. Gewoonlijk schakelt u Analytics in voor een site door een verwijzing naar een analytische configuratie toe te voegen binnen de pagina-eigenschappen [Cloud Servicen](/help/sites-developing/extending-cloud-config.md) tab. De configuratie wordt dan automatisch overgeërfd aan alle subpagina&#39;s zonder de behoefte om het opnieuw te verwijzen tenzij een pagina een verschillende configuratie vereist. Als u een verwijzing naar een site toevoegt, worden ook automatisch meerdere knooppunten van het type gemaakt (12 voor AEM 6.3 en lager of 6 voor AEM 6.4 en hoger) `cq;PollConfig` die PollingImporters concretiseert die worden gebruikt om de gegevens van Analytics in AEM in te voeren. Dientengevolge:

* Veel pagina&#39;s die verwijzen naar Analytics leiden tot een grote hoeveelheid PollingImporters.
* Bovendien, leidt het kopiëren en het kleven van pagina&#39;s met een verwijzing naar een configuratie van Analytics tot een verdubbeling van zijn PollingImporters.

#### Oplossing {#solution-1}

Ten eerste, de analyse van de [error.log](/help/sites-deploying/configure-logging.md) zou u wat inzicht over de hoeveelheid actieve of geregistreerde PollingImporters kunnen geven. Bijvoorbeeld:

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

Lees het volgende artikel voor meer informatie over het maken van aangepaste services voor het importeren van gegevens in AEM [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

## DTM-problemen (verouderd) {#dtm-legacy-issues}

### De DTM-scripttag wordt niet weergegeven in de paginabron {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

De [DTM](/help/sites-administering/dtm.md) scripttag wordt niet correct op de pagina opgenomen, ook al wordt naar de configuratie verwezen in de pagina-eigenschappen [Cloud Servicen](/help/sites-developing/extending-cloud-config.md) tab.

#### Oplossing {#solution-2}

U kunt het volgende proberen om het probleem op te lossen:

* Zorg ervoor dat gecodeerde eigenschappen kunnen worden gedecodeerd (gebruik een andere automatisch gegenereerde sleutel voor elke AEM). Lees voor meer informatie ook [Coderingsondersteuning voor configuratieeigenschappen](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Publiceer de configuraties die u vindt in `/etc/cloudservices/dynamictagmanagement`
* ACLs controleren op `/etc/cloudservices`. ACLs zou moeten zijn:

   * allow; jcr:read; webservice-support-servicelibfinder
   * allow; jcr:read; all; `rep:glob:`&amp;asteren;`/defaults/`&amp;asteren;
   * allow; jcr:read; all; `rep:glob:`&amp;asteren;`/defaults`
   * allow; jcr:read; all; `rep:glob:`&amp;asteren;`/public/`&amp;asteren;
   * allow; jcr:read; all; `rep:glob:`&amp;asteren;`/public`

Voor meer informatie over het beheren van ACLs, lees [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md#permissions-in-aem) pagina.

## Problemen met doelintegratie {#target-integration-issues}

### Gerichte inhoud niet zichtbaar in de modus Voorbeeld bij gebruik van aangepaste pagina-componenten {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dit probleem treedt op omdat aangepaste paginacomponenten niet de juiste JSP- of clientbibliotheken bevatten die de DTM-integratie van het doel afhandelen.

#### Oplossing {#solution-3}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de aangepaste `headlibs.jsp` (indien van toepassing `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`) bevat het volgende:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Zorg ervoor dat de aangepaste `head.html` (indien van toepassing `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **niet** specifieke integratiekoppen , zoals in het onderstaande voorbeeld , selectief opnemen :

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

De `servicelibs.jsp` voegt de vereiste analytische JavaScript-objecten toe en laadt de aan de website gekoppelde cloudservice-bibliotheken. Voor de service Doel worden de bibliotheken geladen via de `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

De set bibliotheken die worden geladen, is afhankelijk van het type doelclientbibliotheek ( `mbox.js` of `at.js`) gebruikt op de configuratie van het Doel.

Bij gebruik van DTM voor levering `mbox.js` of `at.js` Zorg ervoor dat de bibliotheken zijn geladen voordat de inhoud wordt gerenderd. Als u Tag Management Systems gebruikt die deze bibliotheken asynchroon laden, kan dit problemen veroorzaken bij het uitvoeren van de specifieke JavaScript-doelcode.

Lees voor meer informatie de [Ontwikkelen voor gerichte inhoud](/help/sites-developing/target.md#understanding-the-target-component) pagina.

### De fout &quot;Ontbrekende ID van de Reeks van het Rapport in de initialisering van het AppMeasurement&quot;wordt getoond in de browser console {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dit probleem kan optreden wanneer Adobe Analytics op de website wordt geïmplementeerd met DTM en aangepaste code gebruikt. De oorzaak is dat de `s = new AppMeasurement()` om het `s` object.

#### Oplossing {#solution-4}

Gebruiken `s_gi` in plaats van de `new AppMeasurement` instantiemethode. Bijvoorbeeld:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Er wordt willekeurig een standaardvoorstel weergegeven in plaats van de juiste aanbieding {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dit probleem kan meerdere oorzaken hebben:

* Doelclientbibliotheken laden ( `mbox.js` of `at.js`) asynchroon gebruik van Tag Management Systems van derden kan willekeurig afbreken. De doelbibliotheken moeten synchroon in de paginakop worden geladen. Dit geldt altijd wanneer de bibliotheken worden geleverd vanuit AEM.

* Twee doelclientbibliotheken laden ( `at.js`), bijvoorbeeld één met DTM en één met behulp van de doelconfiguratie in AEM. Dit kan tot klassen voor `adobe.target` als de `at.js` versies verschillen.

#### Oplossing {#solution-5}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de klantcode die de DTM-achtige bibliotheken laadt (die op hun beurt de doelbibliotheken laden) synchroon wordt uitgevoerd in de [paginakop](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* als de site is geconfigureerd voor gebruik van DTM om Target-bibliotheken te leveren, zorgt u ervoor dat de **Clientlib geleverd door DTM** Deze optie is ingeschakeld in het dialoogvenster [Doelconfiguratie](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) voor de site.

### Een standaardaanbieding wordt altijd getoond in plaats van correcte aanbieding wanneer het gebruiken van AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Uit het vak AEM 6.2 en 6.3 is niet compatibel met AT.js versie 1.3.0+. Met AT.js versie 1.3.0 die parameterbevestiging voor zijn APIs introduceert, `adobe.target.applyOffer()` vereist een &quot;mbox&quot;-parameter die niet door de `atjs-itegration.js` code.

#### Oplossing {#solution-6}

Bewerken van dit probleem oplossen `atjs-itegration.js` en voeg de `"mbox": mboxName` veld in het parameterobject voor `adobe.target.applyOffer()` als volgt:

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

Dit probleem is waarschijnlijk [A4T Analytics Cloud-configuratie](/help/sites-administering/target-configuring.md) inrichtingsprobleem.

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

Als het antwoord de lijn bevat `a4tEnabled:false`, tegenwerking [Klantenservice Adoben](https://helpx.adobe.com/contact.html) voor een correcte provisioning van uw account.

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
