---
title: Implementeren en onderhouden
description: Leer hoe u aan de slag gaat met de AEM-installatie.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: 3df0662a-0768-4b56-8b94-c517657b4bd9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1792'
ht-degree: 0%

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
* [Start en stop van opdrachtregel](/help/sites-deploying/command-line-start-and-stop.md)
* [Configureren](/help/sites-deploying/configuring.md)
* [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/commerce/cif-classic/deploying/ecommerce.md)
* [Hoe kan ik-artikelen configureren](/help/sites-deploying/ht-deploy.md)
* [Webconsole](/help/sites-deploying/web-console.md)
* [Problemen met replicatie oplossen](/help/sites-deploying/troubleshoot-rep.md)
* [Aanbevolen procedures](/help/sites-deploying/best-practices.md)
* [Gemeenschappen inzetten](/help/communities/deploy-communities.md)
* [Inleiding tot het AEM Platform](/help/sites-deploying/platform.md)
* [Richtlijnen voor prestaties](/help/sites-deploying/performance-guidelines.md)
* [Aan de slag met AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Wat is AEM Screens?](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html)

## Basisconcepten {#basic-concepts}

### Wat is AEM? {#what-is-aem}

Adobe Experience Manager is een op het web gebaseerd clientserversysteem voor het bouwen, beheren en implementeren van commerciële websites en verwante services. Het combineert verscheidene infrastructuur-niveau en toepassing-vlakke functies in één enkel geïntegreerd pakket.

Op het niveau van de infrastructuur biedt AEM het volgende:

* **Webtoepassingsserver**: AEM kan worden geïmplementeerd in zelfstandige modus (inclusief een geïntegreerde Jetty-webserver) of als een webtoepassing binnen een externe toepassingsserver.
* **Web Application Framework**: AEM neemt het het Verdelen Kader van de Toepassing van het Web op dat het schrijven van RESTful, content-oriented Webtoepassingen vereenvoudigt.
* **Inhoudsopslagplaats**: AEM bevat een JCR (Java™ Content Repository), een type hiërarchische database die speciaal is ontworpen voor ongestructureerde en semi-gestructureerde gegevens. De gegevensopslagruimte slaat niet alleen de gebruikersgerichte inhoud op, maar ook alle code, sjablonen en interne gegevens die door de toepassing worden gebruikt.

Op basis van deze basis biedt AEM ook verschillende functies op toepassingsniveau voor het beheer van:

* **Websites**
* **Mobiele toepassingen**
* **Digitale publicaties**
* **Forms &amp; Documenten**
* **Digitale middelen**
* **Gemeenschappen**
* **Online Commerce**

Tot slot kunnen de klanten deze infrastructuur en toepassing-vlakke bouwstenen gebruiken om aangepaste oplossingen tot stand te brengen door toepassingen van hun te bouwen.

De AEM server is **op Java gebaseerd** en wordt uitgevoerd op de meeste besturingssystemen die dat platform ondersteunen. Alle clientinteractie met AEM gebeurt via een **webbrowser**.

>[!NOTE]
>
>De functie Adaptive Forms, die beschikbaar is in AEM 6.5 QuickStart, is alleen ontworpen voor exploratie- en evaluatiedoeleinden. Voor productiegebruik is het van essentieel belang een geldige licentie voor AEM Forms te verkrijgen, aangezien voor de adaptieve Forms-functionaliteit een correcte licentie vereist is.

### Typische implementatiescenario&#39;s {#typical-deployment-scenarios}

In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server wordt uitgevoerd. AEM installaties omvatten gewoonlijk minstens twee instanties, die typisch op afzonderlijke computers lopen:

* **Auteur**: Een AEM die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
* **Publiceren**: Een AEM instantie die de gepubliceerde inhoud aan het publiek levert.

Deze exemplaren zijn identiek wat geïnstalleerde software betreft. Ze worden alleen gedifferentieerd naar configuratie. Bovendien gebruiken de meeste installaties een Dispatcher:

* **Dispatcher**: Een statische webserver (Apache httpd, Microsoft® IIS enzovoort) aangevuld met de module AEM Dispatcher. Webpagina&#39;s die door de instantie publish worden gemaakt, worden in het cachegeheugen opgeslagen om de prestaties te verbeteren.

Er zijn vele geavanceerde opties en de opstelling, maar het basispatroon van auteur, publiceert en Verzender is de kern van de meeste plaatsingen. Laten we ons eerst richten op een eenvoudige opstelling. Hierna volgen besprekingen over geavanceerde implementatieopties.

