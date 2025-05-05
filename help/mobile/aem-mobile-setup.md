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
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# AEM Mobile-configuratie{#aem-mobile-setup}

{{ue-over-mobile}}

>[!CAUTION]
>
>Klanten met bestaande Adobe Experience Manager (AEM) Mobile Apps die migreren van AEM 6.2 of 6.3 naar AEM 6.5, kunnen AEM Mobile Apps blijven gebruiken door een pakket te downloaden van Package Share. Nieuwe installaties van AEM 6.5 ondersteunen echter de functionaliteit van AEM Mobile Apps niet.

Als u AEM wilt gebruiken om inhoud te produceren voor AEM Mobile-apps, moet u het AEM-exemplaar integreren met de op de cloud gebaseerde AEM Mobile On-demand Services-account en -projecten.

Voer de volgende stappen uit om AEM Mobile in te stellen, zodat de gebruiker de inhoud binnen AEM kan maken en beheren.

## AEM Mobile-provisioning {#aem-mobile-provisioning}

Om aan de slag te gaan met het instellen van AEM Mobile, moet u:

* **verzoek een API sleutel**: Om tot de On-Demand API van de Diensten toegang te hebben, moet u om een API sleutel verzoeken. Om de API sleutel aan te vragen, voltooi de [ vorm van de PDF ](https://helpx.adobe.com/nl/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html). Verzend de voltooide vorm naar de Steun van Adobe Developer: [ wwds@adobe.com](mailto:wwds@adobe.com)

* **produceer identiteitskaart van het Apparaat en Symbolisch van het Apparaat**: Zodra u uw API sleutel hebt ontvangen, kunt u apparatenidentiteitskaart en apparatenteken produceren. Ga naar `https://aex.aemmobile.adobe.com` en voer de volgende handelingen uit:

   * De API-sleutel opgeven
   * Aanmelden bij een Adobe ID die u met de volgende machtigingen aan een AEM Mobile-project hebt toegevoegd (zie onderstaande stappen om een project te maken)

      * Beheer > Projecten en gebruikers beheren
      * Inhoud > Inhoud toevoegen en bewerken, Inhoud verwijderen, Inhoud weergeven, Publish-inhoud

Als aan alle voorwaarden wordt voldaan, worden een apparaat-id en apparaattoken gegenereerd.

>[!NOTE]
>
>De Adobe ID moet toegang krijgen tot een AEM Mobile-project. Zie [ Beleid van de Rekening voor AEM Mobile ](https://helpx.adobe.com/nl/digital-publishing-solution/help/aem-mobile-end-of-life-faq.html) in Online Hulp.

## Projecten maken voor AEM Mobile {#creating-projects-for-aem-mobile}

Wanneer u een project maakt, geeft u instellingen op voor elk platform waarvoor u zich richt: iOS, Android™, Windows en Desktop Web Viewer. Veel van de projectinstellingen die u opgeeft, zijn van invloed op het gedrag van de app.

Voor het maken van een project moet u zich aanmelden bij het portal On-Demand Services met een Adobe ID met beheerdersrol als hoofd. Het uitgeven van een project vereist of een Hoofdrol Admin of een gebruikersrol met a **leidt Projecten en Gebruikers** toestemming.

>[!NOTE]
>
>Meer over het Creëren van Projecten in AEM Mobile leren, klik [ hier ](https://helpx.adobe.com/nl/digital-publishing-solution/help/creating-projects.html).

## Een AEM Mobile-connector configureren {#configuring-an-aem-mobile-connector}

AEM opstelling impliceert de volgende stappen voor schakelaarconfiguratie. Zodra de configuratie van de AEM Mobile-connector is voltooid, kan de gebruiker gebruikersgroepen en machtigingen instellen.

De AEM Mobile On-Demand-aansluiting wordt gebruikt om door AEM Mobile beheerde inhoud te binden met Adobe Experience Manager Mobile On-Demand-services. Op deze manier kunnen auteurs van inhoud materiaal voor mobiele toepassingen maken en beheren met behulp van AEM gereedschappen terwijl ze de On-Demand-services van AEM Mobile gebruiken voor eenvoudige distributie van mobiele inhoud.

>[!NOTE]
>
>Dit is een eenmalige stap om de AEM-instantie in te stellen.

### AEM Mobile On-demand Services Client configureren {#configuring-aem-mobile-on-demand-services-client}

Voltooi de configuratiestappen voor de integratie van AEM Mobile correct te functioneren.

1. Ga naar de dienst van OSGI configuratie

   1. AEM > Gereedschappen > Bewerkingen > Webconsole
   1. De rol of het onderzoek naar ***Experience Manager Mobiele Cliënt van de Diensten op bestelling (was de Cliënt van de Oplossing van de Adobe Digitale Publishing)***

1. Bewerk ***Experience Manager de Mobiele Cliënt van de Diensten op bestelling***

   1. **(Verplicht)** ga de vereiste gebieden in:

      1. Client-id.
      1. Clientgeheim.

   1. **(Optioneel)** Bestaande waarden bewerken.

1. Sla de wijzigingen op.
1. Hier volgt een voorbeeldconfiguratie:

![ chlimage_1-53 ](assets/chlimage_1-53.png)

### AEM Mobile On-demand Services CloudService configureren {#configuring-aem-mobile-on-demand-services-cloudservice}

1. Ga naar Cloud Servicen.

   1. AEM > Hulpmiddelen > Plaatsing> [ CloudServices ](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html). De rol of het onderzoek naar ***Adobe Experience Manager Mobile On-demand Services***

1. Selecteer ***nu vormen*** of ***tonen Configuraties*** en selecteren het add configuratiepictogram.

1. Een configuratie maken

   1. Voer een titel en naam in
   1. Apparaat-id invoeren
   1. Apparaattoken invoeren
   1. Selecteer ***de Configuratie van het Apparaat van de Test*** zodat kunt u ingevoerde waarden bevestigen
   1. Selecteer OK

## AEM Mobile-gebruikersrollen toevoegen en machtigingen toewijzen {#adding-aem-mobile-user-roles-and-assigning-permissions}

Nadat u een project hebt gemaakt, moet u rollen maken en gebruikers toegang verlenen. Alleen hoofdbeheerders kunnen rollen maken en bewerken. Wanneer u een rol creeert, laat u mogelijkheden (of toestemmingen) voor toe welke gebruikers die toestemmingen worden toegewezen. U kunt bijvoorbeeld een rol maken die machtigingen voor het maken van apps en een andere rol bevat die machtigingen voor het maken en publiceren van inhoud bevat.

In de ontwikkeling van AEM Mobile-apps bestaan drie verschillende rollen:

* Beheerder
* Developer
* Auteur

Voor meer informatie bij het creëren van rollen met verschillende toestemmingen zoals voor app het bouwen of voor het creëren van en het publiceren van inhoud, klik [ Creërend de Rollen van de Gebruiker en het Verlenen van Toegang ](https://helpx.adobe.com/nl/digital-publishing-solution/help/account-admin-dps.html) in de Hulp van AEM Mobile.

>[!NOTE]
>
>Voor het beheren van app-inhoud is een gezamenlijke inspanning van ontwikkelaars, auteurs van inhoud en beheerders vereist. Auteurs manipuleren pagina&#39;s, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd. Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud. Het instellen AEM Groepen en Toestemmingen bepaalt hun rollen in het app Dashboard of Controlecentrum.
>
>Zie [ het Dashboard van AEM Mobile ](/help/mobile/mobile-apps-ondemand-application-dashboard.md).

Wanneer u wordt gedaan creërend rollen met verschillende toestemmingen, zoals voor app het bouwen of voor het creëren van en het publiceren van inhoud, zie [**uw Gebruiker en de Groepen van de Gebruiker**](/help/mobile/aem-mobile-configure-users.md) vormen. Zo kunt u uw gebruikers en groepen configureren voor ondersteuning van het ontwerpen en beheren van uw mobiele apps.

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de andere twee rollen en verantwoordelijkheden voor het maken van een AEM Mobile On-demand Services-app:

* [AEM voor AEM Mobile On-demand Services ontwikkelen](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM inhoud voor AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)

>[!NOTE]
>
>Om de app inhoud, met inbegrip van doorbladeren pagina&#39;s, en artikelen voor te vertonen, zie [ Voorproef met Preflight ](/help/mobile/aem-mobile-manage-ondemand-services.md).
