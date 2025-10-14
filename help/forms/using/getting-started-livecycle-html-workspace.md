---
title: Aan de slag met de AEM Forms-werkruimte
description: Hoe te beginnen met het gebruiken van de werkruimte van AEM Forms van het LiveCycle om uw bedrijfsautomatiseringsprocessen te beheren.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: d2a962b6-16be-4866-a856-5064f81c9610
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---

# Aan de slag met de AEM Forms-werkruimte {#getting-started-with-aem-forms-workspace}

U kunt de werkruimte van AEM Forms gebruiken om de volgende taken uit te voeren:

* Een bedrijfsproces starten
* De mening en handelt op taken die aan u of aan andere te doen lijsten worden toegewezen die u toegang hebt tot
* De taken van het spoor die deel van de processen uitmaken u begon of aan participeerde

## Navigeren in de AEM Forms-werkruimte {#navigating-html-workspace}

Afhankelijk van het proces en de taak waaraan u werkt, worden verschillende items in de gebruikersinterface van de AEM Forms-werkruimte weergegeven. U kunt de tabbladen Overzicht, Forms, Details, Historie, Bijlagen of Notities, of alle knoppen die in deze Help worden beschreven, al dan niet altijd zien.

U kunt op een van de volgende manieren navigeren in de gebruikersinterface van de AEM Forms-hoofdwerkruimte:

* Klik op de items in de bovenste navigatiebalk voor de opties Start Process, To-do (Proces starten), Voorkeuren, Tracking (Bijhouden), Help en Logout (Afmelden).
* Klik op het tabblad Proces starten, Op-maken of Tekstspatiëring voor toegang tot de drie hoofdwerkgebieden.
* Klik op de tabbladen Proces starten, Te doen en Tekstspatiëring op de items in de lijst in het linkerdeelvenster om toegang te krijgen tot favorieten, procescategorieën, zoeksjablonen, concepten of toegewezen taken. Gebruik de schuifbalk om extra items in de lijst weer te geven.
* Alle actieknoppen (goedkeuren, Afwijzen, Vooruit, Consult, Vergrendelen en Delen) tonen in zowel het document als de Eigendom.
* Klik op het pictogram Alle opties op de navigatiebalk, onder aan de pagina, om de taak door te sturen naar een andere gebruiker, om de taak te delen met een andere gebruiker, om over de taak te raadplegen met een andere gebruiker of om de taak te vergrendelen.
* Selecteer op het tabblad Historie een taak om de tabbladen Bijlagen en Toewijzingen voor die taak weer te geven.
* Gebruik de tabtoets, de pijltoetsen en de spatiebalk om zonder muis door de werkruimte van AEM Forms te navigeren.

## De AEM Forms-werkruimte gebruiken met schermlezers {#using-html-workspace-with-screen-readers}

De AEM Forms-werkruimte is een webtoepassing voor HTML en is compatibel met schermlezers. U kunt met het toetsenbord navigeren door de AEM Forms-werkruimteinterface.

Houd rekening met het volgende als u de AEM Forms-werkruimte met een schermlezer wilt gebruiken:

* AEM Forms-werkruimte is een standaardtoepassing voor HTML die voldoet aan een standaardprogramma voor schermlezers. U hebt geen specifiek script nodig om een schermlezergereedschap uit te voeren.
* Alle navigatie in de AEM Forms-werkruimte verloopt via ankerlabels, die gemakkelijk toegankelijk zijn via tabs.
* Forms kan een paar seconden duren om te laden. De schermlezer geeft geen hoorbare melding dat het formulier wordt geladen en dat u moet wachten.

## Navigeren door de AEM Forms-werkruimte met een toetsenbord {#navigating-html-workspace-using-a-keyboard}

Wanneer u in de AEM Forms-werkruimte navigeert met een toetsenbord, voldoet de navigatie aan de toegankelijkheidsconventies voor HTML. In bepaalde situaties volgt de tabvolgorde niet de gebruikelijke conventionele volgorde. Met de volgende tips kunt u door de interface navigeren:

