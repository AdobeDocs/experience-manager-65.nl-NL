---
title: Beste praktijken voor het werken met adaptieve vormen
seo-title: Beste praktijken voor het werken met adaptieve vormen
description: Verklaart beste praktijken voor vestiging een project van Vormen AEM, ontwikkelend adaptieve vormen, en optimaliserend de prestaties voor het systeem van Vormen AEM.
seo-description: Verklaart beste praktijken voor vestiging een project van Vormen AEM, ontwikkelend adaptieve vormen, en optimaliserend de prestaties voor het systeem van Vormen AEM.
uuid: ed95fc64-56b3-4ea1-a5ba-2e96953fca56
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 43c431e4-5286-4f4e-b94f-5a7451c4a22c
translation-type: tm+mt
source-git-commit: dbfadb0b49c83c38aa2cb55c32517ad70bbd79d0

---


# Beste praktijken voor het werken met adaptieve vormen {#best-practices-for-working-with-adaptive-forms}

## Overzicht {#overview}

De vormen van de Manager van de Ervaring van Adobe (AEM) kunnen u helpen complexe transacties in eenvoudige, heerlijke digitale ervaringen omzetten. Nochtans, vereist het gezamenlijke inspanning om, een efficiënt en productief ecosysteem van de Vormen van AEM uit te voeren, te bouwen, uit te voeren en te handhaven.

Dit document verstrekt richtlijnen en aanbevelingen die beheerder, auteurs, en ontwikkelaars vormen van wanneer het werken met Vormen AEM, vooral de adaptieve vormencomponent kunnen profiteren van. Het bespreekt beste praktijken recht van vestiging een project van de vormenontwikkeling aan het vormen van, het aanpassen van, het ontwerpen van, en het optimaliseren van Vormen AEM. Deze beste praktijken dragen collectief bij tot de algemene prestaties van het ecosysteem van de Vormen van AEM.

Bovendien zijn hier sommige geadviseerde leest voor algemene AEM beste praktijken:

* [Beste praktijken: AEM implementeren en onderhouden](/help/sites-deploying/best-practices.md)
* [Beste praktijken: Inhoud ontwerpen](/help/sites-authoring/best-practices.md)
* [Beste praktijken: AEM-beheer](/help/sites-administering/administer-best-practices.md)
* [Beste praktijken: Oplossingen ontwikkelen](/help/sites-developing/best-practices.md)

## De opstelling en vormt Vormen AEM {#set-up-and-configure-aem-forms}

### Project voor de ontwikkeling van formulieren {#setting-up-forms-development-project}

Een vereenvoudigde en gestandaardiseerde projectstructuur kan de ontwikkelings- en onderhoudsinspanningen aanzienlijk verminderen. Apache Maven is een open-sourcehulpmiddel dat wordt aanbevolen voor de bouw van AEM-projecten.

* Gebruik Apache Maven `aem-project-archetype` om structuur voor AEM-project te maken en te beheren. Het leidt tot geadviseerde structuur en malplaatjes voor uw AEM project. Ook, verstrekt het bouwstijlautomatisering en veranderingscontrolesystemen helpen het project beheren.

   * Gebruik het beproefde `archetype:generate` bevel om de aanvankelijke structuur te produceren.
   * Het gebruik maakte `eclipse:eclipse` bevel om de eclips projectdossiers te produceren en het project in te voeren in eclips.

Voor meer informatie, zie [hoe te AEM Projecten bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md).

* Met de tool FileVault of VLT kunt u de inhoud van een CRX- of AEM-instantie in kaart brengen in uw bestandssysteem. Het verstrekt de beheersverrichtingen van de veranderingscontrole, zoals controle en controle van de AEM- projectinhoud. Zie [hoe te om het Hulpmiddel](/help/sites-developing/ht-vlttool.md)te gebruiken VLT.

* Als u Eclipse-Geïntegreerde ontwikkelomgeving gebruikt, kunt u de hulpmiddelen van de Ontwikkelaar van AEM voor naadloze integratie van winde van de Verduistering met AEM instanties gebruiken om toepassingen tot stand te brengen AEM. Voor details, zie de [ontwikkelaarhulpmiddelen van AEM voor Verduistering](/help/sites-developing/aem-eclipse.md).

### Planning voor ontwerpomgeving {#planning-for-authoring-environment}

Zodra u uw AEM projectopstelling hebt, bepaal strategie voor creatie en het aanpassen van adaptieve vormenmalplaatjes en componenten.

