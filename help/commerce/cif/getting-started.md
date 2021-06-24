---
title: Aan de slag met AEM Inhoud en Handel
description: Leer hoe te om een project van de Inhoud en van de Handel van de AEM op te stellen.
topics: Commerce
feature: Kader voor integratie in de handel
thumbnail: 37843.jpg
exl-id: 92b964f8-6672-4f76-8a9f-5782c3ceb83f
source-git-commit: 61b8d0bf960bd03a19d22061f3c897a56259dd24
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Aan de slag met AEM Inhoud en Handel {#start}

Om met AEM Inhoud en Handel te beginnen, moet u AEM inhoud en Commerce toe:voegen-On voor AEM 6.5 installeren.

## Minimale softwarevereisten

[AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 of later is vereist.

## Onboarding {#onboarding}

Het instappen voor AEM Inhoud en Handel is een proces in twee stappen:

1. Installeer de invoegtoepassing AEM inhoud en handel voor AEM 6.5

2. Verbind AEM met uw handelsoplossing

### Installeer de invoegtoepassing AEM inhoud en handel voor AEM 6.5 {#install-add-on}

Download en installeer de AEM Commerce Add-On voor AEM 6.5 van [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) portal.

Start en installeer het vereiste AEM 6.5 Service Pack. Wij adviseren installerend het laatste beschikbare de dienstpak.

>[!NOTE]
>
>Dit zal door CSE voor AEM Beheerde klanten van de Dienst worden gedaan.

### AEM aansluiten op uw systeem voor handel {#connect}

AEM kan met om het even welk handelssysteem worden verbonden dat een toegankelijk eindpunt GraphQL voor AEM heeft. Deze eindpunten zijn gewoonlijk openbaar beschikbaar, of kunnen via privé VPN of lokale verbindingen afhankelijk van de individuele projectopstelling worden verbonden.

Naar keuze, kan de authentificatiekop worden verstrekt om extra eigenschappen te gebruiken CIF die authentificatie vereisen.

Projecten die worden gegenereerd door het [AEM Project Archetype](https://github.com/adobe/aem-project-archetype) en de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) die al is opgenomen in de [standaardconfig](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json), moeten worden aangepast.

Vervang de waarde van `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt GraphQL van uw handelsysteem. Deze configuratie kan via de console worden gedaan OSGI of door de configuratie OSGI via het project op te stellen. De verschillende configuraties voor het opvoeren en productiesystemen worden gesteund gebruikend verschillende AEM looppas wijzen.

De AEM Inhoud en de Handel toe:voegen-aan en de Componenten van de Kern CIF gebruiken zowel AEM server-kant als cliënt-zijverbindingen. Client-side CIF Core Components and CIF Add-On authoring tools connect by default to `/api/graphql`. Dit kan worden aangepast via de CIF Cloud Service config indien nodig (zie hieronder).

CIF toe:voegen-On verstrekt een de volmachtsservlet GraphQL bij `/api/graphql` die naar keuze voor [lokale ontwikkeling](develop.md) kan worden gebruikt. Voor productieplaatsingen wordt het sterk geadviseerd om een omgekeerde volmacht aan het eindpunt van commerceGraphQL via de AEM Dispatcher of bij andere netwerklagen (zoals CDN) te plaatsen.

## Opslag en catalogi configureren {#catalog}

De toe:voegen-aan en [CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components) kunnen op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handels (of opslagmeningen, etc. worden verbonden). Door gebrek, wordt toe:voegen-On CIF opgesteld met een gebrek config die met de standaardopslag en de catalogus van de Handel van Adobe verbindt (Magento).

Deze configuratie kan voor het project via CIF Cloud Service config worden aangepast die deze stappen volgt:

1. Ga in AEM naar Extra -> Cloud Services -> CIF-configuratie

2. Selecteer de handelsconfiguratie u wilt veranderen

3. De configuratie-eigenschappen openen via de actiebalk

![Configuratie CIF-Cloud Services](/help/commerce/cif/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- Cliënt GraphQL - selecteer de gevormde cliënt GraphQL voor handel achterste mededeling. Dit zou typisch bij gebrek moeten blijven.
- Winkelweergave - de weergave-id (Magento) van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL de Weg van de Volmacht - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt GraphQL.
   >[!NOTE]
   >
   > In de meeste instellingen mag de standaardwaarde `/api/graphql` niet worden gewijzigd. Alleen geavanceerde instellingen die de geleverde GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.
- De Steun van UID van de Catalogus van de inschakelen - laat steun voor UID in plaats van identiteitskaart in de handel achterste vraag GraphQL toe.
   >[!NOTE]
   >
   > Steun voor UIDs werd geïntroduceerd in de Handel van de Adobe (Magento) 2.4.2. Laat slechts dit toe als uw handels achterkant een schema GraphQL van versie 2.4.2 of later steunt.
- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus
   >[!CAUTION]
   >
   > Vanaf CIF Core Components versie 2.0.0 is de ondersteuning voor `id` verwijderd en vervangen door `uid`. Als uw project CIF Core Components versie 2.0.0 gebruikt moet u de Steun van UID van de Catalogus toelaten en een geldige categorieUID als &quot;Identifier van de Categorie van de Hoofdmap van de Catalogus gebruiken&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Zie de zelfstudie [Commerce Multi-Store Setup](configuring/multi-store-setup.md) voor meer complexe instellingen die gebruikmaken van meerdere AEM sitestructuren die zijn gecombineerd met verschillende handelscatalogi.

## Aanvullende bronnen {#additional-resources}

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Multi-Store-installatie voor handel](configuring/multi-store-setup.md)