In de volgende secties worden beide scenario&#39;s beschreven:

* **Op locatie**: AEM geïmplementeerd en beheerd in uw bedrijfsomgeving.

* **Managed Services - Cloud Manager voor Adobe Experience Manager**: AEM geïmplementeerd en beheerd door Adobe Managed Services.

### Op locatie {#on-premise}

U kunt AEM installeren op servers in uw bedrijfsomgeving. Voorbeelden van gebruikelijke installatieprogramma&#39;s zijn: ontwikkelings-, test- en publicatieomgevingen. Zie [Aan de slag](/help/sites-deploying/deploy.md#getting%20started) voor basisinformatie over hoe u de software van de AEM lokaal kunt installeren.

Meer over de typische plaatsingen op-gebouw leren, zie [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md).

### Managed Services met Cloud Manager {#managed-services-using-cloud-manager}

AEM Managed Services is een complete oplossing voor Digital Experience Management. Het biedt voordelen van de oplossing van de ervaringslevering in de wolk terwijl het handhaven van alle controle, veiligheid, en aanpassingsvoordelen van een plaatsing op-premise. AEM Managed Services stelt klanten in staat sneller te starten door te implementeren in de cloud en door te leren van de beste praktijken en ondersteuning van de Adobe. Organisaties en zakelijke gebruikers kunnen hun klanten zo weinig mogelijk tijd in dienst nemen, hun marktaandeel vergroten en zich richten op het maken van innovatieve marketingcampagnes en tegelijk de last voor de IT-afdeling verminderen.

Met AEM Managed Services kunnen klanten de volgende voordelen realiseren:

**Snellere marktintroductie:** Met de flexibele wolkeninfrastructuur van Adobe Managed Services kunnen organisaties snel succesvolle digitale ervaringen plannen, lanceren en optimaliseren. Adobe beheert de cloudarchitectuur zonder extra kapitaal, hardware of software vereist en de technici van de Oplossingen van de Klant van de Adobe, hulp met AEM architectuur, levering, aanpassing voor verbinding met back-end apps en go-live beste praktijken.

**Hogere prestaties:** Verstrekt betrouwbare digitale ervaringen voor uw zaken met vier opties van de de dienstbeschikbaarheid 99.5%, 99.9%, 99.95%, en 99.99%. Bovendien maakt het automatische back-up en multimode modellen voor noodherstel mogelijk om betrouwbaarheid en noodbeheer te garanderen.

**Geoptimaliseerde IT-kosten:** Proactieve begeleiding en expertise Help-organisaties blijven op de hoogte van de nieuwste versie van AEM. Adobe Platinum Maintenance and Support wordt automatisch opgenomen in nieuwe implementaties van AMS Enterprise/Basic, die technische expertise en operationele ervaring bieden om organisaties te helpen hun bedrijfskritieke toepassingen te onderhouden. Gratis basisanalysemogelijkheden of doelmogelijkheden bieden extra waarde, met name voor organisaties uit het midden- en kleinbedrijf die weinig behoefte hebben aan analyses en personalisatie.

**Hoogste beveiliging:** Zorgt voor fysieke beveiliging, netwerk en gegevensbeveiliging op bedrijfsniveau door klantentoepassingen te hosten in een beperkte-toegangsfaciliteit, achter firewallsystemen, of binnen een virtuele privécloud. Het omvat virtuele machines van één huurder met robuuste gegevensopslagencryptie, antivirale middelen, en gegevensisolatie.

**Cloud Manager**: Cloud Manager, een onderdeel van de Adobe Experience Manager Managed Services-aanbieding, is een zelfbedieningsportaal waarmee organisaties Adobe Experience Manager in de cloud verder kunnen beheren. Het omvat een geavanceerde ononderbroken integratie en ononderbroken levering (CI/CD) pijpleiding die de teams van IT en implementatiepartners de levering van aanpassingen of updates laat versnellen zonder prestaties of veiligheid te compromitteren. Cloud Manager is alleen beschikbaar voor Adobe Managed Service-klanten.

Ga voor meer informatie over Cloud Manager en zijn bronnen naar [**Gebruikershandleiding voor Cloud Manager**](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html).

## Aan de slag {#getting-started}

### Vereisten {#prerequisites}

