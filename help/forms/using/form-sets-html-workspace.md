---
title: Werken met indelingen in de werkruimte van AEM-formulieren
seo-title: Werken met indelingen in de werkruimte van AEM-formulieren
description: Een formulierset is een verzameling HTML5-formulieren die zijn gegroepeerd en worden weergegeven als één set formulieren voor eindgebruikers. Leer hoe u met formsets kunt werken in de werkruimte van AEM-formulieren.
seo-description: Een formulierset is een verzameling HTML5-formulieren die zijn gegroepeerd en worden weergegeven als één set formulieren voor eindgebruikers. Leer hoe u met formsets kunt werken in de werkruimte van AEM-formulieren.
uuid: 1a5f3ce8-1d6a-497e-90d0-49765e40cf3b
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: f550b747-2def-4317-9ef7-dc6c1e7bb404
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Werken met indelingen in de werkruimte van AEM-formulieren{#working-with-formsets-in-aem-forms-workspace}

Een formulierset is een verzameling HTML5-formulieren die zijn gegroepeerd en worden weergegeven als één set formulieren voor eindgebruikers. Wanneer eindgebruikers een formulierset beginnen te vullen, worden ze naadloos van het ene formulier naar het andere overgezet. De reeks formulieren kan vervolgens met één klik worden verzonden. Zie [Formset in AEM Forms](../../forms/using/formset-in-aem-forms.md)voor meer informatie over formsets en hoe u deze instelt.

De werkruimte van de Vormen van AEM steunt formsets. Met formsets kunnen meerdere formulieren die betrekking hebben op een service of proces worden gegroepeerd om een bedrijfsproces te automatiseren en aan de eindgebruikers worden gepresenteerd. In dat geval kunnen de gebruikers de gehele set als één geheel invullen en hoeven afzonderlijke formulieren of processen niet te worden opgeslagen, verzonden en bijgehouden.

## Een formulierset koppelen aan het beginpunt in een AEM Forms-werkruimte-app {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Maak de workflow voor het bedrijfsproces in Workbench. Zie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63)voor meer informatie.
1. Van de proceseigenschappen van het startpunt, uitgezocht **Gebruik een Middel** van CRX in Presentatie &amp; Gegevens.

   ![1-3](assets/1-3.png)

1. Klik op ![Bladeren](assets/browse.png) (Bladeren) naast het middelenpad van de CRX. Het dialoogvenster Formulierelement selecteren wordt geopend.

   ![2-1](assets/2-1.png)

1. Klik op het tabblad **Indeling** , selecteer de gewenste indeling in de lijst en klik op **OK**.

1. Implementeer de toepassing nadat u andere relevante proceseigenschappen hebt bijgewerkt.

## Indeling gebruiken in de werkruimte van AEM-formulieren {#using-formset-in-nbsp-aem-forms-workspace}

Zodra een formset aan een startpunt is gekoppeld, kan het startpunt worden aangeroepen, net zoals elk ander startpunt wordt aangeroepen, vanuit de werkruimte van AEM-formulieren.

De volgende bewerkingen worden ondersteund in de indeling via de werkruimte van AEM-formulieren:

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
>Voor prestatieverbetering tijdens het verplaatsen van vorige en volgende formulieren in een indeling, worden alle werkruimteknoppen (Vorige, Volgende, Opslaan, Verzenden en ... (Meer)) worden uitgeschakeld totdat het desbetreffende formulier volledig wordt weergegeven.

