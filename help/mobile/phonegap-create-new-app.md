---
title: Een nieuwe AEM Mobile-app maken met de wizard Maken
seo-title: Een nieuwe AEM Mobile-app maken met de wizard Maken
description: AEM Mobile-toepassingen zijn gebaseerd op een blauwdruk die een paginastructuur en eigenschappen definieert. Volg deze pagina voor meer informatie over het maken van een nieuwe app op basis van een toepassingssjabloon.
seo-description: AEM Mobile-toepassingen zijn gebaseerd op een blauwdruk die een paginastructuur en eigenschappen definieert. Volg deze pagina voor meer informatie over het maken van een nieuwe app op basis van een toepassingssjabloon.
uuid: c2bd63a5-3dff-4a72-b1fb-0c776e0afa33
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 27605eb7-59b2-42d4-8cc5-02cfa52b4491
translation-type: tm+mt
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---


# Een nieuwe AEM Mobile-toepassing maken met een wizard{#creating-a-new-aem-mobile-app-using-create-wizard}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

AEM Mobile-toepassingen zijn gebaseerd op een blauwdruk die een paginastructuur en eigenschappen definieert. U kunt de volgende toepassingseigenschappen configureren:

* **Titel:** de toepassingstitel.
* **Doelpad:** de locatie in de opslagplaats waar de toepassing is opgeslagen. Laat de standaardinstelling ongewijzigd om een pad te maken op basis van de toepassingsnaam.

* **Naam:** De standaardwaarde is de waarde van de eigenschap Titel, waarbij spatietekens zijn verwijderd. De naam wordt binnen AEM gebruikt om naar de toepassing te verwijzen, bijvoorbeeld voor het opslagknooppunt dat de toepassing vertegenwoordigt.
* **Beschrijving:** een beschrijving van de toepassing.
* **Server-URL:** de URL die OTA-inhoud (Over-the-Air) biedt, wordt bijgewerkt naar de toepassing. De standaardwaarde is de URL van de publicatieserver van de instantie die wordt gebruikt om een toepassing te maken (deze is afkomstig van de externalizer-service). Opmerking: dit moet een publicatieserverinstantie zijn in plaats van een auteur, die verificatie vereist.

U kunt ook een afbeeldingsbestand opgeven dat u als miniatuur van de toepassing wilt gebruiken, de configuratie van de PhoneGap Build selecteren en de analytische configuratie voor de mobiele app selecteren die u wilt gebruiken. Deze afbeelding wordt alleen gebruikt als miniatuur voor uw mobiele toepassing in de console voor mobiele apps in Experience Manager.

Er zijn extra (en optionele) tabbladen voor het samenstellen van cloudservice en het integreren van de Adobe Mobile Services SDK-plug-in in uw app.

* Opbouwen: Klik hier op Configuraties beheren en stel de build.phonegap.com-service in. Vervolgens kunt u in de vervolgkeuzelijst de nieuwe PhoneGap-service voor de build-cloud selecteren.
* Analyse: Klik op Configuraties beheren en stel de [Adobe Mobile Services SDK](https://docs.adobe.com/content/help/en/mobile-services/using/home.html)-cloudservice in. Vervolgens kunt u in het keuzemenu de nieuwe mobiele service selecteren die u wilt integreren in uw mobiele app.

## App-sjablonen gebruiken {#using-app-templates}

Toepassingssjablonen bieden een eenvoudige manier om gebruik te maken van bestaande ontwerpen die door ontwikkelaars zijn gemaakt en die worden gebruikt voor het maken van nieuwe apps in AEM.

Wat is een toepassingssjabloon? Beschouw het als een verzameling paginasjablonen en componenten die een basislijn of basis van een app vormen.
Wanneer u een nieuwe app maakt op basis van de sjabloon van een andere app, krijgt u een app met een beginpunt dat representatief is voor de app waarin deze is gemaakt.

U moet een bestaande sjabloon voor mobiele apps (of een app met een toepassingssjabloon) hebben om van deze functie gebruik te kunnen maken.

Het meest recente pakket met voorbeelden van AEM Apps bevat een bijgewerkte versie van de Geometrixx-app met een toepassingssjabloon. U kunt ook [StarterKit](https://github.com/Adobe-Marketing-Cloud-Apps/aem-phonegap-starter-kit) installeren, die ook een sjabloon biedt.

Stappen voor het maken van een nieuwe app op basis van een toepassingssjabloon:

1. Ga naar de AEM Mobile-toepassingscatalogus: &lt;*server-url*>aem/apps.html/content/mobileapps
1. Selecteer **Maken** en kies **App** zoals hieronder wordt getoond

![chlimage_1-158](assets/chlimage_1-158.png)

Selecteer een toepassingssjabloon die u van een AEM ontwikkelaar kunt krijgen. Zie [Structuur van een AEM Mobile App](/help/mobile/phonegap-structure-an-app.md) voor hulp aan ontwikkelaars.

![chlimage_1-159](assets/chlimage_1-159.png)

Vul de details van de nieuwe app zo nodig in, inclusief de mogelijkheid om de miniatuurafbeelding te wijzigen. Deze waarden kunnen later uit **Manage App** tegel worden uitgegeven.

![chlimage_1-160](assets/chlimage_1-160.png)

## De volgende stappen {#the-next-steps}

Zie de volgende middelen om meer over andere auteursrollen te leren:

* [De app-tegel beheren](/help/mobile/phonegap-app-details-tile.md)
* [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md)
* [Toepassingsdefinities](/help/mobile/phonegap-app-definitions.md)
* [Een bestaande hybride app importeren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Inhoudsservices](/help/mobile/develop-content-as-a-service.md)

## Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
