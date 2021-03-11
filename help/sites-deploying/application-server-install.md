---
title: Installeren van toepassingsserver
seo-title: Installeren van toepassingsserver
description: Leer hoe u AEM met een toepassingsserver installeert.
seo-description: Leer hoe u AEM met een toepassingsserver installeert.
uuid: c9571f80-6ed1-46fe-b7c3-946658dfc3f4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 6fdce35d-2709-41cc-87fb-27a4b867e960
translation-type: tm+mt
source-git-commit: 4090b1641467c6fb02b2fcce4df97b9fd5da4e2f
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 0%

---


# Installeren van toepassingsserver{#application-server-install}

>[!NOTE]
>
>`JAR` en  `WAR` zijn de bestandstypen waarin AEM wordt vrijgegeven. Deze formaten ondergaan kwaliteitsgarantie om de steunniveaus aan te passen Adobe heeft toegezegd.


In deze sectie wordt uitgelegd hoe u Adobe Experience Manager (AEM) kunt installeren met een toepassingsserver. Raadpleeg de sectie [Ondersteunde Platforms](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) voor de specifieke supportniveaus voor de afzonderlijke toepassingsservers.

De installatiestappen van de volgende toepassingsservers worden beschreven:

* [WebSphere 8.5](#websphere)
* [JBoss EAP 6.3.0/6.4.0](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over het installeren van webtoepassingen, serverconfiguraties en over het starten en stoppen van de server.

>[!NOTE]
>
>Als u Dynamic Media gebruikt in een WAR-implementatie, raadpleegt u de [Dynamic Media-documentatie](/help/assets/config-dynamic.md#enabling-dynamic-media).

## Algemene beschrijving {#general-description}

### Standaardgedrag bij het installeren van AEM in een toepassingsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wordt geleverd als één oorlogsbestand dat moet worden geïmplementeerd.

Indien opgesteld zal het volgende door gebrek gebeuren:

* de uitvoeringsmodus is `author`
* de instantie (Repository, Felix OSGI-omgeving, bundels enz.) wordt geïnstalleerd in `${user.dir}/crx-quickstart`waarbij `${user.dir}` de huidige werkmap is, wordt dit pad naar crx-quickstart `sling.home` aangeroepen

* de hoofdmap van de context is de naam van het oorlogsbestand, bijvoorbeeld : `aem-6`

#### Configuratie {#configuration}

U kunt het standaardgedrag als volgt wijzigen:

* uitvoeringsmodus: configureren van de parameter `sling.run.modes` in het `WEB-INF/web.xml`-bestand van het AEM-oorlogsbestand vóór implementatie

* sling.home: configureer de parameter `sling.home` in het `WEB-INF/web.xml`bestand van het AEM-oorlogsbestand voor de implementatie

* contextbasis: naam van AEM oorlogsbestand wijzigen

#### Installatie {#publish-installation} publiceren

Als u een publicatie-instantie wilt implementeren, moet u de uitvoeringsmodus instellen voor publicatie:

* De map WEB-INF/web.xml uit het AEM oorlogsbestand verwijderen
* De parameter sling.run.modes wijzigen om te publiceren
* Het bestand web.xml opnieuw omzetten in AEM oorlogsbestand
* AEM oorlogsbestand implementeren

#### Installatiecontrole {#installation-check}

Om te controleren of alles is geïnstalleerd, kunt u:

* staart het `error.log`bestand om te zien dat alle inhoud is geïnstalleerd
* zie in `/system/console` dat alle bundels geïnstalleerd zijn

#### Twee instanties op dezelfde toepassingsserver {#two-instances-on-the-same-application-server}

Voor demonstratiedoeleinden kan het aangewezen zijn om auteur te installeren en instantie in één toepassingsserver te publiceren. Hiervoor doet u het volgende:

1. Wijzig de variabelen sling.home en sling.run.modes van de publicatie-instantie.
1. Pak het bestand WEB-INF/web.xml uit van het AEM oorlogsbestand.
1. Wijzig de parameter sling.home in een ander pad (absolute en relatieve paden zijn mogelijk).
1. Wijzig sling.run.modes om te publiceren voor de publicatie-instantie.
1. Herhaal het bestand web.xml.
1. Wijzig de naam van de oorlogsbestanden, zodat ze verschillende namen hebben: bijvoorbeeld de ene naam wordt gewijzigd in aemauteur.war en de andere in aempublish.war.
1. Gebruik hogere geheugeninstellingen, bijvoorbeeld voor standaardinstellingen AEM bijvoorbeeld: -Xmx3072m
1. Implementeer de twee webtoepassingen.
1. Na de Plaatsing houdt de twee Webtoepassingen tegen.
1. In zowel auteur- als publicatieinstanties zorgt u ervoor dat in de bestanden sling.properties de eigenschap felix.service.urlhandlers=false is ingesteld op false (de standaardwaarde is dat deze is ingesteld op true).
1. Start de twee webtoepassingen opnieuw.

## Installatieprocedures voor toepassingsservers {#application-servers-installation-procedures}

### WebSphere 8.5 {#websphere}

Lees voor een implementatie de bovenstaande [Algemene beschrijving](#general-description).

**Servervoorbereiding**

* Laat de Basiskopballen van de Auditie door overgaan:

   * Één manier om AEM te laten om een gebruiker voor authentiek te verklaren is de globale administratieve veiligheid van de server onbruikbaar te maken WebSphere, om dit te doen: Ga naar Beveiliging -> Algemene beveiliging en schakel het selectievakje Beheersbeveiliging inschakelen uit, sla de server op en start deze opnieuw.

* set `"JAVA_OPTS= -Xmx2048m"`
* Als u AEM wilt installeren met gebruik van contextroot = /, moet u eerst de hoofdmap van de context van de bestaande standaardwebtoepassing wijzigen

**AEM webtoepassing implementeren**

* AEM bestand downloaden
* Stel uw configuraties in web.xml indien nodig in (zie hierboven in de Algemene beschrijving)

   * WEB-INF/web.xml-bestand uitpakken
   * de parameter sling.run.modes wijzigen om te publiceren
   * uncomment sling.home aanvankelijke parameter en reeks dit pad aangezien u nodig hebt
   * Het bestand web.xml herstellen

* AEM oorlogsbestand implementeren

   * Kies een contextwortel (als u de sling looppaswijzen wilt plaatsen moet u de gedetailleerde stappen van de opstellen tovenaar selecteren, dan het specificeren in stap 6 van de tovenaar)

* AEM webtoepassing starten

#### JBoss EAP 6.3.0/6.4.0 {#jboss-eap}

Lees voor een implementatie de bovenstaande [Algemene beschrijving](#general-description).

**JBoss-server voorbereiden**

Geheugenargumenten in uw conf-bestand instellen (bijvoorbeeld `standalone.conf`)

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

als u de implementatie-scanner gebruikt om de AEM webtoepassing te installeren, is het mogelijk goed om de `deployment-timeout,` voor die set een `deployment-timeout`-kenmerk in het XML-bestand van uw instantie te verhogen (bijvoorbeeld `configuration/standalone.xml)`:

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**AEM webtoepassing implementeren**

* Upload de AEM webtoepassing in uw JBoss-beheerconsole.

* Schakel de AEM webtoepassing in.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Lees voor een implementatie de bovenstaande [Algemene beschrijving](#general-description).

Dit gebruikt een eenvoudige serverlay-out met slechts een Server Admin.

**WebLogic-servervoorbereiding**

* In `${myDomain}/config/config.xml`voeg aan de veiligheid-configuratie sectie toe:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` zie op  [https://xmlns.oracle.com/weblogic/domain/1.0/domain.](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) xsdfor de correcte positie (per gebrek om het aan het eind van de sectie te plaatsen is o.k.)

* VM-geheugeninstellingen verhogen:

   * open `${myDomain}/bin/setDomainEnv.cmd` (resp.sh) onderzoek naar WLS_MEM_ARGS, reeks b.v. `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m`
   * WebLogic Server opnieuw starten

* Maak in `${myDomain}` een pakketmap en in een cq-map en maak er een overzichtsmap in

**AEM webtoepassing implementeren**

* AEM bestand downloaden
* Plaats het AEM oorlogsdossier in ${myDomain}/packages/cq omslag
* Stel uw configuraties in `WEB-INF/web.xml` indien nodig in (zie hierboven in de Algemene Beschrijving)

   * `WEB-INF/web.xml`bestand uitpakken
   * de parameter sling.run.modes wijzigen om te publiceren
   * uncomment sling.home aanvankelijke parameter en reeks dit weg zoals u nodig hebt (zie Algemene Beschrijving)
   * Het bestand web.xml herstellen

* Implementeer AEM oorlogsbestand als een toepassing (voor de andere instellingen worden de standaardinstellingen gebruikt)
* De installatie kan tijd in beslag nemen...
* Controleer of de installatie is voltooid zoals hierboven vermeld in de algemene beschrijving (bijv. door op error.log te tikken)
* U kunt de basisinhoud van de context wijzigen op het tabblad Configuratie van de webtoepassing in de webtoepassing `/console`

#### Tomcat 8/8.5 {#tomcat}

Lees voor een implementatie de bovenstaande [Algemene beschrijving](#general-description).

* **Tomcat-server voorbereiden**

   * VM-geheugeninstellingen verhogen:

      * Voeg in `bin/catalina.bat` (resp. `catalina.sh` op unix) de volgende instelling toe:
      * `set "JAVA_OPTS= -Xmx2048m`
   * Tomcat biedt geen toegang voor beheerders of beheerders bij de installatie. Daarom moet u `tomcat-users.xml` manueel uitgeven om toegang voor deze rekeningen toe te staan:

      * Bewerk `tomcat-users.xml` om toegang voor beheerder en manager op te nemen. De configuratie zou gelijkaardig aan het volgende voorbeeld moeten kijken:

         ```xml
         <?xml version='1.0' encoding='utf-8'?>
         <tomcat-users>
         role rolename="manager"/>
         role rolename="tomcat"/>
         <role rolename="admin"/>
         <role rolename="role1"/>
         <role rolename="manager-gui"/>
         <user username="both" password="tomcat" roles="tomcat,role1"/>
         <user username="tomcat" password="tomcat" roles="tomcat"/>
         <user username="admin" password="admin" roles="admin,manager-gui"/>
         <user username="role1" password="tomcat" roles="role1"/>
         </tomcat-users>
         ```
   * Als u AEM wilt implementeren met contextroot &quot;/&quot;, moet u de hoofdmap van de context van de bestaande ROOT-webapp wijzigen:

      * ROOT-webapp stoppen en verwijderen
      * Naam van map ROOT.war wijzigen in de map webapps van Tomcat
      * Webapp opnieuw starten
   * Als u de AEM webtoepassing installeert met behulp van de manager-gui, moet u de maximale grootte van een geüpload bestand verhogen, aangezien de standaard alleen uploadgrootte van 50 MB toestaat. Open hiertoe web.xml van de manager Webtoepassing,

      `webapps/manager/WEB-INF/web.xml`

      en vergroot de max-file-size en maximum-request-size tot minstens 500MB, zie het volgende `multipart-config` voorbeeld van zulk een `web.xml` dossier.

      ```xml
      <multipart-config>
      <!-- 500MB max -->
      <max-file-size>524288000</max-file-size>
      <max-request-size>524288000</max-request-size>
      <file-size-threshold>0</file-size-threshold>
      </multipart-config>
      ```




* **AEM webtoepassing implementeren**

   * AEM bestand downloaden
   * Stel uw configuraties in web.xml indien nodig in (zie hierboven in de Algemene beschrijving)

      * WEB-INF/web.xml-bestand uitpakken
      * de parameter sling.run.modes wijzigen om te publiceren
      * uncomment sling.home aanvankelijke parameter en reeks dit pad aangezien u nodig hebt
      * Het bestand web.xml herstellen
   * Wijzig de naam van AEM oorlogsbestand in ROOT.war als u het wilt gebruiken als hoofdwebapp, en wijzig de naam van het bestand in bijvoorbeeld aemauthor.war als u de hoofdmap van de context als hoofdmap wilt gebruiken.
   * kopiëren naar de map met tomcat-webapps
   * wachten tot AEM is geïnstalleerd


## Problemen oplossen {#troubleshooting}

Voor informatie over het behandelen van kwesties die tijdens installatie kunnen verschijnen, zie:

* [Problemen oplossen](/help/sites-deploying/troubleshooting.md)
