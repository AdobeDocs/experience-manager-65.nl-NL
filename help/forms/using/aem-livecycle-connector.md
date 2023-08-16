---
title: AEM Forms verbinden met Adobe LiveCycle
seo-title: Connecting AEM Forms with Adobe LiveCycle
description: Met AEM aansluiting voor LiveCycles kunt u LiveCycle ES4 Document Services starten vanuit AEM apps en workflows.
seo-description: AEM LiveCycle connector lets you start LiveCycle ES4 Document Services from within AEM apps and workflows.
uuid: 7dc9d5ec-7b19-4d93-936d-81ceb45dfffa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 7e404b45-1302-4dd1-b3c9-3f47fedb5f94
role: Admin
exl-id: 562f8a22-cbab-4915-bc0d-da9bea7d18fa
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 0%

---

# AEM Forms verbinden met Adobe LiveCycle {#connecting-aem-forms-with-adobe-livecycle}

Met de Adobe Experience Manager (AEM) LiveCycle-aansluiting kunt u LiveCycle ES4 Document Services naadloos oproepen vanuit AEM webapps en workflows. LiveCycle biedt een SDK voor rijke clients, waarmee clienttoepassingen met Java API&#39;s services voor LiveCycles kunnen starten. AEM de Schakelaar van het LiveCycle vereenvoudigt het gebruiken van deze APIs binnen het milieu OSGi.

## AEM server verbinden met Adobe LiveCycle {#connecting-aem-server-to-adobe-livecycle}

