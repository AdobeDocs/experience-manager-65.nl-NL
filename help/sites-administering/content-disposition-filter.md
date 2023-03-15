---
title: Filter voor inhoudsafzetting
seo-title: Content Disposition Filter
description: Leer hoe te om de Filter van de Verplaatsing van de Inhoud te gebruiken om aanvallen van XSS te verhinderen.
seo-description: Learn how to use the Content Disposition Filter to prevent XSS attacks.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
exl-id: 1c3d0d48-5c31-42a8-8698-922d7c2127e9
source-git-commit: d1fc2ff44378276522c2ff3208f5b3bdc4484bba
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Filter voor inhoudsafzetting {#content-disposition-filter}

Inhoudsverwijderingsfilter is een beveiligingsfunctie tegen XSS-aanvallen op SVG-bestanden.

Na installatie blokkeert het filter de toegang tot alle elementen. U kunt een PDF bijvoorbeeld niet online weergeven. In deze sectie wordt beschreven hoe u het filter naar wens kunt configureren.

## Filter voor inhoudsafzetting configureren {#configure-content-disposition-filter}

U kunt de [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java).

De opties voor het filter voor het verplaatsen van inhoud bieden de volgende functionaliteit:

* **Paden voor positie van inhoud:** een lijst met paden waarop het filter wordt toegepast, gevolgd door een lijst met MIME-typen die op dat pad worden uitgesloten. Dit pad moet een absoluut pad zijn en mag een jokerteken bevatten (`*`) aan het eind, om elk middelweg met de bepaalde wegprefix te passen. Bijvoorbeeld: `/content/*:image/jpeg,image/svg+xml` past het filter toe op elk knooppunt in `/content?` behalve JPG- en SVG-afbeeldingen

* **Uitgesloten bronpaden:** een lijst van uitgesloten middelen , elk middelpad moet worden gegeven als absoluut en volledig gekwalificeerd pad . Overeenkomende voorvoegsels/jokertekens worden niet ondersteund.

* **Inschakelen voor alle bronnenpaden:** Met deze markering wordt bepaald of dit filter moet worden ingeschakeld voor alle paden, behalve voor de uitgesloten paden die worden gedefinieerd door Uitgesloten bronpaden. Als u deze waarde instelt op &#39;true&#39;, worden paden voor het verwijderen van inhoud genegeerd. Onafhankelijk van de configuratie, slechts zijn de middelwegen behandeld die een genoemd bezit bevatten `jcr:data` of `jcr:content/jcr:data`.
