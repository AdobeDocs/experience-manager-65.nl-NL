---
title: Met gekoppelde assets kunt u DAM-assets delen in de authoringworkflow van Adobe Experience Manager Sites
description: Gebruik de assets die beschikbaar zijn op een externe implementatie van Adobe Experience Manager Assets bij het maken van uw webpagina's op een andere implementatie van een Experience Manager-site.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 7628b5edd52a144aa4f92f8145493b9b927aeda0

---


# Gekoppelde assets gebruiken om DAM-assets te delen in AEM-sites {#use-connected-assets-to-share-dam-assets-in-aem-sites}

In grote ondernemingen is de infrastructuur voor het maken van websites soms gedistribueerd. Soms zijn de functies en de digitale assets voor het maken van websites opgenomen in verschillende implementaties. Enkele redenen zijn bijvoorbeeld bestaande, geografisch gedistribueerde implementaties die vereist zijn voor samenwerking, of acquisities die leiden tot heterogene infrastructuren die het moederbedrijf alsnog samen wil gebruiken.

AEM Sites biedt functies voor het maken van webpagina&#39;s en AEM Assets is het DAM-systeem (Digital Asset Management) dat de vereiste assets voor websites levert. AEM biedt nu ondersteuning voor het bovenstaande gebruiksscenario door de integratie van AEM Sites en AEM Assets.

## Overzicht van gekoppelde assets {#overview-of-connected-assets}

Bij het bewerken van pagina&#39;s in de Pagina-editor kunnen auteurs naadloos zoeken naar assets van een andere AEM Assets-implementatie, door deze assets bladeren en ze insluiten. Een AEM-beheerder kan een eenmalige integratie uitvoeren van een lokale implementatie van AEM Sites met een andere (externe) implementatie van AEM Assets.

Voor Sites-auteurs zijn externe assets lokaal als alleen-lezen beschikbaar. Met deze functie kunt u naadloos zoeken naar telkens een klein aantal externe assets voor gebruik. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets in bulk te migreren. Zie de [Assets-migratiegids](/help/assets/assets-migration-guide.md).

### Vereisten en ondersteunde implementaties {#prerequisites}

Controleer de volgende punten voordat u deze functie gebruikt of configureert:

* De gebruikers maken deel uit van aangewezen gebruikersgroepen voor elke implementatie.
* Voor Adobe Experience Manager-implementatietypen moet aan een van de ondersteunde criteria zijn voldaan. AEM 6.5-middelen werken met AEM als cloudservice. Zie de functionaliteit [Verbonden middelen in AEM als Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html)voor meer informatie.

   |  | AEM Sites as a Cloud Service | AEM 6.5 Sites on AMS | AEM 6.5 Sites on-premise |
   |---|---|---|---|
   | **AEM Assets as a Cloud Service** | Ondersteund | Ondersteund | Ondersteund |
   | **AEM 6.5 Assets on AMS** | Ondersteund | Ondersteund | Ondersteund |
   | **AEM 6.5 Assets on-premise** | Niet ondersteund | Niet ondersteund | Niet ondersteund |

### Ondersteunde bestandsindelingen {#mimetypes}

Met de Content Finder kunnen auteurs zoeken naar afbeeldingen en de volgende typen documenten, waarna ze de gezochte assets gebruiken in de Pagina-editor. U kunt documenten toevoegen aan de `Download`-component en afbeeldingen aan de `Image`-component. Auteurs kunnen de externe assets toevoegen aan elke aangepaste AEM-component die een uitbreiding vormt op de standaardcomponenten `Download` of `Image`. De lijst met ondersteunde indelingen is:

* **Afbeeldingsindelingen**: De afbeeldingsindelingen die door de [component](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/image.html) Image worden ondersteund, worden ondersteund door Connected Assets. Dynamic Media-afbeeldingen worden niet ondersteund.
* **Documentindelingen**: Zie [Ondersteunde documentindelingen voor gekoppelde assets](assets-formats.md#supported-document-formats).

### Betrokken gebruikers en groepen {#users-and-groups-involved}

Hieronder worden de diverse rollen beschreven voor de configuratie en toepassing van een kenmerk en de overeenkomstige gebruikersgroepen. De lokale scope wordt gebruikt voor het gebruiksscenario waarin een webpagina wordt gemaakt door een auteur. De externe scope wordt gebruikt voor de DAM-implementatie die als host fungeert voor de vereiste assets. De Sites-auteur haalt deze externe assets op.

| Rol | Scope | Gebruikersgroep | Gebruikersnaam in voorbeeldprocedure | Vereiste |
|---|---|---|---|---|
| AEM Sites-beheerder | Lokaal | AEM-beheerder | `admin` | Installeer AEM en configureer de integratie met de externe Assets-implementatie. |
| DAM-gebruiker | Lokaal | Auteur | `ksaner` | Wordt gebruikt om de assets die bij `/content/DAM/connectedassets/` zijn opgehaald, weer te geven en te dupliceren. |
| AEM Sites-auteur | Lokaal | Auteur (met leestoegang op de externe DAM en auteurstoegang op lokale sites) | `ksaner` | Eindgebruikers zijn Sites-auteurs die deze integratie gebruiken om de snelheid van de content te verbeteren. De auteurs zoeken met de Content Finder naar assets in de externe DAM en gebruiken de vereiste afbeeldingen op lokale webpagina&#39;s. De referenties van de `ksaner` DAM-gebruiker worden gebruikt. |
| AEM Assets-beheerder | Extern | AEM-beheerder | `admin` op externe AEM | Configureer CORS (Cross-Origin Resource Sharing). |
| DAM-gebruiker | Extern | Auteur | `ksaner` op externe AEM | Auteursrol bij de externe AEM-implementatie. Zoek en blader naar assets in gekoppelde assets met de Content Finder. |
| DAM-distributeur (technische gebruiker) | Extern | Pakketontwikkelaars en siteauteurs | `ksaner` op externe AEM | Deze gebruiker die aanwezig is op de externe implementatie, wordt door de lokale AEM-server (en niet door de rol van de Sites-auteur) gebruikt om de externe assets op te halen namens de Sites-auteur. Deze rol is anders dan de twee bovenstaande `ksaner`-rollen en hoort bij een andere gebruikersgroep. |

## Een koppeling configureren tussen Sites- en Assets-implementaties {#configure-a-connection-between-sites-and-assets-deployments}

Een AEM-beheerder kan deze integratie maken. Wanneer dat is gebeurd, worden de vereiste gebruiksmachtigingen ingesteld via gebruikersgroepen die zijn gedefinieerd in de Sites- en DAM-implementaties.

Voer de volgende stappen uit om gekoppelde assets te configureren met de lokale Sites-connectiviteit.

1. Toegang krijgen tot een bestaande AEM Sites-implementatie of een implementatie maken met de volgende opdracht:

   1. In de map van het JAR-bestand gebruikt u de volgende opdracht op een terminal om elke AEM-server te maken.
      `java -XX:MaxPermSize=768m -Xmx4096m -jar <quickstart jar filepath> -r samplecontent -p 4502 -nofork -gui -nointeractive &`

   1. Na enkele minuten wordt de AEM-server gestart. Beschouw deze AEM Sites-implementatie als de lokale computer voor het ontwerpen van webpagina&#39;s, bijvoorbeeld op `https://[local_sites]:4502`.

1. Zorg dat de AEM Sites-implementatie en de AEM Assets-implementatie op AMS beschikken over gebruikers en rollen met een lokale scope. Maak een technische gebruiker op de Assets-implementatie en voeg deze toe aan de gebruikersgroep die wordt vermeld in de [betrokken gebruikers en groepen](/help/assets/use-assets-across-connected-assets-instances.md#users-and-groups-involved).

1. Ga naar de lokale AEM Sites-implementatie op `https://[local_sites]:4502`. Klik op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Middelen]** > Configuratie **** Verbonden elementen en voer de volgende waarden in:

   1. De locatie van AEM Assets is `https://[assets_servername_ams]:[port]`.
   1. Referenties van een DAM-distributeur (technische gebruiker).
   1. In **[!UICONTROL Mount Point]** field, enter the local AEM path where AEM fetches the assets. Bijvoorbeeld de map `remoteassets`.
   1. Pas de waarden van de **[!UICONTROL Originele Binaire Drempel]** van de overdrachtoptimalisering afhankelijk van uw netwerk aan. De weergave van een asset die groter is dan deze drempelwaarde, wordt asynchroon overgedragen.
   1. Select **[!UICONTROL Datastore Shared with Connected Assets]**, if you use a datastore to store your assets and the Datastore is the common storage between both AEM deployments. In dat geval is de drempelwaarde niet van belang, aangezien de binaire gegevens van de werkelijke asset in de datastore staan en niet worden overgedragen.
      ![Een typische configuratie voor gekoppelde assets](assets/connected-assets-typical-config.png)
   *Afbeelding: Een typische configuratie voor gekoppelde assets*

1. Als de assets al zijn verwerkt en de weergaven zijn opgehaald, schakelt u de startprogramma&#39;s voor de workflow uit. Pas de configuraties van het startprogramma op de lokale (AEM Sites) implementatie aan zodat de map `connectedassets` waarin de externe assets worden opgehaald, wordt uitgesloten.

   1. Klik op de implementatie van AEM-sites op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Workflow]** > **[!UICONTROL Launchers]**.

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
   >Alle weergaven die beschikbaar zijn op de externe AEM-implementatie worden opgehaald wanneer auteurs een asset ophalen. Als u meer weergaven van een opgehaalde asset tot stand wilt brengen, moet u deze configuratiestap overslaan. The [!UICONTROL DAM Update Asset] workflow gets triggered and creates more renditions. These renditions are available only on the local [!DNL Sites] deployment and not on the remote DAM deployment.

