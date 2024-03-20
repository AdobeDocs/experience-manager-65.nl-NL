---
title: SSL configureren voor WebSphere-toepassingsserver
description: Leer hoe u SSL voor WebSphere Application Server configureert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b0786b52-879e-4a24-9cc9-bd9dcb2473cc
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 0%

---

# SSL configureren voor WebSphere-toepassingsserver {#configuring-ssl-for-websphere-application-server}

Deze sectie bevat de volgende stappen om SSL te configureren met uw IBM WebSphere Application Server.

## Een lokale gebruikersaccount maken op WebSphere {#creating-a-local-user-account-on-websphere}

Voor het toelaten van SSL, moet WebSphere toegang tot een gebruikersrekening in het lokale OS gebruikersregister hebben dat toestemming heeft om het systeem te beheren:

* (Vensters) creeer een gebruiker van Vensters die deel van de groep van Beheerders uitmaakt en het voorrecht heeft om als deel van het werkende systeem te handelen. (Zie [Een Windows-gebruiker voor WebSphere maken](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere).)
* (Linux, UNIX) De gebruiker kan een wortelgebruiker of een andere gebruiker zijn die wortelvoorrechten heeft. Wanneer u SSL op WebSphere inschakelt, gebruikt u de serveridentificatie en het wachtwoord van deze gebruiker.

### Een Linux- of UNIX-gebruiker voor WebSphere maken {#create-a-linux-or-unix-user-for-websphere}

1. Meld u aan als de rootgebruiker.
1. Maak een gebruiker door de volgende opdracht in te voeren in de opdrachtprompt:

   * (Linux en Sun Solaris) `useradd`
   * (IBM AIX) `mkuser`

1. Stel het wachtwoord van de nieuwe gebruiker in door de opdrachtprompt in te voeren `passwd` .
1. (Linux en Solaris) Maak een wachtwoordbestand voor schaduwen door (zonder parameters) in de opdrachtprompt in te voeren `pwconv` .

   >[!NOTE]
   >
   >(Linux en Solaris) Het lokale beveiligingsregister van WebSphere Application Server (lokaal besturingssysteem) werkt alleen als er een schaduwwachtwoordbestand aanwezig is. Het wachtwoordbestand voor schaduwen krijgt meestal de naam **/etc/shadow** en is gebaseerd op het bestand /etc/passwd. Als het wachtwoordbestand voor schaduwen niet bestaat, treedt er een fout op nadat de algemene beveiliging is ingeschakeld en het gebruikersregister is geconfigureerd als Lokaal besturingssysteem.

1. Open het groepsbestand vanuit de map /etc in een teksteditor.
1. Voeg de gebruiker die u in stap 2 hebt gemaakt toe aan de `root` groep.
1. Sla het bestand op en sluit het.
1. (UNIX met toegelaten SSL) Start en stop WebSphere als wortelgebruiker.

### Een Windows-gebruiker voor WebSphere maken {#create-a-windows-user-for-websphere}

1. Meld u aan bij Windows met een beheerdersgebruikersaccount.
1. Selecteren **Start > Configuratiescherm > Systeembeheer > Computerbeheer > Lokale gebruikers en groepen**.
1. Klik met de rechtermuisknop op Gebruikers en selecteer **Nieuwe gebruiker**.
1. Typ een gebruikersnaam en wachtwoord in de desbetreffende vakken en typ alle overige gegevens die u nodig hebt in de overige vakken.
1. Deselecteren **Gebruiker moet wachtwoord wijzigen bij volgende aanmelding**, klikt u op **Maken** en klik vervolgens op **Sluiten**.
1. Klikken **Gebruikers**, klikt u met de rechtermuisknop op de gebruiker die u hebt gemaakt en selecteert u **Eigenschappen**.
1. Klik op de knop **Lid van** en klik vervolgens op **Toevoegen**.
1. Typ in het vak Geef de objectnamen op die u wilt selecteren `Administrators`, klikt u op Namen controleren om te controleren of de groepsnaam correct is.
1. Klikken **OK** en klik vervolgens op **OK** opnieuw.
1. Selecteren **Start > Configuratiescherm > Systeembeheer > Lokaal beveiligingsbeleid > Lokaal beleid**.
1. Klik op Toewijzing gebruikersrechten en klik vervolgens met de rechtermuisknop op Handelen als onderdeel van het besturingssysteem en selecteer Eigenschappen.
1. Klikken **Gebruiker of groep toevoegen**.
1. Typ in het vak Voer de objectnamen in die u wilt selecteren de naam van de gebruiker die u in stap 4 hebt gemaakt, en klik op **Namen controleren** om ervoor te zorgen dat de naam correct is, en klik dan **OK**.
1. Klikken **OK** om de handeling te sluiten als onderdeel van het dialoogvenster Eigenschappen van besturingssysteem.

