---
title: AEM Forms-app
seo-title: AEM Forms-app
description: Met de app AEM Forms kunnen workers in het veld adaptieve formulieren gebruiken op hun mobiele apparaten.
seo-description: Met de app AEM Forms kunnen workers in het veld adaptieve formulieren gebruiken op hun mobiele apparaten.
uuid: fac976c8-b713-4492-b153-f567e7a11ceb
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: e18aa345-034c-473b-b4c2-01678bb10616
translation-type: tm+mt
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 0%

---


# Inleiding tot AEM Forms-app {#aem-forms-app}

## Overzicht {#overview}

Met de app AEM Forms kunt u adaptieve formulieren, mobiele formulieren en formsets op mobiele apparaten synchroniseren op basis van uw server. U kunt werkstromen bepalen die de centric werkschema&#39;s van [Vormen op werkschema&#39;s OSGi](/help/forms/using/aem-forms-workflow.md) of van [Vormen op JEE](/help/forms/using/finance-reference-site-walkthrough.md#approving-the-application)zijn. Bijvoorbeeld, stelt u een bankbedrijf in werking, en gebruikt AEM Forms om klantentoepassingen en mededelingen te beheren. Uw klanten vullen een formulier in en verzenden het ter verificatie. Als u het formulier inschakelt op mobiele apparaten, kunnen uw klanten het formulier invullen in de app AEM Forms. U kunt de verificatieworkflow ook beheren door het verificatieformulier in te schakelen op mobiele apparaten. Uw veldworker kan een mobiel apparaat bij de klant dragen, de gegevens controleren en het formulier verzenden. De AEM Forms-app synchroniseert met de AEM Forms-server en haalt de formulieren op die zijn ingeschakeld voor mobiele apparaten. Als de app offline is, worden gegevens lokaal opgeslagen.

