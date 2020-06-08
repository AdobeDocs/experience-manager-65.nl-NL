---
title: AEM-projecten bouwen met Apache Maven
seo-title: AEM-projecten bouwen met Apache Maven
description: In dit document wordt beschreven hoe u een AEM-project instelt op basis van Apache Maven
seo-description: In dit document wordt beschreven hoe u een AEM-project instelt op basis van Apache Maven
uuid: 5db68639-7393-48b7-9d81-5b19b596ff21
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 3ebc1d22-a7a2-4375-9aa5-a18a7ceb446a
docset: aem65
translation-type: tm+mt
source-git-commit: 1669412afb670a9f55f02476e828de55b4f7a55a
workflow-type: tm+mt
source-wordcount: '2424'
ht-degree: 0%

---


# AEM-projecten bouwen met Apache Maven{#how-to-build-aem-projects-using-apache-maven}

## Overzicht {#overview}

In dit document wordt beschreven hoe u een AEM-project instelt op basis van [Apache Maven](https://maven.apache.org/).

Apache Maven is een opensource hulpmiddel om softwareprojecten te beheren door builds te automatiseren en kwaliteitsprojectinformatie te verstrekken. Het is het geadviseerde bouwstijlbeheersinstrument voor projecten AEM.

Het bouwen van uw AEM-project op basis van Maven biedt u verschillende voordelen:

* Een IDE-agnostische ontwikkelomgeving
* Gebruik van Maven Archetypes en Artifacts van Adobe
* Gebruik van Apache Sling- en Apache Felix-gereedschapssets voor op Maven gebaseerde ontwikkelinstellingen
* Versnelling van de invoer in een IDE; bijvoorbeeld Eclipse en/of IntelliJ
* Eenvoudige integratie met systemen voor continue integratie

### Maven Project Archetypes {#maven-project-archetypes}

Adobe biedt twee Maven-archetypen die als basislijn voor uw AEM-projecten kunnen dienen. Meer informatie vindt u op de volgende link:

* [AEM-projectarchetype](https://github.com/adobe/aem-project-archetype)
* [Maven archetype voor applicaties Starter Kit voor één pagina](https://github.com/adobe/aem-spa-project-archetype)

## Afhankelijkheden van Experience Manager API {#experience-manager-api-dependencies}

### Wat is de UberJar? {#what-is-the-uberjar}

Het &quot;UberJar&quot; is de informele naam die wordt gegeven aan het speciale Java Archives-bestand (JAR) dat door Adobe wordt geleverd. Deze JAR-bestanden bevatten alle openbare Java API&#39;s die worden weergegeven door Adobe Experience Manager. Zij omvatten ook beperkte externe bibliotheken, met name alle openbare API&#39;s die in AEM beschikbaar zijn en afkomstig zijn van de Apache Sling, Apache Jackrabbit, Apache Lucene, Google Guava, en twee bibliotheken die worden gebruikt voor beeldverwerking (Werner Randelshofer&#39;s CYMK JPEG ImageIO-bibliotheek en de TwelveMonkeys-afbeeldingsbibliotheek). UberJars bevatten slechts API interfaces en klassen, betekenend dat zij slechts interfaces en klassen bevatten die door een bundel OSGi in AEM worden uitgevoerd. Zij bevatten ook een *MANIFEST.MF* - dossier dat de correcte pakketuitvoerversies voor elk van deze uitgevoerde pakketten bevat, zodat hebben de projecten die tegen UberJar worden gebouwd de correcte pakketinvoerwaaiers.

### Waarom heeft Adobe de UberJars gemaakt? {#why-did-adobe-create-the-uberjars}

In het verleden moesten ontwikkelaars een relatief groot aantal individuele afhankelijkheden beheren voor verschillende AEM-bibliotheken en wanneer elke nieuwe API werd gebruikt, moesten een of meer individuele afhankelijkheden aan het project worden toegevoegd. Bij één project resulteerde de introductie van UberJar in het verwijderen van 30 afzonderlijke afhankelijkheden uit het project.

Vanaf AEM 6.5 biedt Adobe twee UberJars: één die afgekeurde interfaces en één omvat die die afgekeurde interfaces verwijdert. Door uitdrukkelijk bij bouwstijltijd van verwijzingen te voorzien, zijn de klanten zeker om te begrijpen als zij een gebiedsdeel op afgekeurde code hebben.

Tweede Uber Jar schrapt om het even welke verouderde klassen, methodes, en eigenschappen zodat kunnen de klanten tegen hen compileren en begrijpen als de douanecode toekomstige proef is.

### Welk UberJar te gebruiken? {#which-uberjar-to-use}

AEM 6.5 komt voor in twee aroma&#39;s van Uber Jar:

1. Uber Jar - Omvat slechts de openbare interfaces die niet voor afschrijving worden gemerkt. Dit is het **aanbevolen** UberJar-bestand dat u kunt gebruiken omdat het de codebase in de toekomst helpt te controleren of deze afhankelijk is van afgekeurde API&#39;s.
1. Uber Jar met Verouderde APIs - omvat alle openbare interfaces, met inbegrip van die duidelijk voor verval in een toekomstige versie van AEM.

### Hoe gebruik ik de UberJars? {#how-do-i-use-the-uberjars}

Als u Apache Maven gebruikt als een constructiesysteem (dat geldt voor de meeste AEM Java-projecten), moet u een of twee elementen toevoegen aan het bestand *pom.xml* . Het eerste is een *gebiedsdeelelement* die de daadwerkelijke gebiedsafhankelijkheid aan uw project toevoegt:

**Uber Jar-afhankelijkheid *(zonder verouderde API&#39;s)***

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

**Uber Jar-afhankelijkheid met afgekeurde API&#39;s**

>[!CAUTION]
>
>Adobe raadt u aan de geïmplementeerde Uber Jar die ***bevat de verouderde API&#39;s niet* bevat, te gebruiken om ervoor te zorgen dat uw toepassingen correct worden uitgevoerd in toekomstige versies van AEM.
>
>Gebruik Uber Jar met afgekeurde API steun slechts in het geval de code die op afgekeurde APIs baseert niet kan worden gewijzigd om voor de veranderingen aan te passen.

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis-with-deprecations</classifier>
    <scope>provided</scope>
</dependency>
```

Als uw bedrijf al gebruikmaakt van een Maven Repository Manager zoals Sonatype Nexus, Apache Archiva of JFrog Artifactory, voegt u de juiste configuratie toe aan uw project om naar deze opslagplaats te verwijzen en voegt u Adobe&#39;s Maven repository ([https://repo.adobe.com/nexus/content/groups/public/](https://repo.adobe.com/nexus/content/groups/public/)) toe aan uw opslagplaats Manager.

Als u geen gegevensopslagbeheerder gebruikt, moet u een *gegevensopslagsysteem* -element toevoegen aan uw *pom.xml* -bestand:

```xml
<repositories>
    <repository>
        <id>adobe-public-releases</id>
        <name>Adobe Public Repository</name>
        <url>https://repo.adobe.com/nexus/content/groups/public/</url>
        <layout>default</layout>
    </repository>
</repositories>
<pluginRepositories>
    <pluginRepository>
        <id>adobe-public-releases</id>
        <name>Adobe Public Repository</name>
        <url>https://repo.adobe.com/nexus/content/groups/public/</url>
        <layout>default</layout>
    </pluginRepository>
</pluginRepositories>
```

### Wat kan ik doen met de UberJar? {#what-can-i-do-with-the-uberjar}

Met UberJar, kunt u projectcode compileren die van AEM APIs (en APIs afhangt die door de bovengenoemde projecten worden gebruikt). U kunt OSGi Runtime van de Component van de Dienst (SCR) en informatie ook produceren OSGi Metatype. Met sommige beperkingen kunt u ook eenheidstests schrijven en uitvoeren.

### Wat kan ik niet doen met de UberJar? {#what-can-t-i-do-with-the-uberjar}

Aangezien UberJar **alleen** API&#39;s bevat, is het niet uitvoerbaar en kan het niet worden gebruikt om Adobe Experience Manager **uit te voeren** . Als u AEM wilt uitvoeren, hebt u de AEM QuickStart-indeling (Standalone of Web Application Archive, WAR) nodig.

### U noemde beperkingen op eenheidstests. Gelieve nader toe te lichten. {#you-mentioned-limitations-on-unit-tests-please-explain-further}

De tests van de eenheid communiceren over het algemeen met product APIs op drie verschillende manieren, die elk lichtjes verschillend door UberJar worden beïnvloed.

#### Hoofdlettergebruik 1 - Aangepaste code die een API-interface aanroept {#use-case-custom-code-which-calls-a-api-interface}

Dit geval, dat het meest gebruikelijk is, omvat sommige douanecode die methodes op een interface uitvoert Java die door AEM API wordt bepaald. De implementatie van deze interface kan direct worden gegeven of worden geïnjecteerd met behulp van het Dependency Injection pattern. **Dit gebruiksgeval kan met UberJar worden behandeld.**

Een voorbeeld van het eerste zou zijn:

```java
public class ClassWhichHasAEMInterfacePassedIn {
    /**
     * Get the first length characters of the page title.
     */
    public String getTrimmedTitle(Page page, int length) {
         String title = page.getTitle();
         return StringUtils.left(title, length);
    }
}
```

Een voorbeeld hiervan zou zijn:

```java
@Component
@Service
public class ComponentWhichHasAEMInterfaceInjected implements TitleTrimmer {
    @Reference
    private PageManagerFactory pageManagerFactory;

    /**
     * Get the first length characters of the title of the page containing the provided Resource.
     */
    public String getTrimmedTitle(Resource resource, int length) {
        PageManager pageManager = pageManagerFactory.getPageManager(resource.getResourceResolver());
        Page page = pageManager.getContainingPage(resource);
        if (page == null) {
           return null;
        }
        String title = page.getTitle();
        return StringUtils.left(title, length);
    }
}
```

Om een van deze methoden te testen, zou een ontwikkelaar een raamwerk zoals [JMockit](http://jmockit.github.io), [Mockito](https://mockito.org/), [JMock](https://www.jmock.org/)of [Easymock](https://easymock.org/) gebruiken om een mock-object te maken voor de AEM API waarnaar wordt verwezen. Deze voorbeelden maken gebruik van JMockit, maar voor dit specifieke geval is het verschil tussen deze frameworks grotendeels syntactisch.

```java
@RunWith(JMockit.class)
public class ClassWhichHasAEMInterfacePassedInTest {

    @Tested
    private ClassWhichHasAEMInterfacePassedIn instance;

    @Mocked
    private Page page;

    @Test
    public void test_that_long_string_is_trimmed() {
        new Expectations() {{
            page.getTitle();
            result = "a really really really really really long string";
        }};
        assertEquals("a really", instance.getTrimmedTitle(page, 8));
    }
}
```

```java
@RunWith(JMockit.class)
public class ComponentWhichHasAEMInterfaceInjectedTest {

    @Tested
    private ComponentWhichHasAEMInterfaceInjected instance;

    @Mocked
    private Page page;

    @Mocked
    private PageManager pageManager;

    @Injectable
    private PageManagerFactory pageManagerFactory;

    @Mocked
    private Resource resource;

    @Mocked
    private ResourceResolver resourceResolver;

    @Test
    public void test_that_long_string_is_trimmed() {
        new Expectations() {{
            resource.getResourceResolver();
            result = resourceResolver;
            pageManagerFactory.getPageManager(resourceResolver);
            result = pageManager;
            pageManager.getContainingPage(resource);
            result = page;
            page.getTitle();
            result = "a really really really really really long string";
        }};
        assertEquals("a really", instance.getTrimmedTitle(resource, 8));
    }
}
```

#### Hoofdlettergebruik 2 - Aangepaste code die een API-implementatieklasse aanroept {#use-case-custom-code-which-calls-an-api-implementation-class}

Dit gebruiksgeval impliceert het roepen in een statische of instantiemethode van een klasse in AEM API waar u naar een betonnen klasse verwijst, in tegenstelling tot een interface zoals in Geval #1 van het Gebruik.

```java
public class ClassWhichUsesAStaticMethodFromAPI {

    /**
     * Get a map of asset titles to asset objects.
     *
     * @param resource either an asset resource or a folder containing assets.
     * @return an map of titles to assets. if an asset doesn't have a title, the name is used instead.
     */
    public Map<String, Asset> getAssetTitles(Resource resource) {
        Iterator<Asset> assets = DamUtil.getAssets(resource);
        Map<String, Asset> result = new HashMap<String, Asset>();
        while (assets.hasNext()) {
            Asset asset = assets.next();
            String title = asset.getMetadataValue(DamConstants.DC_TITLE);
            if (title == null) {
                title = asset.getName();
            }
            result.put(title, asset);
        }
        return result;
    }
}
```

```java
public class ClassWhichUsesAnInstanceMethodFromAPI {

    /**
     * Count the number of paragraphs in a parsys.
     *
     * @param resource the parsys resource
     * @return the count
     */
    public int countParagraphs(Resource resource) {
        return new ParagraphSystem(resource).paragraphs().size();
    }
}
```

**Dit gebruiksgeval kan met UberJar** worden behandeld. Het is echter nog steeds aan te raden om de API waar mogelijk te controleren voor prestatietests.

```java
@RunWith(JMockit.class)
public class ClassWhichUsesAStaticMethodFromAPITest {

    @Tested
    private ClassWhichUsesAStaticMethodFromAPI instance;

    @Mocked(stubOutClassInitialization = true)
    private DamUtil unusedDamUtil = null;

    @Mocked
    private Resource resource;

    @Test
    public void test_that_empty_iterator_produces_empty_map() {
        new Expectations() {
            {
                DamUtil.getAssets(resource);
                result = Collections.<Asset> emptySet().iterator();
            }
        };
        Map<String, Asset> result = new ClassWhichUsesAStaticMethodFromAPI().getAssetTitles(resource);
        assertNotNull(result);
        assertEquals(0, result.size());
    }
    @Test
    public void test_with_reference_search() {
        assertTrue(true);
    }
}
```

```java
@RunWith(JMockit.class)
public class ClassWhichUsesAnInstanceMethodFromAPITest {

    @Tested
    private ClassWhichUsesAnInstanceMethodFromAPI instance;

    @Mocked
    private Resource parsys;

    @Mocked
    private Paragraph firstPar;

    @Mocked
    private Paragraph secondPar;

    @Test
    public void test_empty_parsys_returns_zero() {
        new MockUp<ParagraphSystem>() {
            @Mock
            public void $init(Resource resource) {
                assertEquals(parsys, resource);
            }
            @Mock
            public List<Paragraph> paragraphs() {
                return Collections.<Paragraph> emptyList();
            }
        };
        assertEquals(0, instance.countParagraphs(parsys));
    }
}
```

#### Hoofdlettergebruik 3 - Aangepaste code die een basisklasse uitbreidt met de API {#use-case-custom-code-which-extends-a-base-class-from-the-api}

Net als bij SCR Generation, als uw code een basisklasse (abstract of beton) van AEM API uitbreidt, **moet** u UberJar gebruiken om het te testen.

## Algemene ontwikkelingstaken met Maven {#common-development-tasks-with-maven}

### Hoe te om Wegen aan de inhoudsmodule toe te voegen {#how-to-add-paths-to-the-content-module}

De inhoudsmodule bevat een bestand src/main/content/META-INF/vault/filter.xml dat de filters definieert voor het AEM-pakket dat door Maven is gemaakt. Het bestand dat wordt gemaakt door het Maven archetype ziet er als volgt uit:

#### src/main/content/META-INF/vault/filter.xml {#src-main-content-meta-inf-vault-filter-xml}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/apps/myproject"/>
</workspaceFilter>
```

Dit bestand wordt op verschillende manieren gebruikt:

* door `content-package-maven-plugin` te bepalen welke inhoud in het pakket moet worden opgenomen
* door het gereedschap VLT om te bepalen welke paden in overweging moeten worden genomen
* als het pakket opnieuw is ingebouwd in AEM Package Manager, definieert dit ook welke paden moeten worden opgenomen

Afhankelijk van de vereisten van uw toepassing kunt u deze paden uitbreiden met meer inhoud, zoals:

* Uitrolconfiguraties
* Blauwdrukken
* Workflowmodellen
* Ontwerppagina&#39;s
* Voorbeeldinhoud

Voeg meer `<filter>` elementen toe aan de paden:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/apps/myproject"/>
    <filter root="/etc/msm/rolloutconfigs/myrolloutconfig"/>
    <filter root="/etc/blueprints/mysite/globalsite"/>
    <filter root="/etc/workflow/models/myproject"/>
    <filter root="/etc/designs/myproject"/>
    <filter root="/content/myproject/sample-content"/>
</workspaceFilter>
```

#### Paden aan het pakket toevoegen zonder ze te synchroniseren {#adding-paths-to-the-package-without-syncing-them}

Als u bestanden hebt die moeten worden toegevoegd aan het pakket dat is gemaakt met de insteekmodule voor het verpakken van inhoud, maar die niet moeten worden gesynchroniseerd tussen het bestandssysteem en de opslagplaats, kunt u `.vltignore` bestanden gebruiken. Deze bestanden hebben dezelfde syntaxis als [.gitignore](https://www.kernel.org/pub/software/scm/git/docs/gitignore.html) -bestanden.

Het archetype gebruikt bijvoorbeeld een `.vltignore` bestand om te voorkomen dat het JAR-bestand dat als onderdeel van de bundel is geïnstalleerd, weer naar het bestandssysteem wordt gesynchroniseerd:

#### src/main/content/jcr_root/apps/myproject/install/.vltignore {#src-main-content-jcr-root-apps-myproject-install-vltignore}

```xml
*.jar
```

#### Paden synchroniseren zonder deze aan het pakket toe te voegen {#syncing-paths-without-adding-them-to-the-package}

In sommige gevallen wilt u bepaalde paden mogelijk synchroniseren tussen het bestandssysteem en de opslagplaats, maar deze niet opnemen in het pakket dat is gemaakt om in AEM te worden geïnstalleerd.

Een typisch geval is de `/libs/foundation` weg. Voor ontwikkelingsdoeleinden, kunt u de inhoud van dit weg beschikbaar in uw dossiersysteem willen hebben, zodat bijvoorbeeld uw winde JSP opneming kan oplossen die JSPs in omvatten `/libs`. Nochtans, wilt u niet dat deel in het pakket omvatten u bouwt, aangezien het `/libs` deel productcode bevat die niet door douaneimplementaties moet worden gewijzigd.

Hiervoor kunt u een bestand opgeven `src/main/content/META-INF/vault/filter-vlt.xml`. Als dit bestand bestaat, wordt het gebruikt door het VLT-gereedschap, bijvoorbeeld wanneer u het uitvoert `vlt up` en `vlt ci`, of wanneer u het hebt ingesteld `vlt sync` . De insteekmodule voor het maken van het pakket blijft het bestand gebruiken `src/main/content/META-INF/vault/filter.xml` tijdens het maken van het pakket.

Als u bijvoorbeeld lokaal `/libs/foundation` beschikbaar wilt maken voor ontwikkeling, maar alleen `/apps/myproject` in het pakket wilt opnemen, gebruikt u de volgende twee bestanden.

#### src/main/content/META-INF/vault/filter.xml {#src-main-content-meta-inf-vault-filter-xml-1}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/apps/myproject"/>
</workspaceFilter>
```

#### src/main/content/META-INF/vault/filter-vlt.xml {#src-main-content-meta-inf-vault-filter-vlt-xml}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<workspaceFilter version="1.0">
    <filter root="/libs/foundation"/>
    <filter root="/apps/myproject"/>
</workspaceFilter>
```

U moet ook de insteekmodule maven-resources opnieuw configureren om deze bestanden niet in het pakket op te nemen: het bestand filter.xml wordt niet toegepast wanneer het pakket is geïnstalleerd, maar alleen wanneer het pakket opnieuw wordt samengesteld met gebruik van pakketbeheer.

Wijzig de `<resources>` sectie in de inhoudspom dienovereenkomstig:

#### src/main/content/pom.xml {#src-main-content-pom-xml}

```xml
<!-- ... -->
<resources>
 <resource>
  <directory>src/main/content/jcr_root</directory>
  <filtering>false</filtering>
  <excludes>
   <exclude>**/.vlt</exclude>
   <exclude>**/.vltignore</exclude>
   <exclude>libs/</exclude>
  </excludes>
 </resource>
</resources>
<!-- ... -->
```

### Werken met JSPs {#how-to-work-with-jsps}

De Maven-installatie die tot nu toe is beschreven, maakt een inhoudspakket dat ook componenten en de bijbehorende JSP&#39;s kan bevatten. Maven behandelt deze echter als elk ander bestand dat deel uitmaakt van het inhoudspakket en herkent ze niet eens als JSP&#39;s.

De resulterende componenten werken allemaal in AEM, maar het bewust maken van de JSPs heeft twee belangrijke voordelen

* Het staat Maven toe om te ontbreken als JSPs fouten bevat, zodat deze bij bouwstijltijd en niet wanneer zij voor het eerst in AEM worden gecompileerd
* Voor IDEs die Gemaakt projecten kunnen invoeren, laat dit ook codevoltooiing en de steun van de markeringsbibliotheek in JSPs toe

Er zijn twee dingen vereist om deze installatie in te schakelen:

1. tagbibliotheekafhankelijkheden toevoegen
1. JSPs als deel van het Maven compileert proces compileren

#### Afhankelijkheden van tagbibliotheken toevoegen {#adding-tag-library-dependencies}

Onder gebiedsdelen moeten aan POM van de `content` modules worden toegevoegd.

>[!NOTE]
>
>Tenzij u de productafhankelijkheden importeert zoals hierboven beschreven in [AEM-productafhankelijkheden](#importingaemproductdependencies) importeren, moeten deze ook worden toegevoegd aan de bovenliggende POM samen met de versie die overeenkomt met uw AEM-instellingen, zoals hierboven beschreven in [Afhankelijkheden](#addingdependencies) toevoegen. De opmerkingen in elk van de onderstaande items tonen het pakket waarnaar u wilt zoeken in de Dependency Finder.

>[!NOTE]
>
>Het `com.adobe.granite.xssprotection` artefact is niet inbegrepen in cq-quickstart-product-gebiedsdelen POM en vereist volledige Maven coördinaten zoals die van de Vinder van de Afhankelijkheid worden verkregen.

#### Het compileren JSPs als deel van de Maven Compile Fase {#compiling-jsps-as-part-of-the-maven-compile-phase}

Om JSPs in de `compile` fase van Maven te compileren, gebruiken wij Apache Sling&#39;s [Maven JspC Plugin](https://sling.apache.org/documentation/development/jspc.html) zoals hieronder getoond:

* wij opstelling een uitvoering voor het `jspc` doel (dat door gebrek aan de `compile` fase bindt, zodat te hoeven wij niet om de fase uitdrukkelijk te specificeren)

* wij vertellen het om het even welke JSPs te compileren in `${project.build.directory}/jsps-to-compile`
* en voer het resultaat uit naar `${project.build.directory}/ignoredjspc` (dat wordt omgezet in `myproject/content/target/ignoredjspc`)

* wij opstelling maven-middelen-stop - in om JSPs aan `${project.build.directory}/jsps-to-compile` in te kopiëren produceren-bronfase en het te vormen om de `libs/` omslag niet te kopiëren (omdat dat productcode AEM is en wij niet de gebiedsdelen voor compilatie voor ons project willen aangaan, noch moeten wij bevestigen dat het compileert.

Ons primaire doel, zoals hierboven vermeld, is JSPs te bevestigen en ervoor te zorgen dat het bouwstijlproces ontbreekt als zij fouten bevatten. Daarom compileren wij hen aan een afzonderlijke folder die wordt genegeerd (en in feite onmiddellijk daarna geschrapt, zoals u over een minuut zult zien).

Het resultaat van de Plugin Maven JspC kan ook als deel van een Bundel worden gebundeld en worden opgesteld OSGi, maar dit heeft andere implicaties en nevengevolgen en gaat voorbij ons doel om JSPs te bevestigen.

Om schrapping van de klassen te bereiken die van JSPs worden gecompileerd, opstelling wij de Gegaveerde Schone Insteekmodule zoals hieronder getoond. Als u het resultaat van de Plug-in Maven JspC wilt inspecteren, voert u `mvn compile` in `myproject/content` - daarna vindt u het resultaat in `myproject/content/target/ignoredjspc`).

#### myproject/content/pom.xml {#myproject-content-pom-xml}

```xml
<build>
  <!-- ... -->
  <plugins>
    <!-- ... -->
    <plugin>
      <artifactId>maven-resources-plugin</artifactId>
      <executions>
        <execution>
          <id>copy-resources</id>
          <phase>generate-sources</phase>
          <goals>
            <goal>copy-resources</goal>
          </goals>
          <configuration>
            <outputDirectory>${project.build.directory}/jsps-to-compile</outputDirectory>
            <resources>
              <resource>
                <directory>src/main/content/jcr_root</directory>
                <excludes>
                  <exclude>libs/**</exclude>
                </excludes>
              </resource>
            </resources>
          </configuration>
        </execution>
      </executions>
    </plugin>
    <plugin>
      <groupId>org.apache.sling</groupId>
      <artifactId>maven-jspc-plugin</artifactId>
      <version>2.0.6</version>
      <executions>
        <execution>
          <id>compile-jsp</id>
          <goals>
            <goal>jspc</goal>
          </goals>
          <configuration>
            <jasperClassDebugInfo>false</jasperClassDebugInfo>
            <sourceDirectory>${project.build.directory}/jsps-to-compile</sourceDirectory>
            <outputDirectory>${project.build.directory}/ignoredjspc</outputDirectory>
          </configuration>
        </execution>
      </executions>
    </plugin>
    <plugin>
      <artifactId>maven-clean-plugin</artifactId>
      <executions>
        <execution>
          <id>remove-compiled-jsps</id>
          <goals>
            <goal>clean</goal>
          </goals>
          <phase>process-classes</phase>
          <configuration>
            <excludeDefaultDirectories>true</excludeDefaultDirectories>
            <filesets>
              <fileset>
                <directory>${project.build.directory}/jsps-to-compile</directory>
                <directory>${project.build.directory}/ignoredjspc</directory>
              </fileset>
            </filesets>
          </configuration>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

>[!NOTE]
>
>Afhankelijk van of u werkelijk gebruik maakt van JSP code in `/libs` (d.w.z. JSPs van daar omvat), zult u moeten verfijnen welke JSPs voor compilatie wordt gekopieerd.
>
>Bijvoorbeeld als u omvat `/libs/foundation/global.jsp`, kunt u de volgende configuratie voor `maven-resources-plugin` in plaats van de configuratie gebruiken waarboven volledig overslaat `/libs`.
>
>
```
> <resource>  
>           <directory>src/main/content/jcr_root</directory>  
>           <includes>  
>                   <include>apps/**</include>  
>                   <include>libs/foundation/global.jsp</include>
>       </includes>  
>   </resource>  
>```

### Hoe kan ik-werken met SCM-systemen {#how-to-work-with-scm-systems}

Wanneer het werken met het Beheer van de Configuratie Source (SCM), wilt u ervoor zorgen dat

* VCS negeert niet-bronartefacten in het dossiersysteem
* VLT negeert artefacten van VCS en controleert hen niet aan de bewaarplaats

>[!NOTE]
>
>Deze beschrijving behandelt niet hoe te om Gemaakt te vormen om met uw SCM te werken, die uitgebreid in de [Gemaakt POM verwijzing](https://maven.apache.org/pom.html#SCM) en de documentatie [van de Insteekmodule](https://maven.apache.org/scm/)Maven SCM wordt beschreven.

#### Patronen die moeten worden uitgesloten van SCM {#patterns-to-exclude-from-scm}

Het volgende is een typische lijst van patronen om van SCM te omvatten. Als u bijvoorbeeld git gebruikt, kunt u deze toevoegen aan het `.gitignore` bestand van uw project.

#### sample.gitignore {#sample-gitignore}

```shell
# Ignore VLT files
.vlt
.vlt-sync.log
.vlt-sync-config.properties

# Ignore Quickstart launches in the source tree
license.properties
crx-quickstart

# Ignore compilation results
target

# Ignore IDE and Operating System artifacts
.idea
.classpath
.metadata
.project
.settings
maven-eclipse.xml
*.iml
*.ipr
*.iws
.DS_Store
```

#### SCM-besturingsbestanden negeren in VLT {#ignoring-scm-control-files-in-vlt}

In sommige gevallen hebt u wellicht SCM-besturingsbestanden in de bronstructuur van de inhoud die u niet wilt inchecken in de opslagplaats.

Denk aan de volgende situatie:

Het archetype heeft al een .vltignore-bestand gemaakt om te voorkomen dat het geïnstalleerde bundeljar-bestand weer naar het bestandssysteem wordt gesynchroniseerd:

#### src/main/content/jcr_root/apps/myproject/install/.vltignore {#src-main-content-jcr-root-apps-myproject-install-vltignore-1}

```shell
*.jar
```

Het is duidelijk dat u dit bestand ook niet in uw SCM wilt opnemen, dus als u bijvoorbeeld git gebruikt, voegt u een corresponderend bestand toe. `gitignore` bestand:

#### src/main/content/jcr_root/apps/myproject/install/.gitignore {#src-main-content-jcr-root-apps-myproject-install-gitignore}

```shell
*.jar
```

Als de . `gitignore` Het bestand mag ook niet in de opslagplaats terechtkomen, de `vltignore` moet worden uitgebreid tot de `gitignore` bestand:

#### src/main/content/jcr_root/apps/myproject/install/.vltignore {#src-main-content-jcr-root-apps-myproject-install-vltignore-2}

```shell
*.jar
.gitignore
```

### Hoe kan ik-werken met implementatieprofielen {#how-to-work-with-deployment-profiles}

Als uw bouwstijlproces deel van een grotere opstelling van het het beheer van de ontwikkelingscyclus, zoals een ononderbroken integratieproces uitmaakt, moet u vaak aan andere machines dan enkel de lokale instantie van de ontwikkelaar opstellen.

Voor dergelijke scenario&#39;s, kunt u nieuwe Gemaakt [Bouwstijl Profielen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) aan POM van het project gemakkelijk toevoegen.

In het onderstaande voorbeeld wordt een profiel toegevoegd `integrationServer`waarmee de hostnamen en -poorten voor de auteur en de publicatie-instanties opnieuw worden gedefinieerd. U kunt aan deze servers opstellen door maven van de projectwortel in werking te stellen zoals hieronder getoond.

```shell
# install on integration test author
$ mvn -PautoInstallPackage -PintegrationServer install

# install on integration test publisher
$ mvn -PautoInstallPackagePublish -PintegrationServer install
```

#### myproject/pom.xml {#myproject-pom-xml}

```xml
<profiles>

    <!-- ... -->

    <profile>
        <id>integrationServer</id>
        <properties>
            <crx.host>dev-author.intranet</crx.host>
            <crx.port>5502</crx.port>
            <publish.crx.host>dev-publish.intranet</publish.crx.host>
            <publish.crx.port>5503</publish.crx.port>
        </properties>
    </profile>
</profiles>
```

### Hoe kan ik-werken met AEM-gemeenschappen {#how-to-work-with-aem-communities}

Als er een licentie voor de AEM Communities-mogelijkheid is, is een extra API-jar nodig.

Zie [Maven gebruiken voor Gemeenschappen voor meer informatie](/help/communities/maven.md)
