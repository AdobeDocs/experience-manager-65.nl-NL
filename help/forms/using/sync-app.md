---
title: De app synchroniseren
description: Synchroniseer de AEM Forms-toepassing op uw mobiele apparaat met de AEM Forms-server.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 6bb1d6df-b322-4112-bc25-6300877ee146
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# De app synchroniseren{#synchronizing-the-app}

## De app synchroniseren {#synchronizing-the-app-1}

De formulieren in uw app worden gedownload van de AEM Forms-server. De formulieren worden gedownload onder Taken en op de tabbladen Forms. Concepten die zijn gemaakt op basis van formulieren, worden gedownload op het tabblad Concepten en concepten die zijn gemaakt op basis van taken, worden gedownload op het tabblad Taken. Voor een zelfstandig formulier op de OSGi-server worden formulieren en concepten gedownload in respectievelijk Forms en Concept tabbladen.

Wanneer u een formulier invult en verzendt, wordt het formulier direct naar de AEM Forms-server geüpload als de app online is. De formulieren worden opgehaald van de server wanneer de app wordt gesynchroniseerd. De concepten worden echter meteen gesynchroniseerd met de server als de app online is.

Wanneer u online bent met de AEM Forms-server, wordt uw app standaard elke 15 minuten gesynchroniseerd. U kunt de synchronisatiefrequentie echter wijzigen. U kunt de app ook op elk gewenst moment handmatig synchroniseren.

**app manueel synchroniseren**

Selecteer de Synchronize knoop ![&#x200B; synchronisatie-app &#x200B;](assets/sync-app.png) bij de laag-juiste hoek van het huisscherm.

**om de synchronisatiefrequentie** te veranderen

1. Om naar het Plaatsende scherm te gaan, selecteer de menuknoop bij de upper-left hoek van het scherm van het Huis, en selecteer dan **Montages**.
1. Selecteer het tabblad Algemeen in het scherm Instellingen.

   ![&#x200B; de frequentie die van de Synchronisatie in het Algemene venster van Montages plaatst &#x200B;](assets/gen-settings-2.png)

1. Selecteer bij de optie Synchronisatiefrequentie de waarde rechts van Synchronisatiefrequentie.
1. Selecteer de nieuwe synchronisatiefrequentie in de vervolgkeuzelijst.

### Technische specificaties {#technical-specifications}

* De hoofdlogica voor het verzenden van de gegevens van de offline-app naar de AEM Forms-server vindt u in runtime/offline/util/offline.js.
* In .js, verzendt de vraag aan de processOfflineSubmissionSavedTasks (...) functie, de bewaarde/voorgelegde taken naar de server. Ook worden eventuele fouten of conflicten in het synchronisatieproces afgehandeld. Als het verzenden van een taak mislukt, wordt de taak in de app gemarkeerd als mislukt. Bovendien blijft de taak in uw Postvak UIT.
* De functie syncSubmissionTask() en syncSavedTask() voeren bewerkingen uit op individuele taken.
* De aanroep van de functie processOfflineSubmissionSavedTasks() wordt geïnitieerd door de component met de takenlijst nadat een gebruiker heeft geselecteerd om offline status te synchroniseren met de server of een automatische synchronisatie met de achtergrondthread.
