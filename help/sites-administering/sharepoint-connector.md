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
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# SharePoint-connector{#sharepoint-connector}

Dit artikel bevat informatie over de Adobe JCR-connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0.

De SharePoint-connector ondersteunt de volgende basisfuncties:

* Inhoud en metagegevens lezen vanuit SharePoint.
* SharePoint-beveiligingsinstellingen voor benaderde inhoud bevestigen door native SharePoint-verificatie en -verificatie toe te passen
* Inhoudsintegratie met Inhoudszoeker
* AEM-componenten gebruiken, zoals External Resource, om SharePoint-afbeeldingen en video&#39;s weer te geven
* SharePoint synchroniseren met AEM-elementen

Alle functies worden uitgevoerd gebruikend de inheemse Webdiensten van SharePoint als interface aan de inhoud en de diensten van SharePoint.

>[!NOTE]
>
>De Schakelaar van SharePoint wordt ook gesteund met AEM 6.1 de dienstpak 2. De connector ondersteunt geen virtuele opslagplaats meer en kan daarom niet worden gemonteerd. Als u toegang wilt krijgen tot de SharePoint-opslagplaats met Java API&#39;s, gebruikt u de JCR-opslagfunctie van de SharePoint-connector in uw project.
>
>De installatie, configuratie, beheer, en de verrichtingen van IT van de server van SharePoint en verwante infrastructuur van IT zijn buiten het werkingsgebied van dit document. Zie verkopersdocumentatie op [SharePoint](https://www.microsoft.com/sharepoint) voor informatie over deze onderwerpen. De aansluiting vereist dat deze delen van de infrastructuur correct worden geïnstalleerd, geconfigureerd en gebruikt.


## Getting started {#getting-started}

Ga als volgt te werk om aan de slag te gaan met de connector:

* Zorg ervoor dat u ten minste Java 7 hebt geïnstalleerd.
* Download het verdelingsdossier van het schakelaarpakket van het Aandeel van het Pakket.
* Kopieer een geldig bestand *license.properties* naar de map die het bestand *cq-quickstart-6.4.0.jar* bevat.

* Dubbelklik of tik op het .jar-bestand om AEM te starten of start het bestand via de opdrachtregel.
* Installeer het aansluitingspakket via Package Manager.
* Configureer de verbindingsopties.

## SharePoint-connector installeren {#installing-sharepoint-connector}

De connector is een inhoudspakket dat eenvoudige installatie mogelijk maakt. Installeer het pakket met behulp van Package Manager en stel vervolgens de SharePoint-server-URL en andere configuratieopties in. De SharePoint-inhoud is beschikbaar in de AEM-opslagruimte.

### Installatievereisten {#installation-requirements}

De schakelaar vereist het volgende:

* Java Runtime Environment 1.7 of hoger
* De Diensten van het Web van SharePoint beschikbaar door het netwerk
* URL SharePoint-server
* Gebruikersreferenties en machtigingen voor CRX- en SharePoint-opslagruimten
* [Ondersteunde platforms](#supported-platforms)

De SharePoint-connector is beschikbaar voor downloaden vanuit [pakketshare](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-17673).

### Ondersteunde platforms {#supported-platforms}

De schakelaar steunt het volgende:

* AEM-versies:

   * AEM 6.5, 6.4, 6.3

* Microsoft SharePoint-versies:

   * Microsoft Office SharePoint Server (MOSS) 2010
   * Microsoft Office SharePoint Server (MOSS) 2013

* Neem contact op met het Adobe-kantoor voor uw regio als u ondersteuning nodig hebt voor aangepaste implementaties van de connector (OEM, speciale vereisten, aangepaste verificatiemethoden).

>[!NOTE]
>
>De connector ondersteunt alleen configuraties die officieel door Microsoft worden ondersteund. Zie [MOSS 2010](https://technet.microsoft.com/en-us/library/cc262485(office.14).aspx) en [MOSS 2013](https://technet.microsoft.com/en-us/library/cc262485.aspx) systeemvereisten.

### Standaardinstallatie {#standard-installation}

AEM-pakket delen wordt gebruikt om productfuncties, voorbeelden en hotfixes te distribueren. Raadpleeg de documentatie bij [Pakketdeling voor meer informatie](/help/sites-administering/package-manager.md#package-share).

Als u Pakketdeling wilt openen op de welkomstpagina van AEM, tikt u op **Gereedschappen** of klikt u op **Pakket delen**. U hebt een geldige Adobe-id nodig die het e-mailadres van uw bedrijf bevat. Nadat u zich hebt aangemeld bij uw account, kunt u bovendien een aanvraag indienen voor toegang tot het delen van pakketten.

#### Integreren met AEM {#integrating-with-aem}

Om het pakket van de schakelaarinhoud te installeren.

1. Open een Adobe Support-ticket om het pakket met connectorfuncties aan te vragen.
1. Download het pakket wanneer het beschikbaar is en open dan de Manager van het Pakket voor uw instantie AEM.
1. Tik/klik op **Installeren** op de pagina met pakketbeschrijving.
1. Tik in het dialoogvenster Pakket **** installeren op of klik op **Installeren**.

   **Opmerking**: Controleer of u bent aangemeld als beheerder.

1. Tik/klik op **Sluiten wanneer het pakket is geïnstalleerd**.

## SharePoint-connector configureren {#configuring-sharepoint-connector}

Nadat u de schakelaar van SharePoint installeert, vorm de toepassing en de lagen van SharePoint voor de schakelaar.

Stel de URL van de SharePoint-server in om de JCR-compatibiliteit van uw SharePoint-opslagruimte te behouden. U kunt extra parameters instellen om de verbinding met de SharePoint-server te configureren. Daarnaast configureert u verificatie met de SharePoint-connector.

### De verbinding met de SharePoint-server configureren {#configuring-the-connection-with-the-sharepoint-server}

Voer de volgende stappen uit om de URL van de SharePoint-server en de geavanceerde opties in te stellen:

1. Navigeer naar de OSGi Management Console: [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr).
1. Zoek naar de Schakelaar van JCR van de **Dag voor de bundel van Microsoft SharePoint** .
1. Bewerk de configuratiewaarden.
1. Stel de URL van de SharePoint-server in als de waarde van **Workspaces**.
1. Tik/klik op **Opslaan**.

![chlimage_1-62](assets/chlimage_1-62.png)

Parameters &#39;Werkruimten&#39; en &#39;Standaardnaam werkruimte&#39;:

Standaard stelt de connector één JCR-werkruimte beschikbaar. De SharePoint-server die door deze werkruimte beschikbaar wordt gemaakt, wordt ingesteld via de configuratieparameter &#39;SharePoint Server URL&#39;.

De schakelaar kan ook voor veelvoudige werkruimten worden gevormd. In dit geval wordt elke werkruimte gekoppeld aan de URL van de respectievelijke SharePoint-server die via de werkruimte beschikbaar wordt gemaakt. Als u een werkruimte wilt toevoegen, voegt u een werkruimtedefinitie toe aan de parameter Werkruimten. Een werkruimtedefinitie heeft de volgende indeling:
`<name>`= `<url>` waar`<name>``<url>` de naam van de JCR-werkruimte is en de URL van de SharePoint-server voor die werkruimte.

Voer in AEM nog één stap uit, afgezien van de bovenstaande configuratiestappen. Whitelist the &#39;**com.day.cq.dam.cq-dam-jcr-connectors**&#39; bundle.

Voer de volgende stappen uit om bundels voor whitelist in AEM uit te voeren:

1. Navigeer naar de OSGi Management Console: http://localhost:4502/system/console/configMgr.
1. Zoek naar de service &quot;Apache Sling Login Admin Whitelist&quot;.
1. Selecteer Witte lijst omzeilen.
1. Voeg &#39;**com.day.cq.dam.cq-dam-jcr-connectors**&#39; toe in de standaardwhitelist-bundels
1. Klik op Opslaan.

![chlimage_1-82](assets/chlimage_1-82a.png)

>[!NOTE]
>
>Als u meerdere werkruimten configureert, geeft u de naam van de standaardwerkruimte op in de parameter Standaardnaam werkruimte.

Voor extra informatie rond authentificatie-verwante parameters, zie [Authentificatie](/help/sites-administering/sharepoint-connector.md#configuring-authentication).

### De installatie van SharePoint controleren {#verifying-the-sharepoint-setup}

Nadat u de schakelaar vormt, verifieer het volgende:

* De serverlooppas van SharePoint, en de Webdiensten zijn toegankelijk voor de schakelaarinstantie
* De gebruikersgeloofsbrieven van SharePoint zijn geldig en de gebruiker heeft noodzakelijke toestemmingen van SharePoint
* De schakelaar is geïnstalleerd en behoorlijk gevormd

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

### Verificatie configureren {#configuring-authentication}

SharePoint omvat de Klassieke en op eisen gebaseerde authentificatiemethodes, die allebei de volgende authentificatietypen steunen:

* Basis
* Op formulieren gebaseerd

Met name zijn de volgende verificatietypen beschikbaar:

* Klassiek-basis
* Op basis van klassieke formulieren
* Vorderingen — Basis
* Op basis van claims-formulieren

De AEM JCR-connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0. steunt op eisen-gebaseerde authentificatie (die door Microsoft wordt voorgesteld), die op de volgende wijzen werkt:

* **Basic-/NTLM-verificatie**: De schakelaar probeert eerst om het gebruiken van basisauthentificatie te verbinden. Als deze optie niet beschikbaar is, wordt overgeschakeld naar verificatie op basis van NTLM.
* **Op formulieren gebaseerde verificatie**: SharePoint valideert gebruikers op geloofsbrieven die de gebruikers in een login vorm (typisch een Web-pagina) typen. Het systeem geeft een teken voor voor authentiek verklaarde verzoeken uit die een sleutel voor het opnieuw vestigen van de identiteit voor verdere verzoeken bevat.

**Verificatie op basis van formulieren configureren**

Ga naar: [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)

1. Klik op OSGI -> Configuration
1. Zoeken naar &quot;Day JCR Connector for Microsoft SharePoint&quot;
1. Klik op &quot;De configuratiewaarden bewerken&quot;
1. Stel de waarde van &quot;Sharepoint Connection Factory&quot; in op &quot;com.day.crx.spi.sharepoint.security.FormsBasedAuthenticationConnectionFactory&quot;
1. Click **Save**.

**Basisverificatie configureren (Windows)**

1. [Tokenverificatie](#disable-token-authentication)uitschakelen.
1. Ga naar [http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).
1. Klik op OSGI > Configuratie.
1. Zoek naar de Schakelaar van JCR van de **Dag voor Microsoft SharePoint**.
1. Click `Edit the configuration values`.
1. Stel de waarde van SharePoint Connection Factory in op `com.day.crx.spi.sharepoint.security.WindowsAuthenticationConnectionFactory`.
1. Click **Save**.

Alleen een gebruiker die op zowel AEM als SharePoint is geverifieerd, heeft via de connector toegang tot de SharePoint-inhoud.

U kunt de schakelaaruitbreiding voor authentificatie ook gebruiken om een module van de douaneauthentificatie tot stand te brengen, die, bijvoorbeeld, toegang door gebruikers AEM aan specifieke gebruikers van SharePoint in kaart brengt. Maak AEM-gebruikers die overeenkomen met SharePoint-gebruikers (gebruikersnaam en wachtwoord moeten overeenkomen) om SharePoint-inhoud te kunnen zien die aan de verbindingsinstantie is toegewezen.

Een gebruiker maken in AEM:

1. Meld u aan bij http://localhost:9502/with.
1. Klik op Gereedschappen.
1. Klik op Beveiliging.
1. Klik op Gebruikers.
1. Klik op **Gebruiker** maken.
1. Geef de gebruikersnaam op (gebruikersnaam die toegang heeft tot SharePoint).
1. Geef het bijbehorende wachtwoord op.
1. Klik op het groene verdeelstreepje om de gebruiker te maken.

De gebruiker toevoegen in de beheergroep:

1. Ga naar Groepsbeheer.
1. Klik op het knooppunt &quot;a&quot;.
1. Klik op &quot;beheerders&quot;.
1. Typ de hierboven gemaakte gebruikersnaam in het tekstvak vóór de knop **Bladeren** .
1. Klik op het groene verdeelstreepje om de gebruiker toe te voegen aan de beheergroep.

### Tokenverificatie uitschakelen {#disable-token-authentication}

1. Download en installeer het pakket `basic auth`. `zip` vanuit Package Share.

1. Sluit QuickStart.
1. Open het bestand *\crx-quickstart\repository\repository.xml*.
1. De tag zoeken `<LoginModule class="com.day.crx.core.CRXLoginModule"> ... </LoginModule>.`
1. Plaats de tag `<param name="disableTokenAuth" value="true"/>` in de tag die in stap 4 wordt vermeld.
1. Sla het XML-bestand op en sluit het.
1. Start QuickStart opnieuw en meld u aan met uw referenties.

#### Verschillende verificatiemethoden van de SharePoint-server worden ondersteund {#supporting-different-authentication-methods-of-the-sharepoint-server}

In zijn standaardversie, steunt de schakelaar de standaardIIS **Windows** authentificatie (Basis) en op vorm-gebaseerde authentificatie (op teken gebaseerd). De [andere authentificatiemethodes](https://technet.microsoft.com/en-us/library/cc262350.aspx#section2) kunnen door het rekbaarheidsmechanisme worden gesteund.

De volgende stappen bevatten richtlijnen voor het uitbreiden van de standaardverificatie ter ondersteuning van verschillende verificatiemethoden van de SharePoint-server:

1. Implementeren `com.day.crx.spi.sharepoint.security.SharepointConnectionFactory` om de clientzijde van uw specifieke verificatieproces af te handelen.
1. Installeer de `SharepointConnectionFactory` implementatie als een fragmentbundel met fragmenthost `com.day.crx.spi.crx2sharepoint-bundle`.

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

1. Registreer de `SharepointConnectionFactory` implementatie in de schakelaarconfiguratie. Klik in het configuratievenster van de connector op **Geavanceerde opties**. Geef in het veld for **SharePoint Connection Factory** de naam van de implementatie op `com.day.crx.spi.sharepoint.auth.CustomConnectionFactory`.

1. Start de connector opnieuw.

