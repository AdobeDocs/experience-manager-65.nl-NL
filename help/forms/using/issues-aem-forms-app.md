---
title: Problemen met AEM Forms-app oplossen
seo-title: Problemen met AEM Forms-app oplossen
description: Meer informatie over algemene problemen met de AEM Forms-app en hoe u deze kunt oplossen.
seo-description: Meer informatie over algemene problemen met de AEM Forms-app en hoe u deze kunt oplossen.
uuid: a5cc3065-0ebf-48c0-a8fe-f1061632ca90
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 2f45a965-590b-43b1-95c6-df4b74ad15b9
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---


# Problemen met AEM Forms-app {#troubleshoot-aem-forms-app} oplossen

In dit artikel worden de foutberichten beschreven die kunnen worden weergegeven tijdens het ontwikkelen van de AEM Forms-app en de stappen die moeten worden uitgevoerd om deze op te lossen.

De volgende secties in dit artikel zijn beschikbaar:

* [Bijlageverlies voor iOS-gebruikers](/help/forms/using/issues-aem-forms-app.md#attachment-loss-for-ios-users)
* [Concepten van HTML5-formulieren die worden verzonden door gebruikers van werkruimten zijn niet zichtbaar op de portal](/help/forms/using/issues-aem-forms-app.md#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal)
* [HTML5-formulieren (niet in cache geplaatst) worden niet geladen in AEM Forms-app](/help/forms/using/issues-aem-forms-app.md#html-forms-not-cached-fail-to-load-in-aem-forms-app)
* [AEM Forms synchroniseert niet in Windows](/help/forms/using/issues-aem-forms-app.md#aem-forms-do-not-sync-on-windows)
* [Niet-ondersteunde versie van Gradle](/help/forms/using/issues-aem-forms-app.md#unsupported-version-of-gradle)
* [Compatibiliteitsproblemen met de insteekmodule Gredle en Android Gradle](/help/forms/using/issues-aem-forms-app.md#gradle-and-android-gradle-plug-in-compatibility-issues)

## Bijlageverlies voor iOS-gebruikers {#attachment-loss-for-ios-users}

De AEM Forms-app voor iOS die is geconfigureerd voor synchronisatie met AEM Forms op OSGi ondersteunt alleen bijlagen op veldniveau. Alle bijlagen moeten unieke namen hebben. Als meerdere bijlagen dezelfde naam hebben, wordt slechts één bijlage bewaard en gaan alle andere bijlagen met dezelfde naam verloren. Voer de volgende stappen uit om te voorkomen dat gebruikers op iOS-apparaten gegevens verliezen:

1. Navigeer op de verbonden server naar **Adobe Experience Manager > Tools > Operations > Web Console**.
1. Zoek en klik **Adaptieve service Formulierconfiguratie**.
1. Schakel in het dialoogvenster Adaptieve formulierconfiguratieservice **Bestandsnamen uniek maken** in.

   Als de instelling **Bestandsnamen uniek maken** is uitgeschakeld, ervaren gebruikers gegevensverlies als ze proberen adaptieve formulieren met meerdere bijlagen te verzenden.

1. Klik **Opslaan**.

## Concepten van HTML5-formulieren die worden verzonden door gebruikers van werkruimten zijn niet zichtbaar op de portal {#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal}

Voor HTML5-formulieren die zijn ingeschakeld in de AEM Forms-toepassing met **Opslaan als concept** HTML-renderprofiel, zijn de opgeslagen concepten niet zichtbaar voor gebruikers in de werkruimte. Voer de volgende stappen uit om opgeslagen concepten van HTML5-formulieren te bekijken die door werkruimtefuncties op de portal zijn verzonden:

1. Open CRXDE en login met beheerdergeloofsbrieven.

   URL: `https://<server>:<port>/lc/crx/de/index.jsp`

1. In de wortelweg van CRXDE, in de Lijst van het Toegangsbeheer onder Toegangsbeheer, klik **+**.
1. Klik in het dialoogvenster **Nieuw bericht toevoegen** op de knop Groepszoekopdracht in het veld Opdrachtgever.
1. Typ `PERM_WORKSPACE_USER` in het veld Naam van het dialoogvenster Opdrachtgever selecteren en klik op **Zoeken**.
1. Selecteer `PERM_WORKSPACE_USER` groep in de Uitgezochte Belangrijkste dialoog en klik **OK**.
1. In de Add Nieuwe de dialoogdoos van de Ingang, wordt `PERM_WORKSPACE_USER` groep geselecteerd op het Belangrijkste gebied.

   Schakel `jcr:read` bevoegdheden in voor de gebruikersgroep.

1. Klik **OK**.

## HTML5-formulieren (niet in cache geplaatst) worden niet geladen in AEM Forms-app {#html-forms-not-cached-fail-to-load-in-aem-forms-app}

Wanneer de AEM Forms-app is verbonden met een oudere versie van de AEM Forms-server, kunnen niet in de cache opgeslagen HTML5-formulieren niet worden geladen in de AEM Forms-app.

Voer de volgende stappen uit om het probleem op te lossen:

1. In auteurinstantie, navigeer aan **Adobe Experience Manager > Hulpmiddelen > vormen de Dienst van de App Offline van de Werkruimte > vormt nu**.
1. Klik in **Workspace App Offline Service**-pagina op **Handmatige broncache**.

   URL: https://&lt;server>:&lt;port>/libs/fd/workspace-offline/content/config.html

1. In **Handmatig Geheime voorgeheugen van het Middel** tabel, klik **+** knoop om een weg van CRX toe te voegen.
1. Typ in het veld **Een nieuwe bron toevoegen**: /etc.clientlibs/fd/xfaforms/I18N/en_US.js en klik **Add**.
1. Klik **Opslaan**.

## AEM Forms synchroniseert niet in Windows {#aem-forms-do-not-sync-on-windows}

In de AEM Forms App in Windows synchroniseert een formulier niet met de verbonden server als het pad van het formulier of een van de bronnen ervan meer dan 256 tekens bevat.

Wijzig het pad van het formulier en de bijbehorende bronnen om het aantal tekens te beperken tot minder dan 256 tekens.

## Niet-ondersteunde versie van Verloopgebied {#unsupported-version-of-gradle}

**Foutbericht:** het project gebruikt een niet-ondersteunde versie van Gradle.

Het foutbericht wordt weergegeven wanneer u een AEM Forms-app maakt in Android Studio. Het probleem treedt op als de versie van Gradle die niet wordt ondersteund op het systeem.

**Resolutie:** klik de Omslag van de Borstel van de  **Reparatie en herimporteer** project om de kwestie op te lossen.

![gradle_unsupported_version](assets/gradle_unsupported_version.png)

## compatibiliteitsproblemen met de insteekmodule voor grijs en Android Gradle{#gradle-and-android-gradle-plug-in-compatibility-issues}

**Foutbericht:** de versies van de insteekmodule Android Gradle en Gradle zijn niet compatibel.

Het foutbericht wordt weergegeven wanneer u **Build APK** kiest in het menu **Build** in de Android Studio-gebruikersinterface.

![gradle_plugin_compatibility](assets/gradle_plugin_compatibility.png)

**Resolutie:** Open  **Gradle Scripts** >  **gradle-wrapper.** propertiesfile en geef  **** distributionUrlproperty uit.

De Android Studio-console raadt u bijvoorbeeld aan de verloopversie te verlagen naar 3.5. Bewerk de versie in het bestand **distributionUrl** of **gradle-wrapper.properties**.

Selecteer **Build** > **Build APK** opnieuw om de fout op te lossen en het .apk-bestand te genereren.

![gradle_wrapper_properties](assets/gradle_wrapper_properties.png)

