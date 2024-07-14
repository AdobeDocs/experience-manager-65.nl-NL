---
title: Werken met taken
description: Gebruik de pagina van het Onderzoek van de Taak aan onderzoek naar taken door gebruikersnaam of taakidentiteitskaart Meer weten over het werken met taken?
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 375376d1-60b3-49a4-8893-ba9336e6bf7b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Werken met taken {#working-with-tasks}

Gebruik de pagina van het Onderzoek van de Taak aan onderzoek naar taken door gebruikersnaam of taakidentiteitskaart De zoekresultaten worden weergegeven op de pagina Taaklijst, waar u de geschiedenis van een taak kunt openen. U kunt een taak ook opnieuw toewijzen als één gebruiker te veel taken heeft of als een gebruiker een taak ten onrechte heeft toegewezen.

>[!NOTE]
>
>Het uitvoeren van taakonderzoeken keert geen resultaten voor gebruikersnamen terug die met een aantalteken (#) beginnen. Maak indien mogelijk geen gebruikersnamen die met een hekje beginnen.

## Zoeken naar taken die aan een gebruiker zijn gekoppeld {#search-for-tasks-associated-with-a-user}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Taakzoekopdracht.
1. Selecteer Gebruikersnaam bij Zoeken op. Als u een gedeelte van de gebruikersnaam kent waarnaar u zoekt, typt u deze in het vak. Klik op Gebruiker zoeken.
1. De pagina Gebruiker zoeken wordt weergegeven. U kunt uw zoekopdracht verder verfijnen door te zoeken op gebruikersnaam of e-mail. Wanneer u de gebruiker zoekt, selecteert u het keuzerondje naast de naam en klikt u op OK.
1. Standaard zoekt de taakzoekopdracht naar taken die momenteel aan de gebruiker zijn toegewezen. Als u ook wilt zoeken naar taken die eerder aan de gebruiker zijn toegewezen, selecteert u Niet toegewezen taak tonen. Als u ook wilt zoeken naar taken die de gebruiker heeft voltooid, selecteert u Voltooide taak tonen.
1. Klik op Zoeken. De pagina Taaklijst wordt weergegeven met een lijst van het zoekresultaat.

## Zoeken naar een taak wanneer u de taak-id kent {#search-for-a-task-when-you-know-its-task-id}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Taakzoekopdracht.
1. Selecteer Taak-id in Zoeken op en typ de taak-id in het vak.
1. Klik op Zoeken. De pagina Taaklijst wordt weergegeven met een lijst van het zoekresultaat.

## Werken met de takenlijst {#working-with-the-task-list}

De resultaten van een taakonderzoek worden getoond op de pagina van de Lijst van de Taak. U kunt een taak selecteren om de pagina van de Geschiedenis van de Taak te openen. Vervolgens kunt u de taak aan een andere gebruiker toewijzen.

De taken worden getoond met de volgende informatie:

**identiteitskaart van de Taak:** het positieve geheel dat het vormwerkschema toewijst wanneer de taak (in werking gesteld door een gebruiker) wordt geconcretiseerd. U kunt deze id gebruiken om de taak door zijn levenscyclus te volgen. Klik op een Taak-id om details over de taakgeschiedenis weer te geven of om de taak opnieuw toe te wijzen aan een andere gebruiker.

**Status:** Toegewezen betekent dat de taak momenteel aan de gebruiker wordt toegewezen. Niet toegewezen betekent dat de taak eerder aan de gebruiker werd toegewezen. De status kan ook worden voltooid.

**Activiteit:** toont de vorm en de naam voor een aanvankelijke verrichting of de procesverrichting die de taak produceerde.

**identiteitskaart van het Proces:** Dit positieve geheel dat door vormenwerkschema wordt toegewezen wanneer het proces (namelijk wanneer een gebruiker of een geautomatiseerde stap een proces) in werking stelt. U kunt deze id gebruiken om de procesinstantie door de levenscyclus te volgen.

**Naam van het Proces - Versie:** de naam van het proces, zoals die in Workbench wordt bepaald.

**Toepassing:** de naam van de toepassing die het proces tot behoort, zoals die in Workbench wordt bepaald.

**Datum van de Verwezenlijking:** de datum en de tijd de taak werd gecreeerd.

## Taakgeschiedenis weergeven en taken opnieuw toewijzen {#viewing-task-history-and-reassigning-tasks}

De pagina van de Geschiedenis van de Taak toont een lijst van de gebruikers en de groepen die aan een bepaalde taak zijn toegewezen.

Voor elke taaktoewijzing, toont de lijst de volgende informatie:

**Naam:** De naam van de gebruiker.

**Status:** Toegewezen betekent de taak momenteel aan de gebruiker wordt toegewezen. Niet toegewezen betekent de taak eerder aan de gebruiker werd toegewezen.

**identiteitskaart van de Werklijst:** het numerieke herkenningsteken van de gebruikersrij waartot de taak behoort. Een proces kan door meerdere gebruikers worden gedeeld.

**Type:** wijst erop hoe de taak werd toegewezen:

**Aanvankelijk:** de gebruiker werd oorspronkelijk toegewezen de taak.

**door:sturen:** de originele taakeigenaar wees de taak aan een andere gebruiker toe.

**Weigeren:** Een door:sturen taak werd verworpen of een taak was teruggekeerd aan een werklijst zonder te zijn voltooid.

**Claim:** de gebruiker beweerde de taak in een gedeelde werklijst.

**Escalatie:** Een vooraf bepaalde tijd die (zoals die in de actie van de Gebruiker in Workbench wordt geplaatst) zonder gebruikersinteractie is verstreken en een andere gebruiker werd toegewezen de taak.

**raadpleeg:** de taakeigenaar heeft deze taak aan een andere gebruiker voor overleg doorgestuurd die de vorm kan openen, gegevens opslaan, de gehechtheid en de nota&#39;s wijzigen, maar niet de stap kan voltooien. De gebruiker moet de taak aan de taakeigenaar terugkeren die met de gebruiker raadpleegde.

**Admin opnieuw toewijzen:** De taak werd opnieuw toegewezen door een beheerder.

**Datum van de Taak:** de datum en de tijd de taak werd toegewezen aan de gebruiker.

### Een nieuwe gebruiker toewijzen aan een taak {#assigning-a-new-user-to-a-task}

Op de pagina Gebruiker toewijzen worden de gebruikers weergegeven die aan een taak kunnen worden toegewezen. U hebt toegang tot de pagina Gebruiker toewijzen door op de pagina Taakgeschiedenis op Nieuwe gebruiker toewijzen te klikken.

1. Typ in het vak Zoeken naar op de pagina Gebruiker toewijzen een deel van of alle vereiste gebruikersnaam of e-mailadres.
1. Selecteer Naam of E-mailadres onder Gebruiken en klik op Zoeken. De gebruikers die overeenkomen met de zoekopdracht worden weergegeven.
1. Selecteer de gebruiker in de lijst en klik op OK. De pagina Taakgeschiedenis wordt weergegeven met de nieuwe gebruikerstoewijzing.
