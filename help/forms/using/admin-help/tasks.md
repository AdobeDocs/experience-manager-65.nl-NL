---
title: Werken met taken
description: Gebruik de pagina van het Onderzoek van de Taak aan onderzoek naar taken door gebruikersnaam of taakidentiteitskaart Meer weten over het werken met taken?
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 375376d1-60b3-49a4-8893-ba9336e6bf7b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
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

**Taak-id:** Het positieve gehele getal dat door de formulierworkflow wordt toegewezen wanneer de taak wordt geïnstantieerd (geïnitieerd door een gebruiker). U kunt deze id gebruiken om de taak door zijn levenscyclus te volgen. Klik op een Taak-id om details over de taakgeschiedenis weer te geven of om de taak opnieuw toe te wijzen aan een andere gebruiker.

**Status:** Toegewezen betekent dat de taak momenteel aan de gebruiker wordt toegewezen. Niet toegewezen betekent dat de taak eerder aan de gebruiker werd toegewezen. De status kan ook worden voltooid.

**Activiteit:** Toont het formulier en de naam voor een eerste bewerking of de procesbewerking die de taak heeft gegenereerd.

**Proces-id:** Dit positieve gehele getal dat door de formulierworkflow wordt toegewezen wanneer het proces wordt geïnstantieerd (wanneer een gebruiker of een geautomatiseerde stap een proces start). U kunt deze id gebruiken om de procesinstantie door de levenscyclus te volgen.

**Procesnaam - Versie:** De naam van het proces, zoals gedefinieerd in Workbench.

**Toepassing:** De naam van de toepassing waartoe het proces behoort, zoals gedefinieerd in Workbench.

**Aanmaakdatum:** De datum en tijd waarop de taak is gemaakt.

## Taakgeschiedenis weergeven en taken opnieuw toewijzen {#viewing-task-history-and-reassigning-tasks}

De pagina van de Geschiedenis van de Taak toont een lijst van de gebruikers en de groepen die aan een bepaalde taak zijn toegewezen.

Voor elke taaktoewijzing, toont de lijst de volgende informatie:

**Naam:** De naam van de gebruiker.

**Status:** Toegewezen betekent de taak momenteel aan de gebruiker wordt toegewezen. Niet toegewezen betekent de taak eerder aan de gebruiker werd toegewezen.

**Werklijst-id:** De numerieke id van de gebruikerswachtrij waartoe de taak behoort. Een proces kan door meerdere gebruikers worden gedeeld.

**Type:** Geeft aan hoe de taak is toegewezen:

**Initiaal:** De gebruiker werd oorspronkelijk toegewezen aan de taak.

**Vooruit:** De oorspronkelijke taakeigenaar wees de taak toe aan een andere gebruiker.

**Afwijzen:** Een door:sturen taak werd verworpen of een taak werd teruggekeerd aan een werklijst zonder te zijn voltooid.

**Claim:** De gebruiker heeft de taak opgeëist in een gedeelde werklijst.

**Escalatie:** Een vooraf bepaalde tijd is verstreken (zoals ingesteld in de actie Gebruiker in Workbench) zonder gebruikersinteractie en een andere gebruiker is toegewezen aan de taak.

**Raadpleeg:** De eigenaar van de taak heeft deze taak doorgestuurd naar een andere gebruiker die het formulier kan openen, gegevens kan opslaan, de bijlagen en notities kan wijzigen, maar de stap niet kan voltooien. De gebruiker moet de taak aan de taakeigenaar terugkeren die met de gebruiker raadpleegde.

**Opnieuw toewijzen beheerder:** De taak is opnieuw toegewezen door een beheerder.

**Datum toewijzing:** De datum en tijd waarop de taak aan de gebruiker is toegewezen.

### Een nieuwe gebruiker toewijzen aan een taak {#assigning-a-new-user-to-a-task}

Op de pagina Gebruiker toewijzen worden de gebruikers weergegeven die aan een taak kunnen worden toegewezen. U hebt toegang tot de pagina Gebruiker toewijzen door op de pagina Taakgeschiedenis op Nieuwe gebruiker toewijzen te klikken.

1. Typ in het vak Zoeken naar op de pagina Gebruiker toewijzen een deel van of alle vereiste gebruikersnaam of e-mailadres.
1. Selecteer Naam of E-mailadres onder Gebruiken en klik op Zoeken. De gebruikers die overeenkomen met de zoekopdracht worden weergegeven.
1. Selecteer de gebruiker in de lijst en klik op OK. De pagina Taakgeschiedenis wordt weergegeven met de nieuwe gebruikerstoewijzing.
