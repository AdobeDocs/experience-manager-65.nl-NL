---
title: Grondbeginselen van sociale grafiek
seo-title: Grondbeginselen van sociale grafiek
description: component volgen en volgende componentenoverzicht volgen
seo-description: component volgen en volgende componentenoverzicht volgen
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Grondbeginselen van sociale grafiek {#social-graph-essentials}

De mogelijkheid voor een lid van de Gemeenschap om [activiteiten](essentials-activities.md) te volgen en te volgen, wordt vastgesteld door middel van twee componenten:

De `follow`component moet met een andere bron worden geassocieerd, en deze vereniging is reeds gevestigd voor bestaande leden van de Gemeenschappen en eigenschappen op een [communautaire plaats](overview.md#communitiessites).

De `following`component maakt een lijst van de leden die of het huidige lid volgen of door het huidige lid worden gevolgd. Deze sociale grafiek van de relaties tussen leden is opgenomen in het gebruikersprofiel dat voor een site van een community is ingesteld.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

### volgende {#following}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>sociale/sociale grafiek/componenten/hbs/relaties</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.hbs.socialgraph</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie Sociale grafiek <a href="socialgraph.md">gebruiken</a></td>
  </tr>
  <tr>
   <td><strong> optionele<br /> eigenschap</strong></td>
   <td>
    <ul>
     <li>Naam: <strong><code>outgoing</code></strong></li>
     <li>Type:Boolean</li>
     <li>Waarde:<br />
      <ul>
       <li><i>true </i>- in de <code>following</code> component worden de leden weergegeven die het momenteel aangemelde lid zijn <code>follows</code></li>
       <li><i>false </i>- de <code>following</code> component geeft een lijst weer van de leden die <code>follow </code>het momenteel aangemelde lid zijn</li>
      </ul> </li>
    </ul> <p>De standaardwaarde is <i>true</i> als de eigenschap ontbreekt. Momenteel is het niet mogelijk om deze eigenschap in te stellen in het dialoogvenster Bewerken in de modus Schrijver. De eigenschap moet aan een instantie van het <code>following </code>knooppunt worden toegevoegd met <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td>
  </tr>
 </tbody>
</table>

### Volg {#follow}

| **resourceType** | sociale/sociale grafiek/componenten/hbs/volgende |
|---|---|
| [**inclusief **](scf.md#add-or-include-a-communities-component) | Nee |
| **templates** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Sociale grafiek-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Eindpunten sociale grafiek](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Aanpassingen op de server](server-customize.md)

