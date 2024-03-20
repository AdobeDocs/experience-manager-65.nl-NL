---
title: Gebruikersinterface Recommendations voor klanten
description: Een lijst met aanbevelingen voor de klassieke en geoptimaliseerde gebruikersinterfaces.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
docset: aem65
exl-id: 7b71119a-ff58-47c0-aeef-a705ed8c40e0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# Gebruikersinterface Recommendations voor klanten{#user-interface-recommendations-for-customers}

Adobe Experience Manager wordt geleverd met twee UI&#39;s: de interface voor één Experience Cloud (ook wel de interface met aanraakbediening genoemd) en de klassieke UI.

Dit document is bedoeld om klanten te helpen een keuze te maken over welke interface ze moeten gebruiken, afhankelijk van hun situatie.

Belangenbeding:

* **UI (of standaardinterface)**
Moderne gebruikersinterface die in 5.6.0 als technologievoorproef werd geïntroduceerd en in verdere versies werd uitgebreid. De interface is gebaseerd op de ervaring van één gebruiker voor de Adobe Experience Cloud, die voorheen wel een interface met aanraakbediening of een interface met aanraakbediening werd genoemd.

* **Klassieke interface**
Gebruikersinterface gebaseerd op ExtJS-technologie die in 2008 werd geïntroduceerd met CQ 5.1.

* **Sitebeheerder**
Mogelijkheden om de sitehiërarchie te beheren (verplaatsen, activeren, beheerde verwijzingen) en nieuwe pagina&#39;s te maken.

* **Pagina&#39;s ontwerpen**
Mogelijkheid om de inhoud van een pagina toe te voegen/te bewerken.

* **DAM/Assets-beheerder**
Mogelijkheid om digitale elementen te beheren (zoals afbeeldingen, video, documenten, downloads).

* **ContextHub**
Mogelijkheid om informatie over de bezoeker samen te voegen en voor verschillende doeleinden te gebruiken. Verstrekt een gebruikersinterface om personen te simuleren die de plaats bezoeken. Beginnend AEM 6.2, vervangt ContextHub de vorige technologie, de Context van de Cliënt.

## Algemeen {#general}

In de afgelopen jaren heeft Adobe alle Adobe Experience Cloud-oplossingen bijgewerkt met één gebruikersinterface. De gebruikers over de oplossingen van de Experience Cloud genieten een verenigbare ervaring met gemeenschappelijke patronen op hoe te om de toepassingen te gebruiken en in werking te stellen. Met elke versie, heeft de Adobe zijn gebruikersinterface verfijnd die op terugkoppelen van klanten wordt gebaseerd die over de diverse oplossingen werken.

De oorspronkelijke gebruikersinterface voor Adobe Experience Manager (voorheen CQ5 genoemd), die in 2008 werd geïntroduceerd en door klanten met versies 5.0-5.6.1 werd gebruikt, staat in AEM 6.5. Dit garandeert dat klanten een update naar versie 6.5 kunnen uitvoeren en kunnen profiteren van een bijgewerkt platform met nieuwe mogelijkheden en dezelfde gebruikersinterface kunnen blijven gebruiken.

Adobe raadt klanten aan om in 2018/2019 over te schakelen op de nieuwe interface. Dit kan of tijdens de update aan 6.5 - of in een afzonderlijke projecten na de update worden gedaan, die de noodzakelijke aanpassingen aan de aanpassingen en componentendialogen zou omvatten.

De klassieke gebruikersinterface is vervangen door AEM 6.4 en de Adobe is niet van plan verdere verbeteringen aan te brengen in de klassieke gebruikersinterface. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd.

### Regels en Recommendations {#rules-and-recommendations}

Hieronder volgt een lijst met aanbevelingen van Product Management voor Adobe Experience Manager 6.5:

<table>
 <tbody>
  <tr>
   <th>Mijn project...</th>
   <th>Recommendations</th>
  </tr>
  <tr>
   <td>Adobe Experience Manager begint net te gebruiken.</td>
   <td>Gebruik de standaardinterface.</td>
  </tr>
  <tr>
   <td><p>Heeft AEM een tijdje gebruikt.</p> <p>Gebruikt de productUI uit-van-de-doos en ontwikkelde douanecomponenten voor de plaatsen.<br /> </p> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen.. enz.<br /> </li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui">Gebruikersinterface selecteren</a>.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe raadt u aan de <a href="/help/sites-developing/modernization-tools.md">AEM moderniseringsinstrumenten</a> om de componenten bij te werken.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Heeft een site gemaakt die de ClientContext met integratie gebruikt.<br /> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen.. enz.</li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui">Gebruikersinterface selecteren</a>.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe raadt u aan de <a href="/help/sites-developing/modernization-tools.md">AEM moderniseringsinstrumenten</a> om de componenten bij te werken.</li>
     <li>Vorm ContextHub (de vervanging voor de ClientContext) en werk de paginasjablonen bij om ContextHub te gebruiken. ContextHub heeft een verenigbaarheidswijze die het laden van de opslag van de douaneClientContext toestaat.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Heeft CQ/AEM jarenlang gebruikt.</p> <p>Bevat een uitgebreide interface voor het product (bijvoorbeeld Sitebeheer) en ingebouwde componenten met uitgebreide dialoogvensters voor bewerken.</p> </td>
   <td><p>Update aan 6.5 en vorm klassieke UI als gebrek voor paginascreatie voor alle gebruikers. Zie <a href="#selecting-your-ui">Gebruikersinterface selecteren</a>.</p> <p>Start vervolgens een project om de deeldialoogvensters aan te passen en te optimaliseren in de indeling Coral 3. Zie <a href="#resources-to-help">Hulpbronnen</a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Veelgestelde vragen {#faq}

Zie het artikel in de Knowledge Base. [Veelgestelde vragen over Touch UI-authoring](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html), voor meer informatie; inclusief informatie over het afbraakschema voor de klassieke interface.

### Gebruikersinterface selecteren {#selecting-your-ui}

Zie [Gebruikersinterface selecteren](/help/sites-authoring/select-ui.md) voor informatie over het configureren van uw systeem naar wens.

### UI-status voor aanraking {#touch-enabled-ui-status}

Zie voor meer informatie over de verbeteringen aan de interface met aanraakbediening in AEM 6.5 [Nieuwe functies](/help/release-notes/release-notes.md#what-s-new) in de opmerkingen bij de release.

Een volledig overzicht van de [Status van TouchUI-functie](/help/release-notes/touch-ui-features-status.md) page

### Hulpbronnen {#resources-to-help}

Voor achtergrondinformatie over basisverwerking:

* [Pagina&#39;s ontwerpen](/help/sites-authoring/page-authoring.md).

Voor gedetailleerde ontwikkelingsinformatie:

* [Interface-architectuur met aanraakbediening](/help/sites-developing/touch-ui-concepts.md).
* Gebruik de [AEM moderniseringsinstrumenten](/help/sites-developing/modernization-tools.md) Hiermee converteert u dialoogvensters voor bewerken van componenten van de klassieke gebruikersinterface naar de interface met aanraakbediening.

* [Structuur van de interface met aanraakbediening](/help/sites-developing/touch-ui-structure.md).

* [De consoles aanpassen in de interface met aanraakbediening](/help/sites-developing/customizing-consoles-touch.md) (bevat voorbeeldcode).

* [Het ontwerpen van pagina&#39;s aanpassen in de interface met aanraakbediening](/help/sites-developing/customizing-page-authoring-touch.md) (bevat voorbeeldcode).

* [Granite UI-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html).
