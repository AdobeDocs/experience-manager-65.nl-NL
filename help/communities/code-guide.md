---
title: Codeerrichtlijnen
description: Richtlijnen, tips en trucs voor ontwikkelaars van gemeenschappen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a23aab83-1dfa-4d91-9b6b-6246a2103896
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# Codeerrichtlijnen {#coding-guidelines}

## Richtlijnen, tips en trucs {#guidelines-tips-and-tricks}

Het werken met AEM Communities is geëvolueerd van sterk afhankelijk zijn van de Pagina&#39;s van de Server van Java aan flexibiliteit in het kiezen van het opmaken van scripttalen waar bedrijfslogica, stijl, en paginacontent van elkaar verschillend zijn.

De verdere flexibiliteit in het werken met gebruiker geproduceerde inhoud (UGC) is door SocialResourceProvider API, die de behoefte aan bewustzijn elimineert waarvan [ SRP ](srp.md) optie voor de plaatsing werd gekozen.

Hieronder vindt u verschillende codeerrichtlijnen en aanbevolen procedures voor AEM Communities-ontwikkelaars:

### Code {#code}

* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - hoe te vermijden schrijvend een toepassing die slechts werkt wanneer UGC in JCR (JSRP) wordt opgeslagen.
* [ SocialUtils Refactoring ](socialutils.md) - nutsmethodes voor SRP die SocialeUtils vervangen.
* [ het Noemen van Conventies ](naming-conventions.md) - noemend overeenkomsten voor de klassen van douaneJava.

### Scripts {#scripts}

* [ Getrouwde Componenten van Gemeenschappen ](sideloading.md) - hoe te om een component dynamisch toe te voegen nadat de pagina laadt.
* {de Hoofdzaak van de Redacteur van de Tekst van 0} Rich [&#128279;](rte.md) - hoe te om de rijke tekst UI aan leden voor het posten van inhoud aan te passen.

### IDE {#ide}

* [ Gebruikend Gemaakt voor Gemeenschappen ](maven.md) - hoe te om de Communautaire API jar te omvatten.
* [ SocialUtils Refactoring ](socialutils.md) - nutsmethodes voor SRP die SocialeUtils vervangen.
