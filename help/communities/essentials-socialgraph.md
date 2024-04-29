---
title: Grondbeginselen van sociale grafiek
description: Leer over de grondbeginselen van Sociale Grafiek door de volgende en volgcomponenten op een communautaire plaats te gebruiken.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: c037a788-c943-4f95-a028-1fcb0ef48f86
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Grondbeginselen van sociale grafiek  {#social-graph-essentials}

Het vermogen van een lid van de Gemeenschap om [activiteiten](essentials-activities.md) en moet worden gevolgd door twee componenten:

De `following` moet worden gekoppeld aan een andere bron, en deze associatie is reeds opgericht voor bestaande leden van de Gemeenschappen en kenmerken in een [community-site](overview.md#communitiessites).

De `following` de component maakt een lijst van de leden die of het huidige lid volgen of door het huidige lid worden gevolgd. Deze sociale grafiek van de relaties tussen leden is opgenomen in het gebruikersprofiel dat voor een site van een community is ingesteld.

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
   <td> <strong>sjablonen</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="socialgraph.md">Sociale grafiek gebruiken</a></td>
  </tr>
  <tr>
   <td><strong> optioneel<br /> eigenschap</strong></td>
   <td>
    <ul>
     <li>Naam: <strong><code>outgoing</code></strong></li>
     <li>Type: Boolean</li>
     <li>Waarde:<br />
      <ul>
       <li><i>Waar </i>- de <code>following</code> de component maakt een lijst van de leden die het ondertekende in lid <code>follows</code></li>
       <li><i>Onwaar </i>- de <code>following</code> de component maakt een lijst van de leden die <code>follow </code>het aangemeld lid</li>
      </ul> </li>
    </ul> <p>Standaardwaarden: <i>true</i> als de eigenschap ontbreekt. Het is niet mogelijk om deze eigenschap in te stellen in het dialoogvenster Bewerken in de modus Auteur. De eigenschap moet worden toegevoegd aan een instantie van de <code>following</code> knoop door te gebruiken <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td>
  </tr>
 </tbody>
</table>

### Volgen {#follow}

| **resourceType** | `social/socialgraph/components/hbs/following` |
|---|---|
| [**inclusief**](scf.md#add-or-include-a-communities-component) | Nee |
| **sjablonen** | `/libs/social/socialgraph/components/hbs/following/following.hbs` |
| **css** | `/libs/social/socialgraph/components/hbs/following/clientlibs/following.css` |

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [Sociale grafiek-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Eindpunten sociale grafiek](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Aanpassingen op de server](server-customize.md)
