---
title: Ontwikkeling van proxy's
description: Een proxy is een AEM-instantie die proxyworkers gebruikt om taken te verwerken. Leer hoe u een AEM-proxy, ondersteunde bewerkingen, proxycomponenten en een aangepaste proxyworker kunt configureren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5cea9ed3be322cb8dedfbc6cb38abbdb72d0b7b7
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---


# Ontwikkeling van proxy&#39;s {#assets-proxy-development}

Adobe Experience Manager (AEM) Assets gebruikt een proxy om verwerking voor bepaalde taken te distribueren.

Een proxy is een specifieke (en soms aparte) AEM-instantie die proxyworkers gebruikt als processors die verantwoordelijk zijn voor het afhandelen van een taak en het maken van een resultaat. Een volmachtsarbeider kan voor een grote verscheidenheid van taken worden gebruikt. In het geval van een AEM Assets-proxy kan dit worden gebruikt voor het laden van elementen voor rendering binnen AEM Assets. De [IDS-proxyworker](indesign.md) gebruikt bijvoorbeeld een InDesign-server om bestanden te verwerken voor gebruik in AEM-middelen.

Wanneer de proxy een afzonderlijke AEM-instantie is, wordt de belasting van de AEM-ontwerpinstantie(s) verminderd. Standaard voert AEM Assets de taken voor middelenverwerking uit in dezelfde JVM (extern via Proxy) om de belasting op de AEM-ontwerpinstantie te verminderen.

## Proxy (HTTP-toegang) {#proxy-http-access}

Een volmacht is beschikbaar via de Server van HTTP wanneer het wordt gevormd om verwerkingstaken goed te keuren bij: `/libs/dam/cloud/proxy`. Deze servlet maakt een slingertaak van de geposte parameters. Deze wordt vervolgens toegevoegd aan de wachtrij van de proxytaak en verbonden met de desbetreffende proxyworker.

### Ondersteunde bewerkingen {#supported-operations}

* `job`

   **Eisen**: de parameter `jobevent` moet als geserialiseerde waardekaart worden geplaatst. Dit wordt gebruikt om een processor `Event` voor een baan te maken.

   **Resultaat**: Hiermee wordt een nieuwe taak toegevoegd. Als dit lukt, wordt een unieke taak-id geretourneerd.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Eisen**: de parameter `jobid` moet worden ingesteld.

   **Resultaat**: Retourneert een JSON-representatie van het resultaatknooppunt zoals gemaakt door de taakprocessor.

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

   **Eisen**: de parameter jobid moet worden ingesteld.

   **Resultaat**: Retourneert een resource die aan de opgegeven taak is gekoppeld.

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

   **Eisen**: de parameter jobid moet worden ingesteld.

   **Resultaten**: Hiermee wordt een taak verwijderd als deze wordt gevonden.

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### Proxy Worker {#proxy-worker}

