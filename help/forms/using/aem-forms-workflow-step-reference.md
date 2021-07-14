---
title: Forms-centric workflow voor OSGi - Step Reference
seo-title: Forms-centric workflow voor OSGi - Step Reference
description: Met een Forms-gerichte workflow voor OSGi-stappen kunt u snel adaptieve formulieren op basis van workflows maken.
seo-description: Met een Forms-gerichte workflow voor OSGi-stappen kunt u snel adaptieve formulieren op basis van workflows maken.
uuid: 6f791c45-0e35-4c55-9106-5340caab94b7
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: f0a5588d-f210-4f04-bc35-b62834f90ab1
docset: aem65
exl-id: 470fcfda-dfde-437c-b539-d5af1e13a7d6
source-git-commit: aaafda59c63ea47c67ec974263013ead468df9cc
workflow-type: tm+mt
source-wordcount: '7150'
ht-degree: 0%

---

# Forms-centric workflow voor OSGi - Step Reference{#forms-centric-workflow-on-osgi-step-reference}

## Stappen Forms Workflow {#forms-workflow-steps}

Forms-workflowstappen voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel adaptieve formulieren maken op basis van Forms-centric workflow voor OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne en interne bedrijfsprocessen binnen de firewall. U kunt ook de stappen van de Forms Workflow gebruiken om documentservices te starten, te integreren met de Adobe Sign-handtekeningworkflow en andere AEM Forms-bewerkingen uit te voeren. U hebt [AEM Forms add-on](https://www.adobe.com/go/learn_aemforms_documentation_63) nodig om deze stappen in een workflow te gebruiken.

## Taakstap toewijzen {#assign-task-step}

De taakstap toewijzen maakt een taak en wijst deze toe aan een gebruiker of groep. Naast het toewijzen van de taak geeft de component ook het adaptieve of niet-interactieve PDF-formulier voor de taak op. Het adaptieve formulier is vereist om invoer van gebruikers te accepteren en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie zijn.

U kunt de component ook gebruiken om het gedrag van de taak te controleren. Bijvoorbeeld, creërend een automatisch document van verslag, toewijzend de taak aan een specifieke gebruiker of een groep, specificerend de weg van de voorgelegde gegevens, specificerend de weg van te vullen gegevens, en specificerend standaardacties. De stap Taak toewijzen heeft de volgende eigenschappen:

* **Titel:** Titel van de taak. De titel wordt weergegeven in AEM Postvak IN.
* **Beschrijving:** Uitleg van de bewerkingen die in de taak worden uitgevoerd. Deze informatie is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Miniatuurpad:** pad van de taakminiatuur. Als er geen pad is opgegeven, wordt voor een aangepaste standaardminiatuur van het formulier weergegeven en voor Document of Record, een standaardpictogram weergegeven.
* **Werkstroomwerkgebied:** een werkstroom kan meerdere fasen hebben. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Selecteren > Pagina > Pagina-eigenschappen > Staven).
* **Prioriteit:** Geselecteerde prioriteit wordt getoond in AEM Inbox. De beschikbare opties zijn Hoog, Normaal en Laag. De standaardwaarde is Normaal.
* **Vervaldatum:** Geef het aantal dagen of uren op waarna de taak achterstallig is. Als u **Uit** selecteert, dan is de taak nooit duidelijk achterstallig. U kunt ook een time-outhandler opgeven om specifieke taken uit te voeren nadat de taak is uitgevoerd.

* **Dagen:** het aantal dagen voordat de taak moet worden voltooid. Het aantal dagen wordt geteld nadat de taak aan een gebruiker is toegewezen. Als een taak niet volledig is en het aantal dagen overschrijdt specificeert op het gebied van Dagen, dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de vervaldatum.
* **Uren:** het aantal uren voordat de taak moet worden voltooid. Het aantal uren wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal uren overschrijdt specificeert op het gebied van Uren, dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de verschuldigde uren.
* **Vertraging na Vervaldatum:** selecteer deze optie om het selectieveld Tijdelijke handler in te schakelen.
* **Timeout-handler:** selecteer het script dat moet worden uitgevoerd wanneer de taakstap toewijzen de juiste datum overschrijdt. Scripts die in de CRX-opslagplaats op [apps]/fd/dashboard/scripts/timeoutHandler worden geplaatst, zijn beschikbaar voor selectie. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt.
* **Markeer de handeling en de opmerking van de laatste taak in Taakdetails:** selecteer deze optie om de laatste actie weer te geven die is uitgevoerd en de opmerking die is ontvangen in de sectie met taakdetails van een taak.
* **Type:** kies het type document dat moet worden ingevuld wanneer de werkstroom wordt gestart. U kunt een adaptief formulier, alleen-lezen adaptief formulier, een niet-interactief PDF-document, de gebruikersinterface van de interactieve communicatieagent of het interactieve communicatie webkanaaldocument kiezen.
* **Adaptief formulier gebruiken:** Geef de methode op waarmee het invoeradaptieve formulier wordt gezocht. Deze optie is beschikbaar als u Adaptief formulier of Alleen-lezen adaptief formulier selecteert in de vervolgkeuzelijst Type. U kunt het adaptieve formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is op een absoluut pad of dat beschikbaar is op een pad in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven.\
   U kunt meerdere aangepaste formulieren aan een workflow koppelen. Hierdoor kunt u een adaptief formulier op de runtime opgeven met de beschikbare invoermethoden.

* **Gebruik Interactieve communicatie:** geef de methode op om de interactieve invoercommunicatie te zoeken. U kunt de interactieve communicatie gebruiken die aan het werkschema wordt voorgelegd, beschikbaar bij een absolute weg, of beschikbaar bij een weg in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven. Deze optie is beschikbaar als u Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.

>[!NOTE]
>
>U moet cm-agent-gebruikers en werkschema-gebruikers groepstaken hebben om tot Interactieve Communicatie Agent UI in AEM inbox toegang te hebben.

