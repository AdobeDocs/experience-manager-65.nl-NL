---
title: Upgrade naar AEM 6.5
seo-title: Upgrade naar AEM 6.5
description: Meer informatie over de basisprincipes van het upgraden van een oudere AEM-installatie naar AEM 6.5.
seo-description: Meer informatie over de basisprincipes van het upgraden van een oudere AEM-installatie naar AEM 6.5.
uuid: 45368056-273c-4f1a-9da6-e7ba5c2bbc0d
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: ebd99cc4-8762-4c28-a177-d62dac276afe
docset: aem65
targetaudience: target-audience upgrader
translation-type: tm+mt
source-git-commit: 5035c9630b5e861f4386e1b5ab4f4ae7a8d26149

---


# Upgrade naar AEM 6.5 {#upgrading-to-aem}

In deze sectie, behandelen wij bevordering van een installatie AEM aan AEM 6.5:

* [Uw upgrade plannen](/help/sites-deploying/upgrade-planning.md)
* [Het beoordelen van de Complexiteit van de Verbetering met de Detector van het Patroon](/help/sites-deploying/pattern-detector.md)
* [Achterwaartse Verenigbaarheid in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
* [Upgradeprocedure](/help/sites-deploying/upgrade-procedure.md)
* [Code en aanpassingen bijwerken](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Onderhoudstaken vóór upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Een in-place upgrade uitvoeren](/help/sites-deploying/in-place-upgrade.md)
* [Controles en probleemoplossing na upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Duurzame verbeteringen](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)
* [Repositoregeling herstructurering in AEM 6.5](/help/sites-deploying/repository-restructuring.md)

Voor gemakkelijkere verwijzing naar de instanties AEM die bij deze procedures betrokken zijn, worden de volgende termen gebruikt in deze artikelen:

* De *broninstantie* is de instantie AEM die u van bevordert.
* De *doelinstantie* is degene waaraan u werkt.

>[!NOTE]
>
>In het kader van de inspanningen om de betrouwbaarheid van upgrades te verbeteren, heeft AEM een uitgebreide herstructurering van de opslagplaats ondergaan. Voor meer informatie over hoe te om zich aan de nieuwe structuur aan te passen, zie de Herstructurering van de [Bewaarplaats in AEM.](/help/sites-deploying/repository-restructuring.md)

## Wat is er veranderd? {#what-has-changed}

Het volgende zijn belangrijke veranderingen van nota over de laatste verscheidene versies van AEM:

AEM 6.0 introduceerde de nieuwe Jackrabbit Oak-opslagplaats. Persistentie Managers werden vervangen door [Micro Kernels](/help/sites-deploying/platform.md#contentbody_title_4). Vanaf versie 6.1 wordt CRX2 niet meer ondersteund. Een migratiehulpmiddel genoemd crx2oak moet worden in werking gesteld om CRX2 bewaarplaatsen van 5.6.1 instanties te migreren. Voor meer informatie, zie het [Gebruiken van het Hulpmiddel](/help/sites-deploying/using-crx2oak.md)van de Migratie CRX2OAK.

Als Asset Insights moet worden gebruikt en u een upgrade uitvoert van een versie die ouder is dan AEM 6.2, moeten de bedrijfsmiddelen worden gemigreerd en moeten er ID&#39;s worden gegenereerd via een JMX-boon. In onze interne tests werden 125.000 bedrijfsmiddelen op een TarMK-omgeving over een uur gemigreerd, maar uw resultaten kunnen afwijken.

6.3 werd een nieuw formaat voor de `SegmentNodeStore`TarMK ingevoerd, dat de basis vormt voor de tenuitvoerlegging van de TarMK. Als u een upgrade uitvoert van een versie die ouder is dan AEM 6.3, is er een migratie naar opslagplaats nodig als onderdeel van de upgrade, met inbegrip van systeemuitvaltijd.

De Techniek van Adobe schat dit om rond 20 minuten te zijn. Merk op dat het opnieuw indexeren niet noodzakelijk zal zijn. Bovendien is een nieuwe versie van de crx2oak-tool vrijgegeven om te werken met de nieuwe repository indeling.

**Deze migratie is niet vereist als upgrade van AEM 6.3 naar AEM 6.5 wordt uitgevoerd.**

De preupgrade-onderhoudstaken zijn geoptimaliseerd om automatisering te ondersteunen.

De gebruiksopties van de de hulpmiddellijn van crx2oak zijn veranderd om automatiseringsvriendelijk te zijn en meer verbeteringswegen te steunen.

De controles na de upgrade zijn ook automatiseringsvriendelijk gemaakt.

De periodieke huisvuilinzameling van revisies en de huisvuilinzameling van de gegevensopslag zijn nu routineonderhoudstaken die periodiek moeten worden uitgevoerd. Met de introductie van AEM 6.3, steunt Adobe en adviseert de Online Schoonmaakbeurt van de Revisie. Zie [de Schoonmaakbeurt](/help/sites-deploying/revision-cleanup.md) van de Revisie voor informatie over hoe te om deze taken te vormen.

AEM introduceert onlangs de Detector [van het](/help/sites-deploying/pattern-detector.md) Patroon voor beoordeling van ingewikkeldheid van de verbetering aangezien u voor de verbetering begint te plannen. 6.5 is ook sterk gericht op [achterwaartse compatibiliteit](/help/sites-deploying/backward-compatibility.md) van functies. Tot slot worden de beste praktijken voor [duurzame verbeteringen](/help/sites-deploying/sustainable-upgrades.md) ook toegevoegd.

Voor meer details over wat anders in recente versies AEM is veranderd, zie de volledige versienota&#39;s:

* [https://helpx.adobe.com/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/experience-manager/6-4/release-notes.html)
* [https://helpx.adobe.com/experience-manager/6-5/release-notes.html](https://helpx.adobe.com/experience-manager/6-5/release-notes.html)

## Overzicht van upgrade {#upgrade-overview}

De bevordering van AEM is een multi-stap, soms multi-maandproces. Het volgende overzicht is verstrekt als overzicht van wat in een verbeteringsproject en de inhoud inbegrepen is die in deze documentatie is omvat:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Upgradestroom {#upgrade-overview-1}

Het diagram hieronder vangt de algemene geadviseerde stroom benadrukt de verbeteringsbenadering. Let op de verwijzing naar de nieuwe functies die we hebben geïntroduceerd. De verbetering zou met de Detector van het Patroon moeten beginnen (zie het [Beoordelen van de Complexiteit van de Verbetering met de Detector](/help/sites-deploying/pattern-detector.md)van het Patroon) die u zou moeten laten beslissen de weg u voor verenigbaarheid met AEM 6.4 wilt nemen die op de patronen in het geproduceerde rapport wordt gebaseerd.

Er was een grote nadruk in 6.5 om alle nieuwe eigenschappen achterwaarts compatibel te houden, maar in gevallen waar u nog sommige achterwaartse verenigbaarheidskwesties ziet, staat de verenigbaarheidswijze u toe om ontwikkeling tijdelijk uit te stellen om uw douanecode volgzaam met 6.5 te houden. Deze benadering helpt u ontwikkelingsinspanning onmiddellijk na de verbetering te vermijden (zie [Achterwaartse Verenigbaarheid in AEM 6.5](/help/sites-deploying/backward-compatibility.md)).

Tot slot, in uw 6.5 ontwikkelingscyclus, helpen de eigenschappen die onder Duurzame Verbeteringen (zie [Duurzame Verbeteringen](/help/sites-deploying/sustainable-upgrades.md)) worden geïntroduceerd u beste praktijken volgen om toekomstige verbeteringen nog efficiënter en naadloos te maken.

![6_4_upgrade_overviewflow-diagram-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)

