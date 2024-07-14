---
title: Opvallende wijzigingen in de CIF
description: Notable veranderingen van het Commerce integration framework (CIF) toe:voegen-on in vergelijking met oude CIF versies.
exl-id: 41dee21a-9ae2-4067-a32a-2d4633323fc4
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Notable Changes to the Commerce integration framework (CIF) add-on{#notable-changes}

Dit document benadrukt de belangrijke verschillen tussen de Commerce integration framework (CIF) toe:voegen-op en oude CIF versies, die hoofdzakelijk als CIF Klassiek (QuickStart) en CIF open-source worden bekend.

## Installatie en updates

Het AEM CIF add-on pakket wordt geïnstalleerd en bijgewerkt met AEM Package Manager.

**Vorige CIF versies**

* CIF Klassiek: Geen installatie nodig, CIF maakte deel uit van de QuickStart. CIF updates maakten deel uit van regelmatige AEM- of servicepack-updates
* CIF Open-source: Installatie via GitHub. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.

## Eindpuntconfiguratie

Het eindpunt wordt gevormd via console OSGi.

**Vorige CIF versies**

* CIF Klassiek: Via OSGi configuratie in AEM
* CIF Open-source: via CIF Configuration Browser

## Invoering van CIF Venia-project

Project beschikbaar op [ GitHub AEM Guides - CIF Project van Venia ](https://github.com/adobe/aem-cif-guides-venia) en plaatsing die via AEM Manager van het Pakket wordt gedaan.

**Vorige CIF versies**

* CIF Classic: via AEM pakketinstallatie

## Productcatalogusgegevens

De catalogusgegevens van het product worden gevraagd op bestelling via vraag in real time aan een extern eindpunt dat vereiste GraphQL APIs steunt. Deze API&#39;s ondersteunen toegang tot live- of gefaseerde gegevens op een bepaalde datum. Geen replicatie nodig.

**Vorige CIF versies**

* CIF Klassiek: live en gefaseerde productgegevens worden geïmporteerd en in de JCR gecontinueerd op AEM auteur via volledige of delta productimport. Live productgegevens worden gerepliceerd naar AEM Publish.

## De catalogus van het product ervaart met AEM teruggeven

AEM geeft de ervaringen van de productcatalogus direct weer met behulp van AEM catalogussjablonen die zijn toegewezen aan producten en categorieën. Geen replicatie nodig.

**Vorige CIF versies**

* CIF Klassiek: AEM auteur maakt een AEM pagina voor elke categorie/elk product met het gereedschap Catalogusblauwdruk. Deze pagina&#39;s worden gerepliceerd naar AEM Publish.

>[!NOTE]
>
>Voor extra documentatie op hoe te om CIF met AEM Beheerde Dienst of AEM te gebruiken On-Premise, zie [ Commerce integration framework ](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
