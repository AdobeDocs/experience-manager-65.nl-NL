---
title: Het gebruiken van grafieken in Interactieve Mededelingen
seo-title: De component van de grafiek in Interactieve Mededelingen
description: Met diagrammen in een interactieve communicatie kunt u grote hoeveelheden informatie comprimeren tot een eenvoudig te analyseren visuele indeling
seo-description: AEM Forms verstrekt een grafiekcomponent die u kunt gebruiken om grafieken in uw Interactieve Communicatie tot stand te brengen. Dit document verklaart basis en agentenconfiguraties van de grafiekcomponent.
uuid: 978aa431-9a5b-4964-b37c-7bfa8c3f49b9
content-type: reference
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e21714ad-d445-4aff-b0db-d577061e0907
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '2613'
ht-degree: 0%

---


# Het gebruiken van grafieken in Interactieve Mededelingen{#using-charts-in-interactive-communications}

Een grafiek of grafiek is een visuele weergave van gegevens. Het versleept grote hoeveelheden informatie in gemakkelijk-aan-begrijpelijke visuele formaat, toelatend de ontvangers van de Interactieve Mededeling om complexe gegevens beter te visualiseren, te interpreteren en te analyseren.

Terwijl het creëren van een Interactieve Communicatie, kunt u grafieken toevoegen om tweedimensionale gegevens van het de vormgegevensmodel van de Interactieve Communicatie visueel te vertegenwoordigen. Met de component Chart kunt u de volgende typen grafieken toevoegen en configureren: Schijf, Kolom, Donut, Bar, Lijn, Lijn en Punt, Punt, Gebied, en Kwadrant.

## Voeg en vorm grafiek in een Interactieve Communicatie toe {#add-and-configure-chart-in-an-interactive-communication}

Voer de volgende stappen uit om een grafiek in een Interactieve Mededeling toe te voegen en te vormen:

1. Tik **Componenten** van de knoop van de Interactieve Mededeling.
1. Sleep de component **Diagram** naar een van de volgende componenten:

   * Kanaal afdrukken: Target-gebied of afbeeldingsveld
   * Webkanaal: Deelvenster of Target-gebied

1. Tik op de diagramcomponent in de Interactieve Communication-editor en selecteer **[!UICONTROL Configure (]** configure_icon ![](assets/configure_icon.png)) op de werkbalk Component.

   De grafiekeigenschappen worden in het linkerdeelvenster weergegeven.

   ![Basiseigenschappen van een lijntekstdiagram in een afdrukkanaal](assets/chart_properties_print_new.png)

   Basiseigenschappen van een lijntekstdiagram in een afdrukkanaal

   ![Basiseigenschappen van een lijntekstdiagram in een webkanaal](assets/chart_properties_web_new.png)

   Basiseigenschappen van een lijntekstdiagram in een webkanaal

