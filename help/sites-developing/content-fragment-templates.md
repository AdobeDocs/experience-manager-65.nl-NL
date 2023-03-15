---
title: Sjablonen voor inhoudsfragmenten
seo-title: Content Fragment Templates
description: Sjablonen worden geselecteerd wanneer u een inhoudsfragment maakt en bieden het nieuwe fragment de basisstructuur, het basiselement en de variatie
seo-description: Templates are selected when creating a content fragmen and provide the new fragment with the basic structure, element, and variation
uuid: d147bac8-b710-40ed-9664-decb5ffcf8e7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: a975ea2e-5e24-4a96-bd62-63bb98836ff2
docset: aem65
exl-id: 1b75721c-b223-41f0-88d9-bd855b529f31
source-git-commit: a2b1bd5462ae1837470e31cfeb87a95af1c69be5
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 4%

---

# Sjablonen voor inhoudsfragmenten{#content-fragment-templates}

>[!CAUTION]
>
>[Inhoudsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) worden aanbevolen voor het maken van alle nieuwe inhoudsfragmenten.
>
>Inhoudsfragmentmodellen worden voor alle voorbeelden in WKND gebruikt.

>[!NOTE]
>
>Voorafgaand aan AEM 6.3 werden de Fragments van de Inhoud gecreeerd gebaseerd op malplaatjes in plaats van modellen.
>
>Sjablonen voor inhoudsfragmenten zijn nu afgekeurd. Ze kunnen nog steeds worden gebruikt voor het maken van fragmenten, maar het gebruik van Content Fragment Models wordt aangeraden. Er worden geen nieuwe functies toegevoegd aan fragmentsjablonen en deze worden in een toekomstige versie verwijderd.

Sjablonen worden geselecteerd wanneer u een inhoudsfragment maakt. Ze bieden het nieuwe fragment de basisstructuur, elementen en variatie. De sjablonen die voor inhoudsfragmenten worden gebruikt, zijn afhankelijk van de Granite Configuration Manager.

De out-of-the-box sjablonen worden bewaard onder:

* `/libs/settings/dam/cfm/templates`

U kunt uw sitespecifieke sjablonen voor inhoudsfragmenten maken onder:

* `/apps/settings/dam/cfm/templates`
De locatie voor het bedekken van out-of-the-box sjablonen of het aanbieden van klantspecifieke, toepassingsbrede sjablonen die niet bedoeld zijn om tijdens runtime te worden uitgebreid/gewijzigd.

* `/conf/global/settings/dam/cfm/templates`
De locatie voor klantspecifieke sjablonen die voor de hele organisatie moeten worden gewijzigd tijdens runtime.

De rangorde is (in aflopende volgorde) `/conf`, `/apps`, `/libs`.

