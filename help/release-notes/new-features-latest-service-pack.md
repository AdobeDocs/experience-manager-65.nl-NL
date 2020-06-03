---
title: Nieuw in Adobe Experience Manager 6.5 Service Pack 5
description: Nieuw in Adobe Experience Manager 6.5 Service Pack 5
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: cc423a199e860429e85895690f6c1a81c20d1a19
workflow-type: tm+mt
source-wordcount: '1845'
ht-degree: 2%

---


# Nieuw in AEM 6.5 Service Pack 5 {#aem-whats-new-service-pack-5}

Met de servicepakketten van Adobe Experience Manager 6.5 beschikt u elk kwartaal over nieuwe functies, door de klant gevraagde verbeteringen, prestaties en aan stabiliteit gerelateerde verbeteringen. Het driemaandelijkse leveringsmodel maakt het gemakkelijker om tot nieuwe eigenschappen en innovaties toegang te hebben en aan te nemen.

Dit artikel benadrukt de eigenschappen inbegrepen in het recentste 6.5 Service Pack, [belangrijkste eigenschappen inbegrepen in de vorige 6.5 Pakken](#key-features-previous-service-packs)van de Dienst, en sommige van de [belangrijkste versies sinds de Versie van de Manager van de Ervaring 6.5.4.0](#key-features-sice-sp3) .

## AEM Sites {#aem-sites}

### Toegankelijkheidsverbeteringen {#accessibility-sites}

* Verbeterde foutrapportage door tekstgegevens toe te voegen

* Verbeterde UI-focus tijdens toetsenbordnavigatie

* Verbeterd tekstcontrast (lichtsterkteverhouding)

* Verbeterde consistentie van alt-kenmerken voor paginaafbeeldingen

* Verbeterde consistentie van Toegankelijke Rich Internet Applications (ARIA) etiketten

* Verbeterde NVDA-mogelijkheden (Non-Visual Desktop Access)

* Verbeterde ondersteuning voor schermlezers

### Andere belangrijke verbeteringen {#other-enhancements-sites}

* Wanneer u een paginastructuur kopieert of plakt, kunt u nu de basispagina plakken of de basispagina plakken met de subpagina&#39;s van de structuur.

* AEM Experience Fragments die naar de werkruimten van het Doel van Adobe worden uitgevoerd verschijnen nu als unieke aanbiedingstypen en bieden bronnen aan in [!DNL Target].

* Beheer van meerdere sites - Met de trigger Publiceren wordt een component verwijderd van de gepubliceerde pagina als een component wordt verwijderd van de bronpagina.

* Beheer van meerdere sites - Wanneer de naam van een lokale component in een LiveCopy identiek is aan de naam van een component in de blauwdruk en de component uit blauwdruk wordt opgerold, wordt nu de term _msm_moving toegevoegd aan de naam van de lokale component.

## AEM Assets {#aem-assets}

### Verbeterde toegankelijkheid in elementen {#assets-accessibility}

[!DNL Adobe Experience Manager] Elementfuncties zijn nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG). De toegankelijkheid is verbeterd op de volgende gebieden:

* Gebruikersinterface-elementen, besturingselementen, pagina&#39;s en dialoogvensters zijn schermlezervriendelijk.

* Gebruikersinterface-elementen, besturingselementen en invoerformuliervelden zijn toegankelijk via het toetsenbord.

* De kleur en het contrast van bepaalde afbeeldingen wijzigen, zodat deze kunnen worden herkend door gebruikers met een beperkt gezichtsvermogen en zonder kleurperceptie. De kleur van sterrenbeoordelingspictogrammen (zoals in de [!UICONTROL Rating] sectie van het [!UICONTROL Advanced] tabblad in het element [!UICONTROL Properties] of in de kaartweergave) wordt bijvoorbeeld gewijzigd voor het juiste contrast.

![kleur van sterrenbeoordelingspictogrammen is gewijzigd om het contrast te verbeteren](assets/star-rating-icons.png)

### Uitgebreide afhandeling van uitzonderingen {#exception-handling}

De stroom van de gebruikersinterface van activa heeft betere uitzonderingsbehandeling. Als een middel niet het juiste type had voor zijn afmetingen, werd een uitzondering waargenomen die ongemerkt en zonder sporen in logboeken werd gevangen. Dit gedrag is veranderd en alle uitzonderingen worden gevangen in logboeken.

