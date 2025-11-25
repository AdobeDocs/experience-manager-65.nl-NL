---
title: Doelinhoud ontwerpen met doelmodus
description: De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor ervaringen te creëren
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
docset: aem65
exl-id: edde225d-0be7-4306-8dda-d18d46fae977
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '5284'
ht-degree: 4%

---

# Doelinhoud ontwerpen met doelmodus{#authoring-targeted-content-using-targeting-mode}

Maak specifieke inhoud met de modus Doel van AEM. De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor ervaringen tot stand te brengen:

* Herken eenvoudig de doelinhoud op de pagina. Een stippellijn vormt een rand rondom alle doelinhoud.
* Selecteer een merk en een activiteit om de ervaringen te bekijken.
* Ervaringen toevoegen aan een activiteit of ervaringen verwijderen.
* A/B-tests uitvoeren en winnaars converteren (alleen Adobe Target).
* Voeg aanbiedingen toe aan een ervaring door aanbiedingen te maken of aanbiedingen uit een bibliotheek te gebruiken.
* Vorm doelstellingen en controleer prestaties.
* Simuleer de gebruikerservaring.
* Voor meer aanpassing, vorm de component van het Doel.

U kunt AEM of Adobe Target gebruiken als de doelengine (u moet over een geldige Adobe Target-account beschikken om Adobe Target te kunnen gebruiken). Als u Adobe Target gebruikt, moet u eerst de integratie configureren. Zie [&#x200B; instructies voor het integreren met Adobe Target &#x200B;](/help/sites-administering/target.md).

![&#x200B; chlimage_1-8 &#x200B;](assets/chlimage_1-8.png)

De activiteiten en de ervaringen die u op de wijze van het Doel ziet wijzen op de [&#x200B; console van Activiteiten &#x200B;](/help/sites-authoring/activitylib.md):

* Wijzigingen die u aanbrengt in activiteiten en ervaringen die gebruikmaken van de modus Doel, worden weerspiegeld in de console Activiteiten.
* De veranderingen die in de console van Activiteiten worden aangebracht worden weerspiegeld in het richten wijze.

>[!NOTE]
>
>Wanneer u een campagne in Adobe Target creeert, wijst het een bezit genoemd `thirdPartyId` aan elke campagne toe. Wanneer u de campagne in Adobe Target verwijdert, wordt de thirdPartyId niet verwijderd. U kunt `thirdPartyId` niet opnieuw gebruiken voor campagnes van verschillende types (AB, XT) en het kan niet manueel worden verwijderd. Om dit probleem te voorkomen, geeft u elke campagne een unieke naam. U kunt de campagnemenamen niet opnieuw gebruiken in verschillende typen campagnes.
>
>Als u dezelfde naam gebruikt in hetzelfde type campagne, overschrijft u de bestaande campagne.
>
>Als tijdens het synchroniseren de fout &quot;Verzoek is mislukt. `thirdPartyId` bestaat al.&quot; Wijzig de naam van de campagne en synchroniseer opnieuw.

>[!NOTE]
>
>Wanneer het richten, blijft de branding en activiteitencombinatie op het gebruikersniveau niet op kanaalniveau voortbestaan.

## Schakelen naar doelmodus {#switching-to-targeting-mode}

Schakel over naar de modus Doel om toegang te krijgen tot de gereedschappen voor het ontwerpen van doelinhoud.

Ga naar de modus Doel:

1. Open de pagina waarvoor u doelinhoud wilt ontwerpen.
1. Klik op de werkbalk boven aan de pagina op de vervolgkeuzelijst Modus om de beschikbare modustypen weer te geven.

   ![&#x200B; chlimage_1-9 &#x200B;](assets/chlimage_1-9.png)

1. Klik **het richten**. De doelopties worden boven aan de pagina weergegeven.

   ![&#x200B; chlimage_1-10 &#x200B;](assets/chlimage_1-10.png)

## Een activiteit toevoegen met de doelmodus {#adding-an-activity-using-targeting-mode}

Gebruik de modus Doel om een activiteit aan een merk toe te voegen. Wanneer u een activiteit toevoegt, bevat het de Standaardervaring. Nadat u de activiteit hebt toegevoegd, start u het proces voor het toewijzen van inhoud voor de activiteit.

U kunt ook Adobe Target-activiteiten vanuit AEM maken en beheren met de optie AEM of Adobe Target (doelengine) en het type activiteit selecteren (Experience Targeting of A/B Test).

Bovendien kunt u doelstellingen en maatstaven voor alle Adobe Target-activiteiten beheren en uw Adobe Target-publiek beheren. Er wordt ook melding gemaakt van Adobe Target-activiteiten, waaronder het converteren van winnaars voor A/B-tests.

Wanneer u een activiteit toevoegt, verschijnt het ook in de [&#x200B; console van Activiteiten &#x200B;](/help/sites-authoring/activitylib.md).

Een activiteit toevoegen:

1. Gebruik het **Merk** drop-down menu om het merk te selecteren waarvoor u de activiteit wilt tot stand brengen.

   >[!NOTE]
   >
   >Adobe adviseert dat u [&#x200B; merken door de activiteitenconsole &#x200B;](/help/sites-authoring/activitylib.md#creating-a-brand-using-the-activities-console) creeert.
   >
   >
   >Als u een merk op een andere manier maakt, moet u controleren of het knooppunt `/campaigns/<brand>/master` bestaat of dat een fout optreedt wanneer u een activiteit wilt maken.

1. Klik + naast het **drop-down menu van de Activiteit**.
1. Typ een naam voor de activiteit.

   >[!NOTE]
   >
   >Wanneer u een activiteit creeert en een de wolkenconfiguratie van Adobe Target verbonden aan de pagina of één van zijn ouder hebt, veronderstelt AEM automatisch Adobe Target als motor.

1. In het **richten** motor drop-down menu, selecteer uw het richten motor.

   * Als u **ContextHub AEM** selecteert, worden de resterende gebieden gedimd en niet beschikbaar. Klik **creëren**.

   * Als u **Adobe Target** selecteert, kunt u een configuratie (door gebrek selecteren, is het de configuratie u verstrekte toen u [&#x200B; de rekening &#x200B;](/help/sites-administering/opt-in.md)) en het Type van Activiteit vormde.

   * Als u de integratie AEM/Adobe Campaign gebruikt en gerichte inhoud (nieuwsbrieven) verzendt, uitgezochte **Adobe Campaign**. Zie [&#x200B; Integrerend met Adobe Campaign &#x200B;](/help/sites-administering/campaign.md) voor meer informatie.

1. In het menu van de Activiteit, selecteer of **Ervaring richtend** of **Test A/B**.

   * Ervaring gericht op het beheren van Adobe Target-activiteiten vanuit AEM.
   * A/B-test - A/B-testactiviteiten maken/beheren in Adobe Target vanuit AEM.

## Het doelproces: Maken, Doel en Doelen &amp; Instellingen {#the-targeting-process-create-target-and-goals-settings}

De gerichte wijze laat u toe om verscheidene aspecten van een activiteit te vormen. Gebruik het volgende proces in drie stappen voor het maken van gerichte inhoud voor een merkactiviteit:

1. [&#x200B; creeer &#x200B;](#create-authoring-the-experiences): Voeg of verwijder ervaringen toe, en voeg aanbiedingen voor elke ervaring toe.
1. [&#x200B; Doel &#x200B;](#diagramtargetconfiguringtheaudiences): Specificeer het publiek dat elke ervaringsdoelstellingen. U kunt een specifiek publiek richten en als het gebruiken van het testen A/B beslist welk percentage van verkeer naar welke ervaring gaat.
1. [&#x200B; Doelen &amp; Montages &#x200B;](#settingsgoalssettingsconfiguringtheactivityandsettinggoals): Plan de activiteit en plaats de prioriteit. U kunt succes metrische doelstellingen ook plaatsen.

Gebruik de volgende procedure om het doelproces voor inhoud voor een activiteit te starten.

>[!NOTE]
>
>Om het het richten proces te gebruiken, moet u een lid van de de gebruikersgroep van de Auteurs van de Activiteit van het Doel zijn.

Een activiteit toevoegen:

1. In het **Merk** drop-down menu, selecteer het merk dat de activiteit bevat die u aan werkt.
1. In het **drop-down menu van de Activiteit**, selecteer de activiteit waarvoor u gerichte inhoud creeert.
1. Om de controles te openbaren die u door het richten proces begeleiden, klik **Beginnen richtend**.

   ![&#x200B; chlimage_1-11 &#x200B;](assets/chlimage_1-11.png)

   >[!NOTE]
   >
   >Om de activiteit te veranderen waarmee u werkt, klik **terug**.

## Maken: de ervaringen ontwerpen {#create-authoring-the-experiences}

Bij het maken van inhoud als doel gaat het om het maken van ervaringen. Tijdens deze stap kunt u de ervaringen van de activiteit creëren of schrappen, en aanbiedingen toevoegen aan elke ervaring.

### Weergaveervaring biedt in doelmodus {#seeing-experience-offers-in-targeting-mode}

Nadat u [&#x200B; het richten proces &#x200B;](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) begint, selecteer een ervaring om de aanbiedingen te zien die voor die ervaring worden verstrekt. Wanneer u een ervaring selecteert, veranderen de doelcomponenten op de pagina om de aanbieding voor die ervaring te tonen.

>[!CAUTION]
>
>Wees voorzichtig wanneer u het richten voor een component onbruikbaar maakt die reeds in de auteursinstantie gericht is. De respectievelijke activiteit wordt automatisch ook uit de publicatie-instantie verwijderd.

>[!NOTE]
>
>Een aanbieding is de inhoud van een doelcomponent.

De ervaringen worden weergegeven in het deelvenster Doelgroep. In het volgende voorbeeld zijn de ervaringen **Standaard**, **Vrouwelijk**, **Vrouwelijk ouder dan 30** en **Vrouwelijk jonger dan 30**. In dit voorbeeld wordt het standaardaanbod van een beoogde **afbeeldingscomponent** getoond.

![&#x200B; chlimage_1-12 &#x200B;](assets/chlimage_1-12.png)

Wanneer u een andere ervaring hebt geselecteerd, wordt in de component Image het aanbod voor die ervaring weergegeven.

![&#x200B; chlimage_1-13 &#x200B;](assets/chlimage_1-13.png)

Wanneer een ervaring wordt geselecteerd en de doelcomponent geen aanbieding voor die ervaring omvat, toont de component **Aanbieding toevoegen** bovenop de semitransparante standaardaanbieding. Wanneer geen aanbieding voor een ervaring is gecreëerd, wordt de **Standaardaanbieding** getoond voor het segment dat aan de ervaring is toegewezen.

![&#x200B; chlimage_1-14 &#x200B;](assets/chlimage_1-14.png)

De ervaring Standaard wordt ook weergegeven wanneer de eigenschappen van de bezoeker niet overeenkomen met segmenten die aan de ervaringen zijn toegewezen. Zie [&#x200B; Toevoegende Ervaringen gebruikend het richten Wijze &#x200B;](#adding-and-removing-experiences-using-targeting-mode).

### Aangepaste aanbiedingen en bibliotheekaanbiedingen {#custom-offers-and-library-offers}

Aanbiedingen die [&#x200B; worden authored op de pagina &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) en voor één enkele ervaring worden gebruikt worden genoemd douaneaanbiedingen. De volgende afbeelding wordt over de inhoud van een aangepaste aanbieding heen geplaatst:

![&#x200B; chlimage_1-15 &#x200B;](assets/chlimage_1-15.png)

Aanbiedingen die [&#x200B; van een aanbiedingsbibliotheek &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library) worden toegevoegd worden overschreven met het volgende beeld:

![&#x200B; chlimage_1-16 &#x200B;](assets/chlimage_1-16.png)

U kunt aangepaste voorstellen opslaan in een aanbiedingsbibliotheek als u besluit dat u deze opnieuw wilt gebruiken. U kunt een bibliotheekaanbieding in een douaneaanbieding ook omzetten als u de inhoud voor een ervaring wilt wijzigen. Na het bewerken kunt u de aanbieding opnieuw opslaan in de bibliotheek.

### Ervaringen toevoegen en verwijderen met de doelmodus {#adding-and-removing-experiences-using-targeting-mode}

Gebruikend de Create stap van [&#x200B; het richten proces &#x200B;](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings), kunt u ervaringen toevoegen en verwijderen. Bovendien kunt u een ervaring dupliceren en ook de naam ervan wijzigen.

#### Ervaringen toevoegen met de doelmodus {#adding-experiences-using-targeting-mode}

Een ervaring toevoegen:

1. Om een ervaring toe te voegen, klik **+** **voeg Ervaring het richten** toe die onder bestaande ervaringen in de **ruit van het publiek** verschijnt.
1. Selecteer en publiek. Standaard is die naam de naam van de ervaring. U kunt desgewenst een andere naam typen. Klik **OK**.

#### Ervaringen verwijderen met de doelmodus {#removing-experiences-using-targeting-mode}

Een ervaring verwijderen:

1. Klik op de pijl naast de naam van de ervaring.

   ![&#x200B; chlimage_1-17 &#x200B;](assets/chlimage_1-17.png)

1. Klik **Schrapping**.

#### Ervaringen hernoemen met doelmodus {#renaming-experiences-using-targeting-mode}

Ervaringen een andere naam geven in de doelmodus:

1. Klik op de pijl naast de naam van de ervaring.
1. Klik **anders noemen Ervaring** en type in de nieuwe naam.
1. Klik ergens anders op het scherm om de wijzigingen op te slaan.

#### Soorten publiek bewerken met doelmodus {#editing-audiences-using-targeting-mode}

U kunt als volgt het publiek bewerken in de doelmodus:

1. Klik op de pijl naast de naam van de ervaring.
1. Klik **uitgeven Publiek** en selecteer een nieuw publiek.
1. Klik **OK**.

#### Dubbele ervaringen met de doelmodus {#duplicating-experiences-using-targeting-mode}

Ervaringen kopiëren met de doelmodus:

1. Klik op de pijl naast de naam van de ervaring.
1. Klik **Dupliceren** en kies het publiek.
1. Wijzig de naam van de ervaring, indien gewenst, en klik **O.K.**.

### Aanbiedingen maken met de doelmodus {#creating-offers-using-targeting-mode}

Kies een component om aanbiedingen voor ervaringen te maken. De gerichte componenten verstrekken de inhoud die als aanbiedingen voor ervaringen wordt gebruikt.

* [&#x200B; Doel een bestaande component &#x200B;](/help/sites-authoring/content-targeting-touch.md#creating-a-default-offer-by-targeting-an-existing-component). De inhoud wordt de standaardervaring.
* [&#x200B; voeg een component van het Doel &#x200B;](/help/sites-authoring/content-targeting-touch.md#creating-an-offer-by-adding-a-target-component) toe, dan voeg inhoud aan de component toe.

Nadat een component is aangewezen, kunt u aanbiedingen voor elke ervaring toevoegen:

* [&#x200B; voeg douaneaanbiedingen &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) toe.
* [&#x200B; voegt aanbiedingen van een bibliotheek &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library) toe.

De volgende gereedschappen zijn beschikbaar voor het werken met aanbiedingen:

* [&#x200B; voeg een douaneaanbieding aan een aanbiedingsbibliotheek &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer-to-a-library) toe.
* [&#x200B; zet een bibliotheekaanbieding in een douaneaanbieding &#x200B;](/help/sites-authoring/content-targeting-touch.md#converting-a-library-offer-to-a-custom-library) om.
* [&#x200B; open een bibliotheekaanbieding en geef de inhoud &#x200B;](/help/sites-authoring/content-targeting-touch.md#editing-a-library-offer) uit.

#### Een standaardaanbieding maken door een bestaande component als doel in te stellen {#creating-a-default-offer-by-targeting-an-existing-component}

Wijs een component op de pagina aan om het als aanbieding voor de Standaardervaring van de activiteit te gebruiken. Wanneer u een component als doel instelt, wordt deze in een doelcomponent verpakt en wordt de inhoud van deze component de aanbieding voor de standaardervaring.

Wanneer u een component als doel instelt, kan alleen die component in de aanbieding worden gebruikt. U kunt de component niet uit de aanbieding verwijderen of andere componenten aan de aanbieding toevoegen.

Voer de volgende procedure na [&#x200B; aanvang uit het richten proces &#x200B;](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings).

1. Klik op de component die u als doel wilt instellen. De werkbalk voor de component wordt weergegeven, net als in het volgende voorbeeld.

   ![&#x200B; chlimage_1-18 &#x200B;](assets/chlimage_1-18.png)

1. Klik op het pictogram Doel.

   ![&#x200B; Doel &#x200B;](do-not-localize/chlimage_1.png)

   De inhoud van de component is de aanbieding voor de Standaardervaring. Wanneer een component wordt gericht, wordt zijn standaardknoop herhaald voor elke ervaring. Dit is nodig voor het bewerken van het juiste inhoudsknooppunt tijdens specifieke ontwerphandelingen. Voor deze niet-gebrek ervaringen, of [&#x200B; voeg een douaneaanbieding &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer) toe of [&#x200B; voeg een bibliotheekaanbieding &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library) toe.

#### Een aanbieding maken door een doelcomponent toe te voegen {#creating-an-offer-by-adding-a-target-component}

Voeg een component van het Doel toe om de aanbieding voor de Standaardervaring tot stand te brengen. De doelcomponent is een container voor andere componenten en componenten die erin worden geplaatst, worden als doel ingesteld. Als u de doelcomponent gebruikt, kunt u verschillende componenten toevoegen om een aanbieding te maken. Bovendien kunt u verschillende componenten in elke ervaring gebruiken om verschillende aanbiedingen te maken.

Zie [&#x200B; Vormend de componentenopties van het Doel &#x200B;](/help/sites-authoring/content-targeting-touch.md#configuring-target-component-options) voor informatie bij het aanpassen van deze component.

>[!NOTE]
>
>Aanbiedingen die u gebruikend de [&#x200B; console van Aanbiedingen &#x200B;](/help/sites-authoring/offerlib.md) creeert kunnen verscheidene componenten ook bevatten. Deze aanbiedingen horen bij een aanbiedingsbibliotheek en kunnen voor meerdere ervaringen worden gebruikt.

Aangezien de doelcomponent een container is, wordt deze weergegeven als een neerzetgebied voor andere componenten.

In de modus Doel heeft de component Doel een blauwe rand en geeft het bericht voor de neerzetbestemming de doelaard aan.

![&#x200B; chlimage_1-19 &#x200B;](assets/chlimage_1-19.png)

In de modus Bewerken heeft de component Doel een pictogram met een opsommingsteken.

![&#x200B; component van het Doel op Edit wijze &#x200B;](do-not-localize/chlimage_1-1.png)

Wanneer u componenten naar de component van het Doel sleept, zijn zij gerichte componenten.

![&#x200B; chlimage_1-20 &#x200B;](assets/chlimage_1-20.png)

Wanneer u een component aan de component van het Doel toevoegt, verstrekt het inhoud voor een specifieke ervaring. Als u de ervaring wilt opgeven, selecteert u de ervaring voordat u de componenten toevoegt.

U kunt een doelcomponent aan de pagina toevoegen in de modus Bewerken of in de modus Doel. U kunt componenten alleen in de modus Doel aan de component Doel toevoegen. De doelcomponent behoort tot de Personalization-componentgroep.

Als het uitgeven van gerichte inhoud, moet u **Begin richtend** klikken alvorens u dit kunt doen.

1. Sleep de component Target naar de pagina waar u het aanbod wilt weergeven.
1. Standaard is er geen locatie-id ingesteld. Klik vormen cog wiel om de plaats te plaatsen.

   >[!NOTE]
   >
   >Indien ingesteld door uw beheerder, moet u de locatie mogelijk expliciet instellen.
   >
   >
   >De beheerders kunnen beslissen of het plaatsen van deze configuratie wordt vereist in **https://&lt;host>:&lt;port>/system/console/configMgr/com.day.cq.personalization.impl.servlets.TargetingConfigurationServlet**
   >
   >
   >Als u wilt dat gebruikers een locatie moeten invoeren, schakelt u het selectievakje **Locatie forceren &#x200B;** in.

1. Selecteer de ervaring waarvoor u de aanbieding wilt maken.
1. Maak het voorstel:

   * Voor de Standaardervaring, sleep componenten aan het gerichte dalingsgebied, en geef de componenteneigenschappen zoals gebruikelijk uit om de inhoud voor de aanbieding tot stand te brengen.
   * Voor niet-gebrek ervaringen, of [&#x200B; voeg een douaneaanbieding &#x200B;](#adding-a-custom-offer) toe of [&#x200B; voeg een bibliotheekaanbieding &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-an-offer-from-an-offer-library) toe.

#### Een aangepaste aanbieding toevoegen {#adding-a-custom-offer}

Maak een aanbieding door de inhoud van een doelcomponent te ontwerpen in de modus Doel. Wanneer u een aangepaste aanbieding maakt, wordt deze gebruikt als de aanbieding voor één ervaring.

Als u besluit dat de aanbieding voor andere ervaringen kan worden gebruikt, kunt u een douaneaanbieding tot stand brengen en [&#x200B; het toevoegen aan de bibliotheek &#x200B;](/help/sites-authoring/content-targeting-touch.md#adding-a-custom-offer-to-a-library). Voor informatie over het gebruiken van de console van Aanbiedingen om een herbruikbare aanbieding tot stand te brengen, zie [&#x200B; een Aanbieding aan een Bibliotheek van de Aanbieding &#x200B;](/help/sites-authoring/offerlib.md#add-an-offer-to-an-offer-library) toevoegen.

1. Selecteer de ervaring waaraan u het voorstel wilt toevoegen.
1. Als u het menu van de component wilt weergeven, klikt u op de doelcomponent waaraan u de aanbieding wilt toevoegen.

   ![&#x200B; chlimage_1-21 &#x200B;](assets/chlimage_1-21.png)

1. Klik op het pictogram +.

   De inhoud van de standaardaanbieding wordt gebruikt als de aanbieding voor de huidige ervaring.

1. Klik op de aanbieding om het aanbiedingsmenu weer te geven en klik vervolgens op het pictogram Bewerken.

   ![&#x200B; het menu van de Aanbieding &#x200B;](do-not-localize/chlimage_1-2.png)

1. Bewerk de inhoud van de component.

#### Een voorstel toevoegen vanuit een aanbiedingenbibliotheek {#adding-an-offer-from-an-offer-library}

Voeg een aanbieding van de [&#x200B; aanbiedingsbibliotheek &#x200B;](/help/sites-authoring/offerlib.md) aan een ervaring toe. U kunt elke aanbieding toevoegen uit de bibliotheek van het merk waarvoor u momenteel kiest.

U kunt geen bibliotheekaanbiedingen toevoegen aan de standaardervaring.

1. Selecteer de ervaring waaraan u het voorstel wilt toevoegen.
1. Als u het menu van de component wilt weergeven, klikt u op de doelcomponent waaraan u de aanbieding wilt toevoegen.

   ![&#x200B; chlimage_1-22 &#x200B;](assets/chlimage_1-22.png)

1. Klik het omslagpictogram.

   ![&#x200B; pictogram van de Omslag &#x200B;](do-not-localize/chlimage_1-3.png)

1. Selecteer de aanbieding in de bibliotheek en klik op het pictogram van het vinkje.

   ![&#x200B; chlimage_1-23 &#x200B;](assets/chlimage_1-23.png)

   Met de aanbiedingenkiezer kunt u naar voorstellen bladeren of filteren. Wanneer u bladert of filtert, kunt u de aanbiedingen ook willen sorteren en veranderen hoe u hen bekijkt. Het getal in de rechterbovenhoek geeft aan hoeveel aanbiedingen beschikbaar zijn in de huidige bibliotheek.

   * Klik **doorbladeren** om aan een andere omslag te navigeren. Het navigatievenster wordt geopend en u klikt op de pijl om naar de mappen te gaan. Klik **doorbladeren** opnieuw om de navigatieruit te sluiten.

   ![&#x200B; chlimage_1-24 &#x200B;](assets/chlimage_1-24.png)

   * Klik **Filter** om de aanbiedingen tegen sleutelwoorden of markeringen te filtreren. U voert trefwoorden in en u selecteert tags in het keuzemenu. Klik **Filter** opnieuw om de het filtreren ruit te sluiten.

   ![&#x200B; chlimage_1-25 &#x200B;](assets/chlimage_1-25.png)

   * Verander hoe u de aanbiedingen door te klikken of de pijl naast **Nieuwst aan Oudst** te tikken sorteert. Aanbiedingen kunnen nieuwste worden gesorteerd op oudst of oudst op nieuwste.

   ![&#x200B; chlimage_1-26 &#x200B;](assets/chlimage_1-26.png)

   Klik het pictogram naast **Mening als** om aanbiedingen als tegels of als lijst te bekijken.

   ![&#x200B; chlimage_1-27 &#x200B;](assets/chlimage_1-27.png)

#### Een aangepaste aanbieding aan een bibliotheek toevoegen {#adding-a-custom-offer-to-a-library}

Voeg een douaneaanbieding aan de [&#x200B; aanbiedingsbibliotheek &#x200B;](/help/sites-authoring/offerlib.md) toe wanneer u het als aanbieding voor veelvoudige ervaringen wilt hergebruiken. U kunt aanbiedingen toevoegen aan de bibliotheek van het huidige merk waarop u zich richt.

Voor informatie over het gebruiken van de console van Aanbiedingen om een herbruikbare aanbieding tot stand te brengen, zie [&#x200B; een Aanbieding aan een Bibliotheek van de Aanbieding &#x200B;](/help/sites-authoring/offerlib.md#add-an-offer-to-an-offer-library) toevoegen.

1. Selecteer de ervaring om de aangepaste aanbieding weer te geven.
1. Klik de douaneaanbieding om het aanbiedingsmenu te openbaren, dan klik **sparen Aanbieding aan de Bibliotheek van de Aanbieding** pictogram.

   ![&#x200B; sparen aanbieding aan de Bibliotheek van de Aanbieding &#x200B;](do-not-localize/chlimage_1-4.png)

1. Typ een naam voor de aanbieding, selecteer de bibliotheek waaraan u de aanbieding toevoegt, en klik dan het controlemerkpictogram.

#### Een bibliotheekaanbod omzetten in een aangepaste bibliotheek {#converting-a-library-offer-to-a-custom-library}

Een bibliotheekaanbieding omzetten in een aangepaste aanbieding om de aanbieding voor de huidige ervaring te wijzigen zonder de aanbieding in andere ervaringen te wijzigen.

1. Selecteer de ervaring om het bibliotheekaanbod weer te geven.
1. Klik op de bibliotheekaanbieding om het aanbiedingsmenu weer te geven en klik vervolgens op het pictogram Omzetten in onlineaanbieding.

   ![&#x200B; Bekeerling in Inline Aanbieding &#x200B;](do-not-localize/chlimage_1-5.png)

#### Een bibliotheekaanbod bewerken {#editing-a-library-offer}

Open een bibliotheekaanbieding vanuit een ervaring in de modus Gericht om de aanbieding te bewerken. De wijzigingen die u aanbrengt, worden weergegeven in alle ervaringen die gebruikmaken van de aanbieding.

1. Selecteer de ervaring om het bibliotheekaanbod weer te geven.
1. De bibliotheekaanbieding omzetten in een lokale/aangepaste aanbieding. Zie [&#x200B; Omzettend een Aanbieding van de Bibliotheek in een Bibliotheek van de Douane &#x200B;](#converting-a-library-offer-to-a-custom-library).
1. Bewerk de inhoud van de aanbieding.

1. Sla het bestand weer op in de bibliotheek. Zie [&#x200B; Toevoegend een Aanbod van de Douane aan een Bibliotheek &#x200B;](#adding-a-custom-offer-to-a-library).

## Doel: Het publiek configureren {#target-configuring-the-audiences}

De stap van het Doel van [&#x200B; het richten proces &#x200B;](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) impliceert kaartpubliek met de ervaringen waarmee u in Create stap werkte. De pagina Doel toont het publiek dat elke ervaring richt. U kunt het publiek voor elke ervaring opgeven of wijzigen. Als u Adobe Target gebruikt, kunt u A/B tests ook tot stand brengen die u percentage van verkeer voor een publiek aan een bepaalde ervaring laten richten.

### Als u AEM targeting of Adobe Target gebruikt (Experience targeting)... {#if-you-are-using-aem-targeting-or-adobe-target-experience-targeting}

Het publiek verschijnt aan de linkerkant van het kaartdiagram, en de ervaringen verschijnen aan de rechterkant.

![&#x200B; chlimage_1-28 &#x200B;](assets/chlimage_1-28.png)

Bepaal een publiek gebruikend een segment. De wolkenconfiguratie voor de pagina bepaalt de segmenten die aan u beschikbaar zijn. Als de pagina niet is gekoppeld aan een Adobe Target-cloudconfiguratie, zijn AEM-segmenten beschikbaar voor het definiëren van soorten publiek. Wanneer de pagina aan een de wolkenconfiguratie van Adobe Target wordt geassocieerd, gebruikt u de segmenten van het Doel.

Voor informatie richtend motoren, zie [&#x200B; het richten Motor &#x200B;](/help/sites-authoring/personalization.md#targeting-engine).

Gebruik geen publiek meer dan één ervaring. Er verschijnt een waarschuwingssymbool naast een ervaring wanneer het wordt toegewezen aan een publiek dat is toegewezen aan een andere ervaring.

![&#x200B; het symbool van de Waarschuwing wanneer in kaart gebracht aan een publiek dat aan een andere ervaring &#x200B;](do-not-localize/chlimage_1-6.png) in kaart wordt gebracht

### Ervaringen met het publiek koppelen (AEM of Adobe Target) {#associating-experiences-with-audiences-aem-or-adobe-target}

Gebruik de volgende procedure om een ervaring aan een publiek te associëren wanneer het gebruiken van het richten van AEM (of de ervaring van Adobe Target het richten):

1. Klik op de vervolgkeuzepijl in het publieksvak dat aan de ervaring is toegewezen.
1. (Optioneel) Klik op **Bewerken** en typ een trefwoord om naar het gewenste segment te zoeken.
1. In de lijst van publiek, selecteer het publiek en klik **O.K.**.

### Als u A/B Testing (Adobe Target) gebruikt... {#if-you-are-using-a-b-testing-adobe-target}

Als u een A/B testactiviteit hebt, zijn de soorten publiek op uw linkerzijde, is het percentage dat elke ervaring wordt bekeken in het midden, en de ervaringen zijn op het recht.

U kunt de percentages wijzigen zolang ze maar optellen tot 100 procent. Een publiek kan door veelvoudige ervaringen in het testen A/B worden gebruikt.

![&#x200B; chlimage_1-29 &#x200B;](assets/chlimage_1-29.png)

### Soorten publiek en verkeerspercentages koppelen aan A/B-tests {#associating-audiences-and-traffic-percentages-with-a-b-testing}

1. Klik op het keuzemenu naast het publiek dat aan de ervaring is toegewezen.
1. (Facultatief) klik **uitgeven**, dan typ een sleutelwoord om naar het gewenste segment te zoeken.
1. Klik **O.K.**
1. Ga in percentages in om te vormen hoe het publieksverkeer aan elke ervaringen wordt verpletterd. Het totale getal moet 100 zijn.
1. (Optioneel) Bewerk de ervaringsnaam door te klikken op het keuzemenu naast de naam van de ervaring.

## Doelstellingen en instellingen: de activiteiten configureren en doelen instellen {#goals-settings-configuring-the-activity-and-setting-goals}

De doelstellingen &amp; stap van Montages van [&#x200B; het het richten proces &#x200B;](/help/sites-authoring/content-targeting-touch.md#the-targeting-process-create-target-and-goals-settings) impliceert het vormen van het gedrag van de merkactiviteit. Geef op wanneer de activiteit begint en eindigt en geef de prioriteit van de activiteit op. Bovendien volgt u ook doelstellingen. Specifiek kunt u beslissen wat u met uw activiteiten wilt meten.

Goal Metrics zijn alleen beschikbaar als je Adobe Target gebruikt voor je doelengine. Bepaal minstens één doel metrisch. Als u Adobe Analytics hebt geconfigureerd en een cloudconfiguratie voor A4T Analytics hebt, kunt u kiezen of u de rapportbron Adobe Target of Adobe Analytics wilt zijn.

De doelmeetgegevens worden alleen gemeten voor de gepubliceerde campagne.

Indien AEM wordt gebruikt als de motor waarop is gericht:

![&#x200B; chlimage_1-30 &#x200B;](assets/chlimage_1-30.png)

Indien Adobe Target wordt gebruikt als de motor waarop is gericht:

![&#x200B; chlimage_1-31 &#x200B;](assets/chlimage_1-31.png)

Als u Adobe Target gebruikt als de doelengine en u A4T Analytics hebt geconfigureerd voor het account, hebt u een extra vervolgkeuzemenu voor **Bron van rapportage**:

![&#x200B; chlimage_1-32 &#x200B;](assets/chlimage_1-32.png)

De volgende succeswaarden zijn beschikbaar (alleen gebruikt voor publiceren):

<table>
 <tbody>
  <tr>
   <td><strong>Conversie</strong></td>
   <td><p>Het percentage bezoekers dat heeft geklikt op een onderdeel van de ervaring die wordt getest. Een conversie kan één keer per bezoeker worden meegeteld of telkens wanneer een bezoeker een conversie voltooit. De omzettingsmetrische waarde wordt geplaatst aan één van het volgende:</p>
    <ul>
     <li><strong> bekeken een pagina </strong> - u kunt bepalen welke pagina het publiek door één van beide <strong> URL wordt bekeken </strong> is en dan URL of veelvoudige URLs bepaalt, of door <strong> URL te selecteren bevat </strong> en dan een weg of sleutelwoord toe te voegen.</li>
     <li><strong> bekeken mbox </strong> - u kunt bepalen welke mbox uw publiek door de naam van mbox in te gaan werd bekeken. U kunt veelvoudige dozen ingaan door <strong> te klikken voegt een Mbox </strong> toe.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Ontvangsten</strong></td>
   <td><p>Door het bezoek gegenereerde inkomsten. U kunt uit de volgende opbrengstmetriek kiezen:</p>
    <ul>
     <li>Opbrengst per bezoeker (RPV)</li>
     <li>Gemiddelde bestelwaarde (AOV)</li>
     <li>Totale verkoop </li>
     <li>Orders</li>
    </ul> <p>Voor al deze opties geeft het feit of een box is weergegeven aan dat het doel is bereikt. U kunt de box of meerdere vakken definiëren.</p> </td>
  </tr>
  <tr>
   <td><strong>Betrokkenheid</strong></td>
   <td><p>U kunt drie soorten betrokkenheid meten:</p>
    <ul>
     <li>Paginaweergaven</li>
     <li>Aangepaste scores</li>
     <li>Tijd op de site</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Bovendien zijn er geavanceerde montages die u laten bepalen hoe te om succesmetriek te tellen. U kunt onder andere de metrische waarde per impositie of één keer per bezoeker tellen en kiezen of de gebruiker in de activiteit moet blijven of de activiteit moet verwijderen.

Gebruik de geavanceerde montages om te bepalen wat **gebeurt nadat** een gebruiker het doel metrisch ontmoet. In de volgende tabel staan de beschikbare opties.

<table>
 <tbody>
  <tr>
   <td><strong>Nadat een gebruiker dit doel metrisch ontmoet..</strong></td>
   <td><strong>U selecteert het volgende om te gebeuren...</strong></td>
  </tr>
  <tr>
   <td><strong>Aantal verhogen en gebruiker actief houden</strong></td>
   <td>Geef op hoe het aantal wordt verhoogd:
    <ul>
     <li>Eenmaal per gegadigde</li>
     <li>Bij elke afbeelding, pagina-vernieuwingen uitsluiten</li>
     <li>Op elke indruk</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Toename, gebruiker vrijgeven en opnieuw invoeren toestaan</strong></td>
   <td>Selecteer de ervaring die de bezoeker ziet als ze de activiteit opnieuw betreden:
    <ul>
     <li>Dezelfde ervaring</li>
     <li>Willekeurige ervaring</li>
     <li>Onzichtbare ervaring</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Toename, Geen gebruiker &amp; Staafherinvoer</strong></td>
   <td>Bepaal wat de gebruiker ziet in plaats van de inhoud van de activiteit:
    <ul>
     <li>Dezelfde ervaring, zonder bijhouden</li>
     <li>Standaardinhoud of andere activiteit-inhoud</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Zie {de documentatie van 0} Adobe Target [&#x200B; voor meer informatie over succesmetriek.](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/success-metrics.html)

### Instellingen configureren (AEM-doelen) {#configuring-settings-aem-targeting}

Instellingen configureren bij gebruik van AEM-doelen:

1. Om te specificeren wanneer de activiteit begint, gebruik het **drop-down menu van het Begin** om één van de volgende waarden te selecteren:

   * **wanneer Geactiveerd**: De activiteit begint wanneer de pagina die de gerichte inhoud bevat wordt geactiveerd.
   * **specificeerde Datum &amp; Tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te starten.

1. Om te specificeren wanneer de activiteit beëindigt, gebruik het **Eind** drop-down menu om één van de volgende waarden te selecteren:

   * **wanneer Gedeactiveerd**: De activiteit beëindigt wanneer de pagina die de gerichte inhoud bevat wordt gedeactiveerd.
   * **specificeerde Datum &amp; Tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te beëindigen.

1. Om een prioriteit voor de activiteit te specificeren, gebruik de schuif om of **Laag**, **Normaal**, of **Hoog** te selecteren.

### Doelstellingen en instellingen configureren (Adobe Target) {#configuring-goals-settings-adobe-target}

Als u Adobe Target gebruikt, kunt u als volgt doelen en instellingen configureren:

1. Om te specificeren wanneer de activiteit begint, gebruik het **drop-down menu van het Begin** om één van de volgende waarden te selecteren:

   * **wanneer Geactiveerd**: De activiteit begint wanneer de pagina die de gerichte inhoud bevat wordt geactiveerd.
   * **specificeerde Datum &amp; Tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te starten.

1. Om te specificeren wanneer de activiteit beëindigt, gebruik het **Eind** drop-down menu om één van de volgende waarden te selecteren:

   * **wanneer Gedeactiveerd**: De activiteit beëindigt wanneer de pagina die de gerichte inhoud bevat wordt gedeactiveerd.
   * **specificeerde Datum &amp; Tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te beëindigen.

1. Om een prioriteit voor de activiteit te specificeren, gebruik de schuif om of **Laag**, **Normaal**, of **Hoog** te selecteren.
1. Als u de Analyse van Adobe met uw Rekening van Adobe Target hebt gevormd, dan ziet u **Meldend Source** drop-down menu. Selecteer **Adobe Target** of **Adobe Analytics** als bron.

   Als u **Adobe Analytics** selecteert, selecteer het bedrijf en rapportreeks. Als u **Adobe Target** selecteert, wordt geen actie vereist.

   ![&#x200B; chlimage_1-33 &#x200B;](assets/chlimage_1-33.png)

1. In het gebied **Metrische data van doel** selecteert u onder **Mijn primaire doel** de metrische data voor succes die u wilt volgen (Omzetting, Inkomsten, Betrokkenheid) en geeft u op hoe deze metrische waarde wordt gemeten (of welke actie de doelgroep uitvoert om aan te geven dat een doel bereikt is). Zie de definitie van de metrische data van doel in de vorige tabel en zie de [Adobe Target-documentatie](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/success-metrics.html) over metrische data voor succes.

   U kunt de naam van het doel wijzigen door op de drie stippen in de rechterbovenhoek te klikken en **Naam wijzigen** te selecteren.

   Als u alle velden wilt wissen, klikt u op de drie stippen in de rechterbovenhoek en selecteert u **Alle velden wissen**.

   Alle metriek hebben ook geavanceerde montages u kunt bepalen. Selecteer **Geavanceerde Montages** om tot die toegang te hebben. Zie definitie van hoe de succesmetriek in vorige lijst worden geteld en [&#x200B; documentatie van Adobe Target &#x200B;](https://experienceleague.adobe.com/docs/target/using/activities/success-metrics/success-metrics.html) zien.

   >[!NOTE]
   >
   >Er moet ten minste één doel zijn gedefinieerd.

   ![&#x200B; chlimage_1-34 &#x200B;](assets/chlimage_1-34.png)

   >[!NOTE]
   >
   >Als er informatie ontbreekt in metrisch, omringt een rode lijn metrisch.

1. Klik **toevoegen een Nieuwe Metrische** om extra succesmetriek te vormen.

   ![&#x200B; chlimage_1-35 &#x200B;](assets/chlimage_1-35.png)

   >[!NOTE]
   >
   >U kunt extra doelstellingen verwijderen door de drie punten te klikken of te tikken en **Schrapping** te klikken of te tikken. AEM vereist dat er ten minste één doel is gedefinieerd.

1. Als u meer controle over wilt hoe de succesmetriek worden geteld, klik **Geavanceerde Montages** om tot die toegang te hebben.
1. Klik **sparen**.

Na het vormen, kunt u [&#x200B; de prestaties van uw activiteiten &#x200B;](/help/sites-authoring/activitylib.md#viewing-performance-and-converting-winning-experiences-a-b-test) bekijken die Adobe Target (of ervaring of A/B test het richten) gebruiken. Bovendien met A/B test het richten, kunt u [&#x200B; de winnaars omzetten.](/help/sites-authoring/activitylib.md#viewing-performance-and-converting-winning-experiences-a-b-test)

## Een ervaring simuleren {#simulating-an-experience}

Simuleer de ervaring van een bezoeker om te controleren of de pagina-inhoud op de verwachte wijze wordt weergegeven, afhankelijk van het ontwerp van uw doelinhoud. Tijdens het simuleren kunt u verschillende gebruikersprofielen laden en de doelinhoud voor die gebruiker bekijken.

De volgende criteria bepalen de inhoud die wordt weergegeven wanneer bezoekerservaring wordt gesimuleerd:

* De gegevens in de zittingsopslag van de gebruiker (via de Hub van de Context).
* De [&#x200B; Activiteiten die &#x200B;](/help/sites-authoring/activitylib.md) zijn.
* De [&#x200B; regels die de segmenten &#x200B;](/help/sites-administering/campaign-segmentation.md) bepalen.
* De inhoud van de ervaringen in de doelcomponenten.
* De [&#x200B; configuratie van de het richten motor &#x200B;](/help/sites-authoring/activitylib.md).

Als er onverwachte inhoud op de pagina wordt weergegeven wanneer u een profiel laadt, controleert u de configuratie van elk item in deze lijst.

>[!NOTE]
>
>Als u A/B het testen gebruikt, wanneer het simuleren van ervaringen wordt getoond gebaseerd op verkeerspercentage. Dit wordt gecontroleerd door Adobe Target, wat tot onverwachte resultaten voor auteurs kan leiden. (De _auteuractiviteit is gesynchroniseerd met specifieke montages die herevaluatie tijdens simulatie toestaan.) De auteurs kunnen moeten verfrissen om de andere ervaringen te zien die op hun verkeersmontages worden gebaseerd.

Gebruik de volgende gereedschappen om de ervaring van de bezoeker te simuleren:

* De simulatieactiviteit op het richten wijze: De pagina toont de aanbiedingen voor de gebruiker die momenteel in de Hub van de Context wordt geselecteerd. U kunt de aanbiedingen bewerken die op de gebruiker zijn gericht.
* De wijze van de voorproef: De Hub van de Context van het gebruik om de gebruikers en de plaatsen te selecteren die aan de criteria van de segmenten voldoen die uw ervaringen op gebaseerd zijn. Wanneer uw selecties van de Hub van de Context veranderen, verandert de gerichte inhoud dienovereenkomstig.

1. Om op de wijze van de Voorproef over te schakelen, op de toolbar klikt **Voorproef**.
1. Voor de hulpmiddelbar, klik het pictogram van de Hub van de Context.

   ![&#x200B; de Hub van de Context &#x200B;](do-not-localize/chlimage_1-7.png)

1. Gebruik Context Hub om context-eigenschappen te wijzigen. Klik bijvoorbeeld op de eigenschap Persona om een andere gebruiker te selecteren.

   ![&#x200B; chlimage_1-36 &#x200B;](assets/chlimage_1-36.png)

   De pagina verandert om de inhoud te tonen die voor de huidige context wordt gericht.

1. Als u de weergegeven aanbiedingen wilt wijzigen, schakelt u over naar de modus Doel. Selecteer de simulatieactiviteit en bewerk de aanbiedingen voor de context die u hebt geconfigureerd in de modus Voorbeeld.

## Opties voor doelcomponenten configureren {#configuring-target-component-options}

U kunt de component van het Doel aanpassen door tot de opties van de component op één van twee manieren toegang te hebben:

1. Nadat u de component, in de component van het Doel hebt gericht, klik de component en toen het montagespictogram (cog).

   ![&#x200B; de componentenmenu van het Doel &#x200B;](do-not-localize/chlimage_1-8.png)

   AEM geeft het venster met opties voor de doelcomponent weer.

   ![&#x200B; chlimage_1-37 &#x200B;](assets/chlimage_1-37.png)

1. U kunt deze instellingen ook openen in de modus Volledig scherm door in het venster met opties voor de doelcomponent op het pictogram Volledig scherm te klikken.

   ![&#x200B; venster van de componentenopties van het Doel &#x200B;](do-not-localize/chlimage_1-9.png)

   AEM geeft het venster met opties voor de doelcomponent voor volledig scherm weer.

   ![&#x200B; chlimage_1-38 &#x200B;](assets/chlimage_1-38.png)

1. Configureer de instellingen voor de doelcomponent zoals beschreven in de volgende tabellen.

<table>
 <tbody>
  <tr>
   <td><strong>Optie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Locatie</strong></td>
   <td><p>De locatie is een tekenreeks die de doellocatie van de inhoud een naam geeft en aanbiedingen verbindt met plaatsen (of locaties of componenten) op de pagina waar deze aanbiedingen moeten worden geplaatst.</p> <p>Dit veld is een algemene waarde.</p> <p>Als u een voorstel in een component zet, onthoudt de aanbieding de locatie-id. Wanneer de pagina wordt uitgevoerd, evalueert de motor de segmenten van de gebruiker en gebaseerd op dit, lost het de ervaringen van de actieve campagnes op die zouden moeten worden getoond. Vervolgens worden de locatie-id's op de pagina gecontroleerd en wordt geprobeerd voorstellen met die locatie-id's aan te passen.</p> </td>
  </tr>
  <tr>
   <td><strong>Engine</strong></td>
   <td>Selecteer tussen <strong> de zijRegels van de Cliënt (zonder het volgen), Adobe Target, ContextHub, </strong> en <strong> Adobe Campaign </strong> afhankelijk van welke motor u zou willen gebruiken.</td>
  </tr>
 </tbody>
</table>

Als u Adobe Target als engine selecteert:

![&#x200B; chlimage_1-39 &#x200B;](assets/chlimage_1-39.png)

<table>
 <tbody>
  <tr>
   <td><strong>Optie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Nauwkeurige bestemming</strong></td>
   <td><p>Wanneer u nauwkeurige adressering inschakelt, weet de component dat deze moet wachten totdat de context- of contexthubgegevens beschikbaar zijn voordat de aanvraag naar Adobe Target wordt verzonden. Hierdoor kan de laadtijd toenemen. Voor creatie, wordt het nauwkeurige richten altijd toegelaten.</p> <p>Als u <strong> nauwkeurig het richten </strong> controledoos selecteert, voert mbox <code>mboxDefine</code> eerst uit en <code>mboxUpdate</code> later resulterend in een verzoek Ajax zodra de gegevens beschikbaar zijn.</p> <p>Als u niet de <strong> Nauwkeurige het richten </strong> controledoos selecteert, voert mbox <code>mboxCreate</code> resulterend in een synchrone aanvraag onmiddellijk uit (in dit geval, niet kunnen alle contextgegevens nog beschikbaar zijn).</p> <p><strong> Nota:</strong> het toelaten of het onbruikbaar maken van nauwkeurig het richten op een specifieke component beïnvloedt niet de montages u globaal hebt geplaatst. U kunt globale instellingen altijd overschrijven door Accurate doelen selecteren in de component.</p> </td>
  </tr>
  <tr>
   <td><strong>Omgezette segmenten opnemen</strong></td>
   <td><p>Het selecteren van deze controledoos omvat alle opgeloste segmenten in de mbox vraag en om het even welke parameters die in de pagina en in het kader worden gevormd.</p> <p>Dit werkt alleen in situaties met XML API waarin u AEM-segmenten synchroniseert. Als u segmenten in AEM hebt die niet door Adobe Target (als manuscriptsegmenten) worden behandeld, dan laat deze optie u het segment in AEM oplossen en informatie verzenden naar Adobe Target dat het segment actief is.</p> </td>
  </tr>
  <tr>
   <td><strong>Overgenomen contextparameters</strong></td>
   <td>Hier worden eventueel van het Adobe Target-framework overgeërfde contextparameters weergegeven die aan de geselecteerde pagina zijn gekoppeld.</td>
  </tr>
  <tr>
   <td><strong>Contextparameters</strong></td>
   <td>Klik <strong> voeg gebied </strong> toe om extra contextparameters (het zelfde als te vormen wat in het kader van het Doel beschikbaar is). De parameters van de context die aan de component worden toegevoegd passen <i> slechts </i> op de component en niet op andere component toe zoals het geval zou zijn als u rechtstreeks contextparameters aan het kader toevoegde.</td>
  </tr>
  <tr>
   <td><strong>Statische parameters</strong></td>
   <td>Klik <strong> voeg gebied </strong> toe om extra statische parameters (het zelfde als te vormen wat in het kader van het Doel beschikbaar is). De statische parameters die aan de component worden toegevoegd passen <i> slechts </i> op de component en niet op andere component toe zoals het geval zou zijn als u statische parameters rechtstreeks aan het kader toevoegde. Statische parameters komen niet uit context (cliëntcontext van inhoudshub).</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wanneer u een component selecteert en deze doelbaar maakt, vervangt AEM ook de component en injecteert een Adobe Target-component. (De Adobe Target-component wordt niet alleen gebruikt wanneer u deze handmatig aan de pagina toevoegt, maar ook wanneer u een bestaande component als doel instelt.)

Als u Client Context (clientzijde) selecteert als de engine:

![&#x200B; chlimage_1-40 &#x200B;](assets/chlimage_1-40.png)

<table>
 <tbody>
  <tr>
   <td><strong>Optie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><strong>Opties aan clientzijde - Strategie</strong></td>
   <td><p>Selecteer een van de volgende opties:</p>
    <ul>
     <li><strong> Eerste </strong>: De hoogste ervaring in de lijst zoals die in de campagne wordt bevolen.</li>
     <li><strong> Willekeurig </strong>: Om het even welke ervaring wordt gebruikt.</li>
     <li><strong> de Score van de KlikStream </strong>: De markeringen en verwante markeringstreffers die in de cliëntcontext worden gevolgd worden gebruikt. De snelheden voor tags die op de teaspagina zijn gedefinieerd, worden vergeleken.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

U selecteert **Adobe Campaign** als motor als u AEM met Adobe Campaign integreert. Zie [&#x200B; Integrating AEM met Adobe Campaign &#x200B;](/help/sites-administering/campaign.md) voor meer informatie.

Selecteer **ContextHub** als motor als u ContextHub voor het richten gebruikt. Zie [&#x200B; het Vormen ContextHub.](/help/sites-developing/ch-configuring.md)
