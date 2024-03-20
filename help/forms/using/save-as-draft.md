---
title: Een taak of formulier opslaan als concept
description: Stappen voor het opslaan van een conceptkopie van een taak of formulier in de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: b4a23b2e-ab18-402c-8dfa-2533ee692912
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Een taak of formulier opslaan als concept {#saving-a-task-or-form-as-a-draft}

Met de optie Opslaan als concept slaat u een momentopname van een taak of formulier op, samen met de gegevens die in het bijbehorende formulier zijn ingevuld. U kunt ook een concept maken op basis van een sjabloon. De concepten worden opgeslagen op het mobiele apparaat en gesynchroniseerd met de Adobe Experience Manager Forms-server voor een latere opvraging.

U kunt [het formulier bijwerken](/help/forms/using/working-with-form.md), [annoteren](/help/forms/using/add-attachments.md) met foto&#39;s en krabbelnotities. Terwijl u doorgaat met het bijwerken van een formulier, wordt aangeraden het formulier op te slaan als concept. In situaties waarin u besluit een ingevuld formulier later te verzenden, is het handig het formulier op te slaan als concept.

Als u de functie Opslaan als concept wilt inschakelen voor formulieren die zijn opgeslagen op de portal Formulieren, raadpleegt u [Een HTML5-formulier opslaan als concept](/help/forms/using/saving-html5-form-draft.md).
Als u de verzending van adaptieve formulieren wilt configureren, raadpleegt u [Concepten en verzendingen](/help/forms/using/draft-submission-component.md). (Niet geldig voor formulieren die zijn gesynchroniseerd met AEM Forms JEE-server.)

Als u een concept wilt maken, opent u het formulier en selecteert u het **Opslaan als concept** ![save-as-concept](assets/save-as-draft.png). Geef de naam van het concept op en selecteer **Opslaan**. Het concept wordt opgeslagen in de map Concepten en gesynchroniseerd met de server. De app wordt opgeslagen in de map Outbox als de app offline is.

Als u het bijbehorende formulier later bijwerkt, worden de wijzigingen direct doorgevoerd. Bij het synchroniseren van de AEM Forms-toepassing met de AEM Forms-server wordt het concept geüpload naar de AEM Forms-server. Bovendien wordt het concept verplaatst van het Postvak UIT naar de map Taken of Concepten. Er verschijnt een bewerkingspictogram naast het pictogram.

Wanneer u aan meerdere taken en beginpunten blijft werken en deze opslaat, worden de concepten opgeslagen. Telkens wanneer uw app wordt gesynchroniseerd met de AEM Forms-server, wordt het concept opgeslagen op de server. Hiermee zorgt u ervoor dat u de concepten op elk gewenst moment kunt herstellen op basis van de laatst opgeslagen datum en tijd. Als u de toepassing bijvoorbeeld opnieuw installeert of uw mobiele apparaat wijzigt, kunt u het concept downloaden van de server.

## Concepten verwijderen {#delete-a-draft}

In de map Concepts worden alle concepten weergegeven. Met de optie Concept verwijderen kunt u concepten permanent van het mobiele apparaat en de mobiele server verwijderen.

De optie om concepten te verwijderen die zijn gemaakt op basis van een taak, is niet beschikbaar. Bij het schrappen van een ontwerp dat van een taak wordt gecreeerd, wordt de taak verlaten.

U kunt concepten zowel offline als online verwijderen. Bij het verwijderen van concepten in de offline modus worden de concepten alleen van de server verwijderd wanneer de verbinding met de server wordt hersteld.

Voer de volgende stappen uit om een concept te verwijderen:

1. Navigeer in de AEM Forms-app naar **Forms.**
1. Selecteren **Concepten** in de vervolgkeuzelijst naast Zoeken.
1. Een formulier met het pictogram Bewerken ![edit-concept-app](assets/edit-draft-app.png) duidt een concept aan. Selecteer de horizontale ellips naast het concept.
1. Selecteer in de opties die worden weergegeven wanneer u de horizontale ellips selecteert **Concept verwijderen**.
