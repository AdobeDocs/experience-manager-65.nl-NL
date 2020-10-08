---
title: Door gebruiker gegenereerde inhoud vertalen
seo-title: Door gebruiker gegenereerde inhoud vertalen
description: De werking van de vertaalfunctie
seo-description: De werking van de vertaalfunctie
uuid: 7ee3242c-2aca-4787-a60d-b807161401ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: bfaf80c5-448b-47fb-9f22-57ee0eb169b2
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 0%

---


# Door gebruiker gegenereerde inhoud vertalen {#translating-user-generated-content}

De vertaalfunctie voor AEM Communities breidt het concept van het [vertalen van pagina-inhoud](../../help/sites-administering/translation.md) uit naar door de gebruiker gegenereerde inhoud (UGC) die via SCF-componenten [(](scf.md)social component framework) naar sites van de gemeenschap wordt gepost.

De vertaling van UGC stelt bezoekers en leden van de site in staat een wereldwijde gemeenschap te ervaren door taalbarrières te verwijderen.

Stel bijvoorbeeld:

* Een Franse afgevaardigde plaatst een recept in het Frans op het communautair forum van een multinationale kookwebsite.
* Een ander Japans lid gebruikt de vertaalfunctie om het recept van het Frans naar het Japans te vertalen.
* Na het lezen van het recept in het Japans heeft het Japanse lid een opmerking geplaatst in het Japans.
* Het Franse lid gebruikt de vertaalfunctie om de Japanse opmerking in het Frans te vertalen.
* Wereldwijde communicatie.

## Overzicht {#overview}

In deze sectie van de documentatie wordt specifiek besproken hoe de vertaalservice met UGC werkt, waarbij wordt uitgegaan van een inzicht in de manier waarop u AEM kunt verbinden met een [vertaalserviceprovider](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) en deze service kunt integreren in een website door een [vertaalintegratieframework](../../help/sites-administering/tc-tic.md)te configureren.

Wanneer een vertaaldienstverlener met de plaats wordt geassocieerd, handhaaft elke taalexemplaar van de plaats zijn eigen draden van UGC die door componenten SCF zoals commentaren wordt gepost.

