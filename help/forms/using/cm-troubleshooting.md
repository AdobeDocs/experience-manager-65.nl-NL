---
title: "Correspondentenbeheer: probleemoplossing"
description: Leer hoe u fouten kunt verwerken die optreden tijdens het opslaan van een brief in een AEM Forms-omgeving.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: cf06796b-bb8c-4a65-8f42-02fb0cfa3ebd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Correspondentenbeheer: Problemen oplossen {#correspondence-management-troubleshooting}

## Fouten bij het opslaan van een letter {#errors-when-saving-a-letter}

### Probleem {#issue}

Een van de volgende fouten wordt weergegeven bij het opslaan van een letter:

* Gegevensbinding niet aanwezig voor de tekstmodule
* Verstrek bezitsinformatie nodig voor het volgende

### Reden {#reason}

Deze fouten kunnen optreden als gevolg van een van de volgende:

* Een gegevenswoordenboek is gebonden aan de letter, maar is niet aanwezig op de server.
* Een gegevenswoordenboek is gebonden aan de letter, maar heeft een onderstrepingsteken (_) in de naam.

### Workaround {#workaround}

Zorg ervoor dat het gegevenswoordenboek dat u in de letter gebruikt, aanwezig is op de server en geen onderstrepingsteken (_) in de naam heeft.

## Fout bij voorvertonen van een letter {#error-when-previewing-a-letter}

### Probleem {#issue-1}

Tijdens het voorvertonen van een letter wordt de fout &#39;&#39;Fout bij het laden van de letter: kan element niet importeren uit XML-invoer&#39;&#39; weergegeven, zelfs wanneer een eerder niet-gepubliceerd tekstelement in de letter wordt gepubliceerd.

### Workaround {#workaround-1}

Stel de lettercache op de publicatieinstantie opnieuw in door de volgende stappen uit te voeren en probeer de letter vervolgens opnieuw weer te geven:

1. Ga naar **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** en aanmelden als Admin.
1. Selecteren **Correspondentiebeheerconfiguraties**.
1. In **Correspondentiebeheerconfiguraties**, uitschakelen **Lettercache inschakelen** en klik vervolgens op **Opslaan.**
1. Controleren **Lettercache inschakelen** en klik vervolgens op **Opslaan**.
1. Bekijk de brief opnieuw.
