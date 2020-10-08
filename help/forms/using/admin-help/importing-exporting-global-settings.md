---
title: Algemene instellingen importeren en exporteren
seo-title: Algemene instellingen importeren en exporteren
description: U kunt zoeksjabloondefinities en algemene instellingen voor Workspace importeren en exporteren.
seo-description: U kunt zoeksjabloondefinities en algemene instellingen voor Workspace importeren en exporteren.
uuid: 8f1f210d-e850-4b2c-bb5a-942fa8299791
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 72fe5749-2fa2-442f-b679-7889faeafcac
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---


# Algemene instellingen importeren en exporteren {#importing-and-exporting-global-settings}

U kunt zoeksjabloondefinities en algemene instellingen voor Workspace importeren en exporteren.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor AEM formulierrelease.

U kunt bijvoorbeeld van een ontwikkelomgeving naar een productieomgeving gaan door de definities van zoeksjablonen en globale instellingen van de ene omgeving te exporteren en deze in de andere omgeving te importeren.

Nadat u het algemene instellingenbestand hebt geëxporteerd, kunt u de instellingen in een XML- of teksteditor wijzigen. De enige instellingen die u wilt bewerken zijn echter de instellingen JChannelConnectionProperties, formViewOnly en specialRoutes. Zie Algemene instellingen voor [werkruimte voor meer informatie](importing-exporting-global-settings.md#workspace-global-settings).


>[!NOTE]
>
>Als u de gebeurteniseigenschappen wijzigt in het algemene instellingenbestand, moet u de server opnieuw starten.

## Een zoeksjabloondefinitie importeren {#import-a-search-template-definition}

1. Klik in de beheerconsole op Services > Workspace > Global Administration.
1. Klik onder Sjabloondefinitie importeren op Bestand kiezen en selecteer de zoeksjabloon. U kunt alleen zoeksjabloondefinities importeren die oorspronkelijk zijn geëxporteerd uit een exemplaar van Workspace.
1. Klik op Importeren.

## Een zoeksjabloondefinitie exporteren {#export-a-search-template-definition}

1. Voor de Globale pagina van het Beleid, onder de definitie van het het onderzoeksmalplaatje van de Uitvoer, klik Lijst allen.
1. Selecteer in de lijst met zoeksjablonen de sjabloon die u wilt exporteren.

   >[!NOTE]
   >
   >U kunt meerdere sjablonen selecteren, maar alleen de laatst geselecteerde sjabloon wordt geëxporteerd.

1. Klik op Exporteren en sla het bestand op uw computer op.

## Algemene instellingen importeren {#import-global-settings}

1. Klik op de pagina Algemeen beheer onder Globale instellingen importeren op Bestand kiezen en selecteer het algemene instellingenbestand. Het algemene instellingenbestand moet de XML-indeling hebben.
1. Klik op Importeren.

## Algemene instellingen exporteren {#export-global-settings}

1. Voor de Globale pagina van het Beleid, onder de Globale Montages van de Uitvoer, klik de Uitvoer.
1. Sla het bestand op uw computer op.

## Algemene instellingen werkruimte {#workspace-global-settings}

U kunt het algemene instellingenbestand wijzigen; de enige instellingen die u wilt bewerken zijn echter de instellingen JChannelConnectionProperties, formViewOnly en specialRoutes.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor AEM formulierrelease.

Het bestand met algemene instellingen voor Workspace bevat de volgende instellingen:

### specialRoutes, instellingen {#specialroutes-settings}

De *specialRoutes* montages specificeren de eigenschappen van de speciale routes, goedkeuren en ontkennen, in Werkruimte. In bepaalde situaties worden de knoppen voor deze routes weergegeven op de taakkaarten in Workspace en kan de gebruiker deze selecteren zonder het formulier te openen. U kunt de specialRoutes montages in het globale montagedossier wijzigen om aangepaste namen toe te voegen voor goedkeuren en ontkennen of om extra routes tot stand te brengen.

**client_specialRoutes_routes_accept_style:** De naam van de stijl die zich in het thema Werkruimte bevindt. Hiermee worden de pictogrammen voor goed keuren weergegeven. De stijl moet waarden voor een ingeschakeld pictogram en een uitgeschakeld pictogram bevatten. Als u een stijl voor een aangepaste knop wilt definiëren, moet u de volgende sjabloon gebruiken:
` .buttonApprove {  icon: Embed('images/LC_DirectApprove_Sm_N.png');  disabledIcon: Embed('images/LC_DirectApprove_Sm_D.png');  paddingLeft: 5;  }` Het CSS-bestand voor de werkruimte is ingesloten in het bestand workspace-theme.swf, dat zich bevindt in het bestand adobe-workspace-client.ear > adobe-workspace-client.war. Als u de weergave van de werkruimte wilt wijzigen, moet u het bestand workspace-theme.swf opnieuw compileren.

**client_specialRoutes_routes_deny_names:** De verscheidenheid van koorden die een gebruiker Workbench kan gebruiken om als &quot;ontkennen&quot;te worden geïnterpreteerd. De tekenreeksen zijn hoofdlettergevoelig. De standaardwaarde is bijvoorbeeld Weigeren. Als de Workbench-gebruiker het woord Weigeren in een proces gebruikt, wordt het woord niet herkend. Het woord ontkent moet aan dit het plaatsen voor de routeknoop worden toegevoegd om te worden aangepast en de stijl hebben op het worden toegepast.

**client_specialRoutes_routes_deny_style:** De naam van de stijl die zich in het het themadossier van de Werkruimte bevindt, dat ontkent knooppictogrammen identificeert. De stijl moet waarden voor een ingeschakeld pictogram en een uitgeschakeld pictogram bevatten. Als u een stijl voor een aangepaste knop wilt definiëren, moet u de volgende sjabloon gebruiken:
`  .buttonDeny {   icon: Embed('images/LC_DirectDeny_Sm_N.png');   disabledIcon: Embed('images/LC_DirectDeny_Sm_D.png');   paddingLeft: 0;   }` **client_specialRoutes_routes_accept_names:** De verscheidenheid van koorden die een gebruiker Workbench kan gebruiken om als &quot;goed te keuren&quot;worden geïnterpreteerd. De tekenreeksen zijn hoofdlettergevoelig. De standaardwaarde is bijvoorbeeld Goedkeuren. Als de Workbench-gebruiker het woord Goedkeuren in een proces gebruikt, wordt het woord niet herkend. Het woord keurt moet aan dit het plaatsen voor de routeknoop worden toegevoegd om worden aangepast en de stijl hebben op het worden toegepast.

**client_specialRoutes_names:** De sleutels die worden gebruikt om van de aangepaste koordwaarde van de middeldossiers de plaats te bepalen. Elk item in deze instelling moet de waarden voor de namen en stijl bevatten.

### JGroup-instellingen {#jgroup-settings}

Deze instellingen worden alleen weergegeven als u een upgrade hebt uitgevoerd vanaf Adobe LiveCycle 2.5 of eerder.

**server_remoteevents_ClientTimeoutMilliseconds:** De maximale tijd die de JGroup wacht voor gebeurtenisberichten. Deze instelling mag niet worden gewijzigd.

**server_remoteevents_ServerTimeoutMilliseconds:** De time-out voor het ontvangen van JGroup-berichten op de server. Met deze optie stelt u de vertraging in voor het verzenden van berichten van de server naar de client.

**server_remoteevents_JChannelConnectionProperties:** De verbindingseigenschappen voor de JGroup die worden gebruikt om tussen de server (waarop een de dienstgebeurtenis door de dienst RemoteEvent wordt verwerkt) en alle instanties van Werkruimte te communiceren.

U kunt de waarden UDP voor het multicast IP adres (mcast_addr), de multicastIP haven (mcast_port), en TTL voor de multicast pakketten (ip_ttl) moeten veranderen. Door gebrek, worden het multicast IP adres en de havenwaarden willekeurig geproduceerd en, over het algemeen, te hoeven de waarden niet worden veranderd. Nochtans, als uw bedrijf om het even welk netwerkbeleid betreffende specifieke multicast waaiers voor multicast IP adressen heeft, kunt u de waarden moeten veranderen.

>[!NOTE]
>
>De TTL moet groter zijn dan het aantal netwerkschakelaars tussen de servers in de cluster; nochtans, als de waarde te hoog wordt geplaatst, kan het multicast pakketten veroorzaken om in subnets te reizen, waar zij zullen worden verworpen.

De overige eigenschappen in deze instelling mogen niet worden gewijzigd.

**server_remoteevents_JGroupName:** De naam van de JGroup die wordt gebruikt voor communicatie via een externe gebeurtenis. Deze waarde wordt willekeurig gegenereerd om conflicten in clusters te voorkomen. Deze waarde moet niet worden gewijzigd.

Voor extra informatie over JGroups en Werkruimte, zie de Werkruimte van [JGroups en AEM van vormen - Verklaard](https://blogs.adobe.com/livecycle/2011/03/jgroups-and-livecycle-workspace-explained.html).

### formView-instellingen {#formview-settings}

**client_formView_openFormInFullScreen:** Als u alle formulieren in Workspace wilt weergeven in de modus Volledig scherm, stelt u deze optie in op true. Deze optie is standaard ingesteld op false en formulieren worden niet in de modus Volledig scherm weergegeven. De service Gebruiker bevat een optie waarmee u het document dat aan een taak is gekoppeld, in de modus Volledig scherm kunt openen. Hierdoor kunt u de weergave per proces besturen.

**client_routes_formViewOnly:** Wanneer geplaatst aan Waar, worden de routes niet getoond in kaartmening of lijstmening in Werkruimte. De standaardwaarde is Vals, betekenend dat de routes in kaartmening en lijstmening worden getoond.

### Overige instellingen {#other-settings}

**client_mimeTypes_openOutsideBrowser:** Het MIME-type van documenten die buiten de Workspace browser-instantie worden geopend. Als de processen van uw organisatie een extra type MIME vereisen, specificeer het hier. De standaardwaarden zijn:

* `application/msword`
* `application/msexcel`
* `application/ms-powerpoint`

**client_customUI_caching:** Hiermee wordt een gebruikersinterface voor een aangepaste taak vastgezet.

**server_debugLevel:** Wijzig deze instelling niet.

**client_pollingInterval:** Hiermee stelt u het opiniepeilingsinterval (in seconden) in dat wordt gebruikt op de Flex Workspace (Vervangen voor AEM formulieren op JEE) voor het detecteren van nieuwe en gewijzigde taken. De standaardwaarde is 3 seconden. Dit werkt niet voor AEM Forms Workspace.

**client_systemContext_name:** Geef een aangepaste naam (bijvoorbeeld Burger) op die u wilt weergeven in het veld Toegevoegd op (op het tabblad Bijlagen) voor de bijlagen van een taak in AEM Forms Workspace.

De aangepaste naam definiëren:

`<client_systemContext_name>[custom name to display]</client_systemContext_name>`

>[!NOTE]
>
>Voor de toepassing Demo is de standaardweergavenaam **Citizen**. Voor een aangepaste toepassing die u maakt, is de standaardweergavenaam **Systeemcontextaccount**.
>
>**client_idleTimeout:** Wanneer een gebruiker gedurende een bepaalde periode inactief blijft, verloopt de AEM Forms Workspace-sessie. Als u deze functie wilt inschakelen, voegt u een item toe aan Algemene instellingen &lt;client_idleTimeout>*IDLE_TIMEOUT_IN_SECONDS*&lt;/client_idleTimeout>. U kunt waarde 0 opgeven om de time-out bij inactiviteit uit te schakelen. De hoeveelheid tijd wordt opgegeven in seconden.
