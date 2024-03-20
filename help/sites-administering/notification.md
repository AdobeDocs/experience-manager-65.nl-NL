---
title: E-mailmelding configureren
description: Leer hoe u e-mailmeldingen configureert in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 918fcbbc-a78a-4fab-a933-f183ce6a907f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2037'
ht-degree: 0%

---


# E-mailmelding configureren{#configuring-email-notification}

AEM stuurt e-mailmeldingen naar gebruikers die:

* Hebt u zich op paginagebeurtenissen geabonneerd, bijvoorbeeld, wijziging of replicatie. De [Melding in vak](/help/sites-classic-ui-authoring/author-env-inbox.md#subscribing-to-notifications) in deze sectie wordt beschreven hoe u zich op dergelijke gebeurtenissen kunt abonneren.

* Hebt u zich geabonneerd op forumgebeurtenissen.
* Een stap in een werkstroom uitvoeren. De [Stap deelnemer](/help/sites-developing/workflows-step-ref.md#participant-step) in deze sectie wordt beschreven hoe u e-mailmeldingen in een workflow kunt activeren.

Voorwaarden:

* Voor de gebruiker(s) moet(en) een geldig e-mailadres zijn gedefinieerd in dit profiel.
* De **Day CQ Mail Service** moet correct worden geconfigureerd.

Wanneer een gebruiker op de hoogte wordt gesteld, ontvangt hij een e-mail in de taal die in zijn profiel wordt bepaald. Elke taal heeft zijn eigen malplaatje dat kan worden aangepast. U kunt nieuwe e-mailsjablonen toevoegen voor nieuwe talen.

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

## De e-mailservice configureren {#configuring-the-mail-service}

Als AEM e-mailberichten wilt kunnen verzenden, **Day CQ Mail Service** moet correct worden geconfigureerd. U kunt de configuratie in de console van het Web bekijken. Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

De volgende beperkingen zijn van toepassing:

* De **SMTP-serverpoort** moet 25 of hoger zijn.

* De **hostnaam SMTP-server** mag niet leeg zijn.
* De **Adres &quot;Van&quot;** mag niet leeg zijn.

Om u te helpen een probleem met **Day CQ Mail Service** kunt u de logbestanden van de service bekijken:

`com.day.cq.mailer.DefaultMailService`

De configuratie kijkt als volgt in de console van het Web:

![Het OSGi-configuratievenster van de Day CQ Mail Service](assets/chlimage_1-276.png)

## Het kanaal voor e-mailmeldingen configureren {#configuring-the-email-notification-channel}

Wanneer u zich abonneert op berichten voor pagina- of forumgebeurtenissen, wordt het e-mailadres ingesteld op `no-reply@acme.com` standaard. U kunt deze waarde wijzigen door het dialoogvenster **E-mailkanaal voor meldingen** in de webconsole.

Als u het e-mailadres wilt configureren, voegt u een `sling:OsgiConfig` aan de gegevensopslagruimte. Gebruik de volgende procedure om de knoop direct toe te voegen gebruikend CRXDE Lite:

1. Voeg in CRXDE Lite een map met de naam `config` onder de toepassingsmap.
1. Voeg in de configuratiemap een knooppunt met de naam:

   `com.day.cq.wcm.notification.email.impl.EmailChannel` van het type `sling:OsgiConfig`

1. Voeg een `String` eigenschap voor de benoemde node `email.from`. Geef voor de waarde het e-mailadres op dat u wilt gebruiken.

1. Klikken **Alles opslaan**.

Gebruik de volgende procedure om het knooppunt in de bronmappen van het inhoudspakket te definiëren:

1. In uw `jcr_root/apps/*app_name*/config folder`, maakt u een bestand met de naam `com.day.cq.wcm.notification.email.impl.EmailChannel.xml`

1. Voeg de volgende XML toe om het knooppunt te vertegenwoordigen:

   `<?xml version="1.0" encoding="UTF-8"?> <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig" email.from="name@server.com"/>`
1. Vervang de waarde van de optie `email.from` attribute ( `name@server.com`) met uw e-mailadres.

1. Sla het bestand op.

## De Workflow Email Notification Service configureren {#configuring-the-workflow-email-notification-service}

Wanneer u e-mailmeldingen over de workflow ontvangt, worden zowel het adres van de e-mail als het URL-voorvoegsel van de host ingesteld op standaardwaarden. U kunt deze waarden wijzigen door het dialoogvenster **Day CQ Workflow Email Notification Service** in de webconsole. Als u dat doet, wordt aanbevolen de wijziging in de opslagplaats voort te zetten.

De standaardconfiguratie kijkt als volgt in de Console van het Web:

![Het configuratievenster voor de Day CQ Workflow Email Notification Service](assets/chlimage_1-277.png)

### E-mailsjablonen voor paginamelding {#email-templates-for-page-notification}

De e-mailsjablonen voor paginaberichten staan hieronder:

`/libs/settings/notification-templates/com.day.cq.wcm.core.page`

De standaardsjabloon Engels ( `en.txt`) wordt als volgt gedefinieerd:

```xml
subject=[CQ Page Event Notification]: Page Event

header=-------------------------------------------------------------------------------------\n \
Time: ${time}\n \
User: ${userFullName} (${userId})\n \
-------------------------------------------------------------------------------------\n\n

message=The following pages were affected by the event: \n \
 \n \
${modifications} \n \
 \n\n
footer=\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### E-mailsjablonen aanpassen voor paginamelding {#customizing-email-templates-for-page-notification}

U kunt als volgt de Engelse e-mailsjabloon voor paginabeldingen aanpassen:

1. Open het bestand in CRXDE:

   `/libs/settings/notification-templates/com.day.cq.wcm.core.page/en.txt`

1. Wijzig het bestand naar wens.
1. Sla de wijzigingen op.

De sjabloon moet de volgende indeling hebben:

```
 subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

Wanneer &lt;text_x> Dit kan een combinatie zijn van statische tekst en dynamische tekenreeksvariabelen. De volgende variabelen kunnen in de e-mailsjabloon voor paginaberichten worden gebruikt:

* `${time}`, de datum en het tijdstip van de gebeurtenis.

* `${userFullName}`, de volledige naam van de gebruiker die de gebeurtenis heeft geactiveerd.

* `${userId}`, de id van de gebruiker die de gebeurtenis heeft geactiveerd.
* `${modifications}`beschrijft het type paginagebeurtenis en het paginapad in de notatie:

  &lt;page event=&quot;&quot; type=&quot;&quot;> => &lt;page path=&quot;&quot;>

  Bijvoorbeeld:

  PageModified => /content/geometrixx/nl/products

### E-mailsjablonen voor workflowmelding {#email-templates-for-workflow-notification}

Het e-mailsjabloon voor workflowmeldingen (Engels) bevindt zich op:

`/libs/settings/workflow/notification/email/default/en.txt`

Het wordt als volgt gedefinieerd:

```xml
subject=Workflow notification: ${event.EventType}

header=-------------------------------------------------------------------------------------\n \
Time: ${event.TimeStamp}\n \
Step: ${item.node.title}\n \
User: ${participant.name} (${participant.id})\n \
Workflow: ${model.title}\n \
-------------------------------------------------------------------------------------\n\n

message=Content: ${host.prefix}${payload.path.open}\n

footer=\n \
-------------------------------------------------------------------------------------\n \
View the overview in your ${host.prefix}/aem/inbox\n \
-------------------------------------------------------------------------------------\n \
This is an automatically generated message. Please do not reply.
```

#### E-mailsjablonen aanpassen voor workflowmelding {#customizing-email-templates-for-workflow-notification}

U kunt als volgt de Engelse e-mailsjabloon voor workflowgebeurtenismeldingen aanpassen:

1. Open het bestand in CRXDE:

   `/libs/settings/workflow/notification/email/default/en.txt`

1. Wijzig het bestand naar wens.
1. Sla de wijzigingen op.

De sjabloon moet de volgende indeling hebben:

```
subject=<text_1>
 header=<text_2>
 message=<text_3>
 footer=<text_4>
```

>[!NOTE]
>
>Wanneer `<text_x>` Dit kan een combinatie zijn van statische tekst en dynamische tekenreeksvariabelen. Elke regel van een `<text_x>` item moet worden beëindigd met een backslash ( `\`), behalve in de laatste instantie, wanneer de afwezigheid van de backslash het einde van de `<text_x>` tekenreeksvariabele
>
>Meer informatie over de sjabloonindeling vindt u in de [javadocs van the Properties.load()](https://docs.oracle.com/javase/8/docs/api/java/util/Properties.html#load-java.io.InputStream-) methode.

De methode `${payload.path.open}` onthult de weg aan de lading van het werkpunt. Voor bijvoorbeeld een pagina in Sites, dan `payload.path.open` zou vergelijkbaar zijn met `/bin/wcmcommand?cmd=open&path=…`.; dit is zonder de servernaam, daarom wordt dit door de sjabloon voorafgegaan `${host.prefix}`.

De volgende variabelen kunnen binnen het e-mailmalplaatje worden gebruikt:

* `${event.EventType}`, type gebeurtenis
* `${event.TimeStamp}`, datum en tijdstip van de gebeurtenis
* `${event.User}`, de gebruiker die de gebeurtenis heeft geactiveerd
* `${initiator.home}`, het pad naar het initiatorknooppunt

* `${initiator.name}`, de naam van de aanvrager

* `${initiator.email}`, e-mailadres van de aanvrager
* `${item.id}`, de id van het werkitem
* `${item.node.id}`, id van het knooppunt in het workflowmodel dat aan dit werkitem is gekoppeld
* `${item.node.title}`, titel van het werkitem
* `${participant.email}`, e-mailadres van de deelnemer
* `${participant.name}`, naam van de deelnemer
* `${participant.familyName}`, familienaam van de deelnemer
* `${participant.id}`, id van de deelnemer
* `${participant.language}`, de taal van de deelnemer
* `${instance.id}`, de workflow-id
* `${instance.state}`, de workflowstatus
* `${model.title}`, titel van het workflowmodel
* `${model.id}`, de id van het workflowmodel

* `${model.version}`, de versie van het workflowmodel
* `${payload.data}`, de lading

* `${payload.type}`, het ladingstype
* `${payload.path}`, pad van de lading
* `${host.prefix}`, hostvoorvoegsel, bijvoorbeeld: `http://localhost:4502`

### Een e-mailsjabloon toevoegen voor een nieuwe taal {#adding-an-email-template-for-a-new-language}

Een sjabloon toevoegen voor een nieuwe taal:

1. Voeg in CRXDE een bestand toe `<language-code>.txt` hieronder:

   * `/libs/settings/notification-templates/com.day.cq.wcm.core.page` : voor paginameldingen
   * `/libs/settings/workflow/notification/email/default` : voor workflowmeldingen

1. Pas het bestand aan de taal aan.
1. Sla de wijzigingen op.

>[!NOTE]
>
>De `<language-code>` gebruikt als de bestandsnaam van de e-mailsjabloon moet een taalcode van twee letters in kleine letters zijn die door AEM wordt herkend. Voor taalcodes is AEM gebaseerd op ISO-639-1.

## E-mailberichten voor AEM Assets configureren {#assetsconfig}

Wanneer Verzamelingen in AEM Assets worden gedeeld of niet gedeeld, kunnen gebruikers e-mailmeldingen ontvangen van AEM. Voer de volgende stappen uit om e-mailmeldingen te configureren.

1. De e-mailservice configureren, zoals hierboven beschreven in [De e-mailservice configureren](/help/sites-administering/notification.md#configuring-the-mail-service).
1. Meld u aan bij AEM als beheerder. Klikken **Gereedschappen** >  **Bewerkingen** >  **Webconsole** om de Configuratie van de Console van het Web te openen.
1. Bewerken **Day CQ DAM Resource Collection Servlet**. Selecteren **e-mail verzenden**. Klikken **Opslaan**.

## OAuth instellen {#setting-up-oauth}

AEM biedt OAuth2 steun voor zijn geïntegreerde Dienst van de Aannemer, om organisaties toe te staan om e-mailvereisten te beveiligen.

U kunt OAuth configureren voor meerdere e-mailproviders, zoals hieronder wordt beschreven.

>[!NOTE]
>
>Deze procedure is een voorbeeld voor een instantie Publish. Als u e-mailmeldingen wilt inschakelen voor een auteur, moet u dezelfde stappen uitvoeren voor de auteur.

### Gmail {#gmail}

1. Uw project maken op `https://console.developers.google.com/projectcreate`
1. Selecteer uw project en ga naar **API&#39;s en services** - **Dashboard - Credentials**
1. Configureer het scherm voor OAuth-instemming naar wens
1. Voeg de volgende twee bereiken toe in het scherm Bijwerken:
   * `https://mail.google.com/`
   * `https://www.googleapis.com//auth/gmail.send`
1. Als u het bereik hebt toegevoegd, gaat u terug naar **Credentials** in het linkermenu, ga dan naar **Credentials maken** - **OAuth-client-id** - **Desktop-app**
1. Er wordt een nieuw venster geopend met daarin de client-id en het clientgeheim.
1. Sla deze gegevens op.

**AEM zijconfiguraties**

>[!NOTE]
>
>Adobe Managed Service-klanten kunnen met hun Customer Service Engineer samenwerken om deze wijzigingen aan te brengen in productieomgevingen.

Eerst, vorm de Dienst van de Post:

1. Open de AEM webconsole door naar `http://serveraddress:serverport/system/console/configMgr`
1. Zoeken naar en klik vervolgens op **Day CQ Mail Service**
1. Voeg de volgende instellingen toe:
   * Naam SMTP-serverhost: `smtp.gmail.com`
   * SMTP-serverpoort: `25` of `587`, afhankelijk van de vereisten
   * Schakel de vakjes in voor **SMPT gebruik StarTLS** en **SMTP vereist StarTLS**
   * Controleren **OAuth-flow** en klik op **Opslaan**.

Daarna, vorm uw leverancier SMTP OAuth door de hieronder procedure te volgen:

1. Open de AEM webconsole door naar `http://serveraddress:serverport/system/console/configMgr`
1. Zoeken naar en klik vervolgens op **SMTP OAuth2-provider van CQ-mailer**
1. Vul de vereiste informatie als volgt in:
   * Autorisatie-URL: `https://accounts.google.com/o/oauth2/auth`
   * Token-URL: `https://accounts.google.com/o/oauth2/token`
   * Scopes: `https://www.googleapis.com/auth/gmail.send` en `https://mail.google.com/`. U kunt meer dan één bereik toevoegen door op de knop **+** knoop aan de rechterkant van elk gevormd werkingsgebied.
   * Client ID and Client Secret: configureer deze velden met de waarden die u hebt opgehaald, zoals beschreven in de bovenstaande alinea.
   * URL token vernieuwen: `https://accounts.google.com/o/oauth2/token`
   * Vervaldatum token vernieuwen: nooit
1. Klikken **Opslaan**.

<!-- clarify refresh token expiry, currently not present in the UI -->

Zodra gevormd, zouden de montages als dit moeten kijken:

![Het de configuratievenster van de Server van de Server SMTP Oauth2 van de Aannemer CQ](assets/oauth-smtpprov2.png)

Activeer nu de OAuth-componenten. U kunt dit doen door:

1. Ga naar de componentenconsole door deze URL te bezoeken: `http://serveraddress:serverport/system/console/components`
1. De volgende componenten zoeken
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeGenerateServlet`
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeAccessTokenGenerator`
1. Druk het pictogram van het Spel links van de componenten

   ![Lijst met componenten die de OAuthCodeGenerateServlet en OAuthCodeAccessTokenGenerator tonen](assets/oauth-components-play.png)

Bevestig ten slotte de configuratie door:

1. Ga naar het adres van de instantie Publiceren en meld u aan als beheerder.
1. Open een nieuw tabblad in de browser en ga naar `http://serveraddress:serverport/services/mailer/oauth2/authorize`. Dit zal u aan de pagina van uw leverancier SMTP, in dit geval Gmail opnieuw richten.
1. Aanmelding en toestemming voor het verlenen van de vereiste machtigingen
1. Na instemming wordt het token opgeslagen in de opslagplaats. U hebt toegang tot dit bestand onder `accessToken` door deze URL rechtstreeks te openen op uw publicatieexemplaar: `http://serveraddress:serverport/crx/de/index.jsp#/conf/global/settings/mailer/oauth`
1. Het bovenstaande voor elke publicatie-instantie herhalen

<!-- clarify if the ip/server address in the last procedure is that of the publish instance -->

### Microsoft Outlook {#microsoft-outlook}

1. Ga naar [https://portal.azure.com/](https://portal.azure.com/) en aanmelden.
1. Zoeken naar **Azure Active Directory** in de zoekbalk en klik op het resultaat. U kunt ook rechtstreeks bladeren naar [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)
1. Klikken op **Toepassingsregistratie** - **Nieuwe registratie**

   ![De nieuwe registratieknop bij het configureren van Microsoft Outlook](assets/oauth-outlook1.png)

1. Vul de gegevens naar wens in en klik op **Registreren**
1. Ga naar de nieuwe app en selecteer **API-machtigingen**
1. Ga naar **Machtiging toevoegen** - **Grafiekmachtigingen** - **Gedelegeerde machtigingen**
1. Selecteer de onderstaande machtigingen voor uw app en klik op **Machtiging toevoegen**:
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. Ga naar **Verificatie** - **Een platform toevoegen** - **Web** en in de **URL omleiden** , voegt u de volgende URL toe voor het omleiden van de OAuth-code en drukt u vervolgens op **Configureren**:
   * `http://localhost:4503/services/mailer/oauth2/token`
1. Het bovenstaande voor elke publicatie-instantie herhalen
1. Configureer de instellingen volgens uw vereisten
1. Ga vervolgens naar **Certificaten en geheimen**, klikt u op **Nieuw clientgeheim** en volg de stappen op het scherm om een geheim te maken. Let op dit geheim voor later gebruik
1. Druk **Overzicht** in het linkerdeelvenster en kopieer de waarden voor **Toepassings-id (client)** en **Directory (huurder)-id** voor later gebruik

Om opnieuw te verpakken, moet u de volgende informatie hebben om OAuth2 voor de dienst van de Aannemer op de AEM te vormen:

* Auth URL, die met huurderidentiteitskaart zal worden geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* De token-URL, die wordt samengesteld met de huurder-id. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Vernieuwen URL, die met huurder identiteitskaart zal worden geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Client-id
* Het clientgeheim

**AEM zijconfiguraties**

Vervolgens integreert u uw OAuth2-instellingen met AEM:

1. Ga naar de webconsole van uw lokale instantie door naar `http://serveraddress:serverport/system/console/configMgr`
1. Zoeken en klikken **Day CQ Mail Service**
1. Voeg de volgende instellingen toe:
   * Naam SMTP-serverhost: `smtp.office365.com`
   * SMTP-gebruiker: uw gebruikersnaam in e-mailindeling
   * Het adres &#39;Van&#39;: Het e-mailadres dat moet worden gebruikt in het veld &#39;Van:&#39; van berichten die door de mailer worden verzonden
   * SMTP-serverpoort: `25` of `587` afhankelijk van de vereisten
   * Schakel de vakjes in voor **SMPT gebruik StarTLS** en **SMTP vereist StarTLS**
   * Controleren **OAuth-flow** en klik op **Opslaan**.
1. Zoeken naar en klik vervolgens op **SMTP OAuth2-provider van CQ-mailer**
1. Vul de vereiste informatie als volgt in:
   * Vul de URL van de autorisatie-URL, de token-URL en de token-URL in door deze te maken zoals beschreven in [het einde van deze procedure](#microsoft-outlook)
   * Clientid en clientgeheim: configureer deze velden met de waarden die u hebt opgehaald zoals hierboven beschreven.
   * Voeg de volgende Scopes aan de configuratie toe:
      * openhartig
      * offline_access
      * `https://outlook.office365.com/Mail.Send`
      * `https://outlook.office365.com/Mail.Read`
      * `https://outlook.office365.com/SMTP.Send`
   * AuthCode Redirect URL: `http://localhost:4503/services/mailer/oauth2/token`
   * Token-URL vernieuwen: deze moet dezelfde waarde hebben als de bovenstaande token-URL
1. Klikken **Opslaan**.

Zodra gevormd, zouden de montages als dit moeten kijken:

![De voltooide configuratie van SMTP OAuth2 van de Mailer CQ](assets/oauth-outlook-smptconfig.png)

Activeer nu de OAuth-componenten. U kunt dit doen door:

1. Ga naar de componentenconsole door deze URL te bezoeken: `http://serveraddress:serverport/system/console/components`
1. De volgende componenten zoeken
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeGenerateServlet`
   * `com.day.cq.mailer.oauth.servlets.handler.OAuthCodeAccessTokenGenerator`
1. Druk het pictogram van het Spel links van de componenten

![Een fragment van de componentenlijst die OAuthCodeGenerateServlet en OAuthCodeAccessTokenGenerator bevat](assets/oauth-components-play.png)

Bevestig ten slotte de configuratie door:

1. Ga naar het adres van de instantie Publiceren en meld u aan als beheerder.
1. Open een nieuw tabblad in de browser en ga naar `http://serveraddress:serverport/services/mailer/oauth2/authorize`. Dit zal u aan de pagina van uw leverancier SMTP, in dit geval Vooruitzichten opnieuw richten.
1. Aanmelding en toestemming voor het verlenen van de vereiste machtigingen
1. Na instemming wordt het token opgeslagen in de opslagplaats. U hebt toegang tot dit bestand onder `accessToken` door deze URL rechtstreeks te openen op uw publicatieexemplaar: `http://serveraddress:serverport/crx/de/index.jsp#/conf/global/settings/mailer/oauth`
