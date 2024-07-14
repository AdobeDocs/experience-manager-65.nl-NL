---
title: Integreren met Adobe Target
description: Leer hoe u Adobe Experience Manager kunt integreren met Adobe Target.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 2b17d8cd-a43c-4d54-b990-a6f0cb1db22b
solution: Experience Manager, Experience Manager Sites
feature: Administering,Personalization
role: Admin
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

Als deel van Adobe Marketing Cloud, [ Adobe Target ](https://www.adobe.com/ro/solutions/testing-targeting/testandtarget.html) laat u inhoudsrelevantie door het richten en het meten over alle kanalen verhogen. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM heeft de doelworkflow overgenomen die wordt gebruikt in Adobe Target Standard. Als u Doel gebruikt, zult u met het richten het uitgeven milieu in AEM vertrouwd zijn.

Integreer uw AEM met Adobe Target om inhoud op uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

Voer de volgende taken uit om met Doel te integreren:

1. [ voer in eerste instantie vereiste taken ](/help/sites-administering/target-requirements.md) uit: Register met Adobe Target en vorm bepaalde aspecten van de AEM auteursinstantie. Uw Adobe Target-account moet minimaal **fiatteur **level-machtigingen hebben. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

1. Ofwel:

   1. [ Opt in Adobe Target ](/help/sites-administering/opt-in.md): De opt-in tovenaar neemt uw de rekeningsinformatie van het Doel en leidt tot een de wolkenconfiguratie van Adobe Target en een Kader van het Doel. De tovenaar associeert ook uw plaatsen met het Kader van het Doel. Als de tovenaar niet met doel kan verbinden, zie het [ oplossen van verbindingsprobleem ](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) sectie. U kunt dan [ de standaardwolkenconfiguraties ](/help/sites-administering/target-configuring.md#modifying-the-opt-in-wizard-configurations) wijzigen: Indien noodzakelijk, wijzig de wolkenconfiguratie en het kader dat de opt-in tovenaar creeerde. Wijzig bijvoorbeeld het framework om aanvullende contextgegevens naar Target te verzenden. Als u Adobe Analytics als rapporteringsbron voor Adobe Target wilt gebruiken, moet u de wolkenconfiguratie wijzigen om aan de configuratie A4T te richten.
   1. [ integreren manueel met Adobe Target ](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).

1. [ vorm Activiteiten ](/help/sites-authoring/activitylib.md): Verdeel uw Activiteiten met de de wolkenconfiguratie van het Doel.

>[!NOTE]
>
>Zie ook [ Integrerend AEM met Adobe Target en Adobe Analytics gebruikend DTM ](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

>[!NOTE]
>
>Als u Doel met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM de 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x wordt gevormd met [ http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt gevormd met [ http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>

>[!CAUTION]
>
>Beveilig de knoop van activiteitenmontages **cq:ActivitySettings** op publiceer instantie zodat het voor normale gebruikers ontoegankelijk is. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [ Vereisten voor het Integreren met Adobe Target ](/help/sites-administering/target-requirements.md#securing-the-activity-settings-node) voor gedetailleerde informatie.

Wanneer de integratie volledig is, kunt u [ auteur gerichte inhoud ](/help/sites-authoring/content-targeting-touch.md) die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [ Ontwikkelen voor gerichte Inhoud ](/help/sites-developing/target.md).)

>[!NOTE]
>
>Wanneer u een component in AEM auteur richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (indien gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM met Adobe Target is kennis van Adobe Target, AEM Activiteitenbeheer en AEM beheer van soorten publiek vereist. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (zie de [ documentatie van Adobe Target ](https://experienceleague.adobe.com/docs/target/using/target-home.html)).
* AEM de console van Activiteiten (zie [ het Leiden Activiteiten ](/help/sites-authoring/activitylib.md)).
* AEM Soorten publiek (zie [ het Leiden Soorten publiek ](/help/sites-authoring/managing-audiences.md)).

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 cijfers
>* 50 rapporteringssegmenten
>
