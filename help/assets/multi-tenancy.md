---
title: Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen
description: Leer hoe u met de functie voor meerdere huurders inhoud in de CRX-opslagplaats kunt scheiden op basis van de organisatie van de klant om ongeoorloofde toegang te voorkomen.
contentOwner: AG
role: Architect, Admin, Leader
feature: Collections
exl-id: f95560c9-f1b9-4e86-94a7-70347d268d8f
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Met de functie voor meerdere huurders kunt u inhoud in CRX segregeren op basis van het organisatievoorvoegsel en de organisatie-id om de inhoud te beschermen tegen ongeoorloofde toegang door gebruikers van andere organisaties.

[!DNL Adobe Experience Manager Assets] slaat gegevens voor elke organisatie in een verschillend weg op. Elk organisatiespecifiek pad wordt geïdentificeerd door het organisatievoorvoegsel en de organisatie-id die zijn opgenomen in de traditionele locatie waar verschillende typen elementen worden opgeslagen in CRX.

Als u bijvoorbeeld een map maakt met de naam `Demo`, [!DNL Experience Manager] elementen slaan de map traditioneel op `../content/dam/Demo`. Als multi-tenancy is ingeschakeld, kunt u de gegevens nu opslaan op `../content/dam/<organization prefix>/<organization id>Demo`

Als bijvoorbeeld [!DNL Adobe Marketing Cloud] gebruikers van [!DNL Assets] (op verzoek) die aan `aodpremium` organisatie, kunt u de multi-huur eigenschap gebruiken om te vormen `../content/dam/<mac>/<aodpremium>Demo` pad om de inhoud te scheiden. In dit voorbeeld: `mac` is het organisatievoorvoegsel en `aodpremium` is de organisatie-id.

Gebaseerd op de organisatie en identiteitskaart van de gebruiker, wordt dit gekwalificeerde weg getoond in [!DNL Assets] interface en diverse tovenaars, met inbegrip van de Beweging en de verwezenlijking van het Fragment tovenaars om segregatie af te dwingen.

Met de functie Multi-tenancy kunt u de volgende typen elementen en componenten scheiden:

* Verzamelingen
* Openbare verzamelingen
* Catalogi (inclusief de wizard Pagina toevoegen/selecteren)
* Sjablonen
* Fragmentsjablonen
* Lichtbak
