---
title: Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag
seo-title: Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag
description: De Bouwer van de Vraag biedt een gemakkelijke manier om de inhoudsbewaarplaats te vragen
seo-description: De Bouwer van de Vraag biedt een gemakkelijke manier om de inhoudsbewaarplaats te vragen
uuid: e71be518-027c-4792-9e02-06405804d9d2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: ef253905-87da-4fa2-9f6c-778f1b12bd58
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# Het uitvoeren van een Evaluator van de Predicatie van de Douane voor de Bouwer van de Vraag{#implementing-a-custom-predicate-evaluator-for-the-query-builder}

Deze sectie beschrijft hoe te om [de Bouwer van de Vraag ](/help/sites-developing/querybuilder-api.md) uit te breiden door een douane te uitvoeren predikaat beoordelaar.

## Overzicht {#overview}

De [Query Builder](/help/sites-developing/querybuilder-api.md) biedt een eenvoudige manier om de opslagplaats voor inhoud op te vragen. CQ wordt geleverd met een set voorspellende beoordelaars die u helpen met uw gegevens om te gaan.

Nochtans zou u uw vragen kunnen willen vereenvoudigen door een douane uit te voeren predikt beoordelaar die wat ingewikkeldheid verbergt en een betere semantiek verzekert.

Een aangepaste predikaat kan ook andere dingen uitvoeren die niet direct mogelijk zijn met XPath, bijvoorbeeld:

* het zoeken van sommige gegevens van één of andere dienst
* aangepaste filtering op basis van berekening

>[!NOTE]
>
>De kwesties van prestaties moeten in overweging worden genomen wanneer het uitvoeren van een douane predikaat.

>[!NOTE]
>
>U kunt voorbeelden van vragen in [de sectie van de Bouwer van de Vraag](/help/sites-developing/querybuilder-api.md) vinden.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-onderzoek-douane-predicaat-evaluatorproject op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)

### Voorspelende evaluator in detail {#predicate-evaluator-in-detail}

Een predikaat beoordelaar behandelt de evaluatie van bepaalde predikaten, die de bepalende beperkingen van een vraag zijn.

Hiermee wordt een zoekrestrictie op een hoger niveau (zoals &quot;breedte > 200&quot;) toegewezen aan een specifieke JCR-query die past bij het werkelijke inhoudsmodel (bijvoorbeeld metagegevens/@breedte > 200). Of het kan knopen manueel filtreren en hun beperkingen controleren.

>[!NOTE]
>
>Zie de [Java-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/search/package-summary.html) voor meer informatie over het `PredicateEvaluator`- en `com.day.cq.search`-pakket.

### Implementatie van een aangepaste voorspellende evaluator voor replicatiemetagegevens {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

Als voorbeeld beschrijft deze sectie hoe te om een douane te creëren predikaat beoordelaar die gegevens helpt die op de replicatiemetagegevens worden gebaseerd:

* `cq:lastReplicated` die de datum van de laatste replicatieactie opslaat

* `cq:lastReplicatedBy` die identiteitskaart van de gebruiker opslaat die de laatste replicatieactie teweegbracht

* `cq:lastReplicationAction` die de laatste replicatiehandeling opslaat (bijvoorbeeld activering, deactivering)

#### Replicatiemetagegevens opvragen met standaardvoorspellende evaluatoren {#querying-replication-metadata-with-default-predicate-evaluators}

De volgende vraag haalt de lijst van knopen in `/content` tak die door `admin` sinds het begin van het jaar zijn geactiveerd.

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

Deze vraag is geldig maar moeilijk te lezen en benadrukt niet het verband tussen de drie replicatieeigenschappen. Het uitvoeren van een douane predikaat evaluator zal de ingewikkeldheid verminderen en de semantiek van deze vraag verbeteren.

#### Doelstellingen {#objectives}

Het doel van `ReplicationPredicateEvaluator` is de bovengenoemde vraag te steunen gebruikend de volgende syntaxis.

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

Het groeperen van replicatiemagegevens predikt met een douane predikaat evaluator helpt om een zinvolle vraag tot stand te brengen.

