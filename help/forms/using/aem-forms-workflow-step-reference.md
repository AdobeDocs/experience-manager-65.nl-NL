---
title: Forms-centric workflow voor OSGi - Step Reference
description: Met een Forms-gerichte workflow voor OSGi-stappen kunt u snel adaptieve formulieren op basis van workflows maken.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: 470fcfda-dfde-437c-b539-d5af1e13a7d6
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '7512'
ht-degree: 0%

---

# Forms-centric workflow voor OSGi - Step Reference {#forms-centric-workflow-on-osgi-step-reference}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html) |
| AEM 6,5 | Dit artikel |

U gebruikt workflowmodellen om een bedrijfslogica om te zetten in een geautomatiseerd, zich herhalend proces. Met behulp van een model kunt u een reeks stappen definiëren en uitvoeren. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt. U kunt [omvat diverse AEM stappen van het Werkschema in een model om bedrijfslogica te bereiken](/help/sites-developing/workflows-models.md#extending-aem).

## Stappen Forms Workflow {#forms-workflow-steps}

Forms Workflows voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel adaptieve formulieren maken op basis van een Forms-gerichte workflow op OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne en interne bedrijfsprocessen binnen de firewall. U kunt ook de stappen van de Forms Workflow gebruiken om documentservices te starten, te integreren met de Adobe Sign-handtekeningworkflow en andere AEM Forms-bewerkingen uit te voeren. U hebt [AEM Forms-invoegtoepassing](https://www.adobe.com/go/learn_aemforms_documentation_63) om deze stappen in een werkstroom te gebruiken.

Forms-centric workflowstappen voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel een op Adaptive Forms gebaseerde Forms-gerichte workflow bouwen op OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne processen en bedrijfsprocessen binnen de firewall.

>[!NOTE]
>
>Als het workflowmodel is gemarkeerd voor externe opslag, kunt u voor alle stappen in de Forms Workflow alleen de optie voor het opslaan of ophalen van gegevensbestanden en bijlagen selecteren.

## Taakstap toewijzen {#assign-task-step}

De taakstap toewijzen maakt een taak en wijst deze toe aan een gebruiker of groep. Naast het toewijzen van de taak geeft de component ook het adaptieve formulier of de niet-interactieve PDF voor de taak op. Het adaptieve formulier is vereist om invoer van gebruikers te accepteren en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie dienen.

U kunt de component ook gebruiken om het gedrag van de taak te controleren. Bijvoorbeeld, creërend een automatisch document van verslag, toewijzend de taak aan een specifieke gebruiker of een groep, specificerend de weg van de voorgelegde gegevens, specificerend de weg van te vullen gegevens, en specificerend standaardacties. De stap Taak toewijzen heeft de volgende eigenschappen:

* **Titel:** Titel van de taak. De titel wordt weergegeven in AEM Postvak IN.
* **Omschrijving:** Uitleg van de bewerkingen die in de taak worden uitgevoerd. Deze informatie is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Pad miniatuur:** Pad van de taakminiatuur. Als er geen pad is opgegeven, wordt voor een aangepaste standaardminiatuur van het formulier weergegeven en voor Document of Record, een standaardpictogram weergegeven.
* **Werkstroomwerkgebied:** Een werkstroom kan uit meerdere fasen bestaan. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Sidekick > Pagina > Pagina-eigenschappen > Staven).
* **Prioriteit:** De geselecteerde prioriteit wordt getoond in AEM Inbox. De beschikbare opties zijn Hoog, Normaal en Laag. De standaardwaarde is Normaal.
* **Vervaldatum:** Geef het aantal dagen of uren op waarna de taak achterstallig is. Als u **Uit** En dan is de taak nooit achterstallig. U kunt ook een time-outhandler opgeven om specifieke taken uit te voeren nadat de taak is uitgevoerd.

* **Dagen:** Het aantal dagen voordat de taak moet worden voltooid. Het aantal dagen wordt geteld nadat de taak aan een gebruiker is toegewezen. Als een taak niet volledig is en het aantal dagen overschrijdt dat op het gebied van Dagen specificeert dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de vervaldatum.
* **Uren:** Het aantal uren voordat de taak moet worden voltooid. Het aantal uren wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal uren overschrijdt specificeert op het gebied van Uren dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de verschuldigde uren.
* **Vertraging na vervaldatum:** Selecteer deze optie om het selectieveld Tijdlijnafhandeling in te schakelen.
* **Time-outhandler:** Selecteer het script dat moet worden uitgevoerd wanneer de taakstap voor toewijzen de gewenste datum overschrijdt. Scripts geplaatst in de CRX-opslagplaats op [apps]/fd/dashboard/scripts/timeoutHandler zijn beschikbaar voor selectie. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt.
* **Markeer de handeling en de opmerking van de laatste taak in Taakdetails:** Selecteer deze optie om de laatste actie weer te geven die is uitgevoerd en de opmerking die is ontvangen in de sectie met taakdetails van een taak.
* **Type:** Kies het type document dat moet worden ingevuld wanneer de workflow wordt gestart. U kunt een adaptief formulier, alleen-lezen adaptief formulier, een niet-interactief PDF-document, de gebruikersinterface van de interactieve communicatieagent of het interactieve communicatie webkanaaldocument kiezen.
* **Adaptief formulier gebruiken:** Geef de methode op om het invoeradaptieve formulier te zoeken. Deze optie is beschikbaar als u Adaptief formulier of Alleen-lezen adaptief formulier selecteert in de vervolgkeuzelijst Type. U kunt het adaptieve formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is op een absoluut pad of dat beschikbaar is op een pad in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven.\
  U kunt meerdere aangepaste formulieren aan een workflow koppelen. Hierdoor kunt u een adaptief formulier op de runtime opgeven met de beschikbare invoermethoden.

* **Interactieve communicatie gebruiken:** Geef de methode op om de interactieve invoercommunicatie te zoeken. U kunt de interactieve communicatie gebruiken die aan het werkschema wordt voorgelegd, beschikbaar bij een absolute weg, of beschikbaar bij een weg in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven. Deze optie is beschikbaar als u Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.

>[!NOTE]
>
>U moet cm-agent-gebruikers en werkschema-gebruikers groepstaken hebben om tot Interactieve Communicatie Agent UI in AEM Inbox toegang te hebben.

* **Aangepast formulier of interactief communicatiepad**: Geef het pad op van het adaptieve formulier of de interactieve communicatie. U kunt het aangepaste formulier of de interactieve communicatie gebruiken die naar de workflow wordt verzonden, beschikbaar via een absoluut pad, of het aangepaste formulier ophalen via een pad dat is opgeslagen in een variabele van het type tekenreeksgegevens.
* **PDF selecteren met:** Geef het pad op van een niet-interactief PDF-document. Het veld is beschikbaar wanneer u een niet-interactief PDF-document kiest in het veld Type. U kunt de invoer-PDF selecteren met behulp van het pad dat relatief is ten opzichte van de payload, opgeslagen op een absoluut pad of met behulp van een variabele van het gegevenstype Document. Bijvoorbeeld: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Het pad bestaat niet in crx-repository. Een beheerder maakt het pad voordat het wordt gebruikt. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om de optie PDF Path te kunnen gebruiken.
* **Voor een voltooide taak geeft u het adaptieve formulier weer als**: Als een taak is gemarkeerd als voltooid, kunt u het adaptieve formulier weergeven als een alleen-lezen adaptief formulier of als een PDF-document. U hebt een optie Document of Record ingeschakeld of op een formuliersjabloon gebaseerde adaptieve formulieren nodig om het adaptieve formulier weer te geven als Document of Record.
* **Vooraf ingevuld:** De volgende velden die hieronder worden vermeld, dienen als invoer voor de taak:

   * **[!UICONTROL Select input data file using]**: Pad van invoergegevensbestand (.json, .xml, .doc of formuliergegevensmodel). U kunt het invoergegevensbestand terugwinnen gebruikend een weg die met betrekking tot de lading is of het dossier terugwinnen dat in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen. Het bestand bevat bijvoorbeeld de gegevens die via een AEM Inbox-toepassing voor het formulier zijn verzonden. Een voorbeeldpad is [Payload_Directory]/workflow/gegevens.

   * **Selecteer invoerbijlagen met:** Bijlagen die op de locatie beschikbaar zijn, worden gekoppeld aan het formulier dat aan de taak is gekoppeld. Het pad kan relatief zijn ten opzichte van de lading of de bijlagen ophalen die zijn opgeslagen in een variabele van het type ArrayList of Document. Een voorbeeldpad is [Payload_Directory]/bijlagen/. U kunt bijlagen opgeven die relatief zijn ten opzichte van de lading of een variabele van het documenttype (Array-lijst > Document) gebruiken om een invoerbijlage op te geven voor het adaptieve formulier.

      * **JSON-invoer kiezen:** Selecteer een invoer-JSON-bestand met een pad dat relatief is ten opzichte van de payload of dat is opgeslagen in een variabele van het gegevenstype Document, JSON of Formuliergegevensmodel. Deze optie is beschikbaar als u Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.
      * **Kies een aangepaste Prefill-service:** Selecteer de prefill dienst om de gegevens terug te winnen en het Interactieve Communicatie het kanaaldocument van het Web of de Agent UI vooraf in te vullen.
      * **Gebruik de vooraf ingevulde service van de hierboven geselecteerde interactieve communicatie:** Gebruik deze optie om de prefill dienst van Interactieve Communicatie te gebruiken die in de Interactieve Communicatie van het Gebruik drop-down lijst wordt bepaald.
      * **Toewijzing verzoekkenmerk:** In het gedeelte Aanvraagkenmerktoewijzing kunt u het volgende definiëren: [naam en waarde van het aanvraagkenmerk](../../forms/using/work-with-form-data-model.md#bindargument). Haal de details van de gegevensbron op die op de attributennaam en waarde wordt gebaseerd in het verzoek wordt gespecificeerd. U kunt een waarde van een aanvraagkenmerk definiëren met een letterlijke waarde of een variabele van het gegevenstype String.\
        De prefill dienst en de opties van de verzoekkenmerkafbeelding zijn beschikbaar slechts als u het Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.

* **Verzonden informatie:** De volgende velden die hieronder worden vermeld, fungeren als uitvoerlocaties voor de taak:

   * **Uitvoergegevensbestand opslaan met:** Sla het gegevensbestand op (.json,. XML, .doc of formuliergegevensmodel). Het gegevensbestand bevat informatie die via het bijbehorende formulier is verzonden. U kunt het uitvoergegevensbestand opslaan met een pad dat relatief is ten opzichte van de lading of dit opslaan in een variabele van het gegevenstype Document, XML of JSON. Bijvoorbeeld: [Payload_Directory]/Workflow/data, waarbij de gegevens een bestand zijn.
   * **Bijlagen opslaan met:** Sla de formulierbijlagen in een taak op. U kunt de bijlagen opslaan met een pad dat relatief is ten opzichte van de lading of deze opslaan in een variabele van een array van documentgegevenstype.
   * **Document van record opslaan met:** Pad om een document van een recordbestand op te slaan. Bijvoorbeeld: [Payload_Directory]/DocumentofRecord/credit-card.pdf. U kunt het Document van Verslag bewaren gebruikend een weg die met betrekking tot de lading is of het opslaan in een variabele van het gegevenstype van het Document. Als u **Ten opzichte van Payload** wordt het document of record niet gegenereerd als het padveld leeg blijft. Deze optie is alleen beschikbaar als u Adaptief formulier selecteert in de vervolgkeuzelijst Type.

   * **Webkanaalgegevens opslaan met:** Sla het webkanaalgegevensbestand op met een pad dat relatief is ten opzichte van de lading of sla het op in een variabele van het gegevenstype Document, JSON of Formuliergegevensmodel. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.
   * **PDF-document opslaan met:** Sla het PDF-document op met een pad dat relatief is ten opzichte van de laadbewerking of sla het op in een variabele van het gegevenstype Document. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.
   * **Lay-outsjabloon opslaan met:** Sla de lay-outsjabloon op met een pad dat relatief is ten opzichte van de laadbewerking of sla deze op in een variabele van het gegevenstype Document. De [lay-outsjabloon](../../forms/using/layout-design-details.md) verwijst naar een XDP-bestand dat u maakt met Forms Designer. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van de drop-down lijst van het Type selecteert.

* **Toewijzen > Opties toewijzen:** Geef de methode op waarmee de taak aan een gebruiker wordt toegewezen. U kunt de taak dynamisch toewijzen aan een gebruiker of groep met behulp van het script Deelnemerkiezer of u kunt de taak toewijzen aan een specifieke AEM gebruiker of groep.
* **Deelnemerkiezer:** De optie is beschikbaar wanneer de optie **Dynamisch naar een gebruiker of groep** is geselecteerd in het veld Opties toewijzen. U kunt een ECMAScript of de dienst gebruiken om een gebruiker of een groep dynamisch te selecteren. Zie voor meer informatie [Een workflow dynamisch toewijzen aan de gebruikers](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) en [Een aangepaste stap voor Adobe Experience Manager Dynamic Participant maken.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en&amp;CID=RedirectAEMCommunityKautuk)

* **Deelnemers:** Het veld is beschikbaar wanneer de **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** is geselecteerd in het dialoogvenster **Deelnemerkiezer** veld. In het veld kunt u gebruikers of groepen selecteren voor de optie RandomParticipantChooser.

* **Geadresseerde:** Het veld is beschikbaar wanneer de **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** is geselecteerd in het dialoogvenster **Deelnemerkiezer** veld. In het veld kunt u een variabele van het gegevenstype String selecteren om de toewijzing te definiëren.

* **Argumenten:** Het veld is beschikbaar wanneer een ander script dan het script RandomParticipantChoose is geselecteerd in het veld Deelnemerkiezer. In het veld kunt u een lijst met door komma&#39;s gescheiden argumenten opgeven voor het script dat is geselecteerd in het veld Deelnemerkiezer.

* **Gebruiker of groep:** De taak wordt toegewezen aan de geselecteerde gebruiker of groep. De optie is beschikbaar wanneer de optie **Aan een specifieke gebruiker of groepsoptie** is geselecteerd in het dialoogvenster **Opties toewijzen** veld. In het veld worden alle gebruikers en groepen van de groep met workflowgebruikers weergegeven.\
  De **Gebruiker of groep** drop-down menu maakt een lijst van de gebruikers en de groepen die de het programma geopende gebruiker toegang heeft tot. De weergave van de gebruikersnaam is afhankelijk van het feit of u toegangsmachtigingen hebt voor de **gebruikers** knooppunt in crx-repository voor die bepaalde gebruiker.

* **[!UICONTROL Send Notification Email]**: Selecteer deze optie als u e-mailberichten wilt verzenden naar de ontvanger. Deze meldingen worden verzonden wanneer een taak wordt toegewezen aan een gebruiker of een groep. U kunt de **[!UICONTROL Recipient Email Address]** om het mechanisme voor het ophalen van het e-mailadres op te geven.

* **[!UICONTROL Recipient Email Address]**: U kunt e-mailadres opslaan in een variabele, een letterlijk teken gebruiken om een permanent e-mailadres op te geven of het standaard e-mailadres van de toegewezen persoon gebruiken die is opgegeven in het profiel van de toegewezen persoon. U kunt het letterlijke of variabele gebruiken om het e-mailadres van een groep op te geven. De optie Variabele is handig bij het dynamisch ophalen en gebruiken van een e-mailadres. De **[!UICONTROL Use default email address of the assignee]** Deze optie geldt slechts voor één enkele ontvanger. In dit geval wordt het e-mailadres gebruikt dat is opgeslagen in het gebruikersprofiel van de toewijzing.

* **HTML-e-mailsjabloon**: Selecteer een e-mailsjabloon voor de e-mailmelding. Als u een sjabloon wilt bewerken, wijzigt u het bestand op /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in de crx-repository.
* **Delegatie toestaan aan:** AEM Inbox verstrekt een optie aan de het programma geopende gebruiker om het toegewezen werkschema aan een andere gebruiker te delegeren. U kunt delegeren binnen dezelfde groep of aan de werkschemagebruiker van een andere groep. Als de taak aan één enkele gebruiker wordt toegewezen en **delegatie aan leden van de groep van gevolmachtigden toestaan** wordt geselecteerd, dan is het niet mogelijk om de taak aan een andere gebruiker of een groep te delegeren.
* **Instellingen voor delen:** AEM Inbox biedt opties om één of alle taken in het Postvak IN te delen met andere gebruikers:
   * Wanneer de **Toestaan dat de ontvanger expliciet in het postvak inbox deelt** is geselecteerd, kan de gebruiker op de taak klikken en deze delen met een andere AEM gebruiker.
   * Wanneer de **Toestaan dat de ontvanger deelt via inbox** wordt geselecteerd en een gebruiker deelt zijn Inbox punten of andere gebruikers toestaat om tot zijn Inbox punten toegang te hebben, slechts worden de taken met bovengenoemde toegelaten optie gedeeld met andere gebruikers.

* **Handelingen > Standaardhandelingen:** De acties Verzenden, Opslaan en Herstellen zijn beschikbaar in het vak. Standaard zijn alle standaardhandelingen ingeschakeld.
* **Routevariabele:** Naam van de routevariabele. De routevariabele vangt douaneacties die een gebruiker in AEM Inbox selecteert.
* **Routes:** Een taak kan zich aan verschillende routes vertakken. Wanneer geselecteerd in AEM Inbox, keert de route een waarde en de werkschematakken terug die op de geselecteerde route worden gebaseerd. U kunt routes opslaan in een variabele van een gegevenstype String of **Letterlijk** om routes manueel toe te voegen.

* **Titel**: Geef de titel voor de route op. Deze wordt weergegeven in AEM Postvak IN.
* **Pictogram Koraal**: Geef het HTML-kenmerk van een koraalpictogram op. De Adobe CorelUI-bibliotheek biedt een uitgebreide set aanraakpictogrammen. U kunt een pictogram voor de route kiezen en gebruiken. Deze wordt samen met de titel in AEM Inbox weergegeven. Als u de routes in een variabele opslaat, gebruiken de routes een standaard &quot;Tags&quot;koraalpictogram.
* **Toestaan dat de ontvanger commentaar toevoegt**: Selecteer deze optie als u opmerkingen voor de taak wilt inschakelen. Een toegewezen persoon kan de opmerkingen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **Opmerking opslaan in variabele:** Sla de opmerking op in een variabele van het gegevenstype String. Deze optie wordt alleen weergegeven als u **Toestaan dat de ontvanger commentaar toevoegt** selectievakje.

* **Toestaan dat de ontvanger een of meer bijlagen aan de taak toevoegt**: Selecteer deze optie om bijlagen in te schakelen voor de taak. Een toegewezen persoon kan de bijlagen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **Uitvoertaakbijlagen opslaan met**: Geef de locatie van de bijlagemap op. U kunt uitvoertaakbijlagen opslaan met een pad dat is gebaseerd op de laadbewerking of met een variabele van een array van documentgegevenstype. Deze optie wordt alleen weergegeven als u **Toestaan dat de ontvanger een of meer bijlagen aan de taak toevoegt** Selectievakje en selecteer **Aangepast formulier**, **Alleen-lezen adaptief formulier**, of **Niet-interactief PDF-document** van de **Type** vervolgkeuzelijst in de **Formulier/Document** tab.

>[!NOTE]
>
>Gebruik het lusje van Bijlagen in Agent UI tijdens runtime om de gehechtheid aan een Interactieve Mededeling te associëren. De bijbehorende bijlagen worden als taakbijlagen weergegeven in het hulpprogramma nadat het werkitem is geopend in de status Voltooid.

* **Aangepaste metagegevens gebruiken:** Selecteer deze optie om het veld Aangepaste metagegevens in te schakelen. Aangepaste metagegevens worden gebruikt in e-mailsjablonen.
* **Aangepaste metagegevens:** Selecteer aangepaste metagegevens voor de e-mailsjablonen. De aangepaste metagegevens zijn beschikbaar in de crx-gegevensopslagruimte op apps/fd/dashboard/scripts/metadataScripts. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt. U kunt ook een service gebruiken voor de aangepaste metagegevens. U kunt de interface WorkitemUserMetadataService ook uitbreiden om douanemetagegevens te verstrekken.
* **Gegevens uit vorige stappen tonen**: Selecteer deze optie als u wilt dat vorige toewijzingen, reeds uitgevoerde handelingen, aan de taak toegevoegde opmerkingen en het document met de opnamen van de voltooide taak, worden weergegeven door de controleurs, indien beschikbaar.
* **Gegevens uit volgende stappen tonen:** Selecteer deze optie om de huidige toegewezen persoon in staat te stellen de actie te bekijken die is ondernomen en de opmerkingen die aan de taak zijn toegevoegd door de volgende toegewezen personen. Ook kan de huidige toegewezen persoon een document bekijken waarin de voltooide taak is vastgelegd, indien beschikbaar.
* **Zichtbaarheid van gegevenstype:** Standaard kan een toegewezen persoon een document met records, toewijzingen, ondernomen actie en opmerkingen bekijken die door eerdere en volgende toewijzingen zijn toegevoegd. Gebruik de zichtbaarheid van de optie Gegevenstype om het type gegevens te beperken dat zichtbaar is voor de ontvangers.

>[!NOTE]
>
>De opties om de Assign stap van de Taak als ontwerp te bewaren en de geschiedenis van de Assign stap van de Taak terug te winnen zijn gehandicapt wanneer u vormt [!DNL Adobe Experience Manager] workflowmodel voor externe gegevensopslag. In Postvak In is bovendien de optie om op te slaan uitgeschakeld.

## E-mailstap verzenden {#send-email-step}

Met de stap E-mail kunt u bijvoorbeeld een e-mailbericht verzenden met een recorddocument, een koppeling naar een adaptief formulier, een koppeling naar een interactieve communicatie of een bijgevoegd PDF-document. E-mailstapondersteuning verzenden [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). HTML e-mailberichten reageren en passen zich aan de e-mailclient en schermgrootte van de ontvangers aan. Met een e-mailsjabloon voor HTML kunt u de weergave, het kleurenschema en het gedrag van de e-mail definiëren.

In de e-mailstap wordt de Day CQ Mail Service gebruikt om e-mailberichten te verzenden. Controleer voordat u de stap E-mail gebruikt of de knop [e-mailservice](../../forms/using/aem-forms-workflow.md) is geconfigureerd. De e-mailstap heeft de volgende eigenschappen:

**Titel:** De titel van de stap helpt de stap in de werkstroomeditor te identificeren.

**Omschrijving:** Uitleg is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

**E-mailonderwerp:** Onderwerp kan uit een werkschemameta-gegevens worden teruggewonnen, manueel worden gespecificeerd, of van de waarde worden teruggewonnen die in een variabele wordt opgeslagen. Selecteer een van de volgende opties:

* **Letterlijk -** Geef een onderwerp handmatig op.
* **Ophalen uit metagegevens van workflow** - Haal het onderwerp op uit een eigenschap metadata.
* **Variabele** - Haal het onderwerp op uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

**HTML-e-mailsjabloon**: HTML sjabloon voor e-mail. U kunt variabelen in een e-mailsjabloon opgeven. De E-mailstap extraheert en geeft alle variabelen weer die in een sjabloon zijn opgenomen voor invoer.

**Metagegevens e-mailsjabloon:** De waarde van de sjabloonvariabelen voor e-mail kan een door de gebruiker opgegeven waarde zijn, het pad van een element op de auteur of de publicatieserver, afbeelding of eigenschap voor metagegevens van de workflow.

* **Letterlijk:** Gebruik deze optie als u precies weet welke waarde u moet opgeven. Bijvoorbeeld: [example@example.com](mailto:example@example.com).

* **Metagegevens werkstroom:** Gebruik de optie wanneer de te gebruiken waarde in een werkschemabezit wordt opgeslagen. Nadat u de optie hebt geselecteerd, typt u de naam van de eigenschap metadata in het lege tekstvak onder de optie Metagegevens werkstroom. Bijvoorbeeld emailAddress.
* **Element-URL:** Gebruik de optie om een webkoppeling van een interactieve communicatie in te sluiten in de e-mail. Nadat u de optie hebt geselecteerd, bladert u door de interactieve communicatie die u wilt insluiten en kiest u deze. Het element kan zich op de auteur of de publicatieserver bevinden.
* **Afbeelding:** Gebruik de optie om een afbeelding in te sluiten in de e-mail. Blader en kies de afbeelding nadat u de optie hebt geselecteerd. De afbeeldingsoptie is alleen beschikbaar voor de afbeeldingstags (&lt;img src=&quot;&lt;span id=&quot; translate=&quot;no&quot; />&quot;/>) die beschikbaar zijn in de e-mailsjabloon.&#42;

**E-mailadres van afzender/ontvanger:** Selecteer de **Letterlijk** om handmatig een e-mailadres op te geven of selecteer de optie **Ophalen uit metagegevens van workflow** om het e-mailadres op te halen uit een eigenschap metadata. U kunt ook een lijst met arrays met metagegevenseigenschappen opgeven voor de **Ophalen uit metagegevens van workflow** -optie. Selecteer de **Variabele** om het e-mailadres op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

**Bestandsbijlage:** Het middel dat op de opgegeven locatie beschikbaar is, wordt als bijlage aan de e-mail toegevoegd. Het pad van het element kan relatief zijn ten opzichte van de payload of het absolute pad. Een voorbeeldpad is [Payload_Directory]/bijlagen/.

Selecteer de **Variabele** om de bestandsbijlage op te halen die is opgeslagen in een variabele van het gegevenstype Document, XML of JSON.

**Bestandsnaam:** Naam van het bestand met e-mailbijlagen. Met de E-mailstap wijzigt u de oorspronkelijke bestandsnaam van de bijlage in de opgegeven bestandsnaam. De naam kan handmatig worden opgegeven of opgehaald uit een eigenschap voor metagegevens van een workflow of een variabele. Gebruik de **Letterlijk** als u precies weet welke waarde u moet opgeven. Gebruik de **Variabele** om de bestandsnaam op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. Gebruik de **Ophalen uit een werkstroommetagegevens** als de te gebruiken waarde wordt opgeslagen in een werkstroommetagegevenseigenschap.

## Document met recordstap genereren {#generate-document-of-record-step}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Dit wordt bedoeld als Document van Verslag (DoR). Met de stap Document van record genereren kunt u een alleen-lezen of interactieve PDF-versie van een adaptief formulier maken. De PDF-versie bevat informatie die in het formulier is ingevuld en de indeling van het adaptieve formulier.

De stap Document of Record heeft de volgende eigenschappen:

**Adaptief formulier gebruiken**: Geef de methode op om het invoeradaptieve formulier te zoeken. U kunt het adaptieve formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is op een absoluut pad of dat beschikbaar is op een pad in een variabele. U kunt een variabele van het gegevenstype String gebruiken om het pad op te geven in het dialoogvenster **Te corrigeren variabele selecteren** veld.\
U kunt meerdere aangepaste formulieren aan een workflow koppelen. Hierdoor kunt u een adaptief formulier op de runtime opgeven met de beschikbare invoermethoden.

**Adaptief formulierpad**: Geef het pad van het adaptieve formulier op. Het veld is beschikbaar wanneer u de optie **Beschikbaar op een absoluut pad** van de **Adaptief formulier gebruiken** veld.

**Selecteer Invoergegevens met:** Pad van de invoergegevens voor het adaptieve formulier. U kunt de gegevens op een plaats met betrekking tot de lading houden, een absolute weg van de gegevens specificeren, of gegevens terugwinnen die in een variabele van document, JSON, of het gegevenstype van XML worden opgeslagen. De invoergegevens worden samengevoegd met het aangepaste formulier om een recorddocument te maken.

**Selecteer Invoerpad voor bijlage met:** Pad van de bijlagen. Deze bijlagen worden opgenomen in het document of record. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.

Als u bijvoorbeeld het pad van een map opgeeft, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, gekoppeld aan het document met records. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document of Record. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

**Gegenereerd document van record opslaan met onderstaande opties:** Geef de locatie op waar u een document van een recordbestand wilt bewaren. U kunt ervoor kiezen om de ladingsomslag te beschrijven, document van verslag bij een plaats binnen de ladingsfolder te plaatsen, of het document van verslag in een variabele van het gegevenstype van het Document op te slaan.

**Landinstelling**: Geef de taal van het document met records op. Selecteren **Letterlijk** om de landinstelling te selecteren in een vervolgkeuzelijst of selecteer **Variabele** om de landinstelling op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. Definieer de landinstellingscode terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **nl_NL** voor het Engels en **fr_FR** voor Frans.

## De stap Service van het formuliergegevensmodel aanroepen {#invoke-form-data-model-service-step}

U kunt [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md) om te vormen en met ongelijksoortige gegevensbronnen te verbinden. Deze gegevensbronnen kunnen een gegevensbestand, de Webdienst, de dienst van REST, de dienst van OData, en oplossing van CRM zijn. Met AEM Forms Data Integration kunt u een formuliergegevensmodel maken dat verschillende services omvat voor het ophalen, optellen en bijwerken van gegevens in de geconfigureerde database. U kunt de **De stap Data Model Service aanroepen** om een model van vormgegevens (FDM) te selecteren en de diensten van FDM te gebruiken om, gegevens terug te winnen bij te werken of toe te voegen om gegevensbronnen te verdelen.

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
* **Omschrijving:** Uitleg nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Formuliergegevensmodelpad**: Blader en selecteer een formuliergegevensmodel dat op de server aanwezig is.

* **Service**: Lijst met services die worden geleverd door het geselecteerde formuliergegevensmodel.
* **Invoer voor services > Invoergegevens opgeven met letterlijke metagegevens, metagegevens van variabelen of workflows en een JSON-bestand**: Een service kan meerdere argumenten hebben. Selecteer de optie om de waarde van de de dienstargumenten van een werkschemabezit, een voorwerp JSON, een variabele te verkrijgen, of direct de waarde in het verstrekte tekstvakje in te gaan:

   * **Letterlijk:** Gebruik deze optie als u precies weet welke waarde u moet opgeven. Bijvoorbeeld srose@we.info.
   * **Variabele:** Gebruik de optie om de waarde op te halen die in een variabele is opgeslagen.
   * **Ophalen uit werkstroommetagegevens:** Gebruik de optie wanneer de te gebruiken waarde in een werkschemabezit wordt opgeslagen. Bijvoorbeeld emailAddress.
   * **[!UICONTROL Relative to Payload]**: Gebruik de optie om de bestandsbijlage op te halen die is opgeslagen op een pad dat relatief is ten opzichte van de laadbewerking. Selecteer de optie en geef de mapnaam op die de bestandsbijlage bevat of geef de naam van de bestandsbijlage op in het tekstvak.

     Bijvoorbeeld als de map Relatief aan Payload in de CRX-opslagplaats een bestandsbijlage bevat in de `attachment\attachment-folder` locatie, opgeven `attachment\attachment-folder` in het tekstvak nadat u de **[!UICONTROL Relative to Payload]** -optie.
   * **JSON-puntnotatie:** Gebruik deze optie als de te gebruiken waarde zich in een JSON-bestand bevindt. Bijvoorbeeld verzekering.customerDetails.emailAddress. De optie Puntnotatie JSON is alleen beschikbaar als de optie Invoervelden toewijzen van invoer-JSON is geselecteerd.
   * **Invoervelden toewijzen uit invoer-JSON:** Geef het pad van een JSON-bestand op om de invoerwaarde van bepaalde serviceargumenten op te halen uit het JSON-bestand. Het pad van het JSON-bestand kan relatief zijn ten opzichte van de payload, een absoluut pad of u kunt een invoer-JSON-document selecteren met een variabele van het type JSON- of Formuliergegevensmodel.

* **Invoer voor services > Invoergegevens opgeven met behulp van een variabele of een JSON-bestand:** Selecteer de optie om waarden voor alle argumenten op te halen uit een JSON-bestand dat is opgeslagen op een absoluut pad, een pad dat relatief is ten opzichte van de payload of een variabele.
* **Invoerdocument JSON selecteren met**: Het JSON-bestand met waarden voor alle serviceargumenten. Het pad van het JSON-bestand kan **ten opzichte van de lading** of een **absoluut pad.** U kunt het invoer-JSON-document ook ophalen met behulp van een variabele van het gegevenstype JSON of Form Data Model.

* **JSON-puntnotatie:** Laat het veld leeg als u alle objecten van het opgegeven JSON-bestand als invoer voor serviceargumenten wilt gebruiken. Als u een specifiek JSON-object uit het opgegeven JSON-bestand wilt lezen als invoer voor serviceargumenten, geeft u puntnotatie voor het JSON-object op. Als u bijvoorbeeld een JSON-object hebt dat vergelijkbaar is met de JSON-object dat aan het begin van de sectie wordt vermeld, geeft u Insurance.customerDetails op om alle details van een klant als invoer voor de service op te geven.
* **Uitvoer van service > Uitvoerwaarden toewijzen en schrijven naar variabele of metagegevens:** Selecteer de optie om de uitvoerwaarden op te slaan als eigenschappen van het metagegevensknooppunt voor workflowinstanties in de crx-repository. Specificeer de naam van het meta-gegevensbezit en selecteer het overeenkomstige attribuut van de de dienstoutput dat met meta-gegevensbezit moet worden in kaart gebracht, bijvoorbeeld, phone_number dat door de outputdienst met het phone_number bezit van werkschemameta-gegevens is teruggekeerd. Op dezelfde manier kunt u de uitvoer opslaan in een variabele van het gegevenstype Long. Wanneer u een eigenschap voor de **[!UICONTROL Service output attribute to be mapped]** optie, alleen variabelen die gegevens van de geselecteerde eigenschap kunnen opslaan, worden gevuld voor de **[!UICONTROL Save the output to]** -optie.

* **Uitvoer van service > Uitvoer opslaan naar variabele of een JSON-bestand:** Selecteer de optie om de uitvoerwaarden in een JSON-bestand op te slaan met een absoluut pad, een pad dat relatief is ten opzichte van de laadtijd of een variabele.
* **JSON-uitvoerdocument opslaan met de onderstaande opties:** Sla het JSON-uitvoerbestand op. Het pad van het JSON-uitvoerbestand kan relatief zijn ten opzichte van de payload of een absoluut pad. U kunt het JSON-uitvoerbestand ook opslaan met een variabele van het gegevenstype JSON of Form Data Model.

## stap Document ondertekenen {#sign-document-step}

Met de stap Document ondertekenen kunt u Adobe Sign gebruiken om documenten te ondertekenen. De stap Document ondertekenen heeft de volgende eigenschappen:

* **Naam overeenkomst:** Geef de titel van de overeenkomst op. De naam van de overeenkomst wordt onderdeel van het onderwerp en de hoofdtekst van de e-mail die naar de ontvangers wordt verzonden. U kunt de naam opslaan in een variabele van het gegevenstype String of **Letterlijk** om de naam handmatig toe te voegen.

* **Landinstelling:** Geef de taal op voor de opties voor e-mail en verificatie. U kunt de landinstelling opslaan in een variabele van het gegevenstype String of **Letterlijk** om de landinstelling te kiezen in de lijst met beschikbare opties. Definieer de landinstellingscode terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **nl_NL** voor het Engels en **fr_FR** voor Frans.

* **Adobe Sign Cloud Configuration**: Kies een Adobe Sign Cloud-configuratie. Als u Adobe Sign for AEM Forms niet hebt geconfigureerd, raadpleegt u [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

* **Selecteer het document dat u wilt ondertekenen:** U kunt een document kiezen op een locatie die relatief is ten opzichte van de lading, de lading als document gebruiken, een absoluut pad van het document opgeven of het document ophalen dat is opgeslagen in een variabele van het documentgegevenstype.


* **Selecteer Pad invoerbijlage met:** Pad van de bijlagen. Deze bijlagen worden opgenomen in het ondertekenende document. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.


  Als u het pad van een map opgeeft, bijvoorbeeld bijlagen, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, als bijlage bij Document ondertekenen gevoegd. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document ondertekenen. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

* **Dagen tot deadline:** Een document is gemarkeerd als opeisbaar (verstreken deadline) nadat de taak gedurende het opgegeven aantal dagen niet is geactiveerd in het dialoogvenster **Dagen tot deadline** veld. Het aantal dagen wordt geteld nadat het document is toegewezen aan een gebruiker voor ondertekening.
* **E-mailfrequentie herinnering:** U kunt een herinnering per dag of wekelijks e-mail verzenden. De week wordt geteld vanaf de dag waarop het document aan een gebruiker is toegewezen voor ondertekening.
* **Handtekeningproces:** U kunt ervoor kiezen om een document in een opeenvolgende of parallelle volgorde te ondertekenen. Eén ontvanger ontvangt het document in opeenvolgende volgorde voor ondertekening. Nadat de eerste ontvanger het ondertekenen van het document heeft voltooid, wordt het document verzonden naar de tweede ontvanger, enzovoort. Parallel hieraan kunnen meerdere ontvangers een document tegelijk ondertekenen.
* **URL omleiden:** Geef een omleidings-URL op. Nadat het document is ondertekend, kunt u de ontvanger omleiden naar een URL. Gewoonlijk bevat deze URL een bedankbericht of verdere instructies.
* **Werkstroomwerkgebied:** Een werkstroom kan uit meerdere fasen bestaan. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Sidekick > Pagina > Pagina-eigenschappen > Staven).
* **Ontvangers selecteren:** Geef de methode op waarmee u de ontvanger voor het document wilt kiezen. U kunt de workflow dynamisch toewijzen aan een gebruiker of groep of gegevens van een ontvanger handmatig toevoegen. Wanneer u Handmatig selecteert in het vervolgkeuzemenu, voegt u gegevens over ontvangers toe, zoals E-mail, Rol en Verificatie.

  >[!NOTE]
  >
  >* In de sectie Rol kunt u de rol van ontvanger opgeven als ondertekenaar, fiatteur, accepteerder, gecertificeerde ontvanger, invuller van formulier en gedelegeerde.
  >* Als u Delegator in de optie van de Rol selecteert, kan de Delegator de ondertekeningstaak aan andere ontvangers toewijzen.
  >* Als u een authentificatiemethode voor hebt gevormd [!DNL Adobe Sign], gebaseerd op uw configuratie, selecteert u een verificatiemethode zoals verificatie via telefoon, verificatie op basis van sociale identiteit, verificatie op basis van kennis, verificatie op basis van identiteit van de overheid.


* **Script of service om ontvangers te selecteren:** De optie is alleen beschikbaar als u in het veld Ontvangers selecteren de optie Dynamisch selecteert. U kunt een ECMAScript of een dienst specificeren om ontvangers en verificatieopties voor een document te kiezen.
* **Gegevens van ontvanger:** De optie is alleen beschikbaar als de optie Handmatig is geselecteerd in het veld Ontvangers selecteren. Geef een e-mailadres op en kies een optioneel verificatiemechanisme. Voordat u een verificatiemechanisme met twee stappen selecteert, moet u controleren of de bijbehorende verificatieoptie is ingeschakeld voor de geconfigureerde Adobe Sign-account. U kunt een variabele van het gegevenstype String gebruiken om waarden te definiëren voor **[!UICONTROL Email]**, **[!UICONTROL Country Code]**, en **[!UICONTROL Phone Number]** velden. De **[!UICONTROL Country Code]** en **[!UICONTROL Phone Number]** velden worden alleen weergegeven als u **[!UICONTROL Phone Verification]** van de **[!UICONTROL 2-step verification]** vervolgkeuzelijst.
* **Statusvariabele:** In een Adobe Sign-document wordt de ondertekeningsstatus van het document opgeslagen in een variabele van het gegevenstype String. Geef de naam van de statusvariabele op (adobeSignStatus). Een statusvariabele van een instantie is beschikbaar in CRXDE op /etc/workflow/instances/&lt;server>/&lt;date-time>/&lt;instance of=&quot;&quot; workflow=&quot;&quot; model=&quot;&quot;>/workItems/&lt;node>/metaData bevat status van een variabele.
* **[!UICONTROL Signed Document]**: U kunt de status van het ondertekende document opslaan als een variabele. Als u een elektronisch audittrail voor handtekeningen wilt toevoegen voor meer beveiliging en wettigheid aan uw ondertekende document, kunt u Auditrapport opnemen. U kunt het ondertekende document opslaan met de map Variabele of Payload.
  >[!NOTE]
  >
  > Het auditrapport wordt toegevoegd aan de laatste pagina van het ondertekende document.
<!--
* **Save signed document using below options:** Specify the location to keep signed documents. You can choose to overwrite the payload file, place the signed document at a location within the payload directory, or store the signed document in a variable of Document type.
-->

## Stappen voor Document Services {#document-services-steps}

AEM Document Services is een set services voor het maken, samenstellen en beveiligen van PDF-documenten. AEM Forms biedt een aparte AEM Workflowstap voor elke documentservice.

Net als bij andere AEM Forms Workflowstappen, zoals Taak toewijzen, E-mail verzenden en Document ondertekenen, kunt u variabelen gebruiken in alle stappen AEM Document Services. Zie voor meer informatie over het maken en beheren van variabelen [Variabelen in AEM werkstromen](../../forms/using/variable-in-aem-workflows.md).

### Tijdstempel document toepassen {#apply-document-time-stamp-step}

Tijdstempel toevoegen aan een document. U geeft documentgegevens op, zoals het pad van het invoerdocument, de naam van het invoerdocument en de locatie waar de geëxporteerde gegevens moeten worden opgeslagen. U kunt desgewenst het bestaande ladingsbestand overschrijven, een andere bestandsnaam kiezen om gegevens op te slaan in een ander bestand onder de ladingmap, een absoluut pad naar de gegevens opgeven of gegevens opslaan in een variabele van het gegevenstype Document.

### Omzetten in afbeeldingsstap {#convert-to-image-step}

Hiermee wordt een PDF-document omgezet in een lijst met afbeeldingen. Ondersteunde afbeeldingsindelingen zijn JPEG, JPEG2000, PNG en TIFF. De volgende informatie is van toepassing op conversies naar TIFF-afbeeldingen:

* Er wordt een TIFF-bestand met meerdere pagina&#39;s gegenereerd.
* Niet alle annotaties zijn opgenomen in TIFF-afbeeldingen. Annotaties waarvoor Acrobat de weergave moet genereren, worden niet opgenomen.

### Omzetten in stap PDF/A {#convert-to-pdf-a-step}

Hiermee converteert u een PDF-document naar de indeling PDF/A met de beschikbare opties. De PDF/A-versie van Portable Document Format (PDF) is gespecialiseerd in het archiveren en op lange termijn bewaren van documenten.

### Omzetten in PS-stap {#convert-to-ps-step}

PDF-documenten converteren naar PostScript. Bij het converteren naar PostScript kunt u het brondocument met de conversiebewerking opgeven en of het document moet worden omgezet in PostScript-niveau 2 of 3. Het PDF-document dat u naar een PostScript-bestand converteert, moet niet-interactief zijn.

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

* **[!UICONTROL Select template file using]**: Geef het pad van het sjabloonbestand op. U kunt het sjabloonbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld: [Payload_Directory]/Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt. Bovendien kunt u ook payload accepteren als het invoergegevensbestand.

* **[!UICONTROL Select data document using]**: Geef het pad op van een invoergegevensbestand. U kunt het invoergegevensbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld: [Payload_Directory]/Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

* **[!UICONTROL Printer Format]**: Een waarde in de indeling Afdrukken die de beschrijvingstaal van de pagina opgeeft die moet worden gebruikt om de uitvoerstroom te genereren wanneer geen XDC-bestand wordt geleverd. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:

   * **[!UICONTROL Custom PCL]**: Gebruik de optie om een aangepast XDC-bestand voor PCL op te geven.
   * **[!UICONTROL Custom PostScript]**: Gebruik de optie om een aangepast XDC-bestand voor PostScript op te geven.
   * **[!UICONTROL Custom ZPL]**: Gebruik de optie om een aangepast XDC-bestand voor ZPL op te geven.
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

* **[!UICONTROL Save output document using]**: Geef de locatie op waar u het uitvoerbestand wilt opslaan. U kunt het uitvoerbestand opslaan op een locatie die relatief is ten opzichte van de lading, in een variabele of u kunt een absolute locatie opgeven om het uitvoerbestand op te slaan. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

**Geavanceerde eigenschappen**

* **[!UICONTROL Select Content Root location using]**: De inhoudsbasis is een tekenreekswaarde die de URI, absolute verwijzing of locatie in de gegevensopslagruimte opgeeft voor het ophalen van relatieve elementen die door het formulierontwerp worden gebruikt. Als het formulierontwerp bijvoorbeeld relatief verwijst naar een afbeelding, zoals ../myImage.gif, moet myImage.gif zich op repository:// bevinden. De standaardwaarde is repository://, die naar het hoofdniveau van de gegevensopslagruimte wijst.

  Wanneer u een element kiest uit uw toepassing, moet het pad van de URI van de inhoudsbasis de juiste structuur hebben. Als bijvoorbeeld een formulier wordt gekozen uit een toepassing met de naam SampleApp en wordt geplaatst op SampleApp/1.0/forms/Test.xdp, moet de URI van de inhoudswortel worden opgegeven als repository://administrator@password/Applications/SampleApp/1.0/forms/ of gegevensopslagruimte:/Applications/SampleApp/1.0/forms/ (als de bevoegdheid null is). Wanneer de URI voor de inhoudsbasis op deze manier wordt opgegeven, worden de paden van alle middelen waarnaar wordt verwezen in het formulier, omgezet met deze URI.

* **[!UICONTROL Select XCI file using]**: XCI-bestanden worden gebruikt om lettertypen en andere eigenschappen te beschrijven die voor formulierontwerpelementen worden gebruikt. U kunt een XCI-bestand relatief ten opzichte van de payload, op een absoluut pad houden of een variabele van het gegevenstype Document gebruiken.

* **[!UICONTROL Locale]**: Geeft de taal aan die wordt gebruikt voor het genereren van het PDF-document. Als u een letterlijke waarde opgeeft, selecteert u een taal in de lijst of selecteert u een van de volgende waarden:
   * **Als u de standaardinstelling van de server gebruikt**: (Standaard) Gebruik de landinstelling die op de AEM Forms-server is geconfigureerd. De landinstelling wordt geconfigureerd met de beheerconsole. (Zie [Help bij Designer](https://www.adobe.com/go/learn_aemforms_designer_65).)

   * **Aangepaste waarde gebruiken**: Typ de landinstellingscode in het letterlijke vak of selecteer een tekenreeksvariabele die de landinstellingscode bevat. Ga naar https://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html voor een volledige lijst met ondersteunde landinstellingscodes.

* **[!UICONTROL Copies]**: Een geheel getal dat het aantal kopieën opgeeft dat voor de uitvoer moet worden gegenereerd. De standaardwaarde is 1.

* **[!UICONTROL Duplex Printing]**: Een pagineringswaarde die aangeeft of dubbelzijdig of enkelzijdig afdrukken moet worden gebruikt. Deze waarde wordt gebruikt voor printers die PostScript en PCL ondersteunen. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:
   * **[!UICONTROL Duplex Long Edge]**: Gebruik dubbelzijdig afdrukken en afdrukken met paginering op lange zijde.
   * **[!UICONTROL Duplex Short Edge]**: Gebruik dubbelzijdig afdrukken en afdrukken met paginering op korte zijde.
   * **[!UICONTROL Simplex]**: enkelzijdig afdrukken gebruiken.