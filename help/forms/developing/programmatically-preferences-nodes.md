---
title: Het programmatisch beheren van PreferencesNodes
seo-title: Het programmatisch beheren van PreferencesNodes
description: 'null'
seo-description: 'null'
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# De knooppunten van de voorkeuren programmatisch beheren {#programmatically-managing-the-preferencesnodes}

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Voorkeur (Java) kunt gebruiken om de Knoop van de Voorkeur programmatically te beheren.

U kunt configuratie-instellingen handmatig wijzigen via de gebruikersinterface van de beheerder. Navigeer naar `Home>Settings>User Management> Configuration>Manual Configuration` om de opties te wijzigen. Importeer `config.xml` nadat u de wijzigingen hebt aangebracht, zullen alle wijzigingen verloren gaan, behalve wijzigingen die op het knooppunt `/Adobe/Adobe Experience Manager Forms/Config/UM persist` zijn aangebracht. In het voorbeeld van het importeren en exporteren van gebruikersbeheer wordt het wijzigen van configuratie-instellingen voor andere componenten niet ondersteund. Deze wijzigingen kunnen nu worden aangebracht met API&#39;s van `PreferencesManagerServiceClient`.

**Overzicht van** stappenVoer de volgende stappen uit om de knooppunten van Voorkeuren programmatisch te beheren:

1. Inclusief projectbestanden.
1. Een PreferencesManagerService-client maken
1. De juiste rol- of machtigingsbewerkingen aanroepen

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een PreferencesManagerService-client maken**

Alvorens u een verrichting van PreferencesManagerService van het Beheer van de Gebruiker programmatically kunt uitvoeren, moet u een cliënt tot stand brengen PreferencesManagerService. Met de Java API wordt dit verwezenlijkt door een voorwerp te creëren PreferencesManagerServiceClient.

**De juiste rol- of machtigingsbewerkingen aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de verrichtingen van de Manager van de Voorkeur dan aanhalen. De de dienstcliënt staat u toe om toestemmingen te lezen en te plaatsen.
