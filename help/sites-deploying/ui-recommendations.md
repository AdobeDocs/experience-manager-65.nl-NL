---
title: Aanbevelingen voor gebruikersinterface voor klanten
description: Een lijst met aanbevelingen voor de klassieke en geoptimaliseerde gebruikersinterfaces.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
docset: aem65
exl-id: 7b71119a-ff58-47c0-aeef-a705ed8c40e0
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 8f638eb384bdca59fb6f4f8990643e64f34622ce
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Aanbevelingen voor gebruikersinterface voor klanten{#user-interface-recommendations-for-customers}

Adobe Experience Manager wordt geleverd met twee UI&#39;s: de Unified Experience Cloud UI (ook wel de interface met aanraakbediening genoemd) en de klassieke UI.

Dit document is bedoeld om klanten te helpen een keuze te maken over welke interface ze moeten gebruiken, afhankelijk van hun situatie.

Belangenbeding:

* **UI (of standaard UI)**
Moderne gebruikersinterface die in 5.6.0 als technologievoorproef werd geïntroduceerd en in verdere versies werd uitgebreid. De interface is gebaseerd op de ervaring van één gebruiker voor de Adobe Experience Cloud, die voorheen wel een interface met aanraakbediening of een interface met aanraakbediening werd genoemd.

* **Klassieke UI**
Gebruikersinterface gebaseerd op ExtJS-technologie die in 2008 werd geïntroduceerd met CQ 5.1.

* **Admin van de Plaats**
Mogelijkheden om de sitehiërarchie te beheren (verplaatsen, activeren, beheerde verwijzingen) en nieuwe pagina&#39;s te maken.

* **pagina Authoring**
Mogelijkheid om de inhoud van een pagina toe te voegen/te bewerken.

* **DAM/Assets Admin**
Mogelijkheid om digitale elementen te beheren (zoals afbeeldingen, video, documenten, downloads).

* **ContextHub**
Mogelijkheid om informatie over de bezoeker samen te voegen en voor verschillende doeleinden te gebruiken. Verstrekt een gebruikersinterface om personen te simuleren die de plaats bezoeken. Beginnend AEM 6.2, vervangt ContextHub de vorige technologie, de Context van de Cliënt.

## Algemeen {#general}

In de afgelopen jaren heeft Adobe alle Adobe Experience Cloud-oplossingen bijgewerkt met één gebruikersinterface. Gebruikers in de Experience Cloud-oplossingen genieten van een consistente ervaring met gangbare patronen voor het gebruik en het gebruik van de toepassingen. Bij elke release heeft Adobe zijn gebruikersinterface verfijnd op basis van feedback van klanten die verschillende oplossingen gebruiken.

De oorspronkelijke gebruikersinterface voor Adobe Experience Manager (voorheen CQ5 genoemd), die in 2008 werd geïntroduceerd en door klanten met versies 5.0-5.6.1 werd gebruikt, is aanwezig in AEM 6.5. Dit garandeert dat klanten een update naar versie 6.5 kunnen uitvoeren en kunnen profiteren van een bijgewerkt platform met nieuwe mogelijkheden en dezelfde gebruikersinterface kunnen blijven gebruiken.

Adobe raadt klanten aan om in 2018/2019 over te schakelen op de nieuwe gebruikersinterface. Dit kan of tijdens de update aan 6.5 - of in een afzonderlijke projecten na de update worden gedaan, die de noodzakelijke aanpassingen aan de aanpassingen en componentendialogen zou omvatten.

De klassieke gebruikersinterface is vervangen door AEM 6.4 en Adobe is niet van plan om verdere verbeteringen aan te brengen in de klassieke gebruikersinterface. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd.

### Regels en aanbevelingen {#rules-and-recommendations}

Hieronder volgt een lijst met aanbevelingen van Product Management voor Adobe Experience Manager 6.5:

<table>
 <tbody>
  <tr>
   <th>Mijn project...</th>
   <th>Aanbevelingen</th>
  </tr>
  <tr>
   <td>Adobe Experience Manager begint net te gebruiken.</td>
   <td>Gebruik de standaardinterface.</td>
  </tr>
  <tr>
   <td><p>Heeft AEM een tijdje gebruikt.</p> <p>Heeft product UI uit-van-de-doos gebruikt en douanecomponenten voor de plaatsen ontwikkeld.<br /> </p> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen.. etc.<br /> </li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui"> Selecterend Uw UI </a>.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe adviseert het gebruiken van <a href="/help/sites-developing/modernization-tools.md"> Hulpmiddelen van de Modernisering van AEM </a> om de componenten bij te werken.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Heeft een plaats gebouwd die ClientContext met integratie gebruikt.<br /> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen.. enz.</li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui"> Selecterend Uw UI </a>.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe adviseert het gebruiken van <a href="/help/sites-developing/modernization-tools.md"> Hulpmiddelen van de Modernisering van AEM </a> om de componenten bij te werken.</li>
     <li>Vorm ContextHub (de vervanging voor ClientContext) en werk de paginasjablonen bij om ContextHub te gebruiken. ContextHub heeft een verenigbaarheidswijze die het laden van de opslag van douaneClientContext toestaat.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Heeft CQ/AEM jarenlang gebruikt.</p> <p>Bevat een uitgebreide interface voor het product (bijvoorbeeld Sitebeheer) en ingebouwde componenten met uitgebreide dialoogvensters voor bewerken.</p> </td>
   <td><p>Update aan 6.5 en vorm klassieke UI als gebrek voor paginascreatie voor alle gebruikers. Zie <a href="#selecting-your-ui"> Selecterend Uw UI </a>.</p> <p>Start vervolgens een project om de deeldialoogvensters aan te passen en te optimaliseren in de indeling Coral 3. Zie <a href="#resources-to-help"> Middelen aan Hulp </a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Gebruikersinterface selecteren {#selecting-your-ui}

Zie [ Selecterend Uw UI ](/help/sites-authoring/select-ui.md) voor informatie over het vormen van uw systeem zoals vereist.

### UI-status voor aanraking {#touch-enabled-ui-status}

Voor details van de verhogingen die aan touch-Toegelaten UI in AEM 6.5 worden aangebracht zie [ wat ](/help/release-notes/release-notes.md#what-s-new) in de Nota&#39;s van de Versie Nieuw is.

Een volledig overzicht ziet de ](/help/release-notes/touch-ui-features-status.md) pagina van de Status van de Eigenschap van 0} Aanraakinterface[

### Hulpbronnen {#resources-to-help}

Voor achtergrondinformatie over basisverwerking:

* [ Authoring Pagina&#39;s ](/help/sites-authoring/page-authoring.md).

Voor gedetailleerde ontwikkelingsinformatie:

* [ Aanraakgevoelige architectuur UI ](/help/sites-developing/touch-ui-concepts.md).
* Gebruik de [ Hulpmiddelen van de Modernisering van AEM ](/help/sites-developing/modernization-tools.md) om component uit te zetten geeft dialogen van klassieke UI in aanraking-toegelaten UI uit.

* [ Structuur van aanraking-toegelaten UI ](/help/sites-developing/touch-ui-structure.md).

* [ die de consoles in aanraking-toegelaten UI aanpassen ](/help/sites-developing/customizing-consoles-touch.md) (omvat steekproefcode).

* [ het Aanpassen van pagina authoring in touch-enabled UI ](/help/sites-developing/customizing-page-authoring-touch.md) (omvat steekproefcode).

* {de documentatie van 0} granite UI ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html).[
