---
title: AEM-middelen configureren met Brand Portal
seo-title: AEM-middelen configureren met Brand Portal
description: Leer hoe te om activa AEM met het Portaal van het Merk te vormen voor het publiceren van activa en inzamelingen aan het Portaal van het Merk.
seo-description: Leer hoe te om activa AEM met het Portaal van het Merk te vormen voor het publiceren van activa en inzamelingen aan het Portaal van het Merk.
uuid: b95c046e-9988-444c-b50e-ff5ec8cafe14
topic-tags: brand-portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
discoiquuid: dca5a2ac-1fc8-4251-b073-730fd6f49b1c
docset: aem65
translation-type: tm+mt
source-git-commit: 36e9743b8b41d53e735dce4ba13c986ea22e612b

---


# AEM-middelen configureren met Brand Portal {#configure-integration-65}

De Activa van de Manager van de Ervaring van Adobe (AEM) wordt gevormd met het Portaal van het Merk door Adobe I/O, dat een teken IMS voor vergunning van uw Poort van het Merk koopt huurder.

>[!NOTE]
>
>Het vormen van activa AEM met het Portaal van het Merk via Adobe I/O wordt gesteund op AEM 6.5.4.0 en hierboven.
>
>Eerder, werd het Portaal van het Merk gevormd in Klassieke UI via de Gateway van de Oudheid OAuth, die de JWT symbolische uitwisseling gebruikt om een teken van de Toegang te verkrijgen IMS voor vergunning.
>
>De configuratie via Oude OAuth wordt niet meer gesteund vanaf 6 April, 2020, en wordt veranderd in het vormen via Adobe I/O.
>
>Als u een bestaande Poortgebruiker van het Merk met configuratie op de Gateway van de erfenisOAuth bent, wordt het geadviseerd om de bestaande configuraties te schrappen en nieuwe configuratie op Adobe te creëren I/O.
>
>Nochtans, zal de bestaande configuratie blijven werken als u niet de configuraties wijzigt.

