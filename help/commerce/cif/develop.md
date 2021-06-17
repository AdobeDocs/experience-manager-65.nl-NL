---
title: Ontwikkelen AEM handel
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving.
topics: Commerce, Development
feature: Kader voor integratie in de handel
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
source-git-commit: d1fc2ff44378276522c2ff3208f5b3bdc4484bba
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---


# Ontwikkeling AEM Handel {#develop}

Voor de ontwikkeling van AEM handelsprojecten op basis van het kader voor de integratie van de handel (CIF) voor AEM gelden dezelfde regels en beste praktijken als voor andere AEM projecten. Controleer eerst deze:

- [AEM 6.5 Handboek voor het ontwikkelen van toepassingen](/help/sites-developing/home.md)
- [AEM kernconcepten](/help/sites-developing/the-basics.md)
- [AEM ontwikkeling - Richtsnoeren en beste praktijken](/help/sites-developing/dev-guidelines-bestpractices.md)
- [Hoe te om AEM Projecten te bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Lokale ontwikkeling voor AEM handel {#local}

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF-projecten.

>[!NOTE]
>
>De volgende instructies helpen u vestiging een lokale AEM ontwikkelomgeving voor AEM Handel gebruikend CIF met nadruk voor AEM 6.5). Als u AEM als Cloud Service gebruikt, te zien gelieve [AEM Handel als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/home.html) documentatie.

De AEM Commerce Add-On voor AEM 6.5 ook bekend. CIF Add-On is ook beschikbaar voor lokale ontwikkeling en verstrekt als AEM pakket. Het kan van [het portaal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) als eigenschappak worden gedownload.

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- Lokale AEM 6.5
- [AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)  7 of hoger
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/)  (3.3.9 of hoger)
- [Knooppunt LTS](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Toegang tot de CIF Add-On

De toe:voegen-op CIF kan van [het portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html), onderzoek naar &quot;AEM Commerce toe:voegen-op&quot;worden gedownload.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie van CIF toe:voegen-aan gebruikt.

### Lokale instellingen

Voor de lokale ontwikkeling van CIF-projecten met behulp van de AEM en de CIF-invoegtoepassing:

1. Krijg AEM 6.5 versie en installeer AEM 6.5 Service Pack. AEM 6.5 Service Pack 7 wordt vereist, nochtans adviseren wij installerend het laatste beschikbare de dienstpak.

1. Pak de AEM .jar uit om de `crx-quickstart` omslag tot stand te brengen, looppas:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install`-map maken

1. Kopieer de CIF add-on alle pakketten, gedownload van de portal voor softwaredistributie, naar de map `crx-quickstart/install`.

>[!TIP]
>
>Het CIF-invoegpakket kan ook worden geïnstalleerd via Package Manager.

1. Start de AEM

Verifieer de opstelling via de console OSGI: `http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI configuraties bevatten. Zorg ervoor dat alle bundels zijn gestart.

## Projectinstelling {#project}

Er zijn twee manieren om uw project van de Handel van de AEM te beginnen gebruikend CIF.

### Projectarchetype AEM gebruiken

Het [AEM Archetype van het Project](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project op te starten met CIF. De Componenten van de Kern van CIF en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Gebruik [AEM Projectarchetype 25 of later](https://github.com/adobe/aem-project-archetype/releases) om het project te genereren.

Zie AEM Project Archetype [gebruiksinstructies](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Als u CIF wilt opnemen in het project, gebruikt u de optie `includeCommerce`.

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

De componenten van de Kern van CIF kunnen in om het even welk project worden gebruikt door of het verstrekte `all` pakket of individueel te omvatten gebruikend het CIF inhoudspakket en verwante bundels OSGI. Om de Componenten van de Kern van CIF aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

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

Een tweede mogelijkheid om een CIF-project te starten, is het klonen en gebruiken van de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldopslagtoepassing die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om aan de slag te gaan met de Venia Reference Store klone eenvoudig de [Git repository](https://github.com/adobe/aem-cif-guides-venia) en begin het project aan uw behoeften aan te passen.

>[!NOTE]
>
>Het project van de Referentieopslag van Venia bevat twee bouwstijlprofielen voor AEM als Cloud Service en AEM 6.5. Controleer [project readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe zij worden gebruikt. Gebruik voor AEM 6.5 het profiel `classic`.

### AEM aansluiten op het systeem voor handel

Om uw project met het handelssysteem te verbinden AEM moet met het eindpunt GraphQL van uw handelssysteem worden gevormd.

Beide, een project dat door [AEM Project Archetype](https://github.com/adobe/aem-project-archetype) of [AEM de Opslag van de Verwijzing van Venia](https://github.com/adobe/aem-cif-guides-venia) wordt geproduceerd, omvat reeds [gebrek config](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) die moet worden aangepast.

Vervang de waarde van `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt GraphQL van uw handelsysteem dat door het project wordt gebruikt.

De AEM Commerce toe:voegen-aan en de Componenten van de Kern CIF verbinden met het commerciële eindpunt GraphQL via de AEM server en direct via browser. Client-side CIF Core Components and CIF Add-On authoring tools by default connect to `/api/graphql`. Indien nodig kan dit worden aangepast via de CIF Cloud Service config (zie hieronder).

De toe:voegen-on CIF verstrekt een de volmachtsservlet GraphQL bij `/api/graphql`. Als u niet van plan bent om een lokale AEM Dispatcher te gebruiken, wordt het geadviseerd om de de volmachtsservlet te vormen GraphQL eveneens.

Navigeer naar http://localhost:4502/system/console/configMgr en creeer een config OSGI voor de `Adobe CIF GraphQL Proxy Configuration` dienst. Gebruik het zelfde eindpunt GraphQL van uw handelensysteem zoals die voor de cliënt GraphQL hierboven wordt gebruikt.

## Aanvullende bronnen

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
