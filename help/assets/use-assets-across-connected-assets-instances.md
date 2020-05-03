---
title: Gebruik Connected Assets om DAM-middelen te delen in de ontwerpworkflow van [!DNL Adobe Experience Manager Sites].
description: Gebruik middelen die beschikbaar zijn op een externe implementatie van [!DNL Adobe Experience Manager Assets] wanneer u uw webpagina's maakt op een andere implementatie van Experience Manager.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 2cdcea028814b40fb178e63f583939df27a46cad

---


# Use Connected Assets to share DAM assets in [!DNL Experience Manager Sites] {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In grote ondernemingen is de infrastructuur voor het maken van websites soms gedistribueerd. Soms zijn de functies en de digitale assets voor het maken van websites opgenomen in verschillende implementaties. Enkele redenen zijn bijvoorbeeld bestaande, geografisch gedistribueerde implementaties die vereist zijn voor samenwerking, of acquisities die leiden tot heterogene infrastructuren die het moederbedrijf alsnog samen wil gebruiken.

[!DNL Adobe Experience Manager Sites] biedt functies voor het maken van webpagina&#39;s en is het DAM-systeem (Digital Asset Management) dat de vereiste assets voor websites levert. [!DNL Adobe Experience Manager Assets] [!DNL Experience Manager] ondersteunt nu het bovenstaande gebruiksgeval door integratie [!DNL Experience Manager Sites] en [!DNL Experience Manager Assets].

## Overzicht van gekoppelde assets {#overview-of-connected-assets}

When editing pages in Page Editor, the authors can seamlessly search, browse, and embed assets from a different [!DNL Experience Manager Assets] deployment. To do an [!DNL Experience Manager] administrator do a one-time integration of a local deployment of [!DNL Experience Manager Sites] with a different (remote) deployment of [!DNL Experience Manager Assets].

For the [!DNL Sites] authors, the remote assets are available as read-only local assets. Met deze functie kunt u naadloos zoeken naar telkens een klein aantal externe assets voor gebruik. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets in bulk te migreren. Zie de migratiehandleiding [voor](/help/assets/assets-migration-guide.md)Experience Manager.

### Vereisten en ondersteunde implementaties {#prerequisites}

Controleer de volgende punten voordat u deze functie gebruikt of configureert:

* De gebruikers maken deel uit van aangewezen gebruikersgroepen voor elke implementatie.
* Voor Adobe Experience Manager-implementatietypen moet aan een van de ondersteunde criteria zijn voldaan. [!DNL Experience Manager] 6.5 [!DNL Assets] werkt samen met [!DNL Experience Manager] de Cloud Service. Zie de functionaliteit [Verbonden middelen in Experience Manager als Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html)voor meer informatie.

   |  | [!DNL Experience Manager Sites] als cloudservice | Experience Manager 6.5 [!DNL Sites] op AMS | Experience Manager 6.5 [!DNL Sites] on-premise |
   |---|---|---|---|
   | **[!DNL Experience Manager Assets]als cloudservice ** | Ondersteund | Ondersteund | Ondersteund |
   | **Experience Manager 6.5[!DNL Assets]op AMS** | Ondersteund | Ondersteund | Ondersteund |
   | **Experience Manager 6.5[!DNL Assets]on-premise** | Niet ondersteund | Niet ondersteund | Niet ondersteund |

### Ondersteunde bestandsindelingen {#mimetypes}

Met de Content Finder kunnen auteurs zoeken naar afbeeldingen en de volgende typen documenten, waarna ze de gezochte assets gebruiken in de Pagina-editor. U kunt documenten toevoegen aan de `Download`-component en afbeeldingen aan de `Image`-component. Authors can also add the remote assets in any custom Experience Manager component that extends the default `Download` or `Image` components. De lijst met ondersteunde indelingen is:

