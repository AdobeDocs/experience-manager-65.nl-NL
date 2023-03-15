---
title: SRP en UGC Essentials
seo-title: SRP and UGC Essentials
description: Overzicht van opslagbronnen en door de gebruiker gegenereerde inhoud
seo-description: Storage resource provider and user-generated content overview
uuid: a4ee8725-f554-4fcf-ac1e-34878d6c02f8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0763f236-5648-49e9-8a24-dbc8f4c77ee3
exl-id: 8279684f-23dd-4234-bf01-fd2ce74bcb4e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# SRP en UGC Essentials {#srp-and-ugc-essentials}

## Inleiding {#introduction}

Als u niet bekend bent met de opslagbronprovider (SRP) en de relatie met door de gebruiker gegenereerde inhoud (UGC), gaat u naar [Opslag van communautaire inhoud](working-with-srp.md) en [Overzicht opslagbronprovider](srp.md).

Deze sectie van de documentatie verstrekt wat essentiële informatie over SRP en UGC.

## StorageResourceProvider API {#storageresourceprovider-api}

De API van SocialResourceProvider (SRP API) is een uitbreiding van diverse API&#39;s van Sling Resource Provider. Het omvat steun voor paginering en atoomverhoging (nuttig voor tally en scoring).

Vragen zijn noodzakelijk voor componenten SCF aangezien er de behoefte is om door datum, nuttigheid, aantal stemmen, etc. te sorteren. Alle opties SRP hebben flexibele vraagmechanismen die zich niet op het knippen baseren.

De opslagplaats SRP neemt de componentenweg op. SRP API zou altijd moeten worden gebruikt om tot UGC toegang te hebben aangezien de wortelweg van de geselecteerde optie SRP, zoals ASRP, MSRP, of JSRP afhangt.

SRP API is geen abstracte klasse, het is een interface. Een aangepaste implementatie moet niet lichtvaardig worden uitgevoerd, aangezien de voordelen van toekomstige verbeteringen van interne implementaties niet worden benut bij de upgrade naar een nieuwe release.

De middelen om SRP API te gebruiken zijn door verstrekte nut, zoals die gevonden in het pakket SocialResourceUtilities.

Wanneer het bevorderen van AEM 6.0 of vroeger, zal het noodzakelijk zijn om UGC voor alle SRPs te migreren, waarvoor een Open Bron hulpmiddel beschikbaar is. Zie [Upgrade uitvoeren naar AEM Communities 6.3](upgrade.md).

>[!NOTE]
>
>Historisch, werden de nut voor de toegang tot van UGC gevonden in het pakket SocialUtils, dat niet meer bestaat.
>
>Voor vervangingshulpprogramma&#39;s raadpleegt u [SocialUtils Refactoring](socialutils.md).

## Hulpprogrammamethode voor toegang tot UGC {#utility-method-to-access-ugc}

Om tot UGC toegang te hebben, gebruik een methode van het pakket SocialResourceUtilities dat een weg geschikt voor de toegang tot van UGC van SRP terugkeert en de vervangen methode vervangt die in het pakket SocialUtils wordt gevonden.

Hieronder ziet u een minimaal voorbeeld van het gebruik van de methode resourceToUGCStoragePath() in een servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String ugcPath = socialResourceUtilities.resourceToUGCStoragePath(request.getResource());
  // rest of servlet
}
```

Voor andere vervangingen van SocialUtils, zie [SocialUtils Refactoring](socialutils.md).

Voor coderingsrichtlijnen gaat u naar [Toegang tot UGC met SRP](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>De path resourceToUGCStoragePath() retourneert is *niet* geschikt voor [ACL-controle](srp.md#for-access-control-acls).

## De Methode van het nut om tot ACLs toegang te hebben {#utility-method-to-access-acls}

Sommige implementaties SRP, zoals ASRP en MSRP, slaan communautaire inhoud in gegevensbestanden op die geen ACL controle verstrekken. De knopen van de schaduw verstrekken een plaats in de lokale bewaarplaats waarop ACLs kan worden toegepast.

Met de SRP API voeren alle SRP-opties dezelfde controle uit op de schaduwlocatie voorafgaand aan alle CRUD-bewerkingen.

Om ACLs te controleren, gebruik een methode die een weg geschikt voor het controleren van de toestemmingen terugkeert die op UGC van het middel worden toegepast.

Hieronder ziet u een eenvoudig voorbeeld van het gebruik van de methode resourceToACLPath() in een servlet:

```java
import com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities;

@Reference
private SocialResourceUtilities socialResourceUtilities;

@Override
protected void doGet(final SlingHttpServletRequest request, final SlingHttpServletResponse response) throws ServletException, IOException {
  String aclPath = socialResourceUtilities.resourceToACLPath(request.getResource());
  // rest of servlet
}
```

>[!CAUTION]
>
>Het pad dat door resourceToACLPath() wordt geretourneerd, is *niet* geschikt voor [toegang tot UGC](#utility-method-to-access-acls) zelf.

## UGC-gerelateerde opslaglocaties {#ugc-related-storage-locations}

De volgende beschrijvingen van opslagplaats kunnen van hulp zijn wanneer het ontwikkelen met JSRP of misschien MSRP. Er is momenteel geen UI om tot UGC toegang te hebben die in ASRP wordt opgeslagen, aangezien er voor JSRP is ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) en MSRP (MongoDB-gereedschappen).

**Locatie van component**

Wanneer een lid UGC in het publicatiemilieu ingaat, communiceren zij met een component als deel van een AEM plaats.

Een voorbeeld van een dergelijke component is de component [component comments](http://localhost:4502/content/community-components/en/comments.html) die in het [Community Components Guide](components-guide.md) site. Het pad naar het knooppunt met opmerkingen in de lokale opslagplaats is:

* Componentpad = `/content/community-components/en/comments/jcr:content/content/includable/comments`

**Locatie schaduwknooppunt**

De oprichting van UGC leidt ook tot een [schaduwknooppunt](srp.md#about-shadow-nodes-in-jcr) waarop noodzakelijke ACLs wordt toegepast. Het pad naar het corresponderende schaduwknooppunt in de lokale opslagruimte is het resultaat van het voorzetten van het hoofdpad van het schaduwknooppunt naar het componentpad:

* Basispad = `/content/usergenerated`
* Commentaar schaduwknooppunt = `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

**UGC-locatie**

De UGC wordt gecreeerd in geen van beide plaatsen, en zou slechts moeten worden betreden gebruikend [hulpprogrammamethode](#utility-method-to-access-ugc) die de SRP API aanroept.

* Basispad = `/content/usergenerated/asi/srp-choice`
* UGC-knooppunt voor JSRP = `/content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/includable/comments/srzd-let_it_be_`

*Wees voorzichtig*, voor JSRP, zal de knoop UGC *alleen* aanwezig zijn op het AEM (auteur of publicatie) waarop het is ingevoerd. Als ingegaan op een publiceer instantie, zal de matiging niet van de moderatieconsole op auteur mogelijk zijn.

## Gerelateerde informatie {#related-information}

* [Overzicht opslagbronprovider](srp.md) - Inleiding en overzicht van het gebruik van de opslagplaats.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtsnoeren.
* [SocialUtils Refactoring](socialutils.md) - Afgekeurde hulpprogrammamethoden worden toegewezen aan de huidige SRP-hulpprogrammamethoden.
