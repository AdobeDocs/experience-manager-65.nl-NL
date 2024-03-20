---
title: Architectuur en plaatsingstopologieën voor AEM Forms
description: Architectuurgegevens voor AEM Forms en aanbevolen topologieën voor nieuwe en bestaande AEM klanten en klanten die van LiveCycle ES4 aan AEM Forms upgraden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: d4421d46-cfc9-424e-8a88-9d0a2994a5cf
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2469'
ht-degree: 0%

---

# Architectuur en plaatsingstopologieën voor AEM Forms {#architecture-and-deployment-topologies-for-aem-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture.html) |
| AEM 6,5 | Dit artikel |

## Architectuur {#architecture}

AEM Forms is een toepassing die in AEM wordt geïmplementeerd als een AEM. Het pakket wordt ook wel AEM Forms-add-onpakket genoemd. Het AEM Forms add-on pakket bevat beide services (API-providers), die worden geïmplementeerd in de AEM OSGi-container, en servlets of JSPs (die zowel front-end als REST API-functionaliteit biedt) die worden beheerd door het AEM Sling-framework. Het volgende diagram toont deze opstelling:

![architectuur](assets/architecture.png)

De architectuur voor AEM Forms omvat de volgende componenten:

* **Core AEM services:** De basisdiensten die aan een opgestelde toepassing AEM verlenen. Deze services omvatten een inhoudsopslagruimte die compatibel is met JCR, een OSGI-servicecontainer, een workflowengine, een vertrouwde opslag, een sleutelarchief, enzovoort. Deze services zijn beschikbaar voor AEM Forms-toepassingen, maar worden niet geleverd door AEM Forms-pakketten. Deze services vormen een integraal onderdeel van de algemene AEM en verschillende AEM Forms-componenten gebruiken deze services.
* **Forms-services:** Formuliergerelateerde functionaliteit bieden, zoals het maken, samenstellen, distribueren en archiveren van PDF-documenten, het toevoegen van digitale handtekeningen om de toegang tot documenten te beperken en het decoderen van streepjesgecodeerde formulieren. Deze diensten zijn openbaar beschikbaar voor consumptie door douanecode die in AEM wordt opgesteld.
* **Weblaag:** JSPs of servlets, die over gemeenschappelijke en vormdiensten worden gebouwd, die de volgende functionaliteit verstrekken:

   * **Voorkant ontwerpen**: Een gebruikersinterface voor het ontwerpen en beheren van formulieren voor het schrijven en beheren van formulieren.
   * **Formulieruitvoering en verzending vooraf**: Een eindgebruiker die wordt geconfronteerd met een interface voor gebruik door de eindgebruikers van de AEM Forms (bijvoorbeeld burgers die een overheidswebsite openen). Dit biedt formulieruitvoering (weergaveformulier in een webbrowser) en verzendfuncties.
   * **REST API&#39;s**: JSPs en servlets voeren een ondergroep vormdiensten voor ver gebruik door HTTP-gebaseerde cliënten, zoals de vormen mobiele SDK uit.

**AEM Forms op OSGi:** Een AEM Forms op OSGi-omgeving is standaard AEM Auteur of AEM Publish met AEM Forms-pakket dat erop is geïmplementeerd. U kunt AEM Forms uitvoeren op OSGi in een [enige serveromgeving, Farm, en gegroepeerde instellingen](/help/sites-deploying/recommended-deploys.md). Clusterinstellingen zijn alleen beschikbaar voor AEM auteur-instanties.

**AEM Forms op JEE:** AEM Forms on JEE is AEM Forms-server die wordt uitgevoerd op JEE-stack. Deze heeft AEM Auteur met AEM Forms add-on pakketten en extra AEM Forms JEE-mogelijkheden die op één JEE-stapel worden geïmplementeerd die op een toepassingsserver wordt uitgevoerd. U kunt AEM Forms op JEE in enig-server en gegroepeerde montages in werking stellen. AEM Forms on JEE is alleen vereist voor het uitvoeren van documentbeveiliging, procesbeheer en voor klanten van LiveCycles die upgraden naar AEM Forms. Hier volgen enkele aanvullende scenario&#39;s voor het gebruik van AEM Forms op JEE:

