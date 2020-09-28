---
title: Use Connected Assets to share DAM assets in [!DNL Sites]
description: Gebruik de middelen die beschikbaar zijn op een [!DNL Adobe Experience Manager Assets] deployment when creating your web pages on another [!DNL Adobe Experience Manager Sites] externe implementatie.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '2017'
ht-degree: 41%

---


# Use Connected Assets to share DAM assets in [!DNL Experience Manager Sites] {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In grote ondernemingen is de infrastructuur voor het maken van websites soms gedistribueerd. Soms zijn de functies en de digitale assets voor het maken van websites opgenomen in verschillende implementaties. Één reden kan geografisch verdeeld bestaande plaatsingen zijn die worden vereist om samen te werken. Een andere reden kunnen acquisities zijn die leiden tot heterogene infrastructuren die de moedermaatschappij samen wil gebruiken.

Gebruikers kunnen webpagina&#39;s maken in [!DNL Experience Manager Sites]. [!DNL Experience Manager Assets] is het DAM-systeem (Digital Asset Management) dat de vereiste middelen voor websites levert. [!DNL Experience Manager] ondersteunt nu het bovenstaande gebruiksgeval door integratie [!DNL Sites] en [!DNL Assets].

## Overzicht van gekoppelde assets {#overview-of-connected-assets}

When editing pages in [!UICONTROL Page Editor], the authors can seamlessly search, browse, and embed assets from a different [!DNL Assets] deployment. De beheerders creëren eenmalig integratie van een plaatsing van [!DNL Sites] met een verschillende (verre) plaatsing van [!DNL Assets].

For the [!DNL Sites] authors, the remote assets are available as read-only local assets. Met deze functie kunt u naadloos zoeken naar telkens een klein aantal externe assets voor gebruik. To make many remote assets available on a [!DNL Sites] deployment in one-go, consider migrating the assets in bulk. Zie de migratiehandleiding voor [Experience Manager Assets](/help/assets/assets-migration-guide.md).

### Vereisten en ondersteunde implementaties {#prerequisites}

Controleer de volgende punten voordat u deze functie gebruikt of configureert:

* De gebruikers maken deel uit van de aangewezen gebruikersgroepen op elke plaatsing.
* Aan een van de ondersteunde criteria wordt voldaan voor [!DNL Adobe Experience Manager] implementatietypen. [!DNL Experience Manager] 6.5 [!DNL Assets] werkt met [!DNL Experience Manager] als Cloud Service. Zie de functionaliteit [Verbonden elementen in Experience Manager als een Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html)voor meer informatie.

   |  | [!DNL Sites] als Cloud Service | [!DNL Experience Manager] 6.5 [!DNL Sites] over AMS | [!DNL Experience Manager] 6.5 [!DNL Sites] on-premise |
   |---|---|---|---|
   | **[!DNL Experience Manager Assets]als Cloud Service** | Ondersteund | Ondersteund | Ondersteund |
   | **[!DNL Experience Manager]6.5[!DNL Assets]over AMS** | Ondersteund | Ondersteund | Ondersteund |
   | **[!DNL Experience Manager]6.5[!DNL Assets]on-premise** | Niet ondersteund | Niet ondersteund | Niet ondersteund |

### Ondersteunde bestandsindelingen {#mimetypes}

Auteurs zoeken naar afbeeldingen en de volgende typen documenten in de Inhoudszoeker en gebruiken de doorzochte elementen in de Pagina-editor. Documenten worden toegevoegd aan de `Download` component en afbeeldingen aan de `Image` component. Authors also add the remote assets in any custom [!DNL Experience Manager] component that extends the default `Download` or `Image` components. De ondersteunde indelingen zijn:

* **Afbeeldingsindelingen**: De indelingen die de [component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/image.html) Image ondersteunt. [!DNL Dynamic Media] afbeeldingen worden niet ondersteund.
* **Documentindelingen**: Zie de [ondersteunde documentindelingen](assets-formats.md#supported-document-formats).

### Betrokken gebruikers en groepen {#users-and-groups-involved}

Hieronder worden de diverse rollen beschreven voor de configuratie en toepassing van een kenmerk en de overeenkomstige gebruikersgroepen. Het lokale bereik wordt gebruikt voor het geval waarin een auteur een webpagina maakt. De externe scope wordt gebruikt voor de DAM-implementatie die als host fungeert voor de vereiste assets. The [!DNL Sites] author fetches these remote assets.

| Rol | Scope | Gebruikersgroep | Gebruikersnaam in voorbeeldprocedure | Vereiste |
|---|---|---|---|---|
| [!DNL Sites] beheerder | Lokaal | [!DNL Experience Manager] `administrators` | `admin` | Set up [!DNL Experience Manager] and configure integration with the remote [!DNL Assets] deployment. |
| DAM-gebruiker | Lokaal | `Authors` | `ksaner` | Wordt gebruikt om de assets die bij `/content/DAM/connectedassets/` zijn opgehaald, weer te geven en te dupliceren. |
| [!DNL Sites] author | Lokaal | `Authors` (met lees toegang op verre DAM en auteurstoegang op lokaal [!DNL Sites]) | `ksaner` | End user are [!DNL Sites] authors who use this integration to improve their content velocity. The authors search and browse assets in remote DAM using [!UICONTROL Content Finder] and using the required images in local web pages. De referenties van de `ksaner` DAM-gebruiker worden gebruikt. |
| [!DNL Assets] beheerder | Extern | [!DNL Experience Manager] `administrators` | `admin` op afstand [!DNL Experience Manager] | Configureer CORS (Cross-Origin Resource Sharing). |
| DAM-gebruiker | Extern | `Authors` | `ksaner` op afstand [!DNL Experience Manager] | Author role on the remote [!DNL Experience Manager] deployment. Zoek en blader naar assets in gekoppelde assets met de [!UICONTROL Content Finder]. |
| DAM-distributeur (technische gebruiker) | Extern | [!DNL Sites] `Authors` | `ksaner` op afstand [!DNL Experience Manager] | This user present on the remote deployment is used by [!DNL Experience Manager] local server (not the [!DNL Sites] author role) to fetch the remote assets, on behalf of [!DNL Sites] author. Deze rol is anders dan de twee bovenstaande `ksaner`-rollen en hoort bij een andere gebruikersgroep. |

## Configure a connection between [!DNL Sites] and [!DNL Assets] deployments {#configure-a-connection-between-sites-and-assets-deployments}

An [!DNL Experience Manager] administrator can create this integration. Zodra gecreeerd, worden de toestemmingen die worden vereist om het te gebruiken gevestigd via gebruikersgroepen. De gebruikersgroepen worden bepaald op de [!DNL Sites] plaatsing en op de plaatsing DAM.

To configure Connected Assets and local [!DNL Sites] connectivity, follow these steps:

1. Access an existing [!DNL Sites] deployment or create a deployment using the following command:

   1. In the folder of the JAR file, execute the following command on a terminal to create each [!DNL Experience Manager] server.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. After a few minutes, the [!DNL Experience Manager] server starts successfully. Consider this [!DNL Sites] deployment as the local machine for web page authoring, say at `https://[local_sites]:4502`.

1. Ensure that the users and roles with local scope exist on the [!DNL Sites] deployment and on the [!DNL Assets] deployment on AMS. Create a technical user on [!DNL Assets] deployment and add to the user group mentioned in [users and groups involved](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Heb toegang tot de lokale [!DNL Sites] plaatsing bij `https://[local_sites]:4502`. Klik op **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Connected Assets Configuration]** en geef de volgende waarden op:

   1. [!DNL Assets] locatie is `https://[assets_servername_ams]:[port]`.
   1. Referenties van een DAM-distributeur (technische gebruiker).
   1. In the **[!UICONTROL Mount Point]** field, enter the local [!DNL Experience Manager] path where [!DNL Experience Manager] fetches the assets. Bijvoorbeeld de map `remoteassets`.
   1. Pas de waarden van **[!UICONTROL Original Binary transfer optimization Threshold]** aan, afhankelijk van uw netwerk. De weergave van een asset die groter is dan deze drempelwaarde, wordt asynchroon overgedragen.
   1. Select **[!UICONTROL Datastore Shared with Connected Assets]**, if you use a datastore to store your assets and the Datastore is the common storage between both deployments. In dat geval is de drempelwaarde niet van belang, aangezien de binaire gegevens van de werkelijke asset in de datastore staan en niet worden overgedragen.

   ![Een typische configuratie voor gekoppelde assets](assets/connected-assets-typical-config.png)

   *Afbeelding: Een typische configuratie voor gekoppelde assets.*

1. Als de assets al zijn verwerkt en de weergaven zijn opgehaald, schakelt u de startprogramma&#39;s voor de workflow uit. Adjust the launcher configurations on the local ([!DNL Sites]) deployment to exclude the `connectedassets` folder, in which the remote assets are fetched.

   1. Klik bij [!DNL Sites] implementatie op **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.

   1. Zoek naar startprogramma&#39;s met workflows als **[!UICONTROL DAM Update Asset]** en **[!UICONTROL DAM Metadata Writeback]**.

   1. Selecteer het workflowstartprogramma en klik op **[!UICONTROL Properties]** op de actiebalk.

   1. In the [!UICONTROL Properties] wizard, change the **[!UICONTROL Path]** fields as the following mappings to update their regular expressions to exclude the mount point **[!UICONTROL connectedassets]**.

   | Voor | Na |
   |---|---|
   | `/content/dam(/((?!/subassets).)*/)renditions/original` | `/content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*/)renditions/original` | `/content/dam(/((?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/.*)/jcr:content/metadata` | `/content/dam(/((?!connectedassets).)*/)jcr:content/metadata` |

   >[!NOTE]
   >
   >Alle uitvoeringen die beschikbaar zijn op de externe implementatie worden opgehaald, wanneer auteurs middelen ophalen. Als u meer weergaven van een opgehaalde asset tot stand wilt brengen, moet u deze configuratiestap overslaan. De [!UICONTROL DAM Update Asset] workflow wordt geactiveerd en er worden meer uitvoeringen gemaakt. These renditions are available only on the local [!DNL Sites] deployment and not on the remote DAM deployment.

1. Voeg de [!DNL Sites] plaatsing als één van **[!UICONTROL Allowed Origins]** op de verre configuratie [!DNL Assets'] CORS toe.

   1. Meld u aan met de beheerdersreferenties. Search for `Cross-Origin`. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   1. Als u een CORS-configuratie voor [!DNL Sites] implementatie wilt maken, klikt u op het pictogram ![Opties voor optie toevoegen naast](assets/do-not-localize/assets_add_icon.png) **[!UICONTROL Adobe Granite Cross-Origin Resource Sharing Policy]**.

   1. In the field **[!UICONTROL Allowed Origins]**, input the URL of the local [!DNL Sites], that is, `https://[local_sites]:[port]`. Sla de configuratie op.

## Externe assets gebruiken {#use-remote-assets}

De auteurs van de website maken gebruik van Content Finder om verbinding te maken met de DAM-implementatie. Auteurs kunnen externe assets zoeken, doorbladeren en naar een component slepen. Om de externe DAM te verifiëren, moet u de referenties van de DAM-gebruiker die door uw beheerder zijn verstrekt, bij de hand houden.

Auteurs kunnen de middelen die beschikbaar zijn op de lokale DAM en de externe DAM-implementatie, in één webpagina gebruiken. Gebruik de Content Finder om te schakelen tussen het doorzoeken van de lokale of de externe DAM.

Alleen die tags met externe elementen worden opgehaald met een exacte corresponderende tag samen met dezelfde taxonomihiërarchie, beschikbaar op de lokale [!DNL Sites] implementatie. Alle andere tags worden verwijderd. Authors can search for remote assets using all the tags present on the remote [!DNL Experience Manager] deployment, as it offers a full-text search.

### Procedure voor gebruik {#walk-through-of-usage}

Gebruik bovenstaande instellingen om de functionaliteit van een authoring-ervaring beter te begrijpen. Gebruik documenten of afbeeldingen van uw keuze op de externe DAM-implementatie.

1. Navigate to the [!DNL Assets] interface on the remote deployment by accessing **[!UICONTROL Assets]** > **[!UICONTROL Files]** from [!DNL Experience Manager] workspace. U kunt `https://[assets_servername_ams]:[port]/assets.html/content/dam` ook in een browser openen. Upload de assets van uw keuze.
1. On the [!DNL Sites] deployment, in the profile activator in the upper-right corner, click **[!UICONTROL Impersonate as]**. Geef `ksaner` op als gebruikersnaam, selecteer de opgegeven optie en klik op **[!UICONTROL OK]**.
1. Open een websitepagina van het type Web.Retail op **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bewerk de pagina. U kunt `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` ook in een browser openen om een pagina te bewerken.

   Klik op **[!UICONTROL Toggle Side Panel]** in de linkerbovenhoek van de pagina.

1. Open the [!UICONTROL Assets] tab and click **[!UICONTROL Log in to Connected Assets]**.
1. Geef de referenties op: `ksaner` als gebruikersnaam en `password` als wachtwoord. This user has authoring permissions on both the [!DNL Experience Manager] deployments.
1. Zoek naar de asset die u aan DAM hebt toegevoegd. De externe assets worden weergegeven in het linkerdeelvenster. Filter op afbeeldingen of documenten en filter verder op de typen ondersteunde documenten. Sleep de afbeeldingen naar een `Image`-component en sleep documenten naar een `Download`-component.

   The fetched assets are read-only on the local [!DNL Sites] deployment. You can still use the options provided by your [!DNL Sites] components to edit the fetched asset. Het bewerken op basis van componenten is niet-destructief.

   ![Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM](assets/filetypes_filter_connected_assets.png)

   *Afbeelding: Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM.*

1. De auteur van een site krijgt een melding als een asset asynchroon wordt opgehaald en als het ophalen mislukt. Tijdens (of zelfs na) het ontwerpen kunnen auteurs gedetailleerde informatie zien over het ophalen van taken en fouten in de gebruikersinterface voor [asynchrone taken](/help/sites-administering/asynchronous-jobs.md).

   ![Melding van het asynchroon op de achtergrond ophalen van assets.](assets/assets_async_transfer_fails.png)

   *Afbeelding: Melding van het asynchroon op de achtergrond ophalen van assets.*

1. When publishing a page, [!DNL Experience Manager] displays a complete list of assets that are used on the page. Zorg ervoor dat de externe assets op het moment van publicatie worden opgehaald. Als u de status van elke opgehaalde asset wilt controleren, raadpleegt u de gebruikersinterface voor [asynchrone taken](/help/sites-administering/asynchronous-jobs.md).

   >[!NOTE]
   >
   >Zelfs als een of meer externe assets niet worden opgehaald, wordt de pagina gepubliceerd. De component die gebruikmaakt van de externe asset, wordt leeg (zonder content) gepubliceerd. The [!DNL Experience Manager] notification area displays a notification for errors that show in async jobs page.

>[!CAUTION]
>
>Nadat de opgehaalde externe elementen in een webpagina zijn gebruikt, kunnen ze worden doorzocht en kunnen ze worden gebruikt door iedereen die toegangsrechten heeft tot de lokale map. De opgehaalde elementen worden opgeslagen in de lokale map (`connectedassets` in de bovenstaande doorloop). De assets zijn ook doorzoekbaar en zichtbaar in de lokale opslagplaats, en wel via [!UICONTROL Content Finder].

De opgehaalde assets kunnen net als elke andere lokale asset worden gebruikt, alleen kunnen de bijbehorende metadata niet worden bewerkt.

## Beperkingen {#limitations}

### Machtigingen en vermogensbeheer {#permissions-and-managing-assets}

* Lokale assets worden niet gesynchroniseerd met de oorspronkelijke assets op de externe implementatie. Eventuele bewerkingen, verwijderingen of intrekkingen van machtigingen voor de DAM-implementatie worden niet verderop in de DAM-implementatie doorgegeven.
* Lokale assets zijn alleen-lezen kopieën. [!DNL Experience Manager] componenten bewerken niet-destructieve elementen in elementen. Andere soorten bewerkingen zijn niet toegestaan.
* Lokaal opgehaalde assets zijn alleen beschikbaar voor authoring. Workflows voor het bijwerken van assets kunnen niet worden toegepast en metadata kunnen niet worden bewerkt.
* Alleen afbeeldingen en de vermelde documentindelingen worden ondersteund. [!DNL Dynamic Media] Elementen, inhoudsfragmenten en ervaringsfragmenten worden niet ondersteund.
* Metadataschema&#39;s worden niet opgehaald.
* Alle [!DNL Sites] auteurs hebben leesmachtigingen voor de opgehaalde kopieën, zelfs als auteurs geen toegang hebben tot de externe DAM-implementatie.
* Geen API-ondersteuning om de integratie aan te passen.
* De functionaliteit ondersteunt naadloos zoeken en gebruiken van externe assets. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets te migreren. Zie de [Assets-migratiegids](assets-migration-guide.md).
* Het is niet mogelijk om een extern element als paginaminiatuur in de [!UICONTROL Page Properties] gebruikersinterface te gebruiken. U kunt een miniatuur van een webpagina in de [!UICONTROL Page Properties] gebruikersinterface instellen via de [!UICONTROL Thumbnail] knop [!UICONTROL Select Image].

### Installatie en licenties {#setup-licensing}

* [!DNL Assets] implementatie op [!DNL Adobe Managed Services] wordt ondersteund.
* [!DNL Sites] kan tegelijkertijd verbinding maken met één [!DNL Assets] opslagplaats.
* A license of [!DNL Assets] working as remote repository.
* One or more licenses of [!DNL Sites] working as local authoring deployment.

### Gebruik {#usage}

* Gebruikers kunnen tijdens het ontwerpen zoeken naar externe elementen en deze naar de lokale pagina slepen. Er wordt geen andere functionaliteit ondersteund.
* Voor ophaalbewerkingen geldt een time-out na 5 seconden. Auteurs kunnen problemen ervaren bij het ophalen van assets, bijvoorbeeld als er netwerkproblemen optreden. Authors can reattempt by dragging the remote asset from [!UICONTROL Content Finder] to [!UICONTROL Page Editor].
* Eenvoudige bewerkingen die niet-destructief zijn en bewerkingen die worden ondersteund via de `Image`-component van , kunnen worden uitgevoerd op opgehaalde elementen. Assets zijn alleen-lezen.
* De enige methode om het element opnieuw op te halen is het op een pagina te slepen. Er is geen API-ondersteuning of andere methoden om middelen opnieuw op te halen om deze bij te werken.

## Problemen oplossen {#troubleshoot}

Ga als volgt te werk om problemen op te lossen voor het algemene foutscenario:

* If you cannot search for remote assets from the [!UICONTROL Content Finder], then ensure that the required roles and permissions are in place.
* Een middel dat van de verre dam wordt gehaald kan niet op een Web-pagina om één of meerdere redenen worden gepubliceerd. Het bestaat niet op verre server, gebrek aan aangewezen toestemmingen om het te halen, of de netwerkmislukking kan de redenen zijn. Zorg ervoor dat het element niet wordt verwijderd van de externe DAM. Zorg ervoor dat de juiste machtigingen zijn ingesteld en dat aan de voorwaarden is voldaan. Voeg het element opnieuw toe aan de pagina en publiceer het opnieuw. Controleer de [lijst met asynchrone taken](/help/sites-administering/asynchronous-jobs.md) op fouten bij het ophalen van assets.
