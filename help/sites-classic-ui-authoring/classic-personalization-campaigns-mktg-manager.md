---
title: Werken met de manager van de Campagne van de Marketing
seo-title: Werken met de manager van de Campagne van de Marketing
description: MCM (Marketing Campaign Manager) is een console waarmee u campagnes met meerdere kanalen kunt beheren. Met deze software voor marketingautomatisering kunt u al uw merken, campagnes en ervaringen beheren, samen met de verwante segmenten, lijsten, leads en rapporten.
seo-description: MCM (Marketing Campaign Manager) is een console waarmee u campagnes met meerdere kanalen kunt beheren. Met deze software voor marketingautomatisering kunt u al uw merken, campagnes en ervaringen beheren, samen met de verwante segmenten, lijsten, leads en rapporten.
uuid: 63b817e4-34b9-42b8-845b-e0b7d9af3a96
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 11ff8bb3-39eb-4f77-b3dc-720262fa7f3f
docset: aem65
translation-type: tm+mt
source-git-commit: dc1985c25c797f7b994f30195d0586f867f9b3ee
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---


# Werken met de Manager van de Campagne van de Marketing{#working-with-the-marketing-campaign-manager}

In AEM, is de Manager van de Campagne van de Marketing (MCM) een console die u multi-kanaalcampagnes helpt beheren. Met deze software voor marketingautomatisering kunt u al uw merken, campagnes en ervaringen beheren, samen met de verwante segmenten, lijsten, leads en rapporten.

MCM is toegankelijk vanaf verschillende locaties in AEM; bijvoorbeeld het welkomstscherm met het pictogram Campagnes of de URL:

`https://<hostname>:<port>/libs/mcm/content/admin.html`

Bijvoorbeeld:

`https://localhost:4502/libs/mcm/content/admin.html`

![screen_shot_2012-02-21at114636am](assets/screen_shot_2012-02-21at114636am.png)

Via de MCM hebt u toegang tot:

