---
title: SSL configureren voor WebLogic Server
seo-title: SSL configureren voor WebLogic Server
description: Leer hoe u een SSL-referentie maakt voor gebruik op een WebLogic-server en hoe u SSL voor WebLogic Server configureert.
seo-description: Leer hoe u een SSL-referentie maakt voor gebruik op een WebLogic-server en hoe u SSL voor WebLogic Server configureert.
uuid: 8ee979fd-2615-451b-a607-4f73ecfed4f9
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 968c2574-ec9a-45ca-9c64-66f4caeec285
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---


# SSL configureren voor WebLogic Server {#configuring-ssl-for-weblogic-server}

Voor het configureren van SSL op WebLogic Server hebt u een SSL-referentie nodig voor verificatie. U kunt Java gebruiken keytool om de volgende taken uit te voeren om een referentie tot stand te brengen:

* Creeer een openbaar/privé zeer belangrijk paar, verpak de openbare sleutel in een X.509 v1 zelf-ondertekend certificaat dat als enig-elementcertificaatketting wordt opgeslagen, en bewaar dan de certificaatketting en de privé sleutel in een nieuw sleutelarchief. Dit sleutelarchief is het sleutelarchief van de Aangepaste Identiteit van de toepassingsserver.
* Extraheer het certificaat en voeg het in een nieuw sleutelarchief in. Dit sleutelarchief is het sleutelarchief van het Aangepast vertrouwen van de toepassingsserver.

Vervolgens configureert u WebLogic zodanig dat deze gebruikmaakt van het sleutelarchief voor aangepaste identiteiten en het sleutelarchief voor aangepaste vertrouwen dat u hebt gemaakt. Schakel ook de WebLogic Hostname Verification-functie uit omdat de DN-naam die is gebruikt om de sleutelarchiefbestanden te maken, niet de naam van de computer bevat die als host fungeert voor WebLogic.

## SSL-referentie maken voor gebruik op WebLogic Server {#creating-an-ssl-credential-for-use-on-weblogic-server}

De opdracht Keytool bevindt zich gewoonlijk in de map JavaJre/bin en moet verschillende opties en optiewaarden bevatten, die in de volgende tabel worden vermeld.

<table>
 <thead>
  <tr>
   <th><p>Gereedschap Keytool, optie</p></th>
   <th><p>Beschrijving</p></th>
   <th><p>Option-waarde</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>-alias</p></td>
   <td><p>De alias van het sleutelarchief.</p></td>
   <td>
    <ul>
     <li><p>Aangepast sleutelarchief voor identiteiten: <code>ads-credentials</code></p></li>
     <li><p>Aangepast sleutelarchief vertrouwen: <code>bedrock</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keyalg</p></td>
   <td><p>Het algoritme dat moet worden gebruikt om het sleutelpaar te genereren.</p></td>
   <td><p>RSA</p><p>U kunt een verschillend algoritme, afhankelijk van het beleid van uw bedrijf gebruiken.</p></td>
  </tr>
  <tr>
   <td><p>-keystore</p></td>
   <td><p>De locatie en naam van het sleutelarchiefbestand.</p><p>De locatie kan het absolute pad van het bestand bevatten. Of het kan relatief zijn ten opzichte van de huidige map van de opdrachtprompt waar de sleutelgereedschapsopdracht wordt ingevoerd.</p></td>
   <td>
    <ul>
     <li><p>Aangepast sleutelarchief voor identiteiten: <code>[</code><i>appserverdomain]</i><code>/adobe/</code><i>[servernaam]</i><code>/ads-ssl.jks</code></p></li>
     <li><p>Aangepast sleutelarchief vertrouwen: <code>[</code><i>appserverdomain]</i><code>/adobe/</code><i>[servernaam]</i><code>/ads-ca.jks</code></p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-file</p></td>
   <td><p>De locatie en naam van het certificaatbestand.</p></td>
   <td><code> ads-ca.cer</code></td>
  </tr>
  <tr>
   <td><p>-geldigheid</p></td>
   <td><p>Het aantal dagen dat het certificaat als geldig wordt beschouwd.</p></td>
   <td><p>3650</p><p>U kunt een verschillende waarde gebruiken, afhankelijk van het beleid van uw bedrijf.</p></td>
  </tr>
  <tr>
   <td><p>-storepass</p></td>
   <td><p>Het wachtwoord waarmee de inhoud van het sleutelarchief wordt beveiligd. </p></td>
   <td>
    <ul>
     <li><p>Aangepast sleutelarchief voor identiteiten: Het sleutelarchiefwachtwoord moet met het SSL credentiewachtwoord beantwoorden dat voor de component van de Opslag van het Vertrouwen van de Console van het Beleid werd gespecificeerd.</p></li>
     <li><p>Aangepast sleutelarchief vertrouwen: Gebruik hetzelfde wachtwoord als voor het sleutelarchief voor aangepaste identiteiten.</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keypass</p></td>
   <td><p>Het wachtwoord dat de persoonlijke sleutel van het sleutelpaar beschermt.</p></td>
   <td><p>Gebruik hetzelfde wachtwoord als voor de <code>-storepass</code> optie. Het sleutelwachtwoord moet ten minste zes tekens lang zijn.</p></td>
  </tr>
  <tr>
   <td><p>-dname</p></td>
   <td><p>De DN-naam die de persoon identificeert die eigenaar is van het sleutelarchief.</p></td>
   <td><p><code>"CN=</code><code>[User name]</code><code>,OU=</code><code>[Group Name]</code><code>, O=</code><code>[Company Name]</code><code>, L=</code><code>[City Name]</code><code>, S=</code><code>[State or province]</code><code>, C=</code><code>[Country Code]</code><code>"</code></p>
    <ul>
     <li><p><code><i>[User name]</i></code> Dit is de identificatie van de gebruiker die eigenaar is van het sleutelarchief.</p></li>
     <li><p><code><i>[Group Name]</i></code> is de identificatie van de ondernemingsgroep waartoe de eigenaar van het sleutelarchief behoort.</p></li>
     <li><p><code><i>[Company Name]</i></code> is de naam van uw organisatie.</p></li>
     <li><p><code><i>[City Name]</i></code> is de stad waar uw organisatie zich bevindt.</p></li>
     <li><p><code><i>[State or province]</i></code> is de staat of provincie waar uw organisatie zich bevindt.</p></li>
     <li><p><code><i>[Country Code]</i></code> Dit is de tweelettercode voor het land waar uw organisatie zich bevindt.</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