1. Vorm de [grafiekeigenschappen](../../forms/using/chart-component-interactive-communications.md#configure-chart-properties) die op het kanaaltype worden gebaseerd.
1. (Alleen kanaal afdrukken) Geef in de **[!UICONTROL Agent Settings]** sectie op of de agent dit diagram moet gebruiken. Als deze **[!UICONTROL t Is Mandatory For the Agent To Use This Chart]** optie niet wordt geselecteerd, kan de agent het oogpictogram voor de grafiek op het **[!UICONTROL Content]** lusje van de UI van de Agent tikken om de grafiek te tonen of te verbergen.

   ![chart_agentproperties](assets/chart_agentproperties.png)

1. Tik op ![done_icon](assets/done_icon.png) om de diagrameigenschappen op te slaan.

   Tik **[!UICONTROL Preview]** om de weergave en de gegevens weer te geven die aan het diagram zijn gekoppeld. Tik **[!UICONTROL Edit]** om de eigenschappen van het diagram opnieuw te configureren.

## Eigenschappen van diagram configureren {#configure-chart-properties}

Configureer de volgende eigenschappen tijdens het maken van grafieken voor afdrukken en webkanalen:

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Beschrijving</td>
   <td>Kanaaltype</td>
  </tr>
  <tr>
   <td>Naam</td>
   <td>Identifier voor het grafiekelement. De naam van het diagram dat in dit veld is opgegeven, is niet zichtbaar in het diagram. Het wordt gebruikt wanneer het verwijzen naar het element van andere componenten, manuscripten, en uitdrukkingen SOM.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Type diagram</td>
   <td>Type diagram dat u wilt genereren. De beschikbare opties zijn Schijf, Kolom, Donut, Bar, Lijn, Lijn en Punt, Punt, en Gebied.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Reeks &gt; Meerdere reeksen</td>
   <td>Selecteer deze optie om meerdere reeksen toe te voegen voor de verzamelingsitems van het formuliergegevensmodel die zijn uitgezet op de X- en Y-as.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Reeks &gt; Gegevensmodelobject</td>
   <td>Naam van het de inzamelingspunt van het model van vormgegevens om veelvoudige reeksen aan de grafiek toe te voegen.<br /> Kies een objecteigenschap van het bovenliggende formuliergegevensmodel voor de eigenschappen die op de X-as en Y-as zijn getekend om een betekenisvolle reeks te vormen. Het gegevensmodelobject dat u koppelt, moet van het type Number, String of Date zijn.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Gestapeld tonen</td>
   <td>Selecteer deze optie om de waarden van elke reeks boven op elkaar te plaatsen.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>X-as &gt; Titel</td>
   <td>Titel voor de X-as.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>X-as &gt; Gegevensmodelobject</td>
   <td><p>Naam van het gegevensmodel van het formulier dat moet worden getekend op de X-as.</p> <p>Kies twee eigenschappen voor verzamel-/arraytype van hetzelfde bovenliggende gegevensmodelobject die van betekenis zijn ten opzichte van elkaar om te plotten op de X- en Y-as van een grafiek. Het gegevensmodelobject dat u koppelt, moet van het type Number, String of Date zijn.</p> </td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Y-as &gt; Titel</td>
   <td>Titel voor de Y-as. </td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Y-as &gt; Gegevensmodelobject</td>
   <td><p>Verzamelingsitem van formuliergegevensmodel dat moet worden getekend op Y-as. In het kanaal van de Druk, zou het gegevensmodelvoorwerp voor de y-as van het type van Aantal moeten zijn.</p> <p>Kies twee eigenschappen voor verzamel-/arraytype van hetzelfde bovenliggende gegevensmodelobject die van betekenis zijn ten opzichte van elkaar om te plotten op de X- en Y-as van een grafiek. </p> </td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Y-as &gt; Functie</td>
   <td>Statistische/aangepaste functie die moet worden gebruikt voor het berekenen van de waarden op y-as.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Object verbergen</td>
   <td>Selecteer deze optie om het diagram in de uiteindelijke uitvoer te verbergen.</td>
   <td>Afdrukken en web</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Titel van het diagram. </td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Hoogte</td>
   <td>Hoogte van het diagram in pixels.</td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Breedte</td>
   <td>Breedte van het diagram in pixels. U kunt de breedte van het diagram in het webkanaal bepalen met behulp van de stijllaag of door een thema toe te passen.</td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Verplicht pagina-einde voor</td>
   <td>Selecteer deze optie om een verplicht pagina-einde toe te voegen vóór het diagram en het diagram boven op een nieuwe pagina te plaatsen. </td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Verplicht pagina-einde na</td>
   <td>Selecteer deze optie om een verplicht pagina-einde toe te voegen na het diagram en de inhoud te volgen op het diagram boven aan een nieuwe pagina. </td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Inspringing</td>
   <td>Inspringing van het diagram links op de pagina. </td>
   <td>Afdrukken</td>
  </tr>
  <tr>
   <td>Knopinfo</td>
   <td><p>Indeling waarin de knopinfo wordt weergegeven op de muis boven een gegevenspunt in het diagram in het webkanaal. De standaardwaarde is ${x} (${y}). Afhankelijk van het grafiektype, wanneer u de muis op een punt, bar, of plak in de grafiek richt, worden variabelen $ {x} en $ {y} dynamisch vervangen met de overeenkomstige waarden op x-as en y-as en getoond in tooltip.</p> <p>Laat het veld <span class="uicontrol">Knopinfo</code> leeg als u knopinfo wilt uitschakelen. Deze optie is niet van toepassing op lijngrafieken en vlakgrafieken. Zie bijvoorbeeld <a href="#chartoutputprintweb">voorbeeld 1: Uitvoer van diagram in afdruk en web</a>.</code></p> </td>
   <td>Web</td>
  </tr>
  <tr>
   <td>Diagramspecifieke configuraties</td>
   <td><p>Naast gemeenschappelijke configuraties, zijn de volgende grafiek-specifieke configuratie beschikbaar:</p>
    <ul>
     <li><strong>Legenda tonen: </strong>Hiermee geeft u een legenda weer voor de taart of het donutdiagram als dit is ingeschakeld.</li>
     <li><strong>Legenda: </strong>Geeft de positie van de legenda ten opzichte van het diagram aan. De beschikbare opties zijn Rechts, Links, Boven en Onder. U wordt aangeraden de rechterlegenda in het afdrukkanaal te gebruiken.</li>
     <li><strong>Binnenstraal</strong>: Beschikbaar voor Donut-grafieken om de straal (in pixel) van de binnencirkel in de grafiek te specificeren.</li>
     <li><strong>Lijnkleur</strong>: Beschikbaar voor de grafieken van de Lijn, van de Lijn en van het Punt, en van het Gebied om de kleur voor de lijn in de grafiek te specificeren.</li>
     <li><strong>Puntkleur</strong>: Beschikbaar voor de grafieken van het Punt en van de Lijn en van het Punt om de kleur voor de punten in de grafiek te specificeren.<br /> </li>
     <li><strong>Gebiedskleur</strong>: Beschikbaar voor vlakgrafieken om de kleur op te geven voor het gebied onder de regel in het diagram.</li>
     <li><strong>Referentiepunt &gt; Type binding: </strong>Beschikbaar voor kwadrangrafieken om het bindingstype voor het referentiepunt te<strong> </strong>specificeren. Gebruik statische tekst of objecteigenschap van gegevensmodel om de waarde voor het referentiepunt te definiëren.</li>
     <li><strong>Referentiepunt &gt; X-as: </strong>Beschikbaar voor Kwadrantgrafieken als u <span class="uicontrol">Statisch</code> van de Bindingstype drop-down lijst selecteert om de x-aswaarde voor het verwijzingspunt te specificeren.</code></li>
     <li><strong>Referentiepunt &gt; Y-as: </strong>Beschikbaar voor Kwadranten als u <span class="uicontrol">Statisch</code> van de Bindende drop-down lijst van het Type selecteert om de y-aswaarde voor het verwijzingspunt te specificeren.</code></li>
     <li><strong>Referentiepunt &gt; Gegevensmodelobject voor reeks: </strong>Beschikbaar voor veelvoudige grafieken van het reekskwadrant als u het ModelVoorwerp <span class="uicontrol">van</code> Gegevens van de drop-down lijst van het Type van Binding selecteert. Definieer de objecteigenschap van het formuliergegevensmodel om de reeks voor het referentiepunt te identificeren. </code></li>
     <li><strong>Referentiepunt &gt; Objectwaarde gegevensmodel voor reeks: </strong>Beschikbaar voor veelvoudige grafieken van het reekskwadrant als u het ModelVoorwerp <span class="uicontrol">van</code> Gegevens van de drop-down lijst van het Type van Binding selecteert. Gebruik de objecteigenschap van het formuliergegevensmodel voor reeksen en de waarde die in dit veld is gedefinieerd om de reeks voor het referentiepunt te identificeren.</code></li>
     <li><strong>Referentiepunt &gt; Gegevensmodelobject voor referentiepunt: </strong>Beschikbaar voor Kwadrant-grafieken als u <span class="uicontrol">Gegevensmodelobject</code> in de vervolgkeuzelijst Bindingstype selecteert. Definieer een objecteigenschap van het formuliergegevensmodel die vergelijkbaar is met de eigenschappen die op de X- en Y-as zijn getekend. Daarnaast definieert u voor meerdere reeksen een objecteigenschap van het gegevensmodel die een onderliggende entiteit is van de objecteigenschap van het gegevensmodel die voor de reeks is gedefinieerd.</code></li>
     <li><strong>Referentiepunt &gt; Objectwaarde gegevensmodel voor referentiepunt: </strong>Beschikbaar voor Kwadrant-grafieken als u <span class="uicontrol">Gegevensmodelobject</code> in de vervolgkeuzelijst Bindingstype selecteert. Gebruik de objecteigenschap van het formuliergegevensmodel voor het referentiepunt en de waarde die in dit veld is gedefinieerd om het referentiepunt voor het diagram te identificeren.<br /> <strong>Kwadrant Labels &gt; Linksboven:</strong> Beschikbaar voor Kwadrantgrafieken om de naam voor Linksboven kwadrant te specificeren.</code></li>
     <li><strong>Kwadrantlabels &gt; Rechtsboven:</strong> Beschikbaar voor Kwadrantgrafieken om de naam voor het Hoogste juiste kwadrant te specificeren.</li>
     <li><strong>Kwadrant Labels &gt; Bottom Right: </strong>Beschikbaar voor Kwadrantgrafieken om de naam voor het Bottom Right kwadrant te specificeren.</li>
     <li><strong>Kwadrant Labels &gt; Bottom Left: </strong>Beschikbaar voor Kwadrantgrafieken om de naam voor de Linkerbenedenkwadrant te specificeren.</li>
    </ul> </td>
   <td>Afdrukken en web</td>
  </tr>
 </tbody>
</table>

## Functies in diagram gebruiken {#use-functions-in-chart}

U kunt een grafiek vormen om statistische functies te gebruiken om waarden van de brongegevens voor het tekenen op de grafiek te berekenen. Door functies in een grafiek toe te passen, kunt u gegevens plotten die niet direct door het model van vormgegevens worden verstrekt.

![Functies in grafieken](assets/functions_charts_new.png)

Terwijl de component van de Grafiek met sommige ingebouwde functies komt, kunt u [douanefuncties](#customfunctionsweb) schrijven en hen ter beschikking stellen voor gebruik in de grafiekconfiguratie in het Webkanaal.

De volgende functies zijn standaard beschikbaar met de component Chart:

**Gemiddeld (gemiddeld)** Geeft als resultaat het gemiddelde van de waarden op de X- of Y-as voor een bepaalde waarde op de andere as.

**Sum** Geeft als resultaat de som van alle waarden op de X- of Y-as voor een bepaalde waarde op de andere as.

**Maximum** Geeft als resultaat het maximum van de waarden op de X- of Y-as voor een bepaalde waarde op de andere as.

**Frequentie** Geeft als resultaat het aantal waarden op de X- of Y-as voor een bepaalde waarde op de andere as.

**Bereik** Geeft het verschil tussen het maximum en het minimum van de waarden op de X- of Y-as voor een bepaalde waarde op de andere as.

**Mediaan** Geeft de waarde die hogere en lagere waarden in de helft op de X- of Y-as scheidt voor een bepaalde waarde op de andere as.

**Minimum** Geeft als resultaat het minimum van de waarden op de X- of Y-as voor een bepaalde waarde op de andere as.

**Modus** retourneert de waarde die de meeste keren voorkomt op de X- of Y-as voor een bepaalde waarde op de andere as.

Zie [Voorbeeld 2 voor meer informatie: De toepassing van de functies van de Som en van de Frequentie in een lijngrafiek](#applicationsumfrequency).

### Aangepaste functies in webkanaal {#customfunctionsweb}

Naast het gebruik van de standaardfuncties in grafieken, kunt u douanefuncties in JavaScript™ schrijven en hen ter beschikking stellen in de lijst van functies in de component van de Grafiek voor Webkanaal.

Een functie neemt een array of waarden en een categorienaam als invoer en retourneert een waarde. Bijvoorbeeld:

```javascript
Multiply(valueArray, category) {
 var val = 1;
 _.each(valueArray, function(value) {
 val = val * value;
 });
 return val;
}
```

Zodra u een douanefunctie hebt geschreven, doe het volgende om het voor gebruik in de grafiekconfiguratie beschikbaar te maken:

1. Voeg de douanefunctie in de cliëntbibliotheek toe verbonden aan de relevante Interactieve Communicatie. Voor meer informatie, zie het [Vormen van de Submit actie](/help/forms/using/configuring-submit-actions.md) en het [Gebruiken van cliënt-zij Bibliotheken](/help/sites-developing/clientlibs.md).

1. Als u de aangepaste functie wilt weergeven in de vervolgkeuzelijst Functie, maakt u in CRXDe Lite een `nt:unstructured` knooppunt in de map apps met de volgende eigenschappen:

   * Eigenschap toevoegen `guideComponentType` met waarde als `fd/af/reducer`. (mandatory)

   * Voeg eigenschap toe `value` aan een volledig gekwalificeerde naam van de aangepaste JavaScript™-functie. (verplicht) en de waarde ervan instellen op de naam van de aangepaste functie, zoals Vermenigvuldigen.
   * Voeg eigenschap toe `jcr:description` met de waarde die u wilt weergeven als de naam van de aangepaste functie die wordt weergegeven in de vervolgkeuzelijst Functie. Bijvoorbeeld, **vermenigvuldigen**.

   * Voeg een eigenschap toe `qtip` met een waarde die een korte beschrijving van de aangepaste functie is. Deze verschijnt als knopinfo wanneer u de aanwijzer boven de functienaam in de vervolgkeuzelijst **Functie** plaatst.

1. Klik op Alles **** opslaan om de configuratie op te slaan.

De functie is nu beschikbaar voor gebruik in de Grafiek.

## Voorbeeld 1: Uitvoer van diagram in afdruk en web {#chartoutputprintweb}

Op het tabblad Standaard definieert u het type grafiek, de eigenschappen van het gegevensmodel van het bronformulier die gegevens bevatten, de labels die moeten worden getekend op de X-as en Y-as van het diagram en eventueel de statistische functie die de waarden voor tekenen op het diagram berekent.

Laten we de minimaal vereiste informatie in basiseigenschappen in detail begrijpen, met behulp van een kaartinstructie die is gegenereerd met een interactieve communicatie. Bedenk dat u een grafiek wilt produceren om de hoeveelheid verschillende uitgaven in de verklaring te schilderen. U wilt verschillende soorten grafieken voor druk en Weboutput van de Interactieve Communicatie gebruiken.

### Kolomdiagram voor afdrukken {#columnchartprint}

Hiervoor geeft u de volgende eigenschappen op:

* **[!UICONTROL Name]** - Geef de naam voor het diagram op.
* **[!UICONTROL Chart Type]** - Selecteer **Kolom** in de vervolgkeuzelijst.
* **[!UICONTROL Title]** - Geef het type kosten op voor de X-as en het bedrag van de transactie voor de Y-as.
* **[!UICONTROL Data Model Objects]** - Selecteer de eigenschappen van het gegevensmodelobject om gegevensbindingen te maken voor de X-as (Type kosten) en de Y-as (Hoeveelheid transactie).

![Kolomdiagram in het afdrukkanaal van een interactieve communicatie](assets/sample_chart_print_column_new.png)

Kolomdiagram in het afdrukkanaal van een interactieve communicatie

### Donut-diagram voor web {#donutchartweb}

Hiervoor geeft u de volgende eigenschappen op:

* **[!UICONTROL Name]** - Geef de naam voor het diagram op.
* **[!UICONTROL Chart Type]** - Selecteer een optie in de **[!UICONTROL Donut]** vervolgkeuzelijst.
* **[!UICONTROL Data Model Objects]** - Selecteer de eigenschappen van het gegevensmodelobject om gegevensbindingen te maken voor de X-as (Type kosten) en de Y-as (Hoeveelheid transactie).
* **[!UICONTROL Inner Radius]** - Geef de waarde voor Binnenstraal op als 150 om de straal (in pixels) van de binnencirkel in het diagram op te geven.
* **[!UICONTROL Tooltip]** - Gebruik de standaardindeling ${x}(${y}) om de knopinfo weer te geven. De knopinfo wordt weergegeven als: Type kosten (transactiebedrag). Voorbeeld: Debitering voor bitmaps (10000).

![Donut grafiek in het Webkanaal van een Interactieve Mededeling](assets/sample_chart_web_new.png)

Donut grafiek in het Webkanaal van een Interactieve Mededeling

## Voorbeeld 2: Toepassing van de functies van de Som en van de Frequentie in een lijngrafiek {#applicationsumfrequency}

Door functies in een grafiek toe te passen, kunt u gegevens plotten die niet direct door het model van vormgegevens worden verstrekt. In dit voorbeeld, gebruiken wij een voorbeeld van de creditcardverklaring om te begrijpen hoe de functies van de Som en van de Frequentie op de grafiek kunnen worden toegepast.

![Regeldiagram zonder functie met twee &quot;Debit for AirBnB&quot;-transacties](assets/line_chart_web_new.png)

Regeldiagram zonder functie met twee &quot;Debit for AirBnB&quot;-transacties

### Sum, functie {#sum-function}

U kunt de functie sum toepassen om waarden van meerdere instanties van dezelfde gegevenseigenschap op te tellen en deze slechts eenmaal weer te geven. In de volgende grafiek wordt bijvoorbeeld de functie Som toegepast op de Y-as om het bedrag van de twee Debit voor AirBnB-transacties (2050 en 1050) op te tellen en slechts één transactie (3100) weer te geven.

De functie van de som kan grafiek nuttiger maken wanneer u som voor vele instanties van het zelfde gegevensbezit wilt sorteren en tonen.

![Lijndiagram samenstellen](assets/line_chart_web_sum_new.png)

### Frequentiefunctie {#frequency-function}

De functie van de Frequentie keert het aantal waarden y-as voor een bepaalde waarde op de andere as terug. Met de toepassing van de Frequentiefunctie op de Y-as (Transactiesom) toont de grafiek dat er twee exemplaren van de Debit voor AirBnB-transacties zijn geweest en één exemplaar van de rest van de soorten transacties.

![Frequentie van lijndiagram](assets/line_chart_web_functions_frequency_new.png)

## Voorbeeld 3: Quadrant-diagram met meerdere reeksen in web {#example-multi-series-quadrant-chart-in-web}

De grafiek geeft een overzicht van het bedrag voor transacties die in een bepaald datumbereik worden uitgevoerd. Het diagram van het kwadrant biedt de mogelijkheid om het grafiekgebied te verdelen in vier gelabelde secties. Het teken gebruikt een statisch referentiepunt voor de X- en Y-as. Gebruik de functie voor meerdere reeksen om gegevens te scheiden op basis van de naam van de bank.

Hiervoor geeft u de volgende eigenschappen op:

* **Naam:** Geef de naam voor het diagram op.
* **Type diagram:** Selecteer **Kwadrant** in de vervolgkeuzelijst.

* Schakel het selectievakje **Meerdere reeksen** in.
* **Gegevensmodelobject**: Geef de objecteigenschap van het gegevensmodel voor de reeks op. De objecteigenschap van het gegevensmodel voor de naam van de bank is een bovenliggend element van de eigenschappen van het gegevensmodel die zijn getekend in de X-as en Y-as.
* **Gegevensmodelobjecten:** Selecteer de eigenschappen van het gegevensmodelobject om gegevensbindingen te maken voor de X-as (Transactiedatum) en de Y-as (Hoeveelheid transactie).
* Selecteer in de sectie **Referentiepunt** de optie **Statisch** als bindingstype.

* Geef de waarden op voor de referentiepunten op de X-as en de Y-as.
* Geef de kwadranslabels op voor de kwadranten Linksboven, Rechtsboven, Rechtsonder en Linksonder.
* Schakel het selectievakje **Lagen** tonen in om de kleurcodes voor de banknamen weer te geven.

![Kwadrantkaarten](assets/charts_quadrant_example_new.png)

