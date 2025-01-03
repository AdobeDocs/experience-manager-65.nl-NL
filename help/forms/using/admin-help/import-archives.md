---
title: Archiefbestanden importeren en beheren
description: Leer hoe u archieven kunt importeren en beheren. Hiermee worden importbewerkingen gearchiveerd en LCA's die in Workbench zijn gemaakt, beheerd. U kunt een archief importeren, configureren, gebruiken en verwijderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0c15677a-ee17-425e-a261-fb3ae8688eb2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1450'
ht-degree: 0%

---

# Archiefbestanden importeren en beheren {#import-and-manage-archives}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Met het tabblad Archieven kunt u LCA&#39;s importeren en beheren die in Workbench zijn gemaakt.

## Een archief importeren {#import-an-archive}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer en klik op het tabblad Archieven.
1. Klik op Import.
1. Klik op Bladeren om het te importeren archief te zoeken en klik vervolgens op Voorvertoning.
1. Controleer de lijst met bronnen en objecten die samen met het archief worden geïnstalleerd. Zorg ervoor dat er geen conflicten zijn met bestaande bronnen, objecten en serviceconfiguraties omdat er geen mogelijkheden voor ongedaan maken beschikbaar zijn.

   Als u selecteert om de de dienstconfiguraties in te voeren, AEM vormen invoert alle dossiers van de procesconfiguratie (eindpunten, veiligheidsprofielen, en de parameters van de de dienstconfiguratie) die door de processen in LCA worden gebruikt.

1. Klik op Import.
1. Controleer de resultaten bij importeren en klik op Configuratie overslaan om het importproces te voltooien of klik op Configureren om het archief te configureren.

   >[!NOTE]
   >
   >Als u op Configuratie overslaan klikt, kunt u het archief later configureren.