Zie het bestand keytool.html in de JDK-documentatie voor meer informatie over het gebruik van de opdracht keytool.

## De sleutelarchieven Aangepaste identiteit en Vertrouwen maken {#create-the-custom-identity-and-trust-keystores}

1. Navigeer vanaf een opdrachtprompt naar *[toepassingsdomein]*/adobe/*[servernaam]*.
1. Voer de volgende opdracht in:

   `[JAVA_HOME]/bin/keytool -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass store_password -keypass key_password -dname "CN=Hostname, OU=Group Name, O=Company Name, L=City Name, S=State,C=Country Code`

   >[!NOTE]
   >
   >Vervang de tekst cursief door de cursieve `[JAVA_HOME]`*map waarin de JDK is geïnstalleerd en vervang deze door waarden die overeenkomen met de omgeving.*

   Bijvoorbeeld:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass P@ssw0rd -keypass P@ssw0rd -dname "CN=wasnode01, OU=LC, O=Adobe, L=Noida, S=UP,C=91
   ```

   Het sleutelarchiefbestand voor aangepaste identiteiten met de naam &quot;ads-credentials.jks&quot; wordt gemaakt in de map [appserverdomain]/adobe/[server name] .

1. Extraheer het certificaat uit het sleutelarchief met advertenties door de volgende opdracht in te voeren:

   [JAVA_HOME]`/bin/keytool -export -v -alias ads-credentials`

   `-file "ads-ca.cer" -keystore "ads-credentials.jks"`

   `-storepass` `*store*`*_**password**

   >[!NOTE]
   >
   >Vervang `[JAVA_HOME]` de map waarin de JDK is geïnstalleerd en vervang `store`*_*`password`* door het wachtwoord voor het sleutelarchief voor aangepaste identiteiten.*

   Bijvoorbeeld:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -export -v -alias ads-credentials -file "ads-ca.cer" -keystore "ads-credentials.jks" -storepass P@ssw0rd
   ```

   Het certificaatbestand &quot;ads-ca.cer&quot; wordt gemaakt in de map [appserverdomain]/adobe/[*server name*] .

1. Kopieer het bestand ads-ca.cer naar alle hostcomputers die beveiligde communicatie met de toepassingsserver nodig hebben.
1. Voeg het certificaat in een nieuw sleutelarchiefbestand in (het sleutelarchief van Aangepast vertrouwen) door de volgende opdracht in te voeren:

   [JAVA_HOME] `/bin/keytool -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass store_password -keypass key_password`

   >[!NOTE]
   >
   >Vervang `[JAVA_HOME]` door de directory waarin JDK is geïnstalleerd, en vervang `store`*_*`password`en`key`*_* `password` *met uw eigen wachtwoorden.*

   Bijvoorbeeld:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass Password1 -keypass Password1
   ```

Het sleutelarchiefbestand voor aangepast vertrouwen met de naam &quot;ads-ca.jks&quot; wordt gemaakt in de map [appserverdomain]/adobe/&#39;server&#39;.

Configureer WebLogic zodanig dat deze gebruikmaakt van het sleutelarchief Aangepaste identiteit en het sleutelarchief Aangepast vertrouwen dat u hebt gemaakt. Schakel ook de WebLogic Hostname Verification-functie uit omdat de DN-naam die is gebruikt om de sleutelarchiefbestanden te maken, niet de naam van de computer bevat die als host fungeert voor WebLogic Server.

## WebLogic configureren om SSL te gebruiken {#configure-weblogic-to-use-ssl}

1. Start de WebLogic Server-beheerconsole door de `https://`*[hostnaam ]*te typen`:7001/console`in de URL-regel van een webbrowser.
1. Selecteer in Domeinconfiguraties onder Omgeving de optie **Servers > &#39;server&#39; > Configuratie > Algemeen**.
1. Onder Algemeen, in Configuratie, zorg ervoor dat de Toegelaten **Haven van de** Luister en **SSL Toegelaten** Haven van de Luister worden geselecteerd. Als deze optie niet is ingeschakeld, voert u de volgende handelingen uit:

   1. Klik onder Wijzigen in midden op **Vergrendelen en bewerken** om selecties en waarden te wijzigen.
   1. Schakel de selectievakjes **Luisteren naar poort ingeschakeld** en **SSL Luister naar poort ingeschakeld** .

1. Als deze server een Beheerde Server is, de verandering luistert Haven aan een ongebruikte havenwaarde (zoals 8001) en SSL luistert Haven aan een ongebruikte havenwaarde (zoals 8002). Voor een stand-alone server, is de standaardSSL haven 7002.
1. Klik op Configuratie **vrijgeven**.
1. Klik in Environment (Domeinconfiguraties) op **Servers >[*Beheerde server*]> Configuratie > Algemeen**.
1. Onder Algemeen, in Configuratie, uitgezochte **Toetsen**.
1. Klik onder Wijzigen in midden op **Vergrendelen en bewerken** om selecties en waarden te wijzigen.
1. Klik op **Wijzigen** om de lijst met sleutelarchieven op te halen als een vervolgkeuzelijst en selecteer **Aangepaste identiteit en aangepast vertrouwen**.
1. Geef onder Identiteit de volgende waarden op:

   **Aangepast identiteitssleutelarchief**: *[appserverdomain]*/adobe/*[server name]*/ads-credentials.jks, waarbij *[appserverdomain] *het daadwerkelijke pad is en de *[servernaam]* de naam van de toepassingsserver.

   **Type** aangepast identiteitssleutelarchief: JKS

   **Passphrase** van het Toetsenarchief van de Identiteit: *mypassword* (aangepast sleutelarchiefwachtwoord voor identiteit)

