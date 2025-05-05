---
title: Scheidingscomponent in adaptieve vormen
description: U kunt de scheidingscomponent gebruiken om delen van een formulier visueel te scheiden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 11cbf865-c8e2-4833-b0b8-a3cb5e42f5cd
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# Scheidingscomponent in adaptieve vormen{#separator-component-in-adaptive-forms}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor het ontwerpen van Adaptive Forms met behulp van stichtingscomponenten. </span>

Met de scheidingscomponent kunt u deelvensters van een formulier visueel van elkaar scheiden. U kunt de algemene vormgeving en stijl van een scheidingscomponent definiëren door de volgende eigenschappen van de scheidingscomponent op te geven:

* **Naam van het Element:** specificeert de naam van de component. De SOM-expressies richten zich op de component met een waarde die is opgegeven in het veld Elementnaam.
* **Dikte:** specificeert de dikte van de separatorcomponent in pixel.

* **CSS Klasse:** specificeert de douaneCSS klasse voor de separatorcomponent

* **Inline stijlen:** met AEM Forms, kunt u inline CSS stijlen nu toepassen op individuele adaptieve vormcomponenten en voorproef de veranderingen in real time.

U kunt de modus Lay-out gebruiken om het aantal kolommen te definiëren waaraan de scheidingscomponent zich uitstrekt. Voor meer informatie, zie {de wijze van de Lay-out van het 0} Gebruik om componenten [&#128279;](../../forms/using/resize-using-layout-mode.md) te resize.

De eigenschappen van een scheidingscomponent opgeven:

1. Selecteer een separatorcomponent en selecteer ![ cmp ](assets/cmppr.png). De eigenschappen worden geopend in het zijpaneel.
1. Klik op een tabblad in de sectie Inline CSS-eigenschappen zodat u CSS-eigenschappen kunt opgeven. Bijvoorbeeld: a. Op het lusje van het Gebied, klik **Punt** toevoegen. Er wordt een rij met twee velden toegevoegd.
1. Geef in het eerste veld links een CSS3-eigenschap op die u wilt toepassen. Bijvoorbeeld, **grens**. U kunt een eigenschap ook selecteren door op de knop pijl-omlaag te klikken. De vervolgkeuzelijst is niet uitputtend en u kunt elke ondersteunde CSS3-eigenschapnaam opgeven in dit veld.
1. Geef in het aangrenzende veld een geldige waarde op voor de opgegeven CSS3-eigenschap. Bijvoorbeeld, **3 px stevige zwarte**.
1. Klik **toevoegen Punt** om een ander bezit en zijn waarde te specificeren.
1. Klik **Voorproef** zodat kunt u voorproef de veranderingen in de vorm.
1. Klik **O.K.** als u de veranderingen wilt bevestigen of **annuleert** om de dialoog zonder enige veranderingen weg te gaan.
