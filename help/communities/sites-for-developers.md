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
* Geef de aangepaste sjabloon op door een eigenschap `page-template` aan het knooppunt `configuration` toe te voegen.

**Standaardmalplaatje**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**malplaatje van de Douane in overlayweg**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Bezit**: pagina-malplaatje

**Type**: Koord

**Waarde**: `template-name` (geen uitbreiding)

**knoop van de Configuratie**:

`/content/community site path/lang/configuration`

Bijvoorbeeld: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle knooppunten in het bovenliggende pad hoeven alleen van het type `Folder` te zijn.

>[!CAUTION]
>
>Als het douanemalplaatje de naam *sitepage.hbs* wordt gegeven, dan worden alle communautaire plaatsen aangepast.

### Voorbeeld van aangepaste sitesjabloon {#custom-site-template-example}

`vertical-sitepage.hbs` is bijvoorbeeld een sitesjabloon dat leidt tot de verticale plaatsing van menukoppelingen links op de pagina in plaats van horizontaal onder de banner.

[&#x200B; krijgt Dossier &#x200B;](assets/vertical-sitepage.hbs)
Plaats de sjabloon voor de aangepaste site in de overlaymap:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identificeer het douanemalplaatje door een `page-template` bezit aan de configuratieknooppunt toe te voegen:

`/content/sites/sample/en/configuration`

![&#x200B; crxde-siteconfiguration &#x200B;](assets/crxde-siteconfiguration.png)

Ben zeker om **te bewaren allen** en douanecode aan alle (AEM) instanties van Adobe Experience Manager te herhalen (de douanecode is niet inbegrepen wanneer de inhoud van de communautaire plaats van de console wordt gepubliceerd).

De geadviseerde praktijk voor het herhalen van douanecode moet [&#x200B; een pakket &#x200B;](../../help/sites-administering/package-manager.md#creating-a-new-package) tot stand brengen en het op alle instanties opstellen.

## Een communautaire site exporteren {#exporting-a-community-site}

Wanneer een communitysite is gemaakt, kan de site worden geëxporteerd als een AEM pakket dat is opgeslagen in Package Manager en dat beschikbaar is voor downloaden en uploaden.

Dit is beschikbaar bij de [&#x200B; console van Plaatsen van Gemeenschappen &#x200B;](sites-console.md#exporting-the-site).

UGC en aangepaste code worden niet opgenomen in het pakket met de communitysite.

Om UGC uit te voeren, gebruik het [&#x200B; Hulpmiddel van de Migratie van AEM Communities UGC &#x200B;](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration), een open-bron migratiehulpmiddel beschikbaar op GitHub.

## Een Community-site verwijderen {#deleting-a-community-site}

Vanaf AEM Communities 6.3 Service Pack 1 wordt het pictogram Site verwijderen weergegeven wanneer u de muisaanwijzer boven de communitysite plaatst vanuit **[!UICONTROL Communities]** > **[!UICONTROL Sites]** -console. Als u tijdens de ontwikkeling een gemeenschapssite wilt verwijderen en een nieuwe site wilt starten, kunt u deze functionaliteit gebruiken. Als u een gemeenschapssite verwijdert, worden de volgende aan die site gekoppelde items verwijderd:

* [UGC](#user-generated-content)
* [Gebruikersgroepen](#community-user-groups)
* [Databasegegevens](#database-records)

### Unieke site-id van community {#community-unique-site-id}

U kunt als volgt de unieke site-id identificeren die is gekoppeld aan de community-site met behulp van CRXDE:

* Navigeer naar de taalhoofdmap van de site, bijvoorbeeld `/content/sites/*<site name>*/en/rep:policy` .

* Zoek het knooppunt `allow<#>` met een `rep:principalName` in deze indeling `rep:principalName = *community-enable-nrh9h-members*` .

* De site-id is de derde component van `rep:principalName`

  Als bijvoorbeeld `rep:principalName = community-enable-nrh9h-members`

   * **plaatsnaam** = *laat* toe
   * **plaats identiteitskaart** = *nrh9h*
   * **unieke plaats identiteitskaart** = *toe:laten-nrh9h*

### Door gebruiker gegenereerde inhoud {#user-generated-content}

Verkrijg het gemeenschap-srp-hulpmiddelen project van GitHub:

* [&#x200B; https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

Dit bevat servlet om al UGC van om het even welk SRP te schrappen.

Alle UGC kan worden verwijderd of voor een specifieke site, bijvoorbeeld:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Hiermee verwijdert u alleen door de gebruiker gegenereerde inhoud (ingevoerd bij publicatie) en geen geschreven inhoud (ingevoerd bij auteur). Daarom [&#x200B; worden de schaduwknopen &#x200B;](srp.md#shadownodes) niet beïnvloed.

### Gebruikersgroepen van de Gemeenschap {#community-user-groups}

Op alle auteur en publiceer instanties, van de [&#x200B; veiligheidsconsole &#x200B;](../../help/sites-administering/security.md), bepaal de plaats, en verwijder de [&#x200B; gebruikersgroepen &#x200B;](users.md) die zijn:

* Vooraf ingesteld met `community`
* Gevolgd door [&#x200B; unieke plaats identiteitskaart &#x200B;](#community-unique-site-id)

Bijvoorbeeld `community-engage-x0e11-members` .
