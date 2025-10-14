---
title: Forms-centric workflow voor OSGi - Step Reference
description: Met een Forms-gerichte workflow voor OSGi-stappen kunt u snel adaptieve formulieren op basis van workflows maken.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: 470fcfda-dfde-437c-b539-d5af1e13a7d6
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '7512'
ht-degree: 0%

---

# Forms-centric workflow voor OSGi - Step Reference {#forms-centric-workflow-on-osgi-step-reference}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

U gebruikt workflowmodellen om een bedrijfslogica om te zetten in een geautomatiseerd, zich herhalend proces. Met behulp van een model kunt u een reeks stappen definiëren en uitvoeren. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt. U kunt [&#x200B; diverse AEM stappen van het Werkschema in een model omvatten om de bedrijfslogica &#x200B;](/help/sites-developing/workflows-models.md#extending-aem) te bereiken.

## Stappen Forms Workflow {#forms-workflow-steps}

Forms Workflows voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel adaptieve formulieren maken op basis van een Forms-gerichte workflow op OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne en interne bedrijfsprocessen binnen de firewall. U kunt ook de stappen van de Forms Workflow gebruiken om documentservices te starten, te integreren met de Adobe Sign-handtekeningworkflow en andere AEM Forms-bewerkingen uit te voeren. U vereist [&#x200B; toe:voegen-op van AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_documentation_63) om deze stappen in een werkschema te gebruiken.

Forms-centric workflowstappen voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel een op Adaptive Forms gebaseerde Forms-gerichte workflow bouwen op OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne processen en bedrijfsprocessen binnen de firewall.

>[!NOTE]
>
>Als het workflowmodel is gemarkeerd voor externe opslag, kunt u voor alle stappen in de Forms Workflow alleen de optie voor het opslaan of ophalen van gegevensbestanden en bijlagen selecteren.

## Taakstap toewijzen {#assign-task-step}

De taakstap toewijzen maakt een taak en wijst deze toe aan een gebruiker of groep. Naast het toewijzen van de taak geeft de component ook het adaptieve formulier of de niet-interactieve PDF voor de taak op. Het adaptieve formulier is vereist om invoer van gebruikers te accepteren en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie dienen.

U kunt de component ook gebruiken om het gedrag van de taak te controleren. Bijvoorbeeld, creërend een automatisch document van verslag, toewijzend de taak aan een specifieke gebruiker of een groep, specificerend de weg van de voorgelegde gegevens, specificerend de weg van te vullen gegevens, en specificerend standaardacties. De stap Taak toewijzen heeft de volgende eigenschappen:

* **Titel:** Titel van de taak. De titel wordt weergegeven in AEM Postvak IN.
* **Beschrijving:** Verklaring van de verrichtingen die in de taak worden uitgevoerd. Deze informatie is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Weg van de Duimnagel van de Duimnagel:** Weg van de taakduimnagel. Als er geen pad is opgegeven, wordt voor een aangepaste standaardminiatuur van het formulier weergegeven en voor Document of Record, een standaardpictogram weergegeven.
* **Stadium van het Werkschema:** Een werkschema kan veelvoudige stadia hebben. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Sidekick > Pagina > Pagina-eigenschappen > Staven).
* **Prioriteit:** Geselecteerde prioriteit wordt getoond in AEM Inbox. De beschikbare opties zijn Hoog, Medium en Laag. De standaardwaarde is Medium.
* **Verschuldigde Datum:** specificeer het aantal dagen of uren waarna de taak achterstallig is. Als u **van** selecteert, dan is de taak nooit duidelijk achterstallig. U kunt ook een time-outhandler opgeven om specifieke taken uit te voeren nadat de taak is uitgevoerd.

* **Dagen:** Het aantal dagen vóór welke de taak moet worden voltooid. Het aantal dagen wordt geteld nadat de taak aan een gebruiker is toegewezen. Als een taak niet volledig is en het aantal dagen overschrijdt dat op het gebied van Dagen specificeert dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de vervaldatum.
* **Uren:** Het aantal uren alvorens de taak moet worden voltooid. Het aantal uren wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal uren overschrijdt specificeert op het gebied van Uren dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de verschuldigde uren.
* **Tijd-uit na Verschuldigde Datum:** selecteer deze optie om het de selectiegebied van de Handler van de Onderbreking toe te laten.
* **manager van de Onderbreking:** selecteer het manuscript dat moet worden uitgevoerd wanneer de taakstap de verouderde datum overgaat. De manuscripten die in CRX-bewaarplaats bij [ worden geplaatst apps ]/fd/dashboard/scripts/timeoutHandler zijn beschikbaar voor selectie. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt.
* **benadruk de actie en de commentaar van de laatste taak in de Details van de Taak:** selecteer deze optie om de laatste actie te tonen die werd genomen en commentaar dat op de sectie van taakdetails van een taak werd ontvangen.
* **Type:** kies het type van document dat moet worden gevuld wanneer het werkschema is begonnen. U kunt een adaptief formulier, alleen-lezen adaptief formulier, een niet-interactief PDF-document, de gebruikersinterface van de interactieve communicatieagent of het interactieve communicatie webkanaaldocument kiezen.
* **Aangepaste Vorm van het Gebruik:** specificeer de methode om van de input adaptieve vorm de plaats te bepalen. Deze optie is beschikbaar als u Adaptief formulier of Alleen-lezen adaptief formulier selecteert in de vervolgkeuzelijst Type. U kunt het adaptieve formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is op een absoluut pad of dat beschikbaar is op een pad in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven.\
  U kunt meerdere aangepaste formulieren aan een workflow koppelen. Hierdoor kunt u een adaptief formulier op de runtime opgeven met de beschikbare invoermethoden.

* **Interactieve Communicatie van het Gebruik:** specificeer de methode om van de input interactieve mededeling de plaats te bepalen. U kunt de interactieve communicatie gebruiken die aan het werkschema wordt voorgelegd, beschikbaar bij een absolute weg, of beschikbaar bij een weg in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven. Deze optie is beschikbaar als u Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.

>[!NOTE]
>
>U moet cm-agent-gebruikers en werkschema-gebruikers groepstaken hebben om tot Interactieve Communicatie Agent UI in AEM Inbox toegang te hebben.

* **Aangepaste Vorm of Interactieve Communicatie Weg**: Specificeer de weg van de adaptieve vorm of de Interactieve Communicatie. U kunt het aangepaste formulier of de interactieve communicatie gebruiken die naar de workflow wordt verzonden, beschikbaar via een absoluut pad, of het aangepaste formulier ophalen via een pad dat is opgeslagen in een variabele van het type tekenreeksgegevens.
* **Uitgezochte input PDF gebruikend:** specificeer de weg van een niet-interactief document van de PDF. Het veld is beschikbaar wanneer u een niet-interactief PDF-document kiest in het veld Type. U kunt de invoer-PDF selecteren met behulp van het pad dat relatief is ten opzichte van de payload, opgeslagen op een absoluut pad of met behulp van een variabele van het gegevenstype Document. Bijvoorbeeld, [ Payload_Directory ] /Workflow/PDF/credit-card.pdf. Het pad bestaat niet in crx-repository. Een beheerder maakt het pad voordat het wordt gebruikt. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om de optie PDF Path te kunnen gebruiken.
* **voor voltooide taak, geef de adaptieve vorm als** terug: Wanneer een taak volledig duidelijk is, kunt u de adaptieve vorm als read-only adaptieve vorm of een document van de PDF teruggeven. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om het adaptieve formulier weer te geven als Document of Record.
* **pre-bevolkt:** de volgende hieronder vermelde gebieden dienen als input aan de taak:

   * **[!UICONTROL Select input data file using]**: pad van invoergegevensbestand (.json, .xml, .doc of formuliergegevensmodel). U kunt het invoergegevensbestand terugwinnen gebruikend een weg die met betrekking tot de lading is of het dossier terugwinnen dat in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen. Het bestand bevat bijvoorbeeld de gegevens die via een AEM Inbox-toepassing voor het formulier zijn verzonden. Een voorbeeldweg is [ Payload_Directory ]/workflow/data.

   * **Uitgezochte inputgehechtheid gebruikend:** de gehechtheid beschikbaar bij de plaats is in bijlage aan de vorm verbonden aan de taak. Het pad kan relatief zijn ten opzichte van de lading of de bijlagen ophalen die zijn opgeslagen in een variabele van het type ArrayList of Document. Een voorbeeldweg is [ Payload_Directory ] /attachments/. U kunt bijlagen opgeven die relatief zijn ten opzichte van de lading of een variabele van het documenttype (Array-lijst > Document) gebruiken om een invoerbijlage op te geven voor het adaptieve formulier.

      * **kies input JSON:** selecteer een inputJSON dossier gebruikend een weg die met lading of opgeslagen in een variabele van Document, JSON, of het gegevenstype van het Model van de Gegevens van de Vorm met betrekking tot lading is. Deze optie is beschikbaar als u Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.
      * **kies een douane prefill dienst:** selecteer de prefill dienst om de gegevens terug te winnen en het Interactieve Communicatie het kanaaldocument van het Web of de Agent UI vooraf in te vullen.
      * **gebruik de prefill dienst van de interactieve hierboven geselecteerde mededeling:** gebruik deze optie om de prefill dienst van de Interactieve Communicatie te gebruiken die in de Van het Gebruik Interactieve Communicatie drop-down lijst wordt bepaald.
      * **Toewijzing van Attributen van het Verzoek:** gebruik de sectie van de Toewijzing van het Attributen van het Verzoek om de [&#x200B; naam en de waarde van de verzoekattributen &#x200B;](../../forms/using/work-with-form-data-model.md#bindargument) te bepalen. Haal de details van de gegevensbron op die op de attributennaam en waarde wordt gebaseerd in het verzoek wordt gespecificeerd. U kunt een waarde van een aanvraagkenmerk definiëren met een letterlijke waarde of een variabele van het gegevenstype String.\
        De prefill dienst en de opties van de verzoekkenmerkafbeelding zijn beschikbaar slechts als u het Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.

* **voorgelegde informatie:** De volgende hieronder vermelde gebieden dienen als outputplaatsen aan de taak:

   * **sparen dossier van outputgegevens gebruikend:** sparen het gegevensbestand (.json,. XML, .doc of formuliergegevensmodel). Het gegevensbestand bevat informatie die via het bijbehorende formulier is verzonden. U kunt het uitvoergegevensbestand opslaan met een pad dat relatief is ten opzichte van de lading of dit opslaan in een variabele van het gegevenstype Document, XML of JSON. Bijvoorbeeld, [ Payload_Directory ]/Workflow/data, waar het gegeven een dossier is.
   * **sparen gehechtheid gebruikend:** sparen de vormgehechtheid verstrekt in een taak. U kunt de bijlagen opslaan met een pad dat relatief is ten opzichte van de lading of deze opslaan in een variabele van een array van documentgegevenstype.
   * **sparen Document van Verslag gebruikend:** Weg om een Document van het dossier van het Verslag te bewaren. Bijvoorbeeld, [ Payload_Directory ] /DocumentofRecord/credit-card.pdf. U kunt het Document van Verslag bewaren gebruikend een weg die met betrekking tot de lading is of het opslaan in een variabele van het gegevenstype van het Document. Als u **met betrekking tot** optie van de Lading selecteert, wordt het Document van Verslag niet geproduceerd als het weggebied leeg is. Deze optie is alleen beschikbaar als u Adaptief formulier selecteert in de vervolgkeuzelijst Type.

   * **sparen de gegevens van het Kanaal van het Web gebruikend:** sparen het de gegevensdossier van het Kanaal van het Web gebruikend een weg die met betrekking tot de lading is of het opslaat in een variabele van Document, JSON, of het gegevenstype van het Model van de Gegevens van de Vorm. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.
   * **sparen het document van de PDF gebruikend:** sparen het document van de PDF gebruikend een weg die met betrekking tot de nuttige lading is of het opslaat in een variabele van het gegevenstype van het Document. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.
   * **sparen lay-outmalplaatje gebruikend:** sparen het lay-outmalplaatje gebruikend een weg die met betrekking tot de lading is of het opslaat in een variabele van het gegevenstype van het Document. Het [&#x200B; lay-outmalplaatje &#x200B;](../../forms/using/layout-design-details.md) verwijst naar een XDP dossier dat u gebruikend Forms Designer creeert. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.

* **toewijzen de Wijs opties toe:** specificeer de methode om de taak aan een gebruiker toe te wijzen. U kunt de taak dynamisch toewijzen aan een gebruiker of groep met behulp van het script Deelnemerkiezer of u kunt de taak toewijzen aan een specifieke AEM gebruiker of groep.
* **Kiezer van de Deelnemer:** de optie is beschikbaar wanneer **dynamisch aan een gebruiker of een groep** optie op het Assign optiesgebied wordt geselecteerd. U kunt een ECMAScript of de dienst gebruiken om een gebruiker of een groep dynamisch te selecteren. Voor meer informatie, zie [&#x200B; dynamisch een werkschema toewijzen aan de gebruikers &#x200B;](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) en [&#x200B; Creërend een stap van de Dynamische Deelnemer van Adobe Experience Manager.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=nl-NL&CID=RedirectAEMCommunityKautuk)

* **Deelnemers:** het gebied is beschikbaar wanneer de **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** optie op het **de Chooser van de Deelnemer** gebied wordt geselecteerd. In het veld kunt u gebruikers of groepen selecteren voor de optie RandomParticipantChooser.

* **Toegewezen:** het gebied is beschikbaar wanneer **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** op het **Chooser van de Deelnemer** gebied wordt geselecteerd. In het veld kunt u een variabele van het gegevenstype String selecteren om de toewijzing te definiëren.

* **Argumenten:** het gebied is beschikbaar wanneer een manuscript buiten het manuscript RandomParticipantChoose op het gebied van de Kiezer van de Deelnemer wordt geselecteerd. In het veld kunt u een lijst met door komma&#39;s gescheiden argumenten opgeven voor het script dat is geselecteerd in het veld Deelnemerkiezer.

* **Gebruiker of Groep:** de taak wordt toegewezen aan geselecteerde gebruiker of groep. De optie is beschikbaar wanneer **aan een specifieke gebruiker of groepsoptie** op **wordt geselecteerd toewijst opties** gebied. In het veld worden alle gebruikers en groepen van de groep met workflowgebruikers weergegeven.\
  Het **Gebruiker of van de Groep** drop-down menu maakt een lijst van de gebruikers en de groepen die het programma geopende gebruiker toegang heeft tot. De gebruikersnaamvertoning hangt van af als u toegangstoestemmingen op de **gebruikers** knoop in crx-bewaarplaats voor die bepaalde gebruiker hebt.

* **[!UICONTROL Send Notification Email]**: Selecteer deze optie om e-mailmeldingen naar de toegewezen persoon te verzenden. Deze meldingen worden verzonden wanneer een taak wordt toegewezen aan een gebruiker of een groep. Met de optie **[!UICONTROL Recipient Email Address]** kunt u opgeven hoe het e-mailadres moet worden opgehaald.

* **[!UICONTROL Recipient Email Address]**: U kunt e-mailadres opslaan in een variabele, een letterlijk teken gebruiken om een permanent e-mailadres op te geven of het standaard e-mailadres gebruiken van de ontvanger die is opgegeven in het profiel van de toegewezen persoon. U kunt het letterlijke of variabele gebruiken om het e-mailadres van een groep op te geven. De optie Variabele is handig bij het dynamisch ophalen en gebruiken van een e-mailadres. De optie **[!UICONTROL Use default email address of the assignee]** is slechts voor één toegewezen persoon. In dit geval wordt het e-mailadres gebruikt dat is opgeslagen in het gebruikersprofiel van de toewijzing.

* **HTML E-mailMalplaatje**: Selecteer e-mailmalplaatje voor het bericht e-mail. Als u een sjabloon wilt bewerken, wijzigt u het bestand op /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in de crx-repository.
* **staat Delegatie aan toe:** AEM Inbox verstrekt een optie aan de het programma geopende gebruiker om het toegewezen werkschema aan een andere gebruiker te delegeren. U kunt delegeren binnen dezelfde groep of aan de werkschemagebruiker van een andere groep. Als de taak aan één enkele gebruiker wordt toegewezen en **delegatie aan leden van de bestemmingsgroep** optie wordt geselecteerd, dan is het niet mogelijk om de taak aan een andere gebruiker of groep te delegeren.
* **de Montages van het Aandeel:** AEM Inbox verstrekt opties om enig of alle taken in inbox met een andere gebruikers te delen:
   * Wanneer **toewees toestaat om uitdrukkelijk in inbox** optie te delen wordt geselecteerd, kan de gebruiker de taak klikken en het met een andere AEM gebruiker delen.
   * Wanneer **toewijser toestaat om via inbox te delen** optie wordt geselecteerd en een gebruiker zijn Inbox punten deelt of andere gebruikers toestaat om tot zijn Inbox punten toegang te hebben, slechts worden de taken met bovengenoemde toegelaten optie gedeeld met andere gebruikers.

* **Acties > StandaardActies:** uit de doos, voorleggen, sparen, en de acties van het Terugstellen zijn beschikbaar. Standaard zijn alle standaardhandelingen ingeschakeld.
* **Variabele van de Route:** Naam van de routevariabele. De routevariabele vangt douaneacties die een gebruiker in AEM Inbox selecteert.
* **Routes:** De taak van A kan zich aan verschillende routes vertakken. Wanneer geselecteerd in AEM Inbox, keert de route een waarde en de werkschematakken terug die op de geselecteerde route worden gebaseerd. U kunt of routes in een variabele van serie van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om routes manueel toe te voegen.

* **Titel**: Specificeer de titel voor de route. Deze wordt weergegeven in AEM Postvak IN.
* **het Pictogram van het Koraal**: Specificeer de attributen van HTML van een koraalpictogram. De Adobe CorelUI-bibliotheek biedt een uitgebreide set aanraakpictogrammen. U kunt een pictogram voor de route kiezen en gebruiken. Deze wordt samen met de titel in AEM Inbox weergegeven. Als u de routes in een variabele opslaat, gebruiken de routes een standaard &quot;Tags&quot;koraalpictogram.
* **staat toe toegewezen om commentaar** toe te voegen: Selecteer deze optie om commentaren voor de taak toe te laten. Een toegewezen persoon kan de opmerkingen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **sparen commentaar in variabele:** sparen de commentaar in een variabele van het gegevenstype van het Koord. Deze optiesvertoningen slechts als u **selecteert staan toegewezen toe om commentaar** checkbox toe te voegen.

* **staat toegewezen toe om gehechtheid(s) aan de taak** toe te voegen: Selecteer deze optie om gehechtheid voor de taak toe te laten. Een toegewezen persoon kan de bijlagen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **sparen de gehechtheid van de outputtaak gebruikend**: Specificeer de plaats van gehechtheidsomslag. U kunt uitvoertaakbijlagen opslaan met een pad dat is gebaseerd op de laadbewerking of met een variabele van een array van documentgegevenstype. Deze optiesvertoningen slechts als u **verkiest toewees toe te voegen om gehechtheid(s) aan de taak** checkbox toe te voegen en **Aangepaste vorm** te selecteren, **Gelezen-slechts adaptieve vorm**, of **Niet-interactief PDF document** van de **Type** drop-down lijst in de **Vorm/het 1&rbrace; tabel.**

>[!NOTE]
>
>Gebruik het lusje van Bijlagen in Agent UI tijdens runtime om de gehechtheid aan een Interactieve Mededeling te associëren. De bijbehorende bijlagen worden als taakbijlagen weergegeven in het hulpprogramma nadat het werkitem is geopend in de status Voltooid.

* **de douanemetagegevens van het Gebruik:** selecteer deze optie om het gebied van douanemetagegevens toe te laten. Aangepaste metagegevens worden gebruikt in e-mailsjablonen.
* **Meta-gegevens van de Douane:** selecteer een douanemetagegevens voor de e-mailmalplaatjes. De aangepaste metagegevens zijn beschikbaar in de crx-gegevensopslagruimte op apps/fd/dashboard/scripts/metadataScripts. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt. U kunt ook een service gebruiken voor de aangepaste metagegevens. U kunt de interface WorkitemUserMetadataService ook uitbreiden om douanemetagegevens te verstrekken.
* **toon Gegevens van Vorige Stappen**: Selecteer deze optie om toegewezen toe te laten om vorige aangewezen te bekijken, actie die reeds op de taak wordt genomen, commentaren die aan de taak worden toegevoegd, en document van verslag van de voltooide taak, als beschikbaar.
* **toon Gegevens van Volgende Stappen:** selecteer deze optie om de huidige aangewezen toe te laten om de genomen actie en commentaren te bekijken die aan taak door verdere wijzers worden toegevoegd. Ook kan de huidige toegewezen persoon een document bekijken waarin de voltooide taak is vastgelegd, indien beschikbaar.
* **Zichtbaarheid van gegevenstype:** Door gebrek, kan een ontvanger een Document van Verslag, aangewezen personen, genomen actie, en commentaren bekijken die de vorige en verdere wijzers hebben toegevoegd. Gebruik de zichtbaarheid van de optie Gegevenstype om het type gegevens te beperken dat zichtbaar is voor de ontvangers.

>[!NOTE]
>
>De opties om de stap Taak toewijzen als concept op te slaan en de geschiedenis van de stap Taak toewijzen op te halen, worden uitgeschakeld wanneer u een [!DNL Adobe Experience Manager] workflowmodel voor externe gegevensopslag configureert. In Postvak In is bovendien de optie om op te slaan uitgeschakeld.

## E-mailstap verzenden {#send-email-step}

Met de stap E-mail kunt u bijvoorbeeld een e-mailbericht verzenden met een recorddocument, een koppeling naar een adaptief formulier, een koppeling naar een interactieve communicatie of een bijgevoegd PDF-document. Verzend E-mailstap steunt [&#x200B; HTML e-mail &#x200B;](https://en.wikipedia.org/wiki/HTML_email). HTML e-mailberichten reageren en passen zich aan de e-mailclient en schermgrootte van de ontvangers aan. Met een e-mailsjabloon voor HTML kunt u de weergave, het kleurenschema en het gedrag van de e-mail definiëren.

In de e-mailstap wordt de Day CQ Mail Service gebruikt om e-mailberichten te verzenden. Alvorens de e-mailstap te gebruiken, zorg ervoor dat de [&#x200B; e-maildienst &#x200B;](../../forms/using/aem-forms-workflow.md) wordt gevormd. De e-mailstap heeft de volgende eigenschappen:

**Titel:** Titel van de staphulp identificeert de stap in de werkschemaredacteur.

**Beschrijving:** de Verklaring is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

**E-mail Onderwerp:** Onderwerp kan van een werkschemameta-gegevens worden teruggewonnen, manueel worden gespecificeerd, of van de waarde worden teruggewonnen die in een variabele wordt opgeslagen. Selecteer een van de volgende opties:

* **Letterlijk -** specificeer manueel een onderwerp.
* **wint van de meta-gegevens van het Werkschema** terug - verkrijg het onderwerp van een meta-gegevensbezit.
* **Variabele** - wint het onderwerp van de waarde terug die in een variabele van koordgegevenstype wordt opgeslagen.

**HTML E-mailMalplaatje**: HTML malplaatje voor e-mail. U kunt variabelen in een e-mailsjabloon opgeven. De E-mailstap extraheert en geeft alle variabelen weer die in een sjabloon zijn opgenomen voor invoer.

**Metagegevens van het Malplaatje van de E-mail:** De waarde van de variabelen van het e-mailmalplaatje kan een user-specified waarde, de weg van een activa op de auteur of de publicatieserver, beeld, of een bezit van werkschemagegevens zijn.

* **Letterlijk:** gebruik de optie wanneer u de nauwkeurige te specificeren waarde kent. Bijvoorbeeld, [&#x200B; example@example.com &#x200B;](mailto:example@example.com).

* **Metagegevens van het Werkschema:** gebruik de optie wanneer de te gebruiken waarde in een bezit van werkschemagegevens wordt bewaard. Nadat u de optie hebt geselecteerd, typt u de naam van de eigenschap metadata in het lege tekstvak onder de optie Metagegevens werkstroom. Bijvoorbeeld emailAddress.
* **Middel URL:** gebruik de optie om een Webverbinding van een interactieve mededeling aan e-mail in te bedden. Nadat u de optie hebt geselecteerd, bladert u door de interactieve communicatie die u wilt insluiten en kiest u deze. Het element kan zich op de auteur of de publicatieserver bevinden.
* **Beeld:** gebruik de optie om een beeld aan e-mail in te bedden. Blader en kies de afbeelding nadat u de optie hebt geselecteerd. De beeldoptie is beschikbaar slechts voor de beeldmarkeringen (&lt;img src=&quot;&#42;&quot;/>) beschikbaar in het e-mailmalplaatje.

**E-mailadres van de afzender / Ontvanger:** selecteer de **Letterlijke** optie om een e-mailadres manueel te specificeren of **te selecteren terugwinnen van de meta-gegevens van het Werkschema** optie om het e-mailadres van een meta-gegevensbezit terug te winnen. U kunt een lijst van de series van het meta-gegevensbezit voor **ook specificeren ontvangt van de meta-gegevens van het Werkschema** optie. Selecteer de **Veranderlijke** optie om het e-mailadres van de waarde terug te winnen die in een variabele van koordgegevenstype wordt opgeslagen.

**Bijlage van het Dossier:** de activa beschikbaar bij de gespecificeerde plaats is in bijlage aan e-mail. Het pad van het element kan relatief zijn ten opzichte van de payload of het absolute pad. Een voorbeeldweg is [ Payload_Directory ] /attachments/.

Selecteer de **Variabele** optie om de dossiergehechtheid terug te winnen die in een variabele van Document, XML, of JSON gegevenstype wordt opgeslagen.

**Naam van het Dossier:** Naam van het dossier van de e-mailgehechtheid. Met de E-mailstap wijzigt u de oorspronkelijke bestandsnaam van de bijlage in de opgegeven bestandsnaam. De naam kan handmatig worden opgegeven of opgehaald uit een eigenschap voor metagegevens van een workflow of een variabele. Gebruik de **Letterlijke** optie wanneer u de nauwkeurige te specificeren waarde kent. Gebruik de **Variabele** optie om het dossier terug te winnen - noem van de waarde die in een variabele van koordgegevenstype wordt opgeslagen. Gebruik **wint van een Meta-gegevens van het Werkschema** optie terug wanneer de te gebruiken waarde in een bezit van werkschemagegevens wordt bewaard.

## Document met recordstap genereren {#generate-document-of-record-step}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Dit wordt bedoeld als Document van Verslag (DoR). Met de stap Document van record genereren kunt u een alleen-lezen of interactieve PDF-versie van een adaptief formulier maken. De PDF-versie bevat informatie die in het formulier is ingevuld en de indeling van het adaptieve formulier.

De stap Document of Record heeft de volgende eigenschappen:

**Aangepaste Vorm van het Gebruik**: Specificeer de methode om van de input adaptieve vorm de plaats te bepalen. U kunt het adaptieve formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is op een absoluut pad of dat beschikbaar is op een pad in een variabele. U kunt een variabele van het gegevenstype van het Koord gebruiken om de weg in **te specificeren Uitgezochte variabele om** gebied op te lossen.\
U kunt meerdere aangepaste formulieren aan een workflow koppelen. Hierdoor kunt u een adaptief formulier op de runtime opgeven met de beschikbare invoermethoden.

**Aangepast Weg van de Vorm**: Specificeer de weg van de adaptieve vorm. Het gebied is beschikbaar wanneer u **Beschikbaar bij een absolute weg** optie van het **Aangepaste gebied van de Vorm van het Gebruik** selecteert.

**Uitgezochte gegevens van de Input gebruikend:** Weg van de inputgegevens voor de adaptieve vorm. U kunt de gegevens op een plaats met betrekking tot de lading houden, een absolute weg van de gegevens specificeren, of gegevens terugwinnen die in een variabele van document, JSON, of het gegevenstype van XML worden opgeslagen. De invoergegevens worden samengevoegd met het aangepaste formulier om een recorddocument te maken.

**Uitgezochte de gehechtheidspad van de Input gebruikend:** Weg van de gehechtheid. Deze bijlagen worden opgenomen in het document of record. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.

Als u bijvoorbeeld het pad van een map opgeeft, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, gekoppeld aan het document met records. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document of Record. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

**sparen Gegenereerd Document van Verslag gebruikend onder opties:** specificeer de plaats om een document van verslagdossier te houden. U kunt ervoor kiezen om de ladingsomslag te beschrijven, document van verslag bij een plaats binnen de ladingsfolder te plaatsen, of het document van verslag in een variabele van het gegevenstype van het Document op te slaan.

**Landinstelling**: specificeer de taal van het document van verslag. Selecteer **Letterlijk** om de scène van een drop-down lijst te selecteren of **Variabele** te selecteren om de scène van de waarde terug te winnen die in een variabele van koordgegevenstype wordt opgeslagen. Definieer de landinstellingscode terwijl u de waarde voor de landinstelling in een variabele opslaat. Bijvoorbeeld, specificeer **en_US** voor Engels en **fr_FR** voor Frans.

## De stap Service van het formuliergegevensmodel aanroepen {#invoke-form-data-model-service-step}

U kunt [&#x200B; Integratie van Gegevens van AEM Forms gebruiken &#x200B;](../../forms/using/data-integration.md) om te vormen en met ongelijksoortige gegevensbronnen te verbinden. Deze gegevensbronnen kunnen een gegevensbestand, de Webdienst, de dienst van REST, de dienst van OData, en oplossing van CRM zijn. Met AEM Forms Data Integration kunt u een formuliergegevensmodel maken dat verschillende services omvat voor het ophalen, optellen en bijwerken van gegevens in de geconfigureerde database. U kunt de **aanhalen stap van de Dienst van het Gegevensmodel** gebruiken om een model van vormgegevens (FDM) te selecteren en de diensten van FDM te gebruiken om, gegevens terug te winnen bij te werken of toe te voegen om gegevensbronnen te verdelen.

Om input voor gebieden van de stap te verklaren, worden de volgende gegevensbestandlijst en het dossier JSON gebruikt als voorbeeld:

**Steekproef CustomerDetails lijst**

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Waarde <br /> </td> 
  </tr> 
  <tr> 
   <td>FirstName <br /> </td> 
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
   <td>E-mailadres <br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Steekproef JSON- dossier**

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
* **Beschrijving:** Verklaring nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **ModelWeg van de Gegevens van de Vorm**: doorblader en selecteer een model van vormgegevens huidig op de server.

* **Dienst**: Lijst van de diensten die het geselecteerde model van vormgegevens verstrekt.
* **Input voor de diensten > verstrekt inputgegevens gebruikend letterlijke, variabele, of werkschemameta-gegevens, en een JSON- dossier**: De dienst kan veelvoudige argumenten hebben. Selecteer de optie om de waarde van de de dienstargumenten van een werkschemabezit, een voorwerp JSON, een variabele te verkrijgen, of direct de waarde in het verstrekte tekstvakje in te gaan:

   * **Letterlijk:** gebruik de optie wanneer u de nauwkeurige te specificeren waarde kent. Bijvoorbeeld srose@we.info.
   * **Variabele:** gebruik de optie om de waarde terug te winnen die in een variabele wordt opgeslagen.
   * **wint van Meta-gegevens van het Werkschema terug:** gebruik de optie wanneer de te gebruiken waarde in een bezit van werkschemagegevens wordt bewaard. Bijvoorbeeld emailAddress.
   * **[!UICONTROL Relative to Payload]**: gebruik de optie om de bestandsbijlage op te halen die is opgeslagen op een pad dat relatief is ten opzichte van de laadbewerking. Selecteer de optie en geef de mapnaam op die de bestandsbijlage bevat of geef de naam van de bestandsbijlage op in het tekstvak.

     Als de map Relatief aan Payload in de CRX-opslagplaats bijvoorbeeld een bestandsbijlage bevat op de locatie `attachment\attachment-folder` , geeft u `attachment\attachment-folder` in het tekstvak op nadat u de optie **[!UICONTROL Relative to Payload]** hebt geselecteerd.
   * **JSON Dot Notation:** Gebruik de optie wanneer de te gebruiken waarde zich in een JSON-bestand bevindt. Bijvoorbeeld verzekering.customerDetails.emailAddress. De optie Puntnotatie JSON is alleen beschikbaar als de optie Invoervelden toewijzen van invoer-JSON is geselecteerd.
   * **de inputgebieden van de Kaart van input JSON:** specificeer weg van een JSON dossier om inputwaarde van sommige de dienstargumenten van het JSON dossier te verkrijgen. Het pad van het JSON-bestand kan relatief zijn ten opzichte van de payload, een absoluut pad of u kunt een invoer-JSON-document selecteren met een variabele van het type JSON- of Formuliergegevensmodel.

* **Input voor de diensten > verstrekt inputgegevens gebruikend variabele of een JSON dossier:** selecteer de optie om waarden voor alle argumenten van een JSON dossier te verkrijgen dat bij een absolute weg, bij een weg met betrekking tot lading, of in een variabele wordt bewaard.
* **Uitgezochte Input JSON- document gebruikend**: Het JSON- dossier dat waarden voor alle de dienstargumenten bevat. De weg van het JSON dossier kan **met betrekking tot de nuttige lading** of een **absolute weg zijn.** U kunt het invoer-JSON-document ook ophalen met behulp van een variabele van het gegevenstype JSON of Form Data Model.

* **JSON Dot Notation:** verlaat het gebied leeg om alle voorwerpen van het gespecificeerde JSON dossier als input voor de dienstargumenten te gebruiken. Als u een specifiek JSON-object uit het opgegeven JSON-bestand wilt lezen als invoer voor serviceargumenten, geeft u puntnotatie voor het JSON-object op. Als u bijvoorbeeld een JSON-object hebt dat vergelijkbaar is met de JSON-object dat aan het begin van de sectie wordt vermeld, geeft u Insurance.customerDetails op om alle details van een klant als invoer voor de service op te geven.
* **Output van de dienst > de waarden van de Kaart en schrijft output aan variabele of meta-gegevens:** selecteer de optie om de outputwaarden als eigenschappen van de knoop van de de meta-gegevens van de werkschemainstantie in crx-bewaarplaats te bewaren. Specificeer de naam van het meta-gegevensbezit en selecteer het overeenkomstige attribuut van de de dienstoutput dat met meta-gegevensbezit moet worden in kaart gebracht, bijvoorbeeld, phone_number dat door de outputdienst met het phone_number bezit van werkschemameta-gegevens is teruggekeerd. Op dezelfde manier kunt u de uitvoer opslaan in een variabele van het gegevenstype Long. Wanneer u een eigenschap voor de optie **[!UICONTROL Service output attribute to be mapped]** selecteert, worden alleen variabelen die gegevens van de geselecteerde eigenschap kunnen opslaan, gevuld voor de optie **[!UICONTROL Save the output to]** .

* **Output van de dienst > sparen output aan variabele of een JSON dossier:** selecteer de optie om de outputwaarden in een JSON dossier bij een absolute weg, bij een weg met betrekking tot nuttige lading, of in een variabele op te slaan.
* **sparen JSON van de Output gebruikend onder opties:** sparen het outputJSON dossier. Het pad van het JSON-uitvoerbestand kan relatief zijn ten opzichte van de payload of een absoluut pad. U kunt het JSON-uitvoerbestand ook opslaan met een variabele van het gegevenstype JSON of Form Data Model.

## stap Document ondertekenen {#sign-document-step}

Met de stap Document ondertekenen kunt u Adobe Sign gebruiken om documenten te ondertekenen. De stap Document ondertekenen heeft de volgende eigenschappen:

* **Naam van de Overeenkomst:** specificeer de titel van de overeenkomst. De naam van de overeenkomst wordt onderdeel van het onderwerp en de hoofdtekst van de e-mail die naar de ontvangers wordt verzonden. U kunt of de naam in een variabele van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om de naam manueel toe te voegen.

* **Landinstelling:** specificeer de taal voor de e-mail en verificatieopties. U kunt of de scène in een variabele van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om de scène van de lijst van beschikbare opties te kiezen. Definieer de landinstellingscode terwijl u de waarde voor de landinstelling in een variabele opslaat. Bijvoorbeeld, specificeer **en_US** voor Engels en **fr_FR** voor Frans.

* **de Configuratie van de Wolk van Adobe Sign**: Kies een Configuratie van de Wolk van Adobe Sign. Als u geen Adobe Sign voor AEM Forms hebt gevormd, zie [&#x200B; Adobe Sign met AEM Forms &#x200B;](../../forms/using/adobe-sign-integration-adaptive-forms.md) integreren.

* **Uitgezochte Te ondertekenen Document gebruikend:** u kunt een document van een plaats met betrekking tot de lading kiezen, gebruik lading als document, specificeren een absolute weg van het document, of het document terugwinnen dat in een variabele van het gegevenstype van het Document wordt opgeslagen.


* **Uitgezochte Weg van de Bijlage van de Input gebruikend:** Weg van de gehechtheid. Deze bijlagen worden opgenomen in het ondertekenende document. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.


  Als u het pad van een map opgeeft, bijvoorbeeld bijlagen, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, als bijlage bij Document ondertekenen gevoegd. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document ondertekenen. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

* **Dagen tot Deadline:** Een document is duidelijk verschuldigd (overgegaan deadline) nadat er geen activiteit op de taak voor het aantal dagen specificeert in het **Dagen tot Deadline** gebied is. Het aantal dagen wordt geteld nadat het document is toegewezen aan een gebruiker voor ondertekening.
* **Herinnering E-mailFrequentie:** u kunt een herinnering e-mail bij dagelijks of wekelijks interval verzenden. De week wordt geteld vanaf de dag waarop het document aan een gebruiker is toegewezen voor ondertekening.
* **Proces van de Handtekening:** u kunt verkiezen om een document in een opeenvolgende of parallelle orde te ondertekenen. Eén ontvanger ontvangt het document in opeenvolgende volgorde voor ondertekening. Nadat de eerste ontvanger het ondertekenen van het document heeft voltooid, wordt het document verzonden naar de tweede ontvanger, enzovoort. Parallel hieraan kunnen meerdere ontvangers een document tegelijk ondertekenen.
* **Redirection URL:** specificeer een redirection URL. Nadat het document is ondertekend, kunt u de ontvanger omleiden naar een URL. Gewoonlijk bevat deze URL een bedankbericht of verdere instructies.
* **Stadium van het Werkschema:** Een werkschema kan veelvoudige stadia hebben. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Sidekick > Pagina > Pagina-eigenschappen > Staven).
* **Uitgezochte Ontvangers:** specificeer de methode om ontvanger voor het document te kiezen. U kunt de workflow dynamisch toewijzen aan een gebruiker of groep of gegevens van een ontvanger handmatig toevoegen. Wanneer u Handmatig selecteert in het vervolgkeuzemenu, voegt u gegevens over ontvangers toe, zoals E-mail, Rol en Verificatie.

  >[!NOTE]
  >
  >* In de sectie Rol kunt u de rol van ontvanger opgeven als ondertekenaar, fiatteur, accepteerder, gecertificeerde ontvanger, invuller van formulier en gedelegeerde.
  >* Als u Delegator in de optie van de Rol selecteert, kan de Delegator de ondertekeningstaak aan andere ontvangers toewijzen.
  >* Als u een verificatiemethode voor [!DNL Adobe Sign] hebt geconfigureerd, selecteert u op basis van uw configuratie een verificatiemethode zoals verificatie via telefoon, verificatie op basis van sociale identiteit, verificatie op basis van kennis en verificatie op basis van identiteit van de overheid.


* **Manuscript of de dienst om ontvangers te selecteren:** de optie is beschikbaar slechts als u dynamisch optie op het Uitgezochte gebied van Ontvangers selecteert. U kunt een ECMAScript of een dienst specificeren om ontvangers en verificatieopties voor een document te kiezen.
* **Begunstigde Details:** de optie is beschikbaar slechts als de manueel optie op het Uitgezochte gebied van Ontvangers wordt geselecteerd. Geef een e-mailadres op en kies een optioneel verificatiemechanisme. Voordat u een verificatiemechanisme met twee stappen selecteert, moet u controleren of de bijbehorende verificatieoptie is ingeschakeld voor de geconfigureerde Adobe Sign-account. U kunt een variabele van het gegevenstype String gebruiken om waarden te definiëren voor de velden **[!UICONTROL Email]** , **[!UICONTROL Country Code]** en **[!UICONTROL Phone Number]** . De velden **[!UICONTROL Country Code]** en **[!UICONTROL Phone Number]** worden alleen weergegeven als u **[!UICONTROL Phone Verification]** selecteert in de vervolgkeuzelijst **[!UICONTROL 2-step verification]** .
* **Variabele van de Status:** een Adobe Sign toegelaten document slaat het ondertekenen status van het document in een variabele van het gegevenstype van het Koord op. Geef de naam van de statusvariabele op (adobeSignStatus). Een statusvariabele van een instantie is beschikbaar in CRXDE op /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of workflow model>/workItems/&lt;node>/metaData bevat status van een variabele.
* **[!UICONTROL Signed Document]**: u kunt de status van het ondertekende document opslaan in Variabele. Als u een elektronisch audittrail voor handtekeningen wilt toevoegen voor meer beveiliging en wettigheid aan uw ondertekende document, kunt u Auditrapport opnemen. U kunt het ondertekende document opslaan met de map Variabele of Payload.
  >[!NOTE]
  >
  > Het auditrapport wordt toegevoegd aan de laatste pagina van het ondertekende document.
<!--
* **Save signed document using below options:** Specify the location to keep signed documents. You can choose to overwrite the payload file, place the signed document at a location within the payload directory, or store the signed document in a variable of Document type.
-->

## Stappen voor Document Services {#document-services-steps}

AEM Document Services is een set services voor het maken, samenstellen en beveiligen van PDF-documenten. AEM Forms biedt een aparte AEM Workflowstap voor elke documentservice.

Net als bij andere AEM Forms Workflowstappen, zoals Taak toewijzen, E-mail verzenden en Document ondertekenen, kunt u variabelen gebruiken in alle stappen AEM Document Services. Voor meer informatie bij het creëren van en het beheren van variabelen, zie [&#x200B; Variabelen in AEM werkschema&#39;s &#x200B;](../../forms/using/variable-in-aem-workflows.md).

### Tijdstempel document toepassen {#apply-document-time-stamp-step}

Tijdstempel toevoegen aan een document. U geeft documentgegevens op, zoals het pad van het invoerdocument, de naam van het invoerdocument en de locatie waar de geëxporteerde gegevens moeten worden opgeslagen. U kunt desgewenst het bestaande ladingsbestand overschrijven, een andere bestandsnaam kiezen om gegevens op te slaan in een ander bestand onder de ladingmap, een absoluut pad naar de gegevens opgeven of gegevens opslaan in een variabele van het gegevenstype Document.

### Omzetten in afbeeldingsstap {#convert-to-image-step}

Hiermee wordt een PDF-document omgezet in een lijst met afbeeldingen. Ondersteunde afbeeldingsindelingen zijn JPEG, JPEG2000, PNG en TIFF. De volgende informatie is van toepassing op conversies naar TIFF-afbeeldingen:

* Er wordt een TIFF-bestand met meerdere pagina&#39;s gegenereerd.
* Niet alle annotaties zijn opgenomen in TIFF-afbeeldingen. Annotaties waarvoor Acrobat de weergave moet genereren, worden niet opgenomen.

### Omzetten in stap PDF/A {#convert-to-pdf-a-step}

Hiermee converteert u een PDF-document naar de indeling PDF/A met de beschikbare opties. De PDF/A-versie van Portable Document Format (PDF) is gespecialiseerd in het archiveren en op lange termijn bewaren van documenten.

### Omzetten in PS-stap {#convert-to-ps-step}

PDF-documenten converteren naar PostScript. Bij de conversie naar PostScript kunt u het brondocument met de conversiebewerking opgeven en of het document moet worden omgezet in PostScript niveau 2 of 3. Het PDF-document dat u naar een PostScript-bestand converteert, moet niet-interactief zijn.

### PDF maken van opgegeven tekststap {#create-pdf-from-specified-type-step}

Een PDF-document genereren op basis van een invoerbestand. Het invoerdocument kan relatief zijn ten opzichte van de payload, een absoluut pad hebben, kan zelf worden geladen of worden opgeslagen in een variabele van het gegevenstype Document.

### PDF maken van URL/HTML/ZIP-stap {#create-pdf-from-url-html-zip-step}

Hiermee genereert u een PDF-document op basis van de opgegeven URL-, HTML- en ZIP-bestanden.

### Gegevensstap exporteren {#export-data-step}

Hiermee exporteert u gegevens uit een PDF forms- of XDP-bestand. Hiervoor moet u het bestandspad van Invoerdocument en de indeling Gegevens exporteren invoeren. De opties voor de Indeling van Gegevens van de Uitvoer zijn Auto, XDP, en XmlData.

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

Voert het DX- dossier op de gespecificeerde kaart van inputdocumenten uit en keert de gemanipuleerde documenten van de PDF terug.

>[!NOTE]
>
>U kunt variabelen gebruiken om het DDX-bestand voor invoerdocumenten op te geven. Sla het DDX-bestand op in een variabele van het gegevenstype Document of XML.

### Optimize PDF-stap {#optimize-pdf-step}

Hiermee optimaliseert u PDF-bestanden door de grootte ervan te verkleinen. Het resultaat van deze conversie zijn PDF-bestanden die mogelijk kleiner zijn dan de oorspronkelijke versie. Met deze bewerking worden ook PDF-documenten geconverteerd naar de PDF-versie die is opgegeven in de optimalisatieparameters.

Optimalisatie-instellingen bepalen hoe bestanden worden geoptimaliseerd. Hier volgen voorbeelden van instellingen:

* Doelversie PDF
* Objecten negeren, zoals JavaScript-handelingen en ingesloten paginaminiaturen
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

* **Direct toegankelijke printer**: Een printer die op de zelfde computer geïnstalleerd is wordt genoemd een directe toegankelijke printer, en de computer wordt genoemd printergastheer. Dit type printer kan een lokale printer zijn die rechtstreeks op de computer is aangesloten.
* **Indirect toegankelijke printer**: De printer die op een drukserver geïnstalleerd is wordt betreden van andere computers. Technologieën zoals het algemene UNIX®-afdruksysteem (CUPS) en het Line Printer Daemon-protocol (LPD) zijn beschikbaar voor verbinding met een netwerkprinter. Als u toegang wilt tot een indirecte toegankelijke printer, geeft u de IP of hostnaam van de afdrukserver op. Met behulp van dit mechanisme kunt u een document naar een LPD URI verzenden wanneer het netwerk een LPD loopt. Met het mechanisme kunt u het document doorsturen naar elke printer die is aangesloten op het netwerk waarop een LPD-scherm wordt uitgevoerd.

### Afgedrukte uitvoerstap genereren {#generatePrintedOutput}

De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer op basis van een formulierontwerp en een gegevensbestand. Het gegevensbestand wordt samengevoegd met het formulierontwerp en voor afdrukken opgemaakt. De uitvoer die door deze stap wordt gegenereerd, kan rechtstreeks naar een printer worden verzonden of als bestand worden opgeslagen. U wordt aangeraden deze stap te gebruiken als u formulierontwerpen of gegevens uit een toepassing wilt gebruiken. Als uw formulierontwerpen of formulierontwerpen zich op het netwerk, het lokale bestandssysteem of de HTTP-locatie bevinden, gebruikt u de bewerking generatePrintedOutput.

Uw toepassing vereist bijvoorbeeld dat u een formulierontwerp samenvoegt met een gegevensbestand. De gegevens bevatten honderden records. Bovendien moet de uitvoer worden verzonden naar een printer die ZPL ondersteunt. Het formulierontwerp en uw invoergegevens bevinden zich in een toepassing. Met de bewerking generatePrintedOutput kunt u elke record samenvoegen met een formulierontwerp en de uitvoer verzenden naar een printer die ZPL ondersteunt.

De stap Afgedrukte uitvoer genereren heeft de volgende eigenschappen:

**eigenschappen van de Input**

* **[!UICONTROL Select template file using]**: geef het pad van het sjabloonbestand op. U kunt het sjabloonbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld, [ Payload_Directory ] /Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt. Bovendien kunt u ook payload accepteren als het invoergegevensbestand.

* **[!UICONTROL Select data document using]**: geef het pad op van een invoergegevensbestand. U kunt het invoergegevensbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld, [ Payload_Directory ] /Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

* **[!UICONTROL Printer Format]**: Een waarde in de afdrukindeling die de beschrijvingstaal van de pagina opgeeft die moet worden gebruikt om de uitvoerstroom te genereren wanneer geen XDC-bestand wordt geleverd. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:

   * **[!UICONTROL Custom PCL]**: gebruik de optie om een aangepast XDC-bestand voor PCL op te geven.
   * **[!UICONTROL Custom PostScript]**: gebruik de optie om een aangepast XDC-bestand voor PostScript op te geven.
   * **[!UICONTROL Custom ZPL]**: gebruik de optie om een aangepast XDC-bestand voor ZPL op te geven.
   * **[!UICONTROL Generic Color PCL (5c)]**: gebruik een algemene kleur PCL (5c).
   * **[!UICONTROL Generic PostScript Level3]**: gebruik algemeen PostScript Level 3.
   * **[!UICONTROL ZPL 300 DPI]**: gebruik ZPL 300 DPI. Zpl300.xdc wordt gebruikt.
   * **[!UICONTROL ZPL 600 DPI]**: gebruik ZPL 600 DPI. Het bestand zpl600.xdc wordt gebruikt.
   * **[!UICONTROL Custom IPL]**: gebruik de optie om een aangepast XDC-bestand voor IPL op te geven.
   * **[!UICONTROL IPL 300 DPI]**: gebruik IPL 300 DPI. Het bestand ipl300.xdc wordt gebruikt.
   * **[!UICONTROL IPL 400 DPI]**: gebruik IPL 400 DPI. Het bestand ipl400.xdc wordt gebruikt.
   * **[!UICONTROL Custom TPCL]**: gebruik de optie om een aangepast XDC-bestand voor TPCL op te geven.
   * **[!UICONTROL TPCL 305 DPI]**: gebruik TPCL 300 DPI. Het bestand tpcl305.xdc wordt gebruikt.
   * **[!UICONTROL PCL 600 DPI]**: gebruik TPCL 600 DPI. Het bestand tpcl600.xdc wordt gebruikt.
   * **[!UICONTROL Custom DPL]**: gebruik de optie om een aangepast XDC-bestand DPL op te geven.
   * **[!UICONTROL DPL300DPI]**: gebruik DPL 300 DPI. Het bestand dpl300.xdc wordt gebruikt.
   * **[!UICONTROL DPL406DPI]**: gebruik DPL 400 DPI. Het bestand dpl406.xdc wordt gebruikt.
   * **[!UICONTROL DPL600DPI]**: gebruik DPL 600 DPI. De dpl600.xdc wordt gebruikt.

**Eigenschappen van de Output**

* **[!UICONTROL Save output document using]**: geef de locatie op waar u het uitvoerbestand wilt opslaan. U kunt het uitvoerbestand opslaan op een locatie die relatief is ten opzichte van de lading, in een variabele of u kunt een absolute locatie opgeven om het uitvoerbestand op te slaan. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

**Geavanceerde Eigenschappen**

* **[!UICONTROL Select Content Root location using]**: De hoofdmap van de inhoud is een tekenreekswaarde die de URI, absolute verwijzing of locatie in de gegevensopslagruimte opgeeft voor het ophalen van relatieve elementen die door het formulierontwerp worden gebruikt. Als het formulierontwerp bijvoorbeeld relatief verwijst naar een afbeelding, zoals ../myImage.gif, moet myImage.gif zich op repository:// bevinden. De standaardwaarde is repository://, die naar het hoofdniveau van de gegevensopslagruimte wijst.

  Wanneer u een element kiest uit uw toepassing, moet het pad van de URI van de inhoudsbasis de juiste structuur hebben. Als bijvoorbeeld een formulier wordt gekozen uit een toepassing met de naam SampleApp en wordt geplaatst op SampleApp/1.0/forms/Test.xdp, moet de URI van de inhoudswortel worden opgegeven als repository://administrator@password/Applications/SampleApp/1.0/forms/ of gegevensopslagruimte:/Applications/SampleApp/1.0/forms/ (als de bevoegdheid null is). Wanneer de URI voor de inhoudsbasis op deze manier wordt opgegeven, worden de paden van alle middelen waarnaar wordt verwezen in het formulier, omgezet met deze URI.

* **[!UICONTROL Select XCI file using]**: XCI-bestanden worden gebruikt om lettertypen en andere eigenschappen te beschrijven die worden gebruikt voor formulierontwerpelementen. U kunt een XCI-bestand relatief ten opzichte van de payload, op een absoluut pad houden of een variabele van het gegevenstype Document gebruiken.

* **[!UICONTROL Locale]** - Geeft de taal aan die wordt gebruikt voor het genereren van het PDF-document. Als u een letterlijke waarde opgeeft, selecteert u een taal in de lijst of selecteert u een van de volgende waarden:
   * **om servergebrek** te gebruiken:
(Standaard) Gebruik de landinstelling die is geconfigureerd op de AEM Forms-server. De landinstelling wordt geconfigureerd met de beheerconsole. (Zie [&#x200B; Hulp van Designer &#x200B;](https://www.adobe.com/go/learn_aemforms_designer_65).)

   * **om douanewaarde** te gebruiken:
Typ de landinstellingscode in het letterlijke vak of selecteer een tekenreeksvariabele die de landinstellingscode bevat. Ga naar https://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html voor een volledige lijst met ondersteunde landinstellingscodes.

* **[!UICONTROL Copies]**: Een geheel getal dat het aantal kopieën opgeeft dat voor de uitvoer moet worden gegenereerd. De standaardwaarde is 1.

* **[!UICONTROL Duplex Printing]**: Een pagineringswaarde die aangeeft of dubbelzijdig of enkelzijdig afdrukken moet worden gebruikt. Deze waarde wordt gebruikt voor printers die PostScript en PCL ondersteunen. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:
   * **[!UICONTROL Duplex Long Edge]**: dubbelzijdig afdrukken en afdrukken met paginering op lange randen.
   * **[!UICONTROL Duplex Short Edge]**: dubbelzijdig afdrukken en afdrukken gebruiken met paginering op korte zijde.
   * **[!UICONTROL Simplex]**: enkelzijdig afdrukken gebruiken.