1. Add the AEM Sites instance as one of the **[!UICONTROL Allowed Origins]** on the remote AEM Assets&#39; CORS configuration.

   1. Meld u aan met de beheerdersreferenties. Zoek naar Cross-Origin. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**.

   1. Als u een CORS-configuratie voor de instantie AEM Sites wilt maken, klikt u op het pictogram ![aem_assets_add_icon](assets/aem_assets_add_icon.png) naast **[!UICONTROL Adobe Granite Cross-Origin Resource Sharing Policy]**.

   1. In the field **[!UICONTROL Allowed Origins]**, input the URL of the local Sites, that is, `https://[local_sites]:[port]`. Sla de configuratie op.

## Externe assets gebruiken {#use-remote-assets}

Auteurs van de website gebruiken Content Finder om verbinding te maken met de DAM-instantie. Auteurs kunnen externe assets zoeken, doorbladeren en naar een component slepen. Om de externe DAM te verifiëren, moet u de referenties van de DAM-gebruiker die door uw beheerder zijn verstrekt, bij de hand houden.

Auteurs kunnen de assets die zowel beschikbaar zijn op de lokale DAM-instantie als op de externe DAM-instantie, op één webpagina gebruiken. Gebruik de Content Finder om te schakelen tussen het doorzoeken van de lokale of de externe DAM.

Alleen die tags met externe elementen worden opgehaald die een exacte corresponderende tag hebben, samen met dezelfde taxonomihiërarchie, die beschikbaar is in de lokale Sites-instantie. Alle andere tags worden verwijderd. Auteurs kunnen naar externe assets zoeken met behulp van alle tags die zich op de externe AEM-implementatie bevinden, aangezien AEM een volledige-tekstzoekopdracht biedt.

### Procedure voor gebruik {#walk-through-of-usage}

Gebruik bovenstaande instellingen om de functionaliteit van een authoring-ervaring beter te begrijpen. Gebruik documenten of afbeeldingen van uw keuze op de externe DAM-implementatie.

