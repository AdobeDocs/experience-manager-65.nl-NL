---
title: Essentiële elementen voor community-sites
seo-title: Essentiële elementen voor community-sites
description: Websites exporteren en verwijderen en aangepaste sitesjablonen maken
seo-description: Websites exporteren en verwijderen en aangepaste sitesjablonen maken
uuid: f0ec0e71-64e9-415a-b14a-939a9b1611c1
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: dc7a085e-d6de-4bc8-bd7e-6b43f8d172d2
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---


# Essentiële elementen voor communautaire sites {#community-site-essentials}

## Aangepaste sitesjabloon {#custom-site-template}

Een malplaatje van de douaneplaats kan voor elke taalexemplaar van een communautaire plaats afzonderlijk worden gespecificeerd.

Daartoe:

* Een aangepaste sjabloon maken.
* Bedek het standaardsjabloonpad van de site.
* Voeg de aangepaste sjabloon toe aan het overlaypad.
* Specificeer het douanemalplaatje door een `page-template` bezit aan `configuration` knoop toe te voegen.

**Standaardsjabloon**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Aangepaste sjabloon in overlaypad**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Eigenschap**: page-template

**Type**: String

**Waarde**:  `template-name` (geen extensie)

**Configuratieknooppunt**:

`/content/community site path/lang/configuration`

Bijvoorbeeld: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle knooppunten in het bovenliggende pad hoeven alleen van het type `Folder` te zijn.

>[!CAUTION]
>
>Als de aangepaste sjabloon de naam *sitepage.hbs* krijgt, worden alle communitysites aangepast.

### Voorbeeld van aangepaste sitesjabloon {#custom-site-template-example}

Als voorbeeld is `vertical-sitepage.hbs` een sitesjabloon dat resulteert in de plaatsing van menukoppelingen verticaal onder de linkerzijde van de pagina in plaats van horizontaal onder de banner.

[Get ](assets/vertical-sitepage.hbs)
FilePlace het malplaatje van de douaneplaats in de bekledingsomslag:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identificeer het douanemalplaatje door een `page-template` bezit aan de configuratieknoop toe te voegen:

`/content/sites/sample/en/configuration`

![crxde-siteconfiguration](assets/crxde-siteconfiguration.png)

Ben zeker aan **sparen allen** en repliceer douanecode aan alle AEM instanties (de douanecode is niet inbegrepen wanneer de inhoud van de communautaire plaats van de console wordt gepubliceerd).

De geadviseerde praktijk voor het herhalen van douanecode is [een pakket ](../../help/sites-administering/package-manager.md#creating-a-new-package) tot stand te brengen en het op alle instanties op te stellen.

## Een communautaire site exporteren {#exporting-a-community-site}

Wanneer een gemeenschapssite is gemaakt, kan de site worden geëxporteerd als een AEM pakket dat is opgeslagen in pakketbeheer en dat kan worden gedownload en geüpload.

Dit is beschikbaar bij [Community Sites console](sites-console.md#exporting-the-site).

Merk op dat UGC en douanecode niet inbegrepen in het pakket van de communautaire plaats is.

Om UGC uit te voeren, gebruik [AEM Communities UGC het Hulpmiddel van de Migratie ](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration), een open bronmigratiehulpmiddel beschikbaar op GitHub.

## Verwijderen van een Community-site {#deleting-a-community-site}

Vanaf AEM Communities 6.3 Service Pack 1 wordt het pictogram Site verwijderen weergegeven wanneer u de muisaanwijzer boven de communitysite plaatst vanuit de **[!UICONTROL Communities]** > **[!UICONTROL Sites]**-console. Als u tijdens de ontwikkeling een gemeenschapssite wilt verwijderen en een nieuwe site wilt starten, kunt u deze functionaliteit gebruiken. Als u een gemeenschapssite verwijdert, worden de volgende aan die site gekoppelde items verwijderd:

* [UGC](#user-generated-content)
* [Gebruikersgroepen](#community-user-groups)
* [Assets](#enablement-assets)
* [Databaserecords](#database-records)

### Unieke site-id {#community-unique-site-id}

U kunt als volgt de unieke site-id identificeren die aan de gemeenschapssite is gekoppeld met behulp van CRXDE:

* Navigeer naar de hoofdtaalmap van de site, bijvoorbeeld `/content/sites/*<site name>*/en/rep:policy`.

* Zoek het `allow<#>` knooppunt met een `rep:principalName` in deze notatie `rep:principalName = *community-enable-nrh9h-members*`.

* De site-id is de derde component van `rep:principalName`

   Als bijvoorbeeld `rep:principalName = community-enable-nrh9h-members`

   * **site name** =  *enable*
   * **site-id** =  *nrh9h*
   * **unieke site-id** =  *enable-nrh9h*

### Door gebruiker gegenereerde inhoud {#user-generated-content}

Verkrijg het gemeenschappen-srpTools project van Github:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Dit bevat servlet om al UGC van om het even welk SRP te schrappen.

Alle UGC kan worden verwijderd of voor een specifieke site, bijvoorbeeld:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Hiermee verwijdert u alleen door de gebruiker gegenereerde inhoud (ingevoerd bij publicatie) en geen geschreven inhoud (ingevoerd bij auteur). Daarom worden [schaduwknooppunten](srp.md#shadownodes) niet beïnvloed.

### Gebruikersgroepen {#community-user-groups}

Zoek en verwijder in alle auteur- en publicatieinstanties in de [beveiligingsconsole](../../help/sites-administering/security.md) de [gebruikersgroepen](users.md) die:

* Vooraf geplaatst met `community`
* Gevolgd door [unieke site-id](#community-unique-site-id)

Bijvoorbeeld, `community-engage-x0e11-members`.

### Elementen {#enablement-assets} inschakelen

Vanaf de hoofdconsole:

* Selecteer **[!UICONTROL Assets]**.
* Ga **[!UICONTROL Select]** wijze in.
* Selecteer een map met de [unieke site-id](#community-unique-site-id).
* Selecteer **[!UICONTROL Delete]** (moet mogelijk **[!UICONTROL More...]** selecteren).

### Databaseverslagen {#database-records}

Er is geen hulpmiddel om gegevensbestandingangen voor één specifieke plaats van de enablement communautaire selectief te schrappen.

Wanneer alle communautaire plaatsen worden geschrapt, dan laat vallen enablementdb en scormenginedb gebruikend MySQL Workbench.
