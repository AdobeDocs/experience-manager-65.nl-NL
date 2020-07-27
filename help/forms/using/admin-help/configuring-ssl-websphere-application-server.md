---
title: SSL configureren voor WebSphere-toepassingsserver
seo-title: SSL configureren voor WebSphere-toepassingsserver
description: Leer hoe te om SSL voor de Server van de Toepassing te vormen WebSphere.
seo-description: Leer hoe te om SSL voor de Server van de Toepassing te vormen WebSphere.
uuid: f939a806-346e-41e0-b2c0-6d0ba83f8f6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7c0efcb3-5b07-4090-9119-b7318c8b7980
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 0%

---


# SSL configureren voor WebSphere-toepassingsserver {#configuring-ssl-for-websphere-application-server}

Deze sectie omvat de volgende stappen om SSL met uw Server van de Toepassing van IBM WebSphere te vormen.

## Een lokale gebruikersaccount maken op WebSphere {#creating-a-local-user-account-on-websphere}

Voor het toelaten van SSL, moet WebSphere toegang tot een gebruikersrekening in het lokale OS gebruikersregister hebben dat toestemming heeft om het systeem te beheren:

* (Vensters) creeer een nieuwe gebruiker van Vensters die deel van de groep van Beheerders uitmaakt en het voorrecht heeft om als deel van het werkende systeem te handelen. (Zie [Een Windows-gebruiker voor WebSphere](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere)maken.)
* (Linux, UNIX) De gebruiker kan een wortelgebruiker of een andere gebruiker zijn die wortelvoorrechten heeft. Wanneer u SSL op WebSphere inschakelt, gebruikt u de serveridentificatie en het wachtwoord van deze gebruiker.

### Een Linux- of UNIX-gebruiker voor WebSphere maken {#create-a-linux-or-unix-user-for-websphere}

1. Meld u aan als hoofdgebruiker.
1. Creeer een gebruiker door het volgende bevel in een bevelherinnering in te gaan:

   * (Linux en Sun Solaris) `useradd`
   * (IBM AIX) `mkuser`

1. Plaats het wachtwoord van de nieuwe gebruiker door `passwd` in de bevelherinnering in te gaan.
1. (Linux en Solaris) Creeer een dossier van het schaduwwachtwoord door `pwconv` (zonder parameters) in de bevelherinnering in te gaan.

   >[!NOTE]
   >
   >(Linux en Solaris) Om het lokale OS-beveiligingsregister van WebSphere Application Server te laten werken, moet er een bestand met een schaduwwachtwoord bestaan. Het bestand met schaduwwachtwoorden krijgt meestal de naam **/etc/shadow** en is gebaseerd op het bestand /etc/password. Als het bestand met schaduwwachtwoorden niet bestaat, treedt er een fout op nadat de algemene beveiliging is ingeschakeld en het gebruikersregister is geconfigureerd als Lokaal besturingssysteem.

1. Open het groepsbestand uit de map /etc in een teksteditor.
1. Voeg de gebruiker toe die u in stap 2 hebt gemaakt aan de `root` groep.
1. Sla het bestand op en sluit het.
1. (UNIX met toegelaten SSL) Start en stop WebSphere als wortelgebruiker.

### Een Windows-gebruiker voor WebSphere maken {#create-a-windows-user-for-websphere}

1. Meld u aan bij Windows met een beheerdersgebruikersaccount.
1. Selecteer **Start > Configuratiescherm > Systeembeheer > Computerbeheer > Lokale gebruikers en groepen**.
1. Klik met de rechtermuisknop op Gebruikers en selecteer **Nieuwe gebruiker**.
1. Typ een gebruikersnaam en wachtwoord in de desbetreffende vakken en typ alle overige gegevens die u nodig hebt in de overige vakken.
1. Schakel de optie Wachtwoord **gebruiker moet wijzigen bij volgende aanmelding** uit, klik op **Maken** en klik vervolgens op **Sluiten**.
1. Klik **Gebruikers**, klik de gebruiker met de rechtermuisknop aan u enkel creeerde en selecteer **Eigenschappen**.
1. Klik op het tabblad **Lid van** en klik vervolgens op **Toevoegen**.
1. Typ in het vak Geef de objectnamen op die u wilt selecteren `Administrators`en klik op Namen controleren om te controleren of de naam van de groep correct is.
1. Klik op **OK** en klik nogmaals op **OK** .
1. Selecteer **Start > Configuratiescherm > Systeembeheer > Lokaal beveiligingsbeleid > Lokaal beleid**.
1. Klik op Toewijzing gebruikersrechten en klik vervolgens met de rechtermuisknop op Handelen als onderdeel van het besturingssysteem en selecteer Eigenschappen.
1. Klik op Gebruiker of Groep **** toevoegen.
1. Typ in het vak Voer de objectnamen in die u wilt selecteren de naam van de gebruiker die u in stap 4 hebt gemaakt, klik op Namen **** controleren om te controleren of de naam correct is en klik vervolgens op **OK**.
1. Klik op **OK** om het dialoogvenster Handeling als onderdeel van het dialoogvenster Eigenschappen besturingssysteem te sluiten.

