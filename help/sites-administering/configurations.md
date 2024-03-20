---
title: Configuraties en de Configuratiebrowser
description: Begrijp AEM configuraties en hoe zij werkruimtemontages in AEM beheren.
exl-id: 1be5849b-748c-48e8-afa8-35a9026c27b3
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 0%

---

# Configuraties en de Configuratiebrowser {#configuration-browser}

AEM configuraties dienen om instellingen in AEM te beheren en dienen als werkruimten.

## Wat is een Configuratie? {#what-is-a-configuration}

Een configuratie kan vanuit twee verschillende gezichtspunten worden overwogen.

* [Beheerder](#configurations-administrator) gebruikt configuraties als werkruimten binnen AEM om groepen montages te bepalen en te beheren.
* [Een ontwikkelaar](#configurations-developer) gebruikt het onderliggende configuratiemechanisme dat configuraties uitvoert om montages in AEM voort te zetten en op te zoeken.

Samengevat: vanuit het standpunt van de beheerder, zijn de configuraties hoe u werkruimten creeert om montages in AEM te beheren, terwijl de ontwikkelaar zou moeten begrijpen hoe AEM deze configuraties binnen de bewaarplaats gebruikt en beheert.

Configuraties hebben, ongeacht uw perspectief, twee hoofddoelen in AEM:

* Configuraties bieden bepaalde functies voor bepaalde groepen gebruikers.
* Configuraties definiëren de toegangsrechten voor deze functies.

## Configuraties als beheerder {#configurations-administrator}

De AEM beheerder en auteurs kunnen configuraties als werkruimten beschouwen. Deze werkruimten kunnen worden gebruikt om groepen instellingen en de bijbehorende inhoud voor organisatorische doeleinden te verzamelen door toegangsrechten voor die functies te implementeren.

Configuraties kunnen worden gemaakt voor vele verschillende functies in AEM.

* [Cloudconfiguraties](/help/sites-administering/configurations.md)
* [Context Hub Segments](/help/sites-administering/segmentation.md)
* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Bewerkbare sjablonen](/help/sites-authoring/templates.md)

### Voorbeeld {#administrator-example}

Een beheerder kan bijvoorbeeld twee configuraties voor bewerkbare sjablonen maken.

* WKND-generaal
* WKND-Magazine

De beheerder kan algemene paginasjablonen dan maken met behulp van de WKND-Algemene configuratie en vervolgens sjablonen die specifiek zijn voor het tijdschrift onder WKND-Magazine.

De beheerder kan vervolgens de WKND-General koppelen aan alle inhoud van de WKND-site. Nochtans zou de configuratie WKND-Magazine slechts met de tijdschriftplaats worden geassocieerd.

Op deze manier:

* Wanneer een inhoudsauteur een pagina voor het tijdschrift maakt, kan de auteur kiezen uit algemene sjablonen (WKND-Algemeen) of tijdschriftsjablonen (WKND-Magazine).
* Wanneer een auteur van inhoud een pagina maakt voor een ander gedeelte van de site dat niet het tijdschrift is, kan de auteur alleen kiezen uit de algemene sjablonen (WKND-Algemeen).

De gelijkaardige montages zijn mogelijk niet alleen voor Bewerkbare Malplaatjes maar ook voor de Configuraties van de Wolk, Segmenten ContextHub, en Modellen van het Fragment van de Inhoud.

### De configuratiebrowser gebruiken {#using-configuration-browser}

Browser van de Configuratie staat een beheerder toe om, toegangsrechten aan configuraties in AEM gemakkelijk tot stand te brengen te beheren en te vormen.

>[!NOTE]
>
>Het is alleen mogelijk om configuraties te maken met de Configuration Browser als de gebruiker `admin` rechten. De rechten van de beheerder worden ook vereist om toegangsrechten aan de configuratie toe te wijzen of anders een configuratie te wijzigen.

#### Een configuratie maken {#creating-a-configuration}

Het is eenvoudig om een configuratie in AEM tot stand te brengen door Browser van de Configuratie te gebruiken.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Gereedschappen** > **Algemeen** > **Configuratiebrowser**.
1. Klikken **Maken**.
1. Geef een **Titel** en **Naam** voor uw configuratie.

   ![Configuratie maken](assets/configuration-create.png)

   * De **Titel** moeten beschrijvend zijn.
   * De **Naam** wordt de knooppuntnaam in de gegevensopslagruimte.
      * Deze wordt automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies.](/help/sites-developing/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.
1. Controleer het type configuraties dat u wilt toestaan.
   * [Cloudconfiguraties](/help/sites-administering/configurations.md)
   * [Context Hub Segments](/help/sites-administering/segmentation.md)
   * [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
   * [Bewerkbare sjablonen](/help/sites-authoring/templates.md)
1. Klikken **Maken**.

>[!TIP]
>
>Configuraties kunnen genest zijn.

#### Configuraties en hun toegangsrechten bewerken {#access-rights}

Als u configuraties als werkruimten beschouwt, kunnen de toegangsrechten op die configuraties worden geplaatst om af te dwingen wie tot die werkruimten kan en niet kan toegang hebben.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Gereedschappen** > **Algemeen** > **Configuratiebrowser**.
1. Selecteer de configuratie die u wilt wijzigen en klik dan **Eigenschappen** in de werkbalk.
1. Selecteer om het even welke extra eigenschappen die u aan de configuratie wilt toevoegen.

   >[!NOTE]
   >
   >Het is niet mogelijk om een functie uit te schakelen wanneer de configuratie is gemaakt.

1. Gebruik de **Effectieve machtigingen** knoop om een matrijs van rollen te bekijken en welke toestemmingen zij momenteel aan configuraties worden verleend.
   ![venster Effectieve machtigingen](assets/configuration-effective-permissions.png)
1. Als u nieuwe machtigingen wilt toewijzen, voert u de naam van de gebruiker of groep in het dialoogvenster **Gebruiker of groep selecteren** in het veld **Nieuwe machtigingen toevoegen** sectie.
   * De  **Gebruiker of groep selecteren** het veld biedt automatisch aanvullen op basis van bestaande gebruikers en rollen.
1. Selecteer de gewenste gebruiker of rol in de resultaten die automatisch worden voltooid.
   * U kunt meerdere gebruikers of rollen selecteren.
1. Controleer de toegangsopties die de geselecteerde gebruikers of rollen zouden moeten hebben en klik **Toevoegen**.
   ![Toegangsrechten toevoegen aan een configuratie](assets/configuration-edit.png)
1. Herhaal de stappen zodat u gebruikers of rollen kunt selecteren en zonodig extra toegangsrechten kunt toewijzen.
1. Selecteren **Opslaan en sluiten** als u klaar bent.

## Configuraties als ontwikkelaar {#configurations-developer}

Als ontwikkelaar, is het belangrijk om te weten hoe AEM as a Cloud Service met configuraties werkt en hoe het configuratieresolutie verwerkt.

### Scheiding van configuratie en inhoud {#separation-of-config-and-content}

Hoewel de [beheerders en gebruikers kunnen configuraties als werkplekken zien](#configurations-administrator) om verschillende instellingen en inhoud te beheren is het belangrijk te begrijpen dat configuraties en inhoud afzonderlijk worden opgeslagen en beheerd door AEM in de opslagplaats.

* `/content` is de thuisbasis van alle inhoud.
* `/conf` is huis aan alle configuratie.

Content verwijst naar de bijbehorende configuratie via een `cq:conf` eigenschap. AEM voert een raadpleging uit die op de inhoud en zijn contextueel wordt gebaseerd `cq:conf` eigenschap om de juiste configuratie te vinden.

### Voorbeeld {#developer-example}

Voor dit voorbeeld, veronderstellen wij u één of andere toepassingscode hebt die in montages DAM geinteresseerd is.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Het uitgangspunt van alle configuratieraadpleging is een inhoudsmiddel, ergens onder `/content`. Dit kan een pagina zijn, een component in een pagina, een element of een DAM-map. Dit is de daadwerkelijke inhoud waarvoor u de juiste configuratie zoekt die in deze context van toepassing is.

Nu met de `Conf` in hand, kunt u het specifieke configuratiepunt terugwinnen dat u in geinteresseerd bent. In dit geval is het `dam/imageserver`, dat een verzameling instellingen is die betrekking hebben op de `imageserver`. De `getItem` call retourneert een `ValueMap`. Daarna leest u een `bgkcolor` string bezit en verstrekken een standaardwaarde van &quot;FFFFFF&quot;voor het geval dat het bezit (of het volledige config punt) niet aanwezig is.

Nu een blik op de overeenkomstige inhoud JCR:

```text
/content/dam/wknd
    + jcr:content
      - cq:conf = "/conf/wknd"
    + image.png [dam:Asset]

/conf/wkns
    + settings
      + dam
        + imageserver [cq:Page]
          + jcr:content
            - bgkcolor = "FF0000"
```

In dit voorbeeld kunt u hier een WKND-specifieke DAM-map en een bijbehorende configuratie aannemen. Vanaf die map `/content/dam/wknd`kunt u zien dat er een tekenreekseigenschap is met de naam `cq:conf` dat verwijst naar de configuratie die voor de substructuur zou moeten van toepassing zijn. De eigenschap wordt ingesteld op het tabblad `jcr:content` van een elementmap of -pagina. Deze `conf` De verbindingen zijn uitdrukkelijk, zodat is het gemakkelijk om hen te volgen door de inhoud in CRXDE te bekijken.

Binnenin pompen `/conf`, kunt u de verwijzing volgen en zien dat er een `/conf/wknd` knooppunt. Deze configuratie. De zoekopdracht is transparant voor de toepassingscode. De voorbeeldcode heeft er nooit een specifieke verwijzing naar, het is verborgen achter de `Conf` object. Welke configuratie van toepassing is, wordt bepaald door de JCR-inhoud.

U kunt zien dat de configuratie een fixed-named bevat `settings` knooppunt dat de werkelijke items bevat, inclusief de `dam/imageserver` dat u in dit geval nodig hebt. Een dergelijk item kan worden beschouwd als een &quot;instellingendocument&quot; en wordt voorgesteld door een `cq:Page` inclusief `jcr:content` de feitelijke inhoud bezitten.

Tot slot kunt u de eigenschap zien `bgkcolor` die voorbeeldcode nodig heeft. De `ValueMap` u bent terug `getItem` is gebaseerd op de `jcr:content` knooppunt.

### Configuratieresolutie {#configuration-resolution}

Het basisvoorbeeld hierboven toonde één enkele configuratie. Maar er zijn veel gevallen waarin u verschillende configuraties wilt hebben, zoals een standaard globale configuratie, een andere configuratie voor elk merk en misschien een specifieke configuratie voor uw subprojecten.

Om dit te steunen, heeft de configuratieraadpleging in AEM een overerving en een reservemechanisme in de volgende orde van voorkeur:

1. `/conf/<siteconfig>/<parentconfig>/<myconfig>`
   * Specifiek config van verwijzingen voorzien `cq:conf` ergens in `/content`
   * De hiërarchie is willekeurig en kan net als uw sitestructuur worden ontworpen, het is niet aan toepassingscode om dit te weten
   * Veranderbaar bij uitvoering door gebruikers met configuratierechten
1. `/conf/<siteconfig>/<parentconfig>`
   * Traverse ouders voor terugvalconfiguraties
   * Veranderbaar bij uitvoering door gebruikers met configuratierechten
1. `/conf/<siteconfig>`
   * Traverse ouders voor terugvalconfiguraties
   * Veranderbaar bij uitvoering door gebruikers met configuratierechten
1. `/conf/global`
   * Globale instellingen van systeem
   * Algemene standaardinstellingen voor uw installatie
   * Met een `admin` rol
   * Veranderbaar bij uitvoering door gebruikers met configuratierechten
1. `/apps`
   * Standaardwaarden toepassing
   * Opgelost met implementatie van toepassingen
   * Alleen-lezen bij uitvoering
1. `/libs`
   * Standaardwaarden AEM product
   * Alleen veranderbaar door Adobe, projecttoegang niet toegestaan
   * Opgelost met implementatie van toepassingen
   * Alleen-lezen bij uitvoering

### Configuraties gebruiken {#using-configurations}

Configuraties in AEM zijn gebaseerd op Sling Context-Aware Configurations. De bundels van de Verkoop verstrekken de dienst API die kan worden gebruikt om context-bewuste configuraties te krijgen. Contextbewuste configuraties zijn configuraties die verwant zijn aan een inhoudsmiddel of een middelboom zoals was [beschreven in het vorige voorbeeld.](#developer-example)

Voor meer informatie over Context-Aware Configuraties, voorbeelden, en hoe te om hen te gebruiken, [zie de documentatie van het Verkopen.](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)

### ConfMgr-webconsole {#confmgr-web-console}

Voor foutopsporing- en testdoeleinden is er een **ConfMgr** webconsole op `https://<host>:<port>/system/console/conf`, die configuraties voor een bepaald pad/item kan weergeven.

![ConfMgr](assets/configuration-confmgr.png)

Verstrek eenvoudig:

* **Inhoudspad**
* **Item**
* **Gebruiker**

Om te zien welke configuraties worden opgelost en een steekproefcode te ontvangen die die configuraties oplost, selecteer **Oplossen**.

### Contextbewuste configuratie webconsole {#context-aware-web-console}

Voor foutopsporing- en testdoeleinden is er een **Contextbewuste configuratie** webconsole op `https://<host>:<port>/system/console/slingcaconfig`, waarmee u contextbewuste configuraties in de opslagplaats kunt opvragen en hun eigenschappen kunt bekijken.

![Contextbewuste configuratie webconsole](assets/configuration-context-aware-console.png)

Verstrek eenvoudig:

* **Inhoudspad**
* **Configuratienaam**

Als u de bijbehorende contextpaden en eigenschappen voor de geselecteerde configuratie wilt ophalen, selecteert u **Oplossen**.
