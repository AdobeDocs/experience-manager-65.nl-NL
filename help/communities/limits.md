---
title: Limieten voor bijdragen van de lidstaten
seo-title: Limieten voor bijdragen van de lidstaten
description: Met de functie voor limiet van bijdragen kunt u de bijdragen beperken om te beschermen tegen spam
seo-description: Met de functie voor limiet van bijdragen kunt u de bijdragen beperken om te beschermen tegen spam
uuid: 99b2a855-3f0d-41a0-9572-517a7f29af9f
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d855aac2-f34d-402f-9dc3-c7ad494b45f2
translation-type: tm+mt
source-git-commit: e4456e80059479ca874681e20f8546f29ac92597

---


# Limieten voor bijdragen van de lidstaten {#member-contribution-limits}

## Overzicht {#overview}

De functie voor bijdragelimieten biedt de mogelijkheid om de bijdragen van leden van de gemeenschap te beperken als middel om bescherming te bieden tegen spam.

Wanneer een lid beperkt is, zal elke post die het toegestane aantal bijdragen overschrijdt, leiden tot een waarschuwing dat de limiet is overschreden en de post wordt afgewezen. Het lid van de gemeenschap kan dan naar het communautaire berichtcentrum gaan en contact opnemen met een manager van de gemeenschap die de grenzen indien nodig kan verwijderen.

De bijdragelimieten kunnen individueel van de console [van de](members.md) Leden worden toegelaten en/of worden gevormd om automatisch worden toegelaten wanneer de bezoekers van de plaats nieuwe leden worden.

Gebruikend de console van Leden, kunnen de bijdragegrenzen proactief voor een lid door een communautaire manager op elk ogenblik worden verwijderd, of reactief worden verwijderd wanneer een lid een bericht naar een communautaire manager verzendt die zulk een verzoek doet.

## Configuratie van door gebruikers gegenereerde inhoudcontributielimieten voor AEM-gemeenschappen {#aem-communities-user-generated-content-contribution-limits-configuration}

Deze configuratie OSGi:

* Hiermee worden de kenmerken van de bijdragelimieten gedefinieerd (aantal posten binnen een tijdsperiode).
* Identificeert wie het lid zal kunnen bericht wanneer de grens is bereikt.
* Identificeert domeinen die nooit hoeven te worden beperkt.

Om deze configuratie te bereiken OSGi:

* Op de primaire uitgever:
* Meld u aan met beheerdersrechten.
* Open de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Zoeken `AEM Communities User Generated Content Contribution Limits Configuration`.
* Selecteer het bewerkingspictogram.

![chlimage_1-127](assets/chlimage_1-127.png)

* **[!UICONTROL UGC-bijdragelimieten automatisch toepassen]**

   Als deze optie ingeschakeld is, worden automatisch bijdragelimieten ingesteld voor gebruikers die zich als leden van de gemeenschap registreren. Dit wordt weerspiegeld in het profiel van het lid van de gemeenschap en kan van de [lidconsole](members.md)worden toegelaten/worden onbruikbaar gemaakt. Nieuwe leden met een e-mailadres uit een domein op de witte lijst hebben nooit een beperking.

   De optie Standaard is uitgeschakeld.

* **[!UICONTROL UGC-limiet]**

   Maximumaantal bijdragen.

   De standaardwaarde is 10 berichten.

* **[!UICONTROL Frequentie UGC-limiet]**

   De tijdsperiode die de UGC-limiet beperkt.

   De standaardwaarde is 60 minuten.

* **[!UICONTROL Domeinen]**

   Een witte lijst met een of meer e-maildomeinen. Selecteer + pictogram om extra ingangen te maken.

   De gebruikers met e-mailadressen in de witte vermelde domeinen worden niet beïnvloed wanneer de de bijdragegrenzen van UGC automatisch worden toegepast. Als domein bijvoorbeeld aan de lijst met domeinen `mycompany.com` wordt toegevoegd, `me@mycompany.com` wordt een lid met een e-mailadres nooit verplicht om te posten.

   Standaard is dit een lege witte lijst.

* **[!UICONTROL Ontvangers van berichten]**

   Lijst van een of meer toegestane id&#39;s van leden die de bijdragelimieten voor leden kunnen wijzigen. Selecteer + pictogram om extra ingangen te maken.

   De leden mogen slechts bepaalde leden bereiken wanneer hun maximum is bereikt.

   Standaard zijn geen berichtontvangers.

Opmerking: De standaardconfiguratie resulteert in een maximum van 10 posten binnen een periode van één uur.
