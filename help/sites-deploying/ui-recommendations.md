---
title: Gebruikersinterface Recommendations voor klanten
seo-title: Gebruikersinterface Recommendations voor klanten
description: Een lijst met aanbevelingen voor de klassieke en geoptimaliseerde gebruikersinterfaces.
seo-description: Een lijst met aanbevelingen voor de klassieke en geoptimaliseerde gebruikersinterfaces.
uuid: 9ec2c9de-a79e-4f2c-a90f-b38ba9553e07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8f06d4b6-7d30-4ebc-9c6a-3bb8607a9be8
docset: aem65
translation-type: tm+mt
source-git-commit: 7035c19a109ff67655ee0419aa37d1723e2189cc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Gebruikersinterface Recommendations voor klanten{#user-interface-recommendations-for-customers}

Adobe Experience Manager wordt geleverd met twee UI&#39;s: de Unified Experience Cloud UI (ook wel de interface met aanraakbediening genoemd) en de klassieke UI.

Dit document is bedoeld om klanten te helpen een keuze te maken over welke interface ze moeten gebruiken, afhankelijk van hun situatie.

Belangenvoorwaarden:

* **UI (of standaard UI)**
Modern gebruikersinterface die in 5.6.0 als technologievoorproef werd geïntroduceerd en in verdere versies werd uitgebreid. De interface is gebaseerd op de ervaring van één gebruiker voor de Adobe Experience Cloud, die voorheen wel een interface met aanraakbediening of een interface met aanraakbediening werd genoemd.

* **Klassieke interface**
UIUser gebaseerd op technologie ExtJS die met CQ 5.1 in 2008 werd geïntroduceerd.

* **Site-**
beheermogelijkheden om de sitehiërarchie te beheren (verwijzingen verplaatsen, activeren, beheren) en nieuwe pagina&#39;s te maken.

* **Page**
AuthoringCapabilities om de inhoud van een pagina toe te voegen of te bewerken.

* **DAM/Assets**
AdminCapabilities voor het beheren van digitale elementen (waaronder afbeeldingen, video, documenten, downloads).

* ****
ContextHubCapabilities om informatie over de bezoeker samen te voegen en het voor diverse doeleinden te gebruiken. Verstrekt een gebruikersinterface om personen te simuleren die de plaats bezoeken. Beginnend AEM 6.2, vervangt ContextHub de vorige technologie, de Context van de Cliënt.

## Algemeen {#general}

In de afgelopen jaren heeft Adobe alle Adobe Experience Cloud-oplossingen bijgewerkt met één gebruikersinterface. Gebruikers in de Experience Cloud-oplossingen genieten van een consistente ervaring met gangbare patronen voor het gebruik en het gebruik van de toepassingen. Met elke versie, heeft Adobe het gebruikersinterface verfijnd die op terugkoppelen van klanten wordt gebaseerd die over de diverse oplossingen werken.

De oorspronkelijke gebruikersinterface voor Adobe Experience Manager (voorheen CQ5 genoemd), die in 2008 werd geïntroduceerd en door klanten met versies 5.0-5.6.1 werd gebruikt, staat in AEM 6.5. Dit garandeert dat klanten een update naar versie 6.5 kunnen uitvoeren en kunnen profiteren van een bijgewerkt platform met nieuwe mogelijkheden en dezelfde gebruikersinterface kunnen blijven gebruiken.

Adobe raadt klanten aan om in 2018/2019 over te schakelen naar de nieuwe interface. Dit kan of tijdens de update aan 6.5 - of in een afzonderlijke projecten na de update worden gedaan, die de noodzakelijke aanpassingen aan de aanpassingen en componentendialogen zou omvatten.

De klassieke gebruikersinterface is vervangen door AEM 6.4 en Adobe is niet van plan om verdere verbeteringen aan te brengen in de klassieke gebruikersinterface. Merk op dat Klassieke UI volledig wordt gesteund terwijl wordt afgekeurd.

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
     <li>De standaardinterface gebruiken voor sitebeheer, elementen, ... etc.<br /> </li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui">Uw interface selecteren</a>.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe raadt aan de <a href="/help/sites-developing/modernization-tools.md">AEM Moderniseringsgereedschappen</a> te gebruiken om de componenten bij te werken.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Heeft een site gemaakt die de ClientContext met integratie gebruikt.<br /> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen, ... enz.</li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui">Uw interface selecteren</a>.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe raadt aan de <a href="/help/sites-developing/modernization-tools.md">AEM Moderniseringsgereedschappen</a> te gebruiken om de componenten bij te werken.</li>
     <li>Vorm ContextHub (de vervanging voor ClientContext) en werk de paginasjablonen bij om ContextHub te gebruiken. Merk op dat ContextHub een verenigbaarheidswijze heeft die het laden van douaneClientContext opslag toestaat.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Heeft CQ/AEM jarenlang gebruikt.</p> <p>De interface voor het product (bijvoorbeeld Sitebeheer) is uitgebreid en componenten met uitgebreide bewerkingsdialoogvensters zijn samengesteld.</p> </td>
   <td><p>Update aan 6.5 en vorm klassieke UI als gebrek voor paginascreatie voor alle gebruikers. Zie <a href="#selecting-your-ui">Uw interface selecteren</a>.</p> <p>Start vervolgens een project om de deeldialoogvensters aan te passen en te optimaliseren in de indeling Coral 3. Zie <a href="#resources-to-help">Bronnen voor Help</a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Veelgestelde vragen {#faq}

Raadpleeg het Knowledge Base-artikel [Touch UI Authoring FAQ](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html) voor meer informatie. met inbegrip van om het even welke informatie over het afschilderingsprogramma voor klassieke UI.

### UI {#selecting-your-ui} selecteren

Zie [Uw interface selecteren](/help/sites-authoring/select-ui.md) voor informatie over het configureren van uw systeem zoals vereist.

### UI-status voor aanraakbediening {#touch-enabled-ui-status}

Zie [Nieuwe functies](/help/release-notes/release-notes.md#what-s-new) in de Opmerkingen bij de release voor meer informatie over de verbeteringen aan de interface met aanraakbediening in AEM 6.5.

Een volledig overzicht vindt u op de pagina [Status van aanraakinterface](/help/release-notes/touch-ui-features-status.md)

### Bronnen voor Help {#resources-to-help}

Voor achtergrondinformatie over basisverwerking:

* [Pagina&#39;s](/help/sites-authoring/page-authoring.md) ontwerpen.

Voor gedetailleerde ontwikkelingsinformatie:

* [UI-architectuur](/help/sites-developing/touch-ui-concepts.md) met aanraakbediening.
* Met de [AEM Moderniseringsgereedschappen](/help/sites-developing/modernization-tools.md) kunt u dialoogvensters voor bewerken van componenten omzetten van de klassieke interface naar de interface voor aanraakbediening.

* [Structuur van de interface](/help/sites-developing/touch-ui-structure.md) met aanraakbediening.

* [De consoles aanpassen in de interface](/help/sites-developing/customizing-consoles-touch.md)  met aanraakbediening (inclusief voorbeeldcode).

* [Aanpassen van het ontwerpen van pagina&#39;s in de interface](/help/sites-developing/customizing-page-authoring-touch.md)  met aanraakbediening (inclusief voorbeeldcode).

* [AEM Gem-sessie bij aanpassing](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html) met aanraakbediening.
* [Granite UI-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html).

