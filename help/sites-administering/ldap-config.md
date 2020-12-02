---
title: LDAP configureren met AEM 6
seo-title: LDAP configureren met AEM 6
description: Leer hoe u LDAP kunt configureren met AEM.
seo-description: Leer hoe u LDAP kunt configureren met AEM.
uuid: 0007def4-86f0-401d-aa37-c8d49d5acea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 5faf6ee5-9242-48f4-87a8-ada887a3be1e
translation-type: tm+mt
source-git-commit: 2fc35bfd93585a586cb1d4e3299261611db49ba6
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 0%

---


# LDAP configureren met AEM 6 {#configuring-ldap-with-aem}

LDAP (de **L** rechter **D** directory **A** cess **P** Protocol) wordt gebruikt voor toegang tot gecentraliseerde directoryservices. Dit helpt de inspanning verminderen die wordt vereist om gebruikersrekeningen te beheren aangezien zij door veelvoudige toepassingen kunnen worden betreden. Een dergelijke LDAP-server is Active Directory. LDAP wordt vaak gebruikt om Single Sign On te bereiken, waardoor een gebruiker toegang heeft tot meerdere toepassingen nadat hij zich eenmaal heeft aangemeld.

Gebruikersaccounts kunnen worden gesynchroniseerd tussen de LDAP-server en de gegevensopslagruimte, waarbij de gegevens van de LDAP-account worden opgeslagen in de gegevensopslagruimte. Hierdoor kunnen de accounts worden toegewezen aan groepen in de opslagplaats voor het toewijzen van de vereiste machtigingen en bevoegdheden.

De gegevensopslagruimte gebruikt LDAP-verificatie om dergelijke gebruikers te verifiëren, waarbij referenties worden doorgegeven aan de LDAP-server voor validatie, wat vereist is voordat toegang tot de gegevensopslagruimte wordt toegestaan. Om de prestaties te verbeteren, kunnen gevalideerde gegevens door de opslagplaats in cache worden opgeslagen, met een vervaltijd om ervoor te zorgen dat de validatie na een geschikte periode wordt uitgevoerd.

Wanneer een account wordt verwijderd uit de LDAP-servervalidatie, wordt geen toegang meer verleend tot de gegevensopslagruimte. Details van LDAP-accounts die in de opslagplaats zijn opgeslagen, kunnen ook worden gewist.

Het gebruik van dergelijke accounts is transparant voor uw gebruikers, ze zien geen verschil tussen gebruikers- en groepsaccounts die met LDAP zijn gemaakt en accounts die alleen in de opslagplaats zijn gemaakt.

In AEM 6 wordt bij LDAP-ondersteuning een nieuwe implementatie geleverd waarvoor een ander type configuratie is vereist dan bij eerdere versies.

Alle configuraties LDAP zijn nu beschikbaar als configuraties OSGi. Zij kunnen via de console van het Beheer van het Web in worden gevormd:
`https://serveraddress:4502/system/console/configMgr`

Om LDAP te hebben werkend met AEM, moet u drie configuraties tot stand brengen OSGi:

1. Een LDAP-identiteitsprovider (IDP).
1. Een synchronisatiehandler.
1. Een externe aanmeldingsmodule.

