---
title: Inleiding tot de werkruimte AEM formulier aanpassen
description: Een snelle inleiding, met conceptuele en technische informatie, om de werkruimte van LiveCycle AEM Forms voor procesbeheer aan te passen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: b183d42f-343c-4acb-bc73-f80ad72e54df
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 0%

---

# Inleiding tot de werkruimte AEM formulier aanpassen{#introduction-to-customizing-aem-form-workspace}

AEM formulierwerkruimte biedt mogelijkheden om de semantiek en functionaliteit van de presentatie van de interface te wijzigen. De typen aanpassingen waarmee u de stijl, lay-out, opmaak, branding en kernfunctionaliteit kunt wijzigen, worden hieronder beschreven.

![&#x200B; cu_customized_workspace_example &#x200B;](assets/cu_customized_workspace_example.png)

Een voorbeeld van een aangepaste werkruimte

## Typen aanpassingen {#types-of-customizations}

De AEM Forms-werkruimte ondersteunt een groot aantal aanpassingen waarmee de lay-out van de gebruikersinterface, de weergave, functionaliteit en nog veel meer kunnen worden bijgewerkt. Bij de aanpassingen moet u een of meer van de volgende handelingen bijwerken:

* Vormgeving van de gebruikersinterface
* Functionaliteit met semantische aanpassingen
* HTML-componenten opnieuw gebruiken in andere toepassingen

### Wijzigingen in gebruikersinterface {#user-interface-changes}

U kunt de vormgeving, lay-out en andere semantische functies van de AEM Forms-werkruimte wijzigen. De werkruimte wijzigen door de CSS-, HTML-sjablonen en JavaScript™-bestanden aan te passen. Alle standaardbestanden worden weergegeven in de standaardinstallatie.

De meest algemeen toepasselijke stappen worden behandeld in [&#x200B; Algemene stappen voor de de werkruimteaanpassing van AEM Forms &#x200B;](../../forms/using/generic-steps-html-workspace-customization.md). Zie de verwante artikelen aan het einde van dit artikel voor specifieke voorbeelden van dergelijke aanpassingen, waaronder de gedetailleerde stappen.

#### De stijlpagina begrijpen {#understanding-the-style-sheet}

Voordat u de werkruimte aanpast, moet u bekend zijn met het standaardstijlblad dat bij AEM Forms wordt geleverd op /libs/ws/css/style.css.

Als u de werkruimte wilt aanpassen, kunt u het beste vertrouwd raken met het bestaande stijlblad style.css in de map /libs/ws/css. Hieronder worden een aantal belangrijke componenten beschreven.

<table>
 <tbody>
  <tr>
   <th><p>CSS-element</p> </th>
   <th><p>Gebruikersinterfacecomponent gewijzigd</p> </th>
  </tr>
  <tr>
   <td><p>#header</p> </td>
   <td><p>Koptekst van de AEM Forms-werkruimte</p> </td>
  </tr>
  <tr>
   <td><p>.categoryList</p> </td>
   <td><p>Categorie</p> </td>
  </tr>
  <tr>
   <td><p>.categoryList.header</p> </td>
   <td><p>Koptekst van categorielijst</p> </td>
  </tr>
  <tr>
   <td><p>.categorieën, .filters</p> </td>
   <td><p>Ruimte onder categorielijst</p> </td>
  </tr>
  <tr>
   <td><p>.category, .filter</p> </td>
   <td><p>Categorie</p> </td>
  </tr>
  <tr>
   <td><p>.category:hover, .category.selected, .filter:hover, .filter.selected</p> </td>
   <td><p>Geselecteerde categorie en muis over stijl van categorie</p> </td>
  </tr>
  <tr>
   <td><p>categoryListBar.tool, categoryListBar.content</p> </td>
   <td><p>Procespagina starten (lijst met gesloten rubrieken)</p> </td>
  </tr>
  <tr>
   <td><p>filterListBar.tool, filterListBar.content</p> </td>
   <td><p>De pagina Taak (gesloten filterlijst)</p> </td>
  </tr>
  <tr>
   <td><p>processNameListBar.tool, processNameListBar.content</p> </td>
   <td><p>Pagina bijhouden (gesloten lijst met procesnamen)</p> </td>
  </tr>
  <tr>
   <td><p>.startPointList, .tasklist</p> </td>
   <td><p>De lijst met startpunten of de takenlijst</p> </td>
  </tr>
  <tr>
   <td><p>.startPointList.header, .tasklist.header</p> </td>
   <td><p>De kopbal van een startpuntlijst of een taaklijst</p> </td>
  </tr>
  <tr>
   <td><p>.startpoint.selected, .task.selected</p> </td>
   <td><p>Het geselecteerde startpunt of de geselecteerde taak</p> </td>
  </tr>
  <tr>
   <td><p>.startpoint.selected.description, .task.selected.description</p> </td>
   <td><p>Beschrijving van het geselecteerde startpunt of de geselecteerde taak</p> </td>
  </tr>
  <tr>
   <td><p>#taskarea</p> </td>
   <td><p>Het taakgebied</p> </td>
  </tr>
  <tr>
   <td><p>#header.dropdown</p> </td>
   <td><p>Vervolgkeuzelijst gebruiker in koptekst</p> </td>
  </tr>
  <tr>
   <td><p>.sortDrop dd ul</p> </td>
   <td><p>Vervolgkeuzelijst voor taken sorteren</p> </td>
  </tr>
 </tbody>
</table>

#### CSS {#css}

De vormgeving van de AEM Forms-werkruimte leent de vormgeving ervan uit een CSS. Door de CSS aan te passen, kunt u de presentatiessemantiek van werkruimte zoals doopvonten, kleuren, branding, en lay-out veranderen.

De stappen op hoofdniveau voor CSS-aanpassing zijn:

* Maak een CSS-bestand.
* Stijlitems toevoegen aan deze CSS. Zie Werken met CSS-stijlen voor meer informatie.
* Werk de verwijzingen bij in `html.jsp` .

Voor de nauwkeurige stappen om deze aanpassingen te doen, zie [&#x200B; Algemene stappen voor de werkruimteaanpassing van AEM Forms &#x200B;](../../forms/using/generic-steps-html-workspace-customization.md). Het CSS-bestand dat wordt geleverd met de AEM Forms-werkruimte bevindt zich op /libs/ws/css/. Voor op CSS betrekking hebbende aanpassingen, gebruik het [&#x200B; Pakket van het Schip &#x200B;](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p). Zie de verwante Help-onderwerpen aan het einde van dit artikel voor specifieke voorbeelden van CSS-gerelateerde aanpassingen.

#### Afbeelding {#image}

U kunt de AEM Forms-werkruimte aanpassen om avatars van gebruikers toe te voegen of om het logo van uw organisatie toe te voegen. Voor deze aanpassingen, gebruik [&#x200B; het Pakket van het Schip &#x200B;](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p).

De stappen op hoofdniveau voor aanpassingen aan de afbeeldingen zijn:

* WebDAV installeren en configureren.
* Voeg nieuwe afbeeldingen toe.
* Voeg nieuwe stijlen toe die overeenkomen met de toegevoegde afbeeldingen.
* Koppeling maken naar het nieuwe CSS-bestand in het `html.jsp` -bestand.

Om met het aanpassen van de beelden in de werkruimte van AEM Forms te beginnen, volg de [&#x200B; Algemene stappen voor de werkruimteaanpassing van AEM Forms &#x200B;](../../forms/using/generic-steps-html-workspace-customization.md). Voor specifieke voorbeelden van beeld-verwante aanpassingen, zie de verwante onderwerpen van de Hulp aan het eind van dit artikel.

#### HTML-sjabloon {#html-template}

Met sjablonen voor HTML kunt u de weergave en lay-out van de gebruikersinterface van de werkruimte definiëren. Door de standaardsjablonen voor HTML bij te werken, kunt u de standaardgebruikersinterface voor de lay-out aanpassen.

De stappen op hoofdniveau voor aanpassingen aan het sjabloon HTML zijn:

* Maak kopieën van de vereiste standaardbestanden in een door de gebruiker gemaakte map.
* Nieuwe sjablonen toevoegen in een door de gebruiker gedefinieerde map.
* Maak relevante updates aan de gekopieerde dossiers als, de weg van het nieuwe malplaatje.

Voor specifieke voorbeelden van dergelijke aanpassingen, zie de onderwerpen van de Hulp die aan het eind van dit artikel worden verstrekt. Kies tussen het [&#x200B; Pakket van het Schip &#x200B;](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p) of het [&#x200B; Dev Pakket &#x200B;](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), afhankelijk van het malplaatje dat moet worden aangepast.

### Semantische wijzigingen {#semantic-changes}

Wijzig de JavaScript-broncode als u de functionaliteit van de AEM Forms-werkruimte wilt wijzigen. Wijzigingen in de kernfunctionaliteit worden aangeduid als Semantische wijzigingen. U wijzigt modellen, weergave en sjablonen die worden geleverd als onderdeel van de broncode van de AEM Forms-werkruimte.

De stappen op hoofdniveau voor semantische wijzigingen om de functionaliteit van de AEM Forms-werkruimte te wijzigen zijn:

* Maak kopieën van de juiste standaardbestanden in een door de gebruiker gemaakte map.
* Voeg nieuwe modellen en meningen in de user-defined omslag toe.
* Breng relevante updates aan zoals het bijwerken van paden van nieuw toegevoegde modellen en meningen in de standaard JavaScript dossiers.
* Minimaal het pakket om de prestaties te optimaliseren.

Voor meer conceptuele informatie over de componenten die deel van de broncode uitmaken, zie de [&#x200B; Beschrijving van herbruikbare componenten &#x200B;](/help/forms/using/description-reusable-components.md). Voor deze aanpassingen, gebruik het Dev Pakket.

### Herbruikbare componenten {#reusable-components}

Aangezien de werkruimte van AEM Forms op componenten-gebaseerde software is, kan het gemakkelijk worden aangepast en worden opnieuw gebruikt. U kunt de werkruimtecomponenten gemakkelijk met uw Webtoepassingen integreren.

Voor meer conceptuele informatie, zie de [&#x200B; Beschrijving van herbruikbare componenten &#x200B;](/help/forms/using/description-reusable-components.md) en voor instructie over het gebruiken van de componenten, zie [&#x200B; Integrerend de werkruimtecomponenten van AEM Forms in Webtoepassingen &#x200B;](/help/forms/using/description-reusable-components.md).

## AEM Forms-werkruimtecode samenstellen {#building-html-workspace-code}

### SDK-pakket {#sdk-package}

Het pakket bevat de broncode van de AEM Forms-werkruimte. Het pakket is beschikbaar via `[LC root]\sdk\html-workspace\adobe-lc-workspace-src.zip` .

Het is hoofdzakelijk bedoeld voor aanpassingen, aangezien het de capaciteit verstrekt om te produceren:

* De pakketten van CRX voor Schip, zuiveren, en Dev profielen (die hieronder in [&#x200B; pakketten van CRX &#x200B;](../../forms/using/introduction-customizing-html-workspace.md#p-crx-package-p) worden vermeld).
* Gimiteerde versie van aangepaste code (voor semantische wijzigingen).

#### WS-inhoud {#ws-content}

* client-pkg:

   * src - Bevat artefacten die nodig zijn om CRX-knooppunten te maken.
   * pom.xml - Script om implementatiepakketten voor verschillende profielen op te bouwen WS-Deplotion Package

* client-html:

   * assembly - Bevat zip.xml die door script wordt gebruikt voor het maken van de AEM Forms-werkruimte SDK.
   * src/main/webapp -

      * css - Bevat stijlbladen voor de werkruimte van AEM Forms.
      * afbeeldingen - Bevat afbeeldingen die worden gebruikt in de AEM Forms-werkruimte.
      * js:

         * libs - Bevat alle bibliotheken van derden die in de AEM Forms-werkruimte worden gebruikt.
         * licenties - Bevat licenties voor HTML- en JS-bestanden en code voor het voorvoegsel van deze licenties voor de desbetreffende bronbestanden.
         * minifier - Wordt gebruikt voor combinatie, minificatie en verzwaring van aangepaste JavaScript-code.
         * resource_optimizer - Gebruikt voor combinatie, minificatie, en vergroting van een bron JavaScript.
         * resource_generator - Gebruikt voor het produceren van register.js en modelcontrollerpath.js.
         * runtime:

            * initializer - Bevat initializer.js die wordt gebruikt om backboneweergaven en modellen te initialiseren die in de werkruimte van AEM Forms worden gebruikt.
            * modellen - Bevat backbonemodellen van alle componenten in de werkruimte van AEM Forms.
            * routes - Bevat JavaScript-bestanden en HTML-bestanden waarmee het proces, taken, bijhouden en voorkeuren in de AEM Forms-werkruimte worden geladen.
            * services - Bevat service.js die wordt gebruikt in de AEM Forms-werkruimte. Alle servervraag wordt gemaakt door service.js.
            * sjablonen - Bevat alle sjablonen, dat wil zeggen HTML-bestanden van alle weergaven in de werkruimte van AEM Forms.
            * util - Bevat alle hulpprogrammabestanden (javascript) die in de AEM Forms-werkruimte worden gebruikt.
            * weergaven - Bevat backboneweergaven van alle componenten in de AEM Forms-werkruimte.

         * main.js
         * router.js

      * libs/ws: pdf.html en pluginPing.pdf worden gebruikt voor het laden van PDF forms in de werkruimte van AEM Forms en WSNextAdapter.swf wordt gebruikt om SWF-formulieren en hulplijnen in de werkruimte van AEM Forms te laden.
      * landinstellingen:

         * de-DE - Bevat vertaling.json voor het Duits.
         * en-US - Bevat translatie.json voor het Engels.
         * fr-FR - Bevat translatie.json voor het Frans.
         * ja-JP - Bevat translatie.json voor Japans.
         * html.jsp - Bevat code om de huidige browserlandinstelling te achterhalen.

      * html.jsp
      * GET.jsp

### CRX-pakket {#crx-package}

CRX-pakket kan worden geïmplementeerd in de CRX™-opslagplaats. Deze is beschikbaar via `[LC root]\crx-repository\install\adobe-lc-workspace-pkg.zip` .

Dit pakket kan worden gemaakt met behulp van de drie hieronder beschreven profielen.

| **Profiel** | **Beschrijving** | **Gebruik** |
|---|---|---|
| Verzendprofiel | Met dit profiel maakt u een CRX-pakket van de kleinst mogelijke grootte met miniatuur. Dit pakket is het meest efficiënt. Alle JavaScript™-bestanden worden gecombineerd en geminiateerd tot één JS-bestand. | Gebruik dit profiel als er geen semantische wijzigingen meer vereist zijn in JS-bestanden. |
| Foutopsporingsprofiel | Met dit profiel wordt een matig efficiënt CRX-pakket gemaakt. De grootte van het pakket is iets groter dan het pakket dat is gemaakt met het profiel Verzenden. Dit pakket bevat de meeste JavaScript-bestanden die in één JS-bestand worden gecombineerd. | Gebruik dit profiel voor foutopsporing. |
| Profiel dev | Met dit profiel wordt een CRX-pakket van de grootst mogelijke grootte gemaakt. Alle JavaScript-bestanden zijn afzonderlijk beschikbaar, net als in het SDK-pakket. | Gebruik dit profiel wanneer u semantische wijzigingen opneemt. |

#### Verzendprofiel {#ship-profile}

#### Opdracht {#command}

* mvn clean -P Ship install on client-pkg folder of Source package sent to client.
* De uitvoering van de opdracht Verzenden van profielen werkt alleen op een 64-bits JVM.

#### WS-inhoud {#ws-content-1}

* css - Bevat style.css, ie.css, en jquery-ui.css.
* afbeeldingen - Bevat alle afbeeldingen.
* js:

   * libs:

      * require - Bevat require.js.
      * jqueryui - Bevat jquery.ui.datepicker.ja.js.

   * runtime:

      * sjablonen - Bevat alle sjablonen, dat wil zeggen: HTML-bestanden van alle componenten in de AEM Forms-werkruimte.

   * main.js (gecombineerd, geminificeerd en aangevuld).
   * registry.js

* libs:

   * ws - Bevat pluginPing.pdf, pdf.html, en WSNextAdapter.swf.

* Landinstelling - Bevat .content.xml.
* landinstellingen:

   * de-DE - Bevat vertaling.json voor het Duits.
   * en-US - Bevat translatie.json voor het Engels.
   * fr-FR - Bevat translatie.json voor het Frans.
   * ja-JP - Bevat translatie.json voor Japans.
   * html.jsp - Bevat code om de huidige browserlandinstelling te achterhalen.

* Index - Bevat .content.xml
* profiel - Bevat offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml

#### Foutopsporingsprofiel {#debug-profile}

#### Opdracht {#command-1}

* mvn clean -P Debug install on client-pkg
* De uitvoering van foutopsporingsprofielopdrachten werkt alleen op 64-bits JVM.

#### WS-inhoud {#ws-content-2}

* css - Bevat style.css, ie.css, en jqueri-ui.css.
* afbeeldingen - Bevat alle afbeeldingen.
* js:

   * libs:

      * require - Bevat require.js.
      * jqueryui - Bevat jquery.ui.datepicker.ja.js.

   * runtime:

      * sjablonen - Bevat alle sjablonen, dat wil zeggen: HTML-bestanden van alle componenten in de AEM Forms-werkruimte.

   * main.js (gecombineerd).
   * registry.js

* libs:

   * ws - Bevat pluginPing.pdf, pdf.html, en WSNextAdapter.swf.

* Landinstelling - Bevat .content.xml.
* landinstellingen:

   * de-DE - Bevat vertaling.json voor het Duits.
   * en-US - Bevat translatie.json voor het Engels.
   * fr-FR - Bevat translatie.json voor het Frans.
   * ja-JP - Bevat translatie.json voor Japans.
   * html.jsp - Bevat code om de huidige browserlandinstelling te achterhalen.

* Index - Bevat .content.xml
* profiel - Bevat offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml

#### Dev-profiel {#dev-profile}

#### Opdracht {#command-2}

mvn clean -P Dev install on client pkg

#### WS-inhoud {#ws-content-3}

* css - Bevat style.css, ie.css, en jqueri-ui.css.
* afbeeldingen - Bevat alle afbeeldingen.
* js:

   * libs - Bevat alle bibliotheken die in de AEM Forms-werkruimte worden gebruikt.
   * require - Bevat require.js
   * jqueryui - Bevat jquery.ui.datepicker.ja.js
   * runtime:

      * initializer - Bevat initializer.js en modelcontrollerpath.js.
      * modellen - Bevat modellen van alle componenten in de werkruimte van AEM Forms.
      * routes - Bevat JavaScript-bestanden en HTML-bestanden waarmee het proces, taken, bijhouden en voorkeuren in de AEM Forms-werkruimte worden geladen.
      * services - Bevat service.js die wordt gebruikt in de AEM Forms-werkruimte.
      * sjablonen - Bevat alle sjablonen, dat wil zeggen: HTML-bestanden van alle componenten in de AEM Forms-werkruimte.
      * util - Bevat alle hulpprogrammabestanden (JavaScript) die in de AEM Forms-werkruimte worden gebruikt.
      * weergaven - Bevat weergaven van alle componenten in de AEM Forms-werkruimte.

   * main.js
   * registry.js
   * router.js

* libs:

   * ws - Bevat pluginPing.pdf, pdf.html, en WSNextAdapter.swf.

* Landinstelling - Bevat .content.xml.
* landinstellingen:

   * de-DE - Bevat vertaling.json voor het Duits.
   * en-US - Bevat translatie.json voor het Engels.
   * fr-FR - Bevat translatie.json voor het Frans.
   * ja-JP - Bevat translatie.json voor Japans.
   * html.jsp - Bevat code om de huidige browserlandinstelling te achterhalen.

* Index - Bevat .content.xml
* profiel - Bevat offline.jsp.
* GET.jsp
* html.jsp
* content.xml
* _rep_policy.xml
