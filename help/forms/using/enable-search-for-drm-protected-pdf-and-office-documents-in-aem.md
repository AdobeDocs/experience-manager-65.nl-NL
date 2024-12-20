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
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# AEM inschakelen om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager biedt een gebruikersinterface voor het zoeken naar en zoeken naar verschillende middelen die zijn opgeslagen in AEM. Met de native zoekopdracht kunt u AEM elementen zoeken en zoeken en tekst zoeken op verschillende veelgebruikte documentindelingen, zoals bestanden met onbewerkte tekst, Microsoft Office-documenten en PDF-documenten. U kunt de native zoekopdracht ook uitbreiden en inschakelen om full-text zoekopdrachten uit te voeren op DRM-beveiligde PDF- en Microsoft Office-documenten.

Voer de volgende stappen uit om AEM in te schakelen om te zoeken naar documenten die zijn beveiligd tegen PDF en Microsoft Office.

## Voordat u begint {#before-you-start}

* Installeer en configureer de beveiliging van AEM Forms-documenten.
* Voeg pakket sun.util.agenda aan de lijst van gewenste personen van de **Configuratie van de Firewall Deserialization toe.** De configuratie wordt weergegeven in `https://'[server]:[port]'/system/console/configMgr` .
* Zorg ervoor dat alle AEM bundels aan de slag zijn. De bundels worden weergegeven bij `https://'[server]:[port]'/system/console/bundles` . Als alle bundels niet actief zijn, wacht u en controleert u de status van de bundels na een paar minuten.

## Een veilige verbinding tot stand brengen binnen de AEM Forms-workflow (AEM Forms op JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Een veilige verbinding laat naadloze stroom van informatie tussen AEM Forms op JEE en de diensten OSGi toe die op de zelfde server lopen. Gebruik een van de volgende methoden om een veilige verbinding tot stand te brengen:

* AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* AEM Forms Client SDK-bundel configureren met wederzijdse verificatie

### AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server URL:** specificeer HTTP URL van AEM Forms op server JEE. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **Naam van de Dienst**: Voeg de RightsManagementService aan de lijst van de gespecificeerde diensten toe.
   * **Gebruikersnaam:** specificeer gebruikersbenaming van AEM Forms op JEE rekening om vraag van AEM Forms op server in werking te stellen JEE. De opgegeven account moet gemachtigd zijn om documentservices aan te roepen op de AEM Forms op de JEE-server.
   * **Wachtwoord**: specificeer wachtwoord van AEM Forms op JEE rekening die op het gebied van de Gebruikersnaam wordt vermeld.

   Klik **sparen**. AEM is ingeschakeld om te zoeken in met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten.

### AEM Forms Client SDK-bundel configureren met wederzijdse verificatie {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms op JEE. Voor gedetailleerde informatie, zie [ CAC en Wederzijdse Authentificatie ](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Open AEM configuratiebeheer en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server URL:** specificeer HTTPS URL van AEM Forms op server JEE. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **laat 2-wegs SSL** toe: Laat 2-wegsSSL optie toe.
   * **het Dossier URL van KeyStore**: Specificeer URL van het keystore dossier.
   * **TrustStore FIle URL**: Specificeer URL van het truststore dossier.
   * **Wachtwoord KeyStore**: Specificeer het wachtwoord voor het keystore dossier.
   * **TrustStorePassword**: Specificeer het wachtwoord voor het truststore dossier.
   * **Naam van de Dienst**: Voeg de RightsManagementService aan de lijst van de gespecificeerde diensten toe.

   Klik **sparen**. AEM is ingeschakeld om te zoeken in documenten met beveiliging van PDF en Microsoft Office

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Een voorbeelddocument met een beleid beveiligde PDF of Microsoft Office-document indexeren {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload een met beleid beveiligd PDF of Microsoft Office-document naar de nieuwe map. Zoek nu de inhoud van documenten die met een beleid zijn beveiligd met AEM zoekopdracht. Het moet het document met gezochte tekst terugkeren.
