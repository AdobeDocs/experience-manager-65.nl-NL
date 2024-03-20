---
title: Naamgevingsconventies voor het testen van elementen
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository. Adobe Experience Manager stelt echter andere conventies op voor de naam van elementknooppunten.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
exl-id: bb6a5913-0871-47c7-8641-936e98920ec0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Naamgevingsconventies voor het testen van elementen{#naming-conventions-for-assets-testing}

Knooppunten in de gegevensopslagruimte zijn onderworpen aan de naamconventies van de [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). Adobe Experience Manager stelt echter andere conventies op voor de naam van elementknooppunten.

## Klassieke interface {#classic-ui}

De klassieke gebruikersinterface legt strengere beperkingen op:

* Valideert de elementnaam wanneer een expliciete knooppuntnaam:

   * er is een elementtitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

* Geldige tekens (alleen deze tekens zijn geldig wanneer een element wordt gemaakt vanuit de klassieke interface):

   * &#39;a&#39; naar &#39;z&#39;
   * &#39;A&#39; naar &#39;Z&#39;
   * 0 tot en met 9
   * _ (onderstrepingsteken)
   * `-` (streepje/min)
