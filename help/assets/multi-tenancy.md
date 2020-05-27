---
title: Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen
description: Leer hoe u met de functie voor meerdere huurders inhoud in de CRX-opslagplaats kunt scheiden op basis van de organisatie van de klant om ongeoorloofde toegang te voorkomen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Met de functie voor meerdere huurders kunt u inhoud in CRX segregeren op basis van het organisatievoorvoegsel en de organisatie-id om de inhoud te beschermen tegen ongeoorloofde toegang door gebruikers van andere organisaties.

In Adobe Experience Manager-middelen worden gegevens voor elke organisatie opgeslagen in een ander pad. Elk organisatiespecifiek pad wordt geïdentificeerd door het organisatievoorvoegsel en de organisatie-id die zijn opgenomen in de traditionele locatie waar verschillende typen elementen worden opgeslagen in CRX.

Als u bijvoorbeeld een map maakt met de naam `Demo`, slaat de Experience Manager-middelen de map traditioneel op in `../content/dam/Demo`. Als multi-tenancy is ingeschakeld, kunt u de gegevens nu opslaan op `../content/dam/<organization prefix>/<organization id>Demo`

Bijvoorbeeld, als voor [!DNL Adobe Marketing Cloud] gebruikers van Activa (op bestelling) die aan de `aodpremium` `../content/dam/<mac>/<aodpremium>Demo` organisatie worden toegewezen, kunt u de multi-huidseigenschap gebruiken om weg te vormen om hun inhoud te segregeren. In dit voorbeeld `mac` is dit het organisatievoorvoegsel en `aodpremium` is dit de organisatie-id.

Gebaseerd op de organisatie en identiteitskaart van de gebruiker, wordt dit gekwalificeerde weg getoond in de interface van Activa en diverse tovenaars, met inbegrip van de Beweging en de verwezenlijking van het Fragment tovenaars om segregatie af te dwingen.

Met de functie Multi-tenancy kunt u de volgende typen elementen en componenten scheiden:

* Verzamelingen
* Openbare verzamelingen
* Catalogi (inclusief de wizard Pagina toevoegen/selecteren)
* Sjablonen
* Fragmentsjablonen
* Lichtbak
