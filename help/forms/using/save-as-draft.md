---
title: Een taak of formulier opslaan als concept
seo-title: Een taak of formulier opslaan als concept
description: Stappen voor het opslaan van een conceptkopie van een taak of formulier in de app AEM Forms
seo-description: Stappen voor het opslaan van een conceptkopie van een taak of formulier in de app AEM Forms
uuid: 1192d2c2-05a4-4a96-9015-e56111aa2646
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 9950288c-b5a2-4945-afad-be9ce2abc8e9
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Een taak of formulier opslaan als concept {#saving-a-task-or-form-as-a-draft}

Met de optie Opslaan als concept slaat u een momentopname van een taak of formulier op, samen met de gegevens die in het bijbehorende formulier zijn ingevuld. U kunt ook een concept maken op basis van een sjabloon. De concepten worden opgeslagen op het mobiele apparaat en gesynchroniseerd met de Adobe Experience Manager Forms-server voor een later herstel.

U kunt het formulier [](/help/forms/using/working-with-form.md)bijwerken, [er notities aan toevoegen](/help/forms/using/add-attachments.md) met foto&#39;s en krabbelnotities. Terwijl u doorgaat met het bijwerken van een formulier, wordt aangeraden het formulier op te slaan als concept. In situaties waarin u besluit een ingevuld formulier later te verzenden, is het handig het formulier op te slaan als concept.

Zie Een HTML5-formulier [opslaan als concept](/help/forms/using/saving-html5-form-draft.md)als u de functie Opslaan als concept wilt inschakelen voor formulieren die zijn opgeslagen op het formulierportaal.
Zie [Concepten en verzendingscomponent](/help/forms/using/draft-submission-component.md)voor informatie over het configureren van de verzending van aangepaste formulieren. (Niet geldig voor formulieren die zijn gesynchroniseerd met AEM Forms JEE-server.)

Als u een concept wilt maken, opent u het formulier en tikt u op **Opslaan als concept** en ![Opslaan als concept](assets/save-as-draft.png). Geef de naam van het concept op en tik op **Opslaan**. Het concept wordt opgeslagen in de map Concepten en gesynchroniseerd met de server. De app wordt opgeslagen in de map Outbox als de app offline is.

Als u het bijbehorende formulier later bijwerkt, worden de wijzigingen direct doorgevoerd. Als u de AEM Forms-toepassing synchroniseert met de AEM Forms-server, wordt het concept geüpload naar de AEM Forms-server. Bovendien wordt het concept verplaatst van het Postvak UIT naar de map Taken of Concepten. Er verschijnt een bewerkingspictogram naast het pictogram.

Wanneer u aan meerdere taken en beginpunten blijft werken en deze opslaat, worden de concepten opgeslagen. Elke keer dat uw app wordt gesynchroniseerd met de AEM Forms-server, wordt het concept opgeslagen op de server. Hiermee zorgt u ervoor dat u de concepten op elk gewenst moment kunt herstellen op basis van de laatst opgeslagen datum en tijd. Als u de toepassing bijvoorbeeld opnieuw installeert of uw mobiele apparaat wijzigt, kunt u het concept downloaden van de server.

## Concepten verwijderen {#delete-a-draft}

In de map Concepts worden alle concepten weergegeven. Met de optie Concept verwijderen kunt u concepten permanent van het mobiele apparaat en de mobiele server verwijderen.

De optie om concepten te verwijderen die zijn gemaakt op basis van een taak, is niet beschikbaar. Bij het schrappen van een ontwerp dat van een taak wordt gecreeerd, wordt de taak verlaten.

U kunt concepten zowel offline als online verwijderen. Bij het verwijderen van concepten in de offline modus worden de concepten alleen van de server verwijderd wanneer de verbinding met de server wordt hersteld.

Voer de volgende stappen uit om een concept te verwijderen:

1. Navigeer in de app AEM Forms naar **Forms.**
1. Selecteer **Concepten** in de keuzelijst naast Zoeken.
1. Een formulier met het bewerkingspictogram ![bewerkt-concept-app](assets/edit-draft-app.png) geeft een concept aan. Tik op de horizontale ellips naast het concept.
1. Tik in de opties die worden weergegeven wanneer u op het horizontale ovaal tikt, op Concept **** verwijderen.
