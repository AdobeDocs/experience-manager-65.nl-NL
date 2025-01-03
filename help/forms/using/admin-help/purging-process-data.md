---
title: Procesgegevens wissen
description: Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat resulteert in lagere AEM formulierprestaties en het gebruik van overbodige schijfruimte. Zie hoe u procesgegevens kunt wissen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0da59dbe-f050-4ee5-b74c-4380b3543b97
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Procesgegevens wissen {#purging-process-data}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat resulteert in lagere AEM formulierprestaties en het gebruik van overbodige schijfruimte. Het is een goede gewoonte om procesgegevens te wissen wanneer records niet meer nodig zijn. AEM formulieren bieden verschillende manieren om procesgegevens te wissen:

* U kunt beheerconsole gebruiken om een eenmalige verwijdering uit te voeren van verouderde records die verwant zijn aan langlevende processen, of om regelmatige automatische purges te plannen. (Zie [ verslagen van het gegevensbestand van de Manager van de Baan ](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database) zuiveren.)
* Met de Java API voor AEM formulieren en de API voor webservices kunt u procesgegevens met betrekking tot langlevende processen programmatisch wissen. (Zie &quot;het Opzuiveren Gegevens van het Proces&quot;in [ Programmering met AEM vormen ](https://www.adobe.com/go/learn_aemforms_programming_63).)
* Gebruik het gereedschap voor het verwijderen van processen om processen op basis van de procesnaam en andere parameters te wissen. Voor details, zie het dossier van het proceszuiveringshulpmiddel, in *[aem_forms wortel]* \sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt.
