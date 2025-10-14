---
title: Connected Assets gebruiken om DAM-elementen te delen in  [!DNL Sites]
description: De activa van het gebruik beschikbaar op een verre  [!DNL Adobe Experience Manager Assets]  plaatsing wanneer het creëren van uw Web-pagina's op een andere  [!DNL Adobe Experience Manager Sites]  plaatsing.
contentOwner: AK
mini-toc-levels: 2
role: User, Admin, Leader
feature: Connected Assets,User and Groups
exl-id: 4ceb49d8-b619-42b1-81e7-c3e83d4e6e62
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3792'
ht-degree: 14%

---

# Connected Assets gebruiken om DAM-middelen te delen in [!DNL Experience Manager Sites] {#use-connected-assets-to-share-dam-assets-in-aem-sites}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/use-assets-across-connected-assets-instances.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


In grote ondernemingen is de infrastructuur voor het maken van websites soms gedistribueerd. Soms zijn de functies en de digitale assets voor het maken van websites opgenomen in verschillende implementaties. Één reden kan geografisch gedistribueerde bestaande plaatsingen zijn die worden vereist om samen te werken. Een andere reden kunnen overnames zijn die leiden tot heterogene infrastructuren, waaronder verschillende [!DNL Experience Manager] -versies, die het moederbedrijf samen wil gebruiken.

De Connected Assets-functionaliteit ondersteunt de bovenstaande gebruiksscenario&#39;s door [!DNL Experience Manager Sites] en [!DNL Experience Manager Assets] te integreren. Gebruikers kunnen in [!DNL Sites] webpagina&#39;s maken die de digitale elementen van afzonderlijke [!DNL Assets] -implementaties gebruiken.

>[!NOTE]
>
>Configureer Connected Assets alleen wanneer u de middelen moet gebruiken die beschikbaar zijn op een externe DAM-implementatie op een aparte Sites-implementatie voor het ontwerpen van webpagina&#39;s.

## Overzicht van Connected Assets {#overview-of-connected-assets}

Wanneer de auteurs pagina&#39;s in [!UICONTROL Page Editor] als doeldoel bewerken, kunnen ze elementen van een andere [!DNL Assets] -implementatie die als bron van elementen fungeert, naadloos zoeken, doorbladeren en insluiten. De beheerders maken een eenmalige integratie van een implementatie van [!DNL Experience Manager] met [!DNL Sites] mogelijkheden met een andere implementatie van [!DNL Experience Manager] met [!DNL Assets] mogelijkheden. Siteauteurs kunnen ook Dynamic Media-afbeeldingen op de webpagina&#39;s van hun site gebruiken via Connected Assets en de Dynamic Media-functies gebruiken, zoals slimme voorinstellingen voor uitsnijden en afbeeldingen.

