---
title: SRP en UGC Essentials
seo-title: SRP en UGC Essentials
description: Overzicht van opslagbronnen en door de gebruiker gegenereerde inhoud
seo-description: Overzicht van opslagbronnen en door de gebruiker gegenereerde inhoud
uuid: a4ee8725-f554-4fcf-ac1e-34878d6c02f8
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0763f236-5648-49e9-8a24-dbc8f4c77ee3
translation-type: tm+mt
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# SRP en UGC Essentials {#srp-and-ugc-essentials}

## Inleiding {#introduction}

Als de leverancier van het opslagmiddel (SRP) en zijn verhouding aan gebruiker-geproduceerde inhoud (UGC) onbekend zijn, bezoek [Communautair Overzicht](working-with-srp.md) van de Opslag [van de Inhoud en van de Leverancier van het Middel van de](srp.md)Opslag.

Deze sectie van de documentatie verstrekt wat essentiële informatie over SRP en UGC.

## StorageResourceProvider API {#storageresourceprovider-api}

De API van SocialResourceProvider (SRP API) is een uitbreiding van diverse API&#39;s van Sling Resource Provider. Het omvat steun voor paginering en atoomverhoging (nuttig voor tally en scoring).

Vragen zijn noodzakelijk voor componenten SCF aangezien er de behoefte is om door datum, nuttigheid, aantal stemmen, etc. te sorteren. Alle opties SRP hebben flexibele vraagmechanismen die zich niet op het knippen baseren.

De opslagplaats SRP neemt de componentenweg op. SRP API zou altijd moeten worden gebruikt om tot UGC toegang te hebben aangezien de wortelweg van de geselecteerde optie SRP, zoals ASRP, MSRP, of JSRP afhangt.

SRP API is geen abstracte klasse, het is een interface. Een aangepaste implementatie moet niet lichtvaardig worden uitgevoerd, aangezien de voordelen van toekomstige verbeteringen van interne implementaties niet worden benut bij de upgrade naar een nieuwe release.

De middelen om SRP API te gebruiken zijn door verstrekte nut, zoals die gevonden in het pakket SocialResourceUtilities.

Wanneer het bevorderen van AEM 6.0 of vroeger, zal het noodzakelijk zijn om UGC voor alle SRPs te migreren, waarvoor een Open Bron hulpmiddel beschikbaar is. Zie [Bijwerken naar AEM-gemeenschappen 6.3](upgrade.md).

>[!NOTE]
>
>Historisch, werden de nut voor de toegang tot van UGC gevonden in het pakket SocialUtils, dat niet meer bestaat.
>
>Voor vervangingsnut, zie Refactoring [SocialUtils](socialutils.md).


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

Voor andere vervangingen SocialUtils, zie Refactoring [SocialUtils](socialutils.md).

Voor coderingsrichtlijnen, bezoek de [Toegang tot van UGC met SRP](accessing-ugc-with-srp.md).

>[!CAUTION]
>
>De weg resourceToUGCStoragePath () keert is *niet* geschikt voor [ACL het controleren](srp.md#for-access-control-acls)terug.


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
>Het pad dat door resourceToACLPath() wordt geretourneerd, is *niet* geschikt voor [toegang tot de UGC](#utility-method-to-access-acls) zelf.


## UGC-gerelateerde opslaglocaties {#ugc-related-storage-locations}

De volgende beschrijvingen van opslagplaats kunnen van hulp zijn wanneer het ontwikkelen met JSRP of misschien MSRP. Er is momenteel geen UI om tot UGC toegang te hebben die in ASRP wordt opgeslagen, aangezien er voor JSRP ([CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)) en MSRP (hulpmiddelen MongoDB) is.

**componentlocatie**

Wanneer een lid UGC in het publicatiemilieu ingaat, communiceren zij met een component als deel van een plaats AEM.

Een voorbeeld van een dergelijke component is de [commentaarcomponent](http://localhost:4502/content/community-components/en/comments.html) die aanwezig is op de site [Community Components Guide](components-guide.md) . Het pad naar het knooppunt met opmerkingen in de lokale opslagplaats is:

* Componentpad = `/content/community-components/en/comments/jcr:content/content/includable/comments`

**locatie van schaduwknooppunten**

De verwezenlijking van UGC leidt ook tot een [schaduwknoop](srp.md#about-shadow-nodes-in-jcr) waarop noodzakelijke ACLs wordt toegepast. Het pad naar het corresponderende schaduwknooppunt in de lokale opslagruimte is het resultaat van het voorzetten van het hoofdpad van het schaduwknooppunt naar het componentpad:

* Basispad = `/content/usergenerated`
* Commentaar schaduwknooppunt = `/content/usergenerated/content/community-components/en/comments/jcr:content/content/includable/comments`

**UGC-locatie**

UGC wordt gecreeerd in geen van die plaatsen, en zou slechts moeten worden betreden gebruikend een [nutsmethode](#utility-method-to-access-ugc) die SRP API aanhaalt.

* Basispad = `/content/usergenerated/asi/srp-choice`
* UGC-knooppunt voor JSRP = `/content/usergenerated/asi/jcr/content/community-components/en/comments/jcr:content/content/includable/comments/srzd-let_it_be_`

*Houd er rekening mee* dat voor JSRP het UGC-knooppunt *alleen* aanwezig is in de AEM-instantie (auteur of publicatie) waarop het knooppunt is ingevoerd. Als ingegaan op een publiceer instantie, zal de matiging niet van de moderatieconsole op auteur mogelijk zijn.

## Gerelateerde informatie {#related-information}

* [Overzicht](srp.md) van Storage Resource Provider - Inleiding en overzicht van het opslaggebruik.
* [Toegang tot UGC met SRP](accessing-ugc-with-srp.md) - Coderingsrichtlijnen.
* [SocialUtils Refactoring](socialutils.md) - Afgekeurde nutsmethodes van de Afbeelding aan huidige SRP hulpprogrammamethodes.

