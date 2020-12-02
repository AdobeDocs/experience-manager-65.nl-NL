---
title: Activiteiten beheren
seo-title: Activiteiten beheren
description: Met de activiteitenconsole kunt u de marketingactiviteiten van uw merken maken, organiseren en beheren
seo-description: Met de activiteitenconsole kunt u de marketingactiviteiten van uw merken maken, organiseren en beheren
uuid: 0aebf88e-f298-410a-8c82-4076b671624f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: ef2321a3-cd51-4298-8782-e1a2ca721868
docset: aem65
translation-type: tm+mt
source-git-commit: 90c99e527a40bb663d4f32d8746b46cf34a2319f
workflow-type: tm+mt
source-wordcount: '2022'
ht-degree: 13%

---


# Activiteiten beheren{#managing-activities}

Met de activiteitenconsole kunt u de marketing [activiteiten](/help/sites-authoring/personalization.md#activities) van uw merken maken, organiseren en beheren:

* Voeg merken toe.
* Voor elk merk, voeg en vorm activiteiten toe.
* Beheer activiteiten.

>[!NOTE]
>
>Als u Adobe Target als doelengine gebruikt, kunt u ook [prestatiegegevens van uw activiteiten bekijken](#viewing-performance-and-converting-winning-experiences-a-b-test). Als u A/B het testen gebruikt, kunt u [winnaars ](#viewing-performance-and-converting-winning-experiences-a-b-test) omzetten.

Op de Activity Console worden de activiteiten georganiseerd door merk. U kunt merken en mappen gebruiken om de organisatie van uw activiteiten te structureren. U navigeert aan de console van Activiteiten door **Personalisatie** te tikken/te klikken en **Activiteiten** te tikken/te klikken.

De activiteiten zijn beschikbaar op het richten wijze voor [creatie gerichte inhoud](/help/sites-authoring/content-targeting-touch.md), waar u activiteiten kunt ook tot stand brengen. De activiteiten die u op het richten wijze creeert verschijnen in de console van Activiteiten.

De activiteiten worden getoond met een etiket beschrijvend welke soort activiteit wordt bepaald:

* XT - Adobe Target-ervaring gericht
* A/B - Adobe Target A/B-tests
* AEM - Adobe Experience Manager-doelversie (context- of clientcontext-afhankelijk)

![chlimage_1-115](assets/chlimage_1-114.png)

>[!NOTE]
>
>Welke soorten activiteiten beschikbaar zijn, wordt bepaald door:
>
>* Als de **xt_only** optie op Adobe Target huurder (cliëntcode) wordt toegelaten die aan de AEM kant wordt gebruikt om met Adobe Target te verbinden, dan kunt u **slechts** XT activiteiten in AEM tot stand brengen.
   >
   >
* Als de **xt_only** opties **not** toegelaten op de huurder van Adobe Target (cliëntcode) is, dan kunt u **zowel** XT en A/B activiteiten in AEM tot stand brengen.
>
>
**Aanvullende opmerking:** **xt_** only options is een instelling die wordt toegepast op een bepaalde doelgebruiker (clientcode) en kan alleen rechtstreeks in Adobe Target worden gewijzigd. U kunt deze optie niet in- of uitschakelen in AEM.

>[!CAUTION]
>
>U moet het knooppunt activity settings **cq:ActivitySettings** op de publicatie-instantie beveiligen zodat dit niet toegankelijk is voor normale gebruikers. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [Voorwaarden voor integratie met Adobe Target](/help/sites-administering/target-requirements.md#securingtheactivitysettings) voor meer informatie.

## Een merk maken met de activiteitenconsole {#creating-a-brand-using-the-activities-console}

Maak een merk waarvoor u marketingactiviteiten wilt beheren.

Wanneer u een merk gebruikend de console van Activiteiten creeert, verschijnt het ook in [de console van Aanbiedingen](/help/sites-authoring/offerlib.md) waar u aanbiedingen voor de ervaringen van uw activiteiten kunt tot stand brengen.

1. Klik of tik op **Personalisatie** in de navigatieconsole. Klik of tik **Activiteiten**.

   ![screen_shot_2018-03-21at151821](assets/screen_shot_2018-03-21at151821.png)

1. Klik of tik op **Maak** then **Brand** in de activiteitenconsole.
1. Selecteer de merksjabloon en klik of tik op **Next**.
1. Typ een titel voor het merk zoals u deze wilt weergeven in de consoles Activiteiten en Aanbiedingen. Typ of selecteer eventueel een of meer tags die u aan het merk wilt koppelen.
1. Klik of tik **Create**. Uw merk wordt weergegeven in de Activiteitenconsole.

## Een activiteit toevoegen/bewerken met de activiteitenconsole {#adding-editing-an-activity-using-the-activities-console}

Voeg een activiteit toe of bewerk een bestaande activiteit om uw marketing inspanningen op specifieke doelgroepen te concentreren. Wanneer u een activiteit creeert/uitgeeft, specificeert u de volgende informatie:

* **Naam:** De naam van de activiteit.
* **Targeting engine:** [AEM](/help/sites-authoring/personalization.md#aem) of [Adobe Target](/help/sites-authoring/personalization.md#adobe-target) als de engine voor gerichte content.

* **Een doelconfiguratie selecteren:** (alleen voor Adobe Target) De cloudconfiguratie die deze activiteit moet gebruiken om verbinding te maken met Adobe Target. Deze optie wordt alleen weergegeven als Adobe Target is geselecteerd als doelengine.
* **Type activiteit: **Type activiteit - A/B-test of ervaring gericht op
* **Doelstelling:** (optioneel) Een beschrijving van de activiteit.
* **Ervaringen:** Toewijzingen tussen doelgroepnamen en de marketingsegmenten waarop u zich richt.
* **Verkeerspercentages:** Als A/B-test is geselecteerd, kunt u aanpassen hoeveel verkeer (in percenten) naar elke ervaring gaat.
* **Duur:** De periode waarin de activiteit wordt toegepast.
* **Prioriteit:** De relatieve prioriteit van de activiteit. Wanneer de activiteiten content voor dezelfde gebruikerssegmenten bieden, krijgt de activiteit met de hogere prioriteit voorrang.
* **Metrische data van doel:** Als Adobe Target is geselecteerd als de doelengine, kunt u metrische data van successen aan de activiteit toevoegen. Eén metrische waarde van successen is vereist.

>[!NOTE]
>
>De nieuwe Adobe Target-activiteiten moeten in de gerichte contenteditor worden ***gemaakt***, en niet in de console **Activiteiten**, omdat de synchronisatie met Adobe Target dan mislukt.
>
>U kunt echter bestaande Adobe Target-activiteiten in de console bewerken.

Een activiteit toevoegen:

1. Klik of tik het merk waarvoor u de activiteit creeert, en klik dan of tik **creeer **dan** creeer Activiteit. **Selecteer bij het bewerken de activiteit in het scherm Mastergebied en klik of tik op **Activiteit bewerken**.
1. Geef de volgende informatie op en klik of tik op **Next**:

   * Een naam voor de activiteit.
   * De doelengine die moet worden gebruikt. ContextHub (AEM) wordt geselecteerd door gebrek. Als u Adobe Target moet gebruiken, maakt u de activiteit in de beoogde inhoudseditor.
   * Als u Adobe Target hebt geselecteerd als de doelengine, selecteert of bewerkt u de cloudconfiguratie die u wilt gebruiken om verbinding te maken met Adobe Target. (Zorg ervoor dat u geen framework selecteert dat u hebt gemaakt voor uw cloudconfiguratie.)
   * (Optioneel) Het doel of een beschrijving van de activiteit.
   * Selecteer het type activiteit.

1. Voeg een of meer ervaringen toe aan de activiteit. Klik of tik op **Ervaring toevoegen**.
1. Als u gebruikmaakt van AEM of Adobe Target-ervaring als doelwit:

   1. Klik of tik **Selecteer Publiek **en selecteer het segment dat uw ervaringsdoelstellingen.
   1. Klik of tik **Ervaring toevoegen**, typ een naam en klik of tik **OK**.

   1. Klik of tik **Volgende**.

   Als u Adobe Target A/B Testen gebruikt:

   1. Klik of tik op het potlood in het vak Soorten publiek om een publiek te selecteren.
   1. Klik of tik **Ervaring toevoegen**, typ een naam en klik of tik **OK**.

   1. Ga het percentage van verkeer in dat elke ervaring toont.
   1. Klik of tik **Volgende**.


1. Als u wilt opgeven wanneer de activiteit begint, gebruikt u het vervolgkeuzemenu **Start** om een van de volgende waarden te selecteren:

   * **Wanneer geactiveerd:** De activiteit wordt gestart wanneer de pagina met de doelinhoud wordt geactiveerd.
   * **Opgegeven datum en tijd:** een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op waarop de activiteit wordt gestart.

1. Als u wilt opgeven wanneer de activiteit eindigt, gebruikt u het vervolgkeuzemenu Einde om een van de volgende waarden te selecteren:

   * **Wanneer gedeactiveerd**: De activiteit eindigt wanneer de pagina die de beoogde inhoud bevat, wordt gedeactiveerd.
   * **Opgegeven datum en tijd**: Een specifieke tijd. Wanneer u deze optie selecteert, klikt of tikt u op het kalenderpictogram, selecteert u een datum en geeft u de tijd op om de activiteit te beëindigen.

1. Als u een prioriteit voor de activiteit wilt opgeven, gebruikt u de schuifregelaar om **Laag**, **Normaal** of **Hoog** te selecteren.
1. Als u Adobe Target gebruikt als de doelengine, selecteert u wat u met deze activiteit wilt meten. Zie [Het vormen van de Activiteit en het Plaatsen Doelstellingen](/help/sites-authoring/content-targeting-touch.md) voor meer informatie over de beschikbare succesmetriek. U moet ten minste één doel selecteren.
1. Klik of tik **Save**.

   >[!NOTE]
   >
   >Nadat u een activiteit hebt gemaakt, moet u deze publiceren zodat deze beschikbaar is.

## Publicatie- en publicatieactiviteiten {#publishing-and-unpublishing-activities}

U moet activiteiten publiceren om deze beschikbaar te maken. Omgekeerd kunt u activiteiten onbeschikbaar maken door deze te verwijderen.

>[!NOTE]
>
>Wanneer u het publiceren van een activiteit ongedaan maakt, verandert de status van de activiteit alleen als u de pagina vernieuwt.

Om activiteiten te publiceren of unpublish:

1. Klik of tik op het merk en vervolgens het gebied met de activiteit die u wilt publiceren of de publicatie ongedaan wilt maken.
1. Tik of klik op het pictogram naast de activiteit of activiteiten die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken.

   ![screen-shot_2019-03-05at123846](assets/screen-shot_2019-03-05at123846.png)

1. Tik of klik op **Publiceren** om te publiceren. Tik of klik op **Publicatie ongedaan maken** om de publicatie ongedaan te maken. Uw activiteit of activiteiten worden gepubliceerd of niet gepubliceerd en hun statusveranderingen in de console van de Activiteiten (kan vereisen verfrissen).

## Activiteiten op instanties Auteur en Publiceren {#activities-on-author-and-publish-instances}

Wanneer een activiteit wordt geactiveerd die de beoogde Adobe Target-engine gebruikt, wordt een tweede activiteit gemaakt op de publicatie-instantie:

* De activiteit op de auteurinstantie volgt activiteit op de auteursinstantie en is nuttig om de bezoekerservaring te simuleren. De analyses die voor deze activiteit worden geregistreerd, weerspiegelen slechts wat op de auteursinstantie voorkomt.
* De activiteit op de publicatie-instantie geeft de activiteit op de publicatieserver weer en reageert hierop. Dit is de activiteit die op de openbare website loopt. Alleen de publicatieactiviteit is relevant voor het bijhouden en analyseren van het gebruik van de feitelijke openbare site.

## Weergaveprestaties en het omzetten van wentelende ervaringen (A/B-test) {#viewing-performance-and-converting-winning-experiences-a-b-test}

U kunt de prestaties van elke Adobe Target-activiteit (XT of A/B) bekijken. Als u A/B tests gebruikt, kunt u het winnen ervaring ook omzetten, die dan de standaardervaring wordt.

Om de prestaties van de activiteit te bekijken en het winnen ervaringen om te zetten:

1. In **Personalisatie**, klik of tik **Activiteiten** om aan de **Activiteiten** console te navigeren.
1. Klik of tik op het merk waarvoor u activiteiten wilt zien.
1. Selecteer de activiteit, klik of tik op **Weergave-eigenschappen**, klik op het tabblad **Rapporten** en selecteer de activiteit waarvoor u prestaties wilt bekijken of waarvoor u winnende ervaringen wilt converteren. Prestatiedata worden weergegeven.

   ![chlimage_1-114](assets/chlimage_1-115.png)

1. Klik of tik **Push winnaar** verbinding om die ervaring als standaardervaring te duwen.

   Als u de winnaar omzet, gebeurt het volgende:

   * De huidige activiteit wordt uitgeschakeld
   * Hiermee wijzigt u alle pagina&#39;s en vervangt u de doelinhoud door de feitelijke inhoud van de winnende ervaring. De inhoud van de winnende ervaring wordt onderdeel van de normale pagina **zonder** het richten.

   ![chlimage_1-116](assets/chlimage_1-116.png)

   Een winnende ervaring is de ervaring die meer Lift in de rapporten produceert, die op de omrekeningskoers gebaseerd is.

1. Klik of tik **Ja** om te bevestigen dat u de winnaar wilt omzetten, de huidige ervaring uitschakelen en vervangen door de inhoud van de winnende ervaring.

## Synchroniseren van activiteiten met Adobe Target {#synchronizing-activities-with-adobe-target}

Activiteiten die gebruikmaken van de Adobe Target-doelengine worden gesynchroniseerd met Adobe Target-campagnes. Een activiteit wordt automatisch gesynchroniseerd met Adobe Target wanneer aan de volgende voorwaarden wordt voldaan:

* De activiteit bevat minstens één ervaring.
* Ten minste één ervaring bevat een toegewezen segment en één aanbieding.
* Elke ervaring in de activiteit moet hetzelfde aantal aanbiedingen hebben.

Deze voorwaarden gelden voor activiteiten met betrekking tot auteur- en publicatieinstanties.

Wanneer een activiteit wordt gesynchroniseerd, wordt een overeenkomstige campagne gecreeerd in Adobe Target:

* De activiteiten op het publicatieexemplaar hebben de zelfde naam zoals de overeenkomstige campagne van Adobe Target.
* De activiteiten op de auteurinstantie corresponderen met campagnes van het Doel van de zelfde naam met het `_author` achtervoegsel.

![chlimage_1-117](assets/chlimage_1-117.png)

De _auteuractiviteiten worden onmiddellijk gesynchroniseerd wanneer de activiteit wordt gewijzigd. De directe synchronisatie laat de simulatie van activiteiten met de Context of ContextHub van de Cliënt toe.

De publicatieactiviteiten worden gesynchroniseerd wanneer de activiteit wordt gepubliceerd naar de AEM-publicatie-instantie.

## Synchronisatie van probleemoplossingsactiviteiten {#troubleshooting-activity-synchronization}

Wanneer AEM een activiteit met Adobe Target synchroniseert, omvat AEM een bezit van de activiteit genoemd `thirdPartyId`. De waarde van deze eigenschap is gebaseerd op het pad van de activiteit in de AEM repository. Geen twee campagnes in Adobe Target kunnen de zelfde waarde voor het `thirdPartyId` bezit hebben. Daarom zal een activiteit er niet in slagen om te synchroniseren als een bestaande campagne (van een verschillend type AB, XT) in Adobe Target de zelfde waarde voor `thirdPartyId` gebruikt.

Deze situatie kan zich voordoen in de volgende omstandigheden:

1. Er wordt een activiteit gemaakt en gesynchroniseerd met Adobe Target.
1. Op een andere AEM wordt een activiteit onder hetzelfde merk en met dezelfde naam gemaakt. Synchronisatie van deze activiteit mislukt bij poging.

Deze situatie kan zich ook voordoen in de volgende omstandigheden:

1. Er wordt een activiteit gemaakt en gesynchroniseerd met Adobe Target. De activiteit wordt dan geschrapt op AEM.
1. Een activiteit wordt gecreeerd onder het zelfde merk en gebruikend de zelfde naam zoals de geschrapte activiteit. Synchronisatie van deze activiteit mislukt bij poging.

Gebruik altijd unieke namen voor activiteiten om synchronisatieproblemen te voorkomen. Als een activiteit er niet in slaagt te synchroniseren, kunt u de campagne in Adobe Target verwijderen die dezelfde naam gebruikt als die campagne niet wordt gebruikt.

>[!NOTE]
>
>Wanneer u een campagne in Adobe Target creeert, wijst het een bezit genoemd `thirdPartyId t`aan elke campagne toe. Wanneer u de campagne in Adobe Target verwijdert, wordt `thirdPartyId` niet verwijderd. U kunt `thirdPartyId` voor campagnes van verschillende types (AB, XT) niet opnieuw gebruiken en het kan niet manueel worden verwijderd. Geef elke campagne een unieke naam om dit probleem te voorkomen. campagnemenamen kunnen daarom niet opnieuw worden gebruikt in verschillende soorten campagnes.
>
>Als u dezelfde naam gebruikt in hetzelfde type campagne, overschrijft u de bestaande campagne.
>
>Als tijdens het synchroniseren de fout &quot;Verzoek is mislukt. `thirdPartyId` bestaat al.&quot; Wijzig de naam van de campagne en synchroniseer opnieuw.

