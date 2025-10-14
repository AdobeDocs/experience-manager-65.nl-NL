---
title: Configuraties en de Configuratiebrowser
description: Begrijp AEM configuraties en hoe zij werkruimtemontages in AEM beheren.
exl-id: 1be5849b-748c-48e8-afa8-35a9026c27b3
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1472'
ht-degree: 0%

---

# Configuraties en de Configuratiebrowser {#configuration-browser}

AEM configuraties dienen om instellingen in AEM te beheren en dienen als werkruimten.

## Wat is een Configuratie? {#what-is-a-configuration}

Een configuratie kan vanuit twee verschillende gezichtspunten worden overwogen.

* [&#x200B; een beheerder &#x200B;](#configurations-administrator) gebruikt configuraties als werkruimten binnen AEM om groepen montages te bepalen en te beheren.
* [&#x200B; de ontwikkelaar van A &#x200B;](#configurations-developer) gebruikt het onderliggende configuratiemechanisme dat configuraties uitvoert om montages in AEM voort te zetten en op te zoeken.

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
>Het is alleen mogelijk om configuraties te maken met de Configuratiebrowser als de gebruiker `admin` -rechten heeft. De rechten van de beheerder worden ook vereist om toegangsrechten aan de configuratie toe te wijzen of anders een configuratie te wijzigen.

#### Een configuratie maken {#creating-a-configuration}

Het is eenvoudig om een configuratie in AEM tot stand te brengen door Browser van de Configuratie te gebruiken.

1. Logboek in AEM as a Cloud Service en van het belangrijkste menu selecteert **Hulpmiddelen** > **Algemeen** > **Browser van de Configuratie**.
1. Klik **creëren**.
1. Verstrek a **Titel** en a **Naam** voor uw configuratie.

   ![&#x200B; creeer configuratie &#x200B;](assets/configuration-create.png)

   * De **Titel** zou beschrijvend moeten zijn.
   * De **Naam** wordt de knoopnaam in de bewaarplaats.
      * Het wordt automatisch geproduceerd gebaseerd op de titel en aangepast volgens [&#x200B; AEM noemende overeenkomsten.](/help/sites-developing/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.
1. Controleer het type configuraties dat u wilt toestaan.
   * [Cloudconfiguraties](/help/sites-administering/configurations.md)
   * [Context Hub Segments](/help/sites-administering/segmentation.md)
   * [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
   * [Bewerkbare sjablonen](/help/sites-authoring/templates.md)
1. Klik **creëren**.

>[!TIP]
>
>Configuraties kunnen genest zijn.

#### Configuraties en hun toegangsrechten bewerken {#access-rights}

Als u configuraties als werkruimten beschouwt, kunnen de toegangsrechten op die configuraties worden geplaatst om af te dwingen wie tot die werkruimten kan en niet kan toegang hebben.

1. Logboek in AEM as a Cloud Service en van het belangrijkste menu selecteert **Hulpmiddelen** > **Algemeen** > **Browser van de Configuratie**.
1. Selecteer de configuratie die u wilt wijzigen en dan **Eigenschappen** in de hulpmiddelbar klikken.
1. Selecteer om het even welke extra eigenschappen die u aan de configuratie wilt toevoegen.

   >[!NOTE]
   >
   >Het is niet mogelijk om een functie uit te schakelen wanneer de configuratie is gemaakt.

1. Gebruik de **Efficiënte knoop van Toestemmingen** om een matrijs van rollen te bekijken en welke toestemmingen zij momenteel aan configuraties worden verleend.
   ![&#x200B; Effectieve toestemmingenvenster &#x200B;](assets/configuration-effective-permissions.png)
1. Om nieuwe toestemmingen toe te wijzen, ga de gebruiker of groepsnaam in het **Uitgezochte gebruiker of groep** gebied in **toevoegen Nieuwe Toestemmingen** sectie.
   * Het **Uitgezochte gebruiker of groep** gebied biedt auto-voltooiing aan die op bestaande gebruikers en rollen wordt gebaseerd.
1. Selecteer de gewenste gebruiker of rol in de resultaten die automatisch worden voltooid.
   * U kunt meerdere gebruikers of rollen selecteren.
1. Controleer de toegangsopties die de geselecteerde gebruikers of de rollen zouden moeten hebben en klik **toevoegen**.
   ![&#x200B; voegt toegangsrechten aan een configuratie &#x200B;](assets/configuration-edit.png) toe
1. Herhaal de stappen zodat u gebruikers of rollen kunt selecteren en zonodig extra toegangsrechten kunt toewijzen.
1. Selecteer **sparen &amp; dicht** wanneer u wordt gebeëindigd.

## Configuraties als ontwikkelaar {#configurations-developer}

Als ontwikkelaar, is het belangrijk om te weten hoe AEM as a Cloud Service met configuraties werkt en hoe het configuratieresolutie verwerkt.

### Scheiding van configuratie en inhoud {#separation-of-config-and-content}

Hoewel de [&#x200B; beheerder en de gebruikers aan configuraties als werkplaatsen &#x200B;](#configurations-administrator) kunnen denken om verschillende montages en inhoud te beheren, is het belangrijk om te begrijpen dat de configuraties en de inhoud afzonderlijk door AEM in de bewaarplaats worden opgeslagen en worden beheerd.

* `/content` staat voor alle inhoud.
* `/conf` is de thuisbasis van alle configuraties.

Inhoud verwijst naar de gekoppelde configuratie via een eigenschap `cq:conf` . AEM voert een zoekopdracht uit op basis van de inhoud en de bijbehorende contextafhankelijke eigenschap `cq:conf` om de juiste configuratie te vinden.

### Voorbeeld {#developer-example}

Voor dit voorbeeld, veronderstellen wij u één of andere toepassingscode hebt die in montages DAM geinteresseerd is.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Het uitgangspunt van alle configuratieraadpleging is een inhoudsmiddel, ergens onder `/content`. Dit kan een pagina zijn, een component in een pagina, een element of een DAM-map. Dit is de daadwerkelijke inhoud waarvoor u de juiste configuratie zoekt die in deze context van toepassing is.

Nu met het `Conf` voorwerp in hand, kunt u het specifieke configuratiepunt terugwinnen dat u in geinteresseerd bent. In dit geval is dit `dam/imageserver` . Dit is een verzameling instellingen die betrekking hebben op `imageserver` . De aanroep van `getItem` retourneert een `ValueMap` . Vervolgens leest u een `bgkcolor` -tekenreekseigenschap en geeft u een standaardwaarde van &quot;FFFFFF&quot; op voor het geval dat de eigenschap (of het volledige config-item) niet aanwezig is.

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

In dit voorbeeld kunt u hier een WKND-specifieke DAM-map en een bijbehorende configuratie aannemen. Vanaf die map `/content/dam/wknd` ziet u dat er een tekenreeks-eigenschap met de naam `cq:conf` is die verwijst naar de configuratie die moet worden toegepast voor de substructuur. De eigenschap wordt ingesteld op de `jcr:content` van een elementmap of -pagina. Deze `conf` -koppelingen zijn expliciet, zodat u deze eenvoudig kunt volgen door alleen naar de inhoud in CRXDE te kijken.

Als u naar binnen springt `/conf` , volgt u de verwijzing en ziet u dat er een knooppunt `/conf/wknd` is. Deze configuratie. De zoekopdracht is transparant voor de toepassingscode. De voorbeeldcode heeft er nooit een specifieke verwijzing naar, maar is verborgen achter het `Conf` -object. Welke configuratie van toepassing is, wordt bepaald door de JCR-inhoud.

U ziet dat de configuratie een knooppunt met een vaste naam `settings` bevat dat de items zelf bevat, inclusief de `dam/imageserver` die u in dit geval nodig hebt. Een dergelijk item kan worden beschouwd als een &quot;instellingendocument&quot; en wordt voorgesteld door een `cq:Page` inclusief een `jcr:content` met daarin de werkelijke inhoud.

Tot slot kunt u het bezit `bgkcolor` zien dat de steekproefcode vereist. De `ValueMap` die u terugkrijgt van `getItem` is gebaseerd op het knooppunt `jcr:content` van de pagina.

### Configuratieresolutie {#configuration-resolution}

Het basisvoorbeeld hierboven toonde één enkele configuratie. Maar er zijn veel gevallen waarin u verschillende configuraties wilt hebben, zoals een standaard globale configuratie, een andere configuratie voor elk merk en misschien een specifieke configuratie voor uw subprojecten.

Om dit te steunen, heeft de configuratieraadpleging in AEM een overerving en een reservemechanisme in de volgende orde van voorkeur:

1. `/conf/<siteconfig>/<parentconfig>/<myconfig>`
   * Specifieke config waarnaar wordt verwezen vanuit `cq:conf` ergens in `/content`
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
   * Instellen op een `admin` -rol
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

Configuraties in AEM zijn gebaseerd op Sling Context-Aware Configurations. De bundels van de Verkoop verstrekken de dienst API die kan worden gebruikt om context-bewuste configuraties te krijgen. Context-bewuste configuraties zijn configuraties die met een inhoudsmiddel of een middelboom verwant zijn zoals [&#x200B; in het vorige voorbeeld werd beschreven.](#developer-example)

Voor verdere details over Context-Aware Configuraties, voorbeelden, en hoe te om hen te gebruiken, [&#x200B; zie de het Schelen documentatie.](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html)

### ConfMgr-webconsole {#confmgr-web-console}

Voor het zuiveren en het testen doeleinden, is er a **ConfMgr** Webconsole bij `https://<host>:<port>/system/console/conf`, die configuraties voor een bepaalde weg/een punt kan tonen.

![&#x200B; ConfMgr &#x200B;](assets/configuration-confmgr.png)

Verstrek eenvoudig:

* **Pad van de Inhoud**
* **Punt**
* **Gebruiker**

Om te zien welke configuraties worden opgelost en een steekproefcode ontvangen die die configuraties oplost, uitgezocht **los** op.

### Contextbewuste configuratie webconsole {#context-aware-web-console}

Voor het zuiveren en het testen doeleinden, is er a **context-Aware Configuratie** Webconsole bij `https://<host>:<port>/system/console/slingcaconfig`, die het vragen van context-bewuste configuraties in de bewaarplaats en het bekijken van hun eigenschappen toestaat.

![&#x200B; Context-Aware het Webconsole van de Configuratie &#x200B;](assets/configuration-context-aware-console.png)

Verstrek eenvoudig:

* **Pad van de Inhoud**
* **Naam Config**

Om de bijbehorende contextwegen en de eigenschappen voor de geselecteerde configuratie terug te winnen, uitgezocht **los** op.
