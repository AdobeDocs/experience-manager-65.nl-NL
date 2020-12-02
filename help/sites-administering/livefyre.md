---
title: Integreren met Livefyre
seo-title: Integreren met Livefyre
description: Leer hoe u de toonaangevende curatiemogelijkheden van Livefy met uw AEM 6.5-exemplaar kunt integreren, zodat u in enkele minuten waardevolle door gebruikers gegenereerde inhoud (UGC) kunt publiceren van sociale netwerken naar uw site.
seo-description: Leer hoe u Livefyre integreert en gebruikt met AEM 6.5.
uuid: c355705d-6e0f-4a33-aa1f-d2d1c818aac0
contentOwner: ind14750
content-type: reference
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: bb3fcb53-b8c3-4b1d-9125-4715f34ceb0b
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 3%

---


# Integreren met Livefyre{#integrating-with-livefyre}

Leer hoe u de toonaangevende curatiemogelijkheden van Livefy met uw AEM 6.5-exemplaar kunt integreren, zodat u in enkele minuten waardevolle door gebruikers gegenereerde inhoud (UGC) kunt publiceren van sociale netwerken naar uw site.

## Aan de slag {#getting-started}

### Livefyre-pakket installeren voor AEM {#install-livefyre-package-for-aem}

AEM 6.5 wordt geleverd met het Livefyre-functiepakket 1.2.6 vooraf geïnstalleerd. Dit pakket bevat alleen beperkte Livefyre-integratie met AEM Sites en moet worden verwijderd voordat een bijgewerkt pakket kan worden geïnstalleerd. Met het nieuwste pakket kunt u de volledige integratie van Livefyre met AEM ervaren, waaronder Sites, Assets en Commerce.

>[!NOTE]
>
>Sommige eigenschappen van het AEM-LF pakket hangen van Sociaal Kader (SCF) af. Als u het functiepakket Livefyre gebruikt als onderdeel van een site zonder gemeenschappen, moet u *cq.social.scf* declareren als afhankelijkheid van de clientlibs van de auteur van de website. Als u het LF eigenschappak als deel van een communautaire website gebruikt, zou deze gebiedsdeel reeds moeten worden verklaard.

1. Klik op de AEM startpagina op het pictogram **Tools** op de linkertrack.
1. Navigeer naar **Implementatie > Pakketten**.
1. Blader in Package Manager totdat u het vooraf geïnstalleerde Livefyre-functiepakket ziet en klik op de pakkettitel **cq-social-livefyre-pkg-1.2.6.zip** om de opties uit te vouwen.
1. Klik op **Meer > Verwijderen**.

   ![livefyre-aem-uninstall-64](assets/livefyre-aem-uninstall-64.png)

