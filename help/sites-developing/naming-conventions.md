---
title: Naamgevingsconventies voor knooppunten in de Java Content Repository
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 01c6bb29-1d2d-4a45-b291-0e8d97c01a08
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Naamgevingsconventies {#naming-conventions}

Knooppunten in de gegevensopslagruimte zijn onderworpen aan de naamconventies van de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Er worden echter AEM andere conventies voor de naam van paginaknooppunten opgelegd.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de AEM uitvoering van de [JCR-hulpprogramma&#39;s](#jcr-utilities).
* PageManager: de [Paginabeheer](#page-manager) biedt methoden voor bewerkingen op paginaniveau.
* Volgens de interface die wordt gebruikt:

   * [Standaardinterface met aanraakbediening](#standard-ui)
   * [Klassieke interface](#classic-ui)

### JCR-hulpprogramma&#39;s {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) is de AEM uitvoering van de hulpprogramma&#39;s van het GCO. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`

   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.

* `createValidName`

   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[PageManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) biedt methoden voor bewerkingen op paginaniveau op basis van [JCRUtil](#jcr-utilities).

### Standaardinterface {#standard-ui}

De standaardinterface met aanraakbediening:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:

   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

### Klassieke interface {#classic-ui}

De klassieke gebruikersinterface legt strengere beperkingen op:

* Valideert de naam wanneer een expliciete knooppuntnaam wanneer één van beiden:

   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

* Geldige tekens (alleen deze tekens zijn geldig wanneer een pagina wordt gemaakt vanuit de klassieke interface, ook al `PageManagerImpl` extra tekens toestaan):

   * &#39;a&#39; naar &#39;z&#39;
   * &#39;A&#39; naar &#39;Z&#39;
   * 0 tot en met 9
   * _ (onderstrepingsteken)
   * `-` (streepje/min)
