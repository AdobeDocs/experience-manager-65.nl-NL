---
title: Gereedschap AEM
description: Het gereedschap AEM repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM repo is vergelijkbaar met het gereedschap Jackrabbit FileVault, maar is sneller, heeft minimale afhankelijkheden en is een eenvoudig bash-script.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: c46c9f0c-b0d2-4f2f-b95c-90fd3ced32a9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Gereedschap AEM{#aem-repo-tool}

Het gereedschap AEM repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM herhalen is vergelijkbaar met het gereedschap [Jackrabbit FileVault, gereedschap](/help/sites-developing/ht-vlttool.md), maar is sneller, heeft minimale gebiedsdelen, en is een eenvoudig bash manuscript.

Dit hulpmiddel vereenvoudigt de overdracht van dossiers voor de ontwikkelaar en kan ook in IntelliJ en Eclipse worden geïntegreerd om ontwikkeling nog efficiënter te maken.

## Overzicht {#overview}

Voor een bepaald pad binnen een `jcr_root` AEM Repo Tool maakt een pakket met één filter voor de gehele substructuur en plaatst dat op de server (vergelijkbaar met FTP) `put`), haalt het op van de server ( `get`) of vergelijkt de verschillen ( `status` en `diff`).

Het gereedschap ondersteunt geen meerdere filterpaden of FileVault-paden `filter.xml`.

>[!CAUTION]
>
>Met het gereedschap AEM repo overschrijft u altijd het gehele opgegeven bestand of de opgegeven map.

## Downloaden en documentatie {#download-and-documentation}

De [AEM Repo Tool is beschikbaar op GitHub via deze koppeling](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) samen met gedetailleerde installatie- en gebruiksinstructies.

Als u de bron van het Hulpmiddel van de AEM wilt downloaden, zie het hieronder verbonden project GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open hulpmiddelenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)
