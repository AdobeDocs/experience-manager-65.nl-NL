---
title: Werken met Adobe Campaign 6.1 en Adobe Campaign Standard
seo-title: Werken met Adobe Campaign 6.1 en Adobe Campaign Standard
description: U kunt e-mailinhoud maken in AEM en deze verwerken in Adobe Campaign-e-mails.
seo-description: U kunt e-mailinhoud maken in AEM en deze verwerken in Adobe Campaign-e-mails.
uuid: 439df7fb-590b-45b8-9768-565b022a808b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 61b2bd47-dcef-4107-87b1-6bf7bfd3043b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# Werken met Adobe Campaign 6.1 en Adobe Campaign Standard{#working-with-adobe-campaign-and-adobe-campaign-standard}

U kunt e-mailinhoud maken in AEM en deze verwerken in Adobe Campaign-e-mails. Daartoe moet u:

1. Maak een nieuwe nieuwsbrief in AEM van een Adobe Campaign-specifieke sjabloon.
1. Selecteer [een Adobe Campaign-service](#selectingtheadobecampaigncloudservice) voordat u de inhoud bewerkt om toegang te krijgen tot alle functies.
1. Bewerk de inhoud.
1. Valideer de inhoud.

Inhoud kan vervolgens worden gesynchroniseerd met een levering in Adobe Campaign. In dit document worden gedetailleerde instructies beschreven.

>[!NOTE]
>
>Voordat u deze functionaliteit kunt gebruiken, moet u AEM configureren voor integratie met [Adobe Campaign](/help/sites-administering/campaignonpremise.md) of [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md).

## E-mailinhoud verzenden via Adobe Campaign {#sending-email-content-via-adobe-campaign}

Nadat u AEM en Adobe Campaign hebt geconfigureerd, kunt u rechtstreeks in AEM inhoud voor e-maillevering maken en deze vervolgens in Adobe Campaign verwerken.

Wanneer u Adobe Campaign-inhoud maakt in AEM, moet u een koppeling maken naar een Adobe Campaign-service voordat u de inhoud bewerkt, zodat u toegang hebt tot alle functies.

Er zijn twee mogelijke gevallen:

* Inhoud kan worden gesynchroniseerd met een levering vanuit Adobe Campaign. Zo kunt u AEM inhoud in een levering gebruiken.
* (Alleen Adobe Campaign op locatie) De inhoud kan rechtstreeks naar Adobe Campaign worden verzonden, waardoor automatisch een nieuwe e-maillevering wordt gegenereerd. Deze modus heeft beperkingen.

In dit document worden gedetailleerde instructies beschreven.

### Nieuwe e-mailinhoud maken {#creating-new-email-content}

>[!NOTE]
>
>Wanneer u e-mailsjablonen toevoegt, moet u deze toevoegen onder **/content/campagnes** om ze beschikbaar te maken.


1. Selecteer in AEM de map **Websites** en blader naar de verkenner om te zoeken waar uw e-mailcampagnes worden beheerd. In het volgende voorbeeld is het betrokken knooppunt **Websites** > **Campagnes** > **Geometrixx Outdoors** > **E-mailcampagnes**.

   >[!NOTE]
   >
   >[E-mailvoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md#weretail). Download voorbeeldinhoud van Geometrixx uit Pakket delen.

   ![chlimage_1-172](assets/chlimage_1-172.png)

1. Selecteer **Nieuw** > **Nieuwe pagina** om nieuwe e-mailinhoud te maken.
1. Selecteer een van de beschikbare sjablonen die specifiek zijn voor Adobe Campaign en vul vervolgens de algemene eigenschappen van de pagina in. Er zijn standaard drie sjablonen beschikbaar:

   * **Adobe Campaign-e-mail (AC 6.1)**: Hiermee kunt u inhoud toevoegen aan een vooraf gedefinieerde sjabloon voordat u deze naar Adobe Campaign 6.1 verzendt voor levering.
   * **Adobe Campaign-e-mail (ACS)**: Hiermee kunt u inhoud toevoegen aan een vooraf gedefinieerde sjabloon voordat u deze naar Adobe Campaign Standard verzendt voor levering.

   ![chlimage_1-173](assets/chlimage_1-173.png)

1. Klik **Maken** om uw e-mail of nieuwsbrief te maken.

### De Adobe Campaign-cloudservice en sjabloon {#selecting-the-adobe-campaign-cloud-service-and-template} selecteren

Voor integratie met Adobe Campaign moet u een Adobe Campaign-cloudservice aan de pagina toevoegen. Zo hebt u toegang tot personalisatie en andere Adobe Campaign-gegevens.

Daarnaast moet u mogelijk ook de Adobe Campaign-sjabloon selecteren en het onderwerp wijzigen en onbewerkte tekstinhoud toevoegen voor gebruikers die de e-mail niet in HTML zullen bekijken.

1. Selecteer het tabblad **Pagina** in het zijpaneel en selecteer vervolgens **Pagina-eigenschappen.**
1. Selecteer **Service toevoegen** op het tabblad **Cloudservices** in het pop-upvenster om de Adobe Campaign-service toe te voegen en klik op **OK**.

   ![chlimage_1-174](assets/chlimage_1-174.png)

1. Selecteer in de vervolgkeuzelijst de configuratie die overeenkomt met uw Adobe Campaign-instantie en klik op **OK**.

   >[!NOTE]
   >
   >Tik op **OK** of **Toepassen** nadat u de cloudservice hebt toegevoegd. Hierdoor werkt het tabblad **Adobe Campaign** correct.

1. Als u een specifiek malplaatje van de e-maillevering (van Adobe Campaign), buiten het gebrek **mail** malplaatje zou willen toepassen, selecteer **Pagina eigenschappen** opnieuw. Voer op het tabblad **Adobe Campaign** de interne naam van de sjabloon voor e-maillevering in het gerelateerde Adobe Campaign-exemplaar in.

   In Adobe Campaign Standard is de sjabloon **Levering met AEM Inhoud**. In Adobe Campaign 6.1 is de sjabloon **E-maillevering met AEM inhoud**.

   Als u de sjabloon selecteert, schakelt AEM automatisch de **Adobe Campaign Newsletter**-componenten in.

### E-mailinhoud bewerken {#editing-email-content}

U kunt e-mailinhoud bewerken in de klassieke gebruikersinterface of in de gebruikersinterface met geoptimaliseerde aanrakingen.

1. Voer het onderwerp en de tekstversie van de e-mail in door **Pagina-eigenschappen** > **E-mail** te selecteren in de gereedschapset.

   ![chlimage_1-175](assets/chlimage_1-175.png)

1. Bewerk e-mailinhoud door de elementen toe te voegen die u van de beschikbare elementen in de assistent wilt gebruiken. U doet dit door ze te slepen en neer te zetten. Dubbelklik vervolgens op het element dat u wilt bewerken.

   U kunt bijvoorbeeld tekst toevoegen die verpersoonlijkingsvelden bevat.

   ![chlimage_1-176](assets/chlimage_1-176.png)

   Zie [Adobe Campaign Components](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md) voor een beschrijving van de componenten beschikbaar voor Adobe Campaign-nieuwsbrieven/e-mailcampagnes.

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Aanpassing {#inserting-personalization} invoegen

Wanneer u de inhoud bewerkt, kunt u het volgende invoegen:

* Adobe Campaign-contextvelden. Dit zijn velden die u in de tekst kunt invoegen en die worden aangepast aan de gegevens van de ontvanger (bijvoorbeeld voornaam, achternaam of gegevens van de doeldimensie).
* Adobe Campaign-verpersoonlijkingsblokken. Dit zijn blokken vooraf gedefinieerde inhoud die niet gerelateerd zijn aan de gegevens van de ontvanger, zoals een merklogo of een koppeling naar een spiegel.

Zie [Adobe Campaign Components](/help/sites-classic-ui-authoring/classic-personalization-ac-components.md) voor een volledige beschrijving van de campagnecomponenten.

>[!NOTE]
>
>* Alleen de velden van de Adobe Campaign **Profiles**-doeldimensie worden in aanmerking genomen.
>* Wanneer het bekijken van Eigenschappen van **Sites**, hebt u geen toegang tot de de contextgebieden van Adobe Campaign. U kunt deze rechtstreeks vanuit de e-mail openen tijdens het bewerken.

>



1. Voeg een nieuwe **nieuwsbrief** > **Tekst en personalisatie (Campagne)** component in.
1. Open de component door erop te dubbelklikken. Het **Edit** venster heeft een functionaliteit die u de verpersoonlijkingselementen laat opnemen.

   >[!NOTE]
   >
   >De beschikbare contextgebieden beantwoorden aan **Profielen** richtend dimensie in Adobe Campaign.
   >
   >Zie [Een AEM pagina koppelen aan een Adobe Campaign-e-mail](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#linkinganaempagetoanadobecampaignemail).

   ![chlimage_1-178](assets/chlimage_1-178.png)

1. Selecteer **Clientcontext** in het hulpprogramma om de aanpassingsvelden te testen met behulp van de gegevens in de persoonlijke profielen.

   ![chlimage_1-179](assets/chlimage_1-179.png)

1. Er verschijnt een venster waarin u de persoon kunt selecteren die u bevalt. De verpersoonlijkingsgebieden worden automatisch vervangen door gegevens van het geselecteerde profiel.

   ![chlimage_1-180](assets/chlimage_1-180.png)

### Een nieuwsbrief {#previewing-a-newsletter} voorvertonen

U kunt een voorvertoning weergeven van de weergave van de nieuwsbrief en een voorvertoning van de personalisatie bekijken.

1. Open de nieuwsbrief u voorproef en klik Voorproef (vergrootglas) om hulpdekick te krimpen.
1. Klik op een van de e-mailclientpictogrammen om te zien hoe uw nieuwsbrief er in elke e-mailclient uitziet.

   ![chlimage_1-181](assets/chlimage_1-181.png)

1. Vouw het hulpwerktuig uit en bewerk het opnieuw.

### Inhoud goedkeuren in AEM {#approving-content-in-aem}

Nadat de inhoud is voltooid, kunt u het goedkeuringsproces starten. Ga naar het **Werkstroom** lusje van toolbox en selecteer **goedkeuren voor Adobe Campaign** werkschema.

Deze out-of-the-box workflow bestaat uit twee stappen: herziening dan goedkeuring, of herziening dan verwerping. Deze workflow kan echter worden uitgebreid en aangepast aan een complexer proces.

![chlimage_1-182](assets/chlimage_1-182.png)

Als u inhoud voor Adobe Campaign wilt goedkeuren, past u de workflow toe door **Workflow** in de assistent te selecteren en **Goedkeuren voor Adobe Campaign** te selecteren en op **Workflow starten** te klikken. Doorloop de stappen en keur de inhoud goed. U kunt de inhoud ook afwijzen door **Afwijzen** te selecteren in plaats van **Goedkeuren** in de laatste workflowstap.

![chlimage_1-183](assets/chlimage_1-183.png)

Nadat de inhoud is goedgekeurd, wordt deze weergegeven als goedgekeurd in Adobe Campaign. Het e-mailbericht kan vervolgens worden verzonden.

In Adobe Campaign Standard:

![chlimage_1-184](assets/chlimage_1-184.png)

In Adobe Campaign 6.1:

![chlimage_1-185](assets/chlimage_1-185.png)

>[!NOTE]
>
>Niet-goedgekeurde inhoud kan worden gesynchroniseerd met een levering in Adobe Campaign, maar de levering kan niet worden uitgevoerd. Alleen goedgekeurde inhoud kan via campagneleveringen worden verzonden.

## AEM koppelen met Adobe Campaign Standard en Adobe Campaign 6.1 {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign}

>[!NOTE]
>
>Zie [AEM koppelen met Adobe Campaign Standard en Adobe Campaign 6.1](/help/sites-authoring/campaign.md#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic) onder [Werken met Adobe Campaign 6.1 en Adobe Campaign Standard](/help/sites-authoring/campaign.md) in de standaard ontwerpdocumentatie voor meer informatie.

