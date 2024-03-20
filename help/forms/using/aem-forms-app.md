---
title: AEM Forms-app
description: Met de AEM Forms-app kunnen uw veldwerkers adaptieve formulieren gebruiken op hun mobiele apparaten.
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 171754a2-1ba5-42dc-b6d2-3d730807cc31
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2380'
ht-degree: 0%

---

# Inleiding tot AEM Forms-app {#aem-forms-app}

## Overzicht {#overview}

De AEM Forms-app maakt het mogelijk om adaptieve formulieren, mobiele formulieren en formsets op mobiele apparaten te synchroniseren op basis van uw server. U kunt workflows definiëren die [Centric workflows voor Forms op OSGi](/help/forms/using/aem-forms-workflow.md) of Forms-workflows op JEE. Bijvoorbeeld, leidt u een bankbedrijf, en gebruikt AEM Forms om klantentoepassingen en mededelingen te beheren. Uw klanten vullen een formulier in en verzenden het ter verificatie. Als u het formulier inschakelt op mobiele apparaten, kunnen uw klanten het formulier invullen in de AEM Forms-app. U kunt de verificatieworkflow ook beheren door het verificatieformulier in te schakelen op mobiele apparaten. Uw veldworker kan een mobiel apparaat bij de klant dragen, de gegevens controleren en het formulier verzenden. De AEM Forms-toepassing synchroniseert met de AEM Forms-server en haalt de formulieren op die zijn ingeschakeld voor mobiele apparaten. Als de app offline is, worden de gegevens lokaal opgeslagen.

