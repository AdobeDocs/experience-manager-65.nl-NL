---
title: Beveiligde beheerinstellingen voor AEM Forms configureren op JEE
seo-title: Beveiligde beheerinstellingen voor AEM Forms configureren op JEE
description: Leer hoe u gebruikersaccounts en services beheert die, hoewel vereist in een particuliere ontwikkelomgeving, niet vereist zijn in een productieomgeving van AEM Forms op JEE.
seo-description: Leer hoe u gebruikersaccounts en services beheert die, hoewel vereist in een particuliere ontwikkelomgeving, niet vereist zijn in een productieomgeving van AEM Forms op JEE.
uuid: 04e45d06-f57d-406c-8228-15f483199430
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: d211d8b0-e75f-49c3-808d-5d0e26ad3a6b
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '884'
ht-degree: 0%

---


# Beveiligde beheerinstellingen voor AEM Forms configureren op JEE {#configuring-secure-administration-settings-for-aem-forms-on-jee}

Leer hoe u gebruikersaccounts en services beheert die, hoewel vereist in een particuliere ontwikkelomgeving, niet vereist zijn in een productieomgeving van AEM Forms op JEE.

Over het algemeen gebruiken ontwikkelaars de productieomgeving niet om hun toepassingen te bouwen en te testen. Daarom moet u gebruikersrekeningen en de diensten beheren die, hoewel vereist in een privé ontwikkelomgeving, niet in een productiemilieu worden vereist.

Dit artikel beschrijft methodes om de algemene aanvalsoppervlakte door beleidsopties te verminderen die AEM Forms op JEE verstrekt.

## Niet-essentiële externe toegang tot services {#disabling-non-essential-remote-access-to-services} uitschakelen

Nadat AEM Forms op JEE is geïnstalleerd en geconfigureerd, zijn veel services beschikbaar voor externe aanroeping via SOAP en Enterprise JavaBeans™ (EJB). De term extern verwijst in dit geval naar elke aanroeper die netwerktoegang heeft tot de SOAP-, EJB- of AMF-poorten (Action Message Format) voor de toepassingsserver.

Hoewel AEM Forms op de diensten JEE geldige geloofsbrieven vereisen om voor een erkende bezoeker worden overgegaan, zou u slechts verre toegang tot de diensten moeten toestaan die u ver toegankelijk moet zijn. Om beperkte toegankelijkheid te bereiken, zou u de reeks ver toegankelijke diensten tot het minimum mogelijk voor een werkend systeem moeten verminderen en dan verre aanroeping voor de extra diensten toelaten die u nodig hebt.

AEM Forms on JEE services hebben altijd minstens SOAP-toegang nodig. Deze services zijn gewoonlijk vereist voor gebruik door Workbench, maar omvatten ook services die door de Workspace-webtoepassing worden aangeroepen.

Voltooi deze procedure gebruikend de Webpagina van Toepassingen en van de Diensten in de Console van het Beleid:

1. Meld u aan bij de beheerconsole door de volgende URL te typen in een webbrowser:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klik **Services > Toepassingen en services > Voorkeuren**.
1. Stel de voorkeuren in om maximaal 200 services en eindpunten op dezelfde pagina weer te geven.
1. Klik **Services** > **Toepassingen en services** > **Eindpuntbeheer**.
1. Selecteer **EJB** in de lijst **Provider** en klik vervolgens op **Filter**.
1. Als u alle EJB-eindpunten wilt uitschakelen, schakelt u het selectievakje naast elk punt in de lijst in en klikt u op **Uitschakelen**.
1. Klik **Volgende** en herhaal de vorige stap voor alle EJB eindpunten. Zorg ervoor dat EJB in de kolom van de Leverancier wordt vermeld alvorens u eindpunten onbruikbaar maakt.
1. Selecteer **SOAP** in de lijst **Provider** en klik vervolgens op **Filter**.
1. Om de eindpunten van de ZEEP te verwijderen, selecteer de controledoos naast elk in de lijst en klik **Remove**. Verwijder de volgende eindpunten niet:

   * AuthenticationManagerService
   * DirectoryManagerService
   * JobManager
   * event_management_service
   * event_configuration_service
   * ProcessManager
   * TemplateManager
   * RepositoryService
   * TaskManagerService
   * TaskQueueManager
   * TaskManagerQueryService
   * WorkspaceSingleSignOn
   * ApplicationManager