## [!DNL Dynamic Media] {#dynamic-media}

### 3D-ondersteuning in [!DNL Dynamic Media] {#support-for-3d}

Met 3D-ondersteuning kunnen klanten [!DNL Dynamic Media] nu 3D-inhoud publiceren en toevoegen aan webpagina&#39;s en toepassingen. Het omvat:

* Publiceren van veelgebruikte 3D-elementen om een element-URL te genereren.

* Interactieve weergave van gepubliceerde 3D-elementen met behulp van een nieuwe 3D-webviewer die beschikbaar is in de [!DNL Dynamic Media] viewerbibliotheek, aangedreven door Adobe Dimension.

* Publiceren en weergeven in 3D op [!DNL Experience Manager Sites] pagina met gebruik van de [!DNL Sites] WCM-component.

## AEM Forms {#aem-forms}

### De kolommen van AEM Inbox aanpassen {#customize-aem-inbox-columns}

U kunt een AEM Inbox aanpassen om de standaardtitel van een kolom te veranderen, de positie van een kolom te herschikken, en extra kolommen te tonen die op de gegevens van een werkschema worden gebaseerd. U bent lid van `administrators` of `workflow-administrators` groep om de kolommen aan te passen.

![Kolommen van AEM Inbox aanpassen](assets/customize-columns.gif)

### Interactieve communicatie opslaan als concept {#save-as-draft}

U kunt de Agent UI gebruiken om één of meerdere concepten voor elke Interactieve Mededeling te bewaren en het ontwerp later terug te winnen om aan het verder te werken. U kunt voor elk concept een andere naam opgeven, zodat u het gemakkelijk kunt herkennen.

![Opslaan als concept](assets/save-as-draft.gif)

### [!DNL Oracle WebLogic] toepassingsserverondersteuning {#weblogic-support}

AEM Forms heeft ondersteuning toegevoegd voor [!DNL Oracle WebLogic 12] AEM Forms on JEE. U kunt een upgrade uitvoeren van een vorige versie of een nieuwe AEM 6.5-formulieren instellen op de JEE-server op [!DNL Oracle WebLogic] 12.2.1.4 en hoger. Later komt dit overeen met de kleine versiewijzigingen, waarbij x in 12.2.1.x wordt vervangen door een versienummer.

### Toegankelijkheidsverbeteringen {#accessibility-improvements}

AEM Forms bevat de volgende toegankelijkheidsverbeteringen:

* Wanneer een gebruiker een adaptief formulier voorvertoont als HTML-formulier, behoudt het [!UICONTROL Scribble Signature] veld de tabfocus.

* De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, bevatten nu het `aria-describedBy` kenmerk. Het kenmerk is gekoppeld aan de velden waarnaar in het foutbericht wordt verwezen. Het `aria-describedby` kenmerk geeft id&#39;s aan van de elementen die het object beschrijven. Het helpt een relatie tot stand te brengen tussen widgets of groepen en tekst die hen beschrijft.

* Als een adaptief formulier een aantal verplichte velden heeft, wordt het verplichte kenmerk voor dergelijke velden in het ARIA-toegankelijkheidsschema ingesteld op `True` dat.

### X-509 op certificaten gebaseerde verificatie voor SOAP-webservices in formuliergegevensmodel {#x509-based-authentication-soap}

Het formuliergegevensmodel ondersteunt nu X-509 op certificaten gebaseerde verificatie terwijl SOAP-webservices als gegevensbron worden gebruikt.

### Andere belangrijke verbeteringen {#other-improvements}

* AEM 6.5 Forms on JEE Document Security is nu gebaseerd op [!DNL Apache Struts 2].

* Extra ondersteuning voor [!DNL Oracle Real Applications Cluster (RAC) 19c].

## Belangrijkste functies in vorige AEM 6.5-servicepacks {#key-features-previous-service-packs}

### AEM Sites {#aem-sites-previous-service-packs}

#### Stijlsysteemverbeteringen (6.5.4.0) {#style-system-enhancements}

