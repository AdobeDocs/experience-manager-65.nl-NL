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
source-git-commit: 4ee3b99a3f0a5d37441eee76c3ec747afcf2e32e
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---


# Transactierapporten weergeven en begrijpen{#viewing-and-understanding-transaction-reports}

Met transactierapporten kunt u het aantal verzonden formulieren, verwerkte documenten en gerenderde documenten vastleggen en bijhouden. Het doel van het volgen van deze transacties is een geïnformeerde beslissing te nemen over het gebruik van producten en het opnieuw in evenwicht brengen van investeringen in hardware en software. Voor meer informatie, zie [Overzicht van de Rapporten van de Transactie van AEM Forms](../../forms/using/transaction-reports-overview.md).

## Transactierapporten {#setting-up-transaction-reports} instellen

De functie Transactierapporten is beschikbaar als onderdeel van het add-on pakket voor AEM formulieren. Zie [Formulieren installeren en configureren](/help/forms/using/installing-configuring-aem-forms-osgi.md) voor informatie over het installeren van het invoegpakket op alle auteur- en publicatieinstanties. Wanneer u het pakket voor de invoegtoepassing voor AEM formulieren hebt geïnstalleerd, gaat u als volgt te werk:

* Omgekeerde replicatie inschakelen voor alle publicatievarianten
* Transactierapporten inschakelen
* Rechten opgeven om een transactierapport te bekijken
* (Optioneel) Configureer Transactie Flush Period en Outboxes [](/help/forms/using/installing-configuring-aem-forms-osgi.md)

>[!NOTE]
>
>* AEM Forms-transactierapporten ondersteunen geen topologieën die alleen publicatieexemplaren bevatten.
>* Voordat u transactierapportage gebruikt, moet u ervoor zorgen dat de omgekeerde replicatie is ingeschakeld voor alle publicatievarianten.
>* Transactiegegevens worden omgekeerd gerepliceerd van een publicatie-instantie naar alleen de overeenkomstige auteur of verwerkingsinstantie. De auteur of verwerkingsinstantie kan gegevens niet verder repliceren naar een andere instantie.

>



### Omgekeerde replicatie inschakelen op alle publicatieexemplaren {#enable-reverse-replication-on-all-the-publish-instances}

Transactierapporten gebruiken omgekeerde replicatie om het aantal transacties van publicatie-instanties tot auteur-instanties te consolideren. Stel de omgekeerde replicatie in voor alle publicatieexemplaren. Voor gedetailleerde instructies aan opstelling omgekeerde replicatie, zie [replicatie](/help/sites-deploying/replication.md).

### Transactierapporten {#enable-transaction-reports} inschakelen

Transactierapporten zijn standaard uitgeschakeld. U kunt de rapporten van AEM Console van het Web toelaten. Als u transactierapporten wilt inschakelen in een AEM Forms-omgeving, voert u de volgende stappen uit op alle auteur- en publicatieinstanties:

1. Meld u als beheerder aan bij een AEM. Ga naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek en open de **Forms Transaction Reporting**-service.
1. Schakel het selectievakje Transacties opnemen in. Klik **Opslaan**.

   Herhaal stap 1-3 voor alle auteur en publiceer instanties.

### Rechten opgeven om een transactierapport {#provide-rights-to-view-a-transaction-report} weer te geven

Alleen leden van de groep fd-administrator kunnen transactierapporten weergeven. Om een gebruiker toe te staan om transactierapporten te bekijken, maak gebruikerslid van de fd-beheerder groep. Voor instructies over het maken van een gebruiker tot lid van een AEM groep, zie [Gebruiker, Groep en het Beleid van de Rechten van de Toegang](/help/sites-administering/user-group-ac-admin.md).

### (Optioneel) Configureer Transactie Flush Period en Outboxes {#optional-configure-transaction-flush-period-and-outboxes}

