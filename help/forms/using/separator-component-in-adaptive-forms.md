---
title: Scheidingscomponent in adaptieve vormen
seo-title: Scheidingscomponent in adaptieve vormen
description: U kunt de scheidingscomponent gebruiken om delen van een formulier visueel te scheiden.
seo-description: U kunt de scheidingscomponent gebruiken om delen van een formulier visueel te scheiden.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: a8aa77fe-5880-4c4e-9e1b-3c5a8772c29d
docset: aem65
translation-type: tm+mt
source-git-commit: 5a76200a573d95026e2347d2049a089d975b5619
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Scheidingscomponent in adaptieve vormen{#separator-component-in-adaptive-forms}

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **Elementnaam:** geeft de naam van de component op. De SOM-expressies richten zich op de component met de waarde die is opgegeven in het veld Elementnaam.
* **Dikte:** geeft de dikte van de scheidingscomponent op in pixels.

* **CSS-klasse:** geeft de aangepaste CSS-klasse voor de scheidingscomponent op

* **Inline stijlen:** met AEM Forms kunt u nu inline CSS-stijlen toepassen op afzonderlijke adaptieve formuliercomponenten en een voorvertoning van de wijzigingen in real-time bekijken.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Zie [De modus Lay-out gebruiken om het formaat van componenten te wijzigen](../../forms/using/resize-using-layout-mode.md) voor meer informatie.

Eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een scheidingscomponent en tik ![cmppr](assets/cmppr.png). De eigenschappen worden in het zijpaneel geopend.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen om CSS-eigenschappen op te geven. Bijvoorbeeld: a. Klik op het tabblad Veld op **Item toevoegen**. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld **border**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld **3px effen zwart**.
1. Klik **Add Punt** om een ander bezit en zijn waarde te specificeren.
1. Klik op **Voorvertoning** om een voorvertoning van de wijzigingen in het formulier weer te geven.
1. Klik **OK** om de wijzigingen te bevestigen of **Annuleren** om het dialoogvenster zonder wijzigingen af te sluiten.