U kunt nu stijlen selecteren in het dialoogvenster met het verbeterde stijlsysteem.

#### Prestatieverbeteringen op verschillende gebieden (6.5.4.0) {#performance-improvements}

* Verminderde tijd voor het laden van en het initialiseren van ContextHub binnen een plaats (`contexthub.kernel.js`). Hierdoor worden pagina&#39;s tijdens een bezoek aan de site sneller geladen.

* Verlaagde tijd om een pagina te vernieuwen nadat u Experience Fragments naar de Editor voor sitepagina hebt gesleept.

* De laadtijd voor vermeldingen op een sitepagina met meer dan 200 actieve kopieën is verkort **[!UICONTROL Live Copy Overview]**.

* Verbeterde verwerking van onvolledige of ongeldige URL&#39;s. Dergelijke URL&#39;s kunnen de Sjablooneditor vertragen.

### AEM Assets {#aem-assets-previous-service-packs}

#### Configure AEM Assets with Brand Portal (6.5.4.0) {#configure-assets-bp}

Het machtigingskanaal tussen AEM Assets en Brand Portal is gewijzigd. Eerder, werd het Portaal van het Merk gevormd in Klassieke UI via Verouderde Gateway OAuth, die de het symbolenuitwisseling van JWT gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning. AEM Assets is nu geconfigureerd met Brand Portal via Adobe I/O, dat een IMS token aanschaft voor toestemming van uw Pantaarn voor merken.

De stappen om AEM Middelen met het Portaal van het Merk te vormen zijn verschillend afhankelijk van uw versie AEM, en of u voor het eerst vormt, of de bestaande configuraties bevordert. Zie AEM-middelen [configureren met Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) voor meer informatie.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#accessibility-enhancements}

De middelen van de Manager van de ervaring omvatten de volgende toegankelijkheidsverhogingen:

* Met de pijltoetsen op het toetsenbord kunt u gebieden binnen ingezoomde afbeeldingen verplaatsen en pannen. Zie alleen [voor](../assets/managing-assets-touch-ui.md#previewing-assets)voorvertoningen van toetsenbordtoetsen voor meer informatie.

* De selectievakjes voor gemengde status (waarin de selectievakjes voor het eerste niveau niet zijn geselecteerd en zijn doorgehaald) in het deelvenster Filters zijn leesbaar voor schermlezers, tenzij u alle geneste selectievakjes selecteert.

* Er zijn beperkingen in de datum- en tijdnotatie opgenomen in veldlabels van datumvelden, zodat gebruikers de datum in de juiste notatie kunnen invoeren met het toetsenbord.

   Bijvoorbeeld, `On Time (MM-DD-YYYY HH:mm)`. Hier is MM maand in het formaat van twee cijfers, YYYY is jaar, DD is dag in het formaat van twee cijfers, HH is uur in 24-uurs militair formaat, en mm is minuut.

* Het `X` symbool op de knop om de momenteel geselecteerde tags te verwijderen, wordt nu door schermlezers aangekondigd samen met het aantal geselecteerde tags.

#### Visuele zoekopdracht naar AEM-elementen (6.5.2.0) {#visual-search}

Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Visueel onderzoek](../assets/search-assets.md).

###  Dynamic Media {#dynamic-media-previous-service-packs}

#### Smart Imaging voor dynamische media {#smart-imaging}

Slimme beeldverwerking gebruikt de unieke weergavekenmerken van elke gebruiker om automatisch de juiste afbeeldingen te leveren die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](../assets/imaging-faq.md).

#### Slim uitsnijden in videoprofielen voor dynamische media (6.5.3.0) {#smart-crop-video}

Slim uitsnijden voor video; een optionele functie in videoprofielen. Dit is een programma dat de kracht van kunstmatige intelligentie in Adobe Sensei gebruikt om automatisch het brandpunt te detecteren en uit te snijden in adaptieve video of progressieve video die u hebt geüpload, ongeacht de grootte. Zie [Informatie over slim uitsnijden in videoprofielen](../assets/video-profiles.md).

### AEM Forms {#aem-forms-previous-service-packs}

#### Afdrukbare uitvoer genereren in AEM Forms-workflows (6.5.4.0) {#generate-printable-output}

