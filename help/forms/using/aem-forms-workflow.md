---
title: Forms-centric workflow op OSGi
seo-title: Maak snel adaptieve op formulieren gebaseerde processen, automatiseer bewerkingen in documentservices en gebruik Adobe Sign met AEM workflows
description: AEM Forms Workflow gebruiken om revisie en goedkeuringen te automatiseren en snel samen te stellen, om documentservices te starten
seo-description: Gebruik AEM Forms Workflow om revisie en goedkeuringen te automatiseren en snel samen te stellen, documentservices te starten (bijvoorbeeld voor het converteren van een PDF-document naar een andere indeling), te integreren met de Adobe Sign-handtekeningworkflow en nog veel meer.
uuid: 797ba0f7-a378-45ac-9f82-fa9a952027be
topic-tags: publish, document_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 73e63493-e821-443f-b50d-10797360f5d1
docset: aem65
translation-type: tm+mt
source-git-commit: 149e505eb4dac0d9a56c53036ce1c6b8d16ad0f1
workflow-type: tm+mt
source-wordcount: '3015'
ht-degree: 0%

---


# Forms-centric workflow op OSGi{#forms-centric-workflow-on-osgi}

![](do-not-localize/header.png)

Ondernemingen verzamelen gegevens uit honderden en duizenden formulieren, verschillende back-endsystemen en online of offline gegevensbronnen. Zij hebben ook een dynamische reeks gebruikers om besluiten over de gegevens te nemen, die herhalende herbeoordeling en goedkeuringsprocessen impliceren.

Samen met overzicht en goedkeuringswerkschema&#39;s voor intern en extern publiek, hebben de grote organisaties en de ondernemingen herhalende taken. Een PDF-document wordt bijvoorbeeld geconverteerd naar een andere indeling. Wanneer manueel gedaan, nemen deze taken veel tijd en middelen op. Ondernemingen hebben ook wettelijke vereisten om een document digitaal te ondertekenen en formuliergegevens te archiveren voor later gebruik in vooraf gedefinieerde indelingen.

## Inleiding tot Forms-centric workflow op OSGi {#introduction-to-forms-centric-workflow-on-osgi}

U kunt AEM Workflows gebruiken om snel adaptieve workflows op basis van formulieren te maken. Deze workflows kunnen worden gebruikt voor revisie en goedkeuringen, bedrijfsprocesstromen, het starten van documentservices, integratie met de Adobe Sign-handtekeningworkflow en vergelijkbare bewerkingen. Bijvoorbeeld: verwerking van creditcardtoepassingen, workflows voor goedkeuring door werknemers, het opslaan van een formulier als PDF-document. Bovendien kunnen deze workflows binnen een organisatie of via een netwerkfirewall worden gebruikt.

Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi, zonder het moeten het volledige vermogen van het Beheer van het Proces op de stapel van JEE installeren. Voor de ontwikkeling en het beheer van workflows wordt gebruikgemaakt van de vertrouwde AEM en AEM Inbox-mogelijkheden. De werkstromen vormen de basis van het automatiseren van echte bedrijfsprocessen die veelvoudige softwaresystemen, netwerken, afdelingen, en zelfs organisaties omspannen.

Zodra opstelling, kunnen deze werkschema&#39;s manueel worden teweeggebracht om een bepaald proces te voltooien of programmatically in werking te stellen wanneer de gebruikers een vorm of [brievenbeheer](/help/forms/using/cm-overview.md) brief indienen. Met deze verbeterde AEM workflowmogelijkheden biedt AEM Forms twee aparte, maar toch vergelijkbare mogelijkheden. Als onderdeel van uw implementatiestrategie moet u bepalen welke strategie voor u werkt. Zie een [vergelijking](capabilities-osgi-jee-workflows.md) van de Forms-centric AEM Workflows op OSGi en Process Management op JEE. Bovendien voor de plaatsingstopologie zie, [Architectuur en plaatsingstopologieën voor AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

