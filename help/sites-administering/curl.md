---
title: cURL gebruiken met AEM
description: Leer hoe u cURL gebruikt voor algemene Adobe Experience Manager-taken.
contentOwner: Silviu Raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: e3f018e6-563e-456f-99d5-d232f1a4aa55
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 12b370e3041ff179cd249f3d4e6ef584c4339909
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 0%

---

# cURL gebruiken met AEM{#using-curl-with-aem}

Beheerders moeten veelvoorkomende taken in elk systeem vaak automatiseren of vereenvoudigen. In AEM bijvoorbeeld, zijn het leiden van gebruikers, het installeren van pakketten, en het beheren van bundels OSGi taken die algemeen moeten worden gedaan.

Wegens de RESTful aard van het Sling kader waarop AEM wordt gebouwd, kunnen de meeste taken met een vraag worden gedaan URL. cURL kan worden gebruikt om dergelijke URL vraag uit te voeren en kan een nuttig hulpmiddel voor beheerders van AEM zijn.

## Wat is cURL {#what-is-curl}

cURL is een opensource opdrachtregelprogramma voor het uitvoeren van URL-bewerkingen. Deze biedt ondersteuning voor een groot aantal internetprotocollen, waaronder HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, DAP, DICT, TELNET, FILE, IMAP, POP3, SMTP en RTSP.

cURL is een gevestigde en wijdverspreide hulpmiddel om gegevens te krijgen of te verzenden gebruikend de syntaxis URL en oorspronkelijk vrijgegeven in 1997. De naam cURL betekende oorspronkelijk &quot;zie URL.&quot;

