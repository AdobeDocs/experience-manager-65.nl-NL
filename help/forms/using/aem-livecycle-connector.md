---
title: AEM Forms verbinden met Adobe LiveCycle
seo-title: AEM Forms verbinden met Adobe LiveCycle
description: Met AEM LiveCycle-aansluiting kunt u LiveCycle ES4 Document Services starten vanuit AEM apps en workflows.
seo-description: Met AEM LiveCycle-aansluiting kunt u LiveCycle ES4 Document Services starten vanuit AEM apps en workflows.
uuid: 7dc9d5ec-7b19-4d93-936d-81ceb45dfffa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 7e404b45-1302-4dd1-b3c9-3f47fedb5f94
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---


# AEM Forms verbinden met Adobe LiveCycle {#connecting-aem-forms-with-adobe-livecycle}

Met de Adobe Experience Manager (AEM) LiveCycle-aansluiting kunt u Adobe LiveCycle ES4 Document Services naadloos oproepen vanuit AEM webapps en workflows. LiveCycle biedt een rijke client SDK, waarmee clienttoepassingen met Java API&#39;s LiveCycle-services kunnen starten. AEM de Schakelaar van de LiveCycle vereenvoudigt het gebruiken van deze APIs binnen het milieu OSGi.

## AEM server verbinden met Adobe LiveCycle {#connecting-aem-server-to-adobe-livecycle}

