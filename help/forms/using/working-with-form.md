---
title: Werken met een formulier
description: Het formulier weergeven en bijwerken dat is gekoppeld aan een taak of beginpunt in de AEM Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: adff5339-e026-4924-a401-f249f37fc6e6
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# Werken met een formulier {#working-with-a-form}

Als een formulier is ingeschakeld voor synchronisatie in de formulierapp, wordt het formulier gedownload en kunt u er direct mee werken.

De formulieren worden gedownload op uw app en zijn offline beschikbaar. U voert bijvoorbeeld een bankbedrijf uit en een klant vult een toepassing op uw site. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en dit opslaat voor revisie. De beheerder controleert het formulier en maakt een verificatieformulier in AEM auteur. Met de beheerder kunt u het formulier synchroniseren met de AEM Forms-app. Als het verificatieformulier beschikbaar is in de AEM Forms-app, kan uw veldagent een mobiel apparaat gebruiken om de gegevens van uw klant te verifiëren. Het mobiele apparaat wordt gesynchroniseerd met de server en het verificatieformulier wordt geladen in de app. De veldagent kan uw klant bezoeken, de gegevens verifiëren, gegevens opslaan als concept of het verificatieformulier verzenden. Het formulier wordt telkens gesynchroniseerd met de server wanneer uw app online is.

Uw formulier synchroniseren in AEM Forms-app:

1. Selecteer een formulier in de ontwerpversie en klik op **Eigenschappen weergeven**.
1. Klik op de pagina met eigenschappen **Geavanceerd.**
1. Schakel onder Geavanceerd de optie in: **Synchroniseren met AEM Forms App** en selecteert u **Opslaan**.

Als u meerdere formulieren wilt synchroniseren, selecteert u in de auteur meerdere formulieren in formulierbeheer en selecteert u **Synchroniseren met AEM Forms App**. Wanneer het formulier wordt gepubliceerd, kan de AEM Forms-toepassing verbinding maken met de publicatieserver en de formulieren ophalen.

Als uw Android-app voor AFA (AEM Form Application) niet synchroniseert, voert u de volgende stappen uit om het synchronisatieprobleem op te lossen:

1. Ga naar de **https://[server]:[poort]/system/console/configMgr**.
1. Zoeken naar **[!UICONTROL Adobe Granite Token Authentication Handler]** en klik op **[!UICONTROL Edit]**.
1. Selecteer de **[!UICONTROL None]** in het vervolgkeuzemenu voor het dialoogvenster **[!UICONTROL SameSite attribute for the login-token cookie]** kenmerk.
1. Klik op **[!UICONTROL Save]**.

![Afbeelding synchroniseren met AFA Android-app](/help/forms/using/assets/afaandroid.png)

>[!NOTE]
>
>Ondersteunde formulieren:
>
>* Adaptieve formulieren (zonder wazig laden)
>* Mobiele formulieren
>
>Bijlagen op formulierniveau worden niet ondersteund in de adaptieve formulieren die worden opgehaald in de AEM Forms-app die is gesynchroniseerd met de AEM Forms OSGi-server. Gebruikers kunnen bestanden in een veld bijvoegen als de auteur op het moment van het ontwerpen van het formulier bijlagen op veldniveau heeft ingeschakeld.


**Een formulier openen en bijwerken**

1. Als u een formulier wilt openen, selecteert u de **[!UICONTROL Form]** in het beginscherm.
1. U kunt de velden van het formulier bijwerken, bijlagen toevoegen, opslaan als concept en het verzenden.
