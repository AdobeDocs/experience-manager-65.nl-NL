---
title: Tags toewijzen
seo-title: Tags toewijzen
description: Tags toewijzen van bronnen voor activering maakt het mogelijk bronnen te filteren en paden te leren terwijl leden door catalogi bladeren
seo-description: Tags toewijzen van bronnen voor activering maakt het mogelijk bronnen te filteren en paden te leren terwijl leden door catalogi bladeren
uuid: daf8a4f4-486b-498c-99e9-d1533a830e64
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: c012d639-c6e6-4f73-bbd8-78a4baa38c17
translation-type: tm+mt
source-git-commit: 2fcd87cd1def7fc265ba40c83b50db86618f3b70
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---


# Tags toewijzen {#tagging-enablement-resources}

## Overzicht {#overview}

Door tags toe te wijzen aan bronnen voor activering kunt u bronnen filteren en paden leren terwijl leden door [catalogi](functions.md#catalog-function)bladeren.

Hoofdzakelijk:

* [Een tagnaamruimte](../../help/sites-administering/tags.md#creating-a-namespace) maken voor elke catalogus

   * [Tagmachtigingen instellen](../../help/sites-administering/tags.md#setting-tag-permissions)
   * Alleen voor leden van de gemeenschap (gesloten community)

      * Leestoegang toestaan voor de lidgroep van de [gemeenschapssite](users.md#publish-group-roles)
   * Voor elke bezoeker van de site, aangemeld of anoniem (open community)

      * Leestoegang voor de `Everyone` groep toestaan
   * [De labels publiceren](../../help/sites-administering/tags.md#publishing-tags)



* [Bepaal het werkingsgebied van markeringen voor een communautaire plaats](sites-console.md#tagging)

   * [Catalogi configureren die in de structuur van de site bestaan](functions.md#catalog-function)

      * Kan tags toevoegen aan de catalogusinstantie om de lijst met tags in de UI-filters te beheren.
      * Kan [voorfilters](catalog-developer-essentials.md#pre-filters)toevoegen om de opgenomen bronnen van een catalogus te beperken.

* [De communitysite publiceren](sites-console.md#publishing-the-site)
* [Tags toepassen op bronnen](resources.md#create-a-resource) voor activering zodat deze categoriaal kunnen worden gefilterd
* [De bronnen voor activering publiceren](resources.md#publish)

## Codes voor communautaire sites {#community-site-tags}

Wanneer u een communitysite maakt of bewerkt, stelt u met de instelling [](sites-console.md#tagging) Tags het bereik in van de tags die beschikbaar zijn voor de sitefuncties door een subset van bestaande tagnaamruimten te selecteren.

Hoewel tags te allen tijde kunnen worden gemaakt en toegevoegd aan de site van de community, wordt aangeraden vooraf een taxonomie te ontwerpen, vergelijkbaar met het ontwerpen van een database. Zie [Tags](../../help/sites-authoring/tags.md)gebruiken.

Wanneer u later tags toevoegt aan een bestaande communitysite, moet u de bewerking opslaan voordat u de nieuwe tag kunt toevoegen aan een catalogusfunctie in de sitestructuur.

Voor een communautaire plaats, nadat de plaats wordt gepubliceerd en de markeringen worden gepubliceerd, is het noodzakelijk om gelezen toegang tot leden van de gemeenschap toe te laten. Zie Tagmachtigingen [instellen](../../help/sites-administering/tags.md#setting-tag-permissions).

Hieronder ziet u hoe het wordt weergegeven in CRXDE wanneer een beheerder leesmachtigingen toepast op `/etc/tags/ski-catalog` de groep `Community Enable Members`.

![sitetags](assets/site-tags.png)

## Catalogustagnaamruimten {#catalog-tag-namespaces}

De catalogusfunctie gebruikt tags om zichzelf te definiëren. Wanneer het vormen van de catalogusfunctie in een communautaire plaats, wordt de reeks markering namespaces om te kiezen bepaald door het werkingsgebied van markeringsruimten die voor de communautaire plaats worden geplaatst.

De functie Catalog bevat een taginstelling die de tags definieert die worden vermeld in de filterinterface voor de catalogus. De instelling &quot;Alle naamruimten&quot; verwijst naar het bereik van tagnaamruimten die voor de communitysite zijn geselecteerd.

![catalog-naamruimte](assets/catalog-namespace.png)

## Tags toepassen op Enablement Resources {#applying-tags-to-enablement-resources}

Inschakelingsbronnen en leerpaden worden in alle catalogus weergegeven wanneer `Show in Catalog` deze worden gecontroleerd. Als u tags toevoegt aan bronnen en leerpaden, kunt u vooraf filteren in specifieke catalogi en filteren in de interface van de catalogus.

Het beperken van enablement middelen en het leren wegen aan specifieke catalogi wordt verwezenlijkt door [pre-filters](catalog-developer-essentials.md#pre-filters)te creëren.

Met de interface van de catalogus kunnen bezoekers een tagfilter toepassen op de lijst met bronnen en leerpaden die in die catalogus worden weergegeven.

De beheerder die de markeringen op enablement middelen toepast moet zich van de markeringsnamespaces verbonden aan de catalogi, evenals taxonomie bewust zijn om een sub-markering voor meer verfijnde categorisatie te selecteren.

Als er bijvoorbeeld een `ski-catalog` naamruimte wordt gemaakt en ingesteld in een catalogus met de naam `Ski Catalog`, heeft deze mogelijk twee onderliggende tags: `lesson-1` en `lesson-2`.

Aldus, om het even welke enablement middelen die met één van worden geëtiketteerd:

* ski-catalogus:les-1
* ski-catalogus:les-2

verschijnt in `Ski Catalog` nadat de enablement resource is gepubliceerd.

![basis-info](assets/applytags-basicinfo.png)

## Catalogus weergeven bij publiceren {#viewing-catalog-on-publish}

Zodra alles is opstelling van het auteursmilieu en gepubliceerd, kan de ervaring van het gebruiken van de catalogus om enablement middelen te vinden in het publicatiemilieu worden ervaren.

Als de vervolgkeuzelijst geen tagnaamruimten bevat, controleert u of de machtigingen correct zijn ingesteld in de publicatieomgeving.

Als er tagnaamruimten zijn toegevoegd en ontbreken, controleert u of de tags en de site opnieuw zijn gepubliceerd.

Als er na het selecteren van een tag tijdens het weergeven van de catalogus geen actiemiddelen worden weergegeven, controleert u of er een tag uit de naamruimte(n) van de catalogus is toegepast op de resource enablement.

![view-catalog](assets/viewcatalog.png)

