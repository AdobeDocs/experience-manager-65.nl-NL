---
title: Het verminderen van rangschikkingskwesties in AEM
seo-title: Mitigating serialization issues in AEM
description: Leer hoe te om rangschikkingskwesties in AEM te verlichten.
seo-description: Learn how to mitigate serialization issues in AEM.
uuid: c3989dc6-c728-40fd-bc47-f8427ed71a49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: f3781d9a-421a-446e-8b49-40744b9ef58e
exl-id: 01e9ab67-15e2-4bc4-9b8f-0c84bcd56862
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 0%

---

# Het verminderen van rangschikkingskwesties in AEM{#mitigating-serialization-issues-in-aem}

## Overzicht {#overview}

Het AEM-team bij Adobe werkt nauw samen met het open-source-project [NotSoSerial](https://github.com/kantega/notsoserial) helpen bij het verhelpen van de kwetsbaarheden die worden beschreven in **CVE-2015-7501**. NotSoSerial is in licentie gegeven onder de [Apache 2-licentie](https://www.apache.org/licenses/LICENSE-2.0) en omvat ASM-code die onder zijn eigen licentie is verleend [BSD-achtige licentie](https://asm.ow2.org/license.html).

De agent jar inbegrepen met dit pakket is Adobe aangepaste distributie van NotSoSerial.

NotSoSerial is een oplossing op Java-niveau voor een probleem op Java-niveau en is niet AEM specifiek. Er wordt een Preflight-controle toegevoegd aan een poging om een object te deserialiseren. Deze controle zal een klassennaam tegen een firewall-stijl lijst van gewenste personen en/of lijst van gewezen personen testen. Vanwege het beperkte aantal klassen in de standaard lijst van gewezen personen is het onwaarschijnlijk dat dit van invloed is op uw systemen of code.

Door gebrek, zal de agent een lijst van gewezen personen controle tegen huidige bekende kwetsbare klassen uitvoeren. Deze lijst van gewezen personen is bedoeld om u te beschermen tegen de huidige lijst van exploitaties die dit type van kwetsbaarheid gebruiken.

De lijst van gewezen personen en de lijst van gewenste personen kunnen worden gevormd door de instructies in te volgen [De agent configureren](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) van dit artikel.

De agent is bedoeld om de recentste bekende kwetsbare klassen te helpen verlichten. Als uw project niet-vertrouwde gegevens deserializing, kan het nog kwetsbaar aan ontkenning van de dienstaanvallen, uit geheugenaanvallen, en onbekende toekomstige deserialization exploiteert.

Adobe biedt officieel ondersteuning voor Java 6, 7 en 8, maar volgens ons biedt NotSoSerial ook ondersteuning voor Java 5.

## De agent installeren {#installing-the-agent}

>[!NOTE]
>
>Als u eerder rangschikkingshotfix voor AEM 6.1 hebt geïnstalleerd, te verwijderen gelieve de bevelen van het agentenbegin van uw de uitvoeringslijn van Java.

1. Installeer de **com.adobe.cq.cq-serialization-tester** bundel.

1. Ga naar de bundel webconsole op `https://server:port/system/console/bundles`
1. Zoek de serialisatiebundel en begin het. Dit zou dynamisch autoload de agent NotSoSerial moeten.

## De Agent installeren op toepassingsservers {#installing-the-agent-on-application-servers}

De agent NotSoSerial is niet inbegrepen in de standaarddistributie van AEM voor toepassingsservers. U kunt deze echter extraheren uit de AEM jar-distributie en deze gebruiken met de configuratie van de toepassingsserver:

1. Download eerst het AEM QuickStart-bestand en extraheer het:

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Ga naar de locatie van de nieuw uitgegumde AEM QuickStart en kopieer de `crx-quickstart/opt/notsoserial/` aan de `crx-quickstart` map van de installatie van de AEM toepassingsserver.

1. Eigendom wijzigen van `/opt` aan de gebruiker die de server uitvoert:

   ```shell
   chown -R opt <user running the server>
   ```

1. Vorm en controleer dat de agent behoorlijk zoals aangetoond in de volgende secties van dit artikel is geactiveerd.

## De agent configureren {#configuring-the-agent}

De standaardconfiguratie is geschikt voor de meeste installaties. Dit omvat een lijst van gewezen personen van bekende klassen die kwetsbaar zijn voor externe uitvoering en een lijst van gewenste personen van pakketten waar deserialization van vertrouwde gegevens relatief veilig zou moeten zijn.

De firewallconfiguratie is dynamisch, en kan op elk ogenblik worden veranderd door:

1. Ga naar de webconsole op `https://server:port/system/console/configMgr`
1. Zoeken naar en klikken op **Configuratie van de firewall voor deserialisatie.**

   >[!NOTE]
   >
   >U kunt de configuratiepagina ook direct bereiken door tot URL toegang te hebben bij:
   >
   >* `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`


Deze configuratie bevat de lijst van gewenste personen, de lijst van gewezen personen, en deserialization registreren.

**Aanbieding toestaan**

In de sectie voor het toestaan van lijsten zijn dit klassen of voorvoegsels van pakketten die kunnen worden gedeserialiseerd. Houd er rekening mee dat als u deserialiseert voor klassen van uw eigen klasse, u klassen of pakketten aan deze lijst van gewenste personen moet toevoegen.

**Aanbieding blokkeren**

In de sectie met bloklijsten staan klassen die nooit voor deserialisatie zijn toegestaan. De aanvankelijke reeks van deze klassen is beperkt tot klassen die aan verre uitvoeringsaanvallen kwetsbaar zijn gevonden. De lijst van gewezen personen wordt toegepast voordat vermelde items worden toegestaan.

**Diagnostische registratie**

In de sectie voor kenmerkend registreren, kunt u verscheidene opties kiezen om te registreren wanneer deserialization plaatsvindt. Deze worden slechts het programma geopend eerste gebruik, en niet opnieuw het programma geopend op verder gebruik.

De standaardinstelling van **class-name-only** Hiermee geeft u op welke klassen worden gedeserialiseerd.

U kunt ook de **vol-stapel** Deze optie registreert een Java-stapel van de eerste deserialisatiepoging om u te informeren waar uw deserialization plaatsvindt. Dit kan nuttig zijn om deserialization van uw gebruik te vinden en te verwijderen.

## De activering van de agent controleren {#verifying-the-agent-s-activation}

U kunt de configuratie van de deserialization agent verifiëren door aan URL te doorbladeren bij:

* `https://server:port/system/console/healthcheck?tags=deserialization`

Zodra u tot URL toegang hebt, zal een lijst van gezondheidscontroles met betrekking tot de agent worden getoond. U kunt bepalen of de agent correct wordt geactiveerd door te controleren of de gezondheidscontroles voldoende zijn. Als zij ontbreken, kunt u de agent manueel moeten laden.

Voor meer informatie over het oplossen van problemenkwesties met de agent, zie [Fouten afhandelen met laden van dynamische agent](#handling-errors-with-dynamic-agent-loading) hieronder.

>[!NOTE]
>
>Als u `org.apache.commons.collections.functors` voor de lijst van gewenste personen zal de gezondheidscontrole altijd mislukken .

## Fouten afhandelen met laden van dynamische agent {#handling-errors-with-dynamic-agent-loading}

Als de fouten in het logboek worden blootgesteld, of de verificatiestappen een probleem ontdekken ladend de agent, zou u de agent manueel kunnen moeten laden. Dit wordt ook aanbevolen voor het geval u een JRE (Java Runtime Environment) gebruikt in plaats van een JDK (Java Development Toolkit), omdat de gereedschappen voor dynamisch laden niet beschikbaar zijn.

Volg onderstaande instructies om de agent handmatig te laden:

1. Wijzig de JVM startparameters van de CQ-jar en voeg de volgende optie toe:

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Dit vereist ook het gebruiken van de optie -nofork CQ/AEM, samen met de aangewezen JVM geheugenmontages, aangezien de agent niet op een forked JVM zal worden toegelaten.

   >[!NOTE]
   >
   >De distributie van de Adobe van de agent NotSoSerial kan in worden gevonden `crx-quickstart/opt/notsoserial/` van de AEM installatie.

1. De JVM stoppen en opnieuw starten;

1. Verifieer opnieuw de activering van de agent door de hierboven beschreven stappen te volgen in [De activering van de agent controleren](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation).

## Andere overwegingen {#other-considerations}

Als u op een IBM JVM werkt, raadpleegt u de documentatie over ondersteuning voor de Java Attach-API op [deze locatie](https://www.ibm.com/support/knowledgecenter/SSSTCZ_2.0.0/com.ibm.rt.doc.20/user/attachapi.html).
