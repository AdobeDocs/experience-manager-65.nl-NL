---
title: Gebruikerssynchronisatie
seo-title: Gebruikerssynchronisatie
description: Meer informatie over gebruikerssynchronisatie in AEM.
seo-description: Meer informatie over gebruikerssynchronisatie in AEM.
uuid: 0a519daf-21b7-4adc-b419-eeb8c404c54f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: c061b358-8c0d-40d3-8090-dc9800309ab3
docset: aem65
translation-type: tm+mt
source-git-commit: 8ed7409740cdd3e45fad006dc6e470a06acc60fe
workflow-type: tm+mt
source-wordcount: '2436'
ht-degree: 2%

---


# Gebruikerssynchronisatie{#user-synchronization}

## Inleiding {#introduction}

Wanneer de plaatsing [publiceer landbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm) is, moeten de leden login kunnen en hun gegevens over om het even welk publicatieknooppunt zien.

Gebruikers en gebruikersgroepen (gebruikersgegevens) die in de publicatieomgeving zijn gemaakt, zijn niet nodig in de ontwerpomgeving.

De meeste gebruikersgegevens die in de auteursomgeving zijn gemaakt, blijven in de auteursomgeving en worden niet gekopieerd naar publicatieinstanties.

Registratie en wijzigingen die zijn aangebracht op één publicatie-instantie moeten worden gesynchroniseerd met andere publicatie-instanties, zodat deze toegang hebben tot dezelfde gebruikersgegevens.

Vanaf AEM 6.1, wanneer gebruikerssynchronisatie wordt toegelaten, worden de gebruikersgegevens automatisch gesynchroniseerd over de publiceer instanties in het landbouwbedrijf en niet gecreeerd op auteur.

## Verspreiding {#sling-distribution}

