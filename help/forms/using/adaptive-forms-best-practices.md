---
title: Aanbevolen werkwijzen voor het werken met adaptieve formulieren
description: Hierin worden de beste praktijken beschreven voor het opzetten van een AEM Forms-project, het ontwikkelen van adaptieve formulieren en het optimaliseren van de prestaties voor het AEM Forms-systeem.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms,Foundation Components,Core Components
exl-id: 5c75ce70-983e-4431-a13f-2c4c219e8dde
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 5699f5814daf16a397eb6129b881ac2035456e39
workflow-type: tm+mt
source-wordcount: '5888'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor het werken met adaptieve formulieren {#best-practices-for-working-with-adaptive-forms}

<span class="preview"> Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [&#x200B; de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)  voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md)  of [&#x200B; toevoegend Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Overzicht {#overview}

Met Adobe Experience Manager (AEM)-formulieren kunt u complexe transacties transformeren in eenvoudige, prachtige digitale ervaringen. Het vereist echter gezamenlijke inspanningen om een efficiënt en productief AEM Forms-ecosysteem te implementeren, op te bouwen, uit te voeren en in stand te houden.

Dit document bevat richtlijnen en aanbevelingen die beheerders, auteurs en ontwikkelaars van formulieren kunnen gebruiken wanneer ze met AEM Forms werken, en met name wanneer ze onderdelen voor adaptieve formulieren gebruiken. Hierin worden de beste werkwijzen besproken, van het instellen van een formulierontwikkelingsproject tot het configureren, aanpassen, ontwerpen en optimaliseren van AEM Forms. Deze beste praktijken dragen collectief bij tot de algemene prestaties van het ecosysteem van AEM Forms.

Daarnaast zijn er enkele aanbevolen instructies voor algemene AEM-best practices:

* [Tips en trucs: AEM implementeren en onderhouden](/help/sites-deploying/best-practices.md)
* [Tips en trucs: inhoud ontwerpen](/help/sites-authoring/best-practices.md)
* [Tips en trucs: AEM beheren](/help/sites-administering/administer-best-practices.md)
* [Tips en trucs: oplossingen ontwikkelen](/help/sites-developing/best-practices.md)

## AEM Forms instellen en configureren {#set-up-and-configure-aem-forms}

### Project voor de ontwikkeling van formulieren opzetten {#setting-up-forms-development-project}

Een vereenvoudigde en gestandaardiseerde projectstructuur kan de ontwikkelings- en onderhoudsinspanningen aanzienlijk verminderen. Apache Maven is een opensource tool die wordt aanbevolen voor het bouwen van AEM-projecten.

* Met Apache Maven `aem-project-archetype` kunt u structuur voor AEM-projecten maken en beheren. Er worden aanbevolen structuren en sjablonen voor uw AEM-project gemaakt. Ook, verstrekt het bouwstijlautomatisering en veranderingscontrolesystemen om het project te helpen beheren.

   * Met de opdracht maven `archetype:generate` kunt u de initiële structuur genereren.
   * Met de opdracht Geweven `eclipse:eclipse` kunt u de ovaalprojectbestanden genereren en het project in een ovaal importeren.

Voor meer informatie, zie [&#x200B; hoe te de Projecten van AEM bouwen gebruikend Apache Maven &#x200B;](/help/sites-developing/ht-projects-maven.md).

* Met het gereedschap FileVault of VLT kunt u de inhoud van een CRX- of AEM-instantie toewijzen aan uw bestandssysteem. Het verstrekt de verrichtingen van het veranderingsbeheer, zoals controle-binnen en controle-out van de het projectinhoud van AEM. Zie [&#x200B; hoe te om het Hulpmiddel VLT &#x200B;](/help/sites-developing/ht-vlttool.md) te gebruiken.

* Als u Eclipse-geïntegreerde ontwikkelomgeving gebruikt, kunt u AEM Developer-gereedschappen gebruiken voor de naadloze integratie van Eclipse IDE met AEM-instanties om AEM-toepassingen te maken. Voor details, zie [&#x200B; de ontwikkelaarshulpmiddelen van AEM voor Verduistering &#x200B;](/help/sites-developing/aem-eclipse.md).

* Sla geen inhoud op en breng geen wijzigingen aan in de map /libs. Maak overlays in /app-mappen om standaardfuncties uit te breiden of te overschrijven.

* Wanneer u pakketten maakt om inhoud te verplaatsen, moet u ervoor zorgen dat paden met pakketfilters correct zijn en dat alleen vereiste paden worden vermeld.

* Sla geen inhoud op en breng geen wijzigingen aan in de map /libs. Maak overlays in /app-mappen om standaardfuncties uit te breiden of te overschrijven.

* Bepaal correcte gebiedsdelen voor de pakketten om een vooraf bepaalde installatieorde/opeenvolging te dwingen.

* Maak geen knooppunten waarnaar kan worden verwezen in /libs of /apps.

### Planning voor ontwerpomgeving {#planning-for-authoring-environment}

Als u uw AEM-project hebt ingesteld, definieert u een strategie voor het ontwerpen en aanpassen van adaptieve formuliersjablonen en componenten.

* Een adaptieve formuliersjabloon is een speciale AEM-pagina die de structuur en de informatie over de kop- en voettekst van een adaptief formulier definieert. Een sjabloon heeft vooraf geconfigureerde indelingen, stijlen en basisstructuur voor een adaptief formulier. AEM Forms beschikt over out-of-the-box sjablonen en componenten waarmee u adaptieve formulieren kunt maken. U kunt echter naar wens aangepaste sjablonen en componenten maken. Het wordt aanbevolen vereisten te verzamelen voor aanvullende sjablonen en componenten die u nodig hebt in uw aangepaste formulieren. Voor details, zie [&#x200B; Aanpasbare vormen en componenten aanpassen &#x200B;](/help/forms/using/adaptive-forms-best-practices.md#customize-components).
* Het wordt aanbevolen de formulierpakketten te uploaden via de gebruikersinterface van Form Manager in plaats van via de gebruikersinterface van CRX Package Manager, omdat het uploaden van pakketten via CRX Package Manager soms tot anomalieën kan leiden.
* Met AEM Forms kunt u adaptieve formulieren maken op basis van de volgende formuliermodellen. De formuliermodellen fungeren als interface voor gegevensuitwisseling tussen een formulier en een AEM-systeem en bieden een op XML gebaseerde structuur voor gegevensstroom binnen en buiten een adaptief formulier. Bovendien leggen de formuliermodellen regels en beperkingen op aan adaptieve formulieren in de vorm van schema- en XFA-beperkingen.

   * **niets**: De adaptieve vormen die met deze optie worden gecreeerd gebruiken geen vormmodel. De XML-gegevens die op basis van dergelijke formulieren worden gegenereerd, hebben een vlakke structuur met velden en bijbehorende waarden.
   * **XML of het schema JSON**: De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin het gegeven wordt geproduceerd of door het achterste deelsysteem in uw organisatie verbruikt. U kunt een schema aan een adaptief formulier koppelen en de elementen ervan gebruiken om dynamische inhoud aan het aangepaste formulier toe te voegen. De elementen van het schema zijn beschikbaar op het tabblad Gegevensmodel van de inhoudbrowser voor het ontwerpen van adaptieve formulieren. U kunt de schema-elementen slepen en neerzetten om het formulier samen te stellen.
   * **XFA vormmalplaatje**: Het is een ideaal vormmodel als u investeringen in op XFA-Gebaseerde HTML5 vormen hebt. Dit biedt een directe manier om uw XFA-formulieren om te zetten in adaptieve formulieren. Bestaande XFA-regels blijven behouden in de bijbehorende adaptieve formulieren. De resulterende adaptieve formulieren ondersteunen XFA-constructies, zoals validaties, gebeurtenissen, eigenschappen en patronen.
   * **Model van de Gegevens van de Vorm**: Het is een aangewezen vormmodel als u uw backendsystemen zoals gegevensbestanden, Webdiensten, en gebruikersprofiel van AEM probeert te integreren om aanpassende vormen vooraf in te vullen en voorgelegde vormgegevens terug naar de achterste deelsystemen te schrijven. Met een formuliergegevensmodeleditor kunt u entiteiten en services definiëren en configureren in een formuliergegevensmodel waarmee u adaptieve formulieren kunt maken. Voor meer informatie, zie [&#x200B; de Integratie van Gegevens van AEM Forms &#x200B;](/help/forms/using/data-integration.md).

Het is belangrijk om zorgvuldig het gegevensmodel te kiezen dat niet alleen aan uw vereisten voldoet maar uw bestaande investeringen in XFA en XSD activa uitbreidt, als om het even welk. Gebruik het XSD-model om formuliersjablonen te maken, omdat de gegenereerde XML gegevens bevat volgens de XPATH die door het schema wordt gedefinieerd. Het gebruik van XSD-model als standaardkeuze voor het formuliergegevensmodel helpt ook omdat het formulierontwerp loskoppelt van een back-end systeem dat gegevens verwerkt en verbruikt, en het verbetert de prestaties van het formulier door een-op-een-toewijzing van formuliervelden. BindRef van het veld kan ook de XPATH van de gegevenswaarde in XML worden gemaakt.

Voor meer informatie, zie [&#x200B; een adaptieve vorm &#x200B;](/help/forms/using/creating-adaptive-form.md) creëren.

* Er zijn enkele algemene secties in adaptieve formulieren. U kunt ze identificeren en een strategie definiëren om hergebruik van inhoud te bevorderen. Met adaptieve formulieren kunt u zelfstandige fragmenten maken en deze hergebruiken in verschillende formulieren. U kunt een deelvenster ook in een adaptief formulier opslaan als een fragment. Wijzigingen in een fragment worden in alle bijbehorende formulieren doorgevoerd. Hierdoor kunt u de ontwerptijd verkorten en consistentie in verschillende formulieren garanderen. Bovendien maakt het gebruik van fragmenten adaptieve formulieren lichtgewicht, wat resulteert in een verbeterde ontwerpervaring, met name in grote vormen. Voor meer informatie, zie [&#x200B; Aangepaste vormfragmenten &#x200B;](/help/forms/using/adaptive-form-fragments.md).

### Aangepaste formulieren en componenten aanpassen {#customize-components}

* AEM Forms biedt adaptieve formuliersjablonen die u kunt gebruiken om adaptieve formulieren te maken. U kunt ook uw eigen sjablonen maken. AEM biedt statische en bewerkbare sjablonen.

   * Statische sjablonen worden gedefinieerd en geconfigureerd door ontwikkelaars.
   * Bewerkbare sjablonen worden gemaakt door auteurs die de sjablooneditor gebruiken. Met de sjablooneditor kunt u een basisstructuur en initiële inhoud in een sjabloon definiëren. Alle wijzigingen in de structuurlaag worden weerspiegeld in alle formulieren die gebruikmaken van die sjabloon. De eerste inhoud kan een vooraf geconfigureerd thema, een vooraf ingevulde service, een verzendactie enzovoort bevatten. Deze instellingen kunnen echter wel worden gewijzigd voor een formulier in de formuliereditor. Voor meer informatie, zie [&#x200B; Aangepaste vormmalplaatjes &#x200B;](/help/forms/using/template-editor.md).

* Voor het stileren van een specifiek gebied of paneelinstantie, gebruik [&#x200B; gealigneerd het stileren &#x200B;](/help/forms/using/inline-style-adaptive-forms.md). U kunt ook een klasse definiëren in een CSS-bestand en de klassenaam opgeven in de CSS-klasseneigenschap van de component.
* Neem een clientbibliotheek in een component op om stijlen consistent toe te passen op adaptieve formulieren of fragmenten die die component gebruiken. Voor meer informatie, zie [&#x200B; een adaptieve component van de vormpagina &#x200B;](/help/forms/using/custom-adaptive-forms-templates.md) creëren.
* Pas stijlen toe die zijn gedefinieerd in een clientbibliotheek om adaptieve formulieren te selecteren door het pad naar de clientbibliotheek op te geven in het veld CSS-bestandspad in de adaptieve eigenschappen van de formuliercontainer.
* Als u een clientbibliotheek met uw stijlen wilt maken, kunt u het aangepaste CSS-bestand configureren in de basisclient van de Thema-editor of in de eigenschappen van de Form Container.
* Aangepaste formulieren bieden deelvensterlay-outs, zoals responsieve formulieren, tabbladen, accordeons en wizard, om te bepalen hoe formuliercomponenten worden ingedeeld in een deelvenster. U kunt aangepaste deelvensterlay-outs maken en beschikbaar maken voor gebruik door formulierauteurs. Voor meer informatie, zie [&#x200B; Creërend de componenten van de douanelay-out voor adaptieve vormen &#x200B;](/help/forms/using/custom-layout-components-forms.md).
* U kunt ook specifieke aangepaste formuliercomponenten aanpassen, zoals velden en de indeling van deelvensters.

   * Gebruik de [&#x200B; functionaliteit van de Bedekking &#x200B;](/help/sites-developing/overlays.md) van AEM om een exemplaar van een component te wijzigen. Het wordt afgeraden standaardcomponenten te wijzigen.
   * Om de lay-out van uit-van-de-doos adaptieve vormcomponenten in /libs aan te passen, [&#x200B; creeer de componenten van de douanelay-out &#x200B;](/help/forms/using/custom-layout-components-forms.md) naast [&#x200B; standaardlay-outs &#x200B;](/help/forms/using/layout-capabilities-adaptive-forms.md).
   * Introduceer aangepaste interactiviteiten door aangepaste widgets of weergaven te maken. Het wordt afgeraden standaardcomponenten te wijzigen. Voor meer informatie, zie [&#x200B; kader van de Vormgeving &#x200B;](/help/forms/using/introduction-widgets.md).

* Zie [&#x200B; Behandelend persoonlijk identificeerbare informatie &#x200B;](/help/forms/using/adaptive-forms-best-practices.md#p-handling-personally-identifiable-information-p) voor aanbevelingen bij de behandeling van PII- gegevens.

### Formuliersjablonen maken

U kunt een adaptieve vorm tot stand brengen gebruikend de vormmalplaatjes die in **Browser van de Configuratie** worden toegelaten. Om de vormmalplaatjes toe te laten, zie [&#x200B; Creërend Aangepast Malplaatje van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/creating-your-first-adaptive-form/create-adaptive-form-template.html?lang=en).

De formuliersjablonen kunnen ook worden geüpload vanuit Adaptief formulierpakketten die zijn gemaakt op een andere auteur. De malplaatjes van de vorm worden ter beschikking gesteld door [&#x200B; aemforms-verwijzingen te installeren -* pakketten &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en). Enkele aanbevolen best practices zijn:

* **nosamplcontent** runmode wordt geadviseerd slechts voor auteur en niet voor publicatieknooppunten.
* Elementen zoals adaptieve formulieren, thema&#39;s, sjablonen of cloudconfiguraties worden alleen via auteurknooppunten gemaakt. Deze kunnen worden gepubliceerd op de geconfigureerde publicatieknooppunten.
Voor meer informatie, zie [&#x200B; het Publiceren en het unpublishing vormen en documenten &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/publishing-unpublishing-forms.html?lang=en)
* Forms addon package is vereist voor Authoring en voor Publishing ter ondersteuning van de bewerkingen van de documentservice; daarom kan het worden beschouwd als een afhankelijkheid.
Als u slechts op Forms betrekking hebbende steekproefmalplaatje, thema&#39;s, en pakketten DOR wilt, dan kunt u hen van [&#x200B; aemforms-references-* pakketten &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/publish-process-aem-forms/publishing-unpublishing-forms.html?lang=en) downloaden.

Voor verdere informatie, zie de beste praktijken in [&#x200B; Inleiding aan auteursadaptieve vormen &#x200B;](/help/forms/using/introduction-forms-authoring.md).

## Aangepaste formulieren van auteurs {#author-adaptive-forms}

### Gebruikend touch-geoptimaliseerde UI voor creatie {#using-touch-optimized-ui-for-authoring}

* Gebruik de browser Objecten in het zijpaneel om snel velden te openen die diep onder in de formulierhiërarchie liggen. Met het zoekvak kunt u zoeken naar objecten in het formulier of in de objectstructuur en van het ene object naar het andere navigeren.
* Om de eigenschappen van een component in componenten te bekijken en uit te geven browser in sidebar, selecteer de component en klik ![&#x200B; cmp-1 &#x200B;](assets/cmppr-1.png). U kunt ook dubbelklikken op een component om de eigenschappen ervan weer te geven in de eigenschappenbrowser.
* Gebruik sneltoetsen om snel actie te ondernemen op uw formulieren. Zie [&#x200B; Sneltoetsen van AEM Forms &#x200B;](/help/forms/using/keyboard-shortcuts.md).

* Aangepaste formuliercomponenten worden alleen aanbevolen voor gebruik op adaptieve formulierpagina&#39;s. De componenten zijn afhankelijk van hun bovenliggende hiërarchie. Gebruik deze daarom niet op een AEM-pagina.

Ook, zie componentenbeschrijvingen en beste praktijken in [&#x200B; Inleiding aan auteursadaptieve vormen &#x200B;](/help/forms/using/introduction-forms-authoring.md).

### Regels in adaptieve formulieren gebruiken {#using-rules-in-adaptive-forms}

AEM Forms verstrekt a [&#x200B; regelredacteur &#x200B;](/help/forms/using/rule-editor.md) die u regels laat tot stand brengen om dynamisch gedrag aan adaptieve vormcomponenten toe te voegen. Met deze regels kunt u voorwaarden evalueren en acties activeren op componenten, zoals velden weergeven of verbergen, waarden berekenen, vervolgkeuzelijst dynamisch wijzigen, enzovoort.

De redacteur van de regel verstrekt een visuele redacteur en een coderedacteur voor het schrijven van regels. Overweeg het volgende wanneer het schrijven van regels gebruikend de wijze van de coderedacteur:

* Gebruik betekenisvolle en unieke namen voor formuliervelden en componenten om mogelijke conflicten te voorkomen tijdens het schrijven van regels.
* Gebruik de operator `this` voor een component om naar zichzelf te verwijzen in een regelexpressie. Het zorgt ervoor dat de regel geldig blijft zelfs als de componentennaam verandert. Bijvoorbeeld `field1.valueCommit script: this.value > 10` .

* Gebruik componentnamen wanneer u naar andere formuliercomponenten verwijst. Gebruik de eigenschap `value` om de waarde van een veld of component op te halen. Bijvoorbeeld `field1.value` .

* Verwijs componenten door relatieve unieke hiërarchie om het even welk conflict te vermijden. Bijvoorbeeld `parentName.fieldName` .

* Wanneer u complexe of veelgebruikte regels afhandelt, kunt u bedrijfslogica als functies in een aparte clientbibliotheek schrijven die u kunt opgeven en hergebruiken voor adaptieve formulieren. De clientbibliotheek moet een zelfstandige bibliotheek zijn en mag geen externe afhankelijkheden hebben, behalve op jQuery en Underscore.js. U kunt de cliëntbibliotheek ook gebruiken om [&#x200B; server-zijbevestiging &#x200B;](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form) van voorgelegde vormgegevens af te dwingen.
* Adaptieve formulieren bieden een set API&#39;s waarmee u kunt communiceren en waarmee u handelingen kunt uitvoeren op adaptieve formulieren. Enkele belangrijke API&#39;s zijn als volgt. Voor meer informatie, zie [&#x200B; de API van de Bibliotheek van JavaScript verwijzing voor Aanpassings Forms &#x200B;](https://adobe.com/go/learn_aemforms_documentation_63).

   * `guideBridge.reset()`: hiermee wordt een formulier opnieuw ingesteld.
   * `guideBridge.submit()`: verzendt een formulier.
   * `guideBridge.setFocus(somExp, focusOption, runCompletionExp)`: hiermee wordt de focus op een veld ingesteld.
   * `guideBridge.validate(errorList, somExpression, focus)` - Valideert een formulier.
   * `guideBridge.getDataXML(options)`: hiermee worden formuliergegevens opgehaald als XML.
   * `guideBridge.resolveNode(somExpression)` : hiermee wordt een formulierobject opgehaald.
   * `guideBridge.setProperty(somList, propertyName, valueList)`: stelt de eigenschap van een formulierobject in.
   * Daarnaast kunt u de volgende veldeigenschappen gebruiken:

      * `field.value` om de waarde van een veld te wijzigen.
      * `field.enabled` om een veld in of uit te schakelen.
      * `field.visible` om de zichtbaarheid van een veld te wijzigen.

* Auteurs van adaptieve formulieren moeten mogelijk JavaScript-code schrijven om bedrijfslogica in een formulier te maken. Hoewel JavaScript krachtig en effectief is, is het waarschijnlijk dat het de veiligheidsverwachtingen in gevaar kan brengen. Daarom moet u ervoor zorgen dat de auteur van het formulier een vertrouwd persoon is en dat er processen zijn om de JavaScript-code te controleren en goed te keuren voordat een formulier in productie wordt genomen. De beheerder kan de toegang tot de toegang van de regelredacteur tot gebruikersgroepen beperken die op hun rol of functie wordt gebaseerd. Zie {de toegang van de de regelredacteur van 0} Verlenen tot uitgezochte gebruikersgroepen [.](/help/forms/using/rule-editor-access-user-groups.md)
* U kunt expressies in regels gebruiken om adaptieve formulieren dynamisch te maken. Alle expressies zijn geldige JavaScript-expressies en gebruiken API&#39;s van het scriptmodel voor aangepaste formulieren. Deze expressies retourneren waarden van bepaalde typen. Voor meer informatie over uitdrukkingen en beste praktijken rond hen, zie [&#x200B; Aangepaste vormuitdrukkingen &#x200B;](/help/forms/using/adaptive-form-expressions.md).

* Adobe raadt u aan synchrone bewerkingen uit JavaScript te gebruiken in plaats van asynchrone bewerkingen wanneer u regels maakt met de regeleditor. Het gebruik van asynchrone bewerkingen wordt sterk afgeraden. Als u zich echter in een situatie bevindt waarin asynchrone bewerkingen onvermijdelijk zijn, is het van essentieel belang dat u de afsluitfuncties van JavaScript implementeert. Door dit te doen, kunt u effectief tegen om het even welke potentiële rassenvoorwaarden beschermen, ervoor zorgen uw regelimplementaties optimale prestaties leveren en stabiliteit handhaven door heel.

  Bijvoorbeeld, veronderstellen wij gegevens van externe API moeten halen en dan sommige regels toepassen die op die gegevens worden gebaseerd. Wij gebruiken een sluiting om de asynchrone API vraag te behandelen en ervoor te zorgen dat de regels worden toegepast nadat de gegevens worden gehaald. Hier volgt de voorbeeldcode:

  ```JavaScript
       function fetchDataFromAPI(apiEndpoint, callback) {
        // Simulate asynchronous API call with setTimeout
        setTimeout(() => {
          // Assuming the API call is successful, we receive some data
          const data = {
            someValue: 42,
          };
          // Invoke the callback with the fetched data
          callback(data);
        }, 2000); // Simulate a 2-second delay for the API call
      }
      // Rule implementation using Closure
      function ruleImplementation(apiEndpoint) {
        // Using a closure to handle the asynchronous API call and rule application
        // say you have set this value in street field inside address panel
        var streetField = address.street;
        fetchDataFromAPI(apiEndpoint, (data) => {
          streetField.value = data.someValue;
        });
      }
      // Example usage of the rule implementation
      const apiEndpoint = "https://example-api.com/data";
      ruleImplementation(apiEndpoint);
  ```

  In dit voorbeeld simuleert `fetchDataFromAPI` een asynchrone API-aanroep met `setTimeout` . Zodra de gegevens worden gehaald, roept het de verstrekte callback functie aan, die de sluiting is om de verdere regeltoepassing te behandelen. De functie `ruleImplementation` bevat de regellogica.


### Werken met thema&#39;s {#working-with-themes}

Met Aangepast voor thema&#39;s kunt u herbruikbare stijlen maken die op verschillende formulieren kunnen worden toegepast voor een consistente vormgeving. Met Thema&#39;s kunt u stijlen definiëren voor formuliercomponenten en deelvensters. De beste praktijken rond thema&#39;s zijn als volgt:

* Gebruik de elementenbibliotheek voor een snelle toepassing van tekststijlen, achtergrond en afbeeldingen. Wanneer een stijl wordt toegevoegd aan de elementenbibliotheek, is deze beschikbaar voor andere thema&#39;s en in de stijlmodus van de formuliereditor.
* Algemene instellingen zoals lettertype en pagina-achtergrond toepassen met behulp van een kiezer op paginaniveau.
* Met clientbibliotheken kunt u bestaande of geavanceerde stijlen in uw thema&#39;s importeren.
* U kunt de opmaak overschrijven voor specifieke velden, deelvensters of knoppen in een formulierstijllaag.
* Als een thema niet aan uw opmaakvereisten voldoet, kunt u vooraf gedefinieerde klassen gebruiken, zoals guideFieldNode, guideFieldLabel, guideFieldWidget en guidePanelNode, om algemene stijl op formulieren toe te passen.

Voor meer informatie, zie [&#x200B; Thema&#39;s &#x200B;](/help/forms/using/themes.md).

### Prestaties van grote en complexe formulieren optimaliseren {#optimizing-performance-of-large-and-complex-forms}

Auteurs van formulieren en eindgebruikers van formulieren hebben doorgaans te maken met prestatieproblemen bij het laden van grote formulieren in de ontwerpmodus of bij uitvoering. Naarmate het aantal objecten (velden en deelvensters) in het formulier toeneemt, wordt het ontwerp en de runtime minder prettig. Het voorkomt ook dat meerdere auteurs tegelijkertijd samenwerken en een formulier ontwerpen.

Overweeg de volgende aanbevolen procedures om prestatieproblemen met grote formulieren te verhelpen:

* Aanbevolen wordt om adaptieve formulieren te maken met behulp van XSD-formuliergegevensmodel, zelfs als een XFA wordt geconverteerd naar een adaptief formulier, indien mogelijk.
* Neem alleen de velden en deelvensters op in adaptieve formulieren die informatie van de gebruiker vastleggen. Houd statische inhoud minimaal of gebruik URL&#39;s om deze in een apart venster te openen.
* Hoewel elk formulier is ontworpen voor een bepaald doel, zijn er in de meeste formulieren enkele gangbare segmenten. Bijvoorbeeld persoonlijke gegevens, adres, werkgelegenheidsgegevens enzovoort. Creeer [&#x200B; adaptieve vormfragmenten &#x200B;](/help/forms/using/adaptive-form-fragments.md) voor gemeenschappelijke vormelementen en secties en gebruik hen over vormen. U kunt een deelvenster in een bestaand formulier ook opslaan als een fragment. Elke wijziging in een fragment wordt weerspiegeld in alle bijbehorende adaptieve formulieren. Het bevordert samenwerkingscreatie aangezien de veelvoudige auteurs aan verschillende fragmenten gelijktijdig kunnen werken die omhoog een vorm maken.

   * U kunt ook formulierfragmenten maken voor niet-herbruikbare secties tijdens het ontwerpen van formulieren. Naarmate formulieren groter en complexer worden, kan het opsplitsen ervan in fragmenten het ontwerpproces aanzienlijk vereenvoudigen en het formulier eenvoudiger te onderhouden maken. Op deze manier kunt u zich richten op kleinere, beter te beheren stukken van het formulier in plaats van het hele formulier tegelijk te verwerken.
   * Net als adaptieve formulieren wordt aangeraden dat alle fragmentspecifieke opmaak en aangepaste scripts in de clientbibliotheek worden gedefinieerd met behulp van het dialoogvenster Fragmentcontainer. Probeer ook zelf-voldoende fragmenten te maken die niet afhankelijk zijn van objecten buiten de fragmenten.
   * Gebruik geen cross-fragments-scripts. Als er een object is buiten het fragment waarnaar u moet verwijzen, probeert u dat object te maken tot onderdeel van het bovenliggende formulier. Als het object zich nog steeds in een ander fragment moet bevinden, kunt u het met de naam ervan in het script raadplegen.

* Met Opslaan en hervatten met automatisch opslaan kunt u het aangepaste formulier periodiek opslaan en gebruikers in staat stellen later opnieuw te klikken om het formulier in te vullen.
* Configureer fragmenten die geleidelijk moeten worden geladen. Tijdens de runtime wordt een fragment dat is gemarkeerd om geladen, alleen gerenderd wanneer dit vereist is. Hierdoor wordt de laadtijd voor grote formulieren aanzienlijk verkort. Deze functie wordt ook ondersteund in fragmenten met herhaalbare deelvensters. Voor meer informatie, zie [&#x200B; luie lading &#x200B;](/help/forms/using/lazy-loading-adaptive-forms.md) vormen.

   * Configureer lui laden niet op fragmenten in een responsieve rasterlay-out of in het eerste deelvenster.
   * Componenten voor bestandsbijlagen en Algemene voorwaarden worden niet ondersteund in laaggeladen fragmenten.
   * Markeer een waarde in een lazy geladen paneel als Waarde globaal gebruiken als die waarde in een ander deel van het formulier wordt gebruikt zodat de waarde beschikbaar is voor gebruik wanneer het bevattende paneel wordt verwijderd.
   * U kunt zichtbaarheidsregels schrijven voor fragmenten die op basis van een voorwaarde moeten worden weergegeven of verborgen.
* Plaats de waarde van het **Aantal vraag per verzoek** in **Apache Sling Main Servlet** aan een vrij groot aantal. Het laat de server van Forms toe om extra vraag toe te staan. De configuratie geeft een standaardwaarde van 1500 weer. De waarde, 1500 aanroepen, is voor andere Experience Manager-componenten zoals Sites en Assets. De standaardwaarde van adaptieve formulieren is 20000. Als u de fout `too many calls` in het logbestand tegenkomt of als het formulier niet wordt weergegeven, kunt u proberen de waarde te verhogen tot een groot aantal om het probleem op te lossen. Als het aantal aanroepen groter is dan 20000, is het formulier complex en kan het enige tijd duren voordat het formulier in de browser wordt weergegeven. Dit gebeurt alleen voor de eerste keer dat het formulier wordt geladen, nadat het formulier in de cache is geplaatst en wanneer het formulier in de cache is geplaatst, heeft dit geen significante invloed op de prestaties.

### Overwegingen met betrekking tot DOM-grootte en browserprestaties

Bij het maken van grote en complexe adaptieve formulieren is het belangrijk rekening te houden met de invloed van DOM-grootte op rendering en prestaties:

* **Effect van de Grootte DOM**: Terwijl er geen harde grens voor DOM grootte in AEM Forms is, kan de bovenmatige grootte DOM prestaties beduidend beïnvloeden, vooral wanneer het behandelen van lui-Geladen fragmenten. Grote DOM-structuren vereisen meer geheugen en verwerkingstijd om te renderen en te bewerken.

* **Browser die Verschillen teruggeeft**: Renderende prestaties kunnen beduidend over verschillende browsers en apparaten variëren. Sommige renderingengines van browsers verwerken dynamische DOM-updates anders, met verschillende benaderingen voor stijlherberekeningen, doorloop en reparaties. Dit is vooral opvallend bij grote, dynamisch geladen inhoud. In sommige browsers kan elke belangrijke DOM-manipulatie een volledige lay-outherberekening en -reparatie van de pagina tot gevolg hebben, waardoor prestatieproblemen met grote of complexe formulieren toenemen.

* **Factoren van Prestaties**: Verscheidene factoren beïnvloeden lazy ladingsprestaties:
   * De grootte en complexiteit van de fragmenten
   * De CSS-stijlen die zijn toegepast op elementen
   * Het aantal terugvloeiingen dat wordt geactiveerd door dynamische updates
   * De apparaat- en browsermogelijkheden

* **Real-world Effect**: In waargenomen gevallen, hebben de vormen met DOM grootte rond 400 KB significante teruggevende vertragingen van tot 15 seconden op bepaalde browsers ervaren. Deze vertragingen zijn niet alleen het gevolg van de fragmentgrootte, maar ook van CSS-verwerking en het opnieuw plaatsen van pagina&#39;s die worden geactiveerd tijdens het invoegen van dynamische inhoud.

**Beste praktijken voor het Leiden de Grootte van DOM:**

* Voor statische inhoud kunt u bijvoorbeeld AEM Content Fragments gebruiken in plaats van dynamisch grote HTML-blokken in te voegen via lui laden. Deze aanpak kan terugvloeiingen, reparaties en de uitvoeringstijd van JavaScript verminderen en de algehele laadprestaties van de pagina verbeteren.

* Wanneer fragmenten dynamisch en uitgelijnd moeten zijn, breekt u grote fragmenten op in kleinere, beter te beheren fragmenten en laadt u alleen de vereiste secties.

* Voer waar nodig progressieve onthullingspatronen uit, die extra vormgebieden slechts wanneer vereist tonen gebaseerd op gebruikersinput.

* Test uw formulieren in meerdere browsers en apparaten, vooral wanneer u uitgelijnde fragmenten gebruikt, voor consistente prestaties in verschillende omgevingen.

* De CSS die in uw formulieren wordt gebruikt, bewaken en optimaliseren, aangezien uitgebreide of slecht gestructureerde CSS de rendertijd aanzienlijk kan verhogen, vooral tijdens dynamische inhoudsupdates.

Voor meer technische details over hoe de verschillende browser teruggevende motoren DOM updates, terugvloeiingen, en reparaties behandelen, overweeg het onderzoeken van browser motordocumentatie zoals die verstrekt door diverse browser verkopers.

### Aangepaste formulieren vooraf invullen {#prefilling-adaptive-forms}

U kunt adaptieve formuliervelden vooraf invullen met gegevens die vanaf de achtergrond zijn opgehaald, zodat gebruikers het formulier snel kunnen invullen en typfouten kunnen voorkomen.

* AEM Forms biedt een vooraf ingevulde service voor het lezen van gegevens uit een vooraf gedefinieerd XML-gegevensbestand en het vooraf invullen van de velden van een adaptief formulier met de inhoud in het vooraf ingevulde XML-bestand.
* De XML van de vooraf ingevulde gegevens moet voldoen aan het schema van het formuliermodel dat is gekoppeld aan het adaptieve formulier.
* Neem secties `afBoundedData` en `afUnBoundedData` op in de vooraf ingevulde XML om zowel gebonden als niet-gebonden velden vooraf in een adaptief formulier in te vullen.

* Voor adaptieve formulieren die zijn gebaseerd op het formuliergegevensmodel, biedt AEM Forms een vooraf ingevulde service voor het formuliergegevensmodel. De Prefill-service zoekt naar gegevensbronnen voor gegevensmodelobjecten in het adaptieve formulier en vult de veldwaarden vooraf in bij het weergeven van het formulier.
* U kunt ook het bestand, de crx, de service of de http-protocollen gebruiken om adaptieve formulieren vooraf in te vullen.
* AEM Forms biedt ondersteuning voor aangepaste Prefill-services die u kunt insluiten als een OSGi-service om adaptieve formulieren vooraf in te vullen.

Voor meer informatie, zie [&#x200B; vooraf aanpasbare vormgebieden &#x200B;](/help/forms/using/prepopulate-adaptive-form-fields.md) vullen.

### Aangepaste formulieren ondertekenen en indienen {#signing-and-submitting-adaptive-forms}

Voor adaptieve formulieren zijn acties verzenden vereist om door de gebruiker opgegeven gegevens te verwerken. Een handeling Verzenden bepaalt de taak die wordt uitgevoerd voor de gegevens die u verzendt met behulp van een adaptief formulier.

* Er zijn verschillende verzendacties beschikbaar in adaptieve formulieren. Voor details, zie [&#x200B; Vormend de Submit actie &#x200B;](/help/forms/using/configuring-submit-actions.md).
* U kunt een aangepaste verzendactie schrijven als de standaardverzendacties niet voldoen aan uw gebruiksscenario. Voor meer informatie, zie [&#x200B; het Schrijven van douane verzendt actie voor adaptieve vormen &#x200B;](/help/forms/using/custom-submit-action-form.md).
* Voeg validaties aan de serverzijde toe om te voorkomen dat er ongeldige gegevens worden verzonden.

U kunt multi-sign ervaring van Adobe gebruiken Sign in adaptieve vormen. Houd rekening met het volgende wanneer u Adobe Sign in adaptieve formulieren configureert. Voor details, zie [&#x200B; Gebruikend het Teken van Adobe in een adaptieve vorm &#x200B;](/help/forms/using/working-with-adobe-sign.md).

* Het adaptieve formulier dat is ingeschakeld voor Adobe Sign wordt alleen verzonden nadat alle ondertekenaars het formulier hebben ondertekend. Forms wordt weergegeven in de status In afwachting van ondertekening totdat het formulier door alle ondertekenaars is ondertekend.
* U kunt ondertekeningservaring in formulieren configureren of ondertekenaars omleiden naar een ondertekeningspagina bij verzending.
* Configureer sequentiële of parallelle ondertekeningservaring, indien van toepassing.

### Document met record genereren {#generating-document-of-record}

Een recorddocument (DoR) is een afgevlakte PDF-versie van een adaptief formulier dat u kunt afdrukken, ondertekenen of archiveren.

* Afhankelijk van het formuliergegevensmodel waarop een adaptief formulier is gebaseerd, kunt u als volgt een sjabloon configureren voor DoR:

   * **XFA vormmalplaatje**: Gebruik het bijbehorende XDP dossier als malplaatje DoR.
   * **XSD schema**: Gebruik het bijbehorende malplaatje XFA dat het zelfde schema van XML gebruikt zoals die door de adaptieve vorm wordt gebruikt.
   * **niets**: Gebruik auto-geproduceerde DoR.

* Configureer kop-, voettekst-, afbeeldingen, kleur-, lettertype-, enzovoort, rechts van het tabblad Document of Record van de adaptieve formuliereditor.
* Gebruik `DoRService` om het DoR programmatically te produceren.
* Verborgen velden uitsluiten van de DoR.
* Gebruik de aanvraagparameter `afAcceptLang` om DoR in een andere landinstelling weer te geven.

<!--### Debugging and testing adaptive forms {#debugging-and-testing-adaptive-forms}

[AEM Chrome Plug-in](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/) is a browser extension for Google Chrome that provides tools for debugging adaptive forms. Form authors and developers can use these tools to:

* Identify bottlenecks and optimize performance of form rendering
* Debug keywords and bindRef errors in the form
* Enable and configure logs
* Debug rules and scripts in the form
* Explore and learn about guideBridge APIs

For more information, see [AEM Chrome Plug-in - Adaptive Form](https://adobe-consulting-services.github.io/acs-aem-tools/aem-chrome-plugin/adaptive-form/).-->

### Aangepaste formulieren valideren op AEM-server {#validating-adaptive-forms-on-aem-server}

Validaties aan de serverzijde zijn vereist om te voorkomen dat er pogingen worden ondernomen om validaties op de client te omzeilen en dat er een mogelijk compromis ontstaat tussen gegevensverzending en overtredingen van de bedrijfsregels. Servervalidaties worden op de server uitgevoerd door de vereiste clientbibliotheek te laden.

* Neem functies op in een clientbibliotheek voor het valideren van expressies in adaptieve formulieren en geef de clientbibliotheek op in het dialoogvenster Container voor adaptieve formulieren. Voor meer informatie, zie [&#x200B; server-zijbevestiging &#x200B;](/help/forms/using/configuring-submit-actions.md#p-server-side-revalidation-in-adaptive-form-p).
* Servervalidatie valideert het formuliermodel. Het wordt aanbevolen een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML-opmaak en DOM-manipulatie in dezelfde clientbibliotheek.

### Aangepaste formulieren lokaliseren {#localizing-adaptive-forms}

AEM biedt vertaalworkflows waarmee u adaptieve formulieren kunt lokaliseren. Voor informatie, zie [&#x200B; Gebruikend het vertaalwerkschema van AEM om adaptieve vormen &#x200B;](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md) te lokaliseren.

U kunt het beste adaptieve formulieren als volgt lokaliseren:

* Gebruik adaptieve formulierfragmenten voor gemeenschappelijke elementen in verschillende formulieren en lokaliseer fragmenten. Zo weet u zeker dat u een fragment één keer lokaliseert en het geeft in alle formulieren weer waar het gelokaliseerde fragment wordt gebruikt.
* Wijzigingen zoals het toevoegen van een nieuwe component of het toepassen van een script in een gelokaliseerd formulier, worden niet automatisch gelokaliseerd. Daarom moet u een formulier invullen voordat u het lokaliseert om meerdere lokalisatiecycli te voorkomen.
* Gebruik de aanvraagparameter `afAcceptLang` om de landinstelling van de browser te overschrijven en het formulier in de opgegeven landinstelling te genereren. De volgende URL is bijvoorbeeld gedwongen het formulier te genereren in een Japanse landinstelling, ongeacht de landinstelling die in de browser is opgegeven:

  `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

* AEM Forms ondersteunt momenteel de lokalisatie van adaptieve formulieren met inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR). U kunt echter tijdens runtime ondersteuning toevoegen voor nieuwe landinstellingen voor adaptieve formulieren. Voor meer informatie, zie [&#x200B; Ondersteunend nieuwe scènes voor adaptieve vormenlocalisatie &#x200B;](/help/forms/using/supporting-new-language-localization.md).

## Formulierproject voorbereiden voor productie {#prepare-forms-project-for-production}

### Processorserver voor formulieren toevoegen {#adding-forms-processing-server}

U kunt een extra instantie van de server van AEM Forms vormen die achter de firewall in een beveiligde streek verblijft. U kunt deze instantie gebruiken voor:

* **verwerking van de Partij**: banen die terugkomen of in partijen met zware lading gepland zijn. U kunt bijvoorbeeld instructies afdrukken, correspondentie genereren en documentservices gebruiken, zoals PDF Generator, Output en Assembler.
* **het Opslaan van PII gegevens**: Sparen PII- gegevens op de verwerkingsserver. Dit is niet verplicht als u al een aangepaste opslagprovider gebruikt voor het opslaan van PII-gegevens.

### Project verplaatsen naar een andere omgeving {#moving-project-to-another-environment}

Vaak moet u AEM-projecten van de ene omgeving naar de andere verplaatsen. Enkele belangrijke dingen die u moet onthouden tijdens het verplaatsen zijn:

* Maak een back-up van uw bestaande clientbibliotheken, aangepaste code en configuraties.
* Implementeer productpakketten en patches handmatig en in de opgegeven volgorde in de nieuwe omgeving.
* Implementeer projectspecifieke codepakketten en -bundels handmatig en als een afzonderlijk pakket of bundel op de nieuwe AEM-server.
* (*AEM Forms op JEE slechts*) stelt LCAs en DSCs manueel op de server van Forms Workflow op.
* Het gebruik [&#x200B; functionaliteit van de uitvoer-Invoer &#x200B;](/help/forms/using/import-export-forms-templates.md) om activa naar het nieuwe milieu te bewegen. U kunt de replicatieagent ook vormen en de activa publiceren.
* Wanneer u een upgrade uitvoert, vervangt u alle verouderde API&#39;s en functies door nieuwe API&#39;s en functies.

### AEM configureren {#configuring-aem}

U kunt het beste AEM configureren om de algehele prestaties te verbeteren:

* Compressie van HTML-clientbibliotheek voor JavaScript en CSS vanuit Felix Console inschakelen.
* Plaats alle clientbibliotheken in `/etc.clientlibs/fd` en eventuele extra aangepaste clientbibliotheken in AEM Dispatcher om de reactiesnelheid en beveiliging van uw gepubliceerde formulieren te verbeteren. Voor meer informatie, zie [&#x200B; Dispatcher &#x200B;](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html).

* Plaats geen `/content/forms/af/` - en `/content/dam/formsanddocuments/*` -paden in de cache. voor gedetailleerde informatie over het vormen van adaptieve vormen caching, zie [&#x200B; Aangepaste vormen in cache plaatsen &#x200B;](/help/forms/using/configure-adaptive-forms-cache.md).

* HTML inschakelen via de compressiemodule van de webserver. Voor meer informatie, zie [&#x200B; Prestaties het stemmen van de server van AEM Forms &#x200B;](/help/forms/using/performance-tuning-aem-forms.md).
* Verhoog de aanroepen per aanvraagconfiguratie voor grote formulieren. Zie [&#x200B; Optimizing prestaties van grote en complexe vormen &#x200B;](/help/forms/using/adaptive-forms-best-practices.md#optimizing-performance-of-large-and-complex-forms).
* Creeer [&#x200B; pagina&#39;s van de douanefout die door foutenmanager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/customizing-errorhandler-pages.html) worden getoond.
* Beveiligde AEM Forms-server.

   * Gebruik de uitvoermodus van `nosamplecontent` om ervoor te zorgen dat er geen voorbeeldinhoud is en dat voorbeeldgebruikers op de productieserver zijn geïmplementeerd. Zie [&#x200B; Lopend AEM op Productie Klaar Wijze &#x200B;](/help/sites-administering/production-ready.md).

* Houd de heapgrootte tot minimaal 8 GB. Voor andere montages, zie [&#x200B; Prestaties het stemmen van de server van AEM Forms &#x200B;](/help/forms/using/performance-tuning-aem-forms.md).
* Gebruik gebruikerssessies voor services in plaats van beheersessies voor het uitvoeren van taken op serviceniveau. Voor meer informatie, zie [&#x200B; authentificatie van de Dienst &#x200B;](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html).

>[!VIDEO](https://vimeo.com/)

### Externe opslag voor concepten en verzonden formuliergegevens configureren {#external-storage}

In een productieomgeving wordt aanbevolen de ingediende formuliergegevens niet op te slaan in de gegevensopslagruimte van AEM. Bij de standaardimplementatie van Forms Portal Store, Store Content en Store PDF-verzendacties worden formuliergegevens opgeslagen in de AEM-opslagplaats. Deze indieningsacties zijn alleen bedoeld voor demonstratiedoeleinden. Bovendien maken de functies Opslaan, Hervatten en Automatisch opslaan standaard gebruik van poortopslag. Overweeg daarom de volgende aanbevelingen:

* **Opslagend ontwerp gegevens**: Als u de eigenschap van het Ontwerp van adaptieve vormen gebruikt, zou u een douaneDienst moeten uitvoeren verstrekken Interface (SPI) om ontwerp gegevens in veiligere opslag zoals gegevensbestand op te slaan. Voor meer informatie, zie [&#x200B; Steekproef voor het integreren van concepten &amp; voorleggingscomponent met gegevensbestand &#x200B;](/help/forms/using/integrate-draft-submission-database.md).

* **Opslagend voorleggingsgegevens**: Als u het Portaal van de Vorm gebruikt dient Opslag voor te leggen, zou u douaneSPI moeten uitvoeren om voorleggingsgegevens in een gegevensbestand op te slaan. Zie [&#x200B; Steekproef voor het integreren van concepten &amp; verzendingscomponent met gegevensbestand &#x200B;](/help/forms/using/integrate-draft-submission-database.md) voor een steekproefintegratie.

  U kunt ook een aangepaste verzendactie schrijven waarmee formuliergegevens en bijlagen worden opgeslagen in een beveiligde opslagruimte. Zie [&#x200B; het Schrijven douanevoorlegt actie voor adaptieve vormen &#x200B;](/help/forms/using/custom-submit-action-form.md) voor meer informatie.

* **Lengte van ontwerpidentiteitskaart**: Wanneer u sparen een adaptieve vorm als ontwerp, een ontwerpidentiteitskaart wordt geproduceerd om het ontwerp uniek te identificeren. De minimumwaarde voor de lengte van het veld concept-id is 26 tekens. Adobe raadt u aan de lengte van de concept-id in te stellen op 26 of meer tekens.

### Persoonlijke identificeerbare gegevens verwerken {#handling-personally-identifiable-information}

Een van de belangrijkste uitdagingen voor organisaties is hoe te om persoonlijk identificeerbare (PII) gegevens te behandelen. Hier volgt een aantal aanbevolen procedures voor het verwerken van dergelijke gegevens:

* Gebruik een beveiligde externe opslagruimte, zoals een database, om gegevens op te slaan uit concepten en verzonden formulieren. Zie [&#x200B; Vormend externe opslag voor concepten en voorgelegde vormengegevens &#x200B;](/help/forms/using/adaptive-forms-best-practices.md#external-storage).
* Met de component Voorwaarden en Voorwaarden van het gebruik kunt u expliciete toestemming van de gebruiker nemen voordat u automatisch opslaat. In dit geval schakelt u automatisch opslaan alleen in als de gebruiker akkoord gaat met de voorwaarden in de component Voorwaarden.

## Kies de Redacteur van de Regel, de Redacteur van de Code, of de Bibliotheken van de Cliënt van de Douane voor uw Aangepast Vorm {#RuleEditor-CodeEditor-ClientLibs}

### Regeleditor {#rule-editor}

<!--The AEM Forms Rule Editor offers predefined functions for defining rules in adaptive forms without extensive programming. It facilitates the implementation of conditional logic, data validation, and integration with external sources. This visual interface is especially valuable for business users and form designers, enabling them to create dynamic and complex rules with ease, here we discusss few use cases where rule editor allows you to:-->

De AEM Forms Rule Editor biedt een visuele interface voor het maken en beheren van regels, waardoor er minder behoefte is aan uitgebreide codering. Het kan vooral nuttig voor bedrijfsgebruikers of vormontwerpers zijn die geen geavanceerde programmeringsvaardigheden kunnen hebben maar bedrijfsregels binnen de vormen moeten bepalen en handhaven, hier bespreken wij weinig gebruiksgevallen waar de regelredacteur u toestaat:

* &#x200B;<!-- Allows you --> Om bedrijfsregels voor uw vormen zonder de behoefte aan uitgebreide programmering te bepalen.
* &#x200B;<!-- Use the Rule Editor when you need --> Voorwaardelijke logica implementeren in uw formulieren. Dit omvat het tonen of verbergen van formulierelementen, het wijzigen van veldwaarden op basis van bepaalde voorwaarden of het dynamisch wijzigen van het gedrag van uw formulieren.
* &#x200B;<!--When you want --> Om de regels van de gegevensbevestiging op vormbijdragen af te dwingen, kan de Redacteur van de Regel worden gebruikt om bevestigingsvoorwaarden te bepalen.
* &#x200B;<!-- When you need --> Als u uw formulieren wilt integreren met externe gegevensbronnen (FDM) of services, kunt u in de Regeleditor regels definiëren voor het ophalen, weergeven of bewerken van gegevens tijdens formulierinteracties.
* &#x200B;<!-- If you want -->Als u dynamische en interactieve formulieren wilt maken die reageren op handelingen van gebruikers, kunt u in de Regeleditor regels definiëren die het gedrag van formulierelementen in real-time bepalen.

De Redacteur van de regel is beschikbaar voor zowel de Componenten van de Stichting van AEM Forms als de Componenten van de Kern.

### Code-editor {#code-editor}

De Redacteur van de code is een hulpmiddel binnen Adobe Experience Manager (AEM) Forms dat u toestaat om douanescripts en code voor complexere en geavanceerdere functionaliteit in uw vormen te schrijven, hier bespreken wij weinig gebruiksgevallen:

* Wanneer u aangepaste logica of gedrag aan de clientzijde moet implementeren die verder gaat dan de mogelijkheden van de AEM Forms Rule Editor. Met de Code-editor kunt u JavaScript-code schrijven voor het verwerken van complexe interacties, berekeningen of validaties.
* Als uw formulier verwerking op de server of integratie met externe systemen vereist, kunt u met de Code-editor een aangepast serverscript schrijven. U kunt tot guideBridge API in code redacteur toegang hebben om het even welke complexe logica op vormgebeurtenissen en voorwerpen uit te voeren.
* Wanneer u hoogst aangepaste gebruikersinterfaces vereist die voorbij de standaardmogelijkheden van de componenten van AEM Forms gaan, staat de Redacteur van de Code u toe om douanestijlen, gedrag uit te voeren, of zelfs douaneformuliercomponenten tot stand te brengen.
* Als in uw formulier asynchrone bewerkingen worden uitgevoerd, zoals het laden van asynchrone gegevens, kunt u de Code-editor gebruiken om deze bewerkingen te beheren met behulp van aangepaste asynchrone JavaScript-code.

Het is belangrijk om op te merken dat het gebruiken van de Redacteur van de Code een goed inzicht in de architectuur van JavaScript en van AEM Forms vereist. Bovendien, wanneer het uitvoeren van douanecode, zorg ervoor dat u beste praktijken volgt, zich aan veiligheidsrichtlijnen houdt, en uw code grondig test om potentiële kwesties in productiemilieu&#39;s te verhinderen. U kunt callback voor FDM uitvoeren gebruikend code redacteur.

De Redacteur van de code is beschikbaar voor de Component van de Stichting van AEM Forms slechts. Voor Aangepaste componenten van de Kern van de Vorm, kunt u douanefuncties gebruiken om uw eigen vormregels tot stand te brengen, die in de volgende sectie worden beschreven.

### Aangepaste functies {#custom-client-libs}

Het gebruik van aangepaste clientbibliotheken in AEM Forms (Adobe Experience Manager Forms) kan in verschillende scenario&#39;s nuttig zijn voor het verbeteren van de functionaliteit, de opmaak of het gedrag van uw formulieren. Hier volgen enkele situaties waarin aangepaste clientbibliotheken geschikt kunnen zijn:

* Als u een uniek ontwerp of merk voor uw formulieren moet implementeren die verder gaan dan de mogelijkheden van de standaardopmaakopties van AEM Forms, kunt u aangepaste clientbibliotheken maken om de vormgeving te bepalen.
* Wanneer u aangepaste logica aan de clientzijde nodig hebt, kunt u methoden in meerdere formulieren opnieuw gebruiken of gedrag dat niet met de standaard AEM Forms-functies kan worden bereikt. Dit kan bestaan uit dynamische formulierinteracties, aangepaste validatie of integratie met bibliotheken van derden.
* U kunt de prestaties van uw formulieren verbeteren door resources aan de clientzijde te optimaliseren en te miniaturen. Met aangepaste clientbibliotheken kunt u JavaScript- en CSS-bestanden bundelen en comprimeren, waardoor de laadtijd van de pagina afneemt.
* Wanneer u extra JavaScript-bibliotheken of -frameworks moet integreren die niet zijn opgenomen in de standaard AEM Forms-instelling. Dit kan nodig zijn voor functies zoals verbeterde datumkiezers, grafieken of andere interactieve componenten.

Voordat u besluit aangepaste clientbibliotheken te gebruiken, is het belangrijk dat u rekening houdt met de overhead voor onderhoud, mogelijke conflicten met toekomstige updates en de naleving van de aanbevolen procedures. Zorg ervoor dat uw aanpassingen goed gedocumenteerd en getest zijn om problemen tijdens upgrades of tijdens het samenwerken met andere ontwikkelaars te voorkomen.

>[!NOTE]
> De Functie van de douane is beschikbaar voor zowel de Componenten van de Stichting van AEM Forms als Componenten van de Kern.

**Voordelen van de Functies van de Douane:**

**de Functies van de Douane** verstrekken een opmerkelijk voordeel over de **Redacteur van de Code** omdat het een duidelijke scheiding tussen inhoud en code verstrekt die samenwerking verbetert en werkschema&#39;s stroomlijnt. Aanbevolen wordt om aangepaste functies te gebruiken voor de volgende voordelen:

* **naadloos gebruiks versioning controle zoals Git:**
   * De isolatie van code van inhoud vermindert de conflicten van de it beduidend tijdens inhoudsbeheer en bevordert een goed georganiseerde bewaarplaats.
   * De Functies van de douane zijn waardevol voor projecten met veelvoudige contribuanten die gelijktijdig werken.

* **Technische Voordelen:**
   * Aangepaste functies bieden modulariteit en inkapseling.
   * Modules kunnen onafhankelijk van elkaar worden ontwikkeld, getest en onderhouden.
   * Verbetert de herbruikbaarheid en het onderhoud van code.

* **Efficiënt Ontwikkelingsproces:**
   * Met modulariteit kunnen ontwikkelaars zich richten op specifieke functies.
   * Vermindert de last van ontwikkelaars door de ingewikkeldheid van de volledige codebase voor een efficiënter ontwikkelingsproces te verminderen.



