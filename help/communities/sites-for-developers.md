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
source-git-commit: 89156f94f2d0494d44d4f0b99abfba4fafbc66d3

---


# Essentiële elementen voor community-sites {#community-site-essentials}

## Aangepaste sitesjabloon {#custom-site-template}

Een malplaatje van de douaneplaats kan voor elke taalexemplaar van een communautaire plaats afzonderlijk worden gespecificeerd.

Daartoe:

* Een aangepaste sjabloon maken.
* Bedek het standaardsjabloonpad van de site.
* Voeg de aangepaste sjabloon toe aan het overlaypad.
* Specificeer het douanemalplaatje door een `page-template` bezit aan de `configuration` knoop toe te voegen.

**Standaardsjabloon**:

`/libs/social/console/components/hbs/sitepage/sitepage.hbs`

**Aangepaste sjabloon in overlaypad**:

`/apps/social/console/components/hbs/sitepage/template-name.hbs`

**Eigenschap**: page-template

**Type**: String

**Waarde**: `template-name` (geen extensie)

**Configuratieknooppunt**:

`/content/community site path/lang/configuration`

Bijvoorbeeld: `/content/sites/engage/en/configuration`

>[!NOTE]
>
>Alle knooppunten in het bovenliggende pad hoeven alleen van het type te zijn `Folder`.


>[!CAUTION]
>
>Als het douanemalplaatje de naam *sitepage.hbs* wordt gegeven, dan zullen alle communautaire plaatsen worden aangepast.


### Voorbeeld van aangepaste sitesjabloon {#custom-site-template-example}

Een voorbeeld hiervan `vertical-sitepage.hbs` is een sitesjabloon dat leidt tot de verticale plaatsing van menukoppelingen links op de pagina in plaats van horizontaal onder de banner.

[Bestand](assets/vertical-sitepage.hbs)ophalen De aangepaste sitesjabloon in de overlaymap plaatsen:

`/apps/social/console/components/hbs/sitepage/vertical-sitepage.hbs`

Identificeer het douanemalplaatje door een `page-template` bezit aan de configuratieknoop toe te voegen:

`/content/sites/sample/en/configuration`

![chlimage_1-80](assets/chlimage_1-80.png)

Ben zeker om allen **te** sparen en douanecode aan alle instanties te herhalen AEM (de douanecode is niet inbegrepen wanneer de inhoud van de communautaire plaats van de console wordt gepubliceerd).

De geadviseerde praktijk voor het herhalen van douanecode is een pakket [tot stand te](../../help/sites-administering/package-manager.md#creating-a-new-package) brengen en het op alle instanties op te stellen.

## Een communautaire site exporteren {#exporting-a-community-site}

Wanneer een communitysite is gemaakt, kan de site worden geëxporteerd als een AEM-pakket dat is opgeslagen in pakketbeheer en dat kan worden gedownload en geüpload.

Dit is beschikbaar bij de console [van de Plaatsen van](sites-console.md#exporting-the-site)Gemeenschappen.

Merk op dat UGC en douanecode niet inbegrepen in het pakket van de communautaire plaats is.

Om UGC uit te voeren, gebruik het Hulpmiddel [van de Migratie van](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)AEM-Gemeenschappen UGC, een open bronmigratiehulpmiddel beschikbaar op GitHub.

## Een Community-site verwijderen {#deleting-a-community-site}

Vanaf AEM Communities 6.3 Service Pack 1 wordt het pictogram Site verwijderen weergegeven wanneer u de muisaanwijzer boven de community plaatst vanuit **[!UICONTROL Communities]** > **[!UICONTROL Sites]** Console. Als u tijdens de ontwikkeling een gemeenschapssite wilt verwijderen en een nieuwe site wilt starten, kunt u deze functionaliteit gebruiken. Als u een gemeenschapssite verwijdert, worden de volgende aan die site gekoppelde items verwijderd:

* [UGC](#user-generated-content)
* [Gebruikersgroepen](#community-user-groups)
* [Assets](#enablement-assets)
* [Databaserecords](#database-records)

### Unieke site-id van community {#community-unique-site-id}

U kunt als volgt de unieke site-id identificeren die aan de gemeenschapssite is gekoppeld met behulp van CRXDE:

* Navigeer naar de taalhoofdmap van de site, bijvoorbeeld `/content/sites/*<site name>*/en/rep:policy`.

* Zoek het `allow<#>` knooppunt met een `rep:principalName` notatie in deze notatie `rep:principalName = *community-enable-nrh9h-members*`.

* De site-id is de derde component van `rep:principalName`

   Als `rep:principalName = community-enable-nrh9h-members`

   * **sitenaam** = *inschakelen*
   * **site-id** = *nrh9h*
   * **unieke site-id** = *enable-nrh9h*

### Door gebruiker gegenereerde inhoud {#user-generated-content}

Verkrijg het gemeenschappen-srpTools project van Github:

* [https://github.com/Adobe-Marketing-Cloud/communities-srp-tools](https://github.com/Adobe-Marketing-Cloud/communities-srp-tools)

Dit bevat servlet om al UGC van om het even welk SRP te schrappen.

Alle UGC kan worden verwijderd of voor een specifieke site, bijvoorbeeld:

* `path=/content/usergenerated/asi/mongo/content/sites/engage`

Hiermee verwijdert u alleen door de gebruiker gegenereerde inhoud (ingevoerd bij publicatie) en geen geschreven inhoud (ingevoerd bij auteur). Dit heeft dus geen invloed op [schaduwknooppunten](srp.md#shadownodes) .

### Gebruikersgroepen van de Gemeenschap {#community-user-groups}

Zoek in alle auteur- en publicatieinstanties vanuit de [beveiligingsconsole](../../help/sites-administering/security.md)de [gebruikersgroepen](users.md) die:

* Vooraf ingesteld met `community`
* Gevolgd door [unieke site-id](#community-unique-site-id)

Bijvoorbeeld, `community-engage-x0e11-members`.

### Enablement Assets {#enablement-assets}

Vanaf de hoofdconsole:

* Selecteer **[!UICONTROL Elementen]**.
* Ga **[!UICONTROL Uitgezochte]** wijze in.
* Selecteer een map met de [unieke site-id](#community-unique-site-id).
* Selecteer **[!UICONTROL Verwijderen]** (moet mogelijk **[!UICONTROL Meer selecteren...]**).

### Databasegegevens {#database-records}

Er is geen hulpmiddel om gegevensbestandingangen voor één specifieke plaats van de enablement communautaire selectief te schrappen.

Wanneer alle communautaire plaatsen worden geschrapt, dan laat vallen enablementdb en scormenginedb gebruikend MySQL Workbench.
