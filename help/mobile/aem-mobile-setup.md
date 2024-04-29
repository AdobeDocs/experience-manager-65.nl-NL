---
title: AEM Mobile-configuratie
description: Volg deze pagina voor het instellen van AEM Mobile en zo kan de gebruiker de inhoud maken en beheren in Adobe Experience Manager (AEM). Deze pagina biedt informatie over het integreren van de AEM instantie met de op cloud gebaseerde AEM Mobile On-demand Services-account en -projecten.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
exl-id: 0ead982d-2315-4947-b762-596aa2aa42a1
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# AEM Mobile-configuratie{#aem-mobile-setup}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>Klanten met bestaande Adobe Experience Manager (AEM) Mobile Apps die migreren van AEM 6.2 of 6.3 naar AEM 6.5, kunnen AEM Mobile Apps blijven gebruiken door een pakket te downloaden van Package Share. Nieuwe installaties van AEM 6.5 ondersteunen echter de functionaliteit van AEM Mobile Apps niet.

Als u AEM wilt gebruiken om inhoud te produceren voor AEM Mobile-apps, moet u het AEM-exemplaar integreren met de op de cloud gebaseerde AEM Mobile On-demand Services-account en -projecten.

Voer de volgende stappen uit om AEM Mobile in te stellen, zodat de gebruiker de inhoud binnen AEM kan maken en beheren.

## AEM Mobile-provisioning {#aem-mobile-provisioning}

Om aan de slag te gaan met het instellen van AEM Mobile, moet u:

* **Een API-sleutel aanvragen**: Voor toegang tot de API voor On-Demand Services moet u een API-sleutel aanvragen. Als u de API-sleutel wilt aanvragen, voert u de [PDF-formulier](https://helpx.adobe.com/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html). Verzend het ingevulde formulier naar Adobe Developer Support: [wwds@adobe.com](mailto:wwds@adobe.com)

* **Apparaat-id en apparaattoken genereren**: Nadat u de API-sleutel hebt ontvangen, kunt u de apparaat-id en het apparaattoken genereren. Ga naar `https://aex.aemmobile.adobe.com` en voer de volgende handelingen uit:

   * De API-sleutel opgeven
   * Aanmelden bij een Adobe ID die u met de volgende machtigingen aan een AEM Mobile-project hebt toegevoegd (zie onderstaande stappen om een project te maken)

      * Beheer > Projecten en gebruikers beheren
      * Inhoud > Inhoud toevoegen en bewerken, Inhoud verwijderen, Inhoud weergeven, Inhoud publiceren

Als aan alle voorwaarden wordt voldaan, worden een apparaat-id en apparaattoken gegenereerd.

>[!NOTE]
>
>De Adobe ID moet toegang krijgen tot een AEM Mobile-project. Zie [Account Administration voor AEM Mobile](https://helpx.adobe.com/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html) in online Help.

## Projecten maken voor AEM Mobile {#creating-projects-for-aem-mobile}

Wanneer u een project maakt, geeft u instellingen op voor elk platform waarvoor u zich richt: iOS, Android™, Windows en Desktop Web Viewer. Veel van de projectinstellingen die u opgeeft, zijn van invloed op het gedrag van de app.

Voor het maken van een project moet u zich aanmelden bij het portal On-Demand Services met een Adobe ID met beheerdersrol als hoofd. Het uitgeven van een project vereist of een Hoofdrol Admin of een gebruikersrol met een **Projecten en gebruikers beheren** toestemming.

>[!NOTE]
>
>Klik voor meer informatie over Projecten maken in AEM Mobile op [hier](https://helpx.adobe.com/digital-publishing-solution/help/creating-projects.html).

## Een AEM Mobile-connector configureren {#configuring-an-aem-mobile-connector}

AEM opstelling impliceert de volgende stappen voor schakelaarconfiguratie. Zodra de configuratie van de AEM Mobile-connector is voltooid, kan de gebruiker gebruikersgroepen en machtigingen instellen.

De AEM Mobile On-Demand-aansluiting wordt gebruikt om door AEM Mobile beheerde inhoud te binden met Adobe Experience Manager Mobile On-Demand-services. Op deze manier kunnen auteurs van inhoud materiaal voor mobiele toepassingen maken en beheren met behulp van AEM tools terwijl ze de On-Demand-services van AEM Mobile gebruiken voor eenvoudige distributie van mobiele inhoud.

>[!NOTE]
>
>Dit is een eenmalige stap om de AEM-instantie in te stellen.

### AEM Mobile On-demand Services Client configureren {#configuring-aem-mobile-on-demand-services-client}

Voltooi de configuratiestappen voor de integratie van AEM Mobile correct te functioneren.

1. Ga naar de dienst van OSGI configuratie

   1. AEM > Gereedschappen > Bewerkingen > Webconsole
   1. Schuiven of zoeken naar ***Experience Manager Mobile On-demand Services Client (was Adobe Digital Publishing Solution Client)***

1. Bewerken ***Experience Manager Mobile On-demand Services Client***

   1. **(Verplicht)** Voer de vereiste velden in:

      1. Client-id.
      1. Clientgeheim.

   1. **(Optioneel)** Bestaande waarden bewerken.

1. Sla de wijzigingen op.
1. Hier volgt een voorbeeldconfiguratie:

![chlimage_1-53](assets/chlimage_1-53.png)

### AEM Mobile On-demand Services CloudService configureren {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Ga naar Cloud Servicen.

   1. AEM > Extra > Implementatie> [CloudServices](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). Schuiven of zoeken naar ***Adobe Experience Manager Mobile On-demand-services***

1. Selecteren ***Nu configureren*** of ***Configuraties tonen*** en selecteert u het configuratiepictogram toevoegen.

1. Een configuratie maken

   1. Voer een titel en naam in
   1. Apparaat-id invoeren
   1. Apparaattoken invoeren
   1. Selecteren ***Apparaatconfiguratie testen*** zodat u ingevoerde waarden kunt valideren
   1. Selecteer OK

## AEM Mobile-gebruikersrollen toevoegen en machtigingen toewijzen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nadat u een project hebt gemaakt, moet u rollen maken en gebruikers toegang verlenen. Alleen hoofdbeheerders kunnen rollen maken en bewerken. Wanneer u een rol creeert, laat u mogelijkheden (of toestemmingen) voor toe welke gebruikers die toestemmingen worden toegewezen. U kunt bijvoorbeeld een rol maken die machtigingen voor het maken van apps en een andere rol bevat die machtigingen voor het maken en publiceren van inhoud bevat.

In de ontwikkeling van AEM Mobile-apps bestaan drie verschillende rollen:

* Beheerder
* Developer
* Auteur

Klik voor meer informatie over het maken van rollen met verschillende machtigingen, zoals voor het maken van apps of voor het maken en publiceren van inhoud. [Gebruikersrollen maken en toegang verlenen](https://helpx.adobe.com/digital-publishing-solution/help/account-admin-dps.html) in AEM Mobile Help.

>[!NOTE]
>
>Voor het beheren van app-inhoud is een gezamenlijke inspanning van ontwikkelaars, auteurs van inhoud en beheerders vereist. Auteurs manipuleren pagina&#39;s, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd. Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud. Het instellen AEM Groepen en Toestemmingen bepaalt hun rollen in het app Dashboard of Controlecentrum.
>
>Zie [AEM Mobile-dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

Wanneer u klaar bent met het maken van rollen met verschillende machtigingen, zoals voor het maken van apps of voor het maken en publiceren van inhoud, raadpleegt u [**Uw gebruikers- en gebruikersgroepen configureren**](/help/mobile/aem-mobile-configure-users.md). Zo kunt u uw gebruikers en groepen configureren voor ondersteuning van het ontwerpen en beheren van uw mobiele apps.

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden voor het maken van een AEM Mobile On-demand Services-app:

* [AEM voor AEM Mobile On-demand Services ontwikkelen](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM inhoud voor AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Als u een voorvertoning van de inhoud van de app wilt weergeven, inclusief bladerpagina&#39;s en artikelen, raadpleegt u [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md).
