---
title: Services integreren met de JMX-console
description: Stel de dienstattributen en verrichtingen bloot om beleidstaken toe te laten om worden uitgevoerd door tot stand te brengen en in te voeren MBans om de diensten te beheren gebruikend de Console JMX
topic-tags: extending-aem
content-type: reference
exl-id: fe727406-09cb-4516-8278-806fd78cfc12
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1621'
ht-degree: 0%

---

# Services integreren met de JMX-console{#integrating-services-with-the-jmx-console}

Maak en implementeer MBans om services te beheren met de JMX-console. Stel de dienstattributen en verrichtingen bloot om beleidstaken toe te laten om worden uitgevoerd.

Voor informatie over het gebruik van de JMX-console raadpleegt u [Serverbronnen controleren met de JMX-console](/help/sites-administering/jmx-console.md).

## JMX Framework in Felix en CQ5 {#the-jmx-framework-in-felix-and-cq}

Op het Apache Felix-platform implementeert u MBans als OSGi-services. Wanneer een dienst MBean in de Registratie van de Dienst OSGi wordt geregistreerd, registreert de module JMX van Aries automatisch MBean met de Server MBean. De MBean is dan beschikbaar aan de Console JMX die de openbare attributen en de verrichtingen blootstelt.

![jmxwhiteboard](assets/jmxwhiteboard.png)

## Bezig met het maken van MBans voor CQ5 en CRX {#creating-mbeans-for-cq-and-crx}

MBeans die u voor het beheren van CQ5 of CRX middelen creeert zijn gebaseerd op de interface javax.management.DynamicMBean. Als u deze wilt maken, volgt u de gebruikelijke ontwerppatronen die in de JMX-specificatie worden beschreven:

* Maak de beheerinterface, inclusief get, set en is methoden om kenmerken te definiëren en andere methoden om bewerkingen te definiëren.
* Maak de implementatieklasse. De klasse moet DynamicMBean implementeren of een implementatieklasse van DynamicMBean uitbreiden.
* Volg de standaard noemende overeenkomst zodat de naam van de implementatieklasse de interfacenaam met het achtervoegsel MBean is.

Naast het bepalen van de beheersinterface, bepaalt de interface ook de OSGi de dienstinterface. De implementatieklasse implementeert de OSGi-service.

### Het gebruiken van Annotaties om Informatie MBean te verstrekken {#using-annotations-to-provide-mbean-information}

De [com.adobe.granite.jmx.annotation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/jmx/annotation/package-summary.html) Het pakket biedt verschillende annotaties en klassen waarmee u eenvoudig metagegevens van MBean aan de JMX-console kunt leveren. Gebruik deze annotaties en klassen in plaats van rechtstreeks informatie toe te voegen aan het MBean-object MBeanInfo.

**Annotaties**

Voeg annotaties aan de beheersinterface toe om meta-gegevens te specificeren MBean. De informatie verschijnt in de console JMX voor elke implementatieklasse die wordt opgesteld. De volgende annotaties zijn beschikbaar (zie voor volledige informatie de [com.adobe.granite.jmx.annotation JavaDocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/jmx/annotation/package-summary.html)):

