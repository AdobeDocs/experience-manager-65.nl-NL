---
title: Hoe te om AEM Projecten te ontwikkelen gebruikend IntelliJ IDEA
description: Leer hoe u IntelliJ IDEA kunt gebruiken om Adobe Experience Manager-projecten te ontwikkelen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 5a79c79b-df65-4cb2-b9d4-eda994c992ec
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Hoe te om AEM Projecten te ontwikkelen gebruikend IntelliJ IDEA{#how-to-develop-aem-projects-using-intellij-idea}

## Overzicht {#overview}

Om met AEM ontwikkeling op IntelliJ te beginnen, zijn de volgende stappen vereist.

Elke stap wordt meer gedetailleerd uitgelegd in de rest van dit onderwerp.

* IntelliJ installeren
* Uw AEM instellen op basis van Maven
* JSP-ondersteuning voor IntelliJ in de Maven POM voorbereiden
* Importeer het Maven Project in IntelliJ

>[!NOTE]
>
>Deze handleiding is gebaseerd op de IntelliJ IDEA Ultimate Edition 12.1.4 en AEM 5.6.1.

### IntelliJ IDEA installeren {#install-intellij-idea}

Download IntelliJ IDEA van [ de pagina van Downloads bij JetBrains ](https://www.jetbrains.com/idea/download/).

Volg vervolgens de installatie-instructies op die pagina.

### Uw AEM instellen op basis van Maven {#set-up-your-aem-project-based-on-maven}

Daarna, opstelling uw project gebruikend Maven zoals die in [ wordt beschreven hoe te AEM Projecten bouwen gebruikend Apache Maven ](/help/sites-developing/ht-projects-maven.md).

Om met AEM Projecten in IDEA te beginnen werken IntelliJ, is de basisopstelling in [ Begonnen het worden in 5 Minuten ](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html) voldoende.

### JSP-ondersteuning voorbereiden voor IntelliJ IDEA {#prepare-jsp-support-for-intellij-idea}

IntelliJ IDEA kan steun in het werken met JSP ook verlenen, bijvoorbeeld:

* tagbibliotheken automatisch invullen
* bewustzijn van objecten die worden gedefinieerd door `<cq:defineObjects />` en `<sling:defineObjects />`

Voor dat om te werken, volg de instructies op [ hoe te met JSPs ](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) in [ hoe te om AEM Projecten te bouwen gebruikend Apache Maven ](/help/sites-developing/ht-projects-maven.md).

### Het Maven-project importeren {#import-the-maven-project}

1. Open de **dialoog van de Invoer** in IntelliJ IDEA door

   * het selecteren van **Project van de Invoer** op het welkome scherm als u nog geen open project hebt
   * het selecteren van **Dossier > het Project van de Invoer** van het belangrijkste menu

1. Selecteer in het dialoogvenster Importeren het POM-bestand van uw project.

   ![ chlimage_1-45 ](assets/chlimage_1-45a.png)

1. Ga verder met de standaardinstellingen zoals weergegeven in het onderstaande dialoogvenster.

   ![ chlimage_1-46 ](assets/chlimage_1-46a.png)

1. Ga door de volgende dialogen door **Volgende** te klikken en **Afwerking**.
1. U bent nu opstelling voor AEM Ontwikkeling gebruikend IntelliJ IDEA

   ![ chlimage_1-47 ](assets/chlimage_1-47a.png)

### Fouten opsporen in JSP&#39;s met IntelliJ IDEA {#debugging-jsps-with-intellij-idea}

De volgende stappen zijn noodzakelijk voor het zuiveren JSPs met IntelliJ IDEA

* Opstelling een Facet van het Web in het Project
* Installeer de JSR45 steunstop in
* Een foutopsporingsprofiel configureren
* AEM configureren voor foutopsporingsmodus

#### Opstelling een Facet van het Web in het Project {#set-up-a-web-facet-in-the-project}

IntelliJ IDEA moet begrijpen waar te om JSPs voor het zuiveren te vinden. Omdat IDEA de `content-package-maven-plugin` montages niet kan interpreteren, moet het manueel worden gevormd.

1. Ga naar **Dossier > de Structuur van het Project**
1. Selecteer de **module van de Inhoud**
1. Klik **+** boven de lijst van modules en selecteer **Web**
1. Als Folder van het Middel van het Web, selecteer `content/src/main/content/jcr_root subdirectory` van uw project zoals aangetoond in het hieronder screenshot.

![ chlimage_1-48 ](assets/chlimage_1-48a.png)

#### Installeer de JSR45 steunstop in {#install-the-jsr-support-plugin}

1. Ga naar de **Plugins** ruit in de montages IntelliJ IDEA
1. Navigeer aan de **Insteekmodule JSR45 van de Integratie** en selecteer de controledoos naast het
1. Klik **toepassen**
1. Start IntelliJ IDEA opnieuw op het verzoek om

![ chlimage_1-49 ](assets/chlimage_1-49a.png)

#### Een foutopsporingsprofiel configureren {#configure-a-debug-profile}

1. Ga naar **Looppas > geef Configuraties** uit
1. Beweeg **+** en selecteer **Ver JSR45**
1. In de configuratiedialoog, vormt de uitgezochte **** naast **Server van de Toepassing** en vormt een Generische server
1. Stel de startpagina in op een geschikte URL als u een browser wilt openen wanneer u de foutopsporing start
1. Verwijder alle **vóór lancering** taken als u vlt autosync gebruikt, of vorm aangewezen Gegraveerde taken als u niet
1. Op de **Startup/Verbinding** ruit, pas de haven, indien nodig aan
1. Kopieer de opdrachtregelargumenten die IntelliJ IDEA voorstelt

![ chlimage_1-50 ](assets/chlimage_1-50a.png) ![ chlimage_1-51 ](assets/chlimage_1-51a.png)

#### AEM configureren voor foutopsporingsmodus {#configure-aem-for-debug-mode}

De laatste vereiste stap is AEM te beginnen met de JVM-opties die door IntelliJ IDEA worden voorgesteld.

Start het AEM jar-bestand rechtstreeks en voeg deze opties bijvoorbeeld toe met de volgende opdrachtregel:

`java -Xdebug -Xrunjdwp:transport=dt_socket,address=58242,suspend=n,server=y -Xmx1024m -jar cq-quickstart-6.5.0.jar`

U kunt deze opties ook toevoegen aan uw beginscript in `crx-quickstart/bin/start`, zoals hieronder wordt weergegeven.

```shell
# ...

# default JVM options
if [ -z "$CQ_JVM_OPTS" ]; then
 CQ_JVM_OPTS='-server -Xmx1024m -Djava.awt.headless=true'
fi

CQ_JVM_OPTS="$CQ_JVM_OPTS -Xdebug -Xrunjdwp:transport=dt_socket,address=58242,suspend=n,server=y"

# ...
```

#### Foutopsporing starten {#start-debugging}

U bent nu allen opstelling voor het zuiveren van uw JSPs in AEM.

1. Selecteer **Looppas > zuivert > Uw Debug Profiel**
1. Onderbrekingspunten instellen in de componentcode
1. Een pagina openen in uw browser

![ chlimage_1-52 ](assets/chlimage_1-52a.png)

### Fouten opsporen in bundels met IntelliJ IDEA {#debugging-bundles-with-intellij-idea}

De code in bundels kan worden gezuiverd gebruikend standaard generische verre zuivert verbinding. U kunt de [ documentatie van Jetbrain op verre het zuiveren ](https://www.jetbrains.com/help/idea/remote-debugging-with-product.html#remote-interpreter) volgen.
