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

Vanaf Adobe Experience Manager (AEM) Communities 6.1 wordt community-inhoud, die doorgaans door gebruikers gegenereerde inhoud (UGC) wordt genoemd, opgeslagen in één gemeenschappelijke opslagplaats die wordt geleverd door een [opslagbronprovider](working-with-srp.md) (SRP).

Er zijn verscheidene opties SRP, die allen tot UGC door een nieuwe interface van AEM Communities toegang hebben, [API voor SocialResourceProvider](srp-and-ugc.md) (SRP API), die alle (CRUD)-bewerkingen (create, read, update and delete) omvat.

Alle SCF componenten worden uitgevoerd gebruikend SRP API, toestaand code om zonder kennis van of te worden ontwikkeld [onderliggende topologie](topologies.md) of locatie van UGC.

***De API voor SocialResourceProvider is alleen beschikbaar voor klanten met een licentie van AEM Communities.***

>[!NOTE]
>
>**Aangepaste componenten**: Voor gelicentieerde klanten van AEM Communities, is SRP API beschikbaar aan ontwikkelaars van douanecomponenten voor de toegang tot van UGC ongeacht de onderliggende topologie. Zie [SRP en UGC Essentials](srp-and-ugc.md).

Zie ook:

* [SRP en UGC Essentials](srp-and-ugc.md) - SRP-gebruiksmethoden en -voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtsnoeren.
* [Refactoring voor sociale hulpmiddelen](socialutils.md) - Afgekeurde hulpprogrammamethoden worden toegewezen aan de huidige SRP-hulpprogrammamethoden.

## Informatie over de opslagplaats {#about-the-repository}

Om SRP te begrijpen, is het nuttig om de rol van de AEM bewaarplaats (Oak) in een AEM communautaire plaats te begrijpen.

