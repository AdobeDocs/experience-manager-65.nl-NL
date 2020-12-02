---
title: Bekende problemen
description: Opmerkingen bij de release specifiek voor de bekende problemen met Adobe Experience Manager 6.5
translation-type: tm+mt
source-git-commit: 8d60e064ab50f24016c049c8d5d0fceb784c99a3
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Bekende problemen {#known-issues}

Deze pagina bevat een lijst met bekende problemen uit Adobe Experience Manager 6.5 die in april 2019 is gepubliceerd.

[Neem contact op met de ](https://helpx.adobe.com/support/experience-manager.html) ondersteuningsafdeling als u meer informatie nodig hebt over de bekende problemen.

## Platform {#platform}

* Er wordt een probleem gerapporteerd waarbij de CRX-Quickstart en de inhoud ervan worden verwijderd.

   Controleer bij elk van deze handelingen of de eigenschap `htmllibmanager.fileSystemOutputCacheLocation` geen lege tekenreeks is:

   1. `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true` aanroepen.
   2. Upgrade naar AEM 6.5.
   3. Uitvoeren van &quot;luie migratie van inhoud&quot; op AEM 6.5.

   Een [Kennisbank](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) artikel is beschikbaar met verdere details en de oplossing voor deze kwestie.

* Als u JDK 11 met AEM 6.5 instantie gebruikt, zouden sommige pagina&#39;s als leeg kunnen tonen na het opstellen van sommige pakketten. Het volgende foutbericht wordt weergegeven in het logbestand:

   ```java
   *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
   java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
   ```

Deze fout oplossen:

1. Stop de AEM instantie. Ga naar `<aem_server_path_on_server>crx-quickstart\conf` en open het `sling.properties` dossier. Adobe raadt u aan een back-up van dit bestand te maken.

1. Zoeken naar `org.osgi.framework.bootdelegation=`. Voeg `jdk.internal.reflect,jdk.internal.reflect.*` eigenschappen toe om het resultaat als te tonen.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Sla het bestand op en start de AEM opnieuw.

## Assets {#assets}

* **Zoeken:** Zoekopdracht resulteert niet in geretourneerde waarden als de zoekreeks een of meer voorloopruimten bevat ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Metagegevensschema** map: Nadat u een keuzerondje hebt toegevoegd, worden het veld Id en Waarde niet weergegeven zoals u had verwacht en werkt de verwijderfunctie niet. (CQ-4261144)
* Wanneer u de naam van een element wijzigt, is het niet mogelijk een witruimte in de elementnaam te gebruiken. (CQ-4266403)

## Forms {#forms}

* Als AEM Forms is geïnstalleerd op Linux-besturingssystemen, werkt Digital Signature met Hardware Security Module niet. (CQ-4266721)
* (Alleen AEM Forms op WebSphere) De optie **Forms Workflow** > **Taakzoekopdracht** retourneert geen resultaat als u een **Beheerder** zoekt met **Gebruikersnaam** als zoekcriteria. (CQ-4266457)

* AEM Forms kan TIF- en TIFF-bestanden met JPEG-compressie niet converteren naar PDF-documenten. (CQ-4265972)
* De **AEM Forms Assets Scanner** en **Letter to Interactive Communication Migration** opties werken niet op de pagina **AEM Forms Migration**. (CQ-4266572)

* (Alleen JBoss 7) Wanneer u een upgrade uitvoert van een vorige versie naar AEM 6.5 Forms en de vorige versie processen had (.lca) die een kopie van het standaard verzendproces of het standaard renderproces maakten en gebruikten, kan HTML5 Forms die dergelijke processen (.lca) gebruikt de vereiste handelingen niet uitvoeren. (CQ-4243928)
* Wanneer een formuliergegevensmodelservice wordt aangeroepen vanuit de regeleditor om de waarden van de afbeeldingskeuzescomponent dynamisch bij te werken, worden de waarden van de afbeeldingskeuzeselectie niet bijgewerkt. (CQ-4254754)
* Het installatieprogramma van AEM Forms Designer vereist de 32-bits versie van [Visuele C++ redistributable runtime package 2012](https://support.microsoft.com/en-in/help/2977003/the-latest-supported-visual-c-downloads) en [Visuele C++ redistributable runtime packages 2013](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Zorg ervoor dat de hierboven vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start. (CQ-4265668)

* De PDF Generator ondersteunt verificatie op basis van smartcards niet.  Wanneer een beheerder het Beleid van de Groep `Interactive Logon: Require Smart card` op een server van Vensters toelaat, worden alle bestaande gebruikers PDF Generator ongeldig gemaakt.

* Wanneer een adaptief formulier is geconfigureerd om de waarden van een component dynamisch bij te werken en het publicatie-exemplaar dat als host fungeert voor het formulier via de verzender, werkt de functionaliteit voor het dynamisch bijwerken van waarden van een veld niet meer. Als u het probleem wilt oplossen, opent u CRXDE in de publicatie-instantie, navigeert u naar `/libs/fd/af/runtime/clientlibs/guideChartReducer` en maakt u de eigenschap die hieronder wordt vermeld.

   * Naam: allowProxy
   * Type: Boolean
   * Waarde: true
   * Beveiligd: Onwaar
   * Verplicht: Onwaar
   * Meerdere: Onwaar
   * Automatisch gemaakt: Onwaar

   Met deze eigenschap hebben de clientbibliotheken in de runtimemap toegang tot proxy&#39;s. (CQ-4268679)

* Wanneer AEM Forms wordt gestart, wordt de waarschuwing `SAX Security Manager could not be setup` weergegeven.
