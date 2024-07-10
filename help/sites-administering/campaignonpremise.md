---
title: AEM 6.5 integreren met Adobe Campaign Classic
description: Leer hoe u AEM 6.5 kunt integreren met Adobe Campaign Classic
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: a7281ca0-461f-4762-a631-6bb539596200
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 6fb844ea428c15adab71503dde6138e46eabf0a3
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 0%

---


# AEM 6.5 integreren met Adobe Campaign Classic {#integrating-campaign-classic}

Door AEM te integreren met Adobe Campaign Classic (ACC), kunt u e-maillevering, inhoud en formulieren direct in AEM beheren. De stappen van de configuratie in zowel Adobe Campaign Classic als AEM zijn nodig om bidirectionele communicatie tussen oplossingen toe te laten.

Dankzij deze integratie kunnen AEM en Adobe Campaign Classic onafhankelijk worden gebruikt. Marketers kunnen campagnes maken en doelgericht gebruik maken in Adobe Campaign, terwijl makers van inhoud tegelijkertijd in AEM aan het ontwerpen van inhoud kunnen werken. Met behulp van de integratie kunnen de inhoud en het ontwerp van de in AEM gemaakte campagne door Adobe Campaign worden aangesproken en geleverd.

>[!INFO]
>
>In dit document wordt beschreven hoe u Adobe Campaign Classic kunt integreren met AEM 6.5. Zie het document voor andere Campagne-integratie [AEM 6.5 integreren met Adobe Campaign.](campaign.md)

## Integratiestappen {#integration-steps}

De integratie tussen AEM en Campagne vereist verscheidene stappen in beide oplossingen.