### WebSphere configureren om de nieuwe gebruiker als beheerder te gebruiken {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Zorg ervoor dat WebSphere wordt uitgevoerd.
1. Selecteer in de beheerconsole van WebSphere de optie **Beveiliging > Algemene beveiliging**.
1. Selecteer onder Administratieve beveiliging **Administratieve gebruikersrollen**.
1. Klik op Toevoegen en voer de volgende handelingen uit:

   1. Type **&amp;asteren;** in het zoekvak en klik op Zoeken.
   1. Klikken **Beheerder** onder rollen.
   1. Voeg de pas gecreëerde gebruiker aan Toegewezen aan rol toe en wijs het aan Beheerder toe.

1. Klikken **OK** en sla uw wijzigingen op.
1. Start het WebSphere-profiel opnieuw.

## Beheersbeveiliging inschakelen {#enable-administrative-security}

1. Selecteer in de beheerconsole van WebSphere de optie **Beveiliging > Algemene beveiliging**.
1. Klikken **Wizard Beveiligingsconfiguratie**.
1. Zorgen **Toepassingsbeveiliging inschakelen** selectievakje is ingeschakeld. Klik op **Next**.
1. Selecteren **Federale opslagplaatsen** en klik op **Volgende**.
1. Geef de referenties op die u wilt instellen en klik op **Volgende**.
1. Klikken **Voltooien**.
1. Start het WebSphere-profiel opnieuw.

   WebSphere begint met het standaardsleutelarchief en het standaardvertrouwensarchief.

## SSL inschakelen (aangepaste sleutel en vertrouwde opslag) {#enable-ssl-custom-key-and-truststore}

U kunt sleutelarchieven en sleutelarchieven maken met het hulpprogramma ikeyman of de beheerconsole. Om het werk van de wijzerplaat behoorlijk te maken, zorg ervoor dat de WebSphere installatiepad geen haakjes bevat.

1. Selecteer in de beheerconsole van WebSphere de optie **Beveiliging > SSL-certificaat en sleutelbeheer**.
1. Klikken **sleutelarchieven en certificaten** onder Verwante objecten.
1. In de **Belangrijke winkeltoepassingen** vervolgkeuzelijst, zorg ervoor dat **SSL-sleutelarchieven** is geselecteerd. Klikken **Nieuw**.
1. Typ een logische naam en beschrijving.
1. Geef het pad op waar u het sleutelarchief wilt maken. Als u al een keystore hebt gemaakt via ikeyman, geeft u het pad naar het keystore-bestand op.
1. Geef het wachtwoord op en bevestig het.
1. Kies het sleutelarchieftype en klik **Toepassen**.
1. Sla de hoofdconfiguratie op.
1. Klikken **Persoonlijk certificaat**.
1. Als u al een sleutelarchief hebt gemaakt met ikeyman, wordt het certificaat weergegeven. Anders moet u een nieuw zelfondertekend certificaat toevoegen door de volgende stappen uit te voeren:

   1. Selecteer **Maken > zelfondertekend certificaat**.
   1. Geef de gewenste waarden op het certificaatformulier op. Zorg ervoor dat u de alias en de algemene naam als volledig gekwalificeerde domeinnaam van de computer behoudt.
   1. Klik op **Toepassen**.

1. Herhaal stap 2 tot en met 10 voor het maken van een truststore.

## Aangepaste keystore en truststore toepassen op de server {#apply-custom-keystore-and-truststore-to-the-server}

