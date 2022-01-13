---
title: Integratie met Adobe Target met Adobe I/O
seo-title: Integration with Adobe Target using Adobe I/O
description: Meer informatie over het integreren van AEM met Adobe Target met behulp van Adobe I/O
seo-description: Learn about integrating AEM with Adobe Target using Adobe I/O
uuid: dd4ed638-e182-4d7e-9c98-282431812467
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: integration
discoiquuid: 3b9285db-8fba-4d12-8f52-41daa50a5403
docset: aem65
exl-id: ba7abc53-7db8-41b1-a0fa-4e4dbbeca402
source-git-commit: d1b4cf87291f7e4a0670a21feca1ebf8dd5e0b5e
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 0%

---

# Integratie met Adobe Target met Adobe I/O{#integration-with-adobe-target-using-adobe-i-o}

Voor de integratie van AEM met Adobe Target via de Target Standard API is de configuratie van Adobe IMS (Identity Management System) en Adobe I/O vereist.

>[!NOTE]
>
>Ondersteuning voor de Adobe Target Standard API is nieuw in AEM 6.5. De doel-standaard-API gebruikt IMS-verificatie.
>
>Het gebruik van de Classic API van Adobe Target in AEM wordt nog steeds ondersteund voor achterwaartse compatibiliteit. De [De Klassieke API van het doel gebruikt gebruikersgeloofsauthentificatie](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).
>
>De API-selectie wordt aangestuurd door de verificatiemethode die wordt gebruikt voor AEM/doelintegratie.
>Zie ook de [Aanbestedings-id en clientcode](#tenant-client) sectie.

## Vereisten {#prerequisites}

Voordat u met deze procedure begint:

* [Adobe-ondersteuning](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) moet je account opgeven voor:

   * Adobe-console
   * Adobe I/O
   * Adobe Target en
   * Adobe IMS (Identity Management-systeem)

* De systeembeheerder van het Systeem van uw organisatie zou de Admin Console moeten gebruiken om de vereiste ontwikkelaars in uw organisatie aan de relevante productprofielen toe te voegen.

   * Dit voorziet de specifieke ontwikkelaars van toestemmingen om integratie binnen Adobe I/O toe te laten.
   * Zie voor meer informatie [Ontwikkelaars beheren](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Een IMS-configuratie configureren - Een openbare sleutel genereren {#configuring-an-ims-configuration-generating-a-public-key}

De eerste fase van de configuratie is het creëren van een Configuratie IMS in AEM en het produceren van de Openbare Sleutel.

1. In AEM opent u de **Gereedschappen** -menu.
1. In de **Beveiliging** sectie selecteren **Adobe IMS-configuraties**.
1. Selecteren **Maken** om de **Configuratie technische account van Adobe IMS**.
1. De vervolgkeuzelijst onder gebruiken **Cloud Configuration**, selecteert u **Adobe Target**.
1. Activeren **Nieuw certificaat maken** en voert u een nieuwe alias in.
1. Bevestigen met **Certificaat maken**.

   ![](assets/integrate-target-io-01.png)

1. Selecteren **Downloaden** (of **Openbare sleutel downloaden**) om het bestand naar uw lokale station te downloaden, zodat het klaar is voor gebruik wanneer [Adobe I/O configureren voor Adobe Target-integratie met AEM](#configuring-adobe-i-o-for-adobe-target-integration-with-aem).

   >[!CAUTION]
   >
   >Zorg dat deze configuratie geopend blijft, dat deze opnieuw nodig is wanneer [De IMS-configuratie voltooien in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-target-io-02.png)

## Adobe I/O configureren voor Adobe Target-integratie met AEM {#configuring-adobe-i-o-for-adobe-target-integration-with-aem}

U moet het Adobe I/O Project (integratie) met Adobe Target tot stand brengen dat AEM zal gebruiken, dan de vereiste voorrechten toewijzen.

### Het project maken {#creating-the-project}

Open de Adobe I/O-console om een I/O-project te maken met Adobe Target dat AEM gebruiken:

>[!NOTE]
>
>Zie ook de [Adobe I/O-zelfstudies](https://www.adobe.io/apis/experienceplatform/home/tutorials/alltutorials.html).

1. Open de Adobe I/O console voor Projecten:

   [https://console.adobe.io/projects](https://console.adobe.io/projects)

1. Alle projecten die u hebt, worden weergegeven. Selecteren **Nieuw project maken** - de locatie en het gebruik zijn afhankelijk van:

   * Als u nog geen project hebt, **Nieuw project maken** wordt midden onderaan weergegeven.
      ![Nieuw project maken - eerste project](assets/integration-target-io-02.png)
   * Als u al bestaande projecten hebt, worden deze weergegeven en **Nieuw project maken** is helemaal rechts.
      ![Nieuw project maken - Meerdere projecten](assets/integration-target-io-03.png)


1. Selecteren **Toevoegen aan project** gevolgd door **API**:

   ![](assets/integration-target-io-10.png)

1. Selecteren **Adobe Target** vervolgens **Volgende**:

   >[!NOTE]
   >
   >Als je bent geabonneerd op Adobe Target, maar deze niet ziet, moet je de knop [Vereisten](#prerequisites).

   ![](assets/integration-target-io-12.png)

1. **Uw openbare sleutel uploaden** en, indien voltooid, doorgaan met **Volgende**:

   ![](assets/integration-target-io-13.png)

1. Controleer de referenties en ga verder met **Volgende**:

   ![](assets/integration-target-io-15.png)

1. Selecteer de vereiste productprofielen en ga verder met **geconfigureerde API opslaan**:

   >[!NOTE]
   >
   >De productprofielen die worden weergegeven met, zijn afhankelijk van het volgende:
   >
   >* Adobe Target Standard - alleen **Standaardwerkruimte** is beschikbaar
   >* Adobe Target Premium - alle beschikbare werkruimten worden weergegeven, zoals hieronder wordt weergegeven


   ![](assets/integration-target-io-16.png)

1. De oprichting zal worden bevestigd.

<!--
1. The creation will be confirmed, you can now **Continue to integration details**; these are needed for [Completing the IMS Configuration in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-target-io-07.png)
-->

### Rechten toewijzen aan de integratie {#assigning-privileges-to-the-integration}

U moet nu de vereiste rechten toewijzen aan de integratie:

1. De Adobe openen **Admin Console**:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigeren naar **Producten** (bovenste werkbalk) selecteert u vervolgens **Adobe Target - &lt;*uw huurder*>** (in het linkerdeelvenster).
1. Selecteren **Productprofielen**, dan uw vereiste werkruimte uit de gepresenteerde lijst. Bijvoorbeeld de standaardwerkruimte.
1. Selecteren **Integraties**, dan de vereiste integratieconfiguratie.
1. Selecteren **Editor** als de **Productrol**; in plaats van **Waarnemer**.

## Details die voor het Project van de Integratie van de Adobe I/O worden opgeslagen {#details-stored-for-the-adobe-io-integration-project}

Van de console van de Projecten van Adobe I/O kunt u een lijst van al uw integratieprojecten zien:

* [https://console.adobe.io/projects](https://console.adobe.io/projects)

Selecteren **Weergave** (rechts van een specifieke projectvermelding) om verdere details over de configuratie te tonen. Deze omvatten:

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

Terugkeren naar AEM kunt u de configuratie voltooien IMS door vereiste waarden van de integratie van Adobe I/O voor Doel toe te voegen:

1. Terugkeren naar de [IMS-configuratie geopend in AEM](#configuring-an-ims-configuration-generating-a-public-key).
1. Selecteren **Volgende**.

1. Hier kunt u de [details van Adobe I/O](#details-stored-for-the-adobe-io-integration-project):

   * **Titel**: Uw tekst.
   * **Autorisatieserver**: Kopieer/plak deze vanuit de `"aud"` lijn van de **Payload** hieronder, bijvoorbeeld `"https://ims-na1.adobelogin.com"` in het onderstaande voorbeeld
   * **API-sleutel**: Kopieer deze van de [Overzicht](#details-stored-for-the-adobe-io-integration-project) deel van de integratie van Adobe I/O voor Target
   * **Clientgeheim**: Dit genereren in het dialoogvenster [Overzicht](#details-stored-for-the-adobe-io-integration-project) sectie van de Adobe I/O integratie voor Doel, en exemplaar
   * **Payload**: Kopieer deze van de [JWT genereren](#details-stored-for-the-adobe-io-integration-project) deel van de integratie van Adobe I/O voor Target

   ![](assets/integrate-target-io-10.png)

1. Bevestigen met **Maken**.

1. Uw Adobe Target-configuratie wordt weergegeven in de AEM console.

   ![](assets/integrate-target-io-11.png)

## De IMS-configuratie bevestigen {#confirming-the-ims-configuration}

Om te bevestigen dat de configuratie zoals verwacht werkt:

1. Open:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Bijvoorbeeld:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Selecteer uw configuratie.
1. Selecteren **Health controleren** van de werkbalk, gevolgd door **Controleren**.

   ![](assets/integrate-target-io-12.png)

1. Als dit lukt, wordt het bericht weergegeven:

   ![](assets/integrate-target-io-13.png)

## De Adobe Target-Cloud Service configureren {#configuring-the-adobe-target-cloud-service}

Er kan nu naar de configuratie worden verwezen, zodat een Cloud Service de standaard-API van het doel kan gebruiken:

1. Open de **Gereedschappen** -menu. Dan, binnen **Cloud Services** sectie, selecteert u **Oudere Cloud Services**.
1. Omlaag schuiven naar **Adobe Target** en selecteert u **Nu configureren**.

   De **Configuratie maken** wordt geopend.

1. Voer een **Titel** en, indien gewenst, een **Naam** (als deze optie leeg blijft, wordt deze gegenereerd op basis van de titel).

   U kunt ook de vereiste sjabloon selecteren (als er meerdere sjablonen beschikbaar zijn).

1. Bevestigen met **Maken**.

   De **Component bewerken** wordt geopend.

1. Voer de gegevens in het dialoogvenster **Adobe Target-instellingen** tab:

   * **Verificatie**: IMS
   * **Tenant-id**: de Adobe IMS Tenant ID. Zie ook de [Aanbestedings-id en clientcode](#tenant-client) sectie.

      >[!NOTE]
      >
      >Voor IMS moet deze waarde van Target zelf worden genomen. U kunt zich aanmelden bij Target en de Tenant-id uit de URL extraheren.
      >
      >Als de URL bijvoorbeeld:
      >
      >`https://experience.adobe.com/#/@yourtenantid/target/activities`
      >
      >Vervolgens gebruikt u `yourtenantid`.
   * **Clientcode**: Zie de [Aanbestedings-id en clientcode](#tenant-client) sectie.
   * **IMS-configuratie**: Selecteer de naam van de IMS-configuratie
   * **API-type**: REST
   * **A4T Analytics Cloud-configuratie**: Selecteer de de wolkenconfiguratie van de Analyse die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. Dit is nodig als u Adobe Analytics als rapportagebron gebruikt wanneer u inhoud als doel instelt. Als u de cloudconfiguratie niet ziet, raadpleegt u de opmerking in [A4T Analytics Cloud-configuratie configureren](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration).
   * **Nauwkeurige doelgerichtheid gebruiken**: Dit selectievakje is standaard ingeschakeld. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.
   * **Segmenten synchroniseren vanuit Adobe Target**: Selecteer deze optie om segmenten te downloaden die in Doel zijn gedefinieerd om deze in AEM te gebruiken. U moet deze optie selecteren wanneer het bezit van het Type API REST is, omdat de gealigneerde segmenten niet worden gesteund en u altijd segmenten van Doel moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)
   * **Clientbibliotheek**: Selecteer of u de AT.js cliëntbibliotheek, of mbox.js (afgekeurd) wilt.
   * **Tagbeheersysteem gebruiken om clientbibliotheek te leveren**: Gebruik DTM (afgekeurd), Adobe Launch of een ander systeem voor tagbeheer.
   * **Aangepaste AT.js**: Laat leeg als u het vak Tagbeheer hebt ingeschakeld of als u de standaard-AT.js wilt gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

   >[!NOTE]
   >
   >[Configuratie van een Cloud Service om de Klassieke API van het Doel te gebruiken](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) is vervangen (gebruikt het tabblad Adobe Recommendations-instellingen).
1. Klikken **Verbinden met doel** om de verbinding met Adobe Target te initialiseren.

   Als de verbinding tot stand is gebracht, wordt het bericht **Verbinding gelukt** wordt weergegeven.

1. Selecteren **OK** op het bericht, gevolgd door **OK** in het dialoogvenster om de configuratie te bevestigen.
1. U kunt nu doorgaan naar [Een doelframework toevoegen](/help/sites-administering/target-configuring.md#adding-a-target-framework) om parameters te vormen ContextHub of ClientContext die naar Doel zullen worden verzonden. Dit is mogelijk niet vereist voor het exporteren AEM Experience Fragments naar Target.

### Aanbestedings-id en clientcode {#tenant-client}

Met [Adobe Experience Manager 6.5.8.0](/help/release-notes/release-notes.md), was het gebied van de Code van de Cliënt toegevoegd aan het de configuratievenster van het Doel.

Houd rekening met het volgende wanneer u de velden Tenant ID en Client Code configureert:

1. Voor de meeste klanten, zijn identiteitskaart van de Aannemer en de Code van de Cliënt het zelfde. Dit betekent dat beide velden dezelfde informatie bevatten en identiek zijn. Zorg ervoor dat u de id van de huurder in beide velden invoert.
2. Voor oudere doeleinden kunt u ook verschillende waarden invoeren in de velden Tenant ID en Client Code.

Houd er in beide gevallen rekening mee dat:

* Door gebrek, zal de Code van de Cliënt (als eerst toegevoegd) ook automatisch in het gebied van identiteitskaart van de Aannemer worden gekopieerd.
* U kunt de standaard huurder-id wijzigen.
* Dienovereenkomstig, zal de achterste vraag aan Doel op identiteitskaart van de Aannemer en de cliënt zijvraag aan Doel worden gebaseerd op de Code van de Cliënt.

Zoals eerder vermeld, is de eerste zaak de meest voorkomende voor AEM 6.5. Hoe dan ook, zorg ervoor **beide** de velden bevatten de juiste gegevens, afhankelijk van uw vereisten.

>[!NOTE]
>
> Als u een bestaande Configuratie van het Doel wilt veranderen:
>
> 1. Voer de huurder-id opnieuw in.
> 2. Maak opnieuw verbinding met Doel.
> 3. Sla de configuratie op.

