---
title: Mobiele toepassingen maken
seo-title: Mobiele toepassingen maken
description: Deze pagina verstrekt een volledig geleidelijke artikel op hoe te om een mobiele toepassing te bouwen gebruikend code beschikbaar bij GitHub is hier beschikbaar.Bouw uw toepassing om aan een apparaat of simulator voor het testen of voor het publiceren aan app winkels te installeren. U kunt toepassingen plaatselijk bouwen gebruikend de Interface van de Lijn van het Bevel PhoneGap, of in de wolk gebruikend PhoneGap Build.
seo-description: Deze pagina verstrekt een volledig geleidelijke artikel op hoe te om een mobiele toepassing te bouwen gebruikend code beschikbaar bij GitHub is hier beschikbaar.Bouw uw toepassing om aan een apparaat of simulator voor het testen of voor het publiceren aan app winkels te installeren. U kunt toepassingen plaatselijk bouwen gebruikend de Interface van de Lijn van het Bevel PhoneGap, of in de wolk gebruikend PhoneGap Build.
uuid: 1ff6fe1a-24cc-4973-a2cd-8d356bc649b0
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b2778086-8280-4306-bf3a-f6ec2a0e04df
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 0%

---


# Mobiele toepassingen maken{#building-mobile-applications}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Stel uw toepassing samen om deze op een apparaat of simulator te installeren voor testdoeleinden of voor publicatie in de App Store. U kunt toepassingen plaatselijk bouwen gebruikend de Interface van de Lijn van het Bevel PhoneGap, of in de wolk gebruikend PhoneGap Build.

