---
title: Introductie van Java API QuickStart
seo-title: Introductie van Java API QuickStart
description: 'null'
seo-description: 'null'
uuid: 480e1809-f789-4ad8-b5d5-2d97aba8411a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools
discoiquuid: 38fd51ec-347e-4ae3-86d4-9d2429f79bdd
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Introductie van Java API Snel starten {#introducing-java-api-quickstart}

Met de Adobe AEM Forms API Quick Start kunt u sneller programma&#39;s ontwikkelen die met de services van de AEM Forms werken. *Snel* starten zijn volledige programma&#39;s die u kunt kopiëren en plakken in uw eigen projecten en als uitgangspunt kunt gebruiken. U kunt een Snel Begin in werking stellen om te zien hoe het zich gedraagt en het voor uw eigen behoeften wijzigt.

De verrichtingen van AEM Forms kunnen worden uitgevoerd gebruikend AEM Forms sterk-getypte API en de verbindingswijze zou aan ZEEP moeten worden geplaatst.

Quick Start van de API voor sterk getypte Java bevat een lijst met JAR-bestanden die vereist zijn om de Java-toepassing uit te voeren. De meeste Java Quick Starts zijn consoletoepassing die binnen loopt `main`. De snel aan de slag zijnde API van Forms Java is echter sterk getypt en is geïmplementeerd als Java servlet die wordt uitgevoerd in een webtoepassing.

De lijst met JAR-bestanden bevindt zich in een opmerkingssectie aan het begin van het snelstarten. De volgende opmerking bevindt zich bijvoorbeeld in een functie voor het snel starten van een uitvoer en is een typische JAR-bestandenlijst die wordt weergegeven in elke Java Quick Start.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-output-client.jar
     * 2. adobe--client.jar
     * 3. adobe-usermanager-client.jar
     *
     * These JAR files are located in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/common
     *
     * The adobe-utilities.jar file is located in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/jboss
     *
     * The jboss-client.jar file is located in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/jboss/bin/client
     *
     * If you want to invoke a remote AEM Forms instance and there is a
     * firewall between the client application and AEM Forms, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files located in the following
     * path
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms library files" in Programming
     * with AEM Forms
     */
```

## Meerdere services snel aan de slag {#multiple-services-quick-start}

De meeste Snelle Begint die in *Programmering met AEM Forms op JEE* wordt gevestigd roepen de specifieke dienst aan om een verrichting uit te voeren. Nochtans, roepen sommige Snel Begint veelvoudige diensten van AEM Forms aan om een bepaalde werkschema uit te voeren. In de volgende lijst vindt u een snelle start van Java waarbij meerdere AEM Forms worden aangeroepen:

[Snel starten (SOAP-modus): Een document in de gegevensopslagruimte van AEM Forms doorgeven aan de uitvoerservice met behulp van de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (hiermee wordt de gegevensopslagruimte en de uitvoerservice aangeroepen)

[Snel starten (SOAP-modus): Een PDF-document maken op basis van fragmenten met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (hiermee wordt de Assembler- en Output-service geactiveerd)

[Snel starten (SOAP-modus): PDF-documenten maken met verzonden XML-gegevens met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (roept de service Formulieren, Uitvoer en Documentbeheer aan)

[Snel starten (SOAP-modus): Documenten doorgeven aan de Forms Service met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (hiermee wordt de service Formulieren en documentbeheer aangeroepen)

[Snel starten (SOAP-modus): Een op XFA gebaseerd formulier digitaal ondertekenen met de Java API](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (hiermee wordt de service Formulieren en handtekening aangeroepen)

[Snel starten (SOAP-modus): Rollen en machtigingen beheren met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) (roept DirectoryManager en de AuthorizationManager-service aan)

[Snel starten (SOAP-modus): Documenten doorgeven aan de uitvoerservice met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) (de service Uitvoer en Documentbeheer aanroepen)

>[!NOTE]
>
>De snelle Begin die in Programmering met AEM Forms wordt gevestigd is gebaseerd op AEM Forms die op de Server van de Toepassing JBoss® en het werkende systeem van Microsoft® Windows® worden opgesteld. Als u echter een ander besturingssysteem gebruikt, zoals UNIX®, vervangt u Windows-specifieke paden door paden die door het desbetreffende besturingssysteem worden ondersteund. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>De meeste van de Webdienst Snel Begint wordt geschreven in C# en gebruikt het .NET kader. Nochtans, kunt u de logica van de cliënttoepassing tot stand brengen die de diensten van AEM Forms in om het even welke ontwikkelomgeving kan aanhalen die de normen van de ZEEP steunt. (Zie AEM Forms [aanroepen met behulp van webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

