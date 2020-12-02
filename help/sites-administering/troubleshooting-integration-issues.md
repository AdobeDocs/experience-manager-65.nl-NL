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
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 0%

---


# Problemen met integratie oplossen{#troubleshooting-integration-issues}

## Algemene tips voor het oplossen van problemen {#general-troubleshooting-tips}

### Zorg ervoor dat er geen JavaScript-fouten {#ensure-there-are-no-javascript-errors} optreden

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

Voor extra details over registreren, zie [Registreren](/help/sites-deploying/configure-logging.md) en [Werken met de Verslagen van de Controle en de pagina&#39;s van het Logboek](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

## Problemen met analytische integratie {#analytics-integration-issues}

### De rapportimportmodule veroorzaakt een hoog CPU/geheugengebruik {#the-report-importer-causes-high-cpu-memory-usage}

De rapportimportmodule veroorzaakt een hoog CPU/geheugengebruik of veroorzaakt `OutOfMemoryError` uitzonderingen.

#### Oplossing {#solution}

U kunt het volgende proberen om dit probleem op te lossen:

* Zorg ervoor dat er geen grote hoeveelheid geregistreerde PollingImporters is (zie de sectie &quot;Sluiting duurt lang toe te schrijven aan PollingImporter&quot; hieronder).
* Voer Rapportimporteurs op een bepaald tijdstip van de dag uit door CRON-expressies te gebruiken voor de configuraties `ManagedPollingImporter` in de [OSGi-console](/help/sites-deploying/configuring-osgi.md).

Lees het volgende artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html) voor meer informatie over het maken van aangepaste services voor het importeren van gegevens in AEM.

### Het afsluiten duurt lang vanwege de PollingImporter {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analyses zijn ontworpen met het oog op een overervingsmechanisme. Gewoonlijk schakelt u Analytics voor een site in door een verwijzing naar een analytische configuratie toe te voegen binnen de pagina-eigenschappen [Cloud Services](/help/sites-developing/extending-cloud-config.md) tab. De configuratie wordt dan automatisch overgeërfd aan alle subpagina&#39;s zonder de behoefte om het opnieuw te verwijzen tenzij een pagina een verschillende configuratie vereist. Als u een verwijzing naar een site toevoegt, worden ook automatisch meerdere knooppunten gemaakt (12 voor AEM 6.3 en lager of 6 voor AEM 6.4)   en hoger) van het type `cq;PollConfig` dat PollingImporters instantieert die worden gebruikt om analysegegevens in AEM in te voeren. Dientengevolge:

* Veel pagina&#39;s die verwijzen naar Analytics leiden tot een grote hoeveelheid PollingImporters.
* Bovendien, leidt het kopiëren en het kleven van pagina&#39;s met een verwijzing naar een configuratie van Analytics tot een verdubbeling van zijn PollingImporters.

#### Oplossing {#solution-1}

Ten eerste zou het analyseren van [error.log](/help/sites-deploying/configure-logging.md) u wat inzicht over de hoeveelheid actieve of geregistreerde PollingImporters kunnen geven. Bijvoorbeeld:

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

Lees het volgende artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html) voor meer informatie over het maken van aangepaste services voor het importeren van gegevens in AEM.

## DTM(Verouderd) problemen {#dtm-legacy-issues}

### De DTM-scripttag wordt niet weergegeven in de paginabron {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

De scripttag [DTM](/help/sites-administering/dtm.md) wordt niet correct opgenomen in de pagina, ook al wordt naar de configuratie verwezen in de pagina-eigenschappen [Cloud Services](/help/sites-developing/extending-cloud-config.md) tab.

#### Oplossing {#solution-2}

U kunt het volgende proberen om het probleem op te lossen:

