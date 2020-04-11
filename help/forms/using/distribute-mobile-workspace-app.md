---
title: AEM Forms-app distribueren
seo-title: AEM Forms-app distribueren
description: Gebruik MDM (Mobile Device Management) voor de grootschalige implementatie van apps op mobiele apparaten.
seo-description: Gebruik MDM (Mobile Device Management) voor de grootschalige implementatie van apps op mobiele apparaten.
uuid: 8a2ce42b-5e9b-42c1-a945-c069f6152f6e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 5756cb52-dd47-4277-981c-fd0af9a20638
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# AEM Forms-app distribueren {#distribute-aem-forms-app}

Met MDM (Mobile Device Management) kunnen toepassingen op grote schaal worden geïmplementeerd op mobiele apparaten.

>[!NOTE]
>
>Deze distributie is alleen van toepassing op iOS- en Android-apparaten.

## Belangrijkste eigenschappen die over het algemeen door oplossingen MDM worden verstrekt: {#main-features-generally-provided-by-mdm-solutions}

* Inschrijving van apparaten inschakelen in uw bedrijfsomgeving
* Het configureren en bijwerken van apparaatinstellingen toestaan
* Naleving van beveiliging afdwingen.
* Veilige mobiele toegang tot bedrijfsmiddelen

Met een MDM-oplossing en het beheer van mobiele toepassingen kunt u interne apps, openbare apps en aangeschafte toepassingen beheren voor alle mobiele apparaten in uw bedrijf.

De beheerder MDM kan zowel ipa als apk dossiers aan de server uploaden MDM en de gebruikers controleren die tot ipa of apk- dossiers kunnen toegang hebben. De beheerder kan ook de profielinstelling bepalen die overeenkomt met elke toepassing.

## Profielinstellingen die van invloed zijn op de app AEM Forms {#profile-settings-affecting-the-aem-forms-app-br}

De volgende profielinstellingen op uw apparaat zijn van invloed op de werking van de app AEM Forms op uw apparaat:

* **Gebruik van camera** toestaan in de sectie **Apparaatfunctionaliteit**

Als u het gebruik van de camera **** toestaan uitschakelt, werkt de camerafunctie van de [fotonotitie](/help/forms/using/add-attachments.md) niet. U moet deze optie inschakelen als u de camera in de app wilt gebruiken.

* **Wachtwoord vereisen op apparaat** in de sectie Wachtwoordbeleid

Als u **codering van toepassingsgegevens** wilt inschakelen, wordt u aangeraden het **wachtwoord** op uw apparaat in te schakelen. Als wachtwoord niet is ingesteld op het apparaat, worden de toepassingsgegevens die op het apparaat zijn opgeslagen, niet gecodeerd.
