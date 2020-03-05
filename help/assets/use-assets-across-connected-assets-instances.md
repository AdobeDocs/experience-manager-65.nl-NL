---
title: Gebruik Verbonden Activa om activa DAM in het auteurswerkschema van de Plaatsen van de Manager van de Ervaring van Adobe te delen
description: De activa van het gebruik beschikbaar op een verre plaatsing van de Activa van de Manager van de Ervaring van Adobe wanneer het creëren van uw Web-pagina's op een andere plaatsing van de Plaats van de Manager van de Ervaring.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c4e6e74e091fe64b0a936b3f1bf95db7b6185956

---


# Gebruik Verbonden activa om activa DAM in de Plaatsen van AEM te delen {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In grote ondernemingen kan de infrastructuur die nodig is om websites te maken, worden verspreid. Soms kunnen de mogelijkheden van de websiteverwezenlijking en digitale activa die worden gebruikt om deze websites tot stand te brengen in verschillende plaatsingen verblijven. Een paar redenen kunnen geografisch verdeelde plaatsingen zijn die worden vereist om gelijktijdig te werken; overnames die leiden tot heterogene infrastructuren die de moedermaatschappij wil consolideren; groei die tot dergelijke schaal leidt dat de specifieke instantie voor activabeheer wordt vereist.

AEM Sites biedt mogelijkheden om webpagina&#39;s te maken en AEM Assets is het Digital Asset Management (DAM)-systeem dat de vereiste middelen voor websites levert. AEM ondersteunt nu het bovenstaande gebruiksscenario door AEM-sites en AEM-bedrijfsmiddelen te integreren.

## Overzicht van Verbonden activa {#overview-of-connected-assets}

Wanneer het uitgeven van pagina&#39;s in de Redacteur van de Pagina, kunnen de auteurs foutloos zoeken, doorbladeren, en activa van een verschillende plaatsing van de Activa inbedden AEM. Een AEM-beheerder doen een eenmalige integratie van een lokale implementatie van AEM-sites met een andere (externe) implementatie van AEM-bedrijfsmiddelen.

Voor de auteurs van Plaatsen, zijn de verre activa beschikbaar als read-only lokale activa. De functionaliteit steunt naadloos onderzoek en gebruik van een paar verre activa tegelijkertijd. Om vele verre activa beschikbaar te maken bij lokale plaatsing in één keer, denk na migrerend de activa in bulk. Zie de [migratiegids](/help/assets/assets-migration-guide.md)voor bedrijfsmiddelen.

### Vereisten en ondersteunde implementaties {#prerequisites}

Alvorens u gebruikt of dit vermogen vormt, verzeker het volgende:

* De gebruikers maken deel uit van aangewezen gebruikersgroepen op elke plaatsing.
* Voor de plaatsingstypes van de Manager van de Ervaring van Adobe, wordt aan één van het gesteunde criterium voldaan. AEM 6.5 Activa werkt met AEM als cloudservice. Voor meer informatie, zie de [Verbonden functionaliteit van Activa in AEM als Dienst](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html)van de Wolk.

   |  | AEM Sites as a Cloud Service | AEM 6.5-locaties op AMS | AEM 6.5 Locaties op locatie |
   |---|---|---|---|
   | **AEM Assets as a Cloud Service** | Gesteund | Gesteund | Gesteund |
   | **AEM 6.5 Activa op AMS** | Gesteund | Gesteund | Gesteund |
   | **AEM 6.5 Activa op locatie** | Niet ondersteund | Niet ondersteund | Niet ondersteund |

### Ondersteunde bestandsindelingen {#mimetypes}

De auteurs kunnen naar beelden en de volgende types van documenten in de Vinder van de Inhoud zoeken en de gezochte activa in de Redacteur van de Pagina gebruiken. De documenten kunnen aan de `Download` component worden toegevoegd en de beelden kunnen aan de `Image` component worden toegevoegd. De auteurs kunnen de verre activa in om het even welke douaneAEM component ook toevoegen die het gebrek `Download` of de `Image` componenten uitbreidt. De lijst van gesteunde formaten is:

* **Afbeeldingsformaten**: De beeldformaten die door de component [van het](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/image.html) Beeld worden gesteund worden gesteund door Verbonden Activa. De dynamische Componenten van Media worden niet gesteund.
* **Documentformaten**: Zie [Verbonden activa gesteunde documentformaten](assets-formats.md#supported-document-formats).

### Gebruikers en betrokken groepen {#users-and-groups-involved}

De diverse rollen die betrokken zijn om het vermogen en hun overeenkomstige gebruikersgroepen te vormen en te gebruiken worden hieronder beschreven. Het lokale werkingsgebied wordt gebruikt voor het gebruiksgeval waar een Web-pagina door een auteur wordt gecreeerd. Het verre werkingsgebied wordt gebruikt voor de plaatsing DAM die de vereiste activa ontvangt. De auteur van Plaatsen haalt deze verre activa.

| Rol | Toepassingsgebied | Gebruikersgroep | Gebruikersnaam in doorloop | Voorschrift |
|----------------------------------|--------|------------------------------------------------------------------------------|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beheerder van AEM-sites | Lokaal | AEM-beheerder | `admin` | De opstelling AEM, vormt integratie met de verre plaatsing van Activa. |
| DAM-gebruiker | Lokaal | Author | `ksaner` | Gebruikt om de gehaald activa bij te bekijken en te dupliceren `/content/DAM/connectedassets/`. |
| auteur van AEM Sites | Lokaal | Auteur (met gelezen toegang op verre DAM en auteurstoegang op lokale Plaatsen) | `ksaner` | De eindgebruiker is de auteurs van Plaatsen die deze integratie gebruiken om hun inhoudssnelheid te verbeteren. De auteurs zoeken en doorbladeren activa in verre DAM gebruikend de Vinder van de Inhoud en het gebruiken van de vereiste beelden in lokale Web-pagina&#39;s. De geloofsbrieven van de gebruiker van `ksaner` DAM worden gebruikt. |
| AEM-middelenbeheerder | Afstandsbediening | AEM-beheerder | `admin` op externe AEM | Vorm het Middel delen van de dwars-Oorsprong (CORS). |
| DAM-gebruiker | Afstandsbediening | Author | `ksaner` op externe AEM | De rol van de auteur op de verre plaatsing AEM. Zoek en doorblader activa in Verbonden Activa gebruikend de Vinder van de Inhoud. |
| DAM-distributeur (technische gebruiker) | Afstandsbediening | verpakkers en plaatsauteurs | `ksaner` op externe AEM | Deze gebruiker huidig op de verre plaatsing wordt gebruikt door lokale server AEM (niet de de auteursrol van de Plaats) om de verre activa, namens de auteur van Plaatsen te halen. Deze rol is niet het zelfde als boven twee `ksaner` rollen en behoort tot een verschillende gebruikersgroep. |

## Vorm een verbinding tussen Plaatsen en de plaatsingen van Activa {#configure-a-connection-between-sites-and-assets-deployments}

Een beheerder AEM kan deze integratie tot stand brengen. Zodra gecreeerd, worden de toestemmingen die worden vereist om het te gebruiken gevestigd via gebruikersgroepen die op de plaatsing van Plaatsen en op de plaatsing DAM worden bepaald.

Om Verbonden Activa en de lokale connectiviteit van Plaatsen te vormen, volg deze stappen.

1. Heb toegang tot een bestaande plaatsing van de Plaatsen AEM of creeer een plaatsing gebruikend het volgende bevel:

   1. In de omslag van het JAR- dossier, voer het volgende bevel op een terminal uit om elke server tot stand te brengen AEM.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. Na een paar minuten begint de AEM-server met succes. Beschouw deze implementatie van AEM-sites als de lokale machine voor het maken van webpagina&#39;s, bijvoorbeeld op `https://[local_sites]:4502`.

1. Ervoor zorgen dat de gebruikers en rollen met lokaal bereik aanwezig zijn op de implementatie van AEM-sites en op de implementatie van AEM-bedrijfsmiddelen op AMS. Creeer een technische gebruiker op de plaatsing van Activa en voeg aan de gebruikersgroep toe die in betrokken [gebruikers en groepen wordt vermeld](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Heb toegang tot de lokale plaatsing van Plaatsen AEM bij `https://[local_sites]:4502`. Klik **[!UICONTROL Hulpmiddelen]** > **[!UICONTROL Activa]** > de Configuratie **[!UICONTROL van]** Verbonden Activa en verstrek de volgende waarden:

   1. De locatie van AEM-bedrijfsmiddelen is `https://[assets_servername_ams]:[port]`.
   1. Geloofsbrieven van een distributeur DAM (technische gebruiker).
   1. Op het gebied van het Punt **[!UICONTROL van de]** Onderstel, ga de lokale weg AEM in waar AEM de activa haalt. Bijvoorbeeld, `remoteassets` omslag.

   1. Pas de waarden van de **[!UICONTROL Originele Binaire Drempel van de overdrachtoptimalisering]** afhankelijk van uw netwerk aan. Een activavertolking met een grootte die groter is dan deze drempel, wordt asynchroon overgebracht.
   1. Selecteer **[!UICONTROL Datastore die met Verbonden Activa]** wordt gedeeld, als u een datastore gebruikt om uw activa op te slaan en de Datastore is de gemeenschappelijke opslag tussen beide plaatsingen AEM. In dit geval is de drempelwaarde niet van belang, aangezien de eigenlijke binaire activa op de datastore verblijven en niet worden overgedragen.
   ![Een typische configuratie voor Verbonden Activa](assets/connected-assets-typical-config.png)

   *Afbeelding: Een typische configuratie voor Verbonden Activa*

1. Aangezien de activa reeds worden verwerkt en de rendities worden gehaald, maak de werkschemalanceerders onbruikbaar. Pas de lanceringsconfiguraties op de lokale (de Plaatsen van AEM) plaatsing aan om de `connectedassets` omslag uit te sluiten, waarin de verre activa worden gehaald.

   1. Voor plaatsing van de Plaatsen AEM, klik **[!UICONTROL Hulpmiddelen]** > **[!UICONTROL Werkschema]** > **[!UICONTROL Lanceringen]**.

   1. Zoek naar Lanceringen met werkschema&#39;s als Activa **[!UICONTROL van de Update van]** DAM en de Terugkeer van de Meta-gegevens van **[!UICONTROL DAM]**.

   1. Selecteer de werkschemalanceerinrichting en klik **[!UICONTROL Eigenschappen]** op de actiebar.

   1. In de tovenaar van Eigenschappen, verander de gebieden van de **[!UICONTROL Weg]** als volgende afbeeldingen om hun regelmatige uitdrukkingen bij te werken om het ophangpunt **[!UICONTROL verbonden activa]** uit te sluiten.
   | Voor | Na |
   |---|---|
   | /content/dam(/(?!/subassets).*/)rendities/oorspronkelijk | /content/dam(/(?!/subassets)(?!connectedassets).)*/)rendities/oorspronkelijk |
   | /content/dam(/...*/)rendities/oorspronkelijk | /content/dam(/(?!connectedassets).*/)rendities/oorspronkelijk |
   | /content/dam(/...*)/jcr:inhoud/metagegevens | /content/dam(/(?!connectedassets).*/)jcr:inhoud/metagegevens |

   >[!NOTE]
   >
   >Alle rendities die op de verre plaatsing beschikbaar zijn AEM worden gehaald, wanneer de auteurs activa halen. Als u meer rendities van een gehaalde activa wilt tot stand brengen, sla deze configuratiestap over. Het werkschema van de Activa van de Update van DAM wordt teweeggebracht en leidt tot meer rendities. Deze rendities zijn beschikbaar slechts op de lokale plaatsing van Plaatsen en niet op de verre plaatsing DAM.

1. Voeg de instantie van de Plaatsen AEM als één van de **[!UICONTROL Toegestane Oorsprong]** op de verre configuratie CORS van de Activa van AEM toe.

   1. Login die de beheerdergeloofsbrieven gebruikt. Zoeken naar crossorigine. De **[!UICONTROL Hulpmiddelen]** van de toegang > **[!UICONTROL Verrichtingen]** > de Console **[!UICONTROL van het]** Web.

   1. Om een configuratie CORS voor de instantie van Plaatsen te creëren AEM, klik ![aem_assets_add_icon](assets/aem_assets_add_icon.png) pictogram naast het het Delen van het Middel van het **[!UICONTROL Middel van de Graniet van]** Adobe het Van verschillende herkomst.

   1. Op het gebied **[!UICONTROL Toegestane Oorsprong]**, voer URL van de lokale Plaatsen in, namelijk, `https://[local_sites]:[port]`. Sparen de configuratie.

## Externe middelen gebruiken {#use-remote-assets}

De websiteauteurs gebruiken de Vinder van de Inhoud om met de instantie te verbinden DAM. De auteurs kunnen doorbladeren, zoeken naar, en de verre activa in een component slepen. Om aan verre DAM voor authentiek te verklaren, houd de geloofsbrieven van de gebruiker van DAM die door uw beheerder handig wordt verstrekt.

De auteurs kunnen de activa gebruiken beschikbaar op zowel, lokale DAM als de verre instanties DAM, in één enkele Web-pagina. Gebruik de Vinder van de Inhoud om tussen het zoeken van lokale DAM of het zoeken van verre DAM te schakelen.

Slechts worden die markeringen van verre activa gehaald die nauwkeurig een corresponderende markering-met zelfde taxonomie hiërarchie-beschikbaar op de lokale instantie van Plaatsen hebben. Andere tags worden weggegooid. De auteurs kunnen naar verre activa zoeken gebruikend alle markeringen aanwezig op de verre plaatsing AEM, aangezien AEM een full-text onderzoek aanbiedt.

### Doorloop van het gebruik {#walk-through-of-usage}

Gebruik de bovengenoemde opstelling om de auteurservaring te proberen om te begrijpen hoe de functionaliteit werkt. Gebruik documenten of beelden van uw keus op de verre plaatsing DAM.

1. Navigeer aan de Activa UI op de verre plaatsing door tot **[!UICONTROL Activa]** > **[!UICONTROL Dossiers]** van werkruimte toegang te hebben AEM. Alternatief, toegang `https://[assets_servername_ams]:[port]/assets.html/content/dam` in browser. Upload de middelen van uw keus.
1. Voor de instantie van Plaatsen, in de profielactivator in de hoger-juiste hoek, **[!UICONTROL Impersonate de klik zoals]**. Verstrek `ksaner` als gebruikersnaam, selecteer de verstrekte optie, en klik **[!UICONTROL O.K.]**.
1. Open een website We.Retail op **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL ons]** > **[!UICONTROL en]**. Bewerk de pagina. Alternatief, toegang `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` in browser om een pagina uit te geven.

   Klik het Zijpaneel van de **[!UICONTROL Knevel]** op upper-left hoek van de pagina.