1. Als u Configure klikt, vormt de Configure pagina van Eindpunten, waar u om het even welke veranderingen kunt aanbrengen die u vereist:

   * Om een eindpunt anders te noemen of zijn beschrijving uit te geven, klik het.
   * Als u een taakbeheereindpunt wilt toevoegen, klikt u op TaskManager toevoegen. Voor details over de montages van de Manager van de Taak, zie [ Vormende eindpunten van de Manager van de Taak ](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints).
   * Als u een eindpunt van een gecontroleerde map wilt toevoegen, klikt u op Controlemap toevoegen. Voor details over de Gecontroleerde montages van de Omslag, zie [ Gecontroleerde montages van het omslageindpunt ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings).
   * Als u een e-maileindpunt wilt toevoegen, klikt u op E-mail toevoegen. Voor details over de E-mailmontages, zie [ E-mail eindpuntmontages ](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings).
   * Om een EJB eindpunt toe te voegen, voegt de klik EJB toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Om een SOAP eindpunt toe te voegen, voegt de klik SOAP toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Als u een eindpunt voor verwijderen wilt toevoegen, klikt u op Verwijdering toevoegen. Voor details over de Verwijderende montages, zie [ het Verwijderen van eindpuntmontages ](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Om een REST eindpunt toe te voegen, voegt de klik REST toe en specificeert een naam en een beschrijving voor het eindpunt. Noteer de URL voor de aanroep van REST die wordt weergegeven op de pagina REST Endpoint toevoegen.
   * Als u een eindpunt wilt verwijderen, schakelt u het selectievakje naast het eindpunt in en klikt u op Verwijderen.

1. Klik op Volgende.
1. Als een proces of de dienst in LCA configuratieparameters heeft, vormt een pagina van Parameters, waar u de de dienstparameters vormt en daarna klikt.
1. Breng op de pagina Beveiligingsprofiel configureren alle gewenste wijzigingen aan:

   * **vereist bezoekers om voor authentiek te verklaren:** Dit het plaatsen wijst erop of de dienst met of zonder geloofsbrieven kan worden aangehaald.

     Als *de Bezoekers momenteel worden vereist om voor authentiek te verklaren* wordt getoond, moet de bezoeker van de dienst voor authentiek worden verklaard en het gebruikershoofd voor die bezoeker moet worden gemachtigd om de dienst aan te halen; anders, zal de aanroepende poging worden geweigerd. Om de behoefte te verwijderen om voor authentiek te verklaren, staat de klik Niet voor authentiek verklaarde Bezoekers toe.

     Als *de Bezoekers niet worden vereist om voor authentiek te verklaren* wordt getoond, te hoeven de bezoeker van de dienst niet voor authentiek worden verklaard. De aanroeping van de dienst zal altijd slagen omdat er geen vergunningscontrole is. Om authentificatie te vereisen, vereist de klik Bezoekers om voor authentiek te verklaren.

   * **Looppas als:** specificeert runtime identiteit die door de dienst wordt gebruikt nadat het is aangehaald. Klik op Wijzigen om deze optie te wijzigen. Kies een van de volgende opties:

     **Niet gespecificeerd:** het standaardgedrag wordt gebruikt.

     **Invoker:** gebruikt de zelfde identiteit zoals de gebruiker die de dienst aanhaalde.

     **Systeem:** stelt de dienst met volledige voorrechten in werking. Dit is de standaardinstelling voor langlevende processen.

     **Benoemde Gebruiker:** laat u toe om de dienst als specifieke gebruiker in werking te stellen. Dit is de standaardinstelling voor kortstondige processen. Wanneer u deze optie selecteert, klikt u op Gebruiker selecteren om de pagina Afzonderlijk kapitaal selecteren weer te geven. Hier kunt u de gebruiker zoeken en selecteren.

   * Als u een principal aan het beveiligingsprofiel wilt toevoegen, klikt u op Afbeelding toevoegen en selecteert u de gebruiker of groep die u als principal wilt toevoegen. Klik daarna en selecteer dan de toestemmingen u aan dit hoofd wilt toewijzen:

     **INVOKE_PERM:** om alle verrichtingen op de dienst aan te halen

     **MODIFY_CONFIG_PERM:** om de configuratie van de dienst te wijzigen

     **SUPERVISOR_PERM:** om procesinstantiegegevens voor de dienst te bekijken die van een proces wordt gecreeerd

     **START_STOP_PERM:** om de dienst te beginnen en tegen te houden

     **ADD_REMOVE_ENDPOINTS_PERM:** om, eindpunten voor de dienst toe te voegen te verwijderen en te wijzigen

     **CREATE_VERSION_PERM:** om een versie van de dienst te creëren

     **DELETE_VERSION_PERM:** om een versie van de dienst te schrappen

     **MODIFY_VERSION_PERM:** om een versie van de dienst te wijzigen

     **READ_PERM:** om de dienst te bekijken

     Klik op Voltooid om de principal aan het beveiligingsprofiel toe te voegen.

1. Klik Voltooid om de configuratie te voltooien.

## De AEM formulieren configureren die deel uitmaken van een archiefbestand {#configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer en klik op het tabblad Archieven.
1. Selecteer op de pagina Archiefbeheer het archiefbestand dat u wilt configureren.
1. Selecteer op de pagina Archief weergeven de gemarkeerde archiefbron.
1. Het geïmporteerde procesarchiefbestand configureren.

## Gebruik de configuratietovenaar om de AEM vormen te vormen die deel van een archiefdossier uitmaken {#use-the-configuration-wizard-to-configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer en klik op het tabblad Archieven.
1. Klik op Configureren naast het archiefbestand dat u wilt configureren.
1. De Configure pagina van Eindpunten verschijnt, waar u om het even welke veranderingen kunt aanbrengen die u vereist:

   * Om een eindpunt anders te noemen of zijn beschrijving uit te geven, klik het.
   * Als u een taakbeheereindpunt wilt toevoegen, klikt u op TaskManager toevoegen. Voor details over de montages van de Manager van de Taak, zie [ Vormende eindpunten van de Manager van de Taak ](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints).
   * Als u een eindpunt van een gecontroleerde map wilt toevoegen, klikt u op Controlemap toevoegen. Voor details over de Gecontroleerde montages van de Omslag, zie [ Gecontroleerde montages van het omslageindpunt ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings).
   * Als u een e-maileindpunt wilt toevoegen, klikt u op E-mail toevoegen. Voor details over de E-mailmontages, zie [ E-mail eindpuntmontages ](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings).
   * Om een EJB eindpunt toe te voegen, voegt de klik EJB toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Om een SOAP eindpunt toe te voegen, voegt de klik SOAP toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Als u een eindpunt voor verwijderen wilt toevoegen, klikt u op Verwijdering toevoegen. Voor details over de Verwijderende montages, zie [ het Verwijderen van eindpuntmontages ](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Om een REST eindpunt toe te voegen, voegt de klik REST toe en specificeert een naam en een beschrijving voor het eindpunt. Noteer de URL voor de aanroep van REST die wordt weergegeven op de pagina REST Endpoint toevoegen.
   * Als u een eindpunt wilt verwijderen, schakelt u het selectievakje naast het eindpunt in en klikt u op Verwijderen.

1. Klik op Volgende.
1. Als een proces of de dienst in LCA configuratieparameters heeft, vormt een pagina van Parameters, waar u de de dienstparameters vormt en daarna klikt.
1. Op de Configure pagina van het Profiel van de Veiligheid, kunt u om het even welke veranderingen aanbrengen die u vereist:

   * **vereist bezoekers om voor authentiek te verklaren:** Dit het plaatsen wijst erop of de dienst met of zonder geloofsbrieven kan worden aangehaald.

     Als *de Bezoekers momenteel worden vereist om voor authentiek te verklaren* wordt getoond, moet de bezoeker van de dienst voor authentiek worden verklaard en het gebruikershoofd voor die bezoeker moet worden gemachtigd om de dienst aan te halen; anders, zal de aanroepende poging worden geweigerd. Om de behoefte te verwijderen om voor authentiek te verklaren, staat de klik Niet voor authentiek verklaarde Bezoekers toe.

     Als *de Bezoekers niet worden vereist om voor authentiek te verklaren* wordt getoond, kan de bezoeker van de dienst of niet voor authentiek worden verklaard. De aanroeping van de dienst zal altijd slagen omdat er geen vergunningscontrole is. Om authentificatie te vereisen, vereist de klik Bezoekers om voor authentiek te verklaren.

   * **Looppas als:** specificeert runtime identiteit die door de dienst wordt gebruikt nadat het is aangehaald. Klik op Wijzigen om deze optie te wijzigen. Kies een van de volgende opties:

     **Niet gespecificeerd:** het standaardgedrag wordt gebruikt.

     **Invoker:** gebruikt de zelfde identiteit zoals de gebruiker die de dienst aanhaalde.

     **Systeem:** stelt de dienst met volledige voorrechten in werking. Dit is de standaardinstelling voor langlevende processen.

     **Benoemde Gebruiker:** laat u toe om de dienst als specifieke gebruiker in werking te stellen. Dit is de standaardinstelling voor kortstondige processen. Wanneer u deze optie selecteert, klikt u op Gebruiker selecteren om de pagina Afzonderlijk kapitaal selecteren weer te geven. Hier kunt u de gebruiker zoeken en selecteren.

   * Als u een principal aan het beveiligingsprofiel wilt toevoegen, klikt u op Afbeelding toevoegen en selecteert u de gebruiker of groep die u als principal wilt toevoegen. Klik daarna en selecteer dan de toestemmingen u aan dit hoofd wilt toewijzen:

     **INVOKE_PERM:** om alle verrichtingen op de dienst aan te halen

     **MODIFY_CONFIG_PERM:** om de configuratie van de dienst te wijzigen

     **SUPERVISOR_PERM:** om procesinstantiegegevens voor de dienst te bekijken die van een proces wordt gecreeerd

     **START_STOP_PERM:** om de dienst te beginnen en tegen te houden

     **ADD_REMOVE_ENDPOINTS_PERM:** om, eindpunten voor de dienst toe te voegen te verwijderen en te wijzigen

     **CREATE_VERSION_PERM:** om een versie van de dienst te creëren

     **DELETE_VERSION_PERM:** om een versie van de dienst te schrappen

     **MODIFY_VERSION_PERM:** om een versie van de dienst te wijzigen

     **READ_PERM:** om de dienst te bekijken

     Klik op Voltooid om de principal aan het beveiligingsprofiel toe te voegen.

## Een archief verwijderen {#remove-an-archive}

>[!NOTE]
>
>Als u een archief wilt verwijderen met middelen die zijn opgeslagen in een externe opslagruimte (EMC Documentum Content Server, IBM FileNet Content Manager of IBM Content Manager), moet u ook de elementbestanden verwijderen uit de opslagplaats met Workbench.

1. Klik in de beheerconsole op Services > Toepassingen en services > Archiefbeheer.
1. Schakel op de pagina Archiefbeheer het selectievakje in van het archief dat u wilt verwijderen en klik op Verwijderen.
