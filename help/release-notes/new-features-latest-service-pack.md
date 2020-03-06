---
title: Wat in Manager 6.5 Service Pack 4 van de Ervaring van Adobe nieuw is
description: Wat in Manager 6.5 Service Pack 4 van de Ervaring van Adobe nieuw is
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 14df85f7a815fe567ea87375727ebe1e54733464

---


# Wat in Manager 6.5 Service Pack 4 van de Ervaring van Adobe nieuw is {#aem-whats-new-service-pack-4}

In 2020, levert de Manager van de Ervaring van Adobe (AEM) 6.5 eigenschappen en ononderbroken verbeteringen in de driemaandelijkse Pakken van de Dienst. De klanten profiteren van deze nieuwe benadering aangezien zij de innovaties sneller kunnen goedkeuren.

Het recentste AEM Service Pack 4 (6.5.4.0) wordt vrijgegeven op 5 **maart 2020**. In dit artikel worden de functies belicht die het nieuwste Service Pack aanbiedt om uw AEM-reis verrijkend te maken.

## AEM Sites {#aem-sites}

### Prestatieverbeteringen op verschillende gebieden {#performance-improvements}

* Verminderde de tijd voor het laden van en het initialiseren van ContextHub binnen een plaats (contexthub.kernel.js). Het resulteert in het laden van een pagina sneller tijdens een plaatsbezoek.

* Verminderde de tijd om een pagina na het slepen te verfrissen &amp; het laten vallen van de Fragmenten van de Ervaring in het canvas van een paginaredacteur te verfrissen.

* In het Levende Overzicht van het Exemplaar, verkortte de tijd om ingangen te laden wanneer een plaats meer dan 200 levende exemplaren heeft.

* In de Redacteur van het Malplaatje, verbeterde de behandeling van onvolledige of ongeldige URLs die de Redacteur van het Malplaatje kan teweegbrengen om te vertragen.

Bovendien omvat AEM 6.5 SP4 de verhogingen van het Systeem van de Stijl. U kunt stijlen binnen een componentendialoog nu ook selecteren.


## AEM Assets {#aem-assets}

### Integratie met het Portaal van het Merk door de Console van Adobe I/O {#assets-integration-bp}

AEM de Activa wordt nu gevormd met het Portaal van het Merk door Adobe I/O, dat een teken IMS voor vergunning van de Poorthuurder van het Merk koopt. Eerder, werd het gevormd in Klassieke UI via de Gateway van de Oudheid OAuth.

De nieuwe integratie met de OAuth van de Oudheid zal niet na 6 april 2020 worden gesteund en zal naar de Console van Adobe I/O verschuiven. Als u niet de integratie wijzigt, zullen de bestaande configuraties blijven werken.

U kunt of een nieuwe integratie tot stand brengen of uw integratiemontages bevorderen aan de Console van Adobe I/O.

### Verbeteringen voor toegankelijkheid {#accessibility-enhancements}

* De gemengde dozen van de staat hebben nu aria-gecontroleerde attributen met een waarde van &quot;gemengd&quot;, om hun gemengde staat aan het schermlezers bloot te stellen.

* De op toetsenbord-gebaseerde controles worden nu gesteund behalve op weg-gebaseerde gebaren om zich rond gezoemde beelden te bewegen.

* De het formaatbeperkingen van de datum zijn verstrekt in gebiedslabels voor toetsenbord-enige gebruikers om datum manueel in te gaan.

* De attributen van Alt zijn toegevoegd aan decoratieve pictogrammen en verwijderd role=img attributen, zodat dergelijke pictogrammen en beelden niet aan de gebruikers van de het schermlezer worden blootgesteld.

* Het attribuut van Alt is toegevoegd aan dichte pictogrammen om op te wijzen aan de gebruikers van de het schermlezer wanneer zij over het lusje.

## AEM Forms {#aem-forms}

### Produceer gedrukte output in de werkschema&#39;s van Vormen AEM {#generate-printable-output}