Deze hulp beschrijft de volgende twee gebruik-gevallen:
* [Nieuwe configuratie](#configure-new-integration-65): Als u een nieuwe gebruiker van het Portaal van het Merk bent en uw AEM auteursinstantie van Activa met het Portaal van het Merk wilt vormen, kunt u nieuwe configuratie op Adobe I/O tot stand brengen.
* [Configuratie](#upgrade-integration-65)bijwerken: Als u een bestaande gebruiker van het Portaal van het Merk met uw AEM de auteur van Activa die instantie is met het Portaal van het Merk op erfenisOAuth Gateway wordt gevormd, wordt het geadviseerd om de bestaande configuraties te schrappen en nieuwe configuratie op Adobe I/O tot stand te brengen.

De verstrekte informatie is gebaseerd op de veronderstelling dat iedereen die deze Hulp leest vertrouwd is met de volgende technologieën:

* Het installeren, het vormen, en het beheren van de pakketten van de Manager van de Ervaring van Adobe en AEM

* Linux- en Microsoft Windows-besturingssystemen gebruiken

## Voorwaarden {#prerequisites}

U vereist het volgende om activa AEM met het Portaal van het Merk te vormen:

* Een in gebruik zijnde AEM Assets auteursinstantie met het recentste Service Pack.
* URL voor merkportal-huurder.
* Een gebruiker met de voorrechten van de systeembeheerder op de organisatie IMS van de Poorthuurder van het Merk.


[AEM 6.5 downloaden en installeren](#aemquickstart)

[Het nieuwste AEM Service Pack downloaden en installeren](#servicepack)

### AEM 6.5 downloaden en installeren {#aemquickstart}

Aanbevolen wordt om AEM 6.5 te hebben voor het instellen van een AEM-auteur. Als u AEM niet in gebruik hebt, download het van de volgende plaatsen:

* Als u een bestaande klant van AEM bent, download AEM 6.5 van de [vergunningswebsite](http://licensing.adobe.com)van Adobe.

* Als u een partner van Adobe bent, gebruik het Programma [van de Opleiding van de Partner van](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) Adobe om AEM 6.5 aan te vragen.

Nadat u AEM downloadt, voor instructies aan opstelling een AEM auteursinstantie, zie het [opstellen en het handhaven](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Download en installeer het laatste AEM Service Pack {#servicepack}

Voor gedetailleerde instructies zie

* [AEM 6.5 de Nota&#39;s van de Versie van het Service Pack](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html)

**Neem contact op met Support** als u het nieuwste AEM-pakket of Service Pack niet kunt vinden.

## Configuratie maken {#configure-new-integration-65}

Voer de volgende stappen in de vermelde opeenvolging uit als u activa AEM met het Portaal van het Merk voor het eerst vormt:
1. [Verkrijg openbaar certificaat](#public-certificate)
1. [Adobe I/O-integratie maken](#createnewintegration)
1. [IMS-accountconfiguratie maken](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)
1. [Testconfiguratie](#test-integration)

### IMS-configuratie maken {#create-ims-configuration}

De configuratie IMS verklaart uw Poorthuurder van het Merk met de auteursinstantie van de Activa voor authentiek AEM.

De configuratie IMS omvat twee stappen:

* [Verkrijg openbaar certificaat](#public-certificate)
* [IMS-accountconfiguratie maken](#create-ims-account-configuration)

### Verkrijg openbaar certificaat {#public-certificate}

Het openbare certificaat staat u toe om uw profiel op Adobe I/O voor authentiek te verklaren.

1. Meld u aan bij de instantie van de auteur van AEM-elementenStandaard-URL: http:// localhost:4502/aem/start.html
1. Van het paneel van **Hulpmiddelen** ![van Hulpmiddelen](assets/tools.png) , navigeer aan **[!UICONTROL Veiligheid]** >> de Configuraties **[!UICONTROL van]** Adobe IMS.

   ![Adobe IMS-accountconfiguratie-UI](assets/ims-config1.png)

1. De pagina van de Configuraties van Adobe IMS opent.

   Klik **[!UICONTROL creëren]**.

   Dit zal u aan de pagina van de Configuratie van de Rekening van **[!UICONTROL Adobe IMS Technische]** nemen.

1. Standaard wordt het tabblad **Certificaat** geopend.

   In de Oplossing **van de** Wolk, het uitgezochte Portaal **[!UICONTROL van het Merk van]** Adobe.

1. Teken checkbox **[!UICONTROL creeer nieuw certificaat]** en specificeer een **alias** voor het certificaat. De alias dient als naam van de dialoog.

1. Klik op Certificaat **[!UICONTROL maken]**. Er verschijnt een dialoogvenster. Klik **[!UICONTROL O.K.]** om het openbare certificaat te produceren.

   ![Certificaat maken](assets/ims-config2.png)

1. Klik **[!UICONTROL Download Openbare Sleutel]** en sla het *AEM-Adobe-IMS.crt* - certificaatdossier op uw machine op. Het certificaatdossier wordt gebruikt om de integratie [van Adobe te](#createnewintegration)creëren I/O.

   ![Downloadcertificaat](assets/ims-config3.png)

1. Click **[!UICONTROL Next]**.

   In het lusje van de **Rekening** , creeert u de Rekening van Adobe IMS maar voor dat zult u de integratiedetails nodig hebben. Houd deze pagina open voor nu.

   Open een nieuw lusje en [creeer de integratie](#createnewintegration) van Adobe I/O om de integratiedetails voor de configuraties van de Rekening te krijgen IMS.

### Adobe I/O-integratie maken {#createnewintegration}

De integratie van Adobe I/O produceert API Sleutel, de Geheim van de Cliënt, en de lading (JWT) die in vestiging de configuraties van de Rekening IMS wordt vereist.

1. Login aan de Console van Adobe I/O met de voorrechten van de systeembeheerder op de organisatie IMS van de Poorthuurder van het Merk.

   Standaard-URL: [https://console.adobe.io/](https://console.adobe.io/)

1. Klik **[!UICONTROL creëren Integratie]**.

1. Selecteer **[!UICONTROL Toegang tot API]**, en de klik **[!UICONTROL gaat]** verder.

   ![Nieuwe integratie maken](assets/create-new-integration1.png)

1. Creeer een nieuwe integratiepagina opent.

   Selecteer uw organisatie van de drop-down lijst.

   In de Wolk **[!UICONTROL van de]** Ervaring, selecteer het Portaal **[!UICONTROL van het Merk]** AEM en klik **[!UICONTROL verdergaan]**.

   Als de Poortoptie van het Merk voor u gehandicapt is, zorg ervoor dat u correcte organisatie van de drop-down doos boven de optie van de Diensten **[!UICONTROL van]** Adobe hebt geselecteerd. Als u uw organisatie niet kent, contacteer uw beheerder.

   ![Integratie maken](assets/create-new-integration2.png)

1. Specificeer een naam en een beschrijving voor de integratie. Klik **[!UICONTROL selecteer een Dossier van uw computer]** en upload het `AEM-Adobe-IMS.crt` dossier dat in wordt gedownload [verkrijg openbare certificaten](#public-certificate) sectie.

1. Selecteer het profiel van uw organisatie.

   Of, selecteer het Portaal **[!UICONTROL van het Merk van de]** Activa van het standaardprofiel en de klik **[!UICONTROL leidt tot Integratie]**. De integratie wordt gecreeerd.

1. Klik op **[!UICONTROL Doorgaan naar integratiedetails]** om de integratiegegevens weer te geven.

   Kopieer de **[!UICONTROL API Sleutel]**

   Klik **[!UICONTROL Win de Geheime]** Cliënt terug en kopieer de sleutel van de Geheime cliënt.

   ![API Sleutel, het Geheim van de Cliënt, en de nuttige ladingsinformatie van een integratie](assets/create-new-integration3.png)

1. Navigeer aan **[!UICONTROL lusje JWT]** , en kopieer de nuttige lading **** JWT.

   De API Sleutel, de Geheime sleutel van de Cliënt, en JWT de nuttige ladingsinformatie zullen worden gebruikt om IMS rekeningsconfiguratie tot stand te brengen.

### IMS-accountconfiguratie maken {#create-ims-account-configuration}

Zorg ervoor dat u de volgende stappen hebt uitgevoerd:

* [Verkrijg openbaar certificaat](#public-certificate)
* [Adobe I/O-integratie maken](#createnewintegration)

**Stappen om IMS rekeningsconfiguratie tot stand te brengen:**

1. Open de pagina van de Configuratie IMS, **[!UICONTROL Rekeningen]** tabel. U hield de pagina open aan het eind van sectie, [verkrijgt openbaar certificaat](#public-certificate).

1. Geef een **[!UICONTROL titel]** op voor de IMS-account.

   In de Server **[!UICONTROL van de]** Vergunning, ga URL in: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Plak de API Sleutel, het Geheim van de Cliënt, en de nuttige lading JWT die u aan het eind van [Create Adobe I/O integratie](#createnewintegration)hebt gekopieerd.

   Klik **[!UICONTROL creëren]**.

   De integratie wordt gecreeerd.

   ![IMS-accountconfiguratie](assets/create-new-integration6.png)

   >[!CAUTION]
   >
   >Creeer slechts één configuratie IMS. Creeer geen veelvoudige configuraties IMS.

1. Selecteer de IMS-configuratie en klik op **[!UICONTROL Controleren op de status]**. Er verschijnt een dialoogvenster.

   Klik **[!UICONTROL Controle]**. Bij succesvolle verbinding, verschijnt het met succes *teruggewonnen* Symbolische bericht.

   ![](assets/create-new-integration5.png)

   <br/> <br/>

### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de configuratie van de de clouddienst van het Merk Portal te creëren:

1. Meld u aan bij de instantie van AEM Assets-auteur

   Standaard-URL: http:// localhost:4502/aem/start.html
1. Van het paneel van **Hulpmiddelen** ![van Hulpmiddelen](assets/tools.png) , navigeer aan de Diensten van de **[!UICONTROL Wolk > AEM het Portaal]** van het Merk.

   De pagina van de Poortconfiguraties van het merk opent.

1. Klik **[!UICONTROL creëren]**.

1. Specificeer een **[!UICONTROL Titel]** voor de configuratie.

   Selecteer de Configuratie IMS die u in de stap hebt gecreeerd, [creeer de configuratie](#create-ims-account-configuration)van de Rekening IMS.

   In de **[!UICONTROL Dienst URL]**, ga uw Portaalhuurder URL van het Merk in.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Opslaan en sluiten]**. De wolkenconfiguratie wordt gecreeerd. De auteur van uw AEM-bedrijfsmiddelen wordt nu geïntegreerd in de Poort-gebruiker van het merk.

### Testconfiguratie {#test-integration}

1. Meld u aan bij de instantie van AEM Assets-auteur

   Standaard-URL: http:// localhost:4502/aem/start.html

1. Van het paneel van **Hulpmiddelen** ![van Hulpmiddelen](assets/tools.png) , navigeer aan **[!UICONTROL Plaatsing > Replicatie]**.

   ![](assets/test-integration1.png)

1. De pagina van de replicatie opent.

   Klik **[!UICONTROL Agenten op auteur]**.

   ![](assets/test-integration2.png)

1. Vier replicatieagenten worden gecreeerd voor elke huurder.

   Bepaal de plaats van de replicatieagenten van uw Poorthuurder van het Merk.

   Klik de replicatieagent URL.

   ![](assets/test-integration3.png)


   >[!NOTE]
   >
   >De replicatieagenten werken parallel en delen de baandistributie gelijk, daardoor verhogend de het publiceren snelheid met vier keer de originele snelheid. Nadat de wolkendienst wordt gevormd, wordt de extra configuratie niet vereist om de replicatieagenten toe te laten die door gebrek worden geactiveerd om het parallelle publiceren van veelvoudige activa toe te laten.

   >[!NOTE]
   >
   >Vermijd onbruikbaar makend om het even welke replicatieagenten, aangezien het de replicatie van sommige activa kan veroorzaken om te ontbreken.


1. Om de verbinding tussen auteur van de Activa AEM en het Portaal van het Merk te verifiëren, klik de Verbinding **[!UICONTROL van de]** Test.

   ![](assets/test-integration4.png)

1. Bekijk de bodem van de testresultaten om te verifiëren dat de replicatie slaagde.

   ![](assets/test-integration5.png)

   >[!NOTE]
   >
   >De replicatieagenten werken parallel en delen de baandistributie gelijk, daardoor verhogend de het publiceren snelheid met vier keer de originele snelheid. Nadat de wolkendienst wordt gevormd, wordt de extra configuratie niet vereist om de replicatieagenten toe te laten die door gebrek worden geactiveerd om het parallelle publiceren van veelvoudige activa toe te laten.

1. Verifieer de testresultaten op alle vier replicatieagenten één voor één.


   >[!NOTE]
   >
   >Vermijd onbruikbaar makend om het even welke replicatieagenten, aangezien het de replicatie van sommige activa kan veroorzaken om te ontbreken.

Het Portaal van het merk wordt met succes gevormd met uw AEM de auteursinstantie van Activa. U kunt nu:

* [Publiceer activa van activa AEM aan het Portaal van het Merk](../assets/brand-portal-publish-assets.md)
* [Mappen publiceren van AEM-bedrijfsmiddelen naar Brand Portal](../assets/brand-portal-publish-folder.md)
* [Verzamelingen van AEM-bedrijfsmiddelen naar Brand Portal publiceren](../assets/brand-portal-publish-collection.md)
* [Bedrijfsmiddelen configureren](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) waarmee de gebruikers van het Merkortaal kunnen bijdragen aan en bedrijfsmiddelen kunnen publiceren voor AEM-bedrijfsmiddelen.

## Upgradeconfiguratie {#upgrade-integration-65}

Voer de volgende stappen in de vermelde opeenvolging uit om bestaande configuraties te bevorderen:
1. [Controleren of er taken worden uitgevoerd](#verify-jobs)
1. [Bestaande configuraties verwijderen](#delete-existing-configuration)
1. [Configuratie maken](#configure-new-integration-65)

### Controleren of er taken worden uitgevoerd {#verify-jobs}

Zorg ervoor dat geen het publiceren baan op uw AEM de auteursinstantie van Activa loopt alvorens u om het even welke wijzigingen aanbrengt. Voor dat, kunt u alle vier replicatieagenten verifiëren en ervoor zorgen dat de rij ideaal/leeg is.

1. Meld u aan bij de instantie van AEM Assets-auteur

   Standaard-URL: http:// localhost:4502/aem/start.html

1. Van het paneel van **Hulpmiddelen** ![van Hulpmiddelen](assets/tools.png) , navigeer aan **[!UICONTROL Plaatsing > Replicatie]**.

1. De pagina van de replicatie opent.

   Klik **[!UICONTROL Agenten op auteur]**.

   ![](assets/test-integration2.png)

1. Bepaal de plaats van de replicatieagenten van uw Poorthuurder van het Merk.

   Zorg ervoor dat de **Rij voor alle replicatieagenten onactief** is, is geen het publiceren baan actief.

   ![](assets/test-integration3.png)

### Bestaande configuraties verwijderen {#delete-existing-configuration}

U moet de volgende controle-lijst in werking stellen terwijl het schrappen van de bestaande configuraties.
* Verwijder alle vier replicatieagents
* Cloudservice verwijderen
* MAC-gebruiker verwijderen

1. Login aan uw AEM de auteur van Activa instantie en open CRX Lite als beheerder.

   Standaard-URL: http:// localhost:4502/crx/de/index.jsp

1. Navigeer aan `/etc/replications/agents.author` en schrap alle vier replicatieagenten van uw Poorthuurder van het Merk.

   ![](assets/delete-replication-agent.png)

1. Navigeer aan `/etc/cloudservices/mediaportal` en schrap de configuratie **van de Dienst van de** Wolk.

   ![](assets/delete-cloud-service.png)

1. Navigeer aan `/home/users/mac` en schrap de gebruiker **van** MAC van uw Poorthuurder van het Merk.

   ![](assets/delete-mac-user.png)


U kunt configuratie [op uw AEM 6.5 auteursinstantie op Adobe I/O nu](#configure-new-integration-65) tot stand brengen.



<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
   -->

Nadat de replicatie slaagt, kunt u activa, omslagen, en inzamelingen aan het Portaal van het Merk publiceren. Zie voor meer informatie:

* [Publiceer activa aan het Portaal van het Merk](/help/assets/brand-portal-publish-assets.md)
* [Mappen publiceren naar Brand Portal](/help/assets/brand-portal-publish-folder.md)
* [Collecties naar Brand-portal publiceren](/help/assets/brand-portal-publish-collection.md)
