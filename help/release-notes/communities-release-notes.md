---
title: Opmerkingen bij de release van AEM Communities
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.5-gemeenschappen.
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---


# Opmerkingen bij de release van AEM Communities {#aem-communities-release-notes}

Lees verder voor de verbeteringen aan AEM Communities sinds de release 6.4. Zie [AEM 6.5 Community Guide](https://helpx.adobe.com/experience-manager/6-4/communities/user-guide.html) voor meer informatie over de nieuwe functies.

Zie de sectie [Gemeenschappen implementeren](https://helpx.adobe.com/in/experience-manager/6-4/help/communities/deploy-communities.html#LatestReleases) van de documentatie voor de nieuwste versie.

## Belangrijke verbeteringen {#major-enhancements}

### Verbeteringen in de betrokkenheid van de gemeenschap {#enhancements-to-community-engagement}

**@Mtifications**
supportAEM Communities staat geregistreerde gebruikers nu toe om andere geregistreerde leden te labelen (vermelden) om hun aandacht te vestigen in Door gebruikers gegenereerde inhoud. De gelabelde (vermelde) leden worden vervolgens op de hoogte gesteld, met een diepe koppeling naar de overeenkomstige door de gebruiker gegenereerde inhoud. Gebruikers kunnen er echter voor kiezen om het web- en e-mailbericht uit te schakelen of in te schakelen.

![Op de vergadering](assets/at-mentions.png)

De gebruikers van de Gemeenschap hoeven niet naar hun voornaam, familienaam, of gebruikersnaam te zoeken om te zien of heeft iemand uit aan hen bereikt of hun aandacht nodig. Bovendien kunnen UGC-auteurs reacties vragen bij specifieke geregistreerde gebruikers die het probleem het beste kunnen oplossen en invoer kunnen toevoegen.

De communautaire beheerders moeten **Mention** op communautaire componenten toelaten om geregistreerde gebruikers toe te staan de functionaliteit op die componenten gebruiken.

**Groepsberichten**

Geregistreerde leden van de community kunnen nu bulksgewijs directe berichten naar groepen verzenden via één e-mailcompositie, in plaats van hetzelfde bericht afzonderlijk naar groepsleden te verzenden. Om [groepsoverseinen](/help/communities/configure-messaging.md) toe te staan, laat beide instanties van [de Dienst van Verrichtingen van het Overseinen](/help/communities/messaging.md#group-messaging) toe.

![Groepsbericht](assets/group-messaging.png)

### Verbeteringen voor Bulk Moderation {#enhancements-to-bulk-moderation}

Aangepaste filters in Bulk Moderatie

[Aangepaste ](/help/communities/moderation.md#custom-filters) filters kunnen nu worden ontwikkeld en toegevoegd aan de gebruikersinterface voor bulkmodernisering.

Een [voorbeeldproject](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) dat het filtreren door markeringen toont is beschikbaar in [Github](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter). Dit project kan als basis worden gebruikt om analoge douanefilters te ontwikkelen.

![Aangepaste filters](assets/custom-tag-filter.png)

**Lijstweergave in bulkmodernisering**

De nieuwe Mening van de Lijst met betere UI is verstrekt in bulkmoderatie om Gebruiker te tonen Gegenereerde Inhoudsingangen.

![Modernisering van de lijst](assets/list-view-moderation.png)

### Verbeteringen voor site- en groepsbeheer {#enhancements-to-site-and-group-management}

**Site- en groepsbeheerders van auteurs**

Gemeenschappen, AEM 6.5 en hoger, maken gedecentraliseerd beheer (en beheer) van verschillende gemeenschapssites en groepen/geneste groepen mogelijk. Organisaties die meerdere communitysites en geneste groepen hosten, kunnen nu leden selecteren voor beheerdersrollen aan de Auteur op het moment dat de site (en groep) wordt gemaakt.

![Sitebeheerder](assets/site-admin.png)

Sitebeheerders kunnen een groep op elk hiërarchisch niveau maken en de standaardbeheerders worden. Deze beheerders kunnen later door andere groepbeheerders worden verwijderd. De beheerders van de groep kunnen hun groep G1 beheren en tot een subgroep leiden die onder G1 wordt genest.

### Verbeteringen voor activering {#enhancements-to-enablement}

**Ondersteuning voor SCORM 2017.1**

De enablement functionaliteit van AEM 6.5 Communities ondersteunt Shareable Content Object Reference Model [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) engine.

* Ondersteuning voor toetsenbordnavigatie op schakelingscomponenten
* De componenten van Enablement (bijvoorbeeld Catalog en Course die spelen, Toewijzingen, de Bibliotheek van het Dossier) in AEM Communities steunen toetsenbordnavigatie voor betere toegankelijkheid.

### Andere verbeteringen {#other-enhancements}

* Solr 7-ondersteuning
* AEM 6.5 Community&#39;s ondersteunen Apache Solr 7.0-versie van het zoekplatform bij het opzetten van MSRP en DSRP.
