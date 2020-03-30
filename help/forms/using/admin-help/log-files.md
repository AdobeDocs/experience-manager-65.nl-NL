---
title: Logbestanden
seo-title: Logbestanden
description: Gebeurtenissen zoals runtime- of opstartfouten worden opgenomen in de logbestanden van de toepassingsserver, die kunnen worden geopend met een teksteditor.
seo-description: Gebeurtenissen zoals runtime- of opstartfouten worden opgenomen in de logbestanden van de toepassingsserver, die kunnen worden geopend met een teksteditor.
uuid: 6ed9fdcd-ff02-4b35-893f-09261a6a557a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: cf140483-470f-4bff-8870-304207508aab
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Logbestanden {#log-files}

Gebeurtenissen zoals runtime- of opstartfouten worden opgenomen in de logbestanden van de toepassingsserver. Als u problemen hebt met de implementatie op de toepassingsserver, kunt u de logbestanden gebruiken om het probleem op te sporen. U kunt de logboekdossiers openen gebruikend om het even welke tekstredacteur.

(JBoss) De volgende logbestanden bevinden zich in de `[appserver root]/server/'server'/log` map:

* boot.log
* server.log.*[jjjj-mm-dd]*
* server.log

(WebLogic) Domeinlogbestanden bevinden zich in de `[appserverdomain]` map en serverlogbestanden bevinden zich in de `[appserverdomain]/servers/[appserver name]/logs` map:

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) De volgende logbestanden bevinden zich in de `[appserver root]/profiles/default/logs/[appserver name]` map:

* SystemErr.log
* SystemOut.log
* StartServer.log

