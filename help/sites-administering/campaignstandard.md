---
title: Integreren met Adobe Campaign Standard
seo-title: Integreren met Adobe Campaign Standard
description: Integreren met Adobe Campaign Standard.
seo-description: Integreren met Adobe Campaign Standard.
uuid: ef31339e-d925-499c-b8fb-c00ad01e38ad
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 5c0fec99-7b1e-45d6-a115-e498d288e9e1
translation-type: tm+mt
source-git-commit: f951c195c581f770dcc87fdf4a89d40ee6dd9ec0
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 0%

---


# Integreren met Adobe Campaign Standard{#integrating-with-adobe-campaign-standard}

>[!NOTE]
>
>In deze documentatie wordt beschreven hoe u AEM kunt integreren met Adobe Campaign Standard, de op abonnementen gebaseerde oplossing. Als u Adobe Campaign 6.1 gebruikt, zie [Integratie met Adobe Campaign 6.1](/help/sites-administering/campaignonpremise.md) voor die instructies.

Met Adobe Campaign kunt u inhoud en formulieren voor e-maillevering rechtstreeks in Adobe Experience Manager beheren.

Om beide oplossingen samen te gebruiken tezelfdertijd, moet u hen eerst vormen om met elkaar te verbinden. Dit omvat configuratiestappen in zowel Adobe Campaign als Adobe Experience Manager. Deze stappen worden in dit document uitgebreid beschreven.

Als u met Adobe Campaign werkt in AEM, kunt u e-mail en formulieren verzenden via Adobe Campaign. Dit wordt beschreven onder [Werken met Adobe Campaign](/help/sites-authoring/campaign.md).

