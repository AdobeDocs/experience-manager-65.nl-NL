---
title: Inleiding tot Java&trade; API QuickStart
description: Leer hoe AEM Forms-bewerkingen kunnen worden uitgevoerd met de AEM Forms Java&trade; sterk getypte API ingeschakeld met SOAP verbinding.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop, development-tools
role: Developer
exl-id: 1d4062ef-fb24-4527-b899-896ce757beda
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 939a2efa64c853928a9082aa30d7338e98deb695
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Introductie van Java™ API, snel aan de slag {#introducing-java-api-quickstart}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Met de Adobe AEM Forms API Quick Start kunt u uw inspanningen versnellen om programma&#39;s te ontwikkelen die met de diensten van AEM Forms communiceren. *Snelle Begin* is volledige programma&#39;s die u in uw eigen projecten en gebruik als uitgangspunt kunt kopiëren en kleven. U kunt een Snel Begin in werking stellen om te zien hoe het zich gedraagt en het voor uw eigen behoeften wijzigt.

AEM Forms-bewerkingen kunnen worden uitgevoerd met de API met sterke typen voor AEM Forms en de verbindingsmodus moet zijn ingesteld op SOAP.

Quick Start van de Java™ sterk getypte API biedt een lijst met JAR-bestanden die vereist zijn om de Java™-toepassing uit te voeren. De meeste Java™ Quick Start-toepassingen zijn consoletoepassingen die binnen `main` worden uitgevoerd. De Forms Java™ API met sterke typen Quick Start wordt echter geïmplementeerd als een Java™ servlet die wordt uitgevoerd in een webtoepassing.

De lijst met JAR-bestanden bevindt zich in een opmerkingensectie aan het begin van de Snelle start. De volgende opmerking bevindt zich bijvoorbeeld in een Output quick start en is een typische JAR-bestandenlijst die wordt weergegeven in elke Java™ Quick Start.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-output-client.jar
     * 2. adobe--client.jar
     * 3. adobe-usermanager-client.jar
     *
     * These JAR files are in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/common
     *
     * The adobe-utilities.jar file is in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/SDK/client-libs/jboss
     *
     * The jboss-client.jar file is in the following path:
     * <install directory>/Adobe/Adobe_Experience_Manager_forms/jboss/bin/client
     *
     * If you want to invoke a remote AEM Forms instance and there is a
     * firewall between the client application and AEM Forms, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
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

## Meerdere services snel starten {#multiple-services-quick-start}

De meeste Snelle Begint in *Programmerend met AEM Forms op JEE* haalt de specifieke dienst aan om een verrichting uit te voeren. Nochtans, roepen sommige Snel Begint veelvoudige diensten van AEM Forms aan om een bepaalde werkschema uit te voeren. In de volgende lijst vindt u snel Java™-start waarmee meerdere AEM Forms-services worden aangeroepen:

[ Snelle Begin (SOAP wijze): Het overgaan van een document in de Bewaarplaats van AEM Forms tot de dienst van de Output die Java™ API ](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) gebruikt (haalt Bewaarplaats en de dienst van de Output aan)

[ Snel Begin (SOAP wijze): Creërend een document van de PDF dat op fragmenten wordt gebaseerd die Java™ API gebruiken ](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api) (haalt de Assembler en de dienst van de Output aan)

[ Snelle Begin (SOAP wijze): Creërend de Documenten van PDF met voorgelegde gegevens van XML gebruikend Java™ API ](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-creating-pdf-documents-with-submitted-xml-data-using-the-java-api) (haalt Forms, Output, en de dienst van het Beheer van het Document aan)

[ Snelle Begin (SOAP wijze): Het overgaan van documenten tot de Dienst van Forms die Java™ API gebruiken ](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-passing-documents-to-the-forms-service-using-the-java-api) (haalt de dienst van het Beheer van Forms en van het Document aan)

[ Snel Begin (SOAP wijze): Digitaal het ondertekenen van een op XFA-Gebaseerde Vorm gebruikend Java™ API ](/help/forms/developing/signature-service-java-api-quick.md#quick-start-soap-mode-digitally-signing-a-xfa-based-form-using-the-java-api) (haalt de dienst van Forms en van de Handtekening aan)

[ Snel Begin (SOAP wijze): Het beheren van rollen en toestemmingen die Java™ API gebruiken ](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api) (haalt DirectoryManager en de dienst AuthorizationManager aan)

[ Snelle Begin (SOAP wijze): Het overgaan van documenten tot de Dienst van de Output die Java™ API ](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api) gebruiken (haalt de dienst van het Beheer van de Output en van het Document aan)

>[!NOTE]
>
>Quick Start in Programming with AEM Forms is gebaseerd op AEM Forms dat wordt geïmplementeerd op JBoss® Application Server en het Microsoft® Windows® besturingssysteem. Als u echter een ander besturingssysteem gebruikt, zoals UNIX®, vervangt u Windows-specifieke paden door paden die door het desbetreffende besturingssysteem worden ondersteund. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. (Zie [ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>De meeste van de Webdienst Snel Begint wordt geschreven in C# en gebruikt het .NET kader. Nochtans, kunt u de logica van de cliënttoepassing tot stand brengen die de diensten van AEM Forms in om het even welke ontwikkelomgeving kan aanhalen die SOAP normen steunt. (Zie [ het aanhalen van AEM Forms die de Diensten van het Web gebruiken ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)
