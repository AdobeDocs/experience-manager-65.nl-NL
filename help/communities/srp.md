---
title: Overzicht opslagbronprovider
description: Leer hoe de communautaire inhoud, die als gebruiker-geproduceerde inhoud (UGC) wordt bekend, in een eenvoudige, gemeenschappelijke opslag wordt opgeslagen die door een leverancier van opslagmiddelen (SRP) wordt verstrekt.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 5f313274-1a2a-4e83-9289-60a4729b99b4
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---

# Overzicht opslagbronprovider {#storage-resource-provider-overview}

## Inleiding {#introduction}

Vanaf Adobe Experience Manager (AEM) Communities 6.1, communautaire inhoud, die algemeen als gebruiker-geproduceerde inhoud (UGC) wordt bedoeld, wordt opgeslagen in één enkele, gemeenschappelijke opslag die door de leverancier van het a [ opslagmiddel ](working-with-srp.md) (SRP) wordt verstrekt.

Er zijn verscheidene opties SRP, allen die tot UGC door een nieuwe interface van AEM Communities toegang hebben, [ SocialResourceProvider API ](srp-and-ugc.md) (SRP API), die allen creeert, leest, update, en schrapt (CRUD) verrichtingen omvat.

Alle componenten SCF worden uitgevoerd gebruikend SRP API, toestaand code om zonder kennis van of de [ onderliggende topologie ](topologies.md) of plaats van UGC worden ontwikkeld.

***SocialResourceProvider API is beschikbaar slechts aan erkende klanten van AEM Communities.***

>[!NOTE]
>
>**Componenten van de Douane**: Voor erkende klanten van AEM Communities, is SRP API beschikbaar aan ontwikkelaars van douanecomponenten voor de toegang tot van UGC zonder rekening te houden met de onderliggende topologie. Zie [ SRP en Hoofdzaak UGC ](srp-and-ugc.md).

Zie ook:

