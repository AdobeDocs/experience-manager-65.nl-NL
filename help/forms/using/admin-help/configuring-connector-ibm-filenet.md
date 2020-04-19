---
title: Connector configureren voor IBM FileNet
seo-title: Connector configureren voor IBM FileNet
description: Leer hoe u de connector voor IBM FileNet configureert om communicatie tussen AEM-formulieren en IBM FileNet mogelijk te maken.
seo-description: Leer hoe u de connector voor IBM FileNet configureert om communicatie tussen AEM-formulieren en IBM FileNet mogelijk te maken.
uuid: 29d4e221-97f7-4cfb-b7e4-75a8289d2604
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: be4994de-12f8-436e-926a-49a6783b006e
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Connector configureren voor IBM FileNet {#configuring-connector-for-ibm-filenet}

Connector voor IBM FileNet maakt communicatie mogelijk tussen AEM-formulieren en IBM FileNet. Zie &quot;Connectors for ECM&quot; in [Services Reference](https://www.adobe.com/go/learn_aemforms_services_63)voor aanvullende achtergrondinformatie.

>[!NOTE]
>
>In eerdere versies konden activa worden opgeslagen in een ECM-opslagplaats. In deze versie worden de elementen opgeslagen in de oorspronkelijke opslagplaats voor AEM-formulieren en zijn de services van de Repository Provider afgekeurd. De migratie van elementen van een ECM-opslagplaats naar de AEM-formulieropslagplaats vindt plaats wanneer u een upgrade uitvoert naar AEM-formulieren. Zie de handleiding voor de upgrade van AEM-formulieren voor uw toepassingsserver voor meer informatie.

## De verbinding met de inhoudsengine configureren {#configure-the-connection-to-the-content-engine}

IBM FileNet P8 Content Engine biedt softwareservices voor het beheer van bedrijfsinhoud en door de klant gedefinieerde zakelijke objecten in opslagruimten voor FileNet-inhoud.

1. Klik in de beheerconsole op Services > Connector voor IBM FileNet.
1. Voer in het vak URL van de inhoudsengine de volledige verbindings-URL in. Bijvoorbeeld:

   Als u FileNet Content Engine 4.x gebruikt met CEWS-transport, voert u het volgende in:

   `cemp:https://ContentEngineHostNameorIP:port/wsi/FNCEWS40DIME?jaasConfigurationName=FileNetP8WSI`

   Als u FileNet Content Engine 4.x gebruikt met EJB-transport, dat alleen op WebLogic wordt ondersteund, voert u het volgende in:

   `cemp:t3://ContentEngineHostNameorIP:port/FileNet/Engine?jaasConfigurationName=FileNetP8Engine`

1. Selecteer een van de volgende beveiligingsniveaus in de lijst Referentiebeschermingsregeling:

   * **Wissen:** Verzendt gegevens in een niet-beveiligde modus via het netwerk
   * **Symmetrisch:** Verzendt gecodeerde gegevens via het netwerk

1. Voer in het vak Locatie van versleutelingsbestand het pad naar het versleutelingsbestand in:

   * Als u Wissen hebt geselecteerd als de regeling voor bescherming tegen referentie, worden dit trefwoord en de bijbehorende waarde genegeerd.
   * Als u Symmetrisch hebt geselecteerd als de regeling voor bescherming van referenties, verwijst het pad dat u invoert naar de locatie van een versleutelingsbestand op de formulierserver dat de te gebruiken cryptografische sleutels bevat.

1. Voer in het vak Standaardobjectarchief de opslagconnector in van het object waarmee AEM-formulieren standaard verbinding maken.
1. Voer in het vak Gebruikersnaam de gebruikersnaam in van een gebruiker die toegangsrechten heeft tot de standaardobberwinkel die u in de vorige stap hebt opgegeven.
1. Voer in het vak Wachtwoord het wachtwoord voor de gebruiker in en klik op Opslaan.

## De instellingen van de procesengine configureren {#configure-the-process-engine-settings}

De connector voor IBM FileNet bevat de Process Engine Connector voor de IBM FileNet-service, die wordt gebruikt voor interactie met de IBM FileNet Process Engine. U kunt instellingen voor deze service configureren.

1. Klik in de beheerconsole op Services > Connector voor IBM FileNet.
1. Om het gebruik van de Schakelaar van de Motor van het Proces voor de dienst van IBM FileNet toe te laten, de uitgezochte Dienst van de Schakelaar van de Motor van het Proces van het Gebruik.
1. In het vakje van de Router van het Proces/van het Punt, ga de gastheernaam of IP adres en havenaantal in dat door de naam van de procesrouter wordt gevolgd. Bijvoorbeeld:

   `rmi://ProcessEngineHostNameorIP:port/Name`

1. In het vakje van de Naam van de Gebruiker, ga de gebruikersnaam in die wordt gebruikt om met de procesmotor te verbinden.
1. Voer in het vak Wachtwoord het wachtwoord in dat wordt gebruikt om verbinding te maken met de procesengine en klik op Opslaan.

## Validatie van service-instellingen {#validation-of-service-settings}

Als u een onjuiste gebruikersnaam of wachtwoord invoert wanneer u de verbinding met de Content Engine of de instellingen van de procesengine configureert, krijgt u de volgende resultaten, afhankelijk van of de services momenteel worden uitgevoerd:

* Als zowel de dienst van de Leverancier van de Bewaarplaats voor IBM FileNet als de Schakelaar van de Bewaarplaats van de Inhoud voor de dienst van IBM FileNet worden tegengehouden, wanneer u sparen de informatie van de de dienstconfiguratie, geen fout verschijnt. Nochtans, de volgende tijd u de dienst begint, zal een uitzondering worden geworpen en de dienst zal niet beginnen.
* Als of de dienst van de Leverancier van de Bewaarplaats voor IBM FileNet of de Verbinding van de Bewaarplaats van de Inhoud voor de dienst van IBM FileNet begonnen zijn, wanneer u sparen de informatie van de de dienstconfiguratie, probeert de dienst om de referentie informatie onmiddellijk te bevestigen. In dit geval treedt een fout op en worden de configuratiegegevens niet opgeslagen.

## De provider van de dataopslagservice wijzigen {#change-the-repository-service-provider}

U kunt configureren welke serviceprovider voor gegevensopslag moet worden gebruikt met FileNet. De de dienstvraag van de bewaarplaats wordt gedelegeerd aan de leverancier u vormt.

De volgende opties zijn beschikbaar:

**Huidige naam leverancier van opslagplaats:** De naam van de huidige aanbieder van datadiensten

**IBM FileNet Repository Provider:** Maakt van de aanbieder van de FileNet-opslagplaats de provider voor de opslagplaats. Deze optie is vervangen.

**aanbieder opslagplaats:** Maakt van de native opslagprovider de provider voor de opslagplaats

>[!NOTE]
>
>Als u een andere opslagplaats-serviceprovider wilt selecteren dan de vermelde, configureert u RepositoryService in Toepassingen en Services. <!-- Fix broken link(See Managing Services) -->

1. Klik in de beheerconsole op Services > Connector voor IBM FileNet.
1. Selecteer in het gebied Providergegevens voor opslagplaats de andere opslagplaats en klik op Opslaan.