### WebSphere configureren om de nieuwe gebruiker als beheerder te gebruiken {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Zorg ervoor dat WebSphere wordt uitgevoerd.
1. Selecteer **Beveiliging > Algemene beveiliging** in de beheerconsole van WebSphere.
1. Onder Administratieve veiligheid, uitgezochte **Administratieve gebruikersrollen**.
1. Klik op Toevoegen en voer de volgende handelingen uit:

   1. Type **&amp;ast;** in het zoekvak en klik op Zoeken.
   1. Klik op **Beheerder** onder rollen.
   1. Voeg de pas gecreëerde gebruiker aan Toegewezen aan rol toe en wijs het aan Beheerder toe.

1. Klik op **OK** en sla uw wijzigingen op.
1. Start het WebSphere-profiel opnieuw.

## Beheersbeveiliging inschakelen {#enable-administrative-security}

1. Selecteer **Beveiliging > Algemene beveiliging** in de beheerconsole van WebSphere.
1. Klik op **Wizard** Beveiligingsconfiguratie.
1. Controleer of het selectievakje Toepassingsbeveiliging **** inschakelen is ingeschakeld. Klik op **Next**.
1. Selecteer **Federatieve opslagplaatsen** en klik op **Volgende**.
1. Geef de referenties op die u wilt instellen en klik op **Volgende**.
1. Click **Finish**.
1. Start het WebSphere-profiel opnieuw.

   WebSphere gebruikt het standaardsleutelarchief en het vertrouwde archief.

## SSL inschakelen (aangepaste sleutel en vertrouwde opslag) {#enable-ssl-custom-key-and-truststore}

U kunt sleutelarchieven en sleutelarchieven maken met het hulpprogramma ikeyman of de beheerconsole. Om het werk van de wijzerplaat behoorlijk te maken, zorg ervoor dat de WebSphere installatiepad geen haakjes bevat.

1. Selecteer **Beveiliging > SSL-certificaat en sleutelbeheer** in de beheerconsole van WebSphere.
1. Klik op **sleutelarchieven en certificaten** onder Verwante items.
1. Controleer of in het vervolgkeuzemenu Gebruik van **sleutelarchief** **SSL-sleutelarchieven** is geselecteerd. Klik op **Nieuw**.
1. Typ een logische naam en beschrijving.
1. Geef het pad op naar het sleutelarchief. Als u al een sleutelarchief hebt gemaakt via ikeyman, geeft u het pad naar het sleutelarchiefbestand op.
1. Geef het wachtwoord op en bevestig het.
1. Kies het keystore-type en klik op **Toepassen**.
1. Sla de master configuratie op.
1. Klik op **Persoonlijk certificaat**.
1. Als u al een sleutelarchief hebt gemaakt met ikeyman, wordt het certificaat weergegeven. Anders moet u een nieuw zelfondertekend certificaat toevoegen door de volgende stappen uit te voeren:

   1. Selecteer **Maken > Zelfondertekend certificaat**.
   1. Geef de gewenste waarden op in het certificaatformulier. Zorg ervoor dat u Alias en gemeenschappelijke naam als volledig-gekwalificeerde domeinnaam van de machine houdt.
   1. Klik op **Toepassen**.

1. Herhaal stap 2 tot en met 10 voor het maken van een vertrouwde opslag.

## Aangepast sleutelarchief en vertrouwde opslag toepassen op de server {#apply-custom-keystore-and-truststore-to-the-server}

