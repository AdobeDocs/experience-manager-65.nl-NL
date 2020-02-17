---
title: Architectuur en plaatsingstopologieën voor Vormen AEM
seo-title: Architectuur en plaatsingstopologieën voor Vormen AEM
description: Architectuurgegevens voor AEM Forms en aanbevolen topologieën voor nieuwe en bestaande AEM-klanten en klanten die een upgrade uitvoeren van LiveCycle ES4 naar AEM Forms.
seo-description: Architectuurgegevens voor AEM Forms en aanbevolen topologieën voor nieuwe en bestaande AEM-klanten en klanten die een upgrade uitvoeren van LiveCycle ES4 naar AEM Forms.
uuid: 90baa57a-4785-4b49-844c-a44717d3c12d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 0156b5c3-3bef-4213-9ada-c7b6ae96ada4
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Architectuur en plaatsingstopologieën voor Vormen AEM {#architecture-and-deployment-topologies-for-aem-forms}

## Architectuur {#architecture}

AEM Forms is een toepassing die als een AEM-pakket in AEM wordt geïmplementeerd. Het pakket wordt AEM Forms add-on pakket genoemd. Het invoegpakket voor AEM-formulieren bevat zowel services (API-providers), die worden geïmplementeerd in de AEM OSGi-container, als servlets of JSPs (die zowel front-end als REST API-functionaliteit biedt) die worden beheerd door het AEM Sling-framework. Het volgende diagram toont deze opstelling:

![architectuur](assets/architecture.png)

De architectuur voor AEM Forms omvat de volgende componenten:

* **** Core AEM-services: De basisdiensten die AEM aan een opgestelde toepassing verleent. Deze services omvatten een inhoudsopslagruimte die compatibel is met JCR, een OSGI-servicecontainer, een workflowengine, een vertrouwde opslag, een sleutelarchief, enzovoort. Deze services zijn beschikbaar voor de toepassing AEM Forms, maar worden niet geleverd door AEM Forms-pakketten. Deze services vormen een integraal onderdeel van de algemene AEM-stapel en deze services worden door verschillende componenten van AEM Forms gebruikt.
* **** Formulierservices: PDF-documenten maken, samenstellen, distribueren en archiveren, digitale handtekeningen toevoegen om de toegang tot documenten te beperken en streepjescodes voor formulieren te decoderen. Deze diensten zijn openbaar beschikbaar voor consumptie door douanecode die in AEM wordt opgesteld.
* **** Weblaag: JSPs of servlets, die over gemeenschappelijke en vormdiensten worden gebouwd, die de volgende functionaliteit verstrekken:

   * **Voorkant** ontwerpen: Een gebruikersinterface voor het ontwerpen en beheren van formulieren voor het ontwerpen en beheren van formulieren.
   * **Formulieruitvoering en verzendvoorzijde**: Een eindgebruiker die wordt geconfronteerd met interface voor gebruik door de eindgebruikers van de Vormen AEM (bijvoorbeeld, burgers die tot een overheidswebsite toegang hebben). Dit biedt formulieruitvoering (weergaveformulier in een webbrowser) en verzendfuncties.
   * **REST-API&#39;s**: JSPs en servlets voeren een ondergroep vormdiensten voor ver gebruik door HTTP-Gebaseerde cliënten, zoals de vormen mobiele SDK uit.

**** AEM-formulieren op OSGi: Een AEM-formulier in een OSGi-omgeving is het standaard AEM-auteur- of AEM-pakket voor publiceren met AEM Forms dat erop wordt geïmplementeerd. U kunt AEM-formulieren op OSGi uitvoeren in [één serveromgeving, Farm en geclusterde instellingen](/help/sites-deploying/recommended-deploys.md). Clusterinstellingen zijn alleen beschikbaar voor AEM-auteur-instanties.

**** AEM-formulieren op JEE: AEM Forms on JEE is een AEM Forms-server die wordt uitgevoerd op een JEE-stapel. Het bevat invoegpakketten voor AEM-auteur met AEM Forms en extra JEE-mogelijkheden voor AEM Forms die op één JEE-stapel worden geïmplementeerd en op een toepassingsserver worden uitgevoerd. U kunt AEM-formulieren op JEE uitvoeren in instellingen met één server en in gegroepeerde instellingen. AEM Forms on JEE is alleen vereist voor het uitvoeren van documentbeveiliging, procesbeheer en voor LiveCycle-klanten die een upgrade naar AEM Forms uitvoeren. Hier zijn een paar extra scenario&#39;s om Vormen AEM op JEE te gebruiken:

* **** Ondersteuning voor HTML-werkruimte (voor klanten die de HTML-werkruimte gebruiken): Met AEM Forms on JEE kunt u zich één keer aanmelden met Verwerkingsinstanties, bepaalde elementen bedienen die bij Verwerkingsinstanties worden weergegeven en de verzending verwerken van formulieren die in de HTML-werkruimte worden gegenereerd.
* **Geavanceerde verwerking** van aanvullende formulieren/interactieve communicatiegegevens: AEM Forms on JEE kan worden gebruikt voor het extra verwerken van formulier-/interactieve communicatiegegevens (en het opslaan van de resultaten in een geschikte gegevensopslag) in complexe gebruiksgevallen waarin geavanceerde mogelijkheden voor procesbeheer vereist zijn.

AEM Forms on JEE omvat ook de volgende ondersteunende services voor de AEM-componenten:

* **** Geïntegreerd gebruikersbeheer: Hiermee kunnen gebruikers van AEM Forms op JEE worden herkend als AEM-formulieren op OSGi-gebruikers en wordt SSO voor zowel OSGi- als JEE-gebruikers ingeschakeld. Dit is vereist voor scenario&#39;s waarbij Single Sign-On tussen AEM-formulieren op OSGi en AEM Forms op JEE vereist is (bijvoorbeeld HTML-werkruimte).
* **** Asset hosting: AEM Forms on JEE kan middelen (bijvoorbeeld HTML5-formulieren) leveren die op AEM Forms op OSGi worden weergegeven.

In de ontwerpgebruikersinterface van AEM Forms wordt het maken van Document of Record (DOR), PDF-formulieren en HTML5-formulieren niet ondersteund. Dergelijke elementen zijn ontworpen met de zelfstandige Forms Designer-toepassing en worden afzonderlijk geüpload naar AEM Forms Manager. Voor AEM Forms on JEE kunnen formulieren ook worden ontworpen als toepassingselementen (in AEM Forms Workbench) en worden geïmplementeerd in AEM Forms op JEE-server.

AEM-formulieren op OSGi en AEM-formulieren op JEE hebben beide workflowmogelijkheden. U kunt basisworkflows voor diverse taken op de AEM-formulieren op OSGi snel bouwen en implementeren, zonder dat u de volledige mogelijkheden voor Process Management van AEM Forms op JEE hoeft te installeren. Er is wat verschil in de [eigenschappen van vorm-centric werkschema op Vormen AEM op OSGi en de capaciteit van het Beheer van het Proces van Vormen AEM op JEE](/help/forms/using/capabilities-osgi-jee-workflows.md). De ontwikkeling en het beheer van Form-centric werkschema&#39;s op Vormen AEM op OSGi gebruikt de vertrouwde mogelijkheden van het Werkschema AEM en van AEM Inbox.

## Terminologie {#terminologies}

In de volgende afbeelding worden verschillende configuraties van AEM Form-servers en hun componenten weergegeven die worden gebruikt bij een standaardimplementatie van AEM Forms:

![aem_forms_-_recommendedtopologie](assets/aem_forms_-_recommendedtopology.png)

**** Auteur: Een auteurinstantie is een server van Vormen AEM die in de standaardwijze van de de looppas van de Auteur loopt. Het kunnen Vormen AEM op Vormen JEE of AEM op milieu OSGi zijn. Het is bedoeld voor interne gebruikers, formulieren en interactieve communicatieontwerpers, en ontwikkelaars. Het maakt de volgende functies mogelijk:

* **** Formulieren en interactieve communicatie ontwerpen en beheren: Ontwerpers en ontwikkelaars kunnen adaptieve formulieren en interactieve communicatie maken en bewerken, andere soorten extern gemaakte formulieren uploaden, bijvoorbeeld formulieren die zijn gemaakt in Adobe Forms Designer, en deze middelen beheren met de Forms Manager-console.
* **** Publiceren van formulieren en interactieve communicatie: Elementen die op een auteurinstantie worden gehost, kunnen naar een publicatie-instantie worden gepubliceerd om runtimebewerkingen uit te voeren. Bij het publiceren van bedrijfsmiddelen worden de replicatiefuncties van AEM gebruikt. Adobe raadt aan dat op alle exemplaren van de auteur een replicatieagent wordt geconfigureerd voor het handmatig duwen van gepubliceerde formulieren naar verwerkingsinstanties en dat een andere replicatieagent wordt geconfigureerd op verwerkingsinstanties waarbij de trigger *Bij ontvangst* is ingeschakeld om de ontvangen formulieren automatisch te repliceren om instanties te publiceren.

**** Publiceren: Een publicatie-instantie is een AEM Forms-server die wordt uitgevoerd in de standaardmodus Publiceren. Publicatie-instanties zijn bedoeld voor eindgebruikers van formuliertoepassingen, bijvoorbeeld gebruikers die een openbare website openen en formulieren verzenden. Het maakt de volgende functies mogelijk:

* Formulieren renderen en verzenden voor eindgebruikers.
* Het vervoer van ruwe ingediende formuliergegevens naar verwerkingsinstanties voor verdere verwerking en opslag in het definitieve registratiesysteem. De standaardimplementatie die in Vormen AEM wordt verstrekt bereikt dit gebruikend de omgekeerde replicatiemogelijkheden van AEM. Er is ook een alternatieve implementatie beschikbaar voor het rechtstreeks verplaatsen van formuliergegevens naar verwerkingsservers in plaats van deze eerst lokaal op te slaan (de laatste is een noodzakelijke voorwaarde voor het activeren van reverse-replicatie). Klanten die zich zorgen maken over de opslag van mogelijk vertrouwelijke gegevens over publicatieinstanties kunnen zich aanmelden voor deze [alternatieve implementatie](/help/forms/using/configuring-draft-submission-storage.md), aangezien verwerkingsinstanties doorgaans in een veiligere zone liggen.
* Interactieve communicatie en letters renderen en verzenden: Bij publicatie-instanties wordt een interactieve communicatie en brief weergegeven en de bijbehorende gegevens worden naar verwerkingsinstanties verzonden voor opslag en naverwerking. De gegevens kunnen lokaal op een publicatie-instantie worden opgeslagen en later worden gerepliceerd naar een verwerkingsinstantie (de standaardoptie), of rechtstreeks naar een verwerkingsinstantie worden geduwd zonder op de publicatie-instantie op te slaan. De laatstgenoemde implementatie is nuttig voor veiligheid-bewuste klanten.

**** Verwerking: Een exemplaar van AEM-formulieren dat wordt uitgevoerd in de uitvoeringsmodus Auteur zonder dat gebruikers zijn toegewezen aan de groep met formulierbeheer. U kunt AEM- Vormen op Vormen JEE of AEM op OSGi als verwerkingsgeval opstellen. De gebruikers worden niet toegewezen om ervoor te zorgen dat de activiteiten van de creatie en het beheer van de vorm niet op de instantie van de Verwerking worden uitgevoerd en slechts op de instantie van de Auteur voorkomen. Een verwerkingsinstantie schakelt de volgende functies in:

* **** Verwerking van onbewerkte formuliergegevens die afkomstig zijn van een instantie Publish: Dit wordt voornamelijk bereikt op een verwerkingsinstantie via AEM-workflows die worden geactiveerd wanneer de gegevens aankomen. De workflows kunnen gebruikmaken van de stap Formuliergegevensmodel die buiten het vak wordt weergegeven om de gegevens of het document naar een geschikte gegevensopslag te archiveren.
* **Beveiligde opslag van formuliergegevens**: Verwerking biedt een opslagplaats achter de firewall voor onbewerkte formuliergegevens die van gebruikers is geïsoleerd. Geen van de formulierontwerpers op de instantie Auteur en eindgebruikers op de instantie Publiceren hebben toegang tot deze opslagplaats.

   >[!NOTE]
   >
   > Adobe raadt u aan een gegevensopslagruimte van derden te gebruiken om de uiteindelijke verwerkte gegevens op te slaan in plaats van AEM-opslagruimte te gebruiken.

* **** Opslag en naverwerking van correspondentiegegevens afkomstig uit een instantie Publish: AEM-workflows voeren de optionele naverwerking van de bijbehorende letterdefinities uit. Deze workflows kunnen de uiteindelijke verwerkte gegevens opslaan in een geschikte externe gegevensopslag.

* **HTML-werkruimte hosten**: Een verwerkingsinstantie host de voorzijde voor HTML Workspace. De werkruimte van HTML verstrekt UI voor bijbehorende taak/groepstoewijzing voor overzicht en goedkeuringsprocessen.

Een instantie van de Verwerking wordt gevormd om op de wijze in werking te stellen van de Auteur omdat:

* Hiermee wordt omgekeerde replicatie van onbewerkte formuliergegevens van een instantie Publish ingeschakeld. De manager van de standaardgegevensopslag vereist de omgekeerde replicatieeigenschap.
* AEM Workflows, de belangrijkste manier om onbewerkte formuliergegevens die afkomstig zijn van een instantie Publish, te verwerken, worden aanbevolen voor gebruik op een auteurssysteem.

## Steekproef fysieke topologieën voor Vormen AEM op JEE {#sample-physical-topologies-for-aem-forms-on-jee}

De AEM-formulieren op JEE-topologieën die hieronder worden aanbevolen, zijn vooral bedoeld voor klanten die een upgrade uitvoeren van LiveCycle of een eerdere versie van AEM Forms op JEE. Adobe raadt u aan AEM Forms op OSGi te gebruiken voor nieuwe installaties. Een nieuwe installatie van AEM Forms op JEE wordt alleen aanbevolen voor het gebruik van de mogelijkheden voor documentbeveiliging en procesbeheer.

### Topologie voor het gebruiken van de diensten van het document of documentveiligheidsmogelijkheden {#topology-for-using-document-services-or-document-security-capabilities}

AEM vormt klanten die van plan zijn om slechts de documentdiensten of de mogelijkheden van de documentveiligheid te gebruiken kunnen een topologie hebben gelijkend op hieronder getoond. Deze topologie adviseert gebruikend één enkel geval van Vormen AEM. U kunt een cluster of een landbouwbedrijf van de servers van Vormen AEM, indien nodig ook tot stand brengen. Deze topologie wordt geadviseerd wanneer de meeste gebruikers programmatically tot mogelijkheden van de server van de Vormen van AEM en interventie door het gebruikersinterface minimum toegang hebben. De topologie is nuttig in partijverwerkingsverrichtingen van de documentdiensten. Met de uitvoerservice kunt u bijvoorbeeld dagelijks honderden niet-bewerkbare PDF-documenten maken.

Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u toch capaciteitsplanning, taakverdeling en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Als u bijvoorbeeld in een omgeving met de service PDF genereren duizenden pagina&#39;s per dag wilt converteren en digitale handtekeningen wilt toevoegen om de toegang tot documenten te beperken, stelt u afzonderlijke AEM Forms-servers in voor de service PDF Generator en de mogelijkheden voor digitale handtekeningen. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

![basisfuncties](assets/basic-features.png)

### Topologie voor het gebruik van AEM Forms Process Management {#topology-for-using-aem-forms-process-management}

Klanten met AEM Forms die de functies voor procesbeheer van AEM Forms willen gebruiken, kunnen in de HTML-werkruimte bijvoorbeeld een topologie hebben die vergelijkbaar is met de hieronder weergegeven topologie. De AEM-formulieren op de JEE-server kunnen zich in één server- of clusterconfiguratie bevinden.

Als u een upgrade uitvoert vanuit LiveCycle ES4, weerspiegelt deze topologie nauw de functies die u al hebt in LiveCycle, met uitzondering van de toevoeging van ingebouwde AEM-auteur aan AEM Forms in JEE. Bovendien is er geen verandering in de het groeperen vereisten voor klanten die een verbetering uitvoeren. Als u AEM Forms in een gegroepeerde omgeving gebruikte, kunt u met hetzelfde doorgaan in AEM 6.5 Forms. Voor een nieuwe installatie van AEM-vormen van JEE voor het gebruik van HTML Workspace, is het uitvoeren van de ingebouwde AEM-auteurinstantie in de JEE-omgeving een extra vereiste.

De opslag van formuliergegevens is een gegevensopslagruimte van derden die wordt gebruikt voor de opslag van de uiteindelijke verwerkte gegevens van formulieren en interactieve communicatie. Dit is een facultatief element in de topologie. U kunt er ook voor kiezen om een verwerkingsinstantie in te stellen en de opslagplaats ervan te gebruiken als het uiteindelijke systeem van gegevensbestanden, indien nodig.

![topologie_for_using_htmlworkspaceandformsapp](assets/topology_for_usinghtmlworkspaceandformsapp.png)

De topologie wordt aanbevolen voor klanten die AEM Forms op JEE-server willen gebruiken voor procesbeheermogelijkheden (HTML Workspace) zonder gebruik te maken van naverwerking, adaptieve formulieren, HTML5-formulieren en interactieve communicatiemogelijkheden.

### Topologie voor het gebruik van adaptieve formulieren, HTML5-formulieren, interactieve communicatiemogelijkheden {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

Klanten met AEM Forms die voornemens zijn om AEM Forms te gebruiken, kunnen bijvoorbeeld adaptieve formulieren, HTML5 Forms en PDF Forms een soortgelijke topologie hebben als hieronder wordt weergegeven. Deze topologie wordt ook aanbevolen voor het gebruik van interactieve communicatiemogelijkheden van AEM Forms.

![topologie-voor-gebruiks-vormen-osgi-modules](assets/topology-for-using-forms-osgi-modules.png)

U kunt de volgende veranderingen/aanpassingen aan de bovengenoemde topologie aanbrengen:

* Voor het gebruik van de app HTML Workspace en AEM Forms is een AEM-auteur of verwerkingsexemplaar vereist. U kunt de ingebouwde AEM-auteurinstantie gebruiken voor AEM Forms op JEE-server in plaats van een extra externe AEM-auteurserver op te zetten.
* Een AEM-auteur of -verwerkingsexemplaar is alleen vereist voor Forms-centric-workflows op OSGi, adaptieve formulieren, Formulierportal en interactieve communicatie.
* De interactieve UI van de communicatieAgent wordt over het algemeen in werking gesteld binnen de organisatie. Zo, kunt u een publicatieserver voor Agent UI binnen het privé netwerk houden.
* AEM-formulieren op OSGi-instanties die zijn ingebouwd in AEM Forms op JEE-server, kunnen ook Forms-centric workflows uitvoeren op OSGi en Gecontroleerde mappen.

## Steekproef fysieke topologieën voor het gebruiken van Vormen AEM op OSGi {#sample-physical-topologies-for-using-aem-forms-on-osgi}

### Topologie voor gegevensvangst, interactieve mededeling, vorm-Centric Workflow op mogelijkheden OSGi {#topology-for-data-capture-interactive-communication-form-centric-workflow-on-osgi-capabilities}

Klanten met AEM Forms die voornemens zijn om AEM Forms te gebruiken, kunnen bijvoorbeeld adaptieve formulieren, HTML5 Forms en PDF Forms een soortgelijke topologie hebben als hieronder wordt weergegeven. Deze topologie wordt ook geadviseerd voor het gebruiken van interactieve mededelingen en Forms-Centric Workflows op vermogen OSGi, bijvoorbeeld, voor het gebruiken van AEM Inbox en AEM vormt App voor bedrijfsproceswerkschema&#39;s.

![interactief gebruik-cases-af-cm-osgi-workflow](assets/interactive-use-cases-af-cm-osgi-workflow.png)

### Topologie voor het gebruiken van gelete op omslagmogelijkheden voor off-line partijverwerking {#topology-for-using-watched-folder-capabilities-for-offline-batch-processing}

Klanten met AEM Forms die gecontroleerde mappen voor batchverwerking willen gebruiken, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. De topologie toont een gegroepeerd milieu maar u besluit om één enkele instantie of een landbouwbedrijf van de servers van Vormen AEM afhankelijk van de lading te gebruiken. De gegevensbron van derden is uw eigen systeem-van-verslag. Deze functie fungeert als invoerbron voor Gecontroleerde mappen. De topologie toont ook output in de vorm van een gedrukt dossier. U kunt de uitvoerinhoud ook opslaan in een bestandssysteem, verzenden via e-mail en andere aangepaste methoden gebruiken om uitvoer te verbruiken.

![offline batchverwerking via gecontroleerde mappen](assets/offline-batch-processing-via-watched-folders.png)

### Topologie voor het gebruiken van de mogelijkheden van de documentdiensten voor off-line API-Gebaseerde verwerking {#topology-for-using-document-services-capabilities-for-offline-api-based-processing}

De klanten van de Vormen AEM die van plan zijn om slechts het vermogen van de documentdiensten te gebruiken kunnen een topologie gelijkend op hieronder getoond hebben. Deze topologie adviseert gebruikend een cluster van Vormen AEM op servers OSGi. Deze topologie wordt geadviseerd wanneer de meeste gebruikers programmatically (Gebruikend APIs) toegangsmogelijkheden van de server van Vormen AEM en interventie door het gebruikersinterface minimum zijn. De topologie is vrij nuttig in veelvoudige scenario&#39;s van de softwarecliënt. Meerdere clients maken bijvoorbeeld PDF Generator-service om PDF-documenten op aanvraag te maken.

Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u capaciteitsplanning uitvoeren, taakverdeling toepassen en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Als u bijvoorbeeld in een omgeving met de service PDF Generator duizenden pagina&#39;s per dag converteert en meerdere adaptieve formulieren gebruikt om gegevens vast te leggen, stelt u afzonderlijke AEM Forms-servers in voor de service PDF Generator en de mogelijkheden voor adaptieve formulieren. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

![offline-api-verwerking](assets/offline-api-based-processing.png)

