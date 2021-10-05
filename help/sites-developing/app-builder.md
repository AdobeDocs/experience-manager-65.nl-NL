---
title: Uitbreiding van [!DNL Adobe Experience Manager] 6.5 met Adobe Developer App Builder.
description: Uitbreiding van [!DNL Adobe Experience Manager] 6.5 met Adobe Developer App Builder.
source-git-commit: e6153e1a816bb9169f96fa75827593485a6ddbd4
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---


# [!DNL Adobe Experience Manager] uitbreiden met Adobe Developer App Builder {#extend-using-app-builder}

## Wat is App Builder voor AEM {#project-firefly}

De nieuwe Adobe Developer App Builder biedt een uitbreidbaarheidskader waarmee een ontwikkelaar AEM functies eenvoudig kan uitbreiden.

App Builder biedt een geïntegreerd extern uitbreidingsframework voor het integreren en maken van aangepaste ervaringen die Adobe Experience Manager uitbreiden. Met dit volledige rekbaarheidskader, dat op Adobe wordt gebouwd kunnen de ontwikkelaars de microdiensten van de douanemenu&#39;s bouwen, uitbreiden, en Adobe Experience Manager over Adobe oplossingen en de rest van de stapel van IT integreren.

App Builder biedt klanten een manier om Adobe Experience Manager in verschillende gebruiksgevallen eenvoudig uit te breiden:

* Middleware-uitbreidbaarheid: sluit externe systemen aan met Adobe-toepassingen die aangepaste connectors maken of gebruikmaken van een reeks vooraf gebouwde integraties.
* De Uitbreidbaarheid van de Diensten van de kern - breid kerntoepassingsmogelijkheden door het standaardgedrag met douaneeigenschappen &amp; bedrijfslogica uit te breiden.
* Gebruikerservaring Uitbreidbaarheid: breid de kernervaring uit om bedrijfsvereisten te ondersteunen of klantspecifieke digitale eigenschappen, winkelcentra en back-office toepassingen te ontwikkelen.

App Builder (voorheen Project Firefly genoemd) is sinds zomer 2020 beschikbaar voor zakelijke klanten en partners via onze Voorvertoning voor ontwikkelaars. De algemene beschikbaarheid (GA) van App Builder is gepland voor december 2021. We verwelkomen ontwikkelaars om App Builder uit te proberen via ons [proefprogramma](http://adobe.ly/appbuilder-trial).

>[!NOTE]
>
> Voor AEM as a Cloud Service klanten die de App Builder willen benutten, gaat u naar [Adobe Experience Manager as a Cloud Service uitbreiden met de Adobe Developer App Builder](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/configuring-and-extending/app-builder.html).

## Architectuur {#architecture}

In plaats van een out-of-the-box oplossing biedt Adobe Developer App Builder een gemeenschappelijk, consistent en gestandaardiseerd ontwikkelingsplatform voor het uitbreiden van Adobe Cloud-oplossingen, zoals AEM:

* Adobe Developer Console — Voor de ontwikkeling van aangepaste microservices en extensies kunnen ontwikkelaars projecten bouwen en beheren en tegelijkertijd toegang krijgen tot alle hulpmiddelen en API&#39;s die zij nodig hebben om plug-ins en integratie te maken.
* Gereedschappen voor ontwikkelaars — Open-source-gereedschappen, SDK&#39;s en bibliotheken waarmee ontwikkelaars eenvoudig aangepaste extensies en integratie kunnen maken. Gebruik Spectrum Reageren (de UI toolkit van Adobe) om één gemeenschappelijke UI voor alle Adobe te hebben apps.
* Services — I/O-runtime voor het hosten van infrastructuur op ons serverplatform en I/O-gebeurtenissen voor op gebeurtenissen gebaseerde integratie. Wij bieden ook offline ondersteuning voor het opslaan van gegevens en bestanden.
* Adobe Experience Cloud — Ontwikkelaars kunnen extensies en integraties indienen die binnen hun Experience Cloud Org moeten worden gepubliceerd. Systeembeheerders kunnen deze extensies vervolgens controleren, beheren en goedkeuren. Na publicatie vindt u naast andere Adobe Experience Cloud-apps ook de aangepaste App Builder-extensies en -gereedschappen.

In het volgende diagram ziet u hoe een standaardtoepassing die is gebaseerd op App Builder, deze functies gebruikt:

![Architectuur](assets/firefly-architecture.jpg)

Voor meer details over de architectuur van de Bouwer van de App, heb een blik bij [Overzicht van de Architectuur](https://www.adobe.io/app-builder/docs/guides/).

## Aan de slag met App Builder {#additional-resources}

Om u te helpen aan de slag te gaan met App Builder hebben we een reeks documentatie gemaakt waarmee u kunt beginnen:

* [Aan de slag met App Builder](https://www.adobe.io/app-builder/docs/getting_started/)

## Doorgaan met leren met documentatie {#appbuilder-documentation}

App Builder biedt video&#39;s en documentatie voor ontwikkelaars, waaronder hulplijnen en documentatie over naslaggidsen, waarmee u uw eigen aangepaste toepassingen kunt ontwikkelen:

* [Documentatie voor App Builder](https://www.adobe.io/app-builder/docs/overview/)
* [Video&#39;s over App Builder](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Een van de voorbeeldtoepassingen uitproberen {#appbuilder-codesamples}

Klaar om te beginnen met ontwikkelen? We hebben veel voorbeeldtoepassingen waarmee u snel aan de slag kunt:

* [Code-labels voor App Builder op de website voor Adobe-ontwikkelaars](https://www.adobe.io/app-builder/docs/resources/)

## Ondersteuning {#support}

Voor het type verzoeken voor ondersteuning van ontwikkelaars raden we ontwikkelaars aan ons [Experience League-forum](https://experienceleaguecommunities.adobe.com/t5/project-firefly/ct-p/project-firefly) te gebruiken.
