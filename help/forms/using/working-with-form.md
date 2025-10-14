---
title: Werken met een formulier
description: Het formulier weergeven en bijwerken dat is gekoppeld aan een taak of beginpunt in de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: adff5339-e026-4924-a401-f249f37fc6e6
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Werken met een formulier {#working-with-a-form}

Als een formulier is ingeschakeld voor synchronisatie in de formulierapp, wordt het formulier gedownload en kunt u er direct mee werken.

De formulieren worden gedownload op uw app en zijn offline beschikbaar. U voert bijvoorbeeld een bankbedrijf uit en een klant vult een toepassing op uw site. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en dit opslaat voor revisie. De beheerder controleert het formulier en maakt een verificatieformulier in AEM auteur. Met de beheerder kunt u het formulier synchroniseren met de AEM Forms-app. Als het verificatieformulier beschikbaar is in de AEM Forms-app, kan uw veldagent een mobiel apparaat gebruiken om de gegevens van uw klant te verifiëren. Het mobiele apparaat wordt gesynchroniseerd met de server en het verificatieformulier wordt geladen in de app. De veldagent kan uw klant bezoeken, de gegevens verifiëren, gegevens opslaan als concept of het verificatieformulier verzenden. Het formulier wordt telkens gesynchroniseerd met de server wanneer uw app online is.

Uw formulier synchroniseren in AEM Forms-app:

1. In auteursinstantie, selecteer een vorm, en klik **Eigenschappen van de Mening**.
1. In de eigenschappen pagina, klik **Geavanceerd.**
1. Onder Geavanceerd, laat optie toe: **Synchronisatie met AEM Forms App**, en selecteer **sparen**.

Om veelvoudige vormen, in de auteursinstantie te synchroniseren, selecteer veelvoudige vormen in vormenmanager en selecteer **Synchronisatie met AEM Forms App**. Wanneer het formulier wordt gepubliceerd, kan de AEM Forms-toepassing verbinding maken met de publicatieserver en de formulieren ophalen.

Als uw AFA (AEM Form Application) Android-app niet synchroniseert, voert u de volgende stappen uit om het synchronisatieprobleem op te lossen:

1. Ga naar **https:// [ server ]:[ haven ]/system/console/configMgr**.
1. Zoek naar **[!UICONTROL Adobe Granite Token Authentication Handler]** en klik **[!UICONTROL Edit]**.
1. Selecteer de optie **[!UICONTROL None]** in het vervolgkeuzemenu voor het kenmerk **[!UICONTROL SameSite attribute for the login-token cookie]** .
1. Klik op **[!UICONTROL Save]**.

![&#x200B; het Beeld van de Synchronisatie met AFA Android app &#x200B;](/help/forms/using/assets/afaandroid.png)

>[!NOTE]
>
>Ondersteunde formulieren:
>
>* Adaptieve formulieren (zonder wazig laden)
>* Mobiele formulieren
>
>Bijlagen op formulierniveau worden niet ondersteund in de adaptieve formulieren die worden opgehaald in de AEM Forms-app die is gesynchroniseerd met de AEM Forms OSGi-server. Gebruikers kunnen bestanden in een veld bijvoegen als de auteur op het moment van het ontwerpen van het formulier bijlagen op veldniveau heeft ingeschakeld.


**om een vorm** te openen en bij te werken

1. Als u een formulier wilt openen, selecteert u de **[!UICONTROL Form]** in het beginscherm.
1. U kunt de velden van het formulier bijwerken, bijlagen toevoegen, opslaan als concept en het verzenden.
