---
title: Editor
description: Leer hoe u terug kunt schakelen naar de klassieke UI-editor.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: 8540e1f0-22d7-4f48-85d9-7c44eb7185df
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Editor{#editor}

Door gebrek, is de capaciteit om op klassieke UI van de redacteur over te schakelen onbruikbaar gemaakt.

De optie opnieuw inschakelen **Openen in klassieke gebruikersinterface** in de **Pagina-informatie** volgen deze stappen.

1. Gebruik CRXDE Lite om het volgende knooppunt te zoeken:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Bijvoorbeeld

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Een overlay maken met de opdracht **Overlayknooppunt** optie; bijvoorbeeld:

   * **Pad**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Overlay-locatie**: `/apps/`
   * **Identieke knooppunttypen**: actief (schakel het selectievakje in)

1. Voeg de volgende teksteigenschap met meerdere waarden toe aan het bovenliggende knooppunt:

   `sling:hideProperties = ["granite:hidden"]`

1. De **Openen in klassieke gebruikersinterface** deze optie is weer beschikbaar in het dialoogvenster **Pagina-informatie** wanneer u pagina&#39;s bewerkt.

   ![openen in klassieke interface, optie vanuit paginagegevens](assets/syui-03-2019-02-27-15-19-48.png)
