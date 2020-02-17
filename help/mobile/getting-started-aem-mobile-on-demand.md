---
title: AEM Mobile On-Demand
seo-title: AEM Mobile On-Demand
description: Voor het starten van een nieuwe AEM Mobile-app-ervaring is een combinatie van rollen vereist voordat deze gereed is voor het bewerken van inhoud. Volg deze pagina om aan de slag te gaan met AEM Mobile On-Demand Services.
seo-description: Voor het starten van een nieuwe AEM Mobile-app-ervaring is een combinatie van rollen vereist voordat deze gereed is voor het bewerken van inhoud. Volg deze pagina om aan de slag te gaan met AEM Mobile On-Demand Services.
uuid: 175c609d-3cb8-4a1b-bfea-278df272e500
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: introduction
content-type: reference
discoiquuid: dc6891cd-19cc-4dff-8bda-a41ed8af8bfb
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM Mobile On-Demand{#aem-mobile-on-demand}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

>[!NOTE]
>
>Als u AEM niet gebruikt als bron voor inhoudsbeheer, raadpleegt u de Help bij [AEM Mobile On-Demand Services](https://helpx.adobe.com/digital-publishing-solution/topics.html).

AEM biedt verschillende gereedschappen waarmee u uw inhoud kunt integreren in mobiele toepassingen.

In het volgende diagram ziet u hoe de verschillende componenten van AEM Mobile en On-Demand Services in elkaar passen om inhoud aan mobiele apps te leveren.

De Preflight-app van AEM kan worden beschouwd als een testomgeving voor het voorvertonen van de app en inhoud voordat deze wordt gepubliceerd. overwegende dat de AEM Mobile-app de laatste app is die is gemaakt voor distributie.

>[!NOTE]
>
>Zie De Preflight-app [van AEM Mobile On-Demand Services Help voor meer informatie over Preflight](https://helpx.adobe.com/digital-publishing-solution/help/preflight-app.html) gebruiken.

![chlimage_1-171](assets/chlimage_1-171.png)

>[!NOTE]
>
>In het diagram hierboven, wordt AEM publiceren instantie niet vereist voor een typisch plaatsingsscenario aan Mobiele On-Demand van AEM.

## Een nieuwe mobiele toepassing starten {#starting-a-new-mobile-app}

AEM Mobile is slechts één pijler die het volledige AEM-platform vormt.

Voor het starten van een nieuwe AEM Mobile-app-ervaring is een combinatie van rollen vereist voordat deze gereed is voor het bewerken van inhoud. De volgende rollen bieden een beginpunt voor het maken van een nieuwe AEM Mobile-toepassing:

* **Beheerder**
* **Ontwikkelaar**
* **Author**

>[!NOTE]
>
>Voordat u met AEM Mobile gaat werken en de stappen in deze gids voor aan de slag uitvoert, moeten gebruikers bekend zijn met AEM. Leer de grondbeginselen van AEM [hier](/help/sites-deploying/deploy.md).

### Het dashboard voor AEM Mobile-toepassingen begrijpen {#understanding-the-aem-mobile-application-dashboard}

Voordat de gebruiker de rollen en verantwoordelijkheden begrijpt, moet hij of zij over voldoende kennis van het **AEM Mobile Control Center** of het **Application Dashboard** beschikken. Klik [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor een diepgaand begrip.

### AEM-beheerder {#aem-administrator}

Een ***AEM-beheerder*** is verantwoordelijk voor het toevoegen van een nieuwe toepassing aan de AEM Mobile-catalogus door een nieuwe toepassing te maken met de wizard Maken of door een bestaande toepassing te importeren. AEM-beheerders die een nieuwe app maken met de *ontwerpwizard* van AEM Mobile, selecteren doorgaans een van de gewenste toepassingssjablonen uit de referentiemonsters die buiten de box vallen of (in de meeste gevallen) een aangepaste toepassingssjabloon die door *AEM-ontwikkelaars is gemaakt.*

Een AEM-beheerder is verantwoordelijk voor de volgende taken wanneer u een app maakt met AEM Mobile On-Demand Services:

* [AEM Mobile instellen](/help/mobile/aem-mobile-setup.md)
* [Uw gebruikers- en gebruikersgroepen configureren](/help/mobile/aem-mobile-configure-users.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
* [Inhoudsservices beheren](/help/mobile/developing-content-services.md)

Zie Inhoud [beheren voor AEM Mobile On-Demand Services](/help/mobile/aem-mobile.md)gebruiken om aan de slag te gaan met de rollen en verantwoordelijkheden van een beheerder.

## AEM-ontwikkelaar {#aem-developer}

Een **AEM-ontwikkelaar** breidt aangepaste websjablonen en componenten uit om de *AEM-auteur *in staat te stellen prachtige en aantrekkelijke mobiele ervaringen te creëren. Deze sjablonen en componenten zijn niet alleen geoptimaliseerd voor mobiele apps; maar communiceer zowel aan het apparaat als aan de server AEM (om het even welke verre server) aan de eindpunten van de netwerkdienst. De ingebouwde inhoudeditor van AEM wordt door *AEM-auteurs* gebruikt om rijke en relevante ervaringen in de app te creëren, waaronder integratie met de rest van de Adobe Marketing Cloud.

Een AEM-ontwikkelaar is verantwoordelijk voor de volgende taken bij het maken van een app met AEM Mobile On-Demand Services:

* [App-sjablonen en -componenten](/help/mobile/app-templates-and-components1.md)
* [Mobiel met inhoudssynchronisatie](/help/mobile/mobile-ondemand-contentsync.md)
* [Eigenschappen van inhoud en inhoud exporteren](/help/mobile/on-demand-content-properties-exporting.md)
* [AEM Mobile Content Services ontwikkelen](//help/mobile/developing-content-services.md)

Om aan de slag te gaan met de rollen en verantwoordelijkheden van de ontwikkelaar, zie het [Ontwikkelen van AEM Inhoud voor Mobiele On-Demand Services](/help/mobile/aem-mobile-on-demand.md)AEM.

>[!NOTE]
>
>De rol van een *AEM-ontwikkelaar* begint en eindigt niet met de ontwikkeling van sjablonen en componenten. Een *AEM-ontwikkelaar* kan een geheel nieuwe app maken in plaats van de voorbeeldcode voor de implementatie van de kant-en-klare referentie uit te breiden.

## AEM-auteur {#aem-author}

Een ***AEM-auteur *(of*Marketer *)**gebruikt de aangepaste ontwikkelde sjablonen of out-of-the-box-componenten om pagina&#39;s toe te voegen en te bewerken, componenten te slepen en neer te zetten en media van alle typen van de DAM toe te voegen, inclusief afbeeldingen, video&#39;s en tekstfragmenten (inhoudsfragmenten). De ingebouwde inhoudeditor van AEM wordt vervolgens door*AEM-auteurs *gebruikt om rijke en relevante ervaringen in de app te creëren, waaronder integratie met de rest van de Adobe Marketing Cloud.

Een auteur van AEM moet de volgende onderwerpen begrijpen, terwijl het creëren van een app gebruikend Mobiele On-Demand Services AEM:

* [AEM Mobile-toepassingsdashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md)
* [Handelingen voor het maken en configureren van toepassingen](/help/mobile/mobile-apps-ondemand-application-create-configure-action.md)
* [Cloud Configuration](/help/mobile/mobile-on-demand-associating-an-on-demand-app-to-cloud-configuration.md)
* [Inhoud beheren](/help/mobile/mobile-apps-ondemand-manage-content-ondemand.md)
* [Overzicht van Content Services](/help/mobile/develop-content-as-a-service.md)

Zie [Authoring AEM Content for AEM Mobile On-Demand Services App](/help/mobile/mobile-apps-ondemand.md)voor AEM Mobile om aan de slag te gaan met de rollen en verantwoordelijkheden van de auteur.

>[!NOTE]
>
>Een AEM-auteur is ook verantwoordelijk voor het instellen van machtigingen, het maken van kaarten en lay-outs en het verzenden van pushberichten. Voor meer informatie over methoden voor het ontwerpen van inhoud. het beheren van voorwerpen en verzamelingen; zie [AEM Mobile On-Demand Portal](https://helpx.adobe.com/digital-publishing-solution/topics.html#dynamicpod_reference_2)voor het maken van banners, kaarten en lay-outs in AEM Mobile.

