---
title: Salesforce Commerce Cloud
seo-title: Salesforce Commerce Cloud/Demandware
description: Leer hoe u eCommerce kunt implementeren met Salesforce Commerce Cloud/Demandware.
seo-description: Leer hoe u eCommerce kunt implementeren met Salesforce Commerce Cloud/Demandware.
uuid: c0270632-bdd2-4dba-bbbe-312757ea20f4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 52cc3162-b638-410d-854a-383399e2effb
docset: aem65
pagetitle: Deploying eCommerce with Demandware
redirecttarget: https //github.com/adobe/commerce-salesforce
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 2%

---


# Salesforce Commerce Cloud{#salesforce-commerce-cloud}

De implementatie van de noodzakelijke e-commercepakketten zal de volledige functionaliteit van het eCommerce-kader bieden, samen met een referentie-implementatie van de eCommerce-functionaliteit zoals voorzien van een Salesforce Commerce Cloud/Demandware-implementatie (inclusief een demonstratiecatalogus).

## Pakketten nodig voor e-handel met Salesforce Commerce Cloud {#packages-needed-for-ecommerce-with-salesforce-commerce-cloud}

Voor de installatie van eCommerce-functionaliteit hebt u het volgende nodig:

* AEM eCommerce-kader:

   * dit maakt deel uit van een standaard AEM installatie

* AEM pakket met informatie over de softwarehandel

   * cq-6.4.0-featurepack-10262

>[!NOTE]
>
>Deze integratie steunt instanties Salesforce Commerce Cloud/Demandware die worden gevormd om OCAPI versie 17.6 of later te gebruiken.

### Installatie van eCommerce met Salesforce Commerce Cloud {#installation-of-ecommerce-with-salesforce-commerce-cloud}

Om AEM met een de integratieconfiguratie van de Handel van de Demandware te installeren (gebruikend de demonstratiecatalogus, Geometrixx Outdoors), zijn de basisstappen:

1. [AEM](/help/sites-deploying/deploy.md) installeren.
1. Installeer het inhoudspakket met behulp van [pakketbeheer](/help/sites-administering/package-manager.md):
1. [](/help/sites-authoring/page-authoring.md) Geef aanvullende pagina&#39;s op die u in AEM nodig hebt.

>[!NOTE]
>
>Navigeer naar [Delen van pakket](/help/sites-administering/package-manager.md#package-share) om de pakketten te downloaden.

De serververbinding tussen AEM en de Duidelijke Sandbox moet worden gevormd. Het grootste deel van de configuratie is reeds preconfigured om met het verstrekte pakket van de de demo van SiteGenisis inhoud te werken gebruikend standaardwegen, bibliotheken, etc. Als de schakelaar met andere plaatsen en bibliotheken wordt gebruikt, zult u deze configuratie moeten bijwerken.

1. Navigeer naar [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Klik **Demandware Client**.
1. Ga **Instantie eindpunt ip of hostname** in zoals vereist.

   ![chlimage_1-5](assets/chlimage_1-5.png)

1. Klik **Opslaan**.
1. Klik **De Insteekmodule van TransportHandler van de Vraag voor WebDAV**.
1. Stel de **WebDAV-gebruiker** en het **WebDAV-gebruikerswachtwoord** in.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Klik **Opslaan**.

#### Replicatie {#replication}

De replicatie zou na de pakketinstallatie moeten worden toegelaten, kunt u verifiëren dat hier: [https://localhost:4502/etc/replication/agents.author/demandware.html](https://localhost:4502/etc/replication/agents.author/demandware.html)

>[!NOTE]
>
>De replicatieagent wordt gevormd aan het niveau van het informatielogboek door gebrek. Als u meer informatie wilt hebben, kunt u het logboekniveau veranderen om te zuiveren.

#### OAuth {#oauth}

De OAuth-client is geconfigureerd om te werken met een veeleisende sandbox-instantie. Voor testdoeleinden is geen wijziging nodig.

Voor het opvoeren en de productiesystemen, moeten de cliënten OAuth met aangewezen cliëntidentiteitskaart en wachtwoord worden gevormd.

1. Navigeer naar [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
1. Klik **De Token van de Toegang van de Vraag leverancier**.

   ![chlimage_1-7](assets/chlimage_1-7.png)

1. Wijzig desgewenst de waarden en klik op **Opslaan**.

### Salesforce Commerce Cloud Sandbox {#salesforce-commerce-cloud-sandbox}

De Duandware Sandbox moet worden gevormd om de nieuwe het malplaatjemotor van de Snelheid in werking te stellen.

>[!NOTE]
>
>De volgende tovenaar maakt geen deel uit van de AEM schakelaar van de Demandware. Deze pagina wordt geleverd als onderdeel van het pakket met demo-inhoud, zodat u snel de SiteGenesis-demopagina&#39;s kunt instellen.

1. Navigeer naar [https://localhost:4502/etc/demandware/init.html](https://localhost:4502/etc/demandware/init.html).
1. Klik **Bewerken.**
1. Verifieer de waarden en klik **OK**.
1. Klik **Initialiseren**.
1. Ga naar de WebDAV omslag en controleer voor gepubliceerde malplaatjedossiers, bijvoorbeeld onder `adobe01-tech-prtnr-na01-dw.demandware.net/on/demandware.servlet/webdav/Sites/Dynamic/SiteGenesis`.

   >[!NOTE]
   >
   >De extensie is `.vs`.

1. Schakel ook in voor geëxporteerde JS- en CSS-bestanden, bijvoorbeeld onder `adobe01-tech-prtnr-na01-dw.demandware.net/on/demandware.servlet/webdav/Sites/Libraries/SiteGenesisSharedLibrary`.

