---
title: SSL configureren voor WebLogic Server
description: Leer hoe u een SSL-referentie maakt voor gebruik op een WebLogic-server en hoe u SSL voor WebLogic Server configureert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---


# SSL configureren voor WebLogic Server {#configuring-ssl-for-weblogic-server}

Voor het configureren van SSL op WebLogic Server hebt u een SSL-referentie nodig voor verificatie. U kunt Java gebruiken keytool om de volgende taken uit te voeren om een referentie tot stand te brengen:

* Creeer een openbaar/privé zeer belangrijk paar, verpak de openbare sleutel in een X.509 v1 zelf-ondertekend certificaat dat als enig-elementcertificaatketting wordt opgeslagen, en bewaar dan de certificaatketting en de privé sleutel in een nieuw sleutelarchief. Dit sleutelarchief is het sleutelarchief voor aangepaste identiteiten van de toepassingsserver.
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
     <li><p>Keystore van de Identiteit van de douane: <code>[</code><i> appserverdomain <code>]</code></i><code>/adobe/</code> <i> [servernaam] </i><code>/ads-ssl.jks</code></p></li>
     <li><p>Keystore van het Vertrouwen van de douane: <code>[</code><i> appserverdomain <code>]</code></i><code>/adobe/</code> <i> [servernaam] </i><code>/ads-ca.jks</code></p></li>
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
     <li><p>Aangepast sleutelarchief voor identiteiten: het sleutelarchiefwachtwoord moet overeenkomen met het SSL-wachtwoord dat is opgegeven voor de component Trust Store van de beheerconsole.</p></li>
     <li><p>Aangepast sleutelarchief voor vertrouwen: gebruik hetzelfde wachtwoord als voor het sleutelarchief voor aangepaste identiteiten.</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>-keypass</p></td>
   <td><p>Het wachtwoord dat de persoonlijke sleutel van het sleutelpaar beschermt.</p></td>
   <td><p>Gebruik hetzelfde wachtwoord als voor de optie <code>-storepass</code> . Het sleutelwachtwoord moet ten minste zes tekens lang zijn.</p></td>
  </tr>
  <tr>
   <td><p>-dname</p></td>
   <td><p>De DN-naam die de eigenaar van het sleutelarchief aangeeft.</p></td>
   <td><p><code>"CN=</code><code>[User name]</code><code>,OU=</code><code>[Group Name]</code><code>, O=</code><code>[Company Name]</code><code>, L=</code><code>[City Name]</code><code>, S=</code><code>[State or province]</code><code>, C=</code><code>[Country Code]</code><code>"</code></p>
    <ul>
     <li><p><code><i>[User name]</i></code> Dit is de identificatie van de gebruiker die eigenaar is van het sleutelarchief.</p></li>
     <li><p><code><i>[Group Name]</i></code> is de identificatie van de ondernemingsgroep waartoe de eigenaar van het sleutelarchief behoort.</p></li>
     <li><p><code><i>[Company Name]</i></code> is de naam van uw organisatie.</p></li>
     <li><p><code><i>[City Name]</i></code> Dit is de stad waar uw organisatie zich bevindt.</p></li>
     <li><p><code><i>[State or province]</i></code> is de staat of provincie waar uw organisatie zich bevindt.</p></li>
     <li><p><code><i>[Country Code]</i></code> Dit is de tweelettercode voor het land waar uw organisatie zich bevindt.</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

Zie het bestand keytool.html in de JDK-documentatie voor meer informatie over het gebruik van de opdracht keytool.

## De sleutelarchieven Aangepaste identiteit en Vertrouwen maken {#create-the-custom-identity-and-trust-keystores}

