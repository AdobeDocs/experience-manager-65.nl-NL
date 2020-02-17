---
title: Opmerkingen bij de release AEM-gemeenschappen
description: Opmerkingen bij de release die specifiek zijn voor Adobe Experience Manager 6.5-gemeenschappen.
uuid: 1b436959-581c-4b34-b2df-cccc5727da59
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: c3505807-1550-491a-8619-e87839afca4f
docset: aem65
translation-type: tm+mt
source-git-commit: 57bad4e74b2dfd9e389643bfe58ef25564c5c545

---


# Opmerkingen bij de release AEM-gemeenschappen{#aem-communities-release-notes}

Lees verder voor de verbeteringen aan AEM Communities sinds de release 6.4. Raadpleeg de gebruikershandleiding [van](https://helpx.adobe.com/experience-manager/6-4/communities/user-guide.html)AEM 6.5 Communities voor meer informatie over de nieuwe functies.

Voor de recentste versie, zie de het [Plaatsen sectie van Gemeenschappen](https://helpx.adobe.com/in/experience-manager/6-4/help/communities/deploy-communities.html#LatestReleases) van de documentatie.

## Belangrijke verbeteringen {#major-enhancements}

### Verbeteringen van de betrokkenheid van de gemeenschap {#enhancements-to-community-engagement}

**@Mtifications ondersteunen** AEM Communities biedt geregistreerde gebruikers nu de mogelijkheid om andere geregistreerde leden te labelen (vermelden) om hun aandacht te vestigen in Door gebruikers gegenereerde inhoud. De gelabelde (vermelde) leden worden vervolgens op de hoogte gesteld, met een diepe koppeling naar de overeenkomstige door de gebruiker gegenereerde inhoud. Gebruikers kunnen er echter voor kiezen om het web- en e-mailbericht uit te schakelen of in te schakelen.

![Op de vergadering](assets/at-mentions.png)

De gebruikers van de Gemeenschap hoeven niet naar hun voornaam, familienaam, of gebruikersnaam te zoeken om te zien of heeft iemand uit aan hen bereikt of hun aandacht nodig. Bovendien kunnen UGC-auteurs reacties vragen bij specifieke geregistreerde gebruikers die het probleem het beste kunnen oplossen en invoer kunnen toevoegen.

De communautaire beheerders moeten Mentie **op communautaire componenten toelaten om geregistreerde gebruikers toe te staan de functionaliteit op die componenten gebruiken.

**Groepsberichten**

Geregistreerde leden van de community kunnen nu bulksgewijs directe berichten naar groepen verzenden via één e-mailcompositie, in plaats van hetzelfde bericht afzonderlijk naar groepsleden te verzenden. Om [groepsoverseinen](/help/communities/configure-messaging.md)toe te staan, laat beide instanties van de Dienst [van de Verrichtingen van het](/help/communities/messaging.md#group-messaging)Overseinen toe.

![Groepsbericht](assets/group-messaging.png)

### Verbeteringen voor Bulk Moderation {#enhancements-to-bulk-moderation}

Aangepaste filters in Bulk Moderatie

[De filters](/help/communities/moderation.md#custom-filters) van de douane kunnen nu worden ontwikkeld en aan BulkModeration UI worden toegevoegd.

Een [voorbeeldproject](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) dat het filteren door markeringen aantoont is beschikbaar in [Github](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter). Dit project kan als basis worden gebruikt om analoge douanefilters te ontwikkelen.

![Aangepaste filters](assets/custom-tag-filter.png)

**Lijstweergave in bulkmodernisering**

De nieuwe Mening van de Lijst met betere UI is verstrekt in bulkmoderatie om Gebruiker te tonen Gegenereerde Inhoudsingangen.

![Modernisering van de lijst](assets/list-view-moderation.png)

### Verbeteringen voor site- en groepsbeheer {#enhancements-to-site-and-group-management}

**Site- en groepsbeheerders van auteurs**

Gemeenschappen, vanaf AEM 6.5, maken gedecentraliseerd beheer (en beheer) van verschillende gemeenschapssites en groepen/geneste groepen mogelijk. Organisaties die meerdere communitysites en geneste groepen hosten, kunnen nu leden selecteren voor beheerdersrollen aan de Auteur op het moment dat de site (en groep) wordt gemaakt.

![Sitebeheerder](assets/site-admin.png)

Sitebeheerders kunnen een groep op elk hiërarchisch niveau maken en de standaardbeheerders worden. Deze beheerders kunnen later door andere groepbeheerders worden verwijderd. De beheerders van de groep kunnen hun groep G1 beheren en tot een subgroep leiden die onder G1 wordt genest.

### Verbeteringen op gebied van activering {#enhancements-to-enablement}

**Ondersteuning voor SCORM 2017.1**

De enablement-functionaliteit van AEM 6.5 Communities ondersteunt Shareable Content Object Reference Model [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) -engine.

**De steun van de toetsenbordnavigatie op enablement componenten**De componenten van Enablement (bijvoorbeeld Catalogus en het Spelen van de Cursus, Toewijzingen, de Bibliotheek van het Dossier) in AEM-Gemeenschappen steunen toetsenbordnavigatie voor betere toegankelijkheid.

### Andere verbeteringen {#other-enhancements}

* **Solr 7 support**AEM 6.5 Communities ondersteunt Apache Solr 7.0 versie van het zoekplatform bij het opzetten van MSRP en DSRP.
