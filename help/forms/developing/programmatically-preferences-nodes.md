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
feature: Adaptive Forms,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---

# Het programmatisch beheren van de Knooppunten van de Voorkeur {#programmatically-managing-the-preferencesnodes}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Voorkeur (Java) kunt gebruiken om de Knoop van de Voorkeur programmatically te beheren.

U kunt configuratie-instellingen handmatig wijzigen via de gebruikersinterface van de beheerder. Navigeer naar `Home>Settings>User Management> Configuration>Manual Configuration` om de opties te wijzigen. Importeren `config.xml` nadat u de wijzigingen hebt aangebracht, gaan alle wijzigingen verloren, behalve de wijzigingen die op het knooppunt `/Adobe/Adobe Experience Manager Forms/Config/UM persist` zijn aangebracht. In het voorbeeld van het importeren en exporteren van gebruikersbeheer wordt het wijzigen van configuratie-instellingen voor andere componenten niet ondersteund. Deze wijzigingen kunnen nu worden aangebracht met API&#39;s van `PreferencesManagerServiceClient` .

**Samenvatting van stappen** programmatically om de Knoop van de Voorkeur te beheren, voer de volgende stappen uit:

1. Inclusief projectbestanden.
1. Een PreferencesManagerService-client maken
1. De juiste rol- of machtigingsbewerkingen aanroepen

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer een cliënt PreferencesManagerService**

Alvorens u een verrichting van PreferencesManagerService van het Beheer van de Gebruiker programmatically kunt uitvoeren, moet u een cliënt tot stand brengen PreferencesManagerService. Met de Java API wordt dit verwezenlijkt door een voorwerp te creëren PreferencesManagerServiceClient.

**voke de aangewezen rol of toestemmingsverrichtingen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de verrichtingen van de Manager van de Voorkeur dan aanhalen. Met de serviceclient kunt u machtigingen lezen en instellen.
