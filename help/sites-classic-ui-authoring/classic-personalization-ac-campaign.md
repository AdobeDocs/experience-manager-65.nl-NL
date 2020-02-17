---
title: Werken met Adobe Campagne 6.1 en Adobe Campaign Standard
seo-title: Werken met Adobe Campagne 6.1 en Adobe Campaign Standard
description: U kunt e-mailinhoud maken in AEM en deze verwerken in e-mails voor Adobe Campagne.
seo-description: U kunt e-mailinhoud maken in AEM en deze verwerken in e-mails voor Adobe Campagne.
uuid: 439df7fb-590b-45b8-9768-565b022a808b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 61b2bd47-dcef-4107-87b1-6bf7bfd3043b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Werken met Adobe Campagne 6.1 en Adobe Campaign Standard{#working-with-adobe-campaign-and-adobe-campaign-standard}

U kunt e-mailinhoud maken in AEM en deze verwerken in e-mails voor Adobe Campagne. Daartoe moet u:

1. Maak een nieuwe nieuwsbrief in AEM van een specifieke sjabloon voor Adobe Campagne.
1. Selecteer [een Adobe Campagne-service](#selectingtheadobecampaigncloudservice) voordat u de inhoud gaat bewerken om toegang te krijgen tot alle functies.
1. Bewerk de inhoud.
1. Valideer de inhoud.

Inhoud kan vervolgens worden gesynchroniseerd met een levering in Adobe Campaign. In dit document worden gedetailleerde instructies beschreven.

>[!NOTE]
>
>Voordat u deze functionaliteit kunt gebruiken, moet u AEM zodanig configureren dat deze kan worden geïntegreerd met [Adobe Campaign](/help/sites-administering/campaignonpremise.md) of [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md).

## E-mailinhoud verzenden via Adobe-campagne {#sending-email-content-via-adobe-campaign}

Nadat u AEM en de Campagne van Adobe vormt, kunt u e-mailleveringsinhoud direct in AEM tot stand brengen en het dan in de Campagne van Adobe verwerken.

Wanneer u Adobe Campagne-inhoud maakt in AEM, moet u een koppeling maken naar een Adobe Campagne-service voordat u de inhoud kunt bewerken om toegang te krijgen tot alle functies.

Er zijn twee mogelijke gevallen:

* Inhoud kan worden gesynchroniseerd met een levering vanuit Adobe Campaign. Op deze manier kunt u AEM-inhoud in een levering gebruiken.
* (Alleen Adobe Campagne op locatie) De inhoud kan rechtstreeks naar Adobe Campagne worden verzonden, waardoor automatisch een nieuwe e-maillevering wordt gegenereerd. Deze modus heeft beperkingen.

In dit document worden gedetailleerde instructies beschreven.

### Nieuwe e-mailinhoud maken {#creating-new-email-content}

>[!NOTE]
>
>Als u e-mailsjablonen toevoegt, moet u deze toevoegen onder **/inhoud/campagnes** om ze beschikbaar te maken.


1. Selecteer in AEM de map **Websites** en blader naar de verkenner om te zoeken waar uw e-mailcampagnes worden beheerd. In het volgende voorbeeld is het betrokken knooppunt **Websites** > **Campagnes** > **Geometrixx Outdoor** > **E-mailcampagnes**.

   >[!NOTE]
   >
   >[E-mailvoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md#weretail). Download voorbeeldinhoud van Geometrixx uit Pakket delen.

   ![chlimage_1-172](assets/chlimage_1-172.png)

1. Selecteer **Nieuw** > **Nieuwe pagina** om nieuwe e-mailinhoud te maken.
1. Selecteer een van de beschikbare sjablonen die specifiek zijn voor Adobe Campagne en vul vervolgens de algemene eigenschappen van de pagina in. Er zijn standaard drie sjablonen beschikbaar:

   * **Adobe Campagne-e-mail (AC 6.1)**: Hiermee kunt u inhoud toevoegen aan een vooraf gedefinieerde sjabloon voordat u deze naar Adobe Campagne 6.1 verzendt voor levering.
   * **Adobe Campagne-e-mail (ACS)**: Hiermee kunt u inhoud toevoegen aan een vooraf gedefinieerde sjabloon voordat u deze naar Adobe Campagnestandaard verzendt voor levering.
   ![chlimage_1-173](assets/chlimage_1-173.png)

1. Klik op **Maken** om uw e-mail of nieuwsbrief te maken.

### De cloudservice en sjabloon voor Adobe Campagne selecteren {#selecting-the-adobe-campaign-cloud-service-and-template}

Voor integratie met Adobe Campaign moet u een Adobe Campagne-cloudservice aan de pagina toevoegen. Zo hebt u toegang tot personalisatie en andere informatie over Adobe Campagne.

Daarnaast moet u mogelijk ook de Adobe Campagne-sjabloon selecteren en het onderwerp wijzigen en onbewerkte tekstinhoud toevoegen voor gebruikers die de e-mail niet in HTML zullen weergeven.

1. Selecteer het tabblad **Pagina** in het zijpaneel en selecteer vervolgens **Pagina-eigenschappen.**
1. Selecteer Service **** toevoegen op het tabblad **Cloudservices** in het pop-upvenster om de Adobe Campagneservice toe te voegen en klik op **OK**.

   ![chlimage_1-174](assets/chlimage_1-174.png)

1. Selecteer in de vervolgkeuzelijst de configuratie die overeenkomt met uw Adobe Campagne-instantie en klik op **OK**.

   >[!NOTE]
   >
   >Tik op **OK** of **Toepassen** nadat u de cloudservice hebt toegevoegd. Hierdoor werkt het tabblad **Adobe Campagne** correct.

1. Als u een specifieke sjabloon voor het verzenden van e-mail (vanuit Adobe Campaign) wilt toepassen, anders dan de standaardsjabloon voor **e-mail** , selecteert u nogmaals **Pagina-eigenschappen** . Voer op het tabblad **Adobe Campagne** de interne naam van de sjabloon voor het verzenden van e-mail in de verwante Adobe Campagne-instantie in.

   In Adobe Campaign Standard is de sjabloon **Aflevering met AEM-inhoud**. In Adobe Campagne 6.1 is de sjabloon **E-maillevering met AEM-inhoud**.

   Wanneer u de sjabloon selecteert, schakelt AEM automatisch de **Adobe Campagne Newsletter** -componenten in.

### E-mailinhoud bewerken {#editing-email-content}

U kunt e-mailinhoud bewerken in de klassieke gebruikersinterface of in de gebruikersinterface met geoptimaliseerde aanrakingen.

1. Voer het onderwerp en de tekstversie van de e-mail in door **Pagina-eigenschappen** > **E-mail** te selecteren in de gereedschapset.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Bewerk e-mailinhoud door de elementen toe te voegen die u van de beschikbare elementen in de assistent wilt gebruiken. U doet dit door ze te slepen en neer te zetten. Dubbelklik vervolgens op het element dat u wilt bewerken.

   U kunt bijvoorbeeld tekst toevoegen die verpersoonlijkingsvelden bevat.

   ![chlimage_1-176](assets/chlimage_1-176.png)

   Zie [Adobe Campagne Components](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md) voor een beschrijving van de componenten die beschikbaar zijn voor nieuwsbrieven/e-mailcampagnes van Adobe Campagne.

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Personalisatie invoegen {#inserting-personalization}

Wanneer u de inhoud bewerkt, kunt u het volgende invoegen:

* Contextvelden voor Adobe Campagne. Dit zijn velden die u in de tekst kunt invoegen en die worden aangepast aan de gegevens van de ontvanger (bijvoorbeeld voornaam, achternaam of gegevens van de doeldimensie).
* Aanmaakblokken voor Adobe Campagne. Dit zijn blokken vooraf gedefinieerde inhoud die niet gerelateerd zijn aan de gegevens van de ontvanger, zoals een merklogo of een koppeling naar een spiegel.

Zie [Adobe Campagne Components](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md) voor een volledige beschrijving van de campagnecomponenten.

>[!NOTE]
>
>* Alleen de velden van de Adobe Campagne **Profiles** voor dimensie worden in aanmerking genomen.
>* Wanneer u Eigenschappen van **sites** weergeeft, hebt u geen toegang tot de contextvelden van Adobe Campagne. U kunt deze rechtstreeks vanuit de e-mail openen tijdens het bewerken.
>



1. Voeg een nieuwe **component Newsletter** > **Tekst en personalisatie (Campagne)** in.
1. Open de component door erop te dubbelklikken. Het venster **Bewerken** heeft een functionaliteit waarmee u de personalisatie-elementen kunt invoegen.

   >[!NOTE]
   >
   >De beschikbare contextvelden komen overeen met de doeldimensie van de **profielen** in Adobe-campagne.
   >
   >Zie Een AEM-pagina [koppelen aan een e-mail](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#linkinganaempagetoanadobecampaignemail)voor Adobe Campagne.

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Selecteer **Clientcontext** in het hulpprogramma om de personalisatievelden te testen aan de hand van de gegevens in de persoonlijke profielen.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Er verschijnt een venster waarin u de persoon kunt selecteren die u bevalt. De verpersoonlijkingsgebieden worden automatisch vervangen door gegevens van het geselecteerde profiel.

   ![chlimage_1-180](assets/chlimage_1-180.png)

### Een voorvertoning van een nieuwsbrief weergeven {#previewing-a-newsletter}

U kunt een voorvertoning weergeven van de weergave van de nieuwsbrief en een voorvertoning van de personalisatie.

1. Open de nieuwsbrief u voorproef en klik Voorproef (vergrootglas) om hulpdekick te krimpen.
1. Klik op een van de e-mailclientpictogrammen om te zien hoe uw nieuwsbrief er in elke e-mailclient uitziet.

   ![chlimage_1-181](assets/chlimage_1-181.png)

1. Vouw het hulpwerktuig uit en bewerk het opnieuw.

### Inhoud goedkeuren in AEM {#approving-content-in-aem}

Nadat de inhoud is voltooid, kunt u het goedkeuringsproces starten. Ga naar het tabblad **Workflow** van de gereedschapset en selecteer de workflow **Goedkeuren voor Adobe-campagne** .

Deze out-of-the-box workflow bestaat uit twee stappen: herziening dan goedkeuring, of herziening dan verwerping. Deze workflow kan echter worden uitgebreid en aangepast aan een complexer proces.

![chlimage_1-182](assets/chlimage_1-182.png)

Als u inhoud voor Adobe Campaign wilt goedkeuren, past u de workflow toe door **Workflow** in het hulpprogramma te selecteren, **Goedkeuren voor Adobe Campagne** te selecteren en op Workflow **** starten te klikken. Doorloop de stappen en keur de inhoud goed. U kunt de inhoud ook afwijzen door **Afwijzen** te selecteren in plaats van **Goedkeuren** in de laatste workflowstap.

![chlimage_1-183](assets/chlimage_1-183.png)

Nadat de inhoud is goedgekeurd, wordt deze weergegeven als goedgekeurd in Adobe Campaign. Het e-mailbericht kan vervolgens worden verzonden.

In Adobe Campaign Standard:

![chlimage_1-184](assets/chlimage_1-184.png)

In Adobe-campagne 6.1:

![chlimage_1-185](assets/chlimage_1-185.png)

>[!NOTE]
>
>Niet-goedgekeurde inhoud kan worden gesynchroniseerd met een levering in Adobe Campaign, maar de levering kan niet worden uitgevoerd. Alleen goedgekeurde inhoud kan via campagneleveringen worden verzonden.

## AEM koppelen met Adobe Campaign Standard en Adobe Campagne 6.1 {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign}

>[!NOTE]
>
>Zie AEM [koppelen aan Adobe Campagne Standard en Adobe Campagne 6.1](/help/sites-authoring/campaign.md#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic) onder [Werken met Adobe Campagne 6.1 en Adobe Campagne Standard](/help/sites-authoring/campaign.md) in de standaarddocumentatie voor het schrijven van programmacode voor meer informatie.

