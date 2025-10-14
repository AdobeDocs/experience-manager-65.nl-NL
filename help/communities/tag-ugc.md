---
title: Door gebruiker gegenereerde inhoud labelen
description: Door tags toe te wijzen aan door gebruikers gegenereerde inhoud (UGC) kunnen leden van de gebruikersgemeenschap andere leden helpen bij het zoeken naar inhoud
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 1ecb41e5-c959-4380-a5c7-df9fc3a7703a
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Door gebruiker gegenereerde inhoud labelen {#tagging-user-generated-content}

## Overzicht {#overview}

Door een tag op te geven aan door gebruikers gegenereerde inhoud (UGC) kunnen leden van de gebruikersgemeenschap andere leden helpen bij het zoeken naar inhoud.

Codes worden doorgaans toegepast door auteurs en beheerders in de auteursomgeving. Het coderen van UGC is uniek in die zin dat de markeringen UGC door communautaire leden in het publicatiemilieu worden toegepast.

De tagnaamruimten en taxonomieën zijn voor beide toepassingen hetzelfde.

## Functies van Gemeenschappen {#communities-features}

De AEM Communities-functies die kunnen worden geconfigureerd om tags toe te staan, zijn:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Bestandsbibliotheek](file-library.md)
* [Forum](forum.md#configuretheaddedforum)
* [Vragen en antwoorden](working-with-qna.md)

## Tags beheren {#administering-tags}

Zie [&#x200B; het Beheer Markeringen &#x200B;](../../help/sites-administering/tags.md#tagging-console) voor het creëren van en het beheren van markeringsnamespaces en taxonomieën.

Zie [&#x200B; Hoofdzaak van de Markering &#x200B;](tag.md) voor ontwikkelaarinformatie.

Zie [&#x200B; Gebruikend de Wolk van de Sociale Markering &#x200B;](tagcloud.md) voor het toevoegen van een component van de Wolk van de Sociale Markering aan een pagina om het zoeken naar geposte UGC te vergemakkelijken gebruikend de toegepaste markeringen.

### Tagmachtigingen {#tag-permissions}

De standaardmachtigingen zijn ingesteld om te voorkomen dat tagnaamruimten worden gelezen door iedereen in de publicatieomgeving.

Omdat tags worden toegepast op UGC in de publicatieomgeving, moet leesmachtigingen zijn ingeschakeld voor leden van de community om tags te kunnen selecteren die moeten worden toegepast.

Zie [&#x200B; Plaatsende Toestemmingen van de Markering &#x200B;](../../help/sites-administering/tags.md#setting-tag-permissions).

Hieronder wordt beschreven hoe de optie wordt weergegeven in CRXDE wanneer een beheerder leesmachtigingen toepast op `/etc/tag/discussions` voor de groep `Community Engage Members` .

![&#x200B; markering-toestemmingen &#x200B;](assets/tag-permissions.png)