* **Ondersteuning voor werkruimte HTML (voor klanten die de werkruimte HTML gebruiken):** AEM Forms on JEE schakelt een eenmalige aanmelding in met Verwerkingsinstanties, geeft bepaalde elementen weer die bij Verwerkingsinstanties worden gegenereerd en verwerkt de verzending van formulieren die in de werkruimte HTML worden gegenereerd.
* **Geavanceerde verwerking van aanvullende formulier-/interactieve communicatiegegevens**: AEM Forms on JEE kan worden gebruikt voor extra verwerking van formulier-/interactieve communicatiegegevens (en het opslaan van de resultaten in een geschikte gegevensopslag) in complexe gebruiksgevallen waarin geavanceerde mogelijkheden voor procesbeheer vereist zijn.

AEM Forms on JEE biedt ook de volgende ondersteunende diensten aan de AEM componenten:

* **Geïntegreerd gebruikersbeheer:** Staat gebruikers van AEM Forms op JEE toe om als AEM vormen op gebruikers OSGi worden erkend en helpt SSO voor zowel gebruikers OSGi als JEE toelaten. Dit is vereist voor scenario&#39;s waar enig teken-binnen tussen AEM vormen op OSGi en AEM Forms op JEE wordt vereist (bijvoorbeeld, werkruimte van HTML).
* **Asset hosten:** AEM Forms on JEE kan activa (bijvoorbeeld, HTML5 vormen) bedienen die op AEM Forms op OSGi worden teruggegeven.

De AEM Forms-ontwerpgebruikersinterface ondersteunt het maken van Document of Record (DOR), PDF forms en HTML5 Forms niet. Dergelijke middelen worden ontworpen met de stand-alone toepassing van Forms Designer en individueel geüpload naar AEM Forms Manager. Voor AEM Forms op JEE kunnen formulieren ook worden ontworpen als toepassingsmiddelen (in AEM Forms Workbench) en worden geïmplementeerd in AEM Forms op de JEE-server.

AEM Forms op OSGi en AEM Forms op JEE hebben beide workflowmogelijkheden. U kunt basisworkflows voor diverse taken op de AEM formulieren op OSGi snel bouwen en implementeren, zonder dat u de volledige Process Management-capaciteit van AEM Forms op JEE hoeft te installeren. Er is een verschil in de [functies van een formuliergerichte workflow op AEM Forms voor OSGi en Process Management van AEM Forms in JEE](capabilities-osgi-jee-workflows.md). De ontwikkeling en het beheer van Form-centric werkschema&#39;s op AEM Forms op OSGi gebruikt de vertrouwde AEM van het Werkschema en AEM Inbox mogelijkheden.

## Terminologie {#terminologies}

In de volgende afbeelding worden verschillende AEM configuraties van formulierservers en hun componenten weergegeven die worden gebruikt bij een gebruikelijke AEM Forms-implementatie:

![aem_forms_-_recommendedtopologie](assets/aem_forms_-_recommendedtopology.png)

**Auteur:** Een auteurinstantie is een server van AEM Forms die in de standaardwijze van de Auteur in werking stelt. Het kan AEM Forms op JEE of AEM Forms op milieu OSGi zijn. Het is bedoeld voor interne gebruikers, formulieren en interactieve communicatieontwerpers, en ontwikkelaars. Het maakt de volgende functies mogelijk:

* **Formulieren en interactieve communicatie ontwerpen en beheren:** Ontwerpers en ontwikkelaars kunnen adaptieve formulieren en interactieve communicatie maken en bewerken, andere soorten extern gemaakte formulieren uploaden, bijvoorbeeld formulieren die zijn gemaakt in Adobe Forms Designer, en deze middelen beheren met de Forms Manager-console.
* **Publiceren van formulieren en interactieve communicatie:** Elementen die op een auteurinstantie worden gehost, kunnen naar een publicatie-instantie worden gepubliceerd om runtimebewerkingen uit te voeren. Bij het publiceren van middelen worden AEM replicatiefuncties gebruikt. Adobe adviseert dat een replicatieagent op alle auteursinstanties wordt gevormd om gepubliceerde formulieren aan verwerkingsinstanties manueel te duwen, en een andere replicatieagent wordt gevormd op verwerkingsinstanties met de *Bij ontvangst* trigger ingeschakeld om de ontvangen formulieren automatisch te repliceren om instanties te publiceren.

**Publiceren:** Een publicatie-instantie is een AEM Forms-server die wordt uitgevoerd in de standaardmodus Publiceren. Publicatie-instanties zijn bedoeld voor eindgebruikers van formuliertoepassingen, bijvoorbeeld gebruikers die een openbare website openen en formulieren verzenden. Het maakt de volgende functies mogelijk:

* Forms renderen en verzenden voor eindgebruikers.
* Het vervoer van ruwe ingediende formuliergegevens naar verwerkingsinstanties voor verdere verwerking en opslag in het definitieve registratiesysteem. De standaardimplementatie die in AEM Forms wordt verstrekt bereikt dit gebruikend de omgekeerde replicatiemogelijkheden van AEM. Er is ook een alternatieve implementatie beschikbaar voor het rechtstreeks verplaatsen van formuliergegevens naar verwerkingsservers in plaats van deze eerst lokaal op te slaan (de laatste is een noodzakelijke voorwaarde voor het activeren van reverse-replicatie). Klanten die zich zorgen maken over de opslag van mogelijk gevoelige gegevens op publicatieinstanties, kunnen hiervoor kiezen [alternatieve implementatie](/help/forms/using/configuring-draft-submission-storage.md), aangezien de verwerkingsinstanties typisch in een veiligere streek liggen.
* Renderen en verzenden van interactieve communicatie en letters: bij publicatie-instanties wordt een interactieve communicatie en brief weergegeven en de bijbehorende gegevens worden naar verwerkingsinstanties verzonden voor opslag en naverwerking. De gegevens kunnen lokaal op een publicatie-instantie worden opgeslagen en later worden gerepliceerd naar een verwerkingsinstantie (de standaardoptie), of rechtstreeks naar een verwerkingsinstantie worden geduwd zonder op de publicatie-instantie op te slaan. De laatstgenoemde implementatie is nuttig voor veiligheid-bewuste klanten.

**Verwerking:** Een instantie van AEM Forms die wordt uitgevoerd in de uitvoeringsmodus Auteur zonder dat gebruikers zijn toegewezen aan de groep met formulierbeheer. U kunt AEM Forms op JEE of AEM Forms op OSGi als verwerkingsinstantie opstellen. De gebruikers worden niet toegewezen om ervoor te zorgen dat de activiteiten van de creatie en het beheer van de vorm niet op de instantie van de Verwerking worden uitgevoerd en slechts op de instantie van de Auteur voorkomen. Een verwerkingsinstantie schakelt de volgende functies in:

* **Verwerking van onbewerkte formuliergegevens die afkomstig zijn van een instantie Publish:** Dit wordt hoofdzakelijk bereikt op een instantie van de Verwerking via AEM werkschema&#39;s die teweegbrengen wanneer de gegevens aankomen. De workflows kunnen gebruikmaken van de stap Formuliergegevensmodel die buiten het vak wordt weergegeven om de gegevens of het document naar een geschikte gegevensopslag te archiveren.
* **Beveiligde opslag van formuliergegevens**: Verwerking biedt een opslagplaats achter de firewall voor onbewerkte formuliergegevens die van gebruikers is geïsoleerd. Geen van de formulierontwerpers op de instantie Auteur en eindgebruikers op de instantie Publiceren hebben toegang tot deze opslagplaats.

  >[!NOTE]
  >
  >Adobe raadt aan een gegevensopslagruimte van derden te gebruiken om de uiteindelijke verwerkte gegevens op te slaan in plaats van AEM opslagplaats te gebruiken.

* **Opslag en naverwerking van correspondentiegegevens afkomstig uit een instantie Publish:** AEM workflows voeren de optionele naverwerking van de bijbehorende letterdefinities uit. Deze workflows kunnen de uiteindelijke verwerkte gegevens opslaan in een geschikte externe gegevensopslag.

* **HTML Workspace hosten**: Een verwerkingsinstantie host de voorzijde voor de werkruimte HTML. De werkruimte van HTML verstrekt UI voor bijbehorende taak/groepstoewijzing voor overzicht en goedkeuringsprocessen.

Een instantie van de Verwerking wordt gevormd om op de wijze in werking te stellen van de Auteur omdat:

* Hiermee wordt omgekeerde replicatie van onbewerkte formuliergegevens van een instantie Publish ingeschakeld. De manager van de standaardgegevensopslag vereist de omgekeerde replicatieeigenschap.
* AEM Workflows, de belangrijkste manier om onbewerkte formuliergegevens die afkomstig zijn van een instantie Publish, te verwerken, worden aanbevolen op een systeem dat het karakter van een auteur heeft.

