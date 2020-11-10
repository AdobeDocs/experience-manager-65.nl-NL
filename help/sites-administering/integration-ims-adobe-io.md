---
title: Integratie met Adobe Target met behulp van Adobe I/O
seo-title: Integratie met Adobe Target met behulp van Adobe I/O
description: Meer informatie over het integreren van AEM met Adobe Target met behulp van Adobe I/O
seo-description: Meer informatie over het integreren van AEM met Adobe Target met behulp van Adobe I/O
uuid: dd4ed638-e182-4d7e-9c98-282431812467
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: integration
discoiquuid: 3b9285db-8fba-4d12-8f52-41daa50a5403
docset: aem65
translation-type: tm+mt
source-git-commit: 26efba567985dcb89b2610935cab18943b7034b3
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 0%

---


# Integratie met Adobe Target met behulp van Adobe I/O{#integration-with-adobe-target-using-adobe-i-o}

De integratie van AEM met Adobe Target via de Target Standard API vereist de configuratie van Adobe IMS (Identity Management System) en Adobe I/O.

>[!NOTE]
>
>Ondersteuning voor de Adobe Target Standard API is nieuw in AEM 6.5. De doel-standaard-API gebruikt IMS-verificatie.
>
>Het gebruik van de Classic API van Adobe Target in AEM wordt nog steeds ondersteund voor achterwaartse compatibiliteit. De Klassieke [API van het Doel gebruikt gebruikersgeloofsauthentificatie](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).
>
>De API-selectie wordt aangestuurd door de verificatiemethode die wordt gebruikt voor AEM/doelintegratie.

## Vereisten {#prerequisites}

Voordat u met deze procedure begint:

* [Adobe Support](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) moet uw account voorzien voor:

   * Adobe-console
   * Adobe I/O
   * Adobe Target en
   * Adobe IMS (Identity Management-systeem)

* De systeembeheerder van het Systeem van uw organisatie zou de Admin Console moeten gebruiken om de vereiste ontwikkelaars in uw organisatie aan de relevante productprofielen toe te voegen.

   * Dit verstrekt de specifieke ontwikkelaars met toestemmingen om integratie binnen Adobe I/O toe te laten.
   * Zie [Ontwikkelaars](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)beheren voor meer informatie.


## Een IMS-configuratie configureren - Een openbare sleutel genereren {#configuring-an-ims-configuration-generating-a-public-key}

De eerste fase van de configuratie is het creëren van een Configuratie IMS in AEM en het produceren van de Openbare Sleutel.

1. Open AEM het menu **Gereedschappen** .
1. Selecteer in de sectie **Beveiliging** de optie **Adobe IMS Configurations**.
1. Selecteer **Maken** om de **Adobe IMS Technical Account Configuration** te openen.
1. Selecteer **Adobe Target** in het keuzemenu onder **Cloud Configuration**.
1. Activeer **Nieuw certificaat** maken en voer een nieuwe alias in.
1. Bevestig met certificaat **** maken.

   ![](assets/integrate-target-io-01.png)

