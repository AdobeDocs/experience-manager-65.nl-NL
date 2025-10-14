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

De capaciteit voor een lid van de Gemeenschap om [&#x200B; activiteiten &#x200B;](essentials-activities.md) te volgen en te worden gevolgd wordt gevestigd door twee componenten:

De `following` component moet met een ander middel worden geassocieerd, en deze vereniging is reeds gevestigd voor bestaande leden van Gemeenschappen en eigenschappen in a [&#x200B; communautaire plaats &#x200B;](overview.md#communitiessites).

De component `following` bevat een lijst met de leden die het huidige lid volgen of die door het huidige lid worden gevolgd. Deze sociale grafiek van de relaties tussen leden is opgenomen in het gebruikersprofiel dat voor een site van een community is ingesteld.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

### volgende {#following}

<table>
 <tbody>
  <tr>
   <td> <strong> resourceType </strong></td>
   <td>sociale/sociale grafiek/componenten/hbs/relaties</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong> inbegrepen </strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong> clientllibs </strong></a></td>
   <td>cq.social.hbs.socialgraph</td>
  </tr>
  <tr>
   <td> <strong> malplaatjes </strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td>
  </tr>
  <tr>
   <td> <strong> css </strong></td>
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="socialgraph.md"> Gebruikend Sociale Grafiek </a></td>
  </tr>
  <tr>
   <td><strong> optional <br /> property</strong></td>
   <td>
    <ul>
     <li>Naam: <strong><code>outgoing</code></strong></li>
     <li>Type: Boolean</li>
     <li>Waarde:<br />
      <ul>
       <li><i> True </i> - De component <code>following</code> geeft een lijst weer van de leden die het lid met aanmelding <code>follows</code></li>
       <li><i> Vals </i> - de <code>following</code> component maakt een lijst van de leden die <code>follow </code> het ondertekende-binnen lid </li>
      </ul> </li>
    </ul> <p>De gebreken aan <i> waar </i> als het bezit mist. Het is niet mogelijk om deze eigenschap in te stellen in het dialoogvenster Bewerken in de modus Auteur. Het bezit moet aan een geval van de <code>following</code> knoop worden toegevoegd door <a href="../../help/sites-developing/developing-with-crxde-lite.md"> CRXDE te gebruiken|Lite </a>.</p> </td>
  </tr>
 </tbody>
</table>

### Volgen {#follow}

| **resourceType** | `social/socialgraph/components/hbs/following` |
|---|---|
| [**inbegrepen**](scf.md#add-or-include-a-communities-component) | Nee |
| **malplaatjes** | `/libs/social/socialgraph/components/hbs/following/following.hbs` |
| **css** | `/libs/social/socialgraph/components/hbs/following/clientlibs/following.css` |

* [Aanpassingen aan de clientzijde](client-customize.md)

## Essentiële elementen voor server-side {#essentials-for-server-side}

* [&#x200B; Sociale Grafiek API &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [&#x200B; Sociale Eindpunten van de Grafiek &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Aanpassingen op de server](server-customize.md)
