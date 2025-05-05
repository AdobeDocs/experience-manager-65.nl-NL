---
title: Forms-centric workflow op OSGi
description: AEM Forms Workflow gebruiken om revisie en goedkeuringen te automatiseren en snel samen te stellen, om documentservices te starten
topic-tags: publish, document_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
exl-id: c3e5f8fc-d2b9-4f76-9a3d-4bc5733f5a5c
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '3579'
ht-degree: 0%

---

# Forms-centric workflow op OSGi{#forms-centric-workflow-on-osgi}

![ held-beeld ](do-not-localize/header.png)

Ondernemingen verzamelen gegevens uit honderden en duizenden formulieren, verschillende back-endsystemen en online of offline gegevensbronnen. Zij hebben ook een dynamische reeks gebruikers om besluiten over de gegevens te nemen, die herhalende herbeoordeling en goedkeuringsprocessen impliceren.

Samen met overzicht en goedkeuringswerkschema&#39;s voor intern en extern publiek, hebben de grote organisaties en de ondernemingen herhalende taken. Bijvoorbeeld het omzetten van een PDF-document in een andere indeling. Wanneer manueel gedaan, nemen deze taken veel tijd en middelen op. Ondernemingen hebben ook wettelijke vereisten om een document digitaal te ondertekenen en formuliergegevens te archiveren voor later gebruik in vooraf gedefinieerde indelingen.

## Inleiding tot Forms-centric workflow op OSGi {#introduction-to-forms-centric-workflow-on-osgi}

U kunt AEM Workflows gebruiken om snel adaptieve workflows op basis van formulieren te maken. Deze workflows kunnen worden gebruikt voor revisie en goedkeuringen, bedrijfsprocesstromen, het starten van documentservices, integratie met de Adobe Sign-handtekeningworkflow en vergelijkbare bewerkingen. Bijvoorbeeld de verwerking van creditcardtoepassingen, de werkstromen van het werknemersverlaten goedkeurings, die een vorm als document van de PDF bewaren. Bovendien kunnen deze workflows binnen een organisatie of via een netwerkfirewall worden gebruikt.

Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi, zonder het moeten het volledige vermogen van het Beheer van het Proces op de stapel van JEE installeren. Voor de ontwikkeling en het beheer van workflows wordt gebruikgemaakt van de vertrouwde AEM en AEM Inbox-mogelijkheden. De werkstromen vormen de basis van het automatiseren van echte bedrijfsprocessen die veelvoudige softwaresystemen, netwerken, afdelingen, en zelfs organisaties omspannen.

Zodra opstelling, kunnen deze werkschema&#39;s manueel worden teweeggebracht om een bepaald proces te voltooien of programmatically in werking te stellen wanneer de gebruikers een vorm of [ brievenbeheer ](/help/forms/using/cm-overview.md) brief voorleggen. Met deze verbeterde AEM workflowmogelijkheden biedt AEM Forms twee aparte, maar toch vergelijkbare mogelijkheden. Als onderdeel van uw implementatiestrategie moet u bepalen welke strategie voor u werkt. Zie a [ vergelijking ](capabilities-osgi-jee-workflows.md) van de Forms-centric AEM Workflows op OSGi en het Beheer van het Proces op JEE. Bovendien voor de plaatsingstopologie zie, [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md).

Forms-centric werkschema op OSGi breidt [ AEM Inbox ](/help/sites-authoring/inbox.md) uit en verstrekt extra componenten (stappen) voor AEM redacteur van het Werkschema om steun voor AEM Forms-centric werkschema&#39;s toe te voegen. Uitgebreide AEM Inbox heeft functionaliteit gelijkend op [ Workspace van AEM Forms ](introduction-html-workspace.md). Samen met het beheren van mens-centric werkschema&#39;s (Goedkeuring, Overzicht, etc.), kunt u AEM werkschema&#39;s gebruiken om [&#128279;](/help/sites-developing/workflows-step-ref.md) verwante verrichtingen van de documentdiensten van 0&rbrace; te automatiseren (bijvoorbeeld, produceer PDF) en elektronisch het ondertekenen (Adobe Sign) documenten.

