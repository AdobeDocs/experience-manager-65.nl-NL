---
title: '"Correspondentenbeheer: Problemen oplossen"'
seo-title: Problemen met Correspondentenbeheer oplossen
description: Problemen met Correspondentenbeheer oplossen
seo-description: Problemen met Correspondentenbeheer oplossen
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Correspondentenbeheer: Problemen oplossen {#correspondence-management-troubleshooting}

## Fouten bij het opslaan van een letter {#errors-when-saving-a-letter}

### Probleem {#issue}

Een van de volgende fouten wordt weergegeven bij het opslaan van een letter:

* Gegevensbinding niet aanwezig voor de tekstmodule
* Geef de benodigde eigenschapgegevens op voor het volgende:

### Reason {#reason}

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
1. Selecteer **Correspondence Management Configurations**.
1. Schakel in **Correspondence Management Configurations** de optie **Lettercache inschakelen uit** en klik **op Opslaan.**
1. Schakel **Lettercache** inschakelen in en klik op **Opslaan**.
1. Bekijk de brief opnieuw.

