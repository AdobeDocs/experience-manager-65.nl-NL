---
title: SRP en UGC Essentials
description: Overzicht van opslagbronnen en door de gebruiker gegenereerde inhoud
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 8279684f-23dd-4234-bf01-fd2ce74bcb4e
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# SRP en UGC Essentials {#srp-and-ugc-essentials}

## Inleiding {#introduction}

Als onbekend met de leverancier van het opslagmiddel (SRP) en zijn verhouding aan gebruiker-geproduceerde inhoud (UGC), bezoek {de Opslag van de Inhoud van de Gemeenschap 1} en [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md).[&#128279;](working-with-srp.md)

Deze sectie van de documentatie verstrekt wat essentiële informatie over SRP en UGC.

## StorageResourceProvider API {#storageresourceprovider-api}

De API van SocialResourceProvider (SRP API) is een uitbreiding van diverse API&#39;s van Sling Resource Provider. Het omvat steun voor paginering en atoomverhoging (nuttig voor tally en scoring).

Vragen zijn noodzakelijk voor componenten SCF aangezien er de behoefte is om door datum, nuttigheid, aantal stemmen, etc. te sorteren. Alle opties SRP hebben flexibele vraagmechanismen die zich niet op het knippen baseren.

De opslagplaats SRP neemt de componentenweg op. SRP API zou altijd moeten worden gebruikt om tot UGC toegang te hebben aangezien de wortelweg van de geselecteerde optie SRP, zoals ASRP, MSRP, of JSRP afhangt.

SRP API is geen abstracte klasse, het is een interface. Een aangepaste implementatie moet niet lichtvaardig worden uitgevoerd, aangezien de voordelen van toekomstige verbeteringen van interne implementaties niet worden benut wanneer een upgrade naar een nieuwe release wordt uitgevoerd.

De middelen om SRP API te gebruiken zijn door verstrekte nut, zoals die gevonden in het pakket SocialResourceUtilities.

Wanneer het bevorderen van AEM 6.0 of vroeger, zal het noodzakelijk zijn om UGC voor alle SRPs te migreren, waarvoor een Open hulpmiddel van Source beschikbaar is. Zie [ Bevorderend aan AEM Communities 6.3 ](upgrade.md).

>[!NOTE]
>
>Historisch, werden de nut voor de toegang tot van UGC gevonden in het pakket SocialUtils, dat niet meer bestaat.
>
>Voor vervangingsnut, zie [ Refactoring SocialUtils ](socialutils.md).

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

Voor andere vervangingen SocialUtils, zie [ Refactoring SocialUtils ](socialutils.md).

Voor coderingsrichtsnoeren, bezoek [ Toegang tot UGC met SRP ](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>De weg resourceToUGCStoragePath () keert is *niet* geschikt voor [ ACL die ](srp.md#for-access-control-acls) controleert.

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
>De weg die door resourceToACLPath () is teruggekeerd is *niet* geschikt voor [ de toegang tot van UGC ](#utility-method-to-access-acls) zelf.

## UGC-gerelateerde opslaglocaties {#ugc-related-storage-locations}

De volgende beschrijvingen van opslagplaats kunnen van hulp zijn wanneer het ontwikkelen met JSRP of misschien MSRP. Er is momenteel geen UI om tot UGC toegang te hebben die in ASRP wordt opgeslagen, aangezien er voor JSRP ([ CRXDE Lite ](../../help/sites-developing/developing-with-crxde-lite.md)) en MSRP (hulpmiddelen MongoDB) is.

**plaats van de Component**

Wanneer een lid UGC in het publicatiemilieu ingaat, communiceren zij met een component als deel van een AEM plaats.

Een voorbeeld van zulk een component is de [ commentaarcomponent ](http://localhost:4502/content/community-components/en/comments.html) die in de [ Communautaire Plaats van de Gids van Componenten ](components-guide.md) bestaat. Het pad naar het knooppunt met opmerkingen in de lokale opslagplaats is:

* Component path = `/content/community-components/en/comments/jcr:content/content/includable/comments`

**de knoopplaats van de Schaduw**

De verwezenlijking van UGC leidt ook tot de knoop van de a [ schaduw ](srp.md#about-shadow-nodes-in-jcr) waarop noodzakelijke ACLs wordt toegepast. Het pad naar het corresponderende schaduwknooppunt in de lokale opslagruimte is het resultaat van het voorzetten van het hoofdpad van het schaduwknooppunt naar het componentpad:

* Basispad = `/content/usergenerated`
* Commentaar schaduwknooppunt = `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

**plaats UGC**

UGC wordt gecreeerd in geen van die plaatsen, en zou slechts moeten worden betreden gebruikend een [ nutsmethode ](#utility-method-to-access-ugc) die SRP API aanhaalt.

* Basispad = `/content/usergenerated/asi/srp-choice`
* UGC-knooppunt voor JSRP = `/content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/includable/comments/srzd-let_it_be_`

*ben zich bewust*, voor JSRP, zal de knoop UGC *slechts* op de AEM instantie (of auteur of publiceert) aanwezig zijn waarop het was ingegaan. Als ingegaan op een publiceer instantie, zal de matiging niet van de moderatieconsole op auteur mogelijk zijn.

## Gerelateerde informatie {#related-information}

* [ Overzicht van de Leverancier van het Middel van de Opslag ](srp.md) - Inleiding en overzicht van het opslagruimtegebruik.
* [ die tot UGC met SRP ](accessing-ugc-with-srp.md) toegang hebben - de richtlijnen van de Codering.
* [ SocialUtils Refactoring ](socialutils.md) - de Afgekeurde nutsmethodes van de afbeelding aan huidige SRP hulpprogrammamethodes.
