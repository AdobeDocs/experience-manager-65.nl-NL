---
title: Scheidingscomponent in adaptieve vormen
description: U kunt de scheidingscomponent gebruiken om delen van een formulier visueel te scheiden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 11cbf865-c8e2-4833-b0b8-a3cb5e42f5cd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Scheidingscomponent in adaptieve vormen{#separator-component-in-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor het ontwerpen van Adaptive Forms met behulp van stichtingscomponenten. </span>

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **Elementnaam:** Specifies the name of the component. De SOM-expressies richten zich op de component met een waarde die is opgegeven in het veld Elementnaam.
* **Dikte:** Hiermee wordt de dikte van de scheidingscomponent in pixels opgegeven.

* **CSS-klasse:** Hiermee wordt de aangepaste CSS-klasse voor de scheidingscomponent opgegeven

* **Inline stijlen:** Met AEM Forms kunt u nu inline CSS-stijlen toepassen op afzonderlijke adaptieve formuliercomponenten en een voorvertoning van de wijzigingen in real-time bekijken.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Zie voor meer informatie [Gebruik de modus Lay-out om het formaat van componenten te wijzigen](../../forms/using/resize-using-layout-mode.md).

De eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een scheidingscomponent en selecteer ![cmppr](assets/cmppr.png). De eigenschappen worden geopend in het zijpaneel.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen zodat u CSS-eigenschappen kunt opgeven. Bijvoorbeeld: a. Klik op het tabblad Veld op **Item toevoegen**. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld: **border**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld: **3-px effen zwart**.
1. Klikken **Item toevoegen** om een andere eigenschap en de bijbehorende waarde op te geven.
1. Klikken **Voorvertoning** zodat u een voorbeeld van de wijzigingen in het formulier kunt bekijken.
1. Klikken **OK** als u de wijzigingen wilt bevestigen of **Annuleren** om het dialoogvenster zonder wijzigingen af te sluiten.