* **Adaptief formulier of interactief communicatiepad**: Geef het pad op van het adaptieve formulier of de interactieve communicatie. U kunt het aangepaste formulier of de interactieve communicatie gebruiken die naar de workflow wordt verzonden, beschikbaar via een absoluut pad, of het aangepaste formulier ophalen via een pad dat is opgeslagen in een variabele van het type tekenreeksgegevens.
* **Selecteer invoer-PDF met:het pad van een niet-interactief PDF-document** opgeven. Het veld is beschikbaar wanneer u een niet-interactief PDF-document kiest in het veld Type. U kunt de invoer-PDF selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld [Payload_Directory]/Workflow/PDF/credit-card.pdf. Het pad bestaat niet in crx-repository. Een beheerder maakt het pad voordat het wordt gebruikt. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om de optie PDF-pad te kunnen gebruiken.
* **Voor voltooide taak geeft u het adaptieve formulier weer als**: Als een taak is gemarkeerd als voltooid, kunt u het adaptieve formulier weergeven als een alleen-lezen adaptief formulier of als een PDF-document. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om het adaptieve formulier weer te geven als Document of Record.
* **Vooraf ingevuld:** De volgende velden hieronder dienen als invoer voor de taak:

   * **Selecteer een invoergegevensbestand met:** Pad van het invoergegevensbestand (.json,. xml-, .doc- of formuliergegevensmodel). U kunt het invoergegevensbestand terugwinnen gebruikend een weg die met betrekking tot de lading is of het dossier terugwinnen dat in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen. Het bestand bevat bijvoorbeeld de gegevens die via een AEM Inbox-toepassing voor het formulier zijn verzonden. Een voorbeeldpad is [Payload_Directory]/workflow/data.
   * **Selecteer invoerbijlagen met:** Bijlagen die beschikbaar zijn op de locatie, zijn gekoppeld aan het formulier dat aan de taak is gekoppeld. Het pad is altijd relatief ten opzichte van de lading. Een voorbeeldpad is [Payload_Directory]/attachments/
   * **Kies invoer-JSON:** selecteer een invoer-JSON-bestand met een pad dat relatief is ten opzichte van de lading of dat is opgeslagen in een variabele van het gegevenstype Document, JSON of Formuliergegevensmodel. Deze optie is beschikbaar als u Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.
   * **Kies een aangepaste Prefill-service:** selecteer de Prefill-service om de gegevens op te halen en het Interactive Communication Web channel-document of de Agent UI vooraf in te vullen.

   * **Gebruik de vooraf ingevulde dienst van de hierboven geselecteerde interactieve mededeling:** Gebruik deze optie om de prefill dienst van Interactieve Communicatie te gebruiken die in de Interactieve Communicatie van het Gebruik drop-down lijst wordt bepaald.
   * **Toewijzing verzoekkenmerk:** gebruik de sectie Aanvraagkenmerktoewijzing om de  [naam en waarde van het aanvraagkenmerk](../../forms/using/work-with-form-data-model.md#bindargument) te definiëren. Haal de details van de gegevensbron op die op de attributennaam en waarde wordt gebaseerd in het verzoek wordt gespecificeerd. U kunt een waarde van het verzoekattribuut bepalen gebruikend een letterlijke waarde of een variabele van het gegevenstype van het Koord.\
      De prefill dienst en de opties van de verzoekkenmerkafbeelding zijn beschikbaar slechts als u het Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.

* **Verzonden informatie:** De volgende hieronder vermelde gebieden dienen als outputplaatsen aan de taak:

   * **Uitvoergegevensbestand opslaan met:** Gegevensbestand opslaan (.json,. xml-, .doc- of formuliergegevensmodel). Het gegevensbestand bevat informatie die via het bijbehorende formulier is verzonden. U kunt het uitvoergegevensbestand opslaan met een pad dat relatief is ten opzichte van de lading of dit opslaan in een variabele van het gegevenstype Document, XML of JSON. Bijvoorbeeld [Payload_Directory]/Workflow/data, waarbij de gegevens een bestand zijn.
   * **Bijlagen opslaan met:de formulierbijlagen in een taak** opslaan. U kunt de bijlagen opslaan met een pad dat relatief is ten opzichte van de lading of deze opslaan in een variabele van een array van documentgegevenstype.
   * **Document met record opslaan met:** pad om een document met recordbestand op te slaan. Bijvoorbeeld [Payload_Directory]/DocumentofRecord/credit-card.pdf. U kunt het Document van Verslag bewaren gebruikend een weg die met betrekking tot de lading is of het opslaan in een variabele van het gegevenstype van het Document. Als u de optie **Ten opzichte van Payload** selecteert, wordt het document of Record niet gegenereerd als het padveld leeg blijft. Deze optie is alleen beschikbaar als u Adaptief formulier selecteert in de vervolgkeuzelijst Type.

   * **Webkanaalgegevens opslaan met:** Sla het webkanaalgegevensbestand op met een pad dat relatief is ten opzichte van de laadbewerking of sla dit op in een variabele van het gegevenstype Document, JSON of Formuliergegevensmodel. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.
   * **PDF-document opslaan met:het PDF-document** opslaan met een pad dat relatief is ten opzichte van de laadbewerking, of het opslaan in een variabele van het gegevenstype Document. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.
   * **Lay-outsjabloon opslaan met:de lay-outsjabloon** opslaan met een pad dat relatief is ten opzichte van de laadbewerking of dit opslaan in een variabele van het gegevenstype Document. De [layout template](../../forms/using/layout-design-details.md) verwijst naar een XDP-bestand dat u maakt met Forms Designer. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.

* **Toewijzen > Opties toewijzen:** geef de methode op waarmee de taak aan een gebruiker wordt toegewezen. U kunt de taak dynamisch toewijzen aan een gebruiker of groep met behulp van het script Deelnemerkiezer of u kunt de taak toewijzen aan een specifieke AEM gebruiker of groep.
* **Deelnemerkiezer:** de optie is beschikbaar wanneer de optie  **Dynamisch naar een gebruiker of** groep is geselecteerd in het veld Opties toewijzen. U kunt een ECMAScript of de dienst gebruiken om een gebruiker of een groep dynamisch te selecteren. Zie [Workflows dynamisch toewijzen aan gebruikers](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) en [Een aangepaste stap Adobe Experience Manager Dynamic Participant maken.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Deelnemers:** het veld is beschikbaar wanneer de  **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** optie is geselecteerd in het veld  **Deelnemerkiezer** . In het veld kunt u gebruikers of groepen selecteren voor de optie RandomParticipantChooser.

* **Toegewezen:** het gebied is beschikbaar wanneer het  **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** wordt geselecteerd in het  **Deelnemergebied** . In het veld kunt u een variabele van het gegevenstype String selecteren om de toewijzing te definiëren.

* **Argumenten:** Het veld is beschikbaar wanneer een ander script dan het script RandomParticipantChoose is geselecteerd in het veld Deelnemerkiezer. In het veld kunt u een lijst met door komma&#39;s gescheiden argumenten opgeven voor het script dat is geselecteerd in het veld Deelnemerkiezer.

* **Gebruiker of Groep:** De taak wordt toegewezen aan geselecteerde gebruiker of groep. De optie is beschikbaar wanneer **Aan een specifieke gebruiker of groepoptie** in **opties toewijzen** gebied wordt geselecteerd. In het veld worden alle gebruikers en groepen van de groep met workflowgebruikers weergegeven.\
   In het vervolgkeuzemenu **Gebruiker of Groep** worden de gebruikers en groepen weergegeven waartoe de aangemelde gebruiker toegang heeft. De vertoning van de gebruikersbenaming hangt af van als u toegangstoestemmingen op de **users** knoop in crx-bewaarplaats voor die bepaalde gebruiker hebt.

* **[!UICONTROL Send Notification Email]**: Selecteer deze optie als u e-mailberichten wilt verzenden naar de ontvanger. Deze meldingen worden verzonden wanneer een taak wordt toegewezen aan een gebruiker of een groep. Met de optie **[!UICONTROL Recipient Email Address]** kunt u opgeven hoe het e-mailadres moet worden opgehaald.

* **[!UICONTROL Recipient Email Address]**: U kunt e-mailadres in een variabele opslaan, letterlijk een permanent e-mailadres opgeven of standaard e-mailadres gebruiken van de ontvanger die is opgegeven in het profiel van de ontvanger. U kunt de letterlijke waarde of een variabele gebruiken om het e-mailadres van een groep op te geven. De optie Variabele is handig bij het dynamisch ophalen en gebruiken van een e-mailadres. De optie **[!UICONTROL Use default email address of the assignee]** is slechts voor één toegewezen persoon. In dit geval wordt het e-mailadres gebruikt dat is opgeslagen in het gebruikersprofiel van de toewijzing.

* **HTML-e-mailsjabloon**: Selecteer een e-mailsjabloon voor het e-mailbericht. Als u een sjabloon wilt bewerken, wijzigt u het bestand op /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in de crx-repository.
* **Delegatie toestaan aan:** AEM InBox biedt een optie voor de aangemelde gebruiker om de toegewezen workflow te delegeren aan een andere gebruiker. U kunt delegeren binnen dezelfde groep of aan de werkschemagebruiker van een andere groep. Als de taak aan één enkele gebruiker wordt toegewezen en **sta delegatie aan leden van de bestemmingsgroep** optie wordt geselecteerd, dan is het niet mogelijk om de taak aan een andere gebruiker of een groep te delegeren.
* **Instellingen voor delen:** AEM InBox biedt opties om één of alle taken in het Postvak IN te delen met andere gebruikers:
   * Wanneer **Toestaan dat toegewezen persoon expliciet mag delen in de optie inbox** is geselecteerd, kan de gebruiker op de taak klikken en deze delen met een andere AEM gebruiker.
   * Wanneer de optie **Toestaan dat een ontvanger kan delen via inbox sharing** is geselecteerd en een gebruiker zijn Postvak-items deelt of andere gebruikers toegang geeft tot zijn Postvak-items, worden alleen taken waarvoor deze optie is ingeschakeld, gedeeld met andere gebruikers.

* **Handelingen > Standaardhandelingen:** Handelingen Verzenden, Opslaan en Herstellen zijn beschikbaar. Standaard zijn alle standaardhandelingen ingeschakeld.
* **De Variabele van de route:** Naam van de routevariabele. De routevariabele vangt douaneacties die een gebruiker in AEM Inbox selecteert.
* **Routes:** Een taak kan zich aan verschillende routes vertakken. Wanneer geselecteerd in AEM Inbox, keert de route een waarde en de werkschematakken terug die op de geselecteerde route worden gebaseerd. U kunt of routes in een variabele van serie van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om routes manueel toe te voegen.

* **Titel**: Specificeer de titel voor de route. Deze wordt weergegeven in AEM Postvak IN.
* **Koraalpictogram**: Geef het HTML-kenmerk van een koraalpictogram op. De Adobe CorelUI-bibliotheek biedt een uitgebreide set aanraakpictogrammen. U kunt een pictogram voor de route kiezen en gebruiken. Deze wordt samen met de titel in AEM Inbox weergegeven. Als u de routes in een variabele opslaat, gebruiken de routes een standaard &quot;Tags&quot;koraalpictogram.
* **Toestaan dat de ontvanger commentaar** toevoegt: Selecteer deze optie als u opmerkingen voor de taak wilt inschakelen. Een toegewezen persoon kan de opmerkingen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **Opmerking opslaan in variabele:de opmerking** opslaan in een variabele van het gegevenstype String. Deze optie wordt alleen weergegeven als u het selectievakje **Toestaan dat een ontvanger commentaar toevoegt** inschakelt.

* **Toestaan dat de ontvanger een of meer bijlagen aan de taak** toevoegt: Selecteer deze optie om bijlagen in te schakelen voor de taak. Een toegewezen persoon kan de bijlagen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **Uitvoertaakbijlagen opslaan met**: Geef de locatie van de map met bijlagen op. U kunt uitvoertaakbijlagen opslaan met een pad dat is gebaseerd op de laadbewerking of met een variabele van een array van documentgegevenstype. Deze optie wordt alleen weergegeven als u het selectievakje **Toestaan dat een ontvanger een bijlage aan de taak toevoegt** selecteert en **Adaptief formulier**, **Alleen-lezen adaptief formulier** of **Niet-interactief PDF-document** selecteert in de vervolgkeuzelijst **Type** het tabblad **Formulier/Document**.

>[!NOTE]
>
>Gebruik het lusje van Bijlagen in Agent UI tijdens runtime om de gehechtheid aan een Interactieve Mededeling te associëren. De bijbehorende bijlagen worden als taakbijlagen weergegeven in het hulpprogramma nadat het werkitem is geopend in de status Voltooid.

* **Aangepaste metagegevens gebruiken:** selecteer deze optie om het veld Aangepaste metagegevens in te schakelen. Aangepaste metagegevens worden gebruikt in e-mailsjablonen.
* **Aangepaste metagegevens:** selecteer aangepaste metagegevens voor de e-mailsjablonen. De aangepaste metagegevens zijn beschikbaar in de crx-gegevensopslagruimte op apps/fd/dashboard/scripts/metadataScripts. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt. U kunt ook een service gebruiken voor de aangepaste metagegevens. U kunt de interface WorkitemUserMetadataService ook uitbreiden om douanemetagegevens te verstrekken.
* **Gegevens uit vorige stappen** tonen: Schakel deze optie in als u wilt dat toewijzen vorige toewijzingen, reeds uitgevoerde handelingen, aan de taak toegevoegde opmerkingen en het document met de record van de voltooide taak, indien beschikbaar, kunnen weergeven.
* **Gegevens uit volgende stappen tonen:** selecteer deze optie om de huidige ontvanger in staat te stellen de actie te bekijken die is uitgevoerd en de opmerkingen die aan de taak zijn toegevoegd door volgende toewijzingen. Ook kan de huidige toegewezen persoon een document bekijken waarin de voltooide taak is vastgelegd, indien beschikbaar.
* **Zichtbaarheid van gegevenstype:** standaard kan een toegewezen persoon een document met record weergeven, toewijzingen, actie die is uitgevoerd en opmerkingen die door eerdere en volgende toewijzingen zijn toegevoegd. Gebruik de zichtbaarheid van de optie Gegevenstype om het type gegevens te beperken dat zichtbaar is voor de ontvangers.

## E-mailstap verzenden {#send-email-step}

Met de stap E-mail kunt u een e-mail verzenden, bijvoorbeeld een e-mail met een recorddocument, een koppeling van een adaptief formulier, een koppeling van een interactieve communicatie of met een bijgevoegd PDF-document. De stap E-mail verzenden ondersteunt [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). HTML-e-mailberichten reageren en passen zich aan de e-mailclient en schermgrootte van de ontvangers aan. U kunt een HTML-e-mailsjabloon gebruiken om de weergave, het kleurenschema en het gedrag van het e-mailadres te definiëren.

In de e-mailstap wordt de Day CQ Mail Service gebruikt om e-mailberichten te verzenden. Controleer voordat u de e-mailstap gebruikt of [e-mailservice](../../forms/using/aem-forms-workflow.md) is geconfigureerd. De e-mailstap heeft de volgende eigenschappen:

**Titel:** Titel van de stap helpt de stap in de werkstroomeditor te identificeren.

**Beschrijving:** Uitleg is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

**E-mailonderwerp:** Onderwerp kan van een werkschemameta-gegevens worden teruggewonnen, manueel worden gespecificeerd, of uit de waarde worden teruggewonnen die in een variabele wordt opgeslagen. Selecteer een van de volgende opties:

* **Letterlijk -** Geef een onderwerp handmatig op.
* **Haal metagegevens**  van de workflow op - Haal het onderwerp op van een eigenschap metadata.
* **Variabele**  - Haal het onderwerp op van de waarde die in een variabele van het type van koordgegevens wordt opgeslagen.

**HTML-e-mailsjabloon**: HTML-sjabloon voor e-mail. U kunt variabelen in een e-mailsjabloon opgeven. De E-mailstap extraheert en geeft alle variabelen weer die in een sjabloon zijn opgenomen voor invoer.

**Metagegevens van e-mailsjabloon: de** waarde van de sjabloonvariabelen van de e-mail kan een door de gebruiker opgegeven waarde zijn, het pad van een element op de auteur of de publicatieserver, afbeelding of metagegevenseigenschap van de workflow.

* **Letterlijk:** gebruik de optie wanneer u precies weet welke waarde u moet opgeven. Bijvoorbeeld [example@example.com](mailto:example@example.com).

* **Werkstroommetagegevens:** gebruik de optie wanneer de te gebruiken waarde wordt opgeslagen in een werkstroommetagegevenseigenschap. Nadat u de optie hebt geselecteerd, typt u de naam van de eigenschap metadata in het lege tekstvak onder de optie Metagegevens werkstroom. Bijvoorbeeld emailAddress.
* **URL van element:** gebruik de optie om een webkoppeling van een interactieve communicatie naar de e-mail in te sluiten. Nadat u de optie hebt geselecteerd, bladert u door de interactieve communicatie die u wilt insluiten en kiest u deze. Het element kan zich op de auteur of de publicatieserver bevinden.
* **Afbeelding:** gebruik de optie om een afbeelding in te sluiten in de e-mail. Blader en kies de afbeelding nadat u de optie hebt geselecteerd. De afbeeldingsoptie is alleen beschikbaar voor de afbeeldingstags (&lt;img src=&quot;*&quot;/>) die beschikbaar zijn in de e-mailsjabloon.

**E-mailadres van afzender/ontvanger:** selecteer de optie  **** Letterlijk om handmatig een e-mailadres op te geven of selecteer de optie  **Ophalen uit** werkstroommetagegevens om het e-mailadres op te halen uit een eigenschap metadata. U kunt ook een lijst met arrays met metagegevenseigenschappen opgeven voor de optie **Ophalen uit metagegevens van workflow**. Selecteer de optie **Variabele** om het e-mailadres op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

**Bestandsbijlage:** het middel dat beschikbaar is op de opgegeven locatie, is als bijlage bij de e-mail gevoegd. Het pad van het element kan relatief zijn ten opzichte van de payload of het absolute pad. Een voorbeeldpad is [Payload_Directory]/attachments/.

Selecteer de optie **Variabele** om de bestandsbijlage op te halen die is opgeslagen in een variabele van het gegevenstype Document, XML of JSON.

**Bestandsnaam:** naam van het bestand met e-mailbijlagen. Met de E-mailstap wijzigt u de oorspronkelijke bestandsnaam van de bijlage in de opgegeven bestandsnaam. De naam kan handmatig worden opgegeven of opgehaald uit een eigenschap voor metagegevens van een workflow of een variabele. Gebruik de optie **Letterlijk** als u de exacte waarde kent die u wilt opgeven. Gebruik de optie **Variabele** om de bestandsnaam op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. Gebruik de optie **Ophalen uit een werkstroommetagegevens** wanneer de te gebruiken waarde is opgeslagen in een eigenschap voor werkstroommetagegevens.

## Document met recordstap genereren {#generate-document-of-record-step}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Dit wordt bedoeld als Document van Verslag (DoR). Met de stap Document van record genereren kunt u een alleen-lezen of interactieve PDF-versie maken van een adaptief formulier. De PDF-versie bevat informatie die in het formulier is ingevuld en de indeling van het adaptieve formulier.

De stap Document of Record heeft de volgende eigenschappen:

**Adaptief formulier** gebruiken: Geef de methode op om het invoeradaptieve formulier te zoeken. U kunt het adaptieve formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is op een absoluut pad of dat beschikbaar is op een pad in een variabele. U kunt een variabele van het gegevenstype van het Koord gebruiken om de weg in **Uitgezochte variabele te specificeren om** gebied op te lossen.\
U kunt meerdere aangepaste formulieren aan een workflow koppelen. Hierdoor kunt u een adaptief formulier op de runtime opgeven met de beschikbare invoermethoden.

**Adaptief formulierpad**: Geef het pad van het adaptieve formulier op. Het veld is beschikbaar wanneer u de optie **Beschikbaar op een absoluut pad** in het veld **Aangepast formulier gebruiken** selecteert.

**Selecteer Invoergegevens met:** Pad van de invoergegevens voor het adaptieve formulier. U kunt de gegevens op een plaats met betrekking tot de lading houden, een absolute weg van de gegevens specificeren, of gegevens terugwinnen die in een variabele van document, JSON, of het gegevenstype van XML worden opgeslagen. De invoergegevens worden samengevoegd met het aangepaste formulier om een recorddocument te maken.

**Selecteer Invoerpad voor bijlage met:** Pad van de bijlagen. Deze bijlagen worden opgenomen in het document of record. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.

Als u bijvoorbeeld het pad van een map opgeeft, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, gekoppeld aan het document met records. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document of Record. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

**Gegenereerd document van record opslaan met onderstaande opties:** geef de locatie op waar u een document van een recordbestand wilt bewaren. U kunt ervoor kiezen om de ladingsomslag te beschrijven, document van verslag bij een plaats binnen de ladingsfolder te plaatsen, of het document van verslag in een variabele van het gegevenstype van het Document op te slaan.

**Landinstelling**: Geef de taal van het recorddocument op. Selecteer **Letterlijk** om de landinstelling in een vervolgkeuzelijst te selecteren of selecteer **Variabele** om de landinstelling op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. U moet de landinstellingscode definiëren terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **en_US** op voor Engels en **fr_FR** voor Frans.

## De stap Service van het formuliergegevensmodel aanroepen {#invoke-form-data-model-service-step}

Met [AEM Forms Data Integration](../../forms/using/data-integration.md) kunt u verschillende gegevensbronnen configureren en verbinden. Deze gegevensbronnen kunnen een gegevensbestand, de Webdienst, de dienst van REST, de dienst van OData, en oplossing van CRM zijn. Met AEM Forms Data Integration kunt u een formuliergegevensmodel maken dat verschillende services omvat voor het ophalen, optellen en bijwerken van gegevens in de geconfigureerde database. Met de **Gegevensmodelservice aanroepen** kunt u een formuliergegevensmodel (FDM) selecteren en de services van de FDM gebruiken om gegevens op te halen, bij te werken of toe te voegen aan verschillende gegevensbronnen.

Om input voor gebieden van de stap te verklaren, worden de volgende gegevensbestandlijst en het dossier JSON gebruikt als voorbeeld:

**Voorbeeld van tabel met klantgegevens**

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Waarde<br /> </td> 
  </tr> 
  <tr> 
   <td>FirstName<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>LastName</td> 
   <td>Roze</td> 
  </tr> 
  <tr> 
   <td>Klant-id</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>E-mailadres<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Voorbeeld-JSON-bestand**

```json
  { 
    customer: { 
     firstName: "Sarah", 
     lastName:"Rose", 
     customerId: "1", 
     emailAddress:"srose@we.info" 
   }, 
    insurance: {
     customerId: "1", 
    policyType: "Premium,
    policyNumber: "Premium-521499",
    customerDetails: { 
     firstName: "Sarah",
     lastName: "Rose",
     customerId: "1",
     emailAddress: "srose@we.info" 
    }
   }
  }
```

Voor de stap Service van het formuliergegevensmodel aanroepen worden de onderstaande velden weergegeven, waarmee bewerkingen in het formuliergegevensmodel worden vergemakkelijkt:

* **Titel:** Titel van de stap. Het helpt de stap in de werkschemaredacteur identificeren.
* **Beschrijving:** Uitleg nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Pad** formuliergegevensmodel: Blader naar een formuliergegevensmodel op de server en selecteer dit.

* **Service**: Lijst met services die worden geleverd door het geselecteerde formuliergegevensmodel.
* **Invoer voor services > Invoergegevens opgeven met letterlijke metagegevens, metagegevens over variabelen of workflows en een JSON-bestand**: Een service kan meerdere argumenten hebben. Selecteer de optie om de waarde van de de dienstargumenten van een werkschemabezit, een voorwerp JSON, een variabele te verkrijgen, of direct de waarde in het verstrekte tekstvakje in te gaan:

   * **Letterlijk:** gebruik de optie wanneer u precies weet welke waarde u moet opgeven. Bijvoorbeeld srose@we.info.
   * **Variabele:** gebruik de optie om de waarde op te halen die in een variabele is opgeslagen.
   * **Ophalen uit metagegevens van workflow:** gebruik de optie wanneer de te gebruiken waarde wordt opgeslagen in een eigenschap voor metagegevens van workflow. Bijvoorbeeld emailAddress.
   * **[!UICONTROL Relative to Payload]**: Gebruik de optie om de bestandsbijlage op te halen die is opgeslagen op een pad dat relatief is ten opzichte van de laadbewerking. Selecteer de optie en geef de mapnaam op die de bestandsbijlage bevat of geef de naam van de bestandsbijlage op in het tekstvak.

      Als de map Relatief aan Payload in de CRX-opslagplaats bijvoorbeeld een bestandsbijlage bevat op de locatie `attachment\attachment-folder`, geeft u `attachment\attachment-folder` in het tekstvak op nadat u de optie **[!UICONTROL Relative to Payload]** hebt geselecteerd.
   * **JSON-puntnotatie:** gebruik de optie wanneer de te gebruiken waarde zich in een JSON-bestand bevindt. Bijvoorbeeld verzekering.customerDetails.emailAddress. De optie Puntnotatie JSON is alleen beschikbaar als de optie Invoervelden toewijzen van invoer-JSON is geselecteerd.
   * **Wijs invoervelden toe vanuit invoer-JSON:** geef het pad van een JSON-bestand op om de invoerwaarde van sommige serviceargumenten op te halen uit het JSON-bestand. Het pad van het JSON-bestand kan relatief zijn ten opzichte van de payload, een absoluut pad of u kunt een invoer-JSON-document selecteren met een variabele van het type JSON- of Formuliergegevensmodel.

* **Invoer voor services > Invoergegevens opgeven met behulp van een variabele of een JSON-bestand:** Selecteer de optie om waarden op te halen voor alle argumenten in een JSON-bestand dat is opgeslagen op een absoluut pad, een pad dat relatief is ten opzichte van de payload of in een variabele.
* **Invoerdocument selecteren met**: Het JSON-bestand met waarden voor alle serviceargumenten. Het pad van het JSON-bestand kan **relatief zijn ten opzichte van de payload** of een **absoluut pad.** U kunt het invoer-JSON-document ook ophalen met behulp van een variabele van het gegevenstype JSON of Form Data Model.

* **JSON-puntnotatie:** laat het veld leeg om alle objecten van het opgegeven JSON-bestand als invoer voor serviceargumenten te gebruiken. Als u een specifiek JSON-object uit het opgegeven JSON-bestand wilt lezen als invoer voor serviceargumenten, geeft u puntnotatie voor het JSON-object op. Als u bijvoorbeeld een JSON-object hebt dat vergelijkbaar is met de JSON-object dat aan het begin van de sectie wordt vermeld, geeft u Insurance.customerDetails op om alle details van een klant als invoer voor de service op te geven.
* **Uitvoer van service > Uitvoerwaarden toewijzen en schrijven naar variabele of metagegevens:** selecteer de optie om de uitvoerwaarden op te slaan als eigenschappen van het metagegevensknooppunt voor workflowinstanties in de crx-gegevensopslagruimte. Specificeer de naam van het meta-gegevensbezit en selecteer het overeenkomstige attribuut van de de dienstoutput dat met meta-gegevensbezit moet worden in kaart gebracht, bijvoorbeeld, phone_number dat door de outputdienst met het phone_number bezit van werkschemameta-gegevens is teruggekeerd. Op dezelfde manier kunt u de uitvoer opslaan in een variabele van het gegevenstype Long. Wanneer u een eigenschap voor de optie **[!UICONTROL Service output attribute to be mapped]** selecteert, worden alleen variabelen die gegevens van de geselecteerde eigenschap kunnen opslaan, gevuld voor de optie **[!UICONTROL Save the output to]**.

* **Uitvoer van service > Uitvoer opslaan naar variabele of een JSON-bestand:** selecteer de optie om de uitvoerwaarden in een JSON-bestand op te slaan op een absoluut pad, een pad dat relatief is ten opzichte van de laadbewerking of in een variabele.
* **Sla het JSON-uitvoerdocument op met de onderstaande opties:** Sla het JSON-uitvoerbestand op. Het pad van het JSON-uitvoerbestand kan relatief zijn ten opzichte van de payload of een absoluut pad. U kunt het JSON-uitvoerbestand ook opslaan met een variabele van het gegevenstype JSON of Form Data Model.

## stap Document ondertekenen {#sign-document-step}

Met de stap Document ondertekenen kunt u Adobe Sign gebruiken om documenten te ondertekenen. De stap Document ondertekenen heeft de volgende eigenschappen:

* **Naam van overeenkomst:** geef de titel van de overeenkomst op. De naam van de overeenkomst wordt onderdeel van het onderwerp en de hoofdtekst van de e-mail die naar de ondertekenaars wordt verzonden. U kunt of de naam in een variabele van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om de naam manueel toe te voegen.

* **Landinstelling:** geef de taal op voor de opties voor e-mail en verificatie. U kunt de landinstelling opslaan in een variabele van het gegevenstype String of **Letterlijk** selecteren om de landinstelling te kiezen in de lijst met beschikbare opties. U moet de landinstellingscode definiëren terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **en_US** op voor Engels en **fr_FR** voor Frans.

* **Adobe Sign Cloud Configuration**: Kies een Adobe Sign Cloud-configuratie. Als u Adobe Sign for AEM Forms niet hebt geconfigureerd, raadpleegt u [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

* **Selecteer Document dat u wilt ondertekenen met:** U kunt een document kiezen op een locatie die relatief is ten opzichte van de lading, de lading gebruiken als document, een absoluut pad van het document opgeven of het document ophalen dat is opgeslagen in een variabele van het gegevenstype Document.
* **Dagen tot deadline:** Een document wordt opgemaakt als opeisbaar (verstreken deadline) nadat er geen activiteit op de taak is gedurende het aantal dagen dat is opgegeven in de  **dagen tot** aan-deadline. Het aantal dagen wordt geteld nadat het document is toegewezen aan een gebruiker voor ondertekening.
* **E-mailfrequentie herinnering:** U kunt een herinnering per dag of per week per e-mail verzenden. De week wordt geteld vanaf de dag waarop de documentatie aan een gebruiker is toegewezen voor ondertekening.
* **Handtekeningproces:** u kunt ervoor kiezen om een document in een opeenvolgende of parallelle volgorde te ondertekenen. Eén ondertekenaar ontvangt het document op volgorde voor ondertekening. Nadat de eerste ondertekenaar het ondertekenen van het document heeft voltooid, wordt het document verzonden naar de tweede ondertekenaar, enzovoort. Parallel hieraan kunnen meerdere ondertekenaars een document tegelijk ondertekenen.
* **URL omleiden:URL omleiden** opgeven. Nadat het document is ondertekend, kunt u de ontvanger omleiden naar een URL. Gewoonlijk bevat deze URL een bedankbericht of verdere instructies.
* **Werkstroomwerkgebied:** een werkstroom kan meerdere fasen hebben. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Selecteren > Pagina > Pagina-eigenschappen > Staven).
* **Selecteer Ondertekenaars:** Geef de methode op waarmee u ondertekenaars voor het document wilt kiezen. U kunt de workflow dynamisch toewijzen aan een gebruiker of groep of gegevens van een ondertekenaar handmatig toevoegen.
* **Script of service om ondertekenaars te selecteren:** de optie is alleen beschikbaar als de optie Dynamisch is geselecteerd in het veld Ondertekenaars selecteren. U kunt een ECMAScript of een dienst specificeren om ondertekenaars en verificatieopties voor een document te kiezen.
* **Details ondertekenaar:** de optie is alleen beschikbaar als de optie Handmatig is geselecteerd in het veld Ondertekenaars selecteren. Geef een e-mailadres op en kies een optioneel verificatiemechanisme. Voordat u een verificatiemechanisme met twee stappen selecteert, moet u controleren of de bijbehorende verificatieoptie is ingeschakeld voor de geconfigureerde Adobe Sign-account. U kunt een variabele van het gegevenstype String gebruiken om waarden te definiëren voor **[!UICONTROL Email]**-, **[!UICONTROL Country Code]**- en **[!UICONTROL Phone Number]**-velden. De velden **[!UICONTROL Country Code]** en **[!UICONTROL Phone Number]** worden alleen weergegeven als u **[!UICONTROL Phone Verification]** in de vervolgkeuzelijst **[!UICONTROL 2-step verification]** selecteert.
* **Statusvariabele:In** een door Adobe Sign ingeschakeld document wordt de ondertekeningsstatus van het document opgeslagen in een variabele van het gegevenstype String. Geef de naam van de statusvariabele op (adobeSignStatus). Een statusvariabele van een instantie is beschikbaar in CRXDE op /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData bevat status van een variabele.
* **Ondertekend document opslaan met onderstaande opties:** Geef de locatie op waar u ondertekende documenten wilt behouden. U kunt ervoor kiezen het ladingsdossier te overschrijven, het ondertekende document bij een plaats binnen de ladingsfolder te plaatsen, of het ondertekende document op te slaan in een variabele van het type van Document.

## Stappen voor Document Services {#document-services-steps}

AEM Document Services is een set services voor het maken, samenstellen en beveiligen van PDF-documenten. AEM Forms biedt een aparte AEM Workflowstap voor elke documentservice.

Net als bij andere AEM Forms-workflowstappen, zoals Taak toewijzen, E-mail verzenden en Document ondertekenen, kunt u variabelen gebruiken in alle stappen van AEM Document Services. Zie [Variabelen in AEM workflows](../../forms/using/variable-in-aem-workflows.md) voor meer informatie over het maken en beheren van variabelen.

### Tijdstempel document toepassen {#apply-document-time-stamp-step}

Tijdstempel toevoegen aan een document. U geeft documentgegevens op, zoals het pad van het invoerdocument, de naam van het invoerdocument en de locatie waar de geëxporteerde gegevens moeten worden opgeslagen. U kunt desgewenst het bestaande ladingsbestand overschrijven, een andere bestandsnaam kiezen om gegevens op te slaan in een ander bestand onder de ladingmap, een absoluut pad naar de gegevens opgeven of gegevens opslaan in een variabele van het gegevenstype Document.

### Omzetten in afbeeldingsstap {#convert-to-image-step}

Hiermee wordt een PDF-document geconverteerd naar een lijst met afbeeldingen. Ondersteunde afbeeldingsindelingen zijn JPEG, JPEG2000, PNG en TIFF. De volgende informatie is van toepassing op conversies naar TIFF-afbeeldingen:

* Er wordt een TIFF-bestand met meerdere pagina&#39;s gegenereerd.
* Niet alle annotaties zijn opgenomen in TIFF-afbeeldingen. Annotaties waarvoor Acrobat de weergave moet genereren, worden niet opgenomen.

### Converteren naar PDF/A-stap {#convert-to-pdf-a-step}

Hiermee wordt een PDF-document naar PDF/A-indeling geconverteerd met de beschikbare opties. De PDF/A-versie van Portable Document Format (PDF) is gespecialiseerd in het archiveren en het op lange termijn bewaren van documenten.

### Omzetten in PS-stap {#convert-to-ps-step}

Converteer PDF-documenten naar PostScript. Bij het converteren naar PostScript kunt u het brondocument met de conversiebewerking opgeven en of het document moet worden omgezet in PostScript-niveau 2 of 3. Het PDF-document dat u naar een PostScript-bestand converteert, moet niet-interactief zijn.

### PDF maken van opgegeven tekststap {#create-pdf-from-specified-type-step}

Genereer een PDF-document op basis van een invoerbestand. Het invoerdocument kan relatief zijn ten opzichte van de payload, een absoluut pad hebben, kan zelf worden geladen of worden opgeslagen in een variabele van het gegevenstype Document.

### PDF maken van stap URL/HTML/ZIP {#create-pdf-from-url-html-zip-step}

Hiermee genereert u een PDF-document op basis van de opgegeven URL-, HTML- en ZIP-bestanden.

### Gegevensstap exporteren {#export-data-step}

Hiermee exporteert u gegevens uit een PDF forms- of XDP-bestand. Hiervoor moet u het bestandspad van Invoerdocument en de indeling Gegevens exporteren invoeren. De opties voor de Indeling van de Gegevens van de Uitvoer zijn Auto, XDP en XmlData.

### Export PDF naar opgegeven tekststap {#export-pdf-to-specified-type-step}

Hiermee converteert u een PDF-document naar een geselecteerde indeling.

### Niet-interactieve PDF-stap genereren {#generatenoninteractive}

Een niet-interactieve PDF genereren. Het biedt verschillende aanpassingsopties.

>[!NOTE]
>
>Met variabelen kunt u het sjabloonbestand voor invoerdocumenten opgeven. Sla het pad van het sjabloonbestand op in een variabele van het gegevenstype String.

### Gegevensstap importeren {#import-data-step}

Hiermee voegt u formuliergegevens samen tot een PDF-formulier. U kunt formuliergegevens importeren in een PDF-formulier.

### DDX-stap aanroepen {#invokeddx}

Hiermee wordt het DDX-bestand uitgevoerd op de opgegeven kaart met invoerdocumenten en worden de gemanipuleerde PDF-documenten geretourneerd.

>[!NOTE]
>
>U kunt variabelen gebruiken om het DDX-bestand voor invoerdocumenten op te geven. Sla het DDX-bestand op in een variabele van het gegevenstype Document of XML.

### Optimize PDF-stap {#optimize-pdf-step}

Hiermee optimaliseert u PDF-bestanden door de grootte ervan te verkleinen. Het resultaat van deze conversie zijn PDF-bestanden die mogelijk kleiner zijn dan de oorspronkelijke versie. Met deze bewerking worden PDF-documenten ook geconverteerd naar de PDF-versie die is opgegeven in de optimalisatieparameters.

Optimalisatie-instellingen bepalen hoe bestanden worden geoptimaliseerd. Hier volgen voorbeelden van instellingen:

* Doelversie PDF
* Objecten zoals JavaScript-handelingen en ingesloten paginaminiaturen negeren
* Gebruikersgegevens zoals opmerkingen en bestandsbijlagen negeren
* Ongeldige of ongebruikte instellingen negeren
* Niet-gecomprimeerde gegevens comprimeren of efficiëntere compressiealgoritmen gebruiken
* Ingesloten lettertypen verwijderen
* Transparantiewaarden instellen

### PDF-formulierstap renderen {#renderpdf}

Hiermee maakt u een formulier dat is gemaakt in Form Designer (XDP), naar een PDF-formulier.

>[!NOTE]
>
>Met variabelen kunt u het sjabloonbestand voor invoerdocumenten opgeven. Sla het pad van het sjabloonbestand op in een variabele van het gegevenstype String.

### Stap voor beveiligd document {#secure-document-step}

Een document versleutelen, ondertekenen en certificeren. AEM Forms ondersteunt zowel op wachtwoorden gebaseerde versleuteling als versleuteling op basis van certificaten. U kunt ook kiezen uit verschillende algoritmen voor het ondertekenen van documenten. Bijvoorbeeld SHA-256 en SH-512. U kunt de workflowstap ook gebruiken om PDF-documenten door te lezen. De workflowstap biedt opties voor het decoderen van streepjescodes, digitale handtekeningen, het importeren en exporteren van PDF-gegevens en andere opties.

### Verzenden naar printer, stap {#send-to-printer-step}

Een document rechtstreeks naar een printer verzenden. De volgende toegangsmechanismen voor afdrukken worden ondersteund:

* **Direct toegankelijke printer**: Een printer die op dezelfde computer is geïnstalleerd, wordt een direct toegankelijke printer genoemd en de computer krijgt de naam van de printerhost. Dit type printer kan een lokale printer zijn die rechtstreeks op de computer is aangesloten.
* **Indirecte toegankelijke printer**: De printer die op een afdrukserver is geïnstalleerd, is toegankelijk vanaf andere computers. Technologieën zoals het algemene UNIX®-afdruksysteem (CUPS) en het Line Printer Daemon-protocol (LPD) zijn beschikbaar voor verbinding met een netwerkprinter. Als u toegang wilt tot een indirecte toegankelijke printer, geeft u de IP of hostnaam van de afdrukserver op. Met behulp van dit mechanisme kunt u een document naar een LPD URI verzenden wanneer het netwerk een LPD loopt. Met het mechanisme kunt u het document doorsturen naar elke printer die is aangesloten op het netwerk waarop een LPD-scherm wordt uitgevoerd.

### Afgedrukte uitvoerstap genereren {#generatePrintedOutput}

De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer op basis van een formulierontwerp en een gegevensbestand. Het gegevensbestand wordt samengevoegd met het formulierontwerp en voor afdrukken opgemaakt. De uitvoer die door deze stap wordt gegenereerd, kan rechtstreeks naar een printer worden verzonden of als bestand worden opgeslagen. U wordt aangeraden deze stap te gebruiken als u formulierontwerpen of gegevens uit een toepassing wilt gebruiken. Als uw formulierontwerpen of formulierontwerpen zich op het netwerk, het lokale bestandssysteem of de HTTP-locatie bevinden, gebruikt u de bewerking generatePrintedOutput.

Uw toepassing vereist bijvoorbeeld dat u een formulierontwerp samenvoegt met een gegevensbestand. De gegevens bevatten honderden records. Bovendien moet de uitvoer worden verzonden naar een printer die ZPL ondersteunt. Het formulierontwerp en uw invoergegevens bevinden zich in een toepassing. Met de bewerking generatePrintedOutput kunt u elke record samenvoegen met een formulierontwerp en de uitvoer verzenden naar een printer die ZPL ondersteunt.

De stap Afgedrukte uitvoer genereren heeft de volgende eigenschappen:

**Invoereigenschappen**

* **[!UICONTROL Select template file using]**: Geef het pad van het sjabloonbestand op. U kunt het sjabloonbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld [Payload_Directory]/Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt. Bovendien kunt u ook payload accepteren als het invoergegevensbestand.

* **[!UICONTROL Select data document using]**: Geef het pad van een invoergegevensbestand op. U kunt het invoergegevensbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld [Payload_Directory]/Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

* **[!UICONTROL Printer Format]**: Een waarde in de indeling Afdrukken die aangeeft welke paginabeschrijvingstaal moet worden gebruikt om de uitvoerstroom te genereren wanneer geen XDC-bestand wordt geleverd. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:

   * **[!UICONTROL Custom PCL]**: Gebruik de optie om een aangepast XDC-bestand voor PCL op te geven.
   * **[!UICONTROL Custom PostScript]**: Gebruik de optie om een aangepast XDC-bestand voor PostScript op te geven.
   * **[!UICONTROL Custom ZPL]**: Gebruik de optie om een aangepast XDC-bestand op te geven voor ZPL.
   * **[!UICONTROL Generic Color PCL (5c)]**: Gebruik een algemene kleur PCL (5c).
   * **[!UICONTROL Generic PostScript Level3]**: Gebruik algemeen PostScript Level 3.
   * **[!UICONTROL ZPL 300 DPI]**: Gebruik ZPL 300 DPI. Zpl300.xdc wordt gebruikt.
   * **[!UICONTROL ZPL 600 DPI]**: Gebruik ZPL 600 DPI. Het bestand zpl600.xdc wordt gebruikt.
   * **[!UICONTROL Custom IPL]**: Gebruik de optie om een aangepast XDC-bestand voor IPL op te geven.
   * **[!UICONTROL IPL 300 DPI]**: Gebruik IPL 300 DPI. Het bestand ipl300.xdc wordt gebruikt.
   * **[!UICONTROL IPL 400 DPI]**: Gebruik IPL 400 DPI. Het bestand ipl400.xdc wordt gebruikt.
   * **[!UICONTROL Custom TPCL]**: Gebruik de optie om een aangepast XDC-bestand voor TPCL op te geven.
   * **[!UICONTROL TPCL 305 DPI]**: Gebruik TPCL 300 DPI. Het bestand tpcl305.xdc wordt gebruikt.
   * **[!UICONTROL PCL 600 DPI]**: Gebruik TPCL 600 DPI. Het bestand tpcl600.xdc wordt gebruikt.
   * **[!UICONTROL Custom DPL]**: Gebruik de optie om een aangepast XDC-bestand DPL op te geven.
   * **[!UICONTROL DPL300DPI]**: Gebruik DPL 300 DPI. Het bestand dpl300.xdc wordt gebruikt.
   * **[!UICONTROL DPL406DPI]**: Gebruik DPL 400 DPI. Het bestand dpl406.xdc wordt gebruikt.
   * **[!UICONTROL DPL600DPI]**: Gebruik DPL 600 DPI. De dpl600.xdc wordt gebruikt.

**Uitvoereigenschappen**

* **[!UICONTROL Save output document using]**: Geef de locatie op waar u het uitvoerbestand wilt opslaan. U kunt het uitvoerbestand opslaan op een locatie die relatief is ten opzichte van de lading, in een variabele of een absolute locatie opgeven om het uitvoerbestand op te slaan. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

**Geavanceerde eigenschappen**

* **[!UICONTROL Select Content Root location using]**: De inhoudsbasis is een tekenreekswaarde die de URI, absolute referentie of locatie in de gegevensopslagruimte opgeeft voor het ophalen van relatieve elementen die door het formulierontwerp worden gebruikt. Als het formulierontwerp bijvoorbeeld relatief verwijst naar een afbeelding, zoals ../myImage.gif, moet myImage.gif zich op repository:// bevinden. De standaardwaarde is repository://. Deze verwijst naar het hoofdniveau van de opslagplaats.

   Wanneer u een element kiest uit uw toepassing, moet het pad van de URI van de inhoudsbasis de juiste structuur hebben. Als bijvoorbeeld een formulier wordt gekozen uit een toepassing met de naam SampleApp en wordt geplaatst op SampleApp/1.0/forms/Test.xdp, moet de URI van de inhoudswortel worden opgegeven als repository://administrator@password/Applications/SampleApp/1.0/forms/ of gegevensopslagruimte:/Applications/SampleApp/1.0/forms/ (als de bevoegdheid null is). Wanneer de URI voor de inhoudsbasis op deze manier wordt opgegeven, worden de paden van alle middelen waarnaar wordt verwezen in het formulier, omgezet met deze URI.

* **[!UICONTROL Select XCI file using]**: XCI-bestanden worden gebruikt om lettertypen en andere eigenschappen te beschrijven die voor formulierontwerpelementen worden gebruikt. U kunt een XCI-bestand relatief ten opzichte van de payload, op een absoluut pad houden of een variabele van het gegevenstype Document gebruiken.

* **[!UICONTROL Locale]**: Hier geeft u de taal op die wordt gebruikt voor het genereren van het PDF-document. Als u een letterlijke waarde opgeeft, selecteert u een taal in de lijst of selecteert u een van de volgende waarden:
   * **Als u de standaardinstelling** van de server wilt gebruiken: (Standaard) Gebruik de landinstelling die is geconfigureerd op de AEM Forms-server. De landinstelling wordt geconfigureerd met de beheerconsole. (Zie [Designer Help](http://www.adobe.com/go/learn_aemforms_designer_65).)

   * **Aangepaste waarde** gebruiken: Typ de landinstellingscode in het letterlijke vak of selecteer een tekenreeksvariabele die de landinstellingscode bevat. Ga naar http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html voor een volledige lijst met ondersteunde landinstellingscodes.

* **[!UICONTROL Copies]**: Een geheel getal dat aangeeft hoeveel exemplaren voor de uitvoer moeten worden gegenereerd. De standaardwaarde is 1.

* **[!UICONTROL Duplex Printing]**: Een pagineringswaarde die aangeeft of dubbelzijdig of enkelzijdig afdrukken moet worden gebruikt. Deze waarde wordt gebruikt voor printers die PostScript en PCL ondersteunen. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:
   * **[!UICONTROL Duplex Long Edge]**: Dubbelzijdig afdrukken en afdrukken met paginering met lange randen.
   * **[!UICONTROL Duplex Short Edge]**: Dubbelzijdig afdrukken en afdrukken met korte paginering.
   * **[!UICONTROL Simplex]**: Enkelzijdig afdrukken gebruiken.