AEM LiveCycle Connector is onderdeel van het [AEM Forms add-on pakket](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nadat u het AEM Forms-invoegpakket hebt geïnstalleerd, voert u de volgende stappen uit om gegevens van de LiveCycle-server toe te voegen aan AEM webconsole.

1. Zoek in AEM configuratiebeheer van de webconsole de configuratiecomponent van de Adobe LiveCycle Client SDK.
1. Klik op de component om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord te bewerken.
1. Controleer de instellingen en klik op **Opslaan**.

Hoewel de eigenschappen vanzelfsprekend zijn, zijn de belangrijkste als volgt:

* **Server URL**  - Geeft URL aan naar de LiveCycle server. Als u wilt dat LiveCycle en AEM communiceren via https, start u AEM met de volgende JVM

   ```java
   argument
    -Djavax.net.ssl.trustStore=<<em>path to LC keystore</em>>
   ```

   optie.

* **Gebruikersnaam** - Geeft de gebruikersnaam op van de account die wordt gebruikt om communicatie tussen AEM en LiveCycle tot stand te brengen. De account is een LiveCycle-gebruikersaccount die gemachtigd is om Document Services te starten.
* **Wachtwoord** - Geeft het wachtwoord op.
* **De Naam**  van de dienst - specificeert de diensten die gebruikend de gebruikersgeloofsbrieven worden begonnen die in de gebieden van de Gebruikersnaam en van het Wachtwoord worden verstrekt. Standaard worden geen referenties doorgegeven bij het starten van LiveCycle-services.

## Documentservices {#starting-document-services} starten

De toepassingen van de cliënt kunnen de diensten van LiveCycle programmatically beginnen gebruikend Java API, de Diensten van het Web, Remoting, en REST. Voor Java-clients kan de toepassing LiveCycle SDK gebruiken. De LiveCycle SDK biedt een Java API waarmee deze services op afstand kunnen worden gestart. Als u bijvoorbeeld een Microsoft Word-document naar PDF wilt converteren, start de client GeneratePDFService. De aanroepingsstroom bestaat uit de volgende stappen:

1. Maak een ServiceClientFactory-instantie.
1. Elke service biedt een clientklasse. Om de dienst te beginnen, creeer een cliëntgeval van de dienst.
1. Start de service en verwerkt het resultaat.

AEM de Schakelaar van de LiveCycle vereenvoudigt de stroom door deze cliëntinstanties als diensten bloot te stellen OSGi die kunnen worden betreden gebruikend standaardOSGi middelen. De aansluiting LiveCycle biedt de volgende functies:

* Clientinstanties als OSGi Service: De clients die als OSGI-bundels zijn verpakt, worden vermeld in de sectie [Document Services list](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Elke cliëntjar registreert de cliëntinstantie als dienst OSGi met de Registratie van de Dienst OSGi.
* Doorgave gebruikersreferenties: De verbindingsgegevens die nodig zijn om verbinding te maken met de LiveCycle-server worden centraal beheerd.
* ServiceClientFactory Service: Om de processen te beginnen, kan de cliënttoepassing tot de instantie toegang hebben ServiceClientFactory.

### Starten via verwijzingen naar service vanuit het OSGi Service Registry {#starting-via-service-references-from-osgi-service-registry}

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

   Om de dienst te beginnen, voeg overeenkomstig Geweven gebiedsdeel voor de dienst toe. Voor de lijst van gebiedsdelen, zie [Lijst van de Dienst van het Document](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Voeg bijvoorbeeld voor de service PDF genereren de volgende afhankelijkheid toe:

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

## RunAs-ondersteuning {#runas-support}

Bijna elke Document Service in LiveCycle vereist authentificatie. U kunt om het even welke volgende opties gebruiken om deze diensten te beginnen zonder expliciete geloofsbrieven in de code te verstrekken:

### Configuratie van Lijst van gewenste personen {#allowlist-configuration}

De configuratie van SDK van de Cliënt van LiveCycle bevat het plaatsen over de dienstnamen. Deze configuratie is een lijst van de diensten waarvoor de aanroepingslogica uit de doos beheerderreferentie gebruikt. Bijvoorbeeld, als u de diensten DirectoryManager (deel van het Beheer van de Gebruiker API) aan deze lijst toevoegt, kan om het even welke cliëntcode de dienst en de aanroepingslaag direct gebruiken automatisch op de gevormde geloofsbrieven als deel van het verzoek overgaan dat naar de server van LiveCycle wordt verzonden

### RunAsManager {#runasmanager}

Als deel van de integratie, wordt de nieuwe dienst RunAsManager verstrekt. Het staat u toe programmatically om referentie te controleren die moet worden gebruikt wanneer het maken van vraag aan de server van LiveCycle.

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

### InvocationRequest-eigenschap {#invocationrequest-property}

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

## Lijst Document Services {#document-services-list}

### Adobe LiveCycle client SDK API-bundel {#adobe-livecycle-client-sdk-api-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.um.api.AuthenticationManager
* com.adobe.idp.um.api.DirectoryManager
* com.adobe.idp.um.api.AuthorizationManager
* com.adobe.idp.dsc.registry.service.ServiceRegistry
* com.adobe.idp.dsc.registry.component.ComponentRegistry

#### Gemaakte afhankelijkheden {#maven-dependencies}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-1}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-cq-integration-api</artifactId>
  <version>1.1.10</version>
</dependency>
```

### Adobe LiveCycle TaskManager Client bundle {#adobe-livecycle-taskmanager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.taskmanager.dsc.client.task.TaskManager
* com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService
* com.adobe.idp.taskmanager.dsc.client.queuemanager.QueueManager
* com.adobe.idp.taskmanager.dsc.client.emailsettings.EmailSettingService
* com.adobe.idp.taskmanager.dsc.client.endpoint.TaskManagerEndpointClient
* com.adobe.idp.taskmanager.dsc.client.userlist.UserlistService

#### Gemaakte afhankelijkheden {#maven-dependencies-2}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-taskmanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Workflow Client Bundle {#adobe-livecycle-workflow-client-bundle}

De volgende service is beschikbaar:

* com.adobe.idp.workflow.client.WorkflowServiceClient

#### Gemaakte afhankelijkheden {#maven-dependencies-3}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-4}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-5}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-applicationmanager-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Assembler-clientbundel {#adobe-livecycle-assembler-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.assembler.client.AssemblerServiceClient

#### Gemaakte afhankelijkheden {#maven-dependencies-6}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-assembler-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle-clientbundel voor de integratie van formuliergegevens {#adobe-livecycle-form-data-integration-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.formdataintegration.client.FormDataIntegrationClient

#### Gemaakte afhankelijkheden {#maven-dependencies-7}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-8}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-9}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-10}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-reader-extensions-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Rights Manager Client-bundel {#adobe-livecycle-rights-manager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.livecycle.rightsmanagement.client.DocumentManager
* com.adobe.livecycle.rightsmanagement.client.EventManager
* com.adobe.livecycle.rightsmanagement.client.ExternalUserManager
* com.adobe.livecycle.rightsmanagement.client.LicenseManager
* com.adobe.livecycle.rightsmanagement.client.WatermarkManager
* com.adobe.livecycle.rightsmanagement.client.PolicyManager
* com.adobe.livecycle.rightsmanagement.client.AbstractPolicyManager

#### Gemaakte afhankelijkheden {#maven-dependencies-11}

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

#### Gemaakte afhankelijkheden {#maven-dependencies-12}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-signatures-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Truststore Client bundle {#adobe-livecycle-truststore-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.truststore.dsc.TrustConfigurationService
* com.adobe.truststore.dsc.CRLService
* com.adobe.truststore.dsc.CredentialService
* com.adobe.truststore.dsc.CertificateService

#### Gemaakte afhankelijkheden {#maven-dependencies-13}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-truststore-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Repository Client-bundel {#adobe-livecycle-repository-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.repository.bindings.ResourceRepository
* com.adobe.repository.bindings.ResourceSynchronizer

#### Gemaakte afhankelijkheden {#maven-dependencies-14}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-repository-client</artifactId>
  <version>11.0.0</version>
</dependency>
```