Een volledig geleidelijke artikel op hoe te om een mobiele toepassing te bouwen gebruikend code beschikbaar bij GitHub is beschikbaar [hier](https://helpx.adobe.com/experience-manager/using/aem62_mobile.html).

## De toepassing verplaatsen naar de instantie Publiceren {#moving-the-application-to-the-publish-instance}

Verplaats toepassingsbestanden naar de publicatie-instantie zodat u inhoud-updates kunt opgeven voor de geïnstalleerde exemplaren van de mobiele toepassing en de toepassing kunt bouwen met behulp van de gepubliceerde inhoud. Toepassingen bestaan uit twee knooppuntvertakkingen in de repository:

* `/content/phonegap/apps/<application name>`: De webpagina&#39;s die auteurs maken en activeren.
* `/content/phonegap/content/<application name>`: Configuratiebestanden voor de toepassing en configuraties voor inhoudssynchronisatie.

>[!NOTE]
>
>Als u de toepassingsbestanden niet naar de publicatie-instantie verplaatst, kunnen de makers van inhoud de cache van Content Sync niet bijwerken.

U hoeft de bestanden alleen in de vertakking `/content/phonegap/content/<application name>` naar de publicatie-instantie te verplaatsen. De bestanden in de vertakking `/content/phonegap/apps/<application name>` worden verplaatst wanneer de auteur de pagina&#39;s activeert.

AEM biedt twee methoden voor het verplaatsen van bulkinhoud naar de publicatie-instantie:

* [Gebruik het ](/help/sites-authoring/publishing-pages.md) bevel van de Boom Activate op de replicatieconsole.
* [Maak een ](/help/sites-administering/package-manager.md) pakket dat de inhoud bevat en repliceer het pakket.

Er wordt bijvoorbeeld een mobiele toepassing met de naam phonegapapp gemaakt. Het volgende knooppunt moet worden verplaatst naar de instantie publish: /content/phonegap/content/phonegapapp.

**Tip:** Als u een pakket van de auteurinstantie naar de publicatie-instantie wilt verplaatsen, gebruikt u de opdracht Kopiëren in het pakket.

![chlimage_1-16](assets/chlimage_1-16.png)

## Samenstellen met de PhoneGap Command Line Interface {#building-using-the-phonegap-command-line-interface}

Compileer de toepassing PhoneGap op uw computer gebruikend bevel-lijn Interface PhoneGap (CLI). Als u de AEM-inhoud in uw toepassing wilt opnemen, AEM maakt u een ZIP-bestand dat de inhoud van uw mobiele toepassing, configuraties voor inhoudssynchronisatie en andere vereiste elementen bevat. Download het ZIP-bestand en neem het op in uw build.

### Uw buildomgeving {#preparing-your-build-environment} voorbereiden

Om te bouwen gebruikend CLI PhoneGap, moet u Node.js en het de cliëntnut installeren PhoneGap. U hebt een internetverbinding nodig om de volgende procedure uit te voeren.

1. [Node.js](https://nodejs.org/) downloaden en installeren.
1. Open een terminal of bevelherinnering en ga het volgende knoopbevel in om het nut te installeren PhoneGap:

   ```shell
   npm install -g phonegap
   ```

   Op een Unix- of Linux-systeem moet u mogelijk `sudo` als voorvoegsel voor de opdracht gebruiken.

   De terminal toont de resultaten van een reeks opdrachten van HTTP-GET. Wanneer de installatie succesvol is, toont de terminal waar de bibliotheken geïnstalleerd gelijkaardig aan het volgende voorbeeld zijn:

   ```xml
   /usr/local/bin/phonegap -> /usr/local/lib/node_modules/phonegap/bin/phonegap.js
   phonegap@3.3.0-0.19.6 /usr/local/lib/node_modules/phonegap
   ├── pluralize@0.0.4
   ├── colors@0.6.0-1
   ├── semver@1.1.0
   ├── qrcode-terminal@0.9.4
   ├── shelljs@0.1.4
   ├── optimist@0.6.0 (...)
   ├── prompt@0.2.11 (...)
   ├── phonegap-build@0.8.4 (...)
   ├── connect-phonegap@0.8.1 (...)
   └── cordova@3.3.0-0.1.1 (...)
   ```

1. (Optioneel) Vraag de SDK aan voor het mobiele platform waarvoor u het doelplatform wilt:

   * Installeer de nieuwste versie van [Xcode](https://developer.apple.com/xcode/) om apps voor het iOS-platform te maken.
   * Installeer de [Android-SDK](https://developer.android.com/) om Android-toepassingen te maken.

### Het ZIP-bestand voor inhoud downloaden {#downloading-the-content-zip-file}

Verplaats de inhoud van uw mobiele toepassing naar uw bestandssysteem.

1. Selecteer de toepassing op de pagina Mobiele toepassingen.
1. (Optioneel) Als u de toepassing voor volledige installaties wilt maken, klikt of tikt u op het pictogram Cache wissen op de werkbalk.

   ![](do-not-localize/chlimage_1.png)

   >[!NOTE]
   >
   >De cache bevat updates van inhoud voor geïnstalleerde toepassingen. Als u de cache wist, worden alle updates in de cache verwijderd.

1. Klik of tik op het pictogram CLI-elementen downloaden op de werkbalk.

   ![](do-not-localize/chlimage_1-1.png)

1. Nadat u het ZIP-bestand hebt opgeslagen, klikt u op Sluiten in het dialoogvenster Succes.
1. Extraheer de inhoud van het ZIP-bestand.

### De CLI van PhoneGap gebruiken om {#using-the-phonegap-cli-to-build} te bouwen

Gebruik de CLI van PhoneGap om de toepassing te compileren en te installeren. Voor informatie over hoe te om CLI te gebruiken PhoneGap, zie PhoneGap [bevel-lijn Interface](https://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html) documentatie.

1. Open een terminal- of opdrachtprompt en wijzig de huidige map in het gedownloade ZIP-bestand van de toepassing. Met de volgende code wordt de map bijvoorbeeld gewijzigd in het bestand ng-app-cli.1392137825303.zip:

   ```shell
   cd ~/Downloads/ng-app-cli.1392137825303
   ```

1. Voer de phonegap-opdracht in voor het platform waarvoor u een doelversie kiest. Met de volgende opdracht wordt bijvoorbeeld de app voor Android gemaakt:

   ```shell
   phonegap build android
   ```

## Samenstellen met PhoneGap Build {#building-using-phonegap-build}

Gebruik de PhoneGap-cloudservice om uw app te maken. Om deze procedure uit te voeren, moet u eerst een configuratie van de PhoneGap Build tot stand brengen.

### Verbinding maken met PhoneGap Build {#connecting-to-phonegap-build}

Creeer een configuratie van de PhoneGap Build zodat u de diensten van de PhoneGap Build van binnen AEM kunt gebruiken. Geef de gebruikersnaam en het wachtwoord op van de PhoneGap Build-account waarmee u mobiele toepassingen gaat maken.

1. Open de pagina Gereedschappen. ([http://localhost:4502/tools.html](http://localhost:4502/tools.html)).
1. Klik in het gebied CQ-bewerkingen op Cloud Services.
1. Klik op de koppeling Nu configureren voor PhoneGap Build.

   ![chlimage_1-17](assets/chlimage_1-17.png)

1. Typ in het dialoogvenster Configuratie maken een waarde voor de eigenschap Titel. Door gebrek, wordt de waarde van het bezit van de Naam afgeleid uit de titel, nochtans kunt u een naam ingaan. Klik op Maken.
1. Typ in het dialoogvenster Configuratie PhoneGap Build uw gebruikersnaam en wachtwoord voor de PhoneGap Build en klik op OK.

### PhoneGap Build {#using-phonegap-build} gebruiken

Verzend uw toepassingsbronnen naar PhoneGap Build voor compilatie voor de verschillende mobiele platforms.

1. Open uw mobiele toepassing op de pagina Mobiele toepassingen. ([http://localhost:4502/mobile.html/content/phonegap](http://localhost:4502/mobile.html/content/phonegap))
1. (Optioneel) Als u de toepassing voor volledige installaties wilt maken, selecteert u de toepassing en klikt u op het pictogram Cache wissen.

   ![](do-not-localize/chlimage_1-2.png)

   >[!NOTE]
   >
   >De cache bevat updates van inhoud voor geïnstalleerde toepassingen. Als u de cache wist, worden alle updates in de cache verwijderd.

1. Selecteer de welkomstpagina en klik op het pictogram Extern maken.

   ![](do-not-localize/chlimage_1-3.png)

   **Opmerking:** de bètaversie van AEM bèta maakt geen melding in het Postvak In wanneer de build met succes is voltooid.

1. Klik in het dialoogvenster Succes op PhoneGap Build om de Adobe PhoneGap Build-pagina op [https://build.phonegap.com/apps](https://build.phonegap.com/apps) te openen. Als u wacht op het verschijnen van uw app, kunt u de [PhoneGap Build Status](https://status.build.phonegap.com/) pagina controleren.

   Voor informatie over het installeren van de bouwstijl, zie [Documentatie ](https://docs.build.phonegap.com/en_US/3.1.0/#googtrans%28en%29).

   >[!NOTE]
   >
   >Gratis PhoneGap Build-accounts zijn toegestaan op één privétoepassing. PhoneGap-builds mislukken als u een extra privétoepassing bouwt.

### De volgende stappen {#the-next-steps}

De volgende stap na het bouwproces leert over de [structuur van een app](/help/mobile/phonegap-structure-an-app.md).
