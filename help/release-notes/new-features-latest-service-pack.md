---
title: Nieuw in Adobe Experience Manager 6.5 Service Pack 4
description: Nieuw in Adobe Experience Manager 6.5 Service Pack 4
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 61d1531c020b5a25207b5e3f1c2b0c14e2974e02

---


# Nieuw in Adobe Experience Manager 6.5 Service Pack 4 {#aem-whats-new-service-pack-4}

Adobe Experience Manager (AEM) 6.5 biedt functies en voortdurende verbeteringen via driemaandelijkse servicepacks. De aanpak is gunstig voor u omdat de innovaties eenvoudiger te gebruiken zijn.

AEM Service Pack 4 (6.5.4.0) wordt vrijgegeven op 5 **maart 2020**. In dit artikel worden de belangrijkste functies van de 6.5 Service Packs beschreven die u helpen uw AEM-reis verrijker te maken.

## AEM Sites {#aem-sites}

### Stijlsysteemverbeteringen

U kunt nu stijlen selecteren in het dialoogvenster met het verbeterde stijlsysteem.

### Prestatieverbeteringen op verschillende gebieden {#performance-improvements}

* Verminderde tijd voor het laden van en het initialiseren van ContextHub binnen een plaats (`contexthub.kernel.js`). Hierdoor worden pagina&#39;s tijdens een bezoek aan de site sneller geladen.

* Verlaagde tijd om een pagina te vernieuwen nadat u Experience Fragments naar de Editor voor sitepagina hebt gesleept.

* De laadtijd voor items op een sitepagina met meer dan 200 actieve kopieën in **[!UICONTROL Live Copy-overzicht]** verkort.

* Verbeterde verwerking van onvolledige of ongeldige URL&#39;s. Dergelijke URL&#39;s kunnen de Sjablooneditor vertragen.

## AEM Assets {#aem-assets}

### AEM-middelen configureren met Brand Portal {#configure-assets-bp}

Het machtigingskanaal tussen AEM Assets en Brand Portal is gewijzigd. Eerder, werd het Portaal van het Merk gevormd in Klassieke UI via Verouderde Gateway OAuth, die de het symbolenuitwisseling van JWT gebruikt om een token van de Toegang te verkrijgen IMS voor vergunning. AEM Assets is nu geconfigureerd met Brand Portal via Adobe I/O, dat een IMS token aanschaft voor toestemming van uw Pantaarn voor merken.

De stappen om AEM Middelen met het Portaal van het Merk te vormen zijn verschillend afhankelijk van uw versie AEM, en of u voor het eerst vormt, of de bestaande configuraties bevordert. Zie AEM-middelen [configureren met Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) voor meer informatie.


### Verbeteringen voor toegankelijkheid {#accessibility-enhancements}

De middelen van de Manager van de ervaring omvatten de volgende toegankelijkheidsverhogingen:

* Met de pijltoetsen op het toetsenbord kunt u gebieden binnen ingezoomde afbeeldingen verplaatsen en pannen. Zie alleen [voor](../assets/managing-assets-touch-ui.md#previewing-assets)voorvertoningen van toetsenbordtoetsen voor meer informatie.

* De selectievakjes voor gemengde status (waarin de selectievakjes voor het eerste niveau niet zijn geselecteerd en zijn doorgehaald) in het deelvenster Filters zijn leesbaar voor schermlezers, tenzij u alle geneste selectievakjes selecteert.

* Er zijn beperkingen in de datum- en tijdnotatie opgenomen in veldlabels van datumvelden, zodat gebruikers de datum in de juiste notatie kunnen invoeren met het toetsenbord.

   Bijvoorbeeld, `On Time (MM-DD-YYYY HH:mm)`. Hier is MM maand in het formaat van twee cijfers, YYYY is jaar, DD is dag in het formaat van twee cijfers, HH is uur in 24-uurs militair formaat, en mm is minuut.

* Het `X` symbool op de knop om de momenteel geselecteerde tags te verwijderen, wordt nu door schermlezers aangekondigd samen met het aantal geselecteerde tags.

## AEM Forms {#aem-forms}

### Afdrukbare uitvoer genereren in AEM Forms-workflows {#generate-printable-output}

Met de workflowstap Afdrukbare uitvoer genereren kunt u een bronsjabloonbestand integreren met een gegevensbestand. Dankzij deze integratie kunt u verschillende exemplaren van het sjabloonbestand afdrukken of opslaan. De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer. Voor meer informatie over deze eigenschap, zie [Forms-centric werkschema op OSGi - de Verwijzing](../forms/using/aem-forms-workflow-step-reference.md)van de Stap.

![Afdrukbare uitvoer genereren](assets/generate-print-output-step.gif)

### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de modus Indeling {#multi-column-adaptive-forms}

U kunt nu het aantal kolommen voor een deelvenster definiëren in adaptieve formulieren en interactieve communicatie. Schakel over naar de lay-outmodus om de nieuwe optie voor meerdere kolommen te gebruiken. Zie De modus Lay-out [gebruiken om het formaat van componenten](../forms/using/resize-using-layout-mode.md)te wijzigen voor meer informatie.

![Lay-out met meerdere kolommen](assets/multi-column-layout.gif)

### AEM Inbox-aanpassingen {#aem-inbox}

Met de nieuwe optie Beheer beheren kunnen beheerders:

* Koptekst en logo aanpassen

* De weergave van navigatiekoppelingen in de koptekst bepalen

De optie Beheer is alleen zichtbaar voor de leden van de groep met beheerders of workflowbeheerders. Zie [Uw Postvak IN](../sites-authoring/inbox.md)voor meer informatie over deze functie.

### RTF-ondersteuning in HTML5-formulieren {#rich-text-support}

Zet een tekstveld in een XFA-formulier om in een RTF-formulier. Zie Formuliersjablonen [ontwerpen voor HTML5-formulieren](../forms/using/designing-form-template.md)voor meer informatie.

### Verbeteringen voor toegankelijkheid {#forms-accessibility-enhancements-6540}

Experience Manager Forms bevat de volgende toegankelijkheidsverbeteringen:

* Schermlezers kondigen selectievakjes, koppelingen, Datumkiezer en Datuminvoer correct aan in een adaptief formulier.

* Elke pagina van een adaptief formulier bevat nu één titel en één hoofdlabel met een liggend streepje.

## Belangrijkste functies in vorige AEM 6.5-servicepacks

### Smart Imaging voor dynamische media (6.5.3.0) {#smart-imaging}

Slimme beeldverwerking gebruikt de unieke weergavekenmerken van elke gebruiker om automatisch de juiste afbeeldingen te leveren die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](../assets/imaging-faq.md).

