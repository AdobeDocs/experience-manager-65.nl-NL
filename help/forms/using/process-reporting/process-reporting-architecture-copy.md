---
title: Hoe procesrapportage werkt
seo-title: Hoe procesrapportage werkt
description: Beschrijving van de services die de AEM Forms on JEE Process Reporting en een inleiding vormen op de interface Process Reporting UI
seo-description: Beschrijving van de services die de AEM Forms on JEE Process Reporting en een inleiding vormen op de interface Process Reporting UI
uuid: 4631b734-a679-495c-a708-2348bf22c1f7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: process-reporting
discoiquuid: a1af9920-5d2a-462f-bdee-ccec4c047c5b
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Hoe procesrapportage werkt {#how-process-reporting-works}

Process Reporting is de rapportmodule van de AEM Forms on JEE.

Met Process Reporting kunt u rapporten uitvoeren over processen en taken in AEM Forms.

Bij Process Reporting wordt gebruikgemaakt van de ingesloten Process Reporting-opslagplaats om Forms-gegevens te publiceren. Vervolgens worden die gegevens gebruikt om rapporten uit te voeren.

Procesrapportage bestaat uit de volgende modules:

* [ProcessDataPublisher-service](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatapublisher-service-br-p)
* [ProcessDataStorage-service](/help/forms/using/process-reporting/process-reporting-architecture.md#p-processdatastorageprovider-service-br-p)
* [OSGi-service](/help/forms/using/process-reporting/process-reporting-architecture.md#p-osgi-service-br-p)
* [Query-gegevensserver](/help/forms/using/process-reporting/process-reporting-architecture.md#p-querydataservlet-service-br-p)
* [Gebruikersinterface voor procesrapportage](/help/forms/using/process-reporting/process-reporting-architecture.md#p-process-reporting-user-interface-br-p)

## Procesrapporteringsarchitectuur {#process-reporting-architecture-br}

![procesrapporteringsarchitectuur](assets/processreportingarchitecture.png)

## Procesrapporteringsmodules {#process-reporting-modules}

### ProcessDataPublisher-service {#processdatapublisher-service-br}

De ProcessDataPublisher-server wordt periodiek uitgevoerd in de AEM Forms-database en extraheert de gegevens die zijn gewijzigd sinds de laatste uitvoering van de service. De gegevens worden vervolgens gepubliceerd naar de service Gegevensopslag verwerken.

Voor details bij het vormen van de dienst, zie de dienst [](/help/forms/using/process-reporting/install-start-process-reporting.md#p-reportconfiguration-service-p)van ProcessDataPublisher vormen.

### ProcessDataStorageProvider-service {#processdatastorageprovider-service-br}

De dienst ProcessDataStorageProvider ontvangt procesgegevens van de dienst ProcessDataPublisher en bewaart de gegevens aan de bewaarplaats van de Rapportering van het Proces.

Zie [ProcessDataStorageProvider-service](/help/forms/using/process-reporting/install-start-process-reporting.md#p-to-configure-the-process-reporting-repository-locations-p)configureren voor meer informatie over het configureren van de service.

### OSGi-service {#osgi-service-br}

QueryDataServlet gebruikt deze dienst om de rapporteringsgegevens van de Opslagplaats van de Rapportering van het Proces te verkrijgen.

### QueryDataServlet-service {#querydataservlet-service-br}

De dienst QueryDataServlet keurt vragen van het Rapport van het Proces gebruikersinterface goed.

De dienst gebruikt dan diensten OSGi om de relevante het melden gegevens te verkrijgen, de gegevens te verwerken, en de gegevens aan het gebruikersinterface terug te keren.

### Gebruikersinterface voor procesrapportage {#process-reporting-user-interface-br}

Het proces dat gebruikersinterface meldt is een browser-gebaseerde interface van het Web. U gebruikt deze interface om proces- en taakinformatie weer te geven die is gepubliceerd vanuit de AEM Forms-database.

### QueryDataServlet-service {#querydataservlet-service-br-1}

De dienst QueryDataServlet keurt vragen van het Rapport van het Proces gebruikersinterface goed.

De dienst gebruikt dan diensten OSGi om de relevante het melden gegevens te verkrijgen, de gegevens te verwerken, en de gegevens aan het gebruikersinterface terug te keren.

### Aangepaste rapporten {#custom-reports-br}

U kunt uw eigen douanerapporten tot stand brengen en deze rapporten tonen in het lusje van de Rapporten van de Douane van het Proces Meldend gebruikersinterface.

Voor de stappen om een douanerapport tot stand te brengen, zie om een douanerapport in het artikel [van de Douane tot stand te brengen Rapporten in het Rapporteren](/help/forms/using/process-reporting/process-reporting-custom-reports.md)van het Proces.
