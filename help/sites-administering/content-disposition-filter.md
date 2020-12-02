---
title: Filter voor inhoudsafzetting
seo-title: Filter voor inhoudsafzetting
description: Leer hoe te om de Filter van de Verplaatsing van de Inhoud te gebruiken om aanvallen van XSS te verhinderen.
seo-description: Leer hoe te om de Filter van de Verplaatsing van de Inhoud te gebruiken om aanvallen van XSS te verhinderen.
uuid: 145a88e0-9fa8-42db-b189-eda507c33049
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
discoiquuid: badfaa18-472e-4777-a7dc-9c28441b38b7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Filter voor inhoudsafzetting{#content-disposition-filter}

Het filter voor de indeling van inhoud is een beveiligingsfunctie tegen XSS-aanvallen op SVG-bestanden.

Na installatie blokkeert het filter de toegang tot alle elementen. U kunt een PDF bijvoorbeeld niet online bekijken. In deze sectie wordt beschreven hoe u het filter naar wens kunt configureren.

## Filter voor inhoudsafzetting configureren {#configure-content-disposition-filter}

U kunt [Apache Sling Content Disposition Filter in GitHub](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java) bekijken.

De opties voor het filter voor het verplaatsen van inhoud bieden de volgende functionaliteit:

* Paden voor positie van inhoud: een lijst met paden waarop het filter wordt toegepast, gevolgd door een lijst met MIME-typen die op dat pad worden uitgesloten. Dit pad moet een absoluut pad zijn en mag aan het einde een jokerteken (&#39;&amp;ast;&#39;) bevatten, zodat elk bronnenpad overeenkomt met het opgegeven padvoorvoegsel. Bijvoorbeeld: /content/&amp;ast;:image/jpeg,image/svg+xml &quot; zal het filter toepassen op elk knooppunt in /content, behalve JPG- en SVG-afbeeldingen

* Uitgesloten bronpaden: een lijst van uitgesloten middelen, moet elk middelweg als absolute en volledig gekwalificeerde weg worden gegeven. Overeenkomende voorvoegsels/jokertekens worden niet ondersteund.

* Inschakelen voor alle bronnenpaden: Met deze markering wordt bepaald of dit filter moet worden ingeschakeld voor alle paden, behalve voor de uitgesloten paden die worden gedefinieerd door Uitgesloten bronpaden. Als u deze waarde instelt op &#39;true&#39;, worden paden voor het verwijderen van inhoud genegeerd. Onafhankelijk van de configuratie worden alleen bronpaden behandeld die een eigenschap met de naam &#39;jcr:data&#39; of &#39;jcr:content jcr:data&#39; bevatten.