AEM de Schakelaar van het LiveCycle maakt deel uit van [AEM Forms-invoegtoepassing](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nadat u het AEM Forms-add-onpakket hebt geïnstalleerd, voert u de volgende stappen uit om gegevens van de server van het LiveCycle toe te voegen aan AEM webconsole.

1. Zoek in AEM configuratiebeheer van de webconsole de configuratiecomponent van de client SDK van het Adobe LiveCycle.
1. Klik op de component om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord te bewerken.
1. Controleer de instellingen en klik op **Opslaan**.

Hoewel de eigenschappen vanzelfsprekend zijn, zijn de belangrijkste als volgt:

* **Server-URL** - Geeft de URL naar de server van het LiveCycle op. Als LiveCycle en AEM moeten communiceren via https, start AEM met de volgende JVM

  ```java
  argument
   -Djavax.net.ssl.trustStore=<<em>path to LC keystore</em>>
  ```

  -optie.

* **Gebruikersnaam**- Hier geeft u de gebruikersnaam op van de account die wordt gebruikt om communicatie tussen AEM en LiveCycle tot stand te brengen. De account is een gebruikersaccount voor LiveCycles die gemachtigd is om Document Services te starten.
* **Wachtwoord**- Geeft het wachtwoord op.
* **Servicenaam** - Geeft de services aan die worden gestart met de gebruikersgegevens in de velden Gebruikersnaam en Wachtwoord. Door gebrek, worden geen geloofsbrieven overgegaan terwijl de aanvang van de diensten van het LiveCycle.

## Documentservices starten {#starting-document-services}

De toepassingen van de cliënt kunnen de diensten van het LiveCycle programmatically beginnen gebruikend Java API, de Diensten van het Web, Remoting, en REST. Voor Java-clients kan de toepassing gebruikmaken van LiveCycle SDK. De LiveCycle SDK biedt een Java API waarmee deze services op afstand kunnen worden gestart. Als u bijvoorbeeld een Microsoft Word-document wilt converteren naar PDF, start de client GeneratePDFService. De aanroepingsstroom bestaat uit de volgende stappen:

1. Maak een ServiceClientFactory-instantie.
1. Elke service biedt een clientklasse. Om de dienst te beginnen, creeer een cliëntgeval van de dienst.
1. Start de service en verwerkt het resultaat.

AEM de Schakelaar van het LiveCycle vereenvoudigt de stroom door deze cliëntinstanties als diensten bloot te stellen OSGi die kunnen worden betreden gebruikend standaardOSGi middelen. De aansluiting van het LiveCycle biedt de volgende functies:

* Clientinstanties als OSGi-service: de clients die als OSGI-bundels zijn verpakt, worden vermeld in de [Lijst met Document Services](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p) sectie. Elke cliëntjar registreert de cliëntinstantie als dienst OSGi met de Registratie van de Dienst OSGi.
* Doorgave gebruikersreferenties: de verbindingsgegevens die nodig zijn om verbinding te maken met de server van het LiveCycle worden centraal beheerd.
* ServiceClientFactory Service: om de processen te starten, heeft de clienttoepassing toegang tot de ServiceClientFactory-instantie.

### Beginnend via de Verwijzingen van de Dienst van OSGi Registratie van de Dienst {#starting-via-service-references-from-osgi-service-registry}

Om de blootgestelde dienst van binnen AEM te beginnen, voer de volgende stappen uit:

1. Geweven afhankelijkheden bepalen. Voeg gebiedsdeel aan de vereiste cliëntbar in uw gegeven pom.xml- dossier toe. Voeg minstens afhankelijkheid toe aan adobe-livecycle-client en adobe-usermanager-client-jars.

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-livecycle-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-usermanager-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-cq-integration-api</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

   Om de dienst te beginnen, voeg overeenkomstig Geweven gebiedsdeel voor de dienst toe. Voor de lijst van gebiedsdelen, zie [Lijst met documentservices](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Bijvoorbeeld, voor de Generate dienst van de PDF voegt de volgende gebiedsdeel toe:

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-generatepdf-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

1. Verkrijg de de dienstverwijzing. Krijg een handvat aan de de dienstinstantie. Als u een klasse van Java schrijft, kunt u de Verklarende annotaties van de Diensten gebruiken.

   ```java
   import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient;
   import com.adobe.livecycle.generatepdf.client.CreatePDFResult;
   import com.adobe.idp.Document;
   
   @Reference
   GeneratePdfServiceClient generatePDF;
   ...
   
   Resource r = resourceResolver.getResource("/path/tp/docx");
   Document sourceDoc = new Document(r.adaptTo(InputStream.class));
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

   Met het bovenstaande codefragment wordt de createPDF API van GeneratePDFServiceClient gestart om een document naar PDF te converteren. U kunt gelijkaardige aanroeping in JSP uitvoeren gebruikend de volgende code. Het belangrijkste verschil is het volgende codegebruik Sling ScriptHelper om tot GeneratePdfServiceClient toegang te hebben.

   ```jsp
   <%@ page import="com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient" %>
   <%@ page import="com.adobe.livecycle.generatepdf.client.CreatePDFResult" %>
   <%@ page import="com.adobe.idp.Document" %>
   
   GeneratePdfServiceClient generatePDF = sling.getService(GeneratePdfServiceClient.class);
   Document sourceDoc = ...
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

### Starten via ServiceClientFactory {#starting-via-serviceclientfactory}

De klasse ServiceClientFactory is in sommige gevallen vereist. U hebt bijvoorbeeld ServiceClientFactory nodig om processen aan te roepen.

```java
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;

@Reference
ServiceClientFactoryProvider scfProvider;

...
ServiceClientFactory scf = scfProvider.getDefaultServiceClientFactory();
...
```

## Ondersteuning voor RunAs {#runas-support}

Bijna vereist elke Document Service in LiveCycle authentificatie. U kunt om het even welke volgende opties gebruiken om deze diensten te beginnen zonder expliciete geloofsbrieven in de code te verstrekken:

### Configuratie Lijst van gewenste personen {#allowlist-configuration}

De configuratie van SDK van de Cliënt van het LiveCycle bevat het plaatsen over de dienstnamen. Deze configuratie is een lijst van de diensten waarvoor de aanroepingslogica uit de doos beheerderreferentie gebruikt. Bijvoorbeeld, als u de diensten DirectoryManager (deel van het Beheer van de Gebruiker API) aan deze lijst toevoegt, kan om het even welke cliëntcode de dienst en de aanroepingslaag direct gebruiken automatisch op de gevormde geloofsbrieven als deel van het verzoek overgaan dat naar de server van het LiveCycle wordt verzonden

### RunAsManager {#runasmanager}

Als deel van de integratie, wordt de nieuwe dienst RunAsManager verstrekt. Het laat u programmatically te gebruiken referentie controleren wanneer het maken van vraag aan de server van het LiveCycle.

```java
import com.adobe.livecycle.dsc.clientsdk.security.PasswordCredential;
import com.adobe.livecycle.dsc.clientsdk.security.PrivilegedAction;
import com.adobe.livecycle.dsc.clientsdk.security.RunAsManager;
import com.adobe.idp.dsc.registry.component.ComponentRegistry;

@Reference
private RunAsManager runAsManager;

List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
            public List<Component> run() {
                return componentRegistry.getComponents();
            }
        });
assertNotNull(components);
```

Als u verschillende referentie wilt overgaan, kunt u de overbelaste methode gebruiken die een instantie PasswordCredential neemt.

```java
PasswordCredential credential = new PasswordCredential("administrator","password");
List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
    public List<Component> run() {
        return componentRegistry.getComponents();
    }
},credential);
```

### InvocationRequest, eigenschap {#invocationrequest-property}

Als u een proces roept of direct gebruik maakt van de klasse ServiceClientFactory en een InvocationRequest creeert, kunt u een bezit specificeren om erop te wijzen dat de aanroepingslaag gevormde geloofsbrieven zou moeten gebruiken.

```java
import com.adobe.idp.dsc.InvocationResponse
import com.adobe.idp.dsc.InvocationRequest
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory
import com.adobe.livecycle.dsc.clientsdk.InvocationProperties

ServiceClientFactoryProvider scfp = sling.getService(ServiceClientFactoryProvider.class)
ServiceClientFactory serviceClientFactory = scfp.getDefaultServiceClientFactory()
InvocationRequest ir = serviceClientFactory.createInvocationRequest("sample/LetterSubmissionProcess", "invoke", new HashMap(), true);

//Here we are invoking the request with system user
ir.setProperty(InvocationProperties.INVOKER_TYPE,InvocationProperties.INVOKER_TYPE_SYSTEM)

InvocationResponse response = serviceClientFactory.getServiceClient().invoke(ir);
```

## Lijst met Document Services {#document-services-list}

### Adobe LiveCycle client SDK API-bundel {#adobe-livecycle-client-sdk-api-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.um.api.AuthenticationManager
* com.adobe.idp.um.api.DirectoryManager
* com.adobe.idp.um.api.AuthorizationManager
* com.adobe.idp.dsc.registry.service.ServiceRegistry
* com.adobe.idp.dsc.registry.component.ComponentRegistry

#### Geweven afhankelijkheden {#maven-dependencies}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-client</artifactId>
  <version>11.0.0</version>
</dependency>
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-usermanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle client SDK-bundel {#adobe-livecycle-client-sdk-bundle}

De volgende services zijn beschikbaar:

* com.adobe.livecycle.dsc.clientsdk.security.RunAsManager
* com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider

#### Geweven afhankelijkheden {#maven-dependencies-1}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-cq-integration-api</artifactId>
  <version>1.1.10</version>
</dependency>
```

### Adobe LiveCycle TaskManager Client-bundel {#adobe-livecycle-taskmanager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.taskmanager.dsc.client.task.TaskManager
* com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService
* com.adobe.idp.taskmanager.dsc.client.queuemanager.QueueManager
* com.adobe.idp.taskmanager.dsc.client.emailsettings.EmailSettingService
* com.adobe.idp.taskmanager.dsc.client.endpoint.TaskManagerEndpointClient
* com.adobe.idp.taskmanager.dsc.client.userlist.UserlistService

#### Geweven afhankelijkheden {#maven-dependencies-2}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-taskmanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Client-bundel voor Adobe LiveCycle Workflow {#adobe-livecycle-workflow-client-bundle}

De volgende service is beschikbaar:

* com.adobe.idp.workflow.client.WorkflowServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-3}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-workflow-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle PDF Generator Client-bundel {#adobe-livecycle-pdf-generator-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-4}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-generatepdf-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Application Manager Client-bundel {#adobe-livecycle-application-manager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.applicationmanager.service.ApplicationManager
* com.adobe.livecycle.applicationmanager.client.ApplicationManager
* com.adobe.livecycle.design.service.DesigntimeService

#### Geweven afhankelijkheden {#maven-dependencies-5}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-applicationmanager-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Assembler Client-bundel {#adobe-livecycle-assembler-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.assembler.client.AssemblerServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-6}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-assembler-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Form Data Integration Client-bundel {#adobe-livecycle-form-data-integration-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.formdataintegration.client.FormDataIntegrationClient

#### Geweven afhankelijkheden {#maven-dependencies-7}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-formdataintegration-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Forms Client-bundel {#adobe-livecycle-forms-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.formsservice.client.FormsServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-8}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-forms-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Output Client-bundel {#adobe-livecycle-output-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.output.client.OutputClient

#### Geweven afhankelijkheden {#maven-dependencies-9}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-output-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Reader Extensions Client-bundel {#adobe-livecycle-reader-extensions-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.readerextensions.client.ReaderExtensionsServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-10}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-reader-extensions-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Client-bundel voor Adobe LiveCycle Rights Manager {#adobe-livecycle-rights-manager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.livecycle.rightsmanagement.client.DocumentManager
* com.adobe.livecycle.rightsmanagement.client.EventManager
* com.adobe.livecycle.rightsmanagement.client.ExternalUserManager
* com.adobe.livecycle.rightsmanagement.client.LicenseManager
* com.adobe.livecycle.rightsmanagement.client.WatermarkManager
* com.adobe.livecycle.rightsmanagement.client.PolicyManager
* com.adobe.livecycle.rightsmanagement.client.AbstractPolicyManager

#### Geweven afhankelijkheden {#maven-dependencies-11}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-rightsmanagement-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Signatures Client bundle {#adobe-livecycle-signatures-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.signatures.client.SignatureServiceClientInterface

#### Geweven afhankelijkheden {#maven-dependencies-12}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-signatures-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Truststore Client-bundel {#adobe-livecycle-truststore-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.truststore.dsc.TrustConfigurationService
* com.adobe.truststore.dsc.CRLService
* com.adobe.truststore.dsc.CredentialService
* com.adobe.truststore.dsc.CertificateService

#### Geweven afhankelijkheden {#maven-dependencies-13}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-truststore-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Client-bundel voor opslagplaats LiveCycle Adobe {#adobe-livecycle-repository-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.repository.bindings.ResourceRepository
* com.adobe.repository.bindings.ResourceSynchronizer

#### Geweven afhankelijkheden {#maven-dependencies-14}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-repository-client</artifactId>
  <version>11.0.0</version>
</dependency>
```
