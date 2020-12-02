---
title: '[!DNL Assets] proxyontwikkeling'
description: Een volmacht is een  [!DNL Experience Manager] instance that uses proxy workers to process jobs. Learn how to configure an [!DNL Experience Manager] volmacht, gesteunde verrichtingen, volmachtscomponenten, en hoe te om een worker van de douanevolmacht te ontwikkelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# [!DNL Assets] proxyontwikkeling  {#assets-proxy-development}

[!DNL Adobe Experience Manager Assets] gebruikt een volmacht om verwerking voor bepaalde taken te verdelen.

Een proxy is een specifieke (en soms aparte) Experience Manager-instantie die proxyworkers gebruikt als processors die een taak afhandelen en een resultaat maken. Een volmachtsarbeider kan voor een grote verscheidenheid van taken worden gebruikt. In het geval van een [!DNL Assets]-proxy kan dit worden gebruikt voor het laden van elementen voor rendering binnen elementen. De [IDS-proxyworker](indesign.md) gebruikt bijvoorbeeld een [!DNL Adobe InDesign]-server om bestanden te verwerken voor gebruik in Middelen.

Wanneer de proxy een aparte [!DNL Experience Manager]-instantie is, wordt de belasting van de ontwerpinstantie(s) van de Experience Manager verminderd. Standaard voert [!DNL Assets] de elementverwerkingstaken uit in dezelfde JVM (extern via Proxy) om de belasting op de Experience Manager-ontwerpinstantie te verminderen.

## Proxy (HTTP-toegang) {#proxy-http-access}

Een volmacht is beschikbaar via de Server van HTTP wanneer het wordt gevormd om verwerkingstaken goed te keuren bij: `/libs/dam/cloud/proxy`. Deze servlet maakt een slingertaak van de geposte parameters. Deze wordt vervolgens toegevoegd aan de wachtrij van de proxytaak en verbonden met de desbetreffende proxyworker.

### Ondersteunde bewerkingen {#supported-operations}

* `job`

   **Eisen**: de parameter  `jobevent` moet als geserialiseerde waardekaart worden geplaatst. Dit wordt gebruikt om een `Event` voor een baanbewerker te creëren.

   **Resultaat**: Hiermee wordt een nieuwe taak toegevoegd. Als dit lukt, wordt een unieke taak-id geretourneerd.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

   **Eisen**: de parameter  `jobid` moet worden ingesteld.

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

### Proxyworker {#proxy-worker}

Een proxyworker is een processor die verantwoordelijk is voor het afhandelen van een taak en het maken van een resultaat. Workers bevinden zich op de proxyinstantie en moeten [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementeren om te worden herkend als een proxyworker.

>[!NOTE]
>
>De worker moet [sling JobProcessor](https://sling.apache.org/site/eventing-and-jobs.html) implementeren om te worden herkend als een proxyworker.

### Client-API {#client-api}

[`JobService`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html) is beschikbaar als dienst OSGi die methodes verstrekt om banen tot stand te brengen, banen te verwijderen en resultaten van die banen te krijgen. De standaardimplementatie van deze dienst (`JobServiceImpl`) gebruikt de cliënt van HTTP om met de verre volmachtsservlet te communiceren.

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

### Configuraties van Cloud Servicen {#cloud-service-configurations}

>[!NOTE]
>
>Referentiedocumentatie voor de proxy-API is beschikbaar onder [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html).

Zowel proxyconfiguraties als proxyarbeidersconfiguraties zijn beschikbaar via cloudserviceconfiguraties die toegankelijk zijn via de [!DNL Assets] **Tools**-console of onder `/etc/cloudservices/proxy`. Van elke proxyworker wordt verwacht dat deze onder `/etc/cloudservices/proxy` een knooppunt toevoegt voor specifieke configuratiegegevens van de worker (bijvoorbeeld `/etc/cloudservices/proxy/workername`).

>[!NOTE]
>
>Zie [Configuratie van de Werknemer van de Volmacht van de InDesign Server](indesign.md#configuring-the-proxy-worker-for-indesign-server) en [Configuratie van Cloud Services](../sites-developing/extending-cloud-config.md) voor meer informatie.

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

### Een aangepaste proxyworker {#developing-a-customized-proxy-worker} ontwikkelen

De [IDS volmachtsarbeider](indesign.md) is een voorbeeld van een [!DNL Assets] volmachtsarbeider die reeds uit-van-de-doos wordt verstrekt om de verwerking van InDesign activa uit te besteden.

U kunt ook uw eigen [!DNL Assets] volmachtsarbeider ontwikkelen en vormen om een gespecialiseerde arbeider tot stand te brengen om uw [!DNL Assets] verwerkingstaken te verzenden en uit te besteden.

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
>In de volgende stappen worden equivalenten van InDesign aangegeven als referentievoorbeelden.

1. Er wordt een [Sling-taak](https://sling.apache.org/site/eventing-and-jobs.html) gebruikt, dus u moet een taakonderwerp definiëren voor uw gebruiksscenario.

   Zie `IDSJob.IDS_EXTENDSCRIPT_JOB` voor de IDS-proxyworker als voorbeeld.

1. De externe stap wordt gebruikt om de gebeurtenis te activeren en dan te wachten tot dat wordt gebeëindigd; dit wordt gedaan door opiniepeilingen over de id . U moet uw eigen stap ontwikkelen om nieuwe functionaliteit uit te voeren.

   Voer `WorkflowExternalProcess` uit, dan gebruik de API JobService en uw baanonderwerp om een baangebeurtenis voor te bereiden en het te verzenden naar JobService (een dienst OSGi).

   Zie `INDDMediaExtractProcess`.java voor de IDS-proxyworker als voorbeeld.

1. Voer een baanmanager voor uw onderwerp uit. Deze manager vereist ontwikkeling zodat het uw specifieke actie uitvoert en beschouwd wordt als om de arbeidersimplementatie.

   Zie `IDSJobProcessor.java` voor de IDS-proxyworker als voorbeeld.

1. Gebruik `ProxyUtil.java` in dam-commons. Hierdoor kunt u taken naar werknemers verzenden met de proxy voor moederdieren.

>[!NOTE]
>
>Wat het [!DNL Assets] volmachtskader niet uit-van-de-doos verstrekt is het poolmechanisme.
>
>Dankzij de integratie [!DNL InDesign] is toegang mogelijk tot een pool van [!DNL InDesign] servers (IDSPool). Deze pooling is specifiek voor [!DNL InDesign] integratie en maakt geen deel uit van het [!DNL Assets] volmachtskader.

>[!NOTE]
>
>Synchronisatie van resultaten:
>
>Bij n instanties die dezelfde proxy gebruiken, blijft het verwerkingsresultaat bij de proxy. Het is de taak van de client (Experience Manager Auteur) om het resultaat aan te vragen met dezelfde unieke taak-id als die aan de client is gegeven bij het maken van een taak. De proxy haalt de taak gewoon uit en zorgt ervoor dat het resultaat klaar is om te worden aangevraagd.
