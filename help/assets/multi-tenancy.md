---
title: Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen
description: Leer hoe u met de functie voor meerdere huurders inhoud in de CRX-opslagplaats kunt scheiden op basis van de organisatie van de klant om ongeoorloofde toegang te voorkomen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Met de functie voor meerdere huurders kunt u inhoud in CRX segregeren op basis van het organisatievoorvoegsel en de organisatie-id om de inhoud te beschermen tegen ongeoorloofde toegang door gebruikers van andere organisaties.

[!DNL Adobe Experience Manager Assets] slaat gegevens voor elke organisatie in een verschillend weg op. Elk organisatiespecifiek pad wordt geïdentificeerd door het organisatievoorvoegsel en organisatie-id
die is opgenomen op de traditionele locatie waar verschillende soorten activa worden opgeslagen in CRX.

Als u bijvoorbeeld een map maakt met de naam `Demo`, slaat [!DNL Experience Manager] elementen traditioneel de map op in `../content/dam/Demo`. Als multi-tenancy wordt ingeschakeld, kunt u de gegevens nu opslaan op `../content/dam/<organization prefix>/<organization id>Demo`

Als voor [!DNL Adobe Marketing Cloud] gebruikers van [!DNL Assets] (op bestelling) die aan de organisatie `aodpremium` worden toegewezen, kunt u de multi-huidseigenschap bijvoorbeeld gebruiken om `../content/dam/<mac>/<aodpremium>Demo` weg te vormen om hun inhoud te segregeren. In dit voorbeeld is `mac` het voorvoegsel van de organisatie en `aodpremium` is de organisatie-id.

Gebaseerd op de organisatie en identiteitskaart van de gebruiker, wordt dit gekwalificeerde weg getoond in de [!DNL Assets] interface en diverse tovenaars, met inbegrip van de Beweging en de verwezenlijking van het Fragment tovenaars om segregatie af te dwingen.

Met de functie Multi-tenancy kunt u de volgende typen elementen en componenten scheiden:

* Verzamelingen
* Openbare verzamelingen
* Catalogi (inclusief de wizard Pagina toevoegen/selecteren)
* Sjablonen
* Fragmentsjablonen
* Lichtbak
