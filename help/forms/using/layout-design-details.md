---
title: Indelingsontwerp
description: Layout Design Details legt uit hoe u lay-outs kunt maken die voor uw brieven of Interactieve Mededelingen moeten worden gebruikt.
content-type: reference
topic-tags: correspondence-management, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Correspondence Management
exl-id: 9e1b0067-c7dc-4bbb-a209-d674592be858
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2171'
ht-degree: 0%

---

# Indelingsontwerp{#layout-design}

XFA-formuliersjablonen of XDP&#39;s zijn de sjablonen voor:

* [Letters](/help/forms/using/create-letter.md)
* [ het kanaal van de Druk ](/help/forms/using/web-channel-print-channel.md#printchannel) van [ Interactieve Mededelingen ](/help/forms/using/interactive-communications-overview.md)

* Layoutfragmenten

Een XDP is ontworpen in Adobe Forms Designer. Dit artikel bevat informatie over hoe u XDP&#39;s kunt ontwerpen voor het maken van effectieve overeenkomsten/interactieve communicatie, zoals waar u formuliervelden of doelgebieden wilt gebruiken en wanneer u lay-outfragmenten wilt gebruiken.

## Een lay-out maken voor letters of voor het afdrukkanaal van Interactieve communicatie {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Een lay-out bepaalt de grafische lay-out van een brief/drukkanaal van een Interactieve Mededeling. De indeling kan typische formuliervelden bevatten, zoals &quot;Adres&quot; en &quot;Referentienummer&quot;. Het bevat ook lege subformulieren die doelgebieden aangeven. Maak de indeling in de formulierontwerper en wanneer deze is voltooid, uploadt de Application Specialist de indeling naar AEM server. Van daar, kunt u de lay-out selecteren wanneer het creëren van een correspondentiesjabloon of een drukkanaal van een Interactieve Mededeling.

![ Designer: creeer een lay-out ](assets/claimsubrogationlayout.png)

Ga als volgt te werk om lay-outs voor letters/drukkanaal van Interactieve Mededelingen tot stand te brengen:

1. Analyseer de lay-out en bepaal de inhoud die over alle pagina&#39;s wordt herhaald; gewoonlijk passen de paginakop en de footer in deze categorie. Deze inhoud wordt op stramienpagina&#39;s van de layout geplaatst. De resterende inhoud gaat naar de tekstpagina&#39;s van de layout. In een beleidsjasje, kunnen het embleem en bedrijfadres aan de kopbal en footer van de hoofdpagina worden toegevoegd. Bericht van annulering gebruikt bijvoorbeeld dezelfde indeling.
1. Teken bij het ontwerpen van de tekstpagina&#39;s de pagina-inhoud op in secties. Elke sectie is ontworpen als een subformulier dat is ingesloten in de indeling zelf of als een fragmentindeling. Als de sectie tabel bevat, modelleert u de sectie als een lay-outfragment.
1. Een lay-out kan als volgt worden ontworpen:

   1. Maak elke sectie als een afzonderlijk subformulier dat alle elementen van de sectie bevat.
   1. Elk subformulier voor secties onderliggend maken van hetzelfde bovenliggende subformulier. De indeling van het bovenliggende subformulier is zo ingesteld dat de secties hieronder kunnen worden verplaatst als er grote gegevens zijn samengevoegd in vorige secties.
   1. Sectie Primaire verblijfplaats kan ook in andere indelingen worden hergebruikt. Maak het als een fragmentlay-out.
   1. Sectie Aanvullende interessdetails bevatten slechts twee elementen die onder elkaar zijn geplaatst, kunnen grote gegevens bevatten en zijn ontworpen als stroominhoud.
   1. Andere secties bevatten elementen op specifieke posities, zodat ze zijn ontworpen als gepositioneerde indeling.
   1. Een sectie onderverdelen in subformulieren als de sectie elementen op specifieke posities bevat, en deze elementen grote hoeveelheden gegevens bevatten. Rangschik de subformulieren vervolgens om het gewenste gedrag te bereiken.
   1. Voor de sectie Primaire woonplaats voegt u een plaatsaanduiding als doelgebied toe. Deze tijdelijke aanduiding is gebonden aan een fragment voor de primaire verblijfplaats op het moment dat er een letter/interactieve communicatie wordt ontworpen.
   1. Upload de lay-out (en het eventuele fragment dat de lay-out gebruikt) naar de AEM Forms-server.

### Subformulier gebruiken in een XDP-sjabloon {#usesubformxdp}

Nadat u de indeling hebt geanalyseerd die nodig is om uw interactieve communicatie te maken, kunt u subformulieren in de XDP-sjabloon maken met Forms Designer. Lege subformuliercomponenten die in de XDP-sjabloon worden gebruikt, resulteren in de weergave van doelgebieden in het kanaal Afdrukken van de interactieve communicatie.

>[!NOTE]
>
>Voeg inhoud toe aan het kanaal van de Druk van de Interactieve Mededeling in plaats van inhoud toe te voegen aan de subformuliercomponent in het malplaatje XDP. Voeg inhoud aan de doelgebieden in het kanaal van de Druk toe gebruikend [ documentfragmenten, grafieken, beelden ](create-interactive-communication.md#step2), en lay-outfragmenten.

Voer de volgende stappen uit om subformulier in een XDP-sjabloon te gebruiken:

1. Open Forms Designer, uitgezochte **Dossier** > **Nieuw** > **Gebruik een lege vorm**, selecteer **daarna**, en selecteer dan **Afwerking** om de vorm voor malplaatjeverwezenlijking te openen.

   Zorg ervoor dat de **Bibliotheek van Objecten** en **3} opties van Objecten {van het** Venster **menu worden geselecteerd.**

1. Sleep-en-daling de **Subform** component van de **Bibliotheek van Objecten** aan de vorm.

   ![ Component Designer ](assets/subform_component_designer_new.png)

1. Selecteer subform om de opties voor subform in het **venster van Objecten** in de juiste ruit te tonen.
1. Selecteer het **Subform** lusje en selecteer **Overlopen** van de **Inhoud** drop-down lijst. Sleep het linkereindpunt van het subformulier om de lengte aan te passen.

   ![ Gestroomd Subform ](assets/object_subform_flowed_new.png)

1. In het **Bindende** lusje:

   1. Specificeer een naam voor subform op het **gebied van de Naam**.
   1. Selecteer **Geen gegevensband** van de **Gegevens die** drop-down lijst binden.

1. Selecteer op dezelfde manier het basissubformulier in het linkerdeelvenster.

   ![ Subform van de Wortel ](assets/root_subform_designer_new.png)

1. Selecteer het **Subform** lusje en selecteer **Overlopen** van de **Inhoud** drop-down lijst. In het **Bindingen** lusje:

   1. Specificeer een naam voor subform op het **gebied van de Naam**.
   1. Selecteer **Geen gegevensband** van de **Gegevens die** drop-down lijst binden.

   Herhaal stap 2-5 om meer subformulieren aan de XDP-sjabloon toe te voegen. Voeg [ tekst, documentfragmenten, beelden, en grafieken ](create-interactive-communication.md#step2) aan de doelgebieden slechts terwijl het ontwerpen van de Interactieve Mededeling toe.

1. Selecteer **Dossier** > **sparen als** om het dossier op het lokale dossiersysteem op te slaan:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef een naam op voor de XDP-sjabloon.
   1. Selecteer **.xdp** van **sparen als type** drop-down lijst.

   1. Selecteer **sparen**.

### De component van het Gebied van het Beeld van het Gebruik in een malplaatje XDP {#use-image-field-component-in-an-xdp-template}

Gebruik Afbeeldingsveld of Subformulier in de XDP-sjabloon en voeg een afbeelding toe tijdens het ontwerpen van de interactieve communicatie.

>[!NOTE]
>
>Voeg afbeelding toe aan het kanaal Afdrukken van de interactieve communicatie in plaats van afbeelding toe te voegen aan het afbeeldingsveld of de subformuliercomponent in de XDP-sjabloon. Voor meer informatie, zie [ Toevoegend inhoud aan de Interactieve Mededeling ](../../forms/using/create-interactive-communication.md#step2).

Voer de volgende stappen uit om de component van het Gebied van het Beeld in een malplaatje te gebruiken XDP:

1. De belemmering-en-daling de **component van het Gebied van het Beeld 1} van de** Bibliotheek van Objecten **aan de vorm.**
1. Selecteer subform om de opties voor subform in het **venster van Objecten** in de juiste ruit te tonen.
1. In het **Bindende** lusje:

   1. Specificeer een naam voor het beeldgebied op het **gebied van de Naam**.
   1. Selecteer **Geen gegevensband** van de **Gegevens die** drop-down lijst binden.

### XDP-sjabloon maken voor layoutfragmenten {#xdplayoutfragments}

Gebruik de component Tabel in Forms Designer om lay-outfragmenten te maken en gebruik deze om tabellen te maken terwijl u het kanaal Afdrukken van interactieve communicatie ontwerpt. Wanneer u lay-outfragmenten gebruikt om tabellen te maken, zorgt u ervoor dat de tabelinhoud de structuur behoudt wanneer het webkanaal automatisch wordt gegenereerd met behulp van het afdrukkanaal.

>[!NOTE]
>
>Ga tekst in de lijstcellen in of [ creeer band met de modelvoorwerpen van vormgegevens ](create-interactive-communication.md#step2) slechts terwijl het ontwerpen van de Interactieve Mededeling.

Voer de volgende stappen uit om de component van de Lijst in het malplaatje te gebruiken XDP gebruikend Forms Designer:

1. Sleep-en-daling de **component van de Lijst** van de **Bibliotheek van Objecten** aan de vorm.
1. In de **dialoog van de Lijst van het Tussenvoegsel**:

   1. Geef het aantal rijen en kolommen voor de tabel op.
   1. Selecteer **omvatten de Rij van de Kopbal in Lijst** checkbox om een rij voor de lijstkopbal te omvatten.
   1. Selecteer **O.K.**.

1. Selecteer **+** in de linkerruit naast de naam van de lijst, klik celnamen inbegrepen in de kopbal en andere rijen met de rechtermuisknop aan, en selecteer **anders noemen Voorwerp** om de lijstcellen anders te noemen.
1. Klik de de tekstgebieden van de lijstkopbal in de **Mening van het Ontwerp** en noem hen anders.
1. De belemmering-en-daling de **component van het Gebied van de Tekst van de** Bibliotheek van Objecten **aan elke lijstcel in de** Mening van het Ontwerp **.** Voer deze stap uit om tabelcellen te kunnen binden aan de formuliergegevensmodelobjecten tijdens het ontwerpen van de interactieve communicatie.

   ![ de gebieden van de Tekst in een lijst ](assets/text_fields_table_new.png)

1. Selecteer de naam van de rij van de linkerruit en selecteer **Voorwerp** > **Bindend** > **Rij voor Elk Punt van Gegevens** herhalen. Voer deze stap uit om ervoor te zorgen dat als een band tussen de lijstcellen van deze rij met de modelvoorwerpen van vormgegevens van inzamelingstype wordt gecreeerd, de lijstrij automatisch voor elk gegevenspunt wordt herhaald beschikbaar in het gegevensbestand.

   Ga tekst in de lijstcellen in of [ creeer band met de modelvoorwerpen van vormgegevens ](create-interactive-communication.md#step2) slechts terwijl het ontwerpen van de Interactieve Mededeling.

1. Selecteer **Dossier** > **sparen als** om het dossier op het lokale dossiersysteem op te slaan:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef de naam voor de XDP-sjabloon op.
   1. Selecteer **.xdp** van **sparen als type** drop-down lijst.

   1. Selecteer **sparen**.

### XDP-sjabloon uploaden naar de AEM Forms-server {#uploadxdptemplate}

Nadat u een XDP-sjabloon hebt gemaakt met de Forms Designer, moet u de sjabloon uploaden naar de AEM Forms-server, zodat de sjabloon beschikbaar is voor gebruik tijdens het maken van de interactieve communicatie.

1. Selecteer **Forms** > **Forms &amp; Documenten**.
1. Selecteer **creëren** > **Dossier uploadt**.
1. Navigeer aan de plaats van het malplaatje XDP op het lokale dossiersysteem en selecteer **Open** om het malplaatje XDP aan de server van AEM Forms in te voeren.

## Schema gebruiken {#using-schema}

U kunt een schema in een lay-out- of lay-outfragment gebruiken, maar het is niet verplicht. Als u een schema gebruikt, zorg het volgende ervoor:

1. Layout en alle fragmentlay-outs die in een brief/Interactieve Communicatie worden gebruikt gebruiken het zelfde schema zoals de brief/Interactieve Communicatie.
1. Alle velden die moeten worden gevuld met gegevens, zijn gebonden aan het schema.

## Betrouwbare velden maken {#creating-relatable-fields}

Standaard worden alle velden beschouwd als relatief ten opzichte van verschillende andere gegevensbronnen. Als uw layout velden bevat die niet kunnen worden vergeleken met een gegevensbron, geeft u het veld een naam met het achtervoegsel &quot;_int&quot; (internal), bijvoorbeeld pageCount_int.

Een relatable veld moet:

* een XFA &lt;field> of &lt;exclGroup> zijn
* hebben een XFA-bindingsverwijzing
* als het een &lt;exclGroup> is, moet het ten minste één onderliggend keuzerondje-veld hebben; anders kan het waardetype niet worden bepaald

Een relatable veld moet:

* hebben een naam

Een relatable veld mag niet:

* Een achtervoegsel &quot;_int&quot; in de naam opnemen
* hebben binding ingesteld als &quot;none&quot;
* onderliggende elementen zijn van een &lt;exclGroup>-element

Zolang een relatable gebied aan de hierboven beschreven criteria voldoet, kan het op om het even welke plaats en bij om het even welke het nesten diepte in de lay-out zijn. U kunt relatable gebieden binnen basispagina&#39;s gebruiken.

Velden zijn flexibeler in hun layoutconfiguratie dan doelgebiedsubformulieren, maar zijn gekoppeld aan één waardetype. U kunt een veld groter maken of instellen op een vaste breedte en hoogte, enzovoort. Het opgeloste module of regelresultaat wordt in het veld geduwd.

## Bepalen wanneer subformulieren en tekstvelden moeten worden gebruikt {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Gebruik een subformulier als u meerdere moduleinhoud wilt vastleggen in een verticaal-stroomindeling (meerdere alinea&#39;s of afbeeldingen) van boven naar beneden. In uw indeling moet rekening worden gehouden met het feit dat het subformulier in hoogte wordt vergroot om de inhoud ervan te kunnen bevatten. Als u er niet zeker van kunt zijn dat de lengte van de inhoud die aan het subformulier/doel is gekoppeld nooit de ruimte overschrijdt die voor het subformulier is gereserveerd in de indeling, maakt u het subformulier als onderliggend subformulier in een container met stroomsubformulieren. Dit proces zorgt ervoor dat indelingsobjecten onder het subformulier naar beneden stromen naarmate het subformulier groter wordt.

Gebruik een veld als u gegevens uit de module of gegevenswoordenboekelementen wilt vastleggen in het schema van uw layout (omdat velden zijn gebonden aan gegevens) of als u moduleinhoud wilt weergeven op een stramienpagina. Houd er rekening mee dat de inhoud van een stramienpagina niet kan doorlopen met inhoud van een tekstpagina. Zorg er dus voor dat het afbeeldingsveld wordt gebruikt als een koptekstlogo. Deze tabel bevat meer criteria om te bepalen wanneer een subformulier of een veld in een indeling moet worden gebruikt.

<table>
 <tbody>
  <tr>
   <td><p><strong>Een subformulier gebruiken wanneer</strong></p> </td>
   <td><p><strong>Een tekstveld gebruiken wanneer</strong></p> </td>
  </tr>
  <tr>
   <td><p>Het bevat een combinatie elementen, zoals een Achternaam en Voornaam</p> </td>
   <td><p>Het bevat één element, zoals een Aantal van het Beleid.</p> </td>
  </tr>
  <tr>
   <td><p>Dit omvat meerdere alinea's</p> </td>
   <td><p>Tekst is omwikkeld en uitgevuld</p> </td>
  </tr>
  <tr>
   <td><p>Herhalende, optionele en voorwaardelijke gegevensgroepen zijn gebonden aan subformulieren om het risico van ontwerpfouten te beperken die kunnen optreden als scripts worden gebruikt om dezelfde resultaten te bereiken</p> </td>
   <td><p>Elementen zoals het logo en het adres van uw organisatie worden op alle pagina's van een brief/interactieve communicatie weergegeven. In dit geval maakt u formuliervelden voor deze elementen en plaatst u deze op de basispagina. Als u de veldbinding instelt op Geen gegevensbinding, worden de velden Geen weergegeven als relateerbare velden in de Letter/Interactive Communication Editor. Als u een bepaald type inhoud aan deze velden wilt koppelen, moeten deze gebonden zijn.</p> <p>Als uw bedrijfsadres meer dan één lijn van gegevens bevat, gebruik tekstgebied met de "Meerdere Lijnen van de Toestaan"optie om het adres op de lay-out te vertegenwoordigen.</p> <p>Als het gegevenstype van een tekstveld is ingesteld op onbewerkte tekst, wordt de onbewerkte tekstversie van de module-uitvoer gebruikt in plaats van de versie met tekstopmaak (alle opmaak wordt genegeerd). Als u de opmaak wilt behouden, stelt u het gegevenstype van het tekstveld in op RTF-tekst.</p> </td>
  </tr>
  <tr>
   <td><p>Tekst loopt over</p> </td>
   <td><p>Tekstvelden en afbeeldingsvelden worden gebruikt op basispagina's. Basispagina's kunnen subformulieren niet gebruiken als doelgebieden.</p> </td>
  </tr>
  <tr>
   <td><p>Objecten worden gegroepeerd en ingedeeld zonder dat het subformulier wordt gebonden aan een gegevenselement</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><p>Het subformulier bevat een tekstveld. Het subformulier kan groter worden en andere objecten eronder in de indeling niet overschrijven.</p> </td>
   <td><p>U hebt eenvoudige toegang tot de gegevens nodig tijdens het postproces.</p> </td>
  </tr>
 </tbody>
</table>

## Herhalende elementen instellen {#setting-up-repetitive-elements}

Wanneer elementen zoals het logo en het adres van uw organisatie op alle pagina&#39;s van een brief/Interactieve Mededeling verschijnen, creeer vormgebieden voor die elementen en plaats hen op de hoofdpagina. Gebruik de binding Naam (veldnaam) voor deze velden.

## De serverrenderindeling opgeven {#specify-the-server-nbsp-render-format}

Gebruik de server-renderindeling van de layout naar dynamisch XML-formulier. Anders kunnen letters/interactieve communicatie op basis van deze indeling niet correct worden gerenderd. Standaard wordt de serverrenderindeling in Forms Designer ingesteld op Dynamisch XML-formulier. U zorgt ervoor dat de juiste indeling wordt gebruikt:

* In Designer, klik **Dossier** > **Eigenschappen van de Vorm** > **Gebreken**, en zorg ervoor dat de PDF teruggeeft/het Formaat plaatsen aan de Dynamische Vorm van XML wordt geplaatst.
