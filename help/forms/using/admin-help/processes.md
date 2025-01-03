---
title: Processen beheren
description: De pagina van de Lijst van het Proces toont de processen die een gebruiker in werking heeft gesteld of die automatisch begonnen zijn. Meer informatie over het beheren van de processen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 21a2317d-3542-4ccb-98db-3cedf20c89ea
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1643'
ht-degree: 0%

---

# Processen beheren {#managing-processes}

De pagina van de Lijst van het Proces toont de processen die een gebruiker in werking heeft gesteld of die automatisch begonnen zijn.

1. Klik in de beheerconsole op Services > Forms-workflow > Forms-workflow. De proceslijst bevat de volgende informatie:

   **Naam van het Proces - Versie:** de naam van het proces, zoals die in Workbench wordt bepaald.

   **Toepassing:** de toepassing dat het proces tot behoort, zoals die in Workbench wordt bepaald.

   **Status:** Actief betekent dat het proces voor de procesversie geactiveerd is. Inactief betekent dat het proces een oude versie is die nog procesinstanties heeft.

   **Datum van de Aanmaak:** de datum en de tijd het proces werd opgesteld.

1. Klik op een procesnaam om de procesinstanties ervan op de pagina Procesinstantie weer te geven.

## Werken met procesinstanties {#working-with-process-instances}

Als u de pagina van de Instantie van het Proces van de pagina van de Lijst van het Proces toegang hebt, zijn alle procesinstanties van het proces u selecteerde vermeld. Als u de pagina van de Instantie van het Proces na het uitvoeren van een onderzoek toegang hebt, slechts zijn de gevonden procesinstanties vermeld.

Voor elke procesinstantie bevat de lijst de volgende informatie:

**identiteitskaart van het Proces:** Het herkenningsteken dat het vormwerkschema toewijst wanneer het proces (namelijk wanneer een gebruiker of een geautomatiseerde stap een proces) in werking stelt. U kunt deze id gebruiken om de procesinstantie door de levenscyclus te volgen.

**Naam van het Proces - Versie:** de naam van het proces, zoals die in Workbench wordt bepaald.

**Status:** wijst erop of de procesinstantie normaal loopt, veranderend staat, of is tegengehouden. (Zie Over status van procesinstanties.)

**Datum van de Verwezenlijking:** de datum en de tijd de procesinstantie werd gecreeerd.

**Datum van de Update:** de datum en de tijd de status van de procesinstantie werd het laatst veranderd.

U kunt de volgende taken uitvoeren op de pagina van de Instantie van het Proces:

* Selecteer een procesinstantie om details over het, zoals zijn verrichtingen en subprocessen te bekijken. Wanneer u een procesinstantie selecteert, wordt de pagina Details procesinstantie weergegeven.
* Procesinstanties onderbreken, opschorten of beëindigen.
* Zoeken naar een procesvariant. Klik op Zoeken om een zoekopdracht te starten.

### Over procesinstantiestatussen {#about-process-instance-statuses}

Een procesinstantie, inclusief subprocessen, kan de volgende statussen hebben:

**VOLTOOID:** Alle takken en verrichtingen in de procesinstantie hebben voltooid. COMPLETE is de definitieve status van een procesinstantie.

**COMPLETING:** het statuut van de procesinstantie staat op het punt om in COMPLETE te veranderen.

**BEGONNEN:** De procesinstantie is gecreeerd maar loopt nog niet. INITIATED is de eerste status van een procesinstantie.

**RUNNING:** de procesinstantie loopt normaal. Er kan een geautomatiseerde stap worden uitgevoerd of de procesinstantie ontvangt gebruikersinvoer of wacht op gebruikersinteractie.

**GESCHORST:** De procesinstantie is opgeschort door een beheerder of door een stap in het proces. Er vinden geen verdere bewerkingen plaats totdat de status wordt gewijzigd.

**HET SCHORTEN:** de status staat op het punt om in GESCHORST te veranderen. Als een verrichting is ontworpen om schorsingsverzoeken te negeren en nog niet voltooid, moet die verrichting voltooien alvorens de procesinstantie wordt opgeschort.

**BEËINDIGD:** de procesinstantie is geëindigd door een beheerder.

**BEËINDIGEN:** de status staat op het punt om in BEËINDIGD te veranderen. Als een verrichting is ontworpen om eindeverzoeken te negeren en nog niet voltooid, moet die verrichting voltooien alvorens de procesinstantie wordt geëindigd.