1. Geef onder Vertrouwd de volgende waarden op:

   **Aangepaste sleutelarchiefbestandsnaam** vertrouwen: `*[appserverdomain]*/adobe/*'server'*/ads-ca.jks`, waar `*[appserverdomain]*` is het werkelijke pad?

   **Type** aangepast sleutelarchief vertrouwen: JKS

   **Wachtwoordgroep** voor aangepast vertrouwen: *mypassword* (aangepast wachtwoord voor vertrouwenssleutel)

1. Onder Algemeen, in Configuratie, uitgezochte **SSL**.
1. Standaard is Keystore geselecteerd voor Identiteit en Vertrouwenslocaties. Als dat niet het geval is, wijzigt u deze in sleutelarchief.
1. Geef onder Identiteit de volgende waarden op:

   **Alias** persoonlijke sleutel: advertenties

   **Wachtwoordzin**: *mypassword*

1. Klik op Configuratie **vrijgeven**.

## De functie Hostnaamverificatie uitschakelen {#disable-the-hostname-verification-feature}

1. Klik op SSL op het tabblad Configuratie.
1. Selecteer onder Geavanceerd de optie Geen in de lijst Hostnaamverificatie.

   Als Hostnaamverificatie niet is uitgeschakeld, moet de CN (Common Name) de hostnaam van de server bevatten.

1. Klik onder Midden wijzigen op Vergrendelen en bewerken om selecties en waarden te wijzigen.
1. Start de toepassingsserver opnieuw.

