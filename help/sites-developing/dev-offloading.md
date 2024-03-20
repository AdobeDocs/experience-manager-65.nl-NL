---
title: Banen voor offloaden maken en consumeren
description: De Apache Sling Discovery-functie biedt een Java API waarmee u JobManager-taken en JobConsumer-services kunt maken die deze gebruiken
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 4e6f452d-0251-46f3-ba29-1bd85cda73a6
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Banen voor offloaden maken en consumeren{#creating-and-consuming-jobs-for-offloading}

De Apache Sling Discovery-functie biedt een Java API waarmee u JobManager-taken en JobConsumer-services kunt maken die deze gebruiken.

Voor informatie over het creëren van het ontladen van topologieën en het vormen onderwerpconsumptie, zie [Taken verschuiven](/help/sites-deploying/offloading.md).

## Taaktaken verwerken {#handling-job-payloads}

Het offloading-framework definieert twee taakeigenschappen die u gebruikt om de taaklading te identificeren. De het ontladen replicatieagenten gebruiken deze eigenschappen om de middelen te identificeren om aan de instanties in de topologie te herhalen:

* `offloading.job.input.payload`: Een door komma&#39;s gescheiden lijst met inhoudspaden. De inhoud wordt gerepliceerd naar de instantie die de taak uitvoert.
* `offloading.job.output.payload`: Een door komma&#39;s gescheiden lijst met inhoudspaden. Wanneer de uitvoering van de taak is voltooid, wordt de taaklading gerepliceerd naar deze paden in de instantie die de taak heeft gemaakt.

Gebruik de `OffloadingJobProperties` enum to reference to the property names:

* `OffloadingJobProperties.INPUT_PAYLOAD.propertyName()`
* `OffloadingJobProperties.OUTPUT_PAYLOAD.propetyName()`

Taken vereisen geen nuttige taken. De payload is echter noodzakelijk als de taak de bewerking van een bron vereist en de taak wordt geoffload naar een computer die de taak niet heeft gemaakt.

## Taken maken voor offloaden {#creating-jobs-for-offloading}

Maak een client die de methode JobManager.addJob aanroept om een taak te maken die automatisch wordt uitgevoerd door een JobConsumer. Geef de volgende informatie op om de taak te maken:

* Onderwerp: Het taakonderwerp.
* Naam: (optioneel)
* Eigenschappenoverzicht: A `Map<String, Object>` object dat een aantal eigenschappen bevat, zoals de invoerlaadpaden en uitvoerpaden voor Payload. Dit object Map is beschikbaar voor het object JobConsumer dat de taak uitvoert.

De volgende voorbeelddienst leidt tot een baan voor een bepaald onderwerp en een weg van de inputlading.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import java.util.HashMap;

import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;

import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.ResourceResolver;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class JobGeneratorImpl implements JobGenerator  {

 @Reference
 private JobManager jobManager;
 @Reference ResourceResolverFactory resolverFactory;

 public String createJob(String topic, String payload) throws Exception {
  Job offloadingJob;

  ResourceResolver resolver = resolverFactory.getResourceResolver(null);
  if(resolver.getResource(payload)!=null){

   HashMap<String, Object> jobprops = new HashMap<String, Object>();
   jobprops.put(OffloadingJobProperties.INPUT_PAYLOAD.propertyName(), payload);

   offloadingJob = jobManager.addJob(topic, null, jobprops);
  } else {
   throw new Exception("Payload for job cannot be found");
  }
  if (offloadingJob == null){
   throw new Exception ("Offloading job could not be created");
  }
  return offloadingJob.getId();
 }
}
```

Het logbestand bevat het volgende bericht wanneer JobGeneratorImpl.createJob wordt aangeroepen voor het `com/adobe/example/offloading` en de `/content/geometrixx/de/services` lading:

```shell
10.06.2013 15:43:33.868 *INFO* [JobHandler: /etc/workflow/instances/2013-06-10/model_1554418768647484:/content/geometrixx/en/company] com.adobe.example.offloading.JobGeneratorImpl Received request to make job for topic com/adobe/example/offloading and payload /content/geometrixx/de/services
```

## Ontwikkeling van een banenconsument {#developing-a-job-consumer}

Om banen te verbruiken, ontwikkelt de dienst OSGi die uitvoert `org.apache.sling.event.jobs.consumer.JobConsumer` interface. Identificeer met het te verbruiken onderwerp gebruikend `JobConsumer.PROPERTY_TOPICS` eigenschap.

Het volgende voorbeeld van de implementatie van JobConsumer registreert bij `com/adobe/example/offloading` onderwerp. De consument plaatst eenvoudig het Consumed bezit van de knoop van de ladingsinhoud aan waar.

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;
import org.apache.sling.event.jobs.consumer.JobConsumer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.jcr.Session;
import javax.jcr.Node;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class MyJobConsumer implements JobConsumer {

 public static final String TOPIC = "com/adobe/example/offloading";

 @Property(value = TOPIC)
 static final String myTopic = JobConsumer.PROPERTY_TOPICS;

 @Reference
 private ResourceResolverFactory resolverFactory;

 @Reference
 private JobManager jobManager;

 private final Logger log = LoggerFactory.getLogger(getClass());

 public JobResult process(Job job) {
  JobResult result = JobResult.FAILED;
  String topic = job.getTopic();
  log.info("Consuming job of topic: {}", topic);
  String payloadIn =  (String) job.getProperty(OffloadingJobProperties.INPUT_PAYLOAD.propertyName());
  String payloadOut =  (String) job.getProperty(OffloadingJobProperties.OUTPUT_PAYLOAD.propertyName());

  log.info("Job has Input Payload {} and Output Payload {}",payloadIn, payloadOut);

  ResourceResolver resolver = null;
  try {
   resolver = resolverFactory.getAdministrativeResourceResolver(null);
   Session session = resolver.adaptTo(Session.class);
   Node inNode = session.getNode(payloadIn);
   inNode.getNode(Node.JCR_CONTENT).setProperty("consumed",true);
   result = JobResult.OK;
  }catch (Exception e){
   log.info("ERROR -- JOB RESULT IS FAILURE " + e.getMessage());
   result = JobResult.FAILED;
  }
  log.info("Job OK for payload {}",payloadIn);
  return result;
 }
}
```

De klasse MyJobConsumer produceert de volgende logboekberichten voor een inputlading van /content/geometrixx/de/services:

```shell
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Consuming job of topic: com/adobe/example/offloading
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job has Input Payload /content/geometrixx/de/services and Output Payload /content/geometrixx/de/services
10.06.2013 16:02:40.884 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job OK for payload /content/geometrixx/de/services
```

De eigenschap Consumed kan worden waargenomen met behulp van CRXDE Lite:

![chlimage_1-25](assets/chlimage_1-25a.png)

## Geweven afhankelijkheden {#maven-dependencies}

Voeg de volgende afhankelijkheidsdefenities toe aan het bestand pom.xml, zodat Maven de klassen die betrekking hebben op Offloading kan oplossen.

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.event</artifactId>
   <version>3.1.5-R1485539</version>
   <scope>provided</scope>
</dependency>
<dependency>
   <groupId>com.adobe.granite</groupId>
   <artifactId>com.adobe.granite.offloading.core</artifactId>
   <version>1.0.4</version>
   <scope>provided</scope>
</dependency>
```

In de voorgaande voorbeelden werden ook de volgende definities van afhankelijkheden vereist:

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.api</artifactId>
   <version>2.4.3-R1488084</version>
   <scope>provided</scope>
</dependency>

<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
   <version>2.0.0</version>
   <scope>provided</scope>
</dependency>
```
