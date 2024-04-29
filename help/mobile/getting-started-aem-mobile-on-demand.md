---
title: Adobe Experience Manager Mobile On-Demand
description: Voor het starten van een nieuwe Adobe Experience Manager (AEM) Mobile-app-ervaring is een combinatie van rollen vereist voordat u inhoud kunt bewerken. Volg deze pagina om te beginnen met AEM mobiele On-Demand-services.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
exl-id: 4be199d8-963d-4807-b9bb-e23fa577c5f2
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---

# AEM Mobile On-Demand{#aem-mobile-on-demand}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>Als u Adobe Experience Manager (AEM) niet gebruikt als bron voor inhoudsbeheer, raadpleegt u [AEM Mobile On-demand Services Help](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM biedt verschillende gereedschappen waarmee u uw inhoud kunt integreren in mobiele toepassingen.

In het volgende diagram ziet u hoe de verschillende componenten van AEM Mobile en On-Demand Services in elkaar passen om inhoud aan mobiele apps te leveren.

AEM Preflight-app kan worden beschouwd als een testomgeving voor het voorvertonen van de app en inhoud voordat deze wordt gepubliceerd; terwijl de AEM Mobile-app de laatste app is die is gemaakt voor distributie.

>[!NOTE]
>
>Ga voor meer informatie over Preflight-app naar [De Preflight-app AEM gebruiken](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) in AEM Mobile On-demand Services Help.

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>In het diagram hierboven, wordt de AEM Publish instantie niet vereist voor een typisch plaatsingsscenario aan AEM Mobile On-demand Services.

## Een nieuwe mobiele toepassing starten {#starting-a-new-mobile-app}

AEM Mobile is slechts één pijler die het volledige AEM platform vormt.

Voor het starten van een nieuwe AEM Mobile-app-ervaring is een consistente rolcombinatie vereist voordat deze gereed is voor het bewerken van inhoud. De volgende rollen bieden een beginpunt voor het maken van een AEM Mobile-toepassing:

* **Beheerder**
* **Ontwikkelaar**
* **Auteur**

>[!NOTE]
>
>Voordat u met AEM Mobile gaat werken en de stappen in deze gids voor aan de slag uitvoert, moeten gebruikers vertrouwd zijn met AEM. Leer de grondbeginselen van AEM [hier](/help/sites-deploying/deploy.md).

### Het AEM Mobile-toepassingsdashboard begrijpen {#understanding-the-aem-mobile-application-dashboard}

Alvorens de rollen en de verantwoordelijkheden te begrijpen, zou de gebruiker grondige kennis van moeten hebben **AEM Mobile Control Center** of de **Toepassingsdashboard**. Klikken [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor een diepgaand begrip.

### AEM-beheerder {#aem-administrator}

An ***AEM*** is verantwoordelijk voor het toevoegen van een toepassing aan de AEM Mobile-catalogus door een toepassing te maken met de wizard Maken of door een bestaande toepassing te importeren. AEM beheerders die een app maken met AEM Mobile *wizard Maken* Selecteer doorgaans een van de gewenste toepassingssjablonen uit de referentiemonsters van de Adobe voor toepassingen die buiten de box vallen of een aangepaste toepassingssjabloon die is gemaakt door *AEM ontwikkelaars*

Een AEM beheerder is verantwoordelijk voor de volgende taken wanneer u een app maakt met AEM Mobile On-demand Services:

* [AEM Mobile instellen](/help/mobile/aem-mobile-setup.md)
* [Uw gebruikers- en gebruikersgroepen configureren](/help/mobile/aem-mobile-configure-users.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Inhoudsservices beheren](/help/mobile/developing-content-services.md)

Om met de rollen en de verantwoordelijkheden van een Beheerder te beginnen, zie [Inhoud beheren voor gebruik van AEM Mobile On-demand Services](/help/mobile/aem-mobile.md).

## AEM Developer {#aem-developer}

An **AEM ontwikkelaar** breidt en creeert douaneWebmalplaatjes en componenten uit om *AEM Auteur *toe te laten om mooie en boeiende mobiele ervaringen tot stand te brengen. Deze sjablonen en componenten zijn niet alleen geoptimaliseerd voor de wereld van de mobiele app, maar communiceren zowel naar het apparaat als naar de AEM server (elke externe server) naar de eindpunten van de lokale service. AEM ingebouwde inhoudeditor wordt gebruikt door *Auteurs AEM* het creëren van rijke en relevante ervaringen binnen de app, waaronder integratie met de rest van de Adobe Experience Cloud.

Een AEM ontwikkelaar is verantwoordelijk voor de volgende taken bij het maken van een app met AEM Mobile On-demand Services:

* [App-sjablonen en -componenten](/help/mobile/app-templates-and-components1.md)
* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
* [Eigenschappen van inhoud en inhoud exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [AEM Mobile Content Services ontwikkelen](/help/mobile/developing-content-services.md)

Ga als volgt te werk om aan de slag te gaan met de rollen en verantwoordelijkheden van de ontwikkelaar: [AEM voor AEM Mobile On-demand Services ontwikkelen](/help/mobile/aem-mobile-on-demand.md).

>[!NOTE]
>
>An *AEM ontwikkelaars* de rol begint en eindigt niet met de ontwikkeling van sjablonen en componenten. An *AEM ontwikkelaar* U kunt een geheel nieuwe app maken in plaats van de voorbeeldcode voor de implementatie van de naslaggids uit te breiden.

## AEM auteur {#aem-author}

An ***AEM auteur* (of *Marketer*)**gebruikt de aangepaste ontwikkelde of out-of-the-box sjablonen en componenten om pagina&#39;s toe te voegen en te bewerken, componenten te slepen en neer te zetten en media van alle typen van de DAM toe te voegen, inclusief afbeeldingen, video&#39;s en tekstfragmenten (inhoudsfragmenten). AEM ingebouwde inhoudeditor wordt dan gebruikt door *Auteurs AEM* het creëren van rijke en relevante ervaringen binnen de app, waaronder integratie met de rest van de Adobe Experience Cloud.

Een AEM auteur moet de volgende onderwerpen begrijpen wanneer hij een app maakt met AEM Mobile On-demand Services:

* [AEM Mobile-toepassingsdashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Handelingen voor het maken en configureren van toepassingen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud Configuration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Inhoud beheren](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Overzicht van Content Services](/help/mobile/develop-content-as-a-service.md)

Ga als volgt te werk om aan de slag te gaan met de rollen en verantwoordelijkheden van een auteur: [Authoring AEM inhoud voor AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md).

>[!NOTE]
>
>Een AEM auteur is ook verantwoordelijk voor het instellen van machtigingen, het maken van kaarten en lay-outs en het verzenden van pushberichten. Zie ook voor meer informatie over methoden voor het ontwerpen van inhoud, het beheren van artikelen en verzamelingen, het maken van banners, kaarten en lay-outs in AEM Mobile [AEM Mobile On-Demand Portal](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2).
