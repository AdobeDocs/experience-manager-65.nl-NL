---
title: Workflows toepassen op pagina's
description: Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit de Sidekick.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: d8b604c5-a6da-47c4-9422-b519e224c7ca
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
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
>AEM beheerders kunnen workflows starten met [diverse andere methoden](/help/sites-administering/workflows-starting.md).

## Workflows toepassen {#applying-workflows}

Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit de Sidekick.

De **Status** in de **Websites** De console wijst erop of een werkschema op een pagina is toegepast:

![workflowstatus](assets/workflowstatus.png)

### Een workflow starten vanuit de websiteconsole {#starting-a-workflow-from-the-websites-console}

1. Open de websiteconsole. ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. Selecteer in de boomstructuur Websites het bovenliggende element van de pagina waarop u de workflow wilt toepassen.
1. Selecteer de pagina in de paginalijst en klik op Workflow.
1. Selecteer in het dialoogvenster Workflow starten de workflow die u wilt toepassen. Voer eventueel een opmerking en een titel in. Klik vervolgens op Start.

### Een workflow starten met Sidekick {#starting-a-workflow-using-sidekick}

1. Open de websiteconsole.
1. Open de gewenste pagina.
1. Selecteer het tabblad Werkstroom in de Sidekick.
1. Breid uit **Workflow** , zodat u het dialoogvenster **Workflow** en naar keuze **Werkstroomtitel** en **Opmerking**.

   ![workflowstartsidekick](assets/workflowstartsidekick.png)

1. Klikken **Workflow starten** om een nieuwe werkschemainstantie met de eigenschappen te beginnen u vormde en de huidige pagina als lading. De workflow wordt nu uitgevoerd.
