---
title: Typen eindpunten
description: Leer meer over de verschillende typen eindpunten. Verschillende typen eindpunten, zoals E-mail, Gecontroleerde map en nog veel meer, kunnen aan services worden toegevoegd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 380cab7f-e7f7-4cb7-bd20-ea530a349fac
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Typen eindpunten {#types-of-endpoints}

Alvorens de dienst kan worden gebruikt, moet u een eindpunt vormen en toelaten. Een eindpunt specificeert hoe de dienst moet worden aangehaald.

>[!NOTE]
>
>In Workbench worden eindpunten beginpunten genoemd.

De volgende soorten eindpunten kunnen aan de diensten worden toegevoegd. Niet alle services ondersteunen alle eindpunten:

**E-mail:** laat een gebruiker toe om de dienst aan te halen door een e-mailbericht met één of meerdere dossiergehechtheid naar een gespecificeerde e-mailrekening te verzenden. Alvorens u een e-maileindpunt vormt, moet u de vereiste e-mailrekeningen vormen. (Zie E-maileindpunten configureren.)

**Gecontroleerde Omslag:** laat een gebruiker toe om de dienst aan te halen door een dossier in een omslag te plaatsen, die bij een bepaald interval wordt gescand. (Zie Gecontroleerde mapeindpunten configureren.)

**TaskManager:** laat een gebruiker van Workspace toe om de dienst aan te halen.

**het Verwijderen:** laat een toepassing toe die met Flex wordt gebouwd om de dienst aan te halen gebruikend (Vervangen voor AEM vormen) AEM het Verwijderen van vormen. Een remoting eindpunt wordt automatisch gecreeerd voor elke geactiveerde dienst. Een bestemming van Flex die de zelfde naam zoals het eindpunt heeft wordt gecreeerd, en de cliënten van Flex kunnen verre voorwerpen tot stand brengen die aan deze bestemming richten om verrichtingen op de relevante dienst aan te halen.

**SOAP:** laat een cliënttoepassing toe die gebruikend de AEM vormen programmerings APIs wordt ontwikkeld om de dienst aan te halen gebruikend SOAP wijze. Een SOAP eindpunt wordt automatisch gecreeerd voor elke geactiveerde dienst.

**nota**: *de Veiligheid kan uit documenten van de documentveiligheid worden verwijderd wanneer het SOAP eindpunt terwijl het bekijken van de documenten in Adobe Acrobat of Adobe Reader wordt gebruikt. Voor details op hoe te om SOAP punten op uw documenten onbruikbaar te maken LCRM, zie [ SOAP eindpunten voor documenten van de documentveiligheid onbruikbaar maken](/help/forms/using/admin-help/configuring-client-server-options.md#disable-soap-endpoints-for-document-security-documents)*

**EJB:** laat een cliënttoepassing toe die gebruikend de AEM vormen wordt ontwikkeld APIs om de dienst aan te halen gebruikend de wijze van JavaBeans van de Onderneming (EJB). Een eindpunt EJB wordt automatisch gecreeerd voor elke geactiveerde dienst.

**WSDL:** laat een cliënttoepassing toe die gebruikend de AEM vormen wordt ontwikkeld APIs om de dienst aan te halen gebruikend de Taal van de Definitie van de Dienst van het Web (WSDL). De pagina Core Configurations bevat een optie om WSDL-generatie in te schakelen voor alle services die onderdeel zijn van AEM formulieren. (Zie Algemene instellingen voor AEM formulieren configureren.)

**REST:** De processen die in Workbench worden gecreeerd kunnen worden gevormd zodat u hen door de verzoeken van de Overdracht van de Staat van de Vertegenwoordiging (REST) kunt aanhalen. REST-aanvragen worden verzonden vanaf HTML-pagina&#39;s. Met andere woorden, u kunt een AEM formulierproces rechtstreeks vanaf een webpagina oproepen met behulp van een REST-aanvraag.

De e-mail, TaskManager, Gecontroleerde Omslag, en het Verwijderen eindpunten stellen slechts een specifieke verrichting van de dienst bloot. Het toevoegen van deze eindpunten vereist een tweede configuratiestap om een methode te selecteren om de dienst aan te halen, configuratieparameters te plaatsen, en input en outputparameterafbeeldingen te specificeren.
