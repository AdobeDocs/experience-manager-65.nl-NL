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

Beginnend met versie 6.0, introduceerde Adobe Experience Manager (AEM) een nieuw gebruikersinterface die als *wordt bedoeld aanraking-toegelaten UI* (ook als *aanraking UI* wordt bekend). Deze wordt uitgelijnd op de Adobe Experience Cloud en de algemene richtlijnen voor de gebruikersinterface voor Adoben. Dit is standaard UI in AEM met de erfenis geworden, Desktop-georiënteerde interface die als *wordt bedoeld klassieke UI*.

Als u AEM met klassieke UI hebt gebruikt, neem actie om uw instantie te migreren. Deze pagina is bedoeld als springboard door koppelingen naar individuele bronnen aan te bieden.

>[!NOTE]
>
>Een dergelijk migratieproject kan grote gevolgen hebben voor uw instantie. Zie [ het Leiden Projecten - Beste praktijken ](/help/managing/best-practices.md) voor geadviseerde richtlijnen.

## De basisbeginselen {#the-basics}

Houd tijdens het migreren rekening met de volgende grote verschillen tussen de klassieke interface en de aanraakinterface:

<table>
 <tbody>
  <tr>
   <td>Klassieke interface</td>
   <td>Interface met aanraakbediening</td>
  </tr>
  <tr>
   <td>Wordt in de JCR-opslagplaats beschreven als een structuur van knooppunten. Elke knoop die een element van UI vertegenwoordigt wordt genoemd a <em> ExtJS widget </em> en op de cliënt-kant door <code>ExtJS</code> teruggegeven.</td>
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
     <li>bijvoorbeeld <br /> <code>cq/gui/components/authoring/dialog</code><br /> </li>
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
     <li>Dialoogwidgets verwijzen rechtstreeks naar de JavaScript-code.</li>
    </ul> </td>
   <td><p>Gebeurtenisafhandeling:</p>
    <ul>
     <li>JavaScript houdt dialooggebeurtenissen bij.</li>
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
     <li>De server verzendt (Duw) UI als documenten van de HTML; het gebruiken van de componenten van de Koraal UI.<br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Met andere woorden, migrerend een sectie van uw UI van klassieke UI aan de aanraking UI betekent om een *widget ExtJS* aan a *Sling component* te haven. Om dit te vergemakkelijken, is de aanraak UI gebaseerd op het kader van Granite UI, dat reeds sommige componenten van het Verkopen voor UI (die als componenten van Granite UI wordt bedoeld) verstrekt.

Controleer voordat u begint de status en de bijbehorende aanbevelingen:

* [Status Touch UI-functies](/help/release-notes/touch-ui-features-status.md)
* [Gebruikersinterface Recommendations voor klanten](/help/sites-deploying/ui-recommendations.md)

De basisbeginselen van de ontwikkeling van de aanraakinterface bieden een solide basis:

* [Concepten van de interface AEM Touch-Enabled](/help/sites-developing/touch-ui-concepts.md)
* [Structuur van de interface voor AEM aanraakbediening](/help/sites-developing/touch-ui-structure.md)

## Paginaontwerp migreren {#migrating-page-authoring}

Dialoogvensters zijn een belangrijke factor bij het migreren van uw componenten:

* [ het Ontwikkelen AEM Componenten ](/help/sites-developing/developing-components.md) (met aanraking-toegelaten UI)
* [Migreren vanuit een klassieke component](/help/sites-developing/developing-components.md#migrating-from-a-classic-component)
* [ AEM Moderniseringshulpmiddelen ](/help/sites-developing/modernization-tools.md) - om u te helpen de dialogen van uw klassieke componenten UI in aanraking UI omzetten

   * Er is een compatibiliteitslaag in aanraak UI om een klassiek UI-dialoogvenster te openen binnen een &quot;Touch UI-wrapper&quot;, maar deze heeft beperkte functionaliteit en wordt niet aanbevolen voor de lange termijn.

* [ het Aanpassen van de Gebieden van de Dialoog in Aanraak UI ](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.html)
* [Een nieuwe graniet-UI-veldcomponent maken](/help/sites-developing/granite-ui-component.md)
* [ het Aanpassen van de Authoring van de Pagina ](/help/sites-developing/customizing-page-authoring-touch.md) (met touch-enabled UI)

## Consoles migreren {#migrating-consoles}

U kunt ook de consoles aanpassen:

* [ die Consoles ](/help/sites-developing/customizing-consoles-touch.md) aanpassen (voor touch-Toegelaten UI)

## Verwante overwegingen {#related-considerations}

Hoewel er niet rechtstreeks verband is met een migratie naar de aanraakinterface, zijn er verwante problemen die u tegelijkertijd moet overwegen, zoals ook aanbevolen wordt:

* [ Malplaatjes ](/help/sites-developing/templates.md) - [ Bewerkbare malplaatjes ](/help/sites-developing/page-templates-editable.md)
* [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)
* [ HTML ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html)

>[!NOTE]
>
>Zie ook [ Ontwikkelen - Beste praktijken ](/help/sites-developing/best-practices.md).

## Aanvullende bronnen {#further-resources}

Voor volledige informatie over het ontwikkelen AEM zie de inzameling van middelen onder:

* [Gebruikershandleiding ontwikkelen](/help/sites-developing/getting-started.md)
* [ de Documentatie van graniet UI ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [ AEM 6.5 Tutorials en Video&#39;s van Plaatsen ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/overview.html)
* [Aan de slag met het ontwikkelen van AEM Sites - WKND-zelfstudie](/help/sites-developing/getting-started.md)
* [ AEM Gems ](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/overview.html)
* [AEM-moderniseringstools](https://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>AEM Moderniseringsinstrumenten zijn een communautaire inspanning en worden niet gesteund of gerechtvaardigd door Adobe.