1. Navigate to the Assets UI on the remote deployment by accessing **[!UICONTROL Assets]** > **[!UICONTROL Files]** from AEM workspace. U kunt `https://[assets_servername_ams]:[port]/assets.html/content/dam` ook in een browser openen. Upload de assets van uw keuze.
1. On the Sites instance, in the profile activator in the upper-right corner, click **[!UICONTROL Impersonate as]**. Provide `ksaner` as user name, select the option provided, and click **[!UICONTROL OK]**.
1. Open een websitepagina Web.Retail op **[!UICONTROL Sites]** > **[!UICONTROL We.Retail]** > **[!UICONTROL us]** > **[!UICONTROL en]**. Bewerk de pagina. U kunt `https://[aem_server]:[port]/editor.html/content/we-retail/us/en/men.html` ook in een browser openen om een pagina te bewerken.

   Klik op Zijpaneel **[!UICONTROL in-/]** uitschakelen in de linkerbovenhoek van de pagina.

1. Open het tabblad Middelen en klik op **[!UICONTROL Aanmelden bij Connected Assets]**.
1. Geef de referenties op: `ksaner` als gebruikersnaam en `password` als wachtwoord. Deze gebruiker heeft auteursmachtigingen op beide AEM-implementaties.
1. Zoek naar de asset die u aan DAM hebt toegevoegd. De externe assets worden weergegeven in het linkerdeelvenster. Filter op afbeeldingen of documenten en filter verder op de typen ondersteunde documenten. Sleep de afbeeldingen naar een `Image`-component en sleep documenten naar een `Download`-component.

   De opgehaalde assets zijn als alleen-lezen beschikbaar op de lokale AEM Sites-implementatie. U kunt nog steeds de opties gebruiken die door uw AEM Sites-componenten worden geboden om de opgehaalde asset te bewerken. Het bewerken op basis van componenten is niet-destructief.

   ![Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM](assets/filetypes_filter_connected_assets.png)

   *Afbeelding: Opties voor het filteren van documenttypen en afbeeldingen bij het zoeken naar assets op de externe DAM*

1. De auteur van een site krijgt een melding als een asset asynchroon wordt opgehaald en als het ophalen mislukt. Tijdens (of zelfs na) het ontwerpen kunnen auteurs gedetailleerde informatie zien over het ophalen van taken en fouten in de gebruikersinterface voor [asynchrone taken](/help/assets/asynchronous-jobs.md).

   ![Melding van het asynchroon op de achtergrond ophalen van assets.](assets/assets_async_transfer_fails.png)

   *Afbeelding: Melding van het asynchroon op de achtergrond ophalen van assets*

1. Bij het publiceren van een pagina wordt in AEM een volledige lijst met assets weergegeven die op de pagina worden gebruikt. Zorg ervoor dat de externe assets op het moment van publicatie worden opgehaald. Als u de status van elke opgehaalde asset wilt controleren, raadpleegt u de gebruikersinterface voor [asynchrone taken](/help/assets/asynchronous-jobs.md).

   >[!NOTE]
   >
   >Zelfs als een of meer externe assets niet worden opgehaald, wordt de pagina gepubliceerd. De component die gebruikmaakt van de externe asset, wordt leeg (zonder content) gepubliceerd. In het AEM-berichtenvak wordt een melding weergegeven voor fouten die worden weergegeven op pagina&#39;s met asynchrone taken.

>[!CAUTION]
>
>Zodra de opgehaalde externe assets op een webpagina worden toegepast, zijn ze doorzoekbaar en bruikbaar door iedereen met toegang tot de lokale map waarin de opgehaalde activa zijn opgeslagen (`connectedassets` in de bovenstaande procedure). The assets are also searchable and visible in the local repository via [!UICONTROL Content Finder].

De opgehaalde assets kunnen net als elke andere lokale asset worden gebruikt, alleen kunnen de bijbehorende metadata niet worden bewerkt.