**ONSUSPENDING:** de status staat op het punt om in RUNNING te veranderen nadat het zijn SUSPENDED.

>[!NOTE]
>
>Wanneer wordt gevraagd om de status van een procesinstantie te wijzigen (bijvoorbeeld om te onderbreken of te beëindigen), voert het verzoek de opdrachtwachtrij voor de formulierwerkstroom in. Afhankelijk van de grootte van de wachtrij en de totale verwerkingssnelheid verandert de weergegeven status pas wanneer de pagina een of meer keren opnieuw wordt geladen.

### Procesinstanties onderbreken of opheffen {#suspend-or-unsuspend-process-instances}

Als u een probleem moet oplossen of als u weet dat een procesinstantie een probleem bij een recentere stap wegens één of andere externe voorwaarde zal ontmoeten, kunt u de procesinstantie tijdelijk opschorten.

U kunt procesinstanties opschorten die de status RUNNING hebben.

Nadat u een procesinstantie opheft, verandert zijn status in SUSPENDING, dan GESCHORST, en het proces pauzeert bij zijn huidige verrichting. De procesinstantie blijft in deze status totdat de status wordt gewijzigd in UNSUSPENDED.

Alleen procesinstanties met de status SUSPENDED kunnen worden gewijzigd in UNSUSPENDED.

Wanneer u een procesinstantie onderbreekt, verandert zijn status in RUNNING, en het gaat met de verrichting voort waar het was opgeschort.

Wanneer u een procesinstantie opheft die andere processen (kindprocessen) gebruikend hun aanroepverrichting heeft aangehaald, worden de kindprocessen ook opgeschort.

1. Klik in de beheerconsole op Services > Forms-workflow > Forms-workflow.
1. Selecteer het proces op de pagina Procesinstantie en klik op Onderbreken of Opschorten.

### Een procesinstantie beëindigen {#terminate-a-process-instances}

Als een bewerking van een procesinstantie is gestopt of een andere fout heeft aangetroffen, of als u een procesinstantie moet dwingen om de uitvoering te stoppen, kunt u de procesinstantie beëindigen.

U kunt procesinstanties beëindigen die om het even welke status hebben.

Wanneer u een procesinstantie beëindigt, verandert zijn status in BEËINDIGEN, dan BEËINDIGD, en het proces houdt bij zijn huidige verrichting op. Er worden geen verdere bewerkingen uitgevoerd en alle bijbehorende bewerkingen en taken worden beëindigd.

1. Klik in de beheerconsole op Services > Forms-workflow > Forms-workflow.
1. Selecteer het proces op de pagina Procesinstantie en klik op Beëindigen.

## Werken met procesinstantiedetails {#working-with-process-instance-details}

De pagina Details procesinstantie geeft de geschiedenis van een procesinstantie weer.

In het gebied Samenvatting wordt basisinformatie over de procesinstantie weergegeven.

Op het tabblad Bewerkingen wordt elke bewerking voor de procesinstantie weergegeven in volgorde van voltooiing, van de eerste naar de laatste met de volgende informatie:

**Naam van de Verrichting:** de naam van de verrichting, zoals die in Workbench wordt bepaald.

**Status:** wijst erop of de verrichting normaal loopt of is tegengehouden. (Zie Over status van procesinstanties.)

**de Naam van de Tak:** de naam van de tak, zoals die in Workbench wordt bepaald.

**Datum van het Begin:** de datum en de tijd de verrichting begonnen.

**Voltooide Datum:** de datum en de tijd voltooide verrichting.

Een subproces is een procesinstantie die door een ander proces is begonnen en onafhankelijk van dat andere proces loopt. Subprocessen worden alleen weergegeven als ze zijn ontworpen als onderdeel van het proces in Workbench. Op het tabblad Subprocessen wordt elk subproces weergegeven met de volgende informatie:

**identiteitskaart van het Proces:** Dit positieve geheel dat het vormwerkschema toewijst wanneer het proces (namelijk wanneer een gebruiker of een geautomatiseerde stap het proces) wordt geconcretiseerd. Met deze id kunt u de procesinstantie gedurende de levenscyclus volgen.

**Naam van het Proces - Versie:** De naam van het proces, zoals die in Designer wordt bepaald.

**Status:** wijst erop of de procesinstantie normaal loopt, veranderend staat, of tegengehouden. (Zie Over status van procesinstanties.)