1. Open het lusje van Activa en klik **[!UICONTROL login aan Verbonden Activa]**.
1. Verstrek de geloofsbrieven — `ksaner` als gebruikersnaam en `password` als wachtwoord. Deze gebruiker heeft auteurstoestemmingen op beide plaatsingen AEM.
1. Zoek naar de activa die u aan DAM toevoegde. De verre activa worden getoond in het linkerpaneel. Filter voor afbeeldingen of documenten en filter voor typen ondersteunde documenten. Sleep de beelden op een `Image` component en documenten op een `Download` component.

   De opgehaalde activa zijn read-only op de lokale plaatsing van Plaatsen AEM. U kunt de opties nog gebruiken die door uw componenten van Plaatsen AEM worden verstrekt om de gehaalde activa uit te geven. Het uitgeven door componenten is niet destructief.

   ![Opties om documenttypes en beelden te filtreren wanneer het zoeken van activa op verre DAM](assets/filetypes_filter_connected_assets.png)

   *Afbeelding: Opties om documenttypes en beelden te filtreren wanneer het zoeken van activa op verre DAM*

1. Een websiteauteur wordt op de hoogte gebracht als een activa asynchroon wordt gehaald en als om het even welke haaltaak ontbreekt. Terwijl creatie of zelfs na creatie, kunnen de auteurs gedetailleerde informatie over haaltaken en fouten in het [async banen](/help/assets/asynchronous-jobs.md) gebruikersinterface zien.

   ![Bericht over het asynchrone halen van activa die op de achtergrond gebeurt.](assets/assets_async_transfer_fails.png)

   *Afbeelding: Bericht over het asynchrone halen van activa die op de achtergrond gebeurt.*

