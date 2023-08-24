---
title: Integratie met Adobe Target met IMS
description: Meer informatie over het integreren van AEM met Adobe Target met IMS
exl-id: 8ddd86d5-a5a9-4907-b07b-b6552d7afdc8
source-git-commit: 06ed2329840e151083bd238ee3a4d33663463c9c
workflow-type: tm+mt
source-wordcount: '1577'
ht-degree: 0%

---


# Integratie met Adobe Target met IMS{#integration-with-adobe-target-using-ims}

Voor de integratie van AEM met Adobe Target via de Target Standard API is de configuratie van Adobe IMS (Identity Management System) met behulp van de Adobe Developer Console vereist.

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

* [Ondersteuning voor Adobe](https://helpx.adobe.com/nl/contact/enterprise-support.ec.html) moet je account opgeven voor:

   * Adobe Console
   * Adobe Developer Console
   * Adobe Target en
   * Adobe IMS (Identity Management-systeem)

* Systeembeheerder van uw organisatie moet de Admin Console gebruiken om de vereiste ontwikkelaars in uw organisatie toe te voegen aan de relevante productprofielen.

   * Hierdoor beschikken de specifieke ontwikkelaars over machtigingen om integratie in de Adobe Developer-console mogelijk te maken.
   * Zie voor meer informatie [Ontwikkelaars beheren](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Een IMS-configuratie configureren - Een openbare sleutel genereren {#configuring-an-ims-configuration-generating-a-public-key}

De eerste fase van de configuratie is een Configuratie IMS in AEM te creëren en de Openbare Sleutel te produceren.

1. In AEM opent u de **Gereedschappen** -menu.
1. In de **Beveiliging** sectie selecteren **Adobe IMS-configuraties**.
1. Selecteren **Maken** om de **Configuratie technische account van Adobe IMS**.
1. De vervolgkeuzelijst onder gebruiken **Cloud Configuration**, selecteert u **Adobe Target**.
1. Activeren **Nieuw certificaat maken** en voert u een nieuwe alias in.
1. Bevestigen met **Certificaat maken**.

   ![wizard Technische accountconfiguratie van Adobe IMS](assets/integrate-target-io-01.png)

1. Selecteren **Downloaden** (of **Openbare sleutel downloaden**) om het bestand naar uw lokale station te downloaden, zodat het klaar is voor gebruik wanneer [IMS configureren voor Adobe Target-integratie met AEM](#configuring-ims-for-adobe-target-integration-with-aem).

   >[!CAUTION]
   >
   >Zorg dat deze configuratie geopend blijft, dat deze opnieuw nodig is wanneer [De IMS-configuratie voltooien in AEM](#completing-the-ims-configuration-in-aem).

   ![Informatiebericht om certificaat toe te voegen bij Adobe I/O](assets/integrate-target-io-02.png)

## IMS configureren voor Adobe Target-integratie met AEM {#configuring-ims-for-adobe-target-integration-with-aem}

Met de Adobe Developer-console moet u een project (integratie) maken met Adobe Target dat AEM gebruiken en vervolgens de vereiste rechten toewijzen.

### Het project maken {#creating-the-project}

Open de Adobe Developer-console om een project te maken met Adobe Target dat AEM gebruiken:

>[!CAUTION]
>
>Momenteel ondersteunen we alleen de **Serviceaccount (JWT)** referentietype.
>
>Gebruik de **OAuth Server-to-Server** type referentie, dat in de toekomst zal worden gesteund.

1. Open de Adobe Developer-console voor projecten:

   [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

1. Alle projecten die u hebt, worden weergegeven. Selecteren **Nieuw project maken** - de locatie en het gebruik zijn afhankelijk van:

   * Als u nog geen project hebt, **Nieuw project maken** wordt midden onderaan weergegeven.
     ![Nieuw project maken - eerste project](assets/integration-target-io-02.png)
   * Als u al bestaande projecten hebt, worden deze weergegeven en **Nieuw project maken** is helemaal rechts.
     ![Nieuw project maken - Meerdere projecten](assets/integration-target-io-03.png)


1. Selecteren **Toevoegen aan project** gevolgd door **API**:

   ![Adobe Developer Console](assets/integration-target-io-10.png)

1. Selecteren **Adobe Target** vervolgens **Volgende**:

   >[!NOTE]
   >
   >Als je bent geabonneerd op Adobe Target, maar deze niet ziet, moet je de knop [Vereisten](#prerequisites).

   ![Klik op Volgende](assets/integration-target-io-12.png)

1. **Uw openbare sleutel uploaden** en, indien voltooid, doorgaan met **Volgende**:

   ![Integraties toevoegen met Developer Console](assets/integration-target-io-13.png)

1. Controleer de referenties en ga verder met **Volgende**:

   ![Een nieuw project maken](assets/integration-target-io-15.png)

1. Selecteer de vereiste productprofielen en ga verder met **geconfigureerde API opslaan**:

   >[!NOTE]
   >
   >De productprofielen die worden weergegeven met, zijn afhankelijk van het volgende:
   >
   >* Adobe Target Standard - alleen **Standaardwerkruimte** is beschikbaar
   >* Adobe Target Premium - alle beschikbare werkruimten worden weergegeven, zoals hieronder wordt weergegeven

   ![Een API selecteren om toe te voegen](assets/integration-target-io-16.png)

1. De oprichting zal worden bevestigd.

<!--
1. The creation will be confirmed, you can now **Continue to integration details**; these are needed for [Completing the IMS Configuration in AEM](#completing-the-ims-configuration-in-aem).

   ![integrate-target-io-07](assets/integrate-target-io-07.png)
-->

### Rechten toewijzen aan de integratie {#assigning-privileges-to-the-integration}

U moet nu de vereiste rechten toewijzen aan de integratie:

1. De Adobe openen **Admin Console**:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigeren naar **Producten** (bovenste werkbalk) selecteert u vervolgens **ADOBE TARGET - &lt;*uw huurder*>** (in het linkerdeelvenster).
1. Selecteren **Productprofielen**, dan uw vereiste werkruimte uit de gepresenteerde lijst. Bijvoorbeeld de standaardwerkruimte.
1. Selecteren **API-referenties**, dan de vereiste integratieconfiguratie.
1. Selecteren **Editor** als de **Productrol**; in plaats van **Waarnemer**.

## Gegevens opgeslagen voor het Adobe Developer Console Integration Project {#details-stored-for-the-ims-integration-project}

Vanuit de Adobe Developer Console - Projecten kunt u een lijst met al uw integratieprojecten zien:

* [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

Selecteren **Weergave** (rechts van een specifieke projectvermelding) om verdere details over de configuratie te tonen. Deze omvatten:

* Overzicht van project
* Inzichten
* Credentials
   * Serviceaccount (JWT)
      * Referentiegegevens
      * JWT genereren
* APIS
   * Bijvoorbeeld Adobe Target

Bij sommige hiervan moet u de integratie van Adobe Target in AEM op basis van IMS voltooien.

## De IMS-configuratie voltooien in AEM {#completing-the-ims-configuration-in-aem}

Als u terugkeert naar AEM kunt u de IMS-configuratie voltooien door de vereiste waarden van de integratie van de Adobe Developer-console voor Target toe te voegen:

1. Terugkeren naar de [IMS-configuratie geopend in AEM](#configuring-an-ims-configuration-generating-a-public-key).
1. Selecteren **Volgende**.

1. Hier kunt u de [details van de projectconfiguratie in de Adobe Developer Console](#details-stored-for-the-ims-integration-project):

   * **Titel**: Uw tekst.
   * **Autorisatieserver**: Kopieer/plak deze vanuit de `aud` lijn van de **Payload** hieronder, bijvoorbeeld `https://ims-na1.adobelogin.com` in het onderstaande voorbeeld
   * **API-sleutel**: Kopieer deze van de [Overzicht](#details-stored-for-the-ims-integration-project) sectie
   * **Clientgeheim**: Genereer dit in het dialoogvenster [Overzicht](#details-stored-for-the-ims-integration-project) en kopiëren
   * **Payload**: Kopieer deze van de [JWT genereren](#details-stored-for-the-ims-integration-project) sectie

   ![Configuratie van technische account](assets/integrate-target-io-10.png)

1. Bevestigen met **Maken**.

1. Uw Adobe Target-configuratie wordt weergegeven in de AEM console.

   ![Configuratie technische account van Adobe IMS](assets/integrate-target-io-11.png)

## De IMS-configuratie bevestigen {#confirming-the-ims-configuration}

Om te bevestigen dat de configuratie zoals verwacht werkt:

1. Open:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Bijvoorbeeld:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`

1. Selecteer uw configuratie.
1. Selecteren **Health controleren** van de werkbalk, gevolgd door **Controleren**.

   ![Adobe IMS-configuraties](assets/integrate-target-io-12.png)

1. Als dit lukt, wordt het bericht weergegeven:

   ![Een configuratie controleren](assets/integrate-target-io-13.png)

## De Adobe Target-Cloud Service configureren {#configuring-the-adobe-target-cloud-service}

Er kan nu naar de configuratie worden verwezen, zodat een Cloud Service de standaard-API van het doel kan gebruiken:

1. Open de **Gereedschappen** -menu. Dan, binnen **Cloud Servicen** sectie, selecteert u **Oudere Cloud Servicen**.
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

   * **IMS-configuratie**: selecteer de naam van de IMS-configuratie

   * **API-type**: REST

   * **A4T Analytics Cloud-configuratie**: Selecteer de cloudconfiguratie Analytics die wordt gebruikt voor doelen en maateenheden voor doelactiviteit. Dit is nodig als u Adobe Analytics als rapportagebron gebruikt wanneer u inhoud als doel instelt. Als u de cloudconfiguratie niet ziet, raadpleegt u de opmerking in [A4T Analytics Cloud-configuratie configureren](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration).

   * **Nauwkeurige doelgerichtheid gebruiken**: Standaard is dit selectievakje ingeschakeld. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.

   * **Segmenten synchroniseren vanuit Adobe Target**: Selecteer deze optie om segmenten te downloaden die in Doel zijn gedefinieerd om deze in AEM te gebruiken. U moet deze optie selecteren wanneer het bezit van het Type API REST is, omdat de gealigneerde segmenten niet worden gesteund en u altijd segmenten van Doel moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)

   * **Clientbibliotheek**: Selecteer of u de AT.js-clientbibliotheek of mbox.js (afgekeurd) wilt.

   * **Tag Management System gebruiken om clientbibliotheek te leveren**: Gebruik DTM (afgekeurd), Adobe Launch of een ander systeem voor tagbeheer.

   * **Aangepaste AT.js**: Laat leeg als u het vak Tag Management hebt ingeschakeld of als u de standaard-AT.js wilt gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

   >[!NOTE]
   >
   >[Configuratie van een Cloud Service om de Klassieke API van het Doel te gebruiken](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) is vervangen (gebruikt het tabblad Adobe Recommendations-instellingen).

1. Klikken **Verbinden met doel** de verbinding met Adobe Target initialiseren.

   Als de verbinding tot stand is gebracht, wordt het bericht **Verbinding gelukt** wordt weergegeven.

1. Selecteren **OK** op het bericht, gevolgd door **OK** in het dialoogvenster om de configuratie te bevestigen.

1. U kunt nu doorgaan naar [Een doelframework toevoegen](/help/sites-administering/target-configuring.md#adding-a-target-framework) om parameters te vormen ContextHub of van de ClientContext die naar Doel zullen worden verzonden. Dit is mogelijk niet vereist voor het exporteren AEM Experience Fragments naar Target.

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
>Als u een bestaande Configuratie van het Doel wilt veranderen:
>
>1. Voer de huurder-id opnieuw in.
>2. Maak opnieuw verbinding met Doel.
>3. Sla de configuratie op.