**Java™ Content Repository (JCR)**
Deze standaard definieert een gegevensmodel en een programmeerinterface voor toepassingen ([JCR-API](https://jackrabbit.apache.org/jcr/jcr-api.html)) voor opslagplaatsen voor inhoud. Het combineert kenmerken van conventionele dossiersystemen met die van relationele gegevensbestanden, en voegt verscheidene extra eigenschappen toe die inhoudstoepassingen vaak nodig hebben.

Eén implementatie van JCR is de AEM opslagplaats, Oak.

**Apache Jackrabbit Oak**
[Eik](../../help/sites-deploying/platform.md) is een implementatie van JCR 2.0 die een gegevensopslagsysteem is dat voor inhoud-centric toepassingen wordt ontworpen. Dit is een soort hiërarchische database die is ontworpen voor ongestructureerde en semi-gestructureerde gegevens. De gegevensopslagruimte slaat niet alleen de gebruikersgerichte inhoud op, maar ook alle code, sjablonen en interne gegevens die door de toepassing worden gebruikt. De interface voor het benaderen van inhoud is [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Zowel JCR als Oak worden doorgaans gebruikt om naar de AEM opslagplaats te verwijzen.

Nadat u site-inhoud hebt ontwikkeld in de privéontwerpomgeving, moet u deze kopiëren naar de openbare publicatieomgeving. Dit gebeurt vaak via een bewerking die *[replicatie](deploy-communities.md#replication-agents-on-author)*. Dit gebeurt onder controle van de auteur/ontwikkelaar/beheerder.

Voor UGC wordt de inhoud ingevoerd door geregistreerde sitebezoekers (leden van de community) in de publicatieomgeving van het publiek. Dit gebeurt willekeurig.

Met het oog op beheer en rapportage is het nuttig om vanuit de omgeving van de particuliere auteur toegang tot UGC te hebben. Met SRP, is de toegang tot UGC van Auteur consistenter en uitvoerender aangezien de omgekeerde replicatie van Publish aan Auteur niet noodzakelijk is.

## SRP {#about-srp}

Wanneer UGC aan gedeelde opslag wordt bewaard, is er één enkel geval van lidinhoud die, in de meeste plaatsingen, van zowel de auteur als publicatiemilieu&#39;s kan worden betreden. Ongeacht de keus SRP (MSRP, ASRP, JSRP), moeten allen programmatically met SRP API worden betreden.

>[!NOTE]
>
>Zie [SRP en UGC Essentials](srp-and-ugc.md) voor de voorbeeldcode en aanvullende gegevens.
>
>Zie [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) voor beste praktijken wanneer het coderen.

### ASRP {#asrp}

Als er ASRP is, wordt UGC niet opgeslagen in JCR, wordt het opgeslagen in de wolkendienst die door Adobe wordt ontvangen en wordt beheerd. UGC die in ASRP is opgeslagen, wordt mogelijk niet weergegeven met CRXDE Lite of benaderd via de JCR API.

Zie [ASRP - Adobe Storage Resource Provider](asrp.md).

Ontwikkelaars hebben niet rechtstreeks toegang tot de UGC.

ASRP gebruikt de wolk van de Adobe voor vragen.

### MSRP {#msrp}

Als er is, MSRP, wordt UGC niet opgeslagen in JCR, wordt het opgeslagen in MongoDB. UGC die in MSRP wordt opgeslagen kan niet met CRXDE Lite worden bekeken of worden betreden gebruikend JCR API.

Zie [MSRP - MongoDB Storage Resource Provider](msrp.md).

Terwijl MSRP aan ASRP vergelijkbaar is, aangezien alle AEM serverinstanties tot zelfde UGC toegang hebben, is het mogelijk om gemeenschappelijke hulpmiddelen te gebruiken om tot UGC direct toegang te hebben die in MongoDB wordt opgeslagen.

MSRP gebruikt Solr voor vragen.

### JSRP {#jsrp}

JSRP is de standaardleverancier voor de toegang tot van al UGC op één enkele AEM instantie. Het laat u snel AEM Communities 6.1 zonder de behoefte ervaren om opstelling MSRP of ASRP.

Zie [JSRP - JCR Storage Resource Provider](jsrp.md).

Als er JSRP is terwijl UGC wordt opgeslagen in JCR, en het toegankelijk is in CRXDE Lite en JCR API, adviseert de Adobe dat u nooit JCR API gebruikt om dit te doen. Als u dit doet, kunnen toekomstige wijzigingen van invloed zijn op aangepaste code.

Bovendien wordt de opslagplaats voor de auteur- en publicatie-omgevingen niet gedeeld. Hoewel een cluster met publicatie-instanties resulteert in een gedeelde publicatieruimte, is UGC die u hebt ingevoerd bij Publiceren niet zichtbaar op Auteur, zodat de UGC niet door de auteur kan worden beheerd. UGC blijft alleen behouden in de AEM repository (JCR) van de instantie waarin het werd ingevoerd.

JSRP gebruikt de indexen van het Eak voor vragen.

## Informatie over schaduwknooppunten in JCR {#about-shadow-nodes-in-jcr}

Schaduwknooppunten, die het pad naar UGC nabootsen, bestaan in de lokale opslagruimte voor twee doeleinden:

1. [Toegangsbeheer (ACLs)](#for-access-control-acls)
1. [Niet-bestaande bronnen (NER&#39;s)](#for-non-existing-resources-ners)

Ongeacht de implementatie SRP, is daadwerkelijke UGC *niet* zichtbaar op dezelfde locatie als het schaduwknooppunt.

### Voor Toegangsbeheer (ACLs) {#for-access-control-acls}

Sommige implementaties SRP, zoals ASRP en MSRP, slaan communautaire inhoud in gegevensbestanden op die geen ACL controle verstrekken. De knopen van de schaduw verstrekken een plaats in de lokale bewaarplaats waarop ACLs kan worden toegepast.

Met de SRP API voeren alle SRP-opties dezelfde controle uit op de schaduwlocatie vóór alle CRUD-bewerkingen.

De ACL controle gebruikt een nutsmethode die een weg geschikt voor het controleren van de toestemmingen terugkeert die op UGC van het middel worden toegepast.

Zie [SRP en UGC Essentials](srp-and-ugc.md) voor voorbeeldcode.

### Voor niet-bestaande bronnen (NER&#39;s) {#for-non-existing-resources-ners}

Sommige componenten van Gemeenschappen zijn inbegrepen binnen een manuscript en vereisen daarom een Sling adressable knoop om de eigenschappen van Gemeenschappen te steunen. [Opgenomen onderdelen](scf.md#add-or-include-a-communities-component) worden niet-bestaande middelen (NER&#39;s) genoemd.

Schaduwknooppunten bieden een adresseerbare locatie in de opslagplaats.

>[!CAUTION]
>
>Aangezien het schaduwknooppunt meerdere toepassingen heeft, doet de aanwezigheid van een schaduwknooppunt dat *niet* impliceren dat de component NER is.

### Opslaglocatie {#storage-location}

Hieronder ziet u een voorbeeld van een schaduwknooppunt, waarbij u de opdracht [Component Opmerkingen](http://localhost:4502/content/community-components/en/comments.html) in de [Community Components Guide](components-guide.md):

* De component bestaat in de lokale opslagplaats op:

  `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Het corresponderende schaduwknooppunt bestaat in de lokale opslagruimte op:

  `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Er is geen UGC gevonden onder het schaduwknooppunt.

Standaard worden schaduwknooppunten ingesteld op een publicatie-instantie wanneer naar de relevante substructuur wordt verwezen voor lezen of schrijven.

Stel dat de implementatie [MSRP](msrp.md) met een TarMK-publicatiebedrijf.

Wanneer een [lid](users.md) Hiermee wordt UGC op pub1 geplaatst (opgeslagen in MongoDB), worden schaduwknooppunten gemaakt in JCR op pub1.

De eerste keer dat de UGC op pub2 wordt gelezen, als er niets is ingesteld, is het standaardgedrag dat de schaduwknooppunten worden gemaakt.

Als u een ander gedrag wilt gebruiken dan het standaardgedrag, moet u dit instellen voor de instantie van de auteur en doorsturen naar alle publicatie-instanties. Dit is doorgaans een handmatig proces.
