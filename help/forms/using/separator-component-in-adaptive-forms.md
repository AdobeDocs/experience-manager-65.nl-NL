---
title: Scheidingscomponent in adaptieve vormen
seo-title: Separator component in adaptive forms
description: U kunt de scheidingscomponent gebruiken om delen van een formulier visueel te scheiden.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: a8aa77fe-5880-4c4e-9e1b-3c5a8772c29d
docset: aem65
feature: Adaptive Forms
exl-id: 11cbf865-c8e2-4833-b0b8-a3cb5e42f5cd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Scheidingscomponent in adaptieve vormen{#separator-component-in-adaptive-forms}

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **Elementnaam:** Specifies the name of the component. De SOM-expressies richten zich op de component met de waarde die is opgegeven in het veld Elementnaam.
* **Dikte:** Hiermee wordt de dikte van de scheidingscomponent in pixels opgegeven.

* **CSS-klasse:** Hiermee wordt de aangepaste CSS-klasse voor de scheidingscomponent opgegeven

* **Inline stijlen:** Met AEM Forms kunt u nu inline CSS-stijlen toepassen op afzonderlijke adaptieve formuliercomponenten en een voorvertoning van de wijzigingen in real-time bekijken.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Zie voor meer informatie [Gebruik de modus Lay-out om het formaat van componenten te wijzigen](../../forms/using/resize-using-layout-mode.md).

Eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een scheidingscomponent en tik op ![cmppr](assets/cmppr.png). De eigenschappen worden in het zijpaneel geopend.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen om CSS-eigenschappen op te geven. Bijvoorbeeld: a. Klik op het tabblad Veld op **Item toevoegen**. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld: **border**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld: **3px effen zwart**.
1. Klikken **Item toevoegen** om een andere eigenschap en de bijbehorende waarde op te geven.
1. Klikken **Voorvertoning** om een voorbeeld van de wijzigingen in het formulier te bekijken.
1. Klikken **OK** om de wijzigingen te bevestigen of **Annuleren** om het dialoogvenster zonder wijzigingen af te sluiten.
