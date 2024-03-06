---
title: Ontwikkelen AEM handel
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving.
topics: Commerce, Development
feature: Commerce Integration Framework
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 48479725-8b52-4ff2-a599-d20958b26ee6
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# Ontwikkeling van AEM handel {#develop}

Voor de ontwikkeling van AEM op Commerce integration framework (CIF) gebaseerde projecten voor AEM gelden dezelfde regels en beste praktijken als voor andere AEM projecten. Bekijk eerst deze:

- [AEM 6.5 Gebruikershandleiding voor ontwikkeling](/help/sites-developing/getting-started.md)
- [AEM kernconcepten](/help/sites-developing/the-basics.md)
- [AEM ontwikkeling - Richtsnoeren en beste praktijken](/help/sites-developing/dev-guidelines-bestpractices.md)
- [Hoe te om AEM Projecten te bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Lokale ontwikkeling voor AEM handel {#local}

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF projecten.

>[!NOTE]
>
>De volgende instructies helpen u vestiging een lokale AEM ontwikkelomgeving voor AEM Handel gebruikend CIF met nadruk voor AEM 6.5). Als u AEM as a Cloud Service gebruikt, zie [AEM Commerce as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/home.html) documentatie.

De AEM Commerce Add-On voor AEM 6.5 ook bekend. CIF Add-On is ook beschikbaar voor lokale ontwikkeling en wordt als een AEM pakket geleverd. Het kan worden gedownload van [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) als een functiepakket.

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- Lokale AEM 6.5
- [AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 of hoger
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 of hoger)
- [Knooppunt LTS](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Toegang tot de CIF

De CIF invoegtoepassing kan worden gedownload van de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html), zoek naar &#39;AEM Commerce add-on&#39;.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie CIF toe:voegen-aan gebruikt.

### Lokale instellingen

Voor de ontwikkeling van lokale CIF projecten met behulp van de AEM en de CIF:

1. Krijg AEM 6.5 versie en installeer AEM 6.5 Service Pack. AEM 6.5 Service Pack 7 is vereist, nochtans adviseert de Adobe installerend het laatste beschikbare de dienstpak.

1. Pak de AEM .jar uit om de `crx-quickstart` map, uitvoeren:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` map

1. Kopieer de CIF invoegtoepassing voor alle pakketten die u hebt gedownload van de portal voor softwaredistributie naar de `crx-quickstart/install` map.

>[!TIP]
>
>U kunt het CIF invoegpakket ook installeren via Package Manager.

1. Start de AEM

Verifieer de opstelling via de console OSGI: `http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI-configuraties bevatten. Zorg ervoor dat alle bundels zijn gestart.

## Projectinstelling {#project}

Er zijn twee manieren om uw AEM Commerce-project te beginnen met CIF.

### Projectarchetype AEM gebruiken

De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een preconfigured project op te starten met CIF. CIF de Componenten van de Kern en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruiken [Projectarchetype 25 of hoger AEM](https://github.com/adobe/aem-project-archetype/releases) om het project te genereren.

Zie AEM projectarchetype [gebruiksaanwijzingen](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Om CIF in het project te omvatten gebruik `includeCommerce` -optie.

Bijvoorbeeld:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D aemVersion=6.5.5 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

CIF de Componenten van de Kern kunnen in om het even welk project worden gebruikt door één van beide inbegrepen verstrekte `all` pakket of individueel met behulp van het CIF-inhoudspakket en verwante OSGI-bundels. Om CIF de Componenten van de Kern aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### AEM Venia Reference Store gebruiken

Een tweede optie om een CIF project te starten is het klonen en gebruiken van de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldtoepassing van de verwijzingsopslag die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Als u aan de slag wilt gaan met de Venia Reference Store, kloont dan gewoon de [Git-opslagplaats](https://github.com/adobe/aem-cif-guides-venia) en begin het project aan uw behoeften aan te passen.

>[!NOTE]
>
>Het project van de Referentieopslag van Venia bevat twee bouwstijlprofielen voor AEM as a Cloud Service en AEM 6.5. Controleer de [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe ze worden gebruikt. Voor AEM 6.5 `classic` profiel.

### AEM aansluiten op het systeem voor handel

Om uw project met het handelssysteem te verbinden AEM moet met het eindpunt van GraphQL van uw handelssysteem worden gevormd.

Beide, een project dat door [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) of de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)bevat al een [standaardconfiguratie](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) die moeten worden aangepast.

Vervang de waarde van de optie `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt van GraphQL van uw handelsysteem dat door het project wordt gebruikt.

De AEM Commerce Add-On en CIF Core Components verbinden met het handelsGraphQL eindpunt via de AEM server en direct via browser. Client CIF Core Components and CIF Add-On authoring tools maken standaard verbinding met `/api/graphql`. Indien nodig kan dit worden aangepast via de configuratie van de CIF Cloud Service (zie hieronder).

De CIF add-on biedt een GraphQL-proxyservlet op `/api/graphql`. Als u niet van plan bent om een lokale AEM Dispatcher te gebruiken, wordt het geadviseerd om de volmachtsservlet van GraphQL eveneens te vormen.

Ga naar http://localhost:4502/system/console/configMgr en creeer een config OSGI voor `Adobe CIF GraphQL Proxy Configuration` service. Gebruik hetzelfde GraphQL-eindpunt van uw handelssysteem als hierboven voor de GraphQL-client.

## Aanvullende bronnen

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