Als u een oplossing veelvoudige exemplaren van een bronmalplaatjedossier wilt drukken en het met een gegevensdossier met talrijke verslagen integreren, is een nieuwe Generate Printable het werkschemastap van de Output beschikbaar in Vormen AEM. Bijvoorbeeld, als u een bronvorm met een verschillende naam wilt drukken telkens als het wordt gedrukt, kunt u die namen in het gegevensdossier hebben en het integreren met een standaardmalplaatjedossier.

Haal voordeel uit deze eigenschap gebruikend **Hulpmiddelen** > **[!UICONTROL Werkschema]** > **[!UICONTROL Modellen]** > **[!UICONTROL creeer]** en zoek dan naar de het werkschemastap van de Output van de **[!UICONTROL Productie]** produceren Afdrukbaar.

![Afdrukbare uitvoer genereren](assets/generate-print-output-demo.gif)

Voor meer informatie over deze eigenschap, zie [vorm-centric werkschema op OSGi - de Verwijzing](../forms/using/aem-forms-workflow-step-reference.md)van de Stap.

### Ondersteuning voor meerdere kolommen voor adaptieve formulieren en interactieve communicatie in de indelingsmodus {#multi-column-adaptive-forms}

U kunt het aantal kolommen voor een paneel in adaptieve vormen en interactieve mededelingen nu bepalen.

U kunt de nieuwe optie vinden door op de wijze van de Lay-out over te schakelen, het paneel te tikken dat u in een multi-kolomformaat wilt omzetten, zijn ouder en tik multi-kolompictogram te selecteren, zoals die in het volgende cijfer wordt getoond, om het aantal kolommen voor het paneel te bepalen.

![Meerdere kolomindeling](assets/multi-column-layout.gif)

Voor meer informatie, zie de wijze van de Lay-out van het [Gebruik resize componenten](../forms/using/resize-using-layout-mode.md).

### Aanpassingen van AEM Inbox {#aem-inbox}

Voelt u ooit de behoefte om opties aan te passen beschikbaar in de kopbal van AEM? Het is nu mogelijk met onze nieuwe versie van Service Pack met de introductie van een optie van de Controle van **[!UICONTROL Admin]** .

**Koptekst aanpassen**

De gebruikers die tot **werkschema-beheerders** behoren kunnen kopbaltekst nu aanpassen beschikbaar bij de bovenkant met tekst van uw eigen keus om de bestaande tekst van de Manager **[!UICONTROL van de Ervaring van]** Adobe te vervangen.

U kunt de nieuwe optie van de **[!UICONTROL Customize kopbaltekst]** onder meningsselecteur (beschikbaar bij bovenkant-recht van de toolbar) vinden > **[!UICONTROL de Controle]** van Admin.

**Logo aanpassen**

Gelijkaardig aan het aanpassen van kopbaltekst, kunnen de gebruikers die tot **werkschema-beheerders** groep behoren het embleem nu aanpassen beschikbaar bij de bovenkant met embleem van uw eigen keus.

U kunt de nieuwe optie van het **[!UICONTROL Logo]** onder meningsselecteur > **[!UICONTROL Admin Controle]** vinden aanpassen.

Voor meer informatie over deze eigenschap, zie [Uw Postbus](../sites-authoring/inbox.md).

### Gebruikersnavigatiecontrole {#user-navigation-control}

De gebruikers die tot **werkschema-beheerders** behoren hebben de optie om het gebruikerswerk aan AEM op een beperkte wijze te maken die op hun rol wordt gebaseerd. De beheerders kunnen de vertoning van navigatieopties controleren beschikbaar in de kopbal en de gebruikers beperken om op werkschemaauteurswijze over te schakelen of aan Hulp of andere oplossingsverbindingen te navigeren.

Bekijk de nieuwe **[!UICONTROL navigatieopties]** verbergen onder de weergaveselector > **[!UICONTROL Beheer]**.