## Steekproef fysieke topologieën voor AEM Forms op JEE {#sample-physical-topologies-for-aem-forms-on-jee}

De hieronder aanbevolen AEM Forms op JEE-topologieën zijn vooral bedoeld voor klanten die hun producten upgraden vanaf LiveCycle of een eerdere versie van AEM Forms op JEE. Adobe beveelt aan AEM Forms op OSGi te gebruiken voor nieuwe installaties. Een nieuwe installatie van AEM Forms op JEE wordt alleen aanbevolen voor het gebruik van de functies Documentbeveiliging en Process Management.

### Topologie voor het gebruiken van de diensten van het document of documentveiligheidsmogelijkheden {#topology-for-using-document-services-or-document-security-capabilities}

AEM Forms-klanten die alleen documentservices of documentbeveiligingsmogelijkheden willen gebruiken, kunnen een topologie hebben die vergelijkbaar is met de hieronder weergegeven topologie. Deze topologie adviseert gebruikend één enkel geval van AEM Forms. Indien nodig kunt u ook een cluster of farm van AEM Forms-servers maken. Deze topologie wordt geadviseerd wanneer de meeste gebruikers programmatically tot mogelijkheden van de server van AEM Forms toegang hebben en de interventie door het gebruikersinterface minimum is. De topologie is nuttig in partijverwerkingsverrichtingen van de documentdiensten. Bijvoorbeeld, gebruikend de outputdienst om honderden niet-editable documenten van PDF dagelijks tot stand te brengen.

Hoewel AEM Forms u in staat stelt alle functies van één server in te stellen en uit te voeren, moet u toch capaciteitsplanning, taakverdeling en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Als u bijvoorbeeld in een omgeving met de service PDF Generator duizenden pagina&#39;s per dag wilt converteren en digitale handtekeningen wilt toevoegen om de toegang tot documenten te beperken, maakt u aparte AEM Forms-servers voor de service PDF Generator en de mogelijkheden voor digitale handtekeningen. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

![basisfuncties](assets/basic-features.png)

### Topologie voor het gebruik van AEM Forms-procesbeheer {#topology-for-using-aem-forms-process-management}

AEM Forms-klanten die AEM Forms-functies voor procesbeheer willen gebruiken, kunnen bijvoorbeeld een topologie hebben die vergelijkbaar is met de hieronder weergegeven topologie. De AEM Forms op JEE-server kan zich in één server- of clusterconfiguratie bevinden.

Als u van LiveCycle ES4 bevordert, spiegelt deze topologie dicht met wat u reeds in LiveCycle behalve de toevoeging van AEM ingebouwde Auteur aan AEM Forms op JEE hebt. Bovendien is er geen verandering in de het groeperen vereisten voor klanten die een verbetering uitvoeren. Als u AEM Forms in een geclusterde omgeving gebruikte, kunt u hetzelfde blijven doen in AEM 6.5 Forms. Voor een nieuwe installatie van AEM Forms of JEE voor het gebruiken van de Werkruimte van de HTML, is het runnen van AEM auteursinstantie ingebouwde aan het milieu JEE een extra vereiste.

De opslag van formuliergegevens is een gegevensopslagruimte van derden die wordt gebruikt voor de opslag van de uiteindelijke verwerkte gegevens van formulieren en interactieve communicatie. Dit is een facultatief element in de topologie. U kunt er ook voor kiezen om een verwerkingsinstantie in te stellen en de opslagplaats ervan te gebruiken als het uiteindelijke systeem van gegevensbestanden, indien nodig.

![topologie_for_using_htmlworkspaceandformsapp](assets/topology_for_usinghtmlworkspaceandformsapp.png)

De topologie wordt aanbevolen voor klanten die AEM Forms op de JEE-server willen gebruiken voor procesbeheermogelijkheden (HTML Workspace) zonder gebruik te maken van naverwerking, adaptieve formulieren, HTML5-formulieren en interactieve communicatiemogelijkheden.

### Topologie voor het gebruik van adaptieve formulieren, HTML5-formulieren, interactieve communicatiemogelijkheden {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

AEM Forms-klanten die AEM Forms-mogelijkheden voor het vastleggen van gegevens willen gebruiken, bijvoorbeeld adaptieve formulieren, HTML5 Forms, PDF forms, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. Deze topologie wordt ook geadviseerd voor het gebruiken van interactieve communicatie mogelijkheden van AEM Forms.

