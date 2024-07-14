---
title: Uw gebruikers en gebruikersgroepen configureren
description: Volg deze pagina om de gebruikersrollen te begrijpen en hoe te om uw gebruikers en groepen te vormen om het ontwerpen en het beheer van uw mobiele On-Demand de dienstenapp te steunen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
exl-id: 58b7d1b9-a851-442a-9d02-212cad8abbed
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# Uw gebruikers en gebruikersgroepen configureren {#configure-your-users-and-user-groups}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [ leer meer ](/help/sites-developing/spa-overview.md).

In dit hoofdstuk worden de gebruikersrollen beschreven en wordt beschreven hoe u uw gebruikers en groepen kunt configureren om het ontwerpen en beheren van uw mobiele apps te ondersteunen.

## AEM Mobile Application Users en Group Administration {#aem-mobile-application-users-and-group-administration}

### AEM Mobile Application Content Authors (groep voor het schrijven van apps) {#aem-mobile-application-content-authors-app-author-group}

Leden van de groep die de app heeft geschreven, zijn verantwoordelijk voor het ontwerpen AEM inhoud van mobiele toepassingen, zoals pagina&#39;s, tekst, afbeeldingen en video&#39;s.

#### Groepsconfiguratie - toepassingsauteurs {#group-configuration-app-authors}

1. Maak een gebruikersgroep met de naam &#39;app-authors&#39;:

   Navigeer aan de Admin Console van de Gebruiker: [ http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Selecteer in de gebruikersgroepconsole de knop &#39;+&#39; om een groep te maken.

   Stel de id van deze groep in op &#39;toepassingsauteurs&#39; om aan te geven dat het een specifiek type gebruikersgroep voor auteurs is die specifiek is voor het ontwerpen van mobiele toepassingen in AEM.

1. Lid toevoegen aan groep: Auteurs

   ![ chlimage_1-167 ](assets/chlimage_1-167.png)

1. Nu u de app-auteursGebruikersgroep hebt gecreeerd, kunt u individuele teamleden aan deze nieuwe groep door de [ Admin Console van de Gebruiker ](http://localhost:4502/libs/granite/security/content/useradmin.md) toevoegen.

   ![ chlimage_1-168 ](assets/chlimage_1-168.png)

1. In het volgende voorbeeld kunt u toevoegen aan AEM groep Content Authors:

   (Lezen) op

   * /app
   * /etc/clientlibs
   * /etc/designs
   * /etc/cloudservices/dps2015

### AEM Mobile Application Administrators Group (groep toepassingsbeheerders) {#aem-mobile-application-administrators-group-app-admins-group}

De leden van app-admins groep kunnen toepassingsinhoud met de zelfde toestemmingen inbegrepen met app-auteurs **EN** bovendien zijn ook verantwoordelijk voor:

* Toepassingsupdates voor ContentSync OTA opslaan, publiceren en wissen

>[!NOTE]
>
>De toestemmingen bepalen beschikbaarheid van sommige gebruikersacties in het Centrum van het Bevel van de AEM App.
>
>Sommige opties zijn niet beschikbaar voor auteurs van apps die beschikbaar zijn voor app-beheerders.

### Groepsconfiguratie - app-beheerders {#group-configuration-app-admins}

1. Maak een groep met de naam app-admins.
1. Voeg de volgende groepen toe aan uw nieuwe groep voor toepassingsbeheer:

   * content-authors
   * workflowgebruikers

   ![ chlimage_1-169 ](assets/chlimage_1-169.png)

   >[!NOTE]
   >
   >workflowgebruikers moeten op afstand bouwen met de service PhoneGap Build

1. Navigeer aan de [ console van Toestemmingen ](http://localhost:4502/useradmin) en voeg toestemmingen toe om cloudservices te beheren

   * (Lezen, Wijzigen, Maken, Verwijderen, Repliceren) op /etc/cloudservices/mobileservices

1. Voeg op dezelfde machtigingenconsole machtigingen toe aan het werkgebied, publiceer en wis de updates van de toepassingsinhoud.

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
1. Inhoud exporteren of uploaden

   * (Lezen) op /etc/contentSync voor toegang tot exportsjablonen
   * (Lezen) op /var aan weg traversal op leest
   * (Lezen, Schrijven, Wijzigen, Verwijderen) op /var/contentSync voor het schrijven, lezen en opschonen van ContentSync-exportinhoud in cache

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden voor het maken van een AEM Mobile On-demand Services-app:

* [AEM voor AEM Mobile On-demand Services ontwikkelen](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM inhoud voor AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)