* Een adaptief vormmalplaatje is een gespecialiseerde AEM- pagina die structuur en de kopbal-footer informatie van een adaptieve vorm bepaalt. Een malplaatje heeft preconfigured lay-outs, stijlen, en basisstructuur voor een adaptieve vorm. De Vormen van AEM verstrekt uit-van-de-doosmalplaatjes en componenten die u aan auteur kunt gebruiken adaptieve vormen. Nochtans, kunt u douanemalplaatjes en componenten tot stand brengen volgens uw vereisten. Het verdient aanbeveling om vereisten te verzamelen voor extra sjablonen en onderdelen die u nodig hebt in uw adaptieve formulieren. Voor details, zie het [Aanpassen van adaptieve vormen en componenten](/help/forms/using/adaptive-forms-best-practices.md#customize-components).
* De Vormen van AEM staat u toe om adaptieve vormen tot stand te brengen die op de volgende vormmodellen worden gebaseerd. De vormmodellen fungeren als interface voor gegevensuitwisseling tussen een formulier en een AEM-systeem en bieden een op XML gebaseerde structuur voor gegevensstroom binnen en buiten een adaptieve vorm. Ook, leggen de vormmodellen regels en beperkingen op aanpassingsvormen in de vorm van schema en beperkingen XFA op.

   * **Geen**: De aanpassingsvormen die met deze optie worden gecreeerd gebruiken geen vormmodel. De gegevens XML die van dergelijke vormen wordt geproduceerd heeft vlakke structuur met gebieden en overeenkomstige waarden.
   * **XML- of JSON-schema**: De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin het gegeven door het achterste deelsysteem in uw organisatie wordt geproduceerd of verbruikt. U kunt een schema aan een adaptieve vorm associëren en zijn elementen gebruiken om dynamische inhoud aan de adaptieve vorm toe te voegen. De elementen van het schema zijn beschikbaar in het lusje van de Objecten van het Model van Gegevens van inhoudsbrowser voor creatie adaptieve vormen. U kunt de schemaelementen slepen-laten vallen om de vorm te bouwen.
   * **Formuliermodel** XFA: Het is een ideaal vormmodel als u investeringen in op XFA-Gebaseerde HTML5 vormen hebt. Het verstrekt een directe manier om uw op XFA-Gebaseerde vormen in aanpassingsvormen om te zetten. Bestaande XFA-regels worden in de bijbehorende adaptieve vormen gehandhaafd. De resulterende adaptieve vormen steunen concepten XFA, zoals bevestigingen, gebeurtenissen, eigenschappen, en patronen.
   * **Model** formuliergegevens: Het is een aangewezen vormmodel als u uw achterste deelsystemen zoals gegevensbestanden, de Webdiensten, en het gebruikersprofiel van AEM probeert te integreren om adaptieve vormen voor te bereiden en voorgelegde vormgegevens terug in de achterste deelsystemen te schrijven. Een modelredacteur van de Gegevens van de Vorm laat u entiteiten en de diensten in een model van vormgegevens bepalen en vormen dat u kunt gebruiken om adaptieve vormen tot stand te brengen. Voor meer informatie, zie de Integratie [van de Gegevens van de Vormen](/help/forms/using/data-integration.md)AEM.

Het is belangrijk om zorgvuldig het gegevensmodel te kiezen dat niet alleen aan uw vereisten voldoet maar uw bestaande investeringen in activa XFA en XSD, als om het even welk uitbreidt. Het wordt geadviseerd om XSD Model te gebruiken om vormmalplaatjes tot stand te brengen omdat geproduceerd XML gegevens zoals per XPATH bevat die door schema wordt bepaald. Het gebruiken van XSD Model als standaardkeus voor het Model van de Gegevens van de Vorm helpt ook omdat het ontwerp van achterste eindsysteem loskoppelt dat verwerkt en gegevens verbruikt en het de prestaties van vorm wegens één aan één afbeelding van vormgebied verbetert. Ook, kan BindRef van het gebied XPATH van zijn gegevenswaarde in XML worden gemaakt.

Voor meer informatie, zie een [aanpassingsvorm](/help/forms/using/creating-adaptive-form.md)creëren.

* Er zijn enkele gemeenschappelijke secties over adaptieve vormen. U kunt hen identificeren en een strategie bepalen om inhoudshergebruik te bevorderen. De adaptieve vormen staan u toe om stand-alone fragmenten tot stand te brengen en hen over vormen opnieuw te gebruiken. U kunt een paneel in een adaptieve vorm als fragment ook bewaren. Om het even welke verandering in een fragment wordt weerspiegeld in alle bijbehorende vormen. Het helpt u de auteurstijd verminderen en verzekert consistentie over vormen. Bovendien maakt het gebruik van fragmenten adaptieve vormen lichtgewicht resulterend in betere auteurservaring, vooral van grote vormen. Voor meer informatie, zie de [Aanpassings vormfragmenten](/help/forms/using/adaptive-form-fragments.md).

### Aangepaste formulieren en onderdelen aanpassen {#customize-components}

* De Vormen van AEM verstrekt uit-van-de-doos adaptieve vormmalplaatjes die u kunt gebruiken om adaptieve vormen tot stand te brengen. U kunt uw eigen malplaatjes ook tot stand brengen. AEM verstrekt statische en editable malplaatjes.

   * De statische malplaatjes worden bepaald en door ontwikkelaars gevormd.
   * De malplaatjes van Editable worden gecreeerd door auteurs gebruikend malplaatjedacteur. De malplaatjedacteur laat u een basisstructuur en aanvankelijke inhoud in een malplaatje bepalen. Om het even welke wijziging in de structuurlaag wordt weerspiegeld in alle vormen gebruikend dat malplaatje. De aanvankelijke inhoud kan pre-gevormd thema, de prefill dienst omvatten, actie voorleggen, etc. Nochtans, kunnen deze montages voor een vorm worden gewijzigd gebruikend de vormredacteur. Voor meer informatie, zie de [Aanpassings vormmalplaatjes](/help/forms/using/template-editor.md).

* Voor het stileren van een specifieke gebied of paneelinstantie, gebruik [gealigneerde het stileren](/help/forms/using/inline-style-adaptive-forms.md). Alternatief, kunt u een klasse in een CSS dossier bepalen en de klassennaam in het CSS bezit van de Klasse van de component specificeren.
* Omvat een cliëntbibliotheek in een component om stijlen over adaptieve vormen of fragmenten constant toe te passen die die component gebruiken. Voor meer informatie, zie een adaptieve component [van de vormpagina](/help/forms/using/custom-adaptive-forms-templates.md)creëren.
* Pas stijlen toe die in een cliëntbibliotheek worden bepaald om adaptieve vormen te selecteren door de weg aan de cliëntbibliotheek op het CSS gebied van de dossierweg in de adaptieve eigenschappen van de vormcontainer te specificeren.
* Om een cliëntbibliotheek van uw stijlen tot stand te brengen, kunt u het douaneCSS dossier in de de basiscliënt van de Redacteur van het Thema of in de eigenschappen van de Container van de Vorm vormen.
* De aanpassingsvormen verstrekken paneellay-outs, zoals ontvankelijk, van labels voorzien, accordions, en tovenaar, om te controleren hoe de vormcomponenten in een paneel worden opgemaakt. U kunt de lay-outs van het douanepaneel tot stand brengen en hen ter beschikking stellen voor gebruik door vormauteurs. Voor meer informatie, zie het [Creëren van de componenten van de douanelay-out voor aanpassingsvormen](/help/forms/using/custom-layout-components-forms.md).
* U kunt specifieke adaptieve vormcomponenten zoals gebieden en paneellay-out ook aanpassen.

   * Gebruik de [functionaliteit van de Bekleding](/help/sites-developing/overlays.md) van AEM om een exemplaar van een component te wijzigen. Het wordt niet geadviseerd om standaardcomponenten te wijzigen.
   * Om de lay-out van uit-de-doos adaptieve vormcomponenten in /libs aan te passen, [creeer de componenten](/help/forms/using/custom-layout-components-forms.md) van de douanelay-out naast de [standaardlay-outs](/help/forms/using/layout-capabilities-adaptive-forms.md).
   * Introduceer douaneinteractiviteiten door douane widgets of verschijningen te creëren. Het wordt niet geadviseerd om standaardcomponenten te wijzigen. Voor meer informatie, zie het kader [van de](/help/forms/using/introduction-widgets.md)Verschijning.

* Zie Persoonlijke identificeerbare informatie [](/help/forms/using/adaptive-forms-best-practices.md#p-handling-personally-identifiable-information-p) verwerken voor aanbevelingen over de verwerking van PII-gegevens.

## Aanpassingsformulieren voor auteurs {#author-adaptive-forms}

### Het gebruiken van aanraking-geoptimaliseerde UI voor creatie {#using-touch-optimized-ui-for-authoring}

* Gebruik objecten browser in sidebar om snel tot gebieden diep in de vormhiërarchie toegang te hebben. U kunt de onderzoeksdoos aan onderzoek naar voorwerpen in de vorm of objecten boom gebruiken om van één voorwerp aan een andere te navigeren.
* Om de eigenschappen van een component in componentenbrowser in sidebar te bekijken en uit te geven, selecteer de component en klik ![cmp-1](assets/cmppr-1.png). U kunt een component ook tweemaal klikken om zijn eigenschappen in eigenschappen browser te bekijken.
* De toetsenbordkortere weg van het gebruik om snelle acties op uw vormen te nemen. Zie [de Kortere weg van het Toetsenbord van Vormen AEM](/help/forms/using/keyboard-shortcuts.md).

* De adaptieve vormcomponenten worden geadviseerd voor gebruik slechts in adaptieve vormpagina&#39;s. De componenten hebben gebiedsdeel op hun ouderhiërarchie. Gebruik ze dus niet op een AEM-pagina.

Ook, zie componentenbeschrijvingen en beste praktijken in [Inleiding aan creatie adaptieve vormen](/help/forms/using/introduction-forms-authoring.md).

### Regels in adaptieve vormen gebruiken {#using-rules-in-adaptive-forms}

De Vormen van AEM verstrekt een [regelredacteur](/help/forms/using/rule-editor.md) die u toestaat om regels tot stand te brengen om dynamisch gedrag aan adaptieve vormcomponenten toe te voegen. Gebruikend deze regels, kunt u voorwaarden evalueren en acties op componenten teweegbrengen, zoals tonen of verbergen gebieden, waarden berekenen, veranderingsdrop-down lijst dynamisch, etc.

De redacteur van de regel verstrekt een visuele redacteur en een coderedacteur voor het schrijven van regels. Overweeg het volgende wanneer het schrijven van regels die de wijze van de coderedacteur gebruiken:

* Gebruik betekenisvolle en unieke namen voor formuliervelden en -componenten om mogelijke conflicten te voorkomen terwijl u regels schrijft.
* De `this` exploitant van het gebruik voor een component om naar zich in een regeluitdrukking te verwijzen. Het zorgt ervoor dat de regel geldig blijft zelfs als de componentennaam verandert. Bijvoorbeeld, `field1.valueCommit script: this.value > 10`.

* De componentennamen van het gebruik wanneer het verwijzen naar andere vormcomponenten. Gebruik het `value` bezit om de waarde van een gebied of een component te halen. Bijvoorbeeld, `field1.value`.

* Verwijs componenten door relatieve unieke hiërarchie om het even welk conflict te vermijden. Bijvoorbeeld, `parentName.fieldName`.

* Wanneer het behandelen van complexe of algemeen gebruikte regels, denk na schrijvend bedrijfslogica als functies in een afzonderlijke cliëntbibliotheek die u kunt specificeren en over adaptieve vormen opnieuw gebruiken. De cliëntbibliotheek zou een met alle accomodatie bibliotheek moeten zijn en zou geen externe gebiedsdelen, behalve op jQuery en Underscore.js moeten hebben. U kunt de cliëntbibliotheek ook gebruiken om [server-zijbevestiging](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form) van voorgelegde vormgegevens af te dwingen.
* De adaptieve vormen verstrekken een reeks APIs die u kunt gebruiken om met te communiceren en acties op adaptieve vormen uit te voeren. Enkele zeer belangrijke APIs is als volgt. Voor meer informatie, zie de verwijzing van de Bibliotheek API van [JavaScript voor de AanpassingsVormen](https://adobe.com/go/learn_aemforms_documentation_63).

   * `guideBridge.reset()`: Geeft een formulier terug.
   * `guideBridge.submit()`: Verzendt een vorm.
   * `guideBridge.setFocus(somExp, focusOption, runCompletionExp)`: De nadruk van reeksen aan een gebied.
   * `guideBridge.validate(errorList, somExpression, focus)`: Bevestigt een vorm.
   * `guideBridge.getDataXML(options)`: Krijgt vormgegevens als XML.
   * `guideBridge.resolveNode(somExpression)`: Krijgt een vormvoorwerp.
   * `guideBridge.setProperty(somList, propertyName, valueList)`: Plaatst bezit van een vormvoorwerp.
   * Bovendien kunt u de volgende gebiedseigenschappen gebruiken:

      * `field.value` om waarde van een gebied te veranderen.
      * f `ield.enabled` om een gebied toe te laten/onbruikbaar te maken.
      * `field.visible` om zicht van een gebied te veranderen.

* De adaptieve vormauteurs kunnen code moeten schrijven JavaScript om bedrijfslogica in een vorm te bouwen. Terwijl JavaScript krachtig en efficiënt is, is het waarschijnlijk dat het op veiligheidsverwachtingen kon compromitteren. Daarom moet u ervoor zorgen dat de vormauteur een vertrouwde op persoon is en er processen zijn om de code te herzien en goed te keuren JavaScript alvorens een vorm in productie wordt gezet. De beheerder kan de toegang tot de toegang van de regelredacteur tot gebruikersgroepen beperken die op hun rol of functie wordt gebaseerd. Zie de toegang van de [de regelredacteur van de toelage tot uitgezochte gebruikersgroepen](/help/forms/using/rule-editor-access-user-groups.md).
* U kunt uitdrukkingen in regels gebruiken om adaptieve vormen dynamisch te maken. Alle uitdrukkingen zijn geldige uitdrukkingen JavaScript en gebruik adaptieve vormen scripting model APIs. Deze uitdrukkingen keren waarden van bepaalde types terug. Voor meer informatie over uitdrukkingen en beste praktijken rond hen, zie de [Aanpassings vormuitdrukkingen](/help/forms/using/adaptive-form-expressions.md).

### Werken met thema&#39;s {#working-with-themes}

Het aanpassings voor thema&#39;s staat u toe om opnieuw te gebruiken stijlen tot stand te brengen die over vormen voor verenigbare blik en het stileren kunnen worden toegepast. Het wordt geadviseerd om Thema&#39;s te gebruiken om het stileren voor vormcomponenten en panelen te bepalen. Enkele beste praktijken rond thema&#39;s zijn als volgt:

* De activabibliotheek van het gebruik voor snelle toepassing van tekststijlen, achtergrond en beelden. Wanneer een stijl in de activabibliotheek wordt toegevoegd, is het beschikbaar voor andere thema&#39;s en op de stijlwijze van de vormredacteur.
* Pas globale montages zoals doopvont en paginaachtergrond toe gebruikend pagina-vlakke selecteur.
* De cliëntbibliotheken van het gebruik om bestaande of geavanceerde het stileren in uw thema&#39;s in te voeren.
* U kunt het stileren voor specifieke gebieden, panelen, of knopen in een laag van de vormstijl met voeten treden.
* Als een thema niet aan uw het stileren vereiste voldoet, kunt u vooraf bepaalde klassen zoals guideFieldNode, guideFieldLabel, guideFieldWidget, en guidePanelNode gebruiken om gemeenschappelijke stijl over vormen toe te passen.

For more information, see [Themes](/help/forms/using/themes.md).

### Optimaliseren van de prestaties van grote en complexe vormen {#optimizing-performance-of-large-and-complex-forms}

De auteurs van de vorm en eind - de gebruikers zien typisch prestatieskwesties wanneer het laden van grote vormen op auteurswijze of bij runtime onder ogen. Aangezien het aantal voorwerpen (gebieden en panelen) in vorm stijgt, beginnen de creatie en runtime ervaring degraderend. Het verhindert ook veelvoudige auteurs om samen te werken en auteur gelijktijdig een vorm.

Overweeg de volgende beste praktijken om prestatieskwesties met grote vormen te overwinnen:

* Aanbevolen wordt om adaptieve formulieren te maken met behulp van het XSD-model voor formuliergegevens, zelfs wanneer een XFA wordt omgezet in een adaptieve vorm, indien mogelijk.
* Omvat slechts die gebieden en panelen in adaptieve vormen die informatie van de gebruiker vangen. Denk na houdend statische inhoud minimaal of gebruik URLs om hen in een afzonderlijk venster te openen.
* Terwijl elke vorm voor een specifiek doel wordt ontworpen, zijn er sommige gemeenschappelijke segmenten in de meeste vormen. Bijvoorbeeld, persoonlijke details, adres, werkgelegenheidsdetails, etc. Creeer [adaptieve vormfragmenten](/help/forms/using/adaptive-form-fragments.md) voor gemeenschappelijke vormelementen en secties en gebruik hen over vormen. U kunt een paneel in een bestaande vorm als fragment ook bewaren. Om het even welke verandering in een fragment wordt weerspiegeld in alle bijbehorende adaptieve vormen. Het bevordert collaboratieve creatie aangezien de veelvoudige auteurs aan verschillende fragmenten gelijktijdig kunnen werken die omhoog een vorm maken.

   * Gelijkaardig aan adaptieve vormen, adviseert men dat alle fragment-specifieke het stileren en douanemanuscripten in de cliëntbibliotheek gebruikend de dialoog van de fragmentcontainer worden bepaald. Ook, probeer creërend zelf-voldoende fragmenten die niet van voorwerpen buiten het afhangen.
   * Vermijd gebruikend dwars-fragmenten scripting. Als er om het even welk voorwerp buiten het fragment is waarnaar u moet verwijzen, probeer om dat voorwerp tot een deel van de oudervorm te maken. Als het voorwerp nog in een ander fragment moet verblijven, verwijs naar het door zijn naam in het manuscript.

* Gebruik Opslaan en hervatten met automatisch opslaan om het adaptieve formulier periodiek op te slaan en gebruikers in staat te stellen later opnieuw te verschijnen om het formulier te voltooien.
* Vorm fragmenten om te laden lazily. Bij runtime, wordt het fragment duidelijk om laaiend te laden teruggegeven slechts wanneer zij worden vereist. Het vermindert beduidend de ladingstijd voor grote vormen. Het wordt ook gesteund in fragmenten met herhaalbare panelen. Voor meer informatie, zie [vormen luie lading](/help/forms/using/lazy-loading-adaptive-forms.md).

   * Vorm geen luie lading op fragmenten in een ontvankelijke netlay-out of in het eerste paneel.
   * De gehechtheid van het dossier en de Termen en de toestandscomponenten worden niet gesteund in lazily geladen fragmenten.
   * Merk een waarde in een lui geladen paneel als Waarde van het Gebruik globaal als die waarde in één of ander ander deel wordt gebruikt de vorm zodat de waarde voor gebruik beschikbaar is wanneer het bevattende paneel wordt leeggemaakt.
   * Overweeg het schrijven van zichtregels voor fragmenten die zouden moeten tonen of verbergen gebaseerd op een voorwaarde.

### Aanpasbare formulieren voor prefilling {#prefilling-adaptive-forms}

U kunt adaptieve vormgebieden met gegevens prefileren die van achterzijde worden gehaald om gebruikers te helpen snel de vorm vullen en typend fouten vermijden.

* De Vormen van AEM verstrekt de prefill dienst om gegevens van een vooraf bepaald dossier van gegevensXML te lezen en de gebieden van een adaptieve vorm met de inhoud in het Prefill dossier van XML te prefill.
* Prefill gegevens XML moet volgzaam met het schema van het vormmodel zijn verbonden aan de adaptieve vorm.
* Omvat `afBoundedData` en de `afUnBoundedData` secties in de prefill XML om zowel verbindende als ongebonden gebieden in een adaptieve vorm te prefill.

* Voor adaptieve vormen die op het model van vormgegevens worden gebaseerd, verstrekt de Vormen AEM de uit-van-de-dooswijze Dienst van de Gegevens van de Vorm ModelPrefill. De prefill dienst vraagt gegevensbronnen voor gegevensmodelvoorwerpen in de adaptieve vorm en geeft gebiedswaarden vooraf in wanneer het teruggeven van de vorm.
* U kunt het dossier, crx, de dienst, of de HTTP- protocollen ook gebruiken prefill aanpassingsvormen.
* De Vormen van AEM steunt de diensten van de douaneprefill die u als dienst OSGi kunt aansluiten om adaptieve vormen te prefill.

Voor meer informatie, zie de aanpassingsgebieden [van de](/help/forms/using/prepopulate-adaptive-form-fields.md)Prefill van de vormvorm.

### Ondertekening en indiening van adaptieve formulieren {#signing-and-submitting-adaptive-forms}

De aanpassingsvormen vereisen voorleggen acties om user-specified gegevens te verwerken. Een Submit actie bepaalt de taak die op de gegevens wordt uitgevoerd die u gebruikend een adaptieve vorm voorlegt.

* Er zijn verscheidene voorgelegde acties beschikbaar uit-van-de-doos in adaptieve vormen. Voor details, zie het [Vormen van de Submit actie](/help/forms/using/configuring-submit-actions.md).
* U kunt een douane schrijven voorlegt actie voor als het gebrek acties voorlegt niet uw gebruiksgeval vervult. Voor meer informatie, zie het [Schrijven van douane actie voor adaptieve vormen](/help/forms/using/custom-submit-action-form.md)voorleggen.
* Omvat server-zijbevestigingen om voorlegging van ongeldige gegevensvoorlegging te verhinderen.

U kunt hefboomwerkings multi-sign ervaring van het Teken van Adobe in adaptieve vormen. Overweeg het volgende wanneer het vormen van het Teken van Adobe in adaptieve vormen. Voor details, zie het [Gebruiken van het Teken van Adobe in een adaptieve vorm](/help/forms/using/working-with-adobe-sign.md).

* Het teken van Adobe liet toe aanpassingsvorm wordt voorgelegd slechts nadat alle signaalgevers de vorm hebben ondertekend. De vormen verschijnen in de Hangende staat van het Teken tot de vorm door alle ondertekenaars wordt ondertekend.
* U kunt in-vorm het ondertekenen ervaring vormen of ondertekenaars aan een het ondertekenen pagina op voorlegging opnieuw richten.
* Vorm opeenvolgende of parallelle het ondertekenen ervaring, zoals aangewezen.

### Opstellen van een document met gegevens {#generating-document-of-record}

Een document van verslag (DoR) is een afgevlakte versie PDF van een adaptieve vorm die u kunt drukken, ondertekenen, of archiveren.

* Afhankelijk van het model van vormgegevens is een adaptieve vorm gebaseerd op, kunt u een malplaatje voor Dor als volgt vormen:

   * **Formuliermodel** XFA: Gebruik het bijbehorende XDP- dossier als malplaatje DoR.
   * **XSD-schema**: Gebruik het bijbehorende malplaatje XFA dat het zelfde schema van XML gebruikt zoals die door de adaptieve vorm wordt gebruikt.
   * **Geen**: Gebruik automatisch gegenereerde DoR.

* Vorm kopbal, footer, beelden, kleur, doopvont, etc. rechts van het Document van het lusje van het Verslag van de adaptieve vormredacteur.
* Gebruik `DoRService` om DoR programmatically te produceren.
* Verborgen velden uitsluiten van het DoR.
* De het `afAcceptLang` verzoekparameter van het gebruik aan meningDoR in een andere scène.

### Het zuiveren en het testen van adaptieve vormen {#debugging-and-testing-adaptive-forms}

[AEM Chrome Plug-in](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/) is een browser extensie voor Google Chrome die tools biedt voor het zuiveren van adaptieve formulieren. De auteurs en de ontwikkelaars van de vorm kunnen deze hulpmiddelen gebruiken om:

* Identificeer knelpunten en optimaliseer prestaties van vormgeven
* Zuiver sleutelwoorden en bindRef fouten in de vorm
* Logbestanden inschakelen en configureren
* Zuiver regels en manuscripten in de vorm
* Ontdek en leer over guideBridge APIs

Voor meer informatie, zie de Plug-in van het Chroom van [AEM - AanpassingsVorm](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/adaptive-form/).

Calvin SDK is een nut API voor de Aanpassings ontwikkelaars van Vormen om AanpassingsVormen te testen. Calvin SDK wordt gebouwd bovenop het testende kader [](https://docs.adobe.com/docs/en/aem/6-3/develop/ref/test-api/index.html)Hobbes.js. U kunt het kader gebruiken om het volgende te testen:

* Renditie-ervaring van een adaptief formulier
* Prefill-ervaring van een adaptief formulier
* Ervaring met een adaptief formulier indienen
* Uitdrukkingsregels
* Valideringen
* Lazy Loading

Voor meer informatie, zie het testen van [Automatiseer het testen van adaptieve vormen](/help/forms/using/calvin.md).

### Adaptieve formulieren valideren op AEM-server {#validating-adaptive-forms-on-aem-server}

De server-zijbevestigingen worden vereist om het even welke pogingen te verhinderen om bevestigingen op de cliënt en om het even welk mogelijk compromis van gegevensvoorlegging en bedrijfsregelingsschendingen te mijden. De server-zijbevestigingen worden uitgevoerd op server door de vereiste cliëntbibliotheek te laden.

* Omvat functies in een cliëntbibliotheek voor het bevestigen van uitdrukkingen in adaptieve vormen en specificeer de cliëntbibliotheek in de adaptieve dialoog van de vormencontainer. Voor meer informatie, zie [server-zijbevestiging](/help/forms/using/configuring-submit-actions.md#p-server-side-revalidation-in-adaptive-form-p).
* De server-zijbevestiging bevestigt het vormmodel. Men adviseert om een afzonderlijke cliëntbibliotheek voor bevestigingen tot stand te brengen en niet het te mengen met andere dingen zoals het stileren van HTML en DOM manipulatie in de zelfde cliëntbibliotheek.

### Aanpasbare formulieren lokaliseren {#localizing-adaptive-forms}

AEM biedt vertaalworkflows die u kunt gebruiken om adaptieve formulieren te lokaliseren. Voor informatie, zie het [Gebruiken van AEM vertaalwerkschema om adaptieve vormen](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md)te lokaliseren.

Sommige beste praktijken wanneer het lokaliseren van adaptieve vormen zijn als volgt:

* Gebruik adaptieve vormfragmenten voor gemeenschappelijke elementen over vormen en lokaliseer fragmenten. Het zorgt ervoor dat u een fragment eens lokaliseert en het wijst op in alle vormen waar het gelokaliseerde fragment wordt gebruikt.
* Om het even welke wijzigingen zoals het toevoegen van een nieuwe component of het toepassen van een manuscript in een gelokaliseerde vorm worden niet automatisch gelokaliseerd. Daarom moet u een vorm voltooien alvorens het te lokaliseren om veelvoudige localisatiecycli te vermijden.
* De het `afAcceptLang` verzoekparameter van het gebruik om de browser scène met voeten te treden en de vorm in de gespecificeerde scène terug te geven. Bijvoorbeeld, zal volgende URL dwingen om de vorm in Japanse scène, ongeacht de scène terug te geven die in browser wordt gespecificeerd die plaatst:

   `https://[server]:[port]/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

* AEM Forms ondersteunt momenteel de lokalisatie van adaptieve formulieren in het Engels (en), Spaans (ES), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW), en Koreaanse (ko-KR) scènes. Nochtans, kunt u steun voor nieuwe scènes voor adaptieve vormen toevoegen bij runtime. Voor meer informatie, zie het [Ondersteunende nieuwe scènes voor adaptieve vormenlocalisatie](/help/forms/using/supporting-new-language-localization.md).

## Formulierproject voorbereiden voor productie {#prepare-forms-project-for-production}

### Het toevoegen van de server van de vormenverwerking {#adding-forms-processing-server}

U kunt een extra geval van AEM vormen server die achter de firewall in een beveiligde streek verblijft. U kunt deze instantie gebruiken voor:

* **Batchverwerking**: taken die terugkerend of gepland in partijen met zware lading zijn. Bijvoorbeeld, druk verklaringen, producerend correspondentie, en gebruikend de documentdiensten zoals Generator PDF, Output, en Assembler.
* **Opslaan van PII-gegevens**: Sparen PII- gegevens over de verwerkingsserver. Het is niet vereist als u reeds de leverancier van de douaneopslag voor het opslaan van PII- gegevens gebruikt.

### Projecten verplaatsen naar een andere omgeving {#moving-project-to-another-environment}

U moet vaak uw projecten van AEM van één milieu naar een andere verplaatsen. Enkele belangrijke dingen om te herinneren wanneer zich het bewegen zijn als volgt:

* Neem steun van uw bestaande cliëntbibliotheken, douanecode, en configuraties.
* Implementeer productpakketten en patches handmatig en in de opgegeven volgorde in de nieuwe omgeving.
* Implementeer projectspecifieke codepakketten en -bundels handmatig en als een afzonderlijk pakket of bundel op de nieuwe AEM-server.
* (*Vormen AEM op slechts* JEE) stellen LCAs en DSCs manueel op de server van het Werkschema van Vormen op.
* De [uitvoer-Invoer](/help/forms/using/import-export-forms-templates.md) van het gebruik functionaliteit om activa naar het nieuwe milieu te verplaatsen. U kunt de replicatieagent ook vormen en de activa publiceren.

### AEM configureren {#configuring-aem}

Sommige beste praktijken om AEM te vormen om de algemene prestaties te verbeteren zijn als volgt:

* Laat de compressie van de de cliëntbibliotheek van HTML voor JavaScript en CSS van de Console van Felix toe. Zie [Clientlibs die door voorbeeld](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)worden verklaard.
* Het geheime voorgeheugen alle cliëntbibliotheken bij `/etc.clientlibs/fd` en om het even welke extra bibliotheken van de douanecliënt op AEM verzender om de ontvankelijkheid en de veiligheid van uw gepubliceerde vormen te verhogen. For more information, see [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html).

* Geen cache `/content/forms/af/` en `/content/dam/formsanddocuments/*` paden. voor gedetailleerde informatie over het vormen van adaptieve vormen caching, zie het [Caching van adaptieve vormen](/help/forms/using/configure-adaptive-forms-cache.md).

* Laat HTML via de compressiemodule van de Webserver toe. Voor meer informatie, zie het stemmen van [Prestaties van de server](/help/forms/using/performance-tuning-aem-forms.md)van Vormen AEM.
* De vraag van de verhoging per verzoekconfiguratie voor grote vormen. Zie [Optimaliserende prestaties van grote en complexe vormen](/help/forms/using/adaptive-forms-best-practices.md#optimizing-performance-of-large-and-complex-forms).
* Creeer de pagina&#39;s van de [douanefout die door foutenmanager](https://helpx.adobe.com/experience-manager/6-2/sites-developing/customizing-errorhandler-pages.html)worden getoond.
* Beveilig de server van Vormen AEM.

   * De `nosamplecontent` looppaswijze van het gebruik om ervoor te zorgen zijn er geen steekproefinhoud en steekproefgebruikers die op de productieserver worden opgesteld. Zie AEM [in de Klaar Wijze](/help/sites-administering/production-ready.md)van de Productie lopen.

* Houd de hoopgrootte aan een minimum van 8 GB. Voor andere montages, zie het stemmen van [Prestaties van de server](/help/forms/using/performance-tuning-aem-forms.md)van Vormen AEM.
* De zittingen van de de dienstgebruiker van het gebruik in plaats van adminzittingen voor het uitvoeren van dienst-vlakke taken. Voor meer informatie, zie de authentificatie [van de](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html)Dienst.

>[!VIDEO](https://vimeo.com/)

### Externe opslag configureren voor concepten en ingediende formuliergegevens {#external-storage}

In een productieomgeving wordt aanbevolen geen ingediende formuliergegevens op te slaan in een AEM-opslagplaats. De standaardimplementatie van de Poortopslag van Vormen, de Inhoud van de Opslag, en de Opslag PDF leggen de gegevens van de actiesopslag in bewaarplaats AEM voor. Deze acties zijn alleen bedoeld voor demonstratiedoeleinden. Ook, gebruiken sparen en hervat en de Auto sparen eigenschappen poortopslag door gebrek. Daarom moeten de volgende aanbevelingen in overweging worden genomen:

* **Ontwerpgegevens** opslaan: Als u de eigenschap van het Ontwerp van adaptieve vormen gebruikt, zou u de douaneDienst moeten uitvoeren verstrekt Interface (SPI) om ontwerpgegevens in veiliger opslag zoals gegevensbestand op te slaan. Voor meer informatie, zie [Steekproef voor het integreren van ontwerp &amp; inleggingscomponent met gegevensbestand](/help/forms/using/integrate-draft-submission-database.md).

* **Opslaan van indieningsgegevens**: Als u het Portaal van de Vorm gebruikt leg Opslag voor, zou u douaneSPI moeten uitvoeren om voorleggingsgegevens in een gegevensbestand op te slaan. Zie [Steekproef voor het integreren van ontwerp &amp; voorleggingscomponent met gegevensbestand](/help/forms/using/integrate-draft-submission-database.md) voor een steekproefintegratie.

   U kunt een douane ook schrijven voorlegt actie die vormgegevens en gehechtheid in veilige opslag opslaat. Zie Aangepaste [schrijfactie verzenden voor adaptieve formulieren](/help/forms/using/custom-submit-action-form.md) voor meer informatie.

### Behandeling van persoonlijk identificeerbare informatie {#handling-personally-identifiable-information}

Één van de belangrijkste uitdagingen voor organisaties is hoe te om persoonlijk identificeerbare (PII) gegevens te behandelen. Sommige beste praktijken die u zullen helpen dergelijke gegevens behandelen zijn als volgt:

* Gebruik een veilige, externe opslag zoals gegevensbestand om gegevens van ontwerp en voorgelegde vormen op te slaan. Zie Externe opslag [configureren voor concepten en ingediende formuliergegevens](/help/forms/using/adaptive-forms-best-practices.md#external-storage).
* De de vormcomponent van de Bepalingen en van de Voorwaarden van het gebruik om expliciete toestemming van gebruiker te nemen alvorens auto sparen toe te laten. In dit geval, laat auto sparen toe slechts wanneer de gebruiker met de voorwaarden in de component van Bepalingen en van de Voorwaarden instemt.