![topologie-voor-gebruiks-vormen-osgi-modules](assets/topology-for-using-forms-osgi-modules.png)

U kunt de volgende veranderingen/aanpassingen aan de bovengenoemde topologie aanbrengen:

* Voor het gebruik van de HTML Workspace- en AEM Forms-app is een AEM auteur of verwerkingsexemplaar vereist. U kunt de AEM auteursinstantie gebruiken ingebouwde aan AEM Forms op server JEE in plaats van vestiging een extra externe AEM auteurserver.
* Een AEM instantie Auteur of van de Verwerking is vereist slechts voor Forms-centric werkschema&#39;s op OSGi, adaptieve vormen, vormenportaal, en interactieve mededeling.
* De interactieve UI van de communicatieAgent wordt over het algemeen in werking gesteld binnen de organisatie. Zo, kunt u een publicatieserver voor Agent UI binnen het privé netwerk houden.
* AEM formulieren op een OSGi-instantie die zijn ingebouwd in AEM Forms op een JEE-server, kunnen ook op Forms gerichte workflows uitvoeren op OSGi en Gecontroleerde mappen.

## Steekproef fysieke topologieën voor het gebruiken van AEM Forms op OSGi {#sample-physical-topologies-for-using-aem-forms-on-osgi}

### Topologie voor gegevensvangst, interactieve mededeling, vorm-Centric Workflow op mogelijkheden OSGi {#topology-for-data-capture-interactive-communication-form-centric-workflow-on-osgi-capabilities}

AEM Forms-klanten die AEM Forms-mogelijkheden voor het vastleggen van gegevens willen gebruiken, bijvoorbeeld adaptieve formulieren, HTML5 Forms, PDF forms, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. Deze topologie wordt ook geadviseerd voor het gebruiken van interactieve mededelingen en Forms-Centric Workflows op vermogen OSGi, bijvoorbeeld, voor het gebruiken van AEM Inbox en de App van AEM Forms voor bedrijfsproceswerkschema&#39;s.

![interactief gebruik-cases-af-cm-osgi-workflow](assets/interactive-use-cases-af-cm-osgi-workflow.png)

### Topologie voor het gebruiken van gelete op omslagmogelijkheden voor off-line partijverwerking {#topology-for-using-watched-folder-capabilities-for-offline-batch-processing}

AEM Forms-klanten die gecontroleerde mappen voor batchverwerking willen gebruiken, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. De topologie toont een gegroepeerd milieu maar u besluit om één enkel geval of een landbouwbedrijf van de servers van AEM Forms afhankelijk van de lading te gebruiken. De gegevensbron van derden is uw eigen systeem-van-verslag. Deze functie fungeert als invoerbron voor Gecontroleerde mappen. De topologie toont ook output in de vorm van een gedrukt dossier. U kunt de uitvoerinhoud ook opslaan in een bestandssysteem, verzenden via e-mail en andere aangepaste methoden gebruiken om uitvoer te verbruiken.

![offline batchverwerking via gecontroleerde mappen](assets/offline-batch-processing-via-watched-folders.png)

### Topologie voor het gebruiken van de mogelijkheden van de documentdiensten voor off-line API-Gebaseerde verwerking {#topology-for-using-document-services-capabilities-for-offline-api-based-processing}

De klanten van AEM Forms die van plan zijn om slechts het vermogen van de documentdiensten te gebruiken kunnen een topologie hebben gelijkend op hieronder getoond. Deze topologie adviseert gebruikend een cluster van AEM Forms op servers OSGi. Deze topologie wordt geadviseerd wanneer de meeste gebruikers programmatically (Gebruikend APIs) toegangsmogelijkheden van de server van AEM Forms en interventie door het gebruikersinterface minimum zijn. De topologie is vrij nuttig in veelvoudige scenario&#39;s van de softwarecliënt. Bijvoorbeeld, veelvoudige cliënten die de dienst van de PDF Generator gebruiken om de documenten van de PDF tot stand te brengen op bestelling.

Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u capaciteitsplanning uitvoeren, taakverdeling toepassen en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Voor een omgeving die bijvoorbeeld gebruikmaakt van de service PDF Generator om duizenden pagina&#39;s per dag om te zetten en meerdere adaptieve formulieren om gegevens vast te leggen, stelt u afzonderlijke AEM Forms-servers in voor de service PDF Generator en de mogelijkheden voor adaptieve formulieren. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

![offline-api-verwerking](assets/offline-api-based-processing.png)