1. Selecteer **Beveiliging > SSL-certificaat en sleutelbeheer** in de beheerconsole van WebSphere.
1. Klik **leiden de configuratie** van de eindpuntveiligheid. De lokale topologiekaart opent.
1. Onder Binnenkomend, uitgezochte directe kind van knopen.
1. Selecteer **SSL-configuraties** onder Verwante items.
1. Selecteer **NodeDeafultSSLSetting**.
1. Selecteer in de vervolgkeuzelijsten Naam van vertrouwde opslag en Naam van sleutelarchief de aangepaste truststore en sleutelarchief die u hebt gemaakt.
1. Klik op **Toepassen**.
1. Sla de master configuratie op.
1. Start het WebSphere-profiel opnieuw.

   Uw profiel wordt nu uitgevoerd op aangepaste SSL-instellingen en uw certificaat.

## Ondersteuning mogelijk maken voor AEM-formuliernative {#enabling-support-for-aem-forms-natives}

1. Selecteer **Beveiliging > Algemene beveiliging** in de beheerconsole van WebSphere.
1. Vouw in de sectie Verificatie de **RMI/IOOP-beveiliging** uit en klik op **CSIv2 binnenkomende communicatie**.
1. Zorg ervoor dat **door SSL ondersteund** is geselecteerd in de vervolgkeuzelijst Vervoer.
1. Start het WebSphere-profiel opnieuw.

## WebSphere configureren voor het converteren van URL&#39;s die beginnen met https {#configuring-websphere-to-convert-urls-that-begins-with-https}

Als u een URL wilt converteren die begint met https, voegt u een handtekeningcertificaat voor die URL toe aan de WebSphere-server.

**Een handtekeningcertificaat maken voor een https-site**

1. Zorg ervoor dat WebSphere wordt uitgevoerd.
1. Navigeer in de beheerconsole van WebSphere naar ondertekenaarcertificaten en klik vervolgens op Beveiliging > SSL-certificaat en sleutelbeheer > Belangrijke opslagruimten en certificaten > NodeDefaultTrustStore > Ondertekenaarcertificaten.
1. Klik op Ophalen van poort en voer de volgende taken uit:

   * Typ de URL in het vak Host. For example, type `www.paypal.com`.
   * Typ in het vak Poort `443`. Deze poort is de standaard-SSL-poort.
   * Typ een alias in het vak Alias.

1. Klik op Informatie van ondertekenaar ophalen en controleer vervolgens of de informatie is opgehaald.
1. Klik op Toepassen en vervolgens op Opslaan.

De conversie van HTML naar PDF vanaf de site waarvan het certificaat is toegevoegd, werkt nu vanuit de service PDF genereren.

>[!NOTE]
>
>Een ondertekenaarscertificaat is vereist om een toepassing vanuit WebSphere verbinding te laten maken met SSL-sites. Deze wordt gebruikt door JSSE (Java Secure Socket Extensions) voor het valideren van certificaten die door de externe zijde van de verbinding worden verzonden tijdens een SSL-handshake.

## Dynamische poorten configureren {#configuring-dynamic-ports}

IBM WebSphere staat geen veelvoudige vraag aan ORB.init () toe wanneer de Globale Veiligheid wordt toegelaten. U kunt de permanente beperking lezen op https://www-01.ibm.com/support/docview.wss?uid=swg1PK58704.

Voer de volgende stappen uit om de poort dynamisch te maken en het probleem op te lossen:

1. Selecteer in de beheerconsole van WebSphere de optie **Servers** > **Servertypen** > **WebSphere-toepassingsserver**.
1. Selecteer de server in de sectie Voorkeuren.
1. In het lusje van de **Configuratie** , onder **Communicatie** sectie, breid **Havens** uit, en klik **Details**.
1. Klik op de volgende poortnamen, wijzig het **poortnummer** in 0 en klik op **OK**.

   * `ORB_LISTENER_ADDRESS`
   * `SAS_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_MUTUALAUTH_LISTENER_ADDRESS`

## Het bestand sling.properties configureren {#configure-the-sling-properties-file}

1. Open het bestand `[aem-forms_root]`\crx-repository\launchpad\sling.properties.
1. Zoek de `sling.bootdelegation.ibm` eigenschap en voeg deze toe `com.ibm.websphere.ssl.*`aan het waardeveld. Het bijgewerkte veld ziet er als volgt uit:

   ```java
   sling.bootdelegation.ibm=com.ibm.xml.*, com.ibm.websphere.ssl.*
   ```

1. Sla het bestand op en start de server opnieuw.

