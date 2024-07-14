---
title: Activiteitendensen
description: Een component Community Activity List aan een pagina toevoegen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2a4297e4-2d88-4fa6-8fea-3fea06753605
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Activiteitendensen {#activity-trends}

## Inleiding {#introduction}

Met de component `Community Activity List` kunt u trending-informatie over posts en weergaven door leden en posts en weergaven van inhoud toevoegen.

In het document wordt beschreven:

* Toevoegend de `Community Activity List` component aan a [ communautaire plaats ](/help/communities/overview.md#community-sites).

* Configuration settings for the `Community Activity List` component.

### Vereiste {#requirement}

Gegevens voor de `Community Activity List` zijn alleen beschikbaar wanneer Adobe Analytics een licentie heeft en is geconfigureerd voor de communitysite.

Zie [ Configuratie Analytics voor de Eigenschappen van Gemeenschappen ](/help/communities/analytics.md).

### Een communautaire activiteitenlijst toevoegen aan een pagina {#adding-a-community-activity-list-to-a-page}

Als u een `Community Activity List` -component in de ontwerpmodus aan een pagina wilt toevoegen, zoekt u de component `Communities / Community Activity List` en sleept u deze naar de juiste plaats op een pagina.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen ](/help/communities/basics.md).[

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![ gemeenschap-activiteit ](assets/community-activity.png)

### Lijst met communautaire activiteiten configureren  {#configuring-community-activity-list}

Selecteer de geplaatste component `Community Activity List` en selecteer vervolgens het pictogram `Configure` zodat u het dialoogvenster Bewerken kunt openen.

![ vormen ](assets/configure-new.png)

Onder het **lusje van Commentaren**, specificeer als en hoe de commentaren voor geupload dossiers verschijnen:

![ eigenschappen ](assets/activity-list-properties.png)

* **Type**

  Geef op of gegevens met betrekking tot leden van de gebruikersgemeenschap of door de gebruiker gegenereerde inhoud (UGC) moeten worden weergegeven.

  Selecteren uit:

   * `Members`
   * `Content`

  De standaardwaarde is `Members` .

* **titel van de Vertoning**

  Een beschrijvende titel die boven de gegevens wordt weergegeven, zoals `Trending Content` .
Standaard is geen titel.

* **Aantal van de Vertoning**

  Het aantal aan te bieden items.
De standaardwaarde is 10.

* **Type van Activiteit**

  Selecteer een van de volgende opties:

   * `Views` (paginabezoeken)
   * `Posts` (UGC maken)
   * `Follows`
   * `Likes`

  De standaardwaarde is Weergaven.

* **periode van de Tijd**

  Selecteer een van de volgende opties:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1)`
   * `Total`

  De standaardwaarde is `Total` .

* **de weg van de Context**

  Hiermee kunt u de activiteit uitbreiden naar een subset van de site, zoals een specifieke blog.
Standaard is dit de hele community-site.

* **samenvoeging van de telling van het Lid**

  Wanneer deze optie is uitgeschakeld, worden alleen de bovenste posts geteld. Als de context bijvoorbeeld de hoofdpagina is (de standaardinstelling), geeft een `Activity Type` van `Posts` nooit enige activiteit weer omdat het niet mogelijk is inhoud naar de hoofdpagina te posten. Wanneer deze optie is ingeschakeld, worden de tellingen op alle afstammende pagina&#39;s opgenomen.
Standaard is ingeschakeld.

### Voorbeeldpagina met vier componenten {#example-page-with-components}

**Hoogste Bezoekers** config: Type = Leden, Type van Activiteit = Bekijken

**Hoogste Medewerkers** config: Type = Leden, Type van Activiteit = Post

**Hoogste Inhoud** config: Type = Inhoud, Type van Activiteit = Bekijken,

**Trending Content** config: Type = Inhoud, Type van Activiteit = Post

![ componenten ](assets/activity-list-components.png)
