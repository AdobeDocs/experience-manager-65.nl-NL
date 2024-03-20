---
title: Developing and Page Diff
description: Leer hoe u de functie page diff in Adobe Experience Manager kunt ontwikkelen en gebruiken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: b07134b2-074a-4d52-8d0c-7e7abe51fc3a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Developing and Page Diff{#developing-and-page-diff}

## Overzicht van functies {#feature-overview}

Inhoud maken is een herhalend proces. Om efficiënt te kunnen ontwerpen moet u kunnen zien wat er van de ene iteratie naar de andere is veranderd. Het weergeven van de ene pagina en de andere is inefficiënt en vatbaar voor fouten. Een auteur wil de huidige pagina met een vorige versie naast elkaar kunnen vergelijken met de gemarkeerde verschillen.

Met het paginagecheiding kan de gebruiker de huidige pagina vergelijken met opstarters, vorige versies enzovoort. Zie voor meer informatie over deze gebruikersfunctie [Pagina grijs](/help/sites-authoring/page-diff.md).

## Bewerkingsdetails {#operation-details}

Wanneer u versies van een pagina vergelijkt, wordt de vorige versie die de gebruiker wenst te vergelijken, op de achtergrond opnieuw gemaakt door AEM om het afschuiven te vergemakkelijken. Dit is nodig om de inhoud te kunnen renderen [voor vergelijking naast elkaar](/help/sites-developing/pagediff.md#operation-details).

Deze recreatiebewerking wordt intern AEM uitgevoerd en is transparant voor de gebruiker en vereist geen interventie. Een beheerder die de gegevensopslagruimte bijvoorbeeld in CRXDE Lite bekijkt, ziet deze opnieuw gemaakte versies echter wel binnen de inhoudsstructuur.

Wanneer de inhoud wordt vergeleken, wordt de hele structuur tot aan de te vergelijken pagina opnieuw gemaakt op de volgende locatie:

`/tmp/versionhistory/`

Er wordt automatisch een opschoningstaak uitgevoerd om deze tijdelijke inhoud op te schonen.

## Machtigingen {#permissions}

Eerder moest in de klassieke gebruikersinterface speciale aandacht worden besteed aan de ontwikkeling om AEM verschillen te vergemakkelijken (zoals het gebruik van `cq:text` tag lib, of aangepaste integratie van de `DiffService` OSGi-service in componenten). Dit is niet meer nodig voor de nieuwe functie voor Diff, aangezien het diff cliënt-kant via DOM vergelijking voorkomt.

Er zijn echter enkele beperkingen die door de ontwikkelaar in overweging moeten worden genomen.

* Deze functie gebruikt CSS-klassen die geen naamruimte hebben voor het AEM Product. Als andere aangepaste CSS-klassen of CSS-klassen van derden met dezelfde namen op de pagina worden opgenomen, kan dit van invloed zijn op de weergave van het diff.

   * `html-added`
   * `html-removed`
   * `cq-component-added`
   * `cq-component-removed`
   * `cq-component-moved`
   * `cq-component-changed`

* Omdat het diff cliënt-kant is en op paginading uitvoert, zullen om het even welke aanpassingen aan DOM nadat de cliënt-zijdiff dienst is in werking gesteld niet administratief worden verwerkt. Dit kan

   * Componenten die AJAX gebruiken om inhoud op te nemen
   * Toepassingen voor één pagina
   * JavaScript-componenten die het DOM op gebruikersinteractie manipuleren.

>[!NOTE]
>
>De vergelijkingsfunctie voor paginascheidingen werkt alleen voor de componenten die geldige knooppunten cq:editConfig hebben.