## Beperkingen {#limitations}

**Machtigingen en assets beheren**

* Lokale assets worden niet gesynchroniseerd met de oorspronkelijke assets op de externe implementatie. Eventuele bewerkingen, verwijderingen of intrekkingen van machtigingen voor de DAM-implementatie worden niet verderop in de DAM-implementatie doorgegeven.
* Lokale assets zijn alleen-lezen kopieën. AEM-componenten voeren niet-destructieve bewerkingen uit op assets. Andere soorten bewerkingen zijn niet toegestaan.
* Lokaal opgehaalde assets zijn alleen beschikbaar voor authoring. Workflows voor het bijwerken van assets kunnen niet worden toegepast en metadata kunnen niet worden bewerkt.
* Alleen afbeeldingen en de vermelde documentindelingen worden ondersteund. Dynamic Media-assets, contentfragmenten en ervaringsfragmenten worden niet ondersteund.
* Metadataschema&#39;s worden niet opgehaald.
* Alle Sites-auteurs hebben leesmachtigingen voor de opgehaalde kopieën, zelfs als ze geen toegang hebben tot de externe DAM-implementatie.
* Geen API-ondersteuning om de integratie aan te passen.
* De functionaliteit ondersteunt naadloos zoeken en gebruiken van externe assets. Als u veel externe assets in één keer beschikbaar wilt maken voor lokale implementatie, kunt u overwegen om de assets te migreren. Zie de [Assets-migratiegids](assets-migration-guide.md).
* Het is niet mogelijk om een extern element te gebruiken als paginaminiatuur in de gebruikersinterface van [!UICONTROL Pagina-eigenschappen] . U kunt een miniatuur van een webpagina instellen in de gebruikersinterface [!UICONTROL Pagina-eigenschappen] vanuit de [!UICONTROL miniatuur] door op Afbeelding selecteren te klikken.

**Installatie en licenties**

* AEM Assets-implementatie op AMS wordt ondersteund.
* AEM Sites kan met één AEM Assets-repository tegelijkertijd worden verbonden.
* Een licentie voor AEM Assets die fungeert als externe repository.
* Een of meer licenties voor AEM Sites die fungeren als lokale implementatie voor authoring.

**Gebruik**

* De enige functionaliteit die wordt ondersteund is het zoeken naar externe assets en deze slepen en neerzetten op de lokale pagina voor de authoring van content.
* Voor ophaalbewerkingen geldt een time-out na 5 seconden. Auteurs kunnen problemen ervaren bij het ophalen van assets, bijvoorbeeld als er netwerkproblemen optreden. Auteurs kunnen opnieuw proberen door het externe element van de [!UICONTROL Content Finder] naar de [!UICONTROL Page Editor]te slepen.
* Eenvoudige bewerkingen die niet-destructief zijn en bewerkingen die worden ondersteund via de `Image`-component van AEM, kunnen worden uitgevoerd op opgehaalde elementen. Assets zijn alleen-lezen.

## Problemen oplossen {#troubleshoot}

Voer de volgende stappen uit om problemen op te lossen voor algemene foutscenario&#39;s:

* Als u niet naar externe assets kunt zoeken in Content Finder, controleert u opnieuw of de vereiste rollen en machtigingen aanwezig zijn.
* Assets die worden opgehaald van een externe DAM, worden mogelijk niet op een webpagina gepubliceerd. Dit kan gebeuren in de volgende gevallen: de asset is niet aanwezig op de externe DAM; de juiste machtigingen voor het ophalen ontbreken; netwerkfout. Zorg ervoor dat de asset niet wordt verwijderd van de externe DAM of dat de machtigingen niet worden gewijzigd; zorg dat aan alle toepasselijke vereisten wordt voldaan; voeg de asset opnieuw toe aan de pagina en publiceer de pagina nogmaals. Controleer de [lijst met asynchrone taken](/help/assets/asynchronous-jobs.md) op fouten bij het ophalen van assets.
