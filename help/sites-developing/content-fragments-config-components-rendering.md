---
title: Inhoudsfragmenten die componenten voor rendering configureren
seo-title: Inhoudsfragmenten die componenten voor rendering configureren
description: Inhoudsfragmenten die componenten voor rendering configureren
seo-description: Inhoudsfragmenten die componenten voor rendering configureren
uuid: 3f5aaf36-e6a7-4a3c-b305-e35ebcc98d0d
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 2aef9048-9d6e-4f5d-b443-5e73f8066d76
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Inhoudsfragmenten die componenten voor rendering configureren{#content-fragments-configuring-components-for-rendering}

Er zijn verschillende [geavanceerde services](/help/sites-developing/content-fragments-config-components-rendering.md#definition-of-advanced-services-that-need-configuration) voor het renderen van inhoudsfragmenten. Om deze diensten te gebruiken, moeten de middeltypes van dergelijke componenten zich aan het kader van inhoudsfragmenten bekendmaken.

Dit wordt gedaan door de Dienst [te vormen OSGi - de Configuratie](#osgi-service-content-fragment-component-configuration)van de Component van het Fragment van de Inhoud.

>[!CAUTION]
>
>Als u de hieronder beschreven [geavanceerde services](/help/sites-developing/content-fragments-config-components-rendering.md#definition-of-advanced-services-that-need-configuration) niet nodig hebt, kunt u deze configuratie negeren.

>[!CAUTION]
>
>Wanneer u de uit-van-de-doos component(en) uitbreidt of gebruikt, wordt het niet aanbevolen om de configuratie te wijzigen.

>[!CAUTION]
>
>U kunt een geheel nieuwe component schrijven die alleen de API voor inhoudsfragmenten gebruikt, zonder geavanceerde services. In een dergelijk geval moet u de component echter zodanig ontwikkelen dat deze de juiste verwerking afhandelt.
>
>Daarom wordt aanbevolen de kerncomponenten te gebruiken.

## Definitie van de Geavanceerde Diensten die Configuratie vereisen {#definition-of-advanced-services-that-need-configuration}

De diensten die de registratie van een component vereisen zijn:

* De afhankelijkheden correct bepalen tijdens de publicatie (zorg er dus voor dat fragmenten en modellen automatisch met een pagina kunnen worden gepubliceerd als ze zijn gewijzigd sinds de laatste publicatie).
* Ondersteuning voor inhoudsfragmenten in volledige tekstzoekopdracht.
* Het beheer/de afhandeling van *tussen inhoud.*
* Beheer/verwerking van *gemengde media-elementen.*
* Dispatcher flush for referenced fragments (if a page containing a fragment is re-published).
* Op alinea&#39;s gebaseerde rendering gebruiken.

Als u een of meer van deze functies nodig hebt, is het (doorgaans) eenvoudiger om de functie uit de doos te gebruiken in plaats van deze vanaf nul te ontwikkelen.

## OSGi Service - Configuratie van de Component van het Fragment van de Inhoud {#osgi-service-content-fragment-component-configuration}

De configuratie moet aan de Configuratie **van de Component van het Fragment van de Component van de** Inhoud worden gebonden OSGi:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

>[!NOTE]
>
>Zie [het Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor verdere details.

Bijvoorbeeld:

![cfm-01](assets/cfm-01.png)

De configuratie OSGi is:

<table>
 <tbody>
  <tr>
   <td>Label</td>
   <td>OSGi-configuratie<br /> </td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td><strong>Het type Resource</strong></td>
   <td><code>dam.cfm.component.resourceType</code></td>
   <td>Het type bron dat moet worden geregistreerd;bijv. <br /> <p><span class="cmp-examples-demo__property-value"><code>core/wcm/components/contentfragment/v1/contentfragment</code></code></p> </td>
  </tr>
  <tr>
   <td><strong>Verwijzing, eigenschap</strong></td>
   <td><code>dam.cfm.component.fileReferenceProp</code></td>
   <td>De naam van de eigenschap die de verwijzing naar het fragment bevat; bijv. <code>fragmentPath</code> of <code>fileReference</code></td>
  </tr>
  <tr>
   <td><strong>Element(en), eigenschap</strong></td>
   <td><code>dam.cfm.component.elementsProp</code></td>
   <td>De naam van de eigenschap die de naam of namen bevat van het element of de elementen die moeten worden gerenderd;bijv.<code>elementName</code></td>
  </tr>
  <tr>
   <td><strong>Variatie, eigenschap</strong><br /> </td>
   <td><code>dam.cfm.component.variationProp</code></td>
   <td>De naam van de eigenschap die de naam bevat van de wijziging die moet worden gerenderd;bijv.<code>variationName</code></td>
  </tr>
 </tbody>
</table>

Voor bepaalde functionaliteit (bijvoorbeeld om alleen een alineabereik te renderen) moet u zich aan een aantal conventies houden:

<table>
 <tbody>
  <tr>
   <td>Eigenschapnaam</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td><code>paragraphRange</code></td>
   <td><p>Een tekenreekseigenschap die het bereik definieert van alinea's die moeten worden uitgevoerd in de rendermodus <em>van</em>één element.</p> <p>Format:</p>
    <ul>
     <li><code>1</code> of <code>1-3</code> of <code>1-3;6;7-8</code> of <code>*-3;5-*</code></li>
     <li>alleen geëvalueerd als <code>paragraphScope</code> is ingesteld op <code>range</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphScope</code></td>
   <td><p>Een tekenreekseigenschap die definieert hoe alinea's moeten worden uitgevoerd als <em>één element wordt gerenderd</em>.</p> <p>Waarden:</p>
    <ul>
     <li><code>all</code> : om alle alinea's te renderen</li>
     <li><code>range</code> : om het bereik van alinea's te bepalen dat wordt verschaft door <code>paragraphRange</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><code>paragraphHeadings</code></td>
   <td>Een Booleaanse eigenschap die definieert of koppen (bijvoorbeeld <code>h1</code>, <code>h2</code>, <code>h3</code>) worden geteld als alinea's (<code>true</code>) of niet (<code>false</code>)</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Dit kan veranderen in latere 6,5 mijlpalen.

## Voorbeeld {#example}

Zie het volgende voorbeeld (bij een AEM-instantie buiten de box):

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config
```

Dit bevat:

```
dam.cfm.component.resourceType="core/wcm/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```

