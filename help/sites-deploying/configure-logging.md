---
title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: b32001a1-0078-43f6-89d6-781d6d2e9c94
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---

# Logboekregistratie{#logging}

AEM biedt u de mogelijkheid om te vormen:

* globale parameters voor de centrale houtkapdienst
* verzoek gegevensregistreren; een gespecialiseerde registrerenconfiguratie voor verzoekinformatie
* specifieke instellingen voor de afzonderlijke services, bijvoorbeeld een afzonderlijk logbestand en een indeling voor de logberichten

Dit zijn allemaal [OSGi-configuraties](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Aanmelden in AEM is gebaseerd op verkoopbeginselen. Zie [Logboekregistratie voor verkoop](https://sling.apache.org/site/logging.html) voor nadere informatie.

## Globale logboekregistratie {#global-logging}

[Configuratie van Apache Sling-logboekregistratie](/help/sites-deploying/osgi-configuration-settings.md) wordt gebruikt om het wortelregistreerapparaat te vormen. Hiermee worden de algemene instellingen voor het aanmelden van AEM gedefinieerd:

* het registratieniveau
* de locatie van het centrale logbestand
* het aantal versies dat moet worden bewaard
* versieomwenteling; of maximumgrootte of een tijdinterval
* de indeling die moet worden gebruikt bij het schrijven van de logberichten

>[!NOTE]
>
>Dit [Kennisbank, artikel](https://helpx.adobe.com/experience-manager/kb/HowToRotateRequestAndAccessLog.html) verklaart hoe te om de request.log en access.log dossiers te roteren.

## Loggers en schrijvers voor de Individuele Diensten {#loggers-and-writers-for-individual-services}

Naast de globale registrerenmontages, AEM kunt u specifieke montages voor de individuele dienst vormen:

* het specifieke registratieniveau
* de locatie van het individuele logbestand
* het aantal versies dat moet worden bewaard
* versieomwenteling; of maximumgrootte of het tijdinterval
* de indeling die moet worden gebruikt bij het schrijven van de logberichten
* de registreermachine (de dienst OSGi die de logboekberichten levert)

Dit laat u logboekberichten voor één enkele dienst in een afzonderlijk dossier kanaliseren. Dit kan bijzonder nuttig tijdens ontwikkeling of het testen zijn; bijvoorbeeld, wanneer u een verhoogd logboekniveau voor de specifieke dienst nodig hebt.

AEM gebruikt het volgende om logberichten naar bestand te schrijven:

1. An **OSGi-service** (logger) schrijft een logboekbericht.
1. A **Logboekregistratie** neemt dit bericht en formatteert het volgens uw specificatie.
1. A **Logboekschrijver** schrijft al deze berichten aan het fysieke dossier dat u hebt bepaald.

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

Bepaalde loggers en schrijvers zijn opgenomen in een standaard AEM installatie.

Het eerste is een speciaal geval omdat het zowel de `request.log` en `access.log` bestanden:

* De logboekregistratie:

   * Apache Sling Aanpasbaar Data Logger Aanvraag

     (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Berichten schrijven over aanvraaginhoud aan `request.log`.

* Koppelingen naar:

   * Apache Sling Request Logger

     (org.apache.sling.engine.impl.log.RequestLogger)

   * Schrijft de berichten naar of `request.log` of `access.log`.

Deze kunnen indien nodig worden aangepast, hoewel de standaardconfiguratie geschikt is voor de meeste installaties.

De andere paren volgen de standaardconfiguratie:

* De logboekregistratie:

   * Logboekconfiguratie Apache Sling Logging

     (org.apache.sling.commons.log.LogManager.factory.config)

   * Schrijven `Information` berichten aan `logs/error.log`.

* Koppelingen naar de schrijver:

   * Configuratie van auteur van Apache Sling Logging

     (org.apache.sling.commons.log.LogManager.factory.writer)

* De logboekregistratie:

   * Configuratie van Apache Sling Logging Logger (org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Schrijven `Warning` berichten aan `../logs/error.log` voor de dienst `org.apache.pdfbox`.

* Koppelt niet aan een specifieke schrijver, zodat er een impliciete schrijver met standaardconfiguratie (dagelijkse logrotatie) wordt gemaakt en gebruikt.

### Uw eigen registreerapparaten en schrijvers maken {#creating-your-own-loggers-and-writers}

U kunt uw eigen registreerapparaat/schrijfpaar definiëren:

1. Creeer een geval van de Configuratie van de Fabriek [Logboekconfiguratie Apache Sling Logging](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geef het logbestand op.
   1. Geef de logboekregistratie op.
   1. Configureer de overige parameters naar wens.

1. Creeer een geval van de Configuratie van de Fabriek [Configuratie van auteur van Apache Sling Logging](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geef het logbestand op. Dit moet overeenkomen met het logbestand dat is opgegeven voor de gebruiker.
   1. Configureer de overige parameters naar wens.

>[!NOTE]
>
>In bepaalde omstandigheden kunt u een [aangepast logbestand](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).
