---
title: Integreren met Adobe Target
seo-title: Integreren met Adobe Target
description: Meer informatie over de integratie van AEM met Adobe Target.
seo-description: Meer informatie over de integratie van AEM met Adobe Target.
uuid: b90346e8-9757-4272-a870-bbe5e647303f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 454854f8-6053-406c-888d-f427777bf570
translation-type: tm+mt
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 1%

---


# Integreren met Adobe Target{#integrating-with-adobe-target}

Als onderdeel van de Adobe Marketing Cloud kunt u met [Adobe Target](http://www.adobe.com/ro/solutions/testing-targeting/testandtarget.html) de relevantie van inhoud vergroten door de inhoud op alle kanalen te richten en te meten. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM heeft de doelworkflow overgenomen die wordt gebruikt in Adobe Target Standard. Als u Target gebruikt, bent u bekend met de omgeving voor doelbewerking in AEM.

Integreer uw AEM-sites met Adobe Target om de inhoud van uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Target-publiek om persoonlijke ervaringen te creëren.
* Contextgegevens naar Target verzenden wanneer bezoekers op je pagina&#39;s reageren.
* Conversietarieven bijhouden.

Voer de volgende taken uit om te integreren met Target:

1. [Voorwaardelijke taken](/help/sites-administering/target-requirements.md)uitvoeren: Registreer u bij Adobe Target en configureer bepaalde aspecten van de AEM-auteur. Uw Adobe Target-account moet minimaal **fiatteur **level-machtigingen hebben. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

1. Ofwel:

   1. [Ga naar Adobe Target](/help/sites-administering/opt-in.md): De wizard voor aanmelding neemt uw Target-accountgegevens in aanmerking en maakt een Adobe Target-cloudconfiguratie en een Target Framework. De wizard koppelt uw sites ook aan het Target Framework. Als de wizard geen verbinding kan maken met het doel, raadpleegt u de sectie Problemen met de [verbinding oplossen](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) . Vervolgens kunt u de standaardwolkenconfiguraties [](/help/sites-administering/target-configuring.md#modifying-the-opt-in-wizard-configurations)wijzigen: Indien nodig wijzigt u de cloudconfiguratie en het framework dat de wizard voor aanmelding heeft gemaakt. Wijzig bijvoorbeeld het framework om extra contextgegevens naar Target te verzenden. Als u Adobe Analytics wilt gebruiken als rapporteringsbron voor Adobe Target, moet u de wolkenconfiguratie aanpassen om naar de configuratie A4T te richten.
   1. [Handmatig integreren met Adobe Target](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).

1. [Activiteiten](/help/sites-authoring/activitylib.md)configureren: Koppel uw activiteiten aan de Target-cloudconfiguratie.

>[!NOTE]
>
>Zie ook AEM [integreren met Adobe Target en Adobe Analytics met DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

>[!NOTE]
>
>Als u Target met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



>[!CAUTION]
>
>U moet het knooppunt activity settings (activity settings) **cq:ActivitySettings** op de publicatie-instantie beveiligen, zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [Vereisten voor Integratie met Adobe Target](/help/sites-administering/target-requirements.md#securing-the-activity-settings-node) voor meer informatie.

Wanneer de integratie is voltooid, kunt u specifieke inhoud [](/help/sites-authoring/content-targeting-touch.md) ontwerpen die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [Ontwikkelen voor gerichte inhoud](/help/sites-developing/target.md).)

>[!NOTE]
>
>Wanneer u een component in auteur AEM richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (indien gevormd). Er worden geen serveraanroepen vanuit AEM uitgevoerd die naar Adobe Target publiceren.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM met Adobe Target is kennis van Adobe Target, AEM-activiteitenbeheer en AEM-publieksbeheer vereist. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (Zie de documentatie [van](https://docs.adobe.com/content/help/en/target/using/target-home.html)Adobe Target).
* AEM Activity Console (zie [Managing Activity](/help/sites-authoring/activitylib.md)).
* AEM-publiek (zie [Soorten publiek](/help/sites-authoring/managing-audiences.md)beheren).

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 metriek
>* 50 rapporteringssegmenten
>



