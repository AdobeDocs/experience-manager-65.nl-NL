---
title: Toegankelijke complexe tabellen maken in HTML5-formulieren
description: Leer hoe u toegankelijke tabellen maakt in HTML5-formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: HTML5 Forms
exl-id: 3b8e3323-9ac4-4f5c-8c52-e2186e9169ea
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Toegankelijke complexe tabellen maken in HTML5-formulieren {#create-accessible-complex-tables-in-html-forms}

De standaardimplementatie van lijsten in HTML5 Forms gebruikt HTML div elementen om een lijst terug te geven. Bij het renderen worden ARIA-rollen gebruikt om aan de toegankelijkheidsvereisten te voldoen.

Om toegankelijkheidsproblemen met schermlezers te voorkomen die de ARIA-rollen die worden gebruikt met gegevenstabellen niet volledig ondersteunen, biedt HTML5 Forms een alternatieve uitvoering voor de tabellen. Deze tabellen zijn gebaseerd op de nieuwe tabelindeling die in Designer is geïntroduceerd en die ook ondersteuning biedt voor:

* Rijkoppen
* Rijbereik

Als u de nieuwe indeling wilt gebruiken in HTML5 Forms, markeert u de tabel als complex. Als u de tabel als complex wilt markeren, voegt u `extras` label in het XML-bron van het tabelsubformulier als volgt:

```xml
</extras>
 <text name="complexTable">1</text>
 </extras>
```

De tabellen die als *complexTable* volgt de native HTML-uitvoering en biedt betere toegankelijkheidsondersteuning voor bepaalde schermlezers.  Als u een rijbereik wilt maken, selecteert u opeenvolgende cellen van een tabel in dezelfde kolom, klikt u met de rechtermuisknop op de selectie en klikt u vervolgens op **[!UICONTROL Merge Cells]**.

>[!NOTE]
>
>Het maken van een rijbereik werkt alleen voor uiterst linkse cellen.

Als u een rij als rijkop wilt markeren, selecteert u alle cellen in de rij, klikt u met de rechtermuisknop op de selectie en klikt u vervolgens op **[!UICONTROL Mark Header]**.

Als u een cel als kolomkop wilt markeren, selecteert u een willekeurige cel in de kolom, klikt u met de rechtermuisknop op de selectie en klikt u vervolgens op **[!UICONTROL Mark Header]**.

Beperkingen in nieuw *AccessibleTable* indeling:

* Gebrek aan steun voor kweekbare gebieden als het rowspan in de lijst wordt gebruikt
* Geen ondersteuning voor geneste tabellen (tabellen in tabelcellen)
* De ondersteuning voor de rowspan is beperkt tot de koptekstrijen en kopcellen
* De ondersteuning is beperkt tot reguliere tabellen
* Geen ondersteuning voor gegevensvooraf ingevulde tabellen met rowspan > 1
