---
title: AEM Mobile-configuratie
seo-title: AEM Mobile-configuratie
description: Volg deze pagina om AEM Mobile in te stellen en zo de gebruiker de inhoud binnen AEM te maken en te beheren. Deze pagina biedt informatie over het integreren van de AEM instantie met de op cloud gebaseerde AEM Mobile On-demand Services-account en -project(en).
seo-description: Volg deze pagina om AEM Mobile in te stellen en zo de gebruiker de inhoud binnen AEM te maken en te beheren. Deze pagina biedt informatie over het integreren van de AEM instantie met de op cloud gebaseerde AEM Mobile On-demand Services-account en -project(en).
uuid: 03bf5b56-7750-4f76-b079-43761367655a
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: 393cf504-917e-4bf6-9a8b-b7a5bd862c65
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---


# AEM Mobile-configuratie{#aem-mobile-setup}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

>[!CAUTION]
>
>Bestaande klanten van AEM Mobile Apps die van AEM 6.2 of 6.3 aan AEM 6.5 migreren kunnen AEM Mobile Apps blijven gebruiken door een [pakket van PackageShare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/compatpack/aem-mobile-package) te downloaden. Nieuwe installaties van AEM 6.5 bieden echter geen ondersteuning voor de functionaliteit van AEM Mobile Apps.

Als u AEM wilt gebruiken om inhoud te produceren voor AEM Mobile-apps, moet u het AEM-exemplaar integreren met de op de cloud gebaseerde AEM Mobile On-demand Services-account en -project(en).

Voer de volgende stappen uit om AEM Mobile in te stellen, zodat de gebruiker de inhoud binnen AEM kan maken en beheren.

## AEM Mobile-provisioning {#aem-mobile-provisioning}

Om aan de slag te gaan met het instellen van AEM Mobile, moet u:

* **Een API-sleutel** aanvragen: Om tot de On-Demand Services API toegang te hebben, moet u een API-sleutel aanvragen. Als u de API-sleutel wilt aanvragen, vult u het [PDF-formulier](https://helpx.adobe.com/digital-publishing-solution/help/integrating-dps.html) in. Verzend het ingevulde formulier naar Adobe Developer Support: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Genereer de apparaat-id en het apparaattoken**: Nadat u de API-sleutel hebt ontvangen, kunt u de apparaat-id en het apparaattoken genereren. Ga naar [https://aex.aemmobile.adobe.com](https://aex.aemmobile.adobe.com/) en voer de volgende handelingen uit:

   * API-sleutel opgeven
   * Aanmelden bij een Adobe ID die u met de volgende machtigingen aan een AEM Mobile-project hebt toegevoegd (zie de onderstaande stappen voor het maken van een project)

      * Beheer > Projecten en gebruikers beheren
      * Inhoud > Inhoud toevoegen en bewerken, Inhoud verwijderen, Inhoud weergeven, Inhoud publiceren

Als aan alle voorwaarden wordt voldaan, worden een apparaat-id en apparaattoken gegenereerd.

>[!NOTE]
>
>De Adobe ID moet toegang krijgen tot een AEM Mobile-project. Zie [Account Administration for AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in Online Help.

## Projecten maken voor AEM Mobile {#creating-projects-for-aem-mobile}

Wanneer u een project creeert, specificeert u montages voor om het even welk platform u richt: iOS, Android, Windows en Desktop Web Viewer. Veel van de projectinstellingen die u opgeeft, zijn van invloed op het gedrag van de app.

Voor het maken van een project moet u zich aanmelden bij het portal On-Demand Services met een Adobe ID met een Master beheerdersrol. Het uitgeven van een project vereist of een Master rol Admin of een gebruikersrol met een **Manage Projecten en Gebruikers** toestemming.

>[!NOTE]
>
>Voor meer informatie over het maken van projecten in AEM Mobile klikt u [hier](https://helpx.adobe.com/digital-publishing-solution/help/creating-projects.html).

## Een AEM Mobile-connector {#configuring-an-aem-mobile-connector} configureren

AEM opstelling impliceert de volgende stappen voor schakelaarconfiguratie. Zodra de configuratie van de AEM Mobile-connector is voltooid, kan de gebruiker gebruikersgroepen en machtigingen instellen.

De AEM Mobile On-Demand-aansluiting wordt gebruikt om door AEM Mobile beheerde inhoud te binden met de On-Demand-services van Adobe Experience Manager Mobile. Hierdoor kunnen auteurs van inhoud materiaal voor mobiele toepassingen maken en beheren met de gereedschappen van AEM terwijl ze de On-Demand-services van AEM Mobile gebruiken voor eenvoudige distributie van mobiele inhoud.

>[!NOTE]
>
>Dit is een eenmalige stap om de AEM-instantie in te stellen.

### AEM Mobile On-demand Services-client {#configuring-aem-mobile-on-demand-services-client} configureren

De AEM Mobile-integratie werkt alleen correct als u de configuratiestappen hebt voltooid.

1. Ga naar de dienst van OSGI configuratie

   1. AEM > Gereedschappen > Bewerkingen > Webconsole
   1. Schuiven of zoeken naar ***Experience Manager Mobile On-demand Services Client (was Adobe Digital Publishing Solution Client)***

1. Bewerk ***Experience Manager Mobile On-demand Services Client***

   1. **(Verplicht)** Voer de vereiste velden in:

      1. Client-id.
      1. Clientgeheim.
   1. **(Optioneel)Bestaande waarden** bewerken.


1. Sla de wijzigingen op.
1. Hier volgt een voorbeeldconfiguratie:

![chlimage_1-53](assets/chlimage_1-53.png)

### AEM Mobile On-demand Services CloudService {#configuring-aem-mobile-on-demand-services-cloudservice} configureren

1. Ga naar Cloud Services

   1. AEM > Extra > Implementatie> [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Schuiven of zoeken naar ***Adobe Experience Manager Mobile On-demand Services***

1. Selecteer ***Nu configureren*** of ***Configuraties tonen*** en selecteer het pictogram Nieuwe configuratie toevoegen

1. Een nieuwe configuratie maken

   1. Voer een titel en naam in
   1. Apparaat-id invoeren
   1. Apparaattoken invoeren
   1. Selecteer ***Apparaatconfiguratie testen*** om ingevoerde waarden te valideren
   1. Selecteer OK

## AEM Mobile-gebruikersrollen toevoegen en machtigingen {#adding-aem-mobile-user-roles-and-assigning-permissions} toewijzen

Nadat u een project hebt gemaakt, moet u rollen maken en gebruikers toegang verlenen. Alleen Master beheerders kunnen rollen maken en bewerken. Wanneer u een rol creeert, laat u mogelijkheden (of toestemmingen) voor toe welke gebruikers die toestemmingen worden toegewezen. U kunt bijvoorbeeld een rol maken die machtigingen voor het maken van apps en een andere rol bevat die machtigingen voor het maken en publiceren van inhoud bevat.

In de ontwikkeling van AEM Mobile-apps bestaan drie verschillende rollen:

* Beheerder
* Developer
* Auteur

Voor meer informatie over het creëren van rollen met verschillende toestemmingen zoals voor app het bouwen of voor het creëren van en het publiceren van inhoud, klik [het Creëren van de Rollen van de Gebruiker en het Verlenen van Toegang](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in de Hulp van AEM Mobile.

>[!NOTE]
>
>Voor het beheren van app-inhoud is een gezamenlijke inspanning van ontwikkelaars, makers van inhoud en beheerders vereist. Auteurs manipuleren pagina&#39;s, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd. Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud. Het instellen AEM Groepen en Toestemmingen bepaalt hun rollen in het app Dashboard of Controlecentrum.
>
>Klik [hier](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor meer informatie over het AEM Mobile-dashboard.

Als u klaar bent met het maken van rollen met verschillende machtigingen, zoals voor het maken van apps of voor het maken en publiceren van inhoud, raadpleegt u [**Uw gebruikers- en gebruikersgroepen configureren**](/help/mobile/aem-mobile-configure-users.md) om uw gebruikers en groepen te configureren ter ondersteuning van het ontwerpen en beheren van uw mobiele apps.

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden voor het maken van een AEM Mobile On-demand Services-app:

* [AEM voor AEM Mobile On-demand Services ontwikkelen](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM inhoud voor AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Zie [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md) voor een voorvertoning van de inhoud van de app, inclusief bladerpagina&#39;s en artikelen.
