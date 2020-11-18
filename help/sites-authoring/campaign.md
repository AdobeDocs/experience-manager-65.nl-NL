---
title: Werken met Adobe Campaign Classic en Adobe Campaign Standard
seo-title: Werken met Adobe Campaign 6.1 en Adobe Campaign Standard
description: U kunt e-mailinhoud maken in AEM en deze verwerken in Adobe Campaign-e-mails
seo-description: U kunt e-mailinhoud maken in AEM en deze verwerken in Adobe Campaign-e-mails
uuid: 23195f0b-71c0-4554-8c8b-b0e7704d71d7
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 2fd0047d-d0f6-4289-98cf-454486f9cd61
translation-type: tm+mt
source-git-commit: 69226ffeb79e0b425b28456cbc64192432863f5d
workflow-type: tm+mt
source-wordcount: '2780'
ht-degree: 0%

---


# Werken met Adobe Campaign Classic en Adobe Campaign Standard{#working-with-adobe-campaign-classic-and-adobe-campaign-standard}

U kunt e-mailinhoud maken in AEM en deze verwerken in Adobe Campaign-e-mails. Daartoe moet u:

1. Maak een nieuwe nieuwsbrief in AEM van een Adobe Campaign-specifieke sjabloon.
1. Selecteer [een Adobe Campaign-service](#selecting-the-adobe-campaign-cloud-service-and-template) voordat u de inhoud gaat bewerken om toegang te krijgen tot alle functies.
1. Bewerk de inhoud.
1. Valideer de inhoud.

Inhoud kan vervolgens worden gesynchroniseerd met een levering in Adobe Campaign. In dit document worden gedetailleerde instructies beschreven.

Zie ook Adobe Campaign Forms [maken in AEM](/help/sites-authoring/adobe-campaign-forms.md).

>[!NOTE]
>
>Voordat u deze functionaliteit kunt gebruiken, moet u AEM configureren voor integratie met [Adobe Campaign](/help/sites-administering/campaignonpremise.md) of [Adobe Campaign Standard](/help/sites-administering/campaignstandard.md).

## E-mailinhoud verzenden via Adobe Campaign {#sending-email-content-via-adobe-campaign}

Nadat u AEM en Adobe Campaign hebt geconfigureerd, kunt u rechtstreeks in AEM inhoud voor e-maillevering maken en deze vervolgens in Adobe Campaign verwerken.

Wanneer u Adobe Campaign-inhoud maakt in AEM, moet u een koppeling maken naar een Adobe Campaign-service voordat u de inhoud bewerkt, zodat u toegang hebt tot alle functies.

Er zijn twee mogelijke gevallen:

* Inhoud kan worden gesynchroniseerd met een levering vanuit Adobe Campaign. Zo kunt u AEM inhoud in een levering gebruiken.
* (Alleen Adobe Campaign Classic) De inhoud kan rechtstreeks naar Adobe Campaign worden verzonden, waardoor automatisch een nieuwe e-maillevering wordt gegenereerd. Deze modus heeft beperkingen.

In dit document worden gedetailleerde instructies beschreven.

### Nieuwe e-mailinhoud maken {#creating-new-email-content}

>[!NOTE]
>
>Als u e-mailsjablonen toevoegt, moet u deze toevoegen onder **/inhoud/campagnes** om ze beschikbaar te maken.


#### Nieuwe e-mailinhoud maken {#creating-new-email-content-1}

1. Selecteer **Sites** en vervolgens **Campagnes** in AEM en blader naar de locatie waar uw e-mailcampagnes worden beheerd. In het volgende voorbeeld is het pad **Sites** > **Campagnes** > **Geometrixx Outdoors** > **E-mailcampagnes**.

   >[!NOTE]
   >
   >[E-mailvoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md). Download voorbeeldinhoud van Geometrixx uit Pakket delen.

   ![chlimage_1-15](assets/chlimage_1-15a.png)

1. Selecteer **Maken** en **Pagina** maken.
1. Selecteer een van de beschikbare sjablonen die specifiek zijn voor de Adobe Campaign waarmee u verbinding maakt en klik op **Volgende**. Er zijn standaard drie sjablonen beschikbaar:

   * **Adobe Campaign Classic-e-mail**: Hiermee kunt u inhoud toevoegen aan een vooraf gedefinieerde sjabloon (twee kolommen) voordat u deze naar Adobe Campaign Classic verzendt voor levering.
   * **Adobe Campaign Standard-e-mail**: Hiermee kunt u inhoud toevoegen aan een vooraf gedefinieerde sjabloon (twee kolommen) voordat u deze naar Adobe Campaign Standard verzendt voor levering.

1. Vul de **Titel** en eventueel de **Beschrijving** in en klik **creëren**. De titel wordt gebruikt als het onderwerp van de nieuwsbrief/e-mail, tenzij u deze overschrijft tijdens het bewerken van de e-mail.

### De Adobe Campaign-cloudservice en -sjabloon selecteren {#selecting-the-adobe-campaign-cloud-service-and-template}

Voor integratie met Adobe Campaign moet u een Adobe Campaign-cloudservice aan de pagina toevoegen. Zo hebt u toegang tot personalisatie en andere Adobe Campaign-gegevens.

Daarnaast moet u mogelijk ook de Adobe Campaign-sjabloon selecteren en het onderwerp wijzigen en onbewerkte tekstinhoud toevoegen voor gebruikers die de e-mail niet in HTML zullen bekijken.

U kunt de cloudservice selecteren op het tabblad **Sites** of vanuit de e-mail/nieuwsbrief nadat u deze hebt gemaakt.

U kunt het beste de cloudservice selecteren op het tabblad **Sites** . Voor het selecteren van de cloudservice in de e-mail/nieuwsbrief is een oplossing nodig.

Van de **pagina van Plaatsen** :

1. Selecteer AEM e-mailpagina en klik op Eigenschappen **** weergeven.

   ![chlimage_1-16](assets/chlimage_1-16a.png)

1. Selecteer **Bewerken** en vervolgens het tabblad **Cloudservices** . Blader omlaag naar de onderkant en klik op + om een configuratie toe te voegen en selecteer **Adobe Campaign**.

   ![chlimage_1-17](assets/chlimage_1-17a.png)

1. Selecteer in de vervolgkeuzelijst de configuratie die overeenkomt met uw Adobe Campaign-instantie en klik op **Opslaan**.
1. U kunt de sjabloon weergeven die de e-mail erop heeft toegepast door op **het tabblad Campagne** van Adobe te klikken. Als u een andere sjabloon wilt selecteren, hebt u tijdens het bewerken toegang tot de sjabloon in de e-mail.

   Als u een specifieke sjabloon voor e-maillevering (vanuit Adobe Campaign) wilt toepassen, anders dan de standaardsjabloon voor e-mail, selecteert u in **Eigenschappen** het tabblad **Adobe Campaign** . Voer de interne naam van de e-mailleveringssjabloon in het gerelateerde Adobe Campaign-exemplaar in.

   Welke sjabloon u selecteert, bepaalt welke aanpassingsvelden beschikbaar zijn in Adobe Campaign.

   ![chlimage_1-18](assets/chlimage_1-18a.png)

Vanuit de nieuwsbrief/e-mail in de ontwerpfase kunt u de configuratie van de Adobe Campaign-cloudservice mogelijk niet selecteren in **Pagina-eigenschappen** vanwege een lay-outprobleem. U kunt de hier beschreven tijdelijke oplossing gebruiken:

1. Selecteer AEM e-mailpagina en klik op **Bewerken**. Klik op Eigenschappen **** openen.

   ![chlimage_1-19](assets/chlimage_1-19a.png)

1. Selecteer **Cloud-services** en klik op **+** om een configuratie toe te voegen. Selecteer om het even welke zichtbare configuratie (maakt niet uit welke). Klik of tik op het **+** -teken om een andere configuratie toe te voegen en selecteer vervolgens **Adobe Campaign**.

   >[!NOTE]
   >
   >U kunt ook de cloudservices selecteren door Eigenschappen **** weergeven te selecteren op het tabblad **Sites** .

1. Selecteer in de vervolgkeuzelijst de configuratie die overeenkomt met uw Adobe Campaign-instantie, verwijder de eerste configuratie die u hebt gemaakt en die niet voor Adobe Campaign was, en bevestig vervolgens door op het vinkje te klikken.
1. Ga verder met stap 4 in de vorige procedure om sjablonen te selecteren en onbewerkte tekst toe te voegen.

### E-mailinhoud bewerken {#editing-email-content}

E-mailinhoud bewerken:

1. Open het e-mailbericht en ga standaard naar de modus Bewerken.

   ![chlimage_1-20](assets/chlimage_1-20a.png)

1. Als u het onderwerp van de e-mail wilt wijzigen of onbewerkte tekst wilt toevoegen voor gebruikers die de e-mail niet in HTML zullen weergeven, selecteert u **E-mail** en voegt u een onderwerp en tekst toe. Selecteer het paginapictogram om automatisch een versie van onbewerkte tekst te genereren vanuit HTML. Klik op het vinkje als u klaar bent.

   U kunt de nieuwsbrief personaliseren door de gebieden van de verpersoonlijking van Adobe Campaign te gebruiken. Als u een verpersoonlijkingsveld wilt toevoegen, opent u de kiezer van het verpersoonlijkingsveld door te klikken op de knop met het Adobe Campaign-logo. Vervolgens kunt u kiezen uit alle velden die beschikbaar zijn voor deze nieuwsbrief.

   >[!NOTE]
   >
   >Als de verpersoonlijkingsgebieden in eigenschappen van binnen de redacteur grayed zijn, gelieve uw configuratie opnieuw te onderzoeken.

   ![chlimage_1-29](assets/chlimage_1-21a.png)

1. Open het deelvenster Componenten links van het scherm en selecteer **Adobe Campaign Newsletter** in het keuzemenu om die componenten te zoeken.

   ![chlimage_1-22](assets/chlimage_1-22a.png)

1. Sleep componenten rechtstreeks naar de pagina en bewerk ze dienovereenkomstig. U kunt bijvoorbeeld een component **Tekst en personalisatie (Campagne)** slepen en gepersonaliseerde tekst toevoegen.

   ![chlimage_1-23](assets/chlimage_1-23a.png)

   Zie [Adobe Campaign Components](/help/sites-authoring/adobe-campaign-components.md) voor een gedetailleerde beschrijving van elke component.

   ![chlimage_1-24](assets/chlimage_1-24a.png)

### Personalisatie invoegen {#inserting-personalization}

Wanneer u de inhoud bewerkt, kunt u het volgende invoegen:

* Adobe Campaign-contextvelden. Dit zijn velden die u in de tekst kunt invoegen en die worden aangepast aan de gegevens van de ontvanger (bijvoorbeeld voornaam, achternaam of gegevens van de doeldimensie).
* Adobe Campaign-verpersoonlijkingsblokken. Dit zijn blokken vooraf gedefinieerde inhoud die niet gerelateerd zijn aan de gegevens van de ontvanger, zoals een merklogo of een koppeling naar een spiegel.

Zie [Adobe Campaign Components](/help/sites-authoring/adobe-campaign-components.md) voor een volledige beschrijving van de campagnecomponenten.

>[!NOTE]
>
>* Alleen de velden van de Adobe Campaign- **profielen** voor dimensie worden in aanmerking genomen.
>* Wanneer u Eigenschappen van **sites** weergeeft, hebt u geen toegang tot de Adobe Campaign-contextvelden. U kunt deze rechtstreeks vanuit de e-mail openen tijdens het bewerken.

>



Personalisatie invoegen:

1. Voeg een nieuwe **component Newsletter** > **Tekst en personalisatie (Campagne)** in door het op de pagina te slepen.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Open de component door op het potloodpictogram te klikken. De editor Inplace wordt geopend.

   ![chlimage_1-26](assets/chlimage_1-26a.png)

   >[!NOTE]
   >
   >**Voor Adobe Campaign Standard:**
   >
   >* Beschikbare contextvelden komen overeen met de **profielen** die zich richten op dimensie in Adobe Campaign.
   >* Zie Een AEM [koppelen aan een Adobe Campaign-e-mail](#linking-an-aem-page-to-an-adobe-campaign-email-adobe-campaign-standard).

   >
   >**Voor Adobe Campaign Classic:**
   >
   >* Beschikbare contextvelden worden dynamisch hersteld via het schema Adobe Campaign **nms:seedMember** . De gegevens van de doelextensie worden dynamisch hersteld vanuit de workflow die de levering bevat die met de inhoud is gesynchroniseerd. (Zie de sectie [Inhoud synchroniseren die is gemaakt in AEM met een levering vanuit Adobe Campaign](#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic) .)
      >
      >
   * Om verpersoonlijkingselementen toe te voegen of te verbergen, zie het [Leiden verpersoonlijkingsgebieden en blokken](/help/sites-administering/campaignonpremise.md#managing-personalization-fields-and-blocks).
   >* **Belangrijk**: Alle velden voor zaadtabellen moeten ook in de ontvangende tabel (of de overeenkomstige contacttabel) staan.


1. Voeg tekst in door te typen. Voeg contextgebieden of verpersoonlijkingsblokken in door de componenten van Adobe Campaign te klikken en hen te selecteren. Selecteer het vinkje als u klaar bent.

   ![chlimage_1-27](assets/chlimage_1-27a.png)

   Nadat u contextvelden of aanpassingsblokken hebt ingevoegd, kunt u een voorvertoning van uw nieuwsbrief bekijken en uw velden testen. Zie Een [nieuwsbrief](#previewing-a-newsletter)voorvertonen.

### Een voorvertoning van een nieuwsbrief weergeven {#previewing-a-newsletter}

U kunt een voorvertoning weergeven van de weergave van de nieuwsbrief en een voorvertoning van de personalisatie bekijken.

1. Open de nieuwsbrief en klik op **Voorvertoning** in de rechterbovenhoek van AEM. AEM toont hoe de nieuwsbrief kijkt wanneer de gebruikers het ontvangen.

   ![chlimage_1-28](assets/chlimage_1-28a.png)

   >[!NOTE]
   >
   >Als u Adobe Campaign Standard gebruikt en de voorbeeldsjabloon gebruikt, zullen twee verpersoonlijkingsblokken met initiële inhoud - **&quot;&lt;%@ include view=&quot;MirrorPage&quot; %>&quot;** en **&quot;&lt;%@ include view=&quot;UnsubscriptionLink&quot; %>&quot;** - fouten genereren bij het importeren van de inhoud tijdens de levering. U kunt deze aanpassen door de corresponderende blokken te selecteren met de kiezer voor het aanpassingsblok.

1. Om voorproef de verpersoonlijking, open ContextHub door het overeenkomstige pictogram in de toolbar te klikken of te tikken. De codes van het verpersoonlijkingsgebied worden nu vervangen door de zaadgegevens van de geselecteerde persoonlijkheid. Zie hoe de variabelen aanpassen wanneer het schakelen personas in ContextHub.

   ![chlimage_1-29](assets/chlimage_1-29a.png)

1. U kunt de zaadgegevens van Adobe Campaign bekijken die aan de momenteel geselecteerde persoon worden geassocieerd. Om dit te doen, klik/tik de module van Adobe Campaign in de bar ContextHub. Hiermee wordt een dialoogvenster geopend waarin alle zaadgegevens van het huidige profiel worden weergegeven. De gegevens worden opnieuw aangepast wanneer naar een andere persoon wordt overgeschakeld.

   ![chlimage_1-30](assets/chlimage_1-30a.png)

### Inhoud in AEM goedkeuren {#approving-content-in-aem}

Nadat de inhoud is voltooid, kunt u het goedkeuringsproces starten. Ga naar het tabblad **Workflow** van de gereedschapset en selecteer de workflow **Goedkeuren voor Adobe Campaign** .

Deze out-of-the-box workflow bestaat uit twee stappen: herziening dan goedkeuring, of herziening dan verwerping. Deze workflow kan echter worden uitgebreid en aangepast aan een complexer proces.

![chlimage_1-31](assets/chlimage_1-31a.png)

Als u inhoud voor Adobe Campaign wilt goedkeuren, past u de workflow toe door **Workflow** te selecteren en **Goedkeuren voor Adobe Campaign** te selecteren en op Workflow **** starten te klikken. Doorloop de stappen en keur de inhoud goed. U kunt de inhoud ook afwijzen door **Afwijzen** te selecteren in plaats van **Goedkeuren** in de laatste workflowstap.

![chlimage_1-32](assets/chlimage_1-32a.png)

Nadat de inhoud is goedgekeurd, wordt deze weergegeven als goedgekeurd in Adobe Campaign. Het e-mailbericht kan vervolgens worden verzonden.

In Adobe Campaign Standard:

![chlimage_1-33](assets/chlimage_1-33a.png)

In Adobe Campaign Classic:

![chlimage_1-34](assets/chlimage_1-34a.png)

>[!NOTE]
Niet-goedgekeurde inhoud kan worden gesynchroniseerd met een levering in Adobe Campaign, maar de levering kan niet worden uitgevoerd. Alleen goedgekeurde inhoud kan via campagneleveringen worden verzonden.

## AEM met Adobe Campaign Standard en Adobe Campaign Classic {#linking-aem-with-adobe-campaign-standard-and-adobe-campaign-classic}

Hoe u AEM met Adobe Campaign koppelt of synchroniseert, hangt af van het feit of u Adobe Campaign Standard op abonnementsbasis of Adobe Campaign Classic op locatie gebruikt.

Zie de volgende secties voor instructies die op uw oplossing van Adobe Campaign worden gebaseerd:

* [Een AEM pagina koppelen aan een Adobe Campaign-e-mail (Adobe Campaign Standard)](#linking-an-aem-page-to-an-adobe-campaign-email-adobe-campaign-standard)
* [In AEM gemaakte inhoud synchroniseren met een levering vanuit Adobe Campaign Classic](#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic)

### Een AEM pagina koppelen aan een Adobe Campaign-e-mail (Adobe Campaign Standard) {#linking-an-aem-page-to-an-adobe-campaign-email-adobe-campaign-standard}

Met Adobe Campaign Standard kunt u inhoud die is gemaakt in AEM herstellen en koppelen met:

* Een e-mail.
* Een e-mailsjabloon.

Zo kunt u de inhoud leveren. U ziet of een nieuwsbrief met één enkele levering door de code verbonden is die op de pagina toont.

![chlimage_1-35](assets/chlimage_1-35a.png)

>[!NOTE]
Als een nieuwsbrief aan verscheidene leveringen wordt verbonden, het aantal verbonden leveringen (maar niet elke identiteitskaart wordt getoond).

Een pagina die is gemaakt in AEM koppelen aan een e-mailbericht van Adobe Campaign:

1. Maak een nieuw e-mailbericht op basis van een AEM-specifieke e-mailsjabloon. Zie E-mails [maken in Adobe Campaign Standard](https://helpx.adobe.com/campaign/standard/channels/using/creating-an-email.html) voor meer informatie.

   ![chlimage_1-36](assets/chlimage_1-36a.png)

1. Open het blok **Inhoud** vanaf het leveringsdashboard.

   ![chlimage_1-37](assets/chlimage_1-37a.png)

1. Selecteer **Koppelen met Adobe Experience Manager-inhoud** op de werkbalk voor toegang tot de inhoudslijst in AEM.

   >[!NOTE]
   Als de optie **Koppelen naar Adobe Experience Manager** niet wordt weergegeven op de actiebalk, controleert u of de modus **** Inhoud bewerken correct is ingesteld op **Adobe Experience Manager** in de e-maileigenschappen.

   ![chlimage_1-38](assets/chlimage_1-38a.png)

1. Selecteer de inhoud die u in uw e-mail wilt gebruiken.

   In deze lijst worden opgegeven:

   * Het label van de inhoud in AEM.
   * De goedkeuringsstatus van de inhoud in AEM. Als de inhoud niet is goedgekeurd, kunt u de inhoud synchroniseren, maar moet deze worden goedgekeurd voordat de levering wordt verzonden. U kunt echter bepaalde bewerkingen uitvoeren, zoals het verzenden van een proefdruk of de voorbeeldtest.
   * De datum van de laatste wijziging van de inhoud.
   * Alle inhoud die al aan een levering is gekoppeld.

   >[!NOTE]
   Standaard is de inhoud die al met een levering is gesynchroniseerd, verborgen. U kunt deze echter wel weergeven en gebruiken. Als u bijvoorbeeld inhoud wilt gebruiken als een sjabloon voor meerdere leveringen.

   Als het e-mailbericht is gekoppeld aan AEM inhoud, kan de inhoud niet worden bewerkt in Adobe Campaign.

1. Geef de andere parameters van de e-mail op vanaf het dashboard (publiek, uitvoeringsschema).
1. Voer de e-maillevering uit. Tijdens de leveringsanalyse, wordt de meest bijgewerkte versie van de AEM inhoud teruggewonnen.

   >[!NOTE]
   Als de inhoud in AEM wordt bijgewerkt terwijl deze aan een e-mailbericht is gekoppeld, wordt deze tijdens de analyse automatisch bijgewerkt in Adobe Campaign. De synchronisatie kan ook handmatig worden uitgevoerd met Adobe Experience Manager-inhoud **** vernieuwen op de actiebalk voor inhoud.
   U kunt de koppeling tussen een e-mail en AEM inhoud annuleren door de koppeling met de Adobe Experience Manager-inhoud **te** verwijderen op de actiebalk voor inhoud. Deze knop is alleen beschikbaar als de inhoud al is gekoppeld aan de levering. Als u een andere inhoud aan een levering wilt koppelen, moet u de huidige inhoudskoppeling verwijderen voordat u een nieuwe koppeling kunt maken.
   Wanneer de koppeling wordt verwijderd, wordt de lokale inhoud bewaard en bewerkbaar in Adobe Campaign. Als u de inhoud opnieuw koppelt nadat u deze hebt gewijzigd, gaan alle wijzigingen verloren.

### In AEM gemaakte inhoud synchroniseren met een levering vanuit Adobe Campaign Classic {#synchronizing-content-created-in-aem-with-a-delivery-from-adobe-campaign-classic}

Met Adobe Campaign kunt u inhoud die is gemaakt in AEM herstellen en synchroniseren met:

* Een campagnelevering
* Een leveringsactiviteit in een campagnewerkstroom
* Een terugkerende levering
* Ononderbroken levering
* Een levering in het Berichtencentrum
* Een leveringssjabloon

Als een nieuwsbrief AEM is gekoppeld aan één levering, wordt de leveringscode weergegeven op de pagina.

![chlimage_1-39](assets/chlimage_1-39a.png)

>[!NOTE]
Als de nieuwsbrief aan verscheidene leveringen wordt gekoppeld, het aantal verbonden leveringen (maar niet elke identiteitskaart wordt getoond).
[!NOTE]
De stap van het Werkschema **publiceert aan Adobe Campaign** is verouderd in AEM 6.1. Deze stap maakte deel uit van de integratie van AEM 6.0 met Adobe Campaign en is niet langer nodig.

Inhoud die is gemaakt in AEM met een levering vanuit Adobe Campaign synchroniseren:

1. Maak een levering of voeg een leveringsactiviteit aan een campagnewerkstroom toe door de **E-maillevering met AEM (mailAEMContent)** leveringsmalplaatje te selecteren.

   ![chlimage_1-40](assets/chlimage_1-40a.png)

1. Selecteer **Synchroniseren** op de werkbalk om de inhoudslijst in AEM te openen.

   >[!NOTE]
   Als de optie **Synchroniseren** niet wordt weergegeven op de werkbalk van de levering, controleert u of het veld **Inhoudsbewerkingsmodus** correct is geconfigureerd in **AEM** door **Eigenschappen** > **Geavanceerd** te selecteren.

   ![chlimage_1-41](assets/chlimage_1-41a.png)

1. Selecteer de inhoud die u met uw levering wilt synchroniseren.

   In deze lijst worden opgegeven:

   * Het label van de inhoud in AEM.
   * De goedkeuringsstatus van de inhoud in AEM. Als de inhoud niet is goedgekeurd, kunt u de inhoud synchroniseren, maar moet deze worden goedgekeurd voordat de levering wordt verzonden. U kunt echter bepaalde bewerkingen uitvoeren, zoals het verzenden van een BBT of de voorvertoningstest.
   * De datum van de laatste wijziging in de inhoud.
   * Alle inhoud die al aan een levering is gekoppeld.

   >[!NOTE]
   Standaard is de inhoud die al met een levering is gesynchroniseerd, verborgen. U kunt deze echter wel weergeven en gebruiken. Als u bijvoorbeeld inhoud wilt gebruiken als een sjabloon voor meerdere leveringen.

   ![chlimage_1-42](assets/chlimage_1-42a.png)

1. Geef de andere parameters voor uw levering op (doel, enz.)
1. Start zo nodig het goedkeuringsproces voor de levering in Adobe Campaign. Goedkeuring van inhoud in AEM is noodzakelijk naast goedkeuringen die in Adobe Campaign zijn geconfigureerd (budget, doel, enz.). Goedkeuring van inhoud in Adobe Campaign is alleen mogelijk als de inhoud al is goedgekeurd in AEM.
1. Voer de levering uit. Tijdens de leveringsanalyse, wordt de meest bijgewerkte versie van de AEM inhoud teruggewonnen.

   >[!NOTE]
   * Nadat de levering en de inhoud zijn gesynchroniseerd, wordt de leveringsinhoud in Adobe Campaign alleen-lezen. Het onderwerp van de e-mail en de inhoud ervan kunnen niet meer worden gewijzigd.
   * Als de inhoud in AEM wordt bijgewerkt terwijl deze aan een levering in Adobe Campaign is gekoppeld, wordt deze tijdens de leveringsanalyse automatisch bijgewerkt in de levering. De synchronisatie kan ook handmatig worden uitgevoerd met de knop Inhoud nu **** vernieuwen.
   * U kunt synchronisatie tussen een levering en AEM inhoud annuleren gebruikend de **Desynchronize** knoop. Dit is alleen beschikbaar als de inhoud al is gesynchroniseerd met de levering. Als u andere inhoud wilt synchroniseren met een levering, moet u de huidige inhoudssynchronisatie annuleren voordat u een nieuwe koppeling kunt maken.
   * Als de synchronisatie van de lokale inhoud is opgeheven, wordt deze bewaard en kan deze worden bewerkt in Adobe Campaign. Als u de inhoud opnieuw synchroniseert nadat u deze hebt gewijzigd, gaan alle wijzigingen verloren.
   * Voor terugkomende en ononderbroken leveringen wordt synchronisatie met AEM inhoud gestopt telkens wanneer de levering wordt uitgevoerd.

