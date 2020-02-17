---
title: Aanbevelingen voor gebruikersinterface voor klanten
seo-title: Aanbevelingen voor gebruikersinterface voor klanten
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
source-git-commit: 5597fb39500ac1f85d03263bfa1e5239d35d2a2c

---


# Aanbevelingen voor gebruikersinterface voor klanten{#user-interface-recommendations-for-customers}

Adobe Experience Manager wordt geleverd met twee gebruikersinterface: de Unified Experience Cloud-gebruikersinterface (ook wel de interface met aanraakbediening genoemd) en de klassieke gebruikersinterface.

Dit document is bedoeld om klanten te helpen een keuze te maken over welke interface ze moeten gebruiken, afhankelijk van hun situatie.

Belangenvoorwaarden:

* **UI (of standaard UI)** Modern gebruikersinterface die in 5.6.0 als technologievoorproef werd geïntroduceerd en in verdere versies werd uitgebreid. De interface is gebaseerd op de ervaring van één gebruiker voor de Adobe Experience Cloud, voorheen bekend als interface met aanraakbediening of interface.

* **Klassieke gebruikersinterface** die op technologie ExtJS wordt gebaseerd die met CQ 5.1 in 2008 werd geïntroduceerd.

* **Sitebeheermogelijkheden** om de sitehiërarchie te beheren (verwijzingen verplaatsen, activeren, beheren) en nieuwe pagina&#39;s te maken.

* **Met de mogelijkheden voor paginaontwerp** kunt u de inhoud van een pagina toevoegen of bewerken.

* **DAM/Assets Admin** Capabilities voor het beheren van digitale elementen (waaronder afbeeldingen, video, documenten, downloads).

* **ContextHub** Mogelijkheden om informatie over de bezoeker samen te voegen en het voor diverse doeleinden te gebruiken. Verstrekt een gebruikersinterface om personen te simuleren die de plaats bezoeken. Beginnend AEM 6.2, vervangt ContextHub de vorige technologie, de Context van de Cliënt.

## Algemeen {#general}

De afgelopen jaren heeft Adobe alle Adobe Experience Cloud-oplossingen bijgewerkt met een uniforme gebruikersinterface. Gebruikers van de Experience Cloud-oplossingen genieten van een consistente ervaring met gangbare patronen voor het gebruik en het gebruik van de toepassingen. Bij elke release heeft Adobe de gebruikersinterface verfijnd op basis van feedback van klanten die met verschillende oplossingen werken.

De oorspronkelijke gebruikersinterface voor Adobe Experience Manager (voorheen bekend als CQ5), die in 2008 werd geïntroduceerd en werd gebruikt door klanten met versies 5.0-5.6.1, bevindt zich in AEM 6.5. Dit garandeert dat klanten een update naar versie 6.5 kunnen uitvoeren en kunnen profiteren van een bijgewerkt platform met nieuwe mogelijkheden en dezelfde gebruikersinterface kunnen blijven gebruiken.

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
   <td>Start nu nog Adobe Experience Manager.</td>
   <td>Gebruik de standaardinterface.</td>
  </tr>
  <tr>
   <td><p>Heeft AEM een tijdje gebruikt.</p> <p>Gebruikt de productUI uit-van-de-doos en ontwikkelde douanecomponenten voor de plaatsen.<br /> </p> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen, ... enz.<br /> </li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui">Uw gebruikersinterface</a>selecteren.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe raadt u aan de componenten bij te werken met het gereedschap <a href="/help/sites-developing/dialog-conversion.md">Dialoogomzetting</a> .</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Heeft een plaats gebouwd die ClientContext met integratie gebruikt.<br /> </td>
   <td>
    <ol>
     <li>Bijwerken naar 6.5</li>
     <li>De standaardinterface gebruiken voor sitebeheer, elementen, ... enz.</li>
     <li>Configureer de actie Pagina bewerken om de klassieke UI-pagina-editor te openen. Zie <a href="#selecting-your-ui">Uw gebruikersinterface</a>selecteren.</li>
    </ol> <p>In een tweede fase:</p>
    <ol>
     <li>Werk uw componentendialogen bij om het Coral 3 dialoogvakje formaat te gebruiken. Adobe raadt u aan de componenten bij te werken met het gereedschap <a href="/help/sites-developing/dialog-conversion.md">Dialoogomzetting</a> .</li>
     <li>Vorm ContextHub (de vervanging voor ClientContext) en werk de paginasjablonen bij om ContextHub te gebruiken. Merk op dat ContextHub een verenigbaarheidswijze heeft die het laden van douaneClientContext opslag toestaat.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><p>Heeft CQ/AEM jarenlang gebruikt.</p> <p>De interface voor het product (bijvoorbeeld Sitebeheer) is uitgebreid en componenten met uitgebreide bewerkingsdialoogvensters zijn samengesteld.</p> </td>
   <td><p>Update aan 6.5 en vorm klassieke UI als gebrek voor paginascreatie voor alle gebruikers. Zie <a href="#selecting-your-ui">Uw gebruikersinterface</a>selecteren.</p> <p>Start vervolgens een project om de deeldialoogvensters aan te passen en te optimaliseren in de indeling Coral 3. Zie <a href="#resources-to-help">Hulpbronnen</a>.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Veelgestelde vragen {#faq}

Raadpleeg het Knowledge Base-artikel, [Touch UI Authoring FAQ](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html), voor meer informatie. met inbegrip van om het even welke informatie over het afschilderingsprogramma voor klassieke UI.

### Gebruikersinterface selecteren {#selecting-your-ui}

Zie [Uw interface](/help/sites-authoring/select-ui.md) selecteren voor informatie over het configureren van uw systeem naar wens.

### UI-status voor aanraking {#touch-enabled-ui-status}

Voor meer informatie over de verbeteringen aan de interface met aanraakbediening in AEM 6.5 raadpleegt u [Nieuw](/help/release-notes/release-notes.md#what-s-new) in de opmerkingen bij de release.

Een volledig overzicht van de statuspagina van de functie [](/help/release-notes/touch-ui-features-status.md) TouchUI

### Hulpbronnen {#resources-to-help}

Voor achtergrondinformatie over basisverwerking:

* [Pagina&#39;s](/help/sites-authoring/page-authoring.md)ontwerpen.

Voor gedetailleerde ontwikkelingsinformatie:

* [UI-architectuur](/help/sites-developing/touch-ui-concepts.md)met aanraakbediening.
* Met het gereedschap [](/help/sites-developing/dialog-conversion.md) Dialoogconversie kunt u dialoogvensters voor het bewerken van componenten converteren van de klassieke interface naar de interface met aanraakbediening.

* [Structuur van de interface](/help/sites-developing/touch-ui-structure.md)met aanraakbediening.

* [De consoles aanpassen in de interface](/help/sites-developing/customizing-consoles-touch.md) met aanraakbediening (inclusief voorbeeldcode).

* [Aanpassen van het ontwerpen van pagina&#39;s in de interface](/help/sites-developing/customizing-page-authoring-touch.md) met aanraakbediening (inclusief voorbeeldcode).

* [AEM Gem-sessie bij aanpassing](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html)met aanraakbediening.
* [Granite UI-documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html).

