---
title: Activiteitendensen
description: Een component Community Activity List aan een pagina toevoegen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2a4297e4-2d88-4fa6-8fea-3fea06753605
source-git-commit: 518207a0d8a95ef17b0972855a58f124fb215c85
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Activiteitendensen {#activity-trends}

## Inleiding {#introduction}

De `Community Activity List` kunt u trending information about posts en views door leden en posten en weergaven van content toevoegen.

In het document wordt beschreven:

* De `Community Activity List` component aan een [community-site](/help/communities/overview.md#community-sites).

* De montages van de configuratie voor de `Community Activity List` component.

### Vereiste {#requirement}

Gegevens voor de `Community Activity List` is alleen beschikbaar als Adobe Analytics een licentie heeft en geconfigureerd voor de community-site.

Zie [Analytische configuratie voor functies van Gemeenschappen](/help/communities/analytics.md).

### Een communautaire activiteitenlijst toevoegen aan een pagina {#adding-a-community-activity-list-to-a-page}

Als u een `Community Activity List` naar een pagina in de modus Schrijver, zoek de component `Communities / Community Activity List` en sleep het naar de juiste plaats op een pagina.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de component voor het eerst op een pagina van een communitysite wordt geplaatst, ziet deze er zo uit:

![gemeenschapsactiviteit](assets/community-activity.png)

### Lijst met communautaire activiteiten configureren  {#configuring-community-activity-list}

Selecteer de geplaatste `Community Activity List` en selecteert u vervolgens de `Configure` zodat u het dialoogvenster Bewerken kunt openen.

![vormen](assets/configure-new.png)

Onder de **Opmerkingen** , geeft u op of en hoe opmerkingen voor geüploade bestanden worden weergegeven:

![eigenschappen](assets/activity-list-properties.png)

* **Type**

  Geef op of gegevens met betrekking tot leden van de gebruikersgemeenschap of door de gebruiker gegenereerde inhoud (UGC) moeten worden weergegeven.

  Selecteren uit:

   * `Members`
   * `Content`

  Standaard is `Members`.

* **Weergavetitel**

  Een beschrijvende titel die boven de gegevens wordt weergegeven, zoals `Trending Content`.
Standaard is geen titel.

* **Aantal weergeven**

  Het aantal aan te bieden items.
De standaardwaarde is 10.

* **Type activiteit**

  Selecteer een van de volgende opties:

   * `Views`(paginabezoeken)
   * `Posts`(maken van UGC)
   * `Follows`
   * `Likes`

  De standaardwaarde is Weergaven.

* **Tijdsperiode**

  Selecteer een van de volgende opties:

   * `Last 24 hours`
   * `Last 7 days`
   * `Last 30 days`
   * `Last 90 days`
   * `This year (since Jan 1)`
   * `Total`

  Standaard is `Total`.

* **Contextpad**

  Hiermee kunt u de activiteit uitbreiden naar een subset van de site, zoals een specifieke blog.
Standaard is dit de hele community-site.

* **Samenvoeging aantal leden**

  Wanneer deze optie is uitgeschakeld, worden alleen de bovenste posts geteld. Als de context bijvoorbeeld de hoofdpagina is (de standaardinstelling), `Activity Type` van `Posts` geeft nooit enige activiteit weer omdat er geen inhoud naar de hoofdpagina kan worden gepost. Wanneer deze optie is ingeschakeld, worden de tellingen op alle afstammende pagina&#39;s opgenomen.
Standaard is ingeschakeld.

### Voorbeeldpagina met vier componenten {#example-page-with-components}

**Topbezoekers** config: Type = Leden, Type Activiteit = Weergaven

**Belangrijkste bijdragers** config: Type = Leden, Type Activiteit = Posten

**Bovenste inhoud** config: Type = Inhoud, Type activiteit = Weergaven,

**Trend Content** config: Type = Inhoud, Type activiteit = Post

![componenten](assets/activity-list-components.png)
