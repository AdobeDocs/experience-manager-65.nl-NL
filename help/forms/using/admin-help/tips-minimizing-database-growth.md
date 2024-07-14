---
title: Tips voor het minimaliseren van databasegroei
description: Bij langlevende processen worden procesgegevens opgeslagen in de database met AEM formulieren. De groei van de AEM formulierdatabase kan worden geminimaliseerd met behulp van een paar eenvoudige strategieën voor procesontwerp en productconfiguratie.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: f64efb06-815a-4608-ba1c-39e22f344ebb
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# Tips voor het minimaliseren van databasegroei {#tips-for-minimizing-database-growth}

Bij langlevende processen worden procesgegevens opgeslagen in de database met AEM formulieren. De groei van de AEM formulierdatabase kan worden geminimaliseerd met behulp van een paar eenvoudige strategieën voor procesontwerp en productconfiguratie.

## Tips voor procesontwerp {#process-design-tips}

Gebruik waar mogelijk kortstondige processen. Bij kortstondige processen worden procesgegevens niet in de database opgeslagen. Het nadeel van het gebruiken van kortstondige processen is dat hun status en staat niet in beleidsconsole worden gevolgd en er is geen geschiedenis van het proces.

Sommige de dienstverrichtingen, zoals de Assign verrichting van de Taak (de dienst van de Gebruiker), vereisen dat zij in langlevende processen worden gebruikt. In dit geval kunt u het proces segmenteren in verschillende subprocessen en ze zo mogelijk van korte duur maken. Als u deze strategie gebruikt, zouden kortstondige subprocessen grote gegevenspunten, zoals documentwaarden moeten behandelen.

Gebruik spaarzaam variabelen. Wanneer het gebruiken van langlevende processen, voor elke procesinstantie, wordt de ruimte toegewezen op het gegevensbestand voor elke variabele in het proces. Met een strategisch gebruik van variabelen kan veel ruimte worden bespaard. U kunt bijvoorbeeld waarden van variabelen overschrijven wanneer oude waarden niet meer nodig zijn in het proces. Verwijder alle variabelen die u hebt gemaakt en die u niet gebruikt. U kunt het proces valideren om ongebruikte variabelen te zoeken.

Gebruik eenvoudige variabeletypen (bijvoorbeeld tekenreeks of int) en vermijd waar mogelijk het gebruik van complexe variabeletypen. De ruimte van het gegevensbestand wordt toegewezen voor variabelen zelfs wanneer zij geen waarde bevatten. Complexe variabelen vereisen doorgaans meer ruimte dan eenvoudige variabelen.

## Tips voor producttoediening {#product-administration-tips}

Gebruik effectief GDS (global document storage). In de GDS-map op de Forms-server worden onder andere bestanden opgeslagen die worden doorgegeven aan services die onderdeel zijn van AEM formulieren in processen. Om de prestaties te verbeteren, worden kleinere documenten in plaats daarvan opgeslagen in het geheugen en in het gegevensbestand voortgeduurd.

De beheerconsole stelt het StandaardGealigneerde bezit van de Grootte van het Document van het Document bloot voor het vormen van de maximumgrootte van documenten die in geheugen worden opgeslagen en in het gegevensbestand voortgeduurd. (Zie [ algemene AEM vormmontages ](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings) vormen.) Als u deze eigenschap instelt op een lage waarde, blijven de meeste documenten in de GDS-map staan in plaats van in de database. Het voordeel is dat u de bestanden gemakkelijker kunt verwijderen wanneer ze niet meer nodig zijn wanneer ze in de GDS-map zijn opgeslagen.
