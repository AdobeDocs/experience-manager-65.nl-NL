---
title: Het beheer van meerdere sites uitbreiden
seo-title: Het beheer van meerdere sites uitbreiden
description: Met deze pagina kunt u de functionaliteit van de beheer van meerdere sites uitbreiden
seo-description: Met deze pagina kunt u de functionaliteit van de beheer van meerdere sites uitbreiden
uuid: dfa7d050-29fc-4401-8d4d-d6ace6b49bea
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6128c91a-4173-42b4-926f-bbbb2b54ba5b
docset: aem65
translation-type: tm+mt
source-git-commit: 3a1d02fc1bc561b54e57cf91abc8f4406ba8c365
workflow-type: tm+mt
source-wordcount: '2601'
ht-degree: 0%

---


# Het uitbreiden van de Manager van de MultiPlaats{#extending-the-multi-site-manager}

Met deze pagina kunt u de functionaliteit van het beheer van meerdere sites uitbreiden:

* Leer meer over de belangrijkste leden van de MSM Java API.
* Creeer een nieuwe synchronisatieactie die in een rollout configuratie kan worden gebruikt.
* Wijzig de standaardtaal en landcodes.

<!-- * Remove the "Chapters" step in the Create Site wizard. -->

>[!NOTE]
>
>Deze pagina moet worden gelezen in combinatie met [Inhoud opnieuw gebruiken: Beheer van meerdere sites](/help/sites-administering/msm.md).
>
>De volgende onderdelen van de herstructurering van de effectenbewaarinstellingen in AEM 6.4 zouden ook van belang kunnen zijn:
>* [Configuraties van blauwdruk voor beheer op meerdere locaties](https://docs.adobe.com/content/help/en/experience-manager-64/deploying/restructuring/sites-repository-restructuring-in-aem-6-4.html#multi-site-manager-blueprint-configurations)
>* [Uitrolconfiguraties voor beheer op meerdere locaties](https://docs.adobe.com/content/help/en/experience-manager-64/deploying/restructuring/sites-repository-restructuring-in-aem-6-4.html#multi-site-manager-rollout-configurations)


>[!CAUTION]
>
>De beheer van meerdere sites en de bijbehorende API worden gebruikt bij het ontwerpen van een website. Ze zijn dus alleen bedoeld voor gebruik in een auteursomgeving.

## Overzicht van de Java API {#overview-of-the-java-api}

Beheer van meerdere sites bestaat uit de volgende pakketten:

* [com.day.cq.wcm.msm.api](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [com.day.cq.wcm.msm.commons](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

De belangrijkste MSM API voorwerpen werken als volgt in wisselwerking (zie ook [Gebruikte Termen](/help/sites-administering/msm.md#terms-used)):

![chlimage_1-73](assets/chlimage_1-73.png)

* **`Blueprint`**

   A `Blueprint` (zoals in [blauwdrukconfiguratie](/help/sites-administering/msm.md#source-blueprints-and-blueprint-configurations)) specificeert de pagina&#39;s waarvan een levende kopie inhoud kan erven.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   * Het gebruik van een blauwdrukconfiguratie ( `Blueprint`) is optioneel, maar:

      * Staat de auteur toe om de **optie van de Uitvoer** op de bron (aan (uitdrukkelijk) duw wijzigingen aan levende exemplaren te gebruiken die van deze bron erven).
      * Hiermee kan de auteur **Site maken/> gebruiken. hierdoor kan de gebruiker eenvoudig talen selecteren en de structuur van de live kopie configureren .**
      * Bepaalt de standaardrollout configuratie voor om het even welke resulterende levende exemplaren.

* **`LiveRelationship`** De  `LiveRelationship` opgegeven verbinding (relatie) tussen een bron in de actieve kopieervertakking en de equivalente bron/blauwdrukbron.

   * De relaties worden gebruikt bij het realiseren van overerving en rollout.
   * `LiveRelationship` de voorwerpen verlenen toegang (verwijzingen) tot de rollout configuraties (  `RolloutConfig`),  `LiveCopy`, en  `LiveStatus` voorwerpen met betrekking tot de verhouding.

   * Bijvoorbeeld, wordt een levende exemplaar gecreeerd in `/content/copy/us` van de bron/blauwdruk bij `/content/we-retail/language-masters`. De bronnen `/content/we.retail/language-masters/en/jcr:content` en `/content/copy/us/en/jcr:content` vormen een relatie.

* **`LiveCopy`** `LiveCopy` bevat de configuratiedetails voor de verhoudingen (  `LiveRelationship`) tussen de levende exemplaarmiddelen en hun bron/blauwdruk middelen.

   * Met de klasse `LiveCopy` hebt u toegang tot het pad van de pagina, het pad van de bron-/blauwdrukpagina, de rollout-configuraties en of onderliggende pagina&#39;s ook worden opgenomen in `LiveCopy`.

   * Elke keer dat `LiveCopy` wordt gemaakt, wordt een **Site maken** of **Live kopie maken** gebruikt.

* **`LiveStatus`**

   `LiveStatus` objecten bieden toegang tot de runtimestatus van een  `LiveRelationship`. Wordt gebruikt om de synchronisatiestatus van een live kopie te controleren.

* **`LiveAction`**

   Een `LiveAction` is een actie die op elk middel wordt uitgevoerd dat bij de uitrol betrokken is.

   * LiveActions wordt slechts geproduceerd door RolloutConfigs.

* **`LiveActionFactory`**

   Hiermee maakt u `LiveAction`-objecten op basis van een `LiveAction`-configuratie. Configuraties worden opgeslagen als bronnen in de opslagplaats.

* **`RolloutConfig`** De code  `RolloutConfig` bevat een lijst met  `LiveActions`objecten die moeten worden gebruikt wanneer ze worden geactiveerd. `LiveCopy` erft `RolloutConfig` en het resultaat is aanwezig in `LiveRelationship`.

   * Voor het eerst dat een live kopie wordt ingesteld, wordt ook een RolloutConfig gebruikt (die de LiveActions activeert).

## Nieuwe synchronisatiehandeling maken {#creating-a-new-synchronization-action}

Creeer de acties van de douanesynchronisatie om met uw rollout configuraties te gebruiken. Creeer een synchronisatieactie wanneer [geïnstalleerde acties](/help/sites-administering/msm-sync.md#installed-synchronization-actions) niet aan uw specifieke toepassingsvereisten voldoen. Hiertoe maakt u twee klassen:

* Een implementatie van de [ `com.day.cq.wcm.msm.api.LiveAction`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/LiveAction.html) interface die de actie uitvoert.
* Een component OSGI die de [ `com.day.cq.wcm.msm.api.LiveActionFactory`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) interface uitvoert en instanties van uw `LiveAction` klasse leidt.

Met `LiveActionFactory` maakt u instanties van de klasse `LiveAction` voor een bepaalde configuratie:

* `LiveAction` klassen omvatten de volgende methoden:

   * `getName`: Retourneert de naam van de handeling De naam wordt gebruikt om naar de handeling te verwijzen, bijvoorbeeld in rollout-configuraties.
   * `execute`: Voert de taken van de actie uit.

* `LiveActionFactory` de klassen omvatten de volgende leden:

   * `LIVE_ACTION_NAME`: Een veld dat de naam van de gekoppelde  `LiveAction`. Deze naam moet overeenkomen met de waarde die wordt geretourneerd door de methode `getName` van de klasse `LiveAction`.

   * `createAction`: Maakt een instantie van de  `LiveAction`. De optionele parameter `Resource` kan worden gebruikt om configuratiegegevens op te geven.

   * `createsAction`: Retourneert de naam van de gekoppelde  `LiveAction`.

### Toegang krijgen tot de LiveAction Configuration Node {#accessing-the-liveaction-configuration-node}

Gebruik het `LiveAction` configuratieknooppunt in de repository om informatie op te slaan die het runtimegedrag van de `LiveAction` instantie beïnvloedt. Het knooppunt in de opslagplaats dat de `LiveAction`-configuratie opslaat, is tijdens runtime beschikbaar voor het `LiveActionFactory`-object. Daarom kunt u eigenschappen aan de configuratieknoop toevoegen aan en hen in uw `LiveActionFactory` implementatie gebruiken zoals nodig.

In een `LiveAction` moet bijvoorbeeld de naam van de auteur van de blauwdruk worden opgeslagen. Een bezit van de configuratieknoop omvat de bezitsnaam van de blauwdruk pagina die de informatie opslaat. Tijdens runtime, wint `LiveAction` de bezitsnaam van de configuratie terug, dan verkrijgt de bezitswaarde.

De parameter van de methode ` [LiveActionFactory](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html).createAction` is een `Resource` voorwerp. Dit `Resource` voorwerp vertegenwoordigt de `cq:LiveSyncAction` knoop voor deze levende actie in de rollout configuratie; zie [Een rollout-configuratie maken](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration). Zoals gebruikelijk wanneer het gebruiken van een configuratieknoop, zou u het aan een `ValueMap` voorwerp moeten aanpassen:

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

### Toegang tot doelknooppunten, bronknooppunten en de LiveRelatie {#accessing-target-nodes-source-nodes-and-the-liverelationship}

De volgende objecten worden opgegeven als parameters van de methode `execute` van het object `LiveAction`:

* Een [ `Resource`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html)-object dat de bron van de actieve kopie vertegenwoordigt.
* Een `Resource`-object dat het doel van de actieve kopie vertegenwoordigt.
* Het [ `LiveRelationship`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) voorwerp voor het levende exemplaar.
* De waarde `autoSave` geeft aan of uw `LiveAction` wijzigingen moet opslaan die in de opslagplaats zijn aangebracht.

* De reset-waarde geeft de rollout reset-modus aan.

Van deze voorwerpen kunt u alle informatie over `LiveCopy` verkrijgen. U kunt de `Resource` voorwerpen ook gebruiken om `ResourceResolver`, `Session`, en `Node` voorwerpen te verkrijgen. Deze objecten zijn handig voor het bewerken van inhoud in opslagruimten:

In de eerste regel van de volgende code is de bron het `Resource`-object van de bronpagina:

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>De argumenten `Resource` kunnen `null` of `Resources` voorwerpen zijn die niet aan `Node` voorwerpen, zoals [ `NonExistingResource`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/NonExistingResource.html) voorwerpen aanpassen.

## Nieuwe rollout-configuratie maken {#creating-a-new-rollout-configuration}

Maak een rollout-configuratie wanneer de geïnstalleerde rollout-configuraties niet voldoen aan de toepassingsvereisten:

* [Maak de rollout-configuratie](#create-the-rollout-configuration).
* [Synchronisatiehandelingen toevoegen aan de rollout-configuratie](#add-synchronization-actions-to-the-rollout-configuration).

De nieuwe rollout configuratie is dan beschikbaar aan u wanneer het plaatsen van rollout configuraties op een blauwdruk of een levende exemplaarpagina.

>[!NOTE]
>
>Zie ook de [beste praktijken voor het aanpassen van rollouts](/help/sites-administering/msm-best-practices.md#customizing-rollouts).

### De rollout-configuratie {#create-the-rollout-configuration} maken

Een nieuwe rollout-configuratie maken:

1. Open CRXDE Lite; bijvoorbeeld:
   [http://localhost:4502/crx/de](http://localhost:4502/crx/de)

1. Ga naar :
   `/apps/msm/<your-project>/rolloutconfigs`

   >[!NOTE]
   >Dit is de aangepaste versie van uw project van:
   >`/libs/msm/wcm/rolloutconfigs`
   >Moet worden gecreeerd als dit uw eerste configuratie is.

   >[!NOTE]
   >
   >U moet niets in de /libs weg veranderen.
   >Dit is omdat de inhoud van /libs de volgende tijd wordt beschreven u uw instantie (en kan goed worden beschreven wanneer u of hotfix of eigenschappak toepast) bevordert.
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >* Het vereiste item opnieuw maken (dat wil zeggen zoals het bestaat in /libs) onder /apps
   >* Wijzigingen aanbrengen in /apps


1. Onder deze **Create** een knooppunt met de volgende eigenschappen:

   * **Naam**: De knooppuntnaam van de rollout configuratie. md#installed-synchronization-actions), bijvoorbeeld `contentCopy` of `workflow`.
   * **Type**:  `cq:RolloutConfig`

1. Voeg de volgende eigenschappen toe aan dit knooppunt:
   * **Naam**:  `jcr:title`

      **Type**:  `String`
      **Waarde**: Een identificerende titel die in UI zal verschijnen.
   * **Naam**:  `jcr:description`

      **Type**:  `String`
      **Waarde**: Een optionele beschrijving.
   * **Naam**:  `cq:trigger`

      **Type**:  `String`
      **Waarde**: De  [rollout-](/help/sites-administering/msm-sync.md#rollout-triggers) trigger die moet worden gebruikt. Selecteer  vanuit:
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. Klik **Alles opslaan**.

### Synchronisatiehandelingen toevoegen aan de configuratie {#add-synchronization-actions-to-the-rollout-configuration}

De configuraties van de rollout worden opgeslagen onder [rollout configuratieknooppunt](#create-the-rollout-configuration) die u onder `/apps/msm/<your-project>/rolloutconfigs` knoop hebt gecreeerd.

Voeg onderliggende knooppunten van het type `cq:LiveSyncAction` toe om synchronisatiehandelingen toe te voegen aan de rollout-configuratie. De volgorde van de actieknooppunten voor synchronisatie bepaalt de volgorde waarin de acties plaatsvinden.

1. Stilstaand in CRXDE Lite, selecteer uw [knoop van de Configuratie van de Output](#create-the-rollout-configuration).

   Bijvoorbeeld:
   `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`

1. **Knooppunt** maken met de volgende knoopeigenschappen:

   * **Naam**: De knooppuntnaam van de synchronisatieactie.
De naam moet het zelfde als **Naam van de Actie** in de lijst onder [Synchronisatieacties](/help/sites-administering/msm-sync.md#installed-synchronization-actions), bijvoorbeeld `contentCopy` of `workflow` zijn.
   * **Type**:  `cq:LiveSyncAction`

1. Voeg en vorm zo vele knopen van de synchronisatieactie toe aangezien u vereist. Wijzig de rangschikking van de actieknoppen zodat de volgorde overeenkomt met de volgorde waarin u deze wilt uitvoeren. Het bovenste actieknooppunt komt eerst voor.

## Een eenvoudige LiveActionFactory-klasse {#creating-and-using-a-simple-liveactionfactory-class} maken en gebruiken

Volg de procedures in deze sectie om `LiveActionFactory` te ontwikkelen en het in een rollout configuratie te gebruiken. De procedures gebruiken Maven en Eclipse om `LiveActionFactory` te ontwikkelen en op te stellen:

1. [Maak het gemaakte ](#create-the-maven-project) project en importeer het in Eclipse.
1. [Voeg ](#add-dependencies-to-the-pom-file) afhankelijke elementen toe aan het POM-bestand.
1. [Voer  `LiveActionFactory` ](#implement-liveactionfactory) interface uit en stel de bundel OSGi op.
1. [Maak de rollout-configuratie](#create-the-example-rollout-configuration).
1. [Maak de live kopie](#create-the-live-copy).

Het Maven-project en de broncode van de Java-klasse zijn beschikbaar in de openbare Git-opslagplaats.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open ExperienceManager-java-msmrollout project op GitHub](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout/archive/master.zip)

### Maven van project {#create-the-maven-project}

Voor de volgende procedure is het vereist dat u het adobe-public profiel hebt toegevoegd aan het Maven-instellingenbestand.

* Zie [De insteekmodule Inhoudspakket verkrijgen](/help/sites-developing/vlt-mavenplugin.md#obtaining-the-content-package-maven-plugin) voor informatie over het adobe-public profiel.
* Voor informatie over het Maven montageendossier, zie de Gemaakt [Verwijzing van Montages](https://maven.apache.org/settings.html).

1. Open een terminal- of opdrachtregelsessie en wijzig de directory om te wijzen naar de locatie waar u het project wilt maken.
1. Voer de volgende opdracht in:

   ```xml
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. Geef de volgende waarden op bij interactieve prompt:

   * `groupId`: `com.adobe.example.msm`
   * `artifactId`:  `MyLiveActionFactory`
   * `version`:  `1.0-SNAPSHOT`
   * `package`:  `MyPackage`
   * `appsFolderName`:  `myapp`
   * `artifactName`:  `MyLiveActionFactory package`
   * `packageGroup`:  `myPackages`

1. Start Eclipse en [importeer het Maven-project](/help/sites-developing/howto-projects-eclipse.md#import-the-maven-project-into-eclipse).

### Afhankelijkheden toevoegen aan het POM-bestand {#add-dependencies-to-the-pom-file}

Voeg gebiedsdelen toe zodat de compiler van de Verduistering de klassen kan van verwijzingen voorzien die in `LiveActionFactory` code worden gebruikt.

1. Open het bestand in Eclipse Project Explorer:

   `MyLiveActionFactory/pom.xml`

1. Klik in de editor op het tabblad `pom.xml` en zoek de sectie `project/dependencyManagement/dependencies`.
1. Voeg de volgende XML in het `dependencyManagement` element toe en sla dan het dossier op.

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

1. Open het POM-bestand voor de bundel vanuit **Projectverkenner** op `MyLiveActionFactory-bundle/pom.xml`.
1. In de redacteur, klik `pom.xml` tabel en bepaal de plaats van de project/gebiedsdeel. Voeg de volgende XML binnen het gebiedsdeelelement toe en bewaar dan het dossier:

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

### LiveActionFactory {#implement-liveactionfactory} implementeren

De volgende `LiveActionFactory` klasse voert `LiveAction` uit die berichten over de bron en doelpagina&#39;s registreert, en kopieert het `cq:lastModifiedBy` bezit van de bronknoop aan de doelknoop. De naam van de live actie is `exampleLiveAction`.

1. In de Ontdekkingsreiziger van het Project van de Verduistering, klik `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm` pakket met de rechtermuisknop aan en klik **Nieuw** > **Klasse**. Voor **Naam**, ga `ExampleLiveActionFactory` in en klik dan **Voltooien**.
1. Open het `ExampleLiveActionFactory.java`-bestand, vervang de inhoud door de volgende code en sla het bestand op.

   ```java
   package com.adobe.example.msm;
   
   import java.util.Collections;
   
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.resource.ResourceResolver;
   import org.apache.sling.api.resource.ValueMap;
   import org.apache.sling.api.wrappers.ValueMapDecorator;
   import org.apache.sling.commons.json.io.JSONWriter;
   import org.apache.sling.commons.json.JSONException;
   
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
   
   @Component(metatype = false)
   @Service
   public class ExampleLiveActionFactory implements LiveActionFactory<LiveAction> {
    @Property(value="exampleLiveAction")
    static final String actionname = LiveActionFactory.LIVE_ACTION_NAME;
   
    public LiveAction createAction(Resource config) {
     ValueMap configs;
     /* Adapt the config resource to a ValueMap */
           if (config == null || config.adaptTo(ValueMap.class) == null) {
               configs = new ValueMapDecorator(Collections.<String, Object>emptyMap());
           } else {
               configs = config.adaptTo(ValueMap.class);
           }
   
     return new ExampleLiveAction(actionname, configs);
    }
    public String createsAction() {
     return actionname;
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
        lastMod = sourcevm.get(com.day.cq.wcm.msm.api.MSMNameConstants.PN_PAGE_LAST_MOD_BY, String.class);
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
   }
   ```

1. Gebruikend de terminal of bevelzitting, verander de folder in `MyLiveActionFactory` folder (de Gemaakt projectfolder). Voer vervolgens de volgende opdracht in:

   ```shell
   mvn -PautoInstallPackage clean install
   ```

   Het AEM `error.log` bestand moet aangeven dat de bundel is gestart.

   Bijvoorbeeld [https://localhost:4502/system/console/status-slinglogs](https://localhost:4502/system/console/status-slinglogs).

   ```xml
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### De voorbeeldconfiguratie {#create-the-example-rollout-configuration} maken

Creeer de MSM rollout configuratie die `LiveActionFactory` gebruikt die u creeerde:

1. Creeer en configuratie een [Configuratie van de Output met de standaardprocedure](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) - en het gebruiken van de eigenschappen:

   * **Titel**: Voorbeeld-uitrolconfiguratie
   * **Naam**: voorbeplerolloutconfig
   * **cq:trigger**:  `publish`

### De actieve handeling toevoegen aan de voorbeeldconfiguratie {#add-the-live-action-to-the-example-rollout-configuration}

Vorm de rollout configuratie die u in de vorige procedure creeerde zodat het de `ExampleLiveActionFactory` klasse gebruikt.

1. Open CRXDE Lite; bijvoorbeeld [https://localhost:4502/crx/de](https://localhost:4502/crx/de).
1. Maak het volgende knooppunt onder `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content`:

   * **Naam**:  `exampleLiveAction`
   * **Type**:  `cq:LiveSyncAction`

1. Klik **Alles opslaan**.
1. Selecteer de `exampleLiveAction` knoop en voeg het volgende bezit toe:

   * **Naam**:  `repLastModBy`
   * **Type**:  `Boolean`
   * **Waarde**:  `true`

   Deze eigenschap geeft aan de klasse `ExampleLiveAction` aan dat de eigenschap `cq:LastModifiedBy` van de bron naar het doelknooppunt moet worden gerepliceerd.

1. Klik **Alles opslaan**.

### Live kopie maken {#create-the-live-copy}

[Creeer een levende ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) kopie van de Engelse/Producten tak van de Plaats van de Verwijzing Wij.Retail gebruikend uw rollout configuratie:

* **Bron**:  `/content/we-retail/language-masters/en/products`

* **Uitrolconfiguratie**: Voorbeeld-uitrolconfiguratie

Activeer de pagina **Products** (english) van de brontak en bekijk de logboekberichten die de `LiveAction` klasse produceert:

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

<!--
## Removing the Chapters Step in the Create Site Wizard {#removing-the-chapters-step-in-the-create-site-wizard}

In some cases, the **Chapters** selection is not required in the create site wizard (only the **Languages** selection is required). To remove this step in the default We.Retail English blueprint:

1. In CRX Explorer, remove the node:
   `/etc/blueprints/weretail-english/jcr:content/dialog/items/tabs/items/tab_chap`.

1. Navigate to `/libs/wcm/msm/templates/blueprint/defaults/livecopy_tab/items` and create a new node:

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
* Standaardlanden voor talen (bijvoorbeeld voor codes `en`, `de`)

De taallijst wordt opgeslagen onder de `/libs/wcm/core/resources/languages` knoop. Elk onderliggend knooppunt vertegenwoordigt een taal of een taal-land:

* De naam van het knooppunt is de taalcode (zoals `en` of `de`) of de taalcode (zoals `en_us` of `de_ch`).

* De `language` bezit van de knoop slaat de volledige naam van de taal voor de code op.
* In de eigenschap `country` van het knooppunt wordt de volledige naam van het land voor de code opgeslagen.
* Wanneer de knooppuntnaam slechts uit een taalcode (zoals `en`) bestaat, is het landbezit `*`, en een extra `defaultCountry` bezit slaat de code van het taal-land op om het te gebruiken land te wijzen.

![chlimage_1-76](assets/chlimage_1-76.png)

De talen wijzigen:

1. Open CRXDE Lite in uw webbrowser; bijvoorbeeld [https://localhost:4502/crx/de](https://localhost:4502/crx/de)
1. Selecteer de map `/apps` en klik op **Maken** en **Map maken.**

   Geef de nieuwe map een naam `wcm`.

1. Herhaal de vorige stap om de mappenstructuur `/apps/wcm/core` te maken. Maak een knooppunt van het type `sling:Folder` in `core` met de naam `resources`. <!-- ![chlimage_1-77](assets/chlimage_1-77.png) -->

1. Klik met de rechtermuisknop op het knooppunt `/libs/wcm/core/resources/languages` en klik op **Copy**.
1. Klik met de rechtermuisknop op de map `/apps/wcm/core/resources` en klik op **Plakken**. Wijzig de onderliggende knooppunten naar wens.
1. Klik **Alles opslaan**.
1. Klik **Gereedschappen**, **Bewerkingen** dan **Webconsole**. Van deze console klik **OSGi**, toen **Configuratie**.
1. Zoek en klik op **Day CQ WCM Language Manager** en wijzig de waarde van **Taallijst** in `/apps/wcm/core/resources/languages` en klik vervolgens op **Opslaan**.

   ![chlimage_1-78](assets/chlimage_1-78.png)

## MSM-vergrendelingen configureren op pagina-eigenschappen (interface met aanraakbediening) {#configuring-msm-locks-on-page-properties-touch-enabled-ui}

Wanneer u een aangepaste pagina-eigenschap maakt, moet u mogelijk overwegen of de nieuwe eigenschap kan worden geïmplementeerd voor live kopieën.

Als bijvoorbeeld twee nieuwe pagina-eigenschappen worden toegevoegd:

* E-mailadres contactpersoon:

   * Dit onroerend goed hoeft niet te worden uitgevoerd, omdat het per land (of merk, enz.) anders zal zijn.

* Belangrijke visuele stijl:

   * Het projectvereiste is dat dit onroerend goed moet worden uitgevoerd zoals het (gewoonlijk) gemeenschappelijk is voor alle landen (of merken, enz.).

Daarna moet u ervoor zorgen dat:

* E-mailadres contactpersoon:

   * is uitgesloten van de opgebouwde eigenschappen; zie [Eigenschappen en knooppunttypen uitsluiten van synchronisatie](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization).

* Belangrijke visuele stijl:

   * Zorg ervoor dat u deze eigenschap niet mag bewerken in de interface met aanraakbediening, tenzij de overerving wordt geannuleerd, en dat u de overerving vervolgens opnieuw kunt installeren. Dit wordt gecontroleerd door de ketting/gebroken-ketting verbindingen te klikken die om op de status van de verbinding van een knevel te wijzen.

Of een pagina-eigenschap moet worden geïmplementeerd en, afhankelijk van het annuleren/opnieuw installeren van overerving tijdens het bewerken, wordt dan gecontroleerd door de dialoogvenster-eigenschap:

* `cq-msm-lockable`

   * is van toepassing op items in een interface-dialoogvenster met aanraakbediening
   * maakt het kettingkoppelingssymbool in het dialoogvenster
   * is alleen bewerken toegestaan als overerving is geannuleerd (de ketting-koppeling is verbroken)
   * alleen van toepassing op het eerste onderliggende niveau van de bron
   * **Type**:  `String`

   * **Waarde**: houder is van de naam van het betrokken goed (en vergelijkbaar is met de waarde van het goed  `name`; zie bijvoorbeeld
      `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

Wanneer `cq-msm-lockable` is bepaald, zal het breken/het sluiten van de ketting op de volgende manier met MSM in wisselwerking staan:

* als de waarde van `cq-msm-lockable`:

   * **Relatief**  (bijvoorbeeld  `myProperty` of  `./myProperty`)

      * de eigenschap wordt toegevoegd en verwijderd uit `cq:propertyInheritanceCancelled`.
   * **Absoluut**  (bv.  `/image`)

      * Als u de keten breekt, wordt de overerving geannuleerd door de `cq:LiveSyncCancelled`-mix toe te voegen aan `./image` en `cq:isCancelledForChildren` in te stellen op `true`.

      * als de keten wordt gesloten , wordt de overerving hersteld .


>[!NOTE]
>
>`cq-msm-lockable` is van toepassing op het eerste onderliggende niveau van de bron die moet worden bewerkt en is niet functioneel op een voorouder van een dieper niveau, ongeacht of de waarde als absoluut of relatief is gedefinieerd.

>[!NOTE]
>
>Wanneer u overerving opnieuw inschakelt, wordt de pagina-eigenschap voor live kopiëren niet automatisch gesynchroniseerd met de eigenschap source. U kunt handmatig een synchronisatie aanvragen als dit vereist is.
