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
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [ leer meer ](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>Als u geen Adobe Experience Manager (AEM) als uw bron van inhoudsbeheer gebruikt, zie [ Hulp van AEM Mobile On-demand Services ](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM biedt verschillende gereedschappen waarmee u uw inhoud kunt integreren in mobiele toepassingen.

In het volgende diagram ziet u hoe de verschillende componenten van AEM Mobile en On-Demand Services in elkaar passen om inhoud aan mobiele apps te leveren.

AEM Preflight-app kan worden beschouwd als een testomgeving voor het voorvertonen van de app en inhoud voordat deze wordt gepubliceerd; terwijl de AEM Mobile-app de laatste app is die is gemaakt voor distributie.

>[!NOTE]
>
>Om diepgaand over Preflight te leren app, zie [ Gebruikend Preflight app van de AEM ](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) in de Hulp van AEM Mobile On-demand Services.

![ chlimage_1-171 ](assets/chlimage_1-171.png)

>[!NOTE]
>
>In het diagram hierboven, wordt de AEM instantie van Publish niet vereist voor een typisch plaatsingsscenario aan AEM Mobile On-demand Services.

## Een nieuwe mobiele toepassing starten {#starting-a-new-mobile-app}

AEM Mobile is slechts één pijler die het volledige AEM platform vormt.

Voor het starten van een nieuwe AEM Mobile-app-ervaring is een consistente rolcombinatie vereist voordat deze gereed is voor het bewerken van inhoud. De volgende rollen bieden een beginpunt voor het maken van een AEM Mobile-toepassing:

* **Beheerder**
* **Ontwikkelaar**
* **Auteur**

>[!NOTE]
>
>Voordat u met AEM Mobile gaat werken en de stappen in deze gids voor aan de slag uitvoert, moeten gebruikers vertrouwd zijn met AEM. Leer de grondbeginselen van AEM [ hier ](/help/sites-deploying/deploy.md).

### Het AEM Mobile-toepassingsdashboard begrijpen {#understanding-the-aem-mobile-application-dashboard}

Alvorens de rollen en de verantwoordelijkheden te begrijpen, zou de gebruiker grondige kennis van **het Centrum van de Controle van AEM Mobile** of het **Dashboard van de Toepassing** moeten hebben. Klik [ hier ](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor diepgaand begrip.

### AEM-beheerder {#aem-administrator}

Een ***AEM beheerder*** is verantwoordelijk voor het toevoegen van een toepassing aan de catalogus van AEM Mobile, of door een toepassing te creëren gebruikend de aanmaaktovenaar, of door een bestaande toepassing in te voeren. AEM beheerders die een app gebruikend AEM Mobile *creatietovenaar* creeren typisch één van de gewenste toepassingsmalplaatjes of van Adobe uit-van-de-doos verwijzingssteekproeven of (gewoonlijk) een douane app malplaatje creëren door *AEM ontwikkelaars.*

Een AEM beheerder is verantwoordelijk voor de volgende taken wanneer u een app maakt met AEM Mobile On-demand Services:

* [AEM Mobile instellen](/help/mobile/aem-mobile-setup.md)
* [Uw gebruikers- en gebruikersgroepen configureren](/help/mobile/aem-mobile-configure-users.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Inhoudsservices beheren](/help/mobile/developing-content-services.md)

Om met de rollen en de verantwoordelijkheden van een Beheerder begonnen te worden, zie [ het Beheer Inhoud om AEM Mobile On-demand Services ](/help/mobile/aem-mobile.md) te gebruiken.

## AEM Developer {#aem-developer}

Een **AEM ontwikkelaar** breidt zich uit en leidt tot de malplaatjes en de componenten van het douaneWeb om *AEM Auteur *toe te laten om mooie en boeiende mobiele ervaringen tot stand te brengen. Deze sjablonen en componenten zijn niet alleen geoptimaliseerd voor de wereld van de mobiele app, maar communiceren zowel naar het apparaat als naar de AEM server (elke externe server) naar de eindpunten van de lokale service. AEM ingebouwde inhoudsredacteur wordt gebruikt door *AEM Auteurs* om rijke en relevante ervaringen binnen app, met inbegrip van integratie met de rest van Adobe Experience Cloud tot stand te brengen.

Een AEM ontwikkelaar is verantwoordelijk voor de volgende taken bij het maken van een app met AEM Mobile On-demand Services:

* [App-sjablonen en -componenten](/help/mobile/app-templates-and-components1.md)
* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
* [Eigenschappen van inhoud en inhoud exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [AEM Mobile Content Services ontwikkelen](/help/mobile/developing-content-services.md)

Om met de rollen en de verantwoordelijkheden van de Ontwikkelaar te beginnen, zie [ het Ontwikkelen AEM Inhoud voor AEM Mobile On-demand Services ](/help/mobile/aem-mobile-on-demand.md).

>[!NOTE]
>
>De *rol van een* AEM ontwikkelaar begint en beëindigt niet met de ontwikkeling van malplaatjes en componenten. Een *AEM ontwikkelaar* kan volledig nieuwe app tot stand brengen eerder dan eenvoudig de uit-van-de-doos steekproef van de verwijzingsimplementatie uitbreiden.

## AEM auteur {#aem-author}

Een ***AEM Auteur* (of *Markering*) **gebruikt de douane ontwikkelde of uit-van-de-doos malplaatjes en componenten om pagina&#39;s toe te voegen en uit te geven, componenten te slepen en neer te zetten en media van alle types van DAM met inbegrip van beelden, video&#39;s, en tekstfragmenten (inhoudsfragmenten) toe te voegen. AEM ingebouwde inhoudsredacteur wordt dan gebruikt door *AEM Auteurs* om rijke en relevante ervaringen binnen app, met inbegrip van integratie met de rest van Adobe Experience Cloud tot stand te brengen.

Een AEM auteur moet de volgende onderwerpen begrijpen wanneer hij een app maakt met AEM Mobile On-demand Services:

* [AEM Mobile-toepassingsdashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Handelingen voor het maken en configureren van toepassingen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud Configuration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Inhoud beheren](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Overzicht van Content Services](/help/mobile/develop-content-as-a-service.md)

Om met de rollen en de verantwoordelijkheden van een Auteur begonnen te worden, zie [ Authoring AEM Inhoud voor AEM Mobile On-demand Services App ](/help/mobile/mobile-apps-ondemand.md).

>[!NOTE]
>
>Een AEM auteur is ook verantwoordelijk voor het instellen van machtigingen, het maken van kaarten en lay-outs en het verzenden van pushberichten. Ook, voor meer informatie over methodes voor auteursinhoud; het beheren van artikelen en inzamelingen; het creëren van banners, kaarten, en lay-outs in AEM Mobile, zie [ AEM Mobile Portaal On-Demand ](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2).
