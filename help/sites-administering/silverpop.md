---
title: Integreren met Silverpop Engage
seo-title: Integrating with Silverpop Engage
description: Leer hoe u AEM kunt integreren met Silverpop Engage
seo-description: Learn how to integrate AEM with Silverpop Engage
uuid: e17deeb6-5339-4ead-9086-cbe2167cdec6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 01029a80-f80e-450c-9c73-16d0662af26d
docset: aem65
exl-id: 6c4b8aaa-bda0-4066-a3fc-d91a5ab1621c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Integreren met Silverpop Engage{#integrating-with-silverpop-engage}

>[!NOTE]
>
>Silverpop-integratie is **niet** beschikbaar in de verpakking. U moet de [Silverpop-integratiepakket](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/aem620/product/cq-mcm-integrations-silverpop-content) vanuit Package Share en installeer deze op uw exemplaar. Nadat u het pakket hebt geïnstalleerd, kunt u het vormen zoals die in dit document wordt beschreven.

Door AEM te integreren met Silverpop Engage kunt u e-mails die in AEM via Silverpop zijn gemaakt, beheren en verzenden. U kunt hiermee ook de beheerfuncties voor leads van Silverpop gebruiken via AEM formulieren op AEM pagina&#39;s.

De integratie biedt u de volgende functies:

* De mogelijkheid om e-mails te maken in AEM en deze te publiceren naar Silverpop voor distributie.
* De mogelijkheid om actie van een AEM formulier in te stellen om een Silverpop-abonnee te maken.

Nadat Silverpop Engage is geconfigureerd, kunt u nieuwsbrieven of e-mails publiceren naar Silverpop Engage.

## Een Silverpop-configuratie maken {#creating-a-silverpop-configuration}

Silverpop-configuraties kunnen worden toegevoegd via **Wolkendiensten**, **Gereedschappen**, of **API-eindpunten**. Alle methoden worden beschreven in deze sectie.

### Silverpop configureren via Cloudservices {#configuring-silverpop-via-cloudservices}

Een Silverpop-configuratie in Cloud Services maken:

1. Tik in AEM of klik op **Gereedschappen** > **Implementatie** > **Cloud Services**. (Of rechtstreeks toegang tot `https://<hostname>:<port>/etc/cloudservices.html`.)
1. Klik onder services van derden op **Silverop Engage** en vervolgens **Configureren**. Het Silverpop-configuratievenster wordt geopend.

   >[!NOTE]
   >
   >Silverpop Engage is niet beschikbaar als optie onder services van derden, tenzij u het pakket downloadt van Package Share.

1. Voer een titel en eventueel een naam in en klik op **Maken**. Het** Silverpop Settings* configuratievenster wordt geopend.
1. Voer de gebruikersnaam en het wachtwoord in en selecteer een API-eindpunt in de vervolgkeuzelijst.
1. Klikken **Verbind met Silverpop.** Wanneer de verbinding tot stand is gebracht, wordt het dialoogvenster geslaagd. Klikken **OK** om het venster te sluiten. U kunt naar Silverpop gaan door op **Ga naar Silverpop Engage**.
1. Silverpop is geconfigureerd. U kunt de configuratie bewerken door op **Bewerken**.
1. Daarnaast kan Silverpop Engage-framework worden geconfigureerd voor persoonlijke acties door titel en naam (optioneel) op te geven. Klik op Maken om het framework voor de reeds geconfigureerde Silverpop-verbinding te maken.

   De ingevoerde kolommen van de gegevensuitbreiding kunnen later door de AEM worden gebruikt - **Tekst en personalisatie**.

### Silverpop configureren via gereedschappen {#configuring-silverpop-via-tools}

Een Silverpop-configuratie maken in de gereedschappen:

1. Tik in AEM of klik op **Gereedschappen** > **Implementatie** > **Cloud Services**. Of navigeer daar rechtstreeks door naar `https://<hostname>:<port>/misadmin#/etc`.
1. Selecteren **Gereedschappen** vervolgens **Cloud Services-configuraties,** dan **Silverpop-engine**.
1. Klikken **Nieuw** om de **Pagina maken** venster.

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

1. Voer de **Titel** en eventueel de **Naam** en klik op **Maken**.
1. Ga de configuratieinformatie in zoals die in stap 4 in de vorige procedure wordt geschetst. Volg die procedure om te voltooien vormend Silverpop.

### Meerdere configuraties toevoegen {#adding-multiple-configurations}

Meerdere configuraties toevoegen:

1. Klik op de welkomstpagina op **Cloud Services** en klik op **Silverpop-engine**. Klikken op **Configuraties tonen** die wordt weergegeven als een of meer Silverpop-configuraties beschikbaar zijn. Alle beschikbare configuraties worden vermeld.
1. Klik op de knop **+** ondertekenen naast Beschikbare configuraties. Hierdoor wordt het **Configuraties maken** venster. Volg de vorige configuratieprocedure om een nieuwe configuratie tot stand te brengen.

### API-eindpunten configureren voor verbinding met Silverpop {#configuring-api-end-points-for-connecting-to-silverpop}

AEM heeft momenteel zes onbeveiligde eindpunten (Engage 1 tot en met 6). Silverpop biedt nu twee nieuwe eindpunten en gewijzigde verbindings eindpunten voor de bestaande.

De API-eindpunten configureren:

1. Ga naar `/libs/mcm/silverpop/components/silverpoppage/dialog/items/general/items/apiendpoint/options node` op `https://<hostname>:<port>/crxde.`
1. Klik met de rechtermuisknop en selecteer **Maken** vervolgens **Knooppunt maken**.
1. Voer de **Naam** als `sp-e0` en kiest u **Type** als `cq:Widget`.
1. Twee eigenschappen toevoegen aan het nieuwe knooppunt:

   1. **Naam**: `text`, **Type**: `String`, **Waarde**: `Engage 0`
   1. **Naam**: `value`, **Type**: `String`, **Waarde**: `https://api0.silverpop.com`

   ![chlimage_1-42](assets/chlimage_1-42.png)

   Klik op de knop Alles opslaan.

1. Maak nog een knooppunt met **Naam** als `sp-e7` en **Type** als `cq:Widget`.

   Twee eigenschappen toevoegen aan het nieuwe knooppunt:

   1. **Naam**: `text`, **Type**: `String`, **Waarde**: `Pilot`
   1. **Naam**: `value`, **Type**: `String`, **Waarde**: `https://apipilot.silverpop.com/XMLAPI`

1. Als u de bestaande API-eindpunten wilt wijzigen (Engage 1 tot en met 6), klikt u op elk van deze eindpunten een voor een en vervangt u de waarden als volgt:

   | **Node Name** | **Bestaande eindpuntwaarde** | **Nieuwe eindpuntwaarde** |
   |---|---|---|
   | sp-e1 | https://api.engage1.silverpop.com/XMLAPI | https://api1.silverpop.com |
   | sp-e2 | https://api.engage2.silverpop.com/XMLAPI | https://api2.silverpop.com |
   | sp-e3 | https://api.engage3.silverpop.com/XMLAPI | https://api3.silverpop.com |
   | sp-e4 | https://api.engage4.silverpop.com/XMLAPI | https://api4.silverpop.com |
   | sp-e5 | https://api.engage5.silverpop.com/XMLAPI | https://api5.silverpop.com |
   | sp-e6 | https://api.pilot.silverpop.com/XMLAPI | https://api6.silverpop.com |

1. Klikken **Alles opslaan**. AEM is nu klaar om verbinding te maken met Silverpop via beveiligde eindpunten.

   ![chlimage_1-7](assets/chlimage_1-7.jpeg)
