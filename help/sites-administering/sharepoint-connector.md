---
title: SharePoint Connector
description: Day JCR Connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 10ea7d2e-6e44-4d5c-a2b2-63c73b18f172
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 0%

---

# SharePoint Connector{#sharepoint-connector}

Dit artikel bevat informatie over de Adobe JCR Connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0.

De SharePoint-connector ondersteunt de volgende basisfuncties:

* Inhoud en metagegevens lezen uit SharePoint.
* SharePoint-beveiligingsinstellingen bevestigen voor benaderde inhoud door native SharePoint-verificatie en -autorisatie toe te passen
* Inhoudsintegratie met Inhoudszoeker
* Met AEM componenten, zoals External Resource, SharePoint-afbeeldingen en video&#39;s weergeven
* SharePoint synchroniseren met AEM Assets

Alle functies worden geïmplementeerd met de native SharePoint-webservices als de interface naar SharePoint-inhoud en -services.

>[!NOTE]
>
>SharePoint Connector wordt ook ondersteund met AEM 6.1 service pack 2. De connector ondersteunt geen virtuele opslagplaats meer en kan daarom niet worden gemonteerd. Als u toegang wilt krijgen tot de SharePoint-opslagplaats met Java API&#39;s, gebruikt u de JCR-opslagfunctie van de SharePoint-connector in uw project.
>
>Installatie-, configuratie-, beheer- en IT-bewerkingen van de SharePoint-server en de bijbehorende IT-infrastructuur vallen buiten het bereik van dit document. Zie documentatie van leveranciers op [SharePoint](https://www.microsoft.com/sharepoint) voor informatie over deze onderwerpen. De aansluiting vereist dat deze delen van de infrastructuur correct worden geïnstalleerd, geconfigureerd en gebruikt.
>

## Aan de slag {#getting-started}

Ga als volgt te werk om aan de slag te gaan met de connector:

* Zorg ervoor dat u ten minste Java 7 hebt geïnstalleerd.
* Download het distributiebestand van het schakelaarpakket van de Distributie van de Software.
* Een geldige kopie maken *license.properties* bestand naar de map die het *cq-quickstart-6.4.0.jar* bestand.

* Dubbelklik op het .jar-bestand om het AEM te starten of start het bestand via de opdrachtregel.
* Installeer het aansluitingspakket via Package Manager.
* Configureer de verbindingsopties.

## SharePoint-connector installeren {#installing-sharepoint-connector}

De connector is een inhoudspakket dat eenvoudige installatie mogelijk maakt. Installeer het pakket met Package Manager en stel vervolgens de URL van de SharePoint-server en andere configuratieopties in. De SharePoint-inhoud is beschikbaar in de AEM repository.

### Installatievereisten {#installation-requirements}

De schakelaar vereist het volgende:

* Java Runtime Environment 1.7 of hoger
* SharePoint Web Services beschikbaar via het netwerk
* URL SharePoint-server
* Gebruikersreferenties en machtigingen voor CRX- en SharePoint-opslagruimten
* [Ondersteunde platforms](#supported-platforms)

De SharePoint-aansluiting kan worden gedownload van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-17673).

### Ondersteunde platforms {#supported-platforms}

De schakelaar steunt het volgende:

* AEM versies:

   * AEM 6.4, 6.3

* Microsoft SharePoint-versies:

   * Microsoft Office SharePoint Server (MOSS) 2010
   * Microsoft Office SharePoint Server (MOSS) 2013

* Als u steun voor douaneplaatsingen van de schakelaar (OEM, speciale vereisten, aangepaste authentificatiemethodes) vereist, contacteer het bureau van de Adobe voor uw regio.

>[!NOTE]
>
>De connector ondersteunt alleen configuraties die officieel door Microsoft worden ondersteund. Zie [MOSS 2010](https://technet.microsoft.com/en-us/library/cc262485(office.14).aspx) en [MOSS 2013](https://technet.microsoft.com/en-us/library/cc262485.aspx) systeemvereisten.

### Standaardinstallatie {#standard-installation}

Softwaredistributie wordt gebruikt om productfuncties, voorbeelden en hotfixes te distribueren. Zie voor meer informatie de [Documentatie voor softwaredistributie](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html#software-distribution).


#### Integreren met AEM {#integrating-with-aem}

Om het pakket van de schakelaarinhoud te installeren.

1. Open een kaartje van de Steun van de Adobe om om het schakelaarkenmerkpak te verzoeken.
1. Download het pakket wanneer het beschikbaar is en open dan de Manager van het Pakket voor uw AEM instantie.
1. Klikken **Installeren** op de pagina met pakketbeschrijving.
1. Van de **Pakket installeren** dialoogvenster, klikt u op **Installeren**.

   **Opmerking**: Controleer of u bent aangemeld als beheerder.

1. Wanneer het pakket is geïnstalleerd, klikt u **Sluiten**.

## SharePoint-connector configureren {#configuring-sharepoint-connector}

Nadat u de SharePoint-connector hebt geïnstalleerd, configureert u de toepassing en de SharePoint-lagen voor de connector.

Stel de URL van de SharePoint-server in om de JCR-compatibiliteit van uw SharePoint-opslagruimte te garanderen. U kunt extra parameters instellen om de verbinding met de SharePoint-server te configureren. Configureer bovendien verificatie met de SharePoint-connector.

### De verbinding met de SharePoint-server configureren {#configuring-the-connection-with-the-sharepoint-server}

Voer de volgende stappen uit om de URL van de SharePoint-server en de geavanceerde opties in te stellen:

1. Navigeer naar de OSGi Management Console: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Zoeken naar **Day JCR Connector voor Microsoft Sharepoint** bundel.
1. Bewerk de configuratiewaarden.
1. Stel de URL van de SharePoint-server in als de waarde van **Werkruimten**.
1. Klikken **Opslaan**.

![chlimage_1-62](assets/chlimage_1-62.png)

Parameters &#39;Werkruimten&#39; en &#39;Standaardnaam werkruimte&#39;:

Standaard stelt de connector één JCR-werkruimte beschikbaar. De SharePoint-server die door deze werkruimte beschikbaar wordt gemaakt, wordt ingesteld via de configuratieparameter &#39;SharePoint Server URL&#39;.

De schakelaar kan ook voor veelvoudige werkruimten worden gevormd. In dit geval wordt elke werkruimte gekoppeld aan de URL van de respectievelijke SharePoint-server die via de werkruimte beschikbaar wordt gemaakt. Als u een werkruimte wilt toevoegen, voegt u een werkruimtedefinitie toe aan de parameter Werkruimten. Een werkruimtedefinitie heeft de volgende indeling:
`<name>`= `<url>` waar
`<name>` is de naam van de JCR-werkruimte en
`<url>` is de URL van de SharePoint-server voor die werkruimte.

Voer in AEM nog een stap uit, apart van de bovenstaande configuratiestappen. LIJST VAN GEWENSTE PERSONEN &#39;**com.day.cq.dam.cq-dam-jcr-connectors** bundel.

Voer de volgende stappen uit om bundels in AEM te lijsten van gewenste personen:

1. Ga naar de OSGi Management Console: http://localhost:4502/system/console/configMgr.
1. Zoek naar de service &quot;Apache Sling Login Admin Whitelist&quot;.
1. Selecteren **De whitelist omzeilen**.
1. Toevoegen `com.day.cq.dam.cq-dam-jcr-connectors` in whitelist-bundels standaard
1. Klik op Opslaan.

![chlimage_1-82](assets/chlimage_1-82a.png)

>[!NOTE]
>
>Als u meerdere werkruimten configureert, geeft u de naam van de standaardwerkruimte op in de parameter Standaardnaam werkruimte.

Zie voor meer informatie over parameters die betrekking hebben op verificatie [Verificatie](/help/sites-administering/sharepoint-connector.md#configuring-authentication).

### De installatie van SharePoint controleren {#verifying-the-sharepoint-setup}

Nadat u de schakelaar vormt, verifieer het volgende:

* SharePoint-server wordt uitgevoerd en de webservices zijn toegankelijk voor de verbindingsinstantie
* SharePoint-gebruikersgegevens zijn geldig en de gebruiker beschikt over de vereiste SharePoint-machtigingen
* De schakelaar is geïnstalleerd en behoorlijk gevormd

### DAM-synchronisatie configureren met de SharePoint-server {#configuring-dam-sync-with-the-sharepoint-server}

Voer de volgende stappen uit om de SharePoint-middelen te synchroniseren met AEM:

1. Navigeer naar de OSGi Management Console: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Zoek naar de service &quot;Default DAMAssetSynchronization&quot;.
1. Bewerk de configuratiewaarden.
1. Stel de gebruikersnaam en het bijbehorende wachtwoord in van de gebruiker die toegang heeft tot de SharePoint-site.
1. Klik op Opslaan.

Schakel de DAM Sync Service in, die standaard is uitgeschakeld:

1. Navigeer naar de componenten van de Console van OSGi Web: [http://localhost:4502/system/console/components](http://localhost:4502/system/console/components)
1. Zoek naar &quot;com.day.cq.dam.jcrconnectors.impl.AssetSynchronizationService.&quot;
1. Klik op Inschakelen.

Naar keuze, kunt u de vertraging van de Synchronisatie tussen verschillende synchronisatiecycli vormen:

1. Navigeer naar de OSGi Management Console: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
1. Zoek naar &quot;DAY CQ DAM JCR Connector Asset Synchronization Service.&quot;
1. Bewerk de configuratiewaarden.
1. Stel de waarde van de synchronisatieperiode in (in seconden).
1. Klik op Opslaan.

### Verificatie configureren {#configuring-authentication}

SharePoint omvat de Klassieke en op eisen gebaseerde authentificatiemethodes, die allebei de volgende authentificatietypen steunen:

* Basis
* Op Forms gebaseerd

Met name zijn de volgende verificatietypen beschikbaar:

* Klassiek-basis
* Op basis van Classic-Forms
* Vorderingen — Basis
* Op Forms gebaseerde claims

De AEM JCR Connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0. ondersteunt op claims gebaseerde verificatie (wat door Microsoft wordt voorgesteld), die in de volgende modi werkt:

* **Basic-/NTLM-verificatie**: De schakelaar probeert eerst om het gebruiken van basisauthentificatie te verbinden. Als deze optie niet beschikbaar is, wordt overgeschakeld naar verificatie op basis van NTLM.
* **Op Forms gebaseerde verificatie**: SharePoint valideert gebruikers op basis van referenties die gebruikers in een aanmeldingsformulier typen (doorgaans een webpagina). Het systeem geeft een teken voor voor authentiek verklaarde verzoeken uit die een sleutel voor het opnieuw vestigen van de identiteit voor verdere verzoeken bevat.

**Op Forms gebaseerde verificatie configureren**

Ga naar: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)

1. Klik op OSGI > Configuration
1. Zoeken naar &quot;Day JCR Connector for Microsoft Sharepoint&quot;
1. Klik op &quot;De configuratiewaarden bewerken&quot;
1. Stel de waarde van &#39;Sharepoint Connection Factory&#39; in op &#39;com.day.crx.spi.sharepoint.security.FormsBasedAuthenticationConnectionFactory&#39;
1. Klikken **Opslaan**.

**Basisverificatie configureren (Windows)**

1. [Tokenverificatie uitschakelen](#disable-token-authentication).
1. Ga naar [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).
1. Klik op OSGI > Configuratie.
1. Zoeken naar **Day JCR Connector voor Microsoft Sharepoint**.
1. Klik op `Edit the configuration values`.
1. Stel de waarde van SharePoint Connection Factory in op `com.day.crx.spi.sharepoint.security.WindowsAuthenticationConnectionFactory`.
1. Klikken **Opslaan**.

Alleen gebruikers die zijn geverifieerd op zowel AEM als SharePoint hebben via de connector toegang tot de SharePoint-inhoud.

U kunt de schakelaaruitbreiding voor authentificatie ook gebruiken om een module van de douaneauthentificatie tot stand te brengen, die, bijvoorbeeld, toegang door AEM gebruikers aan specifieke gebruikers van SharePoint in kaart brengt. Maak AEM gebruikers die overeenkomen met SharePoint-gebruikers (gebruikersnaam en wachtwoord moeten overeenkomen) om SharePoint-inhoud te kunnen zien die is toegewezen aan de connector.

Een gebruiker maken in AEM:

1. Meld u aan bij http://localhost:9502/with.
1. Klik op Gereedschappen.
1. Klik op Beveiliging.
1. Klik op Gebruikers.
1. Klikken **Gebruiker maken**.
1. Geef de gebruikersnaam op (gebruikersnaam die toegang heeft tot SharePoint).
1. Geef het bijbehorende wachtwoord op.
1. Klik op het groene verdeelstreepje om de gebruiker te maken.

De gebruiker toevoegen in de beheergroep:

1. Ga naar Groepsbeheer.
1. Klik op het knooppunt &#39;a&#39;.
1. Klik op &#39;beheerders&#39;.
1. Typ de gebruikers-id die u hierboven hebt gemaakt in het tekstvak ervoor **Bladeren** knop.
1. Klik op het groene verdeelstreepje om de gebruiker toe te voegen aan de beheergroep.

### Tokenverificatie uitschakelen {#disable-token-authentication}

1. Het pakket downloaden en installeren `basic auth`. `zip` van Softwaredistributie.

1. Sluit QuickStart.
1. Het bestand openen *\crx-quickstart\repository\repository.xml*.
1. De tag zoeken `<LoginModule class="com.day.crx.core.CRXLoginModule"> ... </LoginModule>.`
1. De tag invoegen `<param name="disableTokenAuth" value="true"/>` binnen het in stap 4 vermelde label.
1. Sla het XML-bestand op en sluit het.
1. Start QuickStart opnieuw en meld u aan met uw referenties.

#### Verschillende verificatiemethoden van de SharePoint-server worden ondersteund {#supporting-different-authentication-methods-of-the-sharepoint-server}

In zijn standaardversie, steunt de schakelaar standaard IIS **Windows** verificatie (Basic) en op Forms gebaseerde verificatie (op basis van token). De [andere verificatiemethoden](https://technet.microsoft.com/en-us/library/cc262350.aspx#section2) kan worden ondersteund via het uitbreidbaarheidsmechanisme.

De volgende stappen bevatten richtlijnen voor het uitbreiden van de standaardverificatie ter ondersteuning van verschillende verificatiemethoden van de SharePoint-server:

1. Implementeren `com.day.crx.spi.sharepoint.security.SharepointConnectionFactory` om de clientzijde van uw specifieke verificatieproces af te handelen.
1. Installeer de `SharepointConnectionFactory` implementatie als een fragmentbundel met fragmenthost `com.day.crx.spi.crx2sharepoint-bundle`.

   Wanneer het gebruiken van Maven, pas de volgende configuratie van aan `maven-bundle-plugin` aan de vereisten van uw project:

   ```xml
              <plugin>
                  <groupId>org.apache.felix</groupId>
                  <artifactId>maven-bundle-plugin</artifactId>
                  <extensions>true</extensions>
                  <configuration>
                      <instructions>
                          <Export-Package />
                          <Private-Package>
                              <!-- your private package here -->
                          </Private-Package>
                          <Fragment-Host>
                              com.day.crx.spi.crx2sharepoint-bundle
                          </Fragment-Host>
                       </instructions>
                  </configuration>
              </plugin>
   ```

1. Registreer de `SharepointConnectionFactory` implementatie in de schakelaarconfiguratie. Klik in het configuratievenster van de connector op **Geavanceerde opties**. In de lus for **SharePoint Connection Factory** -veld, geeft u de naam van de implementatie op `com.day.crx.spi.sharepoint.auth.CustomConnectionFactory`.

1. Start de connector opnieuw.
