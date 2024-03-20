---
title: AEM inschakelen om te zoeken naar documenten die zijn beveiligd met PDF
description: Leer hoe u native AEM zoekopdracht kunt inschakelen voor het uitvoeren van full-text zoekopdrachten op DRM-beveiligde PDF-documenten.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
docset: aem65
feature: Document Security
exl-id: 7cf17fb6-021a-473e-bc3b-27c317953002
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# AEM inschakelen om te zoeken naar documenten die zijn beveiligd met PDF{#enable-aem-to-search-document-security-protected-pdf-documents}

AEM zoekopdracht kan AEM elementen zoeken en zoeken en tekst zoeken op verschillende veelgebruikte documentindelingen, zoals bestanden met normale tekst, Microsoft Office-documenten en PDF-documenten. U kunt de oorspronkelijke zoekopdracht ook uitbreiden om een zoekopdracht in volledige tekst uit te voeren op [PDF Documenten die zijn beveiligd met AEM documentbeveiliging](../../forms/using/admin-help/document-security.md). Voer de volgende stappen uit om AEM in staat te stellen volledige tekst op dergelijke documenten te zoeken:

1. Een veilige verbinding tot stand brengen
1. Een voorbeelddocument met een door een beleid beveiligde PDF indexeren

## Vereisten {#prerequisites}

* Als u AEM Forms gebruikt op OSGi:

   * Installeren [AEM Forms Document Security Indexer-pakket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) op de AEM Forms-server.

   * Controleer of een AEM Forms op de JEE-server actief is en of documentbeveiliging op de overeenkomstige AEM Forms op de JEE-server is geïnstalleerd. Het AEM Formulier op de JEE-server is vereist om het beveiligde document te indexeren.

* Als u alleen AEM Forms op de JEE-server gebruikt, is het indexeerpakket al geïnstalleerd.
* Zorg ervoor dat alle bundels aan de slag zijn. Als alle bundels niet actief zijn, wacht u tot alle bundels actief zijn.

   * Voor AEM Forms op OSGi worden de bundels weergegeven op https://&#39;[server]:[poort]&quot;/systeem/console/bundels.
   * Voor AEM Forms op JEE worden de bundels weergegeven op https://&#39;[server]:[poort]&#39;/[contextpad]/systeem/console/bundels. Bijvoorbeeld https://localhost:8080/lc/system/console/bundles.

* Voeg de *sun.util.agenda* aan de lijst van gewenste personen. Voer de volgende stappen uit om het pakket aan de lijst van gewenste personen toe te voegen:

   1. Open AEM webconsole. De URL is https://&#39;[server]:[poort]&quot;/system/console/configMgr.
   1. Zoeken en openen **Configuratie van firewall voor deserialisatie**.

   1. Voeg het pakket sun.util.agenda toe aan het Gevoegde op lijst van gewenste personen veld voor klassen of voorvoegsels van pakketten en klik op **Opslaan**.

### Een veilige verbinding tot stand brengen tussen AEM Forms JEE- en OSGi-stapels {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

U kunt een van de volgende methoden gebruiken om de beveiligde verbinding tot stand te brengen:

* De Adobe LiveCycle Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* De SDK-bundel voor client-SDK van Adobe LiveCycle configureren met wederzijdse verificatie

#### De Adobe LiveCycle Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM webconsole. De URL is https://&#39;[server]:[poort]&quot;/system/console/configMgr.
1. Zoek en open de **Adobe LiveCycle client SDK-bundel**. Geef waarde op voor de volgende velden:

   * **Server-URL:** Geef de HTTPS-URL van AEM Forms op de JEE-server op. Start de server opnieuw op met -Djavax.net.ssl.trustStore= om communicatie via https mogelijk te maken&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> parameter.
   * **Servicenaam**: Voeg de RightsManagementService toe aan de lijst met opgegeven services.
   * **Gebruikersnaam:** Geef de gebruikersnaam op van de AEM Forms op de JEE-account die moet worden gebruikt om oproepen van AEM server te starten. De opgegeven account moet beschikken over machtigingen om documentservices te starten op de AEM Forms op de JEE-server.
   * **Wachtwoord**: Geef het wachtwoord van de AEM Forms op voor de JEE-account die in het veld Gebruikersnaam wordt vermeld.

   Klikken **Opslaan**. AEM is ingeschakeld om te zoeken in documenten met een beveiligde PDF.

#### De SDK-bundel voor client-SDK van Adobe LiveCycle configureren met wederzijdse verificatie {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms op JEE. Zie voor meer informatie [CAC en wederzijdse verificatie](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Open AEM webconsole. De URL is https://&#39;[server]:[poort]&quot;/system/console/configMgr.
1. Zoek en open de **Adobe LiveCycle Client SDK** Bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server-URL**: Geef de HTTPS-URL van AEM Forms op de JEE-server op. Start de AEM opnieuw met de -Djavax.net.ssl.trustStore= om communicatie via https mogelijk te maken&lt;path of=&quot;&quot; aem=&quot;&quot; forms=&quot;&quot; on=&quot;&quot; jee=&quot;&quot; keystore=&quot;&quot; file=&quot;&quot;> parameter.
   * **2-wegs SSL inschakelen**: Schakel de optie 2-wegs SSL inschakelen in.
   * **URL sleutelarchiefbestand**: Geef de URL van het sleutelarchiefbestand op.
   * **TrustStore-bestands-URL**: Geef de URL van het bestand truststore op.
   * **KeyStore-wachtwoord**: Geef het wachtwoord voor het sleutelarchiefbestand op.
   * **TrustStorePassword**: Geef het wachtwoord voor het bestand truststore op.
   * **Servicenaam**: Voeg de RightsManagementService toe aan de lijst met opgegeven services.

   Klikken **Opslaan**. AEM is ingeschakeld om te zoeken naar documenten met een beveiligde PDF

### Een voorbeelddocument met een door een beleid beveiligde PDF indexeren {#index-a-sample-policy-protected-pdf-document}

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload de met beleid beveiligde PDF-documenten naar de nieuwe map.

   Nu kunt u de documenten met een beleidsbeveiliging doorzoeken met AEM zoekopdracht.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.
