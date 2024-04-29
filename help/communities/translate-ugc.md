---
title: Door de gebruiker gegenereerde inhoud vertalen
description: Leer hoe bezoekers en leden van sites door de vertaling van UGC-inhoud een wereldwijde gemeenschap kunnen ervaren door taalbarrières te verwijderen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: ac54f06e-1545-44bb-9f8f-970f161ebb72
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 0%

---

# Door de gebruiker gegenereerde inhoud vertalen {#translating-user-generated-content}

Met de vertaalfunctie voor Adobe Experience Manager (AEM) Communities wordt het concept van [pagina-inhoud omzetten](../../help/sites-administering/translation.md) naar de door de gebruiker gegenereerde inhoud (UGC) die naar gemeenschapssites wordt gepost met [SCF-componenten (Social Component Framework)](scf.md).

De vertaling van UGC stelt bezoekers en leden van de site in staat een wereldwijde gemeenschap te ervaren door taalbarrières te verwijderen.

Stel bijvoorbeeld:

* Een Franse afgevaardigde plaatst een recept in het Frans op het communityforum van een multinationale kookwebsite.
* Een ander Japans lid gebruikt de vertaalfunctie om het recept van het Frans naar het Japans te vertalen.
* Na het lezen van het recept in het Japans heeft het Japanse lid een opmerking geplaatst in het Japans.
* Het Franse lid gebruikt de vertaalfunctie om de Japanse opmerking in het Frans te vertalen.
* Algemene communicatie.

## Overzicht {#overview}

Deze sectie bespreekt specifiek hoe de vertaaldienst met UGC werkt. Het veronderstelt ook dat u een inzicht in hebt hoe te om AEM met een [vertaalserviceprovider](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) en integreer die dienst in een website door te vormen [vertaalintegratiekader](../../help/sites-administering/tc-tic.md).

Wanneer een vertaaldienstverlener met de plaats wordt geassocieerd, handhaaft elke taalexemplaar van de plaats zijn eigen draden van UGC die door componenten SCF zoals commentaren wordt gepost.