1. Download LiveCycle-pakket van [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

1. Installeer het gedownloade pakket via Package Manager. Zie [Werken met pakketten](/help/sites-administering/package-manager.md) voor meer informatie over het gebruik van softwaredistributie en -pakketten in AEM

   ![livefyre-aem4-6-4](assets/livefyre-aem4-6-4.png)

   Uw Livefyre-AEM-pakket is nu geïnstalleerd. Voordat u de integratiefuncties kunt gaan gebruiken, moet u AEM configureren om Livefyre te gebruiken.

   Zie [Feature Packs](https://helpx.adobe.com/experience-manager/6-3/release-notes/feature-packs-release-notes.html) voor meer informatie en opmerkingen bij de release.

### Configureer AEM voor gebruik van Livefyre: Een configuratiemap {#configure-aem-to-use-livefyre-create-a-configuration-folder} maken

1. Klik op de AEM startpagina op het pictogram **Tools** in de linkertrack en navigeer vervolgens naar **Algemeen > Configuratiebrowser**.
   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Klik **Maken** om het dialoogvenster Configuratie maken te openen.
1. Geef uw configuratie een naam en schakel het selectievakje **Cloud Configurations** in.

   Hiermee wordt een map gemaakt onder **Extra > Implementatie > LiveCycle Configuration** met de opgegeven naam.

   ![livefyre-aem-create-config-folder](assets/livefyre-aem-create-config-folder.png)

### Configureer AEM voor gebruik van Livefyre: Een LiveCycle-configuratie maken {#configure-aem-to-use-livefyre-create-a-livefyre-configuration}

Configureer AEM om de LiveCyre-licentiereferenties van uw organisatie te gebruiken, zodat communicatie tussen Livefyre en AEM mogelijk is.

1. Klik op de AEM startpagina op het pictogram **Tools** in de linkertrack en navigeer vervolgens naar **Implementatie > LiveCycle Configuration**.
1. Selecteer de configuratiemap waarin u een nieuwe configuratie van de Levensstijl wilt tot stand brengen, dan klik **Create**.

   ![create-livefyre-configuration1](assets/create-livefyre-configuration1.png)

   >[!NOTE]
   >
   >Mappen moeten de eigenschappen van Cloud Configurations hebben ingeschakeld voordat LiveCycle-configuraties eraan kunnen worden toegevoegd. De omslagen van de configuratie worden gecreeerd en worden beheerd in [Browser van de Configuratie.](/help/sites-administering/configurations.md)
   >
   >U kunt geen naam voor een configuratie-het wordt van verwijzingen voorzien door de weg van de omslag het binnen is. U kunt slechts één configuratie per map hebben.

1. Selecteer de nieuwe Livefy-configuratiekaart en klik op **Eigenschappen**.

   ![create-livefyre-configuration2](assets/create-livefyre-configuration2.png)

1. Voer de Livefyre-gegevens van uw organisatie in en klik op **OK**.

   ![configure-aem2](assets/configure-aem2.png)

   Als u deze informatie wilt openen, opent u de Livefyre-studio en navigeert u naar **Instellingen > Integratie-instellingen > Referenties**.

   Uw AEM-instantie is nu geconfigureerd voor gebruik van LiveCycle en u kunt de integratiefuncties gebruiken.

### Single Sign-on integratie aanpassen {#customize-single-sign-on-integration}

Het Livefyre voor AEM pakket omvat een out-of-the-box integratie tussen de profielen van AEM Communities en de dienst van SSO van Livefyre.

Wanneer gebruikers zich aanmelden bij uw AEM, worden ze ook aangemeld bij sociale onderdelen van LiveCycle. Wanneer een aangemelde gebruiker een onderdeel van LiveCycle probeert te gebruiken dat verificatie vereist (zoals het uploaden van een foto), initieert de component LiveCyre gebruikersverificatie.

De standaardintegratie voor verificatie is mogelijk niet perfect voor elke site. Om de verificatiestroom in uw sitesjablonen het beste aan te passen, kunt u de standaard LiveCycle Authentication Delegate negeren en aan uw behoeften voldoen. Voer de volgende stappen uit:

1. Kopieer met behulp van CRXDE Lite */libs/social/integrations/livefyre/components/authorizablecomponent/authclientlib* naar */apps/social/integrations/livefyre/components/authorizablecomponent/authclientlib*.
1. Bewerk en sla */apps/social/integrations/livefyre/components/authorizablecomponent/authclientlib/auth.js* op om een Livefyre Auth-delegatie te implementeren die aan uw behoeften voldoet.

   Voor meer informatie bij het aanpassen van een Afgevaardigde van de Auth, zie [Identiteitsintegratie](https://answers.livefyre.com/developers/identity-integration/).

   Voor meer informatie over AEM Clientlibs, zie [Het gebruiken van cliënt-zij Bibliotheken](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/clientlibs.html).

## Livefre gebruiken met AEM Sites {#use-livefyre-with-aem-sites}

### Bibliotheekcomponenten toevoegen aan een pagina {#add-livefyre-components-to-a-page}

Voordat u LiveCycle-componenten aan een pagina binnen Sites toevoegt, moet u LiveCycle voor de pagina inschakelen door een LiveCycle-cloudconfiguratie van een bovenliggende pagina over te nemen of door de configuratie rechtstreeks aan de pagina toe te voegen. Raadpleeg uw implementatie voor informatie over het opnemen van cloudservices op uw site.

Nadat LiveCycle is ingeschakeld voor de pagina, moeten containers zijn geconfigureerd om Livefyre-componenten toe te staan. Zie [Componenten configureren in ontwerpmodus](https://helpx.adobe.com/experience-manager/6-3/sites/authoring/using/default-components-designmode.html) voor instructies over het inschakelen van verschillende componenten.

>[!NOTE]
>
>Toepassingen waarvoor verificatie moet worden gepost, werken pas nadat verificatie is geconfigureerd in Single Sign-On-integratie aanpassen.

1. Selecteer **Livefyre** in het menu van het zijpaneel **Componenten** in de ontwerpmodus om de lijst te beperken tot beschikbare LiveCycle-componenten.

   ![livefyre-add](assets/livefyre-add.png)

1. Selecteer een component LiveCycle en sleep deze naar de gewenste positie op de pagina.
1. Selecteer of u een nieuwe LiveCycle-app wilt maken of een bestaande wilt insluiten.

   Als u een bestaande app insluit, AEM u wordt gevraagd de app te selecteren. Als u een nieuwe app maakt, moet de app worden ingevuld voordat er inhoud wordt weergegeven. De app wordt gemaakt op de livefyre-site en het netwerk dat is geselecteerd toen de cloudconfiguratie van LiveCycle voor de pagina is ingeschakeld.

   Zie [Pagina-inhoud bewerken](https://helpx.adobe.com/experience-manager/6-3/sites/authoring/using/editing-content.html) voor meer informatie over het invoegen van componenten.

### Een LiveCycle-component voor een AEM pagina bewerken. {#edit-a-livefyre-component-for-an-aem-page}

U kunt een component Livefyre in Studio slechts vormen en uitgeven Livefyre. Van AEM:

1. Klik op de component LiveCycle om te configureren.
1. Klik **Configure** pictogram (moersleutel) om de configuratiedialoog te openen.
1. Klik **om deze component uit te geven, ga naar LiveCyre Studio**.
1. Bewerk de app in LiveCyre Studio.

## Livefre gebruiken met AEM Assets {#use-livefyre-with-aem-assets}

### Rechten aanvragen en UGC importeren in AEM Assets {#request-rights-and-import-ugc-into-aem-assets}

Met de UGC-importmodule kunt u Twitter- en Instagram door gebruikers gegenereerde inhoud (UGC) vanuit LiveCycle Studio naar AEM Assets importeren. Nadat u de inhoud hebt geselecteerd die u wilt importeren, moet u eerst rechten op de inhoud aanvragen voordat het importeren kan worden voltooid.

>[!NOTE]
>
>Voordat u middelen kunt gebruiken om UGC te importeren, moet u accounts voor sociale accounts en verzoeken om rechten instellen in LiveCycle Studio. Zie [Instelling: Verzoeken om rechten](https://docs.adobe.com/content/help/en/livefyre/using/rights-requests/c-how-requesting-rights-works.html) voor meer informatie.

UGC importeren in AEM Assets:

1. Navigeer vanaf de AEM homepage naar **Middelen > Bestanden**.
1. Klik **Maken**, dan klik **Invoer UGC.**

   ![livefyre-aem-import-ugc](assets/livefyre-aem-import-ugc.png)

1. Inhoud zoeken:

   * Klik vanuit LiveCycle op het tabblad UGC-bibliotheek. Gebruik de filters en het onderzoek om inhoud van de Bibliotheek te vinden UGC.
   * Klik op het tabblad Twitter of Instagram op Twitter en Instagram. Gebruik de zoekopdracht of de filters om inhoud te zoeken.

1. Selecteer de elementen die u wilt importeren. De elementen die u selecteert, worden automatisch geteld en opgeslagen onder het tabblad **Geselecteerd**.
1. **Optioneel**: Klik op het tabblad  **** Selectie en bekijk de geselecteerde UGC-inhoud die u wilt importeren.
1. Klik op **Next**.

   ![livefyre-aem-import-ugc2](assets/livefyre-aem-import-ugc2.png)

1. Kies voor aanvragen voor rechten een van de volgende opties voor elk element:

   Voor Instagram:

   * **Vraag handmatig** om rechten om een bericht dat u kunt kopiëren en plakken en handmatig via Instagram naar de eigenaars van inhoud kunt verzenden.
   * **Rechten voor handmatig kenmerkinhoud** om de rechten voor afzonderlijke elementen te overschrijven.

   >[!NOTE]
   >
   >Vanwege updates die van invloed zijn op de aggregatie van inhoud van niet-zakelijke gebruikersaccounts, kunnen we geen opmerkingen meer namens u plaatsen of automatisch controleren op antwoorden van de auteur. [Klik hier voor meer](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/) informatie.

   ![livefyre-aem-import-ugc3-6-4](assets/livefyre-aem-import-ugc3-6-4.png)

   Voor Twitter:

   * **Bericht** Auteur om een bericht naar de eigenaar van de inhoud te verzenden waarin om rechten op het element wordt gevraagd.
   * **Rechten voor handmatig kenmerkinhoud** om de rechten voor afzonderlijke elementen te overschrijven.


1. Klik **Importeren**.

   Als u een aanvraag voor Twitter-rechten hebt verzonden, ziet de eigenaar van de inhoud het bericht voor het aanvragen van rechten op zijn account:

   ![livefyre-aem-rights-request-twitter](assets/livefyre-aem-rights-request-twitter.png)

   >[!NOTE]
   >
   >Twitter heeft limieten voor identieke aanvragen van hetzelfde account. Wanneer het invoeren van meer dan een paar activa, wijzig de berichten individueel om te vermijden die worden gemarkeerd.

1. Klik **Done** in de hoger-juiste hoek om de workflow voor het aanvragen van rechten te voltooien.

   U kunt de status zien van een aanvraag voor rechten in behandeling voor een middel in LiveCyre Studio. Als de inhoud in afwachting is van een verzoek om rechten, wordt het element pas in AEM Assets weergegeven als de rechten zijn verleend. Het middel verschijnt automatisch in AEM Assets wanneer een Verzoek van Rechten wordt verleend.

   Voor Instagram moet u het antwoord van de eigenaar van de inhoud volgen en handmatig rechten verlenen als u rechten hebt op de inhoud.

## Livefre gebruiken met AEM Handel {#use-livefyre-with-aem-commerce}

### Productcatalogi importeren in LiveCycle met AEM handel {#import-product-catalogs-into-livefyre-with-aem-commerce}

AEM gebruikers van Commerce kunnen hun bestaande productcatalogus naadloos integreren in Livefyre om de betrokkenheid van gebruikers in de visualisatie-apps van Livefyre te stimuleren.

Nadat u de productcatalogus hebt geïmporteerd, worden de producten in real-time weergegeven in uw LiveCycle-instantie. Als u items bewerkt of verwijdert in de catalogus AEM Commerce-product, worden de wijzigingen automatisch bijgewerkt in LiveCycle.

1. Zorg ervoor dat u de nieuwste versie van Livefyre voor AEM pakket op uw AEM hebt geïnstalleerd.
1. Navigeer vanaf de AEM homepage naar **AEM Commerce**.
1. Maak een nieuwe verzameling of gebruik een bestaande verzameling.
1. Houd de cursor boven de verzameling en klik op **Verzamelingseigenschappen** (potloodpictogram).
1. Schakel **Synchroniseren met LiveCycle** in.
1. Vul **Prefix LiveCycle Page** in om deze verzameling te koppelen aan een specifieke pagina in AEM.

   Het paginavoorvoegsel definieert het hoofdpad in uw omgeving waar het zoeken naar productpagina&#39;s begint. LiveCycle kiest de eerste pagina waaraan een overeenkomstig product is gekoppeld. Voor verschillende pagina&#39;s voor verschillende producten zijn meerdere verzamelingen nodig.

## Ondersteuningsmatrix AEM voor LiveCyre-apps {#aem-support-matrix-for-livefyre-apps}

| Livefyre Apps | AEM 6,1 | AEM 6,2 | AEM 6,3 | AEM 6,4 |
|---|---|---|---|---|
| Carousel | X | X | X | X |
| Chat | X | X | X | X |
| Opmerkingen | X | X | X | X |
| Filmstrip |  | X | X | X |
| LiveBlog | X | X | X | X |
| Kaart | X | X | X | X |
| Mediumwand | X | X | X | X |
| Mozaïek | X | X | X | X |
| Opiniepeiling |  | X | X | X |
| Revisies |  | X | X | X |
| Enkele kaart | X | X | X | X |
| Storiseren 2 |  | X | X | X |
| Trend |  | X | X | X |
| Knop Uploaden |  | X | X | X |

