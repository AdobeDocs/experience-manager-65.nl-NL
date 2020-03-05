---
title: Formulier-centric werkschema op OSGi - de Verwijzing van de Stap
seo-title: Formulier-centric werkschema op OSGi - de Verwijzing van de Stap
description: De vorm-centric werkschema op stappen OSGi staat u toe snel aanpassings vormen gebaseerde werkschema's bouwen.
seo-description: De vorm-centric werkschema op stappen OSGi staat u toe snel aanpassings vormen gebaseerde werkschema's bouwen.
uuid: 6f791c45-0e35-4c55-9106-5340caab94b7
contentOwner: null
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: f0a5588d-f210-4f04-bc35-b62834f90ab1
docset: aem65
translation-type: tm+mt
source-git-commit: 86649ccfd494435038da06e72fbfed544a7aaf12

---


# Formulier-centric werkschema op OSGi - de Verwijzing van de Stap{#forms-centric-workflow-on-osgi-step-reference}

## De Stappen van het Werkschema van vormen {#forms-workflow-steps}

De het werkschemastappen van vormen voeren AEM vorm-specifieke verrichtingen in een werkschema AEM uit. Deze stappen staan u toe snel bouwend adaptieve vormen gebaseerde vorm-centric werkschema op OSGi. Deze werkschema&#39;s kunnen voor het ontwikkelen van basisoverzicht en goedkeuring-werkschema&#39;s, interne en over de firewall bedrijfsprocessen worden gebruikt. U kunt de stappen van het Werkschema van Vormen ook gebruiken om de documentdiensten te beginnen, met de handtekeningswerkschema van het Teken van Adobe te integreren, en andere verrichtingen van Vormen uit te voeren AEM. U vereist [AEM toe:voegen-op](https://www.adobe.com/go/learn_aemforms_documentation_63) Vormen om deze stappen in een werkschema te gebruiken.

## Taakstap toewijzen {#assign-task-step}

De taakstap toewijzen leidt tot een taak en wijst het aan een gebruiker of een groep toe. Naast het toewijzen van de taak, specificeert de component ook het adaptieve formulier of niet-interactieve PDF voor de taak. Het adaptieve formulier is vereist om invoer van gebruikers te accepteren en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt om alleen werkstromen te bekijken.

U kunt de component ook gebruiken om het gedrag van de taak te controleren. Bijvoorbeeld, creërend een automatisch document van verslag, toewijzend de taak aan een specifieke gebruiker of een groep, specificerend de weg van de voorgelegde gegevens, specificerend de weg van te vullen gegevens, en specificerend standaardacties. De stap Taak toewijzen heeft de volgende eigenschappen:

* **Titel:** Titel van de taak. De titel wordt getoond in AEM Inbox.
* **Beschrijving:** Uitleg van de verrichtingen die in de taak worden uitgevoerd. Deze informatie is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Miniatuurpad:** Pad van de taakminiatuur. Als geen weg wordt gespecificeerd, voor een adaptieve vorm wordt de standaardduimnagel getoond en voor Document van Verslag, wordt een standaardpictogram getoond.
* **Werkstroomstadium:** Een werkschema kan veelvoudige stadia hebben. Deze stadia worden getoond in AEM Inbox. U kunt deze stadia in de eigenschappen van het model bepalen (Sidetrap > Pagina > de Eigenschappen van de Pagina > de Fanden).
* **Prioriteit:** De geselecteerde prioriteit wordt getoond in AEM Inbox. De beschikbare opties zijn Hoog, Middelgroot, en Laag. De standaardwaarde is Middelgroot.
* **Vervaldatum:** Specificeer het aantal dagen of uren waarna de taak duidelijk achterhaald is. Als u **Uit** selecteert, dan is de taak nooit duidelijk achterhaald. U kunt een onderbrekingsmanager ook specificeren om specifieke taken uit te voeren nadat de taak achterhaald is.

* **Dagen:** Het aantal dagen vóór welke de taak moet worden voltooid. Het aantal dagen wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal dagen kruist specificeert op het gebied van Dagen, dan, indien geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de vervaldatum.
* **Uren:** Het aantal uren vóór welke de taak moet worden voltooid. Het aantal uren wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal uren kruist specificeert op het gebied van Uren, dan, indien geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de verschuldigde uren.
* **Vertraging na vervaldatum:** Selecteer deze optie om het de selectiegebied van de Manager van de Onderbreking toe te laten.
* **Time-out-handler:** Selecteer het manuscript dat moet worden uitgevoerd wanneer de toewijst taakstap de vervaldatum kruist. De manuscripten die in CRX-bewaarplaats bij [apps]/fd/dashboard/scripts/timeoutHandler worden geplaatst zijn beschikbaar voor selectie. Het opgegeven pad bestaat niet in crx-repository. Een beheerder leidt tot de weg alvorens het te gebruiken.
* **Benadruk de actie en de commentaar van de laatste taak in de Details van de Taak:** Selecteer deze optie om de laatste actie te tonen die werd genomen en commentaar ontvangen op de sectie van taakdetails van een taak.
* **Type:** Kies het type document dat moet worden ingevuld wanneer de werkstroom wordt gestart. U kunt een adaptieve vorm, read-only adaptieve vorm, een niet interactief Pdf- document, een Interactieve Communicatie Agent UI, of het Interactieve Document van het Kanaal van het Communicatie Web kiezen.
* **Aanpassingsformulier gebruiken:** Specificeer de methode om van de input aanpassingsvorm de plaats te bepalen. Deze optie is beschikbaar als u Aanpassingsformulier of Alleen-lezen adaptieve formulier selecteert in de vervolgkeuzelijst Type. U kunt de adaptieve vorm gebruiken die aan het werkschema wordt voorgelegd, beschikbaar bij een absolute weg, of beschikbaar bij een weg in een variabele wordt voorgelegd die. U kunt een variabele van typeKoord gebruiken om de weg te specificeren.\
   U kunt veelvoudige adaptieve vormen met een werkschema associëren. Dientengevolge, kunt u een adaptieve vorm op runtime specificeren gebruikend de beschikbare inputmethodes.

* **Interactieve communicatie gebruiken:** Specificeer de methode om van de input interactieve mededeling de plaats te bepalen. U kunt de interactieve mededeling gebruiken die aan het werkschema wordt voorgelegd, beschikbaar bij een absolute weg, of beschikbaar bij een weg in een variabele. U kunt een variabele van typeKoord gebruiken om de weg te specificeren. Deze optie is beschikbaar als u de Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.\
   **Opmerking:** U moet cm-agent-gebruikers en werkschema-gebruikers groepstaken hebben om tot Interactieve Communicatie Agent UI in AEM inbox toegang te hebben.

