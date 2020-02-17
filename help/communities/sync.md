---
title: Gebruikerssynchronisatie van gemeenschappen
seo-title: Gebruikerssynchronisatie van gemeenschappen
description: De werking van gebruikerssynchronisatie
seo-description: De werking van gebruikerssynchronisatie
uuid: 772b82bd-a66c-4c1d-b80b-dcff77c873a3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 97286c2c-f6e3-43ec-b1a9-2abb58616778
docset: aem65
translation-type: tm+mt
source-git-commit: 44eb94b917fe88b7c90c29ec7da553e15be391db

---


# Gebruikerssynchronisatie van gemeenschappen{#communities-user-synchronization}

## Inleiding {#introduction}

In AEM-gemeenschappen kunnen *sitebezoekers* vanuit de publicatieomgeving (afhankelijk van geconfigureerde machtigingen) *leden* worden, *gebruikersgroepen* maken en hun *lidprofiel* bewerken.

*Gebruikersgegevens* zijn een term die wordt gebruikt om te verwijzen naar *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen*.

*Leden* zijn een term die wordt gebruikt om te verwijzen naar *gebruikers* die zijn geregistreerd in de publicatieomgeving, in tegenstelling tot gebruikers die zijn geregistreerd in de auteursomgeving.

Ga voor meer informatie over gebruikersgegevens naar Gebruikers [beheren en Gebruikersgroepen](/help/communities/users.md).

## Gebruikers in een publicatiebedrijf synchroniseren {#synchronizing-users-across-a-publish-farm}

Gebruikersgegevens die in de publicatieomgeving zijn gemaakt, worden door het ontwerp niet weergegeven in de ontwerpomgeving.

De meeste gebruikersgegevens die in de auteursomgeving worden gemaakt, blijven in de auteursomgeving en worden niet gesynchroniseerd of gerepliceerd om instanties te publiceren.

Wanneer de [topologie](/help/communities/topologies.md) een [publiceerlandbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm)is, moeten de registratie en de wijzigingen die op één publicatiegeval worden aangebracht met andere worden gesynchroniseerd publiceren instanties. Leden moeten zich kunnen aanmelden en hun gegevens op elk publicatieknooppunt kunnen bekijken.

Wanneer gebruikerssynchronisatie wordt toegelaten, worden de gebruikersgegevens automatisch gesynchroniseerd over publiceer instanties in het landbouwbedrijf.

### Instructies voor het synchroniseren van gebruikers {#user-sync-setup-instructions}

Voor gedetailleerde, geleidelijke instructies, op hoe te om synchronisatie over toe te laten publiceert landbouwbedrijf, zie

* [Gebruikerssynchronisatie](/help/sites-administering/sync.md)

## Gebruikerssynchronisatie op de achtergrond {#user-sync-in-the-background}

![sling-dist-workflow](assets/sling-dist-workflow.png)

* **vlt-pakket**: is een zip-bestand met alle wijzigingen die op een uitgever zijn aangebracht en die over alle uitgevers moeten worden verspreid. Wijzigingen op een uitgever genereren gebeurtenissen die door de gebeurtenislistener voor wijzigingen worden gekozen. Hiermee maakt u een vlt-pakket dat alle wijzigingen bevat.

* **distributiepakket**: Bevat distributiegegevens voor Sling. Dat is informatie over waar de inhoud moet worden verspreid en wanneer deze als laatste werd verspreid.

## Wat gebeurt er als ... {#what-happens-when}

### Site publiceren vanuit console Communitysites {#publish-site-from-communities-sites-console}

Op auteur, wanneer een communautaire plaats van de console [van de Plaatsen van](/help/communities/sites-console.md)Gemeenschappen wordt gepubliceerd, is het effect om de bijbehorende pagina&#39;s te [herhalen](/help/sites-deploying/configuring.md#replication-reverse-replication-and-replication-agents) , en het Schelen verspreidt dynamisch de gecreeerde communautaire gebruikersgroepen, met inbegrip van hun lidmaatschap.

### Gebruiker is gemaakt of bewerkt profiel bij publicatie {#user-is-created-or-edits-profile-on-publish}