#### Geweven afhankelijkheden bijwerken {#updating-maven-dependencies}

>[!NOTE]
>
>De opstelling van nieuwe AEM die maven gebruiken wordt gedocumenteerd door [Hoe te AEM Projecten bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md).

Eerst moet u de Geweven gebiedsdelen van uw project bijwerken. De `PredicateEvaluator` maakt deel uit van het `cq-search` artefact zodat moet het aan uw Maven pom dossier worden toegevoegd.

>[!NOTE]
>
>Het bereik van de `cq-search`-afhankelijkheid wordt ingesteld op `provided` omdat `cq-search` wordt geleverd door de `OSGi`-container.

pom.xml

Het volgende fragment toont de verschillen, in [Unified diff format](https://en.wikipedia.org/wiki/Diff#Unified_format)

```
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)-  [pom.xml](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/7aed6b35b4c8dd3655296e1b10cf40c0dd1eaa61/pom.xml)

#### Het schrijven van ReplicationPredicateEvaluator {#writing-the-replicationpredicateevaluator}

Het `cq-search` project bevat de `AbstractPredicateEvaluator` abstracte klasse. Dit kan met een paar stappen worden uitgebreid om uw eigen douane uit te voeren voorspelt beoordelaar `(PredicateEvaluator`).

>[!NOTE]
>
>In de volgende procedure wordt uitgelegd hoe u een expressie `Xpath` kunt bouwen om gegevens te filteren. Een andere optie zou zijn de `includes` methode uit te voeren die gegevens op een rijbasis selecteert. Zie de [Java-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html#includes28comdaycqsearchpredicatejavaxjcrqueryrowcomdaycqsearchevalevaluationcontext29) voor meer informatie.

1. Een nieuwe Java-klasse maken die `com.day.cq.search.eval.AbstractPredicateEvaluator` uitbreidt
1. Annoteer uw klasse met een `@Component` als het volgende

   src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

   Het volgende fragment toont de verschillen, in [Unified diff format](https://en.wikipedia.org/wiki/Diff#Unified_format)

```
@@ -19,8 +19,11 @@
  */
 package com.adobe.aem.docs.search;

+import org.apache.felix.scr.annotations.Component;
+
 import com.day.cq.search.eval.AbstractPredicateEvaluator;

+@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
 public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

 }
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)-  [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/ec70fac35fbd0d132e00c6066a204804e9cbe70f/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)

>[!NOTE]
>
>De `factory`moet een unieke tekenreeks zijn die begint met `com.day.cq.search.eval.PredicateEvaluator/`en eindigt met de naam van uw aangepaste `PredicateEvaluator`.

>[!NOTE]
>
>De naam van `PredicateEvaluator` is de voorspelbare naam, die wordt gebruikt wanneer het bouwen van vragen.

1. Overschrijven:

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   In de opheffingsmethode bouwt u een `Xpath` uitdrukking die op `Predicate` in argument wordt gebaseerd.

### Voorbeeld van een aangepaste predicate-evaluatiemethode voor replicatiemetagegevens {#example-of-a-custom-predicate-evalutor-for-replication-metadata}

De volledige implementatie van deze `PredicateEvaluator` zou aan de volgende klasse kunnen gelijkaardig zijn.

src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

```
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.search.Predicate;
import com.day.cq.search.eval.AbstractPredicateEvaluator;
import com.day.cq.search.eval.EvaluationContext;

@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";


    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";
    static final String PN_LAST_REPLICATED = "cq:lastReplicated";
    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";
    static final String PREDICATE_SINCE = "since";
    static final String PREDICATE_SINCE_OP = " >= ";
    static final String PREDICATE_ACTION = "action";

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,
            EvaluationContext context) {

        log.debug("predicate {}", predicate);

        String date = predicate.get(PREDICATE_SINCE);
        String user = predicate.get(PREDICATE_BY);
        String action = predicate.get(PREDICATE_ACTION);

        StringBuilder sb = new StringBuilder();

        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);
            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_BY);
            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);
            sb.append(PN_LAST_REPLICATED_ACTION);
            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)-  [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/blob/master/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)
