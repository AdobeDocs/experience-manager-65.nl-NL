---
title: "Correspondentenbeheer: Problemen oplossen"
seo-title: Correspondence Management Troubleshooting
description: Problemen met Correspondentenbeheer oplossen
seo-description: Correspondence Management Troubleshooting
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Correspondence Management
exl-id: cf06796b-bb8c-4a65-8f42-02fb0cfa3ebd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Correspondentenbeheer: Problemen oplossen {#correspondence-management-troubleshooting}

## Fouten bij het opslaan van een letter {#errors-when-saving-a-letter}

### Probleem {#issue}

Een van de volgende fouten wordt weergegeven bij het opslaan van een letter:

* Gegevensbinding niet aanwezig voor de tekstmodule
* Geef de benodigde eigenschapgegevens op voor het volgende:

### Reden {#reason}

Deze fouten kunnen optreden als gevolg van een van de volgende gebeurtenissen:

* Een gegevenswoordenboek is gebonden aan de letter, maar is niet aanwezig op de server.
* Een gegevenswoordenboek is gebonden aan de letter, maar heeft een onderstrepingsteken (_) in de naam.

### Workaround {#workaround}

Zorg ervoor dat het gegevenswoordenboek dat u in de letter gebruikt, aanwezig is op de server en geen onderstrepingsteken (_) in de naam heeft.

## Fout bij voorvertonen van een letter {#error-when-previewing-a-letter}

### Probleem {#issue-1}

Tijdens het voorvertonen van een letter geeft de fout &quot;Fout bij het laden van de letter: Kan element niet importeren uit XML-invoer.&quot; verschijnt zelfs wanneer een eerder niet-gepubliceerd tekstelement in de letter is gepubliceerd.

### Workaround {#workaround-1}

Stel de lettercache op de publicatieinstantie opnieuw in door de volgende stappen uit te voeren en probeer de letter vervolgens opnieuw weer te geven:

1. Ga naar **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** en meld u aan als Admin.
1. Selecteren **Correspondentiebeheerconfiguraties**.
1. In **Correspondentiebeheerconfiguraties**, uitschakelen **Lettercache inschakelen** en klik vervolgens op **Opslaan.**
1. Inschakelen **Lettercache inschakelen** en klik vervolgens op **Opslaan**.
1. Bekijk de brief opnieuw.