1. Selecteer **Download** (of **Download Public Key**) om het bestand naar uw lokale schijf te downloaden, zodat het klaar is voor gebruik wanneer u Adobe I/O [configureert voor Adobe Target-integratie met AEM](#configuring-adobe-i-o-for-adobe-target-integration-with-aem).

   >[!CAUTION]
   >
   >Houd deze configuratie open, zal het opnieuw nodig zijn wanneer het [Voltooien van de Configuratie IMS in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-target-io-02.png)

## Adobe I/O configureren voor Adobe Target-integratie met AEM {#configuring-adobe-i-o-for-adobe-target-integration-with-aem}

U moet het Adobe I/O-project (integratie) maken met Adobe Target dat AEM gebruiken en vervolgens de vereiste rechten toewijzen.

### Het project maken {#creating-the-project}

Open de Adobe I/O-console om een I/O-project te maken met Adobe Target dat AEM gebruikt:

>[!NOTE]
>
>Zie ook de [Adobe I/O-zelfstudies](https://www.adobe.io/apis/experienceplatform/home/tutorials/alltutorials.html).

1. Open de Adobe I/O-console voor projecten:

   [https://console.adobe.io/projects](https://console.adobe.io/projects)

1. Alle projecten die u hebt, worden weergegeven. Selecteer Nieuw project **** maken - de locatie en het gebruik zijn afhankelijk van:

   * Als u nog geen project hebt, **maakt u een nieuw project** onder in het middelpunt.
      ![Nieuw project maken - eerste project](assets/integration-target-io-02.png)
   * Als u al bestaande projecten hebt, worden deze weergegeven en **wordt het nieuwe project** gemaakt.
      ![Nieuw project maken - Meerdere projecten](assets/integration-target-io-03.png)


1. Selecteer **Toevoegen aan project** gevolgd door **API**:

   ![](assets/integration-target-io-10.png)

1. Selecteer **Adobe Target** en vervolgens **Volgende**:

   >[!NOTE]
   >
   >Als je bent geabonneerd op Adobe Target, maar deze niet ziet, moet je de [voorwaarden](#prerequisites)controleren.

   ![](assets/integration-target-io-12.png)

1. **Upload uw openbare sleutel**, en wanneer volledig, ga met **Volgende** verder:

   ![](assets/integration-target-io-13.png)

1. Controleer de referenties en ga verder met **Volgende**:

   ![](assets/integration-target-io-15.png)

1. Selecteer de vereiste productprofielen en ga verder met de geconfigureerde API **voor** opslaan:

   >[!NOTE]
   >
   >De productprofielen die worden weergegeven met, zijn afhankelijk van het volgende:
   >
   >* Adobe Target Standard - alleen de **standaardwerkruimte** is beschikbaar
   >* Adobe Target Premium - alle beschikbare werkruimten worden weergegeven, zoals hieronder wordt weergegeven


   ![](assets/integration-target-io-16.png)

1. De oprichting zal worden bevestigd.

<!--
1. The creation will be confirmed, you can now **Continue to integration details**; these are needed for [Completing the IMS Configuration in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-target-io-07.png)
-->

### Rechten toewijzen aan de integratie {#assigning-privileges-to-the-integration}

U moet nu de vereiste rechten toewijzen aan de integratie:

1. Open de **Admin Console** Adobe:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigeer naar **Producten** (bovenste werkbalk) en selecteer vervolgens **Adobe Target - &lt;*uw-huurder-id*>** (in het linkerdeelvenster).
1. Selecteer **Productprofielen** en vervolgens de gewenste werkruimte in de weergegeven lijst. Bijvoorbeeld de standaardwerkruimte.
1. Selecteer **Integraties**, dan de vereiste integratieconfiguratie.
1. Selecteer **Editor** als de **productrol**; in plaats van **waarnemer**.

## Gegevens die zijn opgeslagen voor het Adobe I/O-integratieproject {#details-stored-for-the-adobe-io-integration-project}

Van de Adobe I/O van Projecten console kunt u een lijst van al uw integratieprojecten zien:

* [https://console.adobe.io/projects](https://console.adobe.io/projects)

Selecteer **Mening** (rechts van een specifieke projectingang) om verdere details over de configuratie te tonen. Deze omvatten:

* Overzicht van project
* Inzichten
* Credentials
   * Serviceaccount (JWT)
      * Referentiegegevens
      * JWT genereren
* APIS
   * Bijvoorbeeld Adobe Target

Bij sommige hiervan moet u de Adobe I/O-integratie voor Target in AEM voltooien.

## De IMS-configuratie voltooien in AEM {#completing-the-ims-configuration-in-aem}

Terugkeren naar AEM kunt u de configuratie voltooien IMS door vereiste waarden van de Adobe I/O integratie voor Doel toe te voegen:

1. Ga terug naar de [IMS-configuratie die is geopend in AEM](#configuring-an-ims-configuration-generating-a-public-key).
1. Selecteer **Volgende**.

1. Hier kunt u de [details van Adobe I/O](#details-stored-for-the-adobe-io-integration-project)gebruiken:

   * **Titel**: Uw tekst.
   * **Autorisatieserver**: Kopieer/plak deze vanuit de `"aud"` regel van de **sectie Payload** hieronder, bijvoorbeeld `"https://ims-na1.adobelogin.com"` in het onderstaande voorbeeld.
   * **API-sleutel**: Kopieer dit uit de sectie [Overzicht](#details-stored-for-the-adobe-io-integration-project) van de Adobe I/O-integratie voor Doel
   * **Clientgeheim**: Genereer dit in de sectie [Overzicht](#details-stored-for-the-adobe-io-integration-project) van de Adobe I/O-integratie voor Doel, en kopieer
   * **Payload**: Kopieer dit uit de sectie [Genereer JWT](#details-stored-for-the-adobe-io-integration-project) van de Adobe I/O-integratie voor Doel

   ![](assets/integrate-target-io-10.png)

1. Bevestig met **Maken**.

1. Uw Adobe Target-configuratie wordt weergegeven in de AEM console.

   ![](assets/integrate-target-io-11.png)

## De IMS-configuratie bevestigen {#confirming-the-ims-configuration}

Om te bevestigen dat de configuratie zoals verwacht werkt:

1. Open:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Bijvoorbeeld:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Selecteer uw configuratie.
1. Selecteer **Health** controleren op de werkbalk, gevolgd door **Check**.

   ![](assets/integrate-target-io-12.png)

1. Als dit lukt, wordt het bericht weergegeven:

   ![](assets/integrate-target-io-13.png)

## De Adobe Target-Cloud Service configureren {#configuring-the-adobe-target-cloud-service}

Er kan nu naar de configuratie worden verwezen, zodat een Cloud Service de standaard-API van het doel kan gebruiken:

1. Open het menu **Gereedschappen** . Selecteer vervolgens in de sectie **Cloud Services** de optie **Oudere Cloud Services**.
1. Blader omlaag naar **Adobe Target** en selecteer **Nu** configureren.

   Het dialoogvenster **Configuratie** maken wordt geopend.

1. Voer een **titel** en desgewenst een **naam** in (als deze leeg wordt gelaten, wordt deze uit de titel gegenereerd).

   U kunt ook de vereiste sjabloon selecteren (als er meerdere sjablonen beschikbaar zijn).

1. Bevestig met **Maken**.

   Het dialoogvenster Component **** bewerken wordt geopend.

1. Voer de gegevens in op het tabblad **Adobe Target-instellingen** :

   * **Verificatie**: IMS
   * **ID** huurder: de Adobe IMS Tenant ID

      >[!NOTE]
      >
      >Voor IMS moet deze waarde van Target zelf worden genomen. U kunt zich aanmelden bij Target en de Tenant-id uit de URL extraheren.
      >
      >Als de URL bijvoorbeeld:
      >
      >`https://experience.adobe.com/#/@yourtenantid/target/activities`
      >
      >Dan zou je gebruiken `yourtenantid`.

   * **IMS-configuratie**: Selecteer de naam van de IMS-configuratie
   * **API-type**: REST
   * **A4T Analytics Cloud-configuratie**: Selecteer de de wolkenconfiguratie van de Analyse die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. Dit is nodig als u Adobe Analytics als rapportagebron gebruikt wanneer u inhoud als doel instelt. Als u uw wolkenconfiguratie niet ziet, zie nota in het [Vormen van de Configuratie](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration)van A4T Analytics Cloud.
   * **Gebruik nauwkeurige doelwitten**: Dit selectievakje is standaard ingeschakeld. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.
   * **Segmenten uit Adobe Target** synchroniseren: Selecteer deze optie om segmenten te downloaden die in Doel zijn gedefinieerd om deze in AEM te gebruiken. U moet deze optie selecteren wanneer het bezit van het Type API REST is, omdat de gealigneerde segmenten niet worden gesteund en u altijd segmenten van Doel moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)
   * **Clientbibliotheek**: Selecteer of u de AT.js cliëntbibliotheek, of mbox.js (afgekeurd) wilt.
   * **Tagbeheersysteem gebruiken om clientbibliotheek** te leveren: Gebruik DTM (afgekeurd), Adobe Launch of een ander systeem voor tagbeheer.
   * **Aangepaste AT.js**: Laat leeg als u het vak Tagbeheer hebt ingeschakeld of als u de standaard-AT.js wilt gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

   >[!NOTE]
   >
   >[De configuratie van een Cloud Service voor het gebruik van de Klassieke API](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) van het Doel is afgekeurd (gebruikt het tabblad Adobe Recommendations-instellingen).

   Bijvoorbeeld:

   ![](assets/integrate-target-io-14.png)

1. Klik op **Verbinding maken met doel** om de verbinding met Adobe Target te initialiseren.

   Als de verbinding succesvol is, wordt het bericht **Verbinding succesvol** getoond.

1. Selecteer **OK** in het bericht, gevolgd door **OK** in het dialoogvenster om de configuratie te bevestigen.
1. U kunt nu aan het [Toevoegen van een Kader](/help/sites-administering/target-configuring.md#adding-a-target-framework) van het Doel te werk gaan om parameters te vormen ContextHub of ClientContext die naar Doel zullen worden verzonden. Dit is mogelijk niet vereist voor het exporteren AEM Experience Fragments naar Target.

