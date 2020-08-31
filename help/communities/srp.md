---
title: Overzicht opslagbronprovider
seo-title: Overzicht opslagbronprovider
description: Gemeenschappelijke opslag voor de Gemeenschappen
seo-description: Gemeenschappelijke opslag voor de Gemeenschappen
uuid: abdf4e5a-767b-428f-9aa4-0dc06819a26e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 63abeda4-6ea1-4b45-b188-f9c6b44ca0cd
translation-type: tm+mt
source-git-commit: 9a4ae73c08657195da2741cccdb196bd7f7142c9
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 0%

---


# Overzicht opslagbronprovider {#storage-resource-provider-overview}

## Inleiding {#introduction}

Vanaf AEM Communities 6.1 wordt de inhoud van de gemeenschap, die algemeen als gebruiker geproduceerde inhoud (UGC) wordt bedoeld, opgeslagen in één enkele, gemeenschappelijke opslag die door een leverancier van [opslagmiddelen](working-with-srp.md) (SRP) wordt verstrekt.

Er zijn verscheidene opties SRP, die allen tot UGC door een nieuwe interface van AEM Communities, [SocialResourceProvider API](srp-and-ugc.md) (SRP API) toegang hebben, die allen creeer, lezen, bijwerken, en schrapt (CRUD) verrichtingen omvat.

Alle componenten SCF worden uitgevoerd gebruikend SRP API, toestaand code om zonder kennis van of de [onderliggende topologie](topologies.md) of plaats van UGC worden ontwikkeld.

***De API voor SocialResourceProvider is alleen beschikbaar voor klanten met een licentie van AEM Communities.***

>[!NOTE]
>
>**Aangepaste componenten**: Voor gelicentieerde klanten van AEM Communities, is SRP API beschikbaar aan ontwikkelaars van douanecomponenten voor de toegang tot van UGC ongeacht de onderliggende topologie. Zie Hoofdzaak [SRP en UGC](srp-and-ugc.md).


Zie ook:

* [SRP en de Hoofdzaak](srp-and-ugc.md) UGC - SRP nutsmethodes en voorbeelden.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md) - Afgekeurde nutsmethodes van de Afbeelding aan huidige SRP hulpprogrammamethodes.

## Informatie over de opslagplaats {#about-the-repository}

Om SRP te begrijpen, is het nuttig om de rol van de AEM bewaarplaats (OAK) in een AEM communautaire plaats te begrijpen.

