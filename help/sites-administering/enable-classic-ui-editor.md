---
title: Editor
seo-title: Editor
description: Leer hoe u terug kunt schakelen naar de klassieke UI-editor.
seo-description: Leer hoe u terug kunt schakelen naar de klassieke UI-editor.
uuid: ca8b07e7-014f-428e-82bd-87f3aae12f6e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 54903f3a-1e7e-4083-a2c9-b2ea4555d7fc
docset: aem65
translation-type: tm+mt
source-git-commit: 954c1d5b06b54d59f523483ce5c1af36c2083a76

---


# Editor{#editor}

Door gebrek, is de capaciteit om op klassieke UI van de redacteur over te schakelen onbruikbaar gemaakt.

Voer de volgende stappen uit om de optie **Openen in klassieke gebruikersinterface** in het menu **Pagina-informatie** weer in te schakelen.

1. Zoek het volgende knooppunt met behulp van CRXDE Lite:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Bijvoorbeeld

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Maak een bedekking met de optie **Overlay knooppunt** . bijvoorbeeld:

   * **Pad**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Locatie** bedekking: `/apps/`
   * **Identieke knooppunttypen**: actief (schakel het selectievakje in)

1. Voeg de volgende teksteigenschap met meerdere waarden toe aan het bovenliggende knooppunt:

   `sling:hideProperties = ["granite:hidden"]`

1. De optie **Openen in klassieke gebruikersinterface** is weer beschikbaar in het menu **Pagina-informatie** wanneer u pagina&#39;s bewerkt.

   ![](assets/syui-03-2019-02-27-15-19-48.png)