Wanneer een kader van de vertaalintegratie naast de vertaaldienstverlener wordt gevormd, is het mogelijk voor elke taalexemplaar van de plaats om één enkele draad van UGC te delen, waarbij globale mededeling over taalexemplaren wordt verstrekt. In plaats van een besprekingsdraad die door taal wordt gescheiden, laat de gevormde [globale gedeelde opslag](#global-translation-of-ugc) toe dat de volledige draad zichtbaar is ongeacht van welke taalexemplaar het wordt bekeken. Bovendien kunnen de veelvoudige configuraties van de vertaalintegratie worden gevormd specificerend verschillende globale gedeelde opslag voor een logische groepering van globale deelnemers, zoals door gebieden.

## De standaardvertaalservice {#the-default-translation-service}

AEM Communities wordt geleverd met een [proeflicentie](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) voor een [standaardvertaalservice](../../help/sites-administering/tc-msconf.md) die is ingeschakeld voor verschillende talen.

Wanneer u een communitysite [](sites-console.md)maakt, wordt de standaardvertaalservice ingeschakeld wanneer deze `Allow Machine Translation` wordt gecontroleerd vanuit het subdeelvenster [TRANSLATION](sites-console.md#translation) .

>[!CAUTION]
>
>De standaardvertaalservice is alleen bedoeld voor demonstratie.
>
>Voor een productiesysteem is een vertaaldienst met licentie vereist. Als er geen licentie is, moet de standaardvertaalservice worden [uitgeschakeld](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license-geometrixx-outdoors).

## Wereldwijde omzetting van UGC {#global-translation-of-ugc}

Wanneer een website meerdere [taalkopieën](../../help/sites-administering/tc-prep.md)heeft, herkent de standaardvertaalservice niet dat UGC die op de ene site is ingevoerd, gerelateerd kan zijn aan UGC die op een andere site is ingevoerd, zoals wanneer de UGC in feite door dezelfde component wordt gegenereerd (de taalkopie van de pagina die de component bevat).

Het is vergelijkbaar met groepen mensen die een onderwerp bespreken dat niet op de hoogte is van opmerkingen die in andere groepen dan hun eigen groepen worden gemaakt, in vergelijking met iedereen in één grote groep die aan één gesprek deelneemt.

Als &quot;één groepsgesprek&quot;wordt gewenst, is het mogelijk om globale vertaling over een website met veelvoudige taalexemplaren toe te laten, zodat de volledige draad zichtbaar is ongeacht welke taalexemplaar het wordt bekeken.

Bijvoorbeeld, als een forum op de basisplaats werd gevestigd, gemaakte taalexemplaren, en globale vertaling werd toegelaten, dan zou een onderwerp dat aan het forum in één taalexemplaar wordt gemaakt in alle taalexemplaren verschijnen. Hetzelfde geldt voor alle antwoorden, ongeacht van welke taalkopie het antwoord is ingevuld. Het resultaat zou zijn dat het onderwerp en zijn volledige draad van antwoorden ongeacht van welke taalexemplaar het onderwerp wordt bekeken zichtbaar zijn.

>[!CAUTION]
>
>UGC&#39;s die vóór de algemene vertaling bestonden, zijn niet meer zichtbaar.
>
>Terwijl UGC nog in de [gemeenschappelijke opslag](working-with-srp.md)is, wordt het gevestigd onder de taal-specifieke plaats UGC, terwijl de nieuwe inhoud, die na globale vertaling werd toegevoegd, van de globale gedeelde opslagplaats wordt teruggewonnen.
>
>Er is geen migratiehulpmiddel om taalspecifieke inhoud in de globale gedeelde opslag te bewegen of samen te voegen.

### Configuratie vertaalintegratie {#translation-integration-configuration}

Om een nieuwe Vertaalintegratie tot stand te brengen, die een schakelaar van de Vertaaldienst met de website op de auteursinstantie integreert:

* Aanmelden als beheerder
* Vanuit het [hoofdmenu](http://localhost:4502/)
* Selecteer **[!UICONTROL Tools]**
* Selecteer **[!UICONTROL Operations]**
* Selecteer **[!UICONTROL Cloud]**
* Selecteer **[!UICONTROL Cloud Services]**
* Omlaag schuiven naar **[!UICONTROL Translation Integration]**

   ![vertaling-integratie](assets/translation-integration.png)

* Selecteer **[!UICONTROL Show Configurations]**

   ![show-configuration](assets/translation-integration1.png)

* Selecteer `[+]` pictogram naast **[!UICONTROL Available Configurations]** om een nieuwe configuratie tot stand te brengen

#### Configuratiedialoogvenster maken {#create-configuration-dialog}

![create-configuration](assets/translation-integration2.png)

* **[!UICONTROL Parent Configuration]**

   (Vereist) Verlaat gewoonlijk als gebrek. Standaard is dit `/etc/cloudservices/translation`.

* **[!UICONTROL Title]**

   (Vereist) Voer de gewenste weergavetoewijzing in. Geen standaardwaarde.

* **[!UICONTROL Name]**

   (Optioneel) Voer een naam in voor de configuratie. De standaardwaarde is een knooppuntnaam die op de Titel wordt gebaseerd.

* Selecteer **[!UICONTROL Create]**

#### Dialoogvenster Config voor vertaling {#translation-config-dialog}

![configuratie-dialoogvenster](assets/translation-integration3.png)

Voor gedetailleerde instructies gaat u naar [Een configuratie voor vertaalintegratie maken](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration)

* **[!UICONTROL Sites]** tab: kan als standaardinstellingen worden verlaten.

* **[!UICONTROL Communities]** tab:
   * **[!UICONTROL Translation Provider]**
Selecteer de vertaalprovider in de vervolgkeuzelijst. Standaard is 
`microsoft`, de testservice.

   * **[!UICONTROL Content Category]**
Selecteer een categorie die de inhoud beschrijft die wordt vertaald. Standaard is 
`General.`

   * **[!UICONTROL Choose A Locale...]**
(Optioneel) Als u een landinstelling selecteert voor het opslaan van UGC, worden posts van alle taalkopieën in één algemeen gesprek weergegeven. Kies bij conventie de landinstelling voor de [basistaal](sites-console.md#translation) voor de website. Als u `No Common Store` kiest, wordt algemene vertaling uitgeschakeld. Globale vertaling is standaard uitgeschakeld.

* **[!UICONTROL Assets]** tab: kan als standaardinstellingen worden verlaten.
* Selecteer **[!UICONTROL OK]**

#### Activering {#activation}

De nieuwe vertaalintegratie-cloudservice moet worden geactiveerd voor de publicatieomgeving. Als de activeringsworkflow nog niet is geactiveerd en aan een website is gekoppeld, wordt gevraagd om deze cloudserviceconfiguratie te publiceren wanneer de pagina wordt gepubliceerd waaraan deze is gekoppeld.

## Vertaalinstellingen beheren {#managing-translation-settings}

>[!NOTE]
>
>**Voorkeurstaal**
>
>Om na te gaan of de post zich in een andere taal dan de voorkeurstaal bevindt, moet de voorkeurstaal van de bezoeker worden vastgesteld.
>
>De voorkeurstaal is de taalvoorkeur die is ingesteld in het profiel van de gebruiker, wanneer de bezoeker van de site is aangemeld en een taalvoorkeur heeft opgegeven.
>
>Wanneer de bezoeker van de site anoniem is of geen taalvoorkeur in hun profiel heeft gespecificeerd, is de aangewezen taal de basistaal van het paginasjabloon.

### Gebruikersvoorkeur {#user-preference}

#### Gebruikersprofiel {#user-profile}

Alle Communitysites bieden een gebruikersprofiel dat de ondertekenaars kunnen bewerken om zich te identificeren voor de community en hun voorkeuren in te stellen.

Een van deze instellingen is of gemeenschapsinhoud altijd in de taal van uw voorkeur moet worden weergegeven. De instelling is standaard niet ingesteld en wordt standaard ingesteld op de systeeminstelling. De gebruiker kan de instelling wijzigen in Aan of Uit en zo de systeeminstelling overschrijven.

Wanneer de pagina&#39;s automatisch in de aangewezen taal van de gebruiker worden vertaald, wordt UI voor het tonen van de originele tekst en het verbeteren van de vertaling nog ter beschikking gesteld.

![gebruikersprofiel](assets/translation-integration4.png)

### Site-instelling van community {#community-site-setting}

Wanneer een communautaire Plaats wordt gecreeerd, kan de vertaaloptie worden toegelaten en worden gevormd. De vertaalinstelling is van kracht voor inhoud die anonieme sitebezoekers kunnen bekijken, maar wordt overschreven door de profielinstelling van de gebruiker.
