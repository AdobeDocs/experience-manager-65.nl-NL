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
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---


# Editor{#editor}

Door gebrek, is de capaciteit om op klassieke UI van de redacteur over te schakelen onbruikbaar gemaakt.

Om de optie **open in Klassieke UI** in het **menu van de Informatie van de Pagina** opnieuw toe te laten, volg deze stappen.

1. Gebruik CRXDE Lite om het volgende knooppunt te zoeken:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Bijvoorbeeld

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Creeer een bedekking gebruikend de **optie van de Knoop van de Bedekking**; bijvoorbeeld:

   * **Weg**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Plaats van de Bedekking**: `/apps/`
   * **de Types van Knoop van de Gelijke**: actief (selecteer checkbox)

1. Voeg de volgende teksteigenschap met meerdere waarden toe aan het bovenliggende knooppunt:

   `sling:hideProperties = ["granite:hidden"]`

1. **Open in Klassieke UI** optie is opnieuw beschikbaar in het **menu van de Informatie van de Pagina** wanneer het uitgeven van pagina&#39;s.

   ![&#x200B; open in klassieke optie UI van paginainformatie &#x200B;](assets/syui-03-2019-02-27-15-19-48.png)
