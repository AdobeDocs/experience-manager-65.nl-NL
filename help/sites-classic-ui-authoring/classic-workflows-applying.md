---
title: Workflows toepassen op pagina's
description: Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit de Sidekick.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: d8b604c5-a6da-47c4-9422-b519e224c7ca
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 8%

---

# Workflows toepassen op pagina&#39;s{#applying-workflows-to-pages}

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.

  U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Optioneel:

   * Een opmerking die informatie bevat over de reden waarom u de workflow hebt gestart.
   * Een titel die helpt de werkstroominstantie in Inbox van een gebruiker identificeren.

>[!NOTE]
>
>AEM de beheerders kunnen werkschema&#39;s beginnen gebruikend [&#x200B; verscheidene andere methodes &#x200B;](/help/sites-administering/workflows-starting.md).

## Workflows toepassen {#applying-workflows}

Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit de Sidekick.

De **kolom van de Status** in de **&#x200B;**&#x200B;console van Websites wijst erop of een werkschema op een pagina is toegepast:

![&#x200B; workflowstatus &#x200B;](assets/workflowstatus.png)

### Een workflow starten vanuit de websiteconsole {#starting-a-workflow-from-the-websites-console}

1. Open de websiteconsole. ([&#x200B; http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. Selecteer in de boomstructuur Websites het bovenliggende element van de pagina waarop u de workflow wilt toepassen.
1. Selecteer de pagina in de paginalijst en klik op Workflow.
1. Selecteer in het dialoogvenster Workflow starten de workflow die u wilt toepassen. Voer eventueel een opmerking en een titel in. Klik vervolgens op Start.

### Een workflow starten met Sidekick {#starting-a-workflow-using-sidekick}

1. Open de websiteconsole.
1. Open de gewenste pagina.
1. Selecteer het tabblad Werkstroom in de Sidekick.
1. Breid de **dialoog van het Werkschema** uit, toestaand u om het **Werkschema** te selecteren en naar keuze **Titel van het Werkschema** en **Commentaar** in te gaan.

   ![&#x200B; workflowstartsidekick &#x200B;](assets/workflowstartsidekick.png)

1. Klik **Werkschema van het Begin** om een nieuwe werkschemainstantie met de eigenschappen te beginnen u en de huidige pagina als nuttige lading vormde. De workflow wordt nu uitgevoerd.
