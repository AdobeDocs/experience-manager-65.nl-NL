---
title: Snelgids voor WCAG 2.1
description: Snelgids voor WCAG 2.1
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1770'
ht-degree: 99%

---


# Snelgids voor WCAG 2.1{#quick-guide-to-wcag}

Adobe Experience Manager (AEM) is ontwikkeld om de naleving van de Web Content Accessibility Guidelines te maximaliseren.

De [Web Content Accessibility Guidelines (WCAG) versie 2.1](https://www.w3.org/TR/WCAG/) zijn een reeks internationaal erkende richtlijnen die door het [World Wide Web Consortium (W3C)](https://www.w3.org/) in het kader van hun [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/) zijn ontwikkeld.

>[!NOTE]
>
>WCAG 2.1 is een update van versie WCAG 2.0 uit 2008. Zie [WCAG 2.1 - Vergelijking met WCAG 2.0](https://www.w3.org/TR/WCAG21/#comparison-with-wcag-2-0).

>[!NOTE]
>
>Een [bijgewerkte versie van de richtlijnen, WCAG 2.2,](https://www.w3.org/TR/WCAG22/) wordt momenteel ontwikkeld, maar wordt hier niet in overweging genomen.

WCAG 2.1 bestaat uit een reeks technologieonafhankelijke richtlijnen en succescriteria om ervoor te zorgen dat webcontent toegankelijk en bruikbaar is voor personen met een handicap. Zij adviseren auteurs, ontwerpers en ontwikkelaars van webcontent om ervoor te zorgen dat de bronnen die zij produceren, zo toegankelijk mogelijk zijn voor zoveel mogelijk mensen, ongeacht hun handicap, bijvoorbeeld een visuele handicap, gehoorverlies, leermoeilijkheden of leeftijdsgebonden beperkingen.

Als u bijvoorbeeld een afbeelding (of andere niet-tekstuele content) beschrijft met het `alt`-kenmerk in HTML, heeft dit grote voordelen voor blinden of slechtzienden. De tekstuele beschrijving in het `alt`-kenmerk kan worden omgezet naar spraakuitvoer of worden verzonden naar elektronische vernieuwbare brailleweergaven.

Daarnaast kan WCAG 2.1 voordelen opleveren voor andere begunstigden, waaronder personen die mogelijk als *arbeidsongeschikt* worden beschouwd. Personen die door omstandigheden problemen ondervinden met bladertechnologie, netwerkverbindingssnelheid of bladeromgeving, kunnen te maken hebben met belemmeringen die vergelijkbaar zijn met mensen met een handicap.

Met Adobe Experience Manager kunnen contentauteurs en/of website-eigenaars webcontent maken die voldoet aan de relevante succescriteria van WCAG 2.1 niveau A en niveau AA.

Daarom is het begrijpen van de doelstellingen van WCAG 2.1 en de structuur van de richtlijnen een belangrijk onderdeel van het begrijpen van webtoegankelijkheid en de manier waarop de richtlijnen kunnen helpen bij het creëren van toegankelijke webcontent.

De bedoeling van WCAG 2.1 is het verstrekken van richtlijnen die:

* **Technologieonafhankelijk zijn:**
Met andere woorden, richtlijnen die kunnen worden toegepast op verschillende webcontentindelingen, niet alleen op HTML. WCAG 2.1 kan dus betrekking hebben op content die is gegenereerd door of wordt geleverd in PDF, Flash, JavaScript en andere huidige en toekomstige webtechnologieën.

* Kunnen worden **getest:**
Elke richtlijn is zodanig opgesteld dat het op objectieve manier kan worden getest om te garanderen dat een groep toegankelijkheidsdeskundigen het er in het algemeen over eens is dat aan de richtlijn is voldaan. Een van de uitdagingen van toegankelijkheidsrichtlijnen is dat sommige richtlijnen technisch getest kunnen worden, terwijl andere vereisen dat mensen oordelen of de richtlijn al dan niet succesvol is nageleefd.

* **Prioritaire en contextafhankelijke implementatie ondersteunen:**
De richtlijnen van WCAG 2.1 krijgen een prioriteitsniveau en hebben betrekking op de mogelijke gevolgen van het niet volgen van een richtlijn voor een bepaalde groep gebruikers met een handicap. Op die manier kunnen auteurs een geïnformeerde beslissing nemen over de belangrijkste richtlijnen voor hun specifieke situatie. Daarnaast wordt het concept van *ondersteunde toegankelijkheid* geïntroduceerd. Op deze manier kunnen auteurs beslissen hoe ze webtechnologieën die mogelijk geen volledige toegankelijkheidsondersteuning bieden, het beste kunnen gebruiken, of van gebruikers verlangen dat ze over specifieke ondersteunende technologische hulpmiddelen en/of browsers beschikken om te kunnen profiteren van toegankelijkheidsfuncties.

Deze doelstellingen hebben de structuur van WCAG 2.1 aanzienlijk beïnvloed.

>[!NOTE]
>
>Het is niet mogelijk om een website te maken die tegemoet komt aan alle mogelijke handicaps of personen. Het doel van WCAG 2.1 is om webauteurs te helpen sites te maken die, voor zover mogelijk, binnen bepaalde omstandigheden en binnen het redelijke toegankelijk zijn.

## Structuur {#structure}

WCAG 2.1 is zodanig gestructureerd dat de concepten voor het maken van toegankelijke webcontent geleidelijk aan tot in detail wordt geïntroduceerd. Dit kan de indruk wekken dat WCAG 2.1 een zeer complexe reeks onderling gekoppelde documenten is, maar het doel is (geleidelijk) gedetailleerdere informatie te verstrekken als en wanneer auteurs die nodig hebben, in plaats van alles in één zeer groot document aan te bieden.

WCAG 2.1 bestaat uit vier basisbeginselen voor toegankelijk ontwerp, waarnaar soms worden verwezen met de afkorting **POUR**. Deze zijn:

1. **Perceivable (waarneembaar)**: kan een gebruiker de webcontent in kwestie waarnemen?
1. **Operable (werkbaar)**: kan een gebruiker navigeren, gegevens invoeren of anderszins met de webcontent communiceren?
1. **Understandable (begrijpbaar)**: kan een gebruiker de voorgestelde webcontent verwerken en begrijpen?
1. **Robust (robuust)**: is de webcontent op de beoogde manier beschikbaar in een voldoende breed scala aan bladeromgevingen , waaronder verouderde en opkomende bladeromgevingen ?

Iets meer uitgewerkt:
* Elk **beginsel** bestaat uit een of meer **richtlijnen**.

* Richtlijnen worden geformuleerd als instructies, die ofwel positief (&quot;Doe dit...&quot;) of negatief (&quot;Doe dit niet...&quot;) zijn.
* De richtlijnen zijn genummerd van 1.1 tot en met 4.1, waarbij het eerste nummer overeenkomt met het hoofdbeginsel.
* Elke richtlijn bestaat uit een of meer **succescriteria**.
* Succescriteria worden geschreven als instructies, die ofwel `True` of `False` zijn voor een bepaalde webpagina.
* Succescriteria kunnen ofwel/of-keuzes omvatten, of uitzonderingen. Dit zijn situaties waarin niet aan de succescriteria moet worden voldaan.
* Succescriteria worden genummerd volgens de hoofdrichtlijn en het hoofdbeginsel, van 1.1.1 tot en met 4.1.1. Ze hebben ook een korte naam die de bedoeling van het criterium samenvat en die ervoor zorgt dat de richtlijn en het beginsel gemakkelijker geraadpleegd kunnen worden. Het succescriterium [1.1.1 is bijvoorbeeld Niet-tekstuele content](https://www.w3.org/TR/WCAG/#non-text-content).
* De succescriteria omvatten een lijst met verwante **technieken** (hieronder nader beschreven).

## Ondersteunende bronnen {#supporting-resources}

Naast de kerncomponenten van WCAG 2.1 van Beginselen, Richtlijnen en Succescriteria, is er een aantal ondersteunende documenten. Sommige daarvan geven specifiek advies over hoe te voldoen aan aspecten van de richtlijnen, andere zijn meer algemene verwijzingen die webauteurs, ontwerpers en ontwikkelaars helpen WCAG 2.1 te begrijpen en zo effectief mogelijk te gebruiken.

Hoewel WCAG 2.1 zelf een stabiel document is en niet zal veranderen, zijn de meeste van deze ondersteunende bronnen dynamische documenten. Dit betekent dat zij in de loop der tijd zullen worden aangepast en uitgebreid wanneer nieuwe technologieën worden ontwikkeld, en er nieuwe voorbeelden zijn van de manier waarop webtoegankelijkheid kan worden bereikt .

### WCAG 2.1-bronnen {#wcag-resources}

Deze lijst is niet uitvoerig, en is bedoeld als een inleiding op de beschikbare bronnen:
* [Een overzicht van alle WCAG-gerelateerde documenten](https://www.w3.org/WAI/standards-guidelines/wcag/)
* [Een samenvatting van de verschillende documenten](https://www.w3.org/WAI/standards-guidelines/wcag/docs/)
* [Web Content Accessibility Guidelines (WCAG) 2.1](https://www.w3.org/TR/WCAG21/)
* [Nieuw in WCAG 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/)
* [Een korte referentiehandleiding over de naleving van WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/)
* [Veelgestelde vragen over WCAG 2](https://www.w3.org/WAI/standards-guidelines/wcag/faq/)


### Nieuw in WCAG 2.1 {#what-is-new}

De richtlijnen bevatten informatie over wat nieuw is in WCAG 2.1:

* [Nieuw in WCAG 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/new-in-21/) biedt waardevolle informatie over de delta tussen WCAG 2.0 en WCAG 2.1.

* In de sectie [WCAG 2.0 en 2.1](https://www.w3.org/WAI/standards-guidelines/wcag/#versions) wordt de status van hun relatie nader toegelicht.

### Technieken voor WCAG 2.1 {#techniques-for-wcag}

Technieken voor WCAG 2.1 zijn beschikbaar op de pagina [Technieken voor WCAG 2.1](https://www.w3.org/WAI/WCAG21/Techniques/).

**Technieken** vormen het niveau onder succescriteria in de hiërarchie van WCAG 2.1. Ze worden door WAI geclassificeerd als informatief, niet als normatief. Met andere woorden, een specifieke techniek hoeft niet te worden gevolgd om een bron in overeenstemming te brengen met WCAG 2.1.

Omdat technieken veel specifieker zijn dan succescriteria, verwijzen ze doorgaans naar een bepaalde technologie of een bepaald contenttype (bijvoorbeeld HTML of video), of naar een situatie (bijvoorbeeld e-commerce of e-learningtoepassing). U kunt technieken zien als bewezen voorbeelden van hoe specifieke richtlijnen en succescriteria kunnen worden nageleefd, zodat ze nuttig zijn voor auteurs en ontwikkelaars die in bepaalde situaties werken.

U hebt op de volgende manieren toegang tot technieken:

* Op verzameling (technieken kunnen algemeen zijn of betrekking hebben op een specifieke technologie of indeling, zoals HTML, CSS of clientscripts), of
* Via gerelateerde succescriteria. Technieken kunnen op meer dan een succescriterium van toepassing zijn.

Elke techniek heeft een uniek getal dat betrekking heeft op de verzameling ervan. Een van de ARIA-technieken is bijvoorbeeld [Technique ARIA2: Vereiste velden identificeren met de eigenschap aria-required](https://www.w3.org/WAI/WCAG21/Techniques/aria/ARIA2.html).

Technieken kunnen Sufficient (toereikend), Advisory (adviserend) of een Failure (mislukking) zijn:

* Een *toereikende techniek* is een techniek die, als ze wordt gevolgd, voldoende is om aan een bepaald succescriterium te voldoen.
* Een *adviserende techniek* is een techniek die, als ze wordt gevolgd, een positief effect zal hebben op de toegankelijkheid, maar op zich misschien niet voldoende is om te garanderen dat aan een bepaald succescriterium wordt voldaan.
* Een *mislukking* is een techniek die een specifiek voorbeeld beschrijft waarbij niet aan een succescriterium is voldaan.

De details voor technieken omvatten een beschrijving, toepasselijkheid, voorbeelden, bronnen voor verdere informatie en details van hoe auteurs de succesvolle toepassing van de techniek kunnen testen.

De lijst met technieken is niet volledig en WAI werkt de lijst voortdurend bij met nieuwe voorbeelden, die de ontwikkelingen in webtechnologie, ontwerpbenaderingen en onderzoeksresultaten weerspiegelen. Het is dus goed om de lijst met technieken regelmatig te controleren op nieuwe toevoegingen.

### WCAG 2.1 begrijpen {#understanding-wcag}

Dit verwijst naar een reeks documenten die lezers advies geven zodat zij het doel van specifieke richtlijnen en succescriteria beter begrijpen. U kunt [een inleiding downloaden en vindt hier ook koppelingen naar meer gedetailleerde informatie](https://www.w3.org/WAI/WCAG21/Understanding/).

Elke afzonderlijke richtlijn en elk succescriterium heeft ook een eigen pagina &quot;Understanding&quot; (Begrijpen) met informatie over:

* De intentie van de richtlijn;
* Specifieke succescriteria;
* Adviserende technieken die helpen te voldoen aan de vereisten van de richtlijnen, maar die niet onder een specifiek succescriterium vallen.

De afzonderlijke pagina Begrijpen van elk succescriterium bevat informatie over:

* De intentie van het succescriterium;
* Algemene voorbeelden van de wijze waarop aan het succescriterium kan worden voldaan;
* Gerelateerde bronnen (niet-W3C) over hoe aan het succescriterium kan worden voldaan;
* Technieken en fouten: specifieke en gedetailleerde voorbeelden van de manier waarop aan het succescriterium kan worden voldaan (hieronder nader beschreven);
* Belangrijke termen: een verklarende woordenlijst van termen die belangrijk zijn om het succescriterium te begrijpen.

Een voorbeeld is te vinden op: [Succescriterium 1.1.1 (&quot;Niet-tekstuele content&quot;) begrijpen](https://www.w3.org/WAI/WCAG21/Understanding/non-text-content).

### Voldoen aan WCAG 2.1 {#how-to-meet-wcag}

De sectie &quot;Voldoen&quot; is beschikbaar op de pagina [Hoe kan ik voldoen aan WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/). Deze sectie biedt een alternatieve presentatie van WCAG, waardoor lezers de content van de richtlijnen kunnen verfijnen tot de richtlijnen die het meest relevant zijn voor de eigen belangen of omstandigheden van de lezer. Lezers kunnen de technieken voor succescriteria die ze willen bekijken, filteren door bepaalde webcontenttechnologieën op te geven, zoals CSS-opmaakprofielen (Cascading Style Sheets) of scripting, of door bepaalde prioriteitsniveaus op te geven.

Zonder filteren biedt deze bron alle succescriteria gegroepeerd op richtlijn. Voor elk succescriterium wordt het volgende verstrekt:

* De tekst van het succescriterium;
* Een koppeling naar het bijbehorende document &quot;Begrijpen&quot;;
* Een lijst met gerelateerde toereikende technieken en koppelingen naar de details van elke techniek;
* Een lijst met gerelateerde adviserende technieken en koppelingen naar de details van elke techniek (indien deze bestaat);
* Een lijst met gerelateerde mislukkingen en koppelingen naar de details van elke mislukking.