### Visuele zoekopdracht naar AEM-elementen (6.5.2.0) {#visual-search}

Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Visueel onderzoek](../assets/search-assets.md).

### Delen en toegang aanvragen tot InBox-items van een gebruiker van AEM Forms (6.5.3.0) {#share-request-access}

U kunt uw Inbox punten met een andere gebruiker delen. Zodra een andere gebruiker toegang krijgt tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken. Zie [Delen en verzoek om toegang tot Inbox-items van een gebruiker](../forms/using/configure-shared-queues-osgi.md).

### De buiten-van-bureaumontages voor Inbox punten van een gebruiker van Vormen AEM (6.5.3.0) vormen {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als uw instellingen buiten het kantoor zijn. U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. Zie [Vorm uit de montages](../forms/using/configure-out-of-office-settings.md)van het Bureau.

### Meerdere interactieve communicatie genereren met de batch-API voor AEM-formulieren (6.5.3.0) {#generate-multiple-ic}

U kunt de batch-API gebruiken om meerdere interactieve communicatie van een sjabloon te maken. De sjabloon is een interactieve communicatie zonder gegevens. De batch-API combineert gegevens met een sjabloon voor interactieve communicatie. De API is nuttig bij de massaproductie van interactieve communicatie. Bijvoorbeeld telefoonrekeningen, creditcardoverzichten voor meerdere klanten. Zie Meerdere interactieve communicatie [genereren met de Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

## Belangrijke releases sinds AEM 6.5 SP3

Tussen 12 december 2019 en 5 maart 2020 heeft Adobe de volgende functies uitgebracht die buiten de kernlevering van AEM vallen:

* AEM Cloud Manager 2020.1.0 en 2020.2.0

   Verbeter de pijpleidingsstatus en de capaciteit om logboeken voor diverse stappen te downloaden. Zie:

   * [Cloud Manager 2020.1.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-1-0.html)


   * [Cloud Manager 2020.2.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-2-0.html)


* AEM Cloud Manager CLI-updates

   Taken in Cloud Manager automatiseren met behulp van het opdrachtregelprogramma. Zie [GitHub](https://github.com/adobe/aio-cli-plugin-cloudmanager/releases).

* AEM-sites: Projectarchetype 23

   De beste manier om een nieuw AEM-project te starten. Archetype 23 voegt het Archetype van het [Project voor SPA en regelmatige plaatsen in één](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-23) samen en verstrekt een standaardthema om uw front-end ontwikkeling te starten.

* AEM-sites: WKND-referentiesite

   [Het nieuwe verwijzingsproject](https://www.wknd.site/) verpakt met beste praktijken op hoe te om plaatsen met AEM te bouwen. Lees voor meer informatie de bijgewerkte [WKND-zelfstudie](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html). U kunt de recentste code van [GitHub](https://github.com/adobe/aem-guides-wknd/releases)nemen.

* AEM-sites: Commerce CIF Core Components 0.7.0 en 0.9.0

   AEM-sites integreren met Magento Commerce. Zie het [uitbreiden van de specifieke Componenten van de Kern en Archetype van het Project met nadruk op Handel](https://github.com/adobe/aem-core-cif-components/releases).

* AEM-elementen: Desktop App 2.0.1.1

   Zie [Toegang tot de middelen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)verkrijgen op het bureaublad.

* AEM-schermen: Feature Pack 202001

   Digitale handtekening rechtstreeks vanuit AEM. Installeer de verbeteringen met het nieuwste elementenpakket om het synchroon afspelen op meerdere mediaspelers [](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202001.html)mogelijk te maken.

## Nuttige bronnen

* [Handleidingen voor AEM 6.5-gebruikers](../user-guide/home.md)

* [Algemene opmerkingen bij de release van Adobe Experience Manager 6.5](release-notes.md)

* [Opmerkingen bij de release van Service Pack voor Adobe Experience Manager 6.5](sp-release-notes.md)
