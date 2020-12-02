---
title: cURL gebruiken met AEM
seo-title: cURL gebruiken met AEM
description: Leer hoe u cURL met AEM gebruikt.
seo-description: Leer hoe u cURL met AEM gebruikt.
uuid: 771b9acc-ff3a-41c9-9fee-7e5d2183f311
contentOwner: Silviu Raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: d4ceb82e-2889-4507-af22-b051af83be38
translation-type: tm+mt
source-git-commit: 4eb5f1c4aa6631d2570279eb1d4bf17a928e3b9f
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---


# cURL gebruiken met AEM{#using-curl-with-aem}

Beheerders moeten veelvoorkomende taken in elk systeem vaak automatiseren of vereenvoudigen. In AEM bijvoorbeeld, zijn het leiden van gebruikers, het installeren van pakketten, en het beheren van bundels OSGi taken die algemeen moeten worden gedaan.

Vanwege de RESTful-aard van het Sling-framework waarop AEM is gebouwd, kunnen de meeste taken worden beperkt tot een URL-aanroep. cURL kan worden gebruikt om dergelijke URL vraag uit te voeren en kan een nuttig hulpmiddel voor AEM beheerders zijn.

## Wat is cURL {#what-is-curl}

cURL is een opensource opdrachtregelprogramma voor het uitvoeren van URL-bewerkingen. Deze biedt ondersteuning voor een groot aantal internetprotocollen, waaronder HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, DAP, DICT, TELNET, FILE, IMAP, POP3, SMTP en RTSP.

cURL is een gevestigde en wijdverspreide hulpmiddel om gegevens te krijgen of te verzenden gebruikend de syntaxis URL en oorspronkelijk vrijgegeven in 1997. De naam cURL betekende oorspronkelijk &quot;zie URL.&quot;

