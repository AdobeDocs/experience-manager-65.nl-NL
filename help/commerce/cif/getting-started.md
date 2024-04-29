---
title: Aan de slag met AEM Content en Commerce
description: Leer hoe u een AEM Content- en Commerce-project implementeert.
topics: Commerce
feature: Commerce Integration Framework
exl-id: 92b964f8-6672-4f76-8a9f-5782c3ceb83f
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 0%

---

# Aan de slag met AEM Content en Commerce {#start}

Als u aan de slag wilt met AEM Content en Commerce, moet u de AEM Content and Commerce Add-On voor AEM 6.5 installeren.

## Minimale softwarevereisten

[AEM 6.5 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 of hoger is vereist.

## Onboarding {#onboarding}

Het instappen voor AEM Inhoud en Handel is een proces in twee stappen:

1. Installeer de AEM Content en de Commerce Add-on voor AEM 6.5

2. Verbind AEM met uw handelsoplossing

### Installeer de AEM Content en de Commerce Add-on voor AEM 6.5 {#install-add-on}

Download en installeer de AEM Commerce Add-on voor AEM 6.5 vanuit de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) portaal.

Start en installeer het vereiste AEM 6.5 Service Pack. Wij adviseren installerend het laatste beschikbare de dienstpak.

>[!NOTE]
>
>Dit zal door CSE voor AEM Beheerde klanten van de Dienst worden gedaan.

### AEM aansluiten op uw Commerce-systeem {#connect}

AEM kunnen worden aangesloten op elk handelssysteem dat een toegankelijk GraphQL-eindpunt voor AEM heeft. Deze eindpunten zijn gewoonlijk openbaar beschikbaar, of kunnen via privé VPN of lokale verbindingen afhankelijk van de individuele projectopstelling worden verbonden.

Naar keuze, kan de authentificatiekop worden verstrekt om extra CIF eigenschappen te gebruiken die authentificatie vereisen.

Door de [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)en de [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) die al in het [standaardconfiguratie](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) moet worden aangepast.

Vervang de waarde van de optie `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het GraphQL-eindpunt van uw handelssysteem. Deze configuratie kan via de console worden gedaan OSGI of door de configuratie OSGI via het project op te stellen. Verschillende configuraties voor staging- en productiesystemen worden ondersteund met verschillende AEM-uitvoeringsmodi.

De AEM Content en Commerce Add-On en CIF Core Components gebruiken zowel AEM server-side als client-side verbindingen. Client CIF Core Components and CIF Add-on authoring tools maken standaard verbinding met `/api/graphql`. Dit kan worden aangepast via de CIF Cloud Service config indien nodig (zie hieronder).

De CIF Add-on biedt een GraphQL-proxyservlet op `/api/graphql` die optioneel kunnen worden gebruikt voor [lokale ontwikkeling](develop.md). Voor productieplaatsingen wordt het sterk geadviseerd om een omgekeerde volmacht aan het handelsGraphQL eindpunt via de AEMVerzender of bij andere netwerklagen (zoals CDN) te plaatsen.

## Opslag en catalogi configureren {#catalog}

De invoegtoepassing en de [CIF kerncomponenten](https://github.com/adobe/aem-core-cif-components) kan op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handels opslag (of opslagmeningen, etc.) worden verbonden. Standaard wordt de CIF Add-On geïmplementeerd met een standaardconfiguratie die verbinding maakt met de standaardopslag en catalogus van Adobe Commerce.

Deze configuratie kan voor het project via CIF Cloud Service worden aangepast config die deze stappen volgt:

1. Ga in AEM naar Extra > Cloud Servicen > Configuratie CIF

2. Selecteer de handelsconfiguratie u wilt veranderen

3. De configuratie-eigenschappen openen via de actiebalk

![Configuratie CIF Cloud Servicen](/help/commerce/cif/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- GraphQL Client - selecteer de geconfigureerde GraphQL-client voor commerciële back-endcommunicatie. Dit moet standaard blijven.
- Winkelweergave - de weergave-id van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL Proxy Path - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt van GraphQL.

  >[!NOTE]
  >
  >In de meeste instellingen is de standaardwaarde `/api/graphql` mogen niet worden gewijzigd. Alleen geavanceerde instellingen die de opgegeven GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.

- Schakel ondersteuning voor UID-catalogus in - schakel ondersteuning voor UID in in plaats van voor ID in de commerciële back-end GraphQL-aanroepen.

  >[!NOTE]
  >
  >Ondersteuning voor UID&#39;s is geïntroduceerd in Adobe Commerce 2.4.2. Schakel deze optie alleen in als uw commerciële backend een GraphQL-schema van versie 2.4.2 of hoger ondersteunt.

- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus

  >[!CAUTION]
  >
  >Vanaf CIF Core Components versie 2.0.0 wordt de ondersteuning voor `id` is verwijderd en vervangen door `uid`. Als uw project CIF versie 2.0.0 van de Componenten van de Kern gebruikt moet u de Steun van UID van de Catalogus toelaten en een geldige categorieUID als &quot;Identifier van de Categorie van de Hoofdstad van de Catalogus gebruiken&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Voor complexere instellingen die meerdere AEM sitestructuren gebruiken die zijn gecombineerd met verschillende handelscatalogi raadpleegt u de [Commerce Multi-Store Setup](configuring/multi-store-setup.md) zelfstudie.

## Aanvullende bronnen {#additional-resources}

- [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce Multi-Store Setup](configuring/multi-store-setup.md)