Voor de [!DNL Sites] -auteurs zijn de externe elementen beschikbaar als alleen-lezen lokale elementen. De functionaliteit ondersteunt naadloze zoekopdrachten en toegang tot externe middelen in de Site-editor. Als u andere gebruiksgevallen wilt gebruiken waarvoor het volledige assetcorpus op Sites beschikbaar moet zijn, kunt u overwegen de middelen in bulk te migreren in plaats van Connected Assets te gebruiken. Zie [&#x200B; de migratiegids van Experience Manager Assets &#x200B;](/help/assets/assets-migration-guide.md).

### Vereisten en ondersteunde implementaties {#prerequisites}

Controleer de volgende punten voordat u deze functie gebruikt of configureert:

* De gebruikers maken deel uit van de aangewezen gebruikersgroepen op elke plaatsing.
* Voor [!DNL Adobe Experience Manager] -implementatietypen is aan een van de ondersteunde criteria voldaan. [!DNL Experience Manager] 6.5 [!DNL Assets] werkt met [!DNL Experience Manager] as a Cloud Service. Voor meer informatie over hoe deze functionaliteit in [!DNL Experience Manager] als a [!DNL Cloud Service] werkt, zie [&#x200B; Verbonden Assets in Experience Manager as a Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/use-assets-across-connected-assets-instances.html?lang=nl-NL).

  | | [!DNL Sites] als een [!DNL Cloud Service] | [!DNL Experience Manager] 6.5 [!DNL Sites] op AMS | [!DNL Experience Manager] 6.5 [!DNL Sites] on-premise |
  |---|---|---|---|
  | **[!DNL Experience Manager Assets]als een[!DNL Cloud Service]** | Ondersteund | Ondersteund | Ondersteund |
  | **[!DNL Experience Manager]6.5 [!DNL Assets] op AMS** | Ondersteund | Ondersteund | Ondersteund |
  | **[!DNL Experience Manager]6.5 [!DNL Assets] on-premise** | Niet ondersteund | Niet ondersteund | Niet ondersteund |

### Ondersteunde bestandsindelingen {#mimetypes}

Auteurs zoeken naar afbeeldingen en de volgende typen documenten in de Inhoudszoeker en slepen de gezochte elementen in de Pagina-editor. Documenten worden toegevoegd aan de component `Download` en afbeeldingen aan de component `Image` . Auteurs kunnen ook de externe elementen toevoegen in elke aangepaste [!DNL Experience Manager] -component die de standaardcomponenten `Download` of `Image` uitbreidt. De ondersteunde indelingen zijn:

* **formaten van het Beeld**: De formaten die de [&#x200B; component van het Beeld &#x200B;](assets-formats.md#supported-raster-image-formats) steunt.
* **formaten van het Document**: Zie [&#x200B; gesteunde documentformaten &#x200B;](assets-formats.md#supported-document-formats).

### Betrokken gebruikers en groepen {#users-and-groups-involved}

Hieronder worden de diverse rollen beschreven voor de configuratie en toepassing van een kenmerk en de overeenkomstige gebruikersgroepen. Het lokale bereik wordt gebruikt voor het geval waarin een auteur een webpagina maakt. De externe scope wordt gebruikt voor de DAM-implementatie die als host fungeert voor de vereiste assets. De auteur [!DNL Sites] haalt deze externe elementen op.

| Rol | Scope | Gebruikersgroep | Gebruikersnaam in voorbeeldprocedure | Beschrijvingen |
|---|---|---|---|---|
| [!DNL Sites] beheerder | Lokaal | [!DNL Experience Manager] `administrators` | `admin` | Stel [!DNL Experience Manager] in en configureer integratie met de externe [!DNL Assets] -implementatie. |
| DAM-gebruiker | Lokaal | `Authors` | `ksaner` | Wordt gebruikt om de assets die bij `/content/DAM/connectedassets/` zijn opgehaald, weer te geven en te dupliceren. |
| [!DNL Sites] auteur | Lokaal | <ul><li>`Authors` (met leestoegang op de externe DAM en toegang tot de auteur op de lokale computer [!DNL Sites] ) </li> <li>`dam-users` op lokaal [!DNL Sites]</li></ul> | `ksaner` | Eindgebruikers zijn [!DNL Sites] auteurs die deze integratie gebruiken om de snelheid van hun inhoud te verbeteren. De auteurs zoeken naar elementen in externe DAM en bladeren door deze elementen met behulp van [!UICONTROL Content Finder] en gebruiken de vereiste afbeeldingen op lokale webpagina&#39;s. De referenties van de `ksaner` DAM-gebruiker worden gebruikt. |
| [!DNL Assets] beheerder | Extern | [!DNL Experience Manager] `administrators` | `admin` op extern [!DNL Experience Manager] | Configureer CORS (Cross-Origin Resource Sharing). |
| DAM-gebruiker | Extern | `Authors` | `ksaner` op extern [!DNL Experience Manager] | Auteurrol bij de externe [!DNL Experience Manager] -implementatie. Zoek en blader middelen in Verbonden Assets gebruikend [!UICONTROL Content Finder]. |
| DAM-distributeur (technische gebruiker) | Extern | [!DNL Sites] `Authors` | `ksaner` op extern [!DNL Experience Manager] | Deze gebruiker die aanwezig is op de externe implementatie, wordt door de lokale server van [!DNL Experience Manager] (niet door de auteurrol van [!DNL Sites] ) gebruikt om de externe middelen op te halen, namens de auteur van [!DNL Sites] . Deze rol is anders dan de twee bovenstaande `ksaner`-rollen en hoort bij een andere gebruikersgroep. |

### Connected Assets-architectuur {#connected-assets-architecture}

Met Experience Manager kunt u een externe DAM-implementatie als bron aansluiten op meerdere Experience Manager [!DNL Sites] -implementaties. U kunt echter een [!DNL Sites] -implementatie verbinden met slechts één externe DAM-implementatie.

Evalueer het optimale aantal instanties van Plaatsen om met een verre plaatsing te verbinden DAM. De Adobe adviseert om instanties van Plaatsen aan de plaatsing en test incrementeel aan te sluiten dat er geen prestatieseffect bij verre DAM is, aangezien elke verbonden instantie van Plaatsen aan het gegevensverkeer op verre DAM bijdraagt.

De volgende diagrammen illustreren de gesteunde scenario&#39;s:

![&#x200B; Verbonden architectuur van Assets &#x200B;](assets/connected-assets-architecture.png)

Het volgende diagram illustreert een niet-ondersteund scenario:

![&#x200B; Verbonden architectuur van Assets &#x200B;](assets/connected-assets-architecture-unsupported.png)

## Een verbinding configureren tussen [!DNL Sites] - en [!DNL Assets] -implementaties {#configure-a-connection-between-sites-and-assets-deployments}

Een [!DNL Experience Manager] -beheerder kan deze integratie maken. Zodra gecreeerd, worden de toestemmingen die worden vereist om het te gebruiken gevestigd via gebruikersgroepen. De gebruikersgroepen worden gedefinieerd voor de [!DNL Sites] -implementatie en de DAM-implementatie.

Voer de volgende stappen uit om Connected Assets en de lokale [!DNL Sites] connectiviteit te configureren:

1. Open een bestaande [!DNL Sites] implementatie of maak een implementatie met de volgende opdracht:

   1. Voer in de map van het JAR-bestand de volgende opdracht uit op een terminal om elke [!DNL Experience Manager] -server te maken.

      `java -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. Na een paar minuten wordt de [!DNL Experience Manager] -server gestart. U kunt deze [!DNL Sites] -implementatie beschouwen als de lokale computer voor het ontwerpen van webpagina&#39;s, bijvoorbeeld `https://[local_sites]:4502` .

1. Zorg ervoor dat de gebruikers en rollen met het juiste bereik aanwezig zijn op de [!DNL Sites] -implementatie en op de [!DNL Assets] -implementatie op AMS. Creeer een technische gebruiker op [!DNL Assets] plaatsing en voeg aan de gebruikersgroep toe die in [&#x200B; wordt vermeld betrokken gebruikers en groepen &#x200B;](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Open de lokale [!DNL Sites] implementatie op `https://[local_sites]:4502` . Klik op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Connected Assets Configuration]** en geef de volgende waarden op:

   1. Een **[!UICONTROL Title]** van de configuratie.
   1. **[!UICONTROL Remote DAM URL]** is de URL van de [!DNL Assets] -locatie in de notatie `https://[assets_servername]:[port]` .
   1. Referenties van een DAM-distributeur (technische gebruiker).
   1. Voer in het veld **[!UICONTROL Mount Point]** het lokale [!DNL Experience Manager] pad in waar [!DNL Experience Manager] de elementen ophaalt. Bijvoorbeeld de map `remoteassets` . De elementen die van DAM worden opgehaald, worden in deze map opgeslagen op de [!DNL Sites] -implementatie.
   1. **[!UICONTROL Local Sites URL]** is de locatie van de [!DNL Sites] -implementatie. [!DNL Assets] -implementatie gebruikt deze waarde om verwijzingen te behouden naar de digitale elementen die door deze [!DNL Sites] -implementatie worden opgehaald.
   1. Referenties van [!DNL Sites] technische gebruiker.
   1. De waarde van het veld **[!UICONTROL Original Binary transfer optimization Threshold]** geeft aan of de oorspronkelijke elementen (inclusief de uitvoeringen) al dan niet synchroon worden overgedragen. Assets met een kleinere bestandsgrootte kan gemakkelijk worden opgehaald terwijl middelen met een relatief grotere bestandsgrootte het beste asynchroon kunnen worden gesynchroniseerd. De waarde hangt van uw netwerkmogelijkheden af.
   1. Selecteer **[!UICONTROL Datastore Shared with Connected Assets]** als u een datastore gebruikt om uw elementen op te slaan en de Datastore wordt gedeeld tussen beide implementaties. In dit geval is de drempellimiet niet van belang omdat de werkelijke binaire activa op de datastore beschikbaar zijn en niet worden overgedragen.

   ![&#x200B; een typische configuratie voor Verbonden functionaliteit van Assets &#x200B;](assets/connected-assets-typical-config.png)

   *Cijfer: Een typische configuratie voor Verbonden functionaliteit van Assets.*

1. De bestaande digitale elementen bij [!DNL Assets] -implementatie worden al verwerkt en de uitvoeringen worden gegenereerd. Deze vertoningen worden opgehaald gebruikend deze functionaliteit zodat is er geen behoefte om de vertoningen opnieuw te produceren. Schakel de workflowdraagprogramma&#39;s uit om te voorkomen dat uitvoeringen opnieuw worden gegenereerd. Pas de startconfiguraties van de ([!DNL Sites]) plaatsing aan om de `connectedassets` omslag (de activa worden gehaald in deze omslag) uit te sluiten.

   1. Klik bij [!DNL Sites] -implementatie op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]** .

   1. Zoek naar startprogramma&#39;s met workflows als **[!UICONTROL DAM Update Asset]** en **[!UICONTROL DAM Metadata Writeback]**.

   1. Selecteer het workflowstartprogramma en klik op **[!UICONTROL Properties]** op de actiebalk.

   1. Wijzig in de wizard [!UICONTROL Properties] de velden **[!UICONTROL Path]** als de volgende toewijzingen om de reguliere expressies bij te werken, zodat het koppelingspunt niet wordt opgenomen **[!UICONTROL connectedassets]** .

   | Voor | Na |
   |---|---|
   | `/content/dam(/((?!/subassets).)*/)renditions/original` | `/content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*/)renditions/original` | `/content/dam(/((?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*)/jcr:content/metadata` | `/content/dam(/((?!connectedassets).)*/)jcr:content/metadata` |

   >[!NOTE]
   >
   >Alle uitvoeringen die beschikbaar zijn op de externe implementatie worden opgehaald, wanneer auteurs middelen ophalen. Als u meer weergaven van een opgehaalde asset tot stand wilt brengen, moet u deze configuratiestap overslaan. De [!UICONTROL DAM Update Asset] -workflow wordt geactiveerd en er worden meer uitvoeringen gemaakt. Deze uitvoeringen zijn alleen beschikbaar bij de lokale [!DNL Sites] implementatie en niet bij de externe DAM-implementatie.

1. Voeg de [!DNL Sites] -implementatie toe als een toegestane oorsprong in de CORS-configuratie voor de [!DNL Assets] -implementatie. Voor meer informatie, zie [&#x200B; CORS &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing.html?lang=nl-NL) begrijpen.

1. Vorm [&#x200B; de zelfde steun van het plaatskoekje &#x200B;](/help/sites-administering/same-site-cookie-support.md).

U kunt de connectiviteit tussen geconfigureerde [!DNL Sites] implementaties en [!DNL Assets] -implementatie controleren.

![&#x200B; Verbindingstest van Verbonden Assets gevormd [!DNL Sites]](assets/connected-assets-multiple-config.png)
*Cijfer: De test van de Verbinding van Verbonden gevormde Assets [!DNL Sites].*

## Dynamic Media-middelen gebruiken {#dynamic-media-assets}


Met Connected Assets kunt u afbeeldingselementen gebruiken die door [!DNL Dynamic Media] zijn verwerkt vanaf de externe DAM-implementatie op sitepagina&#39;s, en Dynamic Media-functies gebruiken, zoals voorinstellingen voor slimme uitsnijdingen en afbeeldingen.

Als u [!DNL Dynamic Media] wilt gebruiken met Connected Assets:

1. Configureer [!DNL Dynamic Media] op externe DAM-implementatie met de synchronisatiemodus ingeschakeld.
1. Vorm [&#x200B; Verbonden Assets &#x200B;](#configure-a-connection-between-sites-and-assets-deployments).
1. Configureer [!DNL Dynamic Media] op de Sites-instantie met dezelfde bedrijfsnaam als die is geconfigureerd op de externe DAM. De plaatsing van Plaatsen moet read-only toegang tot de rekening van Dynamic Media hebben om met verbonden activa te werken. Zorg er daarom voor dat u de synchronisatiemodus in Dynamic Media-configuratie op de Sites-instantie uitschakelt.

>[!CAUTION]
>
>Met Connected Assets en de [!DNL Dynamic Media] -configuratie kunt u [!DNL Dynamic Media] niet gebruiken om lokale elementen die beschikbaar zijn op de [!DNL Sites] -implementatie te verwerken.

## Configureren [!DNL Dynamic Media] {#configure-dynamic-media}

Om [!DNL Dynamic Media] op [!DNL Assets] en [!DNL Sites] plaatsingen te vormen:

1. Schakel [!DNL Dynamic Media] in en configureer het als algemene configuratie op een externe [!DNL Assets] -auteursplaatsing. Om Dynamic Media te vormen, zie [&#x200B; Dynamic Media &#x200B;](/help/assets/config-dynamic.md#configuring-dynamic-media-cloud-services) vormen.
Bij externe [!DNL Assets] -implementatie selecteert u [!UICONTROL Dynamic Media sync mode] in **[!UICONTROL Enabled by default]** .

1. Creeer de Verbonden configuratie van Assets zoals die in [&#x200B; wordt beschreven vormt verbinding tussen plaatsen en activa plaatsingen &#x200B;](#configure-a-connection-between-sites-and-assets-deployments). Selecteer ook de optie **[!UICONTROL Fetch Original Rendition for Dynamic Media Connected Assets]** .

1. Configureer [!DNL Dynamic Media] op lokale [!DNL Sites] en externe [!DNL Assets] implementaties. Volg de instructies aan [&#x200B; vormen  [!DNL Dynamic Media]](/help/assets/config-dynamic.md#configuring-dynamic-media-cloud-services).

   * Gebruik dezelfde bedrijfsnaam in alle configuraties.
   * Op lokaal [!DNL Sites] selecteert u [!UICONTROL Dynamic Media sync mode] in **[!UICONTROL Disabled by default]** . De [!DNL Sites] -implementatie moet alleen-lezen toegang hebben tot de [!DNL Dynamic Media] -account.
   * Selecteer **[!UICONTROL Selective Publish]** bij Lokaal [!DNL Sites] in de optie **[!UICONTROL Publish Assets]** . Selecteer **[!UICONTROL Sync All Content]** niet.

1. Laat [[!DNL Dynamic Media]  steun in de Component van de Kern van het Beeld &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/image.html?lang=nl-NL#dynamic-media) toe. Deze eigenschap laat de standaard [&#x200B; component van het Beeld &#x200B;](https://www.aemcomponents.dev/content/core-components-examples/library/core-content/image.html) toe om [!DNL Dynamic Media] beelden te tonen wanneer [!DNL Dynamic Media] beelden door auteurs in webpages op lokale [!DNL Sites] plaatsing worden gebruikt.

## Externe elementen gebruiken {#use-remote-assets}

De auteurs van de website maken gebruik van Content Finder om verbinding te maken met de DAM-implementatie. Auteurs kunnen externe assets zoeken, doorbladeren en naar een component slepen. Om aan verre DAM voor authentiek te verklaren, houd de geloofsbrieven die door uw beheerder (als om het even welk) worden verstrekt handig.

Auteurs kunnen de middelen die beschikbaar zijn op de lokale DAM en de externe DAM-implementatie, in één webpagina gebruiken. Gebruik de Content Finder om te schakelen tussen het doorzoeken van de lokale of de externe DAM.

Alleen de tags met externe elementen worden opgehaald die een exact overeenkomende tag hebben samen met dezelfde taxonomihiërarchie, die beschikbaar is op de lokale [!DNL Sites] -implementatie. Alle andere tags worden verwijderd. Auteurs kunnen op externe middelen zoeken met alle tags die zich op de externe [!DNL Experience Manager] -implementatie bevinden, omdat deze functie een zoekopdracht in volledige tekst biedt.

### Doorloop van het gebruik {#walk-through-of-usage}

Gebruik bovenstaande instellingen om de functionaliteit van een authoring-ervaring beter te begrijpen. Gebruik documenten of afbeeldingen van uw keuze op de externe DAM-implementatie.

1. Navigeer naar de [!DNL Assets] -interface op de externe implementatie door **[!UICONTROL Assets]** > **[!UICONTROL Files]** vanuit de [!DNL Experience Manager] -werkruimte te openen. U kunt `https://[assets_servername_ams]:[port]/assets.html/content/dam` ook in een browser openen. Upload de assets van uw keuze.
1. Klik in de rechterbovenhoek van de [!DNL Sites] -implementatie op **[!UICONTROL Impersonate as]** . Geef `ksaner` op als gebruikersnaam, selecteer de opgegeven optie en klik op **[!UICONTROL OK]**.
1. Open een websitepagina van het type Web.Retail op **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bewerk de pagina. U kunt `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` ook in een browser openen om een pagina te bewerken.

   Klik op **[!UICONTROL Toggle Side Panel]** in de linkerbovenhoek van de pagina.

1. Open het tabblad [!UICONTROL Assets] (Remote Content Finder) en klik op **[!UICONTROL Log in to Connected Assets]** .
1. Geef de referenties op: `ksaner` als gebruikersnaam en `password` als wachtwoord. Deze gebruiker beschikt over auteursmachtigingen voor beide [!DNL Experience Manager] -implementaties.
1. Zoek naar de asset die u aan DAM hebt toegevoegd. De externe assets worden weergegeven in het linkerdeelvenster. Filter op afbeeldingen of documenten en filter verder op de typen ondersteunde documenten. Sleep de afbeeldingen naar een `Image`-component en sleep documenten naar een `Download`-component.

   De opgehaalde elementen zijn alleen-lezen bij de lokale [!DNL Sites] -implementatie. U kunt nog steeds de opties gebruiken die door de [!DNL Sites] -componenten worden geboden om het opgehaalde element te bewerken. Het bewerken op basis van componenten is niet-destructief.

   ![Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM](assets/filetypes_filter_connected_assets.png)

   *Cijfer: Opties om documenttypes en beelden te filtreren wanneer het zoeken van activa op verre DAM.*

1. De auteur van een site krijgt een melding als het origineel van een element asynchroon wordt opgehaald en als een haaltaak mislukt. Terwijl creatie of zelfs na het ontwerpen, kunnen de auteurs gedetailleerde informatie over het halen van taken en fouten in het [&#x200B; asynchrone banen &#x200B;](/help/sites-administering/asynchronous-jobs.md) gebruikersinterface zien.

   ![Melding van het asynchroon op de achtergrond ophalen van assets.](assets/assets_async_transfer_fails.png)

   *Afbeelding: Melding van het asynchroon op de achtergrond ophalen van assets.*

1. Wanneer u een pagina publiceert, geeft [!DNL Experience Manager] een volledige lijst weer van elementen die op de pagina worden gebruikt. Zorg ervoor dat de externe assets op het moment van publicatie worden opgehaald. Om het statuut van elk gehaald activa te controleren, zie [&#x200B; asynchrone banen &#x200B;](/help/sites-administering/asynchronous-jobs.md) gebruikersinterface.

   >[!NOTE]
   >
   >Zelfs als een of meer externe middelen niet volledig zijn opgehaald, wordt de pagina gepubliceerd. In het systeemvak [!DNL Experience Manager] wordt een melding weergegeven voor fouten die worden weergegeven op de pagina voor asynchrone taken.

>[!CAUTION]
>
>Nadat de opgehaalde externe elementen in een webpagina zijn gebruikt, kunnen ze worden doorzocht en kunnen ze worden gebruikt door iedereen die toegangsrechten heeft tot de lokale map. De opgehaalde elementen worden opgeslagen in de lokale map (`connectedassets` in de bovenstaande doorloop). De assets zijn ook doorzoekbaar en zichtbaar in de lokale opslagplaats, en wel via [!UICONTROL Content Finder].

De opgehaalde assets kunnen net als elke andere lokale asset worden gebruikt, alleen kunnen de bijbehorende metadata niet worden bewerkt.

### Gebruik van een element op verschillende webpagina&#39;s controleren {#asset-usage-references}

Met [!DNL Experience Manager] kunnen DAM-gebruikers alle referenties naar een element controleren. Het helpt het gebruik van een middel in ver [!DNL Sites] en in samenstellingsactiva begrijpen en beheren. Veel auteurs van webpagina&#39;s die [!DNL Experience Manager Sites] implementeren, kunnen een element op een externe [!DNL Assets] gebruiken in verschillende webpagina&#39;s. Om het beheer van bedrijfsmiddelen te vereenvoudigen en niet tot verbroken verwijzingen te leiden, is het belangrijk dat de DAM-gebruikers het gebruik van middelen op lokale en externe webpagina&#39;s controleren. De tab [!UICONTROL References] op de pagina [!UICONTROL Properties] van een element geeft een overzicht van de lokale en externe referenties van het element.

Voer de volgende stappen uit om referenties over de implementatie van [!DNL Assets] weer te geven en te beheren:

1. Selecteer een element in de [!DNL Assets] console en klik op **[!UICONTROL Properties]** op de werkbalk.
1. Klik op het tabblad **[!UICONTROL References]**. Zie **[!UICONTROL Local References]** voor gebruik van het element tijdens de [!DNL Assets] -implementatie. Zie ** [!UICONTROL Remote References] voor gebruik van het element bij [!DNL Sites] plaatsing waar het element werd gehaald gebruikend de Verbonden functionaliteit van Assets.

   ![&#x200B; Verre verwijzingen in de pagina van ActivaEigenschappen &#x200B;](assets/connected-assets-remote-reference.png)

1. De verwijzingen voor [!DNL Sites] pagina&#39;s tonen het totale aantal verwijzingen voor elke lokale [!DNL Sites]. Het kan enige tijd duren om alle verwijzingen te vinden en het totale aantal verwijzingen te tonen.
1. De lijst met verwijzingen is interactief en DAM-gebruikers kunnen op een verwijzing klikken om de pagina waarnaar wordt verwezen, te openen. Als de verre verwijzingen niet om één of andere reden kunnen worden gehaald, wordt een bericht getoond op de hoogte brengend van de mislukking.
1. Gebruikers kunnen het element verplaatsen of verwijderen. Wanneer u een element verplaatst of verwijdert, wordt het totale aantal referenties van alle geselecteerde elementen/mappen weergegeven in een waarschuwingsvenster. Wanneer u een element verwijdert waarvoor de referenties nog niet zijn opgehaald, wordt een waarschuwingsvenster weergegeven.

   ![&#x200B; kracht schrapt waarschuwing &#x200B;](assets/delete-referenced-asset.png)

### Updates van middelen beheren in externe DAM {#manage-updates-in-remote-dam}

Na [&#x200B; vormend een verbinding &#x200B;](#configure-a-connection-between-sites-and-assets-deployments) tussen verre DAM en [!DNL Sites] plaatsingen, worden de activa op verre DAM ter beschikking gesteld op de [!DNL Sites] plaatsing. Vervolgens kunt u de bewerkingen bijwerken, verwijderen, hernoemen en verplaatsen op de externe DAM-middelen of -mappen. De updates zijn, met enige vertraging, automatisch beschikbaar bij de [!DNL Sites] -implementatie. Als bovendien een element op een externe DAM wordt gebruikt op een lokale [!DNL Experience Manager Sites] -pagina, worden de updates van het element op de externe DAM weergegeven op de [!DNL Sites] -pagina.

Terwijl het bewegen van een activa van één plaats aan een andere, zorg ervoor dat u [&#x200B; verwijzingen &#x200B;](/help/assets/manage-assets.md) aanpast zodat de activa op de [!DNL Sites] pagina tonen. Als u middelen naar een plaats verplaatst die niet van de lokale [!DNL Sites] plaatsing toegankelijk is, ontbreekt de activa aan vertoning op de plaatsing van Plaatsen.

U kunt ook de eigenschappen van metagegevens bijwerken voor een element op externe DAM en de wijzigingen zijn beschikbaar voor de lokale [!DNL Sites] -implementatie.

[!DNL Sites] -auteurs kunnen een voorvertoning van de beschikbare updates voor de [!DNL Sites] -implementatie bekijken en de wijzigingen vervolgens opnieuw publiceren om deze beschikbaar te maken in de [!DNL Experience Manager] -publicatieinstantie.

[!DNL Experience Manager] geeft een verlopen visuele statusindicator weer op elementen in `Remote Assets Content Finder` om te voorkomen dat siteauteurs het element op een [!DNL Sites] -pagina gebruiken. Als u een element met een verlopen status op een [!DNL Sites] -pagina gebruikt, wordt het element niet weergegeven op de [!DNL Experience Manager] -publicatie-instantie.

## Veelgestelde vragen {#frequently-asked-questions}

+++**zou u Verbonden Assets vormen als u activa beschikbaar op uw [!DNL Sites] plaatsing moet gebruiken?**

In dat geval hoeft u Connected Assets niet te configureren. U kunt de middelen gebruiken beschikbaar op de [!DNL Sites] plaatsing.

+++

+++**wanneer moet u de Verbonden eigenschap van Assets vormen?**

Configureer de Connected Assets-functie alleen wanneer u de middelen moet gebruiken die beschikbaar zijn op een externe DAM-implementatie tijdens een [!DNL Sites] -implementatie.

+++

+++**kunt u veelvoudige [!DNL Sites] plaatsingen met een verre plaatsing verbinden DAM na het vormen van Verbonden Assets?**

Ja, u kunt meerdere [!DNL Sites] -implementaties verbinden met een externe DAM-implementatie nadat u Connected Assets hebt geconfigureerd. Voor meer informatie, zie [&#x200B; Verbonden architectuur van Assets &#x200B;](#connected-assets-architecture).

+++

+++**hoeveel verre plaatsingen DAM kunt u met een [!DNL Sites] plaatsing verbinden na het vormen van Verbonden Assets?**

Nadat u Connected Assets hebt geconfigureerd, kunt u één externe DAM-implementatie verbinden met een [!DNL Sites] -implementatie. Voor meer informatie, zie [&#x200B; Verbonden architectuur van Assets &#x200B;](#connected-assets-architecture).

+++

+++**kunt u de activa van Dynamic Media van uw [!DNL Sites] plaatsing na het vormen Verbonden Assets gebruiken?**

Nadat u Connected Assets hebt geconfigureerd, zijn [!DNL Dynamic Media] -elementen beschikbaar voor [!DNL Sites] -implementatie in de modus Alleen-lezen. Het gevolg is dat u [!DNL Dynamic Media] niet kunt gebruiken om elementen in de [!DNL Sites] -implementatie te verwerken. Voor meer informatie, zie [&#x200B; een verbinding tussen Plaatsen en de plaatsingen van Dynamic Media &#x200B;](#dynamic-media-assets) vormen.

+++

+++**kunt u activa van beeld en formaat van het Document types van de verre plaatsing DAM op de [!DNL Sites] plaatsing na het vormen van Verbonden Assets gebruiken?**

Ja, u kunt middelen van beeld en formaat van het Document types van de verre plaatsing van DAM op de plaatsing van [!DNL Sites] gebruiken na het vormen van Verbonden Assets.

+++

+++**kunt u inhoudsfragmenten en videoactiva van de verre plaatsing DAM op de [!DNL Sites] plaatsing na het vormen van Verbonden Assets gebruiken?**

Nee, u kunt na het configureren van Connected Assets geen inhoudsfragmenten en video-elementen gebruiken die afkomstig zijn van de externe DAM-implementatie op de [!DNL Sites] -implementatie.

+++

+++**kunt u de activa van Dynamic Media van de verre plaatsing DAM op de [!DNL Sites] plaatsing gebruiken na het vormen van Verbonden Assets?**

Ja, u kunt Dynamic Media image assets configureren en gebruiken vanaf de externe DAM-implementatie op de [!DNL Sites] -implementatie nadat u Connected Assets hebt geconfigureerd. Voor meer informatie, zie [&#x200B; een verbinding tussen Plaatsen en de plaatsingen van Dynamic Media &#x200B;](#dynamic-media-assets) vormen.

+++

+++**na het vormen van Verbonden Assets, kunt u de update uitvoeren, schrappen, hernoemen, en verrichtingen op de verre activa DAM of omslagen verplaatsen?**

Ja, nadat u Connected Assets hebt geconfigureerd, kunt u de update uitvoeren, verwijderen, hernoemen en bewerkingen verplaatsen op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen. Voor meer informatie, zie [&#x200B; updates aan activa in verre DAM &#x200B;](#handling-updates-to-remote-assets) beheren.

+++

+++**na het vormen van Verbonden Assets, kunt u activa op uw [!DNL Sites] plaatsing toevoegen of wijzigen en hen op verre plaatsing van DAM ter beschikking stellen?**

U kunt elementen toevoegen aan de [!DNL Sites] -implementatie, maar deze elementen kunnen niet beschikbaar worden gemaakt voor de externe DAM-implementatie.

+++

## Beperkingen en aanbevolen procedures {#tip-and-limitations}

* Om inzicht over activagebruik te krijgen, vorm de [&#128279;](/help/assets/asset-insights.md) functionaliteit van het Inzicht van 0&rbrace; Assets &lbrace;op de [!DNL Sites] instantie.

* U kunt niet de verre activa op de [&#x200B; Component van het Beeld slepen vormt dialoog &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=nl-NL#configure-dialog). U kunt het externe element echter rechtstreeks naar de afbeeldingscomponent op de pagina Sites slepen zonder op **[!UICONTROL Configure]** te klikken.

### Machtigingen en vermogensbeheer {#permissions-and-managing-assets}

* Lokale assets zijn alleen-lezen kopieën. [!DNL Experience Manager] -componenten bewerken niet-destructieve elementen. Andere soorten bewerkingen zijn niet toegestaan.
* Lokaal opgehaalde assets zijn alleen beschikbaar voor authoring. Workflows voor het bijwerken van assets kunnen niet worden toegepast en metadata kunnen niet worden bewerkt.
* Alleen afbeeldingen en de vermelde documentindelingen worden ondersteund. [!DNL Content Fragments] en [!DNL Experience Fragments] worden niet ondersteund.
* [!DNL Experience Manager] haalt de schema&#39;s voor metagegevens niet op. Dit betekent dat mogelijk niet alle opgehaalde metagegevens worden weergegeven. Als het schema afzonderlijk wordt bijgewerkt tijdens de [!DNL Sites] -implementatie, worden alle metagegevenseigenschappen weergegeven.
* Alle [!DNL Sites] -auteurs hebben leesmachtigingen voor de opgehaalde kopieën, zelfs als auteurs geen toegang hebben tot de externe DAM-implementatie.
* Geen API-ondersteuning om de integratie aan te passen.
* De functionaliteit ondersteunt naadloos zoeken en gebruiken van externe assets. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets te migreren. Zie de [Assets-migratiegids](assets-migration-guide.md).
* Het is niet mogelijk om een extern element als paginaminiatuur in de gebruikersinterface van [!UICONTROL Page Properties] te gebruiken. U kunt een miniatuur van een webpagina in de gebruikersinterface van [!UICONTROL Page Properties] instellen vanuit de [!UICONTROL Thumbnail] door op [!UICONTROL Select Image] te klikken.

### Instellen en licenties verlenen {#setup-licensing}

* [!DNL Assets] -implementatie op [!DNL Adobe Managed Services] wordt ondersteund.
* [!DNL Sites] kan verbinding maken met één [!DNL Assets] -implementatie tegelijk.
* U hebt een licentie van [!DNL Assets] nodig om als externe opslagruimte te werken.
* Een of meer licenties van [!DNL Sites] die als lokale ontwerpimplementatie werken, zijn vereist.

### Gebruik {#usage}

* Gebruikers kunnen tijdens het ontwerpen zoeken naar externe elementen en deze naar de lokale pagina slepen. Er wordt geen andere functionaliteit ondersteund.
* Voor ophaalbewerkingen geldt een time-out na 5 seconden. Auteurs kunnen problemen ervaren bij het ophalen van assets, bijvoorbeeld als er netwerkproblemen optreden. Auteurs kunnen opnieuw proberen door het externe element van [!UICONTROL Content Finder] naar [!UICONTROL Page Editor] te slepen.
* Eenvoudige bewerkingen die niet-destructief zijn en de bewerking die wordt ondersteund via de component `Image` , kunnen worden uitgevoerd op opgehaalde elementen. Assets zijn alleen-lezen.
* De enige methode om het element opnieuw op te halen is het op een pagina te slepen. Er is geen API-ondersteuning of andere methoden om middelen opnieuw op te halen om deze bij te werken.
* Als elementen van de DAM worden gedeactiveerd, worden deze nog steeds gebruikt op [!DNL Sites] -pagina&#39;s.
* De externe referentie-items van een element worden asynchroon opgehaald. De verwijzingen en het totale aantal zijn niet echt - tijd en er kan één of ander verschil zijn als een auteur van Plaatsen het middel gebruikt terwijl een DAM gebruiker de verwijzing bekijkt. DAM-gebruikers kunnen de pagina vernieuwen en het totaalaantal over een paar minuten opnieuw proberen.

## Problemen oplossen {#troubleshoot}

Ga als volgt te werk om algemene fouten op te lossen:

* Als u niet kunt zoeken naar externe elementen vanuit de [!UICONTROL Content Finder] , moet u ervoor zorgen dat de vereiste rollen en machtigingen aanwezig zijn.

* Een middel dat van verre DAM wordt gehaald kan niet op een Web-pagina om één of meerdere redenen worden gepubliceerd. Het bestaat niet op verre server, gebrek aan aangewezen toestemmingen om het te halen, of de netwerkmislukking kan de redenen zijn. Zorg ervoor dat het element niet wordt verwijderd van de externe DAM. Zorg ervoor dat de juiste machtigingen zijn ingesteld en dat aan de voorwaarden is voldaan. Voeg het element opnieuw toe aan de pagina en publiceer het opnieuw. Controleer de [lijst met asynchrone taken](/help/sites-administering/asynchronous-jobs.md) op fouten bij het ophalen van assets.

* Als u tot de verre plaatsing van DAM van de lokale [!DNL Sites] plaatsing niet kunt toegang hebben, zorg ervoor dat de dwars-plaats koekjes worden toegestaan en [&#x200B; de zelfde steun van het plaatscookie &#x200B;](/help/sites-administering/same-site-cookie-support.md) wordt gevormd. Als cookies die naar andere sites verwijzen, worden geblokkeerd, wordt de implementatie van [!DNL Experience Manager] mogelijk niet geverifieerd. [!DNL Google Chrome] kan bijvoorbeeld in de Incognito-modus cookies van derden blokkeren. Om koekjes in [!DNL Chrome] browser toe te staan, klik het &quot;oogpictogram&quot;in de adresbar, navigeer aan **het Werk van de Plaats niet** > **Geblokkeerd**, selecteer Verre DAM URL, en sta login-symbolische koekje toe. Afwisselend, zie [&#x200B; hoe te om derdekoekjes &#x200B;](https://support.google.com/chrome/answer/95647) toe te laten.

  ![&#x200B; fout van het Koekje in browser van Chrome op wijze Incognito &#x200B;](assets/chrome-cookies-incognito-dialog.png)

* Als u geen toegang hebt tot de externe DAM-implementatie van Adobe Managed Services vanaf de implementatie van Experience Manager Sites as a Cloud Service Sites, werkt u het bestand `aem_author.vhost` bij dat beschikbaar is op `"/etc/httpd/conf.d/available_vhosts` , zodat externe DAM de volgende headers kan opnemen in de Dispatcher-configuratie:

  ```xml
  Header Set Access-Control-Allow-Origin <Local Sites instance host>
  Header Set Access-Control-Allow-Credentials true
  ```

* Als externe referenties niet worden opgehaald en een foutbericht opleveren, controleert u of [!DNL Sites] -implementatie beschikbaar is en controleert u op netwerkconnectiviteitsproblemen. Probeer het later opnieuw om te controleren. [!DNL Assets] probeert tweemaal verbinding te maken met [!DNL Sites] -implementatie en rapporteert vervolgens een fout.

  ![&#x200B; mislukking om activa verre verwijzingen terug te winnen &#x200B;](assets/reference-report-failure.png)

* Als de cookies niet van de Sites-server naar de Assets-server in Google Chrome worden verzonden, is dit omdat de Assets-verbinding niet via HTTPS plaatsvindt. Als u geen HTTPS gebruikt op de Assets-instantie, kan de header `SameSite=None` niet worden toegevoegd aan de reactie nadat u deze hebt geverifieerd met de Assets-server.