* **Aanpassingsformulier of interactief communicatiepad**: Specificeer de weg van de adaptieve vorm of de Interactieve Mededeling. U kunt de adaptieve vorm of de interactieve mededeling gebruiken die aan het werkschema, beschikbaar bij een absolute weg wordt voorgelegd, of de adaptieve vorm terugwinnen van een weg die in een variabele van koordgegevenstype wordt opgeslagen.
* **Selecteer invoer PDF gebruikend:** Specificeer de weg van een niet interactief Pdf- document. Het gebied is beschikbaar wanneer u een niet interactief Pdf- document op het gebied van het Type kiest. U kunt de input PDF selecteren gebruikend de weg die met betrekking tot de nuttige lading is, bewaard bij een absolute weg, of gebruikend een variabele van het gegevenstype van het Document. Bijvoorbeeld, [Payload_Directory]/Workflow/PDF/credit-card.pdf. De weg bestaat niet in crx-bewaarplaats. Een beheerder leidt tot de weg alvorens het te gebruiken. U hebt een Document van de toegelaten optie van het Verslag of op malplaatje gebaseerde aanpassingsvormen voor het gebruiken van de optie van de Weg van PDF nodig.
* **Voor voltooide taak, geef de adaptieve vorm terug zoals**: Wanneer een taak duidelijk is voltooid, kunt u de adaptieve vorm teruggeven als een alleen-lezen adaptief formulier of een PDF-document. U hebt een Document van toegelaten optie van het Verslag of op malplaatje gebaseerde aanpassingsvormen nodig om de adaptieve vorm als Document van Verslag terug te geven.
* **Voorgevuld:** De volgende gebieden die hieronder worden vermeld dienen als input aan de taak:

   * **Selecteer een bestand met invoergegevens met:** Pad van invoergegevensbestand (.json,. xml, .doc, of model van vormgegevens). U kunt het dossier van inputgegevens terugwinnen gebruikend een weg die met betrekking tot de nuttige lading is of het dossier terugwinnen dat in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen. Bijvoorbeeld, bevat het dossier de gegevens die voor de vorm door een toepassing van AEM Inbox worden voorgelegd. Een voorbeeldweg is [Payload_Directory]/workflow/data.
   * **Selecteer invoerbijlagen met:** De gehechtheid beschikbaar bij de plaats is in bijlage aan de vorm verbonden aan de taak. De weg is altijd met betrekking tot de nuttige lading. Een voorbeeldweg is [Payload_Directory]/gehechtheid/
   * **Kies input-JSON:** Selecteer een inputJSON dossier gebruikend een weg die met betrekking tot lading is of in een variabele van Document, JSON, of het Model van de Gegevens van de Vorm gegevenstype wordt opgeslagen. Deze optie is beschikbaar als u de Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van de drop-down lijst van het Type selecteert.
   * **Kies een aangepaste prefill-service:** Selecteer de prefill dienst om de gegevens terug te winnen en het Interactieve het kanaaldocument van het Communicatie Web of de Agent UI te prefill.

   * **Gebruik de prefill dienst van de hierboven geselecteerde interactieve mededeling:** Gebruik deze optie om de prefill dienst van de Interactieve Mededeling te gebruiken die in de Van het Gebruik Interactieve Communicatie drop-down lijst wordt bepaald.
   * **Attribuuttoewijzing aanvragen:** Gebruik de sectie van de Afbeelding van Attributen van het Verzoek om de [naam en de waarde van de verzoekattributen](../../forms/using/work-with-form-data-model.md#bindargument)te bepalen. Win de details van de gegevensbron terug die op de attributennaam en de waarde wordt gebaseerd die in het verzoek wordt gespecificeerd. U kunt een waarde van verzoekattributen bepalen gebruikend een letterlijke waarde of een variabele van het gegevenstype van het Koord.\
      De prefill dienst en de opties van de verzoekattributenafbeelding zijn beschikbaar slechts als u de Interactieve Communicatie Agent UI of het Interactieve Document van het Kanaal van het Communicatie Web van het Type van de drop-down lijst selecteert.

* **Voorgelegde informatie:** De volgende hieronder vermelde gebieden dienen als outputplaatsen aan de taak:

   * **Sla het uitvoerbestand op met behulp van:** Sparen het gegevensdossier (.json,. xml, .doc, of model van vormgegevens). Het gegevensdossier bevat informatie die door de bijbehorende vorm wordt voorgelegd. U kunt het dossier van outputgegevens bewaren gebruikend een weg die met betrekking tot de nuttige lading is of het opslaan in een variabele van Document, XML, of JSON gegevenstype. Bijvoorbeeld, [Payload_Directory]/Workflow/data, waar het gegeven een dossier is.
   * **Bevestigingen opslaan met:** Sparen de vormgehechtheid verstrekt in een taak. U kunt de gehechtheid bewaren gebruikend een weg die met betrekking tot de nuttige lading is of het opslaan in een variabele van serie van het gegevenstype van het Document.
   * **Document opslaan met behulp van:** Weg om een Document van het dossier van het Verslag op te slaan. Bijvoorbeeld, [Payload_Directory]/DocumentofRecord/credit-card.pdf. U kunt het Document van Verslag bewaren gebruikend een weg die met betrekking tot de nuttige lading is of het opslaan in een variabele van het gegevenstype van het Document. Als u **ten opzichte van de optie Payload** selecteert, wordt het Document van Verslag niet geproduceerd als het weggebied leeg wordt verlaten. Deze optie is beschikbaar slechts als u Aanpassingsvorm van de drop-down lijst van het Type selecteert.

   * **Sparen de gegevens van het Kanaal van het Web gebruikend:** Sparen het de gegevensdossier van het Kanaal van het Web gebruikend een weg die met betrekking tot de nuttige lading is of sla het in een variabele van Document, JSON, of het Model van de Gegevens van de Vorm gegevenstype op. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van het Type drop-down lijst selecteert.
   * **PDF-document opslaan met:** Sparen het Pdf- document gebruikend een weg die met betrekking tot de nuttige lading is of sla het in een variabele van het gegevenstype van het Document op. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van het Type drop-down lijst selecteert.
   * **Opmaaksjabloon opslaan met:** Sparen het lay-outmalplaatje gebruikend een weg die met betrekking tot de nuttige lading is of sla het in een variabele van het gegevenstype van het Document op. Het [lay-outmalplaatje](../../forms/using/layout-design-details.md) verwijst naar een XDP dossier dat u het gebruiken van de Ontwerper van Vormen creeert. Deze optie is beschikbaar slechts als u Interactieve Communicatie Agent UI van het Type drop-down lijst selecteert.

* **Toegewezen > Opties toewijzen:** Specificeer de methode om de taak aan een gebruiker toe te wijzen. U kunt de taak aan een gebruiker of een groep dynamisch toewijzen gebruikend het manuscript van de Kiezer van de Deelnemer of de taak toewijzen aan een specifieke gebruiker AEM of een groep.
* **Deelnemer:** De optie is beschikbaar wanneer de optie **dynamisch aan een gebruiker of een groep** op het Assign optiesgebied wordt geselecteerd. U kunt een ECMAScript of de dienst gebruiken om een gebruiker of een groep dynamisch te selecteren. Voor meer informatie, zie [dynamisch een werkschema toewijzen aan de gebruikers](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) en [Creërend een stap van de Deelnemer van de Manager van de Ervaring van douaneAdobe de Dynamische.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Deelnemers:** Het gebied is beschikbaar wanneer de **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** optie in het gebied van de Kiezer **van de** Deelnemer wordt geselecteerd. Het gebied staat u toe om gebruikers of groepen voor de optie te selecteren RandomParticipantChooser.

* **Geadresseerde:** Het gebied is beschikbaar wanneer **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** op het gebied van de Kiezer **van de** Deelnemer wordt geselecteerd. Het gebied staat u toe om een variabele van het gegevenstype van het Koord te selecteren om de ontvanger te bepalen.

* **Argumenten:** Het gebied is beschikbaar wanneer een manuscript buiten het manuscript RandomParticipantChoose in het gebied van de Chooser van de Deelnemer wordt geselecteerd. Het gebied staat u toe om een lijst van een komma gescheiden argumenten voor het manuscript te verstrekken dat in het gebied van de Chooser van de Deelnemer wordt geselecteerd.

* **Gebruiker of groep:** De taak wordt toegewezen aan geselecteerde gebruiker of groep. De optie is beschikbaar wanneer **aan een specifieke gebruiker of groepsoptie** op het gebied van de **Toewijzing opties** wordt geselecteerd. Het gebied maakt een lijst van alle gebruikers en groepen van de werkschema-gebruikers groep.\
   Het drop-down menu van de **Gebruiker of van de Groep** maakt een lijst van de gebruikers en de groepen die de het programma geopende gebruiker toegang tot heeft. De gebruikersbenamingsvertoning hangt van af als u toegangstoestemmingen op de **gebruikersknoop** in crx-bewaarplaats voor die bepaalde gebruiker hebt.

* **Stuur de geadresseerde per e-mail op de hoogte:** Selecteer deze optie om e-mailberichten naar de toegewezen persoon te verzenden. Deze berichten worden verzonden wanneer een taak aan een gebruiker wordt toegewezen. Alvorens de optie te gebruiken, laat de berichten van de Console van het Web AEM toe. Voor geleidelijke instructies, zie e-mailberichten [vormen voor toewijst taakstap](../../forms/using/aem-forms-workflow.md)

* **HTML-e-mailtemplate**: Selecteer een e-mailtemplate voor de e-mail met bericht. Om een malplaatje uit te geven, wijzig het dossier dat in /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in crx-bewaarplaats wordt gevestigd.
* **Delegatie toestaan aan:** AEM Inbox verstrekt een optie aan de het programma geopende gebruiker om het toegewezen werkschema aan een andere gebruiker af te vaardigen. U wordt toegestaan om binnen de zelfde groep of aan de werkschemagebruiker van een andere groep te delegeren. Als de taak aan één enkele gebruiker wordt toegewezen en de **sta delegatie aan leden van de optie van de bestemmingsgroep** toe wordt geselecteerd, dan is het niet mogelijk om de taak aan een andere gebruiker of een groep te delegeren.
* **Share Settings:** AEM Inbox verstrekt opties om enig of alle taken in inbox met een andere gebruikers te delen:
   * Wanneer **Allow wordt de toegewezen persoon om uitdrukkelijk in inbox** optie te delen geselecteerd, kan de gebruiker op de taak klikken en het delen met een andere gebruiker AEM.
   * Wanneer **Allow wordt de toegewezen persoon om via inbox het delen** optie te delen geselecteerd en een gebruiker deelt zijn Punten Inbox of andere gebruikers toestaat om tot zijn Inbox punten toegang te hebben, slechts worden de taken met bovengenoemde toegelaten optie gedeeld met andere gebruikers.

* **Acties > Standaardacties:** Uit de doos, leg, sparen voor, en de acties van het Terugstellen zijn beschikbaar. Alle standaardacties worden toegelaten, door gebrek.
* **Routevariabele:** Naam van de routevariabele. De routevariabele vangt douaneacties die een gebruiker in AEM Inbox selecteert.
* **Routes:** Een taak kan zich aan verschillende routes vertakken. Wanneer geselecteerd in AEM Inbox, keert de route een waarde en de werkschematakken terug die op de geselecteerde route worden gebaseerd. U kunt of routes in een variabele van serie van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om routes manueel toe te voegen.

* **Titel**: Specificeer de titel voor de route. Het wordt getoond in AEM Inbox.
* **Koraalpictogram**: Specificeer de attributen van HTML van een koraalpictogram. De bibliotheek van Adobe CorelUI verstrekt een enorme reeks aanraking-eerste pictogrammen. U kunt een pictogram voor de route kiezen en gebruiken. Het wordt getoond samen met de titel in AEM Inbox. Als u de routes in een variabele opslaat, gebruiken de routes een standaard het koraalpictogram van &quot;Markeringen&quot;.
* **Toestaan van de geadresseerde om commentaar** toe te voegen: Selecteer deze optie om commentaren voor de taak toe te laten. Een ontvanger kan de commentaren van binnen AEM Inbox op het tijdstip van taakindiening toevoegen.
* **Commentaar opslaan in variabele:** Sparen de commentaar in een variabele van het gegevenstype van het Koord. Deze optie wordt alleen weergegeven als u het selectievakje Toegewezen persoon **toestaan selecteert om commentaar** toe te voegen.

* **Toestaan van de ontvanger dat deze bijlage(s) aan de taak** toevoegt: Selecteer deze optie om gehechtheid voor de taak toe te laten. Een toegewezen persoon kan de bijlagen toevoegen van binnen AEM Inbox op het tijdstip van het indienen van de taak.
* **Sparen de gehechtheid van de outputtaak gebruikend**: Specificeer de plaats van gehechtheidsomslag. U kunt de gehechtheid van de outputtaak bewaren gebruikend een weg met betrekking tot nuttige lading of in een variabele van serie van documentgegevenstype. Deze optie wordt alleen weergegeven als u de optie Toegewezen persoon **toestaan selecteert om bijlage(s) toe te voegen aan het selectievakje taak** en het **Aanpassingsformulier**, het adaptieve **alleen-lezen adaptieve formulier** of het **niet-interactieve PDF-document** selecteert in de vervolgkeuzelijst **Type** **** op het tabblad Document.

>[!NOTE]
>
>Gebruik het lusje van Gehechtheid in Agent UI tijdens runtime om de gehechtheid aan een Interactieve Mededeling te associëren. De bijbehorende gehechtheid toont als taakgehechtheid in sidekick na het openen van het het werkpunt in een Volledige staat.

* **De douanemeta-gegevens van het gebruik:** Selecteer deze optie om het gebied van de douanemeta-gegevens toe te laten. De meta-gegevens van de douane wordt gebruikt in e-mailmalplaatjes.
* **Aangepaste metagegevens:** Selecteer een douanemeta-gegevens voor de e-mailmalplaatjes. De douanemeta-gegevens is beschikbaar in crx-bewaarplaats bij apps/fd/dashboard/scripts/metadataScripts. Het opgegeven pad bestaat niet in crx-repository. Een beheerder leidt tot de weg alvorens het te gebruiken. U kunt de dienst voor de douanemeta-gegevens ook gebruiken. U kunt de interface ook uitbreiden WorkitemUserMetadataService om douanemeta-gegevens te verstrekken.
* **Toon Gegevens van Vorige Stappen**: Selecteer deze optie om de toewijzing van taken mogelijk te maken om vorige toewijzing, reeds ondernomen actie op de taak, commentaren die aan de taak worden toegevoegd, en document van verslag van de voltooide taak, indien beschikbaar, te bekijken.
* **Gegevens weergeven uit volgende stappen:** Selecteer deze optie om de huidige ontvanger toe te laten om de actie te bekijken en commentaren die aan taak door verdere ontvangers worden toegevoegd te bekijken. Het staat ook de huidige aangewezen toe om een document van verslag van de voltooide taak te bekijken, indien beschikbaar.
* **Zichtbaarheid van het gegevenstype:** Door gebrek, kan een ontvanger een Document van Verslag bekijken, kan de toegewezen personen, de genomen actie, en de commentaren die de vorige en verdere ontvangers hebben toegevoegd. Gebruik het zicht van gegevenstype optie om het type van gegevens te beperken zichtbaar aan de ontvangers.

## E-mailstap verzenden {#send-email-step}

Gebruik de e-mailstap om een e-mail te verzenden, bijvoorbeeld een e-mail met een document van verslag, verbinding van een adaptief formulier, verbinding van een interactieve mededeling, of met een document in bijlage PDF. Stuur e-mailstappen voor [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). De e-mails van HTML zijn ontvankelijk en passen aan de e-mailcliënt en het schermgrootte van de ontvangers aan. U kunt een HTML- e-mailmalplaatje gebruiken om verschijning, kleur-regeling, en gedrag van het van e-mail te bepalen.

De e-mailstap maakt gebruik van de Day CQ Mail Service om e-mails te verzenden. Zorg ervoor dat de [e-mailservice](../../forms/using/aem-forms-workflow.md) is geconfigureerd voordat u de e-mailstap gebruikt. De e-mailstap heeft de volgende eigenschappen:

**Titel:** De titel van de staphulp identificeert de stap in de werkschemaredacteur.

**Beschrijving:** De verklaring is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

**E-mail Betreft:** Onderwerp kan van een werkschemameta-gegevens worden teruggewonnen, manueel worden gespecificeerd, of van de waarde worden teruggewonnen die in een variabele wordt opgeslagen. Selecteer uit de volgende opties:

* **Letterlijk -** specificeer manueel een onderwerp.
* **Win van de meta-gegevens** van het Werkschema terug - Win het onderwerp van een meta-gegevensbezit terug.
* **Variabele** - Win het onderwerp van de waarde terug die in een variabele van het type van koordgegevens wordt opgeslagen.

**HTML-e-mailtemplate**: HTML-template voor de e-mail. U kunt variabelen in een e-mailmalplaatje specificeren. De E-mailStap haalt en toont alle variabelen inbegrepen in een malplaatje voor input uit.

**Metagegevens e-mailtemplate:** De waarde van de variabelen van het e-mailmalplaatje kan een user-specified waarde, de weg van activa op de auteur zijn of publiceert server, beeld, of een bezit van de werkschemameta-gegevens.

* **Letterlijk:** Gebruik de optie wanneer u de nauwkeurige te specificeren waarde kent. Bijvoorbeeld, [example@example.com](mailto:example@example.com).

* **Werkstroommetagegevens:** Gebruik de optie wanneer de te gebruiken waarde in een bezit van de werkschemameta-gegevens wordt bewaard. Na het selecteren van de optie, ga de naam van het meta-gegevensbezit in het lege tekstvakje onder de optie van de Meta-gegevens van het Werkschema in. Bijvoorbeeld, emailAddress.
* **URL van bedrijfsmiddel:** Gebruik de optie om een Webverbinding van een interactieve mededeling aan e-mail in te bedden. Na het selecteren van de optie, doorblader en kies de interactieve mededeling om in te bedden. De activa kunnen op de auteur verblijven of publiceren server.
* **Afbeelding:** Gebruik de optie om een afbeelding in te sluiten op de e-mail. Na het selecteren van de optie, doorblader en kies het beeld. De afbeeldingsoptie is alleen beschikbaar voor de afbeeldingstags (&lt;img src=&quot;*&quot;/>) die beschikbaar zijn in de e-mailsjabloon.

**E-mailadres van verzender/ontvanger:** Selecteer de **Letterlijke** optie om een e-mailadres handmatig op te geven of selecteer de optie **Ophalen uit de optie Werkstroommetagegevens** om het e-mailadres op te halen uit een eigenschap metagegevens. U kunt een lijst van de series van het meta-gegevensbezit voor de optie ook specificeren **Win van de meta-gegevens** van het Werkschema terug. Selecteer de **Veranderlijke** optie om het e-mailadres van de waarde terug te winnen die in een variabele van het type van koordgegevens wordt opgeslagen.

**Bijvoegsel bestand:** De bedrijfsmiddelen die op de opgegeven locatie beschikbaar zijn, zijn aan de e-mail gekoppeld. De weg van de activa kan met betrekking tot de nuttige lading of absolute weg zijn. Een voorbeeldweg is [Payload_Directory]/gehechtheid/.

Selecteer de **Veranderlijke** optie om de dossiergehechtheid terug te winnen die in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen.

**Bestandsnaam:** Naam van het dossier van de e-mailgehechtheid. De E-mailstap verandert de oorspronkelijke bestandsnaam van de bijlage in de opgegeven bestandsnaam. De naam kan manueel worden gespecificeerd of van een bezit van de werkschemameta-gegevens of een variabele worden teruggewonnen. Gebruik de **Letterlijke** optie wanneer u de nauwkeurige te specificeren waarde kent. Gebruik de **Veranderlijke** optie om het dossier terug te winnen - noem van de waarde die in een variabele van het type van koordgegevens wordt opgeslagen. Gebruik **terugwinnen van een optie van de Meta-gegevens** van het Werkschema wanneer de te gebruiken waarde in een bezit van de werkschemameta-gegevens wordt opgeslagen.

## Document genereren in stap Record {#generate-document-of-record-step}

Wanneer een formulier wordt ingevuld of ingediend, kunt u het formulier in gedrukte of in documentformaat registreren. Dit wordt bedoeld als Document van Verslag (DoR). U kunt het Generate Document van verslagstap gebruiken om een read-only of interactieve versie PDF van een adaptieve vorm tot stand te brengen. De PDF-versie bevat informatie die is ingevuld in het formulier en de lay-out van het adaptieve formulier.

Het document van de stap van het Verslag heeft de volgende eigenschappen:

**Aanpassingsformulier** gebruiken: Specificeer de methode om van de input aanpassingsvorm de plaats te bepalen. U kunt de adaptieve vorm gebruiken die aan het werkschema wordt voorgelegd, beschikbaar bij een absolute weg, of beschikbaar bij een weg in een variabele wordt voorgelegd die. U kunt een variabele van gegevenstype van het Koord gebruiken om de weg op de **Uitgezochte variabele te specificeren om gebied op te lossen** .\
U kunt veelvoudige adaptieve vormen met een werkschema associëren. Dientengevolge, kunt u een adaptieve vorm op runtime specificeren gebruikend de beschikbare inputmethodes.

**Aanpassingspad**: Geef het pad van het adaptieve formulier op. Het gebied is beschikbaar wanneer u **Beschikbaar bij een absolute wegoptie** van het gebied van de Vorm **van het** Gebruik de Aanpassings selecteert.

**Selecteer Invoergegevens met behulp van:** Pad van de invoergegevens voor het adaptieve formulier. U kunt de gegevens bij een plaats met betrekking tot de nuttige lading houden, een absolute weg van de gegevens specificeren, of gegevens terugwinnen die in een variabele van Document, JSON, of het gegevenstype van XML worden opgeslagen. De invoergegevens worden samengevoegd met het adaptieve formulier om een recorddocument te maken.

**Selecteer de de gehechtheidsweg van de Input gebruikend:** Pad van de bijlagen. Deze bijlagen zijn opgenomen in het Document of Record. U kunt de gehechtheid houden bij een plaats met betrekking tot de nuttige lading, een absolute weg van de gehechtheid specificeren, of gehechtheid terugwinnen die in een variabele van serie van het gegevenstype van het Document wordt opgeslagen.

Als u de weg van een omslag specificeert, bijvoorbeeld, zijn de gehechtheid, alle dossiers direct beschikbaar in de omslag in bijlage aan Document van Verslag. Als om het even welke dossiers in de omslagen beschikbaar direct beschikbaar in de gespecificeerde gehechtheidsweg zijn, zijn de dossiers inbegrepen in Document van Verslag als gehechtheid. Als er om het even welke omslagen in direct beschikbare omslagen zijn, worden die overgeslagen.

**Opslaan van gegenereerd document met record met de volgende opties:** Specificeer de plaats om een document van verslagdossier te houden. U kunt verkiezen om de nuttige ladingsomslag te beschrijven, document van verslag te plaatsen bij een plaats binnen de ladingsfolder, of het document van verslag op te slaan in een variabele van het gegevenstype van het Document.

**Lokaal**: Specificeer de taal van het document van verslag. Selecteer **Letterlijk** om de scène van een drop-down lijst te selecteren of **Variabele** te selecteren om de scène van de waarde terug te winnen die in een variabele van het type van koordgegevens wordt opgeslagen. U moet de scènecode bepalen terwijl het opslaan van de waarde voor de scène in een variabele. Bijvoorbeeld, specificeer **en_US** voor het Engels en **fr_FR** voor het Frans.

## Formuliergegevensmodel-servicesstap aanhalen {#invoke-form-data-model-service-step}

U kunt de Integratie [van de Gegevens van de Vormen](../../forms/using/data-integration.md) AEM gebruiken om met ongelijksoortige gegevensbronnen te vormen en te verbinden. Deze gegevensbronnen kunnen een gegevensbestand, de Webdienst, de dienst van REST, de dienst van OData, en de oplossing van CRM zijn. De Integratie van de Gegevens van Vormen AEM staat u toe om een model van vormgegevens te creëren dat diverse diensten omvat om gegevensherwinning, toevoeging, bijwerkende verrichtingen op het gevormde gegevensbestand uit te voeren. U kunt de **Invoke stap** van de Dienst van het Model van Gegevens gebruiken om een model van vormgegevens (FDM) te selecteren en de diensten van FDM te gebruiken om, gegevens terug te winnen bij te werken of toe te voegen om gegevensbronnen te verdelen.

Om input voor gebieden van de stap te verklaren, worden de volgende gegevensbestandlijst en het dossier JSON gebruikt als voorbeeld:

**Voorbeeldtabel met klantgegevens**

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
   <td>Achternaam</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>Klant-ID</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>E-mailadres<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Voorbeeld JSON-bestand**

```
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

De aanhalen stap van de ModelDienst van de Gegevens van de Vorm heeft de hieronder vermelde gebieden om modelverrichtingen van vormgegevens te vergemakkelijken:

* **Titel:** Titel van de stap. Het helpt de stap in de werkschemaredacteur identificeren.
* **Beschrijving:** Uitleg nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **Formuliergegevensmodelpad**: Doorblader en selecteer een model van vormgegevens huidig op de server.

* **Service**: Lijst van de diensten die het geselecteerde model van vormgegevens verstrekt.
* **De input voor de diensten > verstrekt inputgegevens gebruikend letterlijke, variabele, of werkschemameta-gegevens, en een JSON dossier**: Een dienst kan veelvoudige argumenten hebben. Selecteer de optie om de waarde van de de dienstargumenten uit een bezit van de werkschemameta-gegevens, een voorwerp JSON, een variabele te verkrijgen, of direct de waarde in het verstrekte tekstvakje in te gaan:

   * **Letterlijk:** Gebruik de optie wanneer u de nauwkeurige te specificeren waarde kent. Bijvoorbeeld, srose@we.info.
   * **Variabele:** Gebruik de optie om de waarde terug te winnen die in een variabele wordt opgeslagen.
   * **Win van de Meta-gegevens van het Werkschema terug:** Gebruik de optie wanneer de te gebruiken waarde in een bezit van de werkschemameta-gegevens wordt bewaard. Bijvoorbeeld, emailAddress.
   * **JSON Dot Notation:** Gebruik de optie wanneer de te gebruiken waarde in een JSON dossier is. Bijvoorbeeld, insurance.customerDetails.emailAddress. De optie van de Nota van de Dot van JSON is beschikbaar slechts als de de inputgebieden van de Kaart van inputJSON optie wordt geselecteerd.
   * **De inputgebieden van de kaart van input JSON:** Specificeer weg van een JSON dossier om inputwaarde van sommige de dienstargumenten uit het JSON dossier te verkrijgen. De weg van het JSON dossier kan met betrekking tot de nuttige lading, een absolute weg zijn, of u kunt een inputJSON- document selecteren gebruikend een variabele van het Model van de Gegevens van JSON of van de Vorm.

* **Input voor services > Voer inputgegevens in met behulp van een variabele of een JSON-bestand:** Selecteer de optie om waarden voor alle argumenten uit een JSON dossier te verkrijgen dat bij een absolute weg, bij een weg met betrekking tot nuttige lading, of in een variabele wordt opgeslagen.
* **Selecteer InvoerJSON-document met**: Het JSON dossier dat waarden voor alle de dienstargumenten bevat. De weg van het JSON dossier kan **met betrekking tot de nuttige lading** of een **absolute weg zijn.** U kunt het inputJSON- document ook terugwinnen gebruikend een variabele van JSON of het Model van de Gegevens van de Vorm gegevenstype.

* **JSON Dot Notation:** Verlaat de gebiedsspatie om alle voorwerpen van het gespecificeerde JSON dossier als input voor de dienstargumenten te gebruiken. Om een specifiek voorwerp JSON van het gespecificeerde JSON dossier als input voor de dienstargumenten te lezen, specificeer puntaantekening voor het voorwerp JSON, bijvoorbeeld, als u een JSON gelijkend op die aan het begin van de sectie hebt wordt vermeld, specificeer insurance.customerDetails om alle details van een klant als input aan de dienst te verstrekken.
* **Output van de dienst > Kaart en schrijft outputwaarden aan variabele of meta-gegevens:** Selecteer de optie om de outputwaarden als eigenschappen van de de meta-gegevensknoop van de werkschemainstantie in crx-bewaarplaats op te slaan. Specificeer de naam van het meta-gegevensbezit en selecteer de overeenkomstige attributen van de de dienstoutput die met meta-gegevensbezit moeten worden in kaart gebracht, bijvoorbeeld, de phone_number die door de outputdienst met het phone_aantalbezit van werkschemameta-gegevens is teruggekeerd in kaart brengen. Op dezelfde manier kunt u de output in een variabele van Lang gegevenstype opslaan.
* **Output van de dienst > sparen output aan variabele of een JSON dossier:** Selecteer de optie om de outputwaarden in een JSON dossier bij een absolute weg, bij een weg met betrekking tot nuttige lading, of in een variabele op te slaan.
* **U kunt het uitvoerJSON-document opslaan met de volgende opties:** Sparen het outputJSON dossier. De weg van het outputJSON dossier kan met betrekking tot de nuttige lading of een absolute weg zijn. U kunt het outputJSON dossier ook bewaren gebruikend een variabele van JSON of het Model van de Gegevens van de Vorm gegevenstype.

## Stap document ondertekenen {#sign-document-step}

De stap van het Document van het Teken laat u toe om het Teken van Adobe te gebruiken om documenten te ondertekenen. De stap van het Document van het Teken heeft de volgende eigenschappen:

* **Naam van overeenkomst:** Geef de titel van de overeenkomst op. De naam van de overeenkomst wordt onderdeel van het onderwerp en de tekst van het lichaam van de e-mail die naar de ondertekenaars wordt verzonden. U kunt of de naam in een variabele van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om de naam manueel toe te voegen.

* **Lokaal:** Geef de taal op voor de opties voor e-mail en verificatie. U kunt of de scène in een variabele van het gegevenstype van het Koord opslaan of **Letterlijk** selecteren om de scène van de lijst van beschikbare opties te kiezen. U moet de scènecode bepalen terwijl het opslaan van de waarde voor de scène in een variabele. Bijvoorbeeld, specificeer **en_US** voor het Engels en **fr_FR** voor het Frans.

* **Configuratie** van de Wolk van het Teken van Adobe: Kies een Configuratie van de Wolk van het Teken van Adobe. Als u het Teken van Adobe niet voor Vormen AEM hebt gevormd, zie het Teken van Adobe met Vormen [](../../forms/using/adobe-sign-integration-adaptive-forms.md)integreren AEM.

* **Selecteer Document dat u wilt ondertekenen met:** U kunt een document van een plaats met betrekking tot de lading kiezen, nuttige lading gebruiken als document, een absolute weg van het document specificeren, of het document terugwinnen dat in een variabele van het gegevenstype van het Document wordt opgeslagen.
* **Dagen tot uiterste termijn:** Een document is duidelijk verschuldigd (overgegaane termijn) nadat er geen activiteit op de taak voor het aantal dagen is specificeert op de **Dagen tot het gebied van de Termijn** . Het aantal dagen wordt geteld nadat het gedocumenteerde aan een gebruiker voor het ondertekenen wordt toegewezen.
* **Frequentie per e-mail herinnering:** U kunt een herinneringse-mail met dagelijkse of wekelijkse tussenpozen verzenden. De week wordt geteld vanaf de dag de gedocumenteerde wordt toegewezen aan een gebruiker voor het ondertekenen.
* **Handtekeningsproces:** U kunt verkiezen om een document in een opeenvolging of een parallelle orde te ondertekenen. In opeenvolgende orde, ontvangt één ondertekenaar het document tegelijkertijd voor het ondertekenen. Nadat de eerste ondertekenaar het ondertekenen van het document voltooit, dan wordt het document verzonden naar de tweede onderschrijver, etc. In parallelle volgorde kunnen meerdere signaalgevers tegelijkertijd een document ondertekenen.
* **URL omleiden:** Specificeer een omleiding URL. Nadat het document is ondertekend, kunt u de toegewezen persoon omleiden naar een URL. Gewoonlijk, bevat dit URL een dank u bericht of verdere instructies.
* **Werkstroomstadium:** Een werkschema kan veelvoudige stadia hebben. Deze stadia worden getoond in AEM Inbox. U kunt deze stadia in de eigenschappen van het model bepalen (Sidetrap > Pagina > de Eigenschappen van de Pagina > de Fanden).
* **Selecteer ondertekenaars:** Specificeer de methode om signers voor het document te kiezen. U kunt het werkschema aan een gebruiker of een groep dynamisch toewijzen of manueel details van een onderschrijver toevoegen.
* **Manuscript of de dienst om signers te selecteren:** De optie is beschikbaar slechts als de dynamisch optie op het Uitgezochte gebied van Ondertekenaars wordt geselecteerd. U kunt een ECMAScript of de dienst specificeren om signers en controleopties voor een document te kiezen.
* **Gegevens van de ondertekenaar:** De optie is beschikbaar slechts als de manueel optie op het Uitgezochte gebied van Ondertekenaars wordt geselecteerd. Geef het e-mailadres op en kies een optioneel verificatiemechanisme. Alvorens een controlemechanisme te selecteren in twee stappen, zorg ervoor dat de overeenkomstige controleoptie voor de gevormde rekening van het Teken van Adobe wordt toegelaten. U kunt een variabele van gegevenstype van het Koord gebruiken om waarden voor de gebieden van het **[!UICONTROL E-mail]**, van de Code **[!UICONTROL van het]** Land, en van het Aantal **[!UICONTROL van de]** Telefoon te bepalen. De velden **[!UICONTROL Landcode]** en **[!UICONTROL Telefoonnummer]** worden alleen weergegeven als u **[!UICONTROL Telefoonverificatie]** selecteert in de vervolgkeuzelijst **[!UICONTROL 2 stappen verificatie]** .
* **Statusvariabele:** Een van het Teken van Adobe toegelaten document slaat het ondertekenen van status van het document in een variabele van het gegevenstype van het Koord op. Specificeer de naam van de statusvariabele (adobeSignStatus). Een statusvariabele van een instantie is beschikbaar in CRXDE bij /etc/workflow/instanties/&lt;server>/&lt;date-time>/&lt;instance van werkschemamodel>/workItems/&lt;node>/metaData bevat status van een variabele.
* **Opslaan van ondertekend document met de volgende opties:** Specificeer de plaats om ondertekende documenten te houden. U kunt verkiezen om het ladingsdossier te beschrijven, het ondertekende document te plaatsen bij een plaats binnen de ladingsfolder, of het ondertekende document op te slaan in een variabele van het type van Document.

## De stappen van de Diensten van het Document {#document-services-steps}

De diensten van het Document AEM zijn een reeks diensten voor het creëren van, het assembleren van, en het beveiligen van Pdf- Documenten. De Vormen van AEM verstrekt een afzonderlijke stap van het Werkschema AEM voor elke documentdienst.

Gelijkaardig aan andere het werkschemastappen van Vormen AEM, zoals Assign Taak, verzend E-mail, en het Document van het Teken, kunt u variabelen in alle de dienstenstappen van het Document gebruiken AEM. Voor meer informatie bij het creëren van en het leiden van variabelen, zie [Variabelen in werkschema](../../forms/using/variable-in-aem-workflows.md)AEM.

### Stempelstap Documenttijd toepassen {#apply-document-time-stamp-step}

Voeg tijdzegel aan een document toe. U verstrekt documentdetails zoals de weg van het inputdocument, de naam van het inputdocument, plaats om uitgevoerde gegevens op te slaan. U kunt verkiezen om bestaand ladingsdossier te beschrijven, een verschillend dossier te kiezen - noem om gegevens in een verschillend dossier op te slaan onder nuttige ladingsomslag, een absolute weg aan de gegevens te verstrekken, of gegevens op te slaan in een variabele van het gegevenstype van het Document.

### Omzetten in stap naar afbeelding {#convert-to-image-step}

Zet een Pdf- document in lijst van beelden om. De gesteunde beeldformaten zijn JPEG, JPEG2000, PNG, en TIF. De volgende informatie is op omzettingen in beelden van TIF van toepassing:

* Er wordt een TIFF-bestand met meerdere pagina&#39;s gegenereerd.
* Sommige annotaties zijn niet inbegrepen in beelden van TIF. De annotaties die Acrobaat vereisen om hun verschijning te produceren zijn niet inbegrepen.

### Converteren naar PDF/A-stap {#convert-to-pdf-a-step}

Zet een Pdf- document in formaat PDF/A om gebruikend de verstrekte opties. De PDF/A-versie van Portable Document Format (PDF) is gespecialiseerd in archivering en langetermijnbewaring van documenten.

### Converteren naar PS-stap {#convert-to-ps-step}

PDF-documenten converteren naar PostScript. Wanneer het omzetten in PostScript, kunt u de omzettingsverrichting gebruiken om het brondocument te specificeren en of om in niveau 2 of 3 van PostScript om te zetten. Het PDF-document dat u converteert naar een PostScript-bestand moet niet interactief zijn.

### PDF maken vanuit opgegeven tekststap {#create-pdf-from-specified-type-step}

Produceer een Pdf- document van een inputdossier. Het inputdocument kan met betrekking tot de nuttige lading zijn, een absolute weg hebben, kan nuttige lading zelf zijn, of in een variabele van het gegevenstype van het Document worden opgeslagen.

### PDF maken vanuit URL/HTML/ZIP-stap {#create-pdf-from-url-html-zip-step}

Produceert een Pdf- document van geleverde URL, HTML, en het dossier van het PIT.

### Gegevensstap exporteren {#export-data-step}

Voert gegevens van een PDF vormen of een XDP dossier uit. Het vereist u om de dossierweg van het Document van de Input en het Formaat van de Gegevens van de Uitvoer in te gaan. De opties voor het Formaat van de Gegevens van de Uitvoer zijn Auto, XDP en XmlData.

### PDF exporteren naar opgegeven tekststap {#export-pdf-to-specified-type-step}

Zet een Pdf- document in een geselecteerd formaat om.

### Niet-interactieve PDF-stap genereren {#generatenoninteractive}

Produceer een niet-Interactieve PDF. Het verstrekt diverse aanpassingsopties.

>[!NOTE]
>
>U kunt variabelen gebruiken om het malplaatjedossier voor inputdocumenten te specificeren. Sla de weg van het malplaatjedossier in een variabele van het gegevenstype van het Koord op.

### Gegevensstap importeren {#import-data-step}

Voegt vormgegevens in een vorm samen PDF. U kunt vormgegevens in een vorm invoeren PDF.

### De stap DDX aanhalen {#invokeddx}

Voert het Ddx- dossier op de gespecificeerde kaart van inputdocumenten uit en keert de gemanipuleerde Pdf- documenten terug.

>[!NOTE]
>
>U kunt variabelen gebruiken om het Ddx- dossier voor inputdocumenten te specificeren. Sla het DDX-bestand op in een variabele van het gegevenstype Document of XML.

### PDF-stap optimaliseren {#optimize-pdf-step}

Optimaliseert Pdf- dossiers door hun grootte te verminderen. Het resultaat van deze omzetting is Pdf- dossiers die kleiner kunnen zijn dan hun originele versies. Deze verrichting zet ook Pdf- documenten in de versie PDF om die in de optimaliseringsparameters wordt gespecificeerd.

De montages van de optimalisering specificeren hoe de dossiers worden geoptimaliseerd. Hier zijn voorbeeldmontages:

* Doelversie PDF
* Objecten zoals JavaScript-acties en ingesloten paginaminiaturen verwijderen
* Het verwerpen van gebruikersgegevens zoals commentaren en dossiergehechtheid
* Ongeldige of ongebruikte instellingen verwijderen
* Comprimeren van niet-gecomprimeerde gegevens of het gebruiken van efficiëntere compressiealgoritmen
* Ingebouwde lettertypen verwijderen
* Transparantiewaarden instellen

### PDF-formulierstap renderen {#renderpdf}

Geeft een vorm terug die in de Ontwerper van de Vorm (XDP) wordt gecreeerd aan een vorm PDF.

>[!NOTE]
>
>U kunt variabelen gebruiken om het malplaatjedossier voor inputdocumenten te specificeren. Sla de weg van het malplaatjedossier in een variabele van het gegevenstype van het Koord op.

### Beveiligde documentstap {#secure-document-step}

Codeer, teken, en certificeer een document. De Vormen van AEM steunen zowel op wachtwoord gebaseerde als op certificaat gebaseerde basisencryptie. U kunt ook kiezen tussen verschillende algoritmen voor het ondertekenen van documenten. Bijvoorbeeld, SHA-256 en SH-512. U kunt de werkschemastap aan lezer ook gebruiken breidt Pdf- documenten uit. De werkschemastap verstrekt optie om streepjescode het decoderen, digitale handtekeningen, de invoer en de uitvoer van Pdf- gegevens, en andere opties toe te laten.

### Verzenden naar printerstap {#send-to-printer-step}

Een document rechtstreeks naar een printer sturen. Het steunt de volgende mechanismen van de druktoegang:

* **Direct toegankelijke printer**: Een printer die op de zelfde computer geïnstalleerd is wordt genoemd een directe toegankelijke printer, en de computer wordt genoemd printergastheer. Dit type printer kan een lokale printer zijn die direct met de computer wordt verbonden.
* **Indirect toegankelijke printer**: De printer die op een drukserver wordt geïnstalleerd wordt betreden van andere computers. De technologieën zoals het gemeenschappelijke systeem van de druk UNIX® (CUPS) en het protocol van de Printer Daemon van de Lijn (LPD) zijn beschikbaar om met een netwerkprinter te verbinden. Om tot een indirecte toegankelijke printer toegang te hebben, specificeer IP van de drukserver of gastheernaam. Gebruikend dit mechanisme, kunt u een document naar LPD URI verzenden wanneer het netwerk LPD het lopen heeft. Het mechanisme laat u het document aan om het even welke printer leiden die met het netwerk wordt verbonden dat LPD het lopen heeft.

### Afgedrukte uitvoerstap genereren {#generatePrintedOutput}

De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer met een formulierontwerp en een gegevensbestand. Het gegevensdossier wordt samengevoegd met het vormontwerp en voor druk geformatteerd. De output die door deze stap wordt geproduceerd kan rechtstreeks naar een printer worden verzonden of als dossier worden opgeslagen. Men adviseert dat u deze stap gebruikt wanneer u vormontwerpen of gegevens van een toepassing wilt gebruiken. Als uw vormontwerpen of vormontwerpen op het netwerk, het lokale dossiersysteem, of de plaats van HTTP worden gevestigd, gebruik de verrichting generatePrintedOutput.

Bijvoorbeeld, vereist uw toepassing dat u een vormontwerp met een gegevensdossier samenvoegt. De gegevens bevatten honderden verslagen. Bovendien vereist het de output wordt verzonden naar een printer die ZPL steunt. Het vormontwerp en uw inputgegevens worden gevestigd in een toepassing. Gebruik de verrichting generatePrintedOutput om elk verslag met een vormontwerp samen te voegen en de output te verzenden naar een printer die ZPL steunt.

De Generate Gedrukte stap van de Output heeft de volgende eigenschappen:

**Invoereigenschappen**

* **[!UICONTROL Selecteer sjabloonbestand met]**: Specificeer de weg van het malplaatjedossier. U kunt het malplaatjedossier selecteren gebruikend de weg die met betrekking tot de nuttige lading is, die bij een absolute weg, of gebruikend een variabele van het gegevenstype van het Document wordt opgeslagen. Bijvoorbeeld, [Payload_Directory]/Workflow/data.xml. Als de weg niet in crx-bewaarplaats bestaat, kan een beheerder de weg tot stand brengen alvorens het te gebruiken. Bovendien kunt u nuttige lading als dossier van inputgegevens ook goedkeuren.

* **[!UICONTROL Selecteer gegevensdocument gebruikend]**: Specificeer de weg van een dossier van inputgegevens. U kunt het dossier van inputgegevens selecteren gebruikend de weg die met betrekking tot de nuttige lading is, die bij een absolute weg, of gebruikend een variabele van het gegevenstype van het Document wordt opgeslagen. Bijvoorbeeld, [Payload_Directory]/Workflow/data.xml. Als de weg niet in crx-bewaarplaats bestaat, kan een beheerder de weg tot stand brengen alvorens het te gebruiken.

* **[!UICONTROL Printerindeling]**: Een waarde van het Formaat van de Druk die de taal specificeert van de paginabeschrijving te gebruiken, wanneer een XDC dossier niet wordt verstrekt, om de outputstroom te produceren. Als u een letterlijke waarde verstrekt, selecteer één van deze waarden:

   * **[!UICONTROL Aangepaste PCL]**: Gebruik de optie om een douaneXDC dossier voor PCL te specificeren.
   * **[!UICONTROL Aangepaste PostScript]**: Gebruik de optie om een douaneXDC dossier voor PostScript te specificeren.
   * **[!UICONTROL Aangepaste ZPL]**: Gebruik de optie om een douaneXDC- dossierdossier voor ZPL te specificeren.
   * **[!UICONTROL Generieke kleur PCL (5c)]**: Gebruik een generische kleur PCL (5c).
   * **[!UICONTROL Generiek PostScript Level3]**: Gebruik generisch Niveau 3 van PostScript.
   * **[!UICONTROL ZPL 300 DPI]**: Gebruik ZPL 300 DPI. De zpl300.xdc wordt gebruikt.
   * **[!UICONTROL ZPL 600 DPI]**: Gebruik ZPL 600 DPI. Het zpl600.xdc- dossier wordt gebruikt.
   * **[!UICONTROL Aangepaste IPL]**: Gebruik de optie om een douaneXDC dossier voor IPL te specificeren.
   * **[!UICONTROL IPL 300 DPI]**: Gebruik IPL 300 DPI. De ipl300.xdc wordt gebruikt.
   * **[!UICONTROL IPL 400 DPI]**: Gebruik IPL 400 DPI. Het ipl400.xdc- dossier wordt gebruikt.
   * **[!UICONTROL Aangepaste TPCL]**: Gebruik de optie om een douaneXDC dossier voor TPCL te specificeren.
   * **[!UICONTROL TPCL 305 DPI]**: Gebruik TPCL 300 DPI. Het tpcl305.xdc- dossier wordt gebruikt.
   * **[!UICONTROL PCL 600 DPI]**: Gebruik TPCL 600 DPI. Het tpcl600.xdc- dossier wordt gebruikt.
   * **[!UICONTROL Aangepaste DPL]**: Gebruik de optie om een douaneXDC dossier DPL te specificeren.
   * **[!UICONTROL DPL300DPI]**: Gebruik DPL 300 DPI. Het dpl300.xdc- dossier wordt gebruikt.
   * **[!UICONTROL DPL406DPI]**: Gebruik DPL 400 DPI. De dpl406.xdc wordt gebruikt.
   * **[!UICONTROL DPL600DPI]**: Gebruik DPL 600 DPI. De dpl600.xdc wordt gebruikt.

**Uitvoereigenschappen**

* **[!UICONTROL Uitvoerdocument opslaan met]**: Specificeer de plaats om het outputdossier op te slaan. U kunt het outputdossier bij een plaats bewaren die met betrekking tot de nuttige lading, in een variabele is, of een absolute plaats specificeren om het outputdossier te bewaren. Als de weg niet in crx-bewaarplaats bestaat, kan een beheerder de weg tot stand brengen alvorens het te gebruiken.

**Geavanceerde eigenschappen**

* **[!UICONTROL Selecteer de plaats van de Wortel van de Inhoud gebruikend]**: De wortel van de inhoud is een koordwaarde die URI, absolute verwijzing, of plaats in de bewaarplaats specificeert om relatieve activa terug te winnen die door het vormontwerp worden gebruikt. Bijvoorbeeld, als de verwijzingen van het vormontwerp relatief een beeld, zoals ../myImage.gif, moet myImage.gif in repository:// worden gevestigd. De standaardwaarde is repository://, wat aan het wortelniveau van de bewaarplaats richt.

   Wanneer u activa van uw toepassing plukt, moet de weg van URI van de Wortel van de Inhoud de correcte structuur hebben. Bijvoorbeeld, als een vorm van een toepassing genoemd SampleApp wordt geplukt, en in SampleApp/1.0/forms/Test.xdp wordt geplaatst, moet de Inhoudwortel URI als repository://administrator@password/Applications/SampleApp/1.0/forms/, of bewaarplaats worden gespecificeerd:/Applications/SampleApp/1.0/forms/ (wanneer het gezag ongeldig is). Wanneer de Inhoudspoot URI op deze manier wordt gespecificeerd, zullen de wegen van alle referenced activa in de vorm tegen dit URI worden opgelost.

* **[!UICONTROL Selecteer XCI-bestand met]**: De dossiers XCI worden gebruikt om doopvonten en andere eigenschappen te beschrijven die voor de elementen van het vormontwerp worden gebruikt. U kunt een XCI- dossier met betrekking tot de nuttige lading, bij een absolute weg houden, of het gebruiken van een variabele van het gegevenstype van het Document.

* **[!UICONTROL Lokaal]**: Specificeert de taal die voor het produceren van het Pdf- document wordt gebruikt. Als u een letterlijke waarde verstrekt, selecteer een taal van de lijst of selecteer één van deze waarden:
   * **Om servergebrek**te gebruiken:
(Gebrek) gebruik de Scène die op de Server van Vormen AEM wordt gevormd plaatst. Het plaatsen van de Scène wordt gevormd gebruikend de Console van het Beleid. (Zie [Ontwerper Hulp](http://www.adobe.com/go/learn_aemforms_designer_65).)

   * **Om douanewaarde**te gebruiken:
Typ de code van de Scène in de letterlijke doos of selecteer een koordvariabele die de scènecode bevat. Voor een volledige lijst van gesteunde scènecodes, zie http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Kopieën]**: Een geheelwaarde die het aantal te produceren exemplaren voor de output specificeert. De standaardwaarde is 1.

* **[!UICONTROL Duplex afdrukken]**:  Een waarde van de Paginering die of specificeert om tweezijdig of enig-zijdig druk te gebruiken. De printers die PostScript en PCL steunen gebruiken deze waarde.Als u een letterlijke waarde verstrekt, selecteer één van deze waarden:
   * **[!UICONTROL Duplex Long Edge]**: Gebruik dubbelzijdig afdrukken en afdrukken met een langlopende paginering.
   * **[!UICONTROL Duplex Short Edge]**: Gebruik dubbelzijdig afdrukken en afdrukken met korte paginering.
   * **[!UICONTROL Simplex]**: Gebruik eenzijdig afdrukken.