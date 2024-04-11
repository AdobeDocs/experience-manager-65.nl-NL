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
>[Inhoudsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) worden aanbevolen voor het maken van alle nieuwe inhoudsfragmenten.
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

De rangorde is (in aflopende volgorde) `/conf`, `/apps`, `/libs`.

>[!CAUTION]
>
>U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het bestaat in `/libs`) onder `/apps`
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

* **Sjabloon**

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
     <td><p><code>String</code></p> <p>vereist<br /> </p> </td>
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
     <td><p><code>Boolean</code></p> <p>vereist</p> </td>
     <td><p><code>true</code>, als de subelementen die de elementen (behalve het hoofdelement) van het inhoudsfragment vertegenwoordigen, moeten worden gemaakt wanneer het inhoudsfragment wordt gemaakt; <em>false</em> als ze "ter plekke" moeten worden gemaakt.</p> <p><strong>Opmerking</strong>: momenteel moet deze parameter worden ingesteld op <code>true</code>.</p> </td>
    </tr>
    <tr>
     <td><code>version</code></td>
     <td><p><code>Long</code></p> <p>vereist</p> </td>
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
     <td><code>elements</code><br /> </td>
     <td><p><code>nt:unstructured</code></p> <p>vereist</p> </td>
     <td><p>Knooppunt dat de definitie van de elementen van het inhoudsfragment bevat. Het is verplicht en moet ten minste één onderliggend knooppunt voor het <strong>Hoofd</strong> element, but can contain [1..n] onderliggende knooppunten.</p> <p>Wanneer de sjabloon wordt gebruikt, wordt de elementensubvertakking gekopieerd naar de modelsubvertakking van het fragment.</p> <p>Het eerste element (zoals weergegeven in CRXDE Lite) wordt automatisch beschouwd als het <i>hoofd</i> element; de knooppuntnaam is irrelevant en de knoop zelf heeft geen speciale betekenis, behalve het feit dat het door het belangrijkste actief wordt vertegenwoordigd; de andere elementen worden behandeld als subactiva.</p> </td>
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
     <td><p><code>String</code></p> <p>vereist</p> </td>
     <td>De titel van het element (wordt weergegeven in de elementenkiezer van de fragmenteditor).</td>
    </tr>
    <tr>
     <td><code>defaultContent</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: ""</p> </td>
     <td>Oorspronkelijke inhoud van het element; alleen gebruikt als <code>precreateElements</code><i> = </i><code>true</code></td>
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

* **Naam variatie**

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
     <td><p>Definieert een oorspronkelijke variatie.<br /> De variatie wordt standaard toegevoegd aan alle elementen van het inhoudsfragment.</p> <p>De wijziging heeft dezelfde initiële inhoud als het betreffende element (zie <code class="code">defaultContent/
       initialContentType</code>)</p> </td>
    </tr>
    <tr>
     <td><code>jcr:title</code></td>
     <td><p><code>String</code></p> <p>vereist</p> </td>
     <td>De titel van de variatie (weergegeven in de fragmenteditor) <strong>Variatie</strong> tab (linkerspoor).</td>
    </tr>
    <tr>
     <td><code>jcr:desciption</code></td>
     <td><p><code>String</code></p> <p>optioneel</p> <p>default: ""</p> </td>
     <td>Een tekst die een beschrijving van de wijziging bevat <span>(wordt weergegeven in de <strong>Variatie</strong> tab (linkerspoor).</code></td>
    </tr>
   </tbody>
  </table>
