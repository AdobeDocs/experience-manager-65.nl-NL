---
title: Sling Adapters gebruiken
seo-title: Sling Adapters gebruiken
description: Sling biedt een adapterpatroon om objecten die de Aanpasbare interface implementeren, gemakkelijk te vertalen
seo-description: Sling biedt een adapterpatroon om objecten die de Aanpasbare interface implementeren, gemakkelijk te vertalen
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
translation-type: tm+mt
source-git-commit: 95c23d29aa1dd1695ed4e541dd11c2bbc7214f75
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 0%

---


# Sling Adapters gebruiken{#using-sling-adapters}

[Sling](https://sling.apache.org) biedt een [adapterpatroon](https://sling.apache.org/site/adapters.html) aan om voorwerpen gemakkelijk te vertalen die de [Aanpasbare](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) interface uitvoeren. Deze interface biedt een algemene methode [adjustTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) die het object omzet in het klassetype dat als argument wordt doorgegeven.

Bijvoorbeeld om een voorwerp van het Middel aan het overeenkomstige voorwerp van de Knoop te vertalen, kunt u eenvoudig doen:

```java
Node node = resource.adaptTo(Node.class);
```

## Gevallen gebruiken {#use-cases}

Er zijn de volgende gebruiksgevallen:

* Hiermee krijgt u implementatiespecifieke objecten.

   Een op JCR gebaseerde implementatie van de algemene [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) interface biedt bijvoorbeeld toegang tot het onderliggende JCR [`Node`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).&quot;

* Het maken van sneltoetsen voor objecten waarvoor interne contextobjecten moeten worden doorgegeven.

   Bijvoorbeeld, op JCR-Gebaseerd [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) houdt een verwijzing naar de verzoek [`JCR Session`](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html), die beurtelings voor vele voorwerpen nodig is die op die verzoekzitting, zoals [`PageManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) of [`UserManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html)zullen werken.

* Snelkoppeling naar services.

   Een zeldzaam geval - `sling.getService()` is ook eenvoudig.

### Null-retourwaarde {#null-return-value}

`adaptTo()` kan null retourneren.

Hiervoor zijn verschillende redenen, waaronder:

* de implementatie ondersteunt het doeltype niet
* een adapterfabriek die deze zaak afhandelt, is niet actief (bijv. vanwege ontbrekende serviceverwijzingen)
* interne voorwaarde is mislukt
* service is niet beschikbaar

Het is belangrijk dat u de null-case netjes afhandelt. Voor jsp-renderingen kan het acceptabel zijn dat de jsp mislukt als dat resulteert in een leeg stuk inhoud.

### Caching {#caching}

Om prestaties te verbeteren, zijn de implementaties vrij om het voorwerp in het voorgeheugen onder te brengen dat van een `obj.adaptTo()` vraag is teruggekeerd. Als de waarde gelijk `obj` is, is het geretourneerde object hetzelfde.

Deze caching wordt uitgevoerd voor alle `AdapterFactory` gebaseerde gevallen.

Er is echter geen algemene regel: het object kan een nieuw of een bestaand object zijn. Dit betekent dat u niet op één van beide gedrag kunt vertrouwen. Daarom is het belangrijk, vooral binnen `AdapterFactory`, dat objecten in dit scenario opnieuw kunnen worden gebruikt.

### Hoe werkt het {#how-it-works}

Er zijn verschillende manieren om te `Adaptable.adaptTo()` implementeren:

* door het object zelf; het implementeren van de methode zelf en het toewijzen aan bepaalde objecten.
* Door een [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)&quot;, dat willekeurige objecten in kaart kan brengen.

   De voorwerpen moeten nog de `Adaptable` interface uitvoeren en moeten uitbreiden [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (die de `adaptTo` vraag tot een centrale adaptermanager overgaat).

   Hierdoor kunnen haken in het `adaptTo` mechanisme voor bestaande klassen, zoals `Resource`.

* Een combinatie van beide.

In het eerste geval kunnen de javadocs aangeven wat `adaptTo-targets` mogelijk is. Voor specifieke subklassen zoals de op JCR gebaseerde Resource is dit echter vaak niet mogelijk. In het laatste geval maken implementaties van `AdapterFactory` een bundel doorgaans deel uit van de klassen van het type private en worden deze dus niet weergegeven in een client-API, noch in javadocs. Theoretisch, zou het mogelijk zijn om tot alle `AdapterFactory` implementaties van [OSGi](/help/sites-deploying/configuring-osgi.md) de dienstruntime toegang te hebben en hun &quot;adaptables&quot;(bronnen en doelstellingen) configuraties te bekijken, maar niet om hen aan elkaar in kaart te brengen. Uiteindelijk hangt dit af van de interne logica, die moet worden gedocumenteerd. Vandaar deze verwijzing.

## Referentie {#reference}

### Sling {#sling}

[**Bronnen **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html)worden aangepast aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Als dit een JCR-node-based resource is of een JCR-eigenschap die verwijst naar een knooppunt.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschap</a></td>
   <td>Als dit een op JCR-eigenschap gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td>
   <td>Als dit een op JCR gebaseerde bron (knooppunt of eigenschap) is.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Kaart</a></td>
   <td>Keert een kaart van de eigenschappen terug, als dit een JCR-knoop-gebaseerd middel (of andere middel ondersteunend waardekaarten) is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Retourneert een handig te gebruiken kaart van de eigenschappen, als dit een JCR-node-based resource (of andere resource die waardekaarten ondersteunt) is. Dit kan ook (eenvoudigere) worden bereikt door gebruik te maken<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> van (Null-case, enz.).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Uitbreiding van <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> waarmee de hiërarchie van bronnen kan worden gebruikt bij het zoeken naar eigenschappen.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModisibleValueMap</a></td>
   <td>Een uitbreiding van <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, die u toestaat om eigenschappen op die knoop te wijzigen.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Hiermee wordt de binaire inhoud van een "bestand" geretourneerd<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**ResourceResolver **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html)wordt aangepast aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sessie</a></td>
   <td>De JCR-sessie van het verzoek, als dit een op JCR gebaseerde resourceoplosser is (standaardwaarde).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Gebaseerd op de zitting JCR, als dit op JCR-Gebaseerde middeloplosser is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>De UserManager biedt toegang tot en middelen om machtigbare objecten, d.w.z. gebruikers en groepen, te onderhouden. De UserManager is gebonden aan een bepaalde Zitting.
   </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Toestemming</a> </td>
   <td>De huidige gebruiker.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">Gebruiker</a><br /> </td>
   <td>De huidige gebruiker.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">ExternalAlizer</a></td>
   <td>Voor het extern maken van absolute URL's, zelfs met het aanvraagobject.<br /> </td>
  </tr>
 </tbody>
</table>

[**SlingHttpServletRequest **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html)wordt aangepast aan:

Geen doelstellingen nog, maar voert Aangepast uit en kon als bron in een douane AdapterFactory worden gebruikt.

[**SlingHttpServletResponse **](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html)wordt aangepast aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td>
   <td>Als dit een sling rewriter reactie is.</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**Pagina** wordt aangepast aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td>
   <td>Bron van de pagina.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van de pagina.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de pagina kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

**Component** wordt aangepast aan:

| [Resource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de component. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Gelabelde bron (== dit). |
| [Knooppunt](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de component. |
| ... | Alles waaraan de bron van de component kan worden aangepast. |

**Sjabloon** wordt aangepast aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Bron van de sjabloon.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van deze sjabloon.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de sjabloon kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

#### Beveiliging {#security}

**De toegelaten**, **Gebruiker** en de **Groep** passen zich aan aan:

| [Knooppunt](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Retourneert het thuisknooppunt van de gebruiker/groep. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Retourneert de replicatiestatus voor het thuisknooppunt van de gebruiker/groep. |

#### DAM {#dam}

**Activum** wordt aangepast aan:

| [Resource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Middelen van het actief. |
|---|---|
| [Knooppunt](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Node of the asset. |
| ... | Alles waaraan de middelen van het actief kunnen worden aangepast. |

#### Tags {#tagging}

**Tag** wordt aangepast aan:

| [Resource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de tag. |
|---|---|
| [Knooppunt](https://docs.adobe.com/content/docs/en/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de tag. |
| ... | Alles waaraan de bron van de tag kan worden aangepast. |

#### Overig {#other}

Daarnaast biedt Sling / JCR / OCM ook een ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` voor aangepaste OCM-objecten ([Object Content Mapping](https://jackrabbit.apache.org/object-content-mapping.html)).
