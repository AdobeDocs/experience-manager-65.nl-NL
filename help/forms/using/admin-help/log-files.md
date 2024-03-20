---
title: Logbestanden
description: Gebeurtenissen zoals runtime- of opstartfouten worden opgenomen in de logbestanden van de toepassingsserver, die kunnen worden geopend met een teksteditor.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 23a65be4-3277-4c73-9189-a9b4d7be73cd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Logbestanden {#log-files}

Gebeurtenissen zoals runtime- of opstartfouten worden opgenomen in de logbestanden van de toepassingsserver. Als u problemen hebt met de implementatie op de toepassingsserver, kunt u de logbestanden gebruiken om het probleem op te sporen. U kunt de logboekdossiers openen gebruikend om het even welke tekstredacteur.

(JBoss) De volgende logbestanden bevinden zich in het dialoogvenster `[appserver root]/server/'server'/log` map:

* boot.log
* server.log.*[jjjj-mm-dd]*
* server.log

(WebLogic) Domeinlogbestanden bevinden zich in de `[appserverdomain]` en de dossiers van het serverlogboek zijn in `[appserverdomain]/servers/[appserver name]/logs` map:

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) De volgende logbestanden bevinden zich in de map `[appserver root]/profiles/default/logs/[appserver name]` map:

* SystemErr.log
* SystemOut.log
* StartServer.log
