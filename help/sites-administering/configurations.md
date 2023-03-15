---
title: Configuraties en de Configuratiebrowser
description: Begrijp AEM configuraties en hoe zij werkruimtemontages in AEM beheren.
exl-id: 1be5849b-748c-48e8-afa8-35a9026c27b3
source-git-commit: 84b16dd1a60f731b568dd87ef89699875cb86596
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 0%

---

# Configuraties en de Configuratiebrowser {#configuration-browser}

AEM configuraties dienen om instellingen in AEM te beheren en dienen als werkruimten.

## Wat is een Configuratie? {#what-is-a-configuration}

Een configuratie kan vanuit twee verschillende gezichtspunten worden overwogen.

* [Beheerder](#configurations-administrator) gebruikt configuraties als werkruimten binnen AEM om groepen montages te bepalen en te beheren.
* [Een ontwikkelaar](#configurations-developer) gebruikt het onderliggende configuratiemechanisme dat configuraties uitvoert om montages in AEM voort te zetten en op te zoeken.

Samenvattend: vanuit het standpunt van een beheerder, zijn de configuraties hoe u werkruimten creeert om montages in AEM te beheren, terwijl de ontwikkelaar zou moeten begrijpen hoe AEM deze configuraties binnen de bewaarplaats gebruikt en beheert.

Configuraties hebben, ongeacht uw perspectief, twee hoofddoelen in AEM:

* Configuraties bieden bepaalde functies voor bepaalde groepen gebruikers.
* Configuraties definiëren de toegangsrechten voor deze functies.

## Configuraties als beheerder {#configurations-administrator}

De AEM beheerder en auteurs kunnen configuraties als werkruimten beschouwen. Deze werkruimten kunnen worden gebruikt om groepen instellingen en de bijbehorende inhoud voor organisatorische doeleinden te verzamelen door toegangsrechten voor die functies te implementeren.

Configuraties kunnen worden gemaakt voor vele verschillende functies in AEM.

* [Cloudconfiguraties](/help/sites-administering/configurations.md)
* [Context Hub Segments](/help/sites-administering/segmentation.md)
* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Bewerkbare sjablonen](/help/sites-authoring/templates.md)

### Voorbeeld {#administrator-example}

Een beheerder kan bijvoorbeeld twee configuraties voor bewerkbare sjablonen maken.

* WKND-generaal
* WKND-Magazine

De beheerder kan algemene paginasjablonen dan maken met behulp van de WKND-Algemene configuratie en vervolgens sjablonen die specifiek zijn voor het tijdschrift onder WKND-Magazine.

De beheerder kan vervolgens de WKND-General koppelen aan alle inhoud van de WKND-site. Nochtans zou de configuratie WKND-Magazine slechts met de tijdschriftplaats worden geassocieerd.

Op deze manier:

* Wanneer een inhoudsauteur een nieuwe pagina voor het tijdschrift maakt, kan de auteur kiezen uit algemene sjablonen (WKND-Algemeen) of tijdschriftsjablonen (WKND-Magazine).
* Wanneer een auteur van inhoud een nieuwe pagina maakt voor een ander gedeelte van de site dat niet het tijdschrift is, kan de auteur alleen kiezen uit de algemene sjablonen (WKND-Algemeen).

De gelijkaardige montages zijn mogelijk niet alleen voor Bewerkbare Malplaatjes maar ook voor de Configuraties van de Wolk, Segmenten ContextHub, en Modellen van het Fragment van de Inhoud.

### De configuratiebrowser gebruiken {#using-configuration-browser}

Browser van de Configuratie staat een beheerder toe om, toegangsrechten aan configuraties in AEM gemakkelijk tot stand te brengen te beheren en te vormen.

>[!NOTE]
>
>Het is alleen mogelijk om configuraties te maken met de Configuration Browser als de gebruiker `admin` rechten. `admin` de rechten worden ook vereist om toegangsrechten aan de configuratie toe te wijzen of anders een configuratie te wijzigen.

#### Een configuratie maken {#creating-a-configuration}

Het is zeer eenvoudig om een nieuwe configuratie in AEM tot stand te brengen door Browser van de Configuratie te gebruiken.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Gereedschappen** -> **Algemeen** -> **Configuratiebrowser**.
1. Tik of klik op **Maken**.
1. Een **Titel** en **Naam** voor uw configuratie.

   ![Configuratie maken](assets/configuration-create.png)

   * De **Titel** moeten beschrijvend zijn.
   * De **Naam** wordt de knooppuntnaam in de repository.
      * Het wordt automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies.](/help/sites-developing/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.
1. Controleer het type configuraties dat u wilt toestaan.
   * [Cloudconfiguraties](/help/sites-administering/configurations.md)
   * [Context Hub Segments](/help/sites-administering/segmentation.md)
   * [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
   * [Bewerkbare sjablonen](/help/sites-authoring/templates.md)
1. Tik of klik op **Maken**.

>[!TIP]
>
>Configuraties kunnen genest zijn.

#### Configuraties en hun toegangsrechten bewerken {#access-rights}

Als u configuraties als werkruimten beschouwt, kunnen de toegangsrechten op die configuraties worden geplaatst om af te dwingen wie tot die werkruimten kan en mag toegang hebben.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Gereedschappen** -> **Algemeen** -> **Configuratiebrowser**.
1. Selecteer de configuratie die u wilt wijzigen en tik of klik op **Eigenschappen** in de werkbalk.
1. Selecteer om het even welke extra eigenschappen u aan de configuratie wilt toevoegen
   >[!NOTE]
   >
   >Het is niet mogelijk om een functie uit te schakelen wanneer de configuratie is gemaakt.
1. Gebruik de **Effectieve machtigingen** knoop om een matrijs van rollen te bekijken en welke toestemmingen zij momenteel aan configuraties worden verleend.
   ![venster Effectieve machtigingen](assets/configuration-effective-permissions.png)
1. Als u nieuwe machtigingen wilt toewijzen, voert u de naam van de gebruiker of groep in het dialoogvenster **Gebruiker of groep selecteren** in het **Nieuwe machtigingen toevoegen** sectie.
   * De  **Gebruiker of groep selecteren** het veld biedt automatisch aanvullen op basis van bestaande gebruikers en rollen.
1. Selecteer de gewenste gebruiker of rol in de resultaten die automatisch worden voltooid.
   * U kunt meerdere gebruikers of rollen selecteren.
1. Controleer de toegangsopties die de geselecteerde gebruiker(s) of rol(en) moet(en) hebben en klik op **Toevoegen**.
   ![Toegangsrechten toevoegen aan een configuratie](assets/configuration-edit.png)
1. Herhaal de stappen om gebruikers of rollen te selecteren en zo nodig extra toegangsrechten toe te wijzen.
1. Tik of klik op **Opslaan en sluiten** wanneer gereed.

## Configuraties als ontwikkelaar {#configurations-developer}

Als ontwikkelaar, is het belangrijk om te weten hoe AEM as a Cloud Service met configuraties werkt en hoe het configuratieresolutie verwerkt.

### Scheiding van configuratie en inhoud {#separation-of-config-and-content}

Hoewel de [beheerders en gebruikers kunnen configuraties als werkplekken zien](#configurations-administrator) om verschillende instellingen en inhoud te beheren is het belangrijk te begrijpen dat configuraties en inhoud afzonderlijk worden opgeslagen en beheerd door AEM in de opslagplaats.

* `/content` is home aan alle inhoud.
* `/conf` is huis aan alle configuratie.

Content verwijst naar de bijbehorende configuratie via een `cq:conf` eigenschap. AEM voert een zoekopdracht uit op basis van de inhoud en het is contextueel `cq:conf` eigenschap om de juiste configuratie te vinden.

### Voorbeeld {#developer-example}

Voor dit voorbeeld, veronderstellen wij u één of andere toepassingscode hebt die in montages DAM geinteresseerd is.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Het uitgangspunt van alle configuratieraadpleging is een inhoudsmiddel, gewoonlijk ergens onder `/content`. Dit kan een pagina zijn, een component in een pagina, een element of een DAM-map. Dit is de inhoud waarvoor we op zoek zijn naar de juiste configuratie die in deze context van toepassing is.

Nu met de `Conf` -object in hand, kunnen we het specifieke configuratieitem ophalen waarin we geïnteresseerd zijn. In dit geval is `dam/imageserver`, dat een verzameling instellingen is die betrekking hebben op de `imageserver`. De `getItem` call retourneert een `ValueMap`. Daarna lezen we een `bgkcolor` string bezit en verstrekken een standaardwaarde van &quot;FFFFFF&quot;voor het geval dat het bezit (of het volledige config punt) niet aanwezig is.

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

In dit voorbeeld nemen we hier een WKND-specifieke DAM-map en een bijbehorende configuratie aan. Vanaf die map `/content/dam/wknd`, zullen wij zien dat er een koordbezit genoemd is `cq:conf` dat verwijst naar de configuratie die voor de substructuur zou moeten van toepassing zijn. De eigenschap wordt meestal ingesteld op de knop `jcr:content` van een elementmap of -pagina. Deze `conf` De verbindingen zijn uitdrukkelijk, zodat is het gemakkelijk om hen te volgen door de inhoud in CRXDE te bekijken.

Binnenin pompen `/conf`, volgen we de referentie en zien we dat er een `/conf/wknd` knooppunt. Dit is een configuratie. De zoekopdracht is volledig transparant voor de toepassingscode. De voorbeeldcode heeft er nooit een specifieke referentie naar, maar is verborgen achter het `Conf` object. Welke configuratie van toepassing is, wordt volledig gecontroleerd door de inhoud JCR.

We zien dat de configuratie een vaste naam bevat `settings` knooppunt dat de werkelijke items bevat, inclusief de `dam/imageserver` in ons geval is dat nodig . Een dergelijk item kan worden beschouwd als een &quot;instellingendocument&quot; en wordt gewoonlijk aangeduid met een `cq:Page` met inbegrip van `jcr:content` de feitelijke inhoud bezitten.

Tot slot zien we de eigenschap `bgkcolor` dat onze voorbeeldcode nodig heeft. De `ValueMap` we komen terug van `getItem` is gebaseerd op de pagina&#39;s `jcr:content` knooppunt.

### Configuratieresolutie {#configuration-resolution}

Het basisvoorbeeld hierboven toonde één enkele configuratie. Maar er zijn veel gevallen waarin u verschillende configuraties wilt hebben, zoals een standaard globale configuratie, een andere configuratie voor elk merk en misschien een specifieke configuratie voor uw subprojecten.

Om dit te steunen heeft de configuratieraadpleging in AEM overerving en fallback mechanisme in de volgende orde van voorkeur:

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
   * Gewoonlijk algemene standaardinstellingen voor uw installatie
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

Klikken **Oplossen** om te zien welke configuraties worden opgelost en steekproefcode te ontvangen die die configuraties zal oplossen.

### Contextbewuste configuratie webconsole {#context-aware-web-console}

Voor foutopsporing- en testdoeleinden is er een **Contextbewuste configuratie** webconsole op `https://<host>:<port>/system/console/slingcaconfig`, waarmee u contextbewuste configuraties in de opslagplaats kunt opvragen en hun eigenschappen kunt bekijken.

![Contextbewuste configuratie webconsole](assets/configuration-context-aware-console.png)

Verstrek eenvoudig:

* **Inhoudspad**
* **Configuratienaam**

Klikken **Oplossen** om de bijbehorende contextwegen en eigenschappen voor de geselecteerde configuratie terug te winnen.
