---
title: Workflows toepassen op pagina's
seo-title: Workflows toepassen op pagina's
description: Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit Sidetrap.
seo-description: Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit Sidetrap.
uuid: 55f6f1d7-da54-4732-b9ff-b7479622db51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 22712b73-90f2-4329-b32f-dbb7ce802d1d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 11%

---


# Workflows toepassen op pagina&#39;s{#applying-workflows-to-pages}

Wanneer u de workflow toepast, geeft u de volgende informatie op:

* De workflow die moet worden toegepast.

   U kunt elke workflow toepassen (waartoe u toegang hebt, zoals is toegewezen door uw AEM-beheerder).
* Optioneel:

   * Een opmerking met informatie over de reden waarom u de workflow hebt gestart.
   * Een titel die helpt de werkstroominstantie in Inbox van een gebruiker identificeren.

>[!NOTE]
>
>AEM beheerders kunnen werkstromen beginnen gebruikend [verscheidene andere methodes](/help/sites-administering/workflows-starting.md).

## Workflows toepassen {#applying-workflows}

Workflows kunnen worden gestart vanuit de websiteconsole of, wanneer u een pagina bewerkt, vanuit Sidetrap.

De **Status** kolom in **Websites** console wijst erop of een werkschema op een pagina is toegepast:

![workflowstatus](assets/workflowstatus.png)

### Een workflow starten vanuit de websiteconsole {#starting-a-workflow-from-the-websites-console}

1. Open de websiteconsole. ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. Selecteer in de boomstructuur Websites het bovenliggende element van de pagina waarop u de workflow wilt toepassen.
1. Selecteer de pagina in de paginalijst en klik op Workflow.
1. Selecteer in het dialoogvenster Workflow starten de workflow die u wilt toepassen. Voer eventueel een opmerking en een titel in. Klik vervolgens op Start.

### Starten van een workflow met Sidetrap {#starting-a-workflow-using-sidekick}

1. Open de websiteconsole.
1. Open de gewenste pagina.
1. Selecteer het tabblad Workflow in de Sidetrap.
1. Breid **Workflow** dialoog uit, toestaand u om **Workflow** te selecteren en naar keuze **Titel van workflow** en **Commentaar** in te gaan.

   ![workflowstartsidekick](assets/workflowstartsidekick.png)

1. Klik **Workflow van het Begin** om een nieuwe werkschemainstantie met de eigenschappen te beginnen u en de huidige pagina als nuttige lading vormde. De workflow wordt nu uitgevoerd.

