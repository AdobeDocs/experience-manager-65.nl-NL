---
title: Uw Adobe PhoneGap Build Cloud-service configureren
seo-title: Uw Adobe PhoneGap Build Cloud-service configureren
description: Volg deze pagina om de cloudservices te configureren en uw toepassing samen te stellen met PhoneGap-build.
seo-description: Volg deze pagina om de cloudservices te configureren en uw toepassing samen te stellen met PhoneGap-build.
uuid: 59aa99c3-1425-4cc5-9839-a57a6a545d45
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 3c84f4ec-d89b-4ad4-802e-ee3e2d49d916
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Uw Adobe PhoneGap Build Cloud-service configureren {#configure-your-adobe-phonegap-build-cloud-service}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

De **PhoneGap Build-tegel** op het dashboard van de toepassing biedt de mogelijkheid om uw PhoneGap mobiele toepassing te maken en distribueren via de Adobe PhoneGap Build-service.

Alle ondersteunde platforms die zijn gedefinieerd in de tegel **App** beheren, worden gebouwd met PhoneGap Build tijdens het uitvoeren van een externe build met de **PhoneGap Build** Tile.

U kunt een externe build naar [https://build.phonegap.com](https://build.phonegap.com) duwen of de bron downloaden om lokaal met [PhoneGap CLI](https://docs.phonegap.com/references/phonegap-cli/)te bouwen.

![PhoneGap Build-tegel](assets/chlimage_1-60.png)

## Cloudservice configureren {#configuring-the-cloud-service}

Als u gebruik wilt maken van PhoneGap Build, moet u de AEM PhoneGap Build Cloud Service configureren met uw PhoneGap Build-accountgegevens.

Als u momenteel geen account hebt, navigeert u naar [https://build.phonegap.com](https://build.phonegap.com) en meldt u zich aan! Als u een Adobe Creative Cloud-lidmaatschap hebt, hebt u mogelijk ondersteuning voor maximaal 25 persoonlijke apps (apps zonder open bron).

Nadat u hebt gecontroleerd of uw PhoneGap Build-account actief is, navigeert u naar uw AEM Cloud Management Console, met name de [PhoneGap Build Cloud Service](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Met het **beheerblok voor cloudservices** kunt u een nieuwe configuratie voor cloudservices configureren.

### Het element Cloud Services beheren gebruiken {#using-manage-cloud-services-tile}

Voordat u begint met het maken van uw app met **PhoneGap Build** -tegel, moet u de cloudservices configureren met behulp van de tegel **Cloud Services** beheren op het mobiele dashboard van AEM.

Volg onderstaande stappen om cloudservices voor uw app te configureren:

1. Klik in de rechterbovenhoek van de tegel **Cloud Services** beheren.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Kies de optie **PhoneGap Build** in het scherm **Cloud Service** toevoegen of bewerken.

   Click **Next**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Voer uw gegevens in om een nieuwe cloudconfiguratie te maken.

   Klik op **Verzenden** als de verificatie is voltooid. Deze geconfigureerde cloudconfiguratie wordt nu weergegeven in de tegel **Cloud Services** beheren.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Uw toepassing samenstellen met PhoneGap Build {#building-your-application-with-phonegap-build}

Nadat u de cloudservices hebt geconfigureerd, kunt u uw toepassing samenstellen met **PhoneGap Build** -tegel. Klik in de rechterbovenhoek om een keuze te maken uit de opties **Build Remote** of **Download Source** .

![chlimage_1-64](assets/chlimage_1-64.png)

Als u een externe build wilt aanroepen met Adobe PhoneGap Build, klikt u op Extern **** maken.

>[!NOTE]
>
>Als de build om welke reden dan ook mislukt (het rode iOS-pictogram geeft aan dat het platform is mislukt), kunt u de muisaanwijzer boven het pictogram plaatsen om het foutbericht op te halen. U kunt ook op de drievoudige stip &#39;...&#39; klikken onder aan de tegel om rechtstreeks naar https://build.phonegap.com (u moet verifiëren) te navigeren en uw build rechtstreeks te bekijken en te beheren.

### Uw toepassing samenstellen met PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap biedt een opdrachtregelinterface waarmee u uw toepassing lokaal kunt maken.

Compileer de toepassing PhoneGap op uw computer gebruikend de de lijninterface van het Bevel PhoneGap (CLI). AEM maakt een ZIP-bestand dat de inhoud van uw mobiele toepassing, configuraties voor het synchroniseren van inhoud en andere vereiste elementen bevat om de AEM-inhoud in uw toepassing op te nemen. Download het ZIP-bestand en neem het op in uw build.

Om van de interface van de bevellijn van PhoneGap voordeel te halen, zult u opstelling uw lokale milieu moeten omvatten:

1. Platform SDK (iOS, Android, WindowsPhone, ...) en
1. PhoneGap CLI

Je kunt [hier](https://docs.phonegap.com/references/phonegap-cli/)meer lezen.

Nadat u de voorwaarden hebt geïnstalleerd, kunt u het beste een eenvoudige test uitvoeren door een eenvoudige app te maken en deze in de simulator of beter nog op het apparaat uit te voeren. U kunt het dan proberen:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>add —emulate aan het eind van deze lijn als u niet het op uw aangesloten apparaat wilt in werking stellen.

Nadat u hebt gecontroleerd of het bovenstaande werkt, gebruikt u de **PhoneGap Build** Tile om de bron **te** downloaden. Sla het bestand op en decomprimeer het naar uw lokale systeem. Zodra dat gebeurt:

* naar dat opgeslagen bestand (map) navigeren
* run &#39;phonegap run ios&#39; (of android, enz.)

### Additional Resources {#additional-resources}

Zie de volgende bronnen voor meer informatie over de rollen en verantwoordelijkheden van auteurs en ontwikkelaars:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Ontwerpen voor Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
