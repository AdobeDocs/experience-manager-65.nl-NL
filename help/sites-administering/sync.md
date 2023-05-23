---
title: Gebruikerssynchronisatie
seo-title: User Synchronization
description: Meer informatie over gebruikerssynchronisatie in AEM.
seo-description: Learn about user synchronization in AEM.
uuid: 0a519daf-21b7-4adc-b419-eeb8c404c54f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: c061b358-8c0d-40d3-8090-dc9800309ab3
docset: aem65
exl-id: 89f55598-e749-42b8-8f2a-496f45face66
feature: Security
source-git-commit: 002b9035f37a1379556378686b64d26bbbc30288
workflow-type: tm+mt
source-wordcount: '2445'
ht-degree: 1%

---

# Gebruikerssynchronisatie{#user-synchronization}

## Inleiding {#introduction}

Wanneer de implementatie een [publicatiebedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm)leden moeten zich kunnen aanmelden en hun gegevens kunnen bekijken op elk publicatieknooppunt.

Gebruikers en gebruikersgroepen (gebruikersgegevens) die in de publicatieomgeving zijn gemaakt, zijn niet nodig in de ontwerpomgeving.

De meeste gebruikersgegevens die in de auteursomgeving zijn gemaakt, blijven in de auteursomgeving en worden niet gekopieerd naar publicatieinstanties.

Registratie en wijzigingen die zijn aangebracht op één publicatie-instantie moeten worden gesynchroniseerd met andere publicatie-instanties, zodat deze toegang hebben tot dezelfde gebruikersgegevens.

Vanaf AEM 6.1, wanneer gebruikerssynchronisatie wordt toegelaten, worden de gebruikersgegevens automatisch gesynchroniseerd over de publiceer instanties in het landbouwbedrijf en niet gecreeerd op auteur.

## Verspreiding {#sling-distribution}

