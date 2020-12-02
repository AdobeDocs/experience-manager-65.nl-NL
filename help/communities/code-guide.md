---
title: Codeerrichtlijnen
seo-title: Codeerrichtlijnen
description: Richtlijnen, tips en trucs voor ontwikkelaars van gemeenschappen
seo-description: Richtlijnen, tips en trucs voor ontwikkelaars van gemeenschappen
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 1%

---


# Codeerrichtlijnen {#coding-guidelines}

## Richtlijnen, tips en trucs {#guidelines-tips-and-tricks}

Het werken met AEM Communities is geëvolueerd van sterk afhankelijk zijn van de Pagina&#39;s van de Server van Java aan flexibiliteit in het kiezen van het opmaken van scripttalen waar bedrijfslogica, stijl, en paginacontent van elkaar verschillend zijn.

De verdere flexibiliteit bij het werken met door de gebruiker gegenereerde inhoud (UGC) is via de API van SocialResourceProvider, waardoor de noodzaak van bewustwording wordt weggenomen, waarvan [SRP](srp.md) is gekozen voor de implementatie.

Hieronder vindt u verschillende codeerrichtlijnen en aanbevolen procedures voor AEM Communities-ontwikkelaars:

### Code {#code}

* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md)  - hoe te vermijden schrijvend een toepassing die slechts werkt wanneer UGC in JCR (JSRP) wordt opgeslagen.
* [SocialUtils Refactoring](socialutils.md)  - nutsmethodes voor SRP die SocialUtils vervangen.
* [Naamgeving van conventies](naming-conventions.md)  - naamconventies voor aangepaste Java-klassen.

### Scripts {#scripts}

* [Sideloading Communities Components](sideloading.md) : hoe u dynamisch een component toevoegt nadat de pagina is geladen.
* [Essentiële elementen](rte.md)  van de Teksteditor - hoe u de RTF-gegevens voor leden kunt aanpassen voor het posten van inhoud.

### IDE {#ide}

* [Maven for Communities](maven.md)  gebruiken - hoe u de Community API-jar moet opnemen.
* [SocialUtils Refactoring](socialutils.md)  - nutsmethodes voor SRP die SocialUtils vervangen.

