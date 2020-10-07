---
title: Implementeren en onderhouden
seo-title: Implementeren en onderhouden
description: Leer hoe u aan de slag gaat met de AEM-installatie.
seo-description: Leer hoe u aan de slag gaat met de AEM-installatie.
uuid: 4429ac4d-abd7-47d8-b19d-773accb7cc7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: e48cc0ed-688c-44c8-b6d6-5f3c8593a295
docset: aem65
translation-type: tm+mt
source-git-commit: cb07e24b01084f57ad46615cb463ad5a0329c181
workflow-type: tm+mt
source-wordcount: '1833'
ht-degree: 1%

---


# Implementeren en onderhouden{#deploying-and-maintaining}

Op deze pagina vindt u:

* [Basisconcepten](#basic-concepts)

   * [Wat is AEM?](#what-is-aem)
   * [Typische implementaties](#typical-deployment-scenarios)

      * [Op locatie](#on-premise)
      * [Managed Services met Cloud Manager](#managed-services-using-cloud-manager)

* [Aan de slag](#getting-started)

   * [Vereisten](#prerequisites)
   * [De software ophalen](#getting-the-software)
   * [Standaard lokale installatie](#default-local-install)
   * [Auteur- en publicatie-installaties](#author-and-publish-installs)
   * [Onverpakte installatiemap](#unpacked-install-directory)
   * [Starten en stoppen](#starting-and-stopping)

Als u zich vertrouwd hebt gemaakt met deze basisbeginselen, vindt u meer geavanceerde en gedetailleerde informatie op de volgende subpagina&#39;s:

* [Technische vereisten](/help/sites-deploying/technical-requirements.md)
* [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md)
* [Aangepaste standalone installatie](/help/sites-deploying/custom-standalone-install.md)
* [Installeren van toepassingsserver](/help/sites-deploying/application-server-install.md)
* [Problemen oplossen](/help/sites-deploying/troubleshooting.md)
* [Start en stop opdrachtregel](/help/sites-deploying/command-line-start-and-stop.md)
* [Configureren](/help/sites-deploying/configuring.md)
* [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/sites-deploying/ecommerce.md)
* [Hoe kan ik-artikelen configureren](/help/sites-deploying/ht-deploy.md)
* [Webconsole](/help/sites-deploying/web-console.md)
* [Problemen met replicatie oplossen](/help/sites-deploying/troubleshoot-rep.md)
* [Best practices voor](/help/sites-deploying/best-practices.md)
* [Gemeenschappen inzetten](/help/communities/deploy-communities.md)
* [Inleiding tot het AEM Platform](/help/sites-deploying/platform.md)
* [Richtlijnen voor prestaties](/help/sites-deploying/performance-guidelines.md)
* [Aan de slag met AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Wat is AEM Screens?](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)

## Basisconcepten {#basic-concepts}

### Wat is AEM? {#what-is-aem}

Adobe Experience Manager is een op het web gebaseerd clientserversysteem voor het bouwen, beheren en implementeren van commerciële websites en gerelateerde services. Het combineert een aantal infrastructuur-niveau en toepassing-vlakke functies in één enkel geïntegreerd pakket.

Op het niveau van de infrastructuur biedt AEM het volgende:

* **Webtoepassingsserver**: AEM kunnen in zelfstandige modus worden geïmplementeerd (inclusief een geïntegreerde Jetty-webserver) of als een webtoepassing binnen een externe toepassingsserver.
* **Web Application Framework**: AEM neemt het het Verdelen Kader van de Toepassing van het Web op dat het schrijven van RESTful, tevreden-georiënteerde Webtoepassingen vereenvoudigt.
* **Inhoudsopslagplaats**: AEM bevat een JCR (Java Content Repository), een soort hiërarchische database die speciaal is ontworpen voor ongestructureerde en semi-gestructureerde gegevens. De dataopslag slaat niet alleen de gebruikersgerichte inhoud op, maar ook alle code, sjablonen en interne gegevens die door de toepassing worden gebruikt.

Op basis van deze basis biedt AEM ook een aantal functies op toepassingsniveau voor het beheer van:

* **Websites**
* **Mobiele toepassingen**
* **Digitale publicaties**
* **Forms**
* **Digitale middelen**
* **Gemeenschappen**
* **Online Commerce**

Tot slot kunnen de klanten deze infrastructuur en toepassing-vlakke bouwstenen gebruiken om aangepaste oplossingen tot stand te brengen door toepassingen van hun te bouwen.

De AEM server is gebaseerd **op** Java en wordt uitgevoerd op de meeste besturingssystemen die dat platform ondersteunen. Alle clientinteractie met AEM vindt plaats via een **webbrowser**.

### Typische implementatiescenario&#39;s {#typical-deployment-scenarios}

In AEM terminologie is een &quot;instantie&quot;een exemplaar van AEM die op een server loopt. AEM installaties omvatten meestal ten minste twee instanties, die doorgaans op afzonderlijke machines worden uitgevoerd:

* **Auteur**: Een AEM die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
* **Publiceren**: Een AEM instantie die de gepubliceerde inhoud aan het publiek aanbiedt.

Deze exemplaren zijn identiek wat geïnstalleerde software betreft. Ze worden alleen gedifferentieerd naar configuratie. Bovendien gebruiken de meeste installaties een verzender:

* **Verzender**: Een statische webserver (Apache httpd, Microsoft IIS, enz.) aangevuld met de AEM dispatchermodule. Webpagina&#39;s die door de instantie publish worden gemaakt, worden in het cachegeheugen opgeslagen om de prestaties te verbeteren.

Er zijn vele geavanceerde opties en uitbreidingen van deze opstelling, maar het basispatroon van auteur, publiceert en verzender is de kern van de meeste plaatsingen. We zullen ons eerst concentreren op een relatief eenvoudige opzet. Hierna zullen de geavanceerde implementatieopties worden besproken.

In de volgende secties worden beide scenario&#39;s beschreven:

* **Op locatie**: AEM geïmplementeerd en beheerd in uw bedrijfsomgeving.

* **Managed Services - Cloud Manager voor Adobe Experience Manager**: AEM geïmplementeerd en beheerd door Adobe Managed Services.

### On-premise {#on-premise}

U kunt AEM installeren op servers in uw bedrijfsomgeving. Voorbeelden van gebruikelijke installatiematerialen zijn: Ontwikkelings-, test- en publicatieomgevingen. Raadpleeg de sectie [Aan de slag](/help/sites-deploying/deploy.md#getting%20started) voor basisinformatie over hoe u de AEM software kunt installeren.

Meer over de typische plaatsingen op-gebouw leren, verwijs naar [Aanbevolen Plaatsingen](/help/sites-deploying/recommended-deploys.md).

### Managed Services met Cloud Manager {#managed-services-using-cloud-manager}

AEM Managed Services is een complete oplossing voor Digital Experience Management. Het biedt voordelen van een oplossing voor het leveren van ervaring in de cloud, terwijl alle voordelen van controle, beveiliging en aanpassing van een on-premise implementatie behouden blijven. AEM Managed Services stelt klanten in staat sneller te starten door te implementeren in de cloud en ook door te leren van de beste praktijken en ondersteuning van Adobe. Organisaties en zakelijke gebruikers kunnen hun klanten zo weinig mogelijk tijd in dienst nemen, hun marktaandeel vergroten en zich richten op het maken van innovatieve marketingcampagnes en tegelijk de last voor de IT-afdeling verminderen.

Met AEM Managed Services kunnen klanten de volgende voordelen realiseren:

**Snellere marktintroductie:** Met de flexibele cloudinfrastructuur van Adobe Managed Services kunnen organisaties snel succesvolle digitale ervaringen plannen, lanceren en optimaliseren. Adobe beheert de cloudarchitectuur zonder extra kapitaal, hardware of software vereist en de Succestechnici van de Klant van Adobe, hulp met AEM architectuur, levering, aanpassing voor het verbinden met back-end apps en go-live beste praktijken.

**Hogere prestaties:** Verstrekt betrouwbare digitale ervaringen voor uw zaken met vier opties van de de dienstbeschikbaarheid 99.5%, 99.9%, 99.95%, en 99.99%. Bovendien maakt het automatische back-up en multimode modellen voor noodherstel mogelijk om betrouwbaarheid en noodbeheer te garanderen.

**Geoptimaliseerde IT-kosten:** Met proactieve begeleiding en expertise kunnen organisaties de nieuwste versie van AEM gebruiken. Adobe Platinum-onderhoud en -support worden automatisch opgenomen in nieuwe implementaties van AMS Enterprise/Basic en bieden technische expertise en operationele ervaring om organisaties te helpen hun bedrijfskritieke toepassingen te onderhouden. Gratis basisanalysemogelijkheden of doelmogelijkheden bieden extra waarde, met name voor organisaties uit het midden- en kleinbedrijf die weinig behoefte hebben aan analyses en personalisatie.

**Hoogste beveiliging:** Zorgt voor fysieke beveiliging, netwerk en gegevensbeveiliging op bedrijfsniveau door klantentoepassingen te hosten in een beperkte-toegangsfaciliteit, achter firewallsystemen, of binnen een virtuele privécloud. Het omvat virtuele machines van één huurder met robuuste gegevensopslagencryptie, antivirale middelen, en gegevensisolatie.

**Wolkenbeheer**: Cloud Manager, een onderdeel van de Adobe Experience Manager Managed Services-aanbieding, is een zelfbedieningsportaal waarmee organisaties Adobe Experience Manager in de cloud verder kunnen beheren. Het omvat een geavanceerde ononderbroken integratie en ononderbroken levering (CI/CD) pijpleiding die de teams van IT en implementatiepartners de levering van aanpassingen of updates laat versnellen zonder prestaties of veiligheid te compromitteren. Cloud Manager is alleen beschikbaar voor Adobe Managed Service-klanten.

Raadpleeg de gebruikershandleiding voor [**Cloud Manager voor meer informatie over Cloud Manager en de bijbehorende bronnen**](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html).

## Aan de slag {#getting-started}

### Vereisten {#prerequisites}

Terwijl de productie instanties gewoonlijk op specifieke machines in werking stellen die een officieel gesteund OS (zie [Technische Vereisten](/help/sites-deploying/technical-requirements.md)) in werking stellen, zal de server van de Experience Manager eigenlijk op om het even welk systeem lopen dat [**StandaardUitgave 8**](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)van Java steunt.

Voor vertrouwdmaking en voor het ontwikkelen op AEM is het vrij gebruikelijk om een instantie te gebruiken die op uw lokale computer wordt geïnstalleerd die Apple OS X of Desktopversies van Microsoft Windows of Linux in werking stelt.

Op de client-kant werkt AEM met alle moderne browsers (**Microsoft Edge**, **Internet Explorer** 11, **Chrome **51+** **, **Firefox **47+, **Safari** 8+) op zowel desktop- als tabletbesturingssystemen. Zie [Ondersteunde clientPlatforms](/help/sites-deploying/technical-requirements.md#supported-client-platforms) voor meer informatie.

### De software ophalen {#getting-the-software}

Klanten met een geldig onderhouds- en ondersteuningscontract moeten een e-mailmelding met een code hebben ontvangen en AEM kunnen downloaden van de [**Adobe Licensing Website**](https://licensing.adobe.com/). Zakelijke partners kunnen om toegang tot het downloaden vragen via [**spphelp@adobe.com**](mailto:spphelp@adobe.com).

Het softwarepakket AEM is beschikbaar in twee formulieren:

* **cq-quickstart-6.5.0.jar:** Een zelfstandig uitvoerbaar *jar* -bestand dat alles bevat wat nodig is om aan de slag te gaan.

* **cq-quickstart-6.5.0.war:** Een *oorlogsdossier* voor plaatsing in een server van de derdetoepassing.

In de volgende sectie beschrijven wij de **standalone installatie**. Zie [Application Server Install](/help/sites-deploying/application-server-install.md)voor meer informatie over het installeren van AEM in een toepassingsserver.

### Standaard lokale installatie {#default-local-install}

1. Maak een installatiemap op uw lokale computer. Bijvoorbeeld:

   Installatielocatie UNIX: **/opt/aem**

   Installatielocatie voor Windows: **`C:\Program Files\aem`**

   Het is ook gebruikelijk om voorbeeldexemplaren in een map rechts op het bureaublad te installeren. In elk geval zullen wij deze plaats in het algemeen als volgt noemen:

   `<aem-install>`

   *Het pad van de bestandsmap mag alleen uit ASCII-tekens van de Verenigde Staten bestaan.*

1. Plaats de **jar** - en **license **files in deze directory:

   ```shell
   <aem-install>/
       cq-quickstart-6.5.0.jar
       license.properties
   ```

   Als u geen `license.properties` bestand opgeeft, leidt AEM de browser bij het opstarten om naar een **welkomstscherm** , waar u een licentiecode kunt invoeren. U moet een geldige licentiecode aanvragen bij Adobe als u die nog niet hebt.

1. Als u de instantie wilt starten in een GUI-omgeving, dubbelklikt u op het **`cq-quickstart-6.5.0.jar`** bestand.

   U kunt ook AEM starten vanaf de opdrachtregel. Voer voor een 32-bits Java VM het volgende in:

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.5.0.jar
   ```

   Voer voor een 64-bits VM het volgende in:

   ```shell
       java -XX:MaxPermSize=256m -Xmx1024M -jar cq-quickstart-6.5.0.jar
   ```

AEM neemt enkele minuten in beslag om het jar-bestand uit te pakken, zelf te installeren en op te starten. Deze procedure leidt tot:

* een **AEM instantie** van de auteur
* uitvoeren op **localhost**
* over poort **4502**

Als u toegang wilt tot de instantie, richt u de browser op:

**`https://localhost:4502`**

Het resultaat in auteurinstantie zal automatisch worden gevormd om met een **publicatieinstantie** te verbinden op **`localhost:4503`**.

### Auteur- en publicatie-installaties {#author-and-publish-installs}

De standaardinstallatie (een **auteurinstantie** op **`localhost:4502`**) kan eenvoudig worden veranderd door het `jar` dossier anders te noemen alvorens het voor het eerst te lanceren. Het naamgevingspatroon is:

**`cq-<instance-type>-p<port-number>.jar`**

De naam van het bestand wijzigen in

**`cq-author-p4502.jar`**

en het lanceren van het zal in een auteursinstantie resulteren die loopt op **`localhost:4502`**.

Ook de naam van het bestand wijzigen en het bestand starten

**`cq-publish-p4503.jar`**

resulteert in een publicatie-instantie die wordt uitgevoerd **`localhost:4503`**.

U installeert deze twee varianten bijvoorbeeld in

`<aem-install>/author`and

**`<aem-install>/publish`**

Raadpleeg de volgende bronnen voor meer informatie over het aanpassen van de installatie:

* [Aangepaste standalone installatie](/help/sites-deploying/custom-standalone-install.md)
* [Modi uitvoeren](/help/sites-deploying/configure-runmodes.md)

### Onverpakte installatiemap {#unpacked-install-directory}

Wanneer de quickstart-jar voor de eerste keer wordt gestart, wordt deze zichzelf in dezelfde map uitgepakt onder een nieuwe submap met de naam `crx-quickstart`. U zou met het volgende moeten eindigen:

```xml
<aem-install>/
    license.properties
    cq-quickstart-6.5.0.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

Als de instantie is geïnstalleerd vanuit de gebruikersinterface, wordt automatisch een browservenster geopend en wordt ook een bureaubladtoepassingsvenster geopend met daarin de host en poort van de instantie en een aan/uit-schakelaar:

![opstartscherm](assets/screen_shot_.png)

>[!NOTE]
>
>Als u symlinks gebruikt, bekijkt u [problemen met symlink](https://helpx.adobe.com/experience-manager/kb/changing-symlink.html).

### Starten en stoppen {#starting-and-stopping}

Wanneer AEM zichzelf heeft losgemaakt en voor het eerst is opgestart, door te dubbelklikken op het jar-bestand in de installatiemap, wordt de instantie gewoon gestart, maar wordt deze niet opnieuw geïnstalleerd.

Als u de instantie van de GUI wilt stoppen, klikt u gewoon op de **aan/uit** -schakelaar in het bureaubladtoepassingsvenster.

U kunt AEM ook stoppen en starten vanaf de opdrachtregel. Ervan uitgaande dat u de instantie al voor het eerst hebt geïnstalleerd, bevinden de **opdrachtregelscripts** zich hier:

**`<aem-install>/crx-quickstart/bin/`**

Deze map bevat de volgende UNIX bash-shellscripts:

* **`start`**: Hiermee wordt de instantie gestart
* `stop`: Hiermee wordt de instantie gestopt
* **`status`**: Rapporteert de status van de instantie
* **`quickstart`**: Gebruikt om begininformatie te vormen, indien nodig.

Er zijn ook equivalente **`bat`** bestanden voor Windows. Zie voor meer informatie:

* [Start en stop opdrachtregel](/help/sites-deploying/command-line-start-and-stop.md)

AEM begint en leidt automatisch uw Webbrowser aan de aangewezen pagina, gewoonlijk de login pagina opnieuw; bijvoorbeeld:

`https://localhost:4502/`

![aanmeldingsscherm](assets/screen_shot_2019-04-08at83533am.png)

Zodra het programma geopend, hebt u toegang tot AEM. Raadpleeg het volgende voor meer informatie, afhankelijk van uw rol:

* [Authoring](/help/sites-authoring/home.md)
* [Beheer](/help/sites-administering/home.md)
* [Ontwikkeling](/help/sites-developing/home.md)
* [Beheer](/help/managing/best-practices.md)

## Geavanceerde implementatie {#advanced-deployment}

In het bovenstaande gedeelte krijgt u een goed inzicht in de grondbeginselen van AEM installatie. De installatie van een volledig productiesysteem van AEM kan echter aanzienlijk complexer zijn. Zie de volgende subpagina&#39;s voor volledige dekking van geavanceerde installatie:

* [Technische vereisten](/help/sites-deploying/technical-requirements.md)
* [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md)
* [Aangepaste standalone installatie](/help/sites-deploying/custom-standalone-install.md)
* [Installeren van toepassingsserver](/help/sites-deploying/application-server-install.md)
* [Problemen oplossen](/help/sites-deploying/troubleshooting.md)
* [Start en stop opdrachtregel](/help/sites-deploying/command-line-start-and-stop.md)
* [Configureren](/help/sites-deploying/configuring.md)
* [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/sites-deploying/ecommerce.md)
* [Hoe kan ik-artikelen configureren](/help/sites-deploying/ht-deploy.md)
* [Webconsole](/help/sites-deploying/web-console.md)
* [Problemen met replicatie oplossen](/help/sites-deploying/troubleshoot-rep.md)
* [Best practices voor](/help/sites-deploying/best-practices.md)
* [Gemeenschappen inzetten](/help/communities/deploy-communities.md)
* [Inleiding tot het AEM Platform](/help/sites-deploying/platform.md)
* [Richtlijnen voor prestaties](/help/sites-deploying/performance-guidelines.md)
* [Aan de slag met AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Wat is AEM Screens?](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/aem-screens-introduction.html)