**Datum van de Aanmaak:** de datum en de tijd het subprocess werd gecreeerd.

**Datum van de Update:** de datum en de tijd de status van subprocess werd het laatst veranderd.

U kunt de volgende taken uitvoeren op de pagina Details van de Instantie van het Proces:

* Selecteer een bewerking om de details ervan weer te geven. Wanneer u een bewerking selecteert, wordt de pagina Bewerkingsdetails weergegeven.
* Selecteer een subproces om details over het te bekijken. Wanneer u een subproces selecteert, wordt de pagina Details procesinstantie weergegeven.
* Bewerkingen of subprocessen beëindigen of opnieuw proberen, afhankelijk van hun status.

### Informatie over bewerkingsstatussen {#about-operation-statuses}

Een bewerking (een stap in een proces) kan de volgende statussen hebben:

**VOLTOOID:** de voltooide verrichting.

**DIE WORDT UITGEVOERD:** de verrichting loopt normaal. Het kan gebruikersinvoer ontvangen of op gebruikersinteractie wachten, of een geautomatiseerde stap kan lopend zijn.

**VERSTALLED:** Een probleem kwam voor terwijl de verrichting werd verwerkt. Controle voor de fout of de uitzondering in de Geroepen pagina van Verrichtingen.

**BEËINDIGD:** de verrichting werd geëindigd door een beheerder.

### Bewerkingen of subprocessen beëindigen {#terminate-operations-or-subprocesses}

Als een bewerking of een subproces is gestopt of een andere foutvoorwaarde heeft aangetroffen, of als u een bewerking of subproces moet forceren om te stoppen met uitvoeren, kunt u deze beëindigen.

U kunt een bewerking beëindigen die wordt uitgevoerd.

Wanneer u een bewerking beëindigt, verandert de status van de bewerking in BEËINDIGD. De bewerking wordt niet voltooid en de procesinstantie stopt met uitvoeren.

U kunt een subproces beëindigen dat om het even welke status heeft.

Wanneer u een subproces beëindigt, verandert zijn status in BEËINDIGEN, dan BEËINDIGD, en de procesinstantie houdt bij zijn huidige verrichtingen op. Er worden geen verdere bewerkingen uitgevoerd in het subproces, hoewel de bovenliggende procesinstantie wordt uitgevoerd.

U kunt geen processen beëindigen die gatewayelementen in het procesdiagram hebben. Als u probeert om deze types van processen te eindigen, worden de verrichtingen binnen de gatewayelementen niet beïnvloed. Om verrichtingen te eindigen die binnen een gatewayelement zijn, moet u de verrichtingen direct eindigen.

1. Voor de pagina van de Details van de Instantie van het Proces, klik het lusje van Verrichtingen of het Subprocess tabel.
1. Selecteer de bewerking of het subproces en klik op Beëindigen.

### Een bewerking opnieuw uitvoeren {#retry-an-operation}

U kunt een bewerking met de status STALLED opnieuw proberen.

Wanneer u een bewerking opnieuw uitvoert, wordt een verzoek verzonden om de bewerking opnieuw te starten. Als het verzoek succesvol is, verandert de status in RUNNING. Als de bewerking niet opnieuw kan worden gestart, blijft deze STALLED en moet u deze wellicht beëindigen.

1. Voor de pagina van de Details van de Instantie van het Proces, klik de Verrichtingen tabel.
1. Selecteer de bewerking en klik op Opnieuw.

## Werken met bewerkingen {#working-with-operations}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

De pagina van de Details van de Verrichting toont een overzicht van één verrichting in een proces en zijn huidige gebruikerstoewijzingen.

1. Klik in de beheerconsole op Services > Forms-workflow > Forms-workflow.
1. Klik op een procesnaam om de procesinstanties ervan weer te geven. Klik op een procesinstantie om de pagina Details procesinstantie weer te geven en selecteer vervolgens een bewerking om de pagina Bewerkingsdetails weer te geven.

   Voor elke taak, toont de lijst de volgende informatie:

   **Naam van het Proces - Versie:** de naam van het proces, zoals die in Workbench wordt bepaald.

   **Toepassing:** de toepassing dat het proces tot behoort, zoals die in Workbench wordt bepaald.

   **Status:** Actief betekent dat het proces voor de procesversie geactiveerd is. Inactief betekent dat het proces een oude versie is die nog procesinstanties heeft.

   **Datum van de Aanmaak:** de datum en de tijd het proces werd opgesteld.