1. Selecteer in de WebSphere Administrative Console de optie **Beveiliging > SSL-certificaat en sleutelbeheer**.
1. Klik op **Beveiligingsconfiguratie voor eindpunten beheren**. De lokale topologiekaart wordt geopend.
1. Selecteer onder Binnenkomend de optie Direct onderliggende element van knooppunten.
1. Selecteer **SSL-configuraties** onder Verwante items.
1. Selecteer **NodeDeafultSSLSetting**.
1. Selecteer in de vervolgkeuzelijsten Naam van vertrouwde opslag en Naam van sleutelarchief de aangepaste truststore en sleutelarchief die u hebt gemaakt.
1. Klikken **Toepassen**.
1. Sla de hoofdconfiguratie op.
1. Start het WebSphere-profiel opnieuw.

   Uw profiel wordt nu uitgevoerd op aangepaste SSL-instellingen en uw certificaat.

## Ondersteuning mogelijk maken voor AEM {#enabling-support-for-aem-forms-natives}

1. Selecteer in de beheerconsole van WebSphere de optie **Beveiliging > Algemene beveiliging**.
1. Vouw in de sectie Verificatie de optie **RMI/IOOP-beveiliging** en klik op **CSIv2 binnenkomende mededelingen**.
1. Zorg ervoor dat **Door SSL ondersteund** wordt geselecteerd in de drop-down lijst van het Vervoer.
1. Start het WebSphere-profiel opnieuw.

## WebSphere configureren voor het converteren van URL&#39;s die beginnen met https {#configuring-websphere-to-convert-urls-that-begins-with-https}

Als u een URL wilt converteren die begint met https, voegt u een handtekeningcertificaat voor die URL toe aan de WebSphere-server.

**Een handtekeningcertificaat maken voor een https-site**

1. Zorg ervoor dat WebSphere wordt uitgevoerd.
1. Navigeer in de beheerconsole van WebSphere naar ondertekenaarcertificaten en klik vervolgens op Beveiliging > SSL-certificaat en sleutelbeheer > Belangrijke opslagruimten en certificaten > NodeDefaultTrustStore > Ondertekenaarcertificaten.
1. Klik op Ophalen van poort en voer de volgende taken uit:

   * Typ de URL in het vak Host. Typ bijvoorbeeld `www.paypal.com`.
   * Typ in het vak Poort `443`. Deze poort is de standaard-SSL-poort.
   * Typ een alias in het vak Alias.

1. Klik op Informatie van ondertekenaar ophalen en controleer vervolgens of de informatie is opgehaald.
1. Klik op Toepassen en vervolgens op Opslaan.

De conversie van HTML naar PDF vanaf de site waarvan het certificaat is toegevoegd, werkt nu vanaf de service PDF genereren.

>[!NOTE]
>
>Een ondertekenaarscertificaat is vereist om een toepassing vanuit WebSphere verbinding te laten maken met SSL-sites. Deze wordt gebruikt door JSSE (Java Secure Socket Extensions) voor het valideren van certificaten die door de externe zijde van de verbinding worden verzonden tijdens een SSL-handshake.

## Dynamische poorten configureren {#configuring-dynamic-ports}

IBM WebSphere staat geen veelvoudige vraag aan ORB.init () toe wanneer de Globale Veiligheid wordt toegelaten. U kunt de permanente beperking lezen op https://www-01.ibm.com/support/docview.wss?uid=swg1PK58704.

Voer de volgende stappen uit om de poort dynamisch te maken en het probleem op te lossen:

1. Selecteer in de beheerconsole van WebSphere de optie **Servers** > **Servertypen** > **WebSphere-toepassingsserver**.
1. Selecteer de server in de sectie Voorkeuren.
1. In de **Configuratie** tab, onder **Communicatie** sectie, uitvouwen **Poorten** en klik op **Details**.
1. Klik op de volgende poortnamen en wijzig de **poortnummer** tot 0, en klik **OK**.

   * `ORB_LISTENER_ADDRESS`
   * `SAS_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_MUTUALAUTH_LISTENER_ADDRESS`

## Het bestand sling.properties configureren {#configure-the-sling-properties-file}

1. Openen `[aem-forms_root]`\crx-repository\launchpad\sling.properties.
1. Zoek de `sling.bootdelegation.ibm` eigenschap en toevoegen `com.ibm.websphere.ssl.*`naar het waardeveld. Het bijgewerkte veld ziet er als volgt uit:

   ```shell
   sling.bootdelegation.ibm=com.ibm.xml.*, com.ibm.websphere.ssl.*
   ```

1. Sla het bestand op en start de server opnieuw.
