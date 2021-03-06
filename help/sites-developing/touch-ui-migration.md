---
title: Migratie naar de aanraakinterface
seo-title: Migratie naar de aanraakinterface
description: Migratie naar de aanraakinterface
seo-description: Migratie naar de aanraakinterface
uuid: 47c43b56-532b-4ada-8503-04d66bab3564
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
discoiquuid: b315720f-e9b8-4063-99e2-1b9aa6bba460
docset: aem65
translation-type: tm+mt
source-git-commit: 7035c19a109ff67655ee0419aa37d1723e2189cc
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 4%

---


# Migratie naar de aanraakinterface{#migration-to-the-touch-ui}

Vanaf versie 6.0 introduceerde Adobe Experience Manager (AEM) een nieuwe gebruikersinterface die wordt aangeduid als de *interface met aanraakbediening* (ook wel de *aanraakinterface* genoemd). De interface wordt uitgelijnd op de Adobe Marketing Cloud en de algemene richtlijnen voor de gebruikersinterface van Adobe. Dit is de standaard UI in AEM met de erfenis, Desktop-oriented interface geworden die als *klassieke UI* wordt bedoeld.

Als u AEM met klassieke UI hebt gebruikt, zult u actie moeten ondernemen om uw instantie te migreren. Deze pagina is bedoeld als springboard door koppelingen naar individuele bronnen te bieden.

>[!NOTE]
>
>Een dergelijk migratieproject kan grote gevolgen hebben voor uw instantie. Zie [Projecten beheren - Beste praktijken](/help/managing/best-practices.md) voor geadviseerde richtlijnen.

## De basisbeginselen {#the-basics}

Houd tijdens het migreren rekening met de volgende (grote) verschillen tussen de klassieke interface en de aanraakinterface:

<table>
 <tbody>
  <tr>
   <td>Klassieke interface</td>
   <td>Interface met aanraakbediening</td>
  </tr>
  <tr>
   <td>Wordt in de JCR-opslagplaats beschreven als een structuur van knooppunten. Elk knooppunt dat een element van de UI vertegenwoordigt, wordt een <em>ExtJS-widget</em> genoemd en op de client-kant door <code>ExtJS</code> gerenderd.</td>
   <td>Wordt in de JCR-opslagplaats ook beschreven als een structuur van knooppunten. In dit geval verwijst elk knooppunt echter naar een Sling-brontype (Sling-component), dat verantwoordelijk is voor de rendering ervan. De gebruikersinterface wordt (in feite) weergegeven op de server.</td>
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
     <li>jcr:primaryType: <code>cq:Dialog</code></li>
    </ul> </td>
   <td><p>Dialoogvensterknooppunten:</p>
    <ul>
     <li>Naam: <code>cq:dialog</code></li>
     <li>jcr:primaryType: <code>nt:unstructured</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Javascript-locatie:</p>
    <ul>
     <li>Imperatieve onderdelen worden rechtstreeks ingesloten met behulp van listeners of beheerd in clientlibs.</li>
    </ul> </td>
   <td><p>Javascript-locatie:</p>
    <ul>
     <li>Imperatieve onderdelen kunnen niet worden ingesloten in de definitie van het dialoogvenster. scheiding van verantwoordelijkheden.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenisafhandeling:</p>
    <ul>
     <li>Dialoogwidgets verwijzen rechtstreeks naar JavaScript-code.</li>
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
     <li>De cli??nt vraagt pagina's samen met verwante UI.</li>
     <li>De server verzendt de gebruikersinterface (push) als HTML-documenten. gebruiken van de componenten van de Koraal UI.<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Met andere woorden, het migreren van een sectie van uw UI van klassieke UI aan aanraak UI betekent het uitvoeren van *ExtJS widget* aan *Sling component*. Om dit te vergemakkelijken, is de aanraak UI gebaseerd op het kader van Granite UI, dat reeds sommige componenten van het Verkopen voor UI (die als componenten van Granite UI wordt bedoeld) verstrekt.

Controleer voordat u begint de status en de bijbehorende aanbevelingen:

* [Status van touch-functies](/help/release-notes/touch-ui-features-status.md)
* [Gebruikersinterface Recommendations voor klanten](/help/sites-deploying/ui-recommendations.md)

De basisbeginselen van de ontwikkeling van de aanraakinterface bieden een solide basis:

* [Concepten van de interface AEM Touch-Enabled](/help/sites-developing/touch-ui-concepts.md)
* [Structuur van de interface voor AEM aanraakbediening](/help/sites-developing/touch-ui-structure.md)

## Paginaontwerp {#migrating-page-authoring} migreren

Dialoogvensters zijn een belangrijke factor bij het migreren van uw componenten:

* [Ontwikkeling AEM Componenten](/help/sites-developing/developing-components.md)  (met de interface met aanraakbediening)
* [Migreren vanuit een klassieke component](/help/sites-developing/developing-components.md#migrating-from-a-classic-component)
* [AEM Moderniseringsgereedschappen](/help/sites-developing/modernization-tools.md)  - om u te helpen de dialoogvensters van uw klassieke UI-componenten om te zetten in een interface

   * Er is een compatibiliteitslaag in aanraak UI om een klassiek UI-dialoogvenster te openen binnen een &quot;Touch UI-wrapper&quot;, maar deze heeft beperkte functionaliteit en wordt niet aanbevolen voor de lange termijn.

* [Dialoogvenstervelden aanpassen in Touch UI](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.html)
* [Een nieuwe graniet UI-veldcomponent maken](/help/sites-developing/granite-ui-component.md)
* [Paginaontwerp](/help/sites-developing/customizing-page-authoring-touch.md)  aanpassen (met de interface met aanraakbediening)

## Consoles {#migrating-consoles} migreren

U kunt ook de consoles aanpassen:

* [De consoles](/help/sites-developing/customizing-consoles-touch.md)  aanpassen (voor de interface met aanraakbediening)

## Verwante overwegingen {#related-considerations}

Hoewel er niet rechtstreeks verband is met een migratie naar de aanraakinterface, zijn er verwante problemen die u tegelijkertijd moet overwegen, zoals ook aanbevolen wordt:

* [Sjablonen](/help/sites-developing/templates.md)  -  [Bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md)
* [Kernonderdelen](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html)

>[!NOTE]
>
>Zie ook [Ontwikkelen - Beste praktijken](/help/sites-developing/best-practices.md).

## Aanvullende bronnen {#further-resources}

Voor volledige informatie over het ontwikkelen AEM zie de inzameling van middelen onder:

* [Gebruikershandleiding ontwikkelen](/help/sites-developing/home.md)
* [Granite UI-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [AEM 6.5 Tutorials en video&#39;s van sites](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/overview.html)
* [Aan de slag met het ontwikkelen van AEM Sites - WKND-tutorial](/help/sites-developing/getting-started.md)
* [AEM Gems](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-index.html)
* [AEM-moderniseringstools](https://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>AEM Moderniseringsgereedschappen zijn een gemeenschapsinspanning en worden niet ondersteund of gegarandeerd door Adobe.