**Java Content Repository (JCR)** Deze standaard definieert een gegevensmodel en een programmeerinterface voor toepassingen ([JCR API](https://jackrabbit.apache.org/jcr/jcr-api.html)) voor opslagruimten voor inhoud. Het combineert kenmerken van conventionele dossiersystemen met die van relationele gegevensbestanden, en voegt een aantal extra eigenschappen toe die inhoudstoepassingen vaak nodig hebben.

Eén implementatie van JCR is de AEM opslagplaats, OAK.

**Apache Jackrabbit Oak (OAK)**[OAK](../../help/sites-deploying/platform.md) is een implementatie van JCR 2.0. Dit is een gegevensopslagsysteem dat speciaal is ontworpen voor inhoudgerichte toepassingen. Dit is een soort hiërarchische database die is ontworpen voor ongestructureerde en semi-gestructureerde gegevens. De dataopslag slaat niet alleen de gebruikersgerichte inhoud op, maar ook alle code, sjablonen en interne gegevens die door de toepassing worden gebruikt. De interface voor het benaderen van inhoud is [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

Zowel JCR als OAK worden typisch gebruikt om naar de AEM bewaarplaats te verwijzen.

Nadat u site-inhoud hebt ontwikkeld in de omgeving van de privéauteur, moet u deze kopiëren naar de openbare publicatieomgeving. Dit wordt vaak gedaan door een verrichting genoemd *[replicatie](deploy-communities.md#replication-agents-on-author)*. Dit gebeurt onder controle van de auteur/ontwikkelaar/beheerder.

Voor UGC wordt de inhoud ingevoerd door geregistreerde sitebezoekers (leden van de community) in de publicatieomgeving van het publiek. Dit gebeurt willekeurig.

Voor beheer en rapportage is het nuttig om vanuit de omgeving van de particuliere auteur toegang tot UGC te hebben. Met SRP, is de toegang tot UGC van auteur consistenter en uitvoerender aangezien de omgekeerde replicatie van publiceren aan auteur niet noodzakelijk is.

## SRP {#about-srp}

Wanneer UGC aan gedeelde opslag wordt bewaard, is er één enkel geval van lidinhoud die, in de meeste plaatsingen, van zowel de auteur als publicatiemilieu&#39;s kan worden betreden. Ongeacht de keus SRP (MSRP, ASRP, JSRP), moeten allen programmatically met SRP API worden betreden.

>[!NOTE]
>
>Zie Hoofdzaak [SRP en UGC](srp-and-ugc.md) voor steekproefcode en extra details.
>
>Zie [Toegang tot van UGC met SRP](accessing-ugc-with-srp.md) voor beste praktijken wanneer het coderen.


### ASRP {#asrp}

In het geval van ASRP, wordt UGC niet opgeslagen in JCR, wordt het opgeslagen in de wolkendienst die door Adobe wordt ontvangen en wordt beheerd. UGC die in ASRP is opgeslagen, kan niet met CRXDE Lite worden bekeken en kan niet worden benaderd met behulp van de JCR API.

Zie [ASRP - de Leverancier](asrp.md)van het Middel van de Opslag van Adobe.

Ontwikkelaars hebben niet rechtstreeks toegang tot de UGC.

ASRP gebruikt de wolk van Adobe voor vragen.

### MSRP {#msrp}

In het geval van MSRP, wordt UGC niet opgeslagen in JCR, wordt het opgeslagen in MongoDB. UGC die is opgeslagen in MSRP kan niet worden weergegeven met CRXDE Lite en kan niet worden benaderd via de JCR API.

Zie [MSRP - de Leverancier](msrp.md)van het Middel van de Opslag MongoDB.

Terwijl MSRP aan ASRP vergelijkbaar is, aangezien alle AEM serverinstanties tot zelfde UGC toegang hebben, is het mogelijk om gemeenschappelijke hulpmiddelen te gebruiken om tot UGC direct toegang te hebben die in MongoDB wordt opgeslagen.

MSRP gebruikt Solr voor vragen.

### JSRP {#jsrp}

JSRP is de standaardleverancier voor de toegang tot van al UGC op één enkele AEM instantie. Het verstrekt de capaciteit om AEM Communities 6.1 zonder de behoefte aan vestiging MSRP of ASRP snel te ervaren.

Zie [JSRP - JCR Storage Resource Provider](jsrp.md).

In het geval van JSRP, terwijl UGC wordt opgeslagen in JCR, en toegankelijk via zowel CRXDE Lite als JCR API, wordt ten zeerste geadviseerd dat JCR API nooit wordt gebruikt om dit te doen, anders kunnen toekomstige veranderingen douanecode beïnvloeden.

Bovendien wordt de opslagplaats voor de auteur- en publicatieomgevingen niet gedeeld. Hoewel een cluster met publicatie-instanties resulteert in een gedeelde publicatierecorder, is UGC die tijdens publicatie wordt ingevoerd, niet zichtbaar voor de auteur, zodat de auteur de UGC niet kan beheren. UGC blijft alleen behouden in de AEM repository (JCR) van de instantie waarin het werd ingevoerd.

JSRP gebruikt de indexen van het Eak voor vragen.

## Informatie over schaduwknooppunten in JCR {#about-shadow-nodes-in-jcr}

Schaduwknooppunten, die het pad naar UGC nabootsen, bestaan in de lokale opslagruimte voor twee doeleinden:

1. [Toegangsbeheer (ACLs)](#for-access-control-acls)
1. [Niet-bestaande bronnen (NER&#39;s)](#for-non-existing-resources-ners)

Ongeacht de implementatie SRP, zal daadwerkelijke UGC *not zichtbaar op de zelfde plaats zoals de schaduwknoop zijn.

### Voor Toegangsbeheer (ACLs) {#for-access-control-acls}

Sommige implementaties SRP, zoals ASRP en MSRP, slaan communautaire inhoud in gegevensbestanden op die geen ACL controle verstrekken. De knopen van de schaduw verstrekken een plaats in de lokale bewaarplaats waarop ACLs kan worden toegepast.

Met de SRP API voeren alle SRP-opties dezelfde controle uit op de schaduwlocatie voorafgaand aan alle CRUD-bewerkingen.

De ACL controle gebruikt een nutsmethode die een weg geschikt voor het controleren van de toestemmingen terugkeert die op UGC van het middel worden toegepast.

Zie Hoofdzaak [SRP en UGC](srp-and-ugc.md) voor steekproefcode.

### Voor niet-bestaande bronnen (NER&#39;s) {#for-non-existing-resources-ners}

Sommige componenten van Gemeenschappen zijn inbegrepen binnen een manuscript en vereisen daarom een Sling adressable knoop om de eigenschappen van Gemeenschappen te steunen. [Opgenomen componenten](scf.md#add-or-include-a-communities-component) worden niet-bestaande bronnen (NER&#39;s) genoemd.

Schaduwknooppunten bieden een adresseerbare locatie in de opslagplaats.

>[!CAUTION]
>
>Aangezien het schaduwknooppunt meerdere toepassingen heeft, impliceert de aanwezigheid van een schaduwknooppunt *niet* dat de component een NER is.


### Opslaglocatie {#storage-location}

Hieronder ziet u een voorbeeld van een schaduwknooppunt met de component [](http://localhost:4502/content/community-components/en/comments.html) Opmerkingen in de [Community Components Guide](components-guide.md):

* De component bestaat in de lokale opslagplaats op:

   `/content/community-components/en/comments/jcr:content/content/includable/comments`

* Het corresponderende schaduwknooppunt bestaat in de lokale opslagruimte op:

   `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

Er wordt geen UGC gevonden onder het schaduwknooppunt.

Standaard worden schaduwknooppunten ingesteld op een publicatie-instantie wanneer naar de relevante substructuur wordt verwezen voor lezen of schrijven.

Als voorbeeld, veronderstel de plaatsing [MSRP](msrp.md) met een TarMK publiceert landbouwbedrijf is.

Wanneer een [lid](users.md) UGC op pub1 (opgeslagen in MongoDB) plaatst, worden de schaduwknopen gecreeerd in JCR op pub1.

De eerste keer dat de UGC op pub2 wordt gelezen, als er niets is ingesteld, is het standaardgedrag dat de schaduwknooppunten worden gemaakt.

Als u een ander gedrag wilt gebruiken dan het standaardgedrag, moet u dit instellen voor de instantie van de auteur en doorsturen naar alle publicatieinstanties. Dit is doorgaans een handmatig proces.
