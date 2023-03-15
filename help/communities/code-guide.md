---
title: Codeerrichtlijnen
seo-title: Coding Guidelines
description: Richtlijnen, tips en trucs voor ontwikkelaars van gemeenschappen
seo-description: Communities developer guidelines, tips, and tricks
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: a23aab83-1dfa-4d91-9b6b-6246a2103896
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# Codeerrichtlijnen {#coding-guidelines}

## Richtlijnen, tips en trucs {#guidelines-tips-and-tricks}

Het werken met AEM Communities is geëvolueerd van sterk afhankelijk zijn van de Pagina&#39;s van de Server van Java aan flexibiliteit in het kiezen van het opmaken van scripttalen waar bedrijfslogica, stijl, en paginacontent van elkaar verschillend zijn.

Meer flexibiliteit bij het werken met door de gebruiker gegenereerde inhoud (UGC) is via de API van SocialResourceProvider, waardoor de noodzaak van bewustwording wordt weggenomen [SRP](srp.md) voor de implementatie is gekozen.

Hieronder vindt u verschillende codeerrichtlijnen en aanbevolen procedures voor AEM Communities-ontwikkelaars:

### Code {#code}

* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - hoe te vermijden schrijvend een toepassing die slechts werkt wanneer UGC in JCR (JSRP) wordt opgeslagen.
* [SocialUtils Refactoring](socialutils.md) - hulpprogrammamethoden voor SRP die SocialUtils vervangen.
* [Naamgevingsconventies](naming-conventions.md) - naamconventies voor aangepaste Java-klassen.

### Scripts {#scripts}

* [Sideloading Communities Components](sideloading.md) - hoe u dynamisch een component toevoegt nadat de pagina is geladen.
* [Essentiële elementen van de Rich Text Editor](rte.md) - hoe te om rijke tekst UI aan leden voor het posten van inhoud aan te passen.

### IDE {#ide}

* [Maven gebruiken voor Gemeenschappen](maven.md) - hoe moet de communautaire API-jar worden opgenomen?
* [SocialUtils Refactoring](socialutils.md) - hulpprogrammamethoden voor SRP die SocialUtils vervangen.
