---
title: Aan de slag met AEM Inhoud en Handel
description: Leer hoe te om een project van de Inhoud en van de Handel van de AEM op te stellen.
topics: Commerce
feature: Commerce Integration Framework
exl-id: 92b964f8-6672-4f76-8a9f-5782c3ceb83f
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Aan de slag met AEM Inhoud en Handel {#start}

Om met AEM Inhoud en Handel te beginnen, moet u AEM inhoud en Commerce toe:voegen-On voor AEM 6.5 installeren.

## Minimale softwarevereisten

[AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 of hoger is vereist.

## Onboarding {#onboarding}

Het instappen voor AEM Inhoud en Handel is een proces in twee stappen:

1. Installeer de invoegtoepassing AEM inhoud en handel voor AEM 6.5

2. Verbind AEM met uw handelsoplossing

### Installeer de invoegtoepassing AEM inhoud en handel voor AEM 6.5 {#install-add-on}

Download en installeer de AEM Commerce Add-On voor AEM 6.5 van de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) portaal.

Start en installeer het vereiste AEM 6.5 Service Pack. Wij adviseren installerend het laatste beschikbare de dienstpak.

>[!NOTE]
>
>Dit zal door CSE voor AEM Beheerde klanten van de Dienst worden gedaan.

### AEM aansluiten op uw systeem voor handel {#connect}

AEM kan met om het even welk handelssysteem worden verbonden dat een toegankelijk eindpunt GraphQL voor AEM heeft. Deze eindpunten zijn gewoonlijk openbaar beschikbaar, of kunnen via privé VPN of lokale verbindingen afhankelijk van de individuele projectopstelling worden verbonden.

Naar keuze, kan de authentificatiekop worden verstrekt om extra eigenschappen te gebruiken CIF die authentificatie vereisen.

Door de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)en de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) die al in het [standaardconfiguratie](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) moet worden aangepast.

Vervang de waarde van de optie `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt GraphQL van uw handelsysteem. Deze configuratie kan via de console worden gedaan OSGI of door de configuratie OSGI via het project op te stellen. De verschillende configuraties voor het opvoeren en productiesystemen worden gesteund gebruikend verschillende AEM looppas wijzen.

De AEM Inhoud en de Handel toe:voegen-aan en de Componenten van de Kern CIF gebruiken zowel AEM server-kant als cliënt-zijverbindingen. Clientside CIF Core Components and CIF Add-On authoring tools connect by default to `/api/graphql`. Dit kan worden aangepast via de CIF Cloud Service config indien nodig (zie hieronder).

CIF toe:voegen-On verstrekt een de volmachtsservlet GraphQL bij `/api/graphql` die optioneel kunnen worden gebruikt voor [lokale ontwikkeling](develop.md). Voor productieplaatsingen wordt het sterk geadviseerd om een omgekeerde volmacht aan het eindpunt van commerceGraphQL via de AEM Dispatcher of bij andere netwerklagen (zoals CDN) te plaatsen.

## Opslag en catalogi configureren {#catalog}

De invoegtoepassing en de [CIF Core-componenten](https://github.com/adobe/aem-core-cif-components) kan op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handels opslag (of opslagmeningen, etc.) worden verbonden. Standaard wordt de CIF Add-On geïmplementeerd met een standaardconfiguratie die verbinding maakt met de standaardopslag en -catalogus van Adobe Commerce.

Deze configuratie kan voor het project via CIF Cloud Service config worden aangepast die deze stappen volgt:

1. Ga in AEM naar Extra -> Cloud Services -> CIF-configuratie

2. Selecteer de handelsconfiguratie u wilt veranderen

3. De configuratie-eigenschappen openen via de actiebalk

![Configuratie CIF-Cloud Services](/help/commerce/cif/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- Cliënt GraphQL - selecteer de gevormde cliënt GraphQL voor handel achterste mededeling. Dit zou typisch bij gebrek moeten blijven.
- Winkelweergave - de weergave-id van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL de Weg van de Volmacht - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt GraphQL.
   >[!NOTE]
   >
   > In de meeste instellingen is de standaardwaarde `/api/graphql` mogen niet worden gewijzigd. Alleen geavanceerde instellingen die de geleverde GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.
- De Steun van UID van de Catalogus van de inschakelen - laat steun voor UID in plaats van identiteitskaart in de handel achterste vraag GraphQL toe.
   >[!NOTE]
   >
   > Ondersteuning voor UID&#39;s is geïntroduceerd in Adobe Commerce 2.4.2. Laat slechts dit toe als uw handels achterkant een schema GraphQL van versie 2.4.2 of later steunt.
- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus
   >[!CAUTION]
   >
   > Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. Als uw project CIF Core Components versie 2.0.0 gebruikt moet u de Steun van UID van de Catalogus toelaten en een geldige categorieUID als &quot;Identifier van de Categorie van de Hoofdmap van de Catalogus gebruiken&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Voor complexere instellingen die meerdere AEM sitestructuren gebruiken die zijn gecombineerd met verschillende handelscatalogi raadpleegt u de [Multi-Store-installatie voor handel](configuring/multi-store-setup.md) zelfstudie.

## Aanvullende bronnen {#additional-resources}

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Multi-Store-installatie voor handel](configuring/multi-store-setup.md)
