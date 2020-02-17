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

---


# Scheidingscomponent in adaptieve vormen{#separator-component-in-adaptive-forms}

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **** Elementnaam: Specifies the name of the component. De SOM-expressies richten zich op de component met de waarde die is opgegeven in het veld Elementnaam.
* **** Dikte: Hiermee wordt de dikte van de scheidingscomponent in pixels opgegeven.

* **** CSS-klasse: Hiermee wordt de aangepaste CSS-klasse voor de scheidingscomponent opgegeven

* **** Inline stijlen: Met AEM Forms kunt u nu inline CSS-stijlen toepassen op afzonderlijke adaptieve formuliercomponenten en een voorvertoning van de wijzigingen weergeven in real-time.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Zie De modus Lay-out [gebruiken om het formaat van componenten](../../forms/using/resize-using-layout-mode.md)te wijzigen voor meer informatie.

Eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een scheidingscomponent en tik op ![cmp](assets/cmppr.png). De eigenschappen worden in het zijpaneel geopend.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen om CSS-eigenschappen op te geven. Bijvoorbeeld:
a. Klik op het tabblad Veld op Item **** toevoegen. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld **rand**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld, effen zwart **,** 3px.
1. Klik op Item **** toevoegen om een andere eigenschap en de bijbehorende waarde op te geven.
1. Klik op **Voorbeeld** om een voorbeeld van de wijzigingen in het formulier te bekijken.
1. Klik op **OK** om de wijzigingen te bevestigen of op **Annuleren** om het dialoogvenster zonder wijzigingen af te sluiten.