Met de workflowstap Afdrukbare uitvoer genereren kunt u een bronsjabloonbestand integreren met een gegevensbestand. Dankzij deze integratie kunt u verschillende exemplaren van het sjabloonbestand afdrukken of opslaan. De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer. Voor meer informatie over deze eigenschap, zie [Forms-centric werkschema op OSGi - de Verwijzing](../forms/using/aem-forms-workflow-step-reference.md)van de Stap.

![Afdrukbare uitvoer genereren](assets/generate-print-output-step.gif)

#### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de modus Lay-out (6.5.4.0) {#multi-column-adaptive-forms}

U kunt nu het aantal kolommen voor een deelvenster definiëren in adaptieve formulieren en interactieve communicatie. Schakel over naar de lay-outmodus om de nieuwe optie voor meerdere kolommen te gebruiken. Zie De modus Lay-out [gebruiken om het formaat van componenten](../forms/using/resize-using-layout-mode.md)te wijzigen voor meer informatie.

![Lay-out met meerdere kolommen](assets/multi-column-layout.gif)

#### AEM Inbox-aanpassingen (6.5.4.0) {#aem-inbox}

Met de nieuwe optie Beheer beheren kunnen beheerders:

* Koptekst en logo aanpassen

* De weergave van navigatiekoppelingen in de koptekst bepalen

De optie Beheer is alleen zichtbaar voor de leden van de groep met beheerders of workflowbeheerders. Zie [Uw Postvak IN](../sites-authoring/inbox.md)voor meer informatie over deze functie.

#### RTF-ondersteuning in HTML5-formulieren (6.5.4.0) {#rich-text-support}

Zet een tekstveld in een XFA-formulier om in een RTF-formulier. Zie Formuliersjablonen [ontwerpen voor HTML5-formulieren](../forms/using/designing-form-template.md)voor meer informatie.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#forms-accessibility-enhancements-6540}

Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Schermlezers kondigen selectievakjes, koppelingen, Datumkiezer en Datuminvoer correct aan in een adaptief formulier.

* Elke pagina van een adaptief formulier bevat nu één titel en één hoofdlabel met een liggend streepje.

#### Delen en toegang aanvragen tot InBox-items van een gebruiker van AEM Forms (6.5.3.0) {#share-request-access}

U kunt uw Inbox punten met een andere gebruiker delen. Zodra een andere gebruiker toegang krijgt tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken. Zie [Delen en verzoek om toegang tot Inbox-items van een gebruiker](../forms/using/configure-shared-queues-osgi.md).

#### De buiten-van-bureaumontages voor Inbox punten van een gebruiker van Vormen AEM (6.5.3.0) vormen {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als uw instellingen buiten het kantoor zijn. U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. Zie [Vorm uit de montages](../forms/using/configure-out-of-office-settings.md)van het Bureau.

#### Meerdere interactieve communicatie genereren met de batch-API voor AEM-formulieren (6.5.3.0) {#generate-multiple-ic}

U kunt de batch-API gebruiken om meerdere interactieve communicatie van een sjabloon te maken. De sjabloon is een interactieve communicatie zonder gegevens. De batch-API combineert gegevens met een sjabloon voor interactieve communicatie. De API is nuttig bij de massaproductie van interactieve communicatie. Bijvoorbeeld telefoonrekeningen, creditcardoverzichten voor meerdere klanten. Zie Meerdere interactieve communicatie [genereren met de Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

## Belangrijke releases sinds AEM 6.5 SP4 {#key-releases-since-last-sp}

Tussen 05 maart 2020 en 4 juni 2020 heeft Adobe de volgende functies uitgebracht die buiten de kernlevering van AEM vallen:

* AEM Cloud Manager [2020.3.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-3-0.html), [2020.4.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-4-0.html)en [2020.5.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html)

* [AEM-elementen: Desktop App 2.0.2.0](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)

* [AEM-schermen: Feature Pack 202004](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202004.html)

## Nuttige bronnen

* [Handleidingen voor AEM 6.5-gebruikers](../user-guide/home.md)

* [Algemene opmerkingen bij de release van Adobe Experience Manager 6.5](release-notes.md)

* [Opmerkingen bij de release van Service Pack voor Adobe Experience Manager 6.5](sp-release-notes.md)
