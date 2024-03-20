---
title: Servicegebruikers in Adobe Experience Manager
description: Meer informatie over servicegebruikers in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: ccd8577b-3bbf-40ba-9696-474545f07b84
feature: Security
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 0%

---


# Gebruikers van services in Adobe Experience Manager (AEM) {#service-users-in-aem}

## Overzicht {#overview}

De belangrijkste manier om een administratieve zitting of middeloplosser in AEM te krijgen was het gebruiken van `SlingRepository.loginAdministrative()` en `ResourceResolverFactory.getAdministrativeResourceResolver()` door Sling verschafte methoden.

Geen van deze methoden was echter ontworpen rond de [beginsel van het minst bevoorrecht](https://en.wikipedia.org/wiki/Principle_of_least_privilege). Het maakt het voor een ontwikkelaar te gemakkelijk om niet voor een juiste structuur en de overeenkomstige Niveaus van het Toegangsbeheer (ACLs) voor hun inhoud vroegtijdig te plannen. Als een kwetsbaarheid in zo&#39;n dienst aanwezig is, leidt het vaak tot voorrechtescalaties aan `admin` gebruiker, zelfs als de code zelf geen administratieve voorrechten zou vereisen om te werken.

## Admin-sessies uitfaseren {#how-to-phase-out-admin-sessions}

### Prioriteit 0: Is de functie actief/nodig/verwijderd? {#priority-is-the-feature-active-needed-derelict}

Er kunnen zich gevallen voordoen waarin de beheersessie niet wordt gebruikt of de functie volledig is uitgeschakeld. Als dat het geval is met uw implementatie, verwijdert u de functie helemaal of past u deze aan [NOP-code](https://en.wikipedia.org/wiki/NOP).

### Prioriteit 1: De aanvraagsessie gebruiken {#priority-use-the-request-session}

Wijzig indien mogelijk uw functie, zodat de opgegeven, geverifieerde aanvraagsessie kan worden gebruikt voor het lezen of schrijven van inhoud. Als dit niet mogelijk is, kan het vaak worden bereikt door de onderstaande prioriteiten toe te passen.

### Prioriteit 2: Inhoud herstructureren {#priority-restructure-content}

Veel problemen kunnen worden opgelost door de inhoud te herstructureren. Houd rekening met de volgende eenvoudige regels wanneer u de herstructurering uitvoert:

* **Toegangsbeheer wijzigen**

   * Zorg ervoor dat de gebruikers of de groepen die werkelijk toegang nodig hebben daadwerkelijk toegang hebben;

* **Inhoudsstructuur verfijnen**

   * Verplaats het naar andere plaatsen, bijvoorbeeld, waar de toegangscontrole de beschikbare verzoekzittingen aanpast;
   * Wijzig de granulariteit van de inhoud.

* **Vernieuw uw code om een juiste service te zijn**

   * Verplaats de bedrijfslogica van code JSP naar de dienst. Dit maakt verschillende inhoudmodellen mogelijk.

Ook, zorg ervoor dat om het even welke nieuwe eigenschappen u ontwikkelt zich aan deze principes houdt:

* **Beveiligingsvereisten moeten de inhoudstructuur bepalen**

   * Het beheer van toegangsbeheer moet natuurlijk zijn
   * Toegangscontrole moet worden afgedwongen door de gegevensopslagplaats, niet door de toepassing

* **Nodetypes gebruiken**

   * De set eigenschappen beperken die kan worden ingesteld

* **Privacy-instellingen respecteren**

   * Als er privéprofielen zijn, kunt u bijvoorbeeld de profielafbeelding, e-mail of volledige naam die op de privécomputer is gevonden, niet weergeven `/profile` knooppunt.

## Strikte toegangscontrole {#strict-access-control}

Of u toegangsbeheer terwijl het herstructureren van inhoud toepast of wanneer u het voor een nieuwe de dienstgebruiker doet, moet u strikt mogelijke ACLs toepassen. Gebruik alle mogelijke toegangsbeheerfaciliteiten:

* Bijvoorbeeld in plaats van `jcr:read` op `/apps`alleen toepassen op `/apps/*/components/*/analytics`

* Gebruiken [beperkingen](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html)

* ACLs voor knooptypes toepassen
* Machtigingen beperken

   * Als u bijvoorbeeld alleen eigenschappen wilt schrijven, moet u de opdracht `jcr:write` toestemming; gebruik `jcr:modifyProperties` in

## Gebruikers en toewijzingen van services {#service-users-and-mappings}

Als het bovenstaande ontbreekt, biedt Sling 7 de dienst van de Toewijzing van de Gebruiker van de Dienst aan, die u een bundel-aan-gebruiker afbeelding en twee overeenkomstige API methodes laat vormen:

* [`SlingRepository.loginService()`](https://sling.apache.org/apidocs/sling7/org/apache/sling/jcr/api/SlingRepository.html#loginService-java.lang.String-java.lang.String-)
* [`ResourceResolverFactory.getServiceResourceResolver()`](https://sling.apache.org/apidocs/sling7/org/apache/sling/api/resource/ResourceResolverFactory.html#getServiceResourceResolver-java.util.Map-)

De methodes keren een zitting/middeloplosser met de voorrechten van een gevormde slechts gebruiker terug. Deze methoden hebben de volgende kenmerken:

* Zij staan kaartdiensten aan gebruikers toe
* Zij maken het mogelijk om de gebruikers van de subdienst te bepalen
* Het centrale configuratiepunt is: `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl`
* `service-id` = `service-name` [&quot;:&quot; subservice-name]

* `service-id` is toegewezen aan een resourceoplosser en/of JCR-opslaggebruikers-id voor verificatie
* `service-name` is de symbolische naam van de bundel die de dienst verleent

## Overige Recommendations {#other-recommendations}

### De admin-sessie vervangen door een service-gebruiker {#replacing-the-admin-session-with-a-service-user}

Een servicegebruiker is een JCR-gebruiker zonder wachtwoord en met een minimale set rechten die nodig zijn om een bepaalde taak uit te voeren. Als er geen wachtwoord is ingesteld, kan u zich niet aanmelden bij een servicegebruiker.

Een manier om een administratieve zitting te verwerpen is het door de zittingen van de de dienstgebruiker te vervangen. Het zou ook door veelvoudige subservice gebruikers indien nodig kunnen worden vervangen.

Als u de beheersessie wilt vervangen door een servicegebruiker, moet u de volgende stappen uitvoeren:

1. Identificeer de noodzakelijke toestemmingen voor uw dienst, die het beginsel van minste toestemming in mening houden.
1. Controleer of er al een gebruiker beschikbaar is met exact de juiste instellingen voor machtigingen. Maak een gebruiker van de systeemservice als geen bestaande gebruiker aan uw behoeften voldoet. RTC is nodig om een servicegebruiker te maken. Soms is het handig om meerdere gebruikers van subservices te maken (bijvoorbeeld voor schrijven en voor lezen) om de toegang nog verder te compartimenteren.
1. Opstelling en test ACEs voor uw gebruiker.
1. Voeg een `service-user` toewijzing voor uw dienst en voor `user/sub-users`

1. Maak de verkoopfunctie van de servicegebruiker beschikbaar voor uw bundel: werk de laatste versie van `org.apache.sling.api`.

1. Vervang de `admin-session` in uw code met de `loginService` of `getServiceResourceResolver` API&#39;s.

## Een servicegebruiker maken {#creating-a-new-service-user}

Nadat u hebt gecontroleerd dat geen gebruiker in de lijst met AEM gebruikers van toepassing is voor uw gebruiksscenario en de bijbehorende RTC-problemen zijn goedgekeurd, voegt u de nieuwe gebruiker toe aan de standaardinhoud.

De aanbevolen aanpak is om een servicegebruiker te maken die de verkenner van de repository kan gebruiken op *https://&lt;server>:&lt;port>/crx/explorer/index.jsp*

Het doel is een geldige `jcr:uuid` eigenschap die verplicht is om de gebruiker te maken via een installatie van een inhoudspakket.

U kunt servicegebruikers maken door:

1. Ga naar de verkenner van de repository op *https://&lt;server>:&lt;port>/crx/explorer/index.jsp*
1. Aanmelden als beheerder door op de knop **Aanmelden** in de linkerbovenhoek van het scherm.
1. Maak vervolgens een systeemgebruiker en geef deze een naam. Als u de gebruiker als een systeemgebruiker wilt maken, stelt u het tussentijdse pad in als `system` en voeg optionele submappen toe, afhankelijk van uw behoeften:

   ![chlimage_1-102](assets/chlimage_1-102a.png)

1. Controleer of het systeemgebruikersknooppunt er als volgt uitziet:

   ![chlimage_1-103](assets/chlimage_1-103a.png)

   >[!NOTE]
   >
   >Er zijn geen mixintypes verbonden aan de dienstgebruikers. Dit betekent dat er geen beleid van de toegangscontrole voor systeemgebruikers is.

Wanneer u het corresponderende .content.xml toevoegt aan de inhoud van uw bundel, moet u ervoor zorgen dat u de `rep:authorizableId` en dat het primaire type `rep:SystemUser`. Het moet er als volgt uitzien:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:rep="internal"
    jcr:primaryType="rep:SystemUser"
    jcr:uuid="4917dd68-a0c1-3021-b5b7-435d0044b0dd"
    rep:principalName="authentication-service"
    rep:authorizableId="authentication-service"/>
```

## Het toevoegen van een configuratieamendement aan de configuratie ServiceUserMapper {#adding-a-configuration-amendment-to-the-serviceusermapper-configuration}

Om een afbeelding van uw dienst aan de overeenkomstige Gebruikers van het Systeem toe te voegen, creeer een fabrieksconfiguratie voor [`ServiceUserMapper`](https://sling.apache.org/apidocs/sling7/org/apache/sling/serviceusermapping/ServiceUserMapper.html) service. Om dit modulaire te houden, kan dergelijke configuratie worden verstrekt gebruikend [Sling-wijzigingsmechanisme](https://issues.apache.org/jira/browse/SLING-3578). U wordt aangeraden dergelijke configuraties met uw bundel te installeren door [Eerste inhoud bij verkoop laden](https://sling.apache.org/documentation/bundles/content-loading-jcr-contentloader.html):

1. Een submap SLING-INF/content maken onder de map src/main/resources van uw bundel
1. Maak in deze map een bestand met de naam org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.modified-&lt;some unique=&quot;&quot; name=&quot;&quot; for=&quot;&quot; your=&quot;&quot; factory=&quot;&quot; configuration=&quot;&quot;>.xml met de inhoud van uw fabrieksconfiguratie (met inbegrip van alle afbeeldingen van de subservicestgebruiker). Voorbeeld:

1. Een `SLING-INF/content` map onder de `src/main/resources` map van de bundel;
1. Maak in deze map een bestand `named org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-<a unique name for your factory configuration>.xml` met de inhoud van uw fabrieksconfiguratie, inclusief alle toewijzingen van gebruikers van de subservice.

   Voor illustratiedoeleinden gebruikt u het bestand `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-com.adobe.granite.auth.saml.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <node>
       <primaryNodeType>sling:OsgiConfig</primaryNodeType>
       <property>
           <name>user.default</name>
           <value></value>
       </property>
       <property>
           <name>user.mapping</name>
           <values>
               <value>com.adobe.granite.auth.saml=authentication-service</value>
           </values>
       </property>
   </node>
   ```

1. Verwijs de het Verkopen aanvankelijke inhoud in de configuratie van `maven-bundle-plugin` in de `pom.xml` van uw bundel. Voorbeeld:

   ```xml
   <Sling-Initial-Content>
      SLING-INF/content;path:=/libs/system/config;overwrite:=true;
   </Sling-Initial-Content>
   ```

1. Installeer de bundel en controleer of de fabrieksconfiguratie is geïnstalleerd. U kunt dit doen door:

   * Ga naar de webconsole op *https://serverhost:serveraddress/system/console/configMgr*
   * Zoeken naar **Wijziging van de Gebruikerstoewijzingsservice Apache Sling Service**
   * Klik de verbinding zodat kunt u zien of is de juiste configuratie op zijn plaats.

## Werken met gedeelde sessies in services {#dealing-with-shared-sessions-in-services}

roept aan `loginAdministrative()` worden vaak samen met gedeelde sessies weergegeven. Deze zittingen worden verworven bij de dienstactivering en slechts het programma geopend nadat de dienst wordt tegengehouden. Hoewel dit gebruikelijk is, leidt het tot twee problemen:

* **Veiligheid:** Dergelijke beheersessies worden gebruikt om bronnen of andere objecten die aan de gedeelde sessie zijn gebonden, in cache te plaatsen en terug te sturen. Later in de vraagstapel konden deze voorwerpen aan zittingen of middeloplossers met opgeheven voorrechten worden aangepast. Het is vaak niet duidelijk aan de bezoeker dat het een adminzitting is waarmee zij werken.
* **Prestaties:** In eiken kunnen gedeelde sessies prestatieproblemen veroorzaken en het wordt afgeraden deze te gebruiken.

De meest voor de hand liggende oplossing voor het veiligheidsrisico is eenvoudigweg de vervanging van de `loginAdministrative()` bellen met een `loginService()` een voor een gebruiker met beperkte rechten. Dit heeft echter geen invloed op een mogelijke verslechtering van de prestaties. Een mogelijkheid om dat te beperken is alle gevraagde informatie te verpakken in een object dat geen koppeling heeft met de sessie. Maak vervolgens de sessie op verzoek (of vernietigt deze).

De aanbevolen aanpak bestaat erin de API van de service te herordenen om de beller controle te geven over het maken/vernietigen van de sessie.

## Administratieve sessies in JSPs {#administrative-sessions-in-jsps}

JSPs kan niet gebruiken `loginService()`, omdat er geen bijbehorende service is. Administratieve sessies in JSP&#39;s zijn echter doorgaans een teken van een schending van het MVC-paradigma.

Dit kan op twee manieren worden opgelost:

1. De inhoud zodanig herstructureren dat de inhoud met de gebruikerssessie kan worden gemanipuleerd;
1. Het halen van de logica aan de dienst die API verstrekt die dan door JSP kan worden gebruikt.

De eerste methode heeft de voorkeur.

## Verwerkingsgebeurtenissen, replicatievoorprocessoren en taken {#processing-events-replication-preprocessors-and-jobs}

Bij het verwerken van gebeurtenissen of taken, en soms ook van workflows, gaat de bijbehorende sessie die de gebeurtenis heeft geactiveerd, verloren. Dit leidt ertoe dat gebeurtenismanagers en baanbewerkers vaak administratieve zittingen gebruiken om hun werk te doen. Er zijn verschillende denkbare benaderingen om dit probleem op te lossen, elk met hun voor- en nadelen:

1. Geef de `user-id` in de gebeurtenislading en gebruik imitatie.

   **Voordelen:** Eenvoudig in gebruik.

   **Nadelen:** Stilstaand gebruik `loginAdministrative()`. Een aanvraag die al is geverifieerd, wordt opnieuw geverifieerd.

1. Creeer of hergebruik een de dienstgebruiker die toegang tot de gegevens heeft.

   **Voordelen:** In overeenstemming met het huidige ontwerp. Moet minimaal worden gewijzigd.

   **Nadelen:** Vereist krachtige de dienstgebruikers om flexibel te zijn, wat tot voorrechtescalaties kan gemakkelijk leiden. Hiermee wordt het beveiligingsmodel omzeild.

1. Geef een serialisatie van de `Subject` in de gebeurtenislading, en creeer `ResourceResolver` op basis van dat onderwerp. Een voorbeeld hiervan zou de JAAS gebruiken `doAsPrivileged` in de `ResourceResolverFactory`.

   **Voordelen:** Schone implementatie vanuit veiligheidsoogpunt. Het vermijdt opnieuw authentificatie en het werkt met de originele voorrechten. Beveiligingsrelevante code is transparant voor de consument van het evenement.

   **Nadelen:** Needs refactoring. Het feit dat de veiligheidsrelevante code transparant is voor de consument van het evenement kan ook tot problemen leiden.

De derde aanpak is de voorkeurstechniek.

## Workflowprocessen {#workflow-processes}

Binnen de implementaties van het werkschemaproces, wordt de overeenkomstige gebruikerszitting die het werkschema teweegbracht verloren. Dit leidt tot werkschemaprocessen die vaak administratieve zittingen gebruiken om hun werk uit te voeren.

Om deze problemen op te lossen, wordt aanbevolen om dezelfde aanpak te kiezen als in [Verwerkingsgebeurtenissen, replicatievoorprocessoren en taken](/help/sites-administering/security-service-users.md#processing-events-replication-preprocessors-and-jobs) worden gebruikt.

## Verkoopprocessors en verwijderde POSTEN {#sling-post-processors-and-deleted-pages}

Er zijn een paar administratieve zittingen die in de implementatie van de bewerker van de POST worden gebruikt. Meestal worden beheersessies gebruikt om toegang te krijgen tot knooppunten die in afwachting zijn van verwijdering binnen de POST die wordt verwerkt. Daarom zijn ze niet meer beschikbaar via de aanvraagsessie. Een knooppunt dat moet worden verwijderd, kan worden benaderd om metagegevens bekend te maken die anders niet toegankelijk zouden moeten zijn.