Voor meer informatie over deze eigenschap, zie [Uw Postbus](../sites-authoring/inbox.md).

### De rijke tekststeun in de vormen van HTML5 {#rich-text-support}

Het tekstgebied kan een lijst van het formatteren opties in de teruggegeven vorm nu tonen HTML5. U moet een gebiedsindeling voor het tekstgebied in de Ontwerper van Vormen bepalen om aangewezen montages op het gebied toe te passen.

Om deze eigenschap te gebruiken, tik het tekstgebied in de Mening **[!UICONTROL van het]** Ontwerp in de Ontwerper van Vormen. In het **[!UICONTROL lusje van het Gebied]** , uitgezochte **[!UICONTROL Rijke Tekst]** van de drop-down lijst van het Formaat **[!UICONTROL van het]** Gebied om de montages toe te passen. Het tekstgebied toont nu het formatteren opties wanneer teruggegeven in een vorm HTML5.

Voor meer informatie, zie het [Ontwerpen van vormmalplaatjes voor HTML5 vormen](../forms/using/designing-form-template.md).

## Belangrijkste kenmerken

Naast de nieuwe eigenschappen, omvat AEM 6.5 Service Pack 4 de volgende belangrijkste hoogtepunten:

* Slechts kunnen de selectieve inhoudsubbomen nu aan Scene7 in plaats van allen worden gesynchroniseerd `content/dam`.

* De modelintegratie van de gegevens van de vorm die de het Webdienst van de ZEEP gebruikt steunt nu keuzegroepen of attributen op elementen.

* De input of de output van de ZEEP en de complexe gegevensstructuren steunen nu de Dynamische Vervanging van de Groep.

## Belangrijkste kenmerken van de vorige AEM 6.5-servicepacks

### Smart Imaging voor dynamische media {#smart-imaging}

Slimme beeldverwerking maakt gebruik van de unieke kijkkenmerken van elke gebruiker om automatisch de juiste afbeeldingen te bedienen die zijn geoptimaliseerd voor hun ervaring, wat resulteert in betere prestaties en een betere service. De slimme beeldvorming werkt met uw bestaand beeld vooraf instelt en gebruikt intelligentie bij de laatste milliseconde van levering om beelddossiergrootte verder te verminderen die op browser of de snelheid van de netwerkverbinding wordt gebaseerd. Zie [Smart Imaging](../assets/imaging-faq.md).

### Visuele zoekopdracht naar AEM-elementen {#visual-search}

De gebruikers van activa kunnen visueel gelijkaardige beelden zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [Visueel onderzoek](../assets/search-assets.md).

### Aandeel en verzoek toegang tot de punten Inbox van een gebruiker {#share-request-access}

Je kunt je Postvak IN-objecten delen met een andere gebruiker. Zodra een andere gebruiker toegang tot uw Inbox punten heeft, kan de gebruiker om aangewezen actie op gedeelde punten eisen en nemen. Op dezelfde manier kunt u om toegang tot punten Inbox van andere gebruikers verzoeken. Zie [Aandeel en verzoek toegang tot punten Inbox van een gebruiker](../forms/using/configure-shared-queues-osgi.md).

### Vorm uit bureau plaatsend voor uw Inbox punten {#configure-out-of-office}

Als u van plan bent om uit het bureau te zijn, kunt u specificeren wat aan punten gebeurt die aan u voor die periode worden toegewezen.
U hebt de optie om een begindatum en tijd en een einddatum en tijd voor uw uit-van-bureaumontages te specificeren om in feite te zijn. Je kunt een standaardpersoon instellen waarnaar al je objecten worden verzonden. Zie [uit de montages](../forms/using/configure-out-of-office-settings.md)van het Bureau vormen.

### Produceer veelvoudige interactieve mededelingen gebruikend Partij API {#generate-multiple-ic}