De broncode van de AEM Forms-app is via Software Distribution beschikbaar voor klanten. Het broncodepakket in Softwaredistributie is beschikbaar als: `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

De AEM Forms-toepassing wordt ondersteund op iOS-, Android- en Windows-apparaten. U kunt de AEM Forms-app voor Android installeren vanuit Google Play, iOS vanuit de App Store en Windows vanuit de Windows-winkel.

    [ ![google_play](assets/google_play.png)](https://play.google.com/store/apps/details?id=com.adobe.aem.forms)
    
    [ ![app_store](assets/app_store.png)](https://itunes.apple.com/us/app/adobe-experience-manager-forms/id1129625976?ls=1&amp;mt=8)
    
    [ ![microsoft-badge-icon](assets/microsoft-badge-icon.png)](https://www.microsoft.com/en-us/store/p/adobe-experience-manager-forms/9nd12rlxtgtt)

Als u de app wilt installeren, aanpassen en distribueren op iOS-, Android- of Windows-apparaten, raadpleegt u [De AEM Forms-app aanpassen, bouwen en distribueren](#customize-build-distribute).

## Vereisten {#prerequisites}

Voor de AEM Forms-app is een AEM Forms-server vereist. Gebruikers kunnen formulieren die u op de AEM Forms-server maakt, invullen, opslaan als concepten en verzenden. De app maakt verbinding met de server en haalt ingeschakelde formulieren ervan op. AEM Forms-toepassingen worden gesynchroniseerd met de server en zodra formulieren in de app worden geladen, kunnen gebruikers offline werken. Als de app offline is, worden gegevens opgeslagen op het apparaat en worden de gegevens gesynchroniseerd met de server wanneer de app online is.

### AEM Forms-app met servers die gebruikmaken van AEM Forms Workflow {#aem-forms-app-with-servers-using-aem-forms-workflow}

Als u een AEM Forms Workflow-server hebt, kunt u formulieren weergeven als taken in de AEM Forms-app. U voert bijvoorbeeld een bankbedrijf uit en de klant vult een toepassing in om uw services te gebruiken. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en deze opslaat als verzending voor revisie. De beheerder controleert een toepassing en stuurt een verificatieaanvraag door naar de veldworker. Met de doorgestuurde toepassing wordt een verificatieformulier ingeschakeld in de app van de veldworker als taak. Uw veldworker stuurt het mobiele apparaat naar de klant en controleert de gegevens.

### AEM Forms-app met servers die Forms-centric workflow gebruiken op OSGi {#aem-forms-app-with-servers-using-forms-centric-workflow-on-osgi}

Als u een AEM Forms-server hebt, kunt u adaptieve formulieren weergeven als AEM Inbox-toepassing en taken in de AEM Forms-app. U voert bijvoorbeeld een bankbedrijf uit en de klant vult een toepassing in om uw services te gebruiken. De toepassing is gekoppeld aan een adaptief formulier dat informatie van uw klanten accepteert, en slaat deze op als verzending voor revisie. De beheerder evalueert de taak en keurt het verificatieverzoek aan de veldworker goed. Uw veldworker stuurt het mobiele apparaat naar de klant en controleert de gegevens.

### Standalone formulieren of AEM Forms-app met servers zonder AEM Forms-workflow {#standalone-forms-or-aem-forms-app-with-servers-without-aem-forms-workflow}

Een AEM Forms-server die geen AEM Forms Workflow gebruikt, is AEM Forms op OSGi of een zelfstandig mobiel formulier of adaptief formulier. De AEM Forms-app werkt met uw AEM Forms-implementatie op [OSGi](/help/sites-deploying/configuring-osgi.md). Forms die u inschakelt en publiceert voor de AEM Forms-app zijn beschikbaar in uw app.

De formulieren worden gedownload op uw app en zijn offline beschikbaar. U voert bijvoorbeeld een bankbedrijf uit en een klant vult een toepassing op uw site. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en dit opslaat voor revisie. De beheerder controleert het formulier en maakt een verificatieformulier in AEM auteur. Met de beheerder kunt u het formulier synchroniseren met de AEM Forms-app en het publiceren. Als het verificatieformulier beschikbaar is in de AEM Forms-app, kan uw veldagent een mobiel apparaat gebruiken om de gegevens van uw klant te verifiëren. Het mobiele apparaat wordt gesynchroniseerd met de server en het verificatieformulier wordt geladen in de app. De veldagent kan uw klant bezoeken, de gegevens verifiëren, gegevens opslaan als concept of het verificatieformulier verzenden. Het formulier wordt gesynchroniseerd met de server wanneer de app online is.

Uw formulier synchroniseren in AEM Forms-app:

1. Selecteer een formulier in de ontwerpversie en klik op **[!UICONTROL View Properties]**.

1. Klik op de pagina met eigenschappen **[!UICONTROL Advanced]**.
1. Schakel onder Geavanceerd de optie in: **[!UICONTROL Sync with AEM Forms App]** en selecteert u **[!UICONTROL Save]**.

Wanneer het formulier wordt gepubliceerd, wordt de app gesynchroniseerd met de server en wordt het formulier opgehaald. Als u meerdere formulieren wilt synchroniseren, selecteert u in de auteur meerdere formulieren in formulierbeheer en selecteert u **[!UICONTROL Sync with AEM Forms App]**.

## Ondersteuning voor mobiele apparaten {#mobile-device-support}

Zie [AEM Forms-app (voorheen bekend als Mobile Workspace)](/help/forms/using/aem-forms-jee-supported-platforms.md#aem-forms-workspace-app)

## Belangrijkste functies van de AEM Forms-app {#key-features-of-aem-forms-app}

### AEM Forms-app met AEM Forms-servers {#aem-forms-app-with-aem-forms-servers}

U kunt uw app synchroniseren met de AEM Forms-server en met formulieren werken op uw mobiele apparaat.

Met AEM Forms Workflow Server kan een formulier worden gekoppeld aan een startpunt in een workbench-proces en AEM Inbox-toepassing. Aan een AEM Inbox-toepassing kan een adaptief formulier zijn gekoppeld. Een startpunt kan een adaptief formulier, een HTML5-formulier of een bijbehorende indeling hebben. Een startpunt kan als taak worden voorgelegd of de taak kan als ontwerp worden bewaard. Zie voor meer informatie over de verschillen tussen een AEM Inbox-toepassing en een startpunt [Handelingen en mogelijkheden van Form-centric AEM Workflows op OSGi- en AEM Forms JEE-workflows](capabilities-osgi-jee-workflows.md).

Met een AEM Forms-server zonder AEM Forms-workflow wordt een formulier dat voor synchronisatie in de app is ingeschakeld, weergegeven in de AEM Forms-app. Forms is beschikbaar op het tabblad Forms van de app. U kunt de app verzenden of opslaan als concept. Aangepaste formulieren en mobiele formulieren worden ondersteund in de app.

1. **Een taak of formulier opslaan als concept**

   Met de optie Opslaan als concept slaat u een momentopname van een taak of formulier op, samen met de gegevens die zijn ingevuld en de bestanden die zijn bijgevoegd in het bijbehorende formulier. De concepten worden opgeslagen op het mobiele apparaat en gesynchroniseerd met de AEM Forms-server voor een later herstel.

   Zie [Een taak of formulier opslaan als concept](/help/forms/using/save-as-draft.md).

1. **Formulier opslaan als sjabloon**

   Soms blijven de gegevens in een paar velden ongewijzigd wanneer gebruikers het formulier invullen. In dergelijke gevallen kunt u in elk geval de velden invullen die identieke waarden vereisen, en het formulier of concept opslaan als een sjabloon. Telkens wanneer u een exemplaar van de sjabloon maakt, worden de opgegeven velden al gevuld met waarden die in de sjabloon zijn opgegeven. Hiermee kunt u tijd en moeite besparen die nodig zijn om het formulier in te vullen.

   Zie [Formulieren opslaan als sjablonen](/help/forms/using/save-forms-and-start-points-as-templates.md).

### Werken met taken en formulieren {#working-with-tasks-and-forms}

U kunt uw app synchroniseren met de AEM Forms Workflow-server en u kunt aan taken en formulieren werken op uw mobiele apparaat.

Een taak op het mobiele apparaat bevat een adaptief formulier, een HTML5-formulier of een formulierset en kan ook bijlagen bevatten en [overzicht-URL](/help/forms/using/getting-task-variables-summary-url.md). Standaard worden de taken die aan u zijn toegewezen, in de **[!UICONTROL Tasks]** map. Wanneer u aan een taak werkt, kunt u de taak wijzigen en een conceptkopie van de taak opslaan op de AEM Forms-server.

Een formulier op het mobiele apparaat kan een adaptief formulier of een mobiel formulier zijn. Forms dat is ingeschakeld voor synchronisatie in de formulierapp is beschikbaar in de Forms-map. U kunt formulieren die zijn ingeschakeld op de AEM Forms-server, synchroniseren zonder AEM Forms-workflow (AEM Forms op OSGi).

Zie:

* [Een taak openen](/help/forms/using/open-task.md)
* [Werken met een formulier](/help/forms/using/working-with-form.md)

### Offline werken {#working-offline}

U kunt in de offlinemodus werken op uw mobiele apparaat. U kunt zich zelfs aanmelden bij de toepassing als er geen netwerkverbinding is en u kunt werken aan alle formulieren die tijdens de laatste onlineperiode met het apparaat waren gesynchroniseerd. Zie voor meer informatie over het synchroniseren van uw formulieren [De app synchroniseren](/help/forms/using/sync-app.md). Als u de aan een formulier gekoppelde bijlagen wilt synchroniseren, kunt u de bijlagen ook in de offlinemodus openen. U kunt het formulier bewerken, notities toevoegen en een formulier verzenden of opslaan in de offline modus. De volgende keer dat u online bent, wordt het formulier gesynchroniseerd met de AEM Forms-server.

Zie voor meer informatie [Werken in de offlinemodus](/help/forms/using/work-offline-mode.md).

### Annotaties toevoegen {#adding-annotations}

U kunt de volgende bijlagen toevoegen aan een formulier op uw mobiele apparaat

* **Notities**- U kunt de functie Notities gebruiken om een vrij geschrift of een tekstnota in uw vorm toe te voegen. Zie voor meer informatie [Een notitie toevoegen](/help/forms/using/add-attachments.md#adding-a-note).

* **Afbeelding**- De AEM Forms-app bevat een functie die de camerafunctionaliteit of de galerie van uw mobiele apparaat gebruikt. Met de fotobijlage kunt u een foto toevoegen met het bijbehorende formulier. Zie voor meer informatie [Een foto toevoegen](/help/forms/using/add-attachments.md#adding-a-photograph).

### Automatisch opslaan {#autosave}

Wanneer een gebruiker gegevens in de AEM Forms-app invoert, slaat de functie voor automatisch opslaan deze op regelmatige intervallen op. Met de functie voor automatisch opslaan in de AEM Forms-app kunt u gegevensverlies voorkomen als de app wordt gesloten als gevolg van omstandigheden zoals een lage batterij.

Zie [Automatisch opslaan gebruiken in AEM Forms-app](/help/forms/using/autosave-data-app.md).

## Verschillen tussen functies van AEM Inbox- en AEM Forms-apps {#differences-between-aem-inbox-and-aem-forms-app-features}

Twee van de belangrijkste manieren om een Forms-centric workflow te starten, worden gebruikt [AEM Inbox](/help/forms/using/manage-applications-inbox.md) en AEM Forms-app. De mogelijkheden van AEM Inbox en AEM Forms-app verschillen echter. AEM Inbox werkt alleen met [Forms-gecentreerde workflows](/help/forms/using/aem-forms-workflow.md) terwijl de AEM Forms-app werkt met zowel Forms-gerichte workflows als procesbeheer. Voor meer informatie over de verschillen tussen de mogelijkheden van AEM Inbox- en AEM Forms-apps raadpleegt u [Handelingen en mogelijkheden van Form-centric AEM Workflows op OSGi- en AEM Forms JEE-workflows](capabilities-osgi-jee-workflows.md).

## Ondersteunde formulieren {#supported-forms}

Ondersteunde formuliertypen in de AEM Forms-app:

### Aangepast formulier {#adaptive-form}

Een adaptief formulier dat dynamisch wordt aangepast aan de gebruikersinvoer, wordt ondersteund in de AEM Forms-app. Lazy loaded adaptive forms are also supported.

### Mobiel formulier {#mobile-form}

In AEM Forms kunt u formulieren voor mobiele apparaten maken. Mobiele formulieren worden weergegeven als HTML-formulieren op mobiele apparaten die zich aanpassen aan weergaveapparaten.

### Inzet {#formset}

Met formsets kunnen meerdere formulieren die betrekking hebben op een service of proces worden gegroepeerd om een bedrijfsproces te automatiseren en aan de eindgebruikers worden gepresenteerd. In dat geval kunnen de gebruikers de gehele set als één geheel invullen en hoeven afzonderlijke formulieren of processen niet te worden opgeslagen, verzonden en bijgehouden.

>[!NOTE]
>
>Vereist AEM Forms Workflow (AEM Forms op JEE).

## Hoe AEM Forms-app werkt {#how-aem-forms-app-works}

De AEM Forms-app biedt een mobiele oplossing voor veldwerkers om te werken aan formulieren die aan hen zijn toegewezen. De toepassing plaatst de volledige gegevens in de cache van de server en biedt een efficiënte gebruikerservaring door al het werk lokaal op te slaan. De gegevens van de schijf worden naar de server verzonden via tijdige synchronisatie-updates.

AEM Forms-app is een PhoneGap 5.0-gebaseerde toepassing waarin het backbonemodel efficiënt wordt gebruikt om gegevens die in de modellen zijn opgeslagen via weergaven te presenteren. Alle native bewerkingen worden uitgevoerd via PhoneGap-plug-ins.

## De AEM Forms-app aanpassen, bouwen en distribueren {#customize-build-distribute}

>[!NOTE]
>
>Dit is alleen van toepassing als u de broncode van de AEM Forms-app gebruikt om de app te maken.

De AEM Forms-app is eenvoudig aan te passen aan de specifieke behoeften van de organisatie. De broncode voor de toepassing wordt samen met AEM Forms verstrekt. U kunt de broncode wijzigen en uw eigen oplossing voor mobiele werknemers maken. U kunt de app ook ondertekenen met uw eigen bedrijfssleutel.

### Aanpassen {#customize}

U kunt uw app aanpassen voor:

**Branding**: wijzig het app-pictogram, de naam van de app, start afbeeldingen en pagina&#39;s in de AEM Forms-app. U kunt tekst ook wijzigen om de app voor een bepaald gebied te lokaliseren. Ga voor meer informatie over het brandmerken van de AEM Forms-app naar [Aanpassing branding](/help/forms/using/branding-customization.md).

**Thema**: Wijzig stijlen zoals kleuren, lettertypen en spatiëring in de gebruikersinterface van de AEM Forms-app. Zie voor meer informatie [Aanpassing thema](/help/forms/using/theme-customization.md).

**Gesture**: Verander bewegingen zoals vegen naar rechts en vegen naar links in de gebruikersinterface van de AEM Forms-app. Zie voor meer informatie [Bewegingsaanpassing](/help/forms/using/gesture-customization.md).

Ga voor meer informatie over het instellen van een AEM Forms-app-project voor aanpassing naar:

* [Omgeving instellen voor AEM Forms-app](/help/forms/using/setup-environment-mobile-workspace.md)
* [Het project van Visual Studio van de opstelling en bouwt Vensters app](/help/forms/using/setup-visual-studio-project-build-installer.md)
* [Xcode-project instellen en iOS-app ontwikkelen](/help/forms/using/setup-xcode-project-build-installer.md)
* [Eclipse-project instellen en Android-app ontwikkelen](/help/forms/using/setup-eclipse-project-build-installer.md)

### Samenstellen en distribueren {#build-and-distribute}

De broncode voor de AEM Forms-toepassing kan uit het dialoogvenster `adobe-lc-mobileworkspace-src.zip` die beschikbaar is als onderdeel van het bronpakket voor de AEM Forms-app voor softwaredistributie.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

**Voor iOS**:

Raadpleeg voor meer informatie over het maken van een iOS-app (.ipa) [Het Xcode-project instellen en de iOS-app ontwikkelen](/help/forms/using/setup-xcode-project-build-installer.md).

Ga voor meer informatie over het ondertekenen van de AEM Forms-toepassing met uw inrichtingsprofiel naar [iOS Code Signing Setup, Process en Troubleshooting](https://developer.apple.com/support/code-signing/).

**Voor Android**:

Raadpleeg voor meer informatie over het maken van een Android-app (.apk) [Het Eclipse-project instellen en de Android-app ontwikkelen](/help/forms/using/setup-eclipse-project-build-installer.md).

Ga voor meer informatie over het ondertekenen van de AEM Forms-app naar [Uw toepassingen ondertekenen](https://developer.android.com/tools/publishing/app-signing.html).

**Voor Windows**:

Raadpleeg voor meer informatie over het maken van een Windows-app (.appx) [Opstelling het project van Visual Studio en bouwt Windows app](/help/forms/using/setup-visual-studio-project-build-installer.md).

Ga voor meer informatie over hoe u de app via MDM kunt distribueren naar [AEM Forms-app distribueren](/help/forms/using/distribute-mobile-workspace-app.md). App-distributie via MDM is alleen van toepassing op iOS en Android.

## Recommendations om de mobiele werkruimte te upgraden naar de AEM Forms-app {#recommendations-to-upgrade-mobile-workspace-to-aem-forms-app}

Als u een upgrade uitvoert naar de nieuwste versie van de AEM Forms-app, moet u de volgende punten doornemen:

* **Als u een eerdere versie van de app uit de afspeelwinkel op Android hebt geïnstalleerd**
U kunt de app rechtstreeks vanuit de afspeelwinkel upgraden.

* **Als een eerdere versie van de app is gemaakt en geïnstalleerd met de broncode (van toepassing op iOS en Android)**:

  Voordat u de nieuwe app installeert, moet u al uw gegevens synchroniseren met de AEM Forms-server. Nadat de gegevens zijn gesynchroniseerd, verwijdert u de eerdere versie van de app en installeert u de nieuwe app.
