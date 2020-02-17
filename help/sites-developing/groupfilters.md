---
title: Apparaatgroepfilters maken
seo-title: Apparaatgroepfilters maken
description: Maak een apparaatgroepfilter om een set vereisten voor apparaatmogelijkheden te definiëren
seo-description: Maak een apparaatgroepfilter om een set vereisten voor apparaatmogelijkheden te definiëren
uuid: 30c0699d-2388-41b5-a062-f5ea9d6f08bc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: mobile-web
content-type: reference
discoiquuid: 9fef1f91-a222-424a-8e20-3599bedb8b41
docset: aem65
legacypath: /content/docs/en/aem/6-0/develop/mobile/groupfilters
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Apparaatgroepfilters maken{#creating-device-group-filters}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Maak een apparaatgroepfilter om een set vereisten voor apparaatmogelijkheden te definiëren. Maak zoveel filters als u nodig hebt om de benodigde groepen apparaatmogelijkheden als doel in te stellen.

Ontwerp uw filters zodat u combinaties ervan kunt gebruiken om de groepen mogelijkheden te bepalen. Gewoonlijk zijn de mogelijkheden van verschillende apparaatgroepen elkaar overlappen. Daarom zou u sommige filters met veelvoudige definities van de apparatengroep kunnen gebruiken.

Nadat u een filter creeert, kunt u het in de [groepsconfiguratie gebruiken.](/help/sites-developing/mobile.md#creating-a-device-group)

## De Java-klasse Filter {#the-filter-java-class}

Een apparaatgroepfilter is een OSGi-component die de [interface com.day.cq.wcm.mobile.api.device.DeviceGroupFilter](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/mobile/api/device/DeviceGroupFilter.html) implementeert. Wanneer opgesteld, verleent de implementatieklasse de filterdienst die aan de configuraties van de apparatengroep beschikbaar is.

De oplossing die in dit artikel wordt beschreven gebruikt Apache Felix Maven SCR Insteekmodule om de ontwikkeling van de component en de dienst te vergemakkelijken. Daarom gebruikt de voorbeeldklasse Java de `@Component`en de `@Service` annotaties. De klasse heeft de volgende structuur:

```java
package com.adobe.example.myapp;

import java.util.Map;

import com.day.cq.wcm.mobile.api.device.DeviceGroup;
import com.day.cq.wcm.mobile.api.device.DeviceGroupFilter;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

@Component(metatype = false)
@Service
public class myDeviceGroupFilter implements DeviceGroupFilter {

       public String getDescription() {
  return null;
 }

 public String getTitle() {
  return null;
 }

 public boolean matches(DeviceGroup arg0, String arg1, Map arg2) {
  return false;
 }

}
```

U moet code opgeven voor de volgende methoden:

* `getDescription`: Retourneert de filterbeschrijving. De beschrijving wordt weergegeven in het dialoogvenster Configuratie apparaatgroep.
* `getTitle`: Retourneert de naam van het filter. De naam wordt weergegeven wanneer u filters voor de apparaatgroep selecteert.
* `matches`: Hiermee wordt bepaald of het apparaat de vereiste mogelijkheden heeft.

### Filternaam en -beschrijving opgeven {#providing-the-filter-name-and-description}

De methoden `getTitle` en `getDescription` retourneren respectievelijk de filternaam en beschrijving. De volgende code illustreert de eenvoudigste implementatie:

```java
public String getDescription() {
    return "An example device group filter";
}

public String getTitle() {
 return "myFilter";
}
```

De harde codering van de naam en beschrijvingstekst is voldoende voor niet-taalse ontwerpomgevingen. U kunt de tekenreeksen extern maken voor meertalig gebruik of voor het inschakelen van het wijzigen van tekenreeksen zonder de broncode opnieuw te compileren.

### Evalueren aan de hand van filtercriteria {#evaluating-against-filter-criteria}

De `matches` functie retourneert `true` als de apparaatmogelijkheden voldoen aan alle filtercriteria. Evalueer de informatie die in methodeargumenten wordt verstrekt om te bepalen als het apparaat tot de groep behoort. De volgende waarden worden als argumenten opgegeven:

* Een DeviceGroup-object
* De naam van de gebruikersagent
* Een object Map dat de apparaatmogelijkheden bevat. De sleutels van de Kaart zijn de WURFL™ bezitsnamen en de waarden zijn de overeenkomstige waarden van het WURFL™ gegevensbestand.

De [interface com.day.cq.wcm.mobile.api.devicespecs.DeviceSpecsConstants](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/mobile/api/device/DeviceGroupFilter.html) bevat een subset van de WURFL™-capaciteitsnamen in statische velden. Gebruik deze veldconstanten als toetsen bij het ophalen van waarden uit de Kaart met apparaatmogelijkheden.

In het volgende codevoorbeeld wordt bijvoorbeeld bepaald of het apparaat CSS ondersteunt:

```xml
boolean cssSupport = true;
cssSupport = NumberUtils.toInt(capabilities.get(DeviceSpecsConstants.DSPEC_XHTML_SUPPORT_LEVEL)) > 1;
```

Het `org.apache.commons.lang.math` pakket biedt de `NumberUtils` klasse.

>[!NOTE]
>
>Zorg ervoor dat de WURFL™-database die naar AEM wordt geïmplementeerd de mogelijkheden bevat die u als filtercriteria gebruikt. (Zie [Apparaatdetectie](/help/sites-developing/mobile.md#server-side-device-detection).)

### Voorbeeldfilter voor schermgrootte {#example-filter-for-screen-size}

De volgende voorbeeldimplementatie DeviceGroupFilter bepaalt of de fysieke grootte van het apparaat aan minimumvereisten voldoet. Dit filter is bedoeld om granulariteit toe te voegen aan de groep aanraakapparaten. De grootte van knoppen in de gebruikersinterface van de toepassing moet gelijk zijn, ongeacht de fysieke schermgrootte. De grootte van andere items, zoals tekst, kan variëren. Het filter laat de dynamische selectie van bepaalde CSS toe die de grootte van de elementen UI controleert.

Dit filter past groottecriteria toe op de namen van de eigenschappen `physical_screen_height` en `physical_screen_width` WURFL™.

```java
package com.adobe.example.myapp;

import java.util.Map;

import com.day.cq.wcm.mobile.api.device.DeviceGroup;
import com.day.cq.wcm.mobile.api.device.DeviceGroupFilter;

import org.apache.commons.lang.math.NumberUtils;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;

@Component(metatype = false)
@Service
@SuppressWarnings("unused")
public class ScreenSizeLarge implements DeviceGroupFilter {
    private int len=400;
    private int wid=200;
    public String getDescription() {

        return "Requires the physical size of the screen to have minimum dimensions " + len + "x" + wid+".";
    }

    public String getTitle() {
        return "Screen Size Large ("+len + "x" + wid+")";
    }

    public boolean matches(DeviceGroup deviceGroup, String userAgent,
            Map<String, String> deviceCapabilities) {

        boolean longEnough=true;
        boolean wideEnough=false;
        int dimension1=NumberUtils.toInt(deviceCapabilities.get("physical_screen_height"));
        int dimension2=NumberUtils.toInt(deviceCapabilities.get("physical_screen_width"));
        if(dimension1>dimension2){
            longEnough=dimension1>=len;
            wideEnough=dimension2>=wid;
        }else{
            longEnough=dimension2>=len;
            wideEnough=dimension1>=wid;
        }

        return longEnough && wideEnough;
    }
}
```

De waarde van het Koord die de methode getTitle terugkeert verschijnt in de drop-down lijst van de eigenschappen van de apparatengroep.

![filteraddtogroup](assets/filteraddtogroup.png)

De waarden van het Koord die getTitle en getDescription methodes terugkeren zijn inbegrepen bij de bodem van de samenvattingspagina van de apparatengroep.

![filterbeschrijving](assets/filterdescription.png)

### Het Maven POM-bestand {#the-maven-pom-file}

De volgende POM-code is handig als u Maven gebruikt om uw toepassingen te maken. De POM verwijst naar verschillende vereiste plug-ins en afhankelijkheden.

**Insteekmodules:**

* Apache Maven Compiler Plugin: Compileert Java-klassen uit broncode.
* Apache Felix Maven Bundle Plugin: Maakt de bundel en het manifest
* Apache Felix Maven SCR-insteekmodule: Creeert het dossier van de componentenbeschrijver en vormt de dienst-component duidelijke kopbal.

**Afhankelijkheden:**

* `cq-wcm-mobile-api-5.5.2.jar`: Verstrekt de interfaces DeviceGroup en DeviceGroupFilter.

* `org.apache.felix.scr.annotations.jar`: Verstrekt de Annotaties van de Component en van de Dienst.

De interfaces DeviceGroup en DeviceGroupFilter zijn inbegrepen in de Communicatie van Dag 5 van de mobiele API bundel van WCM. De Felix-annotaties zijn opgenomen in de bundel Apache Felix Declarative Services. U kunt dit JAR-bestand opvragen in de openbare opslagplaats van Adobe.

Op het moment van ontwerpen is 5.5.2 de versie van de WCM Mobile API-bundel die in de meest recente versie van AEM staat. Gebruik Adobe Web Console ([https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles)) om ervoor te zorgen dat dit de bundelversie is die in uw omgeving wordt geïmplementeerd.

**** POM: (Uw POM gebruikt een andere groupId en versie.)

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
        xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <groupId>com.adobe.example.myapp</groupId>
      <artifactId>devicefilter</artifactId>
      <version>0.0.1-SNAPSHOT</version>
      <name>my app device filter</name>
      <url>https://dev.day.com/docs/en/cq/current.html</url>
  <packaging>bundle</packaging>
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
         <groupId>com.day.cq.wcm</groupId>
         <artifactId>cq-wcm-mobile-api</artifactId>
         <version>5.5.2</version>
         <scope>provided</scope>
     </dependency>
     <dependency>
        <groupId>org.apache.felix</groupId>
        <artifactId>org.apache.felix.scr.annotations</artifactId>
        <version>1.6.0</version>
        <scope>compile</scope>
    </dependency>
</dependencies>
</project>
```

Voeg het profiel toe dat in de sectie [Verkrijgen van de plug](/help/sites-developing/vlt-mavenplugin.md) -in Inhoudspakket wordt geleverd aan het instellingenbestand van uw afbeelding om de openbare Adobe-opslagplaats te gebruiken.