U kunt de Partij API gebruiken om veelvoudige interactieve mededelingen van een malplaatje te veroorzaken. Het malplaatje is een interactieve mededeling zonder enige gegevens. De partij API combineert gegevens met een malplaatje om een interactieve mededeling te veroorzaken. API is nuttig bij de massaproductie van interactieve mededelingen. Bijvoorbeeld, telefoonrekeningen, creditcardverklaringen voor veelvoudige klanten. Zie [veelvoudige interactieve mededelingen produceren gebruikend Partij API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

### Standaardvalidatiefout voor adaptieve formulieren {#standard-validation}

De aanpassingsvormen kunnen nu met de douanediensten integreren om gegevensbevestigingen uit te voeren. Als de inputwaarden niet aan de bevestigingscriteria en de bevestigingsfoutenmelding voldoen dat de serverwinst in het standaardberichtformaat is, tonen de foutenmeldingen op gebied-niveau in de vorm. Als de inputwaarden niet aan de bevestigingscriteria voldoen en de foutenmelding van de serverbevestiging niet in het standaardberichtformaat is, verstrekken de adaptieve vormen een mechanisme om de bevestigingsfoutenmeldingen in een standaardformaat om te zetten zodat zij op gebied-niveau in de vorm tonen. Zie [Standaard bevestigingsfoutberichten voor adaptieve formulieren](../forms/using/standard-validation-error-messages-adaptive-forms.md).

## Zeer belangrijke versies sinds AEM 6.5 SP3

Tussen 12 december 2019 en 5 maart 2020 gaf Adobe de volgende mogelijkheden vrij die buiten de kernAEM leverbaar zijn:

* AEM Cloud Manager 2020.1.0 en 2020.2.0Maandelijkse verbeteringen aan Cloud Manager, laatste twee versies concentreerden zich op het verbeteren van de pijpleidingsstatus en de capaciteit om logboeken voor de diverse stappen te downloaden. Lees hier de volledige releasenota&#39;s:
   * [Cloud Manager 2020.1.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-1-0.html)

   * [Cloud Manager 2020.2.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html)

* CLI-updates van AEM Cloud ManagerAutomate Cloud Manager-taken met het opdrachtregelprogramma. Wij breiden onophoudelijk CLI uit - sluit zich aan bij op [GitHub](https://github.com/adobe/aio-cli-plugin-cloudmanager/releases).

* AEM-sites: Project Archetype 23The beste manier om een nieuw AEM project te beginnen. Met Archetype 23 [fuseren we het Project Archetype voor SPA en reguliere sites tot één](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-23), en bieden we verder een standaardthema om uw front-end ontwikkeling te starten.

* AEM-sites: De Plaats van de Verwijzing van WKNDAl [nieuw verwijzingsproject](https://www.wknd.site/) verpakt met beste praktijken over hoe te om plaatsen met AEM te bouwen. Leer meer lezend het volledig bijgewerkte leerprogramma [WKND](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html) en pak de code van [GitHub](https://github.com/adobe/aem-guides-wknd/releases).

* AEM-sites: Commerce CIF Core Components 0.7.0 en 0.9.0Integratie van AEM-sites en Magento Commerce. We zijn voortdurend bezig met het [uitbreiden van speciale kerncomponenten en een projectarchetype met focus op handel](https://github.com/adobe/aem-core-cif-components/releases).

* AEM-activa: Desktop App 2.0.1.1
   [Krijg Desktoptoegang tot de middelen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)

* AEM-schermen: Feature Pack 202001Digital Signage direct van binnen AEM. Pak de recentste verbeteringen met het recentste Pak van de Eigenschap, dit keer [toelaten wij de synchrone playback over veelvoudige media spelers](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202001.html).

## Nuttige middelen

* [AEM 6.5-gebruikershandleidingen](../user-guide/capabilities.md)

* [De algemene Nota&#39;s van de Versie voor Manager 6.5 van de Ervaring van Adobe](release-notes.md)

* [De Nota&#39;s van de Versie van het Service Pack voor Manager 6.5 van de Ervaring van Adobe](sp-release-notes.md)
