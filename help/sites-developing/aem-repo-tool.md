---
title: AEM-repo
seo-title: AEM-repo
description: Het gereedschap AEM-repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM-server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM-repo is vergelijkbaar met het gereedschap Jackrabbit FileVault, maar is sneller, heeft minimale afhankelijkheden en is een eenvoudig basisscript.
seo-description: Het gereedschap AEM-repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM-server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM-repo is vergelijkbaar met het gereedschap Jackrabbit FileVault, maar is sneller, heeft minimale afhankelijkheden en is een eenvoudig basisscript.
uuid: 6c4a3504-e8e8-46c0-83cb-c18d9791f93e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 7de7b2f9-770e-4af3-8a31-c7b4de64fd43
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM-repo{#aem-repo-tool}

Het gereedschap AEM-repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM-server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM-repo is vergelijkbaar met het gereedschap [](/help/sites-developing/ht-vlttool.md)Jackrabbit FileVault, maar is sneller, heeft minimale afhankelijkheden en is een eenvoudig basisscript.

Dit hulpmiddel vereenvoudigt de overdracht van dossiers voor de ontwikkelaar en kan ook in IntelliJ en Eclipse worden geïntegreerd om ontwikkeling nog efficiënter te maken.

## Overzicht {#overview}

Voor een bepaald pad binnen een `jcr_root` bestandsstructuur op het bestandssysteem maakt AEM Repo Tool een pakket met één filter voor de gehele substructuur en plaatst deze op de server (vergelijkbaar met FTP `put`), haalt deze op van de server ( `get`) of vergelijkt de verschillen ( `status` en `diff`).

Het gereedschap biedt geen ondersteuning voor meerdere filterpaden of FileVault-paden `filter.xml`.

>[!CAUTION]
>
>Houd er rekening mee dat het gereedschap AEM-repo altijd het volledige opgegeven bestand of de opgegeven map overschrijft.

## Downloaden en documentatie {#download-and-documentation}

Het gereedschap [AEM-repo is beschikbaar op GitHub via deze koppeling](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) , samen met gedetailleerde installatie- en gebruiksinstructies.

Als u wenst om de bron van het Hulpmiddel van de Repo te downloaden AEM, verwijs naar het hieronder verbonden project GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open hulpmiddelenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/tools)
* Het project downloaden als [ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)

