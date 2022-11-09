---
title: Integreren met Adobe Target
seo-title: Integrating with Adobe Target
description: Meer informatie over de integratie van AEM met Adobe Target.
seo-description: Learn about integrating AEM with Adobe Target.
uuid: b90346e8-9757-4272-a870-bbe5e647303f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 454854f8-6053-406c-888d-f427777bf570
exl-id: 2b17d8cd-a43c-4d54-b990-a6f0cb1db22b
source-git-commit: 63f066013c34a5994e2c6a534d88db0c464cc905
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 1%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

In het kader van de Adobe Marketing Cloud [Adobe Target](https://www.adobe.com/ro/solutions/testing-targeting/testandtarget.html) Hiermee kunt u de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM heeft de doelworkflow overgenomen die wordt gebruikt in Adobe Target Standard. Als u Doel gebruikt, zult u met het richten het uitgeven milieu in AEM vertrouwd zijn.

Integreer uw AEM met Adobe Target om inhoud op uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

Voer de volgende taken uit om met Doel te integreren:

1. [Voorwaardelijke taken uitvoeren](/help/sites-administering/target-requirements.md): Registreer u bij Adobe Target en configureer bepaalde aspecten van de AEM auteur. Uw Adobe Target-account moet minimaal **fiatteur **level-machtigingen hebben. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

1. Ofwel:

   1. [Opteren in Adobe Target](/help/sites-administering/opt-in.md): De wizard voor aanmelding neemt uw doelaccount-informatie in aanmerking en maakt een Adobe Target-cloudconfiguratie en een Target Framework. De tovenaar associeert ook uw plaatsen met het Kader van het Doel. Als de wizard geen verbinding kan maken met het doel, raadpleegt u de [verbindingsproblemen oplossen](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) sectie. U kunt vervolgens [De standaardcloudconfiguraties wijzigen](/help/sites-administering/target-configuring.md#modifying-the-opt-in-wizard-configurations): Indien nodig wijzigt u de cloudconfiguratie en het framework dat de wizard voor aanmelding heeft gemaakt. Wijzig bijvoorbeeld het framework om aanvullende contextgegevens naar Target te verzenden. Als u Adobe Analytics als rapporteringsbron voor Adobe Target wilt gebruiken, moet u de wolkenconfiguratie wijzigen om aan de configuratie A4T te richten.
   1. [Handmatig integreren met Adobe Target](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).

1. [Activiteiten configureren](/help/sites-authoring/activitylib.md): Koppel uw activiteiten aan de doelwolkenconfiguratie.

>[!NOTE]
>
>Zie ook [AEM integreren met Adobe Target en Adobe Analytics met behulp van DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

>[!NOTE]
>
>Als u Doel met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM de 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>


>[!CAUTION]
>
>U moet het knooppunt met activiteiteninstellingen beveiligen **cq:ActivitySettings** op de publicatie-instantie zodat deze niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [Vereisten voor integratie met Adobe Target](/help/sites-administering/target-requirements.md#securing-the-activity-settings-node) voor nadere informatie.

Wanneer de integratie is voltooid, kunt u [doelinhoud auteur](/help/sites-authoring/content-targeting-touch.md) die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [Ontwikkelen voor gerichte inhoud](/help/sites-developing/target.md).)

>[!NOTE]
>
>Wanneer u een component in AEM auteur richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (indien gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM met Adobe Target is kennis van Adobe Target, AEM Activiteitenbeheer en AEM beheer van soorten publiek vereist. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (Zie de [Adobe Target-documentatie](https://experienceleague.adobe.com/docs/target/using/target-home.html)).
* AEM Activiteitenconsole (zie [Beheersactiviteiten](/help/sites-authoring/activitylib.md)).
* AEM publiek (zie [Soorten publiek beheren](/help/sites-authoring/managing-audiences.md)).

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 metriek
>* 50 rapporteringssegmenten
>