1. Klik **Volgende** en herhaal de vorige stap voor de eindpunten van de ZEEP die niet in de bovengenoemde lijst zijn. Zorg ervoor dat de ZEEP in de kolom van de Leverancier wordt vermeld alvorens u eindpunten verwijdert.

## Niet-essentiële anonieme toegang tot services {#disabling-non-essential-anonymous-access-to-services} uitschakelen

Sommige services van formulierservers staan niet-geverifieerde (anonieme) aanroeping toe voor bepaalde bewerkingen. Dit betekent dat één of meerdere verrichtingen die door de dienst worden blootgesteld als om het even welke voor authentiek verklaarde gebruiker of als geen voor authentiek verklaarde gebruiker kunnen worden aangehaald.

1. Meld u aan bij de beheerconsole door de volgende URL te typen in een webbrowser:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klik op **Services > Toepassingen en services > Servicebeheer**.
1. Klik de naam van de dienst die u (bijvoorbeeld, AuthenticationManagerService) wilt onbruikbaar maken.
1. Klik **Het lusje van de Veiligheid**, schrap **Anonieme Toegang Toegestane**, en klik **sparen**.
1. Voltooi de stappen 3 en 4 voor de volgende services:

   * AuthenticationManagerService
   * EJB
   * E-mail
   * JobManager
   * Controlemap
   * UsermanagerUtilService
   * Verwijderen
   * RepositoryProviderService
   * EMCDocumentumRepositoryProvider
   * IBMFilenetRepositoryProvider
   * FormAugmenter
   * TaskManagerService
   * TaskManagerConnector
   * TaskManagerQueryService
   * TaskQueueManager
   * TaskEndpointManager
   * UserService
   * WorkspaceSearchTemplateService
   * WorkspacePropertyService
   * OutputService
   * FormsService

   Als u om het even welk van deze diensten voor verre aanroeping wilt blootstellen, zou u ook moeten overwegen onbruikbaar makend anonieme toegang voor deze diensten. Anders, kan om het even welke bezoeker met netwerktoegang tot deze dienst de dienst aanhalen zonder geldige geloofsbrieven over te gaan.

   De anonieme toegang zou voor om het even welke diensten moeten worden onbruikbaar gemaakt die niet nodig zijn. Vele interne diensten vereisen anonieme authentificatie om worden toegelaten omdat zij door potentieel om het even welke gebruiker in het systeem moeten worden aangehaald zonder vooraf geautoriseerd.

## De standaard algemene time-out {#changing-the-default-global-time-out} wijzigen

Eindgebruikers kunnen zich bij AEM Forms verifiëren via Workbench, AEM Forms-webtoepassingen of aangepaste toepassingen die de AEM Forms-serverservices aanroepen. Één globale onderbreking wordt geplaatst gebruikt om te specificeren hoe lang dergelijke gebruikers met AEM Forms (gebruikend een op SAML-Gebaseerde Bevestiging) kunnen interactie aangaan alvorens zij worden gedwongen om opnieuw voor authentiek te verklaren. De standaardinstelling is twee uur. In een productieomgeving moet de hoeveelheid tijd tot het minimaal aanvaardbare aantal minuten worden beperkt.

### Limiet voor opnieuw verifiëren {#minimize-reauthentication-time-limit} minimaliseren

1. Meld u aan bij de beheerconsole door de volgende URL te typen in een webbrowser:

   ```java
            https://[host name]:'port'/adminui
   ```

1. Klik op **Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren**.
1. Klik **Exporteren** om een config.xml- dossier met de bestaande montages van AEM Forms te produceren.
1. Open het XML-bestand in een editor en zoek de volgende gegevens:

   `<entry key=”assertionValidityInMinutes” value=”120”/>`

1. Wijzig de waarde in een waarde groter dan 5 (in minuten) en sla het bestand op.
1. Navigeer in de beheerconsole naar de pagina Configuration Files importeren en exporteren.
1. Ga de weg aan het gewijzigde config.xml- dossier in of de klik doorbladert om aan het te navigeren.
1. Klik **Importeren** om het gewijzigde bestand config.xml te uploaden en klik vervolgens op **OK**.