>[!NOTE]
>
>Bekijk [De externe aanmeldingsmodule van Oak - voor authentiek met LDAP en Beyond](https://docs.adobe.com/content/ddc/en/gems/oak-s-external-login-module---authenticating-with-ldap-and-beyon.html#) om de externe aanmeldingsmodules diep te duwen.
>
>Zie [Adobe Experience Manager 6.5 configureren om Apache Directory Service te gebruiken voor een voorbeeld van het configureren van Experience Manager met Apache DS.](https://helpx.adobe.com/experience-manager/using/configuring-aem64-apache-directory-service.html)

## De LDAP-identiteitsprovider {#configuring-the-ldap-identity-provider} configureren

De LDAP-identiteitsprovider wordt gebruikt om te definiëren hoe gebruikers worden opgehaald van de LDAP-server.

Deze vindt u in de beheerconsole onder de naam **Apache Jackrabbit Oak LDAP Identity Provider**.

De volgende configuratieopties zijn beschikbaar voor de LDAP Identiteitsprovider:

<table>
 <tbody>
  <tr>
   <td><strong>Naam LDAP-provider</strong></td>
   <td>Naam van deze LDAP-providerconfiguratie.</td>
  </tr>
  <tr>
   <td><strong>Hostnaam LDAP-server</strong><br /> </td>
   <td>Hostnaam van de LDAP-server</td>
  </tr>
  <tr>
   <td><strong>LDAP-serverpoort</strong></td>
   <td>Poort van de LDAP-server</td>
  </tr>
  <tr>
   <td><strong>SSL gebruiken</strong></td>
   <td>Hiermee wordt aangegeven of een SSL-verbinding (LDAP) moet worden gebruikt.</td>
  </tr>
  <tr>
   <td><strong>TLS gebruiken</strong></td>
   <td>Geeft aan of TLS moet worden gestart op verbindingen.</td>
  </tr>
  <tr>
   <td><strong>Certificaatcontrole uitschakelen</strong></td>
   <td>Hiermee wordt aangegeven of validatie van servercertificaten moet worden uitgeschakeld.</td>
  </tr>
  <tr>
   <td><strong>DN binden</strong></td>
   <td>DN van de gebruiker voor verificatie. Als dit leeg wordt verlaten, zal anonieme bind worden uitgevoerd.</td>
  </tr>
  <tr>
   <td><strong>Wachtwoord binden</strong></td>
   <td>Wachtwoord van de gebruiker voor verificatie</td>
  </tr>
  <tr>
   <td><strong>Time-out zoeken</strong></td>
   <td>Tijd tot een zoektijd uit</td>
  </tr>
  <tr>
   <td><strong>Admin pool max actief</strong></td>
   <td>De maximale actieve grootte van de beheerverbindingspool.</td>
  </tr>
  <tr>
   <td><strong>Maximale aantal gebruikers</strong></td>
   <td>De maximale actieve grootte van de pool van de gebruikersverbinding.</td>
  </tr>
  <tr>
   <td><strong>Gebruiker basis-DN</strong></td>
   <td>De DN voor gebruikerszoekopdrachten</td>
  </tr>
  <tr>
   <td><strong>Gebruikersobjectklassen</strong></td>
   <td>De lijst met objectklassen die een gebruikersinvoer moet bevatten.</td>
  </tr>
  <tr>
   <td><strong>Id-kenmerk van gebruiker</strong></td>
   <td>Naam van het attribuut dat gebruikersidentiteitskaart bevat</td>
  </tr>
  <tr>
   <td><strong>Extra filter Gebruiker</strong></td>
   <td>Extra LDAP-filter bij het zoeken naar gebruikers. Het uiteindelijke filter wordt als volgt opgemaakt: '(&amp;(&lt;idAttr&gt;=&lt;userId&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)' (user.extraFilter)</td>
  </tr>
  <tr>
   <td><strong>DN-paden gebruiker</strong></td>
   <td>Bepaalt of de DN moet worden gebruikt voor het berekenen van een gedeelte van het tussenliggende pad.</td>
  </tr>
  <tr>
   <td><strong>Basis-DN groeperen</strong></td>
   <td>De basis-DN voor groepszoekopdrachten.</td>
  </tr>
  <tr>
   <td><strong>Objectklassen groeperen</strong></td>
   <td>De lijst met objectklassen die een groepsitem moet bevatten.</td>
  </tr>
  <tr>
   <td><strong>Groepsnaam, kenmerk</strong></td>
   <td>Naam van het kenmerk dat de groepsnaam bevat.</td>
  </tr>
  <tr>
   <td><strong>Extra filter groeperen</strong></td>
   <td>Extra LDAP-filter bij het zoeken naar groepen. Het uiteindelijke filter wordt als volgt opgemaakt: '(&amp;(&lt;nameAttr&gt;=&lt;groupName&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)'</td>
  </tr>
  <tr>
   <td><strong>DN-paden groeperen</strong></td>
   <td>Bepaalt of de DN moet worden gebruikt voor het berekenen van een gedeelte van het tussenliggende pad.</td>
  </tr>
  <tr>
   <td><strong>Kenmerk groepslid</strong></td>
   <td>Groepseigenschap die het lid of de leden van een groep bevat.</td>
  </tr>
 </tbody>
</table>

## De Synchronisatie-handler {#configuring-the-synchronization-handler} configureren

De synchronisatiehandler definieert hoe de gebruikers en groepen van de identiteitsprovider worden gesynchroniseerd met de opslagplaats.

Deze bevindt zich onder de naam **Apache Jackrabbit Oak Default Sync Handler** in de beheerconsole.

De volgende configuratieopties zijn beschikbaar voor de Synchronisatie-handler:

<table>
 <tbody>
  <tr>
   <td><strong>Naam synchronisatiehandler</strong></td>
   <td>Naam van de synchronisatieconfiguratie.</td>
  </tr>
  <tr>
   <td><strong>Vervaltijd gebruiker</strong></td>
   <td>Duur totdat een gesynchroniseerde gebruiker is verlopen.</td>
  </tr>
  <tr>
   <td><strong>Automatisch lidmaatschap van gebruiker</strong></td>
   <td>Lijst met groepen waaraan een gesynchroniseerde gebruiker automatisch wordt toegevoegd.</td>
  </tr>
  <tr>
   <td><strong>Toewijzing van gebruikerseigenschappen</strong></td>
   <td>Lijsttoewijzingsdefinitie van lokale eigenschappen van externe eigenschappen.</td>
  </tr>
  <tr>
   <td><strong>Voorvoegsel gebruikerspad</strong></td>
   <td>Het padvoorvoegsel dat wordt gebruikt bij het maken van nieuwe gebruikers.</td>
  </tr>
  <tr>
   <td><strong>Vervaldatum gebruikerslidmaatschap</strong></td>
   <td>Tijd waarna het lidmaatschap verloopt.<br /> </td>
  </tr>
  <tr>
   <td><strong>Geneste diepte van gebruikerslidmaatschap</strong></td>
   <td>Retourneert de maximale diepte van het nesten van groepen wanneer lidmaatschapsrelaties worden gesynchroniseerd. Met de waarde 0 wordt het opzoeken van het groepslidmaatschap effectief uitgeschakeld. Met de waarde 1 voegt u alleen de directe groepen van een gebruiker toe. Deze waarde heeft geen effect wanneer u afzonderlijke groepen alleen synchroniseert wanneer u een abonnement voor een gebruikerslidmaatschap synchroniseert.</td>
  </tr>
  <tr>
   <td><strong>Vervaltijd groep</strong></td>
   <td>Duur tot een gesynchroniseerde groep verloopt.</td>
  </tr>
  <tr>
   <td><strong>Automatisch lidmaatschap groeperen</strong></td>
   <td>Lijst met groepen waaraan een gesynchroniseerde groep automatisch wordt toegevoegd.</td>
  </tr>
  <tr>
   <td><strong>Groepseigenschappen toewijzen</strong></td>
   <td>Lijsttoewijzingsdefinitie van lokale eigenschappen van externe eigenschappen.</td>
  </tr>
  <tr>
   <td><strong>Groepspadvoorvoegsel</strong></td>
   <td>Het padvoorvoegsel dat wordt gebruikt bij het maken van nieuwe groepen.</td>
  </tr>
 </tbody>
</table>

## De externe aanmeldingsmodule {#the-external-login-module}

De externe aanmeldingsmodule bevindt zich onder **Apache Jackrabbit Oak External Login Module** onder de beheerconsole.

>[!NOTE]
>
>De Apache Jackrabbit Oak External Login Module implementeert de Java Authentication and Authorization Service (JAAS)-specificaties. Zie de [officiële Oracle Java Security Reference Guide](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jaas/JAASRefGuide.html) voor meer informatie.

Zijn baan moet bepalen welke Leverancier van de Identiteit en de Handler van de Synchronisatie aan gebruik, effectief binden de twee modules.

De volgende configuratieopties zijn beschikbaar:

| **JAAS Ranking** | Het specificeren van de rangschikking (d.w.z. sorteervolgorde) van deze login moduleingang. De items worden in aflopende volgorde gesorteerd (de configuraties met een hogere waarde worden het eerst gesorteerd). |
|---|---|
| **JAAS-besturingsmarkering** | Eigenschap die opgeeft of een LoginModule al dan niet VEREIST, VEREIST, VOLDOENDE of OPTIONAL.Raadpleeg de configuratiedocumentatie van JAAS voor meer details rond de betekenis van deze vlaggen. |
| **JAAS Realm** | De naam van het domein (of de toepassingsnaam) waartegen LoginModule wordt geregistreerd. Als geen domeinnaam wordt verstrekt dan wordt LoginModule geregistreerd met een standaarddomein zoals die in de configuratie van Felix JAAS wordt gevormd. |
| **Naam identiteitsprovider** | Naam van de identiteitsprovider. |
| **Naam synchronisatiehandler** | Naam van de synchronisatiehandler. |

>[!NOTE]
>
>Als u op het hebben van meer dan één configuratie LDAP met uw AEM instantie van plan bent, moeten de afzonderlijke Leveranciers van de Identiteit en de Managers van de Synchronisatie voor elke configuratie worden gecreeerd.

## LDAP configureren via SSL {#configure-ldap-over-ssl}

AEM 6 kan worden gevormd om met LDAP over SSL voor authentiek te verklaren door de hieronder procedure te volgen:

1. Schakel het selectievakje **SSL** of **TLS** gebruiken in wanneer u de [LDAP-identiteitsprovider](#configuring-the-ldap-identity-provider) configureert.
1. Configureer de synchronisatiehandler en de module Externe aanmelding naar wens.
1. Installeer indien nodig de SSL-certificaten in uw Java VM. Dit kan worden gedaan door keytool te gebruiken:

   `keytool -import -alias localCA -file <certificate location> -keystore <keystore location>`

1. Test de verbinding met de LDAP-server.

### SSL-certificaten maken {#creating-ssl-certificates}

Zelfondertekende certificaten kunnen worden gebruikt wanneer u AEM configureert voor verificatie met LDAP via SSL. Hieronder ziet u een voorbeeld van een werkprocedure voor het genereren van certificaten voor gebruik met AEM.

1. Zorg ervoor dat u een SSL-bibliotheek hebt geïnstalleerd en werkt. Bij deze procedure wordt OpenSSL als voorbeeld gebruikt.

1. Maak een aangepast cnf-bestand (OpenSSL Configuration). Dit kan worden gedaan door het standaard **openssl.cnf **configuratiedossier te kopiëren en het aan te passen. Bij UNIX-systemen bevindt de software zich gewoonlijk op `/usr/lib/ssl/openssl.cnf`

1. Ga aan het creëren van de wortelsleutel van CA door het hieronder bevel in een terminal in werking te stellen:

   ```
   openssl genpkey -algorithm [public key algorithm] -out certificatefile.key -pkeyopt [public key algorithm option]
   ```

1. Maak vervolgens een nieuw zelfondertekend certificaat:

   `openssl req -new -x509 -days [number of days for certification] -key certificatefile.key -out root-ca.crt -config CA/openssl.cnf`

1. Inspect het nieuwe certificaat om te controleren of alles in orde is:

   `openssl x509 -noout -text -in root-ca.crt`

1. Controleer of alle mappen die zijn opgegeven in het cnf-bestand (Certificate Configuration) bestaan. Als dat niet het geval is, maakt u ze.
1. Een willekeurig zaadje maken door bijvoorbeeld te draaien:

   `openssl rand -out private/.rand 8192`

1. Verplaats de gemaakte .pem-bestanden naar de locaties die in het .cnf-bestand zijn geconfigureerd.

1. Voeg ten slotte het certificaat toe aan het sleutelarchief van Java.

## Foutopsporingslogbestand {#enabling-debug-logging} inschakelen

Foutopsporingslogbestand kan worden ingeschakeld voor zowel de LDAP-identiteitsprovider als de externe aanmeldingsmodule om verbindingsproblemen op te lossen.

Om het registreren voor foutopsporing in te schakelen, moet u:

1. Ga naar de webbeheerconsole.
1. Zoek naar &quot;Apache Sling Logging Logger Configuration&quot; en maak twee loggers met de volgende opties:

* Logniveau: Foutopsporing
* Logbestand logs/ldap.log
* Berichtpatroon: {0,date,dd.MM.yyyy HH:mm:ss.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.security.authentication.ldap

* Logniveau: Foutopsporing
* Logbestand: logs/external.log
* Berichtpatroon: {0,date,dd.MM.yyyy HH:mm:ss.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.spi.security.authentication.external

## Een woord over groepsverbinding {#a-word-on-group-affiliation}

Gebruikers die via LDAP zijn gesynchroniseerd, kunnen deel uitmaken van verschillende groepen in AEM. Deze groepen kunnen externe LDAP-groepen zijn die als onderdeel van het synchronisatieproces aan AEM worden toegevoegd, maar het kunnen ook groepen zijn die afzonderlijk worden toegevoegd en geen deel uitmaken van het oorspronkelijke LDAP-groepsverbindingsschema.

In de meeste gevallen, kunnen deze groepen zijn die door een lokale AEM beheerder of door een andere identiteitsleverancier worden toegevoegd.

Als een gebruiker uit een groep op de LDAP-server wordt verwijderd, wordt de wijziging ook aan de AEM kant doorgevoerd bij synchronisatie. Alle andere groepsrelaties van de gebruiker die niet door LDAP zijn toegevoegd, blijven echter wel van kracht.

AEM detecteert en handelt de verwijdering van gebruikers uit externe groepen af door gebruik te maken van de eigenschap `rep:externalId`. Dit bezit wordt automatisch toegevoegd aan om het even welke gebruiker of groep die door de Handler van de Synchronisatie wordt gesynchroniseerd en het bevat informatie over de voortkomende identiteitsleverancier.

Raadpleeg de documentatie bij Apache Oak over [Synchronisatie van gebruikers en groepen](https://jackrabbit.apache.org/oak/docs/security/authentication/usersync.html) voor meer informatie.

## Bekende problemen {#known-issues}

Als u LDAP wilt gebruiken via SSL, moet u ervoor zorgen dat de certificaten die u gebruikt, worden gemaakt zonder de Netscape-opmerkingsoptie. Als deze optie is ingeschakeld, mislukt de verificatie met een SSL Handshake-fout.

