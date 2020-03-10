---
title: Nieuw in Adobe Experience Manager 6.5 Service Pack 4
description: Nieuw in Adobe Experience Manager 6.5 Service Pack 4
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: c9e8e1f2ebb72efc2f54c13c3ddae525ec55349f

---


# Nieuw in Adobe Experience Manager 6.5 Service Pack 4 {#aem-whats-new-service-pack-4}

Adobe Experience Manager (AEM) 6.5 biedt functies en voortdurende verbeteringen via de driemaandelijkse servicepacks dit jaar. De nieuwe aanpak komt onze klanten ten goede wanneer ze de innovaties sneller kunnen toepassen.

Het nieuwste AEM Service Pack 4 (6.5.4.0) wordt uitgebracht op 5 **maart 2020**. In dit artikel worden de functies gemarkeerd die het nieuwste Service Pack biedt om uw AEM-reis verrijkend te maken.

## AEM Sites {#aem-sites}

### Prestatieverbeteringen op verschillende gebieden {#performance-improvements}

* Minder tijd voor het laden en initialiseren van ContextHub binnen een plaats (contexthub.kernel.js). Hierdoor wordt een pagina tijdens een bezoek aan de site sneller geladen.

* Verlaagde tijd om een pagina te vernieuwen nadat u ervaringsfragmenten hebt gesleept en neergezet in het canvas van een pagina-editor.

* De tijd voor het laden van items voor een sitepagina met meer dan 200 actieve kopieën in het overzicht van Actieve kopie verkort.

* Verbeterde verwerking van onvolledige of ongeldige URL&#39;s die ertoe kunnen leiden dat de Sjablooneditor langzamer wordt in de Sjablooneditor.

Bovendien bevat AEM 6.5 Service Pack 4 verbeteringen voor stijlsystemen. U kunt nu ook stijlen selecteren in een deeldialoogvenster.

## AEM Assets {#aem-assets}

### Integratie met Brand Portal via Adobe I/O-console {#assets-integration-bp}

U kunt AEM-middelen nu configureren met Brand Portal via Adobe I/O-console. De Adobe I/O-console verkrijgt een IMS-token voor toestemming van de Poorthuurder van het merk. Eerder, werd AEM Middelen gevormd met het Portaal van het Merk in Klassieke UI via de Verouderde Gateway OAuth. De configuraties die gebruikmaken van de Legacy OAuth Gateway worden ondersteund tot 6 april 2020. Als u de integratie niet wijzigt, blijven de bestaande configuraties werken.

U kunt een nieuwe integratie maken of uw integratie-instellingen upgraden naar Adobe I/O-console.

### Verbeteringen voor toegankelijkheid {#accessibility-enhancements}

* Selectievakjes met gemengde status hebben nu een kenmerk met aria-controle en een waarde &quot;gemengd&quot;, zodat de gemengde status van deze selectievakjes voor schermlezers beschikbaar is.

* Besturingselementen op basis van toetsenborden worden nu ondersteund, met uitzondering van bewegingen op basis van paden, om te navigeren rond ingezoomde afbeeldingen.

* Datumnotatiebeperkingen zijn opgegeven in veldlabels voor gebruikers met alleen het toetsenbord om handmatig datum in te voeren.

* Het kenmerk Alt is toegevoegd aan decoratieve pictogrammen en het kenmerk role=img is verwijderd, zodat dergelijke pictogrammen en afbeeldingen niet beschikbaar worden gemaakt voor schermlezers.

* Het Alt-kenmerk is toegevoegd aan sluitpictogrammen om aan te geven dat de gebruiker van een schermlezer met de Tab-toets omgaat.

## AEM Forms {#aem-forms}

### Afdrukbare uitvoer genereren in AEM Forms-workflows {#generate-printable-output}

Als u een oplossing wilt om veelvoudige exemplaren van een bronmalplaatjedossier te drukken of te bewaren en het met een gegevensdossier met talrijke verslagen te integreren, is een nieuwe Generate Afdrukbare de werkschemastap van de Output beschikbaar in Vormen AEM. Als u bijvoorbeeld een bronformulier met een andere naam wilt afdrukken telkens wanneer het wordt afgedrukt, kunt u deze namen in het gegevensbestand opnemen en het formulier integreren met een standaardsjabloonbestand.

Profiteer van deze functie met **Gereedschappen** > **[!UICONTROL Workflow]** > **[!UICONTROL Modellen]** > **[!UICONTROL Maken]** en zoek vervolgens naar de stap Afdrukbare uitvoer **** genereren.

![Afdrukbare uitvoer genereren](assets/generate-print-output-demo.gif)