* **[](#dashboard)**
DashboardDit bestaat uit vier deelvensters:

   * [](#lists)
LijstenIn dit deelvenster worden de lijsten weergegeven die u al hebt gemaakt, samen met het aantal leads in die lijst. In dit deelvenster kunt u rechtstreeks een nieuwe lijst maken of u kunt leads importeren om een nieuwe lijst te maken.
Als u een specifieke lijst selecteert, gaat u naar de sectie [Lijsten](#lists) met details voor uw lijst.

   * [](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#anoverviewofsegmentation)
SegmentsThis ruit toont de segmenten die u hebt bepaald. Met segmenten kunt u een verzameling bezoekers karakteriseren die bepaalde kenmerken delen.
Als u een specifiek segment selecteert, wordt de pagina voor segmentdefinitie geopend.

   * [](/help/sites-administering/reporting.md)
ReportsAEM verstrekt verschillende rapporten om u te helpen de staat van uw instantie analyseren en controleren. In dit deelvenster MCM worden de rapporten weergegeven.
Als u een rapport selecteert, wordt de rapportpagina geopend.

   * [](#campaigns)
CampaignsIn dit deelvenster worden uw ervaringen met campagnes weergegeven, zoals  [](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) nieuwsbrieven en  [tijdschriften](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#teasers).

* **[](#leads)**
LeadsHier kun je je leads beheren. U kunt leads maken of importeren, specifieke details voor afzonderlijke leads bewerken of verwijderen wanneer u deze niet meer nodig hebt. U kunt ook leads in verschillende groepen plaatsen, genaamd Lijsten. **Opmerking:** Adobe is niet van plan deze mogelijkheid verder te verbeteren.
De aanbeveling is om Adobe Campaign en de integratie in AEM[ te benutten.](/help/sites-administering/campaign.md)

* **[](#lists)**
LijstenHier kunt u uw lijsten (van leads) beheren.**Opmerking:** Adobe is niet van plan deze mogelijkheid verder te verbeteren.
De aanbeveling is om Adobe Campaign en de integratie in AEM[ te benutten.](/help/sites-administering/campaign.md)

* **[](#campaigns)**
CampagnesHier kunt u uw merken, campagnes en ervaringen beheren.

## Dashboard {#dashboard}

Het dashboard bevat vier deelvensters die u een overzicht bieden van uw lijsten (van leads), segmenten, rapporten en campagnes. Hier is ook toegang tot de basisfuncties beschikbaar.

![mcm_dashboard](assets/mcm_dashboard.png)

### Leads {#leads}

>[!NOTE]
>
>Adobe is niet van plan deze mogelijkheid verder te verbeteren (Leads beheren).
>De aanbeveling is om [Adobe Campaign en de integratie in AEM](/help/sites-administering/campaign.md) te benutten.

In AEM MCM, kunt u leiden organiseren en toevoegen door of hen manueel in te gaan of een komma-gescheiden lijst in te voeren; bijvoorbeeld een mailinglijst. Aanvullende manieren om leads te genereren zijn afkomstig van aanmeldingspogingen in een nieuwsbrief of aanmeldingspogingen van de gebruikersgemeenschap (als deze zijn geconfigureerd, kunnen ze een workflow activeren die leads vult). Regelafstand wordt meestal gecategoriseerd en in een lijst geplaatst, zodat u later handelingen kunt uitvoeren op de hele lijst. bijvoorbeeld het verzenden van een aangepaste e-mail naar een bepaalde lijst.

Onder **Leads** in het linkerdeelvenster kunt u uw leads maken, importeren, bewerken en verwijderen en vervolgens desgewenst activeren of deactiveren. U kunt een lead aan een lijst toevoegen of zien tot welke lijsten deze al behoort.

>[!NOTE]
>
>Zie [Werken met leads](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithleads) voor gedetailleerde informatie over specifieke taken.

![screen_shot_2012-02-21at114748am-1](assets/screen_shot_2012-02-21at114748am-1.png)

### Lijsten {#lists}

>[!NOTE]
>
>Adobe is niet van plan deze mogelijkheid verder te verbeteren (lijsten beheren).
>De aanbeveling is om [Adobe Campaign en de integratie in AEM](/help/sites-administering/campaign.md) te benutten.

Met lijsten kunt u uw leads ordenen in groepen. Met lijsten kunt u uw marketingcampagnes richten op een bepaalde groep personen; U kunt bijvoorbeeld een doelnieuwsbrief naar een lijst sturen.

Onder **Lijsten**, kunt u uw lijsten beheren door het creëren, het invoeren, het uitgeven, het samenvoegen en het schrappen van lijsten die u dan kunt activeren of desgewenst deactiveren. U kunt ook de leads in die lijst bekijken, kijken of de lijst lid is van een andere lijst of de beschrijving bekijken.

>[!NOTE]
>
>Zie [Werken met lijsten](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists) voor gedetailleerde informatie over specifieke taken.

![screen_shot_2012-02-21at124828pm-1](assets/screen_shot_2012-02-21at124828pm-1.png)

### Campagnes {#campaigns}

>[!NOTE]
>
>Zie [Teasers en Strategieën](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#workingwithlists), [Uw Campagne](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#settingupyourcampaign) en [Nieuwsbrieven](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md#newsletters) instellen voor gedetailleerde informatie over specifieke taken.

Om tot bestaande campagnes toegang te hebben, in MCM klik **Campagnes**.

![screen_shot_2012-02-21at11106pm](assets/screen_shot_2012-02-21at11106pm.png)

* **In het linkervenster**: Er is een lijst van alle merken en campagnes.
Een enkele klik op een merk zal allebei:

   * de lijst uit te breiden om alle verwante campagnes in de linkerruit te tonen; in deze lijst wordt ook het aantal ervaringen vermeld dat voor elke campagne bestaat .
   * Open het merkoverzicht in de juiste ruit.

* **In het rechterdeelvenster**: Pictogrammen worden voor elk merk getoond (historische campagnes worden niet weergegeven).
U kunt dubbelklikken op deze opties om het merkoverzicht te openen.

#### Brand - overzicht {#brand-overview}

![mcm_brandoverview](assets/mcm_brandoverview.png)

Vanaf hier kunt u:

* Zie het aantal campagnes en ervaringen (nummer weergegeven in het linkervenster) dat voor dit merk bestaat.
* Een **Nieuw maken...** campagne voor dit merk.

* Wijzig de tijdlijn die wordt weergegeven. Selecteer **Week**, **Month** of **Kwart**, gebruik de pijlen om specifieke periodes te selecteren of op **Vandaag** terug te komen.

* Selecteer een campagne (in het rechterdeelvenster) om:

   * Bewerk de **eigenschappen..**
   * **De** campagne verwijderen.

* Open het campagneoverzicht (dubbelklik op een campagne in het rechterdeelvenster of klik met één klik in het linkerdeelvenster).

#### Campagneoverzicht {#campaign-overview}

Voor de afzonderlijke campagnes zijn twee weergaven beschikbaar:

1. **Kalenderweergave**

   Gebruik het pictogram:

   ![](do-not-localize/mcm_iconcalendarview.png)

   Hierin wordt een lijst weergegeven van alle (grijze) aanraakpunten met een horizontaal tijdkader van de (groene) ervaringen die met dat aanraakpunt zijn verbonden:

   ![mcm_banner_calendarview](assets/mcm_banner_calendarview.png)

   Vanaf hier kunt u:

   * Verander timespan u bekijkt door de pijlen te gebruiken, of terugkeer aan **Today**.

   * **Aanraakpunt toevoegen gebruiken...** om een nieuw aanraakpunt voor een bestaande ervaring toe te voegen.

   * Klik op een teaser (in het rechterdeelvenster) om de **On Time** en **Off Time** in te stellen.

1. **Lijstweergave**

   Gebruik het pictogram:

   ![](do-not-localize/mcm_icon_listview.png)

   Hier worden alle ervaringen (zoals theaters en nieuwsbrieven) voor de geselecteerde campagne weergegeven:

   ![mcm_banner_listview](assets/mcm_banner_listview.png)

   Vanaf hier kunt u:

   * Een **Nieuw maken...** ervaring; adobe target biedt bijvoorbeeld, theaters en nieuwsbrieven.
   * **Bewerk de details van een specifieke teaserpagina of nieuwsbrief (u kunt ook dubbelklikken).** 
   * **Eigenschappen definiëren..** voor een specifieke laserpagina of nieuwsbrief.
   * **De** vormgeving van een ervaring simuleren (laserpagina of nieuwsbrief).
Wanneer de gesimuleerde pagina is geopend, kunt u het hulpprogramma openen om over te schakelen naar de bewerkingsmodus voor die pagina.

   * **Analyseren...** de afbeeldingen die voor een pagina zijn gegenereerd.

   * **Items** verwijderen wanneer deze niet meer nodig zijn.
   * **Zoek** naar uw tekst (het veld Titel van de ervaring wordt doorzocht).
   * Gebruik **Geavanceerd** onderzoek om filters op het onderzoek toe te passen.

### Simuleren van uw ervaringen met campagnes {#simulating-your-campaign-experiences}

Klik in de MCM op **Campagnes**. Zorg ervoor dat de lijstmening actief is, dan selecteer de vereiste campagneervaring en klik **Simuleer**. Het aanraakpunt (teaser- of nieuwsbrief) wordt geopend om de ervaring te tonen die u hebt geselecteerd, zoals de bezoeker het ziet.

![mcm_simulatie-ervaring](assets/mcm_simulateexperience.png)

Van hieruit kunt u ook het hulpslot openen (klik op de kleine pijl-omlaag) om de bewerkingsmodus voor het bijwerken van de pagina te wijzigen.

### Uw ervaringen met campagnes analyseren {#analyzing-your-campaign-experiences}

Klik in de MCM op **Campagnes**. Zorg ervoor dat de lijstweergave actief is, selecteer vervolgens de vereiste campagneervaring en selecteer **Analyseren...**. Er wordt een grafiek weergegeven met de paginamonpressies die in de loop der tijd worden weergegeven.

![mcm_campagne analyseren](assets/mcm_campaignanalyze.png)