* [ SRP en Hoofdzaak UGC ](srp-and-ugc.md) - de nutsmethodes en voorbeelden van SRP.
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [ SocialUtils Refactoring ](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.

## Informatie over de opslagplaats {#about-the-repository}

Om SRP te begrijpen, is het nuttig om de rol van de AEM bewaarplaats (Oak) in een AEM communautaire plaats te begrijpen.

**Java™ Content Repository (JCR)**
Deze norm bepaalt een gegevensmodel en toepassing programmeringsinterface ([ JCR API ](https://jackrabbit.apache.org/jcr/jcr-api.html)) voor inhoudsbewaarplaatsen. Het combineert kenmerken van conventionele dossiersystemen met die van relationele gegevensbestanden, en voegt verscheidene extra eigenschappen toe die inhoudstoepassingen vaak nodig hebben.

Eén implementatie van JCR is de AEM opslagplaats, Oak.

**Apache Jackrabbit Oak**
[ Oak ](../../help/sites-deploying/platform.md) is een implementatie van JCR 2.0 die een systeem van de gegevensopslag is dat voor inhoud-centric toepassingen wordt ontworpen. Dit is een soort hiërarchische database die is ontworpen voor ongestructureerde en semi-gestructureerde gegevens. De gegevensopslagruimte slaat niet alleen de gebruikersgerichte inhoud op, maar ook alle code, sjablonen en interne gegevens die door de toepassing worden gebruikt. UI voor de toegang tot van inhoud is [ CRXDE Lite ](../../help/sites-developing/developing-with-crxde-lite.md).

Zowel JCR als Oak worden doorgaans gebruikt om naar de AEM repository te verwijzen.

Nadat u site-inhoud hebt ontwikkeld in de privéontwerpomgeving, moet u deze kopiëren naar de openbare publicatieomgeving. Dit wordt vaak gedaan door een verrichting genoemd *[replicatie](deploy-communities.md#replication-agents-on-author)*. Dit gebeurt onder controle van de auteur/ontwikkelaar/beheerder.

Voor UGC wordt de inhoud ingevoerd door geregistreerde sitebezoekers (leden van de community) in de publicatieomgeving van het publiek. Dit gebeurt willekeurig.

Met het oog op beheer en rapportage is het nuttig om vanuit de omgeving van de particuliere auteur toegang tot UGC te hebben. Met SRP, is de toegang tot UGC van Auteur consistenter en krachtiger aangezien omgekeerde replicatie van Publish aan Auteur niet noodzakelijk is.

## SRP {#about-srp}

Wanneer UGC aan gedeelde opslag wordt bewaard, is er één enkel geval van lidinhoud die, in de meeste plaatsingen, van zowel de auteur als publicatiemilieu&#39;s kan worden betreden. Ongeacht de keus SRP (MSRP, ASRP, JSRP), moeten allen programmatically met SRP API worden betreden.

>[!NOTE]
>
>Zie [ SRP en de Hoofdzaak UGC ](srp-and-ugc.md) voor steekproefcode en extra details.
>
>Zie [ Toegang hebbend tot UGC met SRP ](accessing-ugc-with-srp.md) voor beste praktijken wanneer het coderen.

### ASRP {#asrp}

Als er ASRP is, wordt UGC niet opgeslagen in JCR, wordt het opgeslagen in de wolkendienst die door Adobe wordt ontvangen en wordt beheerd. UGC die in ASRP is opgeslagen, wordt mogelijk niet weergegeven met CRXDE Lite of benaderd via de JCR API.

Zie [ ASRP - de Leverancier van het Middel van de Opslag van de Adobe ](asrp.md).

Ontwikkelaars hebben niet rechtstreeks toegang tot de UGC.

ASRP gebruikt de wolk van de Adobe voor vragen.

### MSRP {#msrp}

Als er is, MSRP, wordt UGC niet opgeslagen in JCR, wordt het opgeslagen in MongoDB. UGC die in MSRP wordt opgeslagen kan niet met CRXDE Lite worden bekeken of worden betreden gebruikend JCR API.

Zie [ MSRP - Leverancier van het Middel van de Opslag MongoDB ](msrp.md).

Terwijl MSRP aan ASRP vergelijkbaar is, aangezien alle AEM serverinstanties tot zelfde UGC toegang hebben, is het mogelijk om gemeenschappelijke hulpmiddelen te gebruiken om tot UGC direct toegang te hebben die in MongoDB wordt opgeslagen.

MSRP gebruikt Solr voor vragen.

### JSRP {#jsrp}

JSRP is de standaardleverancier voor de toegang tot van al UGC op één enkele AEM instantie. Het laat u snel AEM Communities 6.1 zonder de behoefte ervaren om opstelling MSRP of ASRP.

Zie [ JSRP - Leverancier van het Middel van de Opslag JCR ](jsrp.md).

Als er JSRP is terwijl UGC wordt opgeslagen in JCR, en het toegankelijk is in CRXDE Lite en JCR API, adviseert de Adobe dat u nooit JCR API gebruikt om dit te doen. Als u dit doet, kunnen toekomstige wijzigingen van invloed zijn op aangepaste code.

Bovendien wordt de opslagplaats voor de auteur- en Publish-omgevingen niet gedeeld. Hoewel een cluster met publicatie-instanties resulteert in een gedeelde publicatieruimte, is UGC die op Publish is ingevoerd niet zichtbaar op de auteur en kan UGC dus niet door de auteur worden beheerd. UGC blijft alleen behouden in de AEM repository (JCR) van de instantie waarin het werd ingevoerd.

JSRP gebruikt de indexen van Oak voor vragen.

## Informatie over schaduwknooppunten in JCR {#about-shadow-nodes-in-jcr}

Schaduwknooppunten, die het pad naar UGC nabootsen, bestaan in de lokale opslagruimte voor twee doeleinden:

1. [Toegangsbeheer (ACLs)](#for-access-control-acls)
1. [Niet-bestaande bronnen (NER&#39;s)](#for-non-existing-resources-ners)

Ongeacht implementatie SRP, is daadwerkelijke UGC *niet* zichtbaar bij de zelfde plaats zoals de schaduwknoop.

### Voor Toegangsbeheer (ACLs) {#for-access-control-acls}

Sommige implementaties SRP, zoals ASRP en MSRP, slaan communautaire inhoud in gegevensbestanden op die geen ACL controle verstrekken. De knopen van de schaduw verstrekken een plaats in de lokale bewaarplaats waarop ACLs kan worden toegepast.

Met de SRP API voeren alle SRP-opties dezelfde controle uit op de schaduwlocatie vóór alle CRUD-bewerkingen.

De ACL controle gebruikt een nutsmethode die een weg geschikt voor het controleren van de toestemmingen terugkeert die op UGC van het middel worden toegepast.

Zie [ SRP en de Hoofdzaak UGC ](srp-and-ugc.md) voor steekproefcode.

### Voor niet-bestaande bronnen (NER&#39;s) {#for-non-existing-resources-ners}

Sommige componenten van Gemeenschappen zijn inbegrepen binnen een manuscript en vereisen daarom een Sling adressable knoop om de eigenschappen van Gemeenschappen te steunen. [ omvatten componenten ](scf.md#add-or-include-a-communities-component) wordt bedoeld als niet bestaande middelen (NERs).

Schaduwknooppunten bieden een adresseerbare locatie in de opslagplaats.

>[!CAUTION]
>
>Aangezien de schaduwknoop veelvoudige toepassingen heeft, impliceert de aanwezigheid van een schaduwknoop *niet* dat de component NER is.

### Opslaglocatie {#storage-location}

Na is een voorbeeld van een schaduwknoop, gebruikend de [ component van Commentaren ](http://localhost:4502/content/community-components/en/comments.html) in de [ Communautaire Gids van Componenten ](components-guide.md):

* De component bestaat in de lokale opslagplaats op:

  `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Het corresponderende schaduwknooppunt bestaat in de lokale opslagruimte op:

  `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Er is geen UGC gevonden onder het schaduwknooppunt.

Standaard worden schaduwknooppunten ingesteld op een publicatie-instantie wanneer naar de relevante substructuur wordt verwezen voor lezen of schrijven.

Als voorbeeld, veronderstel dat de plaatsing [ MSRP ](msrp.md) met TarMK is publiceert landbouwbedrijf.

Wanneer a [ lid ](users.md) UGC op pub1 (opgeslagen in MongoDB) post, worden de schaduwknopen gecreeerd in JCR op pub1.

De eerste keer dat de UGC op pub2 wordt gelezen, als er niets is ingesteld, is het standaardgedrag dat de schaduwknooppunten worden gemaakt.

Als u een ander gedrag wilt gebruiken dan het standaardgedrag, moet u dit instellen voor de instantie van de auteur en doorsturen naar alle publicatie-instanties. Dit is doorgaans een handmatig proces.