Forms-centric workflow op OSGi breidt [AEM Inbox](/help/sites-authoring/inbox.md) uit en biedt extra componenten (stappen) voor AEM Workfloweditor om ondersteuning toe te voegen voor op AEM Forms gerichte workflows. De uitgebreide AEM Inbox heeft functionaliteiten gelijkend op [AEM Forms Workspace](introduction-html-workspace.md). Samen met het beheren van menselijke-centrische werkschema&#39;s (Goedkeuring, Overzicht, etc.), kunt u AEM werkschema&#39;s gebruiken om [documentservices](/help/sites-developing/workflows-step-ref.md)-gerelateerde bewerkingen (bijvoorbeeld, Genereer PDF) en elektronisch ondertekenende (Adobe Sign) documenten te automatiseren.

Alle AEM Forms-workflowstappen ondersteunen het gebruik van variabelen. Met variabelen kunnen workflowstappen metagegevens tijdens runtime bevatten en doorgeven. U kunt verschillende typen variabelen maken om verschillende typen gegevens op te slaan. U kunt ook variabele verzamelingen (arrays) maken om meerdere instanties van verwante, met hetzelfde type getypte gegevens op te slaan. Typisch, gebruikt u een variabele of een inzameling van variabelen wanneer u een besluit moet nemen dat op de waarde wordt gebaseerd die het houdt of informatie opslaat die u later in een proces nodig hebt. Voor meer informatie over het gebruiken van variabelen in deze Forms-centric werkschemacomponenten (stappen), zie [Forms-centric werkschema op OSGi - Step Reference](../../forms/using/aem-forms-workflow-step-reference.md). Zie [Variabelen in AEM workflows](../../forms/using/variable-in-aem-workflows.md) voor informatie over het maken en beheren van variabelen.

Het volgende diagram toont de procedure van begin tot eind om, een Forms-centric werkschema op OSGi tot stand te brengen in werking te stellen en te controleren.

![introductie-to-name-forms-workflow](assets/introduction-to-aem-forms-workflow.jpg)

## Voordat u begint {#before-you-start}

