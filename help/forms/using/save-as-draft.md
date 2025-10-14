---
title: Een taak of formulier opslaan als concept
description: Stappen voor het opslaan van een conceptkopie van een taak of formulier in de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: b4a23b2e-ab18-402c-8dfa-2533ee692912
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Een taak of formulier opslaan als concept {#saving-a-task-or-form-as-a-draft}

Met de optie Opslaan als concept slaat u een momentopname van een taak of formulier op, samen met de gegevens die in het bijbehorende formulier zijn ingevuld. U kunt ook een concept maken op basis van een sjabloon. De concepten worden opgeslagen op het mobiele apparaat en gesynchroniseerd met de Adobe Experience Manager Forms-server voor een latere opvraging.

U kunt [&#x200B; de vorm &#x200B;](/help/forms/using/working-with-form.md) bijwerken, [&#x200B; annoteren het &#x200B;](/help/forms/using/add-attachments.md) met foto&#39;s, en manuscriptnota&#39;s. Terwijl u doorgaat met het bijwerken van een formulier, wordt aangeraden het formulier op te slaan als concept. In situaties waarin u besluit een ingevuld formulier later te verzenden, is het handig het formulier op te slaan als concept.

Om sparen als ontwerpeigenschap voor vormen toe te laten die op vormenportaal worden bewaard, zie [&#x200B; het Opslaan van een vorm HTML5 als ontwerp &#x200B;](/help/forms/using/saving-html5-form-draft.md).
Om voorlegging van adaptieve vormen te vormen, zie [&#x200B; Concepten en voorleggingscomponent &#x200B;](/help/forms/using/draft-submission-component.md). (Niet geldig voor formulieren die zijn gesynchroniseerd met AEM Forms JEE-server.)

Om een ontwerp tot stand te brengen, open de vorm en selecteer **sparen als Ontwerp** ![&#x200B; sparen-als-ontwerp &#x200B;](assets/save-as-draft.png). Verstrek de naam van het ontwerp en selecteer **sparen**. Het concept wordt opgeslagen in de map Concepten en gesynchroniseerd met de server. De app wordt opgeslagen in de map Outbox als de app offline is.

Als u het bijbehorende formulier later bijwerkt, worden de wijzigingen direct doorgevoerd. Bij het synchroniseren van de AEM Forms-toepassing met de AEM Forms-server wordt het concept geüpload naar de AEM Forms-server. Bovendien wordt het concept verplaatst van het Postvak UIT naar de map Taken of Concepten. Er verschijnt een bewerkingspictogram naast het pictogram.

Wanneer u aan meerdere taken en beginpunten blijft werken en deze opslaat, worden de concepten opgeslagen. Telkens wanneer uw app wordt gesynchroniseerd met de AEM Forms-server, wordt het concept opgeslagen op de server. Hiermee zorgt u ervoor dat u de concepten op elk gewenst moment kunt herstellen op basis van de laatst opgeslagen datum en tijd. Als u de toepassing bijvoorbeeld opnieuw installeert of uw mobiele apparaat wijzigt, kunt u het concept downloaden van de server.

## Concepten verwijderen {#delete-a-draft}

In de map Concepts worden alle concepten weergegeven. Met de optie Concept verwijderen kunt u concepten permanent van het mobiele apparaat en de mobiele server verwijderen.

De optie om concepten te verwijderen die zijn gemaakt op basis van een taak, is niet beschikbaar. Bij het schrappen van een ontwerp dat van een taak wordt gecreeerd, wordt de taak verlaten.

U kunt concepten zowel offline als online verwijderen. Bij het verwijderen van concepten in de offline modus worden de concepten alleen van de server verwijderd wanneer de verbinding met de server wordt hersteld.

Voer de volgende stappen uit om een concept te verwijderen:

1. In AEM Forms app, navigeer aan **Forms.**
1. Selecteer **Concepten** van drop-down naast Onderzoek.
1. Een vorm met het uitgeven pictogram ![&#x200B; geeft-ontwerp-app &#x200B;](assets/edit-draft-app.png) wijst op een ontwerp uit. Selecteer de horizontale ellips naast het concept.
1. In de opties die verschijnen wanneer u de horizontale ellips selecteert, uitgezocht **Schrap Ontwerp**.