De gebruikersgegevens, samen met hun [ACLs](/help/sites-administering/security.md), worden opgeslagen in [Eak Kern](/help/sites-deploying/platform.md), de laag onder Oak JCR, en worden betreden gebruikend [Eak API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/oak/api/package-tree.html). Met niet vaak uitgevoerde updates is het redelijk dat gebruikersgegevens worden gesynchroniseerd met andere publicatie-instanties met [Content Distribution](https://github.com/apache/sling/blob/trunk/contrib/extensions/distribution/README.md) (Sling distribution).

De voordelen van gebruikerssynchronisatie met de verkoopverdeling in vergelijking met traditionele replicatie zijn:

* *gebruikers*,  *gebruikersprofielen* en  *gebruikers* die tijdens het publiceren zijn gegroepeerd, worden niet gemaakt op auteur

* Bij het splitsen van distributiesets worden eigenschappen in jcr-gebeurtenissen ingesteld, zodat u kunt werken binnen gebeurtenislisteners aan de serverzijde zonder dat u zich zorgen hoeft te maken over oneindige replicatielijnen
* De het verdelen van de distributie verzendt slechts gebruikersgegevens naar niet voortkomende publicatieinstanties, die onnodig verkeer elimineren
* [De ](/help/sites-administering/security.md) ACLsset in de gebruikersknoop is inbegrepen in de synchronisatie

>[!NOTE]
>
>Als de zittingen worden vereist, wordt het geadviseerd om of een oplossing te gebruiken SSO of kleverige zitting te gebruiken en klanten te hebben login als zij aan een andere uitgever worden geschakeld.

>[!CAUTION]
>
>Synchronisatie van de groep ***beheerders*** wordt niet ondersteund, zelfs niet wanneer gebruikerssynchronisatie is ingeschakeld. In plaats daarvan wordt een fout bij &#39;het importeren van de diff&#39; in het foutenlogboek geregistreerd.
>
>Daarom wanneer de plaatsing een publicatielandbouwbedrijf is, als een gebruiker aan of verwijderd uit de ***beheerders** groep wordt toegevoegd, moet de wijziging manueel op elke publicatieinstantie worden gemaakt.

## Gebruikerssynchronisatie inschakelen {#enable-user-sync}

>[!NOTE]
>
>Gebruikerssynchronisatie is standaard `disabled`.
>
>Als u gebruikerssynchronisatie inschakelt, moet u *bestaande* OSGi-configuraties wijzigen.
>
>Er mogen geen nieuwe configuraties worden toegevoegd als gevolg van het inschakelen van gebruikerssynchronisatie.

De gebruikerssynchronisatie is afhankelijk van de auteursomgeving voor het beheer van de gegevensdistributies van de gebruiker, ook al worden de gebruikersgegevens niet op auteur gecreeerd. Veel, maar niet alle, van de configuratie vindt plaats in de auteursomgeving en elke stap identificeert duidelijk of het op auteur of publicatie moet worden uitgevoerd.

Hieronder vindt u de stappen die nodig zijn om gebruikerssynchronisatie in te schakelen, gevolgd door een sectie [Problemen oplossen](#troubleshooting):

### Vereisten {#prerequisites}

1. Als gebruikers en gebruikersgroepen al op één uitgever zijn gecreeerd, wordt het geadviseerd om [de gebruikersgegevens aan alle uitgevers manueel te synchroniseren alvorens gebruikerssynchronisatie te vormen en toe te laten.](#manually-syncing-users-and-user-groups)

Zodra gebruikerssynchronisatie is ingeschakeld, worden alleen nieuwe gebruikers en groepen gesynchroniseerd.

1. Controleer of de laatste code is geïnstalleerd:

* [AEM platformupdates](https://helpx.adobe.com/experience-manager/kb/aem62-available-hotfixes.html)
* [AEM Communities-updates](/help/communities/deploy-communities.md#latestfeaturepack)

### 1. Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

**Gebruikerssynchronisatie inschakelen**

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * `Apache Sling Distribution Agent - Sync Agents Factory` zoeken

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)
Verifiëren `name`: **`socialpubsync`**

      * het selectievakje `Enabled` selecteren
      * select `Save`


![](assets/chlimage_1-20.png)

### 2. Gemachtigde gebruiker {#createauthuser} maken

**Vorm**
toestemmingenDeze geautoriseerde gebruiker zal in stap 3 worden gebruikt om de distributie van het Verkopen op auteur te vormen.

* **op elke publicatie-instantie**

   * aanmelden met beheerdersrechten
   * toegang tot [Beveiligingsconsole](/help/sites-administering/security.md)

      * bijvoorbeeld [https://localhost:4503/useradmin](https://localhost:4503/useradmin)
   * een nieuwe gebruiker maken

      * bijvoorbeeld `usersync-admin`
   * deze gebruiker toevoegen aan de **`administrators`**-gebruikersgroep
   * [voeg ACL voor deze gebruiker aan /home toe](#howtoaddacl)

      * `Allow jcr:all` met beperking  `rep:glob=*/activities/*`



>[!CAUTION]
>
>Er moet een nieuwe gebruiker worden gemaakt.
>
>* De standaardgebruiker die wordt toegewezen is **`admin`**.
>* Gebruik `communities-user-admin user.` niet

>



#### Hoe te om ACL {#addacls} toe te voegen

* access CRXDE Lite

   * bijvoorbeeld [https://localhost:4503/crx/de](https://localhost:4503/crx/de)

* knooppunt selecteren `/home`
* in het rechterdeelvenster selecteert u de tab `Access Control`
* selecteer `+` knoop om een ACL ingang toe te voegen

   * **Opdrachtgever**:  *zoeken naar gebruiker gemaakt voor gebruikerssynchronisatie*
   * **Type**:  `Allow`
   * **Bevoegdheden**:  `jcr:all`
   * **** Restrictionsrep:glob:  `*/activities/*`
   * Selecteer **OK**

* Selecteer **Alles opslaan**

![](assets/chlimage_1-21.png)

Zie ook

* [Toegangsbeheer](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Sectie [Bewerkingsuitzondering wijzigen tijdens reactieverwerking](#modify-operation-exception-during-response-processing) voor probleemoplossing.

### 3. Adobe granietdistributie - gecodeerde geheime provider van wachtwoordvervoer {#adobegraniteencpasswrd}

**Machtigingen configureren**

Zodra een geautoriseerde gebruiker, een lid van de **`administrators`**gebruikersgroep, op alle publicatieinstanties is gecreeerd, moet die geautoriseerde gebruiker bij auteur worden geïdentificeerd als hebbend toestemming om gebruikersgegevens van auteur te synchroniseren om te publiceren.

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name` zoeken
   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)
Verifiëren `property name`: **`socialpubsync-publishUser`**

   * Stel de gebruikersnaam en het wachtwoord in op de [geautoriseerde gebruiker](#createauthuser) die is gemaakt bij publicatie in stap 2

      * bijvoorbeeld `usersync-admin`


![](assets/chlimage_1-22.png)

### 4. Apache Sling Distribution Agent - Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

**Gebruikerssynchronisatie inschakelen**

* **bij publicatie**:

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)
   * `Apache Sling Distribution Agent - Queue Agents Factory` zoeken

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)
Verifiëren `Name`: `socialpubsync-reverse`

      * het selectievakje `Enabled` selecteren
      * selecteren `Save`
   * **repeat **for each publish instance



![](assets/chlimage_1-23.png)

### 5. Adobe Social Sync - Diff Observer Factory {#diffobserver}

**Groepssynchronisatie inschakelen**

* **op elke publicatie-instantie**:

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)
   * **`Adobe Social Sync - Diff Observer Factory`** zoeken

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

         Verifiëren `agent name`: `socialpubsync-reverse`

      * het selectievakje `Enabled` selecteren
      * selecteren `Save`


![](assets/screen-shot_2019-05-24at090809.png)

### 6. Apache Sling Distribution Trigger - Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Optioneel) Wijzig het pollinginterval**

Standaard wordt elke 30 seconden een opiniepeiling uitgevoerd. U wijzigt dit interval als volgt:

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * `Apache Sling Distribution Trigger - Scheduled Triggers Factory` zoeken

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

         * Verifiëren `Name`: `socialpubsync-scheduled-trigger`
      * Stel de `Interval in Seconds` in op het gewenste interval
      * selecteren `Save`



![](assets/chlimage_1-24.png)

## Configureren voor meerdere publicatie-instanties {#configure-for-multiple-publish-instances}

De standaardconfiguratie is voor één enkele publicatieinstantie. Aangezien de reden om gebruikerssynchronisatie toe te laten veelvoudige publicatieinstanties moet synchroniseren, zoals voor een publicatielandbouwbedrijf, zullen de extra publicatieinstanties aan de Fabriek van de Agenten van de Synchronisatie moeten worden toegevoegd.

### 7. Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory-1}

**Publicatie-instanties toevoegen:**

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * `Apache Sling Distribution Agent - Sync Agents Factory` zoeken

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)
Verifiëren `Name`: `socialpubsync`


![](assets/chlimage_1-25.png)

* **Exporter**
EndpointsEr zou een exporter eindpunt voor elke uitgever moeten zijn. Als er bijvoorbeeld twee uitgevers zijn, localhost:4503 en 4504, moeten er twee vermeldingen zijn:

   * `https://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse`
   * `https://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse`

* **Importer**
EndpointsEr zou een importereindpunt voor elke uitgever moeten zijn. Als er bijvoorbeeld twee uitgevers zijn, localhost:4503 en 4504, moeten er twee vermeldingen zijn:

   * `https://localhost:4503/libs/sling/distribution/services/importers/socialpubsync`
   * `https://localhost:4504/libs/sling/distribution/services/importers/socialpubsync`

* selecteren `Save`

### 8. AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

**(Optioneel) Aanvullende JCR-knooppunten synchroniseren**

Als er aangepaste gegevens zijn die moeten worden gesynchroniseerd in meerdere publicatievarianten, dan:

* **op elke publicatie-instantie**:

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld `https://localhost:4503/system/console/configMgr`
   * `AEM Communities User Sync Listener` zoeken
   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)
Verifiëren `Name`: `socialpubsync-scheduled-trigger`


![](assets/chlimage_1-26.png)

* **Knooppunttypes**
This is the list of node types that will synchronize. Elk knooppunttype anders dan sling:Folder moet hier worden vermeld (sling:folder wordt afzonderlijk behandeld).
Standaardlijst met knooppunttypen die moeten worden gesynchroniseerd:

   * rep:gebruiker
   * nt:ongestructureerd
   * nt:resource

* **Genegeerde**
eigenschappenDit is de lijst met eigenschappen die wordt genegeerd als er een wijziging wordt gedetecteerd. Wijzigingen in deze eigenschappen worden mogelijk gesynchroniseerd als neveneffect van andere wijzigingen (aangezien synchronisatie altijd op het knooppuntniveau plaatsvindt), maar wijzigingen in deze eigenschappen zullen op zich niet tot synchronisatie leiden.
Standaardeigenschap die moet worden genegeerd:

   * cq:lastModified

* **Genegeerde**
NodesSubpaths die volledig tijdens synchronisatie zullen worden genegeerd. Niets onder deze subpaden zal op elk ogenblik worden gesynchroniseerd.
Standaardknooppunten die moeten worden genegeerd:

   * .tokens
   * systeem

* **Distributed**
FoldersMost sling:Folders worden genegeerd omdat synchronisatie niet nodig is. De weinige uitzonderingen staan hier vermeld.
Standaardmappen voor synchronisatie

   * segmenten/scoring
   * sociale/relaties
   * activiteiten

### 9. Unieke verkoop-id {#unique-sling-id}

>[!CAUTION]
>
>Als de selectie-id overeenkomt met twee of meer publicatie-instanties, mislukt het synchroniseren van de gebruikersgroep.

Als het Verdelen identiteitskaart het zelfde voor veelvoudige publiceer instanties in publiceer landbouwbedrijf is, dan zullen de gebruikersgroepen niet worden gesynchroniseerd.

Om te controleren of alle waarden voor de Verschuivende id verschillen, publiceert u voor elke publicatie-instantie:

1. bladeren naar `http://<host>:<port>/system/console/status-slingsettings`
1. Controleer de waarde van **Schuivende id**

![](assets/chlimage_1-27.png)

Als de Verschuivende-id van een publicatie-instantie overeenkomt met de Verschuivende-id van een andere publicatie-instantie, geldt het volgende:

1. Stop een van de publicatieinstanties die een overeenkomende sloon-id heeft
1. in de map crx-quickstart/launch/felix

   * zoeken naar en het bestand met de naam *sling.id.fi* verwijderen

      * bijvoorbeeld op een Linux-systeem:
         `rm -i $(find . -type f -name sling.id.file)`

      * bijvoorbeeld op een Windows-systeem:
         `use windows explorer and search for *sling.id.file*`

1. De publicatie-instantie starten

   * bij het opstarten wordt er een nieuwe verkoop-id toegewezen

1. Controleren of de **Sling ID** nu uniek is

Herhaal deze stappen totdat alle publicatie-instanties een unieke id voor verkopers hebben.

## Vault Package Builder-fabriek {#vault-package-builder-factory}

Voor een correcte synchronisatie van updates is het nodig om de builder van het vault-pakket te wijzigen voor gebruikerssynchronisatie:

* op elke AEM publicatie-instantie
* toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* `Apache Sling Distribution Packaging - Vault Package Builder Factory` zoeken

   * `Builder name: socialpubsync-vlt`

* Selecteer het bewerkingspictogram
* twee `Package Node Filters` toevoegen:

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* beleidsafhandeling:

   * om bestaande rep:beleidsknopen met nieuwe te overschrijven, voeg een derde Filter van het Pakket toe:

      * `/home/users|+.*/rep:policy`
   * om te voorkomen dat het beleid wordt verspreid,

      * `Acl Handling:` `IGNORE`


![Vault Package Builder-fabriek](assets/vault-package-builder-factory.png)

## Wat gebeurt er als ... {#what-happens-when}

### Gebruiker Zelfinschrijving of Bewerkt Profiel op Publicatie {#user-self-registers-or-edits-profile-on-publish}

Gebruikers en profielen die in de publicatieomgeving (zelfregistratie) zijn gemaakt, worden per ontwerp niet weergegeven in de ontwerpomgeving.

Wanneer de topologie [publiceer landbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm) is en de gebruikerssynchronisatie correct is gevormd, *user *and *gebruikersprofiel* wordt gesynchroniseerd over het publicatielandbouwbedrijf gebruikend het Verschuiven distributie.

### Gebruikers of gebruikersgroepen worden gemaakt met Beveiligingsconsole {#users-or-user-groups-are-created-using-security-console}

Gebruikersgegevens die in de publicatieomgeving zijn gemaakt, worden door het ontwerp niet weergegeven in de auteursomgeving en andersom.

Wanneer de [User Administration and Security](/help/sites-administering/security.md) console wordt gebruikt om nieuwe gebruikers toe te voegen in het publicatiemilieu, zal de gebruikerssynchronisatie de nieuwe gebruikers en hun groepslidmaatschap aan andere publiceren instanties synchroniseren, indien nodig. Gebruikerssynchronisatie synchroniseert ook gebruikersgroepen die zijn gemaakt via de beveiligingsconsole.

## Problemen oplossen {#troubleshooting}

### Gebruikerssynchronisatie offline gebruiken {#how-to-take-user-sync-offline}

Als u gebruikerssynchronisatie offline wilt zetten en een uitgever[ of ](#how-to-remove-a-publisher)gegevens handmatig synchroniseren[ wilt verwijderen, moet de distributierij leeg en stil zijn.](#manually-syncing-users-and-user-groups)

Om de staat van de distributierij te controleren:

* op auteur:

   * gebruiken van [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)

      * zoeken naar items in `/var/sling/distribution/packages`

         * mapknooppunten met het patroon `distrpackage_*`
   * gebruiken [Package Manager](/help/sites-administering/package-manager.md)

      * zoeken naar hangende pakketten (nog niet geïnstalleerd)

         * genoemd met het patroon `socialpubsync-vlt*`
         * gemaakt door `communities-user-admin`


Schakel gebruikerssynchronisatie uit wanneer de distributiestrijd leeg is:

* op auteur

   * *uncheck *the `Enabled` checkbox for [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

Nadat de taken zijn voltooid, kunt u de gebruikerssynchronisatie opnieuw inschakelen:

* op auteur

   * Schakel het selectievakje `Enabled` in voor [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Diagnostische gegevens voor gebruikerssynchronisatie {#user-sync-diagnostics}

Diagnostiek voor gebruikerssynchronisatie is een hulpmiddel dat de configuratie controleert en probeert eventuele problemen op te sporen.

Navigeer bij de auteur eenvoudig van de hoofdconsole door **Hulpmiddelen, Verrichtingen, Diagnose, Diagnostiek van de Synchronisatie van de Gebruiker.**

Als u gewoon de diagnostische console voor gebruikerssynchronisatie invoert, worden de resultaten weergegeven.

Dit is wat wordt getoond wanneer de Synchronisatie van de Gebruiker niet is toegelaten:

![](assets/chlimage_1-28.png)

#### Diagnostiek voor uitgevers uitvoeren {#how-to-run-diagnostics-for-publishers}

Wanneer de diagnose van het auteursmilieu in werking wordt gesteld, zullen de pas/mislukkingsresultaten een [INFO] sectie omvatten die de lijst van gevormde publicatieinstanties voor bevestiging toont.

In de lijst is een URL opgenomen voor elke publicatie-instantie die de diagnostiek voor die instantie uitvoert. De url-parameter `syncUser` wordt toegevoegd aan de diagnostische URL met de waarde ingesteld op *geautoriseerde synchronisatiegebruiker* die is gemaakt in [Stap 2](#createauthuser).

**Opmerking**: voordat u de URL start, moet de  *geautoriseerde* synchronisatiegebruiker al zijn aangemeld bij die publicatie-instantie.

![](assets/chlimage_1-29.png)

### Configuratie onjuist toegevoegd {#configuration-improperly-added}

Wanneer de gebruikerssynchronisatie niet werkt, is het gemeenschappelijkste probleem dat de extra configuraties *werden toegevoegd*. In plaats daarvan, zou *existing *default configuratie *edited* moeten zijn geweest.

Na zijn meningen van hoe uitgegeven, standaardconfiguraties in de Console van het Web zouden moeten verschijnen. Als er meerdere exemplaren worden weergegeven, moet de toegevoegde configuratie worden verwijderd.

#### (auteur) Eén Apache Sling Distribution Agent - Sync Agents Factory {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![](assets/chlimage_1-30.png)

#### (auteur) Eén Apache Sling Distribution Transport Credentials - Gebruikersreferenties gebaseerd DistributionTransportSecretProvider {#author-one-apache-sling-distribution-transport-credentials-user-credentials-based-distributiontransportsecretprovider}

![](assets/chlimage_1-31.png)

#### (publish) One Apache Sling Distribution Agent - Queue Agents Factory {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![](assets/chlimage_1-32.png)

#### (publish) One Adobe Social Sync - Diff Observer Factory {#publish-one-adobe-social-sync-diff-observer-factory}

![](assets/chlimage_1-33.png)

#### (auteur) One Apache Sling Distribution Trigger - Scheduled Triggers Factory {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![](assets/chlimage_1-34.png)

### Bewerkingsuitzondering tijdens reactieverwerking wijzigen {#modify-operation-exception-during-response-processing}

Als het volgende zichtbaar is in het logboek:

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

Controleer vervolgens of de sectie [2. Gemachtigde gebruiker maken](#createauthuser) is op de juiste wijze gevolgd.

Deze sectie beschrijft het creëren van een erkende gebruiker, die op alle publiceer instanties bestaat, en het identificeren van hen in de &quot;Secret Provider&quot;OSGi config op auteur. De gebruiker is standaard `admin`.

De gemachtigde gebruiker zou een lid van **`administrators`** gebruikersgroep moeten worden gemaakt en de toestemmingen voor die groep zouden niet moeten worden veranderd.

De geautoriseerde gebruiker moet expliciet de volgende rechten en beperkingen hebben voor alle publicatieinstanties:

| **path** | **jcr:alles** | **rep:glob** |
|---|---|---|
| /home | X | */activity/* |
| /home/users | X | */activity/* |
| /home/groups | X | */activity/* |

Als lid van de groep `administrators`, zou de gemachtigde gebruiker de volgende voorrechten op alle publicatieinstanties moeten hebben:

| **pad** | **jcr:alles** | **jcr:lezen** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Synchronisatie van gebruikersgroep is mislukt {#user-group-sync-failed}

Als de selectie-id overeenkomt met twee of meer publicatie-instanties, mislukt het synchroniseren van de gebruikersgroep.

Zie sectie [9. Unieke id voor verkopen](#unique-sling-id)

### Gebruikers en gebruikersgroepen handmatig synchroniseren {#manually-syncing-users-and-user-groups}

* op de uitgever waarop gebruikers en gebruikersgroepen bestaan:

   * [indien ingeschakeld, gebruikerssynchronisatie uitschakelen](#how-to-take-user-sync-offline)
   * [een ](/help/sites-administering/package-manager.md#creating-a-new-package) pakket maken van  `/home`

      * bij het bewerken van het pakket

         * Tabblad Filters: Filter toevoegen: Hoofdpad: `/home`
         * Het tabblad Geavanceerd: Wisselstroomverwerking: `Overwrite`
   * [het pakket exporteren](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)


* in andere publicatiegevallen:

   * [het pakket importeren](/help/sites-administering/package-manager.md#installing-packages)

Ga naar stap 1 als u gebruikerssynchronisatie wilt configureren of inschakelen: [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Wanneer een uitgever niet beschikbaar {#when-a-publisher-becomes-unavailable} wordt

Wanneer een publicatie-exemplaar niet beschikbaar is, moet het niet worden verwijderd als het later weer online wordt. De wijzigingen worden in de wachtrij voor de uitgever geplaatst en als deze weer online is, worden de wijzigingen verwerkt.

Als de publicatie-instantie nooit weer online zal zijn, als deze permanent offline is, moet deze worden verwijderd omdat de build van de wachtrij zal resulteren in een merkbaar gebruik van schijfruimte in de auteursomgeving.

Wanneer een uitgever neer is, zal het auteurslogboek uitzonderingen gelijkend op hebben:

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Uitgever {#how-to-remove-a-publisher} verwijderen

Als u een uitgever wilt verwijderen uit [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory), moet de distributierij leeg en stil zijn.

* op auteur:

   * [Gebruikerssynchronisatie offline uitvoeren](#how-to-take-user-sync-offline)
   * Volg [stap 7](#apache-sling-distribution-agent-sync-agents-factory) om de uitgever uit beide serverlijsten te verwijderen:

      * `Exporter Endpoints`
      * `Importer Endpoints`
   * gebruikerssynchronisatie opnieuw inschakelen

      * Schakel het selectievakje `Enabled` in voor [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)
