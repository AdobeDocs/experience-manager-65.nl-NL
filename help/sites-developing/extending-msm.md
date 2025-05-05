---
title: Het beheer van meerdere sites uitbreiden
description: Met deze pagina kunt u de functionaliteit van de beheer van meerdere sites uitbreiden
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
exl-id: bba64ce6-8b74-4be1-bf14-cfdf3b9b60e1
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2444'
ht-degree: 0%

---

# Het beheer van meerdere sites uitbreiden{#extending-the-multi-site-manager}

Met deze pagina kunt u de functionaliteit van het beheer van meerdere sites uitbreiden:

* Leer meer over de belangrijkste leden van de MSM Java API.
* Creeer een synchronisatieactie die in een rollout configuratie kan worden gebruikt.
* Wijzig de standaardtaal en landcodes.

<!-- * Remove the "Chapters" step in the Create Site wizard. -->

>[!NOTE]
>
>Deze pagina zou samen met [ het Hergebruiken Inhoud moeten worden gelezen: De multi Manager van de Plaats ](/help/sites-administering/msm.md).
>
>De volgende onderdelen van de herstructurering van de effectenbewaarinstelling zouden ook van belang kunnen zijn:
>* [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/sites-repository-restructuring-in-aem-6-5.html#multi-site-manager-blueprint-configurations) de Configuraties van de Vervaging van de Manager van 0&rbrace; multi-plaats
>* [ de Configuraties van de Output van de Manager van de Multisite ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/sites-repository-restructuring-in-aem-6-5.html#multi-site-manager-rollout-configurations)

>[!CAUTION]
>
>De beheer van meerdere sites en de bijbehorende API worden gebruikt bij het ontwerpen van een website. Ze zijn dus alleen bedoeld voor gebruik in een auteursomgeving.

## Overzicht van de Java API {#overview-of-the-java-api}

Beheer van meerdere sites bestaat uit de volgende pakketten:

* [ com.day.cq.wcm.msm.api ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [ com.day.cq.wcm.msm.commons ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

De belangrijkste voorwerpen MSM API in wisselwerking als volgt (zie ook [ Gebruikte Termen ](/help/sites-administering/msm.md#terms-used)):

![ HoofdMSM API voorwerpen ](assets/chlimage_1-73.png)

* **`Blueprint`**

  A `Blueprint` (zoals in [ blauwdrukconfiguratie ](/help/sites-administering/msm.md#source-blueprints-and-blueprint-configurations)) specificeert de pagina&#39;s waarvan een levend exemplaar inhoud kan erven.

  ![ Vervaging ](assets/chlimage_1-74.png)

   * Het gebruik van een blauwdrukconfiguratie ( `Blueprint`) is optioneel, maar:

      * Staat de auteur toe om de **optie van de Uitvoer** op de bron (aan (uitdrukkelijk) duw wijzigingen aan levende exemplaren te gebruiken die van deze bron erven).
      * Staat de auteur toe om **te gebruiken creeer Plaats**; dit staat de gebruiker toe om talen gemakkelijk te selecteren en de structuur van het levende exemplaar te vormen.
      * Bepaalt de standaardrollout configuratie voor om het even welke resulterende levende exemplaren.

* **`LiveRelationship`**

  In `LiveRelationship` wordt de verbinding (relatie) aangegeven tussen een bron in de actieve kopieervertakking en de equivalente bron/blauwdrukbron.

   * De relaties worden gebruikt bij het realiseren van overerving en rollout.
   * `LiveRelationship` -objecten bieden toegang (verwijzingen) tot de implementatieconfiguraties ( `RolloutConfig` ), `LiveCopy` en `LiveStatus` -objecten die betrekking hebben op de relatie.

   * Er wordt bijvoorbeeld in `/content/copy/us` een live kopie gemaakt van de bron/blauwdruk op `/content/we-retail/language-masters` . De bronnen `/content/we.retail/language-masters/en/jcr:content` en `/content/copy/us/en/jcr:content` vormen een relatie.

* **`LiveCopy`**

  `LiveCopy` bevat de configuratiedetails voor de relaties ( `LiveRelationship` ) tussen de bronnen van de livekopie en hun bron-/blauwdrukbronnen.

   * Met de klasse `LiveCopy` hebt u toegang tot het pad van de pagina, het pad van de bron-/blauwdrukpagina, de rollout-configuraties en of onderliggende pagina&#39;s ook in de `LiveCopy` worden opgenomen.

   * Een `LiveCopy` knoop wordt gecreeerd telkens als **Plaats** creeert of **Levende Exemplaar** wordt gebruikt tot stand brengen.

* **`LiveStatus`**

  `LiveStatus` -objecten bieden toegang tot de runtimestatus van een `LiveRelationship` . Wordt gebruikt om de synchronisatiestatus van een live kopie te controleren.

* **`LiveAction`**

  Een `LiveAction` is een handeling die wordt uitgevoerd op elke bron die bij de rollout is betrokken.

   * LiveActions wordt slechts geproduceerd door RolloutConfigs.

* **`LiveActionFactory`**

  Maakt `LiveAction` -objecten op basis van een `LiveAction` -configuratie. Configuraties worden opgeslagen als bronnen in de opslagplaats.

* **`RolloutConfig`**

  `RolloutConfig` bevat een lijst met `LiveActions` die moet worden gebruikt wanneer deze wordt geactiveerd. `LiveCopy` erft `RolloutConfig` en het resultaat is aanwezig in `LiveRelationship` .

   * Voor het eerst dat een live kopie wordt ingesteld, wordt ook een RolloutConfig gebruikt (die de LiveActions activeert).

## Nieuwe synchronisatiehandeling maken {#creating-a-new-synchronization-action}

Creeer de acties van de douanesynchronisatie om met uw rollout configuraties te gebruiken. Creeer een synchronisatieactie wanneer de [ geïnstalleerde acties ](/help/sites-administering/msm-sync.md#installed-synchronization-actions) niet aan uw specifieke toepassingsvereisten voldoen. Hiertoe maakt u twee klassen:

* Een implementatie van de [`com.day.cq.wcm.msm.api.LiveAction` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveAction.html) interface die de actie uitvoert.
* Een component OSGI die de [`com.day.cq.wcm.msm.api.LiveActionFactory` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) interface uitvoert en instanties van uw `LiveAction` klasse leidt.

In `LiveActionFactory` worden instanties van de klasse `LiveAction` voor een bepaalde configuratie gemaakt:

* `LiveAction` -klassen bevatten de volgende methoden:

   * `getName`: retourneert de naam van de handeling. De naam wordt gebruikt om naar de actie, bijvoorbeeld, in rollout configuraties te verwijzen.
   * `execute` : voert de taken van de handeling uit.

* `LiveActionFactory` -klassen zijn onder andere de volgende leden:

   * `LIVE_ACTION_NAME`: Een veld dat de naam van de gekoppelde `LiveAction` bevat. Deze naam moet overeenkomen met de waarde die wordt geretourneerd door de methode `getName` van de klasse `LiveAction` .

   * `createAction`: hiermee maakt u een instantie van de lus `LiveAction` . De optionele parameter `Resource` kan worden gebruikt om configuratiegegevens op te geven.

   * `createsAction`: retourneert de naam van de gekoppelde `LiveAction` .

### De LiveAction Configuration-node openen {#accessing-the-liveaction-configuration-node}

Gebruik het configuratieknooppunt `LiveAction` in de opslagplaats om informatie op te slaan die het runtimegedrag van de instantie `LiveAction` beïnvloedt. Het knooppunt in de opslagplaats dat de `LiveAction` -configuratie opslaat, is tijdens runtime beschikbaar voor het `LiveActionFactory` -object. Daarom kunt u eigenschappen aan de configuratieknooppunt aan toevoegen en hen in uw `LiveActionFactory` implementatie gebruiken zoals nodig.

Een `LiveAction` moet bijvoorbeeld de naam van de auteur van het concept opslaan. Een bezit van de configuratieknoop omvat de bezitsnaam van de blauwdruk pagina die de informatie opslaat. Tijdens runtime haalt `LiveAction` de eigenschapnaam uit de configuratie op en verkrijgt vervolgens de eigenschapswaarde.

De parameter van de methode [`LiveActionFactory.createAction` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) is een `Resource` -object. Dit `Resource` voorwerp vertegenwoordigt de `cq:LiveSyncAction` knoop voor deze levende actie in de rollout configuratie; zie [ Creërend een Configuratie van de Output ](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration). Zoals gebruikelijk wanneer het gebruiken van een configuratieknoop, zou u het aan een voorwerp `ValueMap` moeten aanpassen:

```java
public LiveAction createAction(Resource resource) throws WCMException {
        ValueMap config;
        if (resource == null || resource.adaptTo(ValueMap.class) == null) {
            config = new ValueMapDecorator(Collections.<String, Object>emptyMap());
        } else {
            config = resource.adaptTo(ValueMap.class);
        }
        return new MyLiveAction(config, this);
}
```

### Toegang krijgen tot doelknooppunten, Source-knooppunten en de LiveRelationship {#accessing-target-nodes-source-nodes-and-the-liverelationship}

De volgende objecten worden opgegeven als parameters van de methode `execute` van het object `LiveAction` :

* Een [`Resource` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/sling/api/resource/Resource.html) voorwerp dat de bron van Levende Exemplaar vertegenwoordigt.
* Een `Resource` -object dat het doel van de actieve kopie vertegenwoordigt.
* Het [`LiveRelationship` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) voorwerp voor het levende exemplaar.
* De `autoSave` -waarde geeft aan of de `LiveAction` wijzigingen moet opslaan die in de gegevensopslagruimte zijn aangebracht.

* De reset-waarde geeft de rollout reset-modus aan.

Met deze objecten kunt u alle informatie over de `LiveCopy` opvragen. U kunt de `Resource` -objecten ook gebruiken om `ResourceResolver` -, `Session` - en `Node` -objecten te verkrijgen. Deze objecten zijn handig voor het bewerken van inhoud in opslagruimten:

In de eerste regel van de volgende code is de bron het `Resource` -object van de bronpagina:

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>De `Resource` argumenten kunnen `null` of `Resources` objecten zijn die zich niet aanpassen aan `Node` -objecten, zoals [`NonExistingResource` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/org/apache/sling/api/resource/NonExistingResource.html) -objecten.

## Een nieuwe rollout-configuratie maken {#creating-a-new-rollout-configuration}

Maak een rollout-configuratie wanneer de geïnstalleerde rollout-configuraties niet voldoen aan de toepassingsvereisten:

* [ creeer de rollout configuratie ](#create-the-rollout-configuration).
* [ voegt synchronisatieacties aan de rollout configuratie ](#add-synchronization-actions-to-the-rollout-configuration) toe.

De nieuwe rollout configuratie is dan beschikbaar aan u wanneer het plaatsen van rollout configuraties op een blauwdruk of een levende exemplaarpagina.

>[!NOTE]
>
>Zie ook de [ beste praktijken voor het aanpassen van rollouts ](/help/sites-administering/msm-best-practices.md#customizing-rollouts).

### De configuratie van de rollout maken {#create-the-rollout-configuration}

1. Open CRXDE Lite, bijvoorbeeld:
   [ http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Navigeren naar:
   `/apps/msm/<your-project>/rolloutconfigs`

   >[!NOTE]
   >Dit is de aangepaste versie van uw project van:
   >`/libs/msm/wcm/rolloutconfigs`
   >Als dit uw eerste configuratie is, moet deze `/libs` tak als malplaatje worden gebruikt om de nieuwe tak onder `/apps` tot stand te brengen.

   >[!NOTE]
   >
   >Wijzig niets in het `/libs` -pad.
   >De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >* Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
   >* Breng eventuele wijzigingen aan binnen `/apps`

1. Onder dit **creeer** een knoop met de volgende eigenschappen:

   * **Naam**: De knoopnaam van de rollout configuratie. md#installed-synchronization-actions), bijvoorbeeld `contentCopy` of `workflow` .
   * **Type**: `cq:RolloutConfig`

1. Voeg de volgende eigenschappen toe aan dit knooppunt:
   * **Naam**: `jcr:title`

     **Type**: `String`
     **Waarde**: Een het identificeren titel die in UI zal verschijnen.
   * **Naam**: `jcr:description`

     **Type**: `String`
     **Waarde**: Een facultatieve beschrijving.
   * **Naam**: `cq:trigger`

     **Type**: `String`
     **Waarde**: De [ Trigger van de Uitvoer ](/help/sites-administering/msm-sync.md#rollout-triggers) om worden gebruikt. Selecteren uit:
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. Klik **sparen allen**.

### Synchronisatiehandelingen toevoegen aan de configuratie van de rollout {#add-synchronization-actions-to-the-rollout-configuration}

De configuraties van de rollout worden opgeslagen onder de [ knoop van de rollout configuratie ](#create-the-rollout-configuration) die u onder `/apps/msm/<your-project>/rolloutconfigs` knoop hebt gecreeerd.

Voeg onderliggende knooppunten van het type `cq:LiveSyncAction` toe om synchronisatiehandelingen toe te voegen aan de rollout-configuratie. De volgorde van de actieknooppunten voor synchronisatie bepaalt de volgorde waarin de acties plaatsvinden.

1. Nog in CRXDE Lite, selecteer uw [&#128279;](#create-the-rollout-configuration) knoop van de Configuratie van 0&rbrace; Uitvoer &lbrace;.

   Bijvoorbeeld:
   `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`

1. **creeer** een knoop met de volgende knoopeigenschappen:

   * **Naam**: De knoopnaam van de synchronisatieactie.
De naam moet het zelfde zijn zoals de **Naam van de Actie** in de lijst onder [ de Acties van de Synchronisatie ](/help/sites-administering/msm-sync.md#installed-synchronization-actions), bijvoorbeeld, `contentCopy` of `workflow`.
   * **Type**: `cq:LiveSyncAction`

1. Voeg en vorm zo vele knopen van de synchronisatieactie toe aangezien u vereist. Wijzig de rangschikking van de actieknoppen zodat de volgorde overeenkomt met de volgorde waarin u deze wilt uitvoeren. Het bovenste actieknooppunt komt eerst voor.

## Een eenvoudige LiveActionFactory-klasse maken en gebruiken {#creating-and-using-a-simple-liveactionfactory-class}

Volg de procedures in deze sectie om een `LiveActionFactory` te ontwikkelen en het in een rollout configuratie te gebruiken. De procedures gebruiken Maven en Eclipse om `LiveActionFactory` te ontwikkelen en op te stellen:

1. [ creeer het geleide project ](#create-the-maven-project) en voer het in Eclipse in.
1. [ voegt gebiedsdelen ](#add-dependencies-to-the-pom-file) aan het POM- dossier toe.
1. [ voert `LiveActionFactory` interface ](#implement-liveactionfactory) uit en stelt de bundel OSGi op.
1. [ creeer de rollout configuratie ](#create-the-example-rollout-configuration).
1. [ creeer het levende exemplaar ](#create-the-live-copy).

Het Maven-project en de broncode van de Java-klasse zijn beschikbaar in de openbare Git-opslagplaats.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ Open ervaring-java-msmrollout project op GitHub ](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout/archive/master.zip)

### Maven {#create-the-maven-project}

Voor de volgende procedure is het vereist dat u het adobe-public profiel hebt toegevoegd aan het Maven-instellingenbestand.

* Voor informatie over het adobe-openbare profiel, zie [ het Verkrijgen van het Pakket van de Inhoud Gemaakte Insteekmodule ](/help/sites-developing/vlt-mavenplugin.md#obtaining-the-content-package-maven-plugin)
* Voor informatie over het GeMaven montagesdossier, zie de Gemaakt [ Verwijzing van Montages ](https://maven.apache.org/settings.html).

1. Open een terminal- of opdrachtregelsessie en wijzig de directory om te wijzen naar de locatie waar u het project wilt maken.
1. Voer de volgende opdracht in:

   ```xml
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. Geef de volgende waarden op bij interactieve prompt:

   * `groupId`: `com.adobe.example.msm`
   * `artifactId`: `MyLiveActionFactory`
   * `version`: `1.0-SNAPSHOT`
   * `package`: `MyPackage`
   * `appsFolderName`: `myapp`
   * `artifactName`: `MyLiveActionFactory package`
   * `packageGroup`: `myPackages`

1. De Verduistering van het begin en [ voeren het Geweven project ](/help/sites-developing/howto-projects-eclipse.md#import-the-maven-project-into-eclipse) in.

### Afhankelijkheden toevoegen aan het POM-bestand {#add-dependencies-to-the-pom-file}

Voeg gebiedsdelen toe zodat de compiler van de Verduistering de klassen kan van verwijzingen voorzien die in de `LiveActionFactory` code worden gebruikt.

1. Open het bestand in Eclipse Project Explorer:

   `MyLiveActionFactory/pom.xml`

1. Klik in de editor op de tab `pom.xml` en zoek de sectie `project/dependencyManagement/dependencies` .
1. Voeg de volgende XML toe in het `dependencyManagement` -element en sla het bestand op.

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
     <version>5.6.2</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
     <version>2.4.3-R1488084</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
     <version>5.6.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
     <version>2.0.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
     <version>2.0.0</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
   ```

1. Open het POM- dossier voor de bundel van **Ontdekkingsreiziger van het Project** bij `MyLiveActionFactory-bundle/pom.xml`.
1. Klik in de editor op de tab `pom.xml` en zoek de sectie project/afhankelijkheden. Voeg de volgende XML binnen het gebiedsdeelelement toe en bewaar dan het dossier:

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
   ```

### LiveActionFactory implementeren {#implement-liveactionfactory}

De volgende `LiveActionFactory` -klasse implementeert een `LiveAction` -klasse die berichten over de bron- en doelpagina&#39;s registreert, en kopieert de eigenschap `cq:lastModifiedBy` van het bronknooppunt naar het doelknooppunt. De naam van de live actie is `exampleLiveAction` .

1. In de Ontdekkingsreiziger van het Project Eclipse, klik het `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm` pakket met de rechtermuisknop aan en klik **Nieuw** > **Klasse**. Voor de **Naam**, ga `ExampleLiveActionFactory` in en klik dan **Afwerking**.
1. Open het `ExampleLiveActionFactory.java` -bestand, vervang de inhoud door de volgende code en sla het bestand op.

   ```java
   package com.adobe.example.msm;
   
   import java.util.Collections;  
   
   import com.day.cq.wcm.api.NameConstants;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.resource.ResourceResolver;
   import org.apache.sling.api.resource.ValueMap;
   import org.apache.sling.api.wrappers.ValueMapDecorator;
   import org.apache.sling.commons.json.io.JSONWriter;
   import org.apache.sling.commons.json.JSONException;
   
   import org.osgi.service.component.annotations.Component;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   
   import com.day.cq.wcm.msm.api.ActionConfig;
   import com.day.cq.wcm.msm.api.LiveAction;
   import com.day.cq.wcm.msm.api.LiveActionFactory;
   import com.day.cq.wcm.msm.api.LiveRelationship;
   import com.day.cq.wcm.api.WCMException;
   
   @Component(
   service = LiveActionFactory.class,
   property = {LiveActionFactory.LIVE_ACTION_NAME + "=" + ExampleLiveActionFactory.LIVE_ACTION_NAME})
   public class ExampleLiveActionFactory implements LiveActionFactory<LiveAction> {
     private static final Logger logger = LoggerFactory.getLogger(ExampleLiveActionFactory.class);
   
     public static final String LIVE_ACTION_NAME = "CustomAction";
   
     public LiveAction createAction(Resource config) {
       ValueMap configs;
       /* Adapt the config resource to a ValueMap */
       if (config == null || config.adaptTo(ValueMap.class) == null) {
         configs = new ValueMapDecorator(Collections.<String, Object>emptyMap());
       } else {
         configs = config.adaptTo(ValueMap.class);
       }  
   
       return new ExampleLiveAction(LIVE_ACTION_NAME, configs);
     }
     public String createsAction() {
       return LIVE_ACTION_NAME;
     }  
   
     /************* LiveAction ****************/
     private static class ExampleLiveAction implements LiveAction {
       private String name;
       private ValueMap configs;
       private static final Logger log = LoggerFactory.getLogger(ExampleLiveAction.class);  
   
     public ExampleLiveAction(String nm, ValueMap config){
       name = nm;
       configs = config;
     }  
   
     public void execute(Resource source, Resource target,
                         LiveRelationship liverel, boolean autoSave, boolean isResetRollout)
                       throws WCMException {  
   
       String lastMod = null;  
   
       log.info(" *** Executing ExampleLiveAction *** ");  
   
       /* Determine if the LiveAction is configured to copy the cq:lastModifiedBy property */
       if ((Boolean) configs.get("repLastModBy")){  
   
         /* get the source's cq:lastModifiedBy property */
         if (source != null && source.adaptTo(Node.class) !=  null){
           ValueMap sourcevm = source.adaptTo(ValueMap.class);
           lastMod = sourcevm.get(NameConstants.PN_PAGE_LAST_MOD_BY, String.class);
         }  
   
         /* set the target node's la-lastModifiedBy property */
         Session session = null;
         if (target != null && target.adaptTo(Node.class) !=  null){
           ResourceResolver resolver = target.getResourceResolver();
           session = resolver.adaptTo(javax.jcr.Session.class);
           Node targetNode;
           try{
             targetNode=target.adaptTo(javax.jcr.Node.class);
             targetNode.setProperty("la-lastModifiedBy", lastMod);
             log.info(" *** Target node lastModifiedBy property updated: {} ***",lastMod);
           }catch(Exception e){
             log.error(e.getMessage());
           }
         }
         if(autoSave){
           try {
             session.save();
           } catch (Exception e) {
             try {
               session.refresh(true);
             } catch (RepositoryException e1) {
               e1.printStackTrace();
             }
             e.printStackTrace();
           }
         }
       }
     }
     public String getName() {
       return name;
     }  
   
     /************* Deprecated *************/
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
                        ActionConfig arg2, boolean arg3) throws WCMException {
     }
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
                         ActionConfig arg2, boolean arg3, boolean arg4)
                       throws WCMException {
     }
     @Deprecated
     public String getParameterName() {
       return null;
     }
     @Deprecated
       public String[] getPropertiesNames() {
         return null;
     }
     @Deprecated
     public int getRank() {
       return 0;
     }
     @Deprecated
     public String getTitle() {
       return null;
     }
     @Deprecated
     public void write(JSONWriter arg0) throws JSONException {
     }
   }
   ```

1. Wijzig met de terminal- of opdrachtsessie de map in de map `MyLiveActionFactory` (de map Maven project). Voer vervolgens de volgende opdracht in:

   ```shell
   mvn -PautoInstallPackage clean install
   ```

   Het bestand AEM `error.log` moet aangeven dat de bundel is gestart.

   Bijvoorbeeld, [ https://localhost:4502/system/console/status-slinglogs ](https://localhost:4502/system/console/status-slinglogs).

   ```xml
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### De voorbeeldconfiguratie voor rollout maken {#create-the-example-rollout-configuration}

Creeer de MSM rollout configuratie die `LiveActionFactory` gebruikt die u creeerde:

1. Creeer en configuratie a [ Configuratie van de Uitvoer met de standaardprocedure ](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) - en het gebruiken van de eigenschappen:

   * **Titel**: De Configuratie van de Uitvoer van het voorbeeld
   * **Naam**: examplerolloutconfig
   * **cq:trigger**: `publish`

### Voeg de Actieve Actie aan de Configuratie van de Uitvoer van het Voorbeeld toe {#add-the-live-action-to-the-example-rollout-configuration}

Vorm de rollout configuratie die u in de vorige procedure creeerde zodat het de `ExampleLiveActionFactory` klasse gebruikt.

1. Open CRXDE Lite; bijvoorbeeld, [ https://localhost:4502/crx/de ](https://localhost:4502/crx/de).
1. Maak het volgende knooppunt onder `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content` :

   * **Naam**: `exampleLiveAction`
   * **Type**: `cq:LiveSyncAction`

1. Klik **sparen allen**.
1. Selecteer het knooppunt `exampleLiveAction` en voeg de volgende eigenschap toe:

   * **Naam**: `repLastModBy`
   * **Type**: `Boolean`
   * **Waarde**: `true`

   Deze eigenschap geeft aan de klasse `ExampleLiveAction` aan dat de eigenschap `cq:LastModifiedBy` moet worden gerepliceerd van de bron naar het doelknooppunt.

1. Klik **sparen allen**.

### Live kopie maken {#create-the-live-copy}

[ creeer een levend exemplaar ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) van de Engelse/Producten tak van de Plaats van de Verwijzing Wij.Retail gebruikend uw rollout configuratie:

* **Source**: `/content/we-retail/language-masters/en/products`

* **Configuratie van de Uitvoer**: De Configuratie van de Uitvoer van het voorbeeld

Activeer de **Produkten** (Engelse) pagina van de brontak en neem de logboekberichten waar die de `LiveAction` klasse produceert:

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

<!--
## Removing the Chapters Step in the Create Site Wizard {#removing-the-chapters-step-in-the-create-site-wizard}

In some cases, the **Chapters** selection is not required in the create site wizard (only the **Languages** selection is required). To remove this step in the default We.Retail English blueprint:

1. In CRX Explorer, remove the node:
   `/etc/blueprints/weretail-english/jcr:content/dialog/items/tabs/items/tab_chap`.

1. Navigate to `/libs/wcm/msm/templates/blueprint/defaults/livecopy_tab/items` and create a node:

    1. **Name** = `chapters`; **Type** = `cq:Widget`.

1. Add following properties to the new node:

    1. **Name** = `name`; **Type** = `String`; **Value** = `msm:chapterPages`

    1. **Name** = `value`; **Type** = `String`; **Value** = `all`

    1. **Name** = `xtype`; **Type** = `String`; **Value** = `hidden`
-->

## Taalnamen en standaardlanden wijzigen {#changing-language-names-and-default-countries}

AEM gebruikt een standaardset taal- en landcodes.

* De standaardtaalcode is de tweeletterige code in kleine letters, zoals gedefinieerd door ISO-639-1.
* De standaardlandcode is de tweelettercode in kleine letters of hoofdletters, zoals gedefinieerd in ISO 3166.

MSM gebruikt een opgeslagen lijst van taal en landcodes om de naam van het land te bepalen dat met de naam van de taalversie van uw pagina wordt geassocieerd. U kunt de volgende aspecten van de lijst indien nodig wijzigen:

* Taaltitels
* Landnamen
* Standaardlanden voor talen (bijvoorbeeld voor codes zoals `en` en `de` )

De taallijst wordt opgeslagen onder het knooppunt `/libs/wcm/core/resources/languages` . Elk onderliggend knooppunt vertegenwoordigt een taal of een taal-land:

* De naam van het knooppunt is de taalcode (zoals `en` of `de` ) of de taalcode (zoals `en_us` of `de_ch` ).

* De eigenschap `language` van het knooppunt slaat de volledige naam van de taal voor de code op.
* In de eigenschap `country` van het knooppunt wordt de volledige naam van het land voor de code opgeslagen.
* Wanneer de knooppuntnaam alleen uit een taalcode bestaat (zoals `en` ), is de landeigenschap `*` en slaat een extra `defaultCountry` -eigenschap de code van het taal-land op om het land aan te geven dat moet worden gebruikt.

![ de definitie van de Taal ](assets/chlimage_1-76.png)

De talen wijzigen:

1. Open CRXDE Lite in uw Webbrowser; bijvoorbeeld, [ https://localhost:4502/crx/de ](https://localhost:4502/crx/de)
1. Selecteer de `/apps` omslag en klik **creeer**, dan **creeer Omslag.**

   Geef de nieuwe map een naam `wcm` .

1. Herhaal de vorige stap om de mappenstructuur `/apps/wcm/core` te maken. Maak een knooppunt van het type `sling:Folder` in `core` called `resources` . <!-- ![Resources](assets/chlimage_1-77.png) -->

1. Klik de `/libs/wcm/core/resources/languages` knoop met de rechtermuisknop aan en klik **Exemplaar**.
1. Klik met de rechtermuisknop op de `/apps/wcm/core/resources` map en klik op **Plakken** . Wijzig de onderliggende knooppunten naar wens.
1. Klik **sparen allen**.
1. Klik **Hulpmiddelen**, **Verrichtingen** toen **Console van het Web**. Van deze console klik **OSGi**, toen **Configuratie**.
1. Bepaal de plaats en klik {de Manager van de Taal van 0} Dag CQ WCM **, en verander de waarde van** Lijst van de Taal **aan `/apps/wcm/core/resources/languages`, dan klik** sparen **.**

   {de Manager van de Taal van 0} Dag CQ WCM ![&#128279;](assets/chlimage_1-78.png)

## MSM-vergrendelingen configureren op pagina-eigenschappen (interface met aanraakbediening) {#configuring-msm-locks-on-page-properties-touch-enabled-ui}

Wanneer u een aangepaste pagina-eigenschap maakt, moet u mogelijk overwegen of de nieuwe eigenschap kan worden geïmplementeerd voor live kopieën.

Als bijvoorbeeld twee nieuwe pagina-eigenschappen worden toegevoegd:

* E-mailadres contactpersoon:

   * Deze eigenschap hoeft niet te worden uitgevoerd, omdat deze in elk land (of merk, enzovoort) anders zal zijn.

* Belangrijke visuele stijl:

   * Het projectvereiste is dat dit eigendom wordt uitgevoerd zoals het (gewoonlijk) voor alle landen (of merken, enzovoort) gemeenschappelijk is.

Daarna moet u ervoor zorgen dat:

* E-mailadres contactpersoon:

* Is uitgesloten van de opgerold uit eigenschappen; zie [ Uitsluitend Eigenschappen en de Types van Knoop van Synchronisatie ](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization).

* Belangrijke visuele stijl:

* Zorg ervoor dat u deze eigenschap niet mag bewerken in de interface met aanraakbediening, tenzij de overerving wordt geannuleerd, en dat u de overerving vervolgens opnieuw kunt installeren. Dit wordt geregeld door op de ketting-/verbroken-kettingkoppelingen te klikken die in- en uitschakelen om de status van de verbinding aan te geven.

Of een pagina-eigenschap moet worden geïmplementeerd en, afhankelijk van het annuleren/opnieuw installeren van overerving tijdens het bewerken, wordt dan gecontroleerd door de dialoogvenster-eigenschap:

* `cq-msm-lockable`

   * is van toepassing op items in een interface-dialoogvenster met aanraakbediening
   * maakt het kettingkoppelingssymbool in het dialoogvenster
   * is alleen bewerken toegestaan als overerving is geannuleerd (de ketting-koppeling is verbroken)
   * alleen van toepassing op het eerste onderliggende niveau van de bron
      * **Type**: `String`

      * **Waarde**: houdt de naam van het bezit in overweging (en is vergelijkbaar met de waarde van het bezit `name`; bijvoorbeeld, zie

        `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

Wanneer `cq-msm-lockable` is gedefinieerd, wordt de interactie tussen het verbreken en sluiten van de keten en MSM als volgt uitgevoerd:

* als de waarde van `cq-msm-lockable` is:

   * **Relatief** (bijvoorbeeld, `myProperty` of `./myProperty`)

      * de eigenschap wordt toegevoegd en verwijderd uit `cq:propertyInheritanceCancelled` .

   * **Absolute** (bijvoorbeeld, `/image`)

      * Als u de keten breekt, wordt de overerving geannuleerd door de `cq:LiveSyncCancelled` mix toe te voegen aan `./image` en `cq:isCancelledForChildren` in te stellen op `true` .

      * als de keten wordt gesloten , wordt de overerving hersteld .

>[!NOTE]
>
>`cq-msm-lockable` is van toepassing op het eerste onderliggende niveau van de bron die moet worden bewerkt en is niet functioneel op voorouders van een dieper niveau, ongeacht of de waarde als absoluut of relatief is gedefinieerd.

>[!NOTE]
>
>Wanneer u overerving opnieuw inschakelt, wordt de pagina-eigenschap voor live kopiëren niet automatisch gesynchroniseerd met de eigenschap source. U kunt handmatig een synchronisatie aanvragen als dit vereist is.
