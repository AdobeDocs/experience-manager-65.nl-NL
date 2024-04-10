---
title: Het verminderen van rangschikkingskwesties in AEM
description: Leer hoe te om rangschikkingskwesties in AEM te verlichten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 01e9ab67-15e2-4bc4-9b8f-0c84bcd56862
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# Het verminderen van rangschikkingskwesties in AEM{#mitigating-serialization-issues-in-aem}

## Overzicht {#overview}

Het AEM team bij Adobe werkte nauw samen met het open-source-project [NotSoSerial](https://github.com/kantega/notsoserial) helpen de kwetsbaarheden te verlichten die worden beschreven in **CVE-2015-7501**. NotSoSerial is in licentie gegeven onder de [Apache 2-licentie](https://www.apache.org/licenses/LICENSE-2.0) en omvat ASM-code die onder zijn eigen licentie is verleend [BSD-achtige licentie](https://asm.ow2.io/).

De agent jar inbegrepen met dit pakket is de gewijzigde distributie van Adobe van NotSoSerial.

NotSoSerial is een Java™-oplossing voor een Java™-probleem en is niet AEM-specifiek. Er wordt een Preflight-controle toegevoegd aan een poging om een object te deserialiseren. Deze controle test een klassennaam tegen een firewall-stijl lijst van gewenste personen, of lijst van gewezen personen, of allebei. Vanwege het beperkte aantal klassen in de standaard lijst van gewezen personen is het onwaarschijnlijk dat deze test invloed heeft op uw systemen of code.

Door gebrek, voert de agent een lijst van gewezen personen controle tegen huidige bekende kwetsbare klassen uit. Deze lijst van gewezen personen is bedoeld om u tegen de huidige lijst van exploitaties te beschermen die dit type van kwetsbaarheid gebruiken.

De lijst van gewezen personen en de lijst van gewenste personen kunnen worden gevormd door de instructies in te volgen [De agent configureren](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) van dit artikel.

De agent is bedoeld om de recentste bekende kwetsbare klassen te helpen verlichten. Als uw project niet-vertrouwde gegevens deserializing, kan het nog kwetsbaar aan ontkenning van de dienstaanvallen, uit geheugenaanvallen, en onbekende toekomstige deserialization exploiteert.

Adobe biedt officieel ondersteuning voor Java™ 6, 7 en 8. De Adobe heeft echter begrepen dat NotSoSerial ook Java™ 5 ondersteunt.

## De agent installeren {#installing-the-agent}

>[!NOTE]
>
>Als u eerder de rangschikkingshotfix voor AEM 6.1 hebt geïnstalleerd, verwijder de bevelen van het agentenbegin van uw looppas Java™.

1. Installeer de **com.adobe.cq.cq-serialization-tester** bundel.

1. Ga naar de bundel webconsole op `https://server:port/system/console/bundles`
1. Zoek de serialisatiebundel en begin het. Het doen zo dynamisch autoloadt de agent NotSoSerial.

## De Agent installeren op toepassingsservers {#installing-the-agent-on-application-servers}

De agent NotSoSerial is niet inbegrepen in de standaarddistributie van AEM voor toepassingsservers. U kunt deze echter extraheren uit de AEM jar-distributie en deze gebruiken met de configuratie van de toepassingsserver:

1. Download eerst het AEM QuickStart-bestand en extraheer het:

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Ga naar de locatie van de nieuwe AEM zonder ritssluiting en kopieer de `crx-quickstart/opt/notsoserial/` aan de `crx-quickstart` map van de installatie van de AEM toepassingsserver.

1. Eigendom wijzigen van `/opt` aan de gebruiker die de server uitvoert:

   ```shell
   chown -R opt <user running the server>
   ```

1. Vorm en controleer dat de agent behoorlijk zoals aangetoond in de volgende secties van dit artikel is geactiveerd.

## De agent configureren {#configuring-the-agent}

De standaardconfiguratie is geschikt voor de meeste installaties. Deze configuratie omvat een lijst van gewezen personen van bekende verre looppas kwetsbare klassen en een lijst van gewenste personen van pakketten waar deserialization van vertrouwde op gegevens veilig is.

De firewallconfiguratie is dynamisch, en kan op elk ogenblik worden veranderd door:

1. Ga naar de webconsole op `https://server:port/system/console/configMgr`
1. Zoeken naar en klikken **Configuratie van de firewall voor deserialisatie.**

   >[!NOTE]
   >
   >U kunt de configuratiepagina ook direct bereiken door tot URL toegang te hebben bij:
   >
   >* `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`

Deze configuratie bevat de lijst van gewenste personen, de lijst van gewezen personen, en deserialization registreren.

**Aanbieding toestaan**

In de sectie Aanbieding toestaan zijn deze aanbiedingen klassen of voorvoegsels van pakketten die kunnen worden gedeserialiseerd. Als u klassen van uw eigen deserializing, voeg of de klassen of de pakketten aan deze lijst van gewenste personen toe.

**Aanbieding blokkeren**

In de sectie met bloklijsten staan klassen die nooit mogen worden gedeserialiseerd. De aanvankelijke reeks van deze klassen is beperkt tot klassen die aan verre uitvoeringsaanvallen kwetsbaar zijn gevonden. De lijst van gewezen personen wordt toegepast vóór om het even welk toelaat vermelde ingangen.

**Diagnostische registratie**

In de sectie voor kenmerkend registreren, kunt u verscheidene opties kiezen om te registreren wanneer deserialization plaatsvindt. Deze opties worden slechts het programma geopend eerste gebruik, en niet opnieuw het programma geopend op verder gebruik.

De standaardwaarde van **class-name-only** Hiermee wordt u geïnformeerd over de klassen die worden gedeserialiseerd.

U kunt ook de **vol-stapel** Deze optie registreert een stapel Java™ van de eerste deserialization poging om u te informeren waar uw deserialization plaatsvindt. Deze optie is handig als u deserialisatie wilt zoeken en verwijderen uit uw gebruik.

## De activering van de agent controleren {#verifying-the-agent-s-activation}

U kunt de configuratie van de deserialization agent verifiëren door aan URL te doorbladeren bij:

* `https://server:port/system/console/healthcheck?tags=deserialization`

Nadat u tot URL toegang hebt, wordt een lijst van gezondheidscontroles met betrekking tot de agent getoond. U kunt bepalen of de agent correct wordt geactiveerd door te controleren of de gezondheidscontroles voldoende zijn. Als zij ontbreken, moet u de agent manueel laden.

Voor meer informatie over het oplossen van problemenkwesties met de agent, zie [Fouten afhandelen met laden van dynamische agent](#handling-errors-with-dynamic-agent-loading) hieronder.

>[!NOTE]
>
>Als u `org.apache.commons.collections.functors` volgens de lijst van gewenste personen mislukt de gezondheidscontrole altijd .

## Fouten afhandelen met laden van dynamische agent {#handling-errors-with-dynamic-agent-loading}

Als de fouten in het logboek worden blootgesteld, of de verificatiestappen een probleem ontdekken ladend de agent, laadt manueel de agent. Deze workflow wordt ook aanbevolen als u een JRE (Java™ Runtime Environment) gebruikt in plaats van een JDK (Java™ Development Toolkit), omdat de gereedschappen voor dynamisch laden niet beschikbaar zijn.

Ga als volgt te werk om de agent handmatig te laden:

1. Bewerk de JVM-opstartparameters van de CQ-jar en voeg de volgende optie toe:

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Vereist dat u ook de optie -nofork CQ/AEM gebruikt, samen met de juiste JVM-geheugeninstellingen, omdat de agent niet is ingeschakeld op een geforceerde JVM.

   >[!NOTE]
   >
   >De distributie van de Adobe van de agent NotSoSerial kan in worden gevonden `crx-quickstart/opt/notsoserial/` van de AEM installatie.

1. De JVM stoppen en opnieuw starten;

1. Verifieer opnieuw de activering van de agent door de hierboven beschreven stappen te volgen in [De activering van de agent controleren](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation).

## Andere overwegingen {#other-considerations}

Als u een IBM® JVM gebruikt, raadpleegt u de documentatie over ondersteuning voor de Java™ Attach-API op [deze locatie](https://www.ibm.com/docs/en/sdk-java-technology/8?topic=documentation-java-attach-api).
