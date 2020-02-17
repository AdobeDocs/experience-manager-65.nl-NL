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
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7

---


# Integreren met Livefyre{#integrating-with-livefyre}

Leer hoe u de toonaangevende curatiemogelijkheden van Livefy met uw AEM 6.5-exemplaar kunt integreren, zodat u in enkele minuten waardevolle door gebruikers gegenereerde inhoud (UGC) kunt publiceren van sociale netwerken naar uw site.

## Aan de slag {#getting-started}

### Livefyre Package installeren voor AEM {#install-livefyre-package-for-aem}

AEM 6.5 wordt geleverd met het Livefyre-functiepakket 1.2.6 vooraf geïnstalleerd. Dit pakket bevat alleen beperkte Livefyre-integratie met AEM-sites en moet worden verwijderd voordat een bijgewerkt pakket kan worden geïnstalleerd. Met het nieuwste pakket kunt u de volledige integratie van Livefyre met AEM ervaren, inclusief Sites, Assets en Commerce.

>[!NOTE]
>
>Sommige eigenschappen van het pakket AEM-LF hangen van Sociaal Kader (SCF) af. Als u het Livefyre eigenschappak als deel van een niet-gemeenteplaats gebruikt, moet u *cq.social.scf* als gebiedsdeel in de auteursclientlibs van de website verklaren. Als u het LF eigenschappak als deel van een communautaire website gebruikt, zou deze gebiedsdeel reeds moeten worden verklaard.

1. Klik op de AEM-startpagina op het pictogram **Gereedschappen** in de linkertrack.
1. Navigeer naar **Implementatie > Pakketten**.
1. Blader in Pakketbeheer totdat u het vooraf geïnstalleerde Livefyre-functiepakket ziet en klik vervolgens op de pakkettitel **cq-social-livefyre-pkg-1.2.6.zip** om de opties uit te vouwen.
1. Klik op **Meer > Verwijderen**.

   ![livefyre-aem-uninstall-64](assets/livefyre-aem-uninstall-64.png)

1. Keer terug naar de homepage AEM, klik Hulpmiddelen, dan navigeer aan **Plaatsing > het Aandeel** van het Pakket.

   Een lijst met functiepakketten en hotfixes beschikbaar voor downloadweergaven.

1. Zoek in de trefwoordzoekopdracht naar &quot;Livefyre&quot; en selecteer vervolgens het functiepakket Livefyre dat overeenkomt met uw AEM-versie.

   ![livefyre-aem3-6-4](assets/livefyre-aem3-6-4.png)

1. Voor de pagina van de de informatie van het eigenschappak, klik **Download**, lees dan de Overeenkomst van de Vergunning van het Pakket en klik **Accepteren**.
1. Ga terug naar Pakketbeheer, zoek het nieuwe gedownloade pakket en klik op **Installeren**.

   ![livefyre-aem4-6-4](assets/livefyre-aem4-6-4.png)

   Uw Livefyre-AEM-pakket is nu geïnstalleerd. Voordat u de integratiefuncties kunt gaan gebruiken, moet u AEM configureren om Livefyre te gebruiken.

   Voor meer informatie over pakketten, zie [hoe te met Pakketten](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/package-manager.html)werken.

   Voor meer informatie en versienota&#39;s op eigenschapspakken, zie de Packs van de [Eigenschap](https://helpx.adobe.com/experience-manager/6-3/release-notes/feature-packs-release-notes.html).

### AEM configureren voor gebruik van Livefyre: Een configuratiemap maken {#configure-aem-to-use-livefyre-create-a-configuration-folder}

1. Klik op de AEM-startpagina op het pictogram **Gereedschappen** in de linkertrack en navigeer vervolgens naar **Algemeen > Configuratiebrowser**.
1. Klik op **Maken** om het dialoogvenster Configuratie maken te openen.
1. Geef uw configuratie een naam en schakel het selectievakje **Cloud Configurations** in.

   Hiermee wordt een map gemaakt onder **Extra > Implementatie > LiveCycle Configuration** met de opgegeven naam.

   ![livefyre-aem-create-config-folder](assets/livefyre-aem-create-config-folder.png)

