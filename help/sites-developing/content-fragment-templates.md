---
title: Sjablonen voor inhoudsfragmenten
description: Sjablonen worden geselecteerd wanneer u een inhoudsfragment maakt en bieden het nieuwe fragment de basisstructuur, het basiselement en de variatie
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: 1b75721c-b223-41f0-88d9-bd855b529f31
solution: Experience Manager, Experience Manager Sites
feature: Developing,Content Fragments
role: Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 0%

---

# Sjablonen voor inhoudsfragmenten{#content-fragment-templates}

>[!CAUTION]
>
>[ de fragmentmodellen van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) worden geadviseerd voor het creëren van alle nieuwe inhoudsfragmenten.
>
>Inhoudsfragmentmodellen worden voor alle voorbeelden in WKND gebruikt.

>[!NOTE]
>
>Voorafgaand aan AEM 6.3 werden de Fragments van de Inhoud gecreeerd gebaseerd op malplaatjes in plaats van modellen.
>
>Sjablonen voor inhoudsfragmenten zijn nu afgekeurd. Ze kunnen nog steeds worden gebruikt voor het maken van fragmenten, maar het gebruik van Content Fragment Models wordt aangeraden. Er worden geen nieuwe functies toegevoegd aan fragmentsjablonen en deze worden in een toekomstige versie verwijderd.

Sjablonen worden geselecteerd wanneer u een inhoudsfragment maakt. Zij verstrekken het nieuwe fragment de basisstructuur, element(en) en variatie. De sjablonen die voor inhoudsfragmenten worden gebruikt, zijn afhankelijk van de Granite Configuration Manager.

De out-of-the-box sjablonen worden bewaard onder:

* `/libs/settings/dam/cfm/templates`

U kunt uw sitespecifieke sjablonen voor inhoudsfragmenten maken onder:

* `/apps/settings/dam/cfm/templates`
De locatie voor het bedekken van out-of-the-box sjablonen of het aanbieden van klantspecifieke, toepassingsbrede sjablonen die niet bedoeld zijn om tijdens runtime te worden uitgebreid/gewijzigd.

* `/conf/global/settings/dam/cfm/templates`
De locatie voor klantspecifieke sjablonen die voor de hele organisatie moeten worden gewijzigd tijdens runtime.

De prioriteitsvolgorde is (in aflopende volgorde) `/conf` , `/apps` , `/libs` .

