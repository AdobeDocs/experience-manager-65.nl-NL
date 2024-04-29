---
title: Limieten voor bijdragen van de lidstaten
description: Met de functie voor limiet van bijdragen kunt u de bijdragen beperken om te beschermen tegen spam
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: d00a8eb2-47ce-425a-a312-f043f82912be
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Limieten voor bijdragen van de lidstaten {#member-contribution-limits}

## Overzicht {#overview}

Met de functie voor premielimieten kunt u de bijdragen van leden van de gemeenschap beperken als middel om te beschermen tegen spam.

Wanneer een lid beperkt is, leidt elke post die het toegestane aantal bijdragen overschrijdt, tot een waarschuwing dat de limiet is overschreden en de post wordt afgewezen. Het lid van de gemeenschap kan dan naar het communautaire berichtcentrum gaan en contact opnemen met een manager van de gemeenschap die de grenzen indien nodig kan verwijderen.

Bijdragelimieten kunnen individueel worden toegestaan op basis van de [Ledenconsole](members.md) en/of geconfigureerd om automatisch te worden ingeschakeld wanneer bezoekers van de site nieuwe leden worden.

Gebruikend de console van Leden, kunnen de bijdragegrenzen proactief voor een lid door een communautaire manager op elk ogenblik worden verwijderd, of reactief worden verwijderd wanneer een lid een bericht naar een communautaire manager verzendt die zulk een verzoek doet.

## Configuratie van door gebruiker gegenereerde content-contributie van AEM Communities {#aem-communities-user-generated-content-contribution-limits-configuration}

Deze configuratie OSGi:

* Hiermee worden de kenmerken van de bijdragelimieten gedefinieerd (aantal posten binnen een tijdsperiode).
* Identificeert wie het lid kan berichten wanneer de grens is bereikt.
* Identificeert domeinen die nooit hoeven te worden beperkt.

Om deze configuratie te bereiken OSGi:

* Op de primaire uitgever:
* Meld u aan met beheerdersrechten.
* Toegang krijgen tot de [Webconsole](../../help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoeken `AEM Communities User Generated Content Contribution Limits Configuration`.
* Selecteer het pictogram Bewerken.

![configure-Limieten](assets/configure-limits.png)

* **[!UICONTROL Automatically Apply UGC Contribution Limits]**

  Als deze optie ingeschakeld is, worden automatisch bijdragelimieten ingesteld voor gebruikers die zich als leden van de gemeenschap registreren. Dit wordt weerspiegeld in het profiel van het lid van de gemeenschap en kan worden toegelaten/onbruikbaar gemaakt van [ledenconsole](members.md). Nieuwe leden met een e-mailadres uit een lijst van gewenste personen domeinen hebben nooit een beperking.

  De optie Standaard is uitgeschakeld.

* **[!UICONTROL UGC Limit]**

  Maximumaantal bijdragen.

  De standaardwaarde is tien berichten.

* **[!UICONTROL UGC Limit Frequency]**

  De tijdsperiode die de UGC-limiet beperkt.

  De standaardwaarde is 60 minuten.

* **[!UICONTROL Domains]**

  Een lijst met lijsten van gewenste personen van een of meer e-maildomeinen. Selecteer + pictogram om extra ingangen te maken.

  Gebruikers met e-mailadressen in de lijst van gewenste personen van domeinen worden niet beïnvloed wanneer de UGC-bijdragelimieten automatisch worden toegepast. Bijvoorbeeld als domein `mycompany.com` wordt toegevoegd aan de lijst met domeinen en vervolgens een lid met e-mailadres `me@mycompany.com` mag nooit worden gepost.

  Standaard is dit een lege lijst van gewenste personen.

* **[!UICONTROL Messaging Recipients]**

  Lijst van een of meer toegestane id&#39;s van leden die de bijdragelimieten voor leden kunnen wijzigen. Selecteer + pictogram om extra ingangen te maken.

  De leden mogen slechts bepaalde leden bereiken wanneer hun maximum is bereikt.

  Standaard zijn geen berichtontvangers.

Opmerking: de standaardconfiguratie resulteert in een limiet van tien berichten binnen een uur.
