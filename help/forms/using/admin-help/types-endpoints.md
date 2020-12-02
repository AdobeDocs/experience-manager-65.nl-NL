---
title: Typen eindpunten
seo-title: Typen eindpunten
description: Leer meer over de verschillende typen eindpunten.
seo-description: Leer meer over de verschillende typen eindpunten.
uuid: c899245c-14cc-4035-9440-95a5b6c1e47f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8fe572e0-8a53-4129-940f-3fdb990073fe
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Typen eindpunten {#types-of-endpoints}

Alvorens de dienst kan worden gebruikt, moet u een eindpunt vormen en toelaten. Een eindpunt specificeert hoe de dienst moet worden aangehaald.

>[!NOTE]
>
>In Workbench worden eindpunten beginpunten genoemd.

De volgende soorten eindpunten kunnen aan de diensten worden toegevoegd. Niet alle services ondersteunen alle eindpunten:

**E-mail:** Hiermee kan een gebruiker een service aanroepen door een e-mailbericht met een of meer bestandsbijlagen naar een opgegeven e-mailaccount te verzenden. Alvorens u een e-maileindpunt vormt, moet u de vereiste e-mailrekeningen vormen. (Zie E-maileindpunten configureren.)

**Gecontroleerde map:** Hiermee kan een gebruiker een service aanroepen door een bestand in een map te plaatsen, die met een bepaald interval wordt gescand. (Zie Gecontroleerde mapeindpunten configureren.)

**TaskManager:** Laat een gebruiker van de Werkruimte toe om de dienst aan te halen.

**Verwijderen:** Hiermee kan een toepassing die met Flex is gebouwd, de service aanroepen met (Verouderd voor AEM formulieren) AEM formulieren verwijderen. Een remoting eindpunt wordt automatisch gecreeerd voor elke geactiveerde dienst. Een bestemming van Flex die de zelfde naam zoals het eindpunt heeft wordt gecreeerd, en de cliënten van Flex kunnen verre voorwerpen tot stand brengen die aan deze bestemming richten om verrichtingen op de relevante dienst aan te halen.

**SOAP:** Laat een cliënttoepassing toe die wordt ontwikkeld gebruikend de AEM vormen programmerings APIs wordt ontwikkeld om de dienst aan te halen gebruikend de wijze van de ZEEP. Een eindpunt van de ZEEP wordt automatisch gecreeerd voor elke geactiveerde dienst.

**opmerking**:  *De veiligheid kan uit documenten van de documentveiligheid worden verwijderd wanneer het eindpunt van de ZEEP wordt gebruikt terwijl het bekijken van de documenten in Adobe Acrobat of Adobe Reader. Voor details op hoe te om de punten van de ZEEP op uw documenten van LCRM onbruikbaar te maken, zie [EINDpunten van de ZEEP voor documenten van de documentveiligheid onbruikbaar maken](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*

**EJB:** Laat een cliënttoepassing toe die gebruikend de AEM vormen programmerings APIs wordt ontwikkeld om de dienst aan te halen gebruikend de wijze van de Onderneming JavaBeans (EJB). Een eindpunt EJB wordt automatisch gecreeerd voor elke geactiveerde dienst.

**WSDL:** Laat een cliënttoepassing toe die gebruikend de AEM vormen wordt ontwikkeld APIs om de dienst aan te halen gebruikend de Taal van de Definitie van de Dienst van het Web (WSDL). De pagina Core Configurations bevat een optie om WSDL-generatie in te schakelen voor alle services die onderdeel zijn van AEM formulieren. (Zie Algemene instellingen voor AEM formulieren configureren.)

**REST:** De processen die in Workbench worden gecreeerd kunnen worden gevormd zodat u hen door de verzoeken van de Overdracht van de Staat van de Vertegenwoordiging (REST) kunt aanhalen. REST-aanvragen worden verzonden vanuit HTML-pagina&#39;s. Met andere woorden, u kunt een AEM formulierproces rechtstreeks vanaf een webpagina oproepen met behulp van een REST-aanvraag.

De e-mail, TaskManager, Gecontroleerde Omslag, en het Verwijderen eindpunten stellen slechts een specifieke verrichting van de dienst bloot. Het toevoegen van deze eindpunten vereist een tweede configuratiestap om een methode te selecteren om de dienst aan te halen, configuratieparameters te plaatsen, en input en outputparameterafbeeldingen te specificeren.