Vanwege de RESTful-aard van het Sling-framework waarop AEM is gebouwd, kunnen de meeste taken worden beperkt tot een URL-aanroep, die kan worden uitgevoerd met cURL. [Met ](/help/sites-administering/curl.md#common-content-manipulation-aem-curl-commands) cURL kunnen taken voor het manipuleren van inhoud worden geautomatiseerd, zoals het activeren van pagina&#39;s, het starten van workflows en  [operationele ](/help/sites-administering/curl.md#common-operational-aem-curl-commands) taken, zoals pakketbeheer en het beheren van gebruikers. Bovendien kunt u [uw eigen cURL](/help/sites-administering/curl.md#building-a-curl-ready-aem-command) bevelen voor de meeste taken in AEM tot stand brengen.

>[!NOTE]
>
>Elke AEM die via cURL wordt uitgevoerd, moet net als elke gebruiker worden geautoriseerd om te AEM. Alle ACLs en toegangsrechten worden gerespecteerd wanneer het gebruiken van cURL om een AEM bevel uit te voeren.

## URL {#downloading-curl} downloaden

cURL is een standaardonderdeel van macOS en sommige Linux-distros. Deze is echter voor de meeste besturingssystemen beschikbaar. De meest recente downloads vindt u op [https://curl.haxx.se/download.html](https://curl.haxx.se/download.html).

cURL&#39;s bronbewaarplaats kan ook op GitHub worden gevonden.

## Een AEM maken die geschikt is voor cURL {#building-a-curl-ready-aem-command}

cURL-opdrachten kunnen worden samengesteld voor de meeste bewerkingen in AEM, zoals workflows activeren, OSGi-configuraties controleren, JMX-opdrachten activeren, replicatieagents maken en nog veel meer.

Om het nauwkeurige bevel te vinden u voor uw bepaalde verrichting nodig hebt, moet u de ontwikkelaarshulpmiddelen in uw browser gebruiken om de vraag van de POST aan de server te vangen wanneer u het AEM bevel uitvoert.

In de volgende stappen wordt beschreven hoe u dit kunt doen door als voorbeeld een nieuwe pagina te maken in de Chrome-browser.

1. Bereid de actie voor u binnen AEM wenst aan te halen. In dit geval, hebben wij aan het eind van **Create Pagina** tovenaar in gang gezet, maar nog niet **Create** geklikt.

   ![chlimage_1-66](assets/chlimage_1-66a.png)

1. Start de ontwikkelaarsgereedschappen en selecteer het tabblad **Netwerk**. Klik op de optie **Logbestand behouden** voordat u de console wist.

   ![chlimage_1-67](assets/chlimage_1-67a.png)

1. Klik **Create** in **Create Page** tovenaar om de werkstroom eigenlijk tot stand te brengen.
1. Klik met de rechtermuisknop op de resulterende POST en selecteer **Kopiëren** -> **Kopiëren als cURL**.

   ![chlimage_1-68](assets/chlimage_1-68a.png)

1. Kopieer de opdracht cURL naar een teksteditor en verwijder alle koppen uit de opdracht, die beginnen met `-H` (in de onderstaande afbeelding blauw gemarkeerd) en voeg de juiste verificatieparameter toe, zoals `-u <user>:<password>`.

   ![chlimage_1-69](assets/chlimage_1-69a.png)

1. Voer de opdracht cURL uit via de opdrachtregel en bekijk de reactie.

   ![chlimage_1-70](assets/chlimage_1-70a.png)

## Gemeenschappelijke operationele AEM cURL-opdrachten {#common-operational-aem-curl-commands}

Hier volgt een lijst met AEM cURL-opdrachten voor algemene beheertaken en operationele taken.

>[!NOTE]
>
>In de volgende voorbeelden wordt ervan uitgegaan dat AEM op `localhost` op poort `4502` wordt uitgevoerd en de gebruiker `admin` met wachtwoord `admin` wordt gebruikt. Extra plaatsaanduidingen voor opdrachten worden ingesteld tussen punthaken.

### Pakketbeheer {#package-management}

#### Alle geïnstalleerde pakketten weergeven

```shell
curl -u <user>:<password> http://<host>:<port>/crx/packmgr/service.jsp?cmd=ls
```

#### Een pakket maken {#create-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=create -d packageName=<name> -d groupName=<name>
```

#### Een pakket voorvertonen {#preview-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=preview
```

#### Inhoud van pakket weergeven {#list-package-content}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/console.html/etc/packages/mycontent.zip?cmd=contents
```

#### Een pakket maken {#build-a-package}

```shell
curl -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=build
```

#### Een pakket {#rewrap-a-package} omsluiten

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=rewrap
```

#### De naam van een pakket wijzigen {#rename-a-package}

```shell
curl -u <user>:<password> -X POST -Fname=<New Name> http://localhost:4502/etc/packages/<Group Name>/<Package Name>.zip/jcr:content/vlt:definition
```

#### Een pakket {#upload-a-package} uploaden

```shell
curl -u <user>:<password> -F cmd=upload -F force=true -F package=@test.zip http://localhost:4502/crx/packmgr/service/.json
```

#### Pakket {#install-a-package} installeren

```shell
curl -u <user>:<password> -F cmd=install http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### Een pakket {#uninstall-a-package} verwijderen

```shell
curl -u <user>:<password> -F cmd=uninstall http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### Een pakket {#delete-a-package} verwijderen

```shell
curl -u <user>:<password> -F cmd=delete http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### Een pakket {#download-a-package} downloaden

```shell
curl -u <user>:<password> http://localhost:4502/etc/packages/my_packages/test.zip
```

### Gebruikersbeheer {#user-management}

#### Nieuwe gebruiker maken {#create-a-new-user}

```shell
curl -u <user>:<password> -FcreateUser= -FauthorizableId=hashim -Frep:password=hashim http://localhost:4502/libs/granite/security/post/authorizables
```

#### Nieuwe groep maken {#create-a-new-group}

```shell
curl -u <user>:<password> -FcreateGroup=group1 -FauthorizableId=testGroup1 http://localhost:4502/libs/granite/security/post/authorizables
```

#### Een eigenschap toevoegen aan een bestaande gebruiker {#add-a-property-to-an-existing-user}

```shell
curl -u <user>:<password> -Fprofile/age=25 http://localhost:4502/home/users/h/hashim.rw.html
```

#### Een gebruiker maken met een profiel {#create-a-user-with-a-profile}

```shell
curl -u <user>:<password> -FcreateUser=testuser -FauthorizableId=hashimkhan -Frep:password=hashimkhan -Fprofile/gender=male http://localhost:4502/libs/granite/security/post/authorizables
```

#### Een nieuwe gebruiker maken als lid van een groep {#create-a-new-user-as-a-member-of-a-group}

```shell
curl -u <user>:<password> -FcreateUser=testuser -FauthorizableId=testuser -Frep:password=abc123 -Fmembership=contributor http://localhost:4502/libs/granite/security/post/authorizables
```

#### Een gebruiker toevoegen aan een groep {#add-a-user-to-a-group}

```shell
curl -u <user>:<password> -FaddMembers=testuser1 http://localhost:4502/home/groups/t/testGroup.rw.html
```

#### Een gebruiker uit een groep verwijderen {#remove-a-user-from-a-group}

```shell
curl -u <user>:<password> -FremoveMembers=testuser1 http://localhost:4502/home/groups/t/testGroup.rw.html
```

#### Groepslidmaatschap van een gebruiker instellen {#set-a-user-s-group-membership}

```shell
curl -u <user>:<password> -Fmembership=contributor -Fmembership=testgroup http://localhost:4502/home/users/t/testuser.rw.html
```

#### Een gebruiker {#delete-a-user} verwijderen

```shell
curl -u <user>:<password> -FdeleteAuthorizable= http://localhost:4502/home/users/t/testuser 
```

#### Een groep {#delete-a-group} verwijderen

```shell
curl -u <user>:<password> -FdeleteAuthorizable= http://localhost:4502/home/groups/t/testGroup
```

### Back-up {#backup}

Zie [Back-up en herstel](/help/sites-administering/backup-and-restore.md#automating-aem-online-backup) voor meer informatie.

### OSGi {#osgi}

#### Een bundel {#starting-a-bundle} starten

```shell
curl -u <user>:<password> -Faction=start http://localhost:4502/system/console/bundles/<bundle-name>
```

#### Een bundel {#stopping-a-bundle} stoppen

```shell
curl -u <user>:<password> -Faction=stop http://localhost:4502/system/console/bundles/<bundle-name>
```

### Verzending {#dispatcher}

#### De cache {#invalidate-the-cache} ongeldig maken

```shell
curl -H "CQ-Action: Activate" -H "CQ-Handle: /content/test-site/" -H "CQ-Path: /content/test-site/" -H "Content-Length: 0" -H "Content-Type: application/octet-stream" http://localhost:4502/dispatcher/invalidate.cache
```

#### De cache {#evict-the-cache} uitpakken

```shell
curl -H "CQ-Action: Deactivate" -H "CQ-Handle: /content/test-site/" -H "CQ-Path: /content/test-site/" -H "Content-Length: 0" -H "Content-Type: application/octet-stream" http://localhost:4502/dispatcher/invalidate.cache
```

### Replication Agent {#replication-agent}

#### Controleer de Status van een Agent {#check-the-status-of-an-agent}

```shell
curl -u <user>:<password> "http://localhost:4502/etc/replication/agents.author/publish/jcr:conten t.queue.json?agent=publish"
http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.js on?agent=publish
```

#### Een agent {#delete-an-agent} verwijderen

```shell
curl -X DELETE http://localhost:4502/etc/replication/agents.author/replication99 -u <user>:<password>
```

#### Een agent {#create-an-agent} maken

```shell
curl -u <user>:<password> -F "jcr:primaryType=cq:Page" -F "jcr:content/jcr:title=new-replication" -F "jcr:content/sling:resourceType=/libs/cq/replication/components/agent" -F "jcr:content/template=/libs/cq/replication/templates/agent" -F "jcr:content/transportUri=http://localhost:4503/bin/receive?sling:authRequestLogin=1" -F "jcr:content/transportUser=admin" -F "jcr:content/transportPassword={DES}8aadb625ced91ac483390ebc10640cdf"http://localhost:4502/etc/replication/agents.author/replication99
```

#### Een agent {#pause-an-agent} pauzeren

```shell
curl -u <user>:<password> -F "cmd=pause" -F "name=publish"  http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.js on
```

#### Wis een Rij van de Agent {#clear-an-agent-queue}

```shell
curl -u <user>:<password> -F "cmd=clear" -F "name=publish"  http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.js on
```

### Gemeenschappen {#communities}

#### Badges toewijzen en intrekken {#assign-and-revoke-badges}

Zie [Scores van gemeenschappen en Badges](/help/communities/implementing-scoring.md#assign-and-revoke-badges) voor meer informatie.

Zie [Scoring en Badges Essentials](/help/communities/configure-scoring.md#example-setup) voor meer informatie.

#### MSRP opnieuw indexeren {#msrp-reindexing}

Zie [MSRP - MongoDB Storage Resource Provider](/help/communities/msrp.md#running-msrp-reindex-tool-using-curl-command) voor meer informatie.

### Beveiliging {#security}

#### CRX DE Lite {#enabling-and-disabling-crx-de-lite} inschakelen en uitschakelen

Zie [CRXDE Lite inschakelen in AEM](/help/sites-administering/enabling-crxde-lite.md) voor meer informatie.

### Afvalverzameling gegevensopslag {#data-store-garbage-collection}

Zie [Gegevensopslag opschonen](/help/sites-administering/data-store-garbage-collection.md#automating-data-store-garbage-collection) voor meer informatie.

### Analyse en doelintegratie {#analytics-and-target-integration}

Zie [Opteren in Adobe Analytics en Adobe Target](/help/sites-administering/opt-in.md#configuring-the-setup-and-provisioning-via-script) voor meer informatie.

### Enkelvoudige aanmelding {#single-sign-on}

#### Testkop {#send-test-header} verzenden

Zie [Single Sign On](/help/sites-deploying/single-sign-on.md) voor meer informatie.

## Gemeenschappelijke Inhoud Manipulation AEM cURL-opdrachten {#common-content-manipulation-aem-curl-commands}

Hier volgt een lijst met AEM cURL-opdrachten voor het manipuleren van inhoud.

>[!NOTE]
>
>In de volgende voorbeelden wordt ervan uitgegaan dat AEM op `localhost` op poort `4502` wordt uitgevoerd en de gebruiker `admin` met wachtwoord `admin` wordt gebruikt. Extra plaatsaanduidingen voor opdrachten worden ingesteld tussen punthaken.

### Paginabeheer {#page-management}

#### Paginaactivering {#page-activation}

```shell
curl -u <user>:<password> -X POST -F path="/content/path/to/page" -F cmd="activate" http://localhost:4502/bin/replicate.json
```

#### Deactivering van pagina {#page-deactivation}

```shell
curl -u <user>:<password> -X POST -F path="/content/path/to/page" -F cmd="deactivate" http://localhost:4502/bin/replicate.json
```

#### Boomactivering {#tree-activation}

```shell
curl -u <user>:<password> -F cmd=activate -F ignoredeactivated=true -F onlymodified=true -F path=/content/geometrixx http://localhost:4502/etc/replication/treeactivation.html
```

#### Pagina {#lock-page} vergrendelen

```shell
curl -u <user>:<password> -X POST -F cmd="lockPage" -F path="/content/path/to/page" -F "_charset_"="utf-8" http://localhost:4502/bin/wcmcommand
```

#### Pagina {#unlock-page} ontgrendelen

```shell
curl -u <user>:<password> -X POST -F cmd="unlockPage" -F path="/content/path/to/page" -F "_charset_"="utf-8" http://localhost:4502/bin/wcmcommand
```

#### Pagina {#copy-page} kopiëren

```shell
curl -u <user>:<password> -F cmd=copyPage -F destParentPath=/path/to/destination/parent -F srcPath=/path/to/source/location http://localhost:4502/bin/wcmcommand
```

### Workflows {#workflows}

Zie [Interactie met Workflows programmatisch](/help/sites-developing/workflows-program-interaction.md) voor meer informatie.

### Inhoud afspelen {#sling-content}

#### Een map maken {#create-a-folder}

```shell
curl -u <user>:<password> -F jcr:primaryType=sling:Folder http://localhost:4502/etc/test
```

#### Een knooppunt {#delete-a-node} verwijderen

```shell
curl -u <user>:<password> -F :operation=delete http://localhost:4502/etc/test/test.properties
```

#### Een knooppunt {#move-a-node} verplaatsen

```shell
curl -u <user>:<password> -F":operation=move" -F":applyTo=/sourceurl"  -F":dest=/target/parenturl/" https://localhost:4502/content
```

#### Een knooppunt {#copy-a-node} kopiëren

```shell
curl -u <user>:<password> -F":operation=copy" -F":applyTo=/sourceurl"  -F":dest=/target/parenturl/" https://localhost:4502/content
```

#### Bestanden uploaden met Sling PostServlet {#upload-files-using-sling-postservlet}

```shell
curl -u <user>:<password> -F"*=@test.properties"  http://localhost:4502/etc/test
```

#### Bestanden uploaden met Sling PostServlet en het opgeven van de knooppuntnaam {#upload-files-using-sling-postservlet-and-specifying-node-name}

```shell
curl -u <user>:<password> -F"test2.properties=@test.properties"  http://localhost:4502/etc/test
```

#### Bestanden uploaden die een inhoudstype {#upload-files-specifying-a-content-type} opgeven

```shell
curl -u <user>:<password> -F "*=@test.properties;type=text/plain" http://localhost:4502/etc/test
```

### Manipulatie van bedrijfsmiddelen {#asset-manipulation}

Zie [Elementen van HTTP API](/help/assets/mac-api-assets.md) voor meer informatie.
