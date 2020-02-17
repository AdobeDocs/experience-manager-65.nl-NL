---
title: Archiefbestanden importeren en beheren
seo-title: Archiefbestanden importeren en beheren
description: Leer hoe u archieven kunt importeren en beheren.
seo-description: Leer hoe u archieven kunt importeren en beheren.
uuid: aa1613dd-6350-49a7-9643-44365e2acdcc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b6f6463a-2ae4-43d2-8d16-cc20a954e50e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Archiefbestanden importeren en beheren {#import-and-manage-archives}

Met het tabblad Archieven kunt u LCA&#39;s importeren en beheren die in Workbench zijn gemaakt.

## Een archief importeren {#import-an-archive}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer en klik op het tabblad Archieven.
1. Klik op Importeren.
1. Klik op Bladeren om het te importeren archief te zoeken en klik vervolgens op Voorvertoning.
1. Controleer de lijst met bronnen en objecten die samen met het archief worden geïnstalleerd. Zorg ervoor dat er geen conflicten zijn met bestaande bronnen, objecten en serviceconfiguraties omdat er geen mogelijkheden voor ongedaan maken beschikbaar zijn.

   Als u selecteert om de de dienstconfiguraties in te voeren, voert AEM alle dossiers van de procesconfiguratie (eindpunten, veiligheidsprofielen, en de parameters van de de dienstconfiguratie) in die door de processen in LCA worden gebruikt.

1. Klik op Importeren.
1. Controleer de resultaten bij importeren en klik op Configuratie overslaan om het importproces te voltooien of klik op Configureren om het archief te configureren.

   >[!NOTE]
   >
   >Als u op Configuratie overslaan klikt, kunt u het archief later configureren.

1. Als u Configure klikt, vormt de Configure pagina van Eindpunten, waar u om het even welke veranderingen kunt aanbrengen die u vereist:

   * Om een eindpunt anders te noemen of zijn beschrijving uit te geven, klik het.
   * Om een eindpunt van de Manager van de Taak toe te voegen, voegt de klik TaskManager toe. Voor details over de montages van de Manager van de Taak, zie het [Vormen eindpunten](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)van de Manager van de Taak.
   * Als u een eindpunt van een gecontroleerde map wilt toevoegen, klikt u op Controlemap toevoegen. Voor details over de Gecontroleerde montages van de Omslag, zie de [Gecontroleerde montages](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)van het omslageindpunt.
   * Als u een e-maileindpunt wilt toevoegen, klikt u op E-mail toevoegen. Voor details over de E-mailmontages, zie de montages [van het](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)E-maileindpunt.
   * Om een EJB eindpunt toe te voegen, voegt de klik EJB toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Om een eindpunt van de ZEEP toe te voegen, voegt de klik ZEEP toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Als u een eindpunt voor verwijderen wilt toevoegen, klikt u op Verwijdering toevoegen. Voor details over de montages Remoting, zie het [Verwijderen van eindpuntmontages](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Om een REST eindpunt toe te voegen, voegt de klik REST toe en specificeert een naam en een beschrijving voor het eindpunt. Noteer de URL voor de aanroep van REST die wordt weergegeven op de pagina REST Endpoint toevoegen.
   * Als u een eindpunt wilt verwijderen, schakelt u het selectievakje naast het eindpunt in en klikt u op Verwijderen.

1. Klik op Volgende.
1. Als een proces of de dienst in LCA configuratieparameters heeft, vormt een pagina van Parameters, waar u de de dienstparameters vormt en daarna klikt.
1. Breng op de pagina Beveiligingsprofiel configureren alle wijzigingen aan die u nodig hebt:

   * **** Vereisen bezoekers om voor authentiek te verklaren: Deze instelling geeft aan of de service met of zonder referenties kan worden aangeroepen.

      Als de *Bezoekers momenteel worden vereist voor authentiek te verklaren* wordt getoond, moet de bezoeker van de dienst voor authentiek worden verklaard en het gebruikershoofd voor die bezoeker moet worden gemachtigd om de dienst aan te halen; anders wordt de oproeping geweigerd . Om de behoefte te verwijderen om voor authentiek te verklaren, staat de klik Niet voor authentiek verklaarde Bezoekers toe.

      Als de *Bezoekers niet worden vereist voor authentiek te verklaren* wordt getoond, moet de bezoeker van de dienst niet voor authentiek worden verklaard. De aanroeping van de dienst zal altijd slagen omdat er geen vergunningscontrole is. Om authentificatie te vereisen, vereist de klik Bezoekers om voor authentiek te verklaren.

   * **** Uitvoeren als: Specificeert runtime identiteit die door de dienst wordt gebruikt nadat het is aangehaald. Klik op Wijzigen om deze optie te wijzigen. Kies een van de volgende opties:

      **** Niet opgegeven: Het standaardgedrag wordt gebruikt.

      **** Invoker: Gebruikt de zelfde identiteit zoals de gebruiker die de dienst aanhaalde.

      **** Systeem: De service wordt uitgevoerd met volledige rechten. Dit is de standaardinstelling voor langlevende processen.

      **** Benoemde gebruiker: Laat u toe om de dienst als specifieke gebruiker in werking te stellen. Dit is de standaardinstelling voor kortstondige processen. Wanneer u deze optie selecteert, klikt u op Gebruiker selecteren om de pagina Afzonderlijk kapitaal selecteren weer te geven, waar u naar de gebruiker kunt zoeken en deze kunt selecteren.

   * Als u een principal aan het beveiligingsprofiel wilt toevoegen, klikt u op Afbeelding toevoegen en selecteert u de gebruiker of groep die u als principal wilt toevoegen. Klik daarna en selecteer dan de toestemmingen u aan dit hoofd wilt toewijzen:

      **** INVOKE_PERM: Om alle verrichtingen op de dienst aan te halen

      **** MODIFY_CONFIG_PERM: Om de configuratie van de dienst te wijzigen

      **** SUPERVISOR_PERM: Om de gegevens van de procesinstantie voor de dienst te bekijken die van een proces wordt gecreeerd

      **** START_STOP_PERM: Om de dienst te beginnen en te stoppen

      **** ADD_REMOVE_ENDPOINTS_PERM: Om, eindpunten voor de dienst toe te voegen te verwijderen en te wijzigen

      **** CREATE_VERSION_PERM: Een nieuwe versie van de service maken

      **** DELETE_VERSION_PERM: Een versie van de service verwijderen

      **** MODIFY_VERSION_PERM: Om een versie van de dienst te wijzigen

      **** READ_PERM: De service weergeven

      Klik op Voltooid om de principal aan het beveiligingsprofiel toe te voegen.

1. Klik Voltooid om de configuratie te voltooien.

## AEM-formulieren configureren die deel uitmaken van een archiefbestand {#configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer en klik op het tabblad Archieven.
1. Selecteer op de pagina Archiefbeheer het archiefbestand dat u wilt configureren.
1. Selecteer op de pagina Archief weergeven de gemarkeerde archiefbron.
1. Configureer het geïmporteerde procesarchiefbestand.

## Gebruik de configuratietovenaar om de AEM vormen te vormen die deel van een archiefdossier uitmaken {#use-the-configuration-wizard-to-configure-the-aem-forms-that-are-part-of-an-archive-file}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer en klik op het tabblad Archieven.
1. Klik op Configureren naast het archiefbestand dat u wilt configureren.
1. De Configure pagina van Eindpunten verschijnt, waar u om het even welke veranderingen kunt aanbrengen die u vereist:

   * Om een eindpunt anders te noemen of zijn beschrijving uit te geven, klik het.
   * Om een eindpunt van de Manager van de Taak toe te voegen, voegt de klik TaskManager toe. Voor details over de montages van de Manager van de Taak, zie het [Vormen eindpunten](/help/forms/using/admin-help/configuring-task-manager-endpoints.md#configuring-task-manager-endpoints)van de Manager van de Taak.
   * Als u een eindpunt van een gecontroleerde map wilt toevoegen, klikt u op Controlemap toevoegen. Voor details over de Gecontroleerde montages van de Omslag, zie de [Gecontroleerde montages](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#watched-folder-endpoint-settings)van het omslageindpunt.
   * Als u een e-maileindpunt wilt toevoegen, klikt u op E-mail toevoegen. Voor details over de E-mailmontages, zie de montages [van het](/help/forms/using/admin-help/configuring-email-endpoints.md#email-endpoint-settings)E-maileindpunt.
   * Om een EJB eindpunt toe te voegen, voegt de klik EJB toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Om een eindpunt van de ZEEP toe te voegen, voegt de klik ZEEP toe en specificeert een naam en een beschrijving voor het eindpunt.
   * Als u een eindpunt voor verwijderen wilt toevoegen, klikt u op Verwijdering toevoegen. Voor details over de montages Remoting, zie het [Verwijderen van eindpuntmontages](/help/forms/using/admin-help/configuring-remoting-endpoints.md#remoting-endpoint-settings).
   * Om een REST eindpunt toe te voegen, voegt de klik REST toe en specificeert een naam en een beschrijving voor het eindpunt. Noteer de URL voor de aanroep van REST die wordt weergegeven op de pagina REST Endpoint toevoegen.
   * Als u een eindpunt wilt verwijderen, schakelt u het selectievakje naast het eindpunt in en klikt u op Verwijderen.

1. Klik op Volgende.
1. Als een proces of de dienst in LCA configuratieparameters heeft, vormt een pagina van Parameters, waar u de de dienstparameters vormt en daarna klikt.
1. Op de Configure pagina van het Profiel van de Veiligheid, kunt u om het even welke veranderingen aanbrengen die u vereist:

   * **** Vereisen bezoekers om voor authentiek te verklaren: Deze instelling geeft aan of de service met of zonder referenties kan worden aangeroepen.

      Als de *Bezoekers momenteel worden vereist voor authentiek te verklaren* wordt getoond, moet de bezoeker van de dienst voor authentiek worden verklaard en het gebruikershoofd voor die bezoeker moet worden gemachtigd om de dienst aan te halen; anders wordt de oproeping geweigerd . Om de behoefte te verwijderen om voor authentiek te verklaren, staat de klik Niet voor authentiek verklaarde Bezoekers toe.

      Als de *Bezoekers niet worden vereist voor authentiek te verklaren* wordt getoond, kan de bezoeker van de dienst of niet voor authentiek worden verklaard. De aanroeping van de dienst zal altijd slagen omdat er geen vergunningscontrole is. Om authentificatie te vereisen, vereist de klik Bezoekers om voor authentiek te verklaren.

   * **** Uitvoeren als: Specificeert runtime identiteit die door de dienst wordt gebruikt nadat het is aangehaald. Klik op Wijzigen om deze optie te wijzigen. Kies een van de volgende opties:

      **** Niet opgegeven: Het standaardgedrag wordt gebruikt.

      **** Invoker: Gebruikt de zelfde identiteit zoals de gebruiker die de dienst aanhaalde.

      **** Systeem: De service wordt uitgevoerd met volledige rechten. Dit is de standaardinstelling voor langlevende processen.

      **** Benoemde gebruiker: Laat u toe om de dienst als specifieke gebruiker in werking te stellen. Dit is de standaardinstelling voor kortstondige processen. Wanneer u deze optie selecteert, klikt u op Gebruiker selecteren om de pagina Afzonderlijk kapitaal selecteren weer te geven, waar u naar de gebruiker kunt zoeken en deze kunt selecteren.

   * Als u een principal aan het beveiligingsprofiel wilt toevoegen, klikt u op Afbeelding toevoegen en selecteert u de gebruiker of groep die u als principal wilt toevoegen. Klik daarna en selecteer dan de toestemmingen u aan dit hoofd wilt toewijzen:

      **** INVOKE_PERM: Om alle verrichtingen op de dienst aan te halen

      **** MODIFY_CONFIG_PERM: Om de configuratie van de dienst te wijzigen

      **** SUPERVISOR_PERM: Om de gegevens van de procesinstantie voor de dienst te bekijken die van een proces wordt gecreeerd

      **** START_STOP_PERM: Om de dienst te beginnen en te stoppen

      **** ADD_REMOVE_ENDPOINTS_PERM: Om, eindpunten voor de dienst toe te voegen te verwijderen en te wijzigen

      **** CREATE_VERSION_PERM: Een nieuwe versie van de service maken

      **** DELETE_VERSION_PERM: Een versie van de service verwijderen

      **** MODIFY_VERSION_PERM: Om een versie van de dienst te wijzigen

      **** READ_PERM: De service weergeven

      Klik op Voltooid om de principal aan het beveiligingsprofiel toe te voegen.

## Een archief verwijderen {#remove-an-archive}

>[!NOTE]
>
>Als u een archief wilt verwijderen met middelen die zijn opgeslagen in een externe opslagplaats (EMC Documentum Content Server, IBM FileNet Content Manager of IBM Content Manager), moet u ook de elementbestanden verwijderen uit de opslagplaats met Workbench.

1. Klik in de beheerconsole op Services > Toepassingen en services > Archiefbeheer.
1. Schakel op de pagina Archiefbeheer het selectievakje in van het archief dat u wilt verwijderen en klik op Verwijderen.