1. Wanneer het publiceren van een pagina, toont AEM een volledige lijst van activa die in de pagina worden gebruikt. Zorg ervoor dat de verre activa met succes op het tijdstip van het publiceren worden gehaald. Om het statuut van elke gehaald activa te controleren, zie [async banen](/help/assets/asynchronous-jobs.md) gebruikersinterface.

   >[!NOTE]
   >
   >Zelfs als één of meerdere verre activa niet worden gehaald, wordt de pagina gepubliceerd. De component die de verre activa gebruikt wordt gepubliceerd leeg. Het AEM- berichtgebied toont bericht voor fouten die in async baanpagina tonen.

>[!CAUTION]
>
>Zodra gebruikt in een Web-pagina, zijn de gehaalde verre activa doorzoekbaar en bruikbaar door iedereen die toestemmingen heeft om tot de lokale omslag toegang te hebben waar de gehaalde activa (`connectedassets` in de bovengenoemde loop-door) worden opgeslagen. De middelen kunnen ook worden doorzocht en kunnen in de lokale repository worden weergegeven via [!UICONTROL Content Finder].

De gehaalde activa kunnen als andere lokale activa worden gebruikt, behalve dat de bijbehorende meta-gegevens niet kunnen worden uitgegeven.

## Beperkingen {#limitations}

