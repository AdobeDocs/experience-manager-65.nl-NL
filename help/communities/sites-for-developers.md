---
title: Essentiële elementen voor community-sites
description: Websites exporteren en verwijderen en aangepaste sitesjablonen maken
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 1dc568cd-315c-4944-9a3e-e5d7794e5dc0
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Essentiële elementen voor community-sites {#community-site-essentials}

## Aangepaste sitesjabloon {#custom-site-template}

Een malplaatje van de douaneplaats kan voor elke taalexemplaar van een communautaire plaats afzonderlijk worden gespecificeerd.

Daartoe:

* Een aangepaste sjabloon maken.
* Bedek het standaardsjabloonpad van de site.
* Voeg de aangepaste sjabloon toe aan het overlaypad.
* Geef de aangepaste sjabloon op door een `page-template` eigenschap aan de `configuration` knooppunt.

**Standaardsjabloon**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Aangepaste sjabloon in overlaypad**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Eigenschap**: page-template

**Type**: String

**Waarde**: `template-name` (geen extensie)

**Configuration-knooppunt**:

`/content/community site path/lang/configuration`

Bijvoorbeeld: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle knooppunten in het bovenliggende pad hoeven alleen van het type te zijn `Folder`.

>[!CAUTION]
>
>Als de aangepaste sjabloon de naam krijgt *sitepage.hbs*, dan worden alle communautaire plaatsen aangepast.

### Voorbeeld van aangepaste sitesjabloon {#custom-site-template-example}

Als voorbeeld: `vertical-sitepage.hbs` is een sitesjabloon dat leidt tot de plaatsing van menukoppelingen verticaal onder de linkerzijde van de pagina in plaats van horizontaal onder de banner.

[Bestand ophalen](assets/vertical-sitepage.hbs)
Plaats de sjabloon voor de aangepaste site in de overlaymap:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identificeer het douanemalplaatje door een `page-template` eigenschap voor het configuratieknooppunt:

`/content/sites/sample/en/configuration`

![crxde-siteconfiguration](assets/crxde-siteconfiguration.png)

Zorg ervoor dat u **Alles opslaan** en repliceer douanecode aan alle instanties van Adobe Experience Manager (AEM) (de douanecode is niet inbegrepen wanneer de inhoud van de communautaire plaats van de console wordt gepubliceerd).

Voor het repliceren van aangepaste code wordt het volgende aanbevolen: [een pakket maken](../../help/sites-administering/package-manager.md#creating-a-new-package) en implementeren.

## Een communautaire site exporteren {#exporting-a-community-site}

Wanneer een communitysite is gemaakt, kan de site worden geëxporteerd als een AEM pakket dat is opgeslagen in Package Manager en dat beschikbaar is voor downloaden en uploaden.

Dit is beschikbaar via de [Community Sites-console](sites-console.md#exporting-the-site).

UGC en aangepaste code worden niet opgenomen in het pakket met de communitysite.

Als u UGC wilt exporteren, gebruikt u de [AEM Communities UGC-migratiehulpprogramma](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration), een opensource migratiehulpmiddel beschikbaar op GitHub.

## Een Community-site verwijderen {#deleting-a-community-site}

Vanaf AEM Communities 6.3 Service Pack 1 wordt het pictogram Site verwijderen weergegeven als u de muisaanwijzer op de site van de gebruikersgemeenschap plaatst vanuit **[!UICONTROL Communities]** > **[!UICONTROL Sites]** console. Als u tijdens de ontwikkeling een gemeenschapssite wilt verwijderen en een nieuwe site wilt starten, kunt u deze functionaliteit gebruiken. Als u een gemeenschapssite verwijdert, worden de volgende aan die site gekoppelde items verwijderd:

* [UGC](#user-generated-content)
* [Gebruikersgroepen](#community-user-groups)
* [Databasegegevens](#database-records)

### Unieke site-id van community {#community-unique-site-id}

U kunt als volgt de unieke site-id identificeren die is gekoppeld aan de community-site met behulp van CRXDE:

* Ga naar de taalhoofdmap van de site, zoals `/content/sites/*<site name>*/en/rep:policy`.

* Zoek de `allow<#>` knooppunt met een `rep:principalName` in deze notatie `rep:principalName = *community-enable-nrh9h-members*`.

* De site-id is de derde component van `rep:principalName`

  Als `rep:principalName = community-enable-nrh9h-members`

   * **sitenaam** = *enable*
   * **site-id** = *nrh9h*
   * **unieke site-id** = *enable-nrh9h*

### Door gebruiker gegenereerde inhoud {#user-generated-content}

Verkrijg het gemeenschap-srp-hulpmiddelen project van GitHub:

* [https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dit bevat servlet om al UGC van om het even welk SRP te schrappen.

Alle UGC kan worden verwijderd of voor een specifieke site, bijvoorbeeld:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Hiermee verwijdert u alleen door de gebruiker gegenereerde inhoud (ingevoerd bij publicatie) en geen geschreven inhoud (ingevoerd bij auteur). Daarom [schaduwknooppunten](srp.md#shadownodes) niet worden beïnvloed.

### Gebruikersgroepen van de Gemeenschap {#community-user-groups}

Op alle auteur en publiceer instanties, van [beveiligingsconsole](../../help/sites-administering/security.md), zoek en verwijder de [gebruikersgroepen](users.md) die:

* Vooraf ingesteld met `community`
* Gevolgd door [unieke site-id](#community-unique-site-id)

Bijvoorbeeld: `community-engage-x0e11-members`.
