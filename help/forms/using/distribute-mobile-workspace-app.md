---
title: AEM Forms-app distribueren
seo-title: Distribute AEM Forms app
description: Gebruik MDM (Mobile Device Management) voor de grootschalige implementatie van apps op mobiele apparaten.
seo-description: Use Mobile Device Management (MDM) for the large-scale deployment of apps on mobile devices.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
exl-id: 375cfa95-ac6f-44c4-a736-f5dd55d24195
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# AEM Forms-app distribueren {#distribute-aem-forms-app}

Met MDM (Mobile Device Management) kunnen toepassingen op grote schaal worden geïmplementeerd op mobiele apparaten.

>[!NOTE]
>
>Deze distributie is alleen van toepassing op iOS- en Android-apparaten.

## Belangrijkste eigenschappen die over het algemeen door oplossingen MDM worden verstrekt: {#main-features-generally-provided-by-mdm-solutions}

* Inschrijving van apparaten inschakelen in uw bedrijfsomgeving
* Het configureren en bijwerken van apparaatinstellingen toestaan
* Beveiligingsnaleving afdwingen.
* Veilige mobiele toegang tot bedrijfsmiddelen

Met een MDM-oplossing kunt u in combinatie met Mobile Application Management interne apps, openbare apps en aangeschafte apps beheren voor alle mobiele apparaten in uw bedrijf.

De beheerder MDM kan zowel ipa als apk dossiers aan de server uploaden MDM en de gebruikers controleren die tot ipa of apk- dossiers kunnen toegang hebben. De beheerder kan ook de profielinstelling bepalen die overeenkomt met elke toepassing.

## Profielinstellingen die van invloed zijn op de AEM Forms-toepassing {#profile-settings-affecting-the-aem-forms-app-br}

De volgende profielinstellingen op uw apparaat zijn van invloed op de werking van de AEM Forms-toepassing op uw apparaat:

* **Gebruik van camera toestaan** in de **Apparaatfunctionaliteit** sectie

Als u **Gebruik van camera toestaan**, de camerafunctie van de [Fotoaantekening](/help/forms/using/add-attachments.md) werkt niet. U moet deze optie inschakelen als u de camera in de app wilt gebruiken.

* **Wachtwoord vereisen op apparaat** in de sectie Wachtwoordbeleid

Inschakelen **codering van toepassingsgegevens** wordt u aangeraden de **wachtwoord** op uw apparaat. Als wachtwoord niet is ingesteld op het apparaat, worden de toepassingsgegevens die op het apparaat zijn opgeslagen, niet gecodeerd.
