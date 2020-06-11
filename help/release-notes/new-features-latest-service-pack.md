---
title: Nieuw in Adobe Experience Manager 6.5 Service Pack 5
description: Nieuw in Adobe Experience Manager 6.5 Service Pack 5
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b2b8178f96d1e0a551a58ba649443aa03f0608ac
workflow-type: tm+mt
source-wordcount: '1839'
ht-degree: 0%

---


# Nieuw in Adobe Experience Manager 6.5 Service Pack 5 {#aem-whats-new-service-pack-5}

De de dienstpakken van de Manager 6.5 van de Ervaring van Adobe verstrekken nieuwe eigenschappen, klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen met kwartaalintervallen. De beschikbaarheid op kwartaalbasis maakt het gemakkelijk om tot nieuwe eigenschappen en innovaties toegang te hebben en te nemen.

Dit artikel benadrukt de eigenschappen inbegrepen in het recentste 6.5 Service Pack, [belangrijkste eigenschappen inbegrepen in de vorige 6.5 Pakken](#key-features-previous-service-packs)van de Dienst, en sommige van de [belangrijkste versies sinds de Versie van de Manager van de Ervaring 6.5.4.0](#key-releases-since-last-sp) .

## Sites van Adobe Experience Manager {#aem-sites}

### Toegankelijkheidsverbeteringen {#accessibility-sites}

* Verbeterde foutrapportage door tekstgegevens toe te voegen.

* Verbeterde focus van de gebruikersinterface tijdens toetsenbordnavigatie.

* Verbeterde contrastverhouding voor verschillende gebruikersinterface-elementen.

* Verbeterde consistentie van alt-kenmerken voor paginaafbeeldingen.

* Verbeterde consistentie van Toegankelijke Rich Internet Applications (ARIA) etiketten.

* Verbeterde NVDA-mogelijkheden (Non-Visual Desktop Access).

* Verbeterde ondersteuning voor schermlezers.

### Andere belangrijke verbeteringen {#other-enhancements-sites}

* Wanneer u een paginastructuur kopieert of plakt, kunt u nu de basispagina plakken of de basispagina plakken met de subpagina&#39;s van de structuur.

* [!DNL Adobe Experience Manager Experience Fragments] geëxporteerd naar [!DNL Adobe Target] werkruimten worden nu weergegeven als unieke aanbiedingstypen en bieden bronnen aan in [!DNL Target].

* Beheer van meerdere sites - De trigger Publiceren verwijdert nu een component van de gepubliceerde pagina als een component van de bronpagina wordt verwijderd.

* Beheer van meerdere sites - Wanneer de naam van een lokale component in een afbeelding identiek [!UICONTROL Live Copy] is aan de naam van een component in de blauwdruk en de component uit de blauwdruk wordt opgerold, `_msm_moved` wordt de term nu toegevoegd aan de naam van de lokale component.

## [!DNL Adobe Experience Manager Assets] {#aem-assets}

### Verbeterde toegankelijkheid in [!DNL Assets] {#assets-accessibility}

[!DNL Experience Manager Assets] is nu toegankelijker in overeenstemming met de Web Content Accessibility Guidelines (WCAG). De toegankelijkheid is verbeterd dankzij de volgende verbeteringen:

* Veel gebruikersinterface-elementen, besturingselementen, pagina&#39;s en dialoogvensters zijn schermlezervriendelijk.

* Veel elementen, besturingselementen en invoerformuliervelden van de gebruikersinterface zijn toegankelijk via het toetsenbord.

* De kleur- en contrastverhouding van bepaalde elementen van de gebruikersinterface worden bijgewerkt, zodat gebruikers met een beperkt gezichtsvermogen of gebruikers zonder kleurperceptie deze elementen van de gebruikersinterface kunnen onderscheiden. De kleur van sterrenbeoordelingspictogrammen (zoals in de [!UICONTROL Rating] sectie van het [!UICONTROL Advanced] tabblad in het element [!UICONTROL Properties] of in de kaartweergave) wordt bijvoorbeeld gewijzigd voor het juiste contrast.

   ![Classificatiepictogrammen met verbeterde contrastverhouding](assets/star-rating-icons.png)

### Uitgebreide uitzonderingsverwerking {#exception-handling}

[!DNL Assets] de stroom van de gebruikersinterface heeft betere uitzonderingsbehandeling. Als een element geen type heeft voor de dimensie, wordt de waargenomen uitzondering opgenomen in de logbestanden.

### Ondersteuning voor 3D-elementen in [!DNL Dynamic Media] {#support-for-3d}

Met ondersteuning voor 3D-afbeeldingen in [!DNL Dynamic Media] kunnen klanten 3D-inhoud publiceren en toevoegen aan webpagina&#39;s en toepassingen. De steun omvat:

* Publiceer algemene indelingen voor 3D-elementen en genereren een middel-URL die kan worden gebruikt in webpagina&#39;s en andere toepassingen.

* Een 3D-webviewer, ingeschakeld door [!DNL Adobe Dimension], om de gepubliceerde 3D-elementen interactief weer te geven.

* Publiceer en bekijk gemeenschappelijke 3D activa op [!DNL Experience Manager Sites] pagina&#39;s gebruikend de component [!DNL Sites] WCM.

## Adobe Experience Manager Forms {#aem-forms}

### De kolommen in het Postvak In van Adobe Experience Manager aanpassen {#customize-aem-inbox-columns}

U kunt een [!DNL Experience Manager] Postvak IN aanpassen om de standaardtitel van een kolom te wijzigen, de positie van een kolom opnieuw te ordenen en extra kolommen weer te geven op basis van de gegevens van een workflow. Leden van `administrators` of `workflow-administrators` groep kunnen de kolommen aanpassen.

![Inbox-kolommen van Experience Manager aanpassen](assets/customize-columns.gif)

### Interactieve communicatie opslaan als concept {#save-as-draft}

U kunt de Agent UI gebruiken om één of meerdere concepten voor elke Interactieve Mededeling te bewaren en het ontwerp later terug te winnen om aan het verder te werken. U kunt voor elk concept een andere naam opgeven om het te identificeren.

![Opslaan als concept](assets/save-as-draft.gif)

### [!DNL Oracle WebLogic] toepassingsserverondersteuning {#weblogic-support}

Adobe Experience Manager Forms heeft extra ondersteuning toegevoegd voor [!DNL Oracle WebLogic 12] Adobe Experience Manager Forms on JEE. U kunt een upgrade uitvoeren van een vorige versie of een nieuwe Experience Manager 6.5 Forms instellen op JEE-server op [!DNL Oracle WebLogic] 12.2.1.4 en hoger. Later komt dit overeen met de kleine versiewijzigingen, waarbij x in 12.2.1.x wordt vervangen door een versienummer.

### Toegankelijkheidsverbeteringen {#accessibility-improvements}

Adobe Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Wanneer een gebruiker een adaptief formulier voorvertoont als HTML-formulier, behoudt het [!UICONTROL Scribble Signature] veld de tabfocus.

* De foutberichten die worden weergegeven bij het verzenden van een adaptief formulier, bevatten nu het `aria-describedBy` kenmerk. Het kenmerk is gekoppeld aan de velden waarnaar in het foutbericht wordt verwezen. Het `aria-describedby` kenmerk geeft id&#39;s aan van de elementen die het object beschrijven. Het helpt een relatie tot stand te brengen tussen widgets of groepen en tekst die hen beschrijft.

* Als een adaptief formulier een aantal verplichte velden heeft, wordt het verplichte kenmerk voor dergelijke velden in het ARIA-toegankelijkheidsschema ingesteld op `True` dat.

### X-509 op certificaten gebaseerde verificatie voor SOAP-webservices in formuliergegevensmodel {#x509-based-authentication-soap}

Het formuliergegevensmodel ondersteunt nu X-509 op certificaten gebaseerde verificatie terwijl SOAP-webservices als gegevensbron worden gebruikt.

### Andere belangrijke verbeteringen {#other-improvements}

* Experience Manager 6.5 Forms on JEE Document Security is nu gebaseerd op [!DNL Apache Struts 2].

* Extra ondersteuning voor [!DNL Oracle Real Applications Cluster (RAC) 19c].

## Belangrijkste functies in vorige Experience Manager 6.5-servicepacks {#key-features-previous-service-packs}

### Sites van Experience Manager {#aem-sites-previous-service-packs}

#### Stijlsysteemverbeteringen (6.5.4.0) {#style-system-enhancements}

U kunt nu stijlen selecteren in het dialoogvenster met het verbeterde stijlsysteem.

#### Prestatieverbeteringen op verschillende gebieden (6.5.4.0) {#performance-improvements}

* Verminderde tijd om ContextHub binnen een plaats (`contexthub.kernel.js`) te laden en te initialiseren. Hierdoor worden pagina&#39;s tijdens een bezoek aan de site sneller geladen.

* Verlaagde tijd om een pagina te vernieuwen nadat u deze naar de [!DNL Experience Fragments] [!DNL Sites] Pagina-editor hebt gesleept.

* De laadtijd voor vermeldingen op een [!DNL Sites] pagina met meer dan 200 actieve kopieën is verkort **[!UICONTROL Live Copy Overview]**.

* Verbeterde verwerking van onvolledige of ongeldige URL&#39;s. Dergelijke URL&#39;s kunnen de Sjablooneditor vertragen.

### [!DNL Adobe Experience Manager Assets] {#aem-assets-previous-service-packs}

#### Configureren [!DNL Experience Manager Assets] met [!DNL Brand Portal] (6.5.4.0) {#configure-assets-bp}

Het machtigingskanaal tussen [!DNL Experience Manager Assets] en [!DNL Brand Portal] is gewijzigd. Eerder, [!DNL Brand Portal] werd gevormd in Klassieke UI via Verouderde Gateway OAuth, die de het symbolenuitwisseling van JWT gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning. [!DNL Experience Manager Assets] wordt nu geconfigureerd met [!DNL Brand Portal] behulp van Adobe I/O, dat een IMS-token aanschaft voor toestemming van uw [!DNL Brand Portal] huurder.

De stappen om [!DNL Experience Manager Assets] met [!DNL Brand Portal] te vormen zijn verschillend afhankelijk van uw [!DNL Experience Manager] versie, en of u voor het eerst vormt, of de bestaande configuraties bevordert. Zie [De Middelen van de Manager van de Ervaring met het Portaal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) van het Merk voor details vormen.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#accessibility-enhancements}

[!DNL Experience Manager Assets] bevat de volgende toegankelijkheidsverbeteringen:

* Met de pijltoetsen op het toetsenbord kunt u gebieden binnen ingezoomde afbeeldingen verplaatsen en pannen. Zie alleen [voor](../assets/managing-assets-touch-ui.md#previewing-assets)voorvertoningen van toetsenbordtoetsen voor meer informatie.

* De selectievakjes voor gemengde status (waarin de selectievakjes voor het eerste niveau niet zijn geselecteerd en zijn doorgehaald) in het deelvenster Filters zijn leesbaar voor schermlezers, tenzij u alle geneste selectievakjes selecteert.

* Er zijn beperkingen in de datum- en tijdnotatie opgenomen in veldlabels van datumvelden, zodat gebruikers de datum in de juiste notatie kunnen invoeren met het toetsenbord. Bijvoorbeeld, `On Time (MM-DD-YYYY HH:mm)`. Hier is MM maand in het formaat van twee cijfers, YYYY is jaar, DD is dag in het formaat van twee cijfers, HH is uur in 24-uurs militair formaat, en mm is minuut.

* Schermlezers kondigen het `X` symbool aan om de geselecteerde tags en het aantal geselecteerde tags te verwijderen.

#### Visueel zoeken naar [!DNL Adobe Experience Manager Assets] (6.5.2.0) {#visual-search}

[!DNL Assets] gebruikers kunnen visueel vergelijkbare afbeeldingen zoeken. De manager van de ervaring toont slimme geëtiketteerde beelden van de bewaarplaats DAM die aan een gebruiker-geselecteerd beeld gelijkaardig zijn. Zie [Visueel onderzoek](../assets/search-assets.md).

###  Dynamic Media {#dynamic-media-previous-service-packs}

#### Smart Imaging voor dynamische media {#smart-imaging}

Slimme beeldverwerking gebruikt de unieke weergavekenmerken van elke gebruiker om automatisch de juiste afbeeldingen te leveren die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](../assets/imaging-faq.md).

#### Slim uitsnijden in videoprofielen voor dynamische media (6.5.3.0) {#smart-crop-video}

Slim uitsnijden voor video; een optionele functie in videoprofielen. Dit is een programma dat de kracht van kunstmatige intelligentie in Adobe Sensei gebruikt om automatisch het brandpunt te detecteren en uit te snijden in adaptieve video of progressieve video die u hebt geüpload, ongeacht de grootte. Zie [Informatie over slim uitsnijden in videoprofielen](../assets/video-profiles.md).

### Experience Manager Forms {#aem-forms-previous-service-packs}

#### Afdrukbare uitvoer genereren in workflows van Experience Manager Forms (6.5.4.0) {#generate-printable-output}

Met de workflowstap Afdrukbare uitvoer genereren kunt u een bronsjabloonbestand integreren met een gegevensbestand. Dankzij deze integratie kunt u verschillende exemplaren van het sjabloonbestand afdrukken of opslaan. De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer. Voor meer informatie over deze eigenschap, zie [Forms-centric werkschema op OSGi - de Verwijzing](../forms/using/aem-forms-workflow-step-reference.md)van de Stap.

![Afdrukbare uitvoer genereren](assets/generate-print-output-step.gif)

#### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de modus Lay-out (6.5.4.0) {#multi-column-adaptive-forms}

U kunt nu het aantal kolommen voor een deelvenster definiëren in adaptieve formulieren en interactieve communicatie. Schakel over naar de lay-outmodus om de nieuwe optie voor meerdere kolommen te gebruiken. Zie De modus Lay-out [gebruiken om het formaat van componenten](../forms/using/resize-using-layout-mode.md)te wijzigen voor meer informatie.

![Lay-out met meerdere kolommen](assets/multi-column-layout.gif)

#### Inbox-aanpassingen van Experience Manager (6.5.4.0) {#aem-inbox}

Met de nieuwe optie Beheer beheren kunnen beheerders:

* De koptekst en het logo aanpassen.

* Hiermee bepaalt u de weergave van navigatiekoppelingen die beschikbaar zijn in de koptekst.

De optie Beheer is alleen zichtbaar voor de leden van de groep `administrators` `workflow-administrators` of groep. Zie [Uw Postvak IN](../sites-authoring/inbox.md)voor meer informatie over deze functie.

#### RTF-ondersteuning in HTML5-formulieren (6.5.4.0) {#rich-text-support}

Zet een tekstveld in een XFA-formulier om in een RTF-formulier. Zie Formuliersjablonen [ontwerpen voor HTML5-formulieren](../forms/using/designing-form-template.md)voor meer informatie.

#### Toegankelijkheidsverbeteringen (6.5.4.0) {#forms-accessibility-enhancements-6540}

Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Schermlezers kondigen selectievakjes, koppelingen, Datumkiezer en Datuminvoer correct aan in een adaptief formulier.

* Elke pagina van een adaptief formulier bevat nu één titel en één hoofdlabel met een liggend streepje.

#### Deel en verzoek om toegang tot Inbox-items van een gebruiker van Experience Manager Forms (6.5.3.0) {#share-request-access}

U kunt uw Inbox punten met een andere gebruiker delen. Zodra een andere gebruiker toegang krijgt tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken. Zie [Delen en verzoek om toegang tot Inbox-items van een gebruiker](../forms/using/configure-shared-queues-osgi.md).

#### De buiten-van-bureaumontages voor Inbox punten van een gebruiker van Vormen AEM (6.5.3.0) vormen {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als uw instellingen buiten het kantoor zijn. U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. Zie [Vorm uit de montages](../forms/using/configure-out-of-office-settings.md)van het Bureau.

#### Meerdere interactieve communicatie genereren met de batch-API voor AEM-formulieren (6.5.3.0) {#generate-multiple-ic}

U kunt de batch-API gebruiken om meerdere interactieve communicatie van een sjabloon te maken. De sjabloon is een interactieve communicatie zonder gegevens. De batch-API combineert gegevens met een sjabloon voor interactieve communicatie. De API is nuttig bij de massaproductie van interactieve communicatie. Bijvoorbeeld telefoonrekeningen, creditcardoverzichten voor meerdere klanten. Zie Meerdere interactieve communicatie [genereren met de Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

## Belangrijke releases sinds Adobe Experience Manager 6.5 SP4 {#key-releases-since-last-sp}

Tussen 5 maart 2005, 2020 en 4 juni 2020 heeft Adobe het volgende uitgebracht, in aanvulling op de servicepacks en cumulatieve fixepakketten:

* [Het portaal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) van de Distributie van de software is beschikbaar om de dienstpakken van de Manager van de Ervaring, cumulatieve fixepakketten, hete moeilijke situaties, en eigenschapspakken te downloaden.

* [!DNL Adobe Experience Manager Cloud Manager] [2020.3.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-3-0.html), [2020.4.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-4-0.html)en [2020.5.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html).

* [Experience Manager desktop app 2.0.2.0](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html).

* [Schermen van Experience Manager: Feature Pack 202004](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202004.html).

>[!MORELIKETHIS]
>
>* [Adobe Experience Manager 6.5-documentatie](../user-guide/home.md)
>* [Algemene opmerkingen bij de release van Adobe Experience Manager 6.5](release-notes.md)
>* [Opmerkingen bij de release van het servicepack voor Adobe Experience Manager 6.5](sp-release-notes.md)