### AEM configureren voor gebruik van Livefyre: Een LiveCycle-configuratie maken {#configure-aem-to-use-livefyre-create-a-livefyre-configuration}

Configureer AEM om de LiveCyre-licentiereferenties van uw organisatie te gebruiken, zodat u kunt communiceren tussen Livefyre en AEM.

1. Klik op de AEM-startpagina op het pictogram **Gereedschappen** in het linkerspoor en navigeer vervolgens naar **Implementatie > Live View-configuratie**.
1. Selecteer de configuratiemap waarin u een nieuwe configuratie van de Levensstijl wilt tot stand brengen, dan klik **creëren**.

   ![create-livefyre-configuration1](assets/create-livefyre-configuration1.png)

   >[!NOTE]
   >
   >Mappen moeten de eigenschappen van Cloud Configurations hebben ingeschakeld voordat LiveCycle-configuraties eraan kunnen worden toegevoegd. De omslagen van de configuratie worden gecreeerd en in Browser van de Configuratie geleid.
   >
   >U kunt geen naam voor een configuratie-het wordt van verwijzingen voorzien door de weg van de omslag het binnen is. U kunt slechts één configuratie per map hebben.

1. Selecteer de nieuwe Livefy-configuratiekaart en klik op **Eigenschappen**.

   ![create-livefyre-configuration2](assets/create-livefyre-configuration2.png)

1. Voer de Livefyre-gegevens van uw organisatie in en klik op **OK**.

   ![configure-aem2](assets/configure-aem2.png)

   Voor toegang tot deze informatie opent u de Livefyre-studio en navigeert u naar **Instellingen > Integratie-instellingen > Referenties**.

   Uw AEM-instantie is nu geconfigureerd voor het gebruik van LiveCycle en u kunt de integratiefuncties gebruiken.

### Integratie van Single Sign-On aanpassen {#customize-single-sign-on-integration}

Het Livefyre for AEM-pakket omvat een out-of-the-box integratie tussen AEM Communities-profielen en de SSO-service van Livefyre.

Wanneer gebruikers zich aanmelden bij uw AEM-site, worden ze ook aangemeld bij sociale onderdelen van Livefyre. Wanneer een aangemelde gebruiker een onderdeel van LiveCycle probeert te gebruiken dat verificatie vereist (zoals het uploaden van een foto), initieert de component LiveCyre gebruikersverificatie.

De standaardintegratie voor verificatie is mogelijk niet perfect voor elke site. Om de verificatiestroom in uw sitesjablonen het beste aan te passen, kunt u de standaard LiveCycle Authentication Delegate negeren en aan uw behoeften voldoen. Voer de volgende stappen uit:

1. Kopieer met behulp van CRXDE Lite */libs/social/integrations/livefyre/components/authorizablecomponent/authclientlib* naar */apps/social/integrations/livefyre/components/authorizablecomponent/authclientlib*.
1. Bewerk en sla */apps/social/integrations/livefyre/components/authorizablecomponent/authclientlib/auth.js* op om een Livefyre Auth-afgevaardigde te implementeren die aan uw behoeften voldoet.

   Voor meer informatie bij het aanpassen van een Afgevaardigde van de Auth, zie de Integratie [van de](https://answers.livefyre.com/developers/identity-integration/)Identiteit.

   Voor meer informatie over Clientlibs AEM, zie het [Gebruiken van Cliënt-zij Bibliotheken](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/clientlibs.html).

## Livefyre gebruiken met AEM-sites {#use-livefyre-with-aem-sites}

### LiveCycle-componenten aan een pagina toevoegen {#add-livefyre-components-to-a-page}

Voordat u LiveCycle-componenten aan een pagina binnen Sites toevoegt, moet u LiveCycle voor de pagina inschakelen door een LiveCycle-cloudconfiguratie van een bovenliggende pagina over te nemen of door de configuratie rechtstreeks aan de pagina toe te voegen. Raadpleeg uw implementatie voor informatie over het opnemen van cloudservices op uw site.

Nadat LiveCycle is ingeschakeld voor de pagina, moeten containers zijn geconfigureerd om Livefyre-componenten toe te staan. Zie Componenten [configureren in ontwerpmodus](https://helpx.adobe.com/experience-manager/6-3/sites/authoring/using/default-components-designmode.html) voor instructies over het inschakelen van verschillende componenten.

>[!NOTE]
>
>Toepassingen waarvoor verificatie moet worden gepost, werken pas nadat verificatie is geconfigureerd in Single Sign-On-integratie aanpassen.

1. Selecteer in de ontwerpmodus in het deelvenster **Componenten** de optie **LiveCycle** in het menu om de lijst te beperken tot beschikbare LiveCycle-componenten.

   ![livefyre-add](assets/livefyre-add.png)

1. Selecteer een component LiveCycle en sleep deze naar de gewenste positie op de pagina.
1. Selecteer of u een nieuwe LiveCycle-app wilt maken of een bestaande wilt insluiten.

   Als u een bestaande app insluit, vraagt AEM u om de app te selecteren. Als u een nieuwe app maakt, moet de app worden ingevuld voordat er inhoud wordt weergegeven. De app wordt gemaakt op de livefyre-site en het netwerk dat is geselecteerd toen de cloudconfiguratie van LiveCycle voor de pagina is ingeschakeld.

   Zie [Pagina-inhoud](https://helpx.adobe.com/experience-manager/6-3/sites/authoring/using/editing-content.html)bewerken voor meer informatie over het invoegen van componenten.

### Een LiveCycle-component voor een AEM-pagina bewerken. {#edit-a-livefyre-component-for-an-aem-page}

U kunt een component Livefyre in Studio slechts vormen en uitgeven Livefyre. Van AEM:

1. Klik op de component LiveCycle om te configureren.
1. Klik op het pictogram **Configureren** (sleutel) om het configuratiedialoogvenster te openen.
1. Klik **om deze component uit te geven, ga naar LiveCycle Studio**.
1. Bewerk de app in LiveCyre Studio.

## Livefyre gebruiken met AEM-middelen {#use-livefyre-with-aem-assets}

### Rechten aanvragen en UGC importeren in AEM-middelen {#request-rights-and-import-ugc-into-aem-assets}

Met de UGC-importmodule kunt u Twitter- en Instagram door gebruikers gegenereerde inhoud (UGC) vanuit LiveCyre Studio importeren in AEM-middelen. Nadat u de inhoud hebt geselecteerd die u wilt importeren, moet u eerst rechten op de inhoud aanvragen voordat het importeren kan worden voltooid.

>[!NOTE]
>
>Voordat u middelen kunt gebruiken om UGC te importeren, moet u accounts voor sociale accounts en verzoeken om rechten instellen in LiveCycle Studio. Zie [Instelling: Rechten Verzoeken](https://marketing.adobe.com/resources/help/en_US/livefyre/c_how_requesting_rights_works.html) om meer informatie.

UGC importeren in AEM-elementen:

1. Navigeer vanaf de AEM-startpagina naar **Middelen > Bestanden**.
1. Klik op **Maken** en vervolgens op **UGC importeren.**

   ![livefyre-aem-import-ugc](assets/livefyre-aem-import-ugc.png)

1. Inhoud zoeken:

   * Klik vanuit LiveCycle op het tabblad UGC-bibliotheek. Gebruik de filters en het onderzoek om inhoud van de Bibliotheek te vinden UGC.
   * Klik op het tabblad Twitter of Instagram op Twitter en Instagram. Gebruik de zoekopdracht of de filters om inhoud te zoeken.

1. Selecteer de elementen die u wilt importeren. De elementen die u selecteert, worden automatisch geteld en onder het tabblad **Geselecteerd** opgeslagen.
1. **Optioneel**: Klik op het tabblad **Geselecteerd** en bekijk de geselecteerde UGC-inhoud die u wilt importeren.
1. Click **Next**.

   ![livefyre-aem-import-ugc2](assets/livefyre-aem-import-ugc2.png)

1. Kies voor aanvragen voor rechten een van de volgende opties voor elk element:

   Voor Instagram:

   * **Handmatig om rechten** vragen om een bericht te verkrijgen dat via Instagram kan worden gekopieerd en geplakt en handmatig naar de eigenaars van de inhoud kan worden verzonden.
   * **Rechten** voor inhoud handmatig bepalen om de rechten voor afzonderlijke elementen te overschrijven.
   >[!NOTE]
   >
   >Vanwege updates die van invloed zijn op de aggregatie van inhoud van niet-zakelijke gebruikersaccounts, kunnen we geen opmerkingen meer namens u plaatsen of automatisch controleren op antwoorden van de auteur. [Klik hier voor meer](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/)informatie.

   ![livefyre-aem-import-ugc3-6-4](assets/livefyre-aem-import-ugc3-6-4.png)

   Voor Twitter:

   * **Auteur** van bericht om een bericht naar de eigenaar van de inhoud te verzenden waarin om rechten voor het element wordt gevraagd.
   * **Rechten** voor inhoud handmatig bepalen om de rechten voor afzonderlijke elementen te overschrijven.


1. Klik op **Importeren**.

   Als u een aanvraag voor Twitter-rechten hebt verzonden, ziet de eigenaar van de inhoud het bericht voor het aanvragen van rechten op zijn account:

   ![livefyre-aem-rights-request-twitter](assets/livefyre-aem-rights-request-twitter.png)

   >[!NOTE]
   >
   >Twitter heeft limieten voor identieke aanvragen van hetzelfde account. Wanneer het invoeren van meer dan een paar activa, wijzig de berichten individueel om te vermijden die worden gemarkeerd.

1. Klik op **Gereed** in de rechterbovenhoek om de workflow voor het aanvragen van rechten te voltooien.

   U kunt de status zien van een aanvraag voor rechten in behandeling voor een middel in LiveCyre Studio. Als de inhoud in afwachting is van een verzoek om rechten, wordt het element pas weergegeven in AEM Assets nadat rechten zijn verleend. Het element wordt automatisch weergegeven in AEM Assets wanneer een aanvraag voor rechten wordt toegekend.

   Voor Instagram moet u het antwoord van de eigenaar van de inhoud volgen en handmatig rechten verlenen als u rechten hebt op de inhoud.

## Livefyre gebruiken met AEM Commerce {#use-livefyre-with-aem-commerce}

### Productcatalogi met AEM Commerce in Livefyre importeren {#import-product-catalogs-into-livefyre-with-aem-commerce}

Gebruikers van AEM Commerce kunnen hun bestaande productcatalogus naadloos integreren in Livefyre om de betrokkenheid van gebruikers in de visualisatie-apps van Livefyre te stimuleren.

Nadat u de productcatalogus hebt geïmporteerd, worden de producten in real-time weergegeven in uw LiveCycle-instantie. Als u items in de productcatalogus van AEM Commerce bewerkt of verwijdert, worden de wijzigingen automatisch bijgewerkt in LiveCycle.

1. Zorg ervoor dat u het nieuwste Livefyre for AEM-pakket op uw AEM-instantie hebt geïnstalleerd.
1. Navigeer vanaf de AEM-startpagina naar **AEM Commerce**.
1. Maak een nieuwe verzameling of gebruik een bestaande verzameling.
1. Houd de cursor boven de verzameling en klik op **Verzamelingseigenschappen** (potloodpictogram).
1. Schakel **Synchroniseren met LiveCycle** in.
1. Vul het voorvoegsel **van de** bibliotheekpagina in om deze verzameling te koppelen aan een specifieke pagina in AEM.

   Het paginavoorvoegsel definieert het hoofdpad in uw omgeving waar het zoeken naar productpagina&#39;s begint. LiveCycle kiest de eerste pagina waaraan een overeenkomstig product is gekoppeld. Voor verschillende pagina&#39;s voor verschillende producten zijn meerdere verzamelingen nodig.

## AEM-ondersteuningsmatrix voor LiveCyre-apps {#aem-support-matrix-for-livefyre-apps}

| Livefyre Apps | AEM 6.1 | AEM 6.2 | AEM 6.3 | AEM 6.4 |
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