Bovendien kunnen de volgende onderwerpen van belang zijn wanneer het integreren van AEM met [Adobe Campaign](https://docs.campaign.adobe.com/doc/standard/en/home.html):

* [Aanbevolen procedures voor e-mailsjablonen](/help/sites-administering/best-practices-for-email-templates.md)
* [Problemen met de integratie met Adobe Campaign oplossen](/help/sites-administering/troubleshooting-campaignintegration.md)

Als u uw integratie met Adobe Campaign uitbreidt, wilt u wellicht de volgende pagina&#39;s zien:

* [Aangepaste extensies maken](/help/sites-developing/extending-campaign-extensions.md)
* [Aangepaste formuliertoewijzingen maken](/help/sites-developing/extending-campaign-form-mapping.md)

## Adobe Campaign {#configuring-adobe-campaign} configureren

Bij het configureren van Adobe Campaign gaat het om het volgende:

1. Het vormen van **aemserver** gebruiker.
1. Een speciale externe account maken.
1. De optie AEMResourceTypeFilter controleren.
1. Een toegewezen leveringssjabloon maken.

>[!NOTE]
>
>Als u deze bewerkingen wilt uitvoeren, moet u de rol **administration** in Adobe Campaign hebben.

### Vereisten {#prerequisites}

Zorg ervoor dat u de volgende elementen vooraf hebt:

* [Een AEM-ontwerpinstantie](/help/sites-deploying/deploy.md#getting-started)
* [Een AEM-publicatie-instantie](/help/sites-deploying/deploy.md#author-and-publish-installs)
* [Een Adobe Campaign-instantie](https://docs.adobe.com/content/docs/en/campaign/ACS.html)

>[!CAUTION]
>
>Bewerkingen die worden beschreven in de secties [Adobe Campaign configureren](#configuring-adobe-campaign) en [Adobe Experience Manager configureren](#configuring-adobe-experience-manager) zijn nodig om de integratiefuncties tussen AEM en Adobe Campaign correct te laten werken.

### De servergebruiker {#configuring-the-aemserver-user} configureren

De **aemserver** gebruiker moet in Adobe Campaign worden gevormd. De **aemserver** is een technische gebruiker die zal worden gebruikt om de AEM server aan Adobe Campaign aan te sluiten.

Ga naar **Beheer** > **Gebruikers &amp; beveiliging** > **Gebruikers** en selecteer de **mailserver** gebruiker. Klik erop om de gebruikersinstellingen te openen.

* U moet een wachtwoord instellen voor deze gebruiker. Dit kan niet via UI worden gedaan. Deze configuratie moet in REST door een technische beheerder worden gedaan.
* U kunt specifieke rollen aan deze gebruiker, zoals **deliveryPrepare** toewijzen, die de gebruiker toestaat om leveringen tot stand te brengen en uit te geven.

### Een externe Adobe Experience Manager-account {#configuring-an-adobe-experience-manager-external-account} configureren

U moet een externe account configureren waarmee u Adobe Campaign kunt verbinden met uw AEM.

>[!NOTE]
>
>Zorg er AEM voor dat u het wachtwoord voor de externe gebruiker van de campagne instelt. U moet dit wachtwoord instellen om Adobe Campaign te verbinden met AEM. Login als beheerder en in de console van het gebruikersbeleid, onderzoek naar de campagne-verre gebruiker en klik **Reeks Wachtwoord**.

Een AEM externe account configureren:

1. Ga naar **Beheer** > **Toepassingsinstellingen** > **Externe accounts**.

   ![chlimage_1-124](assets/chlimage_1-124a.png)

1. Selecteer de standaard **nameInstance** externe account of maak een nieuwe account door op de knop **Maken** te klikken.
1. Selecteer **Adobe Experience Manager** i in het veld **Type** en voer de toegangsparameters in die worden gebruikt voor uw AEM ontwerpinstantie: serveradres, accountnaam en wachtwoord.

   >[!NOTE]
   >
   >Zorg ervoor dat u geen beëindigende **/** schuine streep aan het eind van URL toevoegt of de verbinding zal niet werken.

1. Zorg ervoor dat **Enabled** checkbox wordt geselecteerd, dan klik **sparen** om uw wijzigingen te bewaren.

### De optie AEMResourceTypeFilter {#verifying-the-aemresourcetypefilter-option} controleren

De optie **AEMResourceTypeFilter** wordt gebruikt om typen AEM te filteren die in Adobe Campaign kunnen worden gebruikt. Op deze manier kan Adobe Campaign AEM inhoud ophalen die specifiek is ontworpen voor gebruik in alleen Adobe Campaign.

Deze optie is vooraf geconfigureerd; als u deze optie wijzigt, kan dit echter tot een niet-functionerende integratie leiden.

Om te verifiëren wordt de **optie AEMResourceTypeFilter** gevormd:

1. Ga naar **Beheer** > **Toepassingsinstellingen** > **Opties**.
1. In de lijst, kunt u ervoor zorgen dat de **optie AEMResourceTypeFilter** vermeld is en dat de wegen correct zijn.

### Een AEM specifieke sjabloon voor e-maillevering maken {#creating-an-aem-specific-email-delivery-template}

Standaard is de functie AEM niet ingeschakeld in e-mailsjablonen van Adobe Campaign. U kunt een nieuwe sjabloon voor e-maillevering configureren die wordt gebruikt om e-mails met AEM inhoud te maken.

Een AEM-specifieke sjabloon voor e-maillevering maken:

1. Ga naar **Bronnen** > **Sjablonen** > **Leveringssjablonen**.
1. **Schakel** selectie in door op het vinkje op de actiebalk te klikken en de bestaande  **standaardsjabloon voor e-mail (e-mail)** te selecteren. Dubbelklik vervolgens op het pictogram  **** Kopiëren en klik op  **Bevestigen**.
1. Schakel de selectiemodus uit door op **x** te klikken en het nieuwe **exemplaar van standaard-e-mailsjabloon (e-mail)** te openen en vervolgens **Eigenschappen bewerken** te selecteren in de actiebalk van het sjabloondashboard.

   U kunt de **Label** van het malplaatje wijzigen.

1. Wijzig in de sectie **Inhoud** de **Inhoudsbron** in **Adobe Experience Manager**. Selecteer vervolgens de externe account die eerder is gemaakt en klik op **Bevestigen**.

   Sla uw wijzigingen op door te klikken op **Bevestigen** en te klikken op **Opslaan.**

   De functie AEM inhoud is ingeschakeld voor e-mailleveringen die zijn gemaakt op basis van deze sjabloon.

   ![chlimage_1-125](assets/chlimage_1-125a.png)

## Adobe Experience Manager {#configuring-adobe-experience-manager} configureren

Om AEM te vormen, moet u het volgende doen:

* Configureer replicatie tussen instanties.
* Sluit AEM aan op Adobe Campaign.
* Configureer de externalizer.

### Het vormen replicatie tussen AEM instanties {#configuring-replication-between-aem-instances}

Inhoud die is gemaakt van de AEM authoring instantie wordt eerst naar de publishing-instantie verzonden. Deze publicatie-instantie brengt de inhoud vervolgens over naar Adobe Campaign. De replicatieagent moet daarom worden gevormd om van de AEM auteursinstantie aan de AEM het publiceren instantie te herhalen.

>[!NOTE]
>
>Als u de replicatie-URL niet wilt gebruiken maar in plaats daarvan publiek-onder ogen ziet URL gebruiken, kunt u **Openbare URL** in de volgende configuratieplaatsen in OSGi (**Tools** > **Webconsole** > **OSGi Configuratie > AEM de Integratie van de Campagne - Configuratie**) plaatsen:
**Openbare URL:** com.day.cq.mcm.campagne.impl.IntegrationConfigImpl#aem.mcm.campagne.publicUrl

Deze stap is ook nodig om bepaalde configuraties van ontwerpinstanties te repliceren in de publicatieinstantie.

Om replicatie tussen AEM instanties te vormen:

1. Selecteer **AEM logo** **Tools** > **Implementatie** > **Replication** > **Agents op auteur** en klik vervolgens op **Default Agent**.

   ![chlimage_1-126](assets/chlimage_1-126a.png)

   >[!NOTE]
   Vermijd het gebruik van localhost (een lokale kopie van AEM) bij het configureren van uw integratie met Adobe Campaign, tenzij de publicatie- en auteurinstantie beide op dezelfde computer staan.

1. Klik **Edit** dan selecteren **Transport** tabel.
1. Vorm URI door **localhost** met het IP adres of het adres van de AEM het publiceren instantie te vervangen.

   ![chlimage_1-127](assets/chlimage_1-127a.png)

### AEM aansluiten op Adobe Campaign {#connecting-aem-to-adobe-campaign}

Voordat u AEM en Adobe Campaign samen kunt gebruiken, moet u het verband tussen beide oplossingen tot stand brengen zodat zij kunnen communiceren.

1. Verbind met uw AEM authoring instantie.
1. Selecteer **Gereedschappen** > **Bewerkingen** > **Wolk** > **Cloud Services** en **Nu configureren** in de Adobe Campaign-sectie.

   ![chlimage_1-128](assets/chlimage_1-128a.png)

1. Maak een nieuwe configuratie door een **Titel** in te voeren en op **Maken** te klikken, of kies de bestaande configuratie die u met uw Adobe Campaign-instantie wilt koppelen.
1. Bewerk de configuratie zodat deze overeenkomt met de parameters van uw Adobe Campaign-instantie.

   * **Gebruikersnaam**:  **aemserver**, de Adobe Campaign AEM Integration package operator gebruikt om het verband tussen de twee oplossingen tot stand te brengen.
   * **Wachtwoord**: Wachtwoord Adobe Campaign-beheerder. U moet het wachtwoord voor deze operator mogelijk rechtstreeks in Adobe Campaign opnieuw opgeven.
   * **API-eindpunt**: Adobe Campaign-instantie-URL.

1. Selecteer **Verbinding maken met Adobe Campaign** en klik op **OK**.

   ![chlimage_1-129](assets/chlimage_1-129a.png)

   >[!NOTE]
   Nadat u [uw e-mail creeert en het publiceert](/help/sites-authoring/campaign.md), moet u de configuratie op uw publiceren instantie opnieuw publiceren.

   ![chlimage_1-130](assets/chlimage_1-130a.png)

>[!NOTE]
Als de verbinding ontbreekt, zorg ervoor u het volgende controleert:
* Er kan een certificaatprobleem optreden wanneer u een beveiligde verbinding met een Adobe Campaign-instantie (https) gebruikt. U moet het Adobe Campaign-instantiecertificaat toevoegen aan het **cacerts **bestand van uw JDK.
* Zie [Problemen met uw AEM/Adobe Campaign-integratie oplossen](/help/sites-administering/troubleshooting-campaignintegration.md).



### De externalizer {#configuring-the-externalizer} configureren

U moet [externalizer](/help/sites-developing/externalizer.md) in AEM op uw auteursinstantie vormen. ExternalAlizer is de dienst OSGi die u een middelweg in een externe en absolute URL laat omzetten. Deze service biedt een centrale plaats om die externe URL&#39;s te configureren en samen te stellen.

Zie [De externalizer](/help/sites-developing/externalizer.md) voor algemene instructies configureren. Voor de integratie van Adobe Campaign moet u de publicatieserver op `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl` niet richten naar `localhost:4503` maar naar een server die bereikbaar is door de Adobe Campaign-console.

Als het verwijst naar `localhost:4503` of een andere server die Adobe Campaign niet kan bereiken, worden uw afbeeldingen niet weergegeven op de Adobe Campaign-console.

![chlimage_1-131](assets/chlimage_1-131a.png)