Wanneer een vertaalintegratie naast de vertaaldienstverlener wordt gevormd, is het mogelijk voor elke taalexemplaar van de plaats om één enkele draad van UGC te delen, die globale mededeling over taalexemplaren verstrekt. In plaats van een besprekingsdraad die door taal wordt gescheiden, gevormd [algemene gedeelde opslag](#global-translation-of-ugc) laat de volledige draad toe om zichtbaar te zijn ongeacht van welke taal het wordt bekeken. Bovendien kunnen de veelvoudige configuraties van de vertaalintegratie worden gevormd specificerend verschillende globale gedeelde opslag voor een logische groepering van globale deelnemers, zoals door gebieden.

## De standaardvertaalservice {#the-default-translation-service}

AEM Communities bevat een [proeflicentie](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) voor een [standaardvertaalservice](../../help/sites-administering/tc-msconf.md) ingeschakeld voor meerdere talen.

Wanneer [het creëren van een communautaire plaats](sites-console.md), wordt de standaardvertaalservice ingeschakeld wanneer `Allow Machine Translation` wordt gecontroleerd door [VERTALING](sites-console.md#translation) subdeelvenster.

>[!CAUTION]
>
>De standaardvertaalservice is alleen bedoeld voor demonstratie.
>
>Voor een productiesysteem is een vertaaldienst met licentie vereist. Als er geen licentie wordt verleend, moet de standaardvertaalservice [uitgeschakeld](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license-geometrixx-outdoors).

## Wereldwijde omzetting van UGC {#global-translation-of-ugc}

Wanneer een website meerdere [taalkopieën](../../help/sites-administering/tc-prep.md), herkent de standaardvertaalservice niet dat UGC die op de ene site is ingevoerd, gerelateerd kan zijn aan UGC die op een andere site is ingevoerd. Dit is waar wanneer UGC door de zelfde component (het taalexemplaar van de pagina die de component bevat) wordt geproduceerd.

Het is vergelijkbaar met groepen mensen die een onderwerp bespreken. Zij zijn niet op de hoogte van opmerkingen die in andere groepen dan hun eigen groepen worden gemaakt, in vergelijking met iedereen in een grote groep die aan één gesprek deelneemt.

Als &quot;één groepsgesprek&quot;wordt gewenst, is het mogelijk om globale vertaling over een website met veelvoudige taalexemplaren toe te laten, zodat de volledige draad zichtbaar is ongeacht welke taalexemplaar het wordt bekeken.

Bijvoorbeeld, als een forum op de basisplaats werd gevestigd, gemaakte taalexemplaren, en globale vertaling werd toegelaten, zou een onderwerp dat aan het forum in één taalexemplaar wordt gemaakt in alle taalexemplaren verschijnen. Hetzelfde geldt voor alle antwoorden, ongeacht van welke taalkopie het antwoord is ingevuld. Het resultaat zou zijn dat het onderwerp en zijn volledige draad van antwoorden ongeacht van welke taalexemplaar het onderwerp wordt bekeken zichtbaar zijn.

>[!CAUTION]
>
>UGC&#39;s die vóór de algemene vertaling bestonden, zijn niet meer zichtbaar.
>
>Terwijl de UGC zich nog steeds in de [gemeenschappelijk archief](working-with-srp.md), wordt het gevestigd onder de taal-specifieke plaats UGC, terwijl de nieuwe inhoud, die na globale vertaling wordt toegevoegd, van de globale gedeelde opslagplaats wordt teruggewonnen.
>
>Er is geen migratiehulpmiddel om taalspecifieke inhoud in de globale gedeelde opslag te bewegen of samen te voegen.

### Configuratie vertaalintegratie {#translation-integration-configuration}

Om een Vertaalintegratie tot stand te brengen, die een schakelaar van de Vertaaldienst met de website op de auteursinstantie integreert:

* Aanmelden als beheerder
* Van de [hoofdmenu](http://localhost:4502/)
* Selecteren **[!UICONTROL Tools]**
* Selecteren **[!UICONTROL Operations]**
* Selecteren **[!UICONTROL Cloud]**
* Selecteren **[!UICONTROL Cloud Services]**
* Omlaag schuiven naar **[!UICONTROL Translation Integration]**

  ![vertaling-integratie](assets/translation-integration.png)

* Selecteren **[!UICONTROL Show Configurations]**

  ![show-configuration](assets/translation-integration1.png)

* Selecteren `[+]` pictogram naast **[!UICONTROL Available Configurations]** zodat kunt u een configuratie creëren.

#### Configuratiedialoogvenster maken {#create-configuration-dialog}

![create-configuration](assets/translation-integration2.png)

* **[!UICONTROL Parent Configuration]**

  (Vereist) Verlaat gewoonlijk als gebrek. Standaard is `/etc/cloudservices/translation`.

* **[!UICONTROL Title]**

  (Vereist) Voer de gewenste weergavetoewijzing in. Geen standaardwaarde.

* **[!UICONTROL Name]**

  (Optioneel) Voer een naam in voor de configuratie. De standaardwaarde is een knooppuntnaam die op de Titel wordt gebaseerd.

* Selecteren **[!UICONTROL Create]**

#### Dialoogvenster Config voor vertaling {#translation-config-dialog}

![configuratie-dialoogvenster](assets/translation-integration3.png)

Zie voor gedetailleerde instructies [Een configuratie voor vertaalintegratie maken](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration).

* **[!UICONTROL Sites]** tab: kan als standaardinstellingen worden ingesteld.

* **[!UICONTROL Communities]** tab:
   * **[!UICONTROL Translation Provider]**
Selecteer de vertaalprovider in de vervolgkeuzelijst. Standaard is `microsoft`, de testservice.

   * **[!UICONTROL Content Category]**
Selecteer een categorie die de inhoud beschrijft die wordt vertaald. Standaard is `General.`

   * **[!UICONTROL Choose A Locale...]**
(Optioneel) Door een landinstelling te selecteren voor het opslaan van UGC, verschijnen publicaties van alle taalkopieën in één algemeen gesprek. Kies bij conventie de landinstelling voor de [basistaal](sites-console.md#translation) voor de website. Kiezen `No Common Store` schakelt algemene vertaling uit. Globale vertaling is standaard uitgeschakeld.

* **[!UICONTROL Assets]** tab: kan als standaardinstellingen worden ingesteld.
* Selecteren **[!UICONTROL OK]**

#### Activering {#activation}

De nieuwe vertaalintegratie-cloudservice moet worden geactiveerd in de publicatieomgeving. Als de activeringsworkflow nog niet is geactiveerd en aan een website is gekoppeld, wordt gevraagd om deze cloudserviceconfiguratie te publiceren wanneer de pagina wordt gepubliceerd waaraan deze is gekoppeld.

## Vertaalinstellingen beheren {#managing-translation-settings}

>[!NOTE]
>
>**Voorkeurstaal**
>
>Wanneer wordt vastgesteld of de post zich in een andere taal dan de voorkeurstaal bevindt, moet de voorkeurstaal van de bezoeker van de site worden vastgesteld.
>
>De voorkeurstaal is de taalvoorkeur die is ingesteld in het profiel van de gebruiker, wanneer de bezoeker van de site is aangemeld en een taalvoorkeur heeft opgegeven.
>
>Wanneer de bezoeker van de site anoniem is of geen taalvoorkeur in hun profiel heeft gespecificeerd, is de aangewezen taal de basistaal van het paginasjabloon.

### Gebruikersvoorkeur {#user-preference}

#### Gebruikersprofiel {#user-profile}

Alle Communitysites bieden een gebruikersprofiel dat de ingelogde leden kunnen bewerken om zich aan de gemeenschap te identificeren en hun voorkeuren in te stellen.

Een van deze instellingen is of gemeenschapsinhoud altijd in de taal van uw voorkeur moet worden weergegeven. De instelling wordt standaard niet ingesteld en wordt standaard ingesteld op de systeeminstelling. De gebruiker kan de instelling in Aan of Uit wijzigen om de systeeminstelling te overschrijven.

Wanneer de pagina&#39;s automatisch in de aangewezen taal van de gebruiker worden vertaald, wordt UI voor het tonen van de originele tekst en het verbeteren van de vertaling nog ter beschikking gesteld.

![gebruikersprofiel](assets/translation-integration4.png)

### Site-instelling van community {#community-site-setting}

Wanneer een communautaire Plaats wordt gecreeerd, kan de vertaaloptie worden toegelaten en worden gevormd. De vertaalinstelling is van kracht voor inhoud die anonieme sitebezoekers kunnen bekijken, maar wordt overschreven door de profielinstelling van de gebruiker.
