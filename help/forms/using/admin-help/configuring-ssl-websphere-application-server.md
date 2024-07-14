---
title: SSL configureren voor WebSphere-toepassingsserver
description: Leer hoe u SSL voor WebSphere Application Server configureert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b0786b52-879e-4a24-9cc9-bd9dcb2473cc
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 0%

---

# SSL configureren voor WebSphere-toepassingsserver {#configuring-ssl-for-websphere-application-server}

Deze sectie bevat de volgende stappen om SSL te configureren met uw IBM WebSphere Application Server.

## Een lokale gebruikersaccount maken op WebSphere {#creating-a-local-user-account-on-websphere}

Voor het toelaten van SSL, moet WebSphere toegang tot een gebruikersrekening in het lokale OS gebruikersregister hebben dat toestemming heeft om het systeem te beheren:

* (Vensters) creeer een gebruiker van Vensters die deel van de groep van Beheerders uitmaakt en het voorrecht heeft om als deel van het werkende systeem te handelen. (Zie [ een gebruiker van Vensters voor WebSphere ](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere) tot stand brengen.)
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
1. Selecteer **Begin > Controlebord > Administratieve Hulpmiddelen > Beheer van de Computer > Lokale Gebruikers en Groepen**.
1. Klik Gebruikers met de rechtermuisknop aan en selecteer **Nieuwe Gebruiker**.
1. Typ een gebruikersnaam en wachtwoord in de desbetreffende vakken en typ alle overige gegevens die u nodig hebt in de overige vakken.
1. Deselecteer **Gebruiker moet Wachtwoord bij Volgende Login** veranderen, **klikken creeert**, en klikt dan **dicht**.
1. Klik **Gebruikers**, klik de gebruiker met de rechtermuisknop aan u creeerde en selecteer **Eigenschappen**.
1. Klik het **Lid van** lusje en klik dan **toevoegen**.
1. Typ `Administrators` in het vak Geef de objectnamen op die u wilt selecteren en klik op Namen controleren om na te gaan of de groepsnaam correct is.
1. Klik **O.K.** en klik dan O.K. **** opnieuw.
1. Selecteer **Begin > Controlebord > Administratieve Hulpmiddelen > Lokaal Beleid van de Veiligheid > Lokale Beleid**.
1. Klik op Toewijzing gebruikersrechten en klik vervolgens met de rechtermuisknop op Handelen als onderdeel van het besturingssysteem en selecteer Eigenschappen.
1. Klik **toevoegen Gebruiker of Groep**.
1. In ga de Namen van Objecten in om doos te selecteren, typ de naam van de gebruiker u in stap 4 creeerde, klik **Namen van de Controle** om ervoor te zorgen dat de naam correct is, en klik dan O.K. ****.
1. Klik **O.K.** om de Akte als deel van de de dialoogdoos van de Eigenschappen van het Werkende Systeem te sluiten.

### WebSphere configureren om de nieuwe gebruiker als beheerder te gebruiken {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Zorg ervoor dat WebSphere wordt uitgevoerd.
1. In Administratieve Console WebSphere, uitgezochte **Veiligheid > Globale Veiligheid**.
1. Onder Administratieve veiligheid, uitgezochte **Administratieve gebruikersrollen**.
1. Klik op Toevoegen en voer de volgende handelingen uit:

   1. Typ **&amp;ast;** in het zoekvak en klik op Zoeken.
   1. Klik **Beheerder** onder rollen.
   1. Voeg de pas gecreëerde gebruiker aan Toegewezen aan rol toe en wijs het aan Beheerder toe.

1. Klik **O.K.** en sparen uw veranderingen.
1. Start het WebSphere-profiel opnieuw.

## Beheersbeveiliging inschakelen {#enable-administrative-security}

1. In Administratieve Console WebSphere, uitgezochte **Veiligheid > Globale Veiligheid**.
1. Klik {de Tovenaar van de Configuratie van 0} Veiligheid **.**
1. Verzeker **checkbox van de Veiligheid van de Toepassing** wordt toegelaten. Klik op **Next**.
1. Selecteer **Federated Repositories** en klik **daarna**.
1. Specificeer de geloofsbrieven u **daarna** wilt plaatsen en klikken.
1. Klik **Afwerking**.
1. Start het WebSphere-profiel opnieuw.

   WebSphere begint met het standaardsleutelarchief en het standaardvertrouwensarchief.