Transacties worden in het geheugen opgeslagen voordat ze worden opgeslagen in de opslagplaats. Standaard is de cacheperiode (Transactie Flush Period) ingesteld op 60 seconden. Voer de volgende stappen uit om de standaardcaching periode te veranderen:

1. Meld u als beheerder aan bij de instanties van de auteur. Ga naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek en open de service **Forms Transaction Repository Storage Provider**.
1. Geef het aantal seconden op in het veld **Transactie doorspoelen**. Klik **Opslaan**.

De omgekeerde replicatie kopieert transactiegegevens aan standaardoutbox van de auteursinstanties. U kunt transactiegegevens in een douane outbox plaatsen. Voer de volgende stappen uit om een aangepast outbox te specificeren:

1. Meld u als beheerder aan bij de instanties van de auteur. Ga naar **Gereedschappen** > **Bewerkingen** > **Webconsole**.
1. Zoek en open de service **Forms Transaction Repository Storage Provider**.
1. Geef de naam op van het aangepaste uitvoervak in het veld **Outboxes**. Klik **Opslaan**. Er wordt een uitsnijdvak met de opgegeven naam gemaakt op alle instanties van de auteur.

## Het transactierapport {#viewing-the-transaction-report} weergeven

U kunt transactierapporten weergeven over auteur- of publicatieinstanties. Het transactierapport over de auteurinstantie verstrekt een bijeengevoegde som van alle transacties die op de gevormde auteur en publiceer instanties plaatsvinden. Het transactierapport over de publicatie-instantie bevat een telling van transacties die alleen op de onderliggende publicatie-instantie plaatsvinden. Voer de volgende stappen uit om het rapport te bekijken:

1. Meld u aan bij de AEM Forms-server op `https://[hostname]:'port'`.
1. Navigeer naar **Tools** > **Forms****Transactierapport weergeven**.

## Het rapport {#understanding-the-report}

AEM Forms geeft transactierapporten weer sinds de geconfigureerde datum, zoals in een samenvattingsrapport hieronder wordt getoond:

![sample-transaction-report-auteur](assets/sample-transaction-report-author.png)

* Gebruik de **Herstel de datum aan vandaag** opties om transactieverslagen terug te stellen. Wanneer u de datum aan vandaag terugstelt, worden alle vorige transactieverslagen verloren. Wanneer u de datum op een auteurinstantie terugstelt, beïnvloedt de verandering geen transactierapporten over de Publish instanties en omgekeerd.
* Gebruik **Show transacties van slechts Publish instanties** om alle transacties te bekijken die slechts op gevormde publiceer instantie voorkwamen of landbouwbedrijf publiceren.
* Gebruik de categorieën: **Document verwerkt**, **Gerenderde documenten** en **Forms verzonden** om de bijbehorende transacties weer te geven. Zie [Billable Transaction Reports APIs](../../forms/using/transaction-reports-billable-apis.md) voor het type transacties dat in deze categorieën wordt verantwoord.

## Logbestanden voor transactierapportage weergeven {#view-transaction-reporting-logs}

Transactierapportering plaatst alle informatie die in het rapport wordt weergegeven en enkele aanvullende informatie in de logboeken. De informatie in de logboeken is nuttig voor de gevorderde gebruikers. Bijvoorbeeld, verdelen de logboeken transacties in veelvoudige granulaire categorieën in vergelijking met drie geconsolideerde categorieën die in het rapport worden getoond. De logbestanden zijn beschikbaar in het `error.log`-bestand in de map `/crx-repository/logs/`. De logboeken zijn beschikbaar zelfs als u de transactierapporten van AEM Console van het Web niet toelaat.

## Verwante artikelen {#related-articles}

* [Overzicht van transactierapporten](../../forms/using/transaction-reports-overview.md)
* [Transactierapporten Billable API&#39;s](../../forms/using/transaction-reports-billable-apis.md)
* [Een transactie opnemen voor aangepaste implementaties](/help/forms/using/record-transaction-custom-implementation.md)