Een proxyworker is een processor die verantwoordelijk is voor het afhandelen van een taak en het maken van een resultaat. Workers bevinden zich op de proxyinstantie en moeten [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementeren om te worden herkend als een proxyworker.

>[!NOTE]
>
>De worker moet [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementeren om te worden herkend als een proxyworker.

### Client-API {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html) is beschikbaar als dienst OSGi die methodes verstrekt om banen tot stand te brengen, banen te verwijderen en resultaten van die banen te krijgen. De standaardimplementatie van deze dienst (`JobServiceImpl`) gebruikt de cliënt van HTTP om met verre volmachtsservlet te communiceren.

Hieronder ziet u een voorbeeld van API-gebruik:

```java
@Reference
 JobService proxyJobService;

 // to create a new job
 final Hashtable props = new Hashtable();
 props.put("someproperty", "some value");
 props.put(JobUtil.PROPERTY_JOB_TOPIC, "myworker/job"); // this is an identifier of the worker
 final String jobId = proxyJobService.addJob(props, new Asset[]{asset});

 // to check status (returns JobService.STATUS_FINISHED or JobService.STATUS_INPROGRESS)
 int status = proxyJobService.getStatus(jobId)

 // to get the result
 final String jsonString = proxyJobService.getResult(jobId);

 // to remove job and cleanup
 proxyJobService.removeJob(jobId);
```

### Cloud Service Configurations {#cloud-service-configurations}

>[!NOTE]
>
>Referentiedocumentatie voor de proxy-API is beschikbaar onder [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html).

Zowel proxyconfiguraties als proxyarbeidersconfiguraties zijn beschikbaar via cloudservices die toegankelijk zijn via de AEM Assets **Tools** Console of onder `/etc/cloudservices/proxy`. Van elke proxyworker wordt verwacht dat deze een knooppunt toevoegt onder `/etc/cloudservices/proxy` voor arbeidersspecifieke configuratiedetails (bijvoorbeeld `/etc/cloudservices/proxy/workername`).

>[!NOTE]
>
>Zie de configuratie [van de Worker van de Volmacht van de Server](indesign.md#configuring-the-proxy-worker-for-indesign-server) InDesign en de configuratie [van de Diensten van de](../sites-developing/extending-cloud-config.md) Wolk van de Server voor meer informatie.

Hieronder ziet u een voorbeeld van API-gebruik:

```java
@Reference(policy = ReferencePolicy.STATIC)
 ProxyConfig proxyConfig;

 // to get proxy config
 Configuration cloudConfig = proxyConfig.getConfiguration();
 final String value = cloudConfig.get("someProperty", "defaultValue");

 // to get worker config
 Configuration cloudConfig = proxyConfig.getConfiguration("workername");
 final String value = cloudConfig.get("someProperty", "defaultValue");
```

### Een aangepaste proxyworker ontwikkelen {#developing-a-customized-proxy-worker}

De [IDS-proxyworker](indesign.md) is een voorbeeld van een AEM Assets-proxy-worker die al buiten het vak is opgegeven om de verwerking van InDesign-elementen uit te besteden.

U kunt ook uw eigen AEM Assets-proxy-worker ontwikkelen en configureren om een gespecialiseerde worker te maken die uw AEM Assets-verwerkingstaken verzendt en uitbesteedt.

Als u uw eigen aangepaste proxyworker wilt instellen, moet u:

* Instellen en implementeren (met gebruik van Gebeurtenis splitsen):

   * een aangepast taakonderwerp
   * een aangepaste taakgebeurtenishandler

* Gebruik vervolgens de JobService-API om:

   * Verzend uw aangepaste taak naar de proxy
   * uw taak beheren

* Als u de proxy uit een workflow wilt gebruiken, moet u een aangepaste externe stap implementeren met de WorkflowExternalProcess-API en de JobService-API.

In het volgende diagram en in de volgende stappen wordt gedetailleerd beschreven hoe u moet doorgaan:

![chlimage_1-249](assets/chlimage_1-249.png)

>[!NOTE]
>
>In de volgende stappen worden equivalenten van InDesign als referentievoorbeelden aangegeven.

1. Er wordt een [verkooptaak](https://sling.apache.org/site/eventing-and-jobs.html) gebruikt, dus u moet een taakonderwerp voor uw gebruiksgeval definiëren.

   Zie bijvoorbeeld `IDSJob.IDS_EXTENDSCRIPT_JOB` voor de IDS-proxyworker.

1. De externe stap wordt gebruikt om de gebeurtenis te activeren en dan te wachten tot dat wordt gebeëindigd; dit wordt gedaan door opiniepeilingen over de id . U moet uw eigen stap ontwikkelen om nieuwe functionaliteit uit te voeren.

   Voer een `WorkflowExternalProcess`uit, dan gebruik de API JobService en uw baanonderwerp om een baangebeurtenis voor te bereiden en het te verzenden naar JobService (een dienst OSGi).

   Zie `INDDMediaExtractProcess`.java voor de IDS-proxyworker als voorbeeld.

1. Voer een baanmanager voor uw onderwerp uit. Deze manager vereist ontwikkeling zodat het uw specifieke actie uitvoert en beschouwd wordt als om de arbeidersimplementatie.

   Zie bijvoorbeeld `IDSJobProcessor.java` voor de IDS-proxyworker.

1. Maak gebruik van `ProxyUtil.java` in dammen. Hierdoor kunt u taken naar werknemers verzenden met de proxy voor moederdieren.

>[!NOTE]
>
>Wat het AEM Assets-proxyframework niet buiten de box biedt, is het poolmechanisme.
>
>De integratie InDesign staat de toegang van een pool van indesign servers (IDSPool) toe. Deze pooling is specifiek voor de integratie van InDesign en maakt geen deel uit van het AEM Assets-proxyframework.

>[!NOTE]
>
>Synchronisatie van resultaten:
>
>Bij n instanties die dezelfde proxy gebruiken, blijft het verwerkingsresultaat bij de proxy. Het is de taak van de client (AEM-auteur) om het resultaat aan te vragen met dezelfde unieke taak-id als die aan de client is gegeven bij het maken van een taak. De proxy haalt de taak gewoon uit en zorgt ervoor dat het resultaat klaar is om te worden aangevraagd.
