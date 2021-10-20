---
title: Bekende problemen
description: Opmerkingen bij de release specifiek voor de bekende problemen met Adobe Experience Manager 6.5
exl-id: 736037cf-af8c-4ce2-969e-c100a939a038
source-git-commit: e0f024c2e1dc9fc7908382d406844575b4b38363
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Bekende problemen {#known-issues}

Deze pagina bevat een lijst met bekende problemen uit Adobe Experience Manager 6.5 die in april 2019 is gepubliceerd.

[Contact opnemen met ondersteuning](https://helpx.adobe.com/support/experience-manager.html) als u meer informatie nodig hebt over de bekende problemen.

## Platform {#platform}

* Er wordt een probleem gerapporteerd waarbij de CRX-Quickstart en de inhoud ervan worden verwijderd.

   Controleer bij elk van deze handelingen of de eigenschap `htmllibmanager.fileSystemOutputCacheLocation` is geen lege tekenreeks:

   1. Aanroepen `/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true`.
   2. Upgrade naar AEM 6.5.
   3. Uitvoeren van &quot;luie migratie van inhoud&quot; op AEM 6.5.

   A [Kennisbank](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) het artikel is beschikbaar met meer details en de oplossing voor deze kwestie .

* Als u JDK 11 met AEM 6.5 instantie gebruikt, zouden sommige pagina&#39;s als leeg kunnen tonen na het opstellen van sommige pakketten. Het volgende foutbericht wordt weergegeven in het logbestand:

   ```java
   *ERROR* [OsgiInstallerImpl] org.apache.sling.scripting.sightly bundle org.apache.sling.scripting.sightly:1.1.2.1_4_0 (558)[org.apache.sling.scripting.sightly.impl.engine.extension.use.JavaUseProvider(3345)] : Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl)
   java.lang.NoClassDefFoundError: jdk/internal/reflect/ConstructorAccessorImpl
   ```

Deze fout oplossen:

1. Stop de AEM instantie. Ga naar `<aem_server_path_on_server>crx-quickstart\conf` en opent u de `sling.properties` bestand. Adobe raadt u aan een back-up van dit bestand te maken.

1. Zoeken naar `org.osgi.framework.bootdelegation=`. Toevoegen `jdk.internal.reflect,jdk.internal.reflect.*` eigenschappen om het resultaat als weer te geven.

```java
org.osgi.framework.bootdelegation=sun.*,com.sun.*,jdk.internal.reflect,jdk.internal.reflect.*
```

1. Sla het bestand op en start de AEM opnieuw.

## Assets {#assets}

* **Zoeken:** Er worden geen resultaten geretourneerd als de zoekreeks een of meer spaties ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Metagegevensschema van map**: Nadat u een keuzerondje hebt toegevoegd, worden het veld Id en Waarde niet weergegeven zoals u had verwacht en werkt de verwijderfunctie niet. (CQ-4261144)
* Wanneer u de naam van een element wijzigt, is het niet mogelijk een witruimte in de elementnaam te gebruiken. (CQ-4266403)

## Forms {#forms}

* Als AEM Forms is geïnstalleerd op Linux-besturingssystemen, werkt Digital Signature met Hardware Security Module niet. (CQ-4266721)
* (Alleen AEM Forms op WebSphere) De **Forms Workflow** > **Zoeken in taken** Deze optie geeft geen resultaat als u naar een **Beheerder** with **Gebruikersnaam** als de zoekcriteria. (CQ-4266457)

* AEM Forms converteert TIF- en TIFF-bestanden met JPEG-compressie niet naar PDF-documenten. (CQ-4265972)
* De **AEM Forms Assets Scanner** en **Letter to Interactive Communication Migration** de opties werken niet op de **AEM Forms-migratie** pagina. (CQ-4266572)

* (Alleen JBoss 7) Wanneer u een upgrade uitvoert van een vorige versie naar AEM 6.5 Forms en de vorige versie processen had (.lca) die een kopie van het standaard verzendproces of het standaard renderproces maakten en gebruikten, voert HTML5 Forms met dergelijke processen (.lca) de vereiste handelingen niet uit. (CQ-4243928)
* Wanneer een formuliergegevensmodelservice wordt aangeroepen vanuit de regeleditor om de waarden van de afbeeldingskeuzescomponent dynamisch bij te werken, worden de waarden van de afbeeldingskeuzeselectie niet bijgewerkt. (CQ-4254754)
* Voor het installatieprogramma van AEM Forms Designer is de 32-bits versie van [Visuele C++ redistributable runtime package 2012](https://support.microsoft.com/en-in/help/2977003/the-latest-supported-visual-c-downloads) en [Visuele C++ redistributable runtime pakketten 2013](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Zorg ervoor dat de hierboven vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start. (CQ-4265668)

* PDF Generator ondersteunt geen verificatie op basis van smartcards.  Wanneer een beheerder het Beleid van de Groep toelaat `Interactive Logon: Require Smart card` op een Windows-server worden alle bestaande PDF Generator-gebruikers ongeldig gemaakt.

* Wanneer een adaptief formulier is geconfigureerd om de waarden van een component dynamisch bij te werken en het publicatie-exemplaar dat als host fungeert voor het formulier via de verzender, werkt de functionaliteit voor het dynamisch bijwerken van waarden van een veld niet meer. Als u het probleem wilt oplossen, opent u CRXDE in de publicatie-instantie en navigeert u naar `/libs/fd/af/runtime/clientlibs/guideChartReducer`en maakt u de eigenschap die hieronder wordt vermeld.

   * Naam: allowProxy
   * Type: Boolean
   * Waarde: true
   * Beveiligd: Onwaar
   * Verplicht: Onwaar
   * Meerdere: Onwaar
   * Automatisch gemaakt: Onwaar

   Met deze eigenschap hebben de clientbibliotheken in de runtimemap toegang tot proxy&#39;s. (CQ-4268679)

* Wanneer AEM Forms wordt gestart, wordt `SAX Security Manager could not be setup` verschijnt.
* Wanneer u een PDF die met AEM Forms Document Security is beveiligd opent op een Apple iOS of iPad OS met Adobe Acrobat Reader versie 20.10.00.
* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Apple iOS 15.1 biedt een oplossing voor het probleem.