* Een werkschema is een vertegenwoordiging van een echt bedrijfsproces. Houd uw real-world bedrijfsproces en lijst van de deelnemers van het bedrijfsproces klaar. Houd ook de hulplijnen (adaptieve formulieren, PDF-documenten en meer) gereed voordat u een workflow gaat maken.
* Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en Help de voortgang van de workflow te melden. Verdeel uw bedrijfsproces in logische stadia.
* U kunt de taakstap van AEM Workflows configureren om e-mailmeldingen te verzenden naar de gebruikers of de toewijzingen. Daarom [schakel e-mailmeldingen in](#configure-email-service).
* Een workflow kan ook Adobe-handtekeningen gebruiken voor digitale handtekeningen. Als u van plan bent om Adobe Sign in een werkstroom te gebruiken, [vorm Adobe Sign voor AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md) alvorens het in een werkschema te gebruiken.

## Een workflowmodel maken {#create-a-workflow-model}

Een workflowmodel bestaat uit logica en stroom van een bedrijfsproces. Het bestaat uit een reeks stappen. Deze stappen zijn AEM componenten. U kunt workflowstappen uitbreiden met parameters en scripts om desgewenst meer functionaliteit en controle te bieden. AEM Forms bevat een aantal stappen naast AEM stappen uit het vak. Voor een gedetailleerde lijst van AEM en AEM Forms stappen, zie [AEM Referentie van de Stap van de Werkstroom](/help/sites-developing/workflows-step-ref.md) en [Forms-centric werkschema op OSGi - Step Referentie](../../forms/using/aem-forms-workflow.md).

AEM biedt een intuïtieve gebruikersinterface voor het maken van een workflowmodel met behulp van de meegeleverde workflowstappen. Zie [Workflowmodellen maken](/help/sites-developing/workflows-models.md) voor stapsgewijze instructies voor het maken van een workflowmodel. In het volgende voorbeeld worden stapsgewijze instructies gegeven voor het maken van een workflowmodel voor een goedkeurings- en revisiewerkstroom:

>[!NOTE]
>
>Als u een workflowmodel wilt maken of bewerken, moet u lid zijn van de groep met workfloweditors.

### Een model maken voor een goedkeurings- en revisiewerkstroom {#create-a-model-for-an-approval-and-review-workflow}

Goedkeuring- en revisiewerkstroom is bedoeld voor de taken waarvoor menselijke tussenkomst vereist is om beslissingen te nemen. In het volgende voorbeeld wordt een workflowmodel gemaakt voor een hypotheekleningaanvraag die moet worden ingevuld door een bankagent voor het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde aanvraag met Adobe Sign naar de aanvrager van elektronische handtekeningen gezonden.

Het voorbeeld is beschikbaar als een hieronder bijgevoegd pakket. Importeer en installeer het voorbeeld met pakketbeheer. U kunt ook de volgende stappen uitvoeren om handmatig het workflowmodel voor de toepassing te maken:

In het voorbeeld wordt een workflowmodel gemaakt voor een hypotheektoepassing die moet worden ingevuld door een bankagent op het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde toepassing met Adobe Sign naar de klant verzonden voor elektronische handtekeningen. U kunt het voorbeeld importeren en installeren met pakketbeheer.

[Bestand ophalen](assets/example-mortgage-loan-application.zip)

1. Open de console Workflowmodellen. De standaard-URL is `https://[server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Selecteer **Maken** en **Model** maken. Het dialoogvenster Workflowmodel toevoegen wordt weergegeven.
1. Voer de **Titel** en **Naam** (optioneel) in. Bijvoorbeeld een hypotheekaanvraag. Tik **Done**.
1. Selecteer het nieuwe workflowmodel en tik **Bewerken**. Nu kunt u workflowstappen toevoegen om bedrijfslogica te maken. Wanneer u voor het eerst een workflowmodel maakt, bevat dit het volgende:

   * De stappen: Start- en stroomeinde van stroom. Deze stappen vertegenwoordigen het begin en het einde van de workflow. Deze stappen zijn vereist en kunnen niet worden bewerkt of verwijderd.
   * Een stap van de voorbeelddeelnemer genoemd Stap 1. Deze stap wordt gevormd om een het werkpunt aan de admin gebruiker toe te wijzen. Verwijder deze stap.

1. E-mailmeldingen inschakelen. U kunt een op Forms gerichte workflow op OSGi configureren om e-mailmeldingen naar de gebruikers of gebruikers te sturen. Voer de volgende configuraties uit om e-mailmeldingen in te schakelen:

   1. Ga naar AEM configuratiemanager op `https://[server]:[port]/system/console/configMgr`.
   1. Open de **[!UICONTROL Day CQ Mail Service]** configuratie. Geef een waarde op voor de velden **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port,]** en **[!UICONTROL "From" address]**. Klik op **[!UICONTROL Save]**.
   1. Open de **[!UICONTROL Day CQ Link Externalizer]** configuratie. Geef in het veld **[!UICONTROL Domains]** het werkelijke hostnaam/IP-adres en poortnummer op voor lokale instanties, auteurs en publicatieinstanties. Klik op **[!UICONTROL Save]**.

1. Workflowfasen maken. Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en de voortgang van de workflow rapporteren.

   Als u een werkgebied wilt definiëren, tikt u op het pictogram ![info-circle](assets/info-circle.png) om de eigenschappen van het workflowmodel te openen, opent u het tabblad **Stages**, voegt u fasen toe voor het workflowmodel en tikt u op **Opslaan en sluiten**. Maak bijvoorbeeld fasen in het voorbeeld van de hypotheektoepassing: leningaanvraag, status van leningaanvraag, te ondertekenen documenten en ondertekend leningsdocument.

1. Sleep en zet **Taak** stappen browser aan het werkschemamodel toe. Maak van het de eerste stap van het model.

   De taakcomponent toewijzen wijst de taak, die door workflow wordt gemaakt, toe aan een gebruiker of groep. Naast het toewijzen van de taak kunt u de component gebruiken om een adaptief formulier of een niet-interactief PDF-bestand voor de taak op te geven. Het adaptieve formulier is vereist om invoer van gebruikers te accepteren en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie zijn.

   U kunt de stap ook gebruiken om het gedrag van de taak te controleren. Als u bijvoorbeeld een automatisch recorddocument maakt, wijst u de taak toe aan een bepaalde gebruiker of groep, het pad van de verzonden gegevens, het pad van de gegevens die vooraf moeten worden ingevuld en de standaardhandelingen. Voor gedetailleerde informatie over de opties van de toewijzingstaakstap, zie [Forms-centric werkschema op OSGi - Step Reference](../../forms/using/aem-forms-workflow.md) document.

   ![workflow-editor](assets/workflow-editor.png)

   In het voorbeeld van de hypotheektoepassing configureert u de taakstap zodanig dat een alleen-lezen adaptief formulier wordt gebruikt en geeft u het PDF-document weer zodra de taak is voltooid. Selecteer ook voor gebruikersgroep die de aanvraag voor een lening mag goedkeuren. Schakel op het tabblad **Handelingen** de optie **Verzenden** uit. Creeer een **actiontaken** variabele van het gegevenstype van het Koord en specificeer de variabele als **Variabele van de Route**. Bijvoorbeeld actionTake. Voeg ook de routes Goedkeuren en Afwijzen toe. De routes worden getoond als afzonderlijke acties (knopen) in AEM Inbox. De werkstroom selecteert een vertakking op basis van de actie (knoop) een gebruiker tikt.

   U kunt het voorbeeldpakket importeren, dat u kunt downloaden vanaf het begin van de sectie, voor de volledige set waarden van alle velden van de taakstap toewijzen die is geconfigureerd, bijvoorbeeld hypotheektoepassing.

