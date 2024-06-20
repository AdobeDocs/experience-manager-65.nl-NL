---
title: Het programmatisch beheren van PreferencesNodes
description: Gebruik de API (Java) van de Dienst van de Manager van de Voorkeur om de Knooppunten van de Voorkeur programmatically te beheren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 108eb249-879b-4e4f-b431-8118b8656e62
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Het programmatisch beheren van de Knooppunten van de Voorkeur {#programmatically-managing-the-preferencesnodes}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Voorkeur (Java) kunt gebruiken om de Knoop van de Voorkeur programmatically te beheren.

U kunt configuratie-instellingen handmatig wijzigen via de gebruikersinterface van de beheerder. Als u de opties wilt wijzigen, navigeert u naar `Home>Settings>User Management> Configuration>Manual Configuration`. Importeren `config.xml` na het aanbrengen van de veranderingen, zou u merken dat alle veranderingen behalve veranderingen die bij knoop worden aangebracht `/Adobe/Adobe Experience Manager Forms/Config/UM persist` verloren gaan. In het voorbeeld van het importeren en exporteren van gebruikersbeheer wordt het wijzigen van configuratie-instellingen voor andere componenten niet ondersteund. Deze wijzigingen kunnen nu worden aangebracht met `PreferencesManagerServiceClient` API&#39;s.

**Overzicht van de stappen** Voer de volgende stappen uit om de knooppunten van Voorkeuren programmatisch te beheren:

1. Inclusief projectbestanden.
1. Een PreferencesManagerService-client maken
1. De juiste rol- of machtigingsbewerkingen aanroepen

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een PreferencesManagerService-client maken**

Alvorens u een verrichting van PreferencesManagerService van het Beheer van de Gebruiker programmatically kunt uitvoeren, moet u een cliënt tot stand brengen PreferencesManagerService. Met de Java API wordt dit verwezenlijkt door een voorwerp te creëren PreferencesManagerServiceClient.

**De juiste rol- of machtigingsbewerkingen aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de verrichtingen van de Manager van de Voorkeur dan aanhalen. Met de serviceclient kunt u machtigingen lezen en instellen.