Gebruikers en profielen die zijn gemaakt in de publicatieomgeving (bijvoorbeeld via zelfinschrijving, aanmelden via een sociaal netwerk of LDAP-verificatie) worden per ontwerp niet weergegeven in de auteursomgeving.

Wanneer de topologie een [publiceerlandbouwbedrijf](/help/communities/topologies.md) is en gebruikerssynchronisatie correct is gevormd, wordt de *gebruiker* en het *gebruikersprofiel* gesynchroniseerd over het publiceerlandbouwbedrijf gebruikend het Verdelen distributie.

### Nieuwe Community Group wordt gemaakt bij Publiceren {#new-community-group-is-created-on-publish}

Hoewel de aanmaak van een communitygroep vanuit een publicatie-instantie wordt gestart, met als resultaat nieuwe sitepagina&#39;s en een nieuwe gebruikersgroep, gebeurt dit in feite op de auteur-instantie.

Als onderdeel van het proces worden de nieuwe sitepagina&#39;s gekopieerd naar alle publicatie-instanties. De dynamisch gecreeerde communautaire gebruikersgroep en zijn lidmaatschap verkopen die aan alle publicatieinstanties worden verdeeld.

### Gebruikers of gebruikersgroepen worden gemaakt met Beveiligingsconsole {#users-or-user-groups-are-created-using-security-console}

Gebruikersgegevens die in de publicatieomgeving zijn gemaakt, worden door het ontwerp niet weergegeven in de auteursomgeving en andersom.

Wanneer de [gebruikersbeheer- en beveiligingsconsole](/help/sites-administering/security.md) wordt gebruikt om nieuwe gebruikers toe te voegen in de publicatieomgeving, worden de nieuwe gebruikers en hun groepslidmaatschap indien nodig gesynchroniseerd met andere publicatieinstanties. Gebruikerssynchronisatie synchroniseert ook gebruikersgroepen die zijn gemaakt via de beveiligingsconsole.

### Inhoud voor berichten van gebruikers publiceren {#user-posts-content-on-publish}

Voor gebruiker geproduceerde inhoud (UGC), worden de gegevens ingegaan op publiceer instantie betreden door [gevormde SRP](/help/communities/srp-config.md).

## Aanbevolen procedures {#bestpractices}

Gebruikerssynchronisatie is standaard **uitgeschakeld**. Het toelaten van gebruikerssynchronisatie impliceert het wijzigen van *bestaande* configuraties OSGi. Er mogen geen nieuwe configuraties worden toegevoegd als gevolg van het inschakelen van gebruikerssynchronisatie.

De gebruikerssynchronisatie is afhankelijk van de auteursomgeving voor het beheer van de gegevensdistributies van de gebruiker, ook al worden de gebruikersgegevens niet op auteur gecreeerd.

**Vereisten**

