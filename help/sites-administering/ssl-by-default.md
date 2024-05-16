---
title: Standaard SSL/TLS
description: Leer hoe u in AEM 6.5 SSL standaard kunt gebruiken.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
docset: aem65
exl-id: 574e2fc2-6ebf-49b6-9b65-928237a8a34d
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 9b766fe6e253782be3bc47849b4857216274ae20
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Standaard SSL/TLS{#ssl-tls-by-default}

In een poging om de veiligheid van AEM onophoudelijk te verbeteren, heeft de Adobe een eigenschap genoemd SSL Door Standaard geïntroduceerd. Het doel is het gebruik van HTTPS aan te moedigen om verbinding te maken met AEM instanties.

## SSL/TLS standaard inschakelen {#enabling-ssl-tls-by-default}

U kunt standaard beginnen SSL/TLS te configureren door te klikken op het betreffende Postvak IN-bericht van uw AEM startscherm. Druk op het belpictogram in de rechterbovenhoek van het scherm om het vak Inbox te bereiken. Klik vervolgens op **Alles weergeven**. Hiermee wordt een lijst weergegeven met alle waarschuwingen die in een lijstweergave zijn besteld.

Selecteer in de lijst de optie **HTTPS configureren** waarschuwing:

![chlimage_1-103](assets/chlimage_1-103.png)

>[!NOTE]
>
>Als de **HTTPS configureren** waakzaamheid is niet aanwezig in Inbox, u kunt rechtstreeks aan de Tovenaar navigeren HTTPS door te gaan *<http://serveraddress:serverport/libs/granite/security/content/sslConfig.html?item=configuration%2fconfiguressl&_charset_=utf-8>*

Een servicegebruiker die **ssl-service** is gemaakt voor deze functie. Zodra u het alarm opent, zult u door de volgende configuratietovenaar worden geleid:

1. Stel eerst de gegevens voor de winkelreferenties in. Dit zijn de referenties voor de **ssl-service** sleutelarchief van de systeemgebruiker dat de persoonlijke sleutel en vertrouwde opslag voor de luisteraar HTTPS zal bevatten.

   ![chlimage_1-104](assets/chlimage_1-104.png)

1. Nadat u de referenties hebt ingevoerd, klikt u op **Volgende** rechtsboven op de pagina. Vervolgens uploadt u de bijbehorende persoonlijke sleutel en het bijbehorende certificaat voor de SSL/TLS-verbinding.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   >[!NOTE]
   >
   >Ga voor informatie over het genereren van een persoonlijke sleutel en een certificaat voor gebruik met de wizard naar [deze procedure](/help/sites-administering/ssl-by-default.md#generating-a-private-key-certificate-pair-to-use-with-the-wizard) hieronder.

1. Geef ten slotte de hostnaam HTTPS en de TCP-poort voor de HTTPS-listener op.

   ![screen_shot_2018-07-25at31658pm](assets/screen_shot_2018-07-25at31658pm.png)

## SSL/TLS standaard automatiseren {#automating-ssl-tls-by-default}

Er zijn drie manieren om standaard SSL/TLS te automatiseren.

### Via HTTP-POST {#via-http-post}

De eerste methode impliceert het posten aan de server SSLSetup die door de configuratietovenaar wordt gebruikt:

```shell
POST /libs/granite/security/post/sslSetup.html
```

U kunt de volgende nuttige lading in uw POST gebruiken om configuratie te automatiseren:

```xml
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="keystorePassword"

test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="keystorePasswordConfirm"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="truststorePassword"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="truststorePasswordConfirm"
test
------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="privatekeyFile"; filename="server.der"
Content-Type: application/x-x509-ca-cert

------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="certificateFile"; filename="server.crt"
Content-Type: application/x-x509-ca-cert

------WebKitFormBoundaryyBO4ArmGlcfdGDbs
Content-Disposition: form-data; name="httpsPort"
8443
```

De servlet zal, net als elke sling POST servlet, met 200 OK of een foutHTTP- statuscode antwoorden. U kunt meer informatie over de status vinden in de HTML-tekst van de reactie.

Hieronder staan voorbeelden voor zowel een geslaagde reactie als een fout.

**SUCCESVOORBEELD** (status = 200):

```xml
<!DOCTYPE html>
<html lang='en'>
<head>
<title>OK</title>
</head>
<body>
<h1>OK</h1>
<dl>
<dt class='foundation-form-response-status-code'>Status</dt>
<dd>200</dd>
<dt class='foundation-form-response-status-message'>Message</dt>
<dd>SSL successfully configured</dd>
<dt class='foundation-form-response-title'>Title</dt>
<dd>OK</dd>
<dt class='foundation-form-response-description'>Description</dt>
<dd>HTTPS has been configured on port 8443. The private key and
certificate were stored in the key store of the user ssl-service.
Take note of the key store password you provided. You need
it for any subsequent updating of the private key or certificate.</dd>
</dl>
<h2>Links</h2>
<ul class='foundation-form-response-links'>
<li><a class='foundation-form-response-redirect' href='/'>Done</a></li>
</ul>
</body>
</html>
```

**FOUTVOORBEELD** (status = 500):

```xml
<!DOCTYPE html>
<html lang='en'>
<head>
<title>Error</title>
</head>
<body>
<h1>Error</h1>
<dl>
<dt class='foundation-form-response-status-code'>Status</dt>
<dd>500</dd>
<dt class='foundation-form-response-status-message'>Message</dt>
<dd>The provided file is not a valid key, DER format expected</dd>
<dt class='foundation-form-response-title'>Title</dt>
<dd>Error</dd>
</dl>
</body>
</html>
```

### Via pakket {#via-package}

U kunt de installatie van SSL/TLS ook automatiseren door een pakket te uploaden dat al deze vereiste items bevat:

* Het sleutelarchief van de gebruiker van de ssl-dienst. Deze bevindt zich onder */home/users/system/security/ssl-service/keystore* in de repository.
* De `GraniteSslConnectorFactory` configuratie

### Een privésleutel/certificaatpaar genereren voor gebruik met de wizard {#generating-a-private-key-certificate-pair-to-use-with-the-wizard}

Hieronder ziet u een voorbeeld voor het maken van een zelfondertekend certificaat in de indeling DER die de wizard SSL/TLS kan gebruiken. Installeer OpenSSL op basis van het besturingssysteem, open de opdrachtprompt OpenSSL en wijzig de map in de map waarin u de persoonlijke sleutel of het certificaat wilt genereren.

>[!NOTE]
>
>Het gebruik van een zelfondertekend certificaat is alleen bedoeld voor voorbeelddoeleinden. Niet gebruiken in de productie.

1. Maak eerst de persoonlijke sleutel:

   ```shell
   openssl genrsa -aes256 -out localhostprivate.key 4096
   openssl rsa -in localhostprivate.key -out localhostprivate.key
   ```

1. Genereer vervolgens een CSR (Certificate Signing Request) met behulp van de persoonlijke sleutel:

   ```shell
   openssl req -sha256 -new -key localhostprivate.key -out localhost.csr -subj "/CN=localhost"
   ```

1. Genereer het SSL/TLS-certificaat en onderteken het met de persoonlijke sleutel. In dit voorbeeld verloopt de bewerking over een jaar:

   ```shell
   openssl x509 -req -days 365 -in localhost.csr -signkey localhostprivate.key -out localhost.crt
   ```

1. Zet de Persoonlijke Sleutel in het formaat van DER om. De reden hiervoor is dat de SSL-wizard vereist dat de sleutel de indeling DER heeft:

   ```shell
   openssl pkcs8 -topk8 -inform PEM -outform DER -in localhostprivate.key -out localhostprivate.der -nocrypt
   ```

1. Ten slotte uploadt u de **localhostprivate.der** als persoonlijke sleutel en **localhost.crt** als het SSL/TLS-certificaat in stap 2 van de grafische SSL/TLS-wizard die aan het begin van deze pagina wordt beschreven.

### De SSL/TLS-configuratie bijwerken via cURL {#updating-the-ssl-tls-configuration-via-curl}

>[!NOTE]
>
>Zie [cURL gebruiken met AEM](https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/curl.html) voor een gecentraliseerde lijst van nuttige cURL bevelen in AEM.

U kunt de SSL/TLS-configuratie ook automatiseren met het gereedschap cURL. U kunt dit doen door de configuratieparameters aan dit URL te posten:

*https://&lt;serveraddress>:&lt;serverport>/libs/granite/security/post/sslSetup.html*

Hieronder vindt u de parameters die u kunt gebruiken om de verschillende instellingen in de configuratietovenaar te wijzigen:

* `-F "keystorePassword=password"` - het sleutelarchiefwachtwoord;

* `-F "keystorePasswordConfirm=password"` - het keystore-wachtwoord bevestigen;

* `-F "truststorePassword=password"` - het truststore-wachtwoord;

* `-F "truststorePasswordConfirm=password"` - het truststore-wachtwoord bevestigen;

* `-F "privatekeyFile=@localhostprivate.der"` - de persoonlijke sleutel specificeren;

* `-F "certificateFile=@localhost.crt"` - het certificaat vermelden;

* `-F "httpsHostname=host.example.com"`- de hostnaam te specificeren;
* `-F "httpsPort=8443"` - de poort waaraan de HTTPS-listener werkt.

>[!NOTE]
>
>De snelste manier om cURL uit te voeren om de configuratie SSL/TLS te automatiseren is van de omslag waar de DER en CRT dossiers zijn. U kunt ook het volledige pad opgeven in het dialoogvenster `privatekeyFile` en certificateFile-argumenten.
>
>U moet ook worden geverifieerd om de update uit te voeren, dus zorg ervoor dat u de opdracht cURL toevoegt aan de opdracht `-u user:passeword` parameter.
>
>Een correcte post cURL zou als dit moeten kijken:

```shell
curl -u user:password -F "keystorePassword=password" -F "keystorePasswordConfirm=password" -F "truststorePassword=password" -F "truststorePasswordConfirm=password" -F "privatekeyFile=@localhostprivate.der" -F "certificateFile=@localhost.crt" -F "httpsHostname=host.example.com" -F "httpsPort=8443" https://host:port/libs/granite/security/post/sslSetup.html
```

#### Meerdere certificaten met cURL {#multiple-certificates-using-curl}

U kunt de server een certificaatketen sturen door de parameter certificateFile als volgt te herhalen:

`-F "certificateFile=@root.crt" -F "certificateFile=@localhost.crt"..`

Zodra u het bevel hebt uitgevoerd, verifieer dat alle certificaten het aan keystore maakten. Controleer de **Keystore** vermeldingen van:
[http://localhost:4502/libs/granite/security/content/v2/usereditor.html/home/users/system/security/ssl-service](http://localhost:4502/libs/granite/security/content/v2/usereditor.html/home/users/system/security/ssl-service)

### Een TLS 1.3-verbinding inschakelen {#enabling-tls-connection}

1. Ga naar de webconsole
1. Blader vervolgens naar **OSGi** - **Configuratie** - **Adobe graniet SSL Connector Factory**
1. Ga naar de **Inclusief cementsuites** en voeg de volgende vermeldingen toe. U kunt elke toevoeging bevestigen door op &quot;**+**&quot;, links van het veld, na elke knop in te voegen:

   * `TLS_AES_256_GCM_SHA384`
   * `TLS_AES_128_GCM_SHA256`
   * `TLS_CHACHA20_POLY1305_SHA256`
   * `TLS_AES_128_CCM_SHA256`
   * `TLS_AES_128_CCM_8_SHA256`
