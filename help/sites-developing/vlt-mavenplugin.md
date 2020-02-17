---
title: Pakketten beheren met Maven
seo-title: Pakketten beheren met Maven
description: Gebruik de plug-in Inhoud pakket met Maven om taken voor pakketbeheer te integreren in uw Maven-projecten
seo-description: Gebruik de plug-in Inhoud pakket met Maven om taken voor pakketbeheer te integreren in uw Maven-projecten
uuid: fa73f0d6-8848-4911-9b96-311c875b45be
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 943de371-0149-4307-be3a-b11c590b3451
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Pakketten beheren met Maven{#managing-packages-using-maven}

Met de plug-in Inhoudspakket Maven kunt u taken voor pakketbeheer integreren in uw Maven-projecten. Met de doelstellingen en parameters van de insteekmodule kunt u veel van de taken automatiseren die u normaal zou uitvoeren met de pagina Package Manager of de opdrachtregel van FileVault:

* Nieuwe pakketten maken van bestanden in het bestandssysteem.
* Installeer en verwijder pakketten op de CRX- of CQ-server.
* Bouw pakketten die reeds op de server worden bepaald.
* Verkrijg een lijst van pakketten die op de server geïnstalleerd zijn.
* Een pakket van de server verwijderen.

## De insteekmodule Inhoudspakket toevoegen aan het POM-bestand {#adding-the-content-package-maven-plugin-to-the-pom-file}

Als u de insteekmodule Inhoudspakket met Maven wilt gebruiken, voegt u het volgende insteekmodule toe in het element build van het POM-bestand:

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Als u Maven wilt inschakelen om de insteekmodule te downloaden, gebruikt u het profiel dat is opgegeven in de sectie [Insteekmodule](#obtaining-the-content-package-maven-plugin) voor inhoudspakket verkrijgen op deze pagina.

## Doelstellingen van de plug-in Inhoudspakket {#goals-of-the-content-package-maven-plugin}

De doelstellingen en doelparameters die de insteekmodule van het Pakket van de Inhoud verstrekt worden beschreven in de secties die volgen. De parameters die in de Gemeenschappelijke sectie van Parameters worden beschreven kunnen voor de meeste doelstellingen worden gebruikt. De parameters die op één doel van toepassing zijn worden beschreven in de sectie voor dat doel.

**Plug-voorvoegsel**

Het voorvoegsel van de plug-in is een inhoudspakket. Gebruik dit voorvoegsel om een doel uit te voeren vanaf de opdrachtregel, zoals in het volgende voorbeeld:

```shell
mvn content-package:build
```

**Parametervoorvoegsel**

Tenzij anders aangegeven, gebruiken de doelstellingen en parameters van de plug-in het voorvoegsel van de vault, zoals in het volgende voorbeeld:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

**Proxy**

De doelstellingen die volmachten voor de server gebruiken CRX of CQ gebruiken de eerste geldige volmachtsconfiguratie die in de GeMaven montages wordt gevonden. Als geen volmachtsconfiguratie wordt gevonden, wordt geen volmacht gebruikt. Zie de parameter useProxy in de Gemeenschappelijke sectie van Montages.

### Algemene parameters {#common-parameters}

De parameters in de volgende lijst zijn gemeenschappelijk voor alle doelstellingen behalve wanneer vermeld in de kolom van Doelen.

<table>
 <tbody>
  <tr>
   <th>Naam</th>
   <th>Type</th>
   <th>Vereist</th>
   <th>Standaardwaarde</th>
   <th>Beschrijving</th>
   <th>Doelen</th>
  </tr>
  <tr>
   <td>failOnError</td>
   <td>boolean</td>
   <td>Nee</td>
   <td>false</td>
   <td>Een waarde van <code>true</code> oorzaken de bouwstijl om te ontbreken wanneer een fout voorkomt. Bij een waarde van <code>false</code> wordt de fout genegeerd.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>name</td>
   <td>Tekenreeks</td>
   <td>bouwen: Ja<br /> installeren: Geen<br /> rm:Ja</td>
   <td>Opbouwen: Geen standaardwaarde.<br /> installeren: De waarde van het bezit artifactId van het GeMaven project.</td>
   <td>De naam van het pakket waarop moet worden gehandeld.</td>
   <td>Alle doelstellingen behalve ls.</td>
  </tr>
  <tr>
   <td>password</td>
   <td>Tekenreeks</td>
   <td>Ja</td>
   <td> beheerder</td>
   <td>Het wachtwoord dat wordt gebruikt voor verificatie met de CRX-server.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>serverId</td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td></td>
   <td>De server-id waarvan de gebruikersnaam en het wachtwoord voor verificatie moeten worden opgehaald.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>targetURL</td>
   <td>Tekenreeks</td>
   <td>Ja</td>
   <td>http://localhost:4502/<br /> crx/packmgr/<br /> service.jsp</td>
   <td>De URL van de HTTP-service-API van het CRX-pakketbeheer.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>timeout</td>
   <td>int</td>
   <td>Nee</td>
   <td>5</td>
   <td>De verbindingsonderbreking voor het communiceren met de dienst van de pakketmanager, in seconden.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>useProxy</td>
   <td>boolean</td>
   <td>Nee</td>
   <td>true</td>
   <td>Hiermee wordt bepaald of proxyconfiguraties uit het instellingenbestand Maven moeten worden gebruikt. Een waarde van <code>true</code> veroorzaakt het gebruik van de eerste actieve volmachtsconfiguratie die aan volmachtsverzoeken aan de pakketmanager wordt gevonden. Bij de waarde false wordt geen proxy gebruikt.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>userId</td>
   <td>Tekenreeks</td>
   <td>Ja</td>
   <td> beheerder</td>
   <td>De gebruikersnaam die moet worden geverifieerd met de CRX-server.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
  <tr>
   <td>uitgebreid</td>
   <td>boolean</td>
   <td>Nee</td>
   <td>false</td>
   <td>Schakelt uitgebreide logboekregistratie in of uit. Een waarde van <code>true</code> laat uitgebreide registreren toe.</td>
   <td>Alle doelstellingen behalve pakket.</td>
  </tr>
 </tbody>
</table>

### build {#build}

Bouwt een inhoudspakket dat reeds op een instantie AEM wordt bepaald.

>[!NOTE]
>
>Dit doel hoeft niet binnen een Maven-project te worden uitgevoerd.

#### Parameters {#parameters}

Alle parameters voor het bouwstijldoel worden beschreven in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

#### Voorbeeld {#example}

Het volgende voorbeeld bouwt het werkschema-boonpakket dat op de instantie AEM met het IP adres 10.36.79.223 geïnstalleerd is. Het doel wordt uitgevoerd gebruikend het volgende bevel:

```shell
mvn content-package:build
```

Het volgende POM-bestand bevindt zich in de huidige map van het opdrachtregelprogramma. De POM geeft de pakketnaam en de URL van de pakketservice aan.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
   <name>workflow-mbean</name>
   <failOnError>true</failOnError>
   <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
     </plugin>
 </plugins>
    </build>
</project>
```

### installeren {#install}

Hiermee installeert u een pakket in de directory. Voor de verwezenlijking van dit doel is geen Maven-project vereist. Het doel is gebonden aan de installatiefase van de Maven-build-levenscyclus.

#### Parameters {#parameters-1}

Naast de volgende parameters, zie de beschrijvingen in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

<table>
 <tbody>
  <tr>
   <th>Naam</th>
   <th>Type</th>
   <th>Vereist</th>
   <th>Standaardwaarde</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>artefact</td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td> De waarde van het bezit artifactId van het GeMaven project.</td>
   <td>Een tekenreeks van de formuliergroepId:artefactId:version[:packaging].</td>
  </tr>
  <tr>
   <td>artifactId</td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td></td>
   <td>De id van het artefact dat moet worden geïnstalleerd</td>
  </tr>
  <tr>
   <td>groupId</td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td></td>
   <td>De groupId van het te installeren artefact</td>
  </tr>
  <tr>
   <td>installeren</td>
   <td>boolean</td>
   <td>Nee</td>
   <td>true</td>
   <td>Hiermee wordt bepaald of het pakket automatisch moet worden uitgepakt wanneer het wordt geüpload. Bij de waarde true wordt het pakket uitgepakt en bij de waarde false wordt het pakket niet uitgepakt.</td>
  </tr>
  <tr>
   <td>localRepository</td>
   <td>org.apache.maven.<br /> artefact. opslagplaats.<br /> ArtifactRepository</td>
   <td>Nee</td>
   <td>De waarde van de systeemvariabele localRepository.</td>
   <td>De lokale Maven-opslagplaats. U kunt deze parameter niet configureren met de insteekmodule-configuratie. De eigenschap system wordt altijd gebruikt.</td>
  </tr>
  <tr>
   <td>packageFile</td>
   <td>java.io.File</td>
   <td>Nee</td>
   <td>Het primaire artefact dat voor het Maven project wordt bepaald.</td>
   <td>De naam van het te installeren pakketbestand.</td>
  </tr>
  <tr>
   <td>verpakking</td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td>zip</td>
   <td>Het type verpakking van het te installeren artefact</td>
  </tr>
  <tr>
   <td>pomRemoteRepositories</td>
   <td>java.util.List</td>
   <td>Ja</td>
   <td>De waarde van het bezit remoteAtRepositories dat voor het Geweven project wordt bepaald.</td>
   <td>Deze waarde kan niet worden gevormd gebruikend de pluginconfiguratie. De waarde moet in het project worden gespecificeerd. </td>
  </tr>
  <tr>
   <td>project</td>
   <td>org.apache.maven.<br /> project.MavenProject</td>
   <td>Ja</td>
   <td>Het project waarvoor de stop wordt gevormd.</td>
   <td>Het Maven-project. Het project is impliciet omdat het project de insteekmoduleconfiguratie bevat.</td>
  </tr>
  <tr>
   <td>repositoryId <i>(POM)</i><br /> repoID <i>(opdrachtregel)</i></td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td>temp</td>
   <td>De id van de opslagplaats waarvan het artefact wordt opgehaald. Gebruik repositoryID in een POM. Gebruik repoID in een opdrachtregel.</td>
  </tr>
  <tr>
   <td>repositoryUrl <i>(POM)</i><br /> repoURL <i>(opdrachtregel)</i></td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td></td>
   <td>De URL van de opslagplaats waarvan het artefact wordt opgehaald. Gebruik repositoryURL in een POM. Gebruik repoURL in een opdrachtregel.</td>
  </tr>
  <tr>
   <td>version</td>
   <td>Tekenreeks</td>
   <td>Nee</td>
   <td></td>
   <td>De versie van het artefact dat moet worden geïnstalleerd.</td>
  </tr>
 </tbody>
</table>

#### Voorbeeld {#example-1}

In het volgende voorbeeld wordt een pakket gemaakt dat de OSGi-bundel voor de workflow bevat (zie het voorbeeld voor het [builddoel](#build) ) en wordt het pakket vervolgens geïnstalleerd. Omdat het installatiedoel aan de fase van de pakketinstallatie gebonden is, voert het volgende bevel het installatiedoel uit:

```shell
mvn install
```

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>

  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>package</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```

### ls {#ls}

Maakt een lijst van de pakketten die aan de Manager van het Pakket worden opgesteld.

#### Parameters {#parameters-2}

Alle parameters van het doel ls worden beschreven in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

#### Voorbeeld {#example-2}

Het volgende voorbeeld maakt een lijst van de pakketten die op de instantie AEM met het IP adres 10.36.79.223 geïnstalleerd zijn. Het doel wordt uitgevoerd gebruikend het volgende bevel:

```shell
mvn content-package:ls
```

Het volgende POM-bestand bevindt zich in de huidige map van het opdrachtregelprogramma. De POM geeft de URL van de pakketservice op.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
      <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
      </plugin>
   </plugins>
     </build>
</project>
```

### rm {#rm}

Hiermee wordt een pakket verwijderd uit Pakketbeheer.

#### Parameters {#parameters-3}

Alle parameters van het rm doel worden beschreven in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

#### Voorbeeld {#example-3}

In het volgende voorbeeld wordt het workflowpakket verwijderd dat op de AEM-instantie met het IP-adres 10.36.79.223 is geïnstalleerd. Het doel wordt uitgevoerd gebruikend het volgende bevel:

```shell
mvn content-package:rm
```

Het volgende POM-bestand bevindt zich in de huidige map van het opdrachtregelprogramma. De POM geeft de URL van de pakketservice en de naam van het pakket op.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
                    <name>workflow-mbean</name>
      <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
      </plugin>
   </plugins>
     </build>
</project>
```

### verwijderen {#uninstall}

Hiermee wordt een pakket verwijderd. Het pakket blijft op de server staan in de toestand Niet-geïnstalleerd.

#### Parameters {#parameters-4}

Alle parameters van het verwijderingsdoel worden beschreven in de sectie [Algemene parameters](#common-parameters) .

#### Voorbeeld {#example-4}

In het volgende voorbeeld wordt het werkstroom-bonpakket verwijderd dat op de AEM-instantie is geïnstalleerd met het IP-adres 10.36.79.223. Het doel wordt uitgevoerd gebruikend het volgende bevel:

```shell
mvn content-package:uninstall
```

Het volgende POM-bestand bevindt zich in de huidige map van het opdrachtregelprogramma. De POM geeft de pakketnaam en de URL van de pakketservice aan.

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
   <name>workflow-mbean</name>
   <failOnError>true</failOnError>
   <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
     </plugin>
 </plugins>
    </build>
</project>
```

### package {#package}

Maakt een inhoudspakket. De standaardconfiguratie van het pakketdoel bevat de inhoud van de map waarin gecompileerde bestanden worden opgeslagen. De uitvoering van het pakketdoel vereist dat de compilatiefase is voltooid. Het pakketdoel is gebonden aan de pakketfase van de Maven-levenscyclus.

#### Parameters {#parameters-5}

Naast de volgende parameters, zie de beschrijving van de `name` parameter in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

<table>
 <tbody>
  <tr>
   <th>Naam</th>
   <th>Type</th>
   <th>Vereist</th>
   <th>Standaardwaarde</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>archive</td>
   <td>org.apache.maven.<br /> archiver.<br /> MavenArchiveConfiguration</td>
   <td>Nee</td>
   <td></td>
   <td>De archiefconfiguratie die moet worden gebruikt. Zie <a href="https://maven.apache.org/shared/maven-archiver/index.html">de documentatie voor Maven Archiver</a>.</td>
  </tr>
  <tr>
   <td>builtContentDirectory</td>
   <td>java.io.File</td>
   <td>Ja</td>
   <td>De waarde van de uitvoerdirectory van de Maven-build.</td>
   <td>De map die de inhoud bevat die in het pakket moet worden opgenomen.</td>
  </tr>
  <tr>
   <td>afhankelijkheden</td>
   <td>java.util.List</td>
   <td>Nee</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>embeddedTarget</td>
   <td>java.lang.String</td>
   <td>Nee</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>insluiten</td>
   <td>java.util.List</td>
   <td>Nee</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>failOnMissingEmbed</td>
   <td>boolean</td>
   <td>Ja</td>
   <td>false</td>
   <td>Een waarde van waar veroorzaakt de bouwstijl om te ontbreken wanneer een ingebed artefact niet in de projectgebiedsdelen wordt gevonden. Bij een gesaldeerde waarde wordt de fout genegeerd.</td>
  </tr>
  <tr>
   <td>filterSource</td>
   <td>java.io.File</td>
   <td>Nee</td>
   <td></td>
   <td>Een bestand dat de bron van het werkruimtefilter aangeeft. De filters die in de configuratie worden opgegeven en via inbedden of subpakketten worden geïnjecteerd, worden samengevoegd met de bestandsinhoud.</td>
  </tr>
  <tr>
   <td>filters</td>
   <td>com.day.jcr.<br /> vault.maven.pack.impl.<br /> DefaultWorkspaceFilter</td>
   <td>Nee</td>
   <td></td>
   <td>Bevat filterelementen die de pakketinhoud definiëren. Wanneer deze worden uitgevoerd, worden de filters opgenomen in het bestand filter.xml. Zie de sectie Filters gebruiken hieronder.</td>
  </tr>
  <tr>
   <td>finalName</td>
   <td>java.lang.String</td>
   <td>Ja</td>
   <td>De finalName die in het Maven project (bouwstijlfase) wordt bepaald.</td>
   <td>De naam van het gegenereerde pakket-ZIP-bestand, zonder de ZIP-bestandsextensie.</td>
  </tr>
  <tr>
   <td> groep</td>
   <td>java.lang.String</td>
   <td>Ja</td>
   <td>The groupID defined in the Maven project.</td>
   <td>De groupId van het gegenereerde inhoudspakket. Deze waarde maakt deel uit van het doelinstallatiepad voor het inhoudspakket.</td>
  </tr>
  <tr>
   <td>outputDirectory</td>
   <td>java.io.File</td>
   <td>Ja</td>
   <td>De bouwstijlfolder die in het Maven project wordt bepaald.</td>
   <td>De lokale map waar het inhoudspakket is opgeslagen.</td>
  </tr>
  <tr>
   <td>prefix</td>
   <td>java.lang.String</td>
   <td>Nee</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>project</td>
   <td>org.apache.maven.<br /> project.MavenProject</td>
   <td>Ja</td>
   <td></td>
   <td>Het Maven-project.</td>
  </tr>
  <tr>
   <td>eigenschappen</td>
   <td>java.util.Map</td>
   <td>Nee</td>
   <td></td>
   <td>Aanvullende eigenschappen die u kunt instellen in het bestand properties.xml. Deze eigenschappen kunnen de volgende vooraf gedefinieerde eigenschappen niet overschrijven:
    <ul>
     <li>groep: Groepsparameter gebruiken om in te stellen</li>
     <li>naam: Naamparameter gebruiken om in te stellen</li>
     <li>versie: Set met versieparameter</li>
     <li>beschrijving: Instellen op basis van de projectbeschrijving</li>
     <li>groupId: groupId van de Maven-projectdescriptor</li>
     <li>artefactId: artifactId van de Maven-projectdescriptor</li>
     <li>afhankelijkheden: Te plaatsen gebiedsparameter gebruiken</li>
     <li>createdBy: De waarde van het user.name systeembezit</li>
     <li>gemaakt: De huidige systeemtijd</li>
     <li>requiresRoot: De parameter requiresRoot gebruiken om in te stellen</li>
     <li>packagePath: Automatisch gegenereerd op basis van de groep- en pakketnaam</li>
    </ul> </td>
  </tr>
  <tr>
   <td>requiresRoot</td>
   <td>boolean</td>
   <td>Ja</td>
   <td>false</td>
   <td>Definieert of het pakket root vereist. Dit wordt de eigenschap &lt;code&gt;requiresRoot&lt;/code&gt; van het bestand properties.xml.</td>
  </tr>
  <tr>
   <td>subpakketten</td>
   <td>java.util.List</td>
   <td>Nee</td>
   <td></td>
   <td></td>
  </tr>
  <tr>
   <td>version</td>
   <td>java.lang.String</td>
   <td>Ja</td>
   <td>De versie die is gedefinieerd in het Maven-project</td>
   <td>De versie van het inhoudspakket.</td>
  </tr>
  <tr>
   <td>workDirectory</td>
   <td>java.io.File</td>
   <td>Ja</td>
   <td>De folder die in het Maven project (bouwstijlfase) wordt bepaald.</td>
   <td>De map die de inhoud bevat die in het pakket moet worden opgenomen.</td>
  </tr>
 </tbody>
</table>

#### Filters gebruiken {#using-filters}

Gebruik het element filters om de pakketinhoud te definiëren. De filters worden toegevoegd aan het element workspaceFilter in het `META-INF/vault/filter.xml` bestand van het pakket.

In het volgende filtervoorbeeld wordt de XML-structuur getoond die moet worden gebruikt:

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode>
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

**Importmodus**

Het `mode` element bepaalt hoe de inhoud de bewaarplaats wordt beïnvloed wanneer het pakket wordt ingevoerd. De volgende waarden kunnen worden gebruikt:

* **** Samenvoegen: Inhoud in het pakket die zich nog niet in de opslagplaats bevindt, wordt toegevoegd. De inhoud in zowel het pakket als de opslagplaats blijft ongewijzigd. Er wordt geen inhoud uit de opslagplaats verwijderd.
* **** Vervangen: Inhoud in het pakket die zich niet in de opslagplaats bevindt, wordt toegevoegd aan de opslagplaats. Inhoud in de opslagplaats wordt vervangen door overeenkomende inhoud in het pakket. Inhoud wordt verwijderd uit de opslagplaats wanneer deze niet bestaat in het pakket.
* **** Bijwerken: Inhoud in het pakket die zich niet in de opslagplaats bevindt, wordt toegevoegd aan de opslagplaats. Inhoud in de opslagplaats wordt vervangen door overeenkomende inhoud in het pakket. Bestaande inhoud wordt verwijderd uit de opslagplaats.

Wanneer het filter geen `mode` element bevat, wordt de standaardwaarde van `replace` gebruikt.

#### Voorbeeld {#example-5}

In het volgende voorbeeld wordt een pakket gemaakt dat de OSGi-bundel voor de workflow bevat. Het POM-bestand identificeert de map jcr_root als de waarde van de eigenschap builtContentDirectory. De map jcr_root bevat het JAR-bundelbestand in de mappenstructuur die de repository spiegelt:

`jcr_root/apps/myapp/install/workflow-mbean-0.03-SNAPSHOT.jar`

Omdat het doel aan het pakket verbindend is bouwt fase, voert het volgende bevel het pakketdoel uit:

`mvn package`

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>

  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>package</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```

In plaats van het `package` doel uit te drukken in de `executions` sectie insteekmodule, kunt u `content-package` als waarde van het `packaging` projectelement gebruiken:

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0"
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>
  <packaging>content-package</packaging>
  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

### help {#help}

#### Parameters {#parameters-6}

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| detail | boolean | Nee | false | Bepaalt of om alle settable eigenschappen voor elk doel te tonen. De waarde true geeft alle settable-eigenschappen weer. |
| doel | Tekenreeks | Nee |  | De naam van het doel waarvoor om hulp te tonen. Als geen waarde wordt gespecificeerd, wordt de hulp voor alle doelstellingen getoond. |
| indentSize | int | Nee | 2 | Het aantal spaties dat moet worden gebruikt voor de inspringing van elk niveau. Als u een waarde opgeeft, moet de waarde positief zijn. |
| lineLength | int | Nee | 80 | De maximumlengte van een weergavelijn. Als u een waarde opgeeft, moet de waarde positief zijn. |

## De insteekmodule voor het inhoudspakket verkrijgen {#obtaining-the-content-package-maven-plugin}

De insteekmodule is beschikbaar in de openbare opslagplaats van Adobe. Als u de plug-in wilt downloaden, voegt u het volgende Maven-profiel toe aan het Maven-instellingenbestand en activeert u dit. Wanneer u een Maven-opdracht gebruikt, wordt de plug-in zo nodig gedownload naar de lokale opslagplaats.

>[!NOTE]
>
>In de Adobe Public Releases-opslagplaats kan niet worden gebladerd, zodat het navigeren naar de URL van de opslagplaats met uw webbrowser resulteert in een fout Niet gevonden. Maven heeft echter wel toegang tot de directory&#39;s van de repository.

```xml
<profile>
    <id>adobe-public</id>
    <activation>
         <activeByDefault>false</activeByDefault>
    </activation>
    <properties>
         <releaseRepository-Id>adobe-public-releases</releaseRepository-Id>
         <releaseRepository-Name>Adobe Public Releases</releaseRepository-Name>
         <releaseRepository-URL>https://repo.adobe.com/nexus/content/groups/public</releaseRepository-URL>
    </properties>
    <repositories>
         <repository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
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
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
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

## OSGi-bundels insluiten in een inhoudspakket {#embedding-osgi-bundles-in-a-content-package}

Gebruik de Inhoudspakket Geweven insteekmodule om OSGi-bundels in te sluiten in het inhoudspakket. Implementeer de volgende configuraties om de bundel in te sluiten:

* De bundel moet worden gedeclareerd als een afhankelijkheid van het Maven-project.
* De insteekmoduleconfiguratie verwijst naar de bundel met behulp van het gewenste pad van de bundel in het pakket.

In het volgende voorbeeld maakt POM een pakket dat de Apache Sling JCR UserManager-bundel bevat. In het pakket bevindt de bundel JAR zich in de `jcr_root/apps/myapp/install` map:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0"
             xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
             https://maven.apache.org/maven-v4_0_0.xsd">
 <modelVersion>4.0.0</modelVersion>
   <groupId>com.adobe.example.myapp</groupId>
 <artifactId>embedded-example</artifactId>
 <packaging>content-package</packaging>
 <version>1.0.0-SNAPSHOT</version>

   <build>
 <plugins>
     <plugin>
        <groupId>com.day.jcr.vault</groupId>
      <artifactId>content-package-maven-plugin</artifactId>
      <version>0.0.24</version>
      <extensions>true</extensions>
      <configuration>
   <filters>
       <filter>
    <root>/apps/myapp</root>
       </filter>
    </filters>
    <embeddeds>
       <embedded>
    <groupId>org.apache.sling</groupId>
    <artifactId>org.apache.sling.jcr.jackrabbit.usermanager</artifactId>
    <target>/apps/myproject/install</target>
        </embedded>
    </embeddeds>
       </configuration>
  </plugin>
    </plugins>
    </build>
    <dependencies>
 <dependency>
      <groupId>org.apache.sling</groupId>
      <artifactId>org.apache.sling.jcr.jackrabbit.usermanager</artifactId>
      <version>2.2.0</version>
 </dependency>
    </dependencies>
</project>
```

## Een miniatuurafbeelding of eigenschappenbestand opnemen in het pakket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Vervang de standaardpakketconfiguratiebestanden om de pakketeigenschappen aan te passen. Neem bijvoorbeeld een miniatuurafbeelding om het pakket te onderscheiden in Pakketbeheer en Delen van pakket.

In het pakket bevinden FileVault-specifieke bestanden zich in de map /META-INF/vault. U kunt de bronbestanden overal in uw bestandssysteem vinden. Definieer in het POM-bestand build-resources om de bronbestanden naar het doel/vault-work/META-INF te kopiëren voor opname in het pakket.

De volgende POM-code voegt de bestanden in de map META-INF van de projectbron toe aan het pakket:

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

Met de volgende POM-code wordt alleen een miniatuurafbeelding aan het pakket toegevoegd. De miniatuurafbeelding moet de naam thumbnail.png hebben en zich in de map META-INF/vault/definition van het pakket bevinden. In dit voorbeeld bevindt het bronbestand zich in de map /src/main/content/META-INF/vault/definition van het project:

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## Archetypen gebruiken om AEM-projecten te genereren {#using-archetypes-to-generate-aem-projects}

Verschillende Maven-archetypen zijn beschikbaar voor het genereren van AEM-projecten. Gebruik het archetype dat met uw ontwikkelingsdoelstellingen beantwoordt:

* A content package that install resources for a AEM application: [simple-content-package-archetype](#simple-content-package-archetype)
* A content package that includes third party artifacts: [simple-content-package-with-embedded-archetype](#simple-content-package-with-embedded-archetype).
* Een meermoduletoepassing die de ontwikkeling van klassen Java en eenheidstests aanpast: [multimodule-content-package-archetype](#multimodule-content-package-archetype).

>[!NOTE]
>
>Het Apache Sling-project biedt ook archetypen die nuttig zijn voor de ontwikkeling van AEM. Deze zijn te vinden op [https://sling.apache.org/site/maven-archetypes.html](https://sling.apache.org/documentation/development/maven-archetypes.html).

Elk archetype produceert de volgende punten:

* De structuur van de projectmap.
* POM-bestanden.
* FileVault-configuratiebestanden.

Artefacten met type Archetype zijn beschikbaar in de openbare gegevensopslagruimte van Adobe. Als u een archetype wilt downloaden en uitvoeren, identificeert u het archetype en de Adobe-opslagplaats met behulp van de parameters van de Maven archetype:generate-opdracht:

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId={id_of_archetype} -DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

De Maven archetype plugin gebruikt interactieve wijze in shell of bevelherinnering om informatie over uw project te verzamelen. De informatie die u verstrekt wordt gebruikt om diverse projecteigenschappen, zoals omslagnamen en artefactidentiteitskaart te vormen.

**POM-bestanden**

De gegenereerde POM-bestanden bevatten opdrachten voor het compileren van code, het maken van bundels en het implementeren van deze bestanden naar AEM in pakketten. De `groupID`, `artifactId`, `version`, en `name` eigenschappen van het Geweven project worden automatisch bevolkt gebruikend de waarden die u aan de GMaven `archetype:generate` interactieve herinnering verstrekt.

U kunt de volgende standaardwaarden in het gegenereerde pom.xml-bestand wijzigen:

* De naam van de CQ-server of het IP-adres: De standaardwaarde is `localhost`. Het `crx.host` element hieronder `project/properties` bevat deze waarde.

* Het poortnummer voor de CQ-server: De standaardwaarde is `4502`. Het `crx.port` element hieronder `project/properties` bevat deze waarde.

* De versie van Content Package Maven Plugin: Gebruik de nieuwste versie als de inhoud van het `version` element voor de plug-in met `artifactId` van `content-package-maven-plugin`. De standaardwaarde is `0.0.24`.

**De archetypen gebruiken**

1. In een shell venster of bevelherinnering, ga het Geweven `archetype:generate` bevel in. Geef bij de aanwijzing waarden op voor de resterende parameters.

   Voor informatie over elke parameter, verwijs naar de sectie voor het archetype dat u gebruikt.

1. Met een teksteditor opent u het bestand pom.xml en bewerkt u de standaardwaarden op basis van uw vereisten.
1. De gegenereerde mappen vullen met bronnen.
1. Voer de `mvn clean install` opdracht in.

### simpleContent-package-archetype {#simple-content-package-archetype}

Maakt een gefabriceerd project dat geschikt is voor het installeren van bronnen voor een eenvoudige AEM-toepassing. De mapstructuur wordt gebruikt onder de `/apps` map van de AEM-opslagplaats. De POM definieert opdrachten voor het verpakken van de bronnen die u in de mappen plaatst en het installeren van de pakketten op de AEM-instantie.

**Artefacteigenschappen voor archetype:**

* Groep-id: `com.day.jcr.vault`
* Artefact-id: `simple-content-package-archetype`
* Versie: `1.0.2`
* Opslagplaats: `adobe-public-releases`

**Maven, opdracht:**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=simple-content-package-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**Parameters Archetype:**

* groupId: De groupId van het inhoudspakket dat Maven produceert. De waarde wordt automatisch gebruikt in het POM-bestand.
* artefactId: De naam van het inhoudspakket. De waarde wordt ook gebruikt als naam van de projectmap.
* versie:De versie van het inhoudspakket.
* pakket: Deze waarde wordt niet gebruikt voor simple-content-package-archetype.
* appsFolderName: De naam van de map hieronder /apps.
* artifactName: De beschrijving van het inhoudspakket.
* packageGroup: De naam van de inhoudspakketgroep. Deze waarde vormt de groepsparameter voor het doel van het Pakket van het Pakket van de Inhoud Gemaakte Insteekmodule.

**Mapstructuur:**

```xml
${artifactId}
   |- pom.xml
   |- README.txt
   |- src
      |- main
         |- content
             |- jcr_root
                 |- apps
                     |- ${appsFolderName}
                            |- components
                               |- .content.xml
                            |- config
                            |- install
             |- META-INF
                 |- vault
                     |- config.xml
                     |- filter.xml
                     |- nodetypes.cnd
                     |- properties.xml
                     |- definition
                        |- .content.xml
```

### simple-content-package-with-embedded-archetype {#simple-content-package-with-embedded-archetype}

Voert de zelfde taken uit zoals het simple-content-package-archetype, en ook downloadt en omvat een artefact van een openbare GeMaven bewaarplaats.

**Eigenschappen van bundel Archetype:**

* Groep-id: `com.day.jcr.vault`
* Artefact-id: `simple-content-package-with-embedded-archetype`
* Versie: `1.0.2`
* Opslagplaats: `adobe-public-releases`

**Maven, opdracht:**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=simple-content-package-with-embedded-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**Parameters Archetype:**

* groupId: De groupId van het inhoudspakket dat Maven produceert. De waarde wordt automatisch gebruikt in het POM-bestand.
* artefactId: De naam van het inhoudspakket. De waarde wordt ook gebruikt als naam van de projectmap.
* versie:De versie van het inhoudspakket.
* pakket: Deze parameter wordt niet gebruikt.
* appsFolderName: De naam van de map hieronder /apps.
* artifactName: De beschrijving van het inhoudspakket.
* embeddedArtifactId: De id van het artefact dat in het inhoudspakket moet worden ingesloten.
* embeddedGroupId: De groep-id van het artefact dat moet worden ingesloten.
* embeddedVersion: De versie van het artefact dat moet worden ingesloten.
* packageGroup: De naam van de inhoudspakketgroep. Deze waarde vormt de groepsparameter voor het doel van het Pakket van het Pakket van de Inhoud Gemaakte Insteekmodule.

**Mapstructuur:**

```xml
${artifactId}
   |- pom.xml
   |- README.txt
   |- src
      |- main
         |- content
             |- jcr_root
                 |- apps
                     |- ${appsFolderName}
                            |- components
                            |- config
                            |- install
             |- META-INF
                 |- vault
                     |- config.xml
                     |- filter.xml
                     |- nodetypes.cnd
                     |- properties.xml
                     |- definition
```

### multimodule-content-package-archetype {#multimodule-content-package-archetype}

Maakt een gemaven project dat de mapstructuur bevat voor het ontwikkelen van een AEM-toepassing en het installeren van bronnen op de server.

De `bundle` map bevat de mapstructuur waarin de Java- en JUnit-bronbestanden zijn opgeslagen die u ontwikkelt. Het bestand pom.xml in deze map maakt de OSGi-bundel. De volgende waarden in POM identificeren het artefact en de bundel:

* artifactID: `${artifactID}-bundle`.
* Bundle-SymbolicName: `${groupId}.${artifactId}-bundle`.

`${artifactID}` en `${groupId}` zijn de waarden die u voor deze parameters verstrekt wanneer het uitvoeren van de archetypes.

De `content` map bevat de bronnen die op de AEM-instantie zijn geïnstalleerd. De waarde van artifactID is `${artifactID}multimodule-bundle`.

De bovenliggende map bevat de bovenliggende POM die Maven-plug-ins en -afhankelijkheden beheert.

**Eigenschappen van bundel Archetype:**

* Groep-id: `com.day.jcr.vault`
* Artefact-id: `multimodule-content-package-archetype`
* Versie: `1.0.2`
* Opslagplaats: `adobe-public-releases`

**Maven, opdracht:**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=multimodule-content-package-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**Parameters Archetype:**

* groupId: De groupId van het inhoudspakket dat Maven produceert. De waarde wordt automatisch gebruikt in het POM-bestand.
* artefactId: De naam van het inhoudspakket. De waarde wordt ook gebruikt als naam van de projectmap.
* versie:De versie van het inhoudspakket.
* pakket: Deze waarde wordt niet gebruikt voor multimodule-content-package-archetype.
* appsFolderName: De naam van de map hieronder /apps.
* artifactName: De beschrijving van het inhoudspakket.
* packageGroup: De naam van de inhoudspakketgroep. Deze waarde vormt de groepsparameter voor het doel van het Pakket van het Pakket van de Inhoud Gemaakte Insteekmodule.

**Mapstructuur:**

```xml
${artifactId}
   |- pom.xml
   |- bundle
      |- pom.xml
      |- src
         |- main
            |- java
               |- ${groupId}
                  |- SimpleDSComponent.java
         |- test
            |- java
               |- ${groupId}
                  |- SimpleUnitTest.java
   |- content
      |- pom.xml
      |- src
         |- main
            |- content
               |- jcr_root
                  |- apps
                     |- ${appsFolderName}
                            |- config
                            |- install
                  |- META-INF
                      |- vault
                         |- config.xml
                         |- filter.xml
                         |- nodetypes.cnd
                         |- properties.xml
                         |- definition
                            |- .content.xml
```

