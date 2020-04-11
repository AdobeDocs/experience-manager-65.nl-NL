---
title: Werken met een formulier
seo-title: Werken met een formulier
description: Het formulier weergeven en bijwerken dat is gekoppeld aan een taak of beginpunt in de app AEM Forms
seo-description: Het formulier weergeven en bijwerken dat is gekoppeld aan een taak of beginpunt in de app AEM Forms
uuid: 7481ca5c-a2c0-4697-9008-1e51bce2012e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 8a5e038e-b39a-41de-88a0-47642e5bd5bf
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Werken met een formulier {#working-with-a-form}

Als een formulier is ingeschakeld voor synchronisatie in de formulierapp, wordt het formulier gedownload en kunt u er direct mee werken.

De formulieren worden gedownload op uw app en zijn offline beschikbaar. U voert bijvoorbeeld een bankbedrijf uit en een klant vult een toepassing op uw site. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en dit opslaat voor revisie. De beheerder controleert het formulier en maakt een verificatieformulier in AEM-auteur. Met de beheerder kunt u het formulier synchroniseren met de app AEM Forms. Als het verificatieformulier beschikbaar is in de app AEM Forms, kan uw veldagent een mobiel apparaat gebruiken om de gegevens van uw klant te verifiëren. Het mobiele apparaat wordt gesynchroniseerd met de server en het verificatieformulier wordt geladen in de app. De veldagent kan uw klant bezoeken, de gegevens verifiëren, gegevens opslaan als concept of het verificatieformulier verzenden. Het formulier wordt telkens gesynchroniseerd met de server wanneer uw app online is.

Uw formulier synchroniseren in de app AEM Forms:

1. Selecteer een formulier in de auteur en klik op **Eigenschappen** weergeven.
1. Klik op **Geavanceerd op de pagina met eigenschappen.**
1. Schakel onder Geavanceerd de optie in: **Synchroniseer met AEM Forms App** en tik op **Opslaan**.

Als u meerdere formulieren wilt synchroniseren, selecteert u in de auteur meerdere formulieren in formulierbeheer en tikt u op **Synchroniseren met AEM Forms App**. Wanneer het formulier wordt gepubliceerd, kan de app AEM Forms verbinding maken met de publicatieserver en de formulieren ophalen.

>[!NOTE]
>
>Ondersteunde formulieren:
>
>* Adaptieve formulieren (zonder wazig laden)
>* Mobiele formulieren
>
>
Bijlagen op formulierniveau worden niet ondersteund in de adaptieve formulieren die worden opgehaald in de AEM Forms-app die is gesynchroniseerd met de AEM Forms OSGi-server. Gebruikers kunnen bestanden in een veld bijvoegen als de auteur op het moment van het ontwerpen van het formulier bijlagen op veldniveau heeft ingeschakeld.

**Een formulier openen en bijwerken**

1. Tik op het formulier in het beginscherm om een formulier te openen.
1. U kunt de velden van het formulier bijwerken, bijlagen toevoegen, opslaan als concept en het verzenden.
