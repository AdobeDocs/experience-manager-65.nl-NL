---
title: SSL configureren voor JBoss Application Server
description: Leer hoe u SSL voor JBoss Application Server configureert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 8eb4f691-a66b-498e-8114-307221f63718
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# SSL configureren voor JBoss Application Server {#configuring-ssl-for-jboss-application-server}

Om SSL op de Server van de Toepassing te vormen JBoss, hebt u SSL referentie voor authentificatie nodig. U kunt het sleutelhulpmiddel van Java gebruiken om een referentie tot stand te brengen of om een referentie van een certificaatgezag (CA) te verzoeken en in te voeren. Vervolgens moet u SSL inschakelen op JBoss.

U kunt keytool uitvoeren met één opdracht die alle informatie bevat die nodig is om het sleutelarchief te maken.

In deze procedure:

* `[appserver root]` is de thuismap van de toepassingsserver waarop AEM formulieren worden uitgevoerd.
* `[type]` Dit is een mapnaam die varieert, afhankelijk van het type installatie dat u hebt uitgevoerd.

## SSL-referenties maken {#create-an-ssl-credential}

1. Navigeer naar een opdrachtprompt *[JAVA HOME]*/bin en typ het volgende bevel om de referentie en keystore tot stand te brengen:

   `keytool -genkey -dname "CN=`*Hostnaam* `, OU=`*Groepsnaam* `, O=`*Bedrijfsnaam* `,L=`*Plaats* `, S=`*Staat* `, C=`Landcode&quot; `-alias "AEMForms Cert"` `-keyalg RSA -keypass`*key_password* `-keystore`*sleutelbestandsnaam* `.keystore`

   >[!NOTE]
   >
   >Vervangen `[JAVA_HOME]` met de directory waarin de JDK is geïnstalleerd, en vervangt u de cursieve tekst door waarden die overeenkomen met uw omgeving. Hostnaam is de volledig gekwalificeerde domeinnaam van de toepassingsserver.

1. Voer de `keystore_password` als er om een wachtwoord wordt gevraagd. Het wachtwoord voor het sleutelarchief en de sleutel moeten identiek zijn.

   >[!NOTE]
   >
   >De `keystore_password` *Bij deze stap kan het wachtwoord (key_password) hetzelfde zijn als bij stap 1, of het kan anders zijn.*

1. De *sleutelbestandsnaam*.keystore aan `[appserver root]/server/[type]/conf` door een van de volgende opdrachten te typen:

   * (Windows Eén server) `copy` `keystorename.keystore[appserver root]\standalone\configuration`
   * (Windows Server Cluster) kopiëren `keystorename.keystore[appserver root]\domain\configuration`
   * (Linux Single Server) `cp keystorename.keystore [appserver root]/standalone/configuration`
   * (Linux-servercluster) `cp <em>keystorename</em>.keystore<em>[appserver root]</em>/domain/configuration`


1. Exporteer het certificaatbestand met de volgende opdracht:

   * (Eén server) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/standalone/configuration/keystorename.keystore`
   * (Servercluster) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/domain/configuration/keystorename.keystore`

1. Voer de *keystore_password* als er om een wachtwoord wordt gevraagd.
1. Kopieer het bestand AEMForms_cert.cer naar het *[appserver-hoofdmap] \conf* directory door het volgende bevel te typen:

   * (Windows Eén server) `copy AEMForms_cert.cer [appserver root]\standalone\configuration`
   * (Windows Server Cluster) `copy AEMForms_cert.cer [appserver root]\domain\configuration`
   * (Linux Single Server) `cp AEMForms _cert.cer [appserver root]\standalone\configuration`
   * (Linux-servercluster) `cp AEMForms _cert.cer [appserver root]\domain\configuration`

1. Geef de inhoud van het certificaat weer door de volgende opdracht te typen:

   * `keytool -printcert -v -file [appserver root]\standalone\configuration\AEMForms_cert.cer`
   * `keytool -printcert -v -file [appserver root]\domain\configuration\AEMForms_cert.cer`

1. Schrijftoegang verlenen tot het cacerts-bestand in `[JAVA_HOME]\jre\lib\security`verricht, indien nodig, de volgende taak:

   * (Windows) Klik met de rechtermuisknop op het controlebestand en selecteer Eigenschappen. Schakel vervolgens het kenmerk Alleen-lezen uit.
   * (Linux) Type `chmod 777 cacerts`

1. Importeer het certificaat door de volgende opdracht te typen:

   `keytool -import -alias "AEMForms Cert" -file`*AEMForms_cert* `.cer -keystore`*JAVA_HOME* `\jre\lib\security\cacerts`

1. Type `changeit` als het wachtwoord. Dit wachtwoord is het standaardwachtwoord voor een Java-installatie en kan door de systeembeheerder zijn gewijzigd.
1. Wanneer wordt gevraagd om `Trust this certificate? [no]`, type `yes`. De bevestiging &quot;Certificaat is toegevoegd aan sleutelarchief&quot; wordt weergegeven.
1. Als u verbinding maakt via SSL vanuit Workbench, installeert u het certificaat op de Workbench-computer.
1. Open in een teksteditor de volgende bestanden om te bewerken:

   * Eén server - `[appserver root]`/standalone/configuration/lc_&lt;dbname turnkey=&quot;&quot;>.xml

   * Servercluster - `[appserver root]`/domain/configuration/host.xml

   * Servercluster - `[appserver root]`/domain/configuration/domain_&lt;dbname>.xml

