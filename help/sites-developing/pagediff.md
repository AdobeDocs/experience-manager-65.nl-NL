---
title: Developing and Page Diff
seo-title: Developing and Page Diff
description: 'null'
seo-description: 'null'
uuid: 06f27bc2-f42a-4176-ab94-255e721c6933
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 6612f89d-c518-4e5a-8df1-6487cc330a9a
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Developing and Page Diff{#developing-and-page-diff}

## Overzicht van functies {#feature-overview}

Het maken van inhoud is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina met een vorige versie naast elkaar kunnen vergelijken met de gemarkeerde verschillen.

Met het paginagecheidingsteken kan de gebruiker de huidige pagina vergelijken met opstarters, vorige versies, enzovoort. Zie [Pagina Diff](/help/sites-authoring/page-diff.md)voor meer informatie over deze gebruikersfunctie.

## Bewerkingsdetails {#operation-details}

Wanneer u versies van een pagina vergelijkt, wordt de vorige versie die de gebruiker wil vergelijken opnieuw gemaakt door AEM op de achtergrond om het afschuiven te vergemakkelijken. Dit is nodig om de inhoud [voor vergelijking](/help/sites-developing/pagediff.md#operation-details)naast elkaar te kunnen weergeven.

Deze recreatiebewerking wordt intern door AEM uitgevoerd en is transparant voor de gebruiker en vereist geen interventie. Nochtans zou een beheerder die de bewaarplaats bijvoorbeeld in CRX DE Lite bekijkt deze ontspannen versies binnen de inhoudsstructuur zien.

Wanneer de inhoud wordt vergeleken, wordt de hele structuur tot aan de te vergelijken pagina opnieuw gemaakt op de volgende locatie:

`/tmp/versionhistory/`

Er wordt automatisch een opschoningstaak uitgevoerd om deze tijdelijke inhoud op te schonen.

## Permissions {#permissions}

Eerder, in Klassieke UI, moest de speciale ontwikkelingsoverweging worden gemaakt om AEM verschil (zoals het gebruiken van `cq:text` markeringslib, of douane te vergemakkelijken die de dienst `DiffService` OSGi in componenten integreert) te vergemakkelijken. Dit is niet meer nodig voor de nieuwe functie voor Diff, aangezien het diff cliënt-kant via DOM vergelijking voorkomt.

Er zijn echter een aantal beperkingen die door de ontwikkelaar in overweging moeten worden genomen.

* Deze functie gebruikt CSS-klassen die geen naamruimte hebben met het AEM-product. Als andere aangepaste CSS-klassen of CSS-klassen van derden met dezelfde namen op de pagina worden opgenomen, kan dit van invloed zijn op de weergave van het diff.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Omdat het diff cliënt-kant is en op paginading uitvoert, zullen om het even welke aanpassingen aan DOM nadat de cliënt-zijdiff dienst is in werking gesteld niet administratief worden verwerkt. Dit kan

   * Componenten die AJAX gebruiken om inhoud op te nemen
   * Toepassingen voor één pagina
   * Op JavaScript gebaseerde componenten die het DOM op gebruikersinteractie manipuleren.