1. Van een bevelherinnering, navigeer aan *[appserverdomain]*/adobe/*[servernaam]*.
1. Voer de volgende opdracht in:

   `[JAVA_HOME]/bin/keytool -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass store_password -keypass key_password -dname "CN=Hostname, OU=Group Name, O=Company Name, L=City Name, S=State,C=Country Code`

   >[!NOTE]
   >
   >Vervang `[JAVA_HOME]`*met de folder waar JDK geïnstalleerd is, en vervang de tekst cursief met waarden die met uw milieu beantwoorden.*

   Bijvoorbeeld:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -genkey -v -alias ads-credentials -keyalg RSA -keystore "ads-credentials.jks" -validity 3650 -storepass P@ssw0rd -keypass P@ssw0rd -dname "CN=wasnode01, OU=LC, O=Adobe, L=Noida, S=UP,C=91
   ```

   Het sleutelarchiefdossier van de Identiteit van de Douane genoemd &quot;ads-credentials.jks&quot;wordt gecreeerd in [ appserverdomain ]/adobe/[ servernaam ] folder.

1. Extraheer het certificaat uit het sleutelarchief met advertenties door de volgende opdracht in te voeren:

   [ JAVA_HOME ]`/bin/keytool -export -v -alias ads-credentials`

   `-file "ads-ca.cer" -keystore "ads-credentials.jks"`

   `-storepass` `*store*` *_ **wachtwoord**

   >[!NOTE]
   >
   >Vervang `[JAVA_HOME]` door de map waarin de JDK is geïnstalleerd en vervang `store`*_* `password`* door het wachtwoord voor het sleutelarchief van de Aangepaste identiteit.*

   Bijvoorbeeld:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -export -v -alias ads-credentials -file "ads-ca.cer" -keystore "ads-credentials.jks" -storepass P@ssw0rd
   ```

   Het certificaatdossier genoemd &quot;ads-ca.cer&quot;wordt gecreeerd in [ appserverdomain ]/adobe/[*servernaam*] folder.

1. Kopieer het bestand ads-ca.cer naar alle hostcomputers die beveiligde communicatie met de toepassingsserver nodig hebben.
1. Voeg het certificaat in een nieuw sleutelarchiefbestand in (het sleutelarchief van Aangepast vertrouwen) door de volgende opdracht in te voeren:

   [ JAVA_HOME ] `/bin/keytool -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass store_password -keypass key_password`

   >[!NOTE]
   >
   >Vervang `[JAVA_HOME]` met de folder waar JDK geïnstalleerd is, en vervang `store`*_* `password` en `key`*_* `password` *met uw eigen wachtwoorden.*

   Bijvoorbeeld:

   ```java
   C:\Program Files\Java\jrockit-jdk1.6.0_24-R28\bin\keytool" -import -v -noprompt -alias bedrock -file "ads-ca.cer" -keystore "ads-ca.jks" -storepass Password1 -keypass Password1
   ```

Het sleutelarchiefdossier van het Vertrouwen van de Douane genoemd &quot;advertenties-ca.jks&quot;wordt gecreeerd in [ appserverdomain ]/adobe/&#39;server&#39; folder.

Configureer WebLogic zodanig dat deze gebruikmaakt van het sleutelarchief Aangepaste identiteit en het sleutelarchief Aangepast vertrouwen dat u hebt gemaakt. Schakel ook de WebLogic Hostname Verification-functie uit omdat de DN-naam die is gebruikt om de sleutelarchiefbestanden te maken, niet de naam van de computer bevat die als host fungeert voor WebLogic Server.

## WebLogic configureren om SSL te gebruiken {#configure-weblogic-to-use-ssl}

1. Begin de WebLogic Server beleidsconsole door `https://`*[ gastheernaam ]*`:7001/console` in de lijn URL van Webbrowser te typen.
1. Onder Milieu, in de Configuraties van het Domein, uitgezochte **Servers > &quot;server&quot;> Configuratie > Algemeen**.
1. Onder Algemeen, in Configuratie, zorg ervoor dat **Toegelaten Haven** beluistert en **SSL Toegelaten Haven** wordt geselecteerd. Als deze optie niet is ingeschakeld, voert u de volgende handelingen uit:

   1. Onder het Centrum van de Verandering, klik **Slot &amp; geef** uit om selecties en waarden te wijzigen.
   1. Controleer **Toegelaten Haven** en **SSL luisteren Toegelaten Haven** controledozen.

1. Als deze server een Beheerde Server is, de verandering luistert Haven aan een ongebruikte havenwaarde (zoals 8001) en SSL luistert Haven aan een ongebruikte havenwaarde (zoals 8002). Voor een stand-alone server, is de standaardSSL haven 7002.
1. Klik **Configuratie van de Versie**.
1. Onder Milieu, in de Configuraties van het Domein, klik **Servers > [*Beheerde Server*] > Configuratie > Algemeen**.
1. Onder Algemeen, in Configuratie, uitgezochte **Sleutelarchieven**.
1. Onder het Centrum van de Verandering, klik **Slot &amp; geef** uit om selecties en waarden te wijzigen.
1. Klik **Verandering** om de sleutelarchieflijst als drop-down lijst te krijgen en **Douane Identiteit en het Vertrouwen van de Douane te selecteren**.
1. Geef onder Identiteit de volgende waarden op:

   **Keystore van de Identiteit van de Douane**: *[appserverdomain]*/adobe/*[servernaam]* /ads-credentials.jks, waar *[ appserverdomain ] *is de daadwerkelijke weg en *[servernaam]* is de naam van de toepassingsserver.

   **Type van Keystore van de Identiteit van de Douane**: JKS

   **Keystore Passphrase van de Identiteit van de Douane**: *mypassword* (het wachtwoord van het sleutelarchief van de douaneidentiteit)

1. Geef onder Vertrouwd de volgende waarden op:

   **Naam van het Dossier van het Sleutelarchief van het Vertrouwen van de Douane**: `*[appserverdomain]*/adobe/*'server'*/ads-ca.jks`, waar `*[appserverdomain]*` de daadwerkelijke weg is

   **Type van Keystore van het Vertrouwen van de Douane**: JKS

   **Uitgezochte Uitgeefte van het Sleutelarchief van het Vertrouwen Wis**: *mypassword* (het belangrijkste wachtwoord van het douanevertrouwen)

1. Onder Algemeen, in Configuratie, uitgezochte **SSL**.
1. Standaard is Keystore geselecteerd voor Identiteit en Vertrouwenslocaties. Als dat niet het geval is, wijzigt u deze in sleutelarchief.
1. Geef onder Identiteit de volgende waarden op:

   **Persoonlijke Zeer belangrijke alias**: advertenties-geloofsbrieven

   **Passphrase**: *mypassword*

1. Klik **Configuratie van de Versie**.

## De functie Hostnaamverificatie uitschakelen {#disable-the-hostname-verification-feature}

1. Klik op SSL op het tabblad Configuratie.
1. Selecteer onder Geavanceerd de optie Geen in de lijst Hostnaamverificatie.

   Als Hostnaamverificatie niet is uitgeschakeld, moet de CN (Common Name) de hostnaam van de server bevatten.

1. Klik onder Midden wijzigen op Vergrendelen en bewerken om selecties en waarden te wijzigen.
1. Start de toepassingsserver opnieuw.

