---
title: Opvallende wijzigingen van de add-on van het kader voor de integratie van de handel (CIF)
description: Opvallende wijzigingen van de add-on van het Commerce Integration Framework (CIF) in vergelijking met de oude CIF-versies.
exl-id: 5a526960-96a1-421e-9fb0-0825e7df8f32,c136763f-56aa-450e-8796-bc84bf6c205d
translation-type: tm+mt
source-git-commit: a8dba82029168660b84b085ab46d0406b19961ef
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Opvallende veranderingen in de toe:voegen-on{#notable-changes} van het Kader van de Integratie van de Handel (CIF)

In dit document worden de belangrijke verschillen tussen de add-on en oude CIF-versies van het kader voor de integratie van de handel (Commerce Integration Framework, CIF) belicht, die voornamelijk CIF Classic (Quickstart) en CIF Open-source worden genoemd.

## Installatie en updates

Het AEM cif-invoegpakket wordt geïnstalleerd en bijgewerkt met AEM pakketbeheer.

**Vorige CIF-versies**

* Klassiek CIF: Geen installatie nodig, CIF maakte deel uit van QuickStart. De updates van CIF maakten deel uit van regelmatige AEM of de updates van het de dienstpak
* CIF Open-source: Installatie via GitHub. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.

## Eindpuntconfiguratie

Het eindpunt wordt gevormd via console OSGi.

**Vorige CIF-versies**

* Klassiek CIF: Via OSGi-configuratie in AEM
* CIF Open-source: Via CIF Configuration Browser

## Plaatsing van het CIF-project van Venia

Project beschikbaar op [GitHub AEMGidsen - CIF Venia Project](https://github.com/adobe/aem-cif-guides-venia) en plaatsing via pakket AEM manager

**Vorige CIF-versies**

* Klassiek CIF: Via AEM

## Productcatalogusgegevens

De catalogusgegevens van het product worden gevraagd op bestelling via vraag in real time aan een extern eindpunt dat vereiste GraphQL APIs steunt. Deze API&#39;s ondersteunen toegang tot live- of gefaseerde gegevens op een bepaalde datum. Geen replicatie nodig.

**Vorige CIF-versies**

* Klassiek CIF: Live en gefaseerde productgegevens worden geïmporteerd en in de JCR voortgezet op AEM Author via volledige of delta productimport. Live-productgegevens worden gerepliceerd naar AEM Publish.

## De catalogus van het product ervaart met AEM teruggeven

AEM geeft de ervaringen van de productcatalogus direct weer met behulp van AEM catalogussjablonen die zijn toegewezen aan producten en categorieën. Geen replicatie nodig.

**Vorige CIF-versies**

* Klassiek CIF: AEM-auteur maakt een AEM pagina voor elke categorie/elk product met het gereedschap Catalogusblauwdruk. Deze pagina&#39;s worden gerepliceerd naar AEM Publish.

>[!NOTE]
>
>Raadpleeg [Commerce Integration Framework](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html) voor aanvullende documentatie over het gebruik van CIF met AEM Beheerde service of AEM On-premisse.
