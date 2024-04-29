---
title: Gebruikerssynchronisatie van gemeenschappen
description: Leer hoe gebruikerssynchronisatie werkt in Adobe Experience Manager Communities.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: ecd30f5d-ad31-4482-96d3-c92f1cf91336
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2403'
ht-degree: 0%

---

# Gebruikerssynchronisatie van gemeenschappen {#communities-user-synchronization}

## Inleiding {#introduction}

In de gemeenschappen van Adobe Experience Manager (AEM), van het Publish milieu (afhankelijk van toestemmingen die worden gevormd), *sitebezoekers* kan worden *leden*, maken *gebruikersgroepen* en bewerken *gebruikersprofiel* .

*Gebruikersgegevens* verwijst naar *gebruikers*, *gebruikersprofielen*, en *gebruikersgroepen*.

*Leden* verwijzen naar *gebruikers* geregistreerd in de publicatieomgeving, in tegenstelling tot gebruikers die zijn geregistreerd in de auteursomgeving.

Ga voor meer informatie over gebruikersgegevens naar [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).

## Gebruikers in een publicatiebedrijf synchroniseren {#synchronizing-users-across-a-publish-farm}

Gebruikersgegevens die in de publicatieomgeving zijn gemaakt, worden door het ontwerp niet weergegeven in de auteuromgeving.

De meeste gebruikersgegevens die in de auteuromgeving worden gemaakt, blijven in de Auteur-omgeving en worden niet gesynchroniseerd of gerepliceerd naar Publicatie-instanties.

Wanneer de [topologie](/help/communities/topologies.md) is een [publicatiebedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm), registratie en wijzigingen die worden aangebracht op één instantie Publiceren, moeten worden gesynchroniseerd met andere instanties Publish. Leden moeten zich kunnen aanmelden en hun gegevens kunnen bekijken op elk knooppunt Publish.

Wanneer gebruikerssynchronisatie wordt toegelaten, worden de gebruikersgegevens automatisch gesynchroniseerd over de Publish instanties in het landbouwbedrijf.

### Instructies voor het synchroniseren van gebruikers {#user-sync-setup-instructions}

Voor gedetailleerde, geleidelijke instructies op hoe te om synchronisatie over toe te laten publiceert landbouwbedrijf, zie [Gebruikerssynchronisatie](/help/sites-administering/sync.md).

## Gebruikerssynchronisatie op de achtergrond {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **vlt-pakket**

  Het is een ZIP-bestand met alle wijzigingen die op een uitgever zijn aangebracht en die over alle uitgevers moeten worden verspreid. Wijzigingen op een uitgever genereren gebeurtenissen die door de gebeurtenislistener voor wijzigingen worden gekozen. Hiermee maakt u een vlt-pakket dat alle wijzigingen bevat.

* **distributiepakket**

  Het bevat distributieinformatie voor Sling. Dat is informatie over waar de inhoud moet worden verspreid en wanneer deze als laatste is verspreid.

## Wat gebeurt er als ... {#what-happens-when}

### Site publiceren vanuit console Communitysites {#publish-site-from-communities-sites-console}

Op auteur, wanneer een communautaire plaats van [Community Sites-console](/help/communities/sites-console.md), heeft het effect [repliceren](/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) de bijbehorende pagina&#39;s, en Sling verdelen de dynamisch gecreeerde communautaire gebruikersgroepen, met inbegrip van hun lidmaatschap.

### Gebruiker is gemaakt of bewerkt profiel bij publicatie {#user-is-created-or-edits-profile-on-publish}

Gebruikers en profielen die zijn gemaakt in de publicatieomgeving (bijvoorbeeld via zelfinschrijving, aanmelden via een sociaal netwerk of LDAP-verificatie) worden per ontwerp niet weergegeven in de auteuromgeving.

Wanneer de topologie een [publicatiebedrijf](/help/communities/topologies.md) en de gebruikerssynchronisatie correct is geconfigureerd, *user* en *gebruikersprofiel* wordt gesynchroniseerd over het publicatielandbouwbedrijf gebruikend de distributie van het Schuiven.

### Nieuwe Community Group wordt gemaakt bij Publiceren {#new-community-group-is-created-on-publish}

