---
title: Transactierapporten weergeven en begrijpen
seo-title: Transactierapporten weergeven en begrijpen
description: Gebruik transactierapporten om een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software.
seo-description: Gebruik transactierapporten om een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software.
uuid: 56d9f01d-4778-47c9-bbb2-6650a73a3f59
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c04c488b-73f3-49ba-9e89-f97497965757
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Transactierapporten weergeven en begrijpen{#viewing-and-understanding-transaction-reports}

Met transactierapporten kunt u het aantal verzonden formulieren, verwerkte documenten en gerenderde documenten vastleggen en bijhouden. Het doel van het volgen van deze transacties is een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software. Voor meer informatie, zie het Overzicht [van de Rapporten van de Transactie van](../../forms/using/transaction-reports-overview.md)Vormen AEM.

## Transactierapporten instellen {#setting-up-transaction-reports}

De functie Transactierapporten is beschikbaar als onderdeel van het invoegpakket voor AEM-formulieren. Zie AEM-formulieren [installeren en configureren voor informatie over het installeren van het invoegpakket op alle auteur- en publicatieinstanties](/help/forms/using/installing-configuring-aem-forms-osgi.md). Als u het invoegpakket voor AEM-formulieren hebt geïnstalleerd, gaat u als volgt te werk:

* Omgekeerde replicatie inschakelen voor alle publicatievarianten
* Transactierapporten inschakelen
* Rechten opgeven om een transactierapport te bekijken
* (Optioneel) Transactie-uitstelperiode en -uitvakken configureren [](/help/forms/using/installing-configuring-aem-forms-osgi.md)

>[!NOTE]
>
>* De transactierapporten van de Vormen AEM steunen geen topologieën die slechts publiceer instanties bevatten.
>* Voordat u transactierapportage gebruikt, moet u ervoor zorgen dat de omgekeerde replicatie is ingeschakeld voor alle publicatievarianten.
>* Transactiegegevens worden omgekeerd gerepliceerd van een publicatie-instantie naar alleen de overeenkomstige auteur of verwerkingsinstantie. De auteur of verwerkingsinstantie kan gegevens niet verder repliceren naar een andere instantie.
>



### Omgekeerde replicatie inschakelen voor alle publicatievarianten {#enable-reverse-replication-on-all-the-publish-instances}

Transactierapporten gebruiken omgekeerde replicatie om het aantal transacties van publicatie-instanties tot auteur-instanties te consolideren. Stel de omgekeerde replicatie in voor alle publicatieexemplaren. Voor gedetailleerde instructies aan opstellings omgekeerde replicatie, zie [replicatie](/help/sites-deploying/replication.md).

### Transactierapporten inschakelen {#enable-transaction-reports}

Transactierapporten zijn standaard uitgeschakeld. U kunt de rapporten van de Console van het Web van AEM toelaten. Als u transactierapporten wilt inschakelen in een omgeving van AEM Forms, voert u de volgende stappen uit op alle auteur- en publicatieinstanties:

1. Meld u als beheerder aan bij een AEM-instantie. Ga naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek en open de service **Forms Transaction Reporting** .
1. Schakel het selectievakje Transacties opnemen in. Click **Save**.

   Herhaal stap 1-3 voor alle auteur en publiceer instanties.

### Rechten opgeven om een transactierapport te bekijken {#provide-rights-to-view-a-transaction-report}

Alleen leden van de groep fd-administrator kunnen transactierapporten weergeven. Om een gebruiker toe te staan om transactierapporten te bekijken, maak gebruikerslid van de fd-beheerder groep. Voor instructies over het maken van een gebruiker tot lid van een groep AEM, zie het Beleid van de Rechten van de [Gebruiker, van de Groep en van de Toegang](/help/sites-administering/user-group-ac-admin.md).

### (Optioneel) Transactie-uitstelperiode en -uitvakken configureren {#optional-configure-transaction-flush-period-and-outboxes}

Transacties worden in het geheugen opgeslagen voordat ze worden opgeslagen in de opslagplaats. Standaard is de cacheperiode (Transactie Flush Period) ingesteld op 60 seconden. Voer de volgende stappen uit om de standaardcaching periode te veranderen:

1. Meld u als beheerder aan bij de instanties van de auteur. Ga naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek en open de **Forms Transaction Repository Storage Provider** -service.
1. Geef het aantal seconden op in het veld **Transactie-uitstelperiode** . Click **Save**.

De omgekeerde replicatie kopieert transactiegegevens aan standaardoutbox van de auteursinstanties. U kunt transactiegegevens in een douane outbox plaatsen. Voer de volgende stappen uit om een aangepast outbox te specificeren:

1. Meld u als beheerder aan bij de instanties van de auteur. Ga naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek en open de **Forms Transaction Repository Storage Provider** -service.
1. Geef de naam op van het aangepaste Postvak UIT in het veld **Postvakken** . Click **Save**. Er wordt een uitsnijdvak met de opgegeven naam gemaakt op alle instanties van de auteur.

## Het transactierapport weergeven {#viewing-the-transaction-report}

U kunt transactierapporten weergeven over auteur- of publicatieinstanties. Het transactierapport over de auteurinstantie verstrekt een bijeengevoegde som van alle transacties die op de gevormde auteur en publiceer instanties plaatsvinden. Het transactierapport over de publicatie-instantie bevat een telling van transacties die alleen op de onderliggende publicatie-instantie plaatsvinden. Voer de volgende stappen uit om het rapport te bekijken:

1. Meld u aan bij de AEM Forms-server op `https://[hostname]:'port'`.
1. Navigeer naar **Gereedschappen** > **Formulieren**>**Transactierapport** weergeven.

## Het rapport begrijpen {#understanding-the-report}

AEM vormt toont transactierapporten sinds de gevormde datum, zoals aangetoond in een samenvattingsrapport hieronder:

![sample-transaction-report-auteur](assets/sample-transaction-report-author.png)

* Met de opties **De datum opnieuw instellen op vandaag** kunt u transactierecords opnieuw instellen. Wanneer u de datum aan vandaag terugstelt, worden alle vorige transactieverslagen verloren. Wanneer u de datum op een auteurinstantie terugstelt, beïnvloedt de verandering geen transactierapporten over de Publish instanties en omgekeerd.
* Gebruik de transacties van de **Show van slechts publiceren instanties** om alle transacties te bekijken die slechts op gevormde publiceer instantie voorkwamen of landbouwbedrijf publiceren.
* Gebruik de categorieën: Verwerkt **** document, gerenderde **** documenten en **formulieren die zijn verzonden** om de bijbehorende transacties weer te geven. Voor het type transacties die in deze categorieën worden geboekt, zie [Billable Transactie Reports APIs](../../forms/using/transaction-reports-billable-apis.md).

## Logboeken voor transactierapporten weergeven {#view-transaction-reporting-logs}

Transactierapportering plaatst alle informatie die in het rapport wordt weergegeven en enkele aanvullende informatie in de logboeken. De informatie in de logboeken is nuttig voor de gevorderde gebruikers. Bijvoorbeeld, verdelen de logboeken transacties in veelvoudige granulaire categorieën in vergelijking met drie geconsolideerde categorieën die in het rapport worden getoond. De logbestanden vindt u op /crx-quickstart/logs/aem-forms-transaction.log.

## Verwante artikelen {#related-articles}

* [Overzicht van transactierapporten](../../forms/using/transaction-reports-overview.md)
* [Transactierapporten Billable API&#39;s](../../forms/using/transaction-reports-billable-apis.md)
* [Een transactie opnemen voor aangepaste implementaties](/help/forms/using/record-transaction-custom-implementation.md)

