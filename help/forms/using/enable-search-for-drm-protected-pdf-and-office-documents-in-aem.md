---
title: AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten
seo-title: AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten
description: Leer hoe u native AEM zoekopdracht kunt inschakelen voor het uitvoeren van full-text zoekopdrachten op DRM-beveiligde PDF-documenten.
seo-description: Leer hoe u native AEM zoekopdracht kunt inschakelen voor het uitvoeren van full-text zoekopdrachten op DRM-beveiligde PDF-documenten.
uuid: dba882f8-bad4-4122-a0df-03cf087afb23
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7eebef08-83b9-4b56-90ec-35ab3b0c27e8
noindex: true
translation-type: tm+mt
source-git-commit: b703c59d7d913fc890c713c6e49e7d89211fd998
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---


# AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager biedt een gebruikersinterface voor het zoeken naar en zoeken naar verschillende middelen die zijn opgeslagen in AEM. Met de native zoekopdracht kunt u AEM elementen zoeken en zoeken en tekst zoeken in verschillende veelgebruikte documentindelingen, zoals bestanden met onbewerkte tekst, Microsoft Office-documenten en PDF-documenten. U kunt de native zoekopdracht ook uitbreiden en inschakelen om full-text zoekopdrachten uit te voeren voor met DRM beveiligde PDF- en Microsoft Office-documenten.

Voer de volgende stappen uit om AEM in te schakelen voor het doorzoeken van met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten:

## Voordat u begint {#before-you-start}

* Installeer en configureer de beveiliging van AEM Forms-documenten.
* Voeg pakket sun.util.agenda aan de lijst van gewenste personen van **Deserialization Firewall Configuration toe.** De configuratie wordt vermeld bij  `https://'[server]:[port]'/system/console/configMgr`.
* Zorg ervoor dat alle AEM bundels aan de slag zijn. De bundels worden vermeld bij `https://'[server]:[port]'/system/console/bundles`. Als alle bundels niet actief zijn, wacht u en controleert u de status van de bundels na een paar minuten.

## Beveiligde verbinding tot stand brengen in AEM Forms-workflow (AEM Forms op JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Een veilige verbinding laat naadloze stroom van informatie tussen AEM Forms op JEE en de diensten OSGi toe die op de zelfde server lopen. Gebruik een van de volgende methoden om een veilige verbinding tot stand te brengen:

* AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* AEM Forms Client SDK-bundel configureren met wederzijdse verificatie

### AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL:HTTP-URL van AEM Forms** opgeven op JEE-server. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **Servicenaam**: Voeg RightsManagementService aan de lijst van de gespecificeerde diensten toe.
   * **Gebruikersnaam:** Geef de gebruikersnaam op van de AEM Forms op JEE-account die moet worden gebruikt om aanroepen vanuit AEM Forms op de JEE-server te starten. De opgegeven account moet gemachtigd zijn om documentservices aan te roepen op de AEM Forms op de JEE-server.
   * **Wachtwoord**: Geef het wachtwoord van de AEM Forms op voor de JEE-account die in het veld Gebruikersnaam wordt vermeld.

   Klik **Opslaan**. AEM is ingeschakeld om te zoeken in met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten.

### AEM Forms Client SDK-bundel configureren met wederzijdse verificatie {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms op JEE. Voor gedetailleerde informatie, zie [CAC en Wederzijdse Authentificatie](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Open AEM configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL:HTTPS-URL van AEM Forms** opgeven op JEE-server. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **2-wegs SSL** inschakelen: Schakel de optie 2-wegs SSL inschakelen in.
   * **URL** sleutelarchiefbestand: Geef de URL van het sleutelarchiefbestand op.
   * **TrustStore-bestands-URL**: Geef de URL van het bestand truststore op.
   * **Wachtwoord** sleutelarchief: Geef het wachtwoord voor het sleutelarchiefbestand op.
   * **TrustStorePassword**: Geef het wachtwoord voor het bestand truststore op.
   * **Servicenaam**: Voeg RightsManagementService aan de lijst van de gespecificeerde diensten toe.

   Klik **Opslaan**. AEM is ingeschakeld om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten

## Een voorbeeld van een met beleid beveiligd PDF- of Microsoft Office-document {#index-a-sample-policy-protected-pdf-or-microsoft-office-document} indexeren

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload een met een beleid beveiligd PDF- of Microsoft Office-document naar de nieuwe map. Zoek nu de inhoud van documenten die met een beleid zijn beveiligd met AEM zoekopdracht. Het moet het document met gezochte tekst terugkeren.

