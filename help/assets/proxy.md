---
title: '[!DNL Assets] proxyontwikkeling'
description: Een volmacht is een  [!DNL Experience Manager]  instantie die volmachtsarbeiders gebruikt om banen te verwerken. Leer hoe te om een  [!DNL Experience Manager]  volmacht, gesteunde verrichtingen, volmachtscomponenten te vormen, en hoe te om een worker van de douanevolmacht te ontwikkelen.
contentOwner: AG
role: Admin, Architect
exl-id: 42fff236-b4e1-4f42-922c-97da32a933cf
solution: Experience Manager, Experience Manager Assets
feature: Proxy Workers
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# [!DNL Assets] proxyontwikkeling {#assets-proxy-development}

[!DNL Adobe Experience Manager Assets] gebruikt een proxy om verwerking voor bepaalde taken te distribueren.

Een proxy is een specifieke (en soms aparte) Experience Manager-instantie die proxyworkers gebruikt als processoren die een taak afhandelen en een resultaat maken. Een volmachtsarbeider kan voor een grote verscheidenheid van taken worden gebruikt. Als er een [!DNL Assets] -proxy is, kan dit worden gebruikt voor het laden van elementen voor rendering binnen Assets. Bijvoorbeeld, gebruikt de [ IDS volmachtsarbeider ](indesign.md) een [!DNL Adobe InDesign] Server om dossiers voor gebruik in Assets te verwerken.

Wanneer de proxy een aparte [!DNL Experience Manager] -instantie is, wordt de belasting van de [!DNL Experience Manager] -ontwerpinstantie(s) verminderd. Standaard voert [!DNL Assets] de elementverwerkingstaken uit in dezelfde JVM (extern via Proxy) om de belasting van de [!DNL Experience Manager] -ontwerpinstantie te verminderen.

## Proxy (HTTP-toegang) {#proxy-http-access}

Een proxy is beschikbaar via de HTTP-server wanneer deze is geconfigureerd voor het accepteren van verwerkingstaken bij: `/libs/dam/cloud/proxy` . Deze servlet maakt een slingertaak van de geposte parameters. Deze wordt vervolgens toegevoegd aan de wachtrij van de proxytaak en verbonden met de desbetreffende proxyworker.

### Ondersteunde bewerkingen {#supported-operations}

* `job`

  **Vereisten**: de parameter `jobevent` moet als geserialiseerde waardekaart worden geplaatst. Hiermee wordt een `Event` voor een taakprocessor gemaakt.

  **Resultaat**: Voegt een nieuwe baan toe. Als dit lukt, wordt een unieke taak-id geretourneerd.

```shell
curl -u admin:admin -F":operation=job" -F"someproperty=xxxxxxxxxxxx"
    -F"jobevent=serialized value map" http://localhost:4502/libs/dam/cloud/proxy
```

* `result`

  **Vereisten**: de parameter `jobid` moet worden geplaatst.

  **Resultaat**: Keert een vertegenwoordiging JSON van de resultaatKnoop terug zoals die door de baanbewerker wordt gecreeerd.

```shell
curl -u admin:admin -F":operation=result" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502   /libs/dam/cloud/proxy
```

* `resource`

  **Vereisten**: De parameterjobid moet worden geplaatst.

  **Resultaat**: Keert een middel verbonden aan de bepaalde baan terug.

```shell
curl -u admin:admin -F":operation=resource" -F"jobid=xxxxxxxxxxxx"
    -F"resourcePath=something.pdf" http://localhost:4502/libs/dam/cloud/proxy
```

* `remove`

  **Vereisten**: De parameterjobid moet worden geplaatst.

  **Resultaten**: Verwijdert een baan als gevonden.

```shell
curl -u admin:admin -F":operation=remove" -F"jobid=xxxxxxxxxxxx"
    http://localhost:4502/libs/dam/cloud/proxy
```

### Proxy Worker {#proxy-worker}