Voor meer informatie over deze eigenschap, zie [Forms-centric werkschema op OSGi - de Verwijzing](../forms/using/aem-forms-workflow-step-reference.md)van de Stap.

### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de modus Lay-out {#multi-column-adaptive-forms}

U kunt nu het aantal kolommen voor een deelvenster definiëren in adaptieve formulieren en interactieve communicatie.

U vindt de nieuwe optie door over te schakelen op de modus Lay-out. Tik op het deelvenster dat u wilt omzetten in een indeling met meerdere kolommen, selecteer het bovenliggende venster en tik op het pictogram met meerdere kolommen om het aantal kolommen voor het deelvenster te definiëren.

![Lay-out met meerdere kolommen](assets/multi-column-layout.gif)

Zie De modus Lay-out [gebruiken om het formaat van componenten](../forms/using/resize-using-layout-mode.md)te wijzigen voor meer informatie.

### AEM Inbox-aanpassingen {#aem-inbox}

Voelt u ooit de behoefte om opties aan te passen beschikbaar in kopbal AEM? Het is nu mogelijk met onze nieuwe versie van Service Pack met de introductie van een optie van de Controle **** Admin.

**Koptekst aanpassen**

Workflowbeheerders kunnen nu naar eigen keuze koptekst opgeven.

U vindt de nieuwe optie Koptekst **[!UICONTROL aanpassen in koptekst]** onder Weergaveselectie (beschikbaar in de rechterbovenhoek van de werkbalk) > **[!UICONTROL Beheer]**.

**Logo aanpassen**

Net als bij het aanpassen van koptekst kunnen workflowbeheerders nu naar keuze het headerlogo opgeven.

U vindt de nieuwe optie Logo **** aanpassen onder Weergaveselectie > **[!UICONTROL Beheer]**.

Zie [Uw Postvak IN](../sites-authoring/inbox.md)voor meer informatie over deze functie.

### Gebruikersnavigatiecontrole {#user-navigation-control}

Workflowbeheerders hebben nu de mogelijkheid om gebruikers in beperkte modus op basis van hun rol aan AEM te laten werken. De beheerders kunnen de weergave van navigatieopties in de koptekst bepalen om de gebruikers te beperken tot het schakelen naar de workflowontwerpmodus of naar andere oplossingskoppelingen.

Bekijk de nieuwe navigatieopties **** Verbergen onder Weergaveselector > **[!UICONTROL Beheer]**.

Zie [Uw Postvak IN](../sites-authoring/inbox.md)voor meer informatie over deze functie.

### RTF-ondersteuning in HTML5-formulieren {#rich-text-support}

In het tekstveld kan nu een lijst met opmaakopties worden weergegeven in het weergegeven HTML5-formulier. U moet een opmaak definiëren voor het tekstveld in Forms Designer om de juiste instellingen op het veld toe te passen.

Tik op het tekstveld in de **[!UICONTROL ontwerpweergave]** in Forms Designer om deze functie te gebruiken. Selecteer op het tabblad **[!UICONTROL Veld]** de optie **[!UICONTROL RTF]** in de vervolgkeuzelijst **[!UICONTROL Veldindeling]** om de instellingen toe te passen.

Zie Formuliersjablonen [ontwerpen voor HTML5-formulieren](../forms/using/designing-form-template.md)voor meer informatie.

## Belangrijke markeringen

Naast de nieuwe functies bevat AEM 6.5 Service Pack 4 de volgende belangrijke kenmerken:

* U kunt selectieve inhoudsubstructuren nu synchroniseren naar Scene7 in plaats van naar alle beschikbare substructuren `content/dam`.

* Integratie van formuliergegevensmodellen met SOAP-webservice ondersteunt nu keuzegroepen of kenmerken voor elementen.

* De invoer of de output van de ZEEP en complexe gegevensstructuren steunen nu Dynamische Vervanging van de Groep.

## Belangrijkste functies in vorige AEM 6.5-servicepacks

### Smart Imaging voor dynamische media {#smart-imaging}

Slimme beeldverwerking maakt gebruik van de unieke weergavekenmerken van elke gebruiker, zodat deze automatisch de juiste afbeeldingen levert die zijn geoptimaliseerd voor zijn of haar ervaring, wat resulteert in betere prestaties en betrokkenheid. Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [Slimme afbeeldingen](../assets/imaging-faq.md).

### Visuele zoekopdracht naar AEM-elementen {#visual-search}

Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Visueel onderzoek](../assets/search-assets.md).

### Deel en verzoek toegang tot Inbox punten van een gebruiker {#share-request-access}

