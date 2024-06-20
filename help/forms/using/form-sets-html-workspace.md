---
title: Werken met indelingen in de AEM Forms-werkruimte
description: Een formulierset is een verzameling van HTML5-formulieren die zijn gegroepeerd en gepresenteerd als één set formulieren voor eindgebruikers. Leer hoe u in de AEM Forms-werkruimte met formsets kunt werken.
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 76a8f93f-eb8a-4e68-8626-efa6dc67668f
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms, Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Werken met indelingen in de AEM Forms-werkruimte{#working-with-formsets-in-aem-forms-workspace}

Een formulierset is een verzameling van HTML5-formulieren die zijn gegroepeerd en gepresenteerd als één set formulieren voor eindgebruikers. Wanneer eindgebruikers een formulierset beginnen te vullen, worden ze naadloos van het ene formulier naar het andere overgezet. De reeks formulieren kan vervolgens met één klik worden verzonden. Ga voor meer informatie over formsets en hoe u deze instelt naar [Opmaak in AEM Forms](../../forms/using/formset-in-aem-forms.md).

De AEM Forms-werkruimte ondersteunt formsets. Met formsets kunnen meerdere formulieren die betrekking hebben op een service of proces worden gegroepeerd om een bedrijfsproces te automatiseren en aan de eindgebruikers worden gepresenteerd. In dat geval kunnen de gebruikers de gehele set als één geheel invullen en hoeven afzonderlijke formulieren of processen niet te worden opgeslagen, verzonden en bijgehouden.

## Een formulierset koppelen aan het beginpunt in een AEM Forms-werkruimte-app {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Maak de workflow voor het bedrijfsproces in Workbench. Zie voor meer informatie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Van de proceseigenschappen van het startpunt, selecteer **Een CRX-element gebruiken** in presentatie en gegevens.

   ![1-3](assets/1-3.png)

1. Klikken ![doorbladeren](assets/browse.png) (Bladeren) naast het CRX-middelenpad. Het dialoogvenster Formulierelement selecteren wordt geopend.

   ![2-1](assets/2-1.png)

1. Klik op de knop **Inzet** selecteert u de desbetreffende indeling in de lijst en klikt u vervolgens op **OK**.

1. Implementeer de toepassing nadat u andere relevante proceseigenschappen hebt bijgewerkt.

## Indeling gebruiken in de AEM Forms-werkruimte {#using-formset-in-nbsp-aem-forms-workspace}

Zodra een formset aan een startpunt is gekoppeld, kan het startpunt worden aangeroepen, net als elk ander startpunt dat wordt aangeroepen, vanuit de AEM Forms-werkruimte.

De volgende bewerkingen worden ondersteund in de indeling in de AEM Forms-werkruimte:

* Opslaan als concept
* Vergrendelen
* Abandon
* Verzenden
* Bijlagen toevoegen
* Notities toevoegen
* Tussen formulieren in een formulierset navigeren met de knoppen Vorige of Volgende

![3-1](assets/3-1.png)

>[!NOTE]
>
>Voor prestatieverbetering tijdens de verplaatsing van vorige en volgende formulieren in een formset, worden alle werkruimteknoppen (Vorige, Volgende, Opslaan, Verzenden en ... (Meer)) uitgeschakeld totdat het desbetreffende formulier volledig wordt weergegeven.
