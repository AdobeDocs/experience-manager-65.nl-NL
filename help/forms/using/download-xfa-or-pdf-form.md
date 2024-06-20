---
title: XFA of een PDF-formuliersjabloon downloaden
description: U kunt formulieren vanuit de gegevensopslagruimte exporteren naar het lokale systeem en de gedownloade formulieren migreren naar een nieuwe gegevensopslagruimte.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
role: Admin,User
exl-id: 5b7b9816-38c1-4780-b1fc-8184971f3772
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# XFA of een PDF-formuliersjabloon downloaden {#download-an-xfa-or-a-pdf-form-template}

Met de downloadbewerking kunt u, zoals de naam aangeeft, formulieren exporteren van de opslagplaats naar het lokale systeem. In combinatie met het uploaden kunt u met deze bewerking uw formulieren migreren van de ene opslagplaats naar de andere.

In AEM Forms wordt het downloaden ondersteund voor de volgende elementtypen:

* Formuliersjablonen (XFA Forms)
* PDF forms
* Documenten (bestanden met platte PDF)

AEM Forms ondersteunt het downloaden van deze formuliertypen afzonderlijk of in een map met een of meer ondersteunde formulieren.

Naast deze elementen kunt u de opdracht `Resource` type element als dit voorkomt in een map. Deze functie is beschikbaar zodat u de bron waarnaar wordt verwezen door een XFA-formulier, samen met het formulier kunt downloaden.

## Een of meer formulieren downloaden {#download-one-or-more-forms}

1. Meld u aan bij de gebruikersinterface van AEM Forms op `https://<server>:<port>/aem/forms.html`.

1. Navigeer naar de locatie van het element dat u wilt downloaden.

1. Selecteer het element. Klik op de knop **[!UICONTROL Download]** ![aem6forms_download](assets/aem6forms_download.png) in de werkbalk.

   >[!NOTE]
   >
   >U kunt slechts één formulier selecteren om te downloaden. Als u meerdere formulieren wilt downloaden, moet u deze downloaden als een map.

1. Klik op **[!UICONTROL Download]**.

   AEM Forms genereert een ZIP-bestand met het geselecteerde bestand of de geselecteerde map.

   Als u een map downloadt, worden de ondersteunde elementen in de map gedownload in de bestaande hiërarchie.

   Het ZIP-bestand wordt opgeslagen in het `Downloads` op uw systeem.

## Verwante overwegingen voor het uploaden {#related-considerations-for-the-upload-operation}

* U kunt het ZIP-bestand uploaden naar een andere locatie in dezelfde opslagplaats of een andere opslagplaats
* De hiërarchie van de elementen in een map blijft behouden tijdens het uploaden
* Wijzigingen in metagegevens die zijn aangebracht in de gedownloade elementen voordat deze zijn gedownload, worden weerspiegeld tijdens het uploaden
