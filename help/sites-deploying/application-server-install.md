---
title: Installeren van toepassingsserver
description: Leer hoe u Adobe Experience Manager met een toepassingsserver installeert.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 3a90f1d2-e53f-4cc4-8122-024ad6500de0
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 0%

---

# Installeren van toepassingsserver{#application-server-install}

>[!NOTE]
>
>`JAR` en `WAR` zijn de bestandstypen waarin Adobe Experience Manager (AEM) wordt vrijgegeven. Deze formaten worden kwaliteitsborgd om de Adobe van steunniveaus aan te passen.
>

In deze sectie wordt uitgelegd hoe u Adobe Experience Manager (AEM) kunt installeren met een toepassingsserver. Raadpleeg de [&#x200B; Gesteunde sectie van Platforms &#x200B;](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) om over de specifieke steunniveaus te lezen die voor de individuele toepassingsservers worden verstrekt.

De installatiestappen van de volgende toepassingsservers worden beschreven:

* [WebSphere](#websphere)
* [JBoss](#jboss-eap)
* [Oracle WebLogic 12.1.3/12.2](#oracle-weblogic)
* [Tomcat 8/8.5](#tomcat)

Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over het installeren van webtoepassingen, serverconfiguraties en over het starten en stoppen van de server.

>[!NOTE]
>
>Als u Dynamic Media in een plaatsing van de OORLOG gebruikt, zie {de documentatie van 0} Dynamic Media [&#128279;](/help/assets/config-dynamic.md#enabling-dynamic-media).

## Algemene beschrijving {#general-description}

### Standaardgedrag bij het installeren van AEM in een toepassingsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wordt geleverd als één oorlogsbestand dat moet worden geïmplementeerd.

Indien opgesteld, gebeurt het volgende door gebrek:

* de uitvoermodus is `author`
* de instantie (Repository, Felix OSGI-omgeving, bundels, enzovoort) is geïnstalleerd in `${user.dir}/crx-quickstart` waar `${user.dir}` de huidige werkmap is. Dit pad naar crx-quickstart wordt `sling.home` genoemd.

* de hoofdmap van de context is bijvoorbeeld de naam van het oorlogsbestand, `aem-6`

#### Configuratie {#configuration}

U kunt het standaardgedrag als volgt wijzigen:

* uitvoeringsmodus: configureer de parameter `sling.run.modes` in het `WEB-INF/web.xml` -bestand van het AEM-oorlogsbestand vóór de implementatie

* sling.home: vorm de `sling.home` parameter in het `WEB-INF/web.xml` dossier van het AEM oorlogsdossier vóór plaatsing

* contextroot: naam van AEM oorlogsbestand wijzigen

#### Publish-installatie {#publish-installation}

Als u een publicatie-instantie wilt implementeren, moet u de uitvoeringsmodus instellen om te publiceren:

* De map WEB-INF/web.xml uit het AEM-oorlogsbestand verwijderen
* De parameter sling.run.modes wijzigen om te publiceren
* Het bestand web.xml opnieuw omzetten in AEM oorlogsbestand
* AEM oorlogsbestand implementeren

#### Installatiecontrole {#installation-check}

Om te controleren of alles is geïnstalleerd, kunt u:

* staart het `error.log` dossier om te zien dat al inhoud wordt geïnstalleerd
* in `/system/console` alle bundels geïnstalleerd zijn

#### Twee instanties op dezelfde toepassingsserver {#two-instances-on-the-same-application-server}

Voor demonstratiedoeleinden kan het aangewezen zijn om auteur te installeren en instantie in één toepassingsserver te publiceren. Hiervoor doet u het volgende:

1. Wijzig de variabelen sling.home en sling.run.modes van de publicatie-instantie.
1. Pak het bestand WEB-INF/web.xml uit van het AEM oorlogsbestand.
1. Wijzig sling.home in een ander pad (absolute en relatieve paden zijn mogelijk).
1. Wijzig sling.run.modes om te publiceren voor de publicatie-instantie.
1. Herhaal het bestand web.xml.
1. Wijzig de naam van de oorlogsbestanden, zodat ze verschillende namen hebben. De ene naam wordt bijvoorbeeld gewijzigd in aemauteur.war en de andere in aempublish.war.
1. Gebruik hogere geheugeninstellingen. Standaard AEM gebruiken bijvoorbeeld `-Xmx3072m`
1. Implementeer de twee webtoepassingen.
1. Na de Plaatsing houdt de twee Webtoepassingen tegen.
1. In zowel auteur- als publicatieinstanties zorgt u ervoor dat in de bestanden sling.properties de eigenschap felix.service.urlhandlers=false is ingesteld op false (de standaardwaarde is dat deze is ingesteld op true).
1. Start de twee webtoepassingen opnieuw.

## Installatieprocedures voor toepassingsservers {#application-servers-installation-procedures}

### WebSphere® 8.5 {#websphere}

Alvorens een plaatsing leest de [&#x200B; Algemene Beschrijving &#x200B;](#general-description) hierboven.

**Voorbereiding van de Server**

* Laat de Basiskopballen van de Auditie door overgaan:

   * Één manier om AEM te laten een gebruiker voor authentiek verklaren is de globale administratieve veiligheid van de server onbruikbaar te maken WebSphere®, om dit te doen: ga naar Veiligheid > Globale Veiligheid en uncheck Enable administratieve veiligheidscheckbox, sparen, en herstart de server.

* set `"JAVA_OPTS= -Xmx2048m"`
* Als u AEM wilt installeren met gebruik van contextroot = /, wijzigt u de basis van de context van de bestaande standaardwebtoepassing.

**opstellen AEM Webtoepassing**

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

Alvorens een plaatsing leest de [&#x200B; Algemene Beschrijving &#x200B;](#general-description) hierboven.

**bereidt server JBoss®** voor

Geheugenargumenten in uw conf-bestand instellen (bijvoorbeeld `standalone.conf`)

* JAVA_OPTS=&quot;-Xms64m -Xmx2048m&quot;

Als u de implementatiescanner gebruikt om de AEM webtoepassing te installeren, is het mogelijk goed om de waarde `deployment-timeout,` voor die set als attribuut `deployment-timeout` op te voeren in het XML-bestand van de instantie (bijvoorbeeld `configuration/standalone.xml)` :

```xml
<subsystem xmlns="urn:jboss:domain:deployment-scanner:1.1">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" deployment-timeout="1000"/>
</subsystem>
```

**opstellen AEM Webtoepassing**

* Upload de AEM webtoepassing in uw JBoss®-beheerconsole.

* Schakel de AEM webtoepassing in.

#### Oracle WebLogic 12.1.3/12.2 {#oracle-weblogic}

Alvorens een plaatsing leest de [&#x200B; Algemene Beschrijving &#x200B;](#general-description) hierboven.

Dit gebruikt een eenvoudige serverlay-out met slechts een Server Admin.

**Voorbereiding van de Server WebLogic**

* In `${myDomain}/config/config.xml` voeg aan de veiligheid-configuratie sectie toe:

   * `<enforce-valid-basic-auth-credentials>false</enforce-valid-basic-auth-credentials>` zie op [&#x200B; https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd &#x200B;](https://xmlns.oracle.com/weblogic/domain/1.0/domain.xsd) voor de correcte positie (per gebrek om het aan het eind van de sectie te plaatsen is o.k.)

* VM-geheugeninstellingen verhogen:

   * open `${myDomain}/bin/setDomainEnv.cmd` (resp.sh) zoekopdracht naar WLS_MEM_ARGS, stel bijvoorbeeld set `WLS_MEM_ARGS_64BIT=-Xms256m -Xmx2048m` in
   * WebLogic Server opnieuw starten

* Maak in `${myDomain}` een pakketmap en in een cq-map en maak er een overzichtsmap van

**opstellen AEM Webtoepassing**

* AEM bestand downloaden
* Plaats het AEM oorlogsdossier in $ {myDomain}/packages/cq omslag
* Maak uw configuraties in `WEB-INF/web.xml` indien nodig (zie hierboven in de Algemene beschrijving)

   * `WEB-INF/web.xml` -bestand uitpakken
   * de parameter sling.run.modes wijzigen om te publiceren
   * uncomment sling.home aanvankelijke parameter en reeks dit weg zoals u nodig hebt (zie Algemene Beschrijving)
   * Het bestand web.xml herstellen

* Implementeer AEM oorlogsbestand als een toepassing (voor de andere instellingen gebruikt u de standaardinstellingen)
* De installatie kan tijd in beslag nemen...
* Controleer of de installatie is voltooid zoals hierboven vermeld in de algemene beschrijving (bijvoorbeeld door te tikken op error.log)
* U kunt de hoofdmap van de context wijzigen op het tabblad Configuratie van de webtoepassing in de WebLogic `/console`

#### Tomcat 8/8.5 {#tomcat}

Alvorens een plaatsing leest de [&#x200B; Algemene Beschrijving &#x200B;](#general-description) hierboven.

* **bereidt de Server van Tomcat voor**

   * VM-geheugeninstellingen verhogen:

      * Voeg in `bin/catalina.bat` (resp. `catalina.sh` op UNIX®) de volgende instelling toe:
      * `set "JAVA_OPTS= -Xmx2048m`

   * Tomcat biedt geen toegang voor beheerders of beheerders bij de installatie. Daarom moet u `tomcat-users.xml` handmatig bewerken om toegang toe te staan voor deze accounts:

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

   * Als u AEM met contextwortel &quot;/&quot;wilt opstellen, dan moet u contextwortel van bestaande Webapp veranderen ROOT:

      * ROOT-webapp stoppen en verwijderen
      * Naam van map ROOT.war wijzigen in de map met webapps van Tomcat
      * Webapp opnieuw starten

   * Als u de AEM webtoepassing installeert met behulp van de manager-gui, moet u de maximale grootte van een geüpload bestand verhogen, aangezien de standaard alleen uploadgrootte van 50 MB toestaat. Open hiertoe web.xml van de manager Webtoepassing,

     `webapps/manager/WEB-INF/web.xml`

     en vergroot de max-file-size en max-request-size tot minstens 500 MB, zie het volgende `multipart-config` voorbeeld van zulk een `web.xml` dossier.

     ```xml
     <multipart-config>
     <!-- 500MB max -->
     <max-file-size>524288000</max-file-size>
     <max-request-size>524288000</max-request-size>
     <file-size-threshold>0</file-size-threshold>
     </multipart-config>
     ```

* **opstellen AEM Webtoepassing**

   * Download AEM oorlogsbestand.
   * Maak uw configuraties in web.xml indien nodig (zie hierboven in de Algemene Beschrijving).

      * WEB-INF/web.xml uitpakken.
      * Wijzig de parameter sling.run.modes die u wilt publiceren.
      * Verwijder de commentaarmarkering.home, eerste parameter, en stel dit pad naar wens in.
      * Herhaal het bestand web.xml.

   * Wijzig de naam AEM oorlogsbestand in ROOT.war als u het wilt implementeren als basiswebapp. Wijzig de naam in aemauthor.war als u een auteur als basis voor de context wilt hebben.
   * Kopieer het bestand naar de webapps-map van Tomcat.
   * Wacht tot AEM is geïnstalleerd.

## Problemen oplossen {#troubleshooting}

Voor informatie over het behandelen van kwesties die tijdens installatie kunnen verschijnen, zie:

* [Problemen oplossen](/help/sites-deploying/troubleshooting.md)