De gebruikersgegevens, samen met hun [ACLs](/help/sites-administering/security.md), worden opgeslagen in de [Eak Core](/help/sites-deploying/platform.md), de laag onder Oak JCR en worden benaderd met de [Eak-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/oak/api/package-tree.html). Met niet vaak uitgevoerde updates is het redelijk dat gebruikersgegevens worden gesynchroniseerd met andere publicatieinstanties die [Distributie van inhoud verkopen](https://github.com/apache/sling/blob/trunk/contrib/extensions/distribution/README.md) (verkoopverdeling).

De voordelen van gebruikerssynchronisatie met de verkoopverdeling in vergelijking met traditionele replicatie zijn:

* *gebruikers*, *gebruikersprofielen* en *gebruikersgroepen* die zijn gemaakt bij publicatie, worden niet gemaakt bij de auteur

* Bij het splitsen van distributiesets worden eigenschappen in jcr-gebeurtenissen ingesteld, zodat u kunt werken binnen gebeurtenislisteners aan de serverzijde zonder dat u zich zorgen hoeft te maken over oneindige replicatielijnen
* De het verdelen van de distributie verzendt slechts gebruikersgegevens naar niet voortkomende publicatieinstanties, die onnodig verkeer elimineren
* [ACLs](/help/sites-administering/security.md) ingesteld in het gebruikersknooppunt wordt opgenomen in de synchronisatie

>[!NOTE]
>
>Als de zittingen worden vereist, wordt het geadviseerd om of een oplossing te gebruiken SSO of kleverige zitting te gebruiken en klanten te hebben login als zij aan een andere publicatieinstantie worden geschakeld.

>[!CAUTION]
>
>Synchronisatie van de **beheerders** wordt niet ondersteund, zelfs niet als gebruikerssynchronisatie is ingeschakeld. In plaats daarvan wordt een fout bij &#39;het importeren van de diff&#39; in het foutenlogboek geregistreerd.
>
>Daarom wanneer de plaatsing een publiceer landbouwbedrijf is, als een gebruiker aan wordt toegevoegd of uit wordt verwijderd **beheerders** , moet de wijziging handmatig worden aangebracht op elk publicatieexemplaar.

## Gebruikerssynchronisatie inschakelen {#enable-user-sync}

>[!NOTE]
>
>Gebruikerssynchronisatie is standaard `disabled`.
>
>Voor het inschakelen van gebruikerssynchronisatie moet u de wijzigingen aanbrengen *bestaand* OSGi-configuraties.
>
>Er mogen geen nieuwe configuraties worden toegevoegd als gevolg van het inschakelen van gebruikerssynchronisatie.

De gebruikerssynchronisatie is afhankelijk van de auteursomgeving voor het beheer van de gegevensdistributies van de gebruiker, ook al worden de gebruikersgegevens niet op auteur gecreeerd. Veel, maar niet alle, van de configuratie vindt plaats in de auteursomgeving en elke stap identificeert duidelijk of het op auteur of publicatie moet worden uitgevoerd.

Hieronder vindt u de stappen die nodig zijn om gebruikerssynchronisatie in te schakelen, gevolgd door een [Problemen oplossen](#troubleshooting) sectie:

### Vereisten {#prerequisites}

1. Als gebruikers en gebruikersgroepen al op één publicatieexemplaar zijn gemaakt, wordt het aanbevolen [handmatig synchroniseren](#manually-syncing-users-and-user-groups) de gebruikersgegevens voor alle publicatieexemplaren voordat gebruikerssynchronisatie wordt geconfigureerd en ingeschakeld.

Zodra gebruikerssynchronisatie is ingeschakeld, worden alleen nieuwe gebruikers en groepen gesynchroniseerd.

1. Controleer of de laatste code is geïnstalleerd:

* [AEM platformupdates](https://helpx.adobe.com/experience-manager/kb/aem62-available-hotfixes.html)
* [AEM Communities-updates](/help/communities/deploy-communities.md#latestfeaturepack)

### 1. Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory}

**Gebruikerssynchronisatie inschakelen**

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * lokaliseren `Apache Sling Distribution Agent - Sync Agents Factory`

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram) Verifiëren `name`: **`socialpubsync`**

      * Selecteer de `Enabled` selectievakje
      * selecteren `Save`


![](assets/chlimage_1-20.png)

### 2. Geautoriseerde gebruiker maken {#createauthuser}

**Machtigingen configureren**
Deze gemachtigde gebruiker zal in stap 3 worden gebruikt om de distributie van het Verkopen op auteur te vormen.

* **op elke publicatie-instantie**

   * aanmelden met beheerdersrechten
   * toegang tot [Beveiligingsconsole](/help/sites-administering/security.md)

      * bijvoorbeeld: [https://localhost:4503/useradmin](https://localhost:4503/useradmin)
   * een nieuwe gebruiker maken

      * bijvoorbeeld: `usersync-admin`
   * deze gebruiker toevoegen aan de **`administrators`** gebruikersgroep
   * [voeg ACL voor deze gebruiker aan /home toe](#howtoaddacl)

      * `Allow jcr:all` met beperking `rep:glob=*/activities/*`



>[!CAUTION]
>
>Er moet een nieuwe gebruiker worden gemaakt.
>
>* De standaardgebruiker die is toegewezen **`admin`**.
>* Niet gebruiken `communities-user-admin user.`
>


#### Hoe te om ACL toe te voegen {#addacls}

* access CRXDE Lite

   * bijvoorbeeld: [https://localhost:4503/crx/de](https://localhost:4503/crx/de)

* selecteren `/home` node
* Selecteer in het rechterdeelvenster de optie `Access Control` tab
* Selecteer de `+` knoop om een ACL ingang toe te voegen

   * **Opdrachtgever**: *zoeken naar gebruiker gemaakt voor gebruikerssynchronisatie*
   * **Type**: `Allow`
   * **Bevoegdheden**: `jcr:all`
   * **Beperkingen** rep:glob: `*/activities/*`
   * selecteren **OK**

* selecteren **Alles opslaan**

![](assets/chlimage_1-21.png)

Zie ook

* [Toegangsbeheer](/help/sites-administering/user-group-ac-admin.md#access-right-management)
* Sectie Problemen oplossen [Uitzondering bewerking wijzigen tijdens reactieverwerking](#modify-operation-exception-during-response-processing).

### 3. Adobe Granite Distribution - Encrypted Password Transport Secret Provider {#adobegraniteencpasswrd}

**Machtigingen configureren**

Zodra een geautoriseerde gebruiker, lid van de **`administrators`** gebruikersgroep, is gemaakt op alle publicatie-instanties en moet worden aangegeven dat de geautoriseerde gebruiker bij de auteur gemachtigd is om gebruikersgegevens van de auteur te synchroniseren voor publicatie.

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * lokaliseren `com.adobe.granite.distribution.core.impl.CryptoDistributionTransportSecretProvider.name`
   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram) Verifiëren `property name`: **`socialpubsync-publishUser`**

   * stel de gebruikersnaam en het wachtwoord in op de [geautoriseerde gebruiker](#createauthuser) gemaakt bij publicatie in stap 2

      * bijvoorbeeld: `usersync-admin`


![](assets/chlimage_1-22.png)

### 4. Apache Sling Distribution Agent - Queue Agents Factory {#apache-sling-distribution-agent-queue-agents-factory}

**Gebruikerssynchronisatie inschakelen**

* **op elke publicatie-instantie**:

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)
   * lokaliseren `Apache Sling Distribution Agent - Queue Agents Factory`

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram) Verifiëren `Name`: `socialpubsync-reverse`

      * Selecteer de `Enabled` selectievakje
      * selecteren `Save`
   * **herhalen** voor elke publicatie-instantie



![](assets/chlimage_1-23.png)

### 5. Adobe Social Sync - Diff Observer Factory {#diffobserver}

**Groepssynchronisatie inschakelen**

* **op elke publicatie-instantie**:

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)
   * lokaliseren **`Adobe Social Sync - Diff Observer Factory`**

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

         Verifiëren `agent name`: `socialpubsync-reverse`

      * Selecteer de `Enabled` selectievakje
      * selecteren `Save`


![](assets/screen-shot_2019-05-24at090809.png)

### 6. Apache Sling Distribution Trigger - Scheduled Triggers Factory {#apache-sling-distribution-trigger-scheduled-triggers-factory}

**(Optioneel) Wijzig het pollinginterval**

Standaard wordt elke 30 seconden een opiniepeiling uitgevoerd. U wijzigt dit interval als volgt:

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * lokaliseren `Apache Sling Distribution Trigger - Scheduled Triggers Factory`

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram)

         * Verifiëren `Name`: `socialpubsync-scheduled-trigger`
      * instellen `Interval in Seconds` naar het gewenste interval
      * selecteren `Save`



![](assets/chlimage_1-24.png)

## Configureren voor meerdere publicatie-instanties {#configure-for-multiple-publish-instances}

De standaardconfiguratie is voor één enkele publicatieinstantie. Aangezien de reden om gebruikerssynchronisatie toe te laten veelvoudige publicatieinstanties moet synchroniseren, zoals voor een publicatielandbouwbedrijf, zullen de extra publicatieinstanties aan de Fabriek van de Agenten van de Synchronisatie moeten worden toegevoegd.

### 7. Apache Sling Distribution Agent - Sync Agents Factory {#apache-sling-distribution-agent-sync-agents-factory-1}

**Publicatie-instanties toevoegen:**

* **op auteur**

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr)
   * lokaliseren `Apache Sling Distribution Agent - Sync Agents Factory`

      * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram) Verifiëren `Name`: `socialpubsync`


![](assets/chlimage_1-25.png)

* **Eindpunten van export**
Voor elke publicatie-instantie moet een eindpunt voor de exportfunctie aanwezig zijn. Als er bijvoorbeeld 2 publicatie-instanties zijn, localhost:4503 en 4504, moeten er 2 vermeldingen zijn:

   * `https://localhost:4503/libs/sling/distribution/services/exporters/socialpubsync-reverse`
   * `https://localhost:4504/libs/sling/distribution/services/exporters/socialpubsync-reverse`

* **Eindpunten importeren**
Voor elke publicatieinstantie moet een eindpunt voor de importer zijn ingesteld. Als er bijvoorbeeld 2 publicatie-instanties zijn, localhost:4503 en 4504, moeten er 2 vermeldingen zijn:

   * `https://localhost:4503/libs/sling/distribution/services/importers/socialpubsync`
   * `https://localhost:4504/libs/sling/distribution/services/importers/socialpubsync`

* selecteren `Save`

### 8. AEM Communities User Sync Listener {#aem-communities-user-sync-listener}

**(Optioneel) Aanvullende JCR-knooppunten synchroniseren**

Als er aangepaste gegevens zijn die moeten worden gesynchroniseerd in meerdere publicatievarianten, dan:

* **op elke publicatie-instantie**:

   * aanmelden met beheerdersrechten
   * toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

      * bijvoorbeeld: `https://localhost:4503/system/console/configMgr`
   * lokaliseren `AEM Communities User Sync Listener`
   * Selecteer de bestaande configuratie die u wilt openen voor bewerken (potloodpictogram) Verifiëren `Name`: `socialpubsync-scheduled-trigger`


![](assets/chlimage_1-26.png)

* **Knooppunttypen**
Dit is de lijst met knooptypen die worden gesynchroniseerd. Elk knooppunttype anders dan sling:Folder moet hier worden vermeld (sling:folder wordt afzonderlijk behandeld).
Standaardlijst met knooppunttypen die moeten worden gesynchroniseerd:

   * rep:gebruiker
   * nt:ongestructureerd
   * nt:resource

* **Genegeerde eigenschappen**
Dit is de lijst met eigenschappen die worden genegeerd als er wijzigingen worden gedetecteerd. Wijzigingen in deze eigenschappen worden mogelijk gesynchroniseerd als neveneffect van andere wijzigingen (aangezien synchronisatie altijd op het knooppuntniveau plaatsvindt), maar wijzigingen in deze eigenschappen zullen op zich niet tot synchronisatie leiden.
Standaardeigenschap die moet worden genegeerd:

   * cq:lastModified

* **Genegeerde knooppunten**
Subpaden die tijdens de synchronisatie volledig worden genegeerd. Niets onder deze subpaden zal op elk ogenblik worden gesynchroniseerd.
Standaardknooppunten die moeten worden genegeerd:

   * .tokens
   * systeem

* **Verdeelde mappen**
De meeste stappen:Mappen worden genegeerd omdat synchronisatie niet nodig is. De weinige uitzonderingen staan hier vermeld.
Standaardmappen voor synchronisatie

   * segmenten/scoring
   * sociale/relaties
   * activiteiten

### 9. Unieke verkoper-id {#unique-sling-id}

>[!CAUTION]
>
>Als de selectie-id overeenkomt met twee of meer publicatie-instanties, mislukt het synchroniseren van de gebruikersgroep.

Als het Verdelen identiteitskaart het zelfde voor veelvoudige publiceer instanties in publiceer landbouwbedrijf is, dan zullen de gebruikersgroepen niet worden gesynchroniseerd.

Om te controleren of alle waarden voor de Verschuivende id verschillen, publiceert u voor elke publicatie-instantie:

1. bladeren naar `http://<host>:<port>/system/console/status-slingsettings`
1. controleer de waarde van **Verkoop-id**

![](assets/chlimage_1-27.png)

Als de Verschuivende-id van een publicatie-instantie overeenkomt met de Verschuivende-id van een andere publicatie-instantie, geldt het volgende:

1. Stop een van de publicatieinstanties die een overeenkomende sloon-id heeft
1. in de map crx-quickstart/launch/felix

   * zoeken naar en het bestand met de naam *sling.id.file*

      * bijvoorbeeld op een Linux-systeem:
         `rm -i $(find . -type f -name sling.id.file)`

      * bijvoorbeeld op een Windows-systeem:
         `use windows explorer and search for *sling.id.file*`

1. De publicatie-instantie starten

   * bij het opstarten wordt er een nieuwe verkoop-id toegewezen

1. valideren dat de **Verkoop-id** is nu uniek

Herhaal deze stappen totdat alle publicatie-instanties een unieke id voor verkopers hebben.

## Vault Package Builder-fabriek {#vault-package-builder-factory}

Voor een correcte synchronisatie van updates is het nodig om de builder van het vault-pakket te wijzigen voor gebruikerssynchronisatie:

* op elke AEM publicatie-instantie
* toegang tot [Webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* zoek de `Apache Sling Distribution Packaging - Vault Package Builder Factory`

   * `Builder name: socialpubsync-vlt`

* Selecteer het bewerkingspictogram
* twee toevoegen `Package Node Filters`:

   * `/home/users|-.*/.tokens`
   * `/home/users|-.*/rep:cache`

* beleidsafhandeling:

   * om bestaande rep:beleidsknopen met nieuwe te overschrijven, voeg een derde Filter van het Pakket toe:

      * `/home/users|+.*/rep:policy`
   * om te voorkomen dat het beleid wordt verspreid,

      * `Acl Handling:` `IGNORE`


![Vault Package Builder-fabriek](assets/vault-package-builder-factory.png)

## Wat gebeurt er als ... {#what-happens-when}

### Gebruikersnaam of Zelfregistratie- of bewerkingsprofiel bij publiceren {#user-self-registers-or-edits-profile-on-publish}

Gebruikers en profielen die in de publicatieomgeving (zelfregistratie) zijn gemaakt, worden per ontwerp niet weergegeven in de ontwerpomgeving.

Wanneer de topologie een [publicatiebedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm) en de gebruikerssynchronisatie correct is geconfigureerd, *user* en *gebruikersprofiel* wordt gesynchroniseerd over het publicatielandbouwbedrijf gebruikend de distributie van het Schuiven.

### Gebruikers of gebruikersgroepen worden gemaakt met Beveiligingsconsole {#users-or-user-groups-are-created-using-security-console}

Gebruikersgegevens die in de publicatieomgeving zijn gemaakt, worden door het ontwerp niet weergegeven in de auteursomgeving en andersom.

Wanneer de [Gebruikersbeheer en beveiliging](/help/sites-administering/security.md) -console wordt gebruikt om nieuwe gebruikers toe te voegen in de publicatieomgeving. Bij gebruikerssynchronisatie worden de nieuwe gebruikers en hun groepslidmaatschap indien nodig gesynchroniseerd met andere publicatieinstanties. Gebruikerssynchronisatie synchroniseert ook gebruikersgroepen die zijn gemaakt via de beveiligingsconsole.

## Problemen oplossen {#troubleshooting}

### Gebruikerssynchronisatie offline uitvoeren {#how-to-take-user-sync-offline}

Gebruikerssynchronisatie offline zetten om [een publicatie-instantie verwijderen](#how-to-remove-a-publish-instance) of [gegevens handmatig synchroniseren](#manually-syncing-users-and-user-groups), moet de distributierij leeg en stil zijn.

Om de staat van de distributierij te controleren:

* op auteur:

   * gebruiken [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)

      * zoeken naar items in `/var/sling/distribution/packages`

         * mapknooppunten met de naam van het patroon `distrpackage_*`
   * gebruiken [Pakketbeheer](/help/sites-administering/package-manager.md)

      * zoeken naar hangende pakketten (nog niet geïnstalleerd)

         * genoemd met het patroon `socialpubsync-vlt*`
         * gemaakt door `communities-user-admin`


Schakel gebruikerssynchronisatie uit wanneer de distributiestrijd leeg is:

* op auteur

   * *uncheck *the `Enabled` selectievakje voor [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

Nadat de taken zijn voltooid, kunt u de gebruikerssynchronisatie opnieuw inschakelen:

* op auteur

   * controleren `Enabled` selectievakje voor [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Diagnostiek gebruikerssynchronisatie {#user-sync-diagnostics}

Diagnostiek voor gebruikerssynchronisatie is een hulpmiddel dat de configuratie controleert en probeert eventuele problemen op te sporen.

Bij de auteur navigeert u eenvoudig van de hoofdconsole door **Gereedschappen, Bewerkingen, Diagnose, Diagnose van gebruikerssynchronisatie.**

Als u gewoon de diagnostische console voor gebruikerssynchronisatie invoert, worden de resultaten weergegeven.

Dit is wat wordt getoond wanneer de Synchronisatie van de Gebruiker niet is toegelaten:

![](assets/chlimage_1-28.png)

#### Diagnostiek voor publicatie-instanties uitvoeren {#how-to-run-diagnostics-for-publish-instances}

Wanneer de diagnose wordt uitgevoerd vanuit de auteursomgeving, bevatten de resultaten voor slagen/zakken een [INFO] sectie waarin de lijst met geconfigureerde publicatieinstanties ter bevestiging wordt weergegeven.

In de lijst is een URL opgenomen voor elke publicatie-instantie die de diagnostiek voor die instantie uitvoert. De url-parameter `syncUser` wordt toegevoegd aan de diagnoseURL met de waarde ingesteld op *geautoriseerde synchronisatiegebruiker* gemaakt in [Stap 2](#createauthuser).

**Opmerking**: voordat u de URL start, *geautoriseerde synchronisatiegebruiker* moet al zijn aangemeld bij dat publicatieexemplaar.

![](assets/chlimage_1-29.png)

### Configuratie onjuist toegevoegd {#configuration-improperly-added}

Wanneer de gebruikerssynchronisatie niet werkt, is het meest voorkomende probleem dat er meer configuraties zijn *added*. In plaats daarvan, zou de *existing *default configuratie moeten geweest zijn *bewerkt*.

Na zijn meningen van hoe uitgegeven, standaardconfiguraties in de Console van het Web zouden moeten verschijnen. Als er meerdere exemplaren worden weergegeven, moet de toegevoegde configuratie worden verwijderd.

#### (auteur) Eén Apache Sling Distribution Agent - Sync Agents Factory {#author-one-apache-sling-distribution-agent-sync-agents-factory}

![](assets/chlimage_1-30.png)

#### (auteur) Eén Apache Sling Distribution Transport Credentials - Gebruikersreferenties gebaseerd DistributionTransportSecretProvider {#author-one-apache-sling-distribution-transport-credentials-user-credentials-based-distributiontransportsecretprovider}

![](assets/chlimage_1-31.png)

#### (publiceren) Eén Apache Sling Distribution Agent - Queue Agents Factory {#publish-one-apache-sling-distribution-agent-queue-agents-factory}

![](assets/chlimage_1-32.png)

#### (publiceren) Eén Adobe Social Sync - Diff Observer Factory {#publish-one-adobe-social-sync-diff-observer-factory}

![](assets/chlimage_1-33.png)

#### (auteur) One Apache Sling Distribution Trigger - Scheduled Triggers Factory {#author-one-apache-sling-distribution-trigger-scheduled-triggers-factory}

![](assets/chlimage_1-34.png)

### Uitzondering bewerking wijzigen tijdens reactieverwerking {#modify-operation-exception-during-response-processing}

Als het volgende zichtbaar is in het logboek:

`org.apache.sling.servlets.post.impl.operations.ModifyOperation Exception during response processing.`

`java.lang.IllegalStateException: This tree does not exist`

Controleer vervolgens of de sectie [2. Geautoriseerde gebruiker maken](#createauthuser) correct is opgevolgd.

Deze sectie beschrijft het creëren van een erkende gebruiker, die op alle publiceer instanties bestaat, en het identificeren van hen in de &quot;Secret Provider&quot;OSGi config op auteur. Standaard is de gebruiker `admin`.

De geautoriseerde gebruiker moet lid worden van de **`administrators`** gebruikersgroep en machtigingen voor die groep mogen niet worden gewijzigd.

De geautoriseerde gebruiker moet expliciet de volgende rechten en beperkingen hebben voor alle publicatieinstanties:

| **pad** | **jcr:alles** | **rep:glob** |
|---|---|---|
| /home | X | &#42;/activities/&#42; |
| /home/users | X | &#42;/activities/&#42; |
| /home/groups | X | &#42;/activities/&#42; |

Als lid van de `administrators` de geautoriseerde gebruiker de volgende rechten verlenen bij alle publicatieexemplaren:

| **pad** | **jcr:alles** | **jcr:lezen** | **rep:write** |
|---|---|---|---|
| /etc/packages/sling/distribution |  |  | X |
| /libs/sling/distribution |  | X |  |
| /var |  |  | X |
| /var/eventing |  | X | X |
| /var/sling/distribution |  | X | X |

### Synchronisatie van gebruikersgroep is mislukt {#user-group-sync-failed}

Als de selectie-id overeenkomt met twee of meer publicatie-instanties, mislukt het synchroniseren van de gebruikersgroep.

Zie sectie [9. Unieke verkoper-id](#unique-sling-id)

### Gebruikers en gebruikersgroepen handmatig synchroniseren {#manually-syncing-users-and-user-groups}

* bij publicatie-instanties waarop gebruikers en gebruikersgroepen aanwezig zijn:

   * [indien ingeschakeld, gebruikerssynchronisatie uitschakelen](#how-to-take-user-sync-offline)
   * [een pakket maken](/help/sites-administering/package-manager.md#creating-a-new-package) van `/home`

      * bij het bewerken van het pakket

         * Tabblad Filters: Filter toevoegen: Hoofdpad: `/home`
         * Het tabblad Geavanceerd: Wisselstroomverwerking: `Overwrite`
   * [het pakket exporteren](/help/sites-administering/package-manager.md#downloading-packages-to-your-file-system)


* in andere publicatiegevallen:

   * [het pakket importeren](/help/sites-administering/package-manager.md#installing-packages)

Ga naar stap 1 als u gebruikerssynchronisatie wilt configureren of inschakelen: [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)

### Wanneer een publicatie-instantie niet meer beschikbaar is {#when-a-publish-instance-becomes-unavailable}

Wanneer een publicatieexemplaar niet beschikbaar wordt, zou het niet moeten worden verwijderd als het in de toekomst weer online zal zijn. De wijzigingen worden in de wachtrij voor de publicatie-instantie geplaatst en als deze weer online is, worden de wijzigingen verwerkt.

Als de publicatie-instantie nooit weer online zal zijn, als deze permanent offline is, moet deze worden verwijderd omdat de build van de wachtrij zal resulteren in een merkbaar gebruik van schijfruimte in de auteursomgeving.

Wanneer een publicatieexemplaar neer is, zal het auteurslogboek uitzonderingen gelijkend op hebben:

```
28.01.2016 15:57:48.475 ERROR
 [pool-12-thread-34-org_apache_sling_distribution_queue_socialpubsync_endpoint1
 (org/apache/sling/distribution/queue/socialpubsync/endpoint1)]
 org.apache.sling.distribution.agent.impl.SimpleDistributionAgent [agent][socialpubsync] could not deliver package distrpackage_1454014575838_a2b45ec8-0400-42f3-bed8-ae09b66381cb
 org.apache.sling.distribution.packaging.DistributionPackageImportException: failed in importing package ...
```

### Een publicatie-instantie verwijderen {#how-to-remove-a-publish-instance}

Een publicatie-instantie verwijderen uit het dialoogvenster [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory), moet de distributierij leeg en stil zijn.

* op auteur:

   * [Gebruikerssynchronisatie offline uitvoeren](#how-to-take-user-sync-offline)
   * volgen [stap 7](#apache-sling-distribution-agent-sync-agents-factory) om het publicatieexemplaar uit beide serverlijsten te verwijderen:

      * `Exporter Endpoints`
      * `Importer Endpoints`
   * gebruikerssynchronisatie opnieuw inschakelen

      * controleren `Enabled` selectievakje voor [Apache Sling Distribution Agent - Sync Agents Factory](#apache-sling-distribution-agent-sync-agents-factory)
