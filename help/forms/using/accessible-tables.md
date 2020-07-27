---
title: Toegankelijke complexe tabellen maken in HTML5-formulieren
seo-title: Toegankelijke complexe tabellen maken in HTML5-formulieren
description: Leer hoe u toegankelijke tabellen maakt in HTML5-formulieren.
seo-description: Leer hoe u toegankelijke tabellen maakt in HTML5-formulieren.
uuid: e52562d2-4dc3-4359-9dbb-c18614921808
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# Toegankelijke complexe tabellen maken in HTML5-formulieren {#create-accessible-complex-tables-in-html-forms}

Bij de standaardimplementatie van tabellen in HTML5 Forms worden HTML DIV-elementen gebruikt om een tabel te renderen. Bij het renderen worden ARIA-rollen gebruikt om aan de toegankelijkheidsvereisten te voldoen.

HTML5 Forms biedt een alternatieve uitvoering voor de tabellen om toegankelijkheidsproblemen met schermlezers te voorkomen die de ARIA-rollen die worden gebruikt met gegevenstabellen niet volledig ondersteunen. Deze tabellen zijn gebaseerd op de nieuwe tabelindeling die in Designer is geïntroduceerd en die ook ondersteuning biedt voor:

* Rijkoppen
* Rijbereik

Als u de nieuwe indeling wilt gebruiken in HTML5 Forms, markeert u de tabel als complex. Als u de tabel als complex wilt markeren, voegt u als volgt `extras` code toe aan de XML-bron van het tabelsubformulier:

```xml
</extras>
 <text name="complexTable">1</text>
 </extras>
```

De tabellen die zijn gemarkeerd als *complexTable* volgen de native HTML-uitvoering en bieden betere toegankelijkheidsondersteuning voor bepaalde schermlezers.  Als u een rijbereik wilt maken, selecteert u opeenvolgende cellen van een tabel in dezelfde kolom, klikt u met de rechtermuisknop op de selectie en klikt u op **[!UICONTROL Merge Cells]**.

>[!NOTE]
>
>Het maken van een rijbereik werkt alleen voor uiterst linkse cellen.

Als u een rij als rijkop wilt markeren, selecteert u alle cellen in de rij, klikt u met de rechtermuisknop op de selectie en klikt u op **[!UICONTROL Mark Header]**.

Als u een cel als kolomkop wilt markeren, selecteert u een willekeurige cel in de kolom, klikt u met de rechtermuisknop op de selectie en klikt u op **[!UICONTROL Mark Header]**.

Beperkingen in de nieuwe *indeling AccessibleTable* :

* Gebrek aan steun voor kweekbare gebieden als het rowspan in de lijst wordt gebruikt
* Geen ondersteuning voor geneste tabellen (tabellen in tabelcellen)
* Ondersteuning voor rowspan is beperkt tot de koptekstrijen en kopcellen
* De ondersteuning is beperkt tot reguliere tabellen
* Geen ondersteuning voor gegevensvooraf ingevulde tabellen met rowspan > 1

