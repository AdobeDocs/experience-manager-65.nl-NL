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
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Werken met indelingen in de AEM Forms-werkruimte{#working-with-formsets-in-aem-forms-workspace}

Een formulierset is een verzameling van HTML5-formulieren die zijn gegroepeerd en gepresenteerd als één set formulieren voor eindgebruikers. Wanneer eindgebruikers een formulierset beginnen te vullen, worden ze naadloos van het ene formulier naar het andere overgezet. De reeks formulieren kan vervolgens met één klik worden verzonden. Voor meer info over formsets en hoe te om hen te plaatsen, zie [&#x200B; Formset in AEM Forms &#x200B;](../../forms/using/formset-in-aem-forms.md).

De AEM Forms-werkruimte ondersteunt formsets. Met formsets kunnen meerdere formulieren die betrekking hebben op een service of proces worden gegroepeerd om een bedrijfsproces te automatiseren en aan de eindgebruikers worden gepresenteerd. In dat geval kunnen de gebruikers de gehele set als één geheel invullen en hoeven afzonderlijke formulieren of processen niet te worden opgeslagen, verzonden en bijgehouden.

## Een formulierset koppelen aan het beginpunt in een AEM Forms-werkruimte-app {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. Maak de workflow voor het bedrijfsproces in Workbench. Voor meer informatie, zie [&#x200B; hulp Workbench &#x200B;](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. Van de proceseigenschappen van het startpunt, uitgezochte **Gebruik een Activa van CRX** in Presentatie &amp; Gegevens.

   ![&#x200B; 1-3 &#x200B;](assets/1-3.png)

1. Klik ![&#x200B; doorbladeren &#x200B;](assets/browse.png) (doorbladeren) naast de de activaweg van CRX. Het dialoogvenster Formulierelement selecteren wordt geopend.

   ![&#x200B; 2-1 &#x200B;](assets/2-1.png)

1. Klik het **Formatteren** lusje, selecteer de relevante formset van de lijst, en klik dan O.K. **&#x200B;**.

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

![&#x200B; 3-1 &#x200B;](assets/3-1.png)

>[!NOTE]
>
>Voor prestatieverbetering tijdens de verplaatsing van vorige en volgende formulieren in een formset, worden alle werkruimteknoppen (Vorige, Volgende, Opslaan, Verzenden en ... (Meer)) uitgeschakeld totdat het desbetreffende formulier volledig wordt weergegeven.
