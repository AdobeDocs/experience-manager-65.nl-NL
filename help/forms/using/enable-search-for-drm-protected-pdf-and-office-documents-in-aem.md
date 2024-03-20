---
title: AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten
description: Leer hoe u native AEM zoekopdracht kunt inschakelen voor het uitvoeren van full-text zoekopdrachten op DRM-beveiligde PDF-documenten.
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
noindex: true
feature: Document Security
exl-id: 91cbd1f1-d53d-455b-8d2c-6918b521db81
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager biedt een gebruikersinterface voor het zoeken naar en zoeken naar verschillende middelen die zijn opgeslagen in AEM. Met de native zoekopdracht kunt u AEM elementen zoeken en zoeken en tekst zoeken op verschillende veelgebruikte documentindelingen, zoals bestanden met onbewerkte tekst, Microsoft Office-documenten en PDF-documenten. U kunt de native zoekopdracht ook uitbreiden en inschakelen om full-text zoekopdrachten uit te voeren op DRM-beveiligde PDF- en Microsoft Office-documenten.

Voer de volgende stappen uit om AEM in te schakelen om te zoeken naar documenten die zijn beveiligd tegen PDF en Microsoft Office.

## Voordat u begint {#before-you-start}

* Installeer en configureer de beveiliging van AEM Forms-documenten.
* Voeg pakket sun.util.agenda aan de lijst van gewenste personen van toe **Configuratie van de firewall voor deserialisatie.** De configuratie wordt vermeld bij `https://'[server]:[port]'/system/console/configMgr`.
* Zorg ervoor dat alle AEM bundels aan de slag zijn. De bundels worden weergegeven op `https://'[server]:[port]'/system/console/bundles`. Als alle bundels niet actief zijn, wacht u en controleert u de status van de bundels na een paar minuten.

## Een veilige verbinding tot stand brengen binnen de AEM Forms-workflow (AEM Forms op JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Een veilige verbinding laat naadloze stroom van informatie tussen AEM Forms op JEE en de diensten OSGi toe die op de zelfde server lopen. Gebruik een van de volgende methoden om een veilige verbinding tot stand te brengen:

* AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* AEM Forms Client SDK-bundel configureren met wederzijdse verificatie

### AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;servername>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL:** Geef de HTTP-URL van AEM Forms op de JEE-server op. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de -Djavax.net.ssl.trustStore=&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> parameter.
   * **Servicenaam**: Voeg de RightsManagementService toe aan de lijst met opgegeven services.
   * **Gebruikersnaam:** Geef de gebruikersnaam van de AEM Forms op de JEE-account op die moet worden gebruikt om aanroepen vanuit AEM Forms op de JEE-server te starten. De opgegeven account moet gemachtigd zijn om documentservices aan te roepen op de AEM Forms op de JEE-server.
   * **Wachtwoord**: Geef het wachtwoord van de AEM Forms op voor de JEE-account die in het veld Gebruikersnaam wordt vermeld.

   Klikken **Opslaan**. AEM is ingeschakeld om te zoeken in met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten.

### AEM Forms Client SDK-bundel configureren met wederzijdse verificatie {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms op JEE. Zie voor meer informatie [CAC en wederzijdse verificatie](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Open AEM configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;servername>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL:** Geef de HTTPS-URL van AEM Forms op de JEE-server op. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de -Djavax.net.ssl.trustStore=&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> parameter.
   * **2-wegs SSL inschakelen**: Schakel de optie 2-wegs SSL inschakelen in.
   * **URL sleutelarchiefbestand**: Geef de URL van het sleutelarchiefbestand op.
   * **TrustStore-bestands-URL**: Geef de URL van het bestand truststore op.
   * **KeyStore-wachtwoord**: Geef het wachtwoord voor het sleutelarchiefbestand op.
   * **TrustStorePassword**: Geef het wachtwoord voor het bestand truststore op.
   * **Servicenaam**: Voeg de RightsManagementService toe aan de lijst met opgegeven services.

   Klikken **Opslaan**. AEM is ingeschakeld om te zoeken in documenten met beveiliging van PDF en Microsoft Office

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Een voorbeelddocument met een beleid beveiligde PDF of Microsoft Office-document indexeren {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload een met beleid beveiligd PDF of Microsoft Office-document naar de nieuwe map. Zoek nu de inhoud van documenten die met een beleid zijn beveiligd met AEM zoekopdracht. Het moet het document met gezochte tekst terugkeren.