Een proxyworker is een processor die verantwoordelijk is voor het afhandelen van een taak en het maken van een resultaat. De arbeiders verblijven op de volmachtsinstantie en moeten [ uitstellen JobProcessor ](https://sling.apache.org/site/eventing-and-jobs.html) uitvoeren om als volmachtsarbeider worden erkend.

>[!NOTE]
>
>De worker moet [ uitputtend JobProcessor ](https://sling.apache.org/site/eventing-and-jobs.html) uitvoeren om als volmachtsarbeider te worden erkend.

### Client-API {#client-api}

[`JobService` ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html) is beschikbaar als dienst OSGi die methodes verstrekt om banen tot stand te brengen, banen te verwijderen en resultaten van die banen te krijgen. De standaardimplementatie van deze dienst (`JobServiceImpl`) gebruikt de cliënt van HTTP om met verre volmachtsservlet te communiceren.

Hieronder ziet u een voorbeeld van API-gebruik:

```java
@Reference
 JobService proxyJobService;

 // to create a job
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

### Cloud Service configuraties {#cloud-service-configurations}

<!-- TBD: Cannot find com.day.cq.dam.api.proxy at https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html which were generated in May 2020. Hiding this broken link for now.
>[!NOTE]
>
>Reference documentation for the proxy API is available under [`com.day.cq.dam.api.proxy`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/proxy/package-summary.html).
-->

Zowel zijn de volmacht als de configuraties van de volmachtsarbeider beschikbaar via de configuraties van de wolkendiensten zoals toegankelijk van de [!DNL Assets] **console van Hulpmiddelen** of onder `/etc/cloudservices/proxy`. Elke proxyworker moet een knooppunt onder `/etc/cloudservices/proxy` toevoegen voor arbeidersspecifieke configuratiegegevens (bijvoorbeeld `/etc/cloudservices/proxy/workername` ).

>[!NOTE]
>
>Zie {de configuratie van de Werknemer van de Volmacht van 0} InDesign Server [&#128279;](indesign.md#configuring-the-proxy-worker-for-indesign-server) en [ configuratie van Cloud Servicen ](../sites-developing/extending-cloud-config.md) voor meer informatie.

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

De [ IDS volmachtsarbeider ](indesign.md) is een voorbeeld van een [!DNL Assets] volmachtsarbeider die reeds uit-van-de-doos wordt verstrekt om de verwerking van de activa van het InDesign uit te besteden.

U kunt ook uw eigen [!DNL Assets] proxy-worker ontwikkelen en configureren om een gespecialiseerde worker te maken die uw [!DNL Assets] -verwerkingstaken verzendt en uitbesteedt.

Als u uw eigen aangepaste proxyworker wilt instellen, moet u:

* Instellen en implementeren (met gebruik van Gebeurtenis splitsen):

   * een aangepast taakonderwerp
   * een aangepaste taakgebeurtenishandler

* Gebruik vervolgens de JobService-API om:

   * Verzend uw aangepaste taak naar de proxy
   * uw taak beheren

* Als u de proxy uit een workflow wilt gebruiken, moet u een aangepaste externe stap implementeren met de WorkflowExternalProcess-API en de JobService-API.

In het volgende diagram en in de volgende stappen wordt gedetailleerd beschreven hoe u moet doorgaan:

![ chlimage_1-249 ](assets/chlimage_1-249.png)

>[!NOTE]
>
>In de volgende stappen worden equivalenten van InDesigns aangegeven als referentievoorbeelden.

1. A [ het Verdelen baan ](https://sling.apache.org/site/eventing-and-jobs.html) wordt gebruikt, zodat moet u een baanonderwerp voor uw gebruiksgeval bepalen.

   Zie `IDSJob.IDS_EXTENDSCRIPT_JOB` voor de IDS-proxyworker als voorbeeld.

1. De externe stap wordt gebruikt om de gebeurtenis te activeren en dan te wachten tot dat wordt gebeëindigd; dit wordt gedaan door op identiteitskaart te pollen. Ontwikkel uw eigen stap om nieuwe functionaliteit uit te voeren.

   Voer een `WorkflowExternalProcess` uit, dan gebruik de API JobService en uw baanonderwerp om een baangebeurtenis voor te bereiden en het te verzenden naar JobService (een dienst OSGi).

   Zie `INDDMediaExtractProcess` .java voor de IDS-proxyworker als voorbeeld.

1. Voer een baanmanager voor uw onderwerp uit. Deze manager vereist ontwikkeling zodat het uw specifieke actie uitvoert en beschouwd wordt als om de arbeidersimplementatie.

   Zie `IDSJobProcessor.java` voor de IDS-proxyworker als voorbeeld.

1. Gebruik `ProxyUtil.java` in dammen en komma&#39;s. Hiermee kunt u taken naar werknemers verzenden met de proxy voor moederdieren.

>[!NOTE]
>
>Wat het proxy-framework van [!DNL Assets] niet buiten de box biedt, is het poolmechanisme.
>
>Dankzij de integratie van [!DNL InDesign] hebt u toegang tot een groep [!DNL InDesign] -servers (IDSPool). Deze pooling is specifiek voor [!DNL InDesign] -integratie en maakt geen deel uit van het [!DNL Assets] -proxyframework.

>[!NOTE]
>
>Synchronisatie van resultaten:
>
>Bij n instanties die dezelfde proxy gebruiken, blijft het verwerkingsresultaat bij de proxy. Het is de taak van de client (Experience Manager Auteur) om het resultaat aan te vragen met dezelfde unieke taak-id als die aan de client is gegeven bij het maken van een taak. De proxy haalt de taak gewoon uit en zorgt ervoor dat het resultaat klaar is om te worden aangevraagd.
