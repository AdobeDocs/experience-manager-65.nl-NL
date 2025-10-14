---
title: Letter maken
description: Dit onderwerp geeft u de stappen om een brief tot stand te brengen, gegevensmodules en gehechtheid aan het toe te voegen, en voorproef het in het Beheer van de Correspondentie.
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: 2f996a50-7c7d-41b6-84b2-523b6609254b
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '3979'
ht-degree: 0%

---

# Letter maken {#create-letter}

## Workflow voor Correspondentenbeheer {#correspondence-management-workflow}

De Correspondentiebeheerworkflow bestaat uit vier fasen:

1. Sjabloon maken
1. Documentfragment maken
1. Letter maken
1. Postverwerking

### Sjabloon maken {#template-creation}

In de volgende afbeelding ziet u een typische workflow voor het maken van een correspondentiesjabloon.

![&#x200B; Werkschema voor het creëren van een correspondentiesjabloon &#x200B;](assets/01.png)

In deze workflow:

1. Formulierontwerpers maken lay-outs en fragmentlay-outs met behulp van Adobe Forms Designer en uploaden deze naar een CRX-opslagplaats. De indelingen bevatten standaardformuliervelden, indelingsfuncties zoals een kop- en voettekst en lege doelgebieden voor de plaatsing van inhoud. Later, brengen de Specialisten van de Toepassing de inhoud in kaart die voor deze doelgebieden wordt vereist. Meer informatie over [&#x200B; het ontwerpen van lay-out &#x200B;](/help/forms/using/layout-design-details.md).
1. Experts op het gebied van Onderwerpen van juridische afdelingen, financiën of marketing maken en uploaden inhoud, zoals disclaimers van tekstclausules, voorwaarden en afbeeldingen, zoals logo&#39;s, die opnieuw worden gebruikt in verschillende correspondentiesjablonen.
1. Toepassingsspecialisten maken correspondentiesjablonen. De toepassingsspecialist

   * Hiermee kunt u tekstclausules en afbeeldingen toewijzen aan doelgebieden in lay-outsjablonen
   * Definieert voorwaarden/regels voor het opnemen van inhoud
   * Hiermee bindt u indelingsvelden en variabelen aan onderliggende gegevensmodellen

1. De auteur geeft een voorvertoning van de brief weer en verzendt deze voor nabewerking. Meer informatie over [&#x200B; postverwerking &#x200B;](/help/forms/using/submit-letter-topostprocess.md).

#### Het gebruiken van brievenmalplaatjes die met Correspondentenbeheer worden verstrekt {#using-letter-templates-provided-with-correspondence-management}

In plaats van een lay-outsjabloon helemaal zelf te maken, kunt u de sjablonen die Correspondence Management biedt, wijzigen en opnieuw gebruiken. U kunt ontwerper gebruiken om de branding en de gegevens en inhoudsgebieden van de malplaatjes snel te wijzigen om de behoeften van uw organisatie aan te passen. Voor meer informatie over de malplaatjes van het Beheer van de Correspondentie, zie [&#x200B; de briefmalplaatjes van de Referentie &#x200B;](/help/forms/using/reference-cm-layout-templates.md).

### Document fragment maken {#document-fragment-creation}

Documentfragmenten zijn herbruikbare\nonderdelen van correspondentie waarmee u letters\correspondentie kunt samenstellen.

De documentfragmenten zijn van de volgende typen:

#### Tekst {#text}

Een tekstelement is een stuk inhoud dat bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn. Een dynamische alinea bevat verwijzingen naar gegevenselementen waarvan de waarden bij uitvoering worden verschaft.

#### Lijst {#list}

List is een reeks documentfragmenten, zoals tekst, lijsten (dezelfde lijst kan niet op zichzelf worden toegevoegd), voorwaarden en afbeeldingen. De volgorde van de lijstelementen kan vast of bewerkbaar zijn. Tijdens het maken van een letter kunt u enkele of alle lijstelementen gebruiken om een herbruikbaar patroon van elementen te repliceren.

#### Voorwaarde {#condition}

De voorwaarden laten u toe om te bepalen welke inhoud inbegrepen bij de tijd van de brievenverwezenlijking wordt, die op de geleverde gegevens wordt gebaseerd. De voorwaarde wordt beschreven in termen van controlevariabelen. De variabelen kunnen een gegevenswoordenboekelement of een plaatsaanduiding zijn. Wanneer u een voorwaarde toevoegt, kunt u verkiezen om een activa op te nemen die op de waarde wordt gebaseerd die de controlevariabele heeft. Voorwaarden hebben één uitvoer op basis van een expressie. De eerste expressie wordt op basis van de variabele van de huidige voorwaarde op true ingesteld. De waarde ervan wordt de uitvoer van de voorwaarde.

#### Lay-outfragment {#layout-fragment}

Een lay-outfragment is een lay-out die binnen één of meerdere letters kan worden gebruikt. Een lay-outfragment wordt gebruikt om herhaalbare patronen, vooral dynamische lijsten tot stand te brengen. De indeling kan typische formuliervelden bevatten, zoals &quot;Adres&quot; en &quot;Referentienummer&quot;. Het bevat ook lege subformulieren die doelgebieden aangeven. De lay-outs (XDPs) worden gecreeerd in Designer en dan [&#x200B; geupload aan Forms en Documenten &#x200B;](/help/forms/using/get-xdp-pdf-documents-aem.md).

### Letter maken {#letter-creation}

Er zijn twee manieren om de correspondentie te produceren die naar uw klanten wordt verzonden: gebruiker-gedreven en systeem-gedreven.

#### Door gebruiker aangedreven {#user-driven}

Aan de klant gerichte werknemers zoals schaderegelaars of casewerkers kunnen aangepaste correspondentie maken. Met een eenvoudige en intuïtieve interface voor het vullen van letters kunnen zakelijke gebruikers optionele tekst aan de correspondentie toevoegen, bewerkbare inhoud personaliseren en de correspondentie in real-time voorvertonen. Zij kunnen dan de aangepaste correspondentie aan een achtereind proces voorleggen.

![&#x200B; gebruiker-gedreven, aangepaste correspondentie &#x200B;](assets/02.png)

#### Systeemgestuurd {#system-driven}

Het genereren van correspondentie wordt geautomatiseerd, gestuurd door gebeurtenistriggers. Een herinnering die bijvoorbeeld naar een burger wordt gestuurd en die haar vraagt om een voorafgaande belastingaangifte, wordt gegenereerd door de vooraf gedefinieerde sjabloon samen te voegen met burgergegevens. De laatste letter kan worden gemaild, afgedrukt, gefaxt of gearchiveerd.

![&#x200B; systeem-gedreven correspondentie &#x200B;](assets/us_cm_generate.png)

### Post-verwerking {#post-processing}

De uiteindelijke correspondentie kan voor nabewerking naar een back-end proces worden gestuurd. De correspondentie kan zijn:

1. Verwerkt voor afdrukken via e-mail, fax of batch of in een map geplaatst voor afdrukken of e-mailen.
1. Ter controle en goedkeuring ingediend.
1. Beveiligd door het toepassen van digitale handtekeningen, certificering, codering of rechtenbeheer.
1. Omgezet in een doorzoekbaar PDF-document dat alle metagegevens bevat die nodig zijn voor archivering en controle.
1. Opgenomen in een PDF-Portfolio dat meer documenten bevat, zoals marketingmateriaal. Het PDF-Portfolio kan vervolgens als laatste briefwisseling worden verzonden.

### Correspondentenbeheeroplossingsarchitectuur {#correspondence-management-solution-architecture}

De volgende afbeelding biedt een overzicht van een voorbeeldarchitectuur van de Letters Solution.

![&#x200B; de oplossingsarchitectuur van de Brief &#x200B;](assets/us_cm_architecture_es3.png)

## Een letter deconstrueren {#deconstructing-a-letter}

Dit annuleringsdocument is een voorbeeld van een gebruikelijke correspondentie:

![&#x200B; een steekproefbrief van annulering &#x200B;](assets/5_deconstructingaletter.png)

<table> 
 <tbody> 
  <tr> 
   <td><strong>Letter-elementen</strong></td> 
   <td><strong>Beschrijving</strong></td> 
   <td><strong>Opgemaakt met</strong></td> 
  </tr> 
  <tr> 
   <td>Gegevens van back-end bedrijfssystemen</td> 
   <td>Gegevens die afkomstig zijn van back-end bedrijfssystemen. De gegevens worden dynamisch samengevoegd met de correspondentiesjabloon.</td> 
   <td>Het <br /> dossier van Gegevens dat op een Woordenboek van Gegevens wordt gecreeerd</td> 
  </tr> 
  <tr> 
   <td>Gegevens <br /> ingegaan door front-line Werknemer</td> 
   <td>Gegevens die door een front-line werknemer kunnen worden geleverd die de brief alvorens het uit te verzenden aanpast.<br /> </td> 
   <td><p>Niet-beveiligde DD-elementen <br /> Bewerkbare tekstalinea's <br /> Variabelen/plaatsaanduidingen <br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Vooraf goedgekeurde <br /> tekstalinea's</td> 
   <td>Vooraf goedgekeurde tekstinhoud. Deskundigen in Juridische Zaken, Financiën, of een lijn van zaken die de bedrijfscontext van de brief begrijpen, typisch auteur de tekstinhoud. De meeste letters bevatten inhoud zoals koptekst, voettekst, disclaimers en aanhef. Inhoud zoals "reden tot beëindiging" zou echter specifiek zijn voor de desbetreffende brief.</td> 
   <td><p>Voorwaarden\indeling tekst\lijsten\<br /></p> <p> </p> </td> 
  </tr> 
  <tr> 
   <td>Gegevens <br /> Gebaseerd op Aangepaste logica?</td> 
   <td>Voor sommige letters, zoals een brief om meer informatie over een claim te vragen, kunnen gebruikers zoals de Aanpassing van claims aangepaste tekst toevoegen.</td> 
   <td>Document <br /> Fragment of type Condition </td> 
  </tr> 
  <tr> 
   <td>Opgeslagen <br /> afbeeldingen uit centrale opslagplaats</td> 
   <td>Afbeeldingen zoals logo's en handtekeningafbeeldingen. Afbeeldingen zoals bedrijfslogo's worden in de meeste of alle correspondentie weergegeven. Afbeeldingen van handtekeningen zijn specifiek voor de brief en voor de persoon namens wie de brief wordt verzonden.</td> 
   <td><p>Beelden opgeslagen in AEM elementen (DAM) <br /> </p> <p> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Een brief analyseren voordat u deze samenstelt {#analyze-a-letter-before-you-construct-it}

Analyseer elke brief om de verschillende stukken te ontdekken die de brief vormen. De toepassingsspecialist analyseert de correspondentie die wordt gegenereerd.

* Welke delen van de correspondentie statisch en dynamisch zijn. De variabelen die worden ingevuld vanuit achterwaartse gegevensbronnen of door eindgebruikers.
* De volgorde waarin de verschillende tekstalinea&#39;s in de correspondentie worden weergegeven, bijvoorbeeld of een zakelijke gebruiker alinea&#39;s kan wijzigen tijdens het maken van correspondentie.
* Is het correspondentiesysteem gegenereerd of vereist het dat een eindgebruiker de correspondentie bewerkt? Hoeveel correspondentie wordt door het systeem gegenereerd en hoeveel gebruikers moeten ingrijpen?
* Hoe vaak verandert het correspondentiesjabloon? Wordt het jaarlijks, driemaandelijks, of slechts wanneer een bepaalde wetgeving verandert, bijgewerkt? Welk type van veranderingen wordt verwacht? Is het een verandering om typografische fouten, een lay-outverandering te bevestigen, meer gebieden toe te voegen, meer paragrafen toe te voegen, etc.
* Wanneer u uw correspondentievereisten plant, stel de lijst van nieuwe correspondentiesjablonen samen. Voor elke correspondentiesjabloon hebt u het volgende nodig:

   * Tekstclausules, afbeeldingen en tabellen
   * Gegevenswaarden van back-endsystemen
   * De lay-out en fragmentlay-outs van de overeenkomst
   * De volgorde waarin de inhoud in de brief staat en de regels voor het opnemen en uitsluiten van inhoud

* De voorwaarden waaronder zakelijke gebruikers, zoals schaderegelaars of casewerkers, inhoud of gedeelten van de letter wijzigen.
* Scenario&#39;s zijn verhalen die de gebruikerservaring, de vereisten, en de voordelen beschrijven om de Oplossing van Letters te gebruiken.
* De scenario&#39;s verstrekken ook:De vereiste vaardigheidsreeksen en de hulpmiddelen u voor uw project vereist.
* Aanbevolen procedures voor het plannen van uw implementatie. &quot;Implementatieoverzicht op hoog niveau.

## Voordelen van het uitvoeren van de analyse {#benefits-of-performing-the-analysis}

**Inhoud hergebruik** U hebt een geconsolideerde lijst van nieuwe inhoud die voor het produceren van correspondentie wordt vereist. Veel van de inhoud, zoals kop- en voetteksten, disclaimers en introducties, komt voor in veel letters en kan in verschillende letters worden hergebruikt. Al dergelijke gemeenschappelijke inhoud kan eenmaal door deskundigen worden gecreëerd en goedgekeurd en vervolgens in veel correspondentie worden hergebruikt.

**bouwend het gegevenswoordenboek** Er zullen gegevenswaarden zoals &quot;identiteitskaart van de Klant&quot;en &quot;Naam van de Klant&quot;zijn die voor vele brieven gemeenschappelijk zijn. U kunt een geconsolideerde lijst van al dergelijke gegevenswaarden opstellen. Meestal wordt iemand van het middleware-team van de onderneming geraadpleegd bij het plannen van de structuur. Dit vormt de basis voor het samenstellen van het gegevenswoordenboek.

**het Bronnen gegevens van de systemen van de achterste onderneming** u zult ook alle gegevenswaarden kennen die nodig zijn en van waar de gegevens van het ondernemingssysteem worden verkregen. U kunt de implementatie vervolgens archiveren om de gegevens uit het bedrijfssysteem te halen en de oplossing Letters te gebruiken.

**die de ingewikkeldheid van brieven** schatten is het belangrijk om te bepalen hoe complex het zal zijn om een bepaalde correspondentie tot stand te brengen. Deze analyse helpt in het bepalen van de hoeveelheid tijd en vaardigheidsreeksen die zullen worden vereist om de brievenmalplaatjes tot stand te brengen. Dit zal op zijn beurt helpen bij het schatten van de middelen en kosten voor de implementatie van de oplossing Letters.

## Correspondentie-complexiteit {#correspondence-complexity}

De complexiteit van de correspondentie kan worden bepaald door de volgende parameters te analyseren:

**ingewikkeldheid van de Lay-out** Hoe complex is de lay-out? Letters zoals Bericht van annulering hebben eenvoudige lay-outs. Terwijl letters zoals de bevestiging van de dekking voor claims een complexe indeling hebben met verschillende tabellen en meer dan 60 formuliervelden. Het maken van complexe lay-outs kost meer tijd en vereist geavanceerde vaardigheden voor het ontwerpen van lay-outs.

**Aantal tekstparagrafen en voorwaarden** Een leningscontract kan 10 pagina&#39;s lang zijn en meer dan 40 tekstclausules bevatten. Veel van deze clausules zouden afhangen van &quot;leningparameters. Op basis van de exacte voorwaarden zouden de clausules worden opgenomen in of uitgesloten van het contract. Het creëren van dergelijke brieven vereist grondige planning en zorgvuldige definitie van de complexe voorwaarden.

In deze tabel vindt u een aantal richtlijnen waarmee u uw letters kunt classificeren:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Complexiteitsniveau</strong></p> </td> 
   <td><p><strong>Indelingscomplexiteit (subjectief)</strong></p> </td> 
   <td><p><strong>Aantal tekstalinea's</strong></p> </td> 
   <td><p><strong>Aantal voorwaardelijke teksten of afbeeldingen</strong></p> </td> 
   <td><p><strong>Vereiste vaardigheidsset</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Lage complexiteit</p> </td> 
   <td><p>Laag. Indeling heeft weinig formuliervelden (&lt;15).</p> <p>Typisch één pagina <span class="acrolinxCursorMarker"></span>.</p> </td> 
   <td><p>8</p> </td> 
   <td><p>1</p> </td> 
   <td><p>Medium Designer.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Medium-complexiteit</p> </td> 
   <td><p>Lay-out complexiteit van Medium. Omvat structuren zoals tabellen. Doorgaans meerdere pagina's lang.</p> </td> 
   <td><p>16</p> </td> 
   <td><p>2</p> </td> 
   <td><p>Medium Designer.</p> <p> </p> <p>Mogelijkheid om complexe expressies te maken met gebruikersinterfaces.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Hoge complexiteit</p> </td> 
   <td><p>Complexe indeling. Kan uit meer dan drie pagina's bestaan. Bevat tabellen en meer dan 60 formuliervelden.</p> </td> 
   <td><p>40</p> </td> 
   <td><p>8</p> </td> 
   <td><p>Expert Designer.</p> <p> </p> <p>Mogelijkheid om complexe expressies te maken met gebruikersinterfaces.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Overzicht van het maken van een letter {#overview-of-creating-a-letter}

1. Selecteer de juiste indeling die als basis voor de letter fungeert en maak een letter.
1. Voeg gegevensmodules of lay-outfragmenten aan de brief toe en vorm hen.
1. Geef een voorvertoning van de correspondentie weer.
1. Bewerk de velden, variabelen, inhoud en bijlagen en stel deze in.

### Vereisten {#prerequisites}

U hebt eerst het volgende nodig om een correspondentie te maken:

* [&#x200B; Pakket van de Verenigbaarheid &#x200B;](compatibility-package.md). Installeer het Pakket van de Verenigbaarheid om de **Brieven** optie op de **Forms** pagina te bekijken.
* De brief XDP ([&#x200B; lay-out &#x200B;](/help/forms/using/document-fragments.md)).
* Andere XDPs ([&#x200B; lay-outfragmenten &#x200B;](document-fragments.md#document-fragments)) die delen van de brief vormen. De Lay-outs XDPs \ worden gecreeerd in [&#x200B; Designer &#x200B;](https://www.adobe.com/go/learn_aemforms_designer_65).
* Het relevante [&#x200B; gegevenswoordenboek &#x200B;](/help/forms/using/data-dictionary.md) (Facultatief).
* De [&#x200B; gegevensmodules &#x200B;](/help/forms/using/document-fragments.md) u in de correspondentie wilt gebruiken.
* [&#x200B; Gegevens van de Test &#x200B;](/help/forms/using/data-dictionary.md#p-working-with-test-data-p) is het dossier van XML met de testgegevens die in het worden uitgevoerd. Testgegevens zijn vereist als u een gegevenswoordenboek gebruikt.

## Een lettertypesjabloon maken {#create-a-letter-template}

### Selecteer een lay-out en voer de lettereigenschappen in {#select-a-layout-and-enter-the-letter-properties}

1. Selecteer **Forms** > **Brieven**.

1. Selecteer **creeer > Brief**. Correspondence Management geeft de beschikbare lay-outs (XDP&#39;s) weer. Deze lay-outs komen uit Designer. De indelingen bevatten ook de lettertypesjablonen die in het vak Correspondentiebeheer zijn opgegeven. Voor meer informatie over de malplaatjes van het Beheer van de Correspondentie, zie [&#x200B; de briefmalplaatjes van de Referentie &#x200B;](/help/forms/using/reference-cm-layout-templates.md). Om uw eigen lay-outs toe te voegen, creeer XDP (lay-out) dossiers in Designer en dan [&#x200B; upload hen aan AEM Forms &#x200B;](/help/forms/using/get-xdp-pdf-documents-aem.md).

   ![&#x200B; creeer-brief &#x200B;](assets/create-letter.png)

1. Selecteer een lay-out door het te tikken en te selecteren **daarna**.

   ![&#x200B; Uitgezochte lay-out om een brief &#x200B;](assets/selectlayout.png) te creëren

1. Ga de eigenschappen voor de Correspondentie in en selecteer **sparen:**

   * **Titel (Facultatief):** ga de titel voor de brief in. De titel hoeft niet uniek te zijn en kan speciale tekens en niet-Engelse tekens bevatten.
   * **Naam:** De unieke naam voor de brief. Geen twee letters in een staat kunnen bestaan met dezelfde naam. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.
   * **Beschrijving (Facultatief):** beschrijf de brief voor uw verwijzing.
   * **Woordenboek van Gegevens (Facultatief)**: Het Woordenboek van Gegevens kan aan de correspondentie worden geassocieerd. De elementen die u later in deze correspondentie invoegt, moeten ofwel hetzelfde gegevenswoordenboek hebben als het gegevenswoordenboek dat u hier voor de correspondentie kiest, ofwel geen gegevenswoordenboek.
   * **Markeringen (Facultatief):** selecteer de markeringen om op de correspondentie van toepassing te zijn. U kunt ook een nieuwe/aangepaste tagnaam typen en op Enter drukken om deze te maken.
   * **Proces van Post (Facultatief):** selecteer het postproces dat op het brievenmalplaatje moet worden toegepast. Er zijn geen postprocessen in de doos en degenen u gebruikend AEM, zoals e-mail en druk hebt gecreeerd.

   ![&#x200B; Eigenschappen van de Correspondentie &#x200B;](assets/createcorrespondenceproperties.png)

1. Het systeem geeft een bericht weer: &quot;Letter created successfully.&quot; (in het waakzame bericht) Uitgezocht **Open** om de gegevensmodules en lay-outfragmenten in het te vormen. Of selecteer **Gereed** om terug naar de vorige pagina te gaan.

   ![&#x200B; Waakzaam bericht: met succes gecreeerde brief &#x200B;](assets/createcorrespondencecreated.png)

   **Volgende**: Wanneer u **Open** selecteert, toont het Beheer van de Correspondentie een vertegenwoordiging van de lay-out met alle vermelde componenten in de lay-out (XDP). Ga met het opnemen van de [&#x200B; Modules van Gegevens en de Fragmenten van de Lay-out door en het Vormen van hen &#x200B;](/help/forms/using/create-letter.md#p-insert-data-modules-and-layout-fragments-in-a-letter-and-configure-them-p).

### Gegevensmodules en lay-outfragmenten in een brief opnemen en hen vormen {#insert-data-modules-and-layout-fragments-in-a-letter-and-configure-them}

Wanneer u een correspondentie hebt gemaakt, selecteert u Openen, wordt in Correspondentiebeheer een weergave weergegeven van de indeling met alle subformulieren/doelgebieden in de indeling (XDP). In elk van de doelgebieden kunt u een gegevensmodule of een layoutfragment invoegen (en vervolgens gegevensmodules in het lay-outfragment).

>[!NOTE]
>
>U kunt er ook voor kiezen om het pictogram Bewerken te selecteren voor een letter op de pagina Letters om gegevensmodules en lay-outfragmenten in een letter in te voegen en ze te configureren.

1. Selecteer **Tussenvoegsel** voor elk van de subformulieren en selecteer de Modules van Gegevens of een Fragment van de Lay-out in elk van de subformulieren op te nemen.

   ![&#x200B; de gegevensmodules van het Tussenvoegsel en lay-outfragmenten &#x200B;](assets/insertdmandlf.png)

1. Selecteer Gegevensmodule of Lay-outfragment voor deze opties voor elk van de subformulieren en kies vervolgens de gegevensmodules of de layoutfragmenten die u wilt invoegen. Met een lay-outfragment kunt u verder gegevensmodules of lay-outfragmenten in het fragment invoegen op basis van het ontwerp (maximaal vier niveaus).

   ![&#x200B; nestedlf &#x200B;](assets/nestedlf.png)

1. Als u een indelingsfragment invoegt, wordt de naam van het indelingsfragment in het subformulier weergegeven. En volgens het geselecteerde fragment worden geneste subformulieren weergegeven in het subformulier.
1. Nadat de gekozen Modules van Gegevens in de lay-out worden opgenomen, kunt u vormen wijze selecteren en het volgende plaatsen nadat het Tikken van het Edit pictogram voor elk van de modules:

   1. **Bewerkbaar**: Wanneer deze optie wordt geselecteerd, kan de inhoud in Create Correspondence gebruikersinterface worden uitgegeven. Inhoud alleen als bewerkbaar markeren als de zakelijke gebruiker deze hoeft te wijzigen (bijvoorbeeld Aanpassingen).
   1. **Verplicht**: Wanneer deze optie wordt geselecteerd, wordt de inhoud vereist in Create Correspondence gebruikersinterface.
   1. **Geselecteerd**: Wanneer deze optie wordt geselecteerd, wordt de inhoud geselecteerd door gebreken in het Create Correspondence gebruikersinterface.
   1. **Inspringing**: Verhoog of verklein de inspringing van de module/inhoud in de brief. De inspringing wordt opgegeven in niveaus, vanaf 0. Elk niveau springt 36 punten in. Voor meer informatie bij het aanpassen van vormen, zie **[!UICONTROL Correspondence Management Configurations]** in [&#x200B; het werkschema van Forms &#x200B;](submit-letter-topostprocess.md#formsworkflow).
   1. **de onderbreking van de Pagina vóór**: Als u de Onderbreking van de Pagina vóór aan op plaatst, toont de inhoud van DEZE module altijd op een nieuwe pagina.
   1. **de onderbreking van de Pagina na**: Als u de Onderbreking van de Pagina na aan voor een specifieke module plaatst, de inhoud van de Volgende module altijd op een nieuwe pagina tonen.

   ![&#x200B; Ingevoegde gegevensmodules en lay-outfragmenten &#x200B;](assets/insertdmandlf2.png)

1. Als u een module wilt bewerken, selecteert u het pictogram Bewerken naast de module. Na het uitgeven van de modules, uitgezocht **sparen**.

   Op deze pagina kunt u ook het volgende doen voor de subformulieren:

   1. **staat Vrije Tekst** toe: Als vrije Tekst wordt toegelaten dan kan de gebruiker inlinetekst in brief in mening toevoegen CCR. In de CCR-weergave is de actie &#39;T&#39; ingeschakeld voor de doelgebieden waarvoor de optie Vrije tekst toestaan is ingeschakeld. Wanneer de gebruiker deze optie selecteert, wordt om de naam en beschrijving van de tekst gevraagd en wordt bij het tikken de tekst geopend in de bewerkingsmodus waar de gebruiker tekst kan toevoegen. Dit werkt dus net als andere tekstmodules
   1. **de Orde van het Slot**: Vergrendelt de orde van subforms in de brief. De auteur mag de subformulieren/componenten niet opnieuw ordenen tijdens het maken van de letter.

   Op deze pagina kunt u ook het volgende doen voor elk element in de subformulieren:

   1. **verander de orde van de activa**: belemmering-en-dalings activa die het herschikkingspictogram voor activa houden ( ![&#x200B; dragndrop &#x200B;](assets/dragndrop.png)).
   1. **activa van de Schrapping**: Selecteer het pictogram van de Schrapping naast activa om het te schrappen.
   1. **activa van de Voorproef**: Selecteer het pictogram van de showvoorproef ( ![&#x200B; showpreview &#x200B;](assets/showpreview.png)) naast een activa.

1. Selecteer **daarna**.
1. Op de gegevenspagina ziet u hoe gegevensvelden en variabelen in de sjabloon worden gebruikt. Gegevens kunnen worden gekoppeld aan gegevensbronnen zoals een gegevenswoordenboek of gebruikersinvoer. Elk veld definieert eigenschappen waarvan gegevens in gegevenswoordenboeken worden toegewezen of welk bijschrift wordt weergegeven voor invoervelden van gebruikers.

   Koppeling:

   * De **gebied** elementen kunnen met letterlijk, gegevenswoordenboekelement, een activa, of een gebruiker worden verbonden gespecificeerde waarde. U kunt een veldelement ook negeren door het aan de Negeren optie te binden.
   * De **veranderlijke** elementen kunnen met letterlijk, gegevenswoordenboekelement, een gebied, een variabele, een activa, of een gebruiker worden verbonden gespecificeerde waarde.

   Hier volgen enkele hoofdvelden in de koppeling:

   * **multi-line**: U kunt specificeren als de gegevensingang voor een gebied of een variabele multi-line is. Als u deze optie selecteert, wordt het invoervak voor het veld of de variabele weergegeven als een invoervak met meerdere regels in de weergave Gegevens bewerken. Het veld of de variabele wordt ook als meerdere regels weergegeven in de weergave Gegevens en inhoud in de gebruikersinterface Correspondentie maken. Het invoerveld met meerdere regels is vergelijkbaar met het veld voor het invoeren van een opmerking in een TextModule. De optie voor meerdere regels is alleen beschikbaar voor velden en variabelen met het koppelingstype Gebruiker of niet-beveiligde gegevenswoordenboekelementen.
   * **Facultatief**: U kunt specificeren als de waarde voor gebied of variabele of niet facultatief is. De optionele veldoptie is beschikbaar voor velden en variabelen met koppelingstype Gebruiker of niet-beveiligde gegevenswoordenboekelementen.

   * **Gebied/Variabele Bevestiging**: Om verbeterde bevestiging van de waarde van een gebied of een variabele te verstrekken, kunt u een validator aan het gebied of de variabele toewijzen. Deze optie is alleen beschikbaar voor velden en variabelen met het koppelingstype Gebruiker of niet-beveiligde gegevenswoordenboekelementen.
   * **Titel** en **Tooltip**: De titel is het etiket van het gebied dat vóór het gebied in het CCR gebruikersinterface verschijnt. Deze optie is beschikbaar voor velden en variabelen met het koppelingstype Gebruiker of niet-beveiligde gegevenswoordenboekelementen.

   Hieronder vindt u de validatietypen die u kunt gebruiken voor de velden:

   * **Validator van het Koord**: Gebruik Validator van het Koord om een minimum en maximumlengte van het koord te specificeren ingegaan op gebied of variabele. Wanneer u een validator voor tekenreeksen maakt, moet u geldige validatieparameters opgeven. Voer een geldige lengte in voor zowel de minimum- als de maximumwaarde. Voor de validator van het Koord, kunt u de min en maximumlengte van de waarde specificeren die kan worden ingegaan. Als de ingevoerde waarde niet overeenkomt met de opgegeven minimale en maximale waarde, wordt het desbetreffende veld in de CCR-gebruikersinterface rood weergegeven.

   * **Validator van het Aantal**: Gebruik Validator van het Aantal om de minimum en maximumnumerieke waarde te specificeren ingegaan op een gebied of een variabele. Wanneer u een Number Validator maakt, moet u geldige validatieparameters opgeven. Voer numerieke waarden in voor zowel de minimum- als de maximumwaarde.

   * **Regelmatige Validator van de Uitdrukking**: Gebruik de Regelmatige Validator van de Uitdrukking om een regelmatige uitdrukking te bepalen die wordt gebruikt om de waarde van een gebied of een variabele te bevestigen. Daarnaast kunt u het foutbericht aanpassen. Wanneer u een validator voor reguliere expressies maakt, moet u geldige reguliere expressies opgeven.

   >[!NOTE]
   >
   >De validators voor velden en variabelen zijn alleen beschikbaar voor velden of variabelen met het koppelingstype Gebruiker of niet-beveiligde gegevenswoordenboekelementen.

   ![&#x200B; verbindingen &#x200B;](assets/linkages.png)

1. Na het specificeren van verbinding, selecteer **daarna**. Correspondentiebeheer geeft het scherm Bijlagen weer.

### De bijlagen instellen {#set-up-the-attachments}

1. Selecteer **Activa** toevoegen.
1. In het Uitgezochte scherm van Activa, selecteer de activa om met de brief vast te maken en **te selecteren Gedaan**. De elementen moeten eerst naar Assets worden geüpload. U kunt het beste alleen PDF- en Microsoft Office-documenten bijvoegen, maar ook afbeeldingen. Voor meer informatie bij het uploaden van activa in DAM, zie [&#x200B; Uploading Assets &#x200B;](/help/assets/manage-assets.md).
1. Om de orde van de activa in de lijst te sluiten zodat de Aanpasser van Vorderingen niet de orde kan veranderen, uitgezochte **Orde van het Slot**. Als u deze optie niet selecteert, kan de Aanpassing van claims de volgorde van de lijstitems wijzigen.
1. Om de orde van de activa te veranderen, sleep-en-dalings activa die het herschikkingspictogram voor activa houden ( ![&#x200B; dragndrop &#x200B;](assets/dragndrop.png)).
1. Selecteer **uitgeven** vóór een gehechtheid en specificeer een gehechtheid zoals Verplicht als u niet de auteur het wilt kunnen schrappen. Specificeer een gehechtheid zoals Geselecteerd als u het in de interface wilt vooraf worden geselecteerd CCR.
1. Selecteer **Toegang van de Bibliotheek** om de toegang tot de bibliotheek te verlenen. Als Bibliotheektoegang is ingeschakeld, heeft de Aanpasser voor claims toegang tot de inhoudsbibliotheek terwijl een brief wordt gemaakt en bijlagen worden ingevoegd.
1. Selecteer **Configuratie van Bijlagen** en specificeer het maximumaantal gehechtheid.

1. Selecteer **sparen**. Uw correspondentie wordt gecreeerd en op de pagina van Letters vermeld.

Nadat een brievenmalplaatje in het Beheer van de Correspondentie wordt gecreeerd, kan het eind - gebruiker/agent/bewering aanpast de brief in het gebruikersinterface openen CCR en een correspondentie tot stand brengen door gegevens in te gaan, inhoud te plaatsen, en gehechtheid te beheren. Voor meer informatie, zie [&#x200B; Correspondentie &#x200B;](/help/forms/using/create-correspondence.md) creëren.

## Typen koppelingen beschikbaar voor elk veld {#types-of-linkage-available-for-each-of-the-fields}

In de volgende tabel wordt beschreven welke typen koppelingen beschikbaar zijn voor verschillende typen velden.

De volgende waarden in de tabel

* **ja**: Het type van gebied in de uiterst linkse kolom steunt dat type van afbeelding
* **Nr**: Het type van gebied in de uiterst linkse kolom steunt niet dat type van afbeelding
* **N/A**: Het type van gebied in de uiterst linkse kolom is niet van toepassing

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Letterlijk</strong></td> 
   <td><strong>Element</strong></td> 
   <td><strong>Gegevenswoordenboek</strong></td> 
   <td><strong>Negeren</strong></td> 
   <td><strong>Gebruiker</strong></td> 
   <td><strong>Veld</strong></td> 
   <td><strong>Variabele</strong></td> 
  </tr> 
  <tr> 
   <td><strong>date</strong></td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong>tijd</strong></td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong>datetime</strong></td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong>integer</strong></td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja<br /> </td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong>zweven</strong></td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja<br /> </td> 
   <td>NVT</td> 
   <td>N.v.t. <br /> </td> 
  </tr> 
  <tr> 
   <td><strong>richtext</strong></td> 
   <td>Ja</td> 
   <td>alleen tekst</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong> duidelijke </strong> <strong> tekst </strong></td> 
   <td>Ja</td> 
   <td>alleen tekst</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>Ja</td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong>image</strong></td> 
   <td>Nee</td> 
   <td>alleen afbeelding</td> 
   <td>Nee</td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>NVT</td> 
   <td>NVT</td> 
  </tr> 
  <tr> 
   <td><strong>handtekening</strong></td> 
   <td>Nee</td> 
   <td>Nee</td> 
   <td>Nee<br /> </td> 
   <td>Ja</td> 
   <td>Nee</td> 
   <td>NVT</td> 
   <td>N.v.t. <br /> </td> 
  </tr> 
 </tbody> 
</table>

## Kopie van een lettertypesjabloon maken {#createcopylettertemplate}

Met een bestaande lettertypesjabloon kunt u snel een lettertypesjabloon maken met vergelijkbare eigenschappen, inhoud en overgeërfde elementen, zoals documentfragmenten en gegevenswoordenboek. Kopieer en plak een brief om dit te doen.

1. Selecteer een of meer letters op de pagina Letters. In de gebruikersinterface wordt het pictogram Kopiëren weergegeven.
1. Selecteer Copy. In de gebruikersinterface wordt het pictogram Plakken weergegeven. U kunt er ook voor kiezen om in een map te gaan voordat u plakt. Verschillende mappen kunnen elementen met dezelfde naam bevatten. Voor meer informatie over omslagen, zie [&#x200B; Omslagen en het organiseren van activa &#x200B;](/help/forms/using/import-export-forms-templates.md#folders-and-organizing-assets).
1. Selecteer Plakken. Het dialoogvenster Plakken wordt geopend. Als u de letters op dezelfde plaats kopieert en plakt, wijst het systeem automatisch namen en titels toe aan de nieuwe exemplaren van letters, maar u kunt de titels en namen van de letters bewerken.
1. Bewerk indien nodig de titel en de naam waarmee u de kopie van de brief wilt opslaan.
1. Selecteer Plakken. De kopie van de brief wordt gemaakt. Nu kunt u de vereiste wijzigingen aanbrengen in uw nieuwe brief.