* **Afbeeldingsindelingen**: De afbeeldingsindelingen die door de [component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/image.html) Image worden ondersteund, worden ondersteund door Connected Assets. [!DNL Dynamic Media] afbeeldingen worden niet ondersteund.
* **Documentindelingen**: Zie [Ondersteunde documentindelingen voor gekoppelde assets](assets-formats.md#supported-document-formats).

### Betrokken gebruikers en groepen {#users-and-groups-involved}

Hieronder worden de diverse rollen beschreven voor de configuratie en toepassing van een kenmerk en de overeenkomstige gebruikersgroepen. De lokale scope wordt gebruikt voor het gebruiksscenario waarin een webpagina wordt gemaakt door een auteur. De externe scope wordt gebruikt voor de DAM-implementatie die als host fungeert voor de vereiste assets. The [!DNL Sites] author fetches these remote assets.

| Rol | Scope | Gebruikersgroep | Gebruikersnaam in voorbeeldprocedure | Vereiste |
|---|---|---|---|---|
| [!DNL Sites] beheerder | Lokaal | Experience Manager `administrators` | `admin` | Stel Experience Manager in en configureer integratie met de externe [!DNL Assets] implementatie. |
| DAM-gebruiker | Lokaal | `Authors` | `ksaner` | Wordt gebruikt om de assets die bij `/content/DAM/connectedassets/` zijn opgehaald, weer te geven en te dupliceren. |
| [!DNL Sites] author | Lokaal | `Authors` (met lees toegang op verre DAM en auteurstoegang op lokaal [!DNL Sites]) | `ksaner` | End user are [!DNL Sites] authors who use this integration to improve their content velocity. De auteurs zoeken met de Content Finder naar assets in de externe DAM en gebruiken de vereiste afbeeldingen op lokale webpagina&#39;s. De referenties van de `ksaner` DAM-gebruiker worden gebruikt. |
| [!DNL Assets] beheerder | Extern | Experience Manager `administrators` | `admin` op externe Experience Manager | Configureer CORS (Cross-Origin Resource Sharing). |
| DAM-gebruiker | Extern | `Authors` | `ksaner` op externe Experience Manager | Auteur-rol bij de implementatie van de externe Experience Manager. Zoek en blader naar assets in gekoppelde assets met de Content Finder. |
| DAM-distributeur (technische gebruiker) | Extern | `Authors` | `ksaner` op externe Experience Manager | This user present on the remote deployment is used by Experience Manager local server (not the Site author role) to fetch the remote assets, on behalf of [!DNL Sites] author. Deze rol is anders dan de twee bovenstaande `ksaner`-rollen en hoort bij een andere gebruikersgroep. |

## Configure a connection between [!DNL Sites] and [!DNL Assets] deployments {#configure-a-connection-between-sites-and-assets-deployments}

Een beheerder van de Manager van de Ervaring kan deze integratie tot stand brengen. Once created, the permissions required to use it are established via user groups that are defined on the [!DNL Sites] deployment and on the DAM deployment.

To configure Connected Assets and local [!DNL Sites] connectivity, follow these steps.

1. Access an existing [!DNL Experience Manager Sites] deployment or create a deployment using the following command:

   1. Voer in de map van het JAR-bestand de volgende opdracht uit op een terminal om elke Experience Manager-server te maken.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. Na een paar minuten wordt de Experience Manager-server gestart. Consider this [!DNL Experience Manager Sites] deployment as the local machine for web page authoring, say at `https://[local_sites]:4502`.

1. Ensure that the users and roles with local scope exist on the Experience Manager Sites deployment and on the [!DNL Experience Manager Assets] deployment on AMS. Create a technical user on [!DNL Assets] deployment and add to the user group mentioned in [users and groups involved](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Heb toegang tot de lokale [!DNL Experience Manager Sites] plaatsing bij `https://[local_sites]:4502`. Klik op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > Configuratie **** Verbonden elementen en voer de volgende waarden in:

   1. [!DNL Experience Manager Assets] locatie is `https://[assets_servername_ams]:[port]`.
   1. Referenties van een DAM-distributeur (technische gebruiker).
   1. Voer in het veld **[!UICONTROL Onderkoppelpunt]** het lokale pad van Experience Manager in, waar Experience Manager de elementen ophaalt. Bijvoorbeeld de map `remoteassets`.
   1. Pas de waarden van de **[!UICONTROL Originele Binaire Drempel]** van de overdrachtoptimalisering afhankelijk van uw netwerk aan. De weergave van een asset die groter is dan deze drempelwaarde, wordt asynchroon overgedragen.
   1. Selecteer **[!UICONTROL Datastore die met Verbonden activa]**wordt gedeeld, als u een datastore gebruikt om uw activa op te slaan en de Datastore is de gemeenschappelijke opslag tussen beide plaatsingen van de Manager van de Ervaring. In dat geval is de drempelwaarde niet van belang, aangezien de binaire gegevens van de werkelijke asset in de datastore staan en niet worden overgedragen.
      ![Een typische configuratie voor gekoppelde assets](assets/connected-assets-typical-config.png)
   *Afbeelding: Een typische configuratie voor gekoppelde assets.*

1. Als de assets al zijn verwerkt en de weergaven zijn opgehaald, schakelt u de startprogramma&#39;s voor de workflow uit. Adjust the launcher configurations on the local ([!DNL Experience Manager Sites]) deployment to exclude the `connectedassets` folder, in which the remote assets are fetched.

   1. Klik bij [!DNL Experience Manager Sites] implementatie op **[!UICONTROL Extra]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.

   1. Zoeken naar opstarters met workflows als **[!UICONTROL DAM Update Asset]** en **[!UICONTROL DAM Metadata Writeback]**.

   1. Select the workflow launcher and click **[!UICONTROL Properties]** on the action bar.

   1. In the Properties wizard, change the **[!UICONTROL Path]** fields as the following mappings to update their regular expressions to exclude the mount point **[!UICONTROL connectedassets]**.
   | Voor | Na |
   |---|---|
   | `/content/dam(/((?!/subassets).)*/)renditions/original` | `/content/dam(/((?!/subassets)(?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/*/)renditions/original` | `/content/dam(/((?!connectedassets).)*/)renditions/original` |
   | `/content/dam(/*)/jcr:content/metadata` | `/content/dam(/((?!connectedassets).)*/)jcr:content/metadata` |

   >[!NOTE]
   >
   >Alle uitvoeringen die beschikbaar zijn op de implementatie van de externe Experience Manager worden opgehaald, wanneer auteurs middelen ophalen. Als u meer weergaven van een opgehaalde asset tot stand wilt brengen, moet u deze configuratiestap overslaan. The [!UICONTROL DAM Update Asset] workflow gets triggered and creates more renditions. These renditions are available only on the local [!DNL Sites] deployment and not on the remote DAM deployment.

1. Voeg de [!DNL Experience Manager Sites] instantie als één van de **[!UICONTROL Toegestane Oorsprong]** op de verre configuratie [!DNL Experience Manager Assets] CORS toe.

   1. Meld u aan met de beheerdersreferenties. Search for `Cross-Origin`. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.

   1. Als u bijvoorbeeld een CORS-configuratie wilt maken, klikt u op het pictogram [!DNL Experience Manager Sites] aem_assets_add_icon ![naast het pictogram](assets/aem_assets_add_icon.png) Adobe Granite Cross-Origin Resource Sharing Policy ****.

   1. In the field **[!UICONTROL Allowed Origins]**, input the URL of the local [!DNL Sites], that is, `https://[local_sites]:[port]`. Sla de configuratie op.

## Externe assets gebruiken {#use-remote-assets}

Auteurs van de website gebruiken Content Finder om verbinding te maken met de DAM-instantie. Auteurs kunnen externe assets zoeken, doorbladeren en naar een component slepen. Om de externe DAM te verifiëren, moet u de referenties van de DAM-gebruiker die door uw beheerder zijn verstrekt, bij de hand houden.

Auteurs kunnen de assets die zowel beschikbaar zijn op de lokale DAM-instantie als op de externe DAM-instantie, op één webpagina gebruiken. Gebruik de Content Finder om te schakelen tussen het doorzoeken van de lokale of de externe DAM.

Only those tags of remote assets are fetched that have an exact corresponding tag along with the same taxonomy hierarchy, available on the local [!DNL Sites] instance. Alle andere tags worden verwijderd. Auteurs kunnen naar externe middelen zoeken met alle tags die aanwezig zijn op de implementatie van de externe Experience Manager, aangezien Experience Manager een full-text zoekopdracht biedt.

### Procedure voor gebruik {#walk-through-of-usage}

Gebruik bovenstaande instellingen om de functionaliteit van een authoring-ervaring beter te begrijpen. Gebruik documenten of afbeeldingen van uw keuze op de externe DAM-implementatie.

1. Navigeer naar de [!DNL Assets] gebruikersinterface op de externe implementatie door **[!UICONTROL Middelen]** > **[!UICONTROL Bestanden]** te openen vanuit de [!DNL Experience Manager] werkruimte. U kunt `https://[assets_servername_ams]:[port]/assets.html/content/dam` ook in een browser openen. Upload de assets van uw keuze.
1. On the [!DNL Sites] instance, in the profile activator in the upper-right corner, click **[!UICONTROL Impersonate as]**. Provide `ksaner` as user name, select the option provided, and click **[!UICONTROL OK]**.
1. Open een websitepagina Web.Retail op **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bewerk de pagina. U kunt `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` ook in een browser openen om een pagina te bewerken.

   Klik op Zijpaneel **[!UICONTROL in-/]** uitschakelen in de linkerbovenhoek van de pagina.

1. Open het tabblad [!UICONTROL Middelen] en klik op **[!UICONTROL Aanmelden bij Connected Assets]**.
1. Geef de referenties op: `ksaner` als gebruikersnaam en `password` als wachtwoord. This user has authoring permissions on both the [!DNL Experience Manager] deployments.
1. Zoek naar de asset die u aan DAM hebt toegevoegd. De externe assets worden weergegeven in het linkerdeelvenster. Filter op afbeeldingen of documenten en filter verder op de typen ondersteunde documenten. Sleep de afbeeldingen naar een `Image`-component en sleep documenten naar een `Download`-component.

   The fetched assets are read-only on the local [!DNL Experience Manager Sites] deployment. You can still use the options provided by your [!DNL Experience Manager Sites] components to edit the fetched asset. Het bewerken op basis van componenten is niet-destructief.

   ![Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM](assets/filetypes_filter_connected_assets.png)

   *Afbeelding: Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM.*

1. De auteur van een site krijgt een melding als een asset asynchroon wordt opgehaald en als het ophalen mislukt. Tijdens (of zelfs na) het ontwerpen kunnen auteurs gedetailleerde informatie zien over het ophalen van taken en fouten in de gebruikersinterface voor [asynchrone taken](/help/assets/asynchronous-jobs.md).

   ![Melding van het asynchroon op de achtergrond ophalen van assets.](assets/assets_async_transfer_fails.png)

   *Afbeelding: Melding van het asynchroon op de achtergrond ophalen van assets.*

1. When publishing a page, [!DNL Experience Manager] displays a complete list of assets that are used in the page. Zorg ervoor dat de externe assets op het moment van publicatie worden opgehaald. Als u de status van elke opgehaalde asset wilt controleren, raadpleegt u de gebruikersinterface voor [asynchrone taken](/help/assets/asynchronous-jobs.md).

   >[!NOTE]
   >
   >Zelfs als een of meer externe assets niet worden opgehaald, wordt de pagina gepubliceerd. De component die gebruikmaakt van de externe asset, wordt leeg (zonder content) gepubliceerd. The [!DNL Experience Manager] notification area displays notification for errors that show in async jobs page.

>[!CAUTION]
>
>Zodra de opgehaalde externe assets op een webpagina worden toegepast, zijn ze doorzoekbaar en bruikbaar door iedereen met toegang tot de lokale map waarin de opgehaalde activa zijn opgeslagen (`connectedassets` in de bovenstaande procedure). The assets are also searchable and visible in the local repository via [!UICONTROL Content Finder].

De opgehaalde assets kunnen net als elke andere lokale asset worden gebruikt, alleen kunnen de bijbehorende metadata niet worden bewerkt.

## Beperkingen {#limitations}

**Machtigingen en assets beheren**

* Lokale assets worden niet gesynchroniseerd met de oorspronkelijke assets op de externe implementatie. Eventuele bewerkingen, verwijderingen of intrekkingen van machtigingen voor de DAM-implementatie worden niet verderop in de DAM-implementatie doorgegeven.
* Lokale assets zijn alleen-lezen kopieën. De componenten van de Manager van de ervaring doen niet-destructieve uitgeeft aan activa. Andere soorten bewerkingen zijn niet toegestaan.
* Lokaal opgehaalde assets zijn alleen beschikbaar voor authoring. Workflows voor het bijwerken van assets kunnen niet worden toegepast en metadata kunnen niet worden bewerkt.
* Alleen afbeeldingen en de vermelde documentindelingen worden ondersteund. [!DNL Dynamic Media] Elementen, inhoudsfragmenten en ervaringsfragmenten worden niet ondersteund.
* Metadataschema&#39;s worden niet opgehaald.
* All [!DNL Sites] authors have read permissions on the fetched copies, even if they do not have access to the remote DAM deployment.
* Geen API-ondersteuning om de integratie aan te passen.
* De functionaliteit ondersteunt naadloos zoeken en gebruiken van externe assets. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets te migreren. Zie de [Assets-migratiegids](assets-migration-guide.md).
* Het is niet mogelijk om een extern element te gebruiken als paginaminiatuur in de gebruikersinterface van [!UICONTROL Pagina-eigenschappen] . U kunt een miniatuur van een webpagina instellen in de gebruikersinterface [!UICONTROL Pagina-eigenschappen] vanuit de [!UICONTROL miniatuur] door op Afbeelding selecteren te klikken.

**Installatie en licenties**

* [!DNL Experience Manager Assets] implementatie op AMS wordt ondersteund.
* [!DNL Experience Manager Sites] kan tegelijkertijd verbinding maken met één [!DNL Experience Manager Assets] opslagplaats.
* A license of [!DNL Experience Manager Assets] working as remote repository.
* One or more licenses of [!DNL Experience Manager Sites] working as local authoring deployment.

**Gebruik**

* De enige functionaliteit die wordt ondersteund is het zoeken naar externe assets en deze slepen en neerzetten op de lokale pagina voor de authoring van content.
* Voor ophaalbewerkingen geldt een time-out na 5 seconden. Auteurs kunnen problemen ervaren bij het ophalen van assets, bijvoorbeeld als er netwerkproblemen optreden. Auteurs kunnen opnieuw proberen door het externe element van de [!UICONTROL Content Finder] naar de [!UICONTROL Page Editor]te slepen.
* Eenvoudige bewerkingen die niet-destructief zijn en bewerkingen die worden ondersteund via de [!DNL Experience Manager]-component van , kunnen worden uitgevoerd op opgehaalde elementen. `Image` Assets zijn alleen-lezen.

## Problemen oplossen {#troubleshoot}

Voer de volgende stappen uit om problemen op te lossen voor algemene foutscenario&#39;s:

* Als u niet naar externe assets kunt zoeken in Content Finder, controleert u opnieuw of de vereiste rollen en machtigingen aanwezig zijn.
* Assets die worden opgehaald van een externe DAM, worden mogelijk niet op een webpagina gepubliceerd. Dit kan gebeuren in de volgende gevallen: de asset is niet aanwezig op de externe DAM; de juiste machtigingen voor het ophalen ontbreken; netwerkfout. Zorg ervoor dat de asset niet wordt verwijderd van de externe DAM of dat de machtigingen niet worden gewijzigd; zorg dat aan alle toepasselijke vereisten wordt voldaan; voeg de asset opnieuw toe aan de pagina en publiceer de pagina nogmaals. Controleer de [lijst met asynchrone taken](/help/assets/asynchronous-jobs.md) op fouten bij het ophalen van assets.
