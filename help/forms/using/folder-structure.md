---
title: De mapstructuur
seo-title: De mapstructuur
description: Uitleg over de mapstructuur van de broncode van de AEM Forms-werkruimte die moet worden aangepast.
seo-description: Uitleg over de mapstructuur van de broncode van de AEM Forms-werkruimte die moet worden aangepast.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# De mappenstructuur {#understanding-the-folder-structure}

AEM Forms-werkruimtecomponenten zijn ontworpen op MVC-architectuur met behulp van backbone. Elke component heeft een bestand voor:

* Model, dat bedrijfslogica bevat.
* Sjabloon, dat wil zeggen een HTML-bestand dat interfacebesturingselementen bevat.
* De mening, die als klasse van het Controlemechanisme aan Malplaatje dienst doet.

De elementen voor alle componenten worden in de hieronder beschreven mapstructuur geplaatst. Als u toegang wilt tot de elementen, meldt u zich aan bij CRXDE Lite en bladert u naar `/libs/ws/js/runtime/`.

**** modelsBevat backbonemodellen.

**** viewsBevat backboneweergaven.

**** templatesBevat alleen de HTML-sjablonen voor de componenten.

**** routesBevat universele routes. De omslag van malplaatjes binnen routes bevat de code van HTML en de verwijzingen naar de componenten.

**** servicesContains de dienstinterface om de server APIs van Adobe Experience Manager op REST eindpunt te roepen.

**** utilContains generische nut bruikbaar door veelvoudige componenten.
