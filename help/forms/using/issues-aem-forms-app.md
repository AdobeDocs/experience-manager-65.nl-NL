---
title: Problemen met de AEM Forms-toepassing oplossen
description: Meer informatie over algemene problemen met de AEM Forms-app en hoe u deze kunt oplossen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: caec5fc3-db52-4bf5-8eb2-17e5189ab819
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Problemen met de AEM Forms-toepassing oplossen {#troubleshoot-aem-forms-app}

In dit artikel worden de foutberichten beschreven die kunnen worden weergegeven tijdens het ontwikkelen van de AEM Forms-app en de stappen die moeten worden uitgevoerd om deze op te lossen.

De volgende secties in dit artikel zijn beschikbaar:

* [Bijlageverlies voor iOS-gebruikers](/help/forms/using/issues-aem-forms-app.md#attachment-loss-for-ios-users)
* [Concepten van HTML5-formulieren die door gebruikers van werkruimten worden verzonden, zijn niet zichtbaar op de portal](/help/forms/using/issues-aem-forms-app.md#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal)
* [HTML5-formulieren (niet in cache geplaatst) worden niet geladen in de AEM Forms-app](/help/forms/using/issues-aem-forms-app.md#html-forms-not-cached-fail-to-load-in-aem-forms-app)
* [AEM Forms synchroniseert niet in Windows](/help/forms/using/issues-aem-forms-app.md#aem-forms-do-not-sync-on-windows)
* [Niet-ondersteunde versie van Gradle](/help/forms/using/issues-aem-forms-app.md#unsupported-version-of-gradle)
* [Compatibiliteitsproblemen met de insteekmodule Gradle en Android Gradle](/help/forms/using/issues-aem-forms-app.md#gradle-and-android-gradle-plug-in-compatibility-issues)

## Bijlageverlies voor iOS-gebruikers {#attachment-loss-for-ios-users}

AEM Forms-app voor iOS die is geconfigureerd voor synchronisatie met AEM Forms op OSGi ondersteunt alleen bijlagen op veldniveau. Alle bijlagen moeten unieke namen hebben. Als meerdere bijlagen dezelfde naam hebben, wordt slechts één bijlage bewaard en gaan alle andere bijlagen met dezelfde naam verloren. Voer de volgende stappen uit om te voorkomen dat gebruikers op iOS-apparaten gegevensverlies ervaren:

1. Voor de verbonden server, navigeer aan **Adobe Experience Manager > Hulpmiddelen > Verrichtingen > de Console van het Web**.
1. Zoeken en klikken **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** .
1. In de [!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration] dialoog, laat **toe maakt de Namen van het Dossier uniek**.

   Als **de Namen van het Dossier uniek maken** het plaatsen wordt onbruikbaar gemaakt, ervaren de gebruikers gegevensverlies als zij proberen om adaptieve vormen met veelvoudige gehechtheid voor te leggen.

1. Klik **sparen**.

## Concepten van HTML5-formulieren die door gebruikers van werkruimten worden verzonden, zijn niet zichtbaar op de portal {#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal}

Voor HTML5 vormen die in AEM Forms worden toegelaten app met **sparen als Ontwerp** HTML geeft Profiel terug, zijn de opgeslagen ontwerpen niet zichtbaar aan werkruimtegebruikers. Voer de volgende stappen uit als u opgeslagen concepten van HTML5-formulieren wilt weergeven die door werkruimtegebruikers op de portal zijn verzonden:

1. Open CRXDE en login met beheerdergeloofsbrieven.

   URL: `https://<server>:<port>/lc/crx/de/index.jsp`

1. In de wortelweg van CRXDE, in de Lijst van het Toegangsbeheer onder Toegangsbeheer, klik **+**.
1. In **voeg Nieuwe Ingang** dialoog toe, klik de knoop van het groepsonderzoek op het Belangrijkste gebied.
1. Op het gebied van de Naam van de Uitgezochte Belangrijkste dialoog, type `PERM_WORKSPACE_USER` en klik **Onderzoek**.
1. Selecteer `PERM_WORKSPACE_USER` groep in de Uitgezochte Belangrijkste dialoog en klik **O.K.**.
1. In het dialoogvenster Nieuw bericht toevoegen is de groep `PERM_WORKSPACE_USER` geselecteerd in het veld Principal.

   Schakel `jcr:read` -bevoegdheden in voor de gebruikersgroep.

1. Klik **OK**.

## HTML5-formulieren (niet in cache geplaatst) worden niet geladen in de AEM Forms-app {#html-forms-not-cached-fail-to-load-in-aem-forms-app}

Wanneer de AEM Forms-app is verbonden met een oudere versie van de AEM Forms-server, kunnen HTML5-formulieren die niet in de cache zijn geplaatst, niet worden geladen in de AEM Forms-app.

Voer de volgende stappen uit om het probleem op te lossen:

1. In auteursinstantie, navigeer aan **Adobe Experience Manager > Hulpmiddelen > Vorm Workspace App Offline Service > vormt nu**.
1. In **Workspace App Offline de pagina van de Dienst**, klik **het Geheime voorgeheugen van het Handmatige Middel**.

   URL: https://&lt;server>:&lt;port>/libs/fd/workspace-offline/content/config.html

1. In het **lusje van het Geheime voorgeheugen van het 0&rbrace; Hand &lbrace;, klik** + **knoop om een weg van CRX toe te voegen.**
1. In **voeg een Nieuw gebied van het Middel** toe, type: /etc.clientlibs/fd/xfaforms/I18N/en_US.js en klik **toevoegen**.
1. Klik **sparen**.

## AEM Forms synchroniseert niet in Windows {#aem-forms-do-not-sync-on-windows}

In de AEM Forms App in Windows synchroniseert een formulier niet met de verbonden server als het pad van het formulier of een van de bronnen ervan meer dan 256 tekens bevat.

Wijzig het pad van het formulier en de bijbehorende bronnen om het aantal tekens te beperken tot minder dan 256 tekens.

## Niet-ondersteunde versie van Gradle {#unsupported-version-of-gradle}

**Bericht van de Fout:** het project gebruikt een niet gestaafde versie van Gradle.

Het foutbericht wordt weergegeven wanneer u een AEM Forms-app maakt in Android Studio. Het probleem treedt op als de versie van Gradle die niet wordt ondersteund op het systeem.

**Resolutie:** klik **herstellen de omslag van de Gradle en hervoeren project** om de kwestie op te lossen.

![&#x200B; gradle_unsupported_version &#x200B;](assets/gradle_unsupported_version.png)

## Compatibiliteitsproblemen met de insteekmodule Gradle en Android Gradle {#gradle-and-android-gradle-plug-in-compatibility-issues}

**Bericht van de Fout:** de versies van de de Gradle stop van Android en Gradle zijn niet compatibel.

Het foutenbericht wordt getoond wanneer u **bouwt APK** optie van **bouwt** menu op het gebruikersinterface van Android Studio.

![&#x200B; gradle_plugin_compatibility &#x200B;](assets/gradle_plugin_compatibility.png)

**Resolutie:** Open **Gradle Scripts** > **gradle-wrapper.properties** dossier en geef het **distributionUrl** bezit uit.

Bijvoorbeeld, adviseert de console van Android Studio degraderend de Versie van de Gradle tot 3.5. Bewerk de versie in **distributionUrl** van **gradle-wrapper.properties** dossier.

Selecteer **bouwen** > **APK** opnieuw bouwen om de fout op te lossen en het .apk dossier te produceren.

![&#x200B; gradle_wrapper_properties &#x200B;](assets/gradle_wrapper_properties.png)