Hoewel de actie is gestart vanuit een instantie Publiceren, vindt het maken van de communitygroep, wat resulteert in nieuwe sitepagina&#39;s en een nieuwe gebruikersgroep, feitelijk plaats op de instantie Auteur.

Als onderdeel van het proces worden de nieuwe sitepagina&#39;s gerepliceerd naar alle publicatievarianten. De dynamisch gecreeerde communautaire gebruikersgroep en zijn lidmaatschap verkopen die aan alle Publish instanties worden verdeeld.

### Gebruikers of gebruikersgroepen worden gemaakt met Beveiligingsconsole {#users-or-user-groups-are-created-using-security-console}

Gebruikersgegevens die in de publicatieomgeving zijn gemaakt, worden door het ontwerp niet weergegeven in de auteuromgeving en omgekeerd.

Wanneer de [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md) De console wordt gebruikt om nieuwe gebruikers in het publicatiemilieu toe te voegen, synchroniseert de gebruikerssynchronisatie de nieuwe gebruikers en hun groepslidmaatschap aan andere te publiceren instanties, indien nodig. Gebruikerssynchronisatie synchroniseert ook gebruikersgroepen die zijn gemaakt via de beveiligingsconsole.

### Inhoud voor berichten van gebruikers publiceren {#user-posts-content-on-publish}

Voor door de gebruiker gegenereerde inhoud (UGC) worden de gegevens die in een publicatie-instantie zijn ingevoerd, benaderd via het dialoogvenster [geconfigureerde SRP](/help/communities/srp-config.md).

## Aanbevolen procedures {#bestpractices}

Gebruikerssynchronisatie is standaard **uitgeschakeld**. Voor het inschakelen van gebruikerssynchronisatie moet u de wijzigingen aanbrengen *bestaand* OSGi-configuraties. Er mogen geen nieuwe configuraties worden toegevoegd als gevolg van het inschakelen van gebruikerssynchronisatie.

De gebruikerssynchronisatie is afhankelijk van de auteursomgeving voor het beheer van de gegevensdistributies van de gebruiker, ook al worden de gebruikersgegevens niet op auteur gecreeerd.

**Vereisten**

