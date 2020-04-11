---
title: De app synchroniseren
seo-title: De app synchroniseren
description: Synchroniseer de app AEM Forms op uw mobiele apparaat met de AEM Forms-server.
seo-description: Synchroniseer de app AEM Forms op uw mobiele apparaat met de AEM Forms-server.
uuid: 3a6fb2d5-2ec4-4f78-a42a-fc921b66238e
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 393e4332-a2cc-42c8-a18f-3035addbcfaa
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# De app synchroniseren{#synchronizing-the-app}

## De app synchroniseren {#synchronizing-the-app-1}

De formulieren in uw app worden gedownload van de AEM Forms-server. De formulieren worden gedownload onder de tabbladen Taken en Formulieren. Concepten die zijn gemaakt op basis van formulieren, worden gedownload op het tabblad Concepten en concepten die zijn gemaakt op basis van taken, worden gedownload op het tabblad Taken. Voor een zelfstandig formulier op de OSGi-server worden formulieren en concepten respectievelijk gedownload in de tabbladen Formulieren en Ontwerp.

Wanneer u een formulier invult en verzendt, wordt het formulier direct naar de AEM Forms-server geüpload als de app online is. De formulieren worden opgehaald van de server wanneer de app wordt gesynchroniseerd. De concepten worden echter meteen gesynchroniseerd met de server als de app online is.

Wanneer u online bent met de AEM Forms-server, wordt uw app standaard elke 15 minuten gesynchroniseerd. U kunt de synchronisatiefrequentie echter wijzigen. U kunt de app ook op elk gewenst moment handmatig synchroniseren.

**De app handmatig synchroniseren**

Tik op de knop Synchroniseren ![synchroniseren-app](assets/sync-app.png) in de rechterbenedenhoek van het beginscherm.

**De synchronisatiefrequentie wijzigen**

1. Tik op de menuknop linksboven in het scherm Home om naar het scherm Instelling te gaan en tik vervolgens op **Instellingen**.
1. Tik in het scherm Instellingen op het tabblad Algemeen.

   ![Frequentie-instelling synchroniseren in venster Algemene instellingen](assets/gen-settings-2.png)

1. Tik in de optie Synchronisatiefrequentie op de waarde rechts van Synchronisatiefrequentie.
1. Selecteer de nieuwe synchronisatiefrequentie in de vervolgkeuzelijst.

### Technische specificaties {#technical-specifications}

* De belangrijkste logica voor het verzenden van de gegevens van de offline-app naar de AEM Forms-server vindt u in runtime/offline/util/offline.js.
* In .js, verzendt de vraag aan de processOfflineSubmissionSavedTasks (...) functie, de bewaarde/voorgelegde taken naar de server. Ook worden eventuele fouten of conflicten in het synchronisatieproces afgehandeld. Als het verzenden van een taak mislukt, wordt de taak in de app gemarkeerd als mislukt. Bovendien blijft de taak in uw Postvak UIT.
* De functie syncSubmissionTask() en syncSavedTask() voeren bewerkingen uit op individuele taken.
* De aanroep van de functie processOfflineSubmissionSavedTasks() wordt geïnitieerd door de component met de takenlijst nadat een gebruiker heeft geselecteerd om offline status te synchroniseren met de server of een automatische synchronisatie met de achtergrondthread.
