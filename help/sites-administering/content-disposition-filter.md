---
title: Filter voor inhoudsafzetting
description: Leer hoe te om de Filter van de Verplaatsing van de Inhoud te gebruiken om aanvallen van XSS te verhinderen.
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Filter voor inhoudsafzetting {#content-disposition-filter}

Inhoudsverwijderingsfilter is een beveiligingsfunctie tegen XSS-aanvallen op SVG-bestanden.

Na installatie blokkeert het filter de toegang tot alle elementen. U kunt een PDF bijvoorbeeld niet online weergeven. In deze sectie wordt beschreven hoe u het filter naar wens kunt configureren.

## Filter voor inhoudsafzetting configureren {#configure-content-disposition-filter}

U kunt de [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java).

De opties voor het filter voor het verplaatsen van inhoud bieden de volgende functionaliteit:

* **Paden voor positie van inhoud:** Een lijst met paden waarop het filter wordt toegepast, gevolgd door een lijst met MIME-typen die op dat pad moeten worden uitgesloten. Dit pad moet een absoluut pad zijn en mag een jokerteken bevatten (`*`) aan het eind, om elk middelweg met de bepaalde wegprefix te passen. Bijvoorbeeld: `/content/*:image/jpeg,image/svg+xml` past het filter toe op elk knooppunt in `/content?` behalve JPG- en SVG-afbeeldingen.

* **Uitgesloten bronpaden:** Een lijst van uitgesloten middelen, moet elk middelweg als absolute en volledig gekwalificeerde weg worden gegeven. Overeenkomende voorvoegsels/jokertekens worden niet ondersteund.

* **Inschakelen voor alle bronnenpaden:** Deze vlag controleert of om deze filter voor alle wegen toe te laten, behalve de uitgesloten wegen die door Uitgesloten Wegen van het Middel worden bepaald. Als u deze markering instelt op &#39;true&#39;, worden paden voor het verwijderen van inhoud genegeerd. Onafhankelijk van de configuratie, slechts zijn de middelwegen behandeld die een genoemd bezit bevatten `jcr:data` of `jcr:content/jcr:data`.
