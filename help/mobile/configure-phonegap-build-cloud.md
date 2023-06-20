---
title: Adobe PhoneGap Build-Cloud Service configureren
seo-title: Configure your Adobe PhoneGap Build Cloud Service
description: Volg deze pagina om de cloudservices te configureren en uw toepassing samen te stellen met PhoneGap-build.
seo-description: Follow this page for configuring the cloud services and building your application with PhoneGap build.
uuid: 59aa99c3-1425-4cc5-9839-a57a6a545d45
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 3c84f4ec-d89b-4ad4-802e-ee3e2d49d916
exl-id: d91a00d1-12fa-4c84-a426-49413f61c126
source-git-commit: 17d13e9b201629d9d1519fde4740cf651fe89d2c
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# Adobe PhoneGap Build-Cloud Service configureren {#configure-your-adobe-phonegap-build-cloud-service}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

De **PhoneGap Build-tegel** op het toepassingsdashboard biedt de mogelijkheid om uw mobiele PhoneGap-toepassing te maken en distribueren via de Adobe PhoneGap Build Service.

Alle ondersteunde platforms die zijn gedefinieerd in het dialoogvenster **App beheren** de tegel wordt met PhoneGap Build gebouwd wanneer u een externe build met de **PhoneGap Build** Tegel.

U kunt een externe build naar `https://build.phonegap.com` of download de bron om lokaal samen te stellen met PhoneGap CLI op `https://docs.phonegap.com/references/phonegap-cli/`.

![PhoneGap Build-tegel](assets/chlimage_1-60.png)

## De Cloud Service configureren {#configuring-the-cloud-service}

Om uit PhoneGap Build voordeel te halen moet u de AEM Cloud Service van de PhoneGap Build met uw de rekeningsinformatie van de PhoneGap Build vormen.

Als u momenteel geen account hebt, navigeert u naar `https://build.phonegap.com` en meld u aan! Als u een Adobe Creative Cloud-lidmaatschap hebt, hebt u mogelijk ondersteuning voor maximaal 25 persoonlijke apps (apps zonder open bron).

Als u hebt gecontroleerd of uw PhoneGap Build-account actief is, navigeert u naar de AEM Cloud Management Console, met name de [PhoneGap Build Cloud Service](http://localhost:4502/etc/cloudservices/phonegap-build.html) (http://localhost:4502/etc/cloudservices/phonegap-build.html).

Gebruik de **Cloud Services beheren** tegel om een nieuwe configuratie van de wolkendienst te vormen.

### De tegel Cloud Services beheren gebruiken {#using-manage-cloud-services-tile}

Voordat u begint met het maken van uw app met **PhoneGap Build** blok, moet u uw wolkendiensten vormen, gebruikend **Cloud Services beheren** tegel van het AEM Mobile-dashboard.

Volg onderstaande stappen om cloudservices voor uw app te configureren:

1. Klik in de rechterbovenhoek van het dialoogvenster **Cloud Services beheren** tegel.

   ![chlimage_1-61](assets/chlimage_1-61.png)

1. Kies **PhoneGap Build** van de **Cloud Service toevoegen of bewerken** scherm.

   Klik op **Next**.

   ![chlimage_1-62](assets/chlimage_1-62.png)

1. Voer uw gegevens in om een nieuwe cloudconfiguratie te maken.

   Klik op **Verzenden**. Deze geconfigureerde cloudconfiguratie wordt nu weergegeven in het dialoogvenster **Cloud Services beheren** tegel.

   ![chlimage_1-63](assets/chlimage_1-63.png)

### Uw toepassing samenstellen met PhoneGap Build {#building-your-application-with-phonegap-build}

Nadat u de cloudservices hebt geconfigureerd, kunt u uw toepassing samenstellen met **PhoneGap Build** tegel. Klik in de rechterbovenhoek om een optie te kiezen in het menu **Extern maken** of **Bron downloaden** opties.

![chlimage_1-64](assets/chlimage_1-64.png)

Als u een externe build wilt aanroepen met Adobe PhoneGap Build, klikt u op **Extern maken**.

>[!NOTE]
>
>Als de build om welke reden dan ook mislukt (het rode iOS-pictogram geeft hieronder aan dat het platform is mislukt), kunt u de muisaanwijzer boven het pictogram plaatsen om het foutbericht op te halen. U kunt ook op de drievoudige stip &#39;...&#39; klikken onder aan de tegel om rechtstreeks naar `https://build.phonegap.com` (u moet verifiëren) en bekijk en beheer uw bouwstijl direct.

### Uw toepassing samenstellen met PhoneGap CLI {#building-your-application-with-phonegap-cli}

PhoneGap biedt een opdrachtregelinterface waarmee u uw toepassing lokaal kunt maken.

Compileer de toepassing PhoneGap op uw computer gebruikend de de lijninterface van het Bevel PhoneGap (CLI). Als u de AEM-inhoud in uw toepassing wilt opnemen, AEM maakt u een ZIP-bestand dat de inhoud van uw mobiele toepassing, configuraties voor inhoudssynchronisatie en andere vereiste elementen bevat. Download het ZIP-bestand en neem het op in uw build.

Om van de interface van de bevellijn van PhoneGap voordeel te halen, zult u opstelling uw lokale milieu moeten omvatten:

1. Platform SDK (iOS, Android, WindowsPhone, ...) en
1. PhoneGap CLI

Meer informatie hier vindt u op `https://docs.phonegap.com/references/phonegap-cli/`.

Nadat u de voorwaarden hebt geïnstalleerd, kunt u het beste een eenvoudige test uitvoeren door een eenvoudige app te maken en deze in de simulator of beter nog op het apparaat uit te voeren. U kunt het dan proberen:

```xml
phonegap create myApp
cd myApp
phonegap run ios (or android, ...)
```

>[!NOTE]
>
>add —emulate aan het eind van deze lijn als u niet het op uw aangesloten apparaat wilt in werking stellen.

Nadat u hebt gecontroleerd of het bovenstaande werkt, kunt u de opdracht **PhoneGap Build** Naast elkaar **Bron downloaden**. Sla het bestand op en decomprimeer het naar uw lokale systeem. Zodra dat gebeurt:

* naar dat opgeslagen bestand (map) navigeren
* run &#39;phonegap run ios&#39; (of android, enz.)

### Aanvullende bronnen {#additional-resources}

Zie de volgende bronnen voor meer informatie over de rollen en verantwoordelijkheden van auteurs en ontwikkelaars:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Ontwerpen voor Adobe PhoneGap Enterprise in AEM](/help/mobile/phonegap.md)
