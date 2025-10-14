---
title: Gebruikers en gebruikersgroepen configureren
description: Volg deze pagina om inzicht te krijgen in de gebruikersrollen en hoe u uw gebruikers en groepen configureert om het ontwerpen en het beheer van uw mobiele apps te ondersteunen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: 9f814204-8cd4-4ba9-9e25-3ff1b25c1955
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---

# Uw gebruikers en gebruikersgroepen configureren {#configure-your-users-and-user-groups}

{{ue-over-mobile}}

In dit hoofdstuk worden de gebruikersrollen beschreven en wordt beschreven hoe u uw gebruikers en groepen kunt configureren om het ontwerpen en beheren van uw mobiele apps te ondersteunen.

## AEM Mobile Application Users en Group Administration {#aem-mobile-application-users-and-group-administration}

Voor het organiseren en beheren van het machtigingsmodel voor AEM apps zijn de volgende twee groepen beschikbaar:

* app-admins voor App Admins
* app-authors voor App Authors

### AEM Mobile Application Content Authors (groep voor het schrijven van apps) {#aem-mobile-application-content-authors-app-author-group}

Leden van de groep die de app heeft geschreven, zijn verantwoordelijk voor het ontwerpen AEM inhoud van mobiele toepassingen, zoals pagina&#39;s, tekst, afbeeldingen en video&#39;s.

#### Groepsconfiguratie - toepassingsauteurs {#group-configuration-app-authors}

1. Maak een gebruikersgroep met de naam &#39;app-authors&#39;:

   Navigeer aan de Admin Console van de Gebruiker: [&#x200B; http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Selecteer in de gebruikersgroepconsole de knop &#39;+&#39; om een groep te maken.

   Stel de id van deze groep in op &#39;toepassingsauteurs&#39; om aan te geven dat het een specifiek type gebruikersgroep voor auteurs is die specifiek is voor het ontwerpen van mobiele toepassingen in AEM.

1. Lid toevoegen aan groep: Auteurs

   ![&#x200B; chlimage_1-18 &#x200B;](assets/chlimage_1-18.png)

   App-auteurs toevoegen aan de groep Auteurs

1. Nu u de app-auteursGebruikersgroep hebt gecreeerd, kunt u individuele teamleden aan deze nieuwe groep door de [&#x200B; Admin Console van de Gebruiker &#x200B;](http://localhost:4502/libs/granite/security/content/useradmin.md) toevoegen.

   ![&#x200B; chlimage_1-19 &#x200B;](assets/chlimage_1-19.png)

   Gebruikersgroepen bewerken

1. Navigeer aan de [&#x200B; console van Toestemmingen &#x200B;](http://localhost:4502/useradmin) en voeg toestemmingen toe om cloudservices te beheren

   * (Lezen) op /etc/cloudservices

   >[!NOTE]
   >
   >App Authors extends the default content-authors (Authors) group from AEM, so that they inherit the ability to create content under /content/phonegap

### AEM Mobile Application Administrators Group (groep toepassingsbeheerders) {#aem-mobile-application-administrators-group-app-admins-group}

De leden van app-admins groep kunnen toepassingsinhoud met de zelfde toestemmingen inbegrepen met app-auteurs **EN** bovendien zijn ook verantwoordelijk voor:

* PhoneGap Build en Adobe mobiele services in AEM configureren
* OTA-updates voor inhoudssynchronisatie van toepassingen opslaan, publiceren en wissen

>[!NOTE]
>
>De toestemmingen bepalen beschikbaarheid van sommige gebruikersacties in het Centrum van het Bevel van de AEM App.
>
>Sommige opties zijn niet beschikbaar voor auteurs van apps die beschikbaar zijn voor app-beheerders.

#### Groepsconfiguratie - app-beheerders {#group-configuration-app-admins}

1. Maak een groep met de naam app-admins.
1. Voeg de volgende groepen toe aan uw nieuwe groep voor toepassingsbeheer:

   * content-authors
   * workflowgebruikers

   ![&#x200B; chlimage_1-20 &#x200B;](assets/chlimage_1-20.png)

1. Navigeer aan de [&#x200B; console van Toestemmingen &#x200B;](http://localhost:4502/useradmin) en voeg toestemmingen toe om cloudservices te beheren

   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/cloudservices/mobileservices
   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/cloudservices/phonegap-build

1. Voeg op dezelfde machtigingenconsole machtigingen toe aan het werkgebied, publiceer en wis de updates voor de inhoud van de app

   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/packages/mobileapp
   * (Lezen) op /var/contentsync

   >[!NOTE]
   >
   >Pakketreplicatie wordt gebruikt om app-updates te publiceren vanaf de ontwerpinstantie naar de publicatieinstantie

   >[!CAUTION]
   >
   >/var/contentSync toegang wordt geweigerd buiten-van-de-doos.
   >
   >Als u de machtiging LEZEN weglaat, kunnen lege updatepakketten worden gemaakt en gerepliceerd.

1. Voeg zo nodig leden toe aan deze groep

## Machtigingen voor dashboard-blokken {#dashboard-tile-permissions}

Dashboardblokken kunnen verschillende handelingen blootstellen op basis van de machtigingen die de gebruiker heeft. Hieronder wordt beschreven welke acties beschikbaar zijn voor elke tegel.

Naast deze machtigingen kan een handeling ook worden weergegeven of verborgen op basis van de configuratie van de huidige app. Het heeft bijvoorbeeld geen zin om de handeling &#39;Remote Build&#39; beschikbaar te maken als er geen PhoneGap-cloudconfiguratie aan de app is toegewezen. Deze zijn hieronder vermeld onder &quot;**sectie van de Voorwaarde van de Configuratie**.

### App-tegel beheren {#manage-app-tile}

De tegel bevat momenteel geen handelingen waarvoor machtigingen vereist zijn, maar de detailpagina voor de toepassing heeft de volgende handelingen:

* *geeft* voor app-auteur en app-admin uit (Trekker UI - jcr:write - op /content/phonegap/{suffix})
* *Download* voor app-auteur en app-admin (Trekker UI - op /content/phonegap/{suffix})

In de onderstaande afbeelding ziet u de opties voor downloaden en bewerken voor een app:

![&#x200B; chlimage_1-21 &#x200B;](assets/chlimage_1-21.png)