>[!CAUTION]
>
>U ***moet*** niets in de `/libs` weg veranderen.
>
>De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie wordt overschreven (en dat deze inhoud ook kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
>
>1. Breng eventuele wijzigingen aan binnen `/apps`
>

De basisstructuur van een template wordt aangehouden onder:

```xml
conf
  global
    settings
      dam
        cfm
          templates
            <template-name>
              ...
```

Met de specifieke structuur:

```xml
+ <template-name>
    - jcr:primaryType
    - jcr:title
    - jcr:description
    - initialAssociatedContent
    - precreateElements
    - version
    + elements
        - jcr:primaryType
        + <element-name>
            - jcr:primaryType
            - jcr:title
            - defaultContent
            - initialContentType
            - name
        ... + other element definitions
    + variations
        - jcr:primaryType
        + <variation-name>
            - jcr:primaryType
            - jcr:title
            - jcr:description
            - name
        ... + other variation definitions
```

Meer details over de knopen en hun eigenschappen zijn:

* **Malplaatje**

  <table>
   <tbody>
    <tr>
     <th>Naam</th>
     <th>Type</th>
     <th>Waarde</th>
    </tr>
    <tr>
     <td><code>&lt;<em>template-name</em>&gt;</code></td>
     <td><code>nt:unstructured</code></td>
     <td>Dit knooppunt is de basis voor elke sjabloon. Het is verplicht en moet een unieke naam hebben.</td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>required<br /> </p> </td>
     <td>De titel van het malplaatje (dat in <strong> wordt getoond leidt tot de tovenaar van het Fragment </strong>).</td>
    </tr>
    <tr>
     <td><code>jcr:description</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> </td>
     <td>Een tekst die het doel van het malplaatje beschrijft (getoond in <strong> creeer de tovenaar van het Fragment </strong>).</td>
    </tr>
    <tr>
     <td><code>initialAssociatedContent</code></td>
     <td><p><code>String[]</code></p> <p>optioneel</p> </td>
     <td>Een array met paden naar verzamelingen die standaard aan een nieuw gemaakt inhoudsfragment moeten worden gekoppeld.</td>
    </tr>
    <tr>
     <td><code>precreateElements</code></td>
     <td><p><code>Boolean</code></p> <p>vereist</p> </td>
     <td><p><code>true</code>, als subassets die de elementen (behalve het hoofdelement) van het inhoudsfragment vertegenwoordigen zouden moeten worden gecreeerd wanneer het inhoudsfragment wordt gecreeerd; <em> vals </em> als zij "op de vlucht"zouden moeten worden gecreeerd.</p> <p><strong> Nota </strong>: momenteel moet deze parameter aan <code>true</code> worden geplaatst.</p> </td>
    </tr>
    <tr>
     <td><code>version</code></td>
     <td><p><code>Long</code></p> <p>vereist</p> </td>
     <td><p>Versie van de inhoudsstructuur; momenteel ondersteund:</p> <p><strong> Nota </strong>: momenteel moet deze parameter aan <code>2</code> worden geplaatst.<br /> </p> </td>
    </tr>
   </tbody>
  </table>

* **Elementen**

  <table>
   <tbody>
    <tr>
     <th>Naam</th>
     <th>Type</th>
     <th>Waarde</th>
    </tr>
    <tr>
     <td><code>elements</code><br /> </td>
     <td><p><code>nt:unstructured</code></p> <p>vereist</p> </td>
     <td><p>Knooppunt dat de definitie van de elementen van het inhoudsfragment bevat. Het is verplicht en moet minstens één kindknoop voor het <strong> Belangrijkste </strong> element bevatten, maar kan [1.. bevatten.n] onderliggende knooppunten.</p> <p>Wanneer de sjabloon wordt gebruikt, wordt de elementensubvertakking gekopieerd naar de modelsubvertakking van het fragment.</p> <p>Het eerste element (zoals die in CRXDE Lite wordt bekeken) wordt automatisch beschouwd als om het <i> belangrijkste </i> element; de knoopnaam is irrelevant en de knoop zelf heeft geen speciale betekenis, behalve het feit dat het door het belangrijkste activa wordt vertegenwoordigd; de andere elementen worden behandeld als subactiva.</p> </td>
    </tr>
   </tbody>
  </table>

* **Naam van het Element**

  <table>
   <tbody>
    <tr>
     <th>Naam</th>
     <th>Type</th>
     <th>Waarde</th>
    </tr>
    <tr>
     <td><code>&lt;<i>element-name</i>&gt;</code></td>
     <td><code>nt:unstructured</code></td>
     <td>Dit knooppunt definieert een element. Het is verplicht en moet een unieke naam hebben.</td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>vereist</p> </td>
     <td>De titel van het element (wordt weergegeven in de elementenkiezer van de fragmenteditor).</td>
    </tr>
    <tr>
     <td><code>defaultContent</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: ""</p> </td>
     <td>Oorspronkelijke inhoud van het element; wordt alleen gebruikt als <code>precreateElements</code><i> = </i><code>true</code></td>
    </tr>
    <tr>
     <td><code>initialContentType</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>standaard: <code>text/html</code></p> </td>
     <td><p>Oorspronkelijk inhoudstype van het element; alleen gebruikt als <code>precreateElements</code><i> = </i><code>true</code>; momenteel ondersteund:</p>
      <ul>
       <li><code>text/html</code></li>
       <li><code>text/plain</code></li>
       <li><code>text/x-markdown</code></li>
      </ul> </td>
    </tr>
    <tr>
     <td><code>name</code></td>
     <td><p><code>String</code></p> <p>vereist</p> </td>
     <td>De interne naam van het element; moet uniek zijn voor het fragmenttype.</td>
    </tr>
   </tbody>
  </table>

* **Variaties**

  <table>
   <tbody>
    <tr>
     <th>Naam</th>
     <th>Type</th>
     <th>Waarde</th>
    </tr>
    <tr>
     <td><code>variations</code><br /> </td>
     <td><p><code>nt:unstructured</code></p> <p>optioneel</p> </td>
     <td>Dit optionele knooppunt bevat de definitie van de initiële variaties van het inhoudsfragment.</td>
    </tr>
   </tbody>
  </table>

* **de Naam van de Variatie**

  <table>
   <tbody>
    <tr>
     <th>Naam</th>
     <th>Type</th>
     <th>Waarde</th>
    </tr>
    <tr>
     <td><code>&lt;<i>variation-name</i>&gt;</code><br /> </td>
     <td><p><code>nt:unstructured</code></p> <p>vereist als er een variatieknooppunt aanwezig is</p> </td>
     <td><p>Definieert een oorspronkelijke variatie.<br /> De variatie wordt standaard toegevoegd aan alle elementen van het inhoudsfragment.</p> <p>De variatie zal de zelfde aanvankelijke inhoud hebben zoals het respectieve element (zie <code class="code">defaultContent/
       initialContentType</code>)</p> </td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>vereist</p> </td>
     <td>De titel van de variatie (die in het 0} wordt getoond van de fragmentredacteur {</strong> lusje van de Variatie (linkerspoor)).<strong></td>
    </tr>
    <tr>
     <td><code>jcr:desciption</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: ""</p> </td>
     <td>Een tekst die een beschrijving van de variatie <span> (getoond in het 1} Verandering </strong> lusje van de fragmentredacteur (linkerspoor)) verstrekt.<strong></code></td>
    </tr>
   </tbody>
  </table>
