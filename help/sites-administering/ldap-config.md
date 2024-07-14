---
title: LDAP configureren met AEM 6
description: Leer om de diensten LDAP met AEM te gebruiken en te vormen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 2ebca4fb-20f7-499c-96a0-4018eaeddc1a
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 0%

---

# LDAP configureren met AEM 6 {#configuring-ldap-with-aem}

LDAP (het **juiste** D **directe** A **toegang** P **protocol) wordt gebruikt voor de toegang tot van de gecentraliseerde indexdiensten.** Het helpt de inspanning te verminderen die wordt vereist om gebruikersrekeningen te beheren aangezien zij door veelvoudige toepassingen kunnen worden betreden. Een dergelijke LDAP-server is Active Directory. LDAP wordt vaak gebruikt om Single Sign On te bereiken, waardoor een gebruiker toegang heeft tot meerdere toepassingen nadat hij zich eenmaal heeft aangemeld.

Gebruikersaccounts kunnen worden gesynchroniseerd tussen de LDAP-server en de gegevensopslagruimte, waarbij de gegevens van de LDAP-account worden opgeslagen in de gegevensopslagruimte. Met deze functionaliteit kunnen de accounts worden toegewezen aan groepen in de opslagplaats voor het toewijzen van de vereiste machtigingen en bevoegdheden.

De gegevensopslagruimte gebruikt LDAP-verificatie om dergelijke gebruikers te verifiëren, waarbij referenties worden doorgegeven aan de LDAP-server voor validatie, wat vereist is voordat toegang tot de gegevensopslagruimte wordt toegestaan. Om de prestaties te verbeteren, kunnen gevalideerde gegevens door de opslagplaats in cache worden opgeslagen, met een vervaltijd om ervoor te zorgen dat de validatie na een geschikte periode wordt uitgevoerd.

Wanneer een account wordt verwijderd van de LDAP-server, wordt de validatie niet meer verleend en wordt de toegang tot de gegevensopslagruimte geweigerd. Details van LDAP-accounts die in de opslagplaats zijn opgeslagen, kunnen ook worden gewist.

Het gebruik van dergelijke accounts is transparant voor uw gebruikers. Dat wil zeggen dat ze geen verschil zien tussen gebruikers- en groepsaccounts die met LDAP zijn gemaakt, en accounts die alleen in de opslagplaats zijn gemaakt.

In AEM 6 wordt bij LDAP-ondersteuning een nieuwe implementatie geleverd waarvoor een ander type configuratie is vereist dan bij eerdere versies.

Alle configuraties LDAP zijn nu beschikbaar als configuraties OSGi. Zij kunnen via de console van het Beheer van het Web in worden gevormd:
`https://serveraddress:4502/system/console/configMgr`

Om LDAP te hebben werkend met AEM, moet u drie configuraties tot stand brengen OSGi:

1. Een LDAP Identity Provider (IDP).
1. Een synchronisatiehandler.
1. Een externe aanmeldingsmodule.

>[!NOTE]
>
>Controle [ de Externe Login Module van Oak - voor authentiek verklaren met LDAP en voorbij ](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-oak-external-login-module-authenticating-with-ldap-and-beyond.html) om Externe Login Modules te duiken.
>
>Om een voorbeeld te lezen van het vormen van Experience Manager met Apache DS, zie [ het Vormen Adobe Experience Manager 6.5 om de Dienst van de Folder te gebruiken Apache.](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/configuring-adobe-experience-manager-6-to-use-apache-directory/m-p/183805)

## De LDAP-identiteitsprovider configureren {#configuring-the-ldap-identity-provider}

De LDAP-identiteitsprovider wordt gebruikt om te definiëren hoe gebruikers worden opgehaald van de LDAP-server.

Het kan in de beheersconsole onder **worden gevonden Apache Jackrabbit Oak LDAP de naam van de Identiteitsleverancier**.

De volgende configuratieopties zijn beschikbaar voor de LDAP Identiteitsprovider:

<table>
 <tbody>
  <tr>
   <td><strong>Naam LDAP-provider</strong></td>
   <td>Naam van deze LDAP-providerconfiguratie.</td>
  </tr>
  <tr>
   <td><strong> gastheer LDAP van de Server </strong><br /> </td>
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
   <td>DN van de gebruiker voor verificatie. Als dit veld leeg blijft, wordt een anonieme binding uitgevoerd.</td>
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
   <td>Extra LDAP-filter bij het zoeken naar gebruikers. Het laatste filter heeft de notatie: '(&amp;(&lt;idAttr&gt;=&lt;userId&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)' (user.extraFilter)</td>
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
   <td>Extra LDAP-filter bij het zoeken naar groepen. Het laatste filter wordt opgemaakt als: '(&amp;(&lt;nameAttr&gt;=&lt;groupName&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)'</td>
  </tr>
  <tr>
   <td><strong>DN-paden groeperen</strong></td>
   <td>Bepaalt of de DN moet worden gebruikt voor het berekenen van een gedeelte van het tussenliggende pad.</td>
  </tr>
  <tr>
   <td><strong>Kenmerk groepslid</strong></td>
   <td>Groepattribuut dat een of meer leden van een groep bevat.</td>
  </tr>
 </tbody>