**Toestemmingen en beheer van activa**

* De lokale activa worden niet gesynchroniseerd met de originele activa op de verre plaatsing. Om het even welk geeft, schrappingen, of het intrekken van toestemmingen op de plaatsing uit DAM worden niet verspreid stroomafwaarts.
* De lokale activa zijn read-only exemplaren. AEM-componenten worden niet-destructief bewerkt aan bedrijfsmiddelen. Geen andere bewerkingen zijn toegestaan.
* De plaatselijk gehaalde activa zijn beschikbaar voor auteursdoeleinden slechts. De de updatewerkschema&#39;s van activa kunnen niet worden toegepast en de meta-gegevens kunnen niet worden uitgegeven.
* Slechts worden de beelden en de vermelde documentformaten gesteund. De dynamische activa van Media, de Fragmenten van de Inhoud, en de Fragmenten van de Ervaring worden niet gesteund.
* De schema&#39;s van meta-gegevens worden niet gehaald.
* Alle Auteurs van Plaatsen hebben toestemmingen op de gehaalde exemplaren gelezen, zelfs als zij geen toegang tot de verre plaatsing DAM hebben.
* Geen API steun om de integratie aan te passen.
* De functionaliteit ondersteunt naadloos zoeken en gebruiken van externe bedrijfsmiddelen. Om vele verre activa beschikbaar te maken bij lokale plaatsing in één keer, denk na migrerend de activa. Zie de [migratiegids](assets-migration-guide.md)voor bedrijfsmiddelen.
* Het is niet mogelijk om verre activa als paginaduimnagel op het gebruikersinterface van de Eigenschappen [!UICONTROL van de] Pagina te gebruiken. U kunt een duimnagel van een Web-pagina in de gebruikersinterface van de Eigenschappen [!UICONTROL van de] Pagina van de [!UICONTROL Duimnagel] plaatsen door Beeld [!UICONTROL te klikken te]selecteren.

**Opstelling en vergunning**

* De implementatie van AEM-bedrijfsmiddelen op AMS wordt ondersteund.
* AEM-sites kunnen tegelijk verbinding maken met één AEM-bedrijfsmiddelenopslagplaats.
* Een licentie van AEM Assets die werkt als externe opslagplaats.
* Één of meerdere vergunningen van de Plaatsen van AEM die als lokale auteursplaatsing werken.

**Gebruik**

* Slechts zoekt de gesteunde functionaliteit naar verre activa en sleept de verre activa op lokale pagina aan auteursinhoud.
* De werktijden van de trek uit na 5 seconden. De auteurs kunnen kwesties hebben die activa halen, zeggen als er netwerkkwesties zijn. De auteurs kunnen opnieuw proberen door de verre activa van de Vinder [!UICONTROL van de] Inhoud aan de Redacteur [!UICONTROL van de]Pagina te slepen.
* Eenvoudig geeft uit die niet-destructief zijn en uitgeeft gesteund via de `Image` component AEM, kan op opgehaalde activa worden gedaan. Activa zijn alleen-lezen.

## Problemen oplossen {#troubleshoot}

Volg deze stappen om voor de gemeenschappelijke foutenscenario&#39;s problemen op te lossen:

* Als u niet naar verre activa van de Vinder van de Inhoud kunt zoeken, controleer opnieuw en zorg ervoor dat de vereiste rollen en de toestemmingen op zijn plaats zijn.
* Een van de verre dam gehaald activa kan niet op een Web-pagina om de volgende redenen worden gepubliceerd: het bestaat niet op ver; het ontbreken van de juiste machtigingen om het op te halen; netwerkstoring. Zorg ervoor dat de activa niet wordt verwijderd uit verre DAM of de toestemmingen niet worden veranderd; ervoor te zorgen dat aan passende voorwaarden wordt voldaan; probeer toevoegend de activa aan de pagina opnieuw en publiceer opnieuw. Controleer de [lijst van asynchrone banen](/help/assets/asynchronous-jobs.md) fouten in activa het halen.