>[!CAUTION]
>
>U ***moet*** niets wijzigen in de `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (bijvoorbeeld zoals het bestaat in `/libs`) onder `/apps`
>
>1. Breng wijzigingen aan in `/apps`

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

* **Sjabloonmodel**

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
     <td>De titel van de sjabloon (weergegeven in de <strong>Fragment maken</strong> wizard).</td>
    </tr>
    <tr>
     <td><code>jcr:description</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> </td>
     <td>Een tekst die het doel van de sjabloon beschrijft (weergegeven in het dialoogvenster <strong>Fragment maken</strong> wizard).</td>
    </tr>
    <tr>
     <td><code>initialAssociatedContent</code></td>
     <td><p><code>String[]</code></p> <p>optioneel</p> </td>
     <td>Een array met paden naar verzamelingen die standaard aan een nieuw gemaakt inhoudsfragment moeten worden gekoppeld.</td>
    </tr>
    <tr>
     <td><code>precreateElements</code></td>
     <td><p><code>Boolean</code></p> <p>required</p> </td>
     <td><p><code>true</code>, als de subassets die de elementen (behalve het master element) van het inhoudsfragment vertegenwoordigen, moeten worden gemaakt wanneer het inhoudsfragment wordt gemaakt; <em>false</em> als ze "ter plekke" moeten worden gemaakt.</p> <p><strong>Opmerking</strong>: momenteel moet deze parameter worden ingesteld op <code>true</code>.</p> </td>
    </tr>
    <tr>
     <td><code>version</code></td>
     <td><p><code>Long</code></p> <p>required</p> </td>
     <td><p>Versie van de inhoudsstructuur; momenteel ondersteund:</p> <p><strong>Opmerking</strong>: momenteel moet deze parameter worden ingesteld op <code>2</code>.<br /> </p> </td>
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
     <td><code>elements</code> </td>
     <td><p><code>nt:unstructured</code></p> <p>required</p> </td>
     <td><p>Knooppunt dat de definitie van de elementen van het inhoudsfragment bevat. Het is verplicht en moet ten minste één onderliggend knooppunt voor het <strong>Hoofd</strong> element, but can contain [1..n] onderliggende knooppunten.</p> <p>Wanneer de sjabloon wordt gebruikt, wordt de elementensubvertakking gekopieerd naar de modelsubvertakking van het fragment.</p> <p>Het eerste element (zoals weergegeven in CRXDE Lite) wordt automatisch beschouwd als het eerste element <i>hoofd</i> element; de knooppuntnaam is irrelevant en het knooppunt zelf heeft geen speciale betekenis, afgezien van het feit dat het wordt vertegenwoordigd door het hoofdactief; de overige elementen worden behandeld als subactiva.</p> </td>
    </tr>
   </tbody>
  </table>

* **Elementnaam**

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
     <td><p><code>String</code></p> <p>required</p> </td>
     <td>De titel van het element (wordt weergegeven in de elementenkiezer van de fragmenteditor).</td>
    </tr>
    <tr>
     <td><code>defaultContent</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: ""</p> </td>
     <td>de initiële inhoud van het element; alleen worden gebruikt als <code>precreateElements</code><i> = </i><code>true</code></td>
    </tr>
    <tr>
     <td><code>initialContentType</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: <code>text/html</code></p> </td>
     <td><p>Eerste inhoudstype van het element; alleen worden gebruikt als <code>precreateElements</code><i> = </i><code>true</code>; momenteel ondersteund:</p>
      <ul>
       <li><code>text/html</code></li>
       <li><code>text/plain</code></li>
       <li><code>text/x-markdown</code></li>
      </ul> </td>
    </tr>
    <tr>
     <td><code>name</code></td>
     <td><p><code>String</code></p> <p>required</p> </td>
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
     <td><code>variations</code> </td>
     <td><p><code>nt:unstructured</code></p> <p>optioneel</p> </td>
     <td>Dit optionele knooppunt bevat de definitie van de initiële variaties van het inhoudsfragment.</td>
    </tr>
   </tbody>
  </table>

* **Naam variatie**

   <table>
   <tbody>
    <tr>
     <th>Naam</th>
     <th>Type</th>
     <th>Waarde</th>
    </tr>
    <tr>
     <td><code>&lt;<i>variation-name</i>&gt;</code> </td>
     <td><p><code>nt:unstructured</code></p> <p>vereist als er een variatieknooppunt aanwezig is</p> </td>
     <td><p>Definieert een oorspronkelijke variatie.<br /> De variatie wordt standaard toegevoegd aan alle elementen van het inhoudsfragment.</p> <p>De wijziging heeft dezelfde initiële inhoud als het betreffende element (zie <code class="code">defaultContent/
       initialContentType</code>)</p> </td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>required</p> </td>
     <td>De titel van de variatie (weergegeven in de fragmenteditor) <strong>Variatie</strong> tab (linkerspoor).</td>
    </tr>
    <tr>
     <td><code>jcr:desciption</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: ""</p> </td>
     <td>Een tekst die een beschrijving van de wijziging bevat <span>(weergegeven in de <strong>Variatie</strong> tab (linkerspoor).</code></td>
    </tr>
   </tbody>
  </table>
