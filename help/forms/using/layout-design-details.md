---
title: Indelingsontwerp
seo-title: Indelingsontwerp
description: Layout Design Details legt uit hoe u lay-outs kunt maken die voor uw brieven of Interactieve Mededelingen moeten worden gebruikt.
seo-description: Layout Design Details legt uit hoe u lay-outs kunt maken die voor uw brieven of Interactieve Mededelingen moeten worden gebruikt.
uuid: 469a8a71-88f7-4102-bb02-38ed05390f6c
content-type: reference
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 683809ac-089b-49bf-a72c-67d32439081f
docset: aem65
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Indelingsontwerp{#layout-design}

XFA-formuliersjablonen of XDP&#39;s zijn de sjablonen voor:

* [Letters](/help/forms/using/create-letter.md)
* [Kanaal](/help/forms/using/web-channel-print-channel.md#printchannel) van de druk van [Interactieve Mededelingen](/help/forms/using/interactive-communications-overview.md)

* Lay-outfragmenten

Een XDP is ontworpen in de Ontwerper van de Vormen van Adobe. Dit artikel bevat informatie over hoe u XDP&#39;s kunt ontwerpen voor het maken van effectieve overeenkomsten/interactieve communicatie, zoals waar u formuliervelden of doelgebieden wilt gebruiken en wanneer u lay-outfragmenten wilt gebruiken.

## Een lay-out maken voor letters of voor het afdrukkanaal van Interactieve communicatie {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Een lay-out bepaalt de grafische lay-out van een brief/drukkanaal van een Interactieve Mededeling. De indeling kan typische formuliervelden bevatten, zoals &quot;Adres&quot; en &quot;Referentienummer&quot;. Het bevat ook lege subformulieren die doelgebieden aangeven. Maak de indeling in de formulierontwerper en wanneer deze is voltooid, uploadt de Application Specialist de indeling naar de AEM-server. Van daar, kunt u de lay-out selecteren wanneer het creëren van een correspondentiesjabloon of een drukkanaal van een Interactieve Mededeling.

![Designer: een lay-out maken](assets/claimsubrogationlayout.png)

Ga als volgt te werk om lay-outs voor letters/drukkanaal van Interactieve Mededelingen tot stand te brengen:

1. Analyseer de lay-out en bepaal de inhoud die over alle pagina&#39;s wordt herhaald; De koptekst en voettekst van de pagina passen meestal in deze categorie. Deze inhoud wordt op stramienpagina&#39;s van de layout geplaatst. De resterende inhoud gaat naar de tekstpagina&#39;s van de layout. In een beleidsjasje, kunnen het embleem en bedrijfadres aan de kopbal en footer van de hoofdpagina worden toegevoegd. Bericht van annulering gebruikt bijvoorbeeld dezelfde indeling.
1. Teken bij het ontwerpen van de tekstpagina&#39;s de pagina-inhoud op in secties. Elke sectie is ontworpen als een subformulier dat is ingesloten in de indeling zelf of als een fragmentindeling. Als de sectie tabel bevat, modelleert u de sectie als een lay-outfragment.
1. Een lay-out kan als volgt worden ontworpen:

   1. Maak elke sectie als een afzonderlijk subformulier dat alle elementen van de sectie bevat.
   1. Elk subformulier voor secties onderliggend maken van hetzelfde bovenliggende subformulier. De indeling van het bovenliggende subformulier is zo ingesteld dat de secties hieronder kunnen worden verplaatst als grote gegevens in vorige secties worden samengevoegd.
   1. Sectie Primaire verblijfplaats kan ook in andere indelingen worden hergebruikt. Maak het als een fragmentlay-out.
   1. Sectie Aanvullende interessdetails bevatten slechts twee elementen die onder elkaar zijn geplaatst, kunnen grote gegevens bevatten en zijn ontworpen als stroominhoud.
   1. Andere secties bevatten elementen op specifieke posities, zodat ze zijn ontworpen als gepositioneerde indeling.
   1. Een sectie onderverdelen in subformulieren als de sectie elementen op specifieke posities bevat, en deze elementen grote hoeveelheden gegevens bevatten. Rangschik de subformulieren vervolgens om het gewenste gedrag te bereiken.
   1. Voor de sectie Primaire woonplaats voegt u een plaatsaanduiding als doelgebied toe. Deze tijdelijke aanduiding is gebonden aan een fragment voor de primaire verblijfplaats op het moment dat er een letter/interactieve communicatie wordt ontworpen.
   1. Upload de indeling (en het eventuele fragment dat de indeling gebruikt) naar de AEM Forms-server.

### Subformulier gebruiken in een XDP-sjabloon {#usesubformxdp}

Nadat u de indeling hebt geanalyseerd die nodig is om uw interactieve communicatie te maken, kunt u subformulieren in de XDP-sjabloon maken met Forms Designer. Lege subformuliercomponenten die in de XDP-sjabloon worden gebruikt, resulteren in de weergave van doelgebieden in het kanaal Afdrukken van de interactieve communicatie.

>[!NOTE]
>
>Voeg inhoud toe aan het kanaal van de Druk van de Interactieve Mededeling in plaats van inhoud toe te voegen aan de subformuliercomponent in het malplaatje XDP. Voeg inhoud aan de doelgebieden in het kanaal van de Druk toe gebruikend [documentfragmenten, grafieken, beelden](create-interactive-communication.md#step2), en lay-outfragmenten.

Voer de volgende stappen uit om subformulier in een XDP-sjabloon te gebruiken:

1. Open Forms Designer, selecteer **Bestand** > **Nieuw** > **Een leeg formulier** gebruiken, tik op **Volgende** en vervolgens op **Voltooien** om het formulier te openen voor het maken van een sjabloon.

   Selecteer de opties **Objectbibliotheek** en **Object** in het menu **Venster** .

1. Sleep de **subformuliercomponent** van de **objectbibliotheek** naar het formulier.

   ![Componentontwerper](assets/subform_component_designer_new.png)

1. Selecteer het subformulier om de opties voor het subformulier in het venster **Object** in het rechterdeelvenster weer te geven.
1. Selecteer het tabblad **Subformulier** en selecteer **Overlopen** in de vervolgkeuzelijst **Inhoud** . Sleep het linkereindpunt van het subformulier om de lengte aan te passen.

   ![Subformulier met stroominhoud](assets/object_subform_flowed_new.png)

1. Op het tabblad **Binding** :

   1. Geef een naam voor het subformulier op in het veld **Naam** .
   1. Selecteer **Geen gegevensbinding** in de vervolgkeuzelijst **Gegevensbinding** .

1. Selecteer op dezelfde manier het basissubformulier in het linkerdeelvenster.

   ![Basissubformulier](assets/root_subform_designer_new.png)

1. Selecteer het tabblad **Subformulier** en selecteer **Overlopen** in de vervolgkeuzelijst **Inhoud** . Op het tabblad **Bindingen** :

   1. Geef een naam voor het subformulier op in het veld **Naam** .
   1. Selecteer **Geen gegevensbinding** in de vervolgkeuzelijst **Gegevensbinding** .
   Herhaal stap 2 tot en met 5 om meer subformulieren aan de XDP-sjabloon toe te voegen. Voeg alleen tijdens het ontwerpen van de interactieve communicatie [tekst, documentfragmenten, afbeeldingen en grafieken](create-interactive-communication.md#step2) toe aan de doelgebieden.

1. Selecteer **Bestand** > **Opslaan als** om het bestand op te slaan op het lokale bestandssysteem:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef een naam op voor de XDP-sjabloon.
   1. Selecteer **.xdp** in de vervolgkeuzelijst **Opslaan als type** .

   1. Tik op **Opslaan**.

### Afbeeldingsveldcomponent gebruiken in een XDP-sjabloon {#use-image-field-component-in-an-xdp-template}

Gebruik Afbeeldingsveld of Subformulier in de XDP-sjabloon en voeg een afbeelding toe tijdens het ontwerpen van de interactieve communicatie.

>[!NOTE]
>
>Voeg afbeelding toe aan het kanaal Afdrukken van de interactieve communicatie in plaats van afbeelding toe te voegen aan het afbeeldingsveld of de subformuliercomponent in de XDP-sjabloon. Zie Inhoud [toevoegen aan de interactieve communicatie](../../forms/using/create-interactive-communication.md#step2)voor meer informatie.

Voer de volgende stappen uit om de component van het Gebied van het Beeld in een malplaatje te gebruiken XDP:

1. Sleep de component **Afbeeldingsveld** van de **objectbibliotheek** naar het formulier.
1. Selecteer het subformulier om de opties voor het subformulier in het venster **Object** in het rechterdeelvenster weer te geven.
1. Op het tabblad **Binding** :

   1. Geef een naam voor het afbeeldingsveld op in het veld **Naam** .
   1. Selecteer **Geen gegevensbinding** in de vervolgkeuzelijst **Gegevensbinding** .

### XDP-sjabloon maken voor layoutfragmenten {#xdplayoutfragments}

Gebruik de component Tabel in Forms Designer om lay-outfragmenten te maken en gebruik deze om tabellen te maken tijdens het ontwerpen van het kanaal Afdrukken voor interactieve communicatie. Wanneer u lay-outfragmenten gebruikt om tabellen te maken, zorgt u ervoor dat de tabelinhoud de structuur behoudt wanneer het webkanaal automatisch wordt gegenereerd met behulp van het afdrukkanaal.

>[!NOTE]
>
>Voer tekst in de tabelcellen in of [maak alleen binding met de formuliergegevensmodelobjecten](create-interactive-communication.md#step2) tijdens het ontwerpen van de interactieve communicatie.

Voer de volgende stappen uit om de component Tabel in de XDP-sjabloon te gebruiken met Forms Designer:

1. Sleep de component **Tabel** van de **Objectbibliotheek** naar het formulier.
1. In het dialoogvenster Tabel **** invoegen:

   1. Geef het aantal rijen en kolommen voor de tabel op.
   1. Schakel het selectievakje Koptekstrij **opnemen in tabel** in om een rij voor de tabelkoptekst op te nemen.
   1. Tik op **OK**.

1. Tik **+** in het linkerdeelvenster naast de naam van de tabel, klik met de rechtermuisknop op de celnamen in de koptekst en andere rijen en selecteer **Naam van object** wijzigen om de tabelcellen een andere naam te geven.
1. Klik op de tekstvelden voor de tabelkoptekst in de **ontwerpweergave** en geef deze een andere naam.
1. Sleep de component **Tekstveld** van de **objectbibliotheek** naar elke tabelcel in de **ontwerpweergave**. Voer deze stap uit om tabelcellen te kunnen binden aan de formuliergegevensmodelobjecten tijdens het ontwerpen van de interactieve communicatie.

   ![Tekstvelden in een tabel](assets/text_fields_table_new.png)

1. Selecteer de naam van de rij in het linkerdeelvenster en selecteer **Object** > **Binding** > Rij **herhalen voor elk gegevensitem**. Voer deze stap uit om ervoor te zorgen dat als een band tussen de lijstcellen van deze rij met de modelvoorwerpen van vormgegevens van inzamelingstype wordt gecreeerd, de lijstrij automatisch voor elk gegevenspunt wordt herhaald beschikbaar in het gegevensbestand.

   Voer tekst in de tabelcellen in of [maak alleen binding met de formuliergegevensmodelobjecten](create-interactive-communication.md#step2) tijdens het ontwerpen van de interactieve communicatie.

1. Selecteer **Bestand** > **Opslaan als** om het bestand op te slaan op het lokale bestandssysteem:

   1. Navigeer naar de locatie waar u het bestand wilt opslaan en geef de naam voor de XDP-sjabloon op.
   1. Selecteer **.xdp** in de vervolgkeuzelijst **Opslaan als type** .

   1. Tik op **Opslaan**.

### XDP-sjabloon uploaden naar de AEM Forms-server {#uploadxdptemplate}

Nadat u een XDP-sjabloon hebt gemaakt met de Forms Designer, moet u de sjabloon uploaden naar de AEM Forms-server, zodat de sjabloon beschikbaar is voor gebruik tijdens het maken van de interactieve communicatie.

1. Selecteer **Formulieren** > **Formulieren en documenten**.
1. Tik op **Maken** > **Bestand uploaden**.
1. Navigeer naar de locatie van de XDP-sjabloon in het lokale bestandssysteem en tik op **Openen** om de XDP-sjabloon te importeren naar de AEM Forms-server.

## Schema gebruiken {#using-schema}

U kunt een schema in een lay-out- of lay-outfragment gebruiken, maar het is niet verplicht. Als u een schema gebruikt, zorg het volgende ervoor:

1. Layout en alle fragmentlay-outs die in een brief/Interactieve Communicatie worden gebruikt gebruiken het zelfde schema zoals de brief/Interactieve Communicatie.
1. Alle velden die moeten worden gevuld met gegevens, zijn gebonden aan het schema.

## Betrouwbare velden maken {#creating-relatable-fields}

Standaard worden alle velden beschouwd als relatief ten opzichte van verschillende andere gegevensbronnen. Als uw layout velden bevat die niet kunnen worden vergeleken met een gegevensbron, geeft u het veld een naam met het achtervoegsel &quot;_int&quot; (internal); bijvoorbeeld pageCount_int.

Een relatable veld moet:

* een XFA &lt;field> of &lt;exclGroup> zijn
* hebben een XFA-bindingsverwijzing
* als het een &lt;exclGroup> is, moet het ten minste één onderliggend keuzerondje hebben; anders kan het waardetype niet worden bepaald

Een relatable veld moet:

* hebben een naam

Een relatable veld mag niet:

* Een achtervoegsel &quot;_int&quot; in de naam opnemen
* hebben binding ingesteld als &quot;none&quot;
* een onderliggend element zijn van een &lt;exclGroup>-element

Zolang een relatable gebied aan de hierboven beschreven criteria voldoet, kan het op om het even welke plaats en bij om het even welke het nesten diepte in de lay-out zijn. U kunt relatable gebieden binnen basispagina&#39;s gebruiken.

De lay-outconfiguratie van velden is flexibeler dan doelgebiedsubformulieren; deze zijn echter gekoppeld aan één waardetype. U kunt een veld groter maken of instellen op een vaste breedte en hoogte, enzovoort. Het opgeloste module of regelresultaat wordt in het veld geduwd.

## Bepalen wanneer subformulieren en tekstvelden worden gebruikt {#deciding-when-to-use-subforms-and-text-nbsp-fields}

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
   <td><p>Elementen zoals het logo en het adres van uw organisatie worden weergegeven op alle pagina's van een brief/interactieve communicatie. In dit geval maakt u formuliervelden voor deze elementen en plaatst u deze op de basispagina. Als u de veldbinding instelt op Geen gegevensbinding, worden de velden Geen weergegeven als relateerbare velden in de Letter/Interactive Communication Editor. Als u een bepaald type inhoud aan deze velden wilt koppelen, moeten deze gebonden zijn.</p> <p>Als uw bedrijfsadres meer dan één lijn van gegevens bevat, gebruik tekstgebied met de "Meerdere Lijnen van de Toestaan"optie om het adres op de lay-out te vertegenwoordigen.</p> <p>Als het gegevenstype van een tekstveld is ingesteld op onbewerkte tekst, wordt de onbewerkte tekstversie van de module-uitvoer gebruikt in plaats van de versie met tekstopmaak (alle opmaak wordt genegeerd). Als u de opmaak wilt behouden, stelt u het gegevenstype van het tekstveld in op RTF-tekst.</p> </td>
  </tr>
  <tr>
   <td><p>Tekst loopt over</p> </td>
   <td><p>Tekstvelden en afbeeldingsvelden worden gebruikt op stramienpagina's. Basispagina's kunnen subformulieren niet gebruiken als doelgebieden.</p> </td>
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

Gebruik de serverrenderindeling van de indeling naar dynamisch XML-formulier; anders, kunnen om het even welke brieven/Interactieve Mededelingen die op deze lay-out worden gebaseerd niet correct teruggeven. Standaard wordt de serverrenderindeling in Forms Designer ingesteld op Dynamisch XML-formulier. U zorgt ervoor dat de juiste indeling wordt gebruikt:

* Klik in Designer op **Bestand** > **Formuliereigenschappen** > **Standaardwaarden** en controleer of de instelling PDF renderen/Indeling is ingesteld op Dynamisch XML-formulier.

