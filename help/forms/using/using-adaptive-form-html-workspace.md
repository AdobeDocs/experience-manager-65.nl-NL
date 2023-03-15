---
title: Een adaptief formulier gebruiken in HTML Workspace
seo-title: Using an adaptive form in HTML Workspace
description: Een adaptief formulier gebruiken in HTML Workspace
seo-description: Using an adaptive form in HTML Workspace
uuid: 473d5daf-a3ed-449f-9136-585755b59922
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 2b6875cd-2ee7-4aa8-90c7-d33583dc2f0e
docset: aem65
exl-id: 15b9ae98-059f-4bf7-bfdd-9cfeb8eb30a4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# Een adaptief formulier gebruiken in HTML Workspace{#using-an-adaptive-form-in-html-workspace}

AEM Forms on JEE biedt de mogelijkheid om een adaptief formulier te gebruiken in HTML Workspace.

Aangezien u tijdens het ontwerpen van processen een XDP kunt selecteren, is de mogelijkheid om vanuit een bestaande adaptieve AEM opslagplaats te bladeren toegevoegd. Het vermogen geeft de ontwerper van het Proces de capaciteit om een adaptief vorm in BeginPunt evenals in Taak te vormen.

## Procesontwerpervaring {#process-design-experience}

Voer het volgende uit om het gebruik van adaptieve formulieren in procesontwerp mogelijk te maken:

* In Taak toewijzen en Beginpunt kunt u naar een adaptief formulierelement in de CRX-opslagruimte bladeren wanneer u een formulierelement aan een taak toewijst.
* In de Werkbank Werkbank toewijzen aan taak/beginpunt kunt u de werkbalk op hoofdniveau/algemeen van een adaptief formulier verbergen.
* U kunt nieuwe actieprofielen gebruiken voor het renderen en verzenden van handelingen in adaptieve formulieren.

### LiveCycle-toepassing exporteren en importeren {#livecycle-application-export-and-import}

Omdat adaptieve formulieren zich in de AEM opslagplaats bevinden, bevat de export van de LiveCycle-toepassing alleen de referenties voor gebruikte adaptieve formulieren. Daarom is het exporteren en importeren van LiveCycle-toepassingen een proces in twee stappen. De toepassing LiveCycle bevat procesdefinities, enzovoort. Een afzonderlijk pakket met adaptieve formulieren wordt vanuit AEM geëxporteerd als een ZIP-bestand. Tijdens het importeren wordt de LiveCycle-toepassing geïmporteerd via Workbench en worden adaptieve formulieren geïmporteerd via AEM.

## Gebruikerservaring met adaptief formulier in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace biedt naast de besturingselementen die beschikbaar zijn voor mobiele formulieren ook enkele adaptieve formulierspecifieke besturingselementen. Een gebruiker kan bijlagen toevoegen, opslaan, ondertekenen, verzenden en in de HTML Workspace door de aangepaste formulieren navigeren wanneer de gebruiker een taak of beginpunt opent. Hieronder volgen de specifieke kenmerken:

1. Voor het bijvoegen van bestanden gebruikt u Taakbijlagen, net als bij Mobile Forms. Een knop van het type bestandsbijlage van het adaptieve formulier is verborgen.

1. Als u een aangepast formulier wilt opslaan, klikt u op **Opslaan**, zoals in Mobile Forms. Elke knop voor het type Opslaan van het adaptieve formulier is verborgen.

1. Als u een adaptief formulier wilt verzenden, gebruikt u de **Verzenden** beschikbare knop- of routeacties, zoals het geval was in Mobile Forms. De knop Verzendtype van het adaptieve formulier is verborgen.

1. **Zichtbaarheid van de werkbalk Adaptief formulier wereldwijd**: Als de procesontwerper de algemene werkbalk of de werkbalk op hoofdniveau verbergt, worden de werkbalk en de knoppen niet weergegeven op adaptieve formulieren.

1. **Workspace navigation controls for Adaptive Forms**: De knoppen Volgende/Vorige zijn beschikbaar samen met de knoppen Opslaan, Verzenden en Route Handeling voor een adaptief formulier in de HTML Workspace. Klik op de knoppen Volgende/Vorige om in de HTML Workspace te navigeren door deelvensters met adaptieve formulieren. De knoppen Volgende/Vorige bieden diepgaande navigatie, vergelijkbaar met navigatiebesturingselementen in de weergave Mobiel van adaptieve formulieren.

1. **eSign Services en Samenvattingscomponent van adaptief formulier**: De overzichtscomponent is niet operationeel in de Werkruimte van HTML. Met andere woorden, als een adaptief formulier een overzichtscomponent heeft, is het niet zichtbaar in de werkruimte. In plaats van Automatisch verzenden in de component Esign, klikt de werkruimteconstructie de Submit of een routeactie in de Werkruimte van de HTML. Nadat een document is ondertekend, is het zichtbaar als een vlak ondertekend document. Klikken **Verzenden** of een routeactie om de taak of het Punt van het Begin te sluiten/te voltooien.\
   Het ondertekende document wordt verzameld van de eSign-serviceserver en het data-xml-bestand wordt doorgestuurd naar de volgende stap in het proces.

## Stappen voor het gebruik van adaptieve formulieren in procesontwerp {#steps-to-use-adaptive-forms-in-process-design}

1. Open Adobe Experience Manager Forms Workbench.

1. Ga naar **Bestand > Nieuw > Toepassing** of gebruik de bestaande toepassing om een toepassing te maken.

   ![Nieuwe toepassing maken](assets/create_new_appl.png)

   Nieuwe toepassing maken

1. Maak een proces of gebruik een bestaand proces in de toepassing.

   ![Nieuw proces maken](assets/create_new_process.png)

   Nieuw proces maken

1. Creeer een Punt van het Begin of wijs Taak toe en klik het tweemaal.
1. Onder de **[!UICONTROL Presentation & Data]** sectie, selecteert u **[!UICONTROL use a CRX asset]** en klik op de ellipsen vóór het element.

   ![Een CRX-element gebruiken](assets/use_crx_asset.png)

   Een CRX-element gebruiken

1. Selecteer het aangepaste formulier dat u via de gebruikersinterface Middelen beheren hebt gemaakt en klik op **[!UICONTROL OK]**.

   ![Een adaptief formulier selecteren](assets/selecting_form.png)

   Een adaptief formulier selecteren

   >[!NOTE]
   >
   >Zie voor meer informatie over het maken van een adaptief formulier [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md).
   >
   >
   >Voor meer informatie over het maken van een proces raadpleegt u [Processen maken en beheren](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
