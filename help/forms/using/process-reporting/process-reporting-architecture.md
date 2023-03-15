---
title: Hoe procesrapportage werkt
seo-title: How Process Reporting Works
description: Beschrijving van de diensten die de AEM Forms vormen voor JEE Process Reporting en een inleiding op de Process Reporting UI
seo-description: Description of the services that make up the AEM Forms on JEE Process Reporting and an introduction to the Process Reporting UI
uuid: 37e31985-088a-4ef6-ba57-10a01597a873
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: a6ff50df-273d-48f7-b0c6-0e69e900b97f
docset: aem65
exl-id: 66dfac36-5b7e-40be-9921-efa9f2a9521c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Hoe procesrapportage werkt{#how-process-reporting-works}

Procesrapportage is de rapporteringsmodule van de AEM Forms op JEE.

Met Process Reporting kunt u rapporten uitvoeren over AEM Forms-processen en -taken.

Procesrapportage gebruikt de ingesloten Process Reporting-opslagplaats om Forms-gegevens te publiceren. Vervolgens worden die gegevens gebruikt om rapporten uit te voeren.

Procesrapportage bestaat uit de volgende modules:

* [ProcessDataPublisher-service](#processdatapublisher-service-br-p)
* [ProcessDataStorage-service](#processdatastorageprovider-service-br-p)
* [OSGi-service](#osgi-service-br-p)
* [Query-gegevensserver](#querydataservlet-service-br-p)
* [Gebruikersinterface voor procesrapportage](#process-reporting-user-interface-br-p)

## Procesrapporteringsarchitectuur {#process-reporting-architecture-br}

![procesrapporteringsarchitectuur](assets/processreportingarchitecture.png)

## Procesrapporteringsmodules {#process-reporting-modules}

### ProcessDataPublisher-service {#processdatapublisher-service-br}

De ProcessDataPublisher-server wordt regelmatig uitgevoerd in de AEM Forms-database en extraheert de gegevens die zijn gewijzigd sinds de laatste uitvoering van de service. De gegevens worden vervolgens gepubliceerd naar de service Gegevensopslag verwerken.

Voor details bij het vormen van de dienst, zie [De service ProcessDataPublisher configureren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p).

### ProcessDataStorageProvider-service {#processdatastorageprovider-service-br}

De dienst ProcessDataStorageProvider ontvangt procesgegevens van de dienst ProcessDataPublisher en bewaart de gegevens aan de bewaarplaats van de Rapportering van het Proces.

Voor details bij het vormen van de dienst, zie [De service ProcessDataStorageProvider configureren](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p).

### OSGi-service {#osgi-service-br}

QueryDataServlet gebruikt deze dienst om de rapporteringsgegevens van de Opslagplaats van de Rapportering van het Proces te verkrijgen.

### QueryDataServlet-service {#querydataservlet-service-br}

De dienst QueryDataServlet keurt vragen van het Rapport van het Proces gebruikersinterface goed.

De dienst gebruikt dan diensten OSGi om de relevante het melden gegevens te verkrijgen, de gegevens te verwerken, en de gegevens aan het gebruikersinterface terug te keren.

### Gebruikersinterface voor procesrapportage {#process-reporting-user-interface-br}

Het proces dat gebruikersinterface meldt is een browser-gebaseerde interface van het Web. U gebruikt deze interface om proces- en taakinformatie weer te geven die is gepubliceerd vanuit de AEM Forms-database.

Voor een inleiding aan het Proces Meldend gebruikersinterface, zie [Gebruikersinterface voor procesrapportage](/help/forms/using/process-reporting/introduction-process-reporting.md).

### QueryDataServlet-service {#querydataservlet-service-br-1}

De dienst QueryDataServlet keurt vragen van het Rapport van het Proces gebruikersinterface goed.

De dienst gebruikt dan diensten OSGi om de relevante het melden gegevens te verkrijgen, de gegevens te verwerken, en de gegevens aan het gebruikersinterface terug te keren.

### Aangepaste rapporten {#custom-reports-br}

U kunt uw eigen douanerapporten tot stand brengen en deze rapporten tonen in het lusje van de Rapporten van de Douane van het Proces Meldend gebruikersinterface.

Voor de stappen om een douanerapport tot stand te brengen, zie om een douanerapport in het artikel tot stand te brengen [Aangepaste rapporten in procesrapportage](/help/forms/using/process-reporting/process-reporting-custom-reports.md).
