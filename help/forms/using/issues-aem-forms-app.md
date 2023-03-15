---
title: Problemen met AEM Forms-app oplossen
seo-title: Troubleshoot AEM Forms app
description: Meer informatie over algemene problemen met de AEM Forms-app en hoe u deze kunt oplossen.
seo-description: Learn about common issues with AEM Forms app and how to troubleshoot them.
uuid: a5cc3065-0ebf-48c0-a8fe-f1061632ca90
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 2f45a965-590b-43b1-95c6-df4b74ad15b9
exl-id: caec5fc3-db52-4bf5-8eb2-17e5189ab819
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# Problemen met AEM Forms-app oplossen {#troubleshoot-aem-forms-app}

In dit artikel worden de foutberichten beschreven die kunnen worden weergegeven tijdens het ontwikkelen van de AEM Forms-app en de stappen die moeten worden uitgevoerd om deze op te lossen.

De volgende secties in dit artikel zijn beschikbaar:

* [Bijlageverlies voor iOS-gebruikers](/help/forms/using/issues-aem-forms-app.md#attachment-loss-for-ios-users)
* [Concepten van HTML5-formulieren die door gebruikers van werkruimten worden verzonden, zijn niet zichtbaar op de portal](/help/forms/using/issues-aem-forms-app.md#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal)
* [HTML5-formulieren (niet in cache geplaatst) worden niet geladen in de AEM Forms-app](/help/forms/using/issues-aem-forms-app.md#html-forms-not-cached-fail-to-load-in-aem-forms-app)
* [AEM Forms synchroniseert niet in Windows](/help/forms/using/issues-aem-forms-app.md#aem-forms-do-not-sync-on-windows)
* [Niet-ondersteunde versie van Gradle](/help/forms/using/issues-aem-forms-app.md#unsupported-version-of-gradle)
* [Compatibiliteitsproblemen met de insteekmodule Gredle en Android Gradle](/help/forms/using/issues-aem-forms-app.md#gradle-and-android-gradle-plug-in-compatibility-issues)

## Bijlageverlies voor iOS-gebruikers {#attachment-loss-for-ios-users}

AEM Forms-app voor iOS die is geconfigureerd voor synchronisatie met AEM Forms op OSGi ondersteunt alleen bijlagen op veldniveau. Alle bijlagen moeten unieke namen hebben. Als meerdere bijlagen dezelfde naam hebben, wordt slechts één bijlage bewaard en gaan alle andere bijlagen met dezelfde naam verloren. Voer de volgende stappen uit om te voorkomen dat gebruikers op iOS-apparaten gegevensverlies ervaren:

1. Navigeer op de verbonden server naar **Adobe Experience Manager > Gereedschappen > Bewerkingen > Webconsole**.
1. Zoeken en klikken **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]**.
1. In de [!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration] dialoogvenster, inschakelen **Bestandsnamen uniek maken**.

   Indien **Bestandsnamen uniek maken** Als deze instelling is uitgeschakeld, gaan gebruikers gegevensverlies ondervinden wanneer ze proberen adaptieve formulieren met meerdere bijlagen te verzenden.

1. Klikken **Opslaan**.

## Concepten van HTML5-formulieren die door gebruikers van werkruimten worden verzonden, zijn niet zichtbaar op de portal {#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal}

Voor HTML5-formulieren ingeschakeld in de AEM Forms-app met **Opslaan als concept** HTML Renderprofiel, zijn de opgeslagen concepten niet zichtbaar voor gebruikers in de werkruimte. Voer de volgende stappen uit als u opgeslagen concepten van HTML5-formulieren wilt weergeven die door werkruimtegebruikers zijn verzonden op de portal:

1. Open CRXDE en login met beheerdergeloofsbrieven.

   URL: `https://<server>:<port>/lc/crx/de/index.jsp`

1. Klik in het hoofdpad van de CRXDE in de lijst Toegangsbeheer onder Toegangsbeheer op **+**.
1. In de **Nieuw bericht toevoegen** klikt u op de zoekknop voor de groep in het veld Principal.
1. Typ in het veld Naam van het dialoogvenster Opdrachtgever selecteren het type `PERM_WORKSPACE_USER` en klik op **Zoeken**.
1. Selecteren `PERM_WORKSPACE_USER` in het dialoogvenster Opdrachtgever selecteren en klik op **OK**.
1. In het dialoogvenster Nieuw bericht toevoegen `PERM_WORKSPACE_USER` wordt geselecteerd in het veld Principal.

   Inschakelen `jcr:read` rechten voor de gebruikersgroep.

1. Klikken **OK**.

## HTML5-formulieren (niet in cache geplaatst) worden niet geladen in de AEM Forms-app {#html-forms-not-cached-fail-to-load-in-aem-forms-app}

Wanneer de AEM Forms-app is verbonden met een oudere versie van de AEM Forms-server, kunnen HTML5-formulieren die niet in de cache zijn geplaatst, niet worden geladen in de AEM Forms-app.

Voer de volgende stappen uit om het probleem op te lossen:

1. Ga in de auteur naar **Adobe Experience Manager > Tools > Configure Workspace App Offline Service > Configure Now**.
1. In **Workspace App Offline Service** pagina, klikt u op **Handmatige broncache**.

   URL: https://&lt;server>:&lt;port>/libs/fd/workspace-offline/content/config.html

1. In de **Handmatige broncache** klikt u op de knop **+** om een CRX-pad toe te voegen.
1. In de **Een nieuwe bron toevoegen** veld, type: /etc.clientlibs/fd/xfaforms/I18N/en_US.js en klik op **Toevoegen**.
1. Klikken **Opslaan**.

## AEM Forms synchroniseert niet in Windows {#aem-forms-do-not-sync-on-windows}

In de AEM Forms App in Windows synchroniseert een formulier niet met de verbonden server als het pad van het formulier of een van de bronnen ervan meer dan 256 tekens bevat.

Wijzig het pad van het formulier en de bijbehorende bronnen om het aantal tekens te beperken tot minder dan 256 tekens.

## Niet-ondersteunde versie van Gradle {#unsupported-version-of-gradle}

**Foutbericht:** Het project gebruikt een niet-ondersteunde versie van Gradle.

Het foutbericht wordt weergegeven wanneer u een AEM Forms-app maakt in Android Studio. Het probleem treedt op als de versie van Gradle die niet wordt ondersteund op het systeem.

**Resolutie:** Klikken **Omslag van de Korrel herstellen en project opnieuw invoeren** om het probleem op te lossen.

![gradle_unsupported_version](assets/gradle_unsupported_version.png)

## Compatibiliteitsproblemen met de insteekmodule Gredle en Android Gradle {#gradle-and-android-gradle-plug-in-compatibility-issues}

**Foutbericht:** De versies van de insteekmodule Android Gradle en Gradle zijn niet compatibel.

Het foutbericht wordt weergegeven wanneer u **APK samenstellen** van de **Opbouwen** in de Android Studio-gebruikersinterface.

![gradle_plugin_compatibility](assets/gradle_plugin_compatibility.png)

**Resolutie:** Openen **Gradle Scripts** > **gradlewrapper.properties** en bewerk de **distributionUrl** eigenschap.

De Android Studio-console raadt u bijvoorbeeld aan de verloopversie te verlagen naar 3.5. De versie bewerken in **distributionUrl** van **gradlewrapper.properties** bestand.

Selecteren **Opbouwen** > **APK samenstellen** om de fout op te lossen en het .apk-bestand te genereren.

![gradle_wrapper_properties](assets/gradle_wrapper_properties.png)
