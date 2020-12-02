---
title: Uw gebruikers en gebruikersgroepen configureren
seo-title: Uw gebruikers en gebruikersgroepen configureren
description: Volg deze pagina om de gebruikersrollen te begrijpen en hoe te om uw gebruikers en groepen te vormen om het ontwerpen en het beheer van uw mobiele On-Demand de dienstenapp te steunen.
seo-description: Volg deze pagina om de gebruikersrollen te begrijpen en hoe te om uw gebruikers en groepen te vormen om het ontwerpen en het beheer van uw mobiele On-Demand de dienstenapp te steunen.
uuid: 461e1725-41dd-4883-92b9-a7e175660401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: c3c73e67-7f85-4308-b4cd-1b42d4f3f2d9
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---


# Uw gebruikers en gebruikersgroepen {#configure-your-users-and-user-groups} configureren

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

In dit hoofdstuk worden de gebruikersrollen beschreven en wordt beschreven hoe u uw gebruikers en groepen kunt configureren om het ontwerpen en beheren van uw mobiele apps te ondersteunen.

## AEM Mobile Application Users and Group Administration {#aem-mobile-application-users-and-group-administration}

### AEM Mobile Application Content Authors (app-auteurgroep) {#aem-mobile-application-content-authors-app-author-group}

Leden van de groep die de app heeft geschreven, zijn verantwoordelijk voor het ontwerpen AEM inhoud van mobiele toepassingen, zoals pagina&#39;s, tekst, afbeeldingen en video&#39;s.

#### Groepsconfiguratie - toepassingsauteurs {#group-configuration-app-authors}

1. Maak een nieuwe gebruikersgroep met de naam &#39;app-authors&#39;:

   Navigeer naar de Admin Console Gebruiker: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Selecteer in de gebruikersgroepconsole de knop &#39;+&#39; om een groep te maken.

   Stel de id van deze groep in op &#39;toepassingsauteurs&#39; om aan te geven dat het een specifiek type gebruikersgroep voor auteurs is die specifiek is voor het ontwerpen van mobiele toepassingen in AEM.

1. Lid toevoegen aan groep: Auteurs

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Nu u de app-auteursGebruikersgroep hebt gecreeerd, kunt u individuele teamleden aan deze nieuwe groep door [de console van Admin van de Gebruiker toevoegen ](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. In het volgende voorbeeld kunt u toevoegen aan AEM Content Authors Group:

   (Lezen) op

   * /app
   * /etc/clientlibs
   * /etc/designs
   * /etc/cloudservices/dps2015

### AEM Mobile Application Administrators Group (app-admins-groep) {#aem-mobile-application-administrators-group-app-admins-group}

Leden van de app-admins-groep kunnen toepassingsinhoud met de zelfde toestemmingen ontwerpen inbegrepen bij app-auteurs **AND** zijn ook verantwoordelijk voor:

* Toepassingsupdates voor ContentSync OTA opslaan, publiceren en wissen

>[!NOTE]
>
>De toestemmingen bepalen beschikbaarheid van sommige gebruikersacties in het Centrum van het Bevel van de AEM App.
>
>Sommige opties zijn niet beschikbaar voor toepassingsauteurs die beschikbaar zijn voor app-beheerders.

### Groepsconfiguratie - app-admins {#group-configuration-app-admins}

1. Maak een nieuwe groep met de naam app-admins.
1. Voeg de volgende groepen toe aan uw nieuwe app-admins-groep:

   * content-authors
   * workflowgebruikers

   ![chlimage_1-169](assets/chlimage_1-169.png)

   >[!NOTE]
   >
   >workflowgebruikers moeten op afstand bouwen met de service PhoneGap Build

1. Navigeer naar [Machtigingen console](http://localhost:4502/useradmin) en voeg machtigingen toe om cloudservices te beheren

   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/cloudservices/mobileservices

1. Voeg op dezelfde machtigingenconsole machtigingen toe aan het werkgebied, publiceer en wis de updates van de toepassingsinhoud.

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
1. Inhoud exporteren of uploaden

   * (Lezen) Bij /etc/contentsync voor toegang tot exportsjablonen
   * (Lezen) op /var naar voor pad traversal bij lezen
   * (Lezen, Schrijven, Wijzigen, Verwijderen) op /var/contentSync voor het schrijven, lezen en opschonen van ContentSync in cache opgeslagen exportinhoud

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden voor het maken van een AEM Mobile On-demand Services-app:

* [AEM voor AEM Mobile On-demand Services ontwikkelen](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM inhoud voor AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)
