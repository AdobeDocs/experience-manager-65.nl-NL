---
title: De mapstructuur begrijpen
description: Uitleg over de mapstructuur van de broncode van de AEM Forms-werkruimte die moet worden aangepast.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: a4c1d3d8-477e-4edf-9dde-4ef9c766be5a
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# De mapstructuur begrijpen {#understanding-the-folder-structure}

AEM Forms-werkruimtecomponenten zijn ontworpen op MVC-architectuur met behulp van backbone. Elke component heeft een bestand voor:

* Model, dat bedrijfslogica bevat.
* Sjabloon, dat wil zeggen een HTML-bestand dat interfacecontroles bevat.
* De mening, die als klasse van het Controlemechanisme aan Malplaatje dienst doet.

De elementen voor alle componenten worden in de hieronder beschreven mapstructuur geplaatst. Meld u aan bij CRXDE Lite en blader naar de elementen om deze te openen `/libs/ws/js/runtime/`.

**modellen** Bevat backbonemodellen.

**views** Bevat backboneweergaven.

**sjablonen** Bevat alleen de HTML-sjablonen voor de componenten.

**routes** Bevat universele routes. De omslag van malplaatjes binnen routes bevat de code van de HTML en de verwijzingen naar de componenten.

**diensten** Bevat de dienstinterface om de server APIs van Adobe Experience Manager op REST eindpunt te roepen.

**util** Bevat generische nut bruikbaar door veelvoudige componenten.
