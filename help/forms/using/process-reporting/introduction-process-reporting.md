---
title: Inleiding tot Process Reporting
description: Inleiding en belangrijkste mogelijkheden van AEM Forms bij JEE Process Reporting
content-type: reference
topic-tags: process-reporting
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: 674d28dc-7353-49de-9e12-b1998e1509c7
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Inleiding tot Process Reporting{#introduction-to-process-reporting}

![procesrapportage](assets/process-reporting.png)

De Rapportering van het proces is een browser-gebaseerd hulpmiddel dat u gebruikt om rapporten over de processen en de taken van AEM Forms tot stand te brengen en te bekijken.

De Rapportering van het proces verstrekt een reeks out-of-the-box rapporten die u, informatie over lange lopende processen, procesduur, en werkschemavolume laten filtreren, bekijken.

Bovendien verstrekt de Rapportering van het Proces een interface om ad hoc vragen in werking te stellen en de meningen van het douanerapport in het Proces te integreren Meldend gebruikersinterface.

Zie voor de lijst met ondersteunde browsers [Door AEM Forms ondersteunde platforms](/help/forms/using/aem-forms-jee-supported-platforms.md).

Procesrapportage is gebaseerd op modules die:

* Procesgegevens uit AEM Forms-database lezen
* Procesgegevens publiceren naar een ingesloten Process Reporting-opslagplaats
* Biedt een op een browser gebaseerde gebruikersinterface voor het weergeven van rapporten

## Belangrijkste mogelijkheden {#key-capabilities}

### Altijd melden {#always-on-reporting}

![locatiebeheer](assets/site-management.png)

Bekijk de lijst van langdurige processen, kaarten van de procesduur, en looppasvragen gebruikend filters.

De Rapportering van het proces verstrekt ook de optie om het rapport en vraaggegevens in formaat uit te voeren CSV.

### Adhocrapporten {#adhoc-reports}

![afdrukken-&amp;-color](assets/print-&-colour.png)

Gebruik filters om een specifieke weergave van uw gegevens op te halen.

U kunt processen of taken op identiteitskaart, duur, begin en einddata, procesinitiator, etc. zoeken.

U kunt meerdere filters combineren om specifieke rapporten te maken.

U kunt de rapportfilters dan opslaan om op een recentere datum of een tijd te lopen.

### Proces-/taakgeschiedenis {#process-task-history}

![bestandsbeheer](assets/file-management.png)

AEM Forms-servers voeren een groot aantal processen parallel uit. Deze processen blijven bij de overgang van de ene naar de andere staat. Door Forms-gegevens regelmatig naar de Process Reporting repository te publiceren, behoudt Process Reporting de overgangsinformatie over de processen die in AEM Forms worden uitgevoerd.

### Toegangsbeheer {#access-control-br}

![naamloos](assets/untitled.png)

Process Reporing biedt op toestemming gebaseerde toegang tot de gebruikersinterface.

Dit betekent slechts hebben de gebruikers met het melden van toestemmingen toegang tot het Proces Meldend gebruikersinterface.