1. Sleep de component OR Splitsen van de stapbrowser naar het workflowmodel. Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

   U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

   Gebruik de uitdrukkingsredacteur om het verpletteren van uitdrukkingen voor Tak 1 en Tak 2 tot stand te brengen. Deze verpletterende uitdrukkingen helpen een tak kiezen die op de gebruikersactie in AEM Inbox wordt gebaseerd.

   **Het verpletteren van uitdrukking voor Tak 1**

   Wanneer een gebruiker **goedkeurt** in AEM Inbox, Tak 1 wordt geactiveerd.

   ![OR Splitsen, voorbeeld](assets/orsplit_branch1_active_new.png)

   **Verpletterende uitdrukking voor Tak 2**

   Wanneer een gebruiker **Afwijzen** in AEM Inbox tikt, wordt Tak 2 geactiveerd.

   ![OR Splitsen, voorbeeld](assets/orsplit_branch2_active_new.png)

   Zie [Variabelen in AEM Forms-workflows](../../forms/using/variable-in-aem-workflows.md) voor informatie over het maken van routeringsexpressies met behulp van variabelen.

1. Voeg andere workflowstappen toe om de bedrijfslogica te bouwen.

   Voor het hypotheekvoorbeeld voegt u een document met een record te genereren, twee taakstappen toe en een stap in het ondertekeningsdocument aan vertakking 1 van het model, zoals in de onderstaande afbeelding wordt weergegeven. De ene taakstap bestaat uit het weergeven en verzenden van **te ondertekenen leningsdocumenten aan de aanvrager** en een andere taakcomponent toewijzen is **om ondertekende documenten weer te geven**. Voeg ook een taakcomponent toe aan vertakking 2. Deze wordt geactiveerd wanneer een gebruiker op Afwijzen in AEM Postvak IN tikt.

   Voor de volledige set waarden van alle velden van de taakstappen toewijzen, de stap Document of Record en de stap voor het ondertekeningsdocument die zijn geconfigureerd voor bijvoorbeeld de hypotheektoepassing, importeert u het voorbeeldpakket dat beschikbaar is om te worden gedownload vanaf het begin van deze sectie.

   Het workflowmodel is gereed. U kunt de workflow op verschillende manieren starten. Zie [Forms-centric workflow starten op OSGi](#launch) voor meer informatie.

   ![workflow-editor-hypotheek](assets/workflow-editor-mortgage.png)

## Een Forms-centric Workflow-toepassing {#create-a-forms-centric-workflow-application} maken

De toepassing is het adaptieve formulier dat aan de workflow is gekoppeld. Wanneer een toepassing via Inbox wordt verzonden, wordt de bijbehorende workflow gestart. Als u een Forms-workflow als toepassing beschikbaar wilt maken in AEM Inbox en AEM Forms App, gaat u als volgt te werk om een workflowtoepassing te maken:

>[!NOTE]
>
>U moet lid van de fd-beheerder groep zijn om werkschematoepassingen te kunnen tot stand brengen en beheren.

1. Ga in de AEM auteur naar ![tools-1](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Manage Workflow Application]** en tikken **[!UICONTROL Create]**.
1. Geef in het venster Workflowtoepassing maken invoer op voor de volgende velden en tik **Maken**. Er wordt een nieuwe toepassing gemaakt en deze wordt weergegeven in het scherm Workflowtoepassingen.

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>De titel is zichtbaar in AEM Postvak IN en helpt gebruikers een toepassing te kiezen. Houd het beschrijvend. Bijvoorbeeld, sparen de Toepassing van het Openen van de Rekening.<br /> </td>
  </tr>
  <tr>
   <td>Naam </td>
   <td>Geef de naam van de toepassing op. Alle andere tekens dan alfabeten, getallen, afbreekstreepjes en onderstrepingstekens worden vervangen door afbreekstreepjes. </td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>De beschrijving is zichtbaar in AEM Postvak IN. Geef in de beschrijvingsvelden gedetailleerde informatie over de toepassing. Bijvoorbeeld, Doel van de toepassing.<br /> </td>
  </tr>
  <tr>
   <td>Adaptief formulier</td>
   <td><p>Geef het pad van een adaptief formulier op. Wanneer een gebruiker een toepassing start, wordt het opgegeven adaptieve formulier weergegeven.</p> <p><strong>Opmerking</strong>: Workflowtoepassingen ondersteunen geen formulieren en PDF-documenten die langer zijn dan één pagina of die moeten worden geschoven op Apple iPad. Wanneer een toepassing wordt geopend op Apple iPad en het adaptieve formulier of het PDF-document langer is dan een pagina, gaan de formuliervelden en de inhoud van de tweede pagina verloren.</p> </td>
  </tr>
  <tr>
   <td>Toegangsgroep</td>
   <td><p>Selecteer een groep. De toepassing is alleen zichtbaar in AEM Postvak IN voor de leden van de geselecteerde groep. De optie van de toegangsgroep maakt alle groepen van de werkschema-gebruikers groep beschikbaar voor selectie. </p> <br /> </td>
  </tr>
  <tr>
   <td>Prefill-service</td>
   <td>Selecteer een <a href="../../forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">prefill-service</a> voor het adaptieve formulier.<br /> </td>
  </tr>
  <tr>
   <td>Workflowmodel</td>
   <td>Selecteer een <a href="../../forms/using/aem-forms-workflow.md#create-a-workflow-model">workflowmodel</a> voor de toepassing. Een workflowmodel bestaat uit logica en stroom van het bedrijfsproces. </td>
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

### Een toepassing verzenden vanuit AEM Inbox {#inbox}

De workflowtoepassing die u hebt gemaakt, is beschikbaar als een toepassing in Inbox. Gebruikers die lid zijn van een groep workflowgebruikers kunnen de toepassing die de bijbehorende workflow activeert, invullen en verzenden. Zie [Forms-toepassingen en -taken beheren in AEM Inbox](../../forms/using/manage-applications-inbox.md) voor informatie over het gebruik van AEM Inbox om toepassingen te verzenden en taken te beheren.

### Een toepassing indienen vanuit AEM Forms App {#afa}

De AEM Forms-toepassing wordt gesynchroniseerd met een AEM Forms-server en u kunt wijzigingen aanbrengen in de formuliergegevens, taken, workflowtoepassingen en opgeslagen informatie (concepten/sjablonen) in uw account. Zie [AEM Forms app](/help/forms/using/aem-forms-app.md) en verwante artikelen voor meer informatie.

### Een adaptief formulier {#af} indienen

U kunt de verzendacties van een adaptief formulier zo configureren dat een workflow wordt gestart bij het verzenden van het adaptieve formulier. Aangepaste formulieren bevatten de **Invoke een AEM Workflow** submit action to start a workflow on submission of an adaptive form. Zie [De handeling Verzenden configureren](../../forms/using/configuring-submit-actions.md) voor gedetailleerde informatie over de verzendactie. Als u een adaptief formulier wilt verzenden via de AEM Forms-app, schakelt u Synchroniseren met AEM Forms App in de adaptieve formuliereigenschappen in.

U kunt een adaptief formulier configureren voor synchronisatie, verzending en activering van een workflow vanuit de AEM Forms-app. Zie [Werken met een formulier](/help/forms/using/working-with-form.md) voor meer informatie.

### Een gecontroleerde map {#watched} gebruiken

Een beheerder (een lid van de groep van fd-beheerders) kan een netwerkomslag vormen om een vooraf gevormde werkschema in werking te stellen wanneer een gebruiker een dossier (zoals een Pdf- dossier) in de omslag plaatst. Nadat de workflow is voltooid, kan het resulterende bestand worden opgeslagen in een opgegeven uitvoermap. Een dergelijke map wordt [Gecontroleerde map](../../forms/using/watched-folder-in-aem-forms.md) genoemd. Voer de volgende procedure uit om een gecontroleerde omslag te vormen om een werkschema te lanceren:

1. Ga in de AEM auteur naar ![tools-1](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Configure Watched Folder]**. Er wordt een lijst met al geconfigureerde gecontroleerde mappen weergegeven.
1. Tik op **[!UICONTROL New]**. Er wordt een lijst met velden weergegeven. Geef een waarde op voor de volgende velden om een gecontroleerde map voor een workflow te configureren:

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
   <td>Selecteer de optie <span class="uicontrol">Workflow </code>. </code></td>
  </tr>
  <tr>
   <td><span class="uicontrol">Workflowmodel</code></td>
   <td>Selecteer een workflowmodel.<br /> </td>
  </tr>
  <tr>
   <td><span class="uicontrol">Uitvoerbestandspatroon</code></td>
   <td>Geef de mapstructuur op voor uitvoerbestanden en -mappen. U kunt ook een <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">patroon opgeven voor uitvoerbestanden en -mappen</a>.</td>
  </tr>
 </tbody>
</table>

1. Tik **Geavanceerd**. Geef een waarde op voor het volgende veld en typ **Maken**. De gecontroleerde map is geconfigureerd om een workflow te starten. Wanneer nu een bestand in de invoermap van de Gecontroleerde map wordt geplaatst, wordt de opgegeven workflow geactiveerd.

   | Veld | Beschrijving |
   |---|---|
   | Filter Payload Mapper | Wanneer u een gecontroleerde map maakt, wordt er een mapstructuur in de crx-opslagplaats gemaakt. De mappenstructuur kan dienen als een lading aan het werkschema. U kunt een script schrijven om een AEM workflow toe te wijzen voor het accepteren van invoer uit de gecontroleerde mapstructuur. Een out van de kaderimplementatie is beschikbaar en vermeld in de Filter van de Toewijzing van de Payload. Als u geen aangepaste implementatie hebt, selecteert u de standaardimplementatie. |

   Het tabblad Geavanceerd bevat meer velden. De meeste van deze velden bevatten een standaardwaarde. Zie [Een gecontroleerde map maken of configureren](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md) voor meer informatie over alle velden.

### Een interactieve communicatie of een brief {#letter} indienen

U kunt een Forms-centric werkschema op OSGi associëren en uitvoeren op voorlegging van een interactieve mededeling of een brief. In correspondentiebeheerworkflows worden gebruikt voor interactieve communicatie en brieven na verwerking. Bijvoorbeeld het e-mailen, afdrukken, faxen of archiveren van uiteindelijke brieven. Zie [Nabewerking van interactieve communicatie en letters](../../forms/using/submit-letter-topostprocess.md) voor gedetailleerde stappen.

## Aanvullende configuraties {#additional-configurations}

### E-mailservice {#configure-email-service} configureren

U kunt de stappen Taak toewijzen en E-mail verzenden van AEM Workflows gebruiken om een e-mail te verzenden. Voer de volgende stappen uit om e-mailservers en andere configuraties op te geven die vereist zijn om e-mail te verzenden:

1. Ga naar AEM configuratiemanager op `https://[server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Day CQ Mail Service]** configuratie. Geef een waarde op voor de velden **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port,]** en **[!UICONTROL "From" address]**. Klik op **[!UICONTROL Save]**.
1. Open de **[!UICONTROL Day CQ Link Externalizer]** configuratie. Geef in het veld **[!UICONTROL Domains]** het werkelijke hostnaam/IP-adres en poortnummer op voor lokale instanties, auteurs en publicatieinstanties. Klik op **[!UICONTROL Save]**.

### Instanties {#purge-workflow-instances} van werkstroom wissen

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen. Voor gedetailleerde informatie, zie [Regular Purging of Workflow Instances](/help/sites-administering/workflows-administering.md#regular) purging of workflow instances