* Zorg ervoor dat gecodeerde eigenschappen kunnen worden gedecodeerd (gebruik een andere automatisch gegenereerde sleutel voor elke AEM). Voor extra details, lees ook [Steun van de Encryptie voor de Eigenschappen van de Configuratie](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Publiceer de configuraties die worden gevonden in `/etc/cloudservices/dynamictagmanagement`
* Controleer ACLs op `/etc/cloudservices`. ACLs zou moeten zijn:

   * toestaan; jcr:read; webservice-support-servicelibfinder
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/default/&amp;ast;
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/default
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/public/&amp;ast;
   * toestaan; jcr:read; iedereen; rep:glob:&amp;ast;/public

Voor meer informatie over het beheren van ACLs, lees [Gebruikersbeleid en Veiligheid](/help/sites-administering/security.md#permissions-in-aem) pagina.

## Problemen met doelintegratie {#target-integration-issues}

### Gerichte inhoud niet zichtbaar in de modus Voorbeeld bij gebruik van aangepaste paginacomponenten {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dit probleem treedt op omdat aangepaste paginacomponenten niet de juiste JSP- of clientbibliotheken bevatten die de DTM-integratie van het doel afhandelen.

#### Oplossing {#solution-3}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de aangepaste `headlibs.jsp` (indien aanwezig `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`) het volgende bevat:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Zorg ervoor dat de aangepaste `head.html` (indien aanwezig `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **niet** selectief specifieke integratiekoplampen bevat, zoals in het onderstaande voorbeeld:

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

Met `servicelibs.jsp` voegt u de vereiste analytische JavaScript-objecten toe en laadt u de aan de website gekoppelde cloudservicebibliotheken. Voor de service Doel worden de bibliotheken geladen via de map `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

De set bibliotheken die worden geladen, is afhankelijk van het type doelclientbibliotheek ( `mbox.js` of `at.js`) dat wordt gebruikt in de doelconfiguratie.

Als u DTM gebruikt om `mbox.js` of `at.js` te leveren, moet u ervoor zorgen dat de bibliotheken zijn geladen voordat de inhoud wordt gerenderd. Als u Tagbeheersystemen gebruikt die deze bibliotheken asynchroon laden, kunnen er problemen optreden bij het uitvoeren van de doelspecifieke JavaScript-code.

Voor extra informatie, lees [Developing for Targeted Content](/help/sites-developing/target.md#understanding-the-target-component) pagina.

### De fout &quot;Ontbrekende ID van de Reeks van het Rapport in initialisatie AppMeasurement&quot;wordt getoond in de browser console {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dit probleem kan optreden wanneer Adobe Analytics op de website wordt geïmplementeerd met DTM en aangepaste code gebruikt. De oorzaak gebruikt `s = new AppMeasurement()` om het `s` voorwerp te concretiseren.

#### Oplossing {#solution-4}

Gebruik `s_gi` in plaats van de `new AppMeasurement` instantiemethode. Bijvoorbeeld:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Een standaardaanbieding wordt willekeurig weergegeven in plaats van de juiste aanbieding {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dit probleem kan meerdere oorzaken hebben:

* Het asynchroon laden van doelclientbibliotheken ( `mbox.js` of `at.js`) met behulp van externe tagbeheersystemen kan willekeurig een doeleinde maken. De doelbibliotheken moeten synchroon in de paginakop worden geladen. Dit geldt altijd wanneer de bibliotheken worden geleverd vanuit AEM.

* Twee doelclientbibliotheken ( `at.js`) tegelijk laden, bijvoorbeeld één met DTM en één met de doelconfiguratie in AEM. Dit kan klassen voor de `adobe.target` definitie veroorzaken als `at.js` versies verschillen.

#### Oplossing {#solution-5}

U kunt de volgende oplossingen uitproberen:

* Zorg ervoor dat de klantcode die de DTM-achtige bibliotheken laadt (die op hun beurt de doelbibliotheken laden) synchroon wordt uitgevoerd in de [paginakop](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* als de site is geconfigureerd om DTM te gebruiken voor het leveren van Target-bibliotheken, controleert u of de optie **Clientlib geleverd door DTM** is ingeschakeld in de [Doelconfiguratie](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) voor de site.

### Een standaardaanbieding wordt altijd getoond in plaats van correcte aanbieding wanneer het gebruiken van AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Uit het vak AEM 6.2 en 6.3 is niet compatibel met AT.js versie 1.3.0+. Met AT.js versie 1.3.0 die parameterbevestiging voor zijn APIs introduceert, `adobe.target.applyOffer()` vereist een &quot;mbox&quot;parameter die niet door `atjs-itegration.js` code wordt verstrekt.

#### Oplossing {#solution-6}

Als u dit probleem wilt oplossen, bewerkt u `atjs-itegration.js` en voegt u het veld `"mbox": mboxName` in het parameterobject voor `adobe.target.applyOffer()` als volgt toe:

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

### De pagina van Doelstellingen &amp; van Montages toont niet de sectie {#the-goals-settings-page-does-not-show-the-reporting-sources-section} van Rapporterende Bronnen

Dit probleem is waarschijnlijk een [A4T Analytics Cloud Configuration](/help/sites-administering/target-configuring.md)-inrichtingsprobleem.

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

Als de reactie de lijn `a4tEnabled:false` bevat, neem dan contact op met [Adobe Customer Care](https://helpx.adobe.com/contact.html) om uw account op de juiste wijze te installeren.

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

