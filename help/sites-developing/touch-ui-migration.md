---
title: Migratie naar de aanraakinterface
description: Meer informatie over de migratie van Adobe Experience Manager naar de Touch-gebruikersinterface en over de gevolgen hiervan voor u.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
docset: aem65
exl-id: 33dc1ee7-1e34-43d8-9265-c66535f5e002
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---

# Migratie naar de aanraakinterface{#migration-to-the-touch-ui}

Vanaf versie 6.0 introduceerde Adobe Experience Manager (AEM) een nieuwe gebruikersinterface die *interface met aanraakbediening* (ook wel bekend als de *aanraakinterface*). Deze wordt uitgelijnd op de Adobe Experience Cloud en de algemene richtlijnen voor de gebruikersinterface voor Adoben. Dit is de standaard UI in AEM met de erfenis, Desktop-oriented interface geworden die als *klassieke gebruikersinterface*.

Als u AEM met klassieke UI hebt gebruikt, neem actie om uw instantie te migreren. Deze pagina is bedoeld als springboard door koppelingen naar individuele bronnen aan te bieden.

>[!NOTE]
>
>Een dergelijk migratieproject kan grote gevolgen hebben voor uw instantie. Zie [Projecten beheren - Aanbevolen procedures](/help/managing/best-practices.md) voor aanbevolen richtlijnen.

## De basisbeginselen {#the-basics}

Houd tijdens het migreren rekening met de volgende grote verschillen tussen de klassieke interface en de aanraakinterface:

<table>
 <tbody>
  <tr>
   <td>Klassieke interface</td>
   <td>Interface met aanraakbediening</td>
  </tr>
  <tr>
   <td>Wordt in de JCR-opslagplaats beschreven als een structuur van knooppunten. Elke knoop die een element van UI vertegenwoordigt wordt genoemd en <em>ExtJS-widget</em> en op de client worden gerenderd door <code>ExtJS</code>.</td>
   <td>Wordt in de JCR-opslagplaats ook beschreven als een structuur van knooppunten. Nochtans, in dit geval, verwijst elke knoop naar een Sling middeltype (de component van het Sling), dat de oorzaak van zijn teruggeven is. De gebruikersinterface wordt (in feite) weergegeven op de server.</td>
  </tr>
  <tr>
   <td><p><code>sling:resourceType</code></p>
    <ul>
     <li>niet gebruikt</li>
    </ul> </td>
   <td><code>sling:resourceType</code>
    <ul>
     <li>gebruikt</li>
     <li>bijvoorbeeld<br /> <code>cq/gui/components/authoring/dialog</code><br /> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Dialoogvensterknooppunten:</p>
    <ul>
     <li>Naam: <code>dialog</code></li>
     <li><code>jcr:primaryType</code>: <code>cq:Dialog</code></li>
    </ul> </td>
   <td><p>Dialoogvensterknooppunten:</p>
    <ul>
     <li>Naam: <code>cq:dialog</code></li>
     <li><code>jcr:primaryType</code>: <code>nt:unstructured</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>JavaScript-locatie:</p>
    <ul>
     <li>Imperatieve onderdelen worden rechtstreeks ingesloten met behulp van listeners of beheerd in clientlibs.</li>
    </ul> </td>
   <td><p>JavaScript-locatie:</p>
    <ul>
     <li>Imperatieve onderdelen kunnen niet worden opgenomen in de definitie van het dialoogvenster, scheiding van verantwoordelijkheden.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenisafhandeling:</p>
    <ul>
     <li>Dialoogvensterwidgets verwijzen rechtstreeks naar JavaScript-code.</li>
    </ul> </td>
   <td><p>Gebeurtenisafhandeling:</p>
    <ul>
     <li>JavaScript merkt dialooggebeurtenissen op.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Rendering uitgevoerd door de client:
    <ul>
     <li>Client maakt dynamisch de UI-componenten.</li>
     <li>Client vraagt (Pull) componentdefinitie (als JSON) van server.</li>
    </ul> </td>
   <td>Renderen uitgevoerd door de server:
    <ul>
     <li>De cliënt vraagt pagina's samen met verwante UI.</li>
     <li>De server verzendt (duw) UI als documenten van HTML; het gebruiken van de componenten van de Koraal UI.<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Met andere woorden, wanneer u een gedeelte van de gebruikersinterface migreert van de klassieke gebruikersinterface naar de aanraakinterface, kunt u een poort *ExtJS-widget* een *Onderdeel Verdelen*. Om dit te vergemakkelijken, is de aanraak UI gebaseerd op het kader van Granite UI, dat reeds sommige componenten van het Verkopen voor UI (die als componenten van Granite UI wordt bedoeld) verstrekt.

Controleer voordat u begint de status en de bijbehorende aanbevelingen:

* [Status Touch UI-functies](/help/release-notes/touch-ui-features-status.md)
* [Gebruikersinterface Recommendations voor klanten](/help/sites-deploying/ui-recommendations.md)

De basisbeginselen van de ontwikkeling van de aanraakinterface bieden een solide basis:

* [Concepten van de interface AEM Touch-Enabled](/help/sites-developing/touch-ui-concepts.md)
* [Structuur van de interface voor AEM aanraakbediening](/help/sites-developing/touch-ui-structure.md)

## Paginaontwerp migreren {#migrating-page-authoring}

Dialoogvensters zijn een belangrijke factor bij het migreren van uw componenten:

* [Ontwikkelen AEM componenten](/help/sites-developing/developing-components.md) (met de interface met aanraakbediening)
* [Migreren vanuit een klassieke component](/help/sites-developing/developing-components.md#migrating-from-a-classic-component)
* [AEM moderniseringsinstrumenten](/help/sites-developing/modernization-tools.md) - om u te helpen de dialoogvensters van uw klassieke UI-componenten om te zetten in aanrakingsinterface

   * Er is een compatibiliteitslaag in aanraak UI om een klassiek UI-dialoogvenster te openen binnen een &quot;Touch UI-wrapper&quot;, maar deze heeft beperkte functionaliteit en wordt niet aanbevolen voor de lange termijn.

* [Dialoogvenstervelden aanpassen in Touch UI](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.html)
* [Een nieuwe graniet-UI-veldcomponent maken](/help/sites-developing/granite-ui-component.md)
* [Paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md) (met de interface met aanraakbediening)

## Consoles migreren {#migrating-consoles}

U kunt ook de consoles aanpassen:

* [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md) (voor de interface met aanraakbediening)

## Verwante overwegingen {#related-considerations}

Hoewel er niet rechtstreeks verband is met een migratie naar de aanraakinterface, zijn er verwante problemen die u tegelijkertijd moet overwegen, zoals ook aanbevolen wordt:

* [Sjablonen](/help/sites-developing/templates.md) - [Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md)
* [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html)

>[!NOTE]
>
>Zie ook [Ontwikkelen - Aanbevolen praktijken](/help/sites-developing/best-practices.md).

## Aanvullende bronnen {#further-resources}

Voor volledige informatie over het ontwikkelen AEM zie de inzameling van middelen onder:

* [Gebruikershandleiding ontwikkelen](/help/sites-developing/getting-started.md)
* [Granite UI-documentatie](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [AEM 6.5 Tutorials en video&#39;s van sites](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/overview.html)
* [Aan de slag met het ontwikkelen van AEM Sites - WKND-zelfstudie](/help/sites-developing/getting-started.md)
* [AEM Gems](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html)
* [AEM-moderniseringstools](https://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>AEM Moderniseringsinstrumenten zijn een communautaire inspanning en worden niet gesteund of gerechtvaardigd door Adobe.
