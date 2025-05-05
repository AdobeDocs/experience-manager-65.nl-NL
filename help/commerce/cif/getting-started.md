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

[ AEM 6.5 Service Pack ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) 7 of later wordt vereist.

## Onboarding {#onboarding}

Het instapproces voor AEM Content en Commerce bestaat uit twee stappen:

1. Installeer de AEM Content en de Commerce Add-on voor AEM 6.5

2. Verbind AEM met uw handelsoplossing

### Installeer de AEM Content en de Commerce Add-on voor AEM 6.5 {#install-add-on}

De download en installeert AEM toe:voegen-On van Commerce voor AEM 6.5 van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

Start en installeer het vereiste AEM 6.5 Service Pack. Wij adviseren installerend het laatste beschikbare de dienstpak.

>[!NOTE]
>
>Dit zal door CSE voor AEM Beheerde klanten van de Dienst worden gedaan.

### AEM aansluiten op uw Commerce-systeem {#connect}

AEM kunnen worden aangesloten op elk handelssysteem dat een toegankelijk GraphQL-eindpunt voor AEM heeft. Deze eindpunten zijn gewoonlijk openbaar beschikbaar, of kunnen via privé VPN of lokale verbindingen afhankelijk van de individuele projectopstelling worden verbonden.

Naar keuze, kan de authentificatiekop worden verstrekt om extra CIF eigenschappen te gebruiken die authentificatie vereisen.

De projecten die door het [ AEM Archieftype van het Project ](https://github.com/adobe/aem-project-archetype) worden geproduceerd, en [ AEM de Opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) die reeds inbegrepen in [ gebrek config ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) is moeten worden aangepast.

Vervang de waarde van `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` door het GraphQL-eindpunt van uw handelssysteem. Deze configuratie kan via de console worden gedaan OSGI of door de configuratie OSGI via het project op te stellen. Verschillende configuraties voor staging- en productiesystemen worden ondersteund met verschillende AEM-uitvoeringsmodi.

De AEM Content en Commerce Add-On en CIF Core Components gebruiken zowel AEM server-side als client-side verbindingen. Client-side CIF Core Components and CIF Add-on authoring tools maken standaard verbinding met `/api/graphql`. Dit kan worden aangepast via de CIF Cloud Service config indien nodig (zie hieronder).

CIF toe:voegen-op verstrekt een de volmachtsservlet van GraphQL bij `/api/graphql` die naar keuze voor [ lokale ontwikkeling ](develop.md) kan worden gebruikt. Voor productieplaatsingen wordt het sterk geadviseerd om een omgekeerde volmacht aan het handelsGraphQL eindpunt via AEM Dispatcher of bij andere netwerklagen (zoals CDN) te plaatsen.

## Opslag en catalogi configureren {#catalog}

Toe:voegen-aan en [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components) kunnen op veelvoudige AEM plaatsstructuren worden gebruikt die met verschillende handelshoudingen (of opslagmeningen, etc. worden verbonden). Standaard wordt de CIF Add-On geïmplementeerd met een standaardconfiguratie die verbinding maakt met de standaardopslag en catalogus van Adobe Commerce.

Deze configuratie kan voor het project via CIF Cloud Service worden aangepast config die deze stappen volgt:

1. Ga in AEM naar Extra > Cloud Servicen > Configuratie CIF

2. Selecteer de handelsconfiguratie u wilt veranderen

3. De configuratie-eigenschappen openen via de actiebalk

![ CIF de Configuratie van Cloud Servicen ](/help/commerce/cif/assets/cif-cloud-service-config.png)

De volgende eigenschappen kunnen worden geconfigureerd:

- GraphQL Client - selecteer de geconfigureerde GraphQL-client voor commerciële back-endcommunicatie. Dit moet standaard blijven.
- Winkelweergave - de weergave-id van de winkel. Als dit leeg is, wordt de standaardwinkelweergave gebruikt.
- GraphQL Proxy Path - de Volmacht van GraphQL van de weg URL in AEM gebruik aan volmachtsverzoeken aan het commerciële achterste eindpunt van GraphQL.

  >[!NOTE]
  >
  >In de meeste instellingen mag de standaardwaarde `/api/graphql` niet worden gewijzigd. Alleen geavanceerde instellingen die de opgegeven GraphQL-proxy niet gebruiken, moeten deze instelling wijzigen.

- Schakel ondersteuning voor UID-catalogus in - schakel ondersteuning voor UID in in plaats van voor ID in de commerciële back-end GraphQL-aanroepen.

  >[!NOTE]
  >
  >Ondersteuning voor UID&#39;s is geïntroduceerd in Adobe Commerce 2.4.2. Schakel deze optie alleen in als uw commerciële backend een GraphQL-schema van versie 2.4.2 of hoger ondersteunt.

- Hoofdcategorie-id van catalogus - de id (UID of ID) van de hoofdmap van de opslagcatalogus

  >[!CAUTION]
  >
  >Vanaf CIF Core Components versie 2.0.0 is de ondersteuning voor `id` verwijderd en vervangen door `uid` . Als uw project CIF versie 2.0.0 van de Componenten van de Kern gebruikt moet u de Steun van UID van de Catalogus toelaten en een geldige categorieUID als &quot;Identifier van de Categorie van de Hoofdstad van de Catalogus gebruiken&quot;.

De configuratie hierboven wordt getoond is voor verwijzing. De projecten zouden hun eigen configuraties moeten verstrekken.

Voor complexere montages die veelvoudige AEM plaatsstructuren gebruiken die met verschillende handelscatalogi worden gecombineerd zien het [&#128279;](configuring/multi-store-setup.md) leerprogramma van de Opstelling van de multi-Opslag van Commerce 0&rbrace; &lbrace;.

## Aanvullende bronnen {#additional-resources}

- [ AEM Archetype van het Project ](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store ](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce Multi-Store Setup](configuring/multi-store-setup.md)
