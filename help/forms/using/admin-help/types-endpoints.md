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

---


# Typen eindpunten {#types-of-endpoints}

Alvorens de dienst kan worden gebruikt, moet u een eindpunt vormen en toelaten. Een eindpunt specificeert hoe de dienst moet worden aangehaald.

>[!NOTE]
>
>In Workbench worden eindpunten beginpunten genoemd.

De volgende soorten eindpunten kunnen aan de diensten worden toegevoegd. Niet alle services ondersteunen alle eindpunten:

**** E-mail: Hiermee kan een gebruiker een service aanroepen door een e-mailbericht met een of meer bestandsbijlagen naar een opgegeven e-mailaccount te verzenden. Alvorens u een e-maileindpunt vormt, moet u de vereiste e-mailrekeningen vormen. (Zie E-maileindpunten configureren.)

**** Gecontroleerde map: Laat een gebruiker toe om de dienst aan te halen door een dossier in een omslag te plaatsen, die met een bepaald interval wordt gescand. (Zie Gecontroleerde mapeindpunten configureren.)

**** TaskManager: Laat een gebruiker van de Werkruimte toe om de dienst aan te halen.

**** Verwijderen: Hiermee kan een toepassing die is gebouwd met Flex, de service aanroepen met AEM-formulieren (afgekeurd voor AEM-formulieren). Een remoting eindpunt wordt automatisch gecreeerd voor elke geactiveerde dienst. Een Flex bestemming die de zelfde naam zoals het eindpunt heeft wordt gecreeerd, en Flex cliënten kunnen verre voorwerpen tot stand brengen die aan deze bestemming richten om verrichtingen op de relevante dienst aan te halen.

**** SOAP: Hiermee wordt een clienttoepassing die is ontwikkeld met de API&#39;s voor het programmeren van AEM-formulieren, ingeschakeld om de service aan te roepen met de SOAP-modus. Een eindpunt van de ZEEP wordt automatisch gecreeerd voor elke geactiveerde dienst.

**opmerking**: De *beveiliging kan uit documenten met documentbeveiliging worden verwijderd wanneer het SOAP-eindpunt wordt gebruikt bij het weergeven van de documenten in Adobe Acrobat of Adobe Reader. Voor details op hoe te om de punten van de ZEEP op uw documenten van LCRM onbruikbaar te maken, zie de EINDpunten van de ZEEP van de[Uitdrukking voor de documenten van de documentveiligheid](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*

**** EJB: Hiermee kan een clienttoepassing die is ontwikkeld met de API&#39;s voor het programmeren van AEM-formulieren, de service aanroepen met de modus Enterprise JavaBeans (EJB). Een eindpunt EJB wordt automatisch gecreeerd voor elke geactiveerde dienst.

**** WSDL: Laat een cliënttoepassing toe die gebruikend de AEM vormen die APIs wordt ontwikkeld om de dienst aan te halen gebruikend de Taal van de Definitie van de Dienst van het Web (WSDL). De pagina Core Configurations bevat een optie om WSDL-generatie in te schakelen voor alle services die deel uitmaken van AEM-formulieren. (Zie Algemene instellingen voor AEM-formulieren configureren.)

**** REST:De processen die in Workbench worden gecreeerd kunnen worden gevormd zodat u hen door de verzoeken van de Overdracht van de Staat van de Vertegenwoordiging (REST) kunt aanhalen. REST-aanvragen worden verzonden vanuit HTML-pagina&#39;s. Met andere woorden, u kunt een AEM-formulierproces rechtstreeks vanaf een webpagina oproepen met behulp van een REST-aanvraag.

De e-mail, TaskManager, Gecontroleerde Omslag, en het Verwijderen eindpunten stellen slechts een specifieke verrichting van de dienst bloot. Het toevoegen van deze eindpunten vereist een tweede configuratiestap om een methode te selecteren om de dienst aan te halen, configuratieparameters te plaatsen, en input en outputparameterafbeeldingen te specificeren.
