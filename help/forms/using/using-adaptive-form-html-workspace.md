---
title: Een adaptief formulier gebruiken in HTML Workspace
description: Leer hoe u een adaptief formulier gebruikt in de HTML Workspace waarmee veldwerkers het formulier op hun apparaten kunnen openen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 15b9ae98-059f-4bf7-bfdd-9cfeb8eb30a4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Workbench
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Een adaptief formulier gebruiken in HTML Workspace{#using-an-adaptive-form-in-html-workspace}

AEM Forms on JEE biedt de mogelijkheid om een adaptief formulier te gebruiken in HTML Workspace.

Aangezien u tijdens het ontwerpen van processen een XDP kunt selecteren, is de mogelijkheid om vanuit een bestaande adaptieve AEM opslagplaats te bladeren toegevoegd. De mogelijkheid biedt de Process Designer de mogelijkheid om een adaptief formulier te configureren in Startpunt en Taken.

## Procesontwerpervaring {#process-design-experience}

Voer het volgende uit om het gebruik van adaptieve formulieren in procesontwerp mogelijk te maken:

* In Taak toewijzen en Beginpunt kunt u naar een adaptief formulierelement in de CRX-opslagruimte bladeren wanneer u een formulierelement aan een taak toewijst.
* In het Werkbalkeigenschappenblad Taak/beginpunt toewijzen kunt u de werkbalk op hoofdniveau/globaal van een adaptief formulier verbergen.
* U kunt nieuwe actieprofielen gebruiken voor het renderen en verzenden van handelingen in adaptieve formulieren.

### Exporteren en importeren van LiveCycles {#livecycle-application-export-and-import}

Omdat adaptieve formulieren zich in de AEM opslagplaats bevinden, bevat de export van de LiveCycle-toepassing alleen de referenties voor gebruikte adaptieve formulieren. Daarom is de uitvoer en de invoer van de toepassing van de LiveCycle een proces in twee stappen. De toepassing van het LiveCycle omvat procesdefinities, etc. Een afzonderlijk pakket met adaptieve formulieren wordt vanuit AEM geëxporteerd als een ZIP-bestand. Tijdens het importeren wordt de toepassing LiveCycle geïmporteerd via Workbench en worden adaptieve formulieren geïmporteerd via AEM.

## Gebruikerservaring met adaptief formulier in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace biedt naast de besturingselementen voor mobiele formulieren ook enkele adaptieve formulierspecifieke besturingselementen. Een gebruiker kan bijlagen toevoegen, opslaan, ondertekenen, verzenden en in de HTML Workspace door de aangepaste formulieren navigeren wanneer de gebruiker een taak of beginpunt opent. Hieronder worden de specifieke kenmerken beschreven:

1. Als u bestanden wilt bijvoegen, gebruikt u Taakbijlagen, net als bij Mobile Forms. Een knop van het type bestandsbijlage van het adaptieve formulier is verborgen.

1. Als u een aangepast formulier wilt opslaan, klikt u op **Opslaan**, zoals ook het geval was in Mobile Forms. Elke knop voor het type Opslaan van het adaptieve formulier is verborgen.

1. Als u een adaptief formulier wilt verzenden, gebruikt u de **Verzenden** beschikbare knop- of routeacties, zoals het geval was in Mobile Forms. De knop Verzendtype van het adaptieve formulier is verborgen.

1. **Zichtbaarheid van de werkbalk Adaptief formulier wereldwijd**: Als Process Designer de algemene werkbalk/werkbalk op hoofdniveau verbergt, worden de werkbalk en de knoppen niet weergegeven op adaptieve formulieren.

1. **Workspace navigation controls for Adaptive Forms**: De knoppen Volgende/Vorige zijn beschikbaar samen met de knoppen Opslaan, Verzenden en Route Handeling voor een adaptief formulier in de HTML Workspace. Klik op de knoppen Volgende/Vorige om door de deelvensters met adaptieve formulieren te navigeren in de HTML Workspace. De knoppen Volgende/Vorige bieden diepgaande navigatie, vergelijkbaar met navigatiebesturingselementen in de weergave Mobiel van adaptieve formulieren.

1. **eSign Services en Samenvattingscomponent van adaptief formulier**: De component Summary is niet operationeel in de werkruimte HTML. Met andere woorden, als een adaptief formulier een overzichtscomponent heeft, is het niet zichtbaar in de werkruimte. In plaats van Automatisch verzenden in de component E-sign, klikt de werkruimteconstructie de Submit of een routeactie in de Werkruimte van de HTML. Nadat een document is ondertekend, is het zichtbaar als een vlak ondertekend document. Klikken **Verzenden** of een routeactie zodat kunt u de taak of het Punt van het Begin sluiten/voltooien.\
   Het ondertekende document wordt verzameld van de eSign-serviceserver en het data-xml-bestand wordt doorgestuurd naar de volgende stap in het proces.

## Stappen voor het gebruik van adaptieve formulieren in procesontwerp {#steps-to-use-adaptive-forms-in-process-design}

1. Open Adobe Experience Manager Forms Workbench.

1. Ga naar **Bestand > Nieuw > Toepassing** of gebruik de bestaande toepassing om een toepassing te maken.

   ![Nieuwe toepassing maken](assets/create_new_appl.png)

   Toepassing maken

1. Maak een proces of gebruik een bestaand proces in de toepassing.

   ![Nieuw proces maken](assets/create_new_process.png)

   Proces maken

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