* Als er problemen optreden met de Tab-toets boven aan de browser, drukt u op Ctrl+Tab om met Tab naar de inhoud van het browservenster te gaan.
* De Help van de AEM Forms-werkruimte wordt in een apart browservenster geopend. Nadat u de Help hebt weergegeven, keert de focus terug naar het browservenster dat de AEM Forms-werkruimte bevat. Het menu Help blijft gefocust wanneer de focus terugkeert.
* Wanneer u een formulier opent om een proces te starten of een taak te voltooien, blijft de focus bij het bestaande element en verandert de focus niet in het formulier. Gebruik tab om de focus naar het formulier te verplaatsen en er doorheen te bladeren. De tabvolgorde door het formulier is afhankelijk van het type en het ontwerp van het formulier.

  Wanneer u in PDF forms met de Tab-toets tot het einde van het formulier gaat of het formulier verzendt, springt de cursorfocus naar de adresbalk van de browser. Tik nogmaals door de menu&#39;s (maar niet door het hele formulier) om naar de knoppen voor formulierhandelingen te gaan, zoals Opslaan als concept en Voltooien. Als het formulier nog steeds geopend is, kunt u ook met de Tab-toets voorbij de knoppen heen en weer in het formulier gaan.

## Voorkeuren beheren {#managing-preferences}

U kunt de verschillende voorkeuren voor de AEM Forms-werkruimte in de volgende categorieën instellen:

**uit Bureau:** plaats voorkeur om te controleren hoe de taken aan andere mensen worden toegewezen terwijl u uit het bureau bent. Zie [&#x200B; Plaatsende uit-van-bureauvoorkeur &#x200B;](todo-lists.md#setting-out-of-office-preferences).

**Lijsten:** plaats voorkeur voor het delen van uw te doen lijst met andere gebruikers of voor het verzoeken van toegang tot de lijst van een andere gebruiker. Zie [&#x200B; Werkend met taken van groep en gedeelde rijen &#x200B;](todo-lists.md#working-with-tasks-from-group-and-shared-queues).

**Montages UI:** plaats voorkeur voor hoe u met de werkruimte van AEM Forms in wisselwerking staat. Zie [&#x200B; plaatsen gebruikersinterfacevoorkeur &#x200B;](#set-user-interface-preferences).

### Gebruikersinterfacevoorkeuren instellen {#set-user-interface-preferences}

Stel de voorkeuren voor de gebruikersinterface in op het tabblad Voorkeuren > UI-instellingen. De volgende voorkeuren zijn beschikbaar.

* **Plaats van het Begin:** specificeert de pagina die wanneer u login aan de werkruimte van AEM Forms verschijnt. De vier beschikbare opties zijn Start Process, To Do, Tracking en Favorites.
* **LogoutVragen:** specificeert of u wordt ertoe aangezet om te bevestigen dat u zich wilt afmelden nadat u Logout klikt.
* **Formaat van de Datum:** specificeert het formaat van de datumvertoning dat over de werkruimte van AEM Forms wordt gebruikt.
* **Formaat van de Tijd**: Specificeert het formaat van de tijdvertoning dat over de werkruimte van AEM Forms wordt gebruikt.
* **breng de Gebeurtenissen van de Taak via E-mail op de hoogte:** specificeert of u e-mailberichten voor taakgebeurtenissen, met inbegrip van taaktaken, herinneringen, en termijnen voor taken in uw te doen lijst en in groep te doen lijsten ontvangt die u tot behoort.
* **maak Forms in E-mail vast:** specificeert of een exemplaar van de vorm aan e-mailberichtberichten in bijlage is. Bijlagen worden alleen ondersteund voor PDF- en XDP-formulieren.
* **sparen ontwerp periodiek:** specificeert of uw vormconcepten auto-bewaarde periodiek of niet zijn. Als u uw concepten periodiek wilt opslaan, schakelt u deze optie in en stelt u de duur voor automatisch opslaan in op 1 tot 30 minuten. Wanneer automatisch opslaan is ingeschakeld en een gebruiker aan een concept werkt, wordt het concept periodiek opgeslagen na het opgegeven aantal minuten. Het concept wordt alleen automatisch opgeslagen wanneer het concept is gewijzigd sinds de laatste keer dat het is opgeslagen of automatisch is opgeslagen. Wanneer het concept wordt opgeslagen, verschijnt er een waarschuwingsbericht op het scherm.