Terwijl productieinstanties worden uitgevoerd op speciale machines waarop een door de overheid ondersteund besturingssysteem wordt uitgevoerd (zie [Technische vereisten](/help/sites-deploying/technical-requirements.md)), zal de server van de Experience Manager eigenlijk op om het even welk systeem lopen dat steunt [**Java™ Standard Edition 8**](https://www.oracle.com/java/technologies/downloads/#java8).

Om vertrouwd te raken en zich op AEM te ontwikkelen, is het gebruikelijk om een instantie te gebruiken die op uw lokale computer wordt geïnstalleerd die OS X of Desktopversies van Microsoft® Windows of Linux® in werking stelt.

Op de client werkt AEM met alle moderne browsers (**Microsoft® Edge**, **Internet Explorer** 11, **Chrome **51+** **, **Firefox **47+, **Safari** 8+) op zowel desktop als tablet besturingssystemen. Zie [Ondersteunde clientplatforms](/help/sites-deploying/technical-requirements.md#supported-client-platforms) voor meer informatie.

### De software ophalen {#getting-the-software}

Klanten met een geldig onderhouds- en supportcontract hadden een e-mailmelding met een code moeten ontvangen en AEM van de [**Licentiewebsite voor Adobe**](https://licensing.adobe.com/). Zakelijke partners kunnen om downloadtoegang vragen van [**spphelp@adobe.com**](mailto:spphelp@adobe.com).

Het AEM softwarepakket is beschikbaar in twee vormen:

* **cq-quickstart-6.5.0.jar:** Een zelfstandig uitvoerbaar bestand *jar* bestand dat alles bevat wat u nodig hebt om actief te worden.

* **cq-quickstart-6.5.0.war:** A *oorlog* bestand voor implementatie op een externe toepassingsserver.

In de volgende sectie beschrijven we de **zelfstandige installatie**. Zie voor meer informatie over het installeren van AEM in een toepassingsserver [Installeren van toepassingsserver](/help/sites-deploying/application-server-install.md).

### Standaard lokale installatie {#default-local-install}

1. Maak een installatiemap op uw lokale computer. Bijvoorbeeld:

   Installatielocatie voor UNIX®: **/opt/aem**

   Installatielocatie voor Windows: **`C:\Program Files\aem`**

   Het is ook gebruikelijk om voorbeeldexemplaren in een map rechts op het bureaublad te installeren. In elk geval wordt in de Adobe deze locatie doorgaans als volgt aangeduid:

   `<aem-install>`

   *Het pad van de bestandsmap mag alleen uit ASCII-tekens van de Verenigde Staten bestaan.*

1. Plaats de **jar** en **licentie** bestanden in deze map:

   ```shell
   <aem-install>/
       cq-quickstart-6.5.0.jar
       license.properties
   ```

   Als u geen `license.properties` bestand, AEM uw browser om naar een **Welkom** scherm bij het opstarten, waar u een licentiecode kunt invoeren. U moet een geldige licentiecode aanvragen bij Adobe als u die nog niet hebt.

1. Als u de instantie wilt starten in een GUI-omgeving, dubbelklikt u op de knop **`cq-quickstart-6.5.0.jar`** bestand.

   U kunt ook AEM starten vanaf de opdrachtregel:

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.5.0.jar
   ```

AEM neemt een paar minuten in beslag om het jar-bestand uit te pakken, te installeren en op te starten. Deze procedure leidt tot:

* een **AEM auteur** instance
* wordt uitgevoerd op **localhost**
* op poort **4502**

Als u toegang wilt krijgen tot de instantie, moet u de browser raadplegen op:

**`https://localhost:4502`**

Het resultaat in auteursinstantie zal automatisch worden gevormd om met een **publish-instantie** op **`localhost:4503`**.

### Auteur- en publicatie-installaties {#author-and-publish-installs}

De standaardinstallatie (en **auteur** instantie op **`localhost:4502`**) kan worden gewijzigd door de naam van de `jar` voordat u het voor het eerst start. Het naamgevingspatroon is:

**`cq-<instance-type>-p<port-number>.jar`**

De naam van het bestand wijzigen in

**`cq-author-p4502.jar`**

En het lanceren van het, resulteert in een auteursinstantie lopend op **`localhost:4502`**.

Ook de naam van het bestand wijzigen en het bestand starten

**`cq-publish-p4503.jar`**

Resultaten van een publicatie-instantie die wordt uitgevoerd op **`localhost:4503`**.

U installeert deze twee varianten bijvoorbeeld in

`<aem-install>/author`en

**`<aem-install>/publish`**

Raadpleeg de volgende bronnen voor meer informatie over het aanpassen van de installatie:

* [Aangepaste standalone installatie](/help/sites-deploying/custom-standalone-install.md)
* [Modi uitvoeren](/help/sites-deploying/configure-runmodes.md)

### Onverpakte installatiemap {#unpacked-install-directory}

Wanneer de QuickStart-pot voor het eerst wordt gestart, wordt deze zichzelf in dezelfde map uitgepakt onder een nieuwe submap met de naam `crx-quickstart`. U zou het volgende moeten hebben:

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

Als de instantie is geïnstalleerd via de gebruikersinterface, wordt automatisch een browservenster geopend en wordt ook een venster van de bureaubladtoepassing geopend met daarin de host en poort van de instantie en een aan/uit-schakelaar:

![opstartscherm](assets/screen_shot_.png)

>[!NOTE]
>
>Als u symlinks gebruikt, kunt u het volgende doen: [kwesties met symlink](https://helpx.adobe.com/experience-manager/kb/changing-symlink.html).

### Starten en stoppen {#starting-and-stopping}

Wanneer AEM zichzelf heeft losgemaakt en voor het eerst is opgestart en u dubbelklikt op het jar-bestand in de installatiemap, wordt de instantie gewoon gestart, maar wordt deze niet opnieuw geïnstalleerd.

Als u de instantie wilt stoppen vanuit de interface, klikt u op de knop **aan/uit** schakelt u het toepassingsvenster van het bureaublad in.

U kunt AEM ook stoppen en starten vanaf de opdrachtregel. Ervan uitgaande dat u de instantie al voor de eerste keer hebt geïnstalleerd, wordt **opdrachtregelscripts** zijn hier:

**`<aem-install>/crx-quickstart/bin/`**

Deze map bevat de volgende UNIX® bash shell-scripts:

* **`start`**: Start de instantie
* `stop`: Stopt de instantie
* **`status`**: meldt de status van de instantie
* **`quickstart`**: Gebruikt om begininformatie te vormen, indien nodig.

Er zijn ook gelijkwaardige **`bat`** bestanden voor Windows. Zie voor meer informatie:

* [Start en stop van opdrachtregel](/help/sites-deploying/command-line-start-and-stop.md)

AEM begint en leidt uw webbrowser automatisch naar de juiste pagina, meestal de aanmeldingspagina, bijvoorbeeld:

`https://localhost:4502/`

![aanmeldingsscherm](assets/screen_shot_2019-04-08at83533am.png)

Nadat u bent aangemeld, hebt u toegang tot AEM. Raadpleeg de volgende secties voor meer informatie, afhankelijk van uw rol:

* [Authoring](/help/sites-authoring/first-steps.md)
* [Beheer](/help/sites-administering/home.md)
* [Ontwikkelen](/help/sites-developing/getting-started.md)
* [Beheer](/help/managing/best-practices.md)

## Geavanceerde implementatie {#advanced-deployment}

In het bovenstaande gedeelte krijgt u een goed inzicht in de grondbeginselen van AEM installatie. De installatie van een volledig productiesysteem van AEM kan echter aanzienlijk complexer zijn. Zie de volgende subpagina&#39;s voor volledige dekking van geavanceerde installatie:

* [Technische vereisten](/help/sites-deploying/technical-requirements.md)
* [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md)
* [Aangepaste standalone installatie](/help/sites-deploying/custom-standalone-install.md)
* [Installeren van toepassingsserver](/help/sites-deploying/application-server-install.md)
* [Problemen oplossen](/help/sites-deploying/troubleshooting.md)
* [Start en stop van opdrachtregel](/help/sites-deploying/command-line-start-and-stop.md)
* [Configureren](/help/sites-deploying/configuring.md)
* [Upgrade uitvoeren naar AEM 6.5](/help/sites-deploying/upgrade.md)
* [eCommerce](/help/commerce/cif-classic/deploying/ecommerce.md)
* [Hoe kan ik-artikelen configureren](/help/sites-deploying/ht-deploy.md)
* [Webconsole](/help/sites-deploying/web-console.md)
* [Problemen met replicatie oplossen](/help/sites-deploying/troubleshoot-rep.md)
* [Aanbevolen procedures](/help/sites-deploying/best-practices.md)
* [Gemeenschappen inzetten](/help/communities/deploy-communities.md)
* [Inleiding tot het AEM Platform](/help/sites-deploying/platform.md)
* [Richtlijnen voor prestaties](/help/sites-deploying/performance-guidelines.md)
* [Aan de slag met AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Wat is AEM Screens?](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html)
