---
title: SharePoint-connector
seo-title: SharePoint-connector
description: De Schakelaar van JCR van de dag voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0.
seo-description: Leer over de Schakelaar van SharePoint in AEM.
uuid: df650476-4e2a-486f-a007-b5ac437ff99f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 907316d1-3d23-4c46-bccb-bad6fe1bd1bb
docset: aem65
translation-type: tm+mt
source-git-commit: cc3a2ce7cb3dc020f5466a4b65cf5a9714e7a344
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---


# SharePoint-connector{#sharepoint-connector}

Dit artikel omvat details rond de Schakelaar van JCR van Adobe voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0.

De SharePoint-connector ondersteunt de volgende basisfuncties:

* Inhoud en metagegevens lezen vanuit SharePoint.
* SharePoint-beveiligingsinstellingen voor benaderde inhoud bevestigen door native SharePoint-verificatie en -verificatie toe te passen
* Inhoudsintegratie met Inhoudszoeker
* Het gebruiken van AEM componenten, zoals Extern Middel om beelden en video&#39;s van SharePoint te tonen
* SharePoint synchroniseren met AEM Assets

Alle functies worden uitgevoerd gebruikend de inheemse Webdiensten van SharePoint als interface aan de inhoud en de diensten van SharePoint.

>[!NOTE]
>
>De Schakelaar van SharePoint wordt ook gesteund met AEM 6.1 de dienstpak 2. De connector ondersteunt geen virtuele opslagplaats meer en kan daarom niet worden gemonteerd. Als u toegang wilt krijgen tot de SharePoint-opslagplaats met Java API&#39;s, gebruikt u de JCR-opslagfunctie van de SharePoint-connector in uw project.
>
>De installatie, configuratie, beheer, en de verrichtingen van IT van de server van SharePoint en verwante infrastructuur van IT zijn buiten het werkingsgebied van dit document. Raadpleeg de documentatie van leveranciers over [SharePoint](https://www.microsoft.com/sharepoint) voor informatie over deze onderwerpen. De aansluiting vereist dat deze delen van de infrastructuur correct worden ge??nstalleerd, geconfigureerd en gebruikt.


## Aan de slag {#getting-started}

Ga als volgt te werk om aan de slag te gaan met de connector:

* Zorg ervoor dat u ten minste Java 7 hebt ge??nstalleerd.
* Download het distributiebestand van het schakelaarpakket van de Distributie van de Software.
* Kopieer een geldig *license.properties* dossier aan de folder die *cq-quickstart-6.4.0.jar* dossier bevat.

* Dubbelklik op of tik op het .jar-bestand om het te AEM of start het bestand via de opdrachtregel.
* Installeer het aansluitingspakket via Package Manager.
* Configureer de verbindingsopties.

## SharePoint-connector {#installing-sharepoint-connector} installeren

De connector is een inhoudspakket dat eenvoudige installatie mogelijk maakt. Installeer het pakket met behulp van Package Manager en stel vervolgens de URL van de SharePoint-server in
en andere configuratieopties. De inhoud van SharePoint is beschikbaar in de AEM bewaarplaats.

### Installatievereisten {#installation-requirements}

De schakelaar vereist het volgende:

* Java Runtime Environment 1.7 of hoger
* De Diensten van het Web van SharePoint beschikbaar door het netwerk
* URL SharePoint-server
* Gebruikersreferenties en machtigingen voor CRX- en SharePoint-opslagruimten
* [Ondersteunde platforms](#supported-platforms)

De SharePoint-connector is beschikbaar voor downloaden vanaf [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-17673).

### Ondersteunde Platforms {#supported-platforms}

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

Softwaredistributie wordt gebruikt om productfuncties, voorbeelden en hotfixes te distribueren. Zie de [documentatie voor softwaredistributie](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html#software-distribution) voor meer informatie.


#### Integreren met AEM {#integrating-with-aem}

Om het pakket van de schakelaarinhoud te installeren.

1. Open een Adobe Support-ticket om een aanvraag in te dienen voor het connectorfunctiepakket.
1. Download het pakket wanneer het beschikbaar is en open dan de Manager van het Pakket voor uw AEM instantie.
1. Tik/klik op **Installeren** op de pagina met de pakketbeschrijving.
1. Tik in het dialoogvenster **Pakket installeren** op **Installeren**.

   **Opmerking**: Controleer of u bent aangemeld als beheerder.

1. Tik op **Close** wanneer het pakket is ge??nstalleerd.

## SharePoint-connector {#configuring-sharepoint-connector} configureren

Nadat u de schakelaar van SharePoint installeert, vorm de toepassing en de lagen van SharePoint voor de schakelaar.

Stel de URL van de SharePoint-server in om de JCR-compatibiliteit van uw SharePoint-opslagruimte te behouden. U kunt extra parameters instellen om de verbinding met de SharePoint-server te configureren. Daarnaast configureert u verificatie met de SharePoint-connector.

### De verbinding configureren met de SharePoint-server {#configuring-the-connection-with-the-sharepoint-server}

Voer de volgende stappen uit om de URL van de SharePoint-server en de geavanceerde opties in te stellen:

1. Navigeer naar de OSGi Management Console: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Zoek naar de **Day JCR Connector voor Microsoft SharePoint** bundel.
1. Bewerk de configuratiewaarden.
1. Stel de URL van de SharePoint-server in als de waarde van **Workspaces**.
1. Tik/klik **Opslaan**.

![chlimage_1-62](assets/chlimage_1-62.png)

Parameters &#39;Werkruimten&#39; en &#39;Standaardnaam werkruimte&#39;:

Standaard stelt de connector ????n JCR-werkruimte beschikbaar. De SharePoint-server die door deze werkruimte beschikbaar wordt gemaakt, wordt ingesteld via de configuratieparameter &#39;SharePoint Server URL&#39;.

De schakelaar kan ook voor veelvoudige werkruimten worden gevormd. In dit geval wordt elke werkruimte gekoppeld aan de URL van de respectievelijke SharePoint-server die via de werkruimte beschikbaar wordt gemaakt. Als u een werkruimte wilt toevoegen, voegt u een werkruimtedefinitie toe aan de parameter Werkruimten. Een werkruimtedefinitie heeft de volgende indeling:
`<name>`= `<url>` waarbij
`<name>` is de naam van de JCR-werkruimte en
`<url>` is de URL van de SharePoint-server voor die werkruimte.

Voer in AEM nog een stap uit, apart van de bovenstaande configuratiestappen. Lijst van gewenste personen de bundel &#39;**com.day.cq.dam.cq-dam-jcr-connectors**&#39;.

Voer de volgende stappen uit om bundels in AEM te lijsten van gewenste personen:

1. Navigeer naar de OSGi Management Console: http://localhost:4502/system/console/configMgr.
1. Zoek naar de service &quot;Apache Sling Login Admin Whitelist&quot;.
1. Selecteer **De whitelist** omzeilen.
1. `com.day.cq.dam.cq-dam-jcr-connectors` toevoegen in standaardbundels whitelist
1. Klik op Opslaan.

![chlimage_1-82](assets/chlimage_1-82a.png)

>[!NOTE]
>
>Als u meerdere werkruimten configureert, geeft u de naam van de standaardwerkruimte op in de parameter Standaardnaam werkruimte.

Voor extra informatie rond authentificatie-verwante parameters, zie [Authentificatie](/help/sites-administering/sharepoint-connector.md#configuring-authentication).

### De installatie van SharePoint {#verifying-the-sharepoint-setup} controleren

Nadat u de schakelaar vormt, verifieer het volgende:

* De serverlooppas van SharePoint, en de Webdiensten zijn toegankelijk voor de schakelaarinstantie
* De gebruikersgeloofsbrieven van SharePoint zijn geldig en de gebruiker heeft noodzakelijke toestemmingen van SharePoint
* De schakelaar is ge??nstalleerd en behoorlijk gevormd

### DAM-synchronisatie configureren met de SharePoint-server {#configuring-dam-sync-with-the-sharepoint-server}

Voer de volgende stappen uit om de SharePoint-elementen te synchroniseren met AEM:

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

### Verificatie {#configuring-authentication} configureren

SharePoint omvat de Klassieke en op eisen gebaseerde authentificatiemethodes, die allebei de volgende authentificatietypen steunen:

* Basis
* Op Forms gebaseerd

Met name zijn de volgende verificatietypen beschikbaar:

* Klassiek-basis
* Op basis van Classic-Forms
* Vorderingen ??? Basis
* Op Forms gebaseerde claims

De AEM JCR-connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0. steunt op eisen-gebaseerde authentificatie (die door Microsoft wordt voorgesteld), die op de volgende wijzen werkt:

* **Basic-/NTLM-verificatie**: De schakelaar probeert eerst om het gebruiken van basisauthentificatie te verbinden. Als deze optie niet beschikbaar is, wordt overgeschakeld naar verificatie op basis van NTLM.
* **Op Forms gebaseerde verificatie**: SharePoint valideert gebruikers op geloofsbrieven die de gebruikers in een login vorm (typisch een Web-pagina) typen. Het systeem geeft een teken voor voor authentiek verklaarde verzoeken uit die een sleutel voor het opnieuw vestigen van de identiteit voor verdere verzoeken bevat.

**Op Forms gebaseerde verificatie configureren**

Ga naar: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)

1. Klik op OSGI -> Configuration
1. Zoeken naar &quot;Day JCR Connector for Microsoft SharePoint&quot;
1. Klik op &quot;De configuratiewaarden bewerken&quot;
1. Stel de waarde van &quot;Sharepoint Connection Factory&quot; in op &quot;com.day.crx.spi.sharepoint.security.FormsBasedAuthenticationConnectionFactory&quot;
1. Klik **Opslaan**.

**Basisverificatie configureren (Windows)**

1. [Tokenverificatie](#disable-token-authentication) uitschakelen.
1. Ga naar [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).
1. Klik op OSGI > Configuratie.
1. Zoeken naar **Day JCR Connector voor Microsoft SharePoint**.
1. Klik op `Edit the configuration values`.
1. Stel de waarde van SharePoint Connection Factory in op `com.day.crx.spi.sharepoint.security.WindowsAuthenticationConnectionFactory`.
1. Klik **Opslaan**.

Slechts kan een gebruiker die op zowel AEM als SharePoint voor authentiek wordt verklaard tot de inhoud van SharePoint door de schakelaar toegang hebben.

U kunt de schakelaaruitbreiding voor authentificatie ook gebruiken om een module van de douaneauthentificatie tot stand te brengen, die, bijvoorbeeld, toegang door AEM gebruikers aan specifieke gebruikers van SharePoint in kaart brengt. Creeer AEM gebruikers die aan de gebruikers van SharePoint (gebruikersnaam en wachtwoord zouden moeten aanpassen) beantwoorden om de inhoud van SharePoint te kunnen zien die aan de schakelaarinstantie in kaart wordt gebracht.

Een gebruiker maken in AEM:

1. Meld u aan bij http://localhost:9502/with.
1. Klik op Gereedschappen.
1. Klik op Beveiliging.
1. Klik op Gebruikers.
1. Klik **Gebruiker maken**.
1. Geef de gebruikersnaam op (gebruikersnaam die toegang heeft tot SharePoint).
1. Geef het bijbehorende wachtwoord op.
1. Klik op het groene verdeelstreepje om de gebruiker te maken.

De gebruiker toevoegen in de beheergroep:

1. Ga naar Groepsbeheer.
1. Klik op het knooppunt &quot;a&quot;.
1. Klik op &quot;beheerders&quot;.
1. Typ de hierboven gemaakte gebruikersnaam in het tekstvak v????r de knop **Bladeren**.
1. Klik op het groene verdeelstreepje om de gebruiker toe te voegen aan de beheergroep.

### Tokenverificatie {#disable-token-authentication} uitschakelen

1. Download en installeer het pakket `basic auth`. `zip` van Software Distribution.

1. Sluit QuickStart.
1. Open het bestand *\crx-quickstart\repository\repository.xml*.
1. De tag `<LoginModule class="com.day.crx.core.CRXLoginModule"> ... </LoginModule>.` zoeken
1. Plaats de tag `<param name="disableTokenAuth" value="true"/>` in de tag die in stap 4 wordt vermeld.
1. Sla het XML-bestand op en sluit het.
1. Start QuickStart opnieuw en meld u aan met uw referenties.

#### Verschillende verificatiemethoden van de SharePoint-server {#supporting-different-authentication-methods-of-the-sharepoint-server} worden ondersteund

In zijn standaardversie, steunt de schakelaar de standaardIIS **Windows** authentificatie (Basis) en op Forms-Gebaseerde authentificatie (op teken gebaseerd). De [andere verificatiemethoden](https://technet.microsoft.com/en-us/library/cc262350.aspx#section2) kunnen worden ondersteund via het mechanisme voor uitbreidbaarheid.

De volgende stappen bevatten richtlijnen voor het uitbreiden van de standaardverificatie ter ondersteuning van verschillende verificatiemethoden van de SharePoint-server:

1. Implementeer `com.day.crx.spi.sharepoint.security.SharepointConnectionFactory` om de clientzijde van uw specifieke verificatieproces af te handelen.
1. Installeer de `SharepointConnectionFactory`-implementatie als een fragmentbundel met fragmenthost `com.day.crx.spi.crx2sharepoint-bundle`.

   Wanneer het gebruiken van Maven, pas de volgende configuratie van `maven-bundle-plugin` aan de vereisten van uw project aan:

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

1. Registreer de `SharepointConnectionFactory` implementatie in de schakelaarconfiguratie. Klik in het configuratievenster van de connector op **Geavanceerde opties**. Geef in het veld for **Sharepoint Connection Factory** de naam van de implementatie `com.day.crx.spi.sharepoint.auth.CustomConnectionFactory` op.

1. Start de connector opnieuw.

