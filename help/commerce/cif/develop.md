---
title: Ontwikkelen AEM Commerce
description: Leer hoe te om een handel-toegelaten AEM project te produceren gebruikend het AEM projectarchetype. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving.
topics: Commerce, Development
feature: Commerce Integration Framework
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 48479725-8b52-4ff2-a599-d20958b26ee6
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# Ontwikkeling AEM Commerce {#develop}

Voor de ontwikkeling AEM Commerce-projecten op basis van Commerce integration framework (CIF) voor AEM gelden dezelfde regels en beste praktijken als voor andere AEM projecten. Bekijk eerst deze:

- [AEM 6.5 Gebruikershandleiding voor ontwikkeling](/help/sites-developing/getting-started.md)
- [AEM kernconcepten](/help/sites-developing/the-basics.md)
- [AEM ontwikkeling - Richtsnoeren en beste praktijken](/help/sites-developing/dev-guidelines-bestpractices.md)
- [Hoe te om AEM Projecten te bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Lokale ontwikkeling voor AEM Commerce {#local}

Een lokale ontwikkelomgeving wordt aanbevolen voor CIF projecten.

>[!NOTE]
>
>De volgende instructies helpen u bij het instellen van een lokale AEM-ontwikkelomgeving voor AEM Commerce die CIF gebruikt met focus voor AEM 6.5). Als u AEM as a Cloud Service gebruikt, zie [ AEM de as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/home.html) documentatie van Commerce.

De AEM Commerce Add-On voor AEM 6.5 ook bekend. CIF Add-On is ook beschikbaar voor lokale ontwikkeling en wordt als een AEM pakket geleverd. Het kan van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) als eigenschappak worden gedownload.

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- Lokale AEM 6.5
- [ AEM 6.5 Service Pack ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 of later
- [ Java 11 ](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [ Apache Maven ](https://maven.apache.org/) (3.3.9 of nieuwer)
- [ Knoop LTS ](https://nodejs.org/en/)
- [ npm 6+ ](https://www.npmjs.com/)
- [ Git ](https://git-scm.com/)

### Toegang tot de CIF

CIF toe:voegen-op kan van het [ portaal van de Distributie van de Software worden gedownload ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html), onderzoek naar &quot;AEM Commerce toe:voegen-op&quot;.

>[!TIP]
>
>Zorg ervoor u altijd de recentste versie CIF toe:voegen-aan gebruikt.

### Lokale instellingen

Voor de ontwikkeling van lokale CIF projecten met behulp van de AEM en de CIF:

1. Krijg AEM 6.5 versie en installeer AEM 6.5 Service Pack. AEM 6.5 Service Pack 7 is vereist, nochtans adviseert de Adobe installerend het laatste beschikbare de dienstpak.

1. Pak de AEM .jar uit om de map `crx-quickstart` te maken en voer de volgende handelingen uit:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` -map maken

1. Kopieer de CIF add-on alle pakketten, gedownload van de Software Distribution Portal, naar de map `crx-quickstart/install` .

>[!TIP]
>
>U kunt het CIF invoegpakket ook installeren via Package Manager.

1. Start de AEM

Controleer de installatie via de OSGI-console: `http://localhost:4502/system/console/osgi-installer` . De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI-configuraties bevatten. Zorg ervoor dat alle bundels zijn gestart.

## Projectinstelling {#project}

Er zijn twee manieren om uw AEM Commerce-project te starten met CIF.

### Projectarchetype AEM gebruiken

Het [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project op te starten om met CIF te beginnen. CIF de Componenten van de Kern en alle vereiste configuraties kunnen in een geproduceerd project met één extra optie worden omvat.

>[!TIP]
>
>Het gebruik [ AEM Archetype 25 van het Project of recenter ](https://github.com/adobe/aem-project-archetype/releases) om het project te produceren.

Zie AEM het gebruiksinstructies van de Archetype van het Project [ ](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een AEM project te produceren. Als u CIF wilt opnemen in het project, gebruikt u de optie `includeCommerce` .

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

CIF Core Components kunnen in elk project worden gebruikt door ofwel het meegeleverde `all` -pakket op te nemen ofwel het individuele pakket met CIF inhoud en verwante OSGI-bundels. Om CIF de Componenten van de Kern aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

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

Een tweede optie om een CIF project te beginnen is het [ AEM de Opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) te klonen en te gebruiken. De AEM Venia Reference Store is een voorbeeldtoepassing van de verwijzingsopslag die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om met de Opslag van de Verwijzing van Venia eenvoudig te beginnen klonen de [ bewaarplaats van het Git ](https://github.com/adobe/aem-cif-guides-venia) en beginnen het project overeenkomstig uw behoeften aan te passen.

>[!NOTE]
>
>Het Venia Reference Store-project bevat twee buildprofielen voor AEM as a Cloud Service en AEM 6.5. Controleer [ project readme.md ](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe zij worden gebruikt. Gebruik voor AEM 6.5 het profiel `classic` .

### AEM verbinden met het Commerce-systeem

Om uw project met het handelssysteem te verbinden AEM moet met het eindpunt van GraphQL van uw handelssysteem worden gevormd.

Zowel, omvat een project dat door het [ AEM Archieftype van het Project ](https://github.com/adobe/aem-project-archetype) of [ AEM de Opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) wordt geproduceerd, reeds a [ gebrek config ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) dat moet worden aangepast.

Vervang de waarde van `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt van GraphQL van uw handelsysteem dat door het project wordt gebruikt.

De AEM toe:voegen-aan en CIFComponenten van de Kern verbinden met het handelsGraphQL eindpunt via de AEM server en direct via browser. Client-side CIF Core Components and CIF Add-on authoring tools by default connect to `/api/graphql`. Indien nodig kan dit worden aangepast via de configuratie van de CIF Cloud Service (zie hieronder).

De CIF add-on biedt een GraphQL-proxyservlet op `/api/graphql` . Als u niet van plan bent om een lokale AEM Dispatcher te gebruiken, wordt het geadviseerd om de volmachtsservlet van GraphQL eveneens te vormen.

Navigeer naar http://localhost:4502/system/console/configMgr en maak een OSGI-config voor de `Adobe CIF GraphQL Proxy Configuration` -service. Gebruik hetzelfde GraphQL-eindpunt van uw handelssysteem als hierboven voor de GraphQL-client.

## Aanvullende bronnen

- [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store ](https://github.com/adobe/aem-cif-guides-venia)