1. Als gebruikers en gebruikersgroepen al op één uitgever zijn gemaakt, wordt aangeraden de gebruikersgegevens [handmatig te synchroniseren](/help/sites-administering/sync.md#manually-syncing-users-and-user-groups) met alle uitgevers voordat u de gebruikerssynchronisatie configureert en inschakelt.
Zodra gebruikerssynchronisatie is ingeschakeld, worden alleen nieuwe gebruikers en groepen gesynchroniseerd.

1. Controleer of de laatste code is geïnstalleerd:

   * [AEM-platformupdates](https://helpx.adobe.com/experience-manager/kb/aem62-available-hotfixes.html)
   * [Updates van AEM-gemeenschappen](/help/communities/deploy-communities.md#latestfeaturepack)

De volgende configuraties zijn noodzakelijk om gebruikerssynchronisatie op Gemeenschappen toe te laten AEM. Zorg ervoor dat deze configuraties correct zijn om te voorkomen dat de distributie van de inhoud van de sling mislukt.

###  Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

Met deze configuratie haalt u de inhoud op die voor alle uitgevers moet worden gesynchroniseerd. De configuratie bevindt zich op de instantie Auteur. De auteur moet alle uitgevers die er zijn en waar alle informatie kan worden gesynchroniseerd, volgen.

De standaardwaarden in de configuratie zijn voor één publicatie-instantie. Aangezien gebruikerssynchronisatie nuttig is om veelvoudige te synchroniseren publiceer instanties, zoals voor publiceer landbouwbedrijf, moet de extra publiceer instanties aan de configuratie worden toegevoegd.

**Hoe wordt de inhoud gesynchroniseerd?**

De instantie van de auteur pingelt het exportereindpunt van uitgevers. Telkens wanneer een gebruiker op specifieke uitgevers (n) wordt gecreeerd of bijgewerkt, krijgt de Auteur de inhoud van hun uitvoereindpunten en [duwt de inhoud](/help/communities/sync.md#main-pars-image-1413756164) aan andere uitgevers (n-1, die behalve de uitgevers is waarvan de inhoud wordt gehaald).

Configuratie van Apache Sling Sync Agents configureren

Instantie van AEM-auteur:

1. Meld u aan met beheerdersrechten.
1. Open de [webconsole](https://helpx.adobe.com/experience-manager/6-4/help/sites-deploying/configuring-osgi.html). Bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Zoek **Apache Sling Distribution Agent - Sync Agents Factory.**

   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).
   Naam verifiëren: **sociale pubsync.**

   * Schakel het selectievakje **Ingeschakeld** in.
   * Selecteer Meerdere wachtrijen **gebruiken.**
   * Geef **Eindpunten** voor Exporter en Eindpunten **voor** Importer op (u kunt meer eindpunten voor Exporter en Importer toevoegen).

      Deze eindpunten bepalen waar u de inhoud van wilt krijgen en waar u de inhoud wilt duwen. De auteur haalt de inhoud van het gespecificeerde exportereindpunt op en duwt de inhoud aan de uitgevers (buiten de uitgever waarvan het de inhoud haalde).


![sync-agent-fact](assets/sync-agent-fact.png)

### Adobe Granite Distribution - Encrypted Password Transport Secret Provider {#adobe-granite-distribution-encrypted-password-transport-secret-provider}

Hiermee kan de auteur de geautoriseerde gebruiker identificeren, zodat deze kan zien welke machtiging hij heeft om gebruikersgegevens van de auteur te synchroniseren voor publicatie.

De [geautoriseerde gebruiker die op alle publicatie-instanties is gemaakt](/help/sites-administering/sync.md#createauthuser) , helpt de uitgevers om verbinding te maken met de auteur en distributie van de stijlpagina op de auteur te configureren. Deze erkende gebruiker heeft al vereiste [ACLs](/help/sites-administering/sync.md#howtoaddacl).

Wanneer gegevens op of moeten worden geïnstalleerd van uitgevers, dan verbindt de auteur met uitgevers gebruikend de geloofsbrieven (gebruikersnaam en wachtwoord) die in deze configuratie worden geplaatst.

Om auteur met uitgevers te verbinden die geautoriseerde gebruiker gebruiken

Instantie van AEM-auteur:

1. Meld u aan met beheerdersrechten.
1. Open de [webconsole](/help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Zoek **Adobe Granite Distribution - Encrypted Password Transport Secret Provider.**
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

   Verifieer bezit **socialpubsync** - **publishUser.**

1. Stel de gebruikersnaam en het wachtwoord in op de [geautoriseerde gebruiker](/help/sites-administering/sync.md#createauthorizeduser).

   Bijvoorbeeld **gebruikerssync - admin**

![graniet-paswrd-trans](assets/granite-paswrd-trans.png)

###  Apache Sling Distribution Agent - Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

Deze configuratie wordt gebruikt om de gegevens te vormen u over uitgevers wilt synchroniseren. Wanneer gegevens worden gemaakt/bijgewerkt in paden die zijn opgegeven in **Toegestane hoofdmappen**, wordt &quot;var/community/distribution/diff&quot; geactiveerd en haalt de gemaakte replicator de gegevens op van een uitgever en installeert deze op andere uitgevers.

De te synchroniseren gegevens (knooppaden) configureren

Op AEM-publicatieexemplaar:

1. Meld u aan met beheerdersrechten.
1. Open de [webconsole](https://helpx.adobe.com/experience-manager/6-4/help/sites-deploying/configuring-osgi.html).

   Bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Zoek **Apache Sling Distribution Agent - Queue Agents Factory.**
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

   Naam verifiëren: **sociale pubsync - reverse.**

1. Schakel het selectievakje **Ingeschakeld** in en sla het op.
1. Geef de knooppaden op die moeten worden gerepliceerd in **Toegestane wortels**.
1. Herhaal deze bewerking voor elk **publicatieexemplaar** .

![queue-agents-fact](assets/queue-agents-fact.png)

### Adobe Granite Distribution - Diff Observer Factory {#adobe-granite-distribution-diff-observer-factory}

Met deze configuratie wordt groepslidmaatschap voor alle uitgevers gesynchroniseerd.
Als het wijzigen van het lidmaatschap van een groep in één uitgever zijn lidmaatschap op andere uitgevers niet bijwerkt, dan zorg ervoor dat **ref:members** aan **getoonde eigenschappen** wordt toegevoegd.

Om lidsynchronisatie te verzekeren

Op elke publicatie-instantie van AEM:

1. Meld u aan met beheerdersrechten.
1. Open de [webconsole](https://helpx.adobe.com/experience-manager/6-4/help/sites-deploying/configuring-osgi.html).

   Bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

1. Zoek **Adobe Granite Distribution - Diff Observer Factory.**
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram).

   Naam van **agent controleren: socialpubsync - reverse**.

1. Schakel het selectievakje **Ingeschakeld** in.
1. Specificeer **rep:members** als beschrijving voor propertyName in **getoonde eigenschappen namen**, en sparen.

![diff-obs](assets/diff-obs.png)

###  Apache Sling Distribution Trigger - Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

Met deze configuratie kunt u het opiniepeilingsinterval (waarna uitgevers worden gepingeld en wijzigingen door de auteur worden aangeroepen) configureren om de wijzigingen in de verschillende uitgevers te synchroniseren.

De auteur opiniepeilt uitgevers om de 30 seconden (standaard). Als er pakketten aanwezig zijn in de map */var/sling/distribution/packages/social pubsync - vlt /shared*, worden deze pakketten opgehaald en op andere uitgevers geïnstalleerd.

Het opiniepeilingsinterval wijzigen

Instantie van AEM-auteur:

1. Meld u aan met beheerdersrechten.
1. Open de [webconsole](/help/sites-deploying/configuring-osgi.md), bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
1. Zoek naar **Apache Sling Distribution Trigger - Scheduled Triggers Factory**

   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

      Verifieer **socialpubsync -scheduled-trigger**

   * Stel het interval in seconden in op het gewenste interval en sla het op.

![gepland-trigger](assets/scheduled-trigger.png)

###  AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

Voor kwesties in het Verkopen distributie waar er een discrepantie in abonnementen en volgt is, controleer of de volgende eigenschappen in de configuraties van de Lijst van de Synchronisatie van de Gebruiker van de **Gemeenschappen van de Gemeenschappen AEM worden geplaatst** :

* NodeTypes
* IgnorableProperties
* IgnorableNodes
* DistributedFolders

Abonnementen, volgen en meldingen synchroniseren

Op elke publicatie-instantie van AEM:

1. Meld u aan met beheerdersrechten.
1. Open de [webconsole](/help/sites-deploying/configuring-osgi.md). Bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Zoek naar **AEM Communities User Sync Listener.**
1. Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

   Naam verifiëren: **socialpubsync - scheduled-trigger**

1. Stel de volgende **NodeTypes** in:

   rep:gebruiker

   nt:ongestructureerd

   nt:resource

   rep:ACL

   sling:map

   sling:OrderedFolder

   De knooppunttypen die in deze eigenschap worden opgegeven, worden gesynchroniseerd en de meldingen (blogs en configuraties die worden gevolgd) worden gesynchroniseerd tussen verschillende uitgevers.

1. Voeg alle omslagen toe om in **DistributedFolders** te synchroniseren. Bijvoorbeeld,

   segmenten/scoring

   sociale/relaties

   activiteiten

1. Stel de **onwetende** waarden in op:

   .tokens

   systeem

   rep:cache (omdat we plaksessies gebruiken, hoeven we dit knooppunt niet te synchroniseren met verschillende uitgevers)

![user-sync-listener](assets/user-sync-listner.png)

###  Unieke verkoper-id {#unique-sling-id}

De auteur-instantie van AEM gebruikt Verschuivende ID om te bepalen van waar de gegevens komen en naar welke uitgevers het pakket moet (of niet moet) terugsturen naar.

Zorg ervoor alle uitgevers in een publicatielandbouwbedrijf een unieke Verkoop identiteitskaart hebben Als het Verdelen identiteitskaart het zelfde voor veelvoudige publiceer instanties in publiceer landbouwbedrijf is, dan zal de gebruikerssynchronisatie ontbreken. Aangezien de auteur niet zal weten waar te om het pakket van en te halen waar te om het pakket te installeren.

Om unieke verkoopsidentiteitskaart van uitgevers in publicatielandbouwbedrijf te verzekeren

Op elke publicatie-instantie:

1. Blader naar [https://_host:poort_/systeem/console/status-slingsettings](https://localhost:4503/system/console/status-slingsettings).
1. Controleer de waarde van de **verkoopID.**

![slingerend](assets/slingid.png)

Als de Verschuivende-id van een publicatie-instantie overeenkomt met de Verschuivende-id van een andere publicatie-instantie, geldt het volgende:

1. Stop een van de publicatie-instanties met een overeenkomende slingerID.
1. Zoek in de `crx-quickstart/launchpad/felix` map naar het bestand *sling.id.file en verwijder dit.*

   bijvoorbeeld op een Linux-systeem:

   `rm -i $(find . -type f -name sling.id.file)`

   bijvoorbeeld op een Windows-systeem:

   Windows Verkenner gebruiken en zoeken naar `sling.id.file`

1. Start de publicatie-instantie. Bij het opstarten wordt er een nieuwe verkoop-id toegewezen.
1. Controleer of de **verkoop-id** nu uniek is.

Herhaal deze stappen totdat alle publicatie-instanties een unieke id voor verkopers hebben.

### Vault Package Builder-fabriek {#vault-package-builder-factory}

Voor updates die correct worden gesynchroniseerd, is het nodig om de builder van het vault-pakket te wijzigen voor gebruikerssynchronisatie.
In **/home/users** wordt een knooppunt ***/rep:cache **gemaakt. Het is een geheime voorgeheugen dat wordt gebruikt om te vinden dat als wij op de belangrijkste naam van een knoop dan vragen dit geheime voorgeheugen direct kan worden gebruikt.

De synchronisatie van gebruikers kan worden beëindigd als de `rep :cache `knopen over uitgevers worden gesynchroniseerd.

Om ervoor te zorgen dat updates correct over uitgevers worden gesynchroniseerd

Op elke publicatie-instantie van AEM:

1. Toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).
1. Zoek de **Apache Sling Distribution Packaging - Vault Package Builder Factory**

   Builder-naam: socialpubsync-vlt.

1. Selecteer het bewerkingspictogram.
1. Twee filters voor pakketknooppunten toevoegen:
   * /home/users|-*/.tokens
   * /home/users|**-**.*/rep:cache

1. Beleidsafhandeling

   * om bestaande rep:beleidsknopen met nieuwe te overschrijven, voeg een derde Filter van het Pakket toe:

      /home/users|**+**.*/rep:beleid

   * om te voorkomen dat het beleid wordt verspreid,

      Acl-verwerking: IGNORE

![Fabrikant van Vault-pakket](assets/vault-package-builder-factory.png)

## Distributie van Sling-software in AEM-gemeenschappen oplossen {#troubleshoot-sling-distribution-in-aem-communities}

Als de distributie van het Verdelen ontbreekt, probeer de volgende het zuiveren stappen:

1. **Controleren op[onjuist toegevoegde configuraties](/help/sites-administering/sync.md#improperconfig).** Zorg ervoor dat er geen meerdere configuraties worden toegevoegd of bewerkt, maar dat de bestaande standaardconfiguraties worden bewerkt.
1. **Configuraties** controleren. Zorg ervoor dat alle [](/help/communities/sync.md#bestpractices)configuraties op de juiste wijze zijn ingesteld in uw AEM Author-instantie, zoals vermeld in de [Best Practices](/help/communities/sync.md#main-pars-header-863110628).
1. **Controleer geautoriseerde gebruikersmachtigingen**. Als de pakketten niet behoorlijk geïnstalleerd zijn, dan controleer dat de [erkende gebruiker](/help/sites-administering/sync.md#createauthuser) die in eerste wordt gecreeerd publiceer instantie correcte ACLs heeft.

   Om dit te bevestigen, in plaats van de [gecreeerde geautoriseerde gebruiker](/help/sites-administering/sync.md#createauthuser) verander de de Distributie van [Adobe Granite - de Encrypted configuratie van de Leverancier](/help/sites-administering/sync.md#adobegraniteencpasswrd) van het Vervoer van het Geheime Wachtwoord op de instantie van de Auteur om Admin gebruikersgeloofsbrieven te gebruiken. Installeer de pakketten nu opnieuw. Als de gebruikerssynchronisatie prima met beheerdergeloofsbrieven werkt, dan betekent het dat gecreeerd publiceerde gebruiker geen aangewezen ACLs had.

1. **Controleer de configuratie** van de Fabriek van de Waarnemer van Diff. Als slechts specifieke knopen niet over publiceer landbouwbedrijf worden gesynchroniseerd - bijvoorbeeld, zijn de groepsleden niet gesynchroniseerd - dan zorg ervoor dat de [Distributie van Adobe Granite - de configuratie van de Fabriek](/help/sites-administering/sync.md#diffobserver) van de Waarnemer van Diff wordt toegelaten en **rep: leden** worden ingesteld in namen van **weergegeven eigenschappen**.
1. **Controleer de configuratie van AEM Communities User Sync Listener.** Als de gemaakte gebruikers zijn gesynchroniseerd maar de volgende abonnementen en abonnementen niet werken, moet u ervoor zorgen dat de configuratie van de listener voor gebruikerssynchronisatie van de AEM-gemeenschappen het volgende bevat:

   * Knooppunttypen - ingesteld op **rep:User, nt :untured**, **nt :resource**, **rep:ACL**, **sling:Folder**, en **sling:OrderedFolder**
   * Genegeerde knooppunten - ingesteld op **.tokens**, **system** en **rep:cache**
   * Gedistribueerde mappen - instellen op de mappen die u wilt distribueren

1. **Logboeken controleren die zijn gegenereerd bij het maken van gebruikers op de instantie** Publiceren. Als de bovenstaande configuraties juist zijn ingesteld maar gebruikerssynchronisatie nog niet werkt, controleert u de logbestanden die bij het maken van de gebruiker worden gegenereerd.

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
   1. Meld u aan bij de AEM-auteur-instantie met beheerdersrechten.

      1. Open de [webconsole](/help/sites-deploying/configuring-osgi.md). Bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
      1. Zoek de configuratie **Apache Sling Distribution Agent - Sync Agents Factory**.
      1. Schakel het selectievakje **Ingeschakeld** uit.
Wanneer de gebruikerssynchronisatie wordt uitgeschakeld bij de instantie van de auteur, worden de eindpunten (exportfunctie en importer) uitgeschakeld en is de instantie van de auteur statisch. De **vlt** -pakketten worden niet gepingeld of opgehaald door de auteur.
Als een gebruiker nu bij de publicatie-instantie wordt gemaakt, wordt het **vlt** -pakket gemaakt in */var/sling/distribution/packages/socialpubsync - vlt/data* -knooppunt. En als deze pakketten door de auteur aan een andere dienst worden geduwd. U kunt deze gegevens downloaden en uitpakken om te controleren wat alle eigenschappen aan andere diensten worden geduwd.
   1. Ga naar een uitgever en maak een gebruiker op de uitgever. Hierdoor worden gebeurtenissen gemaakt.
   1. Controleer de [volgorde van logboeken](/help/communities/sync.md#troubleshoot-sling-distribution-in-aem-communities)die bij het maken van de gebruiker worden gemaakt.
   1. Controleer of er een **vlt **package is gemaakt op **/var/sling/distribution/packages/socialpubsync-vlt/data**.
   1. Schakel nu de gebruikerssynchronisatie in de AEM-auteurinstantie in.
   1. Wijzig op de uitgever de eindpunten voor de exporteur of de importeur in **Apache Sling Distribution Agent - Sync Agents Factory**.
We kunnen pakketgegevens downloaden en uitpakken om te controleren welke eigenschappen aan andere uitgevers worden doorgegeven en welke gegevens verloren gaan.
