---
title: Snelle gids aan WCAG 2.0
seo-title: Snelle gids aan WCAG 2.0
description: Lees een kort overzicht van de WCAG 2.0 toegankelijkheidsrichtlijnen.
seo-description: Lees een kort overzicht van de WCAG 2.0 toegankelijkheidsrichtlijnen.
uuid: a5cf463e-89e9-4cc0-9c91-69a1fd3d8ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
topic-tags: managing-accessibility
content-type: reference
discoiquuid: 3cac0e34-7514-48ce-a93b-592bbdbcd252
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Snelle gids aan WCAG 2.0{#quick-guide-to-wcag}

AEM is ontwikkeld om de naleving van de Web Content Accessibility Guidelines te maximaliseren:

De [Web Content Accessibility Guidelines versie 2.0 (WCAG2)](https://www.w3.org/TR/WCAG/) zijn een reeks internationaal erkende richtlijnen die door het Consortium van het [World Wide Web (W3C)](https://www.w3.org/) in het kader van hun [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/)worden ontwikkeld.

WCAG 2.0 bestaat uit een reeks technologie-onafhankelijke richtlijnen en succescriteria om ervoor te zorgen dat webinhoud toegankelijk en bruikbaar is voor personen met een handicap. Zij adviseren auteurs, ontwerpers en ontwikkelaars van webinhoud om ervoor te zorgen dat de middelen die zij produceren zo toegankelijk mogelijk zijn voor zoveel mogelijk mensen, ongeacht hun handicap; bijvoorbeeld visuele stoornissen, gehoorverlies, leermoeilijkheden, leeftijdsgebonden beperkingen.

Als u bijvoorbeeld een afbeelding (of andere niet-tekstuele inhoud) beschrijft met het `alt` kenmerk in HTML, heeft dit grote voordelen voor blinden of slechtzienden. De tekstuele beschrijving in het `alt` kenmerk kan worden omgezet in spraakuitvoer of worden verzonden naar elektronische vernieuwbare brailleweergaven.

Bovendien kan WCAG 2.0 leiden tot voordelen voor andere begunstigden, waaronder mensen die *situationeel gehandicapt* kunnen worden geacht. Personen die door omstandigheden zoals bladertechnologie, netwerkverbindingssnelheid of bladeromgeving te maken hebben met belemmeringen die vergelijkbaar zijn met mensen met een handicap.

Met Adobe Experience Manager kunnen auteurs van inhoud en/of eigenaars van websites webinhoud maken die voldoet aan de relevante succescriteria van WCAG 2.0 Level A en Level AA.

Daarom is het begrijpen van de doelstellingen van WCAG 2.0 en de structuur van de richtsnoeren een belangrijk onderdeel van het begrijpen van webtoegankelijkheid en van de manier waarop de richtsnoeren kunnen helpen bij het creëren van toegankelijke webinhoud.

WCAG 2.0 is voornemens richtsnoeren te verstrekken die:

* Zijn **technologie-agnostisch:**

   Met andere woorden, richtlijnen die kunnen worden toegepast op een reeks webinhoud-indelingen, niet alleen op HTML. WCAG 2.0 kan dus inhoud bestrijken die is gegenereerd door of wordt geleverd in PDF, Flash, JavaScript en andere huidige en toekomstige webtechnologieën. Dit is bedoeld om een erkende zwakte van WCAG 1.0 aan te pakken, aangezien het gericht was op HTML ten koste van andere webinhoud-indelingen.

* kunnen worden **getest:**

   Elk richtsnoer is zodanig opgesteld dat het objectief kan worden getest om te garanderen dat een groep toegankelijkheidsdeskundigen het er in het algemeen over eens is dat aan het richtsnoer is voldaan. Een van de uitdagingen van toegankelijkheidsrichtlijnen is dat sommige richtlijnen technisch getest kunnen worden, terwijl andere eisen dat mensen oordeelkundig beoordelen of het richtsnoer al dan niet succesvol is uitgevoerd. WCAG 2.0 is geschreven om de subjectiviteit te verminderen die in sommige van de WCAG 1.0-richtsnoeren en -controlepunten aanwezig was.

* Prioritaire en contextafhankelijke implementatie **van ondersteuning:**

   Net als bij WCAG 1.0 worden prioriteiten gesteld voor WCAG 2.0, die betrekking hebben op de waarschijnlijke gevolgen van het niet volgen van een richtsnoer voor een bepaalde groep gebruikers met een handicap. Op die manier kunnen auteurs een geïnformeerde beslissing nemen over de belangrijkste richtsnoeren voor hun specifieke situatie. Daarnaast wordt het concept van ondersteunde ** toegankelijkheid geïntroduceerd. Op deze manier kunnen auteurs beslissen hoe ze webtechnologieën die mogelijk geen volledige toegankelijkheidsondersteuning bieden, het beste kunnen gebruiken, of van gebruikers verlangen dat ze over specifieke ondersteunende hulpmiddelen en/of browsers beschikken om te kunnen profiteren van toegankelijkheidsfuncties.

Deze doelstellingen hebben de structuur van WCAG 2.0 aanzienlijk beïnvloed.

>[!NOTE]
>
>Het is niet mogelijk om een website te maken die alle mogelijke handicaps of soorten personen behandelt. Het doel van WCAG 2.0 is Webauteurs te helpen plaatsen tot stand te brengen die, voor zover mogelijk, binnen bepaalde voorwaarden en binnen reden toegankelijk zijn.

>[!NOTE]
>
>Als u met WCAG 1.0 vertrouwd bent, zult u sommige veranderingen in WCAG 2.0 opmerken. Deze hebben betrekking op reikwijdte, organisatie en doel.

## Structuur {#structure}

WCAG 2.0 is op een manier gestructureerd die concepten van het toegankelijk maken van webinhoud op progressieve wijze introduceert. Dit kan de indruk wekken dat WCAG 2.0 een zeer complex geheel van onderling gekoppelde documenten is, maar het doel is (geleidelijk) gedetailleerdere informatie te verstrekken wanneer en wanneer auteurs die nodig hebben - in plaats van deze allemaal in één zeer groot document te verstrekken.

WCAG 2.0 bestaat uit vier basisbeginselen voor toegankelijk ontwerp. Dit zijn:

1. **Vermoedelijk**: kan een gebruiker de webinhoud in kwestie voelen?
1. **Werkbaar**: kan een gebruiker navigeren, gegevens invoeren of anderszins met de webinhoud communiceren?
1. **Begrijpbaar**: kan een gebruiker de webinhoud verwerken en begrijpen die aan hen wordt voorgesteld?
1. **Robuust**: is de webinhoud op de beoogde manier beschikbaar in een voldoende breed scala aan browseringsomgevingen , waaronder verouderde en opkomende browseromgevingen ?

Deze beginselen worden soms genoemd door het acroniem POUR.

* Elk **beginsel** bestaat uit een of meer **richtsnoeren**.

   * Richtlijnen worden geformuleerd als instructies, die ofwel positief (doe dit...) of negatief (doe dit niet...) zijn.
   * De richtsnoeren zijn de nummers 1.1 tot en met 4.1, waar het eerste nummer overeenkomt met het moederbeginsel.

* Elk richtsnoer bestaat uit een of meer **succescriteria**.

   * Succescriteria worden geschreven als instructies, die ofwel `True` ofwel `False` voor een bepaalde webpagina zijn.
   * Succescriteria kunnen een keuze of keuze omvatten, of kunnen uitzonderingen omvatten; situaties waarin niet aan de succescriteria moet worden voldaan.
   * Succescriteria worden genummerd volgens het richtsnoer en het beginsel van de moedermaatschappij, van 1.1.1 tot en met 4.1.1. Zij hebben ook een korte naam die de intentie van het criterium samenvat, voor gemakkelijkere verwijzing. Het succescriterium 1.1.1 is bijvoorbeeld een alternatief dat geen tekst is.
   * De succescriteria omvatten een lijst van verwante **technieken** (hieronder nader beschreven).

## Ondersteunende bronnen {#supporting-resources}

Naast de kerncomponenten van WCAG 2.0 van Beginselen, Richtsnoeren en Succes Criteria, zijn er een aantal ondersteunende documenten. Sommige van hen verstrekken specifiek advies over hoe te om aan aspecten van de richtlijnen te voldoen, zijn andere meer algemene verwijzingen die Webauteurs, ontwerpers en ontwikkelaars van alle Mogelijkheden helpen WCAG 2.0 begrijpen en zo effectief mogelijk gebruiken.

Terwijl WCAG 2.0 een stabiel document is en niet zal veranderen, zijn de meeste van deze steunmiddelen dynamische documenten; zij zullen in de loop der tijd veranderen en groeien naarmate nieuwe technologieën zich ontwikkelen , en er zijn nieuwe voorbeelden te vinden van de wijze waarop toegankelijkheid van het web kan worden bereikt .

### WCAG 2.0-bronnen {#wcag-resources}

* [een overzicht van alle met WCAG 2.0 verband houdende documenten](https://www.w3.org/WAI/intro/wcag.php);
* [een toelichting op de onderlinge](https://www.w3.org/WAI/intro/wcag20)relatie tussen de verschillende onderdelen;
* [WCAG 2.0 Veelgestelde vragen](https://www.w3.org/WAI/WCAG20/wcag2faq.html);

### Technieken voor WCAG 2.0 {#techniques-for-wcag}

De technieken voor WCAG 2.0 zijn beschikbaar op de [Technieken voor WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/) pagina.

**Technieken** vormen het niveau onder succescriteria in de hiërarchie WCAG 2.0. Ze worden door WAI geclassificeerd als informatief, niet als normatief. Met andere woorden, een specifieke techniek hoeft niet te worden gevolgd om een middel in overeenstemming te brengen met WCAG 2.0.

Omdat technieken veel specifieker zijn dan succescriteria, verwijzen ze meestal naar een bepaald technologie- of inhoudstype (bijvoorbeeld HTML of video) of naar een situatie (bijvoorbeeld e-commerce of e-learningtoepassing). U kunt technieken zien als bewezen voorbeelden van hoe specifieke richtlijnen en succescriteria kunnen worden vervuld, zodat ze nuttig zijn voor auteurs en ontwikkelaars die in bepaalde situaties werken.

De technieken kunnen worden betreden:

* Op verzameling (technieken kunnen algemeen zijn of betrekking hebben op een specifieke technologie of indeling, zoals HTML, CSS of clientscripts), of
* Uit gerelateerde succescriteria. Technieken kunnen op meer dan één succescriterium van toepassing zijn.

Elke techniek heeft een uniek getal dat betrekking heeft op de verzameling ervan. Een van de ARIA-technieken is bijvoorbeeld *Technique ARIA2: Vereiste velden identificeren met de eigenschap*&quot;required&quot;.

Technieken kunnen Volstaan, Adviserend, of een Mislukking zijn:

* Een *toereikende techniek* is een techniek die, als ze wordt gevolgd, voldoende is om aan een bepaald succescriterium te voldoen.
* Een *adviestechniek* is een techniek die, als ze wordt gevolgd, een positief effect zal hebben op de toegankelijkheid, maar op zich misschien niet voldoende is om te garanderen dat aan een bepaald succescriterium wordt voldaan.
* Een *mislukking* is een techniek die specifiek voorbeeld beschrijft van waar een succescriterium niet zou worden vervuld.

De details voor technieken omvatten een beschrijving, toepasselijkheid, voorbeelden, middelen voor verdere informatie en details van hoe de auteurs voor succesvolle toepassing van de techniek kunnen testen.

De lijst met technieken is niet compleet en WAI werkt de lijst voortdurend bij met nieuwe voorbeelden, die de ontwikkelingen in webtechnologie, ontwerpbenaderingen en onderzoeksresultaten weerspiegelen. Het is dus goed om de lijst met technieken voor nieuwe toevoegingen regelmatig te controleren.

### WCAG 2.0 begrijpen {#understanding-wcag}

Dit betreft een reeks documenten die lezers advies geven om het doel van specifieke richtsnoeren en succescriteria te beoordelen. U kunt een inleiding [downloaden, plus verbindingen aan meer gedetailleerde informatie](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/Overview.html).

Elk afzonderlijk richtsnoer en succescriterium heeft ook een eigen &quot;Understanding&quot;-pagina, die informatie bevat over:

* de intentie van het richtsnoer;
* specifieke succescriteria;
* Adviestechnieken die helpen te voldoen aan de vereisten van de richtsnoeren, maar die niet onder een specifiek succescriterium vallen.

De afzonderlijke pagina &quot;Understanding&quot; van elk succescriterium bevat informatie over:

* de intentie van het succescriterium;
* Algemene voorbeelden van de wijze waarop aan het succescriterium kan worden voldaan;
* gerelateerde (niet W3C) bronnen over hoe aan het succescriterium kan worden voldaan;
* Technieken en fouten: specifieke en gedetailleerde voorbeelden van de wijze waarop aan het succescriterium kan worden voldaan (hieronder nader beschreven)
* Belangrijke termen - een verklarende woordenlijst van termen die belangrijk zijn om het succescriterium te begrijpen.

Een voorbeeld is te vinden op: [Succescriterium 1.1.1 (&quot;Niet-tekstuele inhoud&quot;)](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/text-equiv-all.html).

### Hoe te om WCAG 2.0 te ontmoeten {#how-to-meet-wcag}

De sectie &quot;Hoe kan ik ontmoeten&quot; is beschikbaar op de pagina [Hoe kan ik aan WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref/) voldoen. Deze paragraaf biedt een alternatieve presentatie van WCAG, waardoor de inhoud van de richtsnoeren kan worden verfijnd tot de richtsnoeren die het meest relevant zijn voor de eigen belangen of omstandigheden van de lezer. Lezers kunnen de technieken met succescriteria die ze willen bekijken filteren door bepaalde webinhoud-technologieën op te geven, zoals Cascading Style Sheets of scripting, of door een bepaald prioriteitsniveau of -niveaus op te geven.

Zonder filtreren, verstrekt dit middel alle succescriteria die door richtlijn worden gegroepeerd. Voor elk succescriterium wordt het volgende verstrekt:

* de tekst van het succescriterium;
* een link naar het bijbehorende &quot;document van overeenstemming&quot;;
* een lijst van verwante technieken die toereikend zijn en die verband houden met de bijzonderheden van elke techniek;
* een lijst van verwante adviestechnieken, die verband houdt met de bijzonderheden van elke techniek (indien deze bestaat);
* Een lijst van verwante mislukkingen, die aan details van elke mislukking verbinden.