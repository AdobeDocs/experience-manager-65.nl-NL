---
title: Logboekregistratie
seo-title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
seo-description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
uuid: 8c9e3628-2f2c-445d-9706-5c7725b85fe2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 5aa69b10-2cd0-4d34-8104-8c3b88405926
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Logboekregistratie{#logging}

AEM biedt u de mogelijkheid om te vormen:

* globale parameters voor de centrale houtkapdienst
* verzoeken om registratie van gegevens; een gespecialiseerde registrerenconfiguratie voor verzoekinformatie
* specifieke instellingen voor de afzonderlijke diensten; bijvoorbeeld een afzonderlijk logbestand en een indeling voor de logberichten

Dit zijn allemaal [OSGi configuraties](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Aanmelden bij AEM is gebaseerd op verkoopbeginselen. Zie Logboekregistratie [](https://sling.apache.org/site/logging.html) voor meer informatie.

## Globale logboekregistratie {#global-logging}

[Apache Sling Logging Configuration](/help/sites-deploying/osgi-configuration-settings.md) wordt gebruikt om het hoofdlogger te configureren. Hiermee worden de algemene instellingen voor het aanmelden bij AEM gedefinieerd:

* het registratieniveau
* de locatie van het centrale logbestand
* het aantal versies dat moet worden bewaard
* versierotatie; of maximumgrootte of een tijdinterval
* de indeling die moet worden gebruikt bij het schrijven van de logberichten

>[!NOTE]
>
>Dit artikel [van de](https://helpx.adobe.com/experience-manager/kb/HowToRotateRequestAndAccessLog.html) Kennisbank verklaart hoe te om de request.log en access.log dossiers te roteren.

## Loggers en schrijvers voor de Individuele Diensten {#loggers-and-writers-for-individual-services}

Naast de globale registrerenmontages, staat AEM u toe om specifieke montages voor de individuele dienst te vormen:

* het specifieke registratieniveau
* de locatie van het individuele logbestand
* het aantal versies dat moet worden bewaard
* versierotatie; of maximumgrootte of tijdinterval
* de indeling die moet worden gebruikt bij het schrijven van de logberichten
* de registreermachine (de dienst OSGi die de logboekberichten levert)

Dit staat u toe om logboekberichten voor één enkele dienst in een afzonderlijk dossier te kanaliseren. Dit kan met name nuttig zijn tijdens de ontwikkeling of het testen; bijvoorbeeld, wanneer u een verhoogd logboekniveau voor de specifieke dienst nodig hebt.

AEM gebruikt het volgende om logboekberichten aan dossier te schrijven:

1. Een **dienst** OSGi (registreerder) schrijft een logboekbericht.
1. Een **Logging Logger** neemt dit bericht en formatteert het volgens uw specificatie.
1. Een **Logging Schrijver** schrijft al deze berichten aan het fysieke dossier dat u hebt bepaald.

Deze elementen zijn gekoppeld aan de volgende parameters voor de desbetreffende elementen:

* **Logger (Logging Logger)**

   Definieer de service(s) die de berichten genereren.

* **Logbestand (Logging Logger)**

   Bepaal het fysieke dossier voor het opslaan van de logboekberichten.

   Dit wordt gebruikt om een Logging Logger met een het Registreren Schrijver te verbinden. De waarde moet aan de zelfde parameter in de Logging configuratie van de Schrijver identiek zijn om de verbinding te maken.

* **Logbestand (logboekschrijver)**

   Definieer het fysieke bestand waarnaar de logberichten worden geschreven.

   Dit moet gelijk zijn aan dezelfde parameter in de configuratie van Logging Writer, anders wordt de overeenkomst niet gemaakt. Als er geen gelijke is dan zal een impliciete Schrijver met standaardconfiguratie (dagelijkse logboekomwenteling) worden gecreeerd.

### Standaardloggers en -schrijvers {#standard-loggers-and-writers}

Bepaalde Loggers en Schrijvers zijn inbegrepen in een standaardAEM installatie.

Het eerste is een speciaal geval aangezien het zowel de `request.log` als `access.log` dossiers controleert:

* De logboekregistratie:

   * Apache Sling Aanpasbaar Data Logger Aanvraag

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Schrijf berichten over aanvraaginhoud aan `request.log`.

* Koppelingen naar:

   * Apache Sling Request Logger

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Schrijft de berichten naar of `request.log` of `access.log`.

Deze kunnen indien nodig worden aangepast, hoewel de standaardconfiguratie geschikt is voor de meeste installaties.

De andere paren volgen de standaardconfiguratie:

* De logboekregistratie:

   * Logboekconfiguratie Apache Sling Logging

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Schrijft `Information` berichten naar `logs/error.log`.

* Koppelingen naar de schrijver:

   * Configuratie van auteur van Apache Sling Logging

      (org.apache.sling.commons.log.LogManager.factory.writer)

* De logboekregistratie:

   * Apache Sling Logging Logger Configuration(org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Schrijft `Warning` berichten aan `../logs/error.log` voor de dienst `org.apache.pdfbox`.

* Koppelt niet aan een specifieke schrijver, zodat er een impliciete schrijver met standaardconfiguratie (dagelijkse logrotatie) wordt gemaakt en gebruikt.

### Uw eigen registreerapparaten en schrijvers maken {#creating-your-own-loggers-and-writers}

U kunt uw eigen registreerapparaat/schrijfpaar definiëren:

1. Maak een nieuwe instantie van de configuratie- [Apache Sling Logging Logger](/help/sites-deploying/osgi-configuration-settings.md)van de Fabriek.

   1. Geef het logbestand op.
   1. Geef de logboekregistratie op.
   1. Configureer de overige parameters naar wens.

1. Maak een nieuw exemplaar van de Configuratie [Apache Sling Logging Writer Configuration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geef het logbestand op. Dit moet overeenkomen met het logbestand dat is opgegeven voor de gebruiker.
   1. Configureer de overige parameters naar wens.

>[!NOTE]
>
>In bepaalde omstandigheden wilt u mogelijk een [aangepast logbestand](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file)maken.

