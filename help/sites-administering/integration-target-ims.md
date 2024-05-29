---
title: Integratie met Adobe Target met IMS
description: Leer hoe u AEM met Adobe Target integreert met IMS.
exl-id: 8ddd86d5-a5a9-4907-b07b-b6552d7afdc8
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
hide: true
hidefromtoc: true
index: false
source-git-commit: 3ccf41ed2c413171ea55a63e969e72e18c189fb7
workflow-type: tm+mt
source-wordcount: '1533'
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

* [Ondersteuning voor Adobe](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support) moet je account opgeven voor:

   * Adobe Console
   * Adobe Developer Console
   * Adobe Target en
   * Adobe IMS (Identity Management-systeem)

* De systeembeheerder van het Systeem van uw organisatie zou de Admin Console moeten gebruiken om de vereiste ontwikkelaars in uw organisatie aan de relevante productprofielen toe te voegen.

   * Hierdoor beschikken de specifieke ontwikkelaars over machtigingen om integratie in de Adobe Developer-console mogelijk te maken.
   * Zie [Ontwikkelaars beheren](https://helpx.adobe.com/enterprise/using/manage-developers.html).


## Een IMS-configuratie configureren - Een openbare sleutel genereren {#configuring-an-ims-configuration-generating-a-public-key}

De eerste fase van de configuratie is een Configuratie IMS in AEM te creëren en de Openbare Sleutel te produceren.

1. In AEM opent u de **Gereedschappen** -menu.
1. In de **Beveiliging** sectie, selecteert u **Adobe IMS-configuraties**.
1. Selecteren **Maken** om de **Configuratie technische account van Adobe IMS**.
1. De vervolgkeuzelijst onder gebruiken **Cloud Configuration**, selecteert u **Adobe Target**.
1. Activeren **Nieuw certificaat maken** en voert u een nieuwe alias in.
1. Bevestigen met **Certificaat maken**.

   ![wizard Technische accountconfiguratie van Adobe IMS](assets/integrate-target-io-01.png)

1. Selecteren **Downloaden** (of **Openbare sleutel downloaden**) om het bestand naar uw lokale station te downloaden, zodat het klaar is voor gebruik wanneer [IMS configureren voor Adobe Target-integratie met AEM](#configuring-ims-for-adobe-target-integration-with-aem).

   >[!CAUTION]
   >
   >Houd deze configuratie open; deze is opnieuw nodig wanneer [De IMS-configuratie voltooien in AEM](#completing-the-ims-configuration-in-aem).

   ![Informatiebericht om certificaat toe te voegen bij Adobe I/O](assets/integrate-target-io-02.png)

## IMS configureren voor Adobe Target-integratie met AEM {#configuring-ims-for-adobe-target-integration-with-aem}

Maak met de Adobe Developer-console een project (integratie) met Adobe Target dat AEM kan gebruiken en wijs vervolgens de vereiste rechten toe.

### Het project maken {#creating-the-project}

Open de Adobe Developer-console om een project te maken met Adobe Target dat AEM kan gebruiken:

>[!CAUTION]
>
>Adobe biedt momenteel alleen ondersteuning voor de Adobe Developer Console **Serviceaccount (JWT)** referentietype.
>
>Gebruik de **OAuth Server-to-Server** type referentie, dat in de toekomst zal worden gesteund.

1. Open de Adobe Developer-console voor projecten:

   [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

1. Alle projecten die u hebt, worden weergegeven. Selecteren **Nieuw project maken** - de locatie en het gebruik zijn afhankelijk van het volgende:

   * Als u nog geen project hebt, **Nieuw project maken** is gecentreerd, onder.
     ![Nieuw project maken - eerste project](assets/integration-target-io-02.png)
   * Als u reeds bestaande projecten hebt, zijn deze vermeld en **Nieuw project maken** bevindt zich rechtsboven.
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

   ![Een project maken](assets/integration-target-io-15.png)

1. Selecteer de vereiste productprofielen en ga verder met **geconfigureerde API opslaan**:

   >[!NOTE]
   >
   >De productprofielen die worden weergegeven met, zijn afhankelijk van het volgende:
   >
   >* Adobe Target Standard - alleen **Standaardwerkruimte** is beschikbaar
   >* Adobe Target Premium - alle beschikbare werkruimten worden weergegeven, zoals hieronder wordt weergegeven

   ![Een API selecteren om toe te voegen](assets/integration-target-io-16.png)

1. De oprichting wordt bevestigd.

<!--
1. The creation is confirmed, you can now **Continue to integration details**; these are needed for [Completing the IMS Configuration in AEM](#completing-the-ims-configuration-in-aem).

   ![integrate-target-io-07](assets/integrate-target-io-07.png)
-->

### Rechten toewijzen aan de integratie {#assigning-privileges-to-the-integration}

Wijs nu de vereiste rechten toe aan de integratie:

1. De Adobe openen **Admin Console**:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigeren naar **Producten** (bovenste werkbalk) selecteert u vervolgens **ADOBE TARGET - &lt;*uw huurder*>** (in het linkerdeelvenster).
1. Selecteren **Productprofielen**, dan uw vereiste werkruimte uit de gepresenteerde lijst. Bijvoorbeeld de standaardwerkruimte.
1. Selecteren **API-referenties**, dan de vereiste integratieconfiguratie.
1. Selecteren **Editor** als de **Productrol**; in plaats van **Waarnemer**.

## Gegevens opgeslagen voor het Adobe Developer Console Integration Project {#details-stored-for-the-ims-integration-project}

Vanuit de Adobe Developer Console - Projecten kunt u een lijst met al uw integratieprojecten zien:

* [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

Om verdere details over de configuratie te tonen, selecteer **Weergave** (rechts van een specifieke projectvermelding). Deze omvatten:

* Overzicht van project
* Inzichten
* Credentials
   * Serviceaccount (JWT)
      * Referentiegegevens
      * JWT genereren
* APIS
   * Bijvoorbeeld Adobe Target

Sommige hiervan moeten de integratie van Adobe Target in AEM op basis van IMS voltooien.

## De IMS-configuratie voltooien in AEM {#completing-the-ims-configuration-in-aem}

Als u terugkeert naar AEM, kunt u de IMS-configuratie voltooien door de vereiste waarden van de Adobe Developer Console-integratie voor Doel toe te voegen:

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

1. Openen:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Bijvoorbeeld:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`

1. Selecteer uw configuratie.
1. Selecteren **Health controleren** van de werkbalk, gevolgd door **Controleren**.

   ![Adobe IMS-configuraties](assets/integrate-target-io-12.png)

1. Als dit gelukt is, ziet u het bericht:

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
     >Voor IMS, moet deze waarde van Doel zelf worden genomen. U kunt zich aanmelden bij Target en de Tenant-id uit de URL extraheren.
     >
     >Als de URL bijvoorbeeld:
     >
     >`https://experience.adobe.com/#/@yourtenantid/target/activities`
     >
     >Vervolgens gebruikt u `yourtenantid`.

   * **Clientcode**: Zie de [Aanbestedings-id en clientcode](#tenant-client) sectie.

   * **IMS-configuratie**: selecteer de naam van de IMS-configuratie

   * **API-type**: REST

   * **A4T Analytics Cloud-configuratie**: Selecteer de configuratie van Analytics Cloud die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. Dit is nodig als u Adobe Analytics als rapportagebron gebruikt wanneer u inhoud als doel instelt. Zie de opmerking in [A4T Analytics Cloud-configuratie configureren](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration).

   * **Nauwkeurige doelgerichtheid gebruiken**: Standaard is dit selectievakje ingeschakeld. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.

   * **Segmenten synchroniseren vanuit Adobe Target**: Selecteer deze optie zodat u segmenten die in Doel zijn gedefinieerd, kunt downloaden en in AEM kunt gebruiken. Selecteer deze optie als de eigenschap API Type REST is, omdat inline-segmenten niet worden ondersteund en u altijd segmenten van Target moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)

   * **Clientbibliotheek**: Selecteer of u de AT.js-clientbibliotheek of mbox.js (afgekeurd) wilt.

   * **Tag Management System gebruiken om clientbibliotheek te leveren**: Gebruik DTM (afgekeurd), Adobe Launch of een ander tagbeheersysteem.

   * **Aangepaste AT.js**: Laat leeg als u het vak Tag Management hebt ingeschakeld of als u de standaard-AT.js wilt gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

   >[!NOTE]
   >
   >[Configuratie van een Cloud Service om de Klassieke API van het Doel te gebruiken](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) is vervangen (gebruikt het tabblad Adobe Recommendations-instellingen).

1. Klikken **Verbinden met doel** de verbinding met Adobe Target initialiseren.

   Als de verbinding tot stand is gebracht, wordt het bericht **Verbinding gelukt** wordt weergegeven.

1. Selecteren **OK** op het bericht, gevolgd door **OK** op de dialoogdoos zodat kunt u de configuratie bevestigen.

1. U kunt nu doorgaan naar [Een doelframework toevoegen](/help/sites-administering/target-configuring.md#adding-a-target-framework) om parameters te vormen ContextHub of van de ClientContext die naar Doel worden verzonden. Dit is mogelijk niet vereist voor het exporteren AEM Experience Fragments naar Target.

### Aanbestedings-id en clientcode {#tenant-client}

Met [Adobe Experience Manager 6.5.8.0](/help/release-notes/release-notes.md), was het gebied van de Code van de Cliënt toegevoegd aan het de configuratievenster van het Doel.

Houd rekening met het volgende wanneer u de velden Tenant ID en Client Code configureert:

1. Voor de meeste klanten, zijn identiteitskaart van de Aannemer en de Code van de Cliënt het zelfde. Dit betekent dat beide velden dezelfde informatie bevatten en identiek zijn. Zorg ervoor dat u de id van de huurder in beide velden invoert.
2. Voor oudere doeleinden kunt u ook verschillende waarden invoeren in de velden Tenant ID en Client Code.

Houd in beide gevallen rekening met het volgende:

* Door gebrek, wordt de Code van de Cliënt (als eerst toegevoegd) ook automatisch gekopieerd in het gebied van identiteitskaart van de Aannemer.
* U kunt naar keuze de standaardIdentiteitskaart veranderen van de Haan.
* Zo, zijn de achterste vraag aan Doel gebaseerd op identiteitskaart van de Aannemer en de cliënt zijvraag aan Doel is gebaseerd op de Code van de Cliënt.

Zoals eerder vermeld, is de eerste zaak de meest voorkomende voor AEM 6.5. Zorg ervoor dat **beide** de velden bevatten de juiste gegevens, afhankelijk van uw vereisten.

>[!NOTE]
>
>Als u een bestaande Configuratie van het Doel wilt veranderen:
>
>1. Voer de huurder-id opnieuw in.
>2. Maak opnieuw verbinding met Doel.
>3. Sla de configuratie op.
