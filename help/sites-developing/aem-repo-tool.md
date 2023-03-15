---
title: AEM
seo-title: AEM Repo Tool
description: Het gereedschap AEM repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM repo is vergelijkbaar met het gereedschap Jackrabbit FileVault, maar is sneller, heeft minimale afhankelijkheden en is een eenvoudig bash-script.
seo-description: The AEM Repo Tool is a simple solution to transfer JCR content between your local filesystem and the AEM server via the command line comparable to FTP. The AEM Repo Tool is similar to the Jackrabbit FileVault tool, but is faster, has minimal dependencies, and is a simple bash script.
uuid: 6c4a3504-e8e8-46c0-83cb-c18d9791f93e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 7de7b2f9-770e-4af3-8a31-c7b4de64fd43
exl-id: c46c9f0c-b0d2-4f2f-b95c-90fd3ced32a9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# AEM{#aem-repo-tool}

Het gereedschap AEM repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM herhalen is vergelijkbaar met het gereedschap [Jackrabbit FileVault, gereedschap](/help/sites-developing/ht-vlttool.md), maar is sneller, heeft minimale gebiedsdelen, en is een eenvoudig bash manuscript.

Dit hulpmiddel vereenvoudigt de overdracht van dossiers voor de ontwikkelaar en kan ook in IntelliJ en Eclipse worden geïntegreerd om ontwikkeling nog efficiënter te maken.

## Overzicht {#overview}

Voor een bepaald pad binnen een `jcr_root` AEM Repo Tool maakt een pakket met één filter voor de gehele substructuur en plaatst dat op de server (vergelijkbaar met FTP) `put`), haalt het op van de server ( `get`) of vergelijkt de verschillen ( `status` en `diff`).

Het gereedschap biedt geen ondersteuning voor meerdere filterpaden of FileVault-paden `filter.xml`.

>[!CAUTION]
>
>Houd er rekening mee dat het gereedschap AEM repo altijd het volledige opgegeven bestand of de opgegeven map overschrijft.

## Downloaden en documentatie {#download-and-documentation}

De [AEM Repo Tool is beschikbaar op GitHub via deze koppeling](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) samen met gedetailleerde installatie- en gebruiksinstructies.

Als u wenst om de bron van het AEM Hulpmiddel van de Repo te downloaden, verwijs naar het hieronder verbonden project GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open hulpmiddelenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)