Wegens het RESTful karakter van het Sling kader waarop AEM wordt gebouwd, kunnen de meeste taken tot een vraag worden beperkt URL, die met cURL kan worden uitgevoerd. [ de manipulatietaken van de Inhoud ](/help/sites-administering/curl.md#common-content-manipulation-aem-curl-commands) zoals het activeren van pagina&#39;s, en het beginnen werkschema&#39;s en [ operationele taken ](/help/sites-administering/curl.md#common-operational-aem-curl-commands) zoals pakketbeheer en het beheren van gebruikers kunnen worden geautomatiseerd gebruikend cURL. Bovendien kunt u [ uw eigen cURL ](/help/sites-administering/curl.md#building-a-curl-ready-aem-command) bevelen voor de meeste taken in AEM tot stand brengen.

>[!NOTE]
>
>Elke AEM-opdracht die via cURL wordt uitgevoerd, moet op dezelfde manier worden geautoriseerd als elke gebruiker aan AEM. Alle ACLs en toegangsrechten worden gerespecteerd wanneer het gebruiken van cURL om een bevel van AEM uit te voeren.

## cURL downloaden {#downloading-curl}

cURL is een standaardonderdeel van macOS en sommige Linux-distros. Deze is echter voor de meeste besturingssystemen beschikbaar. De recentste downloads kunnen in [ https://curl.haxx.se/download.html ](https://curl.haxx.se/download.html) worden gevonden.

cURL&#39;s bronbewaarplaats kan ook op GitHub worden gevonden.

## Een AEM-opdracht maken die geschikt is voor cURL {#building-a-curl-ready-aem-command}

cURL-opdrachten kunnen worden samengesteld voor de meeste bewerkingen in AEM, zoals workflows activeren, OSGi-configuraties controleren, JMX-opdrachten activeren, replicatieagents maken en nog veel meer.

Als u de exacte opdracht wilt vinden die u voor een bepaalde bewerking nodig hebt, moet u de ontwikkelaarsgereedschappen in uw browser gebruiken om de POST-aanroep naar de server vast te leggen wanneer u de AEM-opdracht uitvoert.

In de volgende stappen wordt beschreven hoe u dit kunt doen door als voorbeeld een nieuwe pagina in de Chrome-browser te maken.

1. Bereid de actie voor u binnen AEM wenst aan te halen. In dit geval, hebben wij aan het eind van **voorafgegaan leidt tot de tovenaar van de Pagina**, maar nog niet geklikt **creeer**.

   ![ chlimage_1-66 ](assets/chlimage_1-66a.png)

1. Begin de ontwikkelaarshulpmiddelen en selecteer het **Netwerk** lusje. Klik de **optie van het Logboek van het Behoud** alvorens de console te ontruimen.

   ![ chlimage_1-67 ](assets/chlimage_1-67a.png)

1. Klik **creëren** in **creëren de tovenaar van de Pagina** om het werkschema eigenlijk tot stand te brengen.
1. Klik de resulterende POST actie met de rechtermuisknop aan en selecteer **Exemplaar** > **Exemplaar als cURL**.

   ![ chlimage_1-68 ](assets/chlimage_1-68a.png)

1. Kopieer de opdracht cURL naar een teksteditor en verwijder alle koppen uit de opdracht, die beginnen met `-H` (in de onderstaande afbeelding blauw gemarkeerd) en voeg de juiste verificatieparameter toe, zoals `-u <user>:<password>` .

   ![ chlimage_1-69 ](assets/chlimage_1-69a.png)

1. Voer de opdracht cURL uit via de opdrachtregel en bekijk de reactie.

   ![ chlimage_1-70 ](assets/chlimage_1-70a.png)

## Algemene AEM cURL-opdrachten {#common-operational-aem-curl-commands}

Hier volgt een lijst met AEM cURL-opdrachten voor algemene beheertaken en operationele taken.

>[!NOTE]
>
>In de volgende voorbeelden wordt ervan uitgegaan dat AEM wordt uitgevoerd op `localhost` on port `4502` en dat de gebruiker `admin` met wachtwoord `admin` wordt gebruikt. Extra plaatsaanduidingen voor opdrachten worden ingesteld tussen punthaken.

### Pakketbeheer {#package-management}

#### Alle geïnstalleerde pakketten weergeven

```shell
curl -u <user>:<password> http://<host>:<port>/crx/packmgr/service.jsp?cmd=ls
```

#### Een pakket maken {#create-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=create -d packageName=<name> -d groupName=<name>
```

#### Een voorbeeld van een pakket bekijken {#preview-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=preview
```

#### Pakketinhoud weergeven {#list-package-content}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/console.html/etc/packages/mycontent.zip?cmd=contents
```

#### Een pakket maken {#build-a-package}

```shell
curl -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=build
```

#### Een pakket opnieuw inpakken {#rewrap-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=rewrap
```

#### De naam van een pakket wijzigen {#rename-a-package}

```shell
curl -u <user>:<password> -X POST -Fname=<New Name> http://localhost:4502/etc/packages/<Group Name>/<Package Name>.zip/jcr:content/vlt:definition
```

#### Een pakket uploaden {#upload-a-package}

```shell
curl -u <user>:<password> -F cmd=upload -F force=true -F package=@test.zip http://localhost:4502/crx/packmgr/service/.json
```

#### Een pakket installeren {#install-a-package}

```shell
curl -u <user>:<password> -F cmd=install http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### Een pakket verwijderen {#uninstall-a-package}

```shell
curl -u <user>:<password> -F cmd=uninstall http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### Een pakket verwijderen {#delete-a-package}

```shell
curl -u <user>:<password> -F cmd=delete http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### Een pakket downloaden {#download-a-package}

```shell
curl -u <user>:<password> http://localhost:4502/etc/packages/my_packages/test.zip
```

#### Een pakket repliceren {#replicate-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip?cmd=replicate
```

### Gebruikersbeheer {#user-management}

#### Een nieuwe gebruiker maken {#create-a-new-user}

```shell
curl -u <user>:<password> -FcreateUser= -FauthorizableId=hashim -Frep:password=hashim http://localhost:4502/libs/granite/security/post/authorizables
```

#### Een nieuwe groep maken {#create-a-new-group}

```shell
curl -u <user>:<password> -FcreateGroup=group1 -FauthorizableId=testGroup1 http://localhost:4502/libs/granite/security/post/authorizables
```

#### Een eigenschap toevoegen aan een bestaande gebruiker {#add-a-property-to-an-existing-user}

```shell
curl -u <user>:<password> -Fprofile/age=25 http://localhost:4502/home/users/h/hashim.rw.html
```

#### Een gebruiker met een profiel maken {#create-a-user-with-a-profile}

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

#### Gebruikersgroeplidmaatschap instellen {#set-a-user-s-group-membership}

```shell
curl -u <user>:<password> -Fmembership=contributor -Fmembership=testgroup http://localhost:4502/home/users/t/testuser.rw.html
```

#### Een gebruiker verwijderen {#delete-a-user}

```shell
curl -u <user>:<password> -FdeleteAuthorizable= http://localhost:4502/home/users/t/testuser
```

#### Een groep verwijderen {#delete-a-group}

```shell
curl -u <user>:<password> -FdeleteAuthorizable= http://localhost:4502/home/groups/t/testGroup
```

### Back-up {#backup}

Zie [ Steun en herstel ](/help/sites-administering/backup-and-restore.md#automating-aem-online-backup) voor details.

### OSGi {#osgi}

#### Een bundel starten {#starting-a-bundle}

```shell
curl -u <user>:<password> -Faction=start http://localhost:4502/system/console/bundles/<bundle-name>
```

#### Een bundel stoppen {#stopping-a-bundle}

```shell
curl -u <user>:<password> -Faction=stop http://localhost:4502/system/console/bundles/<bundle-name>
```

### Dispatcher {#dispatcher}

#### De cache ongeldig maken {#invalidate-the-cache}

```shell
curl -H "CQ-Action: Activate" -H "CQ-Handle: /content/test-site/" -H "CQ-Path: /content/test-site/" -H "Content-Length: 0" -H "Content-Type: application/octet-stream" http://localhost:4502/dispatcher/invalidate.cache
```

#### De cache verwijderen {#evict-the-cache}

```shell
curl -H "CQ-Action: Deactivate" -H "CQ-Handle: /content/test-site/" -H "CQ-Path: /content/test-site/" -H "Content-Length: 0" -H "Content-Type: application/octet-stream" http://localhost:4502/dispatcher/invalidate.cache
```

### Replication Agent {#replication-agent}

#### Controleer de Status van een Agent {#check-the-status-of-an-agent}

```shell
curl -u <user>:<password> "http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json?agent=publish"
http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json?agent=publish
```

#### Een agent verwijderen {#delete-an-agent}

```shell
curl -X DELETE http://localhost:4502/etc/replication/agents.author/replication99 -u <user>:<password>
```

#### Een agent maken {#create-an-agent}

```shell
curl -u <user>:<password> -F "jcr:primaryType=cq:Page" -F "jcr:content/jcr:title=new-replication" -F "jcr:content/sling:resourceType=/libs/cq/replication/components/agent" -F "jcr:content/template=/libs/cq/replication/templates/agent" -F "jcr:content/transportUri=http://localhost:4503/bin/receive?sling:authRequestLogin=1" -F "jcr:content/transportUser=admin" -F "jcr:content/transportPassword={DES}8aadb625ced91ac483390ebc10640cdf"http://localhost:4502/etc/replication/agents.author/replication99
```

#### Een agent pauzeren {#pause-an-agent}

```shell
curl -u <user>:<password> -F "cmd=pause" -F "name=publish"  http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json
```

#### Wis een Rij van de Agent {#clear-an-agent-queue}

```shell
curl -u <user>:<password> -F "cmd=clear" -F "name=publish"  http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json
```

### Gemeenschappen {#communities}

#### Badges toewijzen en intrekken {#assign-and-revoke-badges}

Zie [ het Scoren en Badges van Gemeenschappen ](/help/communities/implementing-scoring.md#assign-and-revoke-badges) voor details.

Zie [ het Scoren en de Hoofdzaak van Badges ](/help/communities/configure-scoring.md#example-setup) voor details.

#### MSRP opnieuw indexeren {#msrp-reindexing}

Zie [ MSRP - Leverancier van het Middel van de Opslag MongoDB ](/help/communities/msrp.md#running-msrp-reindex-tool-using-curl-command) voor details.

### Beveiliging {#security}

#### CRX DE Lite in- en uitschakelen {#enabling-and-disabling-crx-de-lite}

Zie [ toelatend CRXDE Lite in AEM ](/help/sites-administering/enabling-crxde-lite.md) voor details.

### Opruimverzameling gegevensopslag {#data-store-garbage-collection}

Zie [ de Inzameling van het Afval van de Opslag van Gegevens ](/help/sites-administering/data-store-garbage-collection.md#automating-data-store-garbage-collection) voor details.

### Analyses en doelintegratie {#analytics-and-target-integration}

Zie [ Opting in Adobe Analytics en Adobe Target ](/help/sites-administering/opt-in.md#configuring-the-setup-and-provisioning-via-script) voor details.

### Single Sign On {#single-sign-on}

#### Testkop verzenden {#send-test-header}

Zie [ Enig Teken ](/help/sites-deploying/single-sign-on.md) voor details.

## Algemene AEM cURL-opdrachten voor Manipulatie van inhoud {#common-content-manipulation-aem-curl-commands}

Hier volgt een lijst met AEM cURL-opdrachten voor het manipuleren van inhoud.

>[!NOTE]
>
>In de volgende voorbeelden wordt ervan uitgegaan dat AEM wordt uitgevoerd op `localhost` on port `4502` en dat de gebruiker `admin` met wachtwoord `admin` wordt gebruikt. Extra plaatsaanduidingen voor opdrachten worden ingesteld tussen punthaken.

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

#### Pagina vergrendelen {#lock-page}

```shell
curl -u <user>:<password> -X POST -F cmd="lockPage" -F path="/content/path/to/page" -F "_charset_"="utf-8" http://localhost:4502/bin/wcmcommand
```

#### Pagina ontgrendelen {#unlock-page}

```shell
curl -u <user>:<password> -X POST -F cmd="unlockPage" -F path="/content/path/to/page" -F "_charset_"="utf-8" http://localhost:4502/bin/wcmcommand
```

#### Pagina kopiëren {#copy-page}

```shell
curl -u <user>:<password> -F cmd=copyPage -F destParentPath=/path/to/destination/parent -F srcPath=/path/to/source/location http://localhost:4502/bin/wcmcommand
```

### Een oppervlakkige uitrol uitvoeren {#shallow-rollout}

Als u AEM as a Cloud Service gebruikt, kan het gebeuren dat u één specifieke pagina moet implementeren zonder de subpagina&#39;s ervan te verspreiden. Als deze optie niet correct is geconfigureerd, bevat de standaardopdracht voor het uitrollen van pagina&#39;s mogelijk per ongeluk subpagina&#39;s. In deze sectie wordt beschreven hoe u de opdracht Krullen aanpast om een ondiepe rollout van een opgegeven pagina te maken en extra subpagina&#39;s uit te sluiten.

Voer de volgende stappen uit om een oppervlakkige rollout uit te voeren:

1. Wijzig de bestaande curl-opdracht door de parameter van `type=deep` in `type=page` te wijzigen.
1. Gebruik de volgende syntaxis voor de krullopdracht:

```shell
curl -H "Authorization: Bearer <token>" "https://<instance-url>/bin/asynccommand" \
   -d type=page \
   -d operation=asyncRollout \
   -d cmd=rollout \
   -d path="/content/<your-path>"
```

Controleer ook het volgende:

1. Vervang `<token>` door uw huidige verificatietoken en `<instance-url>` door uw specifieke instantie-URL.
1. Vervang `/content/<your-path>` door het pad van de specifieke pagina die u wilt uitrollen.

Door `type=page` in te stellen, richt de opdracht zich alleen op de opgegeven pagina, met uitzondering van subpagina&#39;s. Als dusdanig, laat deze configuratie nauwkeurige controle over inhoudsplaatsing toe, die ervoor zorgt dat slechts de voorgenomen veranderingen over milieu&#39;s worden verspreid. Bovendien wordt deze aanpassing ook afgestemd op de manier waarop rollouts worden beheerd via de AEM GUI bij het selecteren van afzonderlijke pagina&#39;s.

### Workflows {#workflows}

Zie [ die met Werkschema&#39;s programmatically ](/help/sites-developing/workflows-program-interaction.md) met details in wisselwerking staan.

### Inhoud verkopen {#sling-content}

#### Een map maken {#create-a-folder}

```shell
curl -u <user>:<password> -F jcr:primaryType=sling:Folder http://localhost:4502/etc/test
```

#### Een knooppunt verwijderen {#delete-a-node}

```shell
curl -u <user>:<password> -F :operation=delete http://localhost:4502/etc/test/test.properties
```

#### Een knooppunt verplaatsen {#move-a-node}

```shell
curl -u <user>:<password> -F":operation=move" -F":applyTo=/sourceurl"  -F":dest=/target/parenturl/" https://localhost:4502/content
```

#### Een knooppunt kopiëren {#copy-a-node}

```shell
curl -u <user>:<password> -F":operation=copy" -F":applyTo=/sourceurl"  -F":dest=/target/parenturl/" https://localhost:4502/content
```

#### Bestanden uploaden met Sling PostServlet {#upload-files-using-sling-postservlet}

```shell
curl -u <user>:<password> -F"*=@test.properties"  http://localhost:4502/etc/test
```

#### Bestanden uploaden met Sling PostServlet en door Node Name op te geven {#upload-files-using-sling-postservlet-and-specifying-node-name}

```shell
curl -u <user>:<password> -F"test2.properties=@test.properties"  http://localhost:4502/etc/test
```

#### Bestanden uploaden die een inhoudstype opgeven {#upload-files-specifying-a-content-type}

```shell
curl -u <user>:<password> -F "*=@test.properties;type=text/plain" http://localhost:4502/etc/test
```

### Manipulatie van middelen {#asset-manipulation}

Zie [ HTTP API van Assets ](/help/assets/mac-api-assets.md) voor details.
