---
title: Sling Adapters
seo-title: Using Sling Adapters
description: Sling biedt een adapterpatroon om objecten die de Aanpasbare interface implementeren, gemakkelijk te vertalen
seo-description: Sling offers an Adapter pattern to conveniently translate objects that implement the Adaptable interface
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 6465e2c4-28e5-4fc8-8cca-7b632f10ba5a
source-git-commit: 2bae11eafb875f01602c39c0dba00a888e11391a
workflow-type: tm+mt
source-wordcount: '2318'
ht-degree: 0%

---

# Sling Adapters{#using-sling-adapters}

[](https://sling.apache.org) Slingaanbiedingen een  [adapterpatroon ](https://sling.apache.org/site/adapters.html) om voorwerpen gemakkelijk te vertalen die de interface  [](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) Adaptable uitvoeren. Deze interface biedt een algemene methode [adjustTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) waarmee het object wordt omgezet in het klassetype dat als argument wordt doorgegeven.

Bijvoorbeeld om een voorwerp van het Middel aan het overeenkomstige voorwerp van de Knoop te vertalen, kunt u eenvoudig doen:

```java
Node node = resource.adaptTo(Node.class);
```

## Gevallen gebruiken {#use-cases}

Er zijn de volgende gebruiksgevallen:

* Hiermee krijgt u implementatiespecifieke objecten.

   Bijvoorbeeld, verleent een op JCR-Gebaseerde implementatie van generische [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) interface toegang tot onderliggende JCR [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* Het maken van sneltoetsen voor objecten waarvoor interne contextobjecten moeten worden doorgegeven.

   Bijvoorbeeld, op JCR-Gebaseerd [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) houdt een verwijzing naar [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html) van het verzoek, die beurtelings voor vele voorwerpen nodig is die op die verzoekzitting gebaseerd zullen werken, zoals [`PageManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) of [`UserManager`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

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

Om prestaties te verbeteren, zijn de implementaties vrij om het voorwerp in het voorgeheugen onder te brengen dat van een `obj.adaptTo()` vraag is teruggekeerd. Als `obj` het zelfde is, is het teruggekeerde voorwerp het zelfde.

Deze caching wordt uitgevoerd voor alle `AdapterFactory` gebaseerde gevallen.

Er is echter geen algemene regel: het object kan een nieuw of een bestaand object zijn. Dit betekent dat u niet op één van beide gedrag kunt vertrouwen. Daarom is het belangrijk, vooral binnen `AdapterFactory`, dat de voorwerpen in dit scenario herbruikbaar zijn.

### Hoe werkt het {#how-it-works}

Er zijn verschillende manieren waarop `Adaptable.adaptTo()` kan worden geïmplementeerd:

* door het object zelf; het implementeren van de methode zelf en het toewijzen aan bepaalde objecten.
* Door een [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), die willekeurige voorwerpen in kaart kan brengen.

   De objecten moeten nog steeds de `Adaptable`-interface implementeren en [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) uitbreiden (die de `adaptTo`-aanroep aan een centrale adapterbeheerder doorgeeft).

   Hierdoor kunnen koppelingen naar het `adaptTo`-mechanisme voor bestaande klassen worden gebruikt, zoals `Resource`.

* Een combinatie van beide.

In het eerste geval kunnen de javadocs aangeven wat `adaptTo-targets` mogelijk is. Voor specifieke subklassen zoals de op JCR gebaseerde Resource is dit echter vaak niet mogelijk. In het laatste geval maken implementaties van `AdapterFactory` doorgaans deel uit van de klassen van het type private van een bundel en worden ze dus niet weergegeven in een client-API, en worden ze niet vermeld in javadocs. Theoretisch, zou het mogelijk zijn om tot alle `AdapterFactory` implementaties van [OSGi](/help/sites-deploying/configuring-osgi.md) de dienstruntime toegang te hebben en hun &quot;adaptable&quot;(bronnen en doelstellingen) configuraties te bekijken, maar niet hen aan elkaar in kaart te brengen. Uiteindelijk hangt dit af van de interne logica, die moet worden gedocumenteerd. Vandaar deze verwijzing.

## Referentie {#reference}

### Sling {#sling}

[****](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) Bron wordt aangepast aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Als dit een JCR-node-based resource is of een JCR-eigenschap die verwijst naar een knooppunt.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschap</a></td>
   <td>Als dit een op JCR-eigenschap gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td>
   <td>Als dit een op JCR gebaseerde bron (knooppunt of eigenschap) is.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">Kaart</a></td>
   <td>Keert een kaart van de eigenschappen terug, als dit een JCR-knoop-gebaseerd middel (of andere middel ondersteunend waardekaarten) is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Retourneert een handig te gebruiken kaart van de eigenschappen, als dit een JCR-node-based resource (of andere resource die waardekaarten ondersteunt) is. Kan ook (eenvoudigere) worden bereikt door <br /> <code><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> (behandelt ongeldige geval, enz.) te gebruiken.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Uitbreiding van <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> waarmee de hiërarchie van bronnen kan worden gebruikt wanneer u eigenschappen zoekt.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModisibleValueMap</a></td>
   <td>Een uitbreiding van <a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a>, die u toestaat om eigenschappen op die knoop te wijzigen.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Retourneert de binaire inhoud van een bestandsbron (als dit een op JCR-knooppunten gebaseerde bron is en het knooppunttype <code>nt:file</code> of <code>nt:resource</code> is; als dit een bundelbron is; bestandsinhoud als dit een bestandssysteembron is) of de gegevens van een binaire JCR-eigenschapbron.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Hiermee wordt een URL naar de bron geretourneerd (de URL van de gegevensopslagruimte van dit knooppunt als dit een op een JCR-knooppunt gebaseerde bron is; jar bundle URL if this is a bundle resource; bestand-URL als dit een bestandssysteembron is).</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/File.html">Bestand</a></td>
   <td>Als dit een bestandssysteembron is.</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Als deze bron een script (bijvoorbeeld jsp-bestand) is waarvoor een scriptengine is geregistreerd met sling.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/products/servlet/2.2/javadoc/javax/servlet/Servlet.html">Servlet</a></td>
   <td>Als deze bron een script (bijvoorbeeld jsp-bestand) is waarvoor een scriptengine is geregistreerd met sling of als dit een servlet-resource is.</td>
  </tr>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Double.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html"></a><br /> <a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html"></a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html">StringBooleanLongDoubleCalendarValueString[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Boolean.html">Boolean[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/lang/Long.html">Long[]</a><br /> <a href="https://java.sun.com/j2se/1.5.0/docs/api/java/util/Calendar.html">Calendar[]</a><br /> <a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Value.html">Value[]</a></td>
   <td>Retourneert de waarde(n) als dit een JCR-eigenschap-gebaseerde resource is (en de value-fit).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Als dit een op JCR-knooppunten gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html">Pagina</a></td>
   <td>Als dit een JCR-node-based resource is en het knooppunt een <code>cq:Page</code> (of <code>cq:PseudoPage</code>) is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html">Component</a></td>
   <td>Als dit een <code>cq:Component</code> knoopmiddel is.</td>
  </tr>  
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Design.html">Ontwerp</a></td>
   <td>Als dit een ontwerpknooppunt is (<code>cq:Page</code>).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html">Sjabloonmodel</a></td>
   <td>Als dit een <code>cq:Template</code> knoopmiddel is.</td>
  </tr>  
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blauwdruk</a></td>
   <td>Als dit een <code>cq:Template</code> knoopmiddel is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html">Element</a></td>
   <td>Als dit een dam:Middelen van de knoop van Activa is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Rendition.html">Vertoning</a></td>
   <td>Als dit een dam is:Vertoning van activa (nt:dossier onder de vertoningsomslag van een dam:Assert)</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Als dit een <code>cq:Tag</code> knoopmiddel is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Gebaseerd op de zitting JCR als dit een op JCR-Gebaseerde middel is en de gebruiker toestemmingen heeft om tot UserManager toegang te hebben.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Toestemming</a></td>
   <td>Autorisable is de gemeenschappelijke basisinterface voor Gebruiker en Groep.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">Gebruiker</a></td>
   <td>De gebruiker is een speciale Authorizable die voor authentiek en kan worden verklaard.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Zoekt onder de bron (of gebruik setSearchIn()) als dit een op JCR gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflowstatus voor het opgegeven payload-knooppunt voor de pagina/workflow.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replicatiestatus voor de opgegeven resource of het JCR:content-subknooppunt (eerst ingeschakeld).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Retourneert een aangepaste connectorbron voor bepaalde typen als dit een op JCR-knooppunten gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Als dit een <code>cq:ContentSyncConfig</code> knoopmiddel is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Als dit onder een <code>cq:ContentSyncConfig</code> knoopmiddel is.</td>
  </tr>
 </tbody>
</table>

[****](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) ResourceResolveradapts aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">Sessie</a></td>
   <td>De JCR-sessie van het verzoek, als dit een op JCR gebaseerde resourceoplosser is (standaardwaarde).</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Gebaseerd op de zitting JCR, als dit op JCR-Gebaseerde middeloplosser is.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
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
   <td>Voor het externaliseren van absolute URLs, zelfs met uit het verzoekvoorwerp.<br /> </td>
  </tr>
 </tbody>
</table>

[****](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) SlingHttpServletRequestadapts aan:

Geen doelstellingen nog, maar voert Aangepast uit en kon als bron in een douane AdapterFactory worden gebruikt.

[****](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) SlingHttpServletResponse past zich aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br />  (XML)</td>
   <td>Als dit een sling rewriter reactie is.</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**[](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html)** Pagina-aanpassingen aan:

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
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van de pagina.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de pagina kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

**[](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html)** Componenten worden aangepast aan:

| [Resource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de component. |
|---|---|
| [LabeledResource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | Gelabelde bron (== dit). |
| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de component. |
| ... | Alles waaraan de bron van de component kan worden aangepast. |

**[](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html)** Temperaturen aanpassen aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Bron van de sjabloon.</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron (== dit).</td>
  </tr>
  <tr>
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van deze sjabloon.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de sjabloon kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

#### Beveiliging {#security}

**Toegestane**,  **** gebruikers en  **** groepen passen zich aan:

| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Retourneert het thuisknooppunt van de gebruiker/groep. |
|---|---|
| [ReplicationStatus](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | Retourneert de replicatiestatus voor het thuisknooppunt van de gebruiker/groep. |

#### DAM {#dam}

**** Elementen aanpassen aan:

| [Resource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Middelen van het actief. |
|---|---|
| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Node of the asset. |
| ... | Alles waaraan de middelen van het actief kunnen worden aangepast. |

#### Tags {#tagging}

**** Tags aanpassen aan:

| [Resource](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de tag. |
|---|---|
| [Knooppunt](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de tag. |
| ... | Alles waaraan de bron van de tag kan worden aangepast. |

#### Overig {#other}

Daarnaast biedt Sling / JCR / OCM ook een ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` voor aangepaste OCM-objecten ([Objectinhoudtoewijzing](https://jackrabbit.apache.org/object-content-mapping.html)).