1. [Installeer het AEM integratiepakket in de campagne.](#install-package)
1. [Een operator maken voor AEM in campagne](#create-operator)
1. [Integratie van campagnes configureren in AEM](#campaign-integration)
1. [De AEM ExternalAlizer configureren](#externalizer)
1. [De externe gebruiker van de campagne configureren in AEM](#configure-user)
1. [De externe AEM-account configureren in Campagne](#acc-setup)

Dit document leidt u door elk van deze stappen in detail.

## Vereisten {#prerequisites}

* Toegang tot Adobe Campaign Classic voor beheerders
   * Om de integratie uit te voeren, hebt u een werkende instantie van Adobe Campaign Classic, met inbegrip van een gevormd gegevensbestand nodig.
   * Als u meer informatie nodig hebt over het instellen en configureren van Adobe Campaign Classic, raadpleegt u de [Adobe Campaign Classic-documentatie;](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html) met name de gids Installatie en Configuratie.
* Toegang tot AEM beheerder

## Het AEM integratiepakket in de campagne installeren {#install-package}

De **AEM integratie** -pakket in Adobe Campaign bevat diverse standaardconfiguraties die nodig zijn om verbinding te maken met AEM.

1. Meld u als beheerder aan bij de Adobe Campaign-instantie met de clientconsole.

1. Selecteren **Gereedschappen** > **Geavanceerd** > **Pakket importeren...**.

   ![Pakket importeren](assets/import-package.png)

1. Klikken **Een standaardpakket installeren** en klik vervolgens op **Volgende**.

1. Controleer de **AEM integratie** pakket.

   ![Een standaardpakket installeren](assets/select-package.png)

1. Klikken **Volgende** en vervolgens **Start** om de installatie te starten.

   ![Voortgang van installatie](assets/installation.png)

1. Klikken **Sluiten** als de installatie is voltooid.

Het integratiepakket is nu geïnstalleerd.

## De operator voor AEM in campagne maken {#create-operator}

Het integratiepakket maakt automatisch de `aemserver` operator die AEM gebruikt om verbinding te maken met Adobe Campaign. Definieer een beveiligingszone voor deze operator en stel het wachtwoord ervan in.

1. Meld u met de clientconsole aan bij Adobe Campaign als beheerder.

1. Selecteren **Gereedschappen** > **Verkenner** in de menubalk.

1. Ga in de verkenner naar de **Administratie** > **Toegangsbeheer** > **Operatoren** knooppunt.

1. Selecteer de `aemserver` operator.

1. Op de **Bewerken** selecteert u de **Toegangsrechten** subtab en klik vervolgens op de knop **Bewerk de toegangsparameters...** koppeling.

   ![Beveiligingszone instellen](assets/access-rights.png)

1. Selecteer de aangewezen veiligheidsstreek en bepaal zonodig het vertrouwde op IP masker.

   >[!CAUTION]
   >
   >De te configureren beveiligingszone is **Netwerk van het privé bedrijf (VPN+LAN)**.

1. Klikken **Opslaan**.

1. Afmelden bij de Adobe Campaign-client.

1. Navigeer in het bestandssysteem van de Adobe Campaign-server naar de installatielocatie voor Campagne en bewerk de `serverConf.xml` als beheerder. Dit bestand bevindt zich doorgaans onder:
   * `C:\Program Files\Adobe\Adobe Campaign Classic v7\conf` in Windows.
   * `/usr/local/neolane/nl6/conf/eng` in Linux.

1. Zoeken naar `securityZone` en ervoor zorgen dat de volgende parameters worden ingesteld voor de beveiligingszone van de AEM.

   * `allowHTTP="true"`
   * `sessionTokenOnly="true"`
   * `allowUserPassword="true"`.

1. Sla het bestand op.

1. Zorg ervoor dat de beveiligingszone niet wordt overschreven door de desbetreffende instelling in het dialoogvenster `config-<server name>.xml` bestand.

   * Als het configuratiebestand een afzonderlijke instelling voor de beveiligingszone bevat, wijzigt u de instelling `allowUserPassword` kenmerk naar `true`.

1. Als u de Adobe Campaign Classic server poort wilt wijzigen, vervangt u `8080` met de gewenste poort.

   >[!CAUTION]
   >
   >Door gebrek, is er geen veiligheidsstreek die voor de exploitant wordt gevormd. Als u AEM verbinding wilt maken met Adobe Campaign, moet u een zone selecteren zoals in de vorige stappen wordt beschreven.
   >
   >Adobe beveelt ten zeerste aan een veiligheidszone in te stellen die is gewijd aan AEM om veiligheidsproblemen te voorkomen. Voor meer informatie over dit onderwerp raadpleegt u de [Adobe Campaign Classic-documentatie.](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/security-zones.html)

1. Ga in de Campagne-client terug naar de `aemserver` en selecteert u de **Algemeen** tab.

1. Klik op de knop **Wachtwoord opnieuw instellen...** koppeling.

1. Geef een wachtwoord op en bewaar dit op een veilige locatie voor toekomstig gebruik.

1. Klikken **OK** om het wachtwoord voor de `aemserver` operator.

## Campagne-integratie configureren in AEM {#campaign-integration}

AEM [de operator die u al hebt ingesteld in Campagne](#create-operator) om te communiceren met Campagne

1. Meld u als beheerder aan bij de AEM ontwerpinstantie.

1. Selecteer vanuit de globale spoorstaaf voor de navigatie **Gereedschappen** > **Cloud Servicen** > **Oudere Cloud Servicen** > **Adobe Campaign** en klik vervolgens op **Nu configureren**.

   ![Adobe Campaign configureren](assets/configure-campaign-service.png)

1. In de dialoog, creeer een de dienstconfiguratie van de Campagne door een **Titel** en klik op **Maken**.

   ![Het dialoogvenster Campagne configureren](assets/configure-campaign-dialog.png)

1. Er wordt een nieuw venster en dialoogvenster geopend om de configuratie te bewerken. Verstrek de noodzakelijke informatie.

   * **Gebruikersnaam** - Dit is [de Adobe Campaign AEM Integration package operator gemaakt in de vorige stap.](#create-operator) Standaard is dit `aemserver`.
   * **Wachtwoord** - Dit is het wachtwoord voor [de Adobe Campaign AEM Integration package operator gemaakt in de vorige stap.](#create-operator)
   * **API-eindpunt** - Dit is de URL van de Adobe Campaign-instantie.

   ![Adobe Campaign configureren in AEM](assets/configure-campaign.png)

1. Selecteren **Verbinding maken met Adobe Campaign** om de verbinding te verifiëren en klik vervolgens op **OK**.

AEM kan nu communiceren met Adobe Campaign.

>[!NOTE]
>
>Zorg ervoor dat uw Adobe Campaign-server via internet bereikbaar is. AEM heeft geen toegang tot particuliere netwerken.

## Replicatie configureren naar AEM Publish-instantie {#replication}

Campagne-inhoud wordt gemaakt door de auteurs van de inhoud op de AEM ontwerpinstantie. Dit exemplaar is typisch slechts intern beschikbaar bij uw organisatie. Als u inhoud, zoals afbeeldingen en elementen, toegankelijk wilt maken voor de ontvangers van uw campagne, moet u die inhoud publiceren.

De replicatieagent is verantwoordelijk voor het publiceren van uw inhoud van de AEM auteurinstantie aan de publicatieinstantie en moet opstelling voor de integratie zijn behoorlijk te werken. Deze stap is ook nodig om bepaalde configuraties van ontwerpinstanties te repliceren in de publicatieinstantie.

Om replicatie van uw AEM auteursinstantie aan te vormen publiceer instantie:

1. Meld u als beheerder aan bij de AEM ontwerpinstantie.

1. Selecteer vanuit de globale spoorstaaf voor de navigatie **Gereedschappen** > **Implementatie** > **Replicatie** > **Medewerkers op auteur** en klik vervolgens op **Standaardagent (publiceren)**.

   ![Replicatieagent configureren](assets/acc-replication-config.png)

1. Klikken **Bewerken** Selecteer vervolgens de **Vervoer** tab.

1. Vorm **URI** veld door de standaardwaarde te vervangen `localhost` waarde met het IP adres van de AEM het publiceren instantie.

   ![Tabblad Vervoer](assets/acc-transport-tab.png)

1. Klikken **OK** om de veranderingen in de agentenmontages te bewaren.

U hebt replicatie aan de AEM gevormd publiceer instantie zodat kunnen uw campagneontvangers tot uw inhoud toegang hebben.

>[!NOTE]
>
>Als u niet replicatie URL wilt gebruiken maar in plaats daarvan openbaar-onder ogen ziet URL gebruiken, kunt u openbare URL in de volgende configuratie plaatsen die via OSGi plaatst
>
>Selecteer vanuit de globale spoorstaaf voor de navigatie **Gereedschappen** > **Bewerkingen** > **Webconsole** > **OSGi-configuratie** en zoek naar **AEM Campagne-integratie - Configuratie**. De configuratie bewerken en het veld wijzigen **Openbare URL** (`com.day.cq.mcm.campaign.impl.IntegrationConfigImpl#aem.mcm.campaign.publicUrl`).

## De AEM ExternalAlizer configureren {#externalizer}

[De externalizer](/help/sites-developing/externalizer.md) is de dienst OSGi in AEM die een middelweg in externe en absolute URL omzet, die voor AEM noodzakelijk is om inhoud te dienen die de Campagne kan gebruiken. Vorm het zodat de integratie van de Campagne werkt.

1. Meld u als beheerder aan bij de AEM-ontwerpinstantie.
1. Selecteer vanuit de globale spoorstaaf voor de navigatie **Gereedschappen** > **Bewerkingen** > **Webconsole** > **OSGi-configuratie** en zoek naar **Day CQ-koppeling ExternalAlizer**.
1. Standaard wordt de laatste vermelding in het dialoogvenster **Domeinen** is bestemd voor de publicatie-instantie. De URL wijzigen vanuit de standaardinstelling `http://localhost:4503` naar uw openbaar beschikbare publicatie-instantie.

   ![Het vormen van Externalzer](assets/acc-externalizer-config.png)

1. Klikken **Opslaan**.

U hebt de Externalzer geconfigureerd en Adobe Campaign heeft nu toegang tot uw inhoud.

>[!NOTE]
>
De publicatie-instantie moet bereikbaar zijn vanaf de Adobe Campaign-server. Als deze naar `localhost:4503` of een andere server die Adobe Campaign niet kan bereiken, worden afbeeldingen van AEM niet weergegeven in de Adobe Campaign-console.

## Vorm de campagne-verre Gebruiker in AEM {#configure-user}

Als campagne moet communiceren met AEM, moet u een wachtwoord instellen voor de `campaign-remote` gebruiker in AEM.

1. Meld u aan bij AEM als beheerder.
1. Klik in de hoofdnavigatieconsole op **Gereedschappen** in het linkerspoor.
1. Klik vervolgens op **Beveiliging** > **Gebruikers** om de gebruikersbeheerconsole te openen.
1. Zoek de `campaign-remote` gebruiker.
1. Selecteer de `campaign-remote` gebruiker en klik op **Eigenschappen** om de gebruiker te bewerken.
1. In de **Gebruikersinstellingen bewerken** venster, klikt u op **Wachtwoord wijzigen**.
1. Geef de gebruiker een nieuw wachtwoord op en noteer het wachtwoord op een veilige locatie voor toekomstig gebruik.
1. Klikken **Opslaan** om de wachtwoordwijziging op te slaan.
1. Klikken **Opslaan en sluiten** om de wijzigingen in de `campaign-remote` gebruiker.

## De externe AEM-account configureren in de campagne {#acc-setup}

Wanneer [installeren **AEM integratie** pakket in campagne,](#install-package) er wordt een externe account voor AEM gemaakt. Door deze externe account te configureren, kan Adobe Campaign verbinding maken met AEM, waardoor tweerichtingscommunicatie tussen de oplossingen mogelijk is.

1. Meld u met de clientconsole aan bij Adobe Campaign als beheerder.

1. Selecteren **Gereedschappen** > **Verkenner** in de menubalk.

1. Ga in de verkenner naar de **Administratie** > **Platform** > **Externe rekeningen** knooppunt.

   ![Externe rekeningen](assets/external-accounts.png)

1. Zoek de externe AEM. Standaard heeft het de volgende waarden:

   * **Type** - `AEM`
   * **Label** - `AEM Instance`
   * **Interne naam** - `aemInstance`

1. Op de **Algemeen** van dit account, voert u de gebruikersgegevens in die u in het [Wachtwoord voor externe gebruiker voor campagne instellen](#set-campaign-remote-password) stap.

   * **Server** - Het AEM serveradres van de auteur
      * De AEM auteurserver moet van de de serverinstantie van Adobe Campaign Classic bereikbaar zijn.
      * Controleer of het serveradres **niet** eindigt in een schuine streep.
   * **Account** - Standaard is dit de `campaign-remote` gebruiker die u instelt in AEM in het dialoogvenster [Wachtwoord voor externe gebruiker voor campagne instellen](#set-campaign-remote-password) stap.
   * **Wachtwoord** - Dit wachtwoord is hetzelfde als het `campaign-remote` gebruiker die u instelt in AEM in het dialoogvenster [Wachtwoord voor externe gebruiker voor campagne instellen](#set-campaign-remote-password) stap.

1. Selecteer de **Ingeschakeld** selectievakje.

1. Klikken **Opslaan**.

Adobe Campaign kan nu communiceren met AEM.

## Volgende stappen {#next-steps}

Met zowel Adobe Campaign Classic als AEM geconfigureerd is de integratie nu voltooid.

Je kunt nu leren hoe je een nieuwsbrief kunt maken in Adobe Experience Manager door door te gaan met [dit document.](/help/sites-authoring/campaign.md)
