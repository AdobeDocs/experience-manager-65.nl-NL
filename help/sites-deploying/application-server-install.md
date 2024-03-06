---
title: Installeren van toepassingsserver
description: Leer hoe u Adobe Experience Manager met een toepassingsserver installeert.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 3a90f1d2-e53f-4cc4-8122-024ad6500de0
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---

# Installeren van toepassingsserver{#application-server-install}

>[!NOTE]
>
>`JAR` en `WAR` zijn de bestandstypen waarin Adobe Experience Manager (AEM) wordt vrijgegeven. Deze formaten worden kwaliteitsborgd om de Adobe van steunniveaus aan te passen.
>

In deze sectie wordt uitgelegd hoe u Adobe Experience Manager (AEM) kunt installeren met een toepassingsserver. Raadpleeg de [Ondersteunde platforms](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) voor meer informatie over de specifieke supportniveaus die voor de afzonderlijke toepassingsservers zijn opgegeven.

De installatiestappen van de volgende toepassingsservers worden beschreven:

* [WebSphere](#websphere)
* [JBoss](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over het installeren van webtoepassingen, serverconfiguraties en over het starten en stoppen van de server.

>[!NOTE]
>
>Als u Dynamic Media gebruikt in een WAR-implementatie, raadpleegt u [Dynamic Media-documentatie](/help/assets/config-dynamic.md#enabling-dynamic-media).

## Algemene beschrijving {#general-description}

### Standaardgedrag bij het installeren van AEM in een toepassingsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wordt geleverd als één oorlogsbestand dat moet worden geïmplementeerd.

Indien opgesteld, gebeurt het volgende door gebrek:

* de uitvoeringsmodus is `author`
* de instantie (Repository, Felix OSGI-omgeving, bundels, enzovoort) is geïnstalleerd in `${user.dir}/crx-quickstart`waar `${user.dir}` Dit pad naar crx-quickstart wordt de huidige werkmap genoemd `sling.home`

* de hoofdmap van de context is bijvoorbeeld de naam van het oorlogsbestand;  `aem-6`

#### Configuratie {#configuration}

U kunt het standaardgedrag als volgt wijzigen:

* run mode: configure `sling.run.modes` in de `WEB-INF/web.xml` dossier van het AEM oorlogsdossier vóór plaatsing

* sling.home: configureer de `sling.home` in de `WEB-INF/web.xml`dossier van het AEM oorlogsdossier vóór plaatsing

* contextroot: naam van AEM oorlogsbestand wijzigen

#### Installatie publiceren {#publish-installation}

Als u een publicatie-instantie wilt implementeren, moet u de uitvoeringsmodus instellen om te publiceren:

* De map WEB-INF/web.xml uit het AEM-oorlogsbestand verwijderen
* De parameter sling.run.modes wijzigen om te publiceren
* Het bestand web.xml opnieuw omzetten in AEM oorlogsbestand
* AEM oorlogsbestand implementeren

#### Installatiecontrole {#installation-check}

Om te controleren of alles is geïnstalleerd, kunt u:

* staart `error.log`bestand om te controleren of alle inhoud is geïnstalleerd
* zoeken in `/system/console` dat alle bundels zijn geïnstalleerd

#### Twee instanties op dezelfde toepassingsserver {#two-instances-on-the-same-application-server}

Voor demonstratiedoeleinden kan het aangewezen zijn om auteur te installeren en instantie in één toepassingsserver te publiceren. Hiervoor doet u het volgende:

1. Wijzig de variabelen sling.home en sling.run.modes van de publicatie-instantie.
1. Pak het bestand WEB-INF/web.xml uit van het AEM oorlogsbestand.
1. Wijzig sling.home in een ander pad (absolute en relatieve paden zijn mogelijk).
1. Wijzig sling.run.modes om te publiceren voor de publicatie-instantie.
1. Herhaal het bestand web.xml.
1. Wijzig de naam van de oorlogsbestanden, zodat ze verschillende namen hebben. De ene naam wordt bijvoorbeeld gewijzigd in aemauteur.war en de andere in aempublish.war.
1. Gebruik hogere geheugeninstellingen. Standaard AEM instanties bijvoorbeeld `-Xmx3072m`
1. Implementeer de twee webtoepassingen.
1. Na de Plaatsing houdt de twee Webtoepassingen tegen.
1. In zowel auteur- als publicatieinstanties zorgt u ervoor dat in de bestanden sling.properties de eigenschap felix.service.urlhandlers=false is ingesteld op false (de standaardwaarde is dat deze is ingesteld op true).
1. Start de twee webtoepassingen opnieuw.

## Installatieprocedures voor toepassingsservers {#application-servers-installation-procedures}

### WebSphere® 8.5 {#websphere}

Voordat een implementatie de [Algemene beschrijving](#general-description) hierboven.

**Servervoorbereiding**

* Laat de Basiskopballen van de Auditie door overgaan:

   * Één manier om AEM te laten een gebruiker voor authentiek verklaren is de globale administratieve veiligheid van de server onbruikbaar te maken WebSphere®, om dit te doen: ga naar Veiligheid > Globale Veiligheid en uncheck Enable administratieve veiligheidscheckbox, sparen, en herstart de server.

* set `"JAVA_OPTS= -Xmx2048m"`
* Als u AEM wilt installeren met gebruik van contextroot = /, wijzigt u de basis van de context van de bestaande standaardwebtoepassing.

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

#### JBoss® EAP 6.3.0/6.4.0 {#jboss-eap}

Voordat een implementatie de [Algemene beschrijving](#general-description) hierboven.

**JBoss®-server voorbereiden**

Geheugenargumenten instellen in het conf-bestand (bijvoorbeeld `standalone.conf`)

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

Als u de implementatie-scanner gebruikt om de AEM webtoepassing te installeren, is het mogelijk verstandig om de `deployment-timeout,` voor die set `deployment-timeout` in het xml-bestand van uw instantie (bijvoorbeeld `configuration/standalone.xml)`:

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**AEM webtoepassing implementeren**

* Upload de AEM webtoepassing in uw JBoss®-beheerconsole.

* Schakel de AEM webtoepassing in.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Voordat een implementatie de [Algemene beschrijving](#general-description) hierboven.

Dit gebruikt een eenvoudige serverlay-out met slechts een Server Admin.

**WebLogic-servervoorbereiding**

* In `${myDomain}/config/config.xml`toevoegen aan de veiligheid-configuratie sectie:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` zie op [https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) voor de correcte positie (per gebrek om het aan het eind van de sectie te plaatsen is OK)

* VM-geheugeninstellingen verhogen:

   * open `${myDomain}/bin/setDomainEnv.cmd` (resp.sh) zoek naar WLS_MEM_ARGS, stel bijvoorbeeld een set in `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m`
   * WebLogic Server opnieuw starten

* Maken in `${myDomain}` een pakketmap en in een cq-map en daarin een overzichtsmap

**AEM webtoepassing implementeren**

* AEM bestand downloaden
* Zet het AEM oorlogsdossier in ${myDomain}/packages/cq folder
* Configuraties maken in `WEB-INF/web.xml` indien nodig (zie hierboven in de algemene beschrijving)

   * Uitpakken `WEB-INF/web.xml`file
   * de parameter sling.run.modes wijzigen om te publiceren
   * uncomment sling.home aanvankelijke parameter en reeks dit weg zoals u nodig hebt (zie Algemene Beschrijving)
   * Het bestand web.xml herstellen

* Implementeer AEM oorlogsbestand als een toepassing (voor de andere instellingen gebruikt u de standaardinstellingen)
* De installatie kan tijd in beslag nemen...
* Controleer of de installatie is voltooid zoals hierboven vermeld in de algemene beschrijving (bijvoorbeeld door te tikken op error.log)
* U kunt de basisinhoud van de context wijzigen op het tabblad Configuratie van de webtoepassing in de WebLogic `/console`

#### Tomcat 8/8.5 {#tomcat}

Voordat een implementatie de [Algemene beschrijving](#general-description) hierboven.

* **Tomcat-server voorbereiden**

   * VM-geheugeninstellingen verhogen:

      * In `bin/catalina.bat` (resp. `catalina.sh` op UNIX®) voeg de volgende instelling toe:
      * `set "JAVA_OPTS= -Xmx2048m`

   * Tomcat biedt geen toegang voor beheerders of beheerders bij de installatie. Daarom moet u handmatig bewerken `tomcat-users.xml` deze rekeningen toegankelijk te maken:

      * Bewerken `tomcat-users.xml` toegang voor beheerder en manager op te nemen. De configuratie zou gelijkaardig aan het volgende voorbeeld moeten kijken:

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

   * Als u AEM met contextwortel &quot;/&quot;wilt opstellen, dan moet u contextwortel van bestaande Webapp veranderen ROOT:

      * ROOT-webapp stoppen en verwijderen
      * Naam van map ROOT.war wijzigen in de map met webapps van Tomcat
      * Webapp opnieuw starten

   * Als u de AEM webtoepassing installeert met behulp van de manager-gui, moet u de maximale grootte van een geüpload bestand verhogen, aangezien de standaard alleen uploadgrootte van 50 MB toestaat. Open hiertoe web.xml van de manager Webtoepassing,

     `webapps/manager/WEB-INF/web.xml`

     en vergroot de maximale bestandsgrootte en maximale aanvraaggrootte tot minstens 500 MB. Raadpleeg de volgende secties `multipart-config` voorbeeld van een dergelijke `web.xml` bestand.

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

   * Wijzig de naam van AEM oorlogsbestand in ROOT.war als u het wilt gebruiken als hoofdwebapp, wijzig de naam van het bestand in bijvoorbeeld aemauthor.war als u een hoofdmap van de context wilt hebben
   * kopiëren naar de map met tomcat-webapps
   * wachten tot AEM is geïnstalleerd

## Problemen oplossen {#troubleshooting}

Voor informatie over het behandelen van kwesties die tijdens installatie kunnen verschijnen, zie:

* [Problemen oplossen](/help/sites-deploying/troubleshooting.md)
