---
title: Essentiële elementen voor community-sites
seo-title: Community Site Essentials
description: Websites exporteren en verwijderen en aangepaste sitesjablonen maken
seo-description: Exporting and deleting community sites and creating custom site templates
uuid: f0ec0e71-64e9-415a-b14a-939a9b1611c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: dc7a085e-d6de-4bc8-bd7e-6b43f8d172d2
exl-id: 1dc568cd-315c-4944-9a3e-e5d7794e5dc0
source-git-commit: cc0574ae22758d095a3ca6b91f0ceae4a8691f0e
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Essentiële elementen voor community-sites {#community-site-essentials}

## Aangepaste sitesjabloon {#custom-site-template}

Een malplaatje van de douaneplaats kan voor elke taalexemplaar van een communautaire plaats afzonderlijk worden gespecificeerd.

Daartoe:

* Een aangepaste sjabloon maken.
* Bedek het standaardsjabloonpad van de site.
* Voeg de aangepaste sjabloon toe aan het overlaypad.
* Geef de aangepaste sjabloon op door een `page-template` aan de `configuration` knooppunt.

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
>Als de aangepaste sjabloon de naam krijgt *site.hbs* Vervolgens worden alle communitysites aangepast.

### Voorbeeld van aangepaste sitesjabloon {#custom-site-template-example}

Als voorbeeld: `vertical-sitepage.hbs` is een sitesjabloon dat leidt tot de plaatsing van menukoppelingen verticaal onder de linkerzijde van de pagina in plaats van horizontaal onder de banner.

[Bestand ophalen](assets/vertical-sitepage.hbs)
Plaats de sjabloon voor de aangepaste site in de overlaymap:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identificeer het douanemalplaatje door een `page-template` eigenschap voor het configuratieknooppunt:

`/content/sites/sample/en/configuration`

![crxde-siteconfiguration](assets/crxde-siteconfiguration.png)

Zorg ervoor dat u **Alles opslaan** en repliceer douanecode aan alle AEM instanties (de douanecode is niet inbegrepen wanneer de inhoud van de communautaire plaats van de console wordt gepubliceerd).

Voor het repliceren van aangepaste code wordt het volgende aanbevolen: [een pakket maken](../../help/sites-administering/package-manager.md#creating-a-new-package) en implementeren.

## Een communautaire site exporteren {#exporting-a-community-site}

Wanneer een gemeenschapssite is gemaakt, kan de site worden geëxporteerd als een AEM pakket dat is opgeslagen in pakketbeheer en dat kan worden gedownload en geüpload.

Dit is beschikbaar via de [Community Sites-console](sites-console.md#exporting-the-site).

Merk op dat UGC en douanecode niet inbegrepen in het pakket van de communautaire plaats is.

Als u UGC wilt exporteren, gebruikt u de opdracht [AEM Communities UGC-migratiehulpprogramma](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration), een open bronmigratiehulpmiddel beschikbaar op GitHub.

## Een Community-site verwijderen {#deleting-a-community-site}

Vanaf AEM Communities 6.3 Service Pack 1 wordt het pictogram Site verwijderen weergegeven als u de muisaanwijzer op de site van de gebruikersgemeenschap plaatst vanuit **[!UICONTROL Communities]** > **[!UICONTROL Sites]** console. Als u tijdens de ontwikkeling een gemeenschapssite wilt verwijderen en een nieuwe site wilt starten, kunt u deze functionaliteit gebruiken. Als u een gemeenschapssite verwijdert, worden de volgende aan die site gekoppelde items verwijderd:

* [UGC](#user-generated-content)
* [Gebruikersgroepen](#community-user-groups)
* [Databaserecords](#database-records)

### Unieke site-id van community {#community-unique-site-id}

U kunt als volgt de unieke site-id identificeren die aan de gemeenschapssite is gekoppeld met behulp van CRXDE:

* Ga naar de taalhoofdmap van de site, zoals `/content/sites/*<site name>*/en/rep:policy`.

* Zoek de `allow<#>` knooppunt met een `rep:principalName` in deze notatie `rep:principalName = *community-enable-nrh9h-members*`.

* De site-id is de derde component van `rep:principalName`

   Als `rep:principalName = community-enable-nrh9h-members`

   * **sitenaam** = *enable*
   * **site-id** = *nrh9h*
   * **unieke site-id** = *enable-nrh9h*

### Door gebruiker gegenereerde inhoud {#user-generated-content}

Verkrijg het gemeenschappen-srpTools project van Github:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Dit bevat servlet om al UGC van om het even welk SRP te schrappen.

Alle UGC kan worden verwijderd of voor een specifieke site, bijvoorbeeld:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Hiermee verwijdert u alleen door de gebruiker gegenereerde inhoud (ingevoerd bij publicatie) en geen geschreven inhoud (ingevoerd bij auteur). Daarom [schaduwknooppunten](srp.md#shadownodes) niet worden beïnvloed.

### Gebruikersgroepen van de Gemeenschap {#community-user-groups}

Op alle auteur en publiceer instanties, van [beveiligingsconsole](../../help/sites-administering/security.md), zoek en verwijder de [gebruikersgroepen](users.md) die:

* Vooraf ingesteld met `community`
* Gevolgd door [unieke site-id](#community-unique-site-id)

Bijvoorbeeld, `community-engage-x0e11-members`.
