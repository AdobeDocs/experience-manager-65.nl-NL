---
title: AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten
seo-title: AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten
description: Leer hoe u native AEM-zoekopdrachten kunt inschakelen om met volledige tekst te zoeken op DRM beveiligde PDF-documenten.
seo-description: Leer hoe u native AEM-zoekopdrachten kunt inschakelen om met volledige tekst te zoeken op DRM beveiligde PDF-documenten.
uuid: dba882f8-bad4-4122-a0df-03cf087afb23
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7eebef08-83b9-4b56-90ec-35ab3b0c27e8
noindex: true
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager biedt een gebruikersinterface voor het zoeken en zoeken van verschillende middelen die zijn opgeslagen in AEM. Met de native zoekopdracht kunt u zoeken naar AEM-elementen en zoeken naar tekst op verschillende veelgebruikte documentindelingen, zoals bestanden met onbewerkte tekst, Microsoft Office-documenten en PDF-documenten. U kunt de native zoekopdracht ook uitbreiden en inschakelen om full-text zoekopdrachten uit te voeren voor met DRM beveiligde PDF- en Microsoft Office-documenten.

Voer de volgende stappen uit om AEM in staat te stellen te zoeken in met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten:

## Voordat u begint {#before-you-start}

* Documentbeveiliging voor AEM Forms installeren en configureren.
* Voeg pakket sun.util.agenda aan whitelist van de Configuratie van de Firewall van de **Deserialization toe.** De configuratie wordt vermeld bij `https://'[server]:[port]'/system/console/configMgr`.
* Zorg ervoor dat alle AEM-bundels actief zijn. De bundels worden vermeld bij `https://'[server]:[port]'/system/console/bundles`. Als alle bundels niet actief zijn, wacht u en controleert u de status van de bundels na een paar minuten.

## Een veilige verbinding tot stand brengen in de AEM Forms workflow (AEM Forms on JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Een veilige verbinding laat naadloze stroom van informatie tussen Vormen AEM op JEE en de diensten OSGi toe die op de zelfde server lopen. Gebruik een van de volgende methoden om een veilige verbinding tot stand te brengen:

* AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* AEM Forms Client SDK-bundel configureren met wederzijdse verificatie

### AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM-configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL:** Geef de HTTP-URL van AEM Forms op de JEE-server op. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **Servicenaam**: Voeg RightsManagementService aan de lijst van de gespecificeerde diensten toe.
   * **Gebruikersnaam:** Geef de gebruikersnaam op van de AEM Forms on JEE-account die moet worden gebruikt om aanroepen vanuit AEM Forms te starten op de JEE-server. De opgegeven account moet gemachtigd zijn om documentservices aan te roepen op de AEM Forms op de JEE-server.
   * **Wachtwoord**: Geef het wachtwoord op van de AEM Forms on JEE-account die in het veld Gebruikersnaam wordt vermeld.
   Click **Save**. AEM is ingeschakeld om te zoeken in met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten.

### AEM Forms Client SDK-bundel configureren met wederzijdse verificatie {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms on JEE. Voor gedetailleerde informatie, zie [CAC en Wederzijdse Authentificatie](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Open AEM-configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL:** Geef de HTTPS-URL van AEM Forms op de JEE-server op. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **2-wegs SSL** inschakelen: Schakel de optie 2-wegs SSL inschakelen in.
   * **URL** sleutelarchiefbestand: Geef de URL van het sleutelarchiefbestand op.
   * **TrustStore-bestands-URL**: Geef de URL van het bestand truststore op.
   * **Wachtwoord** sleutelarchief: Geef het wachtwoord voor het sleutelarchiefbestand op.
   * **TrustStorePassword**: Geef het wachtwoord voor het bestand truststore op.
   * **Servicenaam**: Voeg RightsManagementService aan de lijst van de gespecificeerde diensten toe.
   Click **Save**. AEM is ingeschakeld om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten

## Een PDF- of Microsoft Office-document indexeren dat met een voorbeeldbeleid is beveiligd {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload een met een beleid beveiligd PDF- of Microsoft Office-document naar de nieuwe map. Zoek nu de inhoud van documenten die met een beleid zijn beveiligd met AEM-zoekopdracht. Het moet het document met gezochte tekst terugkeren.