De broncode van de app AEM Forms is via Software Distribution beschikbaar voor klanten. Het broncodepakket in Softwaredistributie is beschikbaar als: `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

De app AEM Forms wordt ondersteund op iOS-, Android- en Windows-apparaten. U kunt AEM Forms-app voor Android installeren via Google Play, iOS vanuit de App Store en Windows vanuit de Windows-winkel.

    [ ![google_play](assets/google_play.png)](https://play.google.com/store/apps/details?id=com.adobe.aem.forms)
    
    [ ![app_store](assets/app_store.png)](https://itunes.apple.com/us/app/adobe-experience-manager-forms/id1129625976?ls=1&amp;mt=8)
    
    [![microsoft-badge-icon](assets/microsoft-badge-icon.png)](https://www.microsoft.com/en-us/store/p/adobe-experience-manager-forms/9nd12rlxtgtt)

Zie [De app](#customize-build-distribute)AEM Forms aanpassen, bouwen en distribueren voor informatie over het installeren, aanpassen en distribueren van de app op iOS-, Android- of Windows-apparaten.

## Vereisten {#prerequisites}

Voor de app AEM Forms is een AEM Forms-server vereist. Gebruikers kunnen formulieren die u maakt op de AEM FormsServer, invullen, opslaan als concepten en verzenden. De app maakt verbinding met de server en haalt ingeschakelde formulieren ervan op. AEM Forms app synchroniseert met de server en zodra formulieren in de app zijn geladen, kunnen gebruikers offline werken. Als de app offline is, worden gegevens opgeslagen op het apparaat en worden de gegevens gesynchroniseerd met de server wanneer de app online is.

### AEM Forms-app met servers met behulp van AEM Forms Workflow {#aem-forms-app-with-servers-using-aem-forms-workflow}

Als u een AEM Forms Workflowserver hebt, kunt u formulieren weergeven als taken in de app AEM Forms. U voert bijvoorbeeld een bankbedrijf uit en de klant vult een toepassing in om uw services te gebruiken. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en deze opslaat als verzending voor revisie. De beheerder controleert een toepassing en stuurt een verificatieaanvraag door naar de veldworker. Met de doorgestuurde toepassing wordt een verificatieformulier ingeschakeld in de app van de veldworker als taak. Uw veldworker stuurt het mobiele apparaat naar de klant en controleert de gegevens.

### AEM Forms-app met servers die Forms-centric workflow gebruiken op OSGi {#aem-forms-app-with-servers-using-forms-centric-workflow-on-osgi}

Als u een AEM Forms-server hebt, kunt u adaptieve formulieren weergeven als AEM Inbox-toepassing en taken uitvoeren in de AEM Forms-app. U voert bijvoorbeeld een bankbedrijf uit en de klant vult een toepassing in om uw services te gebruiken. De toepassing is gekoppeld aan een adaptief formulier dat informatie van uw klanten accepteert, en slaat deze op als verzending voor revisie. De beheerder evalueert de taak en keurt het verificatieverzoek aan de veldworker goed. Uw veldworker stuurt het mobiele apparaat naar de klant en controleert de gegevens.

### Standalone formulieren of AEM Forms-app met servers zonder AEM Forms Workflow {#standalone-forms-or-aem-forms-app-with-servers-without-aem-forms-workflow}

Een AEM Forms-server die geen AEM Forms Workflow gebruikt, is AEM Forms op OSGi of een zelfstandig mobiel formulier of een adaptief formulier. De app AEM Forms werkt samen met uw AEM Forms-implementatie op [OSGi](/help/sites-deploying/configuring-osgi.md). Formulieren die u inschakelt en publiceert voor de app AEM Forms, zijn beschikbaar in uw app.

De formulieren worden gedownload op uw app en zijn offline beschikbaar. U voert bijvoorbeeld een bankbedrijf uit en een klant vult een toepassing op uw site. De toepassing is een adaptief formulier dat informatie van uw klanten accepteert en dit opslaat voor revisie. De beheerder controleert het formulier en maakt een verificatieformulier in AEM-auteur. Met de beheerder kunt u het formulier synchroniseren met de app AEM Forms en het publiceren. Als het verificatieformulier beschikbaar is in de app AEM Forms, kan de veldagent een mobiel apparaat gebruiken om de gegevens van uw klant te verifiëren. Het mobiele apparaat wordt gesynchroniseerd met de server en het verificatieformulier wordt geladen in de app. De veldagent kan uw klant bezoeken, de gegevens verifiëren, gegevens opslaan als concept of het verificatieformulier verzenden. Het formulier wordt gesynchroniseerd met de server wanneer de app online is.

Uw formulier synchroniseren in de AEM Forms-app:

1. Selecteer een formulier in de auteur en klik op **[!UICONTROL View Properties]**.

1. Klik op de pagina met eigenschappen **[!UICONTROL Advanced]**.
1. Schakel onder Geavanceerd de optie in: **[!UICONTROL Sync with AEM Forms App]** tikken **[!UICONTROL Save]**.

Wanneer het formulier wordt gepubliceerd, wordt de app gesynchroniseerd met de server en wordt het formulier opgehaald. Als u meerdere formulieren wilt synchroniseren, selecteert u in de auteur meerdere formulieren in formulierbeheer en tikt u op **[!UICONTROL Sync with AEM Forms App]**.

## Ondersteuning voor mobiele apparaten {#mobile-device-support}

Zie [AEM Forms-app (voorheen bekend als Mobile Workspace)](/help/forms/using/aem-forms-jee-supported-platforms.md#aem-forms-workspace-app)

## Belangrijkste functies van de app AEM Forms {#key-features-of-aem-forms-app}

### AEM Forms-app met AEM Forms-servers {#aem-forms-app-with-aem-forms-servers}

U kunt uw app synchroniseren met de AEM Forms-server en met formulieren op uw mobiele apparaat werken.

Met de AEM Forms Workflowserver kan een formulier worden gekoppeld aan een startpunt in een workbench-proces en een AEM Inbox-toepassing. Aan een AEM Inbox-toepassing kan een adaptief formulier zijn gekoppeld. Aan een startpunt kan een adaptief formulier, HTML5-formulier of een bijbehorende indeling zijn gekoppeld. Een startpunt kan als taak worden voorgelegd of de taak kan als ontwerp worden bewaard. Voor meer informatie over verschillen tussen een toepassing AEM Inbox en een startpunt zie [Acties en mogelijkheden van vorm-centric AEM Workflows op OSGi en AEM Forms JEE werkschema](capabilities-osgi-jee-workflows.md).

Met een AEM Forms-server zonder AEM Forms-workflow wordt een formulier dat is ingeschakeld voor synchronisatie in de app, weergegeven in de AEM Forms-app. Formulieren zijn beschikbaar op het tabblad Formulieren van de app en kunnen worden verzonden of opgeslagen als concept. Aangepaste formulieren en mobiele formulieren worden ondersteund in de app.

1. **Een taak of formulier opslaan als concept**

   Met de optie Opslaan als concept slaat u een momentopname van een taak of formulier op, samen met de gegevens die zijn ingevuld en de bestanden die zijn bijgevoegd in het bijbehorende formulier. De concepten worden opgeslagen op het mobiele apparaat en gesynchroniseerd met de AEM Forms-server voor een latere opvraging.

   Zie Een taak of formulier [opslaan als concept](/help/forms/using/save-as-draft.md).

1. **Formulier opslaan als sjabloon**

   Soms blijven de gegevens in een paar velden ongewijzigd wanneer gebruikers het formulier invullen. In dergelijke gevallen kunt u in elk geval de velden invullen die identieke waarden vereisen, en het formulier of concept opslaan als een sjabloon. Telkens wanneer u een exemplaar van de sjabloon maakt, worden de opgegeven velden al gevuld met waarden die in de sjabloon zijn opgegeven. Hiermee kunt u tijd en moeite besparen die nodig zijn om het formulier in te vullen.

   Zie Formulieren [opslaan als sjablonen](/help/forms/using/save-forms-and-start-points-as-templates.md).

### Werken met taken en formulieren {#working-with-tasks-and-forms}

U kunt uw app synchroniseren met de AEM Forms Workflow-server en u kunt aan taken en formulieren werken op uw mobiele apparaat.

Een taak op het mobiele apparaat bevat een adaptief formulier, HTML5-formulier of een formulierset en kan ook bijlagen en een [overzicht-URL](/help/forms/using/getting-task-variables-summary-url.md)bevatten. Standaard worden de aan u toegewezen taken in de **[!UICONTROL Tasks]** map geplaatst. Wanneer u aan een taak werkt, kunt u de taak wijzigen en een conceptkopie van de taak opslaan op de server AEM Forms.

Een formulier op het mobiele apparaat kan een adaptief formulier of een mobiel formulier zijn. Formulieren die kunnen worden gesynchroniseerd in de formulierapp, zijn beschikbaar in de map Forms. U kunt formulieren die zijn ingeschakeld op de AEM Forms-server synchroniseren zonder AEM Forms-workflow (AEM Forms op OSGi).

Zie:

* [Een taak openen](/help/forms/using/open-task.md)
* [Werken met een formulier](/help/forms/using/working-with-form.md)

### Offline werken {#working-offline}

U kunt in de offlinemodus werken op uw mobiele apparaat. U kunt zich zelfs aanmelden bij de toepassing als er geen netwerkverbinding is en u kunt werken aan alle formulieren die tijdens de laatste onlineperiode met het apparaat waren gesynchroniseerd. Zie De app [synchroniseren voor meer informatie over het synchroniseren van formulieren](/help/forms/using/sync-app.md). Als u de aan een formulier gekoppelde bijlagen wilt synchroniseren, kunt u de bijlagen ook in de offlinemodus openen. U kunt het formulier bewerken, notities toevoegen en een formulier verzenden of opslaan in de offlinemodus. De volgende keer dat u online bent, wordt het formulier gesynchroniseerd met de AEM Forms-server.

Zie [Werken in de offlinemodus](/help/forms/using/work-offline-mode.md)voor meer informatie.

### Annotaties toevoegen {#adding-annotations}

U kunt de volgende bijlagen toevoegen aan een formulier op uw mobiele apparaat

* **Opmerkingen**- Met de functie Notities kunt u een uit de vrije hand geschreven tekst of een tekstnotitie toevoegen aan uw formulier. Zie Een notitie [toevoegen](/help/forms/using/add-attachments.md#adding-a-note)voor meer informatie.

* **Foto**- De app AEM Forms bevat een functie die de camerafunctionaliteit of de galerie van uw mobiele apparaat gebruikt. Met de fotobijlage kunt u een foto toevoegen met het bijbehorende formulier. Zie Een foto [toevoegen voor meer informatie](/help/forms/using/add-attachments.md#adding-a-photograph).

### Automatisch opslaan {#autosave}

Wanneer een gebruiker gegevens in de AEM Forms-app invoert, slaat de functie voor automatisch opslaan deze op regelmatige intervallen op. Met de functie voor automatisch opslaan in de app AEM Forms kunt u gegevensverlies voorkomen als de app wordt gesloten vanwege omstandigheden zoals een lage accu.

Zie Automatisch opslaan [gebruiken in de app](/help/forms/using/autosave-data-app.md)AEM Forms.

## Verschillen tussen de toepassingsfuncties van AEM Inbox en AEM Forms {#differences-between-aem-inbox-and-aem-forms-app-features}

Twee van de belangrijkste manieren om een Forms-centric workflow te starten, zijn met de app [AEM Inbox](/help/forms/using/manage-applications-inbox.md) en AEM Forms. De mogelijkheden van de app AEM Inbox en AEM Forms verschillen echter. AEM Inbox werkt alleen met [Forms-centric workflows](/help/forms/using/aem-forms-workflow.md) , terwijl de app AEM Forms werkt met zowel Forms-centric workflows als met procesbeheer. Voor meer informatie over verschillen tussen AEM Inbox en AEM Forms app mogelijkheden, zie [Acties en mogelijkheden van vorm-centric AEM Workflows op OSGi en AEM Forms JEE werkschema](capabilities-osgi-jee-workflows.md).

## Ondersteunde formulieren {#supported-forms}

Ondersteunde formuliertypen in de app AEM Forms:

### Aangepast formulier {#adaptive-form}

Een adaptief formulier dat dynamisch wordt aangepast aan de gebruikersinvoer, wordt ondersteund in de AEM Forms-app. Lazy loaded adaptive forms are also supported.

### Mobiel formulier {#mobile-form}

U kunt formulieren voor mobiele apparaten maken in AEM Forms. Mobiele formulieren worden weergegeven als HTML-formulieren op mobiele apparaten die zich aanpassen aan weergaveapparaten.

### Inzet {#formset}

Met formsets kunnen meerdere formulieren die betrekking hebben op een service of proces worden gegroepeerd om een bedrijfsproces te automatiseren en aan de eindgebruikers worden gepresenteerd. In dat geval kunnen de gebruikers de gehele set als één geheel invullen en hoeven afzonderlijke formulieren of processen niet te worden opgeslagen, verzonden en bijgehouden.

>[!NOTE]
>
>Vereist AEM Forms-workflow (AEM Forms op JEE).

## De werking van de app AEM Forms {#how-aem-forms-app-works}

De app AEM Forms biedt een mobiele oplossing voor veldwerkers om te werken aan formulieren die aan hen zijn toegewezen. De toepassing plaatst de volledige gegevens in de cache van de server en biedt een efficiënte gebruikerservaring door al het werk lokaal op te slaan. De gegevens van de schijf worden naar de server verzonden via tijdige synchronisatie-updates.

De app AEM Forms is een toepassing die is gebaseerd op PhoneGap 5.0 en waarin het backbonemodel efficiënt wordt gebruikt om gegevens die in de modellen zijn opgeslagen, te presenteren via weergaven. Alle native bewerkingen worden uitgevoerd via PhoneGap-plug-ins.

## De app AEM Forms aanpassen, maken en distribueren {#customize-build-distribute}

>[!NOTE]
>
>Alleen van toepassing als u de app maakt met de broncode van de AEM Forms-app.

De app AEM Forms is eenvoudig aan te passen aan de specifieke behoeften van de organisatie. De broncode voor de toepassing wordt samen met AEM Forms verstrekt. U kunt de broncode wijzigen en uw eigen oplossing voor mobiele werknemers maken. U kunt de app ook ondertekenen met uw eigen bedrijfssleutel.

### Aanpassen {#customize}

U kunt uw app aanpassen voor:

**Branding**: Wijzig het toepassingspictogram, de toepassingsnaam, start afbeeldingen en pagina&#39;s in de app AEM Forms. U kunt tekst ook wijzigen om de app voor een bepaald gebied te lokaliseren. Zie Aanpassing [branding voor meer informatie over branding van de app AEM Forms](/help/forms/using/branding-customization.md).

**Thema**: Wijzig stijlen zoals kleuren, lettertypen en spatiëring in de gebruikersinterface van de AEM Forms-app. Zie [Thema aanpassen](/help/forms/using/theme-customization.md)voor meer informatie.

**Bewegingen**: Verander bewegingen zoals veeggebaren naar rechts en vegen naar links in de gebruikersinterface van de AEM Forms-app. Zie [Bewegingsaanpassing](/help/forms/using/gesture-customization.md)voor meer informatie.

Ga voor meer informatie over het instellen van een AEM Forms-app-project voor aanpassing naar:

* [Omgeving instellen voor de app AEM Forms](/help/forms/using/setup-environment-mobile-workspace.md)
* [Het project van Visual Studio van de opstelling en bouwt Vensters app](/help/forms/using/setup-visual-studio-project-build-installer.md)
* [Xcode-project instellen en iOS-app ontwikkelen](/help/forms/using/setup-xcode-project-build-installer.md)
* [Eclipse-project instellen en Android-app ontwikkelen](/help/forms/using/setup-eclipse-project-build-installer.md)

### Samenstellen en distribueren {#build-and-distribute}

De broncode voor de AEM Forms-app kan worden geëxtraheerd uit de `adobe-lc-mobileworkspace-src.zip` code die beschikbaar is als onderdeel van het bronpakket van de AEM Forms-app voor softwaredistributie.

Voer de volgende stappen uit om de bron van de AEM Forms-app op te halen:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de Softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In het **[!UICONTROL Filters]** gedeelte:
   1. Selecteer een optie **[!UICONTROL Forms]** in de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt de **[!UICONTROL Search Downloads]** optie ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik op **[!UICONTROL Download]**.
1. Open [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.

**Voor iOS**:

Raadpleeg Het Xcode-project [instellen en de iOS-app](/help/forms/using/setup-xcode-project-build-installer.md)maken voor meer informatie over het maken van een iOS-app (.ipa).

Zie [iOS Code Signing Setup, Process en Troubleshooting](https://developer.apple.com/support/code-signing/)voor meer informatie over het ondertekenen van de AEM Forms-app met uw inrichtingsprofiel.

**Voor Android**:

Raadpleeg Het Eclipse-project [instellen en de Android-app](/help/forms/using/setup-eclipse-project-build-installer.md)ontwikkelen voor meer informatie over het maken van een Android-app (.apk).

Zie [Uw toepassingen](https://developer.android.com/tools/publishing/app-signing.html)ondertekenen voor meer informatie over het ondertekenen van de app AEM Forms.

**Voor Windows**:

Voor details op hoe te om Vensters tot stand te brengen app (.appx), verwijs [Opstelling het project van Visual Studio en bouwt Windows app](/help/forms/using/setup-visual-studio-project-build-installer.md).

Zie AEM Forms [distribueren in de app](/help/forms/using/distribute-mobile-workspace-app.md)voor meer informatie over het distribueren van de app via MDM. App-distributie via MDM is alleen van toepassing op iOS en Android.

## Aanbevelingen voor het upgraden van de mobiele werkruimte naar de app AEM Forms {#recommendations-to-upgrade-mobile-workspace-to-aem-forms-app}

Als u een upgrade uitvoert naar de nieuwste versie van de app AEM Forms, moet u de volgende punten doornemen:

* **Als u een eerdere versie van de app in de afspeelwinkel op Android** hebt geïnstalleerd, kunt u de app rechtstreeks vanuit de afspeelwinkel upgraden.

* **Als een eerdere versie van de app is gemaakt en geïnstalleerd met de broncode (van toepassing op iOS en Android)**:

   Voordat u de nieuwe app installeert, moet u al uw gegevens synchroniseren met de AEM Forms-server. Nadat de gegevens zijn gesynchroniseerd, verwijdert u de eerdere versie van de app en installeert u de nieuwe app.