Alle AEM Forms-workflowstappen ondersteunen het gebruik van variabelen. Met variabelen kunnen workflowstappen metagegevens tijdens runtime bevatten en doorgeven. U kunt verschillende typen variabelen maken om verschillende typen gegevens op te slaan. U kunt ook variabele verzamelingen (arrays) maken om meerdere instanties van verwante, met hetzelfde type getypte gegevens op te slaan. Typisch, gebruikt u een variabele of een inzameling van variabelen wanneer u een besluit moet nemen dat op de waarde wordt gebaseerd die het houdt of informatie opslaat die u later in een proces nodig hebt. Voor meer informatie bij het gebruiken van variabelen in deze Forms-centric werkschemacomponenten (stappen), zie [ Forms-centric werkschema op OSGi - de Verwijzing van de Stap ](../../forms/using/aem-forms-workflow-step-reference.md). Voor informatie bij het creëren van en het beheren van variabelen, zie [ Variabelen in AEM werkschema&#39;s ](../../forms/using/variable-in-aem-workflows.md).

Het volgende diagram toont de procedure van begin tot eind om, een Forms-centric werkschema op OSGi tot stand te brengen in werking te stellen en te controleren.

![ inleiding-aan-naam-vormen-werkschema ](assets/introduction-to-aem-forms-workflow.jpg)

## Voordat u begint {#before-you-start}

* Een werkschema is een vertegenwoordiging van een echt bedrijfsproces. Houd uw real-world bedrijfsproces en lijst van de deelnemers van het bedrijfsproces klaar. Houd ook de hulplijnen (adaptieve formulieren, PDF-documenten en meer) gereed voordat u een workflow gaat maken.
* Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en Help de voortgang van de workflow te melden. Verdeel uw bedrijfsproces in logische stadia.
* U kunt de taakstap van AEM Workflows configureren om e-mailmeldingen te verzenden naar de gebruikers of de toewijzingen. Zo, [ laat e-mailberichten ](#configure-email-service) toe.
* Een workflow kan ook gebruikmaken van een Adobe voor digitale handtekeningen. Als u van plan bent om Adobe Sign in een werkschema te gebruiken, vormt [ Adobe Sign voor AEM Forms ](../../forms/using/adobe-sign-integration-adaptive-forms.md) alvorens het in een werkschema te gebruiken.

## Een workflowmodel maken {#create-a-workflow-model}

Een workflowmodel bestaat uit logica en stroom van een bedrijfsproces. Het bestaat uit een reeks stappen. Deze stappen zijn AEM componenten. U kunt workflowstappen uitbreiden met parameters en scripts om desgewenst meer functionaliteit en controle te bieden. AEM Forms bevat een aantal stappen naast AEM stappen uit het vak. Voor een gedetailleerde lijst van AEM en de stappen van AEM Forms, zie [ AEM de Verwijzing van de Stap van het Werkschema ](/help/sites-developing/workflows-step-ref.md) en [ Forms-centric werkschema op OSGi - de Verwijzing van de Stap ](../../forms/using/aem-forms-workflow.md).

AEM biedt een intuïtieve gebruikersinterface voor het maken van een workflowmodel met behulp van de meegeleverde workflowstappen. Voor geleidelijke instructies om een werkschemamodel tot stand te brengen, zie [ Creërend de Modellen van het Werkschema ](/help/sites-developing/workflows-models.md). In het volgende voorbeeld worden stapsgewijze instructies gegeven voor het maken van een workflowmodel voor een goedkeurings- en revisiewerkstroom:

>[!NOTE]
>
>Als u een workflowmodel wilt maken of bewerken, moet u lid zijn van de groep met workfloweditors.

### Een model maken voor een goedkeurings- en revisiewerkstroom {#create-a-model-for-an-approval-and-review-workflow}

Goedkeuring- en revisiewerkstroom is bedoeld voor de taken waarvoor menselijke tussenkomst vereist is om beslissingen te nemen. In het volgende voorbeeld wordt een workflowmodel gemaakt voor een hypotheekleningaanvraag die moet worden ingevuld door een bankagent voor het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde aanvraag met Adobe Sign naar de aanvrager van elektronische handtekeningen gezonden.

Het voorbeeld is beschikbaar als een hieronder bijgevoegd pakket. Importeer en installeer het voorbeeld met pakketbeheer. U kunt ook de volgende stappen uitvoeren om handmatig het workflowmodel voor de toepassing te maken:

In het voorbeeld wordt een workflowmodel gemaakt voor een hypotheektoepassing die moet worden ingevuld door een bankagent op het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde toepassing met Adobe Sign naar de klant verzonden voor elektronische handtekeningen. U kunt het voorbeeld importeren en installeren met pakketbeheer.

[Bestand ophalen](assets/example-mortgage-loan-application.zip)

1. Open de console Workflowmodellen. De standaard-URL is `https://[server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Selecteer **creeer**, dan **creeer Model**. Het dialoogvenster Workflowmodel toevoegen wordt weergegeven.
1. Ga de **Titel** en **Naam** (facultatief) in. Bijvoorbeeld een hypotheekaanvraag. Selecteer **Gereed**.
1. Selecteer het pas gecreëerde werkschemamodel en selecteer **uitgeven**. Nu kunt u workflowstappen toevoegen om bedrijfslogica te maken. Wanneer u voor het eerst een workflowmodel maakt, bevat dit:

   * De stappen: Start en Einde stroom. Deze stappen vertegenwoordigen het begin en het einde van de workflow. Deze stappen zijn vereist en kunnen niet worden bewerkt of verwijderd.
   * Een stap van de voorbeelddeelnemer genoemd Stap 1. Deze stap wordt gevormd om een het werkpunt aan de admin gebruiker toe te wijzen. Verwijder deze stap.

1. E-mailmeldingen inschakelen. U kunt een op Forms gerichte workflow op OSGi configureren om e-mailmeldingen naar de gebruikers of gebruikers te sturen. Voer de volgende configuraties uit om e-mailmeldingen in te schakelen:

   1. Ga naar AEM configuratiemanager op `https://[server]:[port]/system/console/configMgr` .
   1. Open de **[!UICONTROL Day CQ Mail Service]** -configuratie. Geef een waarde op voor de velden **[!UICONTROL SMTP server host name]** , **[!UICONTROL SMTP server port,]** en **[!UICONTROL "From" address]** . Klik op **[!UICONTROL Save]**.
   1. Open de **[!UICONTROL Day CQ Link Externalizer]** -configuratie. Geef in het veld **[!UICONTROL Domains]** het werkelijke hostnaam/IP-adres en poortnummer op voor lokale instanties, auteurs en publicatieinstanties. Klik op **[!UICONTROL Save]**.

1. Workflowfasen maken. Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en de voortgang van de workflow rapporteren.

   Om een stadium te bepalen, selecteer het ![ info-circle ](assets/info-circle.png) pictogram om de eigenschappen van het werkschemamodel te openen, open het **lusje van Staven**, voeg stadia voor het werkschemamodel toe, en selecteer **sparen &amp; dicht**. Voor het voorbeeld van de hypotheektoepassing kunt u fasen maken: aanvraag voor een lening, status van de leningaanvraag, te ondertekenen documenten en ondertekend leningdocument.

1. De belemmering-en-daling **wijst de stappen van de Taak** browser aan het werkschemamodel toe. Maak van het de eerste stap van het model.

   De taakcomponent toewijzen wijst de taak, die door workflow wordt gemaakt, toe aan een gebruiker of groep. Naast het toewijzen van de taak kunt u de component gebruiken om een adaptief formulier of een niet-interactieve PDF voor de taak op te geven. Het adaptieve formulier is vereist om invoer van gebruikers te accepteren en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie dienen.

   U kunt de stap ook gebruiken om het gedrag van de taak te controleren. Als u bijvoorbeeld een automatisch recorddocument maakt, wijst u de taak toe aan een bepaalde gebruiker of groep, het pad van de verzonden gegevens, het pad van de gegevens die vooraf moeten worden ingevuld en de standaardhandelingen. Voor gedetailleerde informatie over de opties van de taakstap toewijzen, zie [ Forms-centric werkschema op OSGi - het document van de Verwijzing van de Stap ](../../forms/using/aem-forms-workflow.md).

   ![ werkschema-redacteur ](assets/workflow-editor.png)

   In het voorbeeld van de hypotheektoepassing configureert u de taakstap zodanig dat een alleen-lezen adaptief formulier wordt gebruikt en het PDF-document wordt weergegeven wanneer de taak is voltooid. Selecteer ook voor gebruikersgroep die de aanvraag voor een lening mag goedkeuren. Op het **lusje van Acties**, maak **&#x200B;**&#x200B;optie voor voorleggen onbruikbaar. Creeer een **actiontaken** variabele van het gegevenstype van het Koord en specificeer de variabele als **Variabele van de Route**. Bijvoorbeeld actionTake. Voeg ook de routes Goedkeuren en Afwijzen toe. De routes worden getoond als afzonderlijke acties (knopen) in AEM Inbox. De werkstroom selecteert een vertakking op basis van de actie (knoop) een gebruiker tikt.

   U kunt het voorbeeldpakket importeren, dat u kunt downloaden vanaf het begin van de sectie, voor de volledige set waarden van alle velden van de taakstap toewijzen die is geconfigureerd, bijvoorbeeld hypotheektoepassing.

1. Sleep de component OR Splitsen van de stapbrowser naar het workflowmodel. Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

   U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

   Gebruik de uitdrukkingsredacteur om het verpletteren van uitdrukkingen voor Tak 1 en Tak 2 tot stand te brengen. Deze verpletterende uitdrukkingen helpen een tak kiezen die op de gebruikersactie in AEM Inbox wordt gebaseerd.

   **Verpletterend uitdrukking voor Tak 1**

   Wanneer een gebruiker **tikt goedkeuren** in AEM Inbox, Tak 1 wordt geactiveerd.

   ![ OF Gesplitst voorbeeld ](assets/orsplit_branch1_active_new.png)

   **Verpletterend uitdrukking voor Tak 2**

   Wanneer een gebruiker **Afwijzen** in AEM Inbox tikt, wordt Tak 2 geactiveerd.

   ![ OF Gesplitst voorbeeld ](assets/orsplit_branch2_active_new.png)

   Voor informatie bij het creëren van het verpletteren van uitdrukkingen die variabelen gebruiken, zie [ Variabelen in de werkschema&#39;s van AEM Forms ](../../forms/using/variable-in-aem-workflows.md).

1. Voeg andere workflowstappen toe om de bedrijfslogica te bouwen.

   Voor het hypotheekvoorbeeld voegt u een document met een record te genereren, twee taakstappen toe en een stap in het ondertekeningsdocument aan vertakking 1 van het model, zoals in de onderstaande afbeelding wordt weergegeven. Één wijst taakstap toe moet **tonen en verzenden om ondertekende leningsdocumenten aan de aanvrager** te zijn en een andere taakcomponent toewijzen is **om ondertekende documenten** te tonen. Voeg ook een taakcomponent toe aan vertakking 2. Deze wordt geactiveerd wanneer een gebruiker op Afwijzen in AEM Postvak IN tikt.

   Voor de volledige set waarden van alle velden van de taakstappen toewijzen, documentstap en stap voor ondertekeningsdocumenten die zijn geconfigureerd, bijvoorbeeld hypotheektoepassing, importeert u het voorbeeldpakket dat beschikbaar is voor downloaden in het begin van deze sectie.

   Het workflowmodel is gereed. U kunt de workflow op verschillende manieren starten. Voor details, zie [ Lancering een Forms-centric werkschema op OSGi ](#launch).

   ![ werkschema-redacteur-hypotheek ](assets/workflow-editor-mortgage.png)

## Een Forms-centric Workflow-toepassing maken {#create-a-forms-centric-workflow-application}

De toepassing is het adaptieve formulier dat aan de workflow is gekoppeld. Wanneer een toepassing via Inbox wordt verzonden, wordt de bijbehorende workflow gestart. Als u een Forms-workflow als toepassing beschikbaar wilt maken in AEM Inbox en AEM Forms App, gaat u als volgt te werk om een workflowtoepassing te maken:

>[!NOTE]
>
>U moet lid van de fd-beheerder groep zijn om werkschematoepassingen te kunnen tot stand brengen en beheren.

1. Op uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Manage Workflow Application]** en tikken **[!UICONTROL Create]**.
1. In het Create venster van de Toepassing van het Werkschema, verstrek input voor de volgende gebieden, en tikt **&#x200B;**&#x200B;creëren. Er wordt een nieuwe toepassing gemaakt en deze wordt weergegeven in het scherm Workflowtoepassingen.

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>De titel is zichtbaar in AEM Postvak IN en helpt gebruikers een toepassing te kiezen. Houd het beschrijvend. Bijvoorbeeld, sparen de Toepassing van de Rekening die.<br /> opent </td>
  </tr>
  <tr>
   <td>Naam </td>
   <td>Geef de naam van de toepassing op. Alle andere tekens dan alfabeten, getallen, koppeltekens en onderstrepingstekens worden vervangen door afbreekstreepjes. </td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>De beschrijving is zichtbaar in AEM Postvak IN. Geef in de beschrijvingsvelden gedetailleerde informatie over de toepassing. Bijvoorbeeld, Doel van de toepassing.<br /> </td>
  </tr>
  <tr>
   <td>Adaptief formulier</td>
   <td><p>Geef het pad van een adaptief formulier op. Wanneer een gebruiker een toepassing start, wordt het opgegeven adaptieve formulier weergegeven.</p> <p><strong> Nota </strong>: De toepassingen van het werkschema steunen geen vormen en documenten van de PDF die langer zijn dan één pagina of vereisen het scrollen op Apple iPad. Wanneer een toepassing wordt geopend op Apple iPad en het adaptieve formulier of het PDF-document langer is dan een pagina, gaan de formuliervelden en inhoud van de tweede pagina verloren.</p> </td>
  </tr>
  <tr>
   <td>Toegangsgroep</td>
   <td><p>Selecteer een groep. De toepassing is alleen zichtbaar in AEM Postvak IN voor de leden van de geselecteerde groep. De optie van de toegangsgroep maakt alle groepen van de werkschema-gebruikers groep beschikbaar voor selectie. </p> <br /> </td>
  </tr>
  <tr>
   <td>Prefill-service</td>
   <td>Selecteer de a <a href="../../forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank"> prefill dienst </a> voor de adaptieve vorm.<br /> </td>
  </tr>
  <tr>
   <td>Workflowmodel</td>
   <td>Selecteer het model van het a <a href="../../forms/using/aem-forms-workflow.md#create-a-workflow-model"> werkschema </a> voor de toepassing. Een workflowmodel bestaat uit logica en stroom van het bedrijfsproces. </td>
  </tr>
  <tr>
   <td>Pad gegevensbestand</td>
   <td>Geef het pad op van het gegevensbestand in de crx-gegevensopslagruimte. Het pad is relatief ten opzichte van de aangepaste lading van het formulier en bevat de naam van het gegevensbestand. Neem altijd de volledige naam van het bestand op, inclusief de extensie, indien van toepassing. Bijvoorbeeld [payload]/data.xml. </td>
  </tr>
  <tr>
   <td>Pad bijlage</td>
   <td>Geef het pad van de map voor bijlagen op in de crx-repository. Het pad naar de bijlage is relatief ten opzichte van de laadlocatie. Bijvoorbeeld [payload]/data.xml. </td>
  </tr>
  <tr>
   <td>Document van Recordpad</td>
   <td>Geef het pad op van het document of recordbestand in de crx-gegevensopslagruimte. Het pad is relatief ten opzichte van de aangepaste locatie van de formulierlading. Neem altijd de volledige naam van het bestand op, inclusief de extensie, indien van toepassing. Bijvoorbeeld [payload]/DOR/creditcard.pdf.</td>
  </tr>
 </tbody>
</table>

## Een Forms-centric workflow starten op OSGi {#launch}

U kunt een Forms-centric workflow starten of activeren door:

* [Een toepassing verzenden vanuit AEM Postvak In](#inbox)
* [Een toepassing verzenden vanuit een AEM Forms-toepassing](#afa)

* [Een adaptief formulier indienen](#af)
* [Gecontroleerde map gebruiken](#watched)

* [Een interactieve communicatie of een brief indienen](#letter)

### Een toepassing verzenden vanuit AEM Postvak In {#inbox}

De workflowtoepassing die u hebt gemaakt, is beschikbaar als een toepassing in Inbox. Gebruikers die lid zijn van een groep gebruikers in de workflow, kunnen de toepassing die de bijbehorende workflow activeert, invullen en verzenden. Voor informatie over het gebruiken van AEM Inbox om toepassingen voor te leggen en taken te beheren, zie [ de toepassingen en de taken van Forms in AEM Inbox ](../../forms/using/manage-applications-inbox.md) leiden.

### Een toepassing verzenden vanuit een AEM Forms-toepassing {#afa}

De AEM Forms-toepassing wordt gesynchroniseerd met een AEM Forms-server en u kunt de formuliergegevens, taken, workflowtoepassingen en opgeslagen informatie (concepten/sjablonen) in uw account wijzigen. Voor meer informatie, zie [ app van AEM Forms ](/help/forms/using/aem-forms-app.md) en verwante artikelen.

### Een adaptief formulier indienen {#af}

U kunt de verzendacties van een adaptief formulier zo configureren dat een workflow wordt gestart bij het verzenden van het adaptieve formulier. De adaptieve vormen verstrekken **aanhalen een AEM van het Werkschema** actie om een werkschema op voorlegging van een adaptieve vorm te beginnen voorlegt. Voor gedetailleerde informatie over voorlegt actie, zie [ Vormend de Submit actie ](../../forms/using/configuring-submit-actions.md). Als u een adaptief formulier wilt verzenden via de AEM Forms-app, schakelt u Sync with AEM Forms App in de adaptieve formuliereigenschappen in.

U kunt een adaptief formulier configureren voor synchronisatie, verzending en activering van een workflow vanuit de AEM Forms-app. Voor details, zie [ werkend met een vorm ](/help/forms/using/working-with-form.md).

### Een controlemap gebruiken {#watched}

Een beheerder (een lid van de groep van fd-beheerders) kan een netwerkomslag vormen om een pre-gevormde werkschema in werking te stellen wanneer een gebruiker een dossier (zoals een dossier van PDF) in de omslag plaatst. Nadat de workflow is voltooid, kan het resulterende bestand worden opgeslagen in een opgegeven uitvoermap. Zulk een omslag is gekend als [ Gecontroleerde Omslag ](../../forms/using/watched-folder-in-aem-forms.md). Voer de volgende procedure uit om een gecontroleerde omslag te vormen om een werkschema te lanceren:

1. Op uw AEM auteursinstantie, ga ![ hulpmiddelen-1 ](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Configure Watched Folder]**. Er wordt een lijst met al geconfigureerde gecontroleerde mappen weergegeven.
1. Selecteer **[!UICONTROL New]**. Er wordt een lijst met velden weergegeven. Geef een waarde op voor de volgende velden om een gecontroleerde map voor een workflow te configureren:

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td><span class="uicontrol">Naam</code></td>
   <td>Geef de naam van de gecontroleerde map op. Dit veld ondersteunt alleen alfanumeriek.</td>
  </tr>
  <tr>
   <td><span class="uicontrol">Pad</code></td>
   <td>Geef de fysieke locatie van de gecontroleerde map op. In een gegroepeerde milieu, gebruik een gedeelde netwerkomslag die van AEM clusterknoop toegankelijk is.</td>
  </tr>
  <tr>
   <td><span class="uicontrol">Bestanden verwerken met</code></td>
   <td>Selecteer het <span class="uicontrol"> Werkschema </code>-optie. </td>
  </tr>
  <tr>
   <td><span class="uicontrol">Workflowmodel</code></td>
   <td>Selecteer een workflowmodel.<br /> </td>
  </tr>
  <tr>
   <td><span class="uicontrol">Uitvoerbestandspatroon</code></td>
   <td>Geef de mapstructuur op voor uitvoerbestanden en -mappen. U kunt a <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank"> patroon voor outputdossiers en folders </a> ook specificeren.</td>
  </tr>
 </tbody>
</table>

1. Selecteer **Geavanceerd**. Specificeer een waarde voor het volgende gebied en de tikken **creëren**. De gecontroleerde map is geconfigureerd om een workflow te starten. Wanneer nu een bestand in de invoermap van de Gecontroleerde map wordt geplaatst, wordt de opgegeven workflow geactiveerd.

   | Veld | Beschrijving |
   |---|---|
   | Filter Payload Mapper | Wanneer u een gecontroleerde map maakt, wordt er een mapstructuur in de crx-opslagplaats gemaakt. De mappenstructuur kan dienen als een lading aan het werkschema. U kunt een script schrijven om een AEM workflow toe te wijzen voor het accepteren van invoer uit de gecontroleerde mapstructuur. Een out van de kaderimplementatie is beschikbaar en vermeld in de Filter van de Toewijzing van de Payload. Als u geen aangepaste implementatie hebt, selecteert u de standaardimplementatie. |

   Het tabblad Geavanceerd bevat meer velden. De meeste van deze velden bevatten een standaardwaarde. Om over alle gebieden te leren, zie [ creeer of vorm een gecontroleerd omslag ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md) artikel.

### Een interactieve communicatie of een brief indienen {#letter}

U kunt een Forms-centric werkschema op OSGi associëren en uitvoeren op voorlegging van een interactieve mededeling of een brief. In correspondentiebeheerworkflows worden gebruikt voor interactieve communicatie en brieven na verwerking. Bijvoorbeeld het e-mailen, afdrukken, faxen of archiveren van uiteindelijke brieven. Voor gedetailleerde stappen, zie [ verwerking van Post van interactieve mededelingen en brieven ](../../forms/using/submit-letter-topostprocess.md).

## Aanvullende configuraties {#additional-configurations}

### E-mailservice configureren {#configure-email-service}

U kunt de stappen Taak toewijzen en E-mail verzenden van AEM Workflows gebruiken om een e-mail te verzenden. Voer de volgende stappen uit om e-mailservers en andere configuraties op te geven die vereist zijn om e-mail te verzenden:

1. Ga naar AEM configuratiemanager op `https://[server]:[port]/system/console/configMgr` .
1. Open de **[!UICONTROL Day CQ Mail Service]** -configuratie. Geef een waarde op voor de velden **[!UICONTROL SMTP server host name]** , **[!UICONTROL SMTP server port,]** en **[!UICONTROL "From" address]** . Klik op **[!UICONTROL Save]**.
1. Open de **[!UICONTROL Day CQ Link Externalizer]** -configuratie. Geef in het veld **[!UICONTROL Domains]** het werkelijke hostnaam/IP-adres en poortnummer op voor lokale instanties, auteurs en publicatieinstanties. Klik op **[!UICONTROL Save]**.

### Workflowinstanties wissen {#purge-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen. Voor gedetailleerde informatie zie, [ Regelmatige het Schrappen van de Instanties van het Werkschema ](/help/sites-administering/workflows-administering.md#regular) het zuiveren van werkschemainstanties.

## Gevoelige gegevens beperken tot workflowvariabelen en opslaan in externe gegevensopslagruimten {#externalize-wf-variables}

Alle gegevens die vanuit adaptieve formulieren naar [!DNL Experience Manager] -workflows worden verzonden, kunnen beschikken over PII (Persoonlijk identificeerbare informatie) of EPD (Gevoelige persoonlijke gegevens) van de eindgebruikers van uw bedrijf. Nochtans, is het niet verplicht om uw gegevens te hebben die in [!DNL Adobe Experience Manager] worden opgeslagen [ bewaarplaats JCR ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/underlying-technology/introduction-jcr.html). U kunt de opslag van eindgebruikergegevens in uw beheerde gegevensopslag (bijvoorbeeld, Azure blob opslag) externaliseren door de informatie in [ werkschemariabelen ](/help/forms/using/variable-in-aem-workflows.md) te bepalen.

In een [!DNL Adobe Experience Manager] Forms-workflow worden gegevens verwerkt en doorgegeven via een reeks workflowstappen aan de hand van workflowvariabelen. Deze variabelen zijn benoemde eigenschappen of sleutelwaardeparen die zijn opgeslagen in de metagegevensnode voor workflowinstanties, bijvoorbeeld `/var/workflow/instances/<serverid>/<datebucket>/<uniquenameof model>_<id>/data/metaData` . Deze workflowvariabelen kunnen worden geexternaliseerd naar een andere opslagplaats dan de JCR en vervolgens worden verwerkt door [!DNL Adobe Experience Manager] -workflows. [!DNL Adobe Experience Manager] biedt API `[!UICONTROL UserMetaDataPersistenceProvider]` voor het opslaan van de workflowvariabelen in uw beheerde externe opslag. Meer over het Gebruiken van werkschemariabelen voor klant bezeten datastores in [!DNL Adobe Experience Manager], zie [ werkschemariabelen voor externe datastores beheren ](/help/sites-administering/workflows-administering.md#using-workflow-variables-customer-datastore).
[!DNL Adobe] verstrekt het volgende [ steekproef ](https://github.com/adobe/workflow-variable-externalizer) om variabelen van werkschemakaart aan Azure blob opslag op te slaan, door API [ UserMetaDataPersistenceProvider ](https://github.com/adobe/workflow-variable-externalizer/blob/master/README.md) te gebruiken. Op de gelijkaardige lijnen kunt u de steekproef als gids gebruiken [ UserMetaDataPersistenceProvider ] API om de werkschemariabelen in een andere gegevensopslag buiten [!DNL Adobe Experience Manager] te externaliseren en het zelfde te beheren.

>[!NOTE]
>
>Wanneer u uw werkschemavariabelen aan een externe gegevensopslag opslaat, verwijs de wijzers in de [ richtlijnen voor werkschema&#39;s externe gegevensopslag ](#guidelines-workflows-external-data-storage).

### De voorbeeldimplementatie voor de workflow-API installeren

Workflowvariabelen opslaan in uw beheerde Azure-blob-opslag:
1. Installeer [ steekproef ](https://github.com/adobe/workflow-variable-externalizer) werkschema API [ UserMetaDataPersistenceProvider ](https://github.com/adobe/workflow-variable-externalizer/blob/master/README.md) als volgt:

   1. Voer in de hoofdmap van het project de opdracht `mvn clean install` met Maven 3 uit.

   1. Voer `mvn clean install -PautoInstallPackage` uit als u de bundel en het inhoudspakket wilt implementeren op de auteur.

   1. Voer `mvn clean install -PautoInstallBundle` uit als u alleen de bundel op de auteur wilt implementeren.

1. Initialiseer de volgende eigenschappen in het extern alizer OSGi configuratiedossier in het `ui.config` inhoudspakket:

   ```JQL
      accountKey=""
      accountName=""
      endpointSuffix=""
      containerName=""
      protocol=""
   ```

Hier volgen de doeleinden (en voorbeelden) van deze eigenschappen:

* **accountKey** is de geheime sleutel om toegang toe te staan.

* **accountName** is de azure rekening waar het gegeven moet worden opgeslagen.

* **EndpointSuffix**, bijvoorbeeld, `core.windows.net`.

* **containerName** is de container in de rekening waar de gegevens moeten worden opgeslagen. Het voorbeeld gaat ervan uit dat de container bestaat.

* **protocol**, bijvoorbeeld, `https` of `http`.

1. Configureer het workflowmodel in [!DNL Adobe Experience Manager] . Om te weten hoe te om het werkschemamodel voor een externe opslag te vormen, zie [ het werkschemamodel ](#configure-aem-wf-model) vormen.

### Workflowmodel configureren in [!DNL Adobe Experience Manager] voor externe gegevensopslag {#configure-aem-wf-model}

Een AEM workflowmodel configureren voor externe gegevensopslag:

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .

1. Selecteer een modelnaam en selecteer **[!UICONTROL Edit]** .

1. Selecteer het pictogram Pagina-informatie en selecteer **[!UICONTROL Open Properties]** .

1. Selecteer **[!UICONTROL Externalize workflow data storage]** .

1. Selecteer **[!UICONTROL Save & Close]** om de eigenschappen op te slaan.

### Richtlijnen voor AEM werkstromen voor externe gegevensopslag {#guidelines-workflows-external-data-storage}

Hieronder volgen de richtlijnen wanneer u [!DNL Adobe Experience Manager] -workflows gebruikt en gegevens opslaat naar externe gegevensopslagsystemen (bijvoorbeeld Microsoft Azure-opslagserver):

* Gebruik variabelen om gegevens op te slaan tijdens het definiëren van invoer- en uitvoergegevensbestanden en bijlagen in stappen van het workflowmodel. Selecteer geen opties **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** . De **[!UICONTROL Relative to Payload]** en **[!UICONTROL Available at an absolute path]** opties tonen automatisch niet zodra u [ vormt een  [!DNL Adobe Experience Manager]  werkschemamodel voor externe gegevensopslag ](#configure-aem-wf-model).

* Gebruik variabelen om gegevensbestand en gehechtheid op te slaan terwijl het voorleggen van een adaptief formulier aan een AEMWerkstroom. Selecteer de optie **[!UICONTROL Relative to Payload]** niet als u een aangepast formulier naar een [!DNL Adobe Experience Manager] -workflow verzendt. De **[!UICONTROL Relative to Payload]** optie toont automatisch niet zodra u [ een  [!DNL Adobe Experience Manager]  werkschemamodel voor externe gegevensopslag ](#configure-aem-wf-model) vormt.

* Gebruik geen aangepaste [!DNL Adobe Experience Manager] workflowstap in een workflowmodel voor het opslaan van gegevens in de [!UICONTROL CRX DE] -opslagplaats.

* Wanneer u [ een  [!DNL Adobe Experience Manager]  werkschemamodel voor externe gegevensopslag ](#configure-aem-wf-model) vormt, creeer geen douanekolommen voor [!DNL Adobe Experience Manager] [!UICONTROL Inbox] aangezien de waarden van de douanekolommen niet worden gehaald als het het werkpunt in [!DNL Adobe Experience Manager] [!UICONTROL Inbox] tot een werkschema behoort dat voor externe opslag duidelijk is.
