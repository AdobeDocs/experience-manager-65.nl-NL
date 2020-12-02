---
title: Naamgevingsconventies
seo-title: Naamgevingsconventies
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
seo-description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
uuid: 0515c5c5-3e93-4710-983f-c08c146467fc
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 198098c0-432b-4a93-a94e-2552337435dd
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---


# Naamgeving van conventies{#naming-conventions}

Nodes in de opslagplaats zijn onderworpen aan naamconventies van de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Er worden echter AEM andere conventies voor de naam van paginaknooppunten opgelegd.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de AEM implementatie van de [JCR-hulpprogramma&#39;s](#jcr-utilities).
* PageManager: de [Paginabeheer](#page-manager) biedt methoden voor bewerkingen op paginaniveau.
* Volgens de interface die wordt gebruikt:

   * [Standaardinterface met aanraakbediening](#standard-ui)
   * [Klassieke interface](#classic-ui)

### JCR-hulpprogramma {#jcr-utilities}

[](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) JcrUtilis de AEM implementatie van de hulpprogramma&#39;s van het JCR. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`

   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.

* `createValidName`

   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) PageManager biedt methoden voor bewerkingen op paginaniveau op basis van  [JCRUtil](#jcr-utilities).

### Standaardinterface {#standard-ui}

De standaardinterface met aanraakbediening:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:

   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

### Klassieke UI {#classic-ui}

De klassieke gebruikersinterface legt strengere beperkingen op:

* Valideert de naam wanneer een expliciete knooppuntnaam wanneer één van beiden:

   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

* Geldige tekens (alleen deze tekens zijn geldig wanneer een pagina wordt gemaakt vanuit de klassieke interface, ook al staan `PageManagerImpl` extra tekens toe):

   * &#39;a&#39; naar &#39;z&#39;
   * &#39;A&#39; naar &#39;Z&#39;
   * 0 tot en met 9
   * _ (onderstrepingsteken)
   * `-` (streepje/min)