* **Omschrijving:** Verstrekt een beschrijving van de klasse MBean of de methode. Wanneer gebruikt op de klassendeclaratie, verschijnt de beschrijving op de pagina van de Console JMX voor MBean. Wanneer de beschrijving bij een methode wordt gebruikt, wordt deze weergegeven als zwevende tekst voor het bijbehorende kenmerk of de bijbehorende bewerking.
* **Effect:** Het effect van een methode. Geldige parameterwaarden zijn de velden die worden gedefinieerd door [javax.management.MBeanOperationInfo](https://docs.oracle.com/javase/1.5.0/docs/api/javax/management/MBeanOperationInfo.html).

* **Naam:** Geeft de naam op die voor een bewerkingsparameter moet worden weergegeven. Gebruik deze aantekening om de daadwerkelijke naam van de methodeparameter met voeten te treden die in de interface wordt gebruikt.
* **OpenTypeInfo:** Geeft de klasse op die moet worden gebruikt voor het weergeven van samengestelde gegevens of tabelgegevens in de JMX-console. Voor gebruik met Open MBans
* **TabularTypeInfo:** Wordt gebruikt om een annotatie toe te voegen aan de klasse die wordt gebruikt om tabelgegevens te vertegenwoordigen.

**Klassen**

De klassen worden verstrekt voor het creëren van Dynamische MBans die de annotaties verbruiken die u aan hun interfaces toevoegt:

* **AnnoatedStandardMBean:** Een subklasse van de klasse javax.management.StandardMBean die de JMX-console automatisch de metagegevens voor annotaties verschaft.
* **OpenAnnoatedStandardMBean:** Een subklasse van de klasse AnnoatedStandardMBean voor het maken van Open Mbeans die de OpenTypeInfo-annotatie gebruiken.

### Bezig met ontwikkelen van MBeans {#developing-mbeans}

Typisch, is uw MBean een bezinning op de dienst OSGi die u wilt beheren. Op het platform van Felix, creeert u MBean zoals u voor plaatsing op andere de serverplatforms van Java zou willen. Een primair verschil is dat u annotaties kunt gebruiken om MBean-informatie op te geven:

* Beheerinterface: definieert kenmerken met behulp van getter, setter en is methoden. Bepaalt verrichtingen gebruikend een andere openbare methode. Gebruikt annotaties om metagegevens voor het BeanInfo-object op te geven.
* MBean-klasse: implementeert de beheerinterface. Breidt de klasse AnnotatedStandardMBean uit zodat het de annotaties op de interface verwerkt.

Het volgende voorbeeld MBean verstrekt informatie over de bewaarplaats CRX. De interface gebruikt de aantekening van de Beschrijving om informatie aan de console te verstrekken JMX.

#### Management Interface {#management-interface}

```java
package com.adobe.example.myapp;

import com.adobe.granite.jmx.annotation.Description;

@Description("Example MBean that exposes repository properties.")
public interface ExampleMBean {

    @Description("The name of the repository.")
    String getRepositoryName();

    @Description("The vendor of the repository.")
    String   getRepositoryVendor();

    @Description("The URL of repository vendor.")
    String getVendorUrl();
}
```

De implementatieklasse gebruikt de SlingRepository-service om informatie over de CRX-opslagplaats op te halen.

#### MBean Implementation Class {#mbean-implementation-class}

```java
package com.adobe.example.myapp;

import org.apache.felix.scr.annotations.*;
import org.apache.sling.jcr.api.SlingRepository;

import com.adobe.granite.jmx.annotation.AnnotatedStandardMBean;

import javax.management.*;

public class ExampleMBeanImpl extends AnnotatedStandardMBean implements ExampleMBean {

    @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
    private SlingRepository repository;

    public ExampleMBeanImpl() throws NotCompliantMBeanException {
        super(ExampleMBean.class);
    }

    public String getRepositoryName() {
        return repository.getDescriptor("jcr.repository.name");
    }

    public String getRepositoryVendor() {
        return repository.getDescriptor("jcr.repository.vendor");
    }

    public String getVendorUrl() {
        return repository.getDescriptor("jcr.repository.vendor.url");
    }
}
```

In de volgende afbeelding ziet u de pagina voor deze MBean in de JMX-console.

![jmxdescription](assets/jmxdescription.png)

### Registreren van MBeans {#registering-mbeans}

Wanneer u MBeans als dienst OSGi registreert, worden zij automatisch geregistreerd met de Server MBean. Om een MBean op CQ5 te installeren, omvat het in een bundel en voert de dienst MBean uit zoals u een andere dienst OSGi.

Naast OSGi-verwante meta-gegevens, moet u meta-gegevens ook verstrekken die de module JMX Whiteboard van Aries voor het registreren van MBean met de Server MBean vereist:

* **De naam van de DynamicMBean-interface:** Verklaar dat de dienst MBean uitvoert `javax.management.DynamicMBea`n interface. Deze verklaring deelt de module JMX Whiteboard van Aries mee dat de dienst een dienst MBean is.

* **Het domein MBean en belangrijkste eigenschappen:** Voor Felix, verstrekt u deze informatie als bezit van de dienst OSGi van MBean. Dit is de zelfde informatie die u normaal aan de Server MBean in a verstrekt `javax.management.ObjectName` object.

Wanneer uw MBean een bezinning van de enige dienst is, slechts wordt één enkel geval van de dienst MBean vereist. In dit geval, als u de SCR van Felix Geweven stop gebruikt, kunt u de Runtime van de Component van de Dienst van Apache (SCR) annotaties op de MBean implementatieklasse gebruiken om JMX-verwante metatgegevens te specificeren. Om verscheidene instanties te concretiseren MBean, kon u een andere klasse tot stand brengen die die registratie van de dienst OSGi van MBean uitvoert. In dit geval worden de JMX-metagegevens gegenereerd bij uitvoering.

**Eén MBean**

MBans waarvoor u alle attributen en verrichtingen in ontwerptijd kunt bepalen kan worden opgesteld gebruikend SCR annotaties in de MBean implementatieklasse. In het volgende voorbeeld wordt `value` kenmerk van de `Service` annotatie verklaart dat de dienst uitvoert `DynamicMBean` interface. De `name` kenmerk van de `Property` Met aantekening worden het JMX-domein en de sleuteleigenschappen opgegeven.

#### MBean de Klasse van de Implementatie met SCR Annotaties {#mbean-implementation-class-with-scr-annotations}

```java
package com.adobe.example.myapp;

import org.apache.felix.scr.annotations.*;
import org.apache.sling.jcr.api.SlingRepository;

import com.adobe.granite.jmx.annotation.AnnotatedStandardMBean;

import javax.management.*;

@Component(immediate = true)
@Property(name = "jmx.objectname", value="com.adobe.example:type=CRX")
@Service(value = DynamicMBean.class)
public class ExampleMBeanImpl extends AnnotatedStandardMBean implements ExampleMBean {

    @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
    private SlingRepository repository;

    public ExampleMBeanImpl() throws NotCompliantMBeanException {
        super(ExampleMBean.class);
    }

    public String getRepositoryName() {
        return repository.getDescriptor("jcr.repository.name");
    }

    public String getRepositoryVendor() {
        return repository.getDescriptor("jcr.repository.vendor");
    }

    public String getVendorUrl() {
        return repository.getDescriptor("jcr.repository.vendor.url");
    }
}
```

**Meerdere MBean-serviceinstanties**

Om veelvoudige instanties van de beheerde dienst te beheren, creeert u veelvoudige instanties van de overeenkomstige dienst MBean. Voorts zouden de de dienstinstanties MBean moeten worden gecreeerd of worden verwijderd wanneer de beheerde instanties zijn begonnen of gestopt. U kunt een MBean managerklasse tot stand brengen om de diensten MBean bij runtime te concretiseren, en de de dienstlevenscyclus te beheren.

Gebruik BundleContext om MBean als dienst te registreren OSGi. Neem de JMX-gerelateerde informatie op in het object Dictionary die u gebruikt als argument voor de methode BundleContext.registerService.

In het volgende codevoorbeeld, wordt de dienst ExampleMBean programmatically geregistreerd. Het componentContext-object is ComponentContext, dat toegang biedt tot BundleContext.

#### Codefragment: Programmatische MBean Service Registration {#code-snippet-programmatic-mbean-service-registration}

```java
Dictionary mbeanProps = new Hashtable();
mbeanProps.put("jmx.objectname", "com.adobe.example:type=CRX");
ExampleMBeanImpl mbean = new ExampleMBeanImpl();
ServiceRegistration serviceregistration =
            componentContext.getBundleContext().registerService(DynamicMBean.class.getName(), mbean, mbeanProps);
```

Het voorbeeld MBean in de volgende sectie verstrekt meer details.

Een MBean de dienstmanager is nuttig wanneer de dienstconfiguraties in de bewaarplaats worden opgeslagen. De manager kan de dienstinformatie terugwinnen en het gebruiken om het overeenkomstige MBean te vormen en tot stand te brengen. De manager-klasse kan ook luisteren naar wijzigingsgebeurtenissen in de repository en de MBean-services dienovereenkomstig bijwerken.

## Voorbeeld: workflowmodellen controleren met JMX {#example-monitoring-workflow-models-using-jmx}

In dit voorbeeld geeft de MBean informatie over de CQ5-workflowmodellen die in de opslagplaats zijn opgeslagen. Een MBean managerklasse leidt tot MBans die op de modellen van het Werkschema wordt gebaseerd die in de bewaarplaats worden opgeslagen en hun dienst OSGi bij runtime registreert. Dit voorbeeld bestaat uit één bundel die de volgende leden bevat:

* WorkflowMBean: De beheerinterface.
* WorkflowMBeanImpl: De implementatieklasse MBean.
* WorkflowMBeanManager: De interface van de MBean managerklasse.
* WorkflowMBeanManagerImpl: De implementatieklasse van de MBean-manager.

**Opmerking:** Voor de eenvoud voert de code in dit voorbeeld geen logboekregistratie uit of reageert op gegenereerde uitzonderingen.

WorkflowMBeanManagerImpl omvat een methode van de componentenactivering. Wanneer de component wordt geactiveerd, voert de methode de volgende taken uit:

* Verkrijgt een BundleContext voor de bundel.
* Zoekt de opslagplaats om de wegen van de bestaande modellen van het Werkschema te verkrijgen.
* Maakt MBans voor elk workflowmodel.
* Registreert de MBans bij het OSGi de dienstregister.

De metagegevens van MBean worden weergegeven in de JMX Console met het domein com.adobe.example, het type workflow_model en Eigenschappen is het pad van het knooppunt voor configuratie van het workflowmodel.

![jmxworkflowboon](assets/jmxworkflowmbean.png)

### Het voorbeeld MBean {#the-example-mbean}

Dit voorbeeld vereist een interface MBean en een implementatie die een bezinning op `com.day.cq.workflow.model.WorkflowModel` interface. MBean is zeer eenvoudig zodat het voorbeeld zich op de configuratie en plaatsingsaspecten van het ontwerp kan concentreren. De MBean stelt één enkel attribuut, de modelnaam bloot.

#### WorkflowMBean Interface {#workflowmbean-interface}

```java
package com.adobe.example.myapp.api;

import com.adobe.granite.jmx.annotation.Description;

@Description("Example MBean that exposes Workflow model properties.")
public interface WorkflowMBean {

 @Description("The name of the Workflow model.")
 String getModelName();
}
```

#### WorkflowMBeanImpl {#workflowmbeanimpl}

```java
package com.adobe.example.myapp.impl;

import javax.management.NotCompliantMBeanException;

import com.day.cq.workflow.model.WorkflowModel;
import com.adobe.example.myapp.api.WorkflowMBean;
import com.adobe.granite.jmx.annotation.AnnotatedStandardMBean;

public class WorkflowMBeanImpl extends AnnotatedStandardMBean implements WorkflowMBean {

 WorkflowModel model;

 protected WorkflowMBeanImpl(WorkflowModel inmodel)
   throws NotCompliantMBeanException {
  super(WorkflowMBean.class);
  model=inmodel;
 }

 public String getModelName() {
  return model.getTitle();
 }
}
```

### De voorbeeld-MBean-manager {#the-example-mbean-manager}

De dienst WorkflowMBeanManager omvat de methode van de componentenactivering die tot de diensten WorkflowMBean leidt. De de dienstimplementatie omvat de volgende methodes:

* activeren: de componentactivator. Maakt de JCR-sessie voor het lezen van Workflowmodel-configuratieknooppunten. Het basisknooppunt waar modelconfiguraties worden opgeslagen, wordt gedefinieerd in een statisch veld. De naam van het configuratieknooppunt wordt ook gedefinieerd in een statisch veld. Deze methode roept andere methodes die de wegen van het knoopmodel verkrijgen en modelWorkflowMBans creëren.
* getModelIds: doorloopt de gegevensopslagruimte onder het hoofdknooppunt en haalt het pad van elk modelknooppunt op.
* makeMBean: Gebruikt de modelweg om een voorwerp te creëren WorkflowModel, creeert een WorkflowMBean voor het, en registreert zijn dienst OSGi.

>[!NOTE]
>
>De implementatie WorkflowMBeanManager leidt slechts tot de diensten MBean voor modelconfiguraties die bestaan wanneer de component wordt geactiveerd. Een robuustere implementatie luistert naar opslagplaatsgebeurtenissen met betrekking tot nieuwe modelconfiguraties en wijzigingen of verwijderingen van bestaande modelconfiguratie. Wanneer een verandering voorkomt, kan de manager, de overeenkomstige dienst creëren wijzigen of verwijderen WorkflowMBean.
>

#### WorkflowMBeanManager Interface {#workflowmbeanmanager-interface}

```java
package com.adobe.example.myapp.api;

public interface WorkflowMBeanManager {

}
```

#### WorkflowMBeanManagerImpl {#workflowmbeanmanagerimpl}

```java
package com.adobe.example.myapp.impl;

import java.util.*;

import org.apache.felix.scr.annotations.*;

import javax.jcr.Session;
import javax.jcr.Node;
import javax.jcr.NodeIterator;
import javax.jcr.RepositoryException;
import javax.management.ObjectName;

import org.apache.sling.jcr.api.SlingRepository;
import org.osgi.framework.ServiceRegistration;
import org.osgi.service.component.ComponentContext;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.workflow.WorkflowService;
import com.day.cq.workflow.WorkflowSession;
import com.adobe.example.myapp.api.WorkflowMBean;
import com.adobe.example.myapp.api.WorkflowMBeanManager;

/**Instantiates and registers WorkflowMBean services */
@Component(immediate=true)
@Service(value=WorkflowMBeanManager.class)
public class WorkflowMBeanManagerImpl implements WorkflowMBeanManager {
 //The ComponentContext provides access to the BundleContext
 private ComponentContext componentContext;

 //Use the SlingRepository service to read model nodes
 @Reference
        private SlingRepository repository = null;

 //Use the WorkflowService service to create WorkflowModel objects
 @Reference
 private WorkflowService workflowservice = null;

  private Session session;

         //Details about model nodes
  private static final String MODEL_ROOT ="/etc/workflow/models";
  private static final String MODEL_NODE = "model";

  private Set<String> modelIds = new HashSet<String>();

        //Storage for ServiceRegistrations for MBean services
  private Collection<ServiceRegistration> mbeanRegistrations= new Vector<ServiceRegistration>(0,1);

 @Activate
        protected void activate(ComponentContext ctx) {
             //Traverse the repository and load the model nodes
             try {
                   session = repository.loginAdministrative(null);
                   // load and store model node paths
                   if (session.nodeExists(MODEL_ROOT)) {
                          getModelIds(session.getNode(MODEL_ROOT));
                   }
                   //Create MBeans for each model
                   for(String modid: modelIds){
                    makeMBean(modid);
                    }
             }catch(Exception e){ }
          }

        /**
         * Add JMX domain and key properties to a collection
         * Instantiate a WorkflowModel and its WorkflowMBeanImpl object
         * Register the MBean OSGi service
         */
 private void makeMBean(String modelId) {
             // create MBean for the model
             try {
                 Dictionary<String, String> mbeanProps = new Hashtable<String, String>();
                 //These properties appear on the JMX Console home page
                 mbeanProps.put("jmx.objectname", "com.adobe.example:type=workflow_model,id=" + ObjectName.quote(modelId));
                 WorkflowSession wfsession = workflowservice.getWorkflowSession(session);
                 WorkflowMBeanImpl mbean = new WorkflowMBeanImpl(wfsession.getModel(modelId));

                ServiceRegistration serviceregistration = componentContext.getBundleContext().registerService(WorkflowMBean.class.getName(), mbean, mbeanProps);
                //Store the ServiceRegistration objects for deactivation
                mbeanRegistrations.add(serviceregistration);
             } catch (Throwable t) {}
         }

        /**
         * Traverses the repository branch below a given Node. Stores the path of each model node.
         */
 private void getModelIds(Node node) throws RepositoryException {
  try{
                     NodeIterator iter = node.getNodes();
                     while (iter.hasNext()) {
                           Node n = iter.nextNode();
                           //Look for "jcr:content" nodes
                           if (n.getName().equals("jcr:content")) {
                                //get the path of the model node and save it
                                if(n.hasNode(MODEL_NODE)){
                                      modelIds.add(n.getNode(MODEL_NODE).getPath());
                                 }
                           } else{
                                   //Scan child nodes
                                   getModelIds(n);
                           }
                       }
  }catch(Exception e){ }
       }

        /**
         * Log out of the JCR session and unregister WorkflowMBean services
         */
        @Deactivate
        protected void deactivate() {
          session.logout();
          session=null;
          for(ServiceRegistration sr:mbeanRegistrations){
         sr.unregister();
          }
        }
}
```

### Het POM-bestand voor het voorbeeld MBean {#the-pom-file-for-the-example-mbean}

Voor uw gemak, kunt u de volgende code van XML in uw project pom.xml- dossier kopiëren en kleven voor de bouw van de componentenbundel. De POM verwijst naar verschillende vereiste plug-ins en afhankelijkheden.

**Insteekmodules:**

* Apache Maven Compiler Plugin: compileert Java-klassen uit broncode.
* Apache Felix Maven Bundle Plugin: maakt de bundel en het manifest
* Apache Felix Maven SCR Insteekmodule: Creeert het dossier van de componentenbeschrijver en vormt de dienst-component duidelijke kopbal.

**Opmerking:** Op het moment dat u schrijft, is de gemeten scr-insteekmodule niet compatibel met de m2e-insteekmodule voor Eclipse. (Zie [Felix bug 3170](https://issues.apache.org/jira/browse/FELIX-3170).) Om winde van de Verduistering te gebruiken, installeer Geweven en gebruik de interface van de bevellijn om bouwstijlen uit te voeren.

#### Voorbeeld-POM-bestand {#example-pom-file}

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.2-SNAPSHOT</version>
  <name>mbean-simple</name>
  <url>www.adobe.com</url>
  <description>A simple MBean</description>
  <packaging>bundle</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>
    <build>
        <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <configuration>
                <source>1.5</source>
                <target>1.5</target>
            </configuration>
        </plugin>
            <plugin>
                <groupId>org.apache.felix</groupId>
                <artifactId>maven-scr-plugin</artifactId>
                <version>1.7.2</version>
                <executions>
                    <execution>
                        <id>generate-scr-scrdescriptor</id>
              <goals>
                 <goal>scr</goal>
              </goals>
            </execution>
         </executions>
            </plugin>
             <plugin>
            <groupId>org.apache.felix</groupId>
            <artifactId>maven-bundle-plugin</artifactId>
            <version>1.4.3</version>
            <extensions>true</extensions>
            <configuration>
                <instructions>
                    <Export-Package>com.adobe.example.myapp.*;version=${project.version}</Export-Package>
                </instructions>
            </configuration>
        </plugin>
        </plugins>
    </build>
    <dependencies>
        <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr.annotations</artifactId>
            <version>1.6.0</version>
            <scope>provided</scope>
        </dependency>
         <dependency>
            <groupId>org.apache.sling</groupId>
            <artifactId>org.apache.sling.api</artifactId>
            <version>2.0.8</version>
            <scope>provided</scope>
        </dependency>
         <dependency>
            <groupId>org.apache.felix</groupId>
            <artifactId>org.apache.felix.scr</artifactId>
            <version>1.6.1-R1236132</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
            <groupId>org.apache.sling</groupId>
            <artifactId>org.apache.sling.jcr.api</artifactId>
            <version>2.0.4</version>
        </dependency>
        <dependency>
            <groupId>com.adobe.granite</groupId>
            <artifactId>com.adobe.granite.jmx</artifactId>
            <version>0.1.6</version>
            <scope>provided</scope>
        </dependency>
        <dependency>
       <groupId>com.day.cq.wcm</groupId>
       <artifactId>cq-wcm-mobile-api</artifactId>
       <version>5.5.2</version>
       <scope>provided</scope>
      </dependency>
      <dependency>
       <groupId>com.day.cq.workflow</groupId>
       <artifactId>cq-workflow-api</artifactId>
       <version>5.5.0</version>
       <scope>provided</scope>
      </dependency>
      <dependency>
       <groupId>javax.jcr</groupId>
       <artifactId>jcr</artifactId>
       <version>2.0</version>
       <scope>provided</scope>
      </dependency>
      <dependency>
                <groupId>org.slf4j</groupId>
  <artifactId>slf4j-api</artifactId>
  <version>1.6.4</version>
  <scope>provided</scope>
 </dependency>
    </dependencies>
</project>
```

Voeg het volgende profiel toe aan het instellingenbestand van uw image om de opslagplaats voor openbare Adoben te gebruiken.

#### Geweven profiel {#maven-profile}

```xml
<profile>
    <id>adobe-public</id>
    <activation>
         <activeByDefault>false</activeByDefault>
    </activation>
    <properties>
         <releaseRepository-Id>adobe-public-releases</releaseRepository-Id>
         <releaseRepository-Name>Adobe Public Releases</releaseRepository-Name>
         <releaseRepository-URL>https://repo1.maven.org/maven2/com/adobe/</releaseRepository-URL>
    </properties>
    <repositories>
         <repository>
             <id>adobe-public-releases</id>
             <name>Adobe  Public Repository</name>
             <url>https://repo1.maven.org/maven2/com/adobe/</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </repository>
     </repositories>
     <pluginRepositories>
         <pluginRepository>
             <id>adobe-public-releases</id>
             <name>Adobe Public Repository</name>
             <url>https://repo1.maven.org/maven2/com/adobe/</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </pluginRepository>
     </pluginRepositories>
</profile>
```
