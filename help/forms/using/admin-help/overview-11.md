---
title: Overzicht van Health Monitor
description: Dit document geeft een overzicht van de Health Monitor en informatie over hoe u deze kunt openen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 05f8b430-141e-4921-98b1-a0d8f636e478
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Overzicht van Health Monitor {#overview-of-health-monitor}

Health Monitor biedt kritieke informatie over het AEM formuliersysteem, zoals serverinformatie, geheugengebruik en processorgebruik. Ook beschikbaar zijn de statistieken van de Manager van het Werk, zoals het aantal werkpunten of banen in de rij en hun status. U kunt de volgende taken uitvoeren met Health Monitor:

* Controleren of uw systeem correct wordt uitgevoerd
* Informatie weergeven om systeemproblemen te diagnostiseren terwijl deze zich voordoen
* Bewerkingen uitvoeren op werkitems of taken die problemen geven
* Verouderde records uit de taakbeheerdatabase verwijderen

De pagina Health Monitor in de beheerconsole heeft drie tabbladen:

* Het lusje van het Systeem toont middel controlerende grafieken en informatie over de Server van Forms (of knoop in een gegroepeerde milieu). (Zie [&#x200B; het systeeminformatie van de Mening &#x200B;](/help/forms/using/admin-help/view-system-information.md#view-system-information).)
* Op het tabblad Werkbeheer worden gegevens weergegeven die betrekking hebben op Werkbeheer, zoals het aantal werkitems in de werkbeheerwachtrij. U kunt de informatie filteren door diverse criteria te gebruiken of individuele het werkpunten te beheren door de verrichtingshulpmiddelen te gebruiken. (Zie [&#x200B; statistieken van de Mening met betrekking tot de Manager van het Werk &#x200B;](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)
* Met het tabblad Planning voor taakverwijdering kunt u verouderde records uit de database van Taakbeheer verwijderen. (Zie [&#x200B; verslagen van het gegevensbestand van de Manager van de Baan &#x200B;](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database) zuiveren.)

De webpagina Health Monitor wordt gevuld met statistieken die via een Gemfire-API zijn verzameld. Deze API ontdekt automatisch alle knopen in een cluster. Het lost ook veiligheidskwesties op die voorkomen wanneer het verzamelen van statistieken van achter volmachtsservers of ladingsbalancers. Java-opties zijn beschikbaar om de Health Monitor te verfijnen, waardoor de invloed op de prestaties van de omgeving van uw AEM formulieren afneemt. (Zie [&#x200B; de prestaties van de Monitor van de Gezondheid verfijnen &#x200B;](/help/forms/using/admin-help/fine-tuning-health-monitor-performance.md#fine-tuning-health-monitor-performance).)

**Monitor van de Gezondheid van de Toegang**

1. Klik in de beheerconsole op Health Monitor rechtsboven op de pagina.