## SSL inschakelen (aangepaste sleutel en vertrouwde opslag) {#enable-ssl-custom-key-and-truststore}

U kunt sleutelarchieven en sleutelarchieven maken met het hulpprogramma ikeyman of de beheerconsole. Om het werk van de wijzerplaat behoorlijk te maken, zorg ervoor dat de WebSphere installatiepad geen haakjes bevat.

1. In Administratieve Console WebSphere, uitgezochte **Veiligheid > SSL certificaat en zeer belangrijk beheer**.
1. Klik **Sleutelarchieven en certificaten** onder Verwante punten.
1. In het **Zeer belangrijke opslaggebruik** dropdown, zorg ervoor dat **SSL Keystores** wordt geselecteerd. Klik **Nieuw**.
1. Typ een logische naam en beschrijving.
1. Geef het pad op waar u het sleutelarchief wilt maken. Als u al een keystore hebt gemaakt via ikeyman, geeft u het pad naar het keystore-bestand op.
1. Geef het wachtwoord op en bevestig het.
1. Kies het keystore type en klik **toepassen**.
1. Sla de hoofdconfiguratie op.
1. Klik **Persoonlijk Certificaat**.
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
1. Klik **toepassen**.
1. Sla de hoofdconfiguratie op.
1. Start het WebSphere-profiel opnieuw.

   Uw profiel wordt nu uitgevoerd op aangepaste SSL-instellingen en uw certificaat.

## Ondersteuning mogelijk maken voor AEM {#enabling-support-for-aem-forms-natives}

1. In Administratieve Console WebSphere, uitgezochte **Veiligheid > Globale Veiligheid**.
1. In de sectie van de Authentificatie, breid **veiligheid RMI/IOOP** uit en klik **CSIv2 binnenkomende mededelingen**.
1. Zorg ervoor dat **SSL-gesteunde** in de drop-down lijst van het Vervoer wordt geselecteerd.
1. Start het WebSphere-profiel opnieuw.

## WebSphere configureren voor het converteren van URL&#39;s die beginnen met https {#configuring-websphere-to-convert-urls-that-begins-with-https}

Als u een URL wilt converteren die begint met https, voegt u een handtekeningcertificaat voor die URL toe aan de WebSphere-server.

**creeer een certificaat van de Ondertekenaar voor een https toegelaten plaats**

1. Zorg ervoor dat WebSphere wordt uitgevoerd.
1. Navigeer in de beheerconsole van WebSphere naar ondertekenaarcertificaten en klik vervolgens op Beveiliging > SSL-certificaat en sleutelbeheer > Belangrijke opslagruimten en certificaten > NodeDefaultTrustStore > Ondertekenaarcertificaten.
1. Klik op Ophalen van poort en voer de volgende taken uit:

   * Typ de URL in het vak Host. Typ bijvoorbeeld `www.paypal.com` .
   * Typ `443` in het vak Poort. Deze poort is de standaard-SSL-poort.
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

1. In Administratieve Console WebSphere, uitgezochte **Servers** > **de Types van Server** > **WebSphere toepassingsserver**.
1. Selecteer de server in de sectie Voorkeuren.
1. In het **lusje van de Configuratie**, onder **Mededelingen** sectie, breid **Havens** uit, en klik **Details**.
1. Klik de volgende havennamen, verander het **havenaantal** in 0, en klik **O.K.**.

   * `ORB_LISTENER_ADDRESS`
   * `SAS_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_MUTUALAUTH_LISTENER_ADDRESS`

## Het bestand sling.properties configureren {#configure-the-sling-properties-file}

1. Open `[aem-forms_root]` \crx-repository\launchpad\sling.properties- dossier voor het uitgeven.
1. Zoek de eigenschap `sling.bootdelegation.ibm` en voeg `com.ibm.websphere.ssl.*` toe aan het waardeveld. Het bijgewerkte veld ziet er als volgt uit:

   ```shell
   sling.bootdelegation.ibm=com.ibm.xml.*, com.ibm.websphere.ssl.*
   ```

1. Sla het bestand op en start de server opnieuw.
