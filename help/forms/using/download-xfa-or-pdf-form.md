---
title: XFA of een PDF-formuliersjabloon downloaden
seo-title: XFA of een PDF-formuliersjabloon downloaden
description: U kunt formulieren vanuit de gegevensopslagruimte exporteren naar het lokale systeem en de gedownloade formulieren migreren naar een nieuwe gegevensopslagruimte.
seo-description: U kunt formulieren vanuit de gegevensopslagruimte exporteren naar het lokale systeem en de gedownloade formulieren migreren naar een nieuwe gegevensopslagruimte.
uuid: 5f7fbd14-cb9d-4749-8708-7efe49df89d7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 6699e0e7-fd42-41ae-86a2-3b940d905111
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Een XFA of een PDF-formuliersjabloon {#download-an-xfa-or-a-pdf-form-template} downloaden

Met de downloadbewerking kunt u, zoals de naam aangeeft, formulieren exporteren van de opslagplaats naar het lokale systeem. In combinatie met het uploaden kunt u met deze bewerking uw formulieren migreren van de ene opslagplaats naar de andere.

In AEM Forms wordt het downloaden ondersteund voor de volgende elementtypen:

* Formuliersjablonen (XFA Forms)
* PDF forms
* Documenten (vlakke PDF-bestanden)

AEM Forms ondersteunt het downloaden van deze formuliertypen afzonderlijk of in een map met een of meer ondersteunde formulieren.

Naast deze elementen kunt u het type element `Resource` downloaden als dit in een map aanwezig is. Deze functie is beschikbaar zodat u de bron waarnaar wordt verwezen door een XFA-formulier, samen met het formulier kunt downloaden.

## Een of meer formulieren {#download-one-or-more-forms} downloaden

1. Meld u aan bij de AEM Forms-gebruikersinterface op `https://<server>:<port>/aem/forms.html`.

1. Navigeer naar de locatie van het element dat u wilt downloaden.

1. Selecteer het element. Klik op het pictogram **[!UICONTROL Download]** ![aem6forms_download](assets/aem6forms_download.png) op de werkbalk.

   >[!NOTE]
   >
   >U kunt slechts één formulier selecteren om te downloaden. Als u meerdere formulieren wilt downloaden, moet u deze downloaden als een map.

1. Klik in het dialoogvenster dat wordt weergegeven op **[!UICONTROL Download]**.

   AEM Forms genereert een ZIP-bestand met het geselecteerde bestand of de geselecteerde map.

   Als u een map downloadt, worden de ondersteunde elementen in de map gedownload in de bestaande hiërarchie.

   Het ZIP-bestand wordt opgeslagen in de map `Downloads` op uw systeem.

## Gerelateerde overwegingen voor uploadbewerking {#related-considerations-for-the-upload-operation}

* U kunt het ZIP-bestand uploaden naar een andere locatie in dezelfde opslagplaats of een andere opslagplaats
* De hiërarchie van de elementen in een map blijft behouden tijdens het uploaden
* Wijzigingen in metagegevens die zijn aangebracht in de gedownloade elementen voordat deze zijn gedownload, worden weerspiegeld tijdens het uploaden

