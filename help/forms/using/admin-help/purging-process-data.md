---
title: Procesgegevens wissen
seo-title: Procesgegevens wissen
description: Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat resulteert in lagere prestaties van AEM-formulieren en het gebruik van overbodige schijfruimte. Zie hoe u procesgegevens kunt wissen.
seo-description: Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat resulteert in lagere prestaties van AEM-formulieren en het gebruik van overbodige schijfruimte. Zie hoe u procesgegevens kunt wissen.
uuid: 2f04452c-71c6-452c-88c2-7560d35e7dec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3157bb92-4b07-40f2-be4c-8f5807f9a380
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Procesgegevens wissen {#purging-process-data}

Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat resulteert in lagere prestaties van AEM-formulieren en het gebruik van overbodige schijfruimte. Het is een goede gewoonte om procesgegevens te wissen wanneer records niet meer nodig zijn. AEM-formulieren bieden verschillende manieren om procesgegevens te wissen:

* U kunt beheerconsole gebruiken om een eenmalige verwijdering uit te voeren van verouderde records die verwant zijn aan langlevende processen, of om regelmatige automatische purges te plannen. (Zie [Records verwijderen uit de database](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database)van Taakbeheer.)
* Met de API voor AEM-formulieren en de API voor webservices kunt u procesgegevens met betrekking tot langlevende processen programmatisch wissen. (Zie &quot;gegevens van het zuiveringsproces&quot;in [Programmering met AEM- formulieren](https://www.adobe.com/go/learn_aemforms_programming_63).)
* Gebruik het gereedschap voor het verwijderen van processen om processen op basis van de procesnaam en andere parameters te wissen. Zie voor meer informatie het Lees mij-bestand over het gereedschap Repareren in *[map_forms root]*\sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt.

