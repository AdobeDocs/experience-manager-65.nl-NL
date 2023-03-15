---
title: Naamconventies voor het testen van elementen
seo-title: Naming conventions for assets
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository. Adobe Experience Manager stelt echter andere conventies op voor de naam van elementknooppunten.
seo-description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
uuid: 6b622a60-90e8-461e-9b67-42c11c7038f9
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 55e66c66-0120-4ed4-94c5-d65a434bb59b
exl-id: bb6a5913-0871-47c7-8641-936e98920ec0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Naamconventies voor het testen van elementen{#naming-conventions-for-assets-testing}

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