</table>

## Synchronisatie-handler configureren {#configuring-the-synchronization-handler}

De synchronisatiehandler definieert hoe de gebruikers en groepen van Identiteitsproviders worden gesynchroniseerd met de gegevensopslagruimte.

Het wordt gevestigd onder **Apache Jackrabbit Oak de naam van de Handler van de Standaard van de Synchronisatie** in de beheersconsole.

De volgende configuratieopties zijn beschikbaar voor de Synchronisatie-handler:

<table>
 <tbody>
  <tr>
   <td><strong>Naam synchronisatiehandler</strong></td>
   <td>Naam van de sync-configuratie.</td>
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
   <td>List-mapping definitie van lokale eigenschappen van externe eigenschappen.</td>
  </tr>
  <tr>
   <td><strong>Voorvoegsel gebruikerspad</strong></td>
   <td>Het padvoorvoegsel dat wordt gebruikt bij het maken van gebruikers.</td>
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
   <td>List-mapping definitie van lokale eigenschappen van externe eigenschappen.</td>
  </tr>
  <tr>
   <td><strong>Groepspadvoorvoegsel</strong></td>
   <td>Het padvoorvoegsel dat wordt gebruikt bij het maken van groepen.</td>
  </tr>
 </tbody>
</table>

## De externe aanmeldingsmodule {#the-external-login-module}

De externe login module wordt gevestigd onder **Apache Jackrabbit Oak Externe Login Module** onder de beheersconsole.

>[!NOTE]
>
>De Apache Jackrabbit Oak External Login Module implementeert de Java™ Authentication and Authorization Servi (JAAS)-specificaties. Zie de [ officiële Gids van de Verwijzing van de Veiligheid Java™ van het Oracle ](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jaas/JAASRefGuide.html) voor meer informatie.

Zijn baan moet bepalen welke Leverancier van de Identiteit en de Handler van de Synchronisatie aan gebruik, effectief binden de twee modules.

De volgende configuratieopties zijn beschikbaar:

| **JAAS Rangschikkend** | Het specificeren van het rangschikken (namelijk, soortorde) van deze login moduleingang. De items worden in aflopende volgorde gesorteerd (dat wil zeggen dat configuraties met een hogere waarde het eerst komen). |
|---|---|
| **Vlag van de Controle JAAS** | Eigenschap die aangeeft of een LoginModule VEREIST, VEREIST, VOLDOENDE of OPTIONEEL is. Zie de configuratiedocumentatie van JAAS voor meer details rond de betekenis van deze vlaggen. |
| **JAAS Realm** | De naam van het domein (of de toepassingsnaam) waartegen LoginModule wordt geregistreerd. Als geen domeinnaam wordt verstrekt, dan wordt LoginModule geregistreerd met een standaarddomein zoals die in de configuratie van Felix JAAS wordt gevormd. |
| **Naam van de Identiteitsprovider** | Naam van de identiteitsprovider. |
| **Naam van de Handler van de Synchronisatie** | Naam van de synchronisatiehandler. |

>[!NOTE]
>
>Als u op het hebben van meer dan één configuratie LDAP met uw AEM instantie van plan bent, moeten de afzonderlijke Leveranciers van de Identiteit en de Managers van de Synchronisatie voor elke configuratie worden gecreeerd.

## LDAP configureren via SSL {#configure-ldap-over-ssl}

AEM 6 kan worden gevormd om met LDAP over SSL voor authentiek te verklaren door de hieronder procedure te volgen:

1. Controle het **SSL van het Gebruik** of **gebruiken TLS** checkboxes wanneer het vormen van de [ LDAP Identiteitsleverancier ](#configuring-the-ldap-identity-provider).
1. Configureer de synchronisatiehandler en de module Externe aanmelding naar wens.
1. Installeer indien nodig de SSL-certificaten in uw Java™ VM. U kunt deze installatie uitvoeren met behulp van het hulpprogramma:

   `keytool -import -alias localCA -file <certificate location> -keystore <keystore location>`

1. Test de verbinding met de LDAP-server.

### SSL-certificaten maken {#creating-ssl-certificates}

Zelfondertekende certificaten kunnen worden gebruikt bij het configureren van AEM voor verificatie met LDAP via SSL. Hieronder ziet u een voorbeeld van een werkprocedure voor het genereren van certificaten voor gebruik met AEM.

1. Zorg ervoor dat u een SSL-bibliotheek hebt geïnstalleerd en werkt. Bij deze procedure wordt OpenSSL als voorbeeld gebruikt.

1. Maak een aangepast cnf-bestand (OpenSSL Configuration). Deze configuratie kan worden gedaan door het standaard **openssl.cnf **configuratiedossier te kopiëren en het aan te passen. Op UNIX®-systemen staat deze op `/usr/lib/ssl/openssl.cnf`

1. Ga aan het creëren van de wortelsleutel van CA door het hieronder bevel in een terminal in werking te stellen:

   ```
   openssl genpkey -algorithm [public key algorithm] -out certificatefile.key -pkeyopt [public key algorithm option]
   ```

1. Maak vervolgens een zelfondertekend certificaat:

   `openssl req -new -x509 -days [number of days for certification] -key certificatefile.key -out root-ca.crt -config CA/openssl.cnf`

1. Om ervoor te zorgen dat alles in orde is, inspecteer het onlangs geproduceerde certificaat:

   `openssl x509 -noout -text -in root-ca.crt`

1. Controleer of alle mappen die zijn opgegeven in het cnf-bestand (Certificate Configuration) bestaan. Als dat niet het geval is, maakt u ze.
1. Een willekeurig zaadje maken door bijvoorbeeld te draaien:

   `openssl rand -out private/.rand 8192`

1. Verplaats de gemaakte .pem-bestanden naar de locaties die in het .cnf-bestand zijn geconfigureerd.

1. Voeg ten slotte het certificaat toe aan het Java™ sleutelarchief.

## Foutopsporingsregistratie inschakelen {#enabling-debug-logging}

Foutopsporingslogbestand kan worden ingeschakeld voor zowel de LDAP-identiteitsprovider als de externe aanmeldingsmodule om verbindingsproblemen op te lossen.

Om te toelaten zuivert registreren, moet u het volgende doen:

1. Ga naar de webbeheerconsole.
1. Zoek naar &quot;Apache Sling Logging Logger Configuration&quot; en maak twee loggers met de volgende opties:

* Logniveau: Foutopsporing
* Logbestand logs/ldap.log
* Berichtpatroon: {0,date,`dd.MM.yyyy` `HH:mm:ss.SSS` &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.security.authentication.ldap

* Logniveau: Foutopsporing
* Logbestand: logs/external.log
* Berichtpatroon: {0,date,`dd.MM.yyyy` `HH:mm:ss.SSS` &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.spi.security.authentication.external

## Een woord over groepsverbinding {#a-word-on-group-affiliation}

Gebruikers die via LDAP zijn gesynchroniseerd, kunnen deel uitmaken van verschillende groepen in AEM. Deze groepen kunnen externe LDAP-groepen zijn die als onderdeel van het synchronisatieproces aan AEM worden toegevoegd. Ze kunnen echter ook groepen zijn die afzonderlijk worden toegevoegd en geen deel uitmaken van het oorspronkelijke LDAP-groepslidmaatschapsschema.

Gewoonlijk worden deze groepen toegevoegd door een lokale AEM beheerder of door een andere identiteitsprovider.

Als een gebruiker wordt verwijderd uit een groep op de LDAP-server, wordt de wijziging tijdens de synchronisatie weerspiegeld aan de AEM kant. Alle andere groepsrelaties van de gebruiker die niet door LDAP zijn toegevoegd, blijven echter van kracht.

AEM detecteert en verwerkt het leegmaken van gebruikers van externe groepen met behulp van de eigenschap `rep:externalId` . Dit bezit wordt automatisch toegevoegd aan om het even welke gebruiker of groep die door de Handler van de Synchronisatie wordt gesynchroniseerd en het bevat informatie over de voortkomende identiteitsleverancier.

Zie de documentatie van Apache Oak op [ de Synchronisatie van de Gebruiker en van de Groep ](https://jackrabbit.apache.org/oak/docs/security/authentication/usersync.html).

## Bekende problemen {#known-issues}

Als u LDAP wilt gebruiken via SSL, moet u ervoor zorgen dat de certificaten die u gebruikt, worden gemaakt zonder de Netscape-commentaaroptie. Als deze optie is ingeschakeld, mislukt de verificatie met een SSL Handshake-fout.
