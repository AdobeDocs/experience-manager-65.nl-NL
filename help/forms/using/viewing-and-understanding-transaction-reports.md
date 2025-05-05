---
title: Transactierapporten weergeven en begrijpen
description: Gebruik transactierapporten om een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software.
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Transaction Reports
exl-id: 3c7cbe1f-ac81-4df9-96b2-662cbc5f2075
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# Transactierapporten voor AEM Forms bekijken en begrijpen op OSGi{#viewing-and-understanding-transaction-reports}

Met transactierapporten kunt u het aantal verzonden formulieren, verwerkte documenten en gerenderde documenten vastleggen en bijhouden. Het doel van het volgen van deze transacties is een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software. Voor meer informatie, zie [ Overzicht van de Rapporten van de Transactie van AEM Forms ](../../forms/using/transaction-reports-overview.md).

## Transactierapporten instellen  {#setting-up-transaction-reports}

De functie Transactierapporten is beschikbaar als onderdeel van het add-on pakket voor AEM formulieren. Voor informatie over het installeren van het toe:voegen-on pakket op alle auteur en publiceer instanties, zie [ Installerend en vormend AEM vormen ](/help/forms/using/installing-configuring-aem-forms-osgi.md). Wanneer u het pakket voor de invoegtoepassing voor AEM formulieren hebt geïnstalleerd, gaat u als volgt te werk:

* Omgekeerde replicatie inschakelen voor alle publicatievarianten
* Transactierapporten inschakelen
* Rechten opgeven om een transactierapport te bekijken
* (Optioneel) Transactie-uitstelperiode en -uitvakken configureren [&#128279;](/help/forms/using/installing-configuring-aem-forms-osgi.md)

>[!NOTE]
>
>* AEM Forms-transactierapporten ondersteunen geen topologieën die alleen publicatieexemplaren bevatten.
>* Voordat u transactierapportage gebruikt, moet u ervoor zorgen dat de omgekeerde replicatie is ingeschakeld voor alle publicatievarianten.
>* Transactiegegevens worden omgekeerd gerepliceerd van een publicatie-instantie naar alleen de overeenkomstige auteur of verwerkingsinstantie. De auteur of verwerkingsinstantie kan gegevens niet verder repliceren naar een andere instantie.
>

### Omgekeerde replicatie inschakelen voor alle publicatievarianten {#enable-reverse-replication-on-all-the-publish-instances}

Transactierapporten gebruiken omgekeerde replicatie om het aantal transacties van publicatieinstanties tot auteur te consolideren. Stel de omgekeerde replicatie in voor alle publicatieexemplaren. Voor gedetailleerde instructies aan opstellings omgekeerde replicatie, zie [ replicatie ](/help/sites-deploying/replication.md).

### Transactierapporten inschakelen {#enable-transaction-reports}

Transactierapporten zijn standaard uitgeschakeld. U kunt de rapporten van AEM Console van het Web toelaten. Als u transactierapporten wilt inschakelen in een AEM Forms-omgeving, voert u de volgende stappen uit op alle auteur- en publicatieinstanties:

1. Meld u als beheerder aan bij een AEM. Ga naar **Hulpmiddelen** > **Verrichtingen** > **Console van het Web**.
1. Bepaal en open de **dienst van de Transactie van Forms die** meldt.
1. Schakel het selectievakje Transacties opnemen in. Klik **sparen**.

   Herhaal stap 1-3 voor alle auteur en publiceer instanties.

### Rechten opgeven om een transactierapport te bekijken {#provide-rights-to-view-a-transaction-report}

Alleen leden van de groep fd-administrator kunnen transactierapporten weergeven. Om een gebruiker toe te staan om transactierapporten te bekijken, maak gebruikerslid van de fd-beheerder groep. Voor instructies over het maken van een gebruiker een lid van een AEM groep, zie [ Gebruiker, Groep en het Beleid van de Rechten van de Toegang ](/help/sites-administering/user-group-ac-admin.md).

### (Optioneel) Transactie-uitstelperiode en -uitvakken configureren {#optional-configure-transaction-flush-period-and-outboxes}

Transacties worden in het geheugen opgeslagen voordat ze in de opslagplaats worden opgeslagen. Het proces wordt gevolgd om ervoor te zorgen dat er niet vaak naar de gegevensopslagplaats wordt geschreven. Standaard is de cacheperiode (Transactie Flush Period) ingesteld op 60 seconden. U kunt de standaardperiode aanpassen aan uw omgeving. Voer de volgende stappen uit om de standaardcaching periode te veranderen:

1. Meld u als beheerder aan bij de instanties van de auteur. Ga naar **Hulpmiddelen** > **Verrichtingen** > **Console van het Web**.
1. Zoek en open de **dienst van de Opslag van de Opslag van de Opslag van de Transactie van 0&rbrace; Forms.**
1. Specificeer het aantal seconden op het **gebied van de Periode van de Duw van de Transactie**. Klik **sparen**.

De omgekeerde replicatie kopieert transactiegegevens aan standaardoutbox van de auteursinstanties. U kunt transactiegegevens in een douane outbox plaatsen. Voer de volgende stappen uit om een aangepast outbox te specificeren:

1. Meld u als beheerder aan bij de instanties van de auteur. Ga naar **Hulpmiddelen** > **Verrichtingen** > **Console van het Web**.
1. Zoek en open de **dienst van de Opslag van de Opslag van de Opslag van de Transactie van 0&rbrace; Forms.**
1. Specificeer de naam van douanecontourbox het **Outboxes** gebied. Klik **sparen**. Er wordt een uitsnijdvak met de opgegeven naam gemaakt op alle instanties van de auteur.

## Het transactierapport weergeven {#viewing-the-transaction-report}

U kunt transactierapporten weergeven over auteur- of publicatieinstanties. Het transactierapport over de auteurinstantie verstrekt een bijeengevoegde som van alle transacties die op de gevormde auteur en publiceer instanties plaatsvinden. Het transactierapport over de publicatie-instantie bevat een telling van transacties die alleen op de onderliggende publicatie-instantie plaatsvinden. Voer de volgende stappen uit om het rapport te bekijken:

1. Meld u aan bij de AEM Forms-server op `https://[hostname]:'port'` .
1. Navigeer aan **Hulpmiddelen** > **Forms** > **het Rapport van de Transactie van de Mening**.

## Het rapport begrijpen {#understanding-the-report}

AEM Forms geeft transactierapporten weer sinds de geconfigureerde datum, zoals in een samenvattingsrapport hieronder wordt getoond:

![ steekproef-transactie-rapport-auteur ](assets/sample-transaction-report-author.png)

* Gebruik **het Terugstellen van de datum aan vandaag** opties om transactieverslagen terug te stellen. Wanneer u de datum aan vandaag terugstelt, worden alle vorige transactieverslagen verloren. Wanneer u de datum opnieuw instelt op een auteurinstantie, beïnvloedt de verandering geen transactierapporten over de instanties van Publish en omgekeerd.
* Gebruik **toont transacties van slechts de instanties van Publish** om alle transacties te bekijken die slechts op gevormd voorkwamen publiceren instantie of landbouwbedrijf publiceren.
* Gebruik de categorieën: **Verwerkt Document**, **Gerenderde Documenten**, en **Voorgelegde Forms** om overeenkomstige transacties te bekijken. Voor het type van transacties die in deze categorieën worden vermeld, zie [ Billable Transactie Rapporten APIs ](../../forms/using/transaction-reports-billable-apis.md).

## Logboeken voor transactierapporten weergeven {#view-transaction-reporting-logs}

Transactierapportering plaatst alle informatie die in het rapport wordt weergegeven en enkele aanvullende informatie in de logboeken. De informatie in de logboeken is nuttig voor de gevorderde gebruikers. Bijvoorbeeld, verdelen de logboeken transacties in veelvoudige granulaire categorieën in vergelijking met drie geconsolideerde categorieën die in het rapport worden getoond. De logbestanden zijn beschikbaar in het bestand `error.log` in de map `/crx-repository/logs/` . De logboeken zijn beschikbaar zelfs als u de transactierapporten van AEM Console van het Web niet toelaat.

## Verwante artikelen {#related-articles}

* [Transactierapporten Overzicht voor AEM Forms op OSGi](../../forms/using/transaction-reports-overview.md)
* [Transactierapporten Billable API&#39;s voor AEM Forms op OSGi](../../forms/using/transaction-reports-billable-apis.md)
* [Registreer een transactie voor douaneimplementaties voor AEM Forms op OSGi](/help/forms/using/record-transaction-custom-implementation.md)