U kunt uw Inbox punten met een andere gebruiker delen. Zodra een andere gebruiker toegang heeft tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken. Zie [Delen en verzoek om toegang tot Inbox-items van een gebruiker](../forms/using/configure-shared-queues-osgi.md).

### Vorm uit bureau het plaatsen voor uw Inbox punten {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U kunt een begindatum en -tijd en een einddatum en -tijd opgeven die van kracht moeten worden als uw instellingen buiten het kantoor zijn. U kunt een standaardpersoon instellen waarnaar al uw items worden verzonden. Zie [Vorm uit de montages](../forms/using/configure-out-of-office-settings.md)van het Bureau.

### Meerdere interactieve communicatie genereren met de Batch-API {#generate-multiple-ic}

U kunt de batch-API gebruiken om meerdere interactieve communicatie van een sjabloon te maken. De sjabloon is een interactieve communicatie zonder gegevens. De batch-API combineert gegevens met een sjabloon voor interactieve communicatie. De API is nuttig bij de massaproductie van interactieve communicatie. Bijvoorbeeld telefoonrekeningen, creditcardoverzichten voor meerdere klanten. Zie Meerdere interactieve communicatie [genereren met de Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

### Standaardvalidatiefoutenberichten voor adaptieve formulieren {#standard-validation}

Aangepaste formulieren kunnen nu worden geïntegreerd met aangepaste services om gegevensvalidaties uit te voeren. Als de invoerwaarden niet voldoen aan de validatiecriteria en het foutbericht dat de server retourneert, de standaardberichtindeling heeft, worden de foutberichten in het formulier op veldniveau weergegeven. Als de invoerwaarden niet voldoen aan de validatiecriteria en het foutbericht voor servervalidatie niet in de standaardberichtindeling is, bieden de adaptieve formulieren een mechanisme om de foutberichten voor validatie om te zetten in een standaardnotatie, zodat ze op veldniveau in het formulier worden weergegeven. Zie [Standaardfoutberichten voor validatie voor adaptieve formulieren](../forms/using/standard-validation-error-messages-adaptive-forms.md).

## Belangrijke releases sinds AEM 6.5 SP3

Tussen 12 december 2019 en 5 maart 2020 heeft Adobe de volgende functies uitgebracht die buiten de kernlevering van AEM vallen:

* AEM Cloud Manager 2020.1.0 en 2020.2.0Maandelijkse verbeteringen in Cloud Manager, de laatste twee versies waren gericht op het verbeteren van de pijpleidingsstatus en de capaciteit om logboeken voor de diverse stappen te downloaden. Lees hier de volledige opmerkingen over de release:
   * [Cloud Manager 2020.1.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-1-0.html)

   * [Cloud Manager 2020.2.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html)

* Updates van AEM Cloud Manager CLIAutomate Cloud Manager-taken met behulp van het opdrachtregelprogramma. Wij breiden voortdurend CLI uit - sluit zich aan bij op [GitHub](https://github.com/adobe/aio-cli-plugin-cloudmanager/releases).

* AEM-sites: Projectarchetype 23The best way to start a new AEM project. Met Archetype 23 [verenigen wij het Archetype van het Project voor SPA en regelmatige plaatsen in één](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-23), verder verstrekkend een standaardthema om uw front-end ontwikkeling te starten.

* AEM-sites: WKND Reference SiteAll [nieuw referentieproject](https://www.wknd.site/) verpakt met beste praktijken op hoe te om plaatsen met AEM te bouwen. Leer meer door het volledig bijgewerkte [WKND leerprogramma](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html) te lezen en de code van [GitHub](https://github.com/adobe/aem-guides-wknd/releases)te pakken.

* AEM-sites: Commerce CIF Core Components 0.7.0 en 0.9.0Integrating AEM Sites and Magento Commerce. We [breiden voortdurend speciale kerncomponenten uit en een projectarchetype dat zich richt op handel](https://github.com/adobe/aem-core-cif-components/releases).

* AEM-elementen: Desktop App 2.0.1.1
   [Desktoptoegang tot de middelen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)

* AEM-schermen: Feature Pack 202001Digital Signage rechtstreeks vanuit AEM. Bekijk de nieuwste verbeteringen met het nieuwste Feature Pack. Dit keer [maken we het synchroon afspelen op meerdere mediaspelers](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202001.html)mogelijk.

## Nuttige bronnen

* [Handleidingen voor AEM 6.5-gebruikers](../user-guide/capabilities.md)

* [Algemene opmerkingen bij de release van Adobe Experience Manager 6.5](release-notes.md)

* [Opmerkingen bij de release van Service Pack voor Adobe Experience Manager 6.5](sp-release-notes.md)
