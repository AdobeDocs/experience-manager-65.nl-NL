---
title: SharePoint Connector
description: Day JCR Connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013, versie 4.0.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 10ea7d2e-6e44-4d5c-a2b2-63c73b18f172
feature: Integration
role: Admin
source-git-commit: c4133584e9c2328b3a55042902c67770d78afcf7
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
>Installatie-, configuratie-, beheer- en IT-bewerkingen van de SharePoint-server en de bijbehorende IT-infrastructuur vallen buiten het bereik van dit document. Zie verkopersdocumentatie op [ SharePoint ](https://www.microsoft.com/sharepoint) voor informatie over deze onderwerpen. De aansluiting vereist dat deze delen van de infrastructuur correct worden geïnstalleerd, geconfigureerd en gebruikt.
>

## Aan de slag {#getting-started}

Ga als volgt te werk om aan de slag te gaan met de connector:

* Zorg ervoor dat u ten minste Java 7 hebt geïnstalleerd.
* Download het distributiebestand van het schakelaarpakket van de Distributie van de Software.
* Kopieer een geldig *license.properties* dossier aan de folder die het *cq-quickstart-6.4.0.jar* dossier bevat.

* Dubbelklik op het .jar-bestand om het AEM te starten of start het bestand via de opdrachtregel.
* Installeer het aansluitingspakket via Package Manager.
* Configureer de verbindingsopties.

## SharePoint-connector installeren {#installing-sharepoint-connector}

De connector is een inhoudspakket dat eenvoudige installatie mogelijk maakt. Installeer het pakket met Package Manager en stel vervolgens de URL van de SharePoint-server in
en andere configuratieopties. De SharePoint-inhoud is beschikbaar in de AEM repository.

### Installatievereisten {#installation-requirements}

De schakelaar vereist het volgende:

* Java Runtime Environment 1.7 of hoger
* SharePoint Web Services beschikbaar via het netwerk
* URL SharePoint-server
* Gebruikersreferenties en machtigingen voor CRX- en SharePoint-opslagruimten
* [Ondersteunde platforms](#supported-platforms)

De schakelaar van SharePoint is beschikbaar voor het downloaden van [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-17673).

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
>De connector ondersteunt alleen configuraties die officieel door Microsoft worden ondersteund. Zie [ MOSS 2010 ](https://technet.microsoft.com/en-us/library/cc262485(office.14).aspx) en [ MOSS 2013 ](https://technet.microsoft.com/en-us/library/cc262485.aspx) systeemvereisten.

### Standaardinstallatie {#standard-installation}

Softwaredistributie wordt gebruikt om productfuncties, voorbeelden en hotfixes te distribueren. Voor details, zie de [ documentatie van de Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html#software-distribution).


#### Integreren met AEM {#integrating-with-aem}

Om het pakket van de schakelaarinhoud te installeren.

1. Open een kaartje van de Steun van de Adobe om om het schakelaarkenmerkpak te verzoeken.
1. Download het pakket wanneer het beschikbaar is en open dan de Manager van het Pakket voor uw AEM instantie.
1. Klik **installeren** van de pagina van de pakketbeschrijving.
1. Van **installeer de dialoog van het Pakket**, klik **installeer**.

   **Nota**: Zorg ervoor dat u als beheerder het programma wordt geopend.

1. Wanneer het pakket wordt geïnstalleerd, klik **dicht**.

## SharePoint-connector configureren {#configuring-sharepoint-connector}

Nadat u de SharePoint-connector hebt geïnstalleerd, configureert u de toepassing en de SharePoint-lagen voor de connector.

Stel de URL van de SharePoint-server in om de JCR-compatibiliteit van uw SharePoint-opslagruimte te garanderen. U kunt extra parameters instellen om de verbinding met de SharePoint-server te configureren. Configureer bovendien verificatie met de SharePoint-connector.

### De verbinding met de SharePoint-server configureren {#configuring-the-connection-with-the-sharepoint-server}

Voer de volgende stappen uit om de URL van de SharePoint-server en de geavanceerde opties in te stellen:

1. Navigeer aan de Console van het Beheer OSGi: [ http://localhost:4502/system/console/configMgr ](http://localhost:4502/system/console/configMgr).
1. Onderzoek naar de **Schakelaar van JCR van de Dag voor Microsoft SharePoint** bundel.
1. Bewerk de configuratiewaarden.
1. Plaats URL van de Server van SharePoint als waarde van **Werkruimten**.
1. Klik **sparen**.

![ chlimage_1-62 ](assets/chlimage_1-62.png)

Parameters Workspaces en Default Workspace Name:

Standaard stelt de connector één JCR-werkruimte beschikbaar. De SharePoint-server die door deze werkruimte beschikbaar wordt gemaakt, wordt ingesteld via de configuratieparameter &#39;SharePoint Server URL&#39;.

De schakelaar kan ook voor veelvoudige werkruimten worden gevormd. In dit geval wordt elke werkruimte gekoppeld aan de URL van de respectievelijke SharePoint-server die via de werkruimte beschikbaar wordt gemaakt. Als u een werkruimte wilt toevoegen, voegt u een werkruimtedefinitie toe aan de parameter Werkruimten. Een werkruimtedefinitie heeft de volgende indeling:
`<name>`= `<url>` waar
`<name>` is de naam van de JCR-werkruimte en
`<url>` is de URL van de SharePoint-server voor die werkruimte.

Voer in AEM nog een stap uit, apart van de bovenstaande configuratiestappen. Lijst van gewenste personen &#39;**com.day.cq.dam.cq-dam-jcr-connectors**&#39; bundel.

Voer de volgende stappen uit om bundels in AEM te lijsten van gewenste personen:

1. Ga naar de OSGi Management Console: http://localhost:4502/system/console/configMgr.
1. Zoek naar de service &quot;Apache Sling Login Admin Whitelist&quot;.
1. Selecteer **mijden whitelist**.
1. `com.day.cq.dam.cq-dam-jcr-connectors` toevoegen in standaardbundels whitelist
1. Klik op Opslaan.

![ chlimage_1-82 ](assets/chlimage_1-82a.png)

>[!NOTE]
>
>Als u meerdere werkruimten configureert, geeft u de naam van de standaardwerkruimte op in de parameter Standaard Workspace-naam.

Voor extra informatie rond authentificatie-verwante parameters, zie [ Authentificatie ](/help/sites-administering/sharepoint-connector.md#configuring-authentication).

### De installatie van SharePoint controleren {#verifying-the-sharepoint-setup}

Nadat u de schakelaar vormt, verifieer het volgende:

* SharePoint-server wordt uitgevoerd en de webservices zijn toegankelijk voor de verbindingsinstantie
* SharePoint-gebruikersgegevens zijn geldig en de gebruiker beschikt over de vereiste SharePoint-machtigingen
* De schakelaar is geïnstalleerd en behoorlijk gevormd

### DAM-synchronisatie configureren met de SharePoint-server {#configuring-dam-sync-with-the-sharepoint-server}

Voer de volgende stappen uit om de SharePoint Assets met AEM te synchroniseren:

1. Navigeer aan de Console van het Beheer OSGi: [ http://localhost:4502/system/console/configMgr ](http://localhost:4502/system/console/configMgr).
1. Zoek naar de service &quot;Default DAMAssetSynchronization&quot;.
1. Bewerk de configuratiewaarden.
1. Stel de gebruikersnaam en het bijbehorende wachtwoord in van de gebruiker die toegang heeft tot de SharePoint-site.
1. Klik op Opslaan.

Schakel de DAM Sync Service in, die standaard is uitgeschakeld:

1. Navigeer aan de Componenten van de Console van OSGi van het Web: [ http://localhost:4502/system/console/components](http://localhost:4502/system/console/components)
1. Zoek naar &quot;com.day.cq.dam.jcrconnectors.impl.AssetSynchronizationService.&quot;
1. Klik op Inschakelen.

Naar keuze, kunt u de vertraging van de Synchronisatie tussen verschillende synchronisatiecycli vormen:

1. Navigeer aan de Console van het Beheer OSGi: [ http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr)
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

* **Basis/NTLM authentificatie**: De schakelaar probeert eerst om het gebruiken van basisauthentificatie te verbinden. Als deze optie niet beschikbaar is, wordt overgeschakeld naar verificatie op basis van NTLM.
* **op Forms-Gebaseerde authentificatie**: SharePoint bevestigt gebruikers die op geloofsbrieven worden gebaseerd die de gebruikers in een login vorm (typisch een Web-pagina) typen. Het systeem geeft een teken voor voor authentiek verklaarde verzoeken uit die een sleutel voor het opnieuw vestigen van de identiteit voor verdere verzoeken bevat.

**Vormend Forms Gebaseerde Authentificatie**

Ga naar: [ http://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles)

1. Klik op OSGI > Configuration
1. Zoeken naar &quot;Day JCR Connector for Microsoft Sharepoint&quot;
1. Klik op &quot;De configuratiewaarden bewerken&quot;
1. Stel de waarde van &#39;Sharepoint Connection Factory&#39; in op &#39;com.day.crx.spi.sharepoint.security.FormsBasedAuthenticationConnectionFactory&#39;
1. Klik **sparen**.

**Vormend BasisAuthentificatie (Vensters)**

1. [ maak Symbolische Authentificatie ](#disable-token-authentication) onbruikbaar.
1. Ga naar [ http://localhost:4502/system/console/bundles ](http://localhost:4502/system/console/bundles).
1. Klik op OSGI > Configuratie.
1. Onderzoek naar **Schakelaar van JCR van de Dag voor Microsoft Sharepoint**.
1. Klik op `Edit the configuration values`.
1. Stel de waarde van SharePoint Connection Factory in op `com.day.crx.spi.sharepoint.security.WindowsAuthenticationConnectionFactory` .
1. Klik **sparen**.

Alleen gebruikers die zijn geverifieerd op zowel AEM als SharePoint hebben via de connector toegang tot de SharePoint-inhoud.

U kunt de schakelaaruitbreiding voor authentificatie ook gebruiken om een module van de douaneauthentificatie tot stand te brengen, die, bijvoorbeeld, toegang door AEM gebruikers aan specifieke gebruikers van SharePoint in kaart brengt. Maak AEM gebruikers die overeenkomen met SharePoint-gebruikers (gebruikersnaam en wachtwoord moeten overeenkomen) om SharePoint-inhoud te kunnen zien die is toegewezen aan de connector.

Een gebruiker maken in AEM:

1. Meld u aan bij http://localhost:9502/with.
1. Klik op Gereedschappen.
1. Klik op Beveiliging.
1. Klik op Gebruikers.
1. Klik **creëren Gebruiker**.
1. Geef de gebruikersnaam op (gebruikersnaam die toegang heeft tot SharePoint).
1. Geef het bijbehorende wachtwoord op.
1. Klik op het groene verdeelstreepje om de gebruiker te maken.

De gebruiker toevoegen in de beheergroep:

1. Ga naar Groepsbeheer.
1. Klik op het knooppunt &#39;a&#39;.
1. Klik op &#39;beheerders&#39;.
1. Typ hierboven tot gebruiker - identiteitskaart in het tekstvakje alvorens **doorbladert** knoop.
1. Klik op het groene verdeelstreepje om de gebruiker toe te voegen aan de beheergroep.

### Tokenverificatie uitschakelen {#disable-token-authentication}

1. Download en installeer het pakket `basic auth` . `zip` van Software Distribution.

1. Sluit QuickStart.
1. Open het dossier *\crx-quickstart\repository\repository.xml*.
1. De tag zoeken `<LoginModule class="com.day.crx.core.CRXLoginModule"> ... </LoginModule>.`
1. Plaats de tag `<param name="disableTokenAuth" value="true"/>` in de tag die in stap 4 wordt vermeld.
1. Sla het XML-bestand op en sluit het.
1. Start QuickStart opnieuw en meld u aan met uw referenties.

#### Verschillende verificatiemethoden van de SharePoint-server worden ondersteund {#supporting-different-authentication-methods-of-the-sharepoint-server}

In zijn standaardversie, steunt de schakelaar de standaardIIS **authentificatie van Vensters** (Basis) en op Forms-Gebaseerde authentificatie (op teken gebaseerd). De [ andere authentificatiemethodes ](https://technet.microsoft.com/en-us/library/cc262350.aspx#section2) kunnen door het rekbaarheidsmechanisme worden gesteund.

De volgende stappen bevatten richtlijnen voor het uitbreiden van de standaardverificatie ter ondersteuning van verschillende verificatiemethoden van de SharePoint-server:

1. Implementeer `com.day.crx.spi.sharepoint.security.SharepointConnectionFactory` om de clientzijde van uw specifieke verificatieproces af te handelen.
1. Installeer de `SharepointConnectionFactory` -implementatie als een fragmentbundel met fragmenthost `com.day.crx.spi.crx2sharepoint-bundle` .

   Wanneer u Maven gebruikt, past u de volgende configuratie van de `maven-bundle-plugin` aan de vereisten van uw project aan:

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

1. Registreer de `SharepointConnectionFactory` implementatie in de schakelaarconfiguratie. In het configuratievenster van de schakelaar, klik **Geavanceerde opties**. In het voor **gebied van de Fabriek van de Verbinding van SharePoint**, specificeer de naam van de implementatie `com.day.crx.spi.sharepoint.auth.CustomConnectionFactory`.

1. Start de connector opnieuw.
