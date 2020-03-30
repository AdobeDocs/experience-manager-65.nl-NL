---
title: Beveiligde beheerinstellingen configureren voor AEM-formulieren op JEE
seo-title: Beveiligde beheerinstellingen configureren voor AEM-formulieren op JEE
description: Leer hoe te om gebruikersrekeningen en de diensten te beheren die, hoewel vereist in een privé ontwikkelomgeving, niet in een productiemilieu van Vormen AEM op JEE worden vereist.
seo-description: Leer hoe te om gebruikersrekeningen en de diensten te beheren die, hoewel vereist in een privé ontwikkelomgeving, niet in een productiemilieu van Vormen AEM op JEE worden vereist.
uuid: 04e45d06-f57d-406c-8228-15f483199430
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: d211d8b0-e75f-49c3-808d-5d0e26ad3a6b
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Beveiligde beheerinstellingen configureren voor AEM-formulieren op JEE {#configuring-secure-administration-settings-for-aem-forms-on-jee}

Leer hoe te om gebruikersrekeningen en de diensten te beheren die, hoewel vereist in een privé ontwikkelomgeving, niet in een productiemilieu van Vormen AEM op JEE worden vereist.

Over het algemeen gebruiken ontwikkelaars de productieomgeving niet om hun toepassingen te bouwen en te testen. Daarom moet u gebruikersrekeningen en de diensten beheren die, hoewel vereist in een privé ontwikkelomgeving, niet in een productiemilieu worden vereist.

Dit artikel beschrijft methodes om de algemene aanvalsoppervlakte door beleidsopties te verminderen die de Vormen AEM op JEE verstrekt.

## Het onbruikbaar maken van niet essentiële verre toegang tot de diensten {#disabling-non-essential-remote-access-to-services}

Nadat de Vormen van AEM op JEE worden geïnstalleerd en gevormd, zijn vele diensten beschikbaar voor verre aanroeping over ZEEP en Onderneming JavaBeans™ (EJB). De term ver, in dit geval, verwijst naar om het even welke bezoeker die netwerktoegang tot de havens van de Formaat van de ZEEP, EJB, of van het Bericht van de Actie (AMF) voor de toepassingsserver heeft.

Hoewel de Vormen AEM op de diensten JEE geldige geloofsbrieven vereisen om voor een erkende bezoeker worden overgegaan, zou u slechts verre toegang tot de diensten moeten toestaan die u ver toegankelijk moet zijn. Om beperkte toegankelijkheid te bereiken, zou u de reeks ver toegankelijke diensten tot het minimum mogelijk voor een werkend systeem moeten verminderen en dan verre aanroeping voor de extra diensten toelaten die u nodig hebt.

AEM-formulieren op JEE-services hebben altijd minstens SOAP-toegang nodig. Deze services zijn gewoonlijk vereist voor gebruik door Workbench, maar omvatten ook services die door de Workspace-webtoepassing worden aangeroepen.

Voltooi deze procedure gebruikend de Webpagina van Toepassingen en van de Diensten in de Console van het Beleid:

1. Meld u aan bij de beheerconsole door de volgende URL te typen in een webbrowser:

   ```as3
            https://[host name]:'port'/adminui
   ```

1. Klik op **Services > Toepassingen en services > Voorkeuren**.
1. Stel de voorkeuren in om maximaal 200 services en eindpunten op dezelfde pagina weer te geven.
1. Klik op **Services** > **Toepassingen en services** > **Eindpuntbeheer**.
1. Selecteer **EJB** in de lijst **Provider** en klik op **Filter**.
1. Als u alle EJB-eindpunten wilt uitschakelen, schakelt u het selectievakje naast elk punt in de lijst in en klikt u op **Uitschakelen**.
1. Klik op **Volgende** en herhaal de vorige stap voor alle EJB-eindpunten. Zorg ervoor dat EJB in de kolom van de Leverancier wordt vermeld alvorens u eindpunten onbruikbaar maakt.
1. Selecteer **SOAP** in de lijst **Provider** en klik op **Filter**.
1. Als u de eindpunten van de SOAP wilt verwijderen, schakelt u het selectievakje naast elk punt in de lijst in en klikt u op **Verwijderen**. Verwijder de volgende eindpunten niet:

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

1. Klik op **Volgende** en herhaal de vorige stap voor SOAP-eindpunten die zich niet in de bovenstaande lijst bevinden. Zorg ervoor dat de ZEEP in de kolom van de Leverancier wordt vermeld alvorens u eindpunten verwijdert.

## Niet-essentiële anonieme toegang tot services uitschakelen {#disabling-non-essential-anonymous-access-to-services}

Sommige services van formulierservers staan niet-geverifieerde (anonieme) aanroeping toe voor bepaalde bewerkingen. Dit betekent dat één of meerdere verrichtingen die door de dienst worden blootgesteld als om het even welke voor authentiek verklaarde gebruiker of als geen voor authentiek verklaarde gebruiker kunnen worden aangehaald.

1. Meld u aan bij de beheerconsole door de volgende URL te typen in een webbrowser:

   ```as3
            https://[host name]:'port'/adminui
   ```

1. Klik op **Services > Toepassingen en services > Servicebeheer**.
1. Klik de naam van de dienst die u (bijvoorbeeld, AuthenticationManagerService) wilt onbruikbaar maken.
1. Klik op het tabblad **** Beveiliging, schakel de optie **Anonieme toegang toegestaan** uit en klik op **Opslaan**.
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

## De standaard algemene time-out wijzigen {#changing-the-default-global-time-out}

Eindgebruikers kunnen zich via Workbench, AEM Forms-webtoepassingen of aangepaste toepassingen die AEM Forms-serverservices oproepen, verifiëren op AEM Forms. Één globale onderbreking wordt geplaatst gebruikt om te specificeren hoe lang dergelijke gebruikers met Vormen AEM (gebruikend een op SAML-Gebaseerde Bevestiging) kunnen interactie aangaan alvorens zij worden gedwongen om opnieuw voor authentiek te verklaren. De standaardinstelling is twee uur. In een productieomgeving moet de hoeveelheid tijd tot het minimaal aanvaardbare aantal minuten worden beperkt.

### Limiet voor opnieuw verifiëren minimaliseren {#minimize-reauthentication-time-limit}

1. Meld u aan bij de beheerconsole door de volgende URL te typen in een webbrowser:

   ```as3
            https://[host name]:'port'/adminui
   ```

1. Klik op **Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden** importeren en exporteren.
1. Klik op **Exporteren** om een bestand config.xml te maken met de bestaande instellingen voor AEM-formulieren.
1. Open het XML-bestand in een editor en zoek de volgende gegevens:

   `<entry key=”assertionValidityInMinutes” value=”120”/>`

1. Wijzig de waarde in een waarde groter dan 5 (in minuten) en sla het bestand op.
1. Navigeer in de beheerconsole naar de pagina Configuration Files importeren en exporteren.
1. Ga de weg aan het gewijzigde config.xml- dossier in of de klik doorbladert om aan het te navigeren.
1. Klik op **Importeren** om het gewijzigde bestand config.xml te uploaden en klik vervolgens op **OK**.