1. 
   * **Voor één server:** in lc_&lt;dbaname tunkey=&quot;&quot;>.xml-bestand, voeg het volgende toe na &lt;security-realms> sectie:

   ```xml
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMformsCert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Zoek de `<server>` sectie aanwezig na de volgende code:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Voeg het volgende toe aan de &lt;server> sectie aanwezig na bovenstaande code:

   ```xml
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

   * **Voor servercluster:** in de [appserver-hoofdmap]\domain\configuration\host.xml op alle knooppunten, voegt u het volgende toe na &lt;security-realms> sectie:

   ```xml
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMForms Cert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Op het primaire knooppunt van de servercluster, in de [appserver-hoofdmap]\domain\configuration\domain_&lt;dbname>.xml, zoek de &lt;server> sectie aanwezig na de volgende code:

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Voeg het volgende toe aan de &lt;server> sectie aanwezig na bovenstaande code:

   ```xml
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

1. Wijzig de waarde voor de `keystoreFile` en de `keystorePass` kenmerk aan het sleutelarchiefwachtwoord dat u hebt opgegeven bij het maken van het sleutelarchief.
1. Start de toepassingsserver opnieuw:

   * Voor sleutelinstallaties:

      * Van het Controlebord van Vensters, klik Administratieve Hulpmiddelen, en klik dan de Diensten.
      * Selecteer JBoss voor Adobe Experience Manager-formulieren.
      * Selecteer Actie > Stoppen.
      * Wacht tot de status van de service wordt weergegeven als gestopt.
      * Selecteer Actie > Begin.

   * Voor Adobe preconfigured of manueel gevormde installaties JBoss:

      * Van een bevelherinnering, navigeer aan *`[appserver root]`*/bin.
      * Stop de server door het volgende bevel in te gaan:

         * (Windows) `shutdown.bat -S`
         * (Linux) `./shutdown.sh -S`

      * Wacht tot het proces JBoss volledig is gesloten (wanneer het proces JBoss controle aan de terminal terugkeert het binnen was begonnen).
      * Start de server door de volgende opdracht in te voeren:

         * (Windows) `run.bat -c <profile>`
         * (Linux) `./run.sh -c <profile>`

1. Om tot beleidsconsole toegang te hebben gebruikend SSL, type `https://[host name]:'port'/adminui` in een webbrowser:

   De standaard-SSL-poort voor JBoss is 8443. Geef vanaf hier deze poort op wanneer u AEM formulieren opent.

## Vraag om een referentie van een CA {#request-a-credential-from-a-ca}

1. Navigeer naar een opdrachtprompt *[JAVA HOME]*/bin en typ het volgende bevel om keystore en de sleutel tot stand te brengen:

   `keytool -genkey -dname "CN=`*Hostnaam* `, OU=`*Groepsnaam* `, O=`*Bedrijfsnaam* `, L=`*Plaats* `, S=`*Staat* `, C=`*Landcode*&quot; `-alias "AEMForms Cert"` `-keyalg RSA -keypass`-*key_password* `-keystore`*sleutelbestandsnaam* `.keystore`

   >[!NOTE]
   >
   >Vervangen *`[JAVA_HOME]`* met de directory waarin de JDK is geïnstalleerd, en vervangt u de cursieve tekst door waarden die overeenkomen met uw omgeving.

1. Typ de volgende opdracht om een certificaataanvraag te genereren voor verzending naar de certificeringsinstantie:

   `keytool -certreq -alias` &quot;AEMForms Cert&quot; `-keystore`*sleutelbestandsnaam* `.keystore -file`*AEMFormscertRequest.csr*

1. Wanneer uw verzoek om een certificaatdossier wordt voldaan, voltooi de volgende procedure.

## Een referentie van een CA gebruiken om SSL in te schakelen {#use-a-credential-obtained-from-a-ca-to-enable-ssl}

1. Navigeer naar een opdrachtprompt *`[JAVA HOME]`*/bin en typ het volgende bevel om het wortelcertificaat van CA in te voeren waarmee CSR is ondertekend:

   `keytool -import -trustcacerts -file` rootcert.pem-sleutelarchief` keystorename.keystore -alias root`

   Als het basiscertificaat zich niet in de browser bevindt, importeert u het ook daar.

   >[!NOTE]
   >
   >Vervangen *`[JAVA_HOME]`met de directory waarin de JDK is geïnstalleerd, en vervangt u de cursieve tekst door waarden die overeenkomen met uw omgeving.*

1. Navigeer naar een opdrachtprompt *`[JAVA HOME]`*/bin en typ het volgende bevel om de referentie in keystore in te voeren:

   `keytool -import -trustcacerts -file`*CACCertificateName* `.crt -keystore`*sleutelbestandsnaam* `.keystore`

   >[!NOTE]
   >
   >* Vervangen `[JAVA_HOME]` met de directory waarin de JDK is geïnstalleerd, en vervangt u de cursieve tekst door waarden die overeenkomen met uw omgeving.
   >* Het geïmporteerde CA-ondertekende certificaat vervangt een zelfondertekend openbaar certificaat als dit bestaat.

1. Voer de stappen 13 tot en met 18 van Een SSL-referentie maken uit.
