---
title: Uw gebruikers en gebruikersgroepen configureren
seo-title: Uw gebruikers en gebruikersgroepen configureren
description: Volg deze pagina om inzicht te krijgen in de gebruikersrollen en hoe u uw gebruikers en groepen configureert voor ondersteuning van het ontwerpen en beheren van uw mobiele apps.
seo-description: Volg deze pagina om inzicht te krijgen in de gebruikersrollen en hoe u uw gebruikers en groepen configureert voor ondersteuning van het ontwerpen en beheren van uw mobiele apps.
uuid: 55cea2b3-d7e6-4174-92b3-ee97e46b59c4
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 167f3bd9-7dbc-4e6b-9868-3ee53935641b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Uw gebruikers en gebruikersgroepen configureren {#configure-your-users-and-user-groups}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

In dit hoofdstuk worden de gebruikersrollen beschreven en wordt beschreven hoe u uw gebruikers en groepen kunt configureren om het ontwerpen en beheren van uw mobiele apps te ondersteunen.

## AEM Mobile Application Users en Group Administration {#aem-mobile-application-users-and-group-administration}

Voor het organiseren en beheren van het machtigingsmodel voor AEM Apps zijn de volgende twee groepen beschikbaar:

* app-admins voor App Admins
* app-authors voor App Authors

### AEM Mobile Application Content Authors (groep voor het schrijven van apps) {#aem-mobile-application-content-authors-app-author-group}

Leden van de groep die de app heeft geschreven, zijn verantwoordelijk voor het ontwerpen van inhoud voor mobiele toepassingen van AEM, waaronder pagina&#39;s, tekst, afbeeldingen en video&#39;s.

#### Groepsconfiguratie - toepassingsauteurs {#group-configuration-app-authors}

1. Maak een nieuwe gebruikersgroep met de naam &#39;app-authors&#39;:

   Ga naar de beheerconsole voor gebruikers: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Selecteer in de gebruikersgroepconsole de knop &#39;+&#39; om een groep te maken.

   Stel de id van deze groep in op &#39;toepassingsauteurs&#39; om aan te geven dat het een specifiek type gebruikersgroep voor auteurs is die specifiek is voor het ontwerpen van mobiele toepassingen in AEM.

1. Lid toevoegen aan groep:Auteurs

   ![chlimage_1-18](assets/chlimage_1-18.png)

   App-auteurs toevoegen aan de groep Auteurs

1. Nu u de gebruikersgroep voor toepassingsauteurs hebt gemaakt, kunt u afzonderlijke teamleden aan deze nieuwe groep toevoegen via de [gebruikersbeheerconsole](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-19](assets/chlimage_1-19.png)

   Gebruikersgroepen bewerken

1. Navigeer naar de [machtigingenconsole](http://localhost:4502/useradmin) en voeg machtigingen toe om cloudservices te beheren

   * (Lezen) op /etc/cloudservices
   >[!NOTE]
   >
   >App Authors extends the default content-authors (Authors) group from AEM and inheress the ability to create content under /content/phonegap

### AEM Mobile Application Administrators Group (app-admins-groep) {#aem-mobile-application-administrators-group-app-admins-group}

Leden van de groep app-admins kunnen toepassingsinhoud met de zelfde toestemmingen ontwerpen inbegrepen bij app-auteurs **EN** zijn ook verantwoordelijk voor:

* PhoneGap Build- en Adobe Mobile Services-cloudservices configureren in AEM
* OTA-updates voor inhoudssynchronisatie van toepassingen opslaan, publiceren en wissen

>[!NOTE]
>
>De toestemmingen bepalen beschikbaarheid van sommige gebruikersacties in het Centrum van het Bevel van AEM App.
>
>Sommige opties zijn niet beschikbaar voor toepassingsauteurs die beschikbaar zijn voor app-beheerders.

#### Groepsconfiguratie - app-beheerders {#group-configuration-app-admins}

1. Maak een nieuwe groep met de naam app-admins.
1. Voeg de volgende groepen toe aan uw nieuwe app-admins-groep:

   * content-authors
   * workflowgebruikers
   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Navigeer naar de [machtigingenconsole](http://localhost:4502/useradmin) en voeg machtigingen toe om cloudservices te beheren

   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/cloudservices/mobileservices
   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/cloudservices/phonegap-build

1. Voeg op dezelfde machtigingenconsole machtigingen toe aan het werkgebied, publiceer en wis de updates van de toepassingsinhoud

   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/packages/mobileapp
   * (Lezen) op /var/contentsync
   >[!NOTE]
   >
   >Pakketreplicatie wordt gebruikt om app-updates te publiceren vanaf de ontwerpinstantie naar de publicatieinstantie

   >[!CAUTION]
   >
   >/var/contentSync toegang wordt geweigerd OOTB.
   >
   >Als u de machtiging LEZEN weglaat, kunnen lege updatepakketten worden gemaakt en gerepliceerd.

1. Voeg zo nodig leden toe aan deze groep

## Machtigingen voor dashboard-blokken {#dashboard-tile-permissions}

Dashboardblokken kunnen verschillende handelingen blootstellen op basis van de machtigingen die de gebruiker heeft. Hieronder wordt beschreven welke acties beschikbaar zijn voor elke tegel.

Naast deze machtigingen kan een handeling ook worden weergegeven of verborgen op basis van de configuratie van de huidige app. Het heeft bijvoorbeeld geen zin om de handeling &#39;Remote Build&#39; beschikbaar te maken als er geen PhoneGap-cloudconfiguratie aan de app is toegewezen. Deze zullen hieronder onder de &quot;secties van de Voorwaarde van de **Configuratie**&quot;worden vermeld.

### App-tegel beheren {#manage-app-tile}

De tegel bevat momenteel geen handelingen waarvoor machtigingen vereist zijn, maar de detailpagina voor de toepassing heeft de volgende handelingen:

* *Bewerken* voor app-auteur en app-admin (UI Trigger - jcr:write - on /content/phonegap/{suffix})
* *Downloaden* voor app-auteur en app-admin (UI-activering - op /content/phonegap/{suffix})

In de onderstaande afbeelding ziet u de opties voor downloaden en bewerken voor een app:

![chlimage_1-21](assets/chlimage_1-21.png)