1. Als gebruikers en gebruikersgroepen al op één uitgever zijn gemaakt, wordt het aanbevolen [handmatig synchroniseren](/help/sites-administering/sync.md#manually-syncing-users-and-user-groups) de gebruikersgegevens voor alle uitgevers voordat ze worden geconfigureerd en gebruikerssynchronisatie wordt ingeschakeld.

   Nadat gebruikerssynchronisatie is ingeschakeld, worden alleen nieuwe gebruikers en groepen gesynchroniseerd.

1. Controleer of de laatste code is geïnstalleerd:

   * [AEM platformupdates](https://helpx.adobe.com/experience-manager/kb/aem62-available-hotfixes.html)
   * [AEM Communities-updates](/help/communities/deploy-communities.md#latestfeaturepack)

De volgende configuraties zijn nodig om gebruikerssynchronisatie op AEM Communities in te schakelen. Zorg ervoor dat deze configuraties correct zijn om te voorkomen dat de distributie van de inhoud van de sling mislukt.

### Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

Met deze configuratie haalt u de inhoud op die voor alle uitgevers moet worden gesynchroniseerd. De configuratie bevindt zich op de instantie Auteur. De auteur moet alle uitgevers die er zijn en waar alle informatie kan worden gesynchroniseerd, volgen.

De standaardwaarden in de configuratie zijn voor één publicatie-instantie. Aangezien gebruikerssynchronisatie nuttig is om veelvoudige te synchroniseren publiceer instanties, zoals voor publiceer landbouwbedrijf, moet de extra publiceer instanties aan de configuratie worden toegevoegd.

**Hoe wordt de inhoud gesynchroniseerd?**

De instantie van de auteur pingelt het exportereindpunt van uitgevers. Wanneer een gebruiker op specifieke uitgevers (n) wordt gecreeerd of bijgewerkt, krijgt de Auteur de inhoud van hun exporter eindpunten en [duwt de inhoud](/help/communities/sync.md#main-pars-image-1413756164) aan andere uitgevers (n-1, dat wil zeggen behalve de uitgevers waarvan de inhoud wordt opgehaald).

Configuratie van Apache Sling Sync Agents configureren:

1. Meld u aan met beheerdersrechten voor de AEM auteur.
1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md). Bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Zoeken **Apache Sling Distribution Agent - Sync Agents Factory**.

   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

     Naam verifiëren: **socialpubsync.**

   * Selecteer de **Ingeschakeld** selectievakje.
   * Selecteren **Meerdere wachtrijen gebruiken.**
   * Opgeven **Eindpunten van export** en **Eindpunten importeren** (U kunt meer eindpunten voor de exportfunctie en de importfunctie toevoegen.)

     Deze eindpunten bepalen waar u de inhoud van wilt krijgen en waar u de inhoud wilt duwen. De auteur haalt de inhoud van het gespecificeerde exportereindpunt op en duwt de inhoud aan de uitgevers (buiten de uitgever waarvan het de inhoud haalde).

   ![sync-agent-fact](assets/sync-agent-fact.png)

### Adobe Granite Distribution - Encrypted Password Transport Secret Provider {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Hiermee kan de auteur de geautoriseerde gebruiker identificeren, zodat deze kan zien welke machtiging hij heeft om gebruikersgegevens van de auteur te synchroniseren voor publicatie.

De [geautoriseerde gebruiker gemaakt](/help/sites-administering/sync.md#createauthuser) op alle publicatie-instanties kunnen de uitgevers verbinding maken met de auteur en de distributie van Sling op de auteur configureren. Deze geautoriseerde gebruiker heeft alle vereiste [ACLs](/help/sites-administering/sync.md#howtoaddacl).

Wanneer gegevens op of moeten worden geïnstalleerd van uitgevers, dan verbindt de auteur met uitgevers gebruikend de geloofsbrieven (gebruikersnaam en wachtwoord) die in deze configuratie worden geplaatst.

De auteur verbinden met uitgevers die geautoriseerde gebruiker gebruiken:

1. Meld u aan met beheerdersrechten voor de AEM auteur.
1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Zoeken **Adobe Granite Distribution - Encrypted Password Transport Secret Provider.**
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

   Eigenschappen verifiëren **socialpubsync** - **publishUser.**

1. Stel de gebruikersnaam en het wachtwoord in op de [geautoriseerde gebruiker](/help/sites-administering/sync.md#createauthorizeduser).

   Bijvoorbeeld: **usersync - admin**

![graniet-paswrd-trans](assets/granite-paswrd-trans.png)

### Apache Sling Distribution Agent - Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

Deze configuratie wordt gebruikt om de gegevens te vormen u over uitgevers wilt synchroniseren. Wanneer gegevens worden gemaakt/bijgewerkt in paden die zijn opgegeven in **Toegestane wortelen**, wordt &quot;var/community/distribution/diff&quot; geactiveerd en haalt de gemaakte replicator de gegevens op van een uitgever en installeert deze op andere uitgevers.

De te synchroniseren gegevens (knooppaden) configureren:

1. Meld u aan met beheerdersrechten voor uw publicatieexemplaar.
1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Zoeken **Apache Sling Distribution Agent - Queue Agents Factory**.
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

   Naam verifiëren: **socialpubsync - reverse**

1. Selecteer de **Ingeschakeld** en opslaan.
1. Geef de knooppaden op die moeten worden gerepliceerd **Toegestane wortels**.
1. Herhalen voor elk **publish** -instantie.

   ![queue-agents-fact](assets/queue-agents-fact.png)

### Adobe granietdistributie - Diff Observer Factory {#adobe-granite-distribution-diff-observer-factory}

Met deze configuratie wordt groepslidmaatschap voor alle uitgevers gesynchroniseerd.
Als het wijzigen van het lidmaatschap van een groep in één uitgever zijn lidmaatschap op andere uitgevers niet bijwerkt, dan zorg ervoor dat **ref:leden** wordt toegevoegd aan **look-eigenschappen**.

Synchronisatie van leden garanderen:

1. Meld u aan met beheerdersrechten voor uw publicatieexemplaar.
1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Zoeken **Adobe granietdistributie - Diff Observer Factory**.
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

   Verifiëren **naam van de agent: socialpubsync -reverse**.

1. Selecteer de **Ingeschakeld** selectievakje.
1. Opgeven **rep:leden** als beschrijving voor propertyName in **look-eigenschappen** en Opslaan.

   ![diff-obs](assets/diff-obs.png)

### Apache Sling Distribution Trigger - Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Met deze configuratie kunt u het opiniepeilingsinterval (waarna uitgevers worden gepingeld en wijzigingen door de auteur worden doorgevoerd) configureren om de wijzigingen voor alle uitgevers te synchroniseren.

De auteur opiniepeilt uitgevers om de 30 seconden (standaard). Als er pakketten aanwezig zijn in de map `/var/sling/distribution/packages/  socialpubsync -  vlt /shared`Vervolgens worden deze pakketten opgehaald en op andere uitgevers geïnstalleerd.

Het opiniepeilingsinterval wijzigen:

1. Meld u aan met beheerdersrechten voor de AEM auteur.
1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md), bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. Zoeken **Apache Sling Distribution Trigger - Scheduled Triggers Factory**

   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

     Verifiëren **socialpubsync - scheduled-trigger**

   * Stel het interval in seconden in op het gewenste interval en sla het op.

   ![gepland-trigger](assets/scheduled-trigger.png)

### AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

Voor problemen in verkoopverdeling waarbij er een discrepantie is in abonnementen en volgt, controleert u of de volgende eigenschappen in **AEM Communities User Sync Listener** configuraties worden ingesteld:

* NodeTypes
* IgnorableProperties
* IgnorableNodes
* DistributedFolders

Abonnementen, volgen en meldingen synchroniseren

Op elke AEM-publicatie-instantie:

1. Meld u aan met beheerdersrechten.
1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md). Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Zoeken **AEM Communities User Sync Listener**.
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

   Naam verifiëren: **socialpubsync - scheduled-trigger**

1. Het volgende instellen **NodeTypes**:

   `rep:User`

   `nt:unstructured`

   `nt:resource`

   `rep:ACL`

   `sling:Folder`

   `sling:OrderedFolder`

   De knooppunttypen die in deze eigenschap worden opgegeven, worden gesynchroniseerd en de meldingen (blogs en configuraties gevolgd) worden gesynchroniseerd tussen verschillende uitgevers.

1. Alle mappen toevoegen om in te synchroniseren **DistributedFolders**. Bijvoorbeeld:

   `segments/scoring`

   `social/relationships`

   `activities`

1. Stel de **onwetendheid** tot:

   `.tokens`

   `system`

   `rep:cache` (omdat er kleverige sessies worden gebruikt, hoeft u dit knooppunt niet te synchroniseren met verschillende uitgevers).

   ![user-sync-listener](assets/user-sync-listner.png)

### Unieke verkoper-id {#unique-sling-id}

AEM auteurinstantie gebruikt Verschuivende identiteitskaart om te identificeren van waar de gegevens komen en aan welke uitgevers het (of niet nodig) het pakket moet terugsturen naar.

Zorg ervoor alle uitgevers in een publicatielandbouwbedrijf een unieke Verkoop identiteitskaart hebben Als het Verdelen identiteitskaart het zelfde voor veelvoudige publiceer instanties in publiceer landbouwbedrijf is, dan ontbreekt de gebruikerssynchronisatie. Aangezien de auteur niet weet waar het pakket moet worden opgehaald en waar het pakket moet worden geïnstalleerd.

Om ervoor te zorgen dat uitgevers in het publicatielandbouwbedrijf unieke verkoopidentiteitskaart van uitgevers, op elke Publish instantie:

1. Bladeren naar [https://_host:poort_/system/console/status-slingsettings](https://localhost:4503/system/console/status-slingsettings).
1. Controleer de waarde van **Verkoop-id**.

   ![slingerend](assets/slingid.png)

   Als de verkoop-id van een instantie Publish overeenkomt met de id Sling van een andere instantie Publish, dan:

1. Stop een van de publicatie-instanties met een overeenkomende verkoop-id.
1. In de `crx-quickstart/launchpad/felix` map, zoek en verwijder het bestand met de naam *sling.id.fi.*

   Bijvoorbeeld op een Linux-systeem:

   `rm -i $(find . -type f -name sling.id.file)`

   Op een Windows-systeem:

   Windows Verkenner gebruiken en zoeken naar `sling.id.file`

1. Start de instantie Publiceren. Bij het opstarten wordt er een nieuwe verkoop-id toegewezen.
1. Valideren dat de **Verkoop-id** is nu uniek.

Herhaal deze stappen totdat alle instanties Publiceren een unieke id voor verkopers hebben.

### Vault Package Builder-fabriek {#vault-package-builder-factory}

Voor updates die correct worden gesynchroniseerd, is het nodig om de builder van het vault-pakket te wijzigen voor gebruikerssynchronisatie.
In `/home/users`, `*/rep:cache` node wordt gemaakt. Het is een geheime voorgeheugen dat wordt gebruikt om te vinden dat als wij op de belangrijkste naam van een knoop dan vragen dit geheime voorgeheugen direct kan worden gebruikt.

Gebruikerssynchronisatie kan worden beëindigd als `rep :cache` knooppunten worden gesynchroniseerd tussen uitgevers.

Om ervoor te zorgen dat updates correct over uitgevers, op elke AEM Publish instantie worden gesynchroniseerd:

1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md)

   Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Zoek de **Apache Sling Distribution Packaging - Vault Package Builder-fabriek**

   Builder-naam: social pubsync-vlt.

1. Selecteer het pictogram Bewerken.
1. Twee filters voor pakketknooppunten toevoegen:
   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`
1. Beleidsafhandeling
   * Om bestaande rep:beleidsknopen met nieuwe te overschrijven, voeg een derde Filter van het Pakket toe: `/home/users|+.*/rep:policy`
   * Als u wilt voorkomen dat beleid wordt verspreid, stelt u: `Acl Handling: IGNORE`

   ![Fabrikant van Vault-pakket](assets/vault-package-builder-factory.png)

## Probleemoplossing voor verkoopverdeling in AEM Communities {#troubleshoot-sling-distribution-in-aem-communities}

Als de distributie van het Verdelen ontbreekt, probeer de volgende het zuiveren stappen:

1. **Controleren op [onjuist toegevoegde configuraties](/help/sites-administering/sync.md#improperconfig)**

   Zorg ervoor dat er geen meerdere configuraties worden toegevoegd of bewerkt, maar dat de bestaande standaardconfiguraties worden bewerkt.
1. **Configuraties controleren**

   Zorg ervoor dat alle [configuraties](/help/communities/sync.md#bestpractices) worden op de juiste wijze ingesteld in uw AEM instantie Auteur, zoals wordt vermeld in het dialoogvenster [Aanbevolen procedures](/help/communities/sync.md#main-pars-header-863110628).

1. **Machtigingsgebruikersmachtigingen controleren**

   Als de pakketten niet correct zijn geïnstalleerd, controleert u of de [geautoriseerde gebruiker](/help/sites-administering/sync.md#createauthuser) gecreeerd in eerste publiceer instantie heeft correcte ACLs.

   Om dit te bevestigen, in plaats van [geautoriseerde gebruiker maken](/help/sites-administering/sync.md#createauthuser) de [Adobe Granite Distribution - Encrypted Password Transport Secret Provider](/help/sites-administering/sync.md#adobegraniteencpasswrd) configuratie op de instantie Auteur om de referenties van de Admin-gebruiker te gebruiken. Installeer de pakketten nu opnieuw. Als de gebruikerssynchronisatie prima met beheerdergeloofsbrieven werkt, dan betekent het dat gecreeerd publiceerde gebruiker geen aangewezen ACLs had.

1. **Configuratie van de fabriek van Diff Observer controleren**

   Als slechts specifieke knopen niet over publiceer landbouwbedrijf - worden gesynchroniseerd, bijvoorbeeld, zijn de groepsleden niet gesynchroniseerd - dan zorg ervoor dat [Adobe granietdistributie - Diff Observer Factory](/help/sites-administering/sync.md#diffobserver) configuratie is ingeschakeld en **vertegenwoordiger: leden** worden ingesteld in **look-eigenschappen**.

1. **Controleer de configuratie van AEM Communities User Sync Listener.** Als de gemaakte gebruikers zijn gesynchroniseerd maar de volgende abonnementen en abonnementen niet werken, moet u ervoor zorgen dat de configuratie van AEM Communities User Sync Listener:

   * Knooppunttypen - ingesteld op **rep:gebruiker, niet:ongestructureerd**, **nt:resource**, **rep:ACL**, **sling:map**, en **sling:OrderedFolder**.
   * Genegeerde knooppunten - ingesteld op **.tokens**, **systeem**, en **rep:cache**.
   * Gedistribueerde mappen - ingesteld op de mappen die u wilt distribueren.

1. **Logboeken controleren die zijn gegenereerd bij het maken van een gebruiker in de instantie Publiceren**

   Als de bovenstaande configuraties juist zijn ingesteld maar gebruikerssynchronisatie nog niet werkt, controleert u de logbestanden die bij het maken van de gebruiker worden gegenereerd.

   Controleer als volgt of de volgorde van de logbestanden gelijk is:

   ```shell
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7422] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ2: ADD paths=[/home/users/C, /home/users/C/Cw-5avWqilmqsNn5hCvK], user=communities-user-admin
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy]
   15.05.2016 18:33:01.523 *INFO* [sling-oak-observation-7431] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ3: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK, /home/users/C/Cw-5avWqilmqsNn5hCvK/profile, /home/users/C/Cw-5avWqilmqsNn5hCvK/rep:policy], user=communities-user-admin
   15.05.2016 18:33:01.757 *INFO* [sling-oak-observation-7431] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_ebb27ad9-a861-4405-9342-d64c916654e2:0.0.1
   15.05.2016 18:33:01.820 *INFO* [sling-oak-observation-7422] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337181554_58811273-5861-48fe-95d2-4aff367b99c3:0.0.1
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] com.adobe.cq.social.sync.impl.PublisherSyncServiceImpl Handing these paths to the distribution subsystem: [/home/users/C/Cw-5avWqilmqsNn5hCvK/profile]
   15.05.2016 18:33:02.023 *INFO* [sling-oak-observation-7430] org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync-reverse] REQUEST-START DSTRQ4: ADD paths=[/home/users/C/Cw-5avWqilmqsNn5hCvK/profile], user=communities-user-admin
   15.05.2016 18:33:02.273 *INFO* [sling-oak-observation-7430] org.apache.jackrabbit.vault.packaging.impl.JcrPackageDefinitionImpl unwrapping package sling/distribution:socialpubsync-vlt_1463337182039_f34f4fa6-10b9-42eb-8740-4da9d4d38f99:0.0.1
   ```

Foutopsporing:

1. De gebruikerssynchronisatie uitschakelen:
1. Meld u aan bij AEM instantie van de auteur met beheerdersrechten.

   1. Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md). Bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. De configuratie zoeken **Apache Sling Distribution Agent - Sync Agents Factory**.
   1. Hef de selectie van **Ingeschakeld** selectievakje.

      Wanneer de gebruikerssynchronisatie wordt uitgeschakeld op eindpunten van de Auteur (exportfunctie en importer), wordt de instantie Auteur statisch. De **vlt** pakketten worden niet gepingeld of opgehaald door de auteur.

      Wanneer een gebruiker bij een publicatie-instantie is gemaakt, wordt de opdracht **vlt** pakket is gemaakt in */var/sling/distribution/packages/socialpubsync - vlt/data* knooppunt. En als deze pakketten door de auteur aan een andere dienst worden geduwd. U kunt deze gegevens downloaden en uitpakken om te controleren wat alle eigenschappen aan andere diensten worden geduwd.

1. Ga naar een uitgever en maak een gebruiker op de uitgever. Hierdoor worden gebeurtenissen gemaakt.
1. Controleer de [volgorde van logbestanden](/help/communities/sync.md#troubleshoot-sling-distribution-in-aem-communities) gemaakt bij het maken van gebruikers.
1. Controleren of een **vlt** pakket is gemaakt op **/var/sling/distribution/packages/socialpubsync-vlt/data**.
1. Schakel nu de gebruikerssynchronisatie in AEM instantie Auteur in.
1. Wijzig bij de uitgever de eindpunten voor de exportfunctie of de importer in **Apache Sling Distribution Agent - Sync Agents Factory**.
We kunnen pakketgegevens downloaden en uitpakken om te controleren welke eigenschappen aan andere uitgevers worden doorgegeven en welke gegevens verloren gaan.
