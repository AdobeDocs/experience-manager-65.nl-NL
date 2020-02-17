---
title: De mapstructuur
seo-title: De mapstructuur
description: Uitleg over de mapstructuur van de broncode van de AEM Forms-werkruimte om deze aan te passen.
seo-description: Uitleg over de mapstructuur van de broncode van de AEM Forms-werkruimte om deze aan te passen.
uuid: ee844f89-887e-4f07-9db3-389859baa374
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 7427858d-8eec-423d-a0a9-444140420620
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# De mapstructuur {#understanding-the-folder-structure}

De componenten van de werkruimte van Vormen AEM worden ontworpen op architectuur MVC gebruikend Backbone. Elke component heeft een bestand voor:

* Model, dat bedrijfslogica bevat.
* Sjabloon, dat wil zeggen een HTML-bestand dat interfacebesturingselementen bevat.
* De mening, die als klasse van het Controlemechanisme aan Malplaatje dienst doet.

De elementen voor alle componenten worden in de hieronder beschreven mapstructuur geplaatst. Meld u aan bij CRXDE Lite en blader naar de elementen om deze te openen `/libs/ws/js/runtime/`.

**modellen** bevatten backbonemodellen.

**weergaven** bevat backboneweergaven.

**sjablonen** bevatten alleen de HTML-sjablonen voor de componenten.

**De routes** bevatten universele routes. De omslag van malplaatjes binnen routes bevat de code van HTML en de verwijzingen naar de componenten.

**services** Bevat service-interface waarmee API&#39;s van de Adobe Experience Manager-server op het REST-eindpunt worden aangeroepen.

**util** bevat generische nut bruikbaar door veelvoudige componenten.

**[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)**
