---
title: Bekende problemen
description: Opmerkingen bij de release specifiek voor de bekende problemen met Adobe Experience Manager 6.3
uuid: 8fbdb167-833a-4179-aad1-0a26a4e5b3a7
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: d11fc727-f23a-4cde-9fa6-97e2c81b4ad0
docset: aem65
translation-type: tm+mt
source-git-commit: 0ae42d9f81df89a7e1c08fac5cce5240f14e8c60

---


# Bekende problemen {#known-issues}

Deze pagina bevat een lijst met bekende problemen uit Adobe Experience Manager 6.5 die in april 2019 is gepubliceerd.

[Neem contact op met de ondersteuningsafdeling](https://helpx.adobe.com/support/experience-manager.html) als u meer informatie nodig hebt over de bekende problemen.

## Platform {#platform}

Er wordt een probleem gerapporteerd waarbij de CRX-Quickstart en de inhoud ervan worden verwijderd.

Controleer bij elk van deze handelingen of de eigenschap &quot;*htmllibmanager.fileSystemOutputCacheLocation*&quot; nooit een lege tekenreeks is:

1. Roept &quot;*/libs/granite/ui/content/dumplibs.rebuild.html?invalidate=true*&quot; aan.
2. Upgrade uitvoeren naar AEM 6.5.
3. Uitvoeren van &quot;luie contentmigratie&quot; op AEM 6.5.

Er is een [Knowledge Base](https://helpx.adobe.com/experience-manager/kb/avoid-crx-quickstart-deletion-in-aem-6-5.html) -artikel beschikbaar met nadere details en de oplossing voor dit probleem.

## Assets {#assets}

* **Zoeken:** Er wordt geen zoekopdracht geretourneerd als de zoekreeks een of meer voorloopruimten bevat ([OAK-4786](https://issues.apache.org/jira/browse/OAK-4786))
* **Metagegevensschema** map: Nadat u een keuzerondje hebt toegevoegd, worden het veld Id en Waarde niet weergegeven zoals u had verwacht en werkt de verwijderfunctie niet. (CQ-4261144)
* Wanneer u de naam van een element wijzigt, is het niet mogelijk een witruimte in de elementnaam te gebruiken. (CQ-4266403)

## Formulieren {#forms}

* Als AEM Forms is geïnstalleerd op een Linux-besturingssysteem, werkt Digital Signature with Hardware Security Module niet. (CQ-4266721)
* (Alleen AEM-formulieren op WebSphere) De optie **Forms Workflow **> **Taak zoeken** retourneert geen resultaat als u naar een **beheerder** zoekt met **Gebruikersnaam** als zoekcriteria. (CQ-4266457)

* AEM Forms kan .tif- en .tiff-bestanden met JPEG-compressie niet converteren naar PDF-documenten. (CQ-4265972)
* De opties **AEM Forms Assets Scanner** en **Letter to Interactive Communication Migration** werken niet op de pagina Migratie **van** AEM-formulieren. (CQ-4266572)

* (Alleen JBoss 7) Wanneer u een upgrade uitvoert van een vorige versie naar AEM 6.5 Forms en de vorige versie processen had (.lca) die een kopie van het standaard verzendings- of standaardrenderproces maakten en gebruikten, worden door HTML5 Forms de vereiste handelingen (.lca) niet uitgevoerd. (CQ-4243928)
* Wanneer een formuliergegevensmodelservice wordt aangeroepen vanuit de regeleditor om de waarden van de afbeeldingskeuzescomponent dynamisch bij te werken, worden de waarden van de afbeeldingskeuzeselectie niet bijgewerkt. (CQ-4254754)
* Het installatieprogramma van de Ontwerper van de Vormen van AEM vereist de versie met 32 bits van [Visuele C++ redistributable runtime pakket 2012](https://support.microsoft.com/en-in/help/2977003/the-latest-supported-visual-c-downloads) en [Visuele C++ redistributable runtime pakketten 2013](https://support.microsoft.com/en-in/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). Zorg ervoor dat de hierboven vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start. (CQ-4265668)

* Wanneer een adaptief formulier is geconfigureerd om de waarden van een component dynamisch bij te werken en het publicatie-exemplaar dat als host fungeert voor het formulier via de verzender, werkt de functionaliteit voor het dynamisch bijwerken van waarden van een veld niet meer. Om de kwestie op te lossen, op de publicatie instantie, open CRXDE, navigeer aan /libs/fd/af/runtime/clientlibs/guideChartReducer, en creeer het bezit dat in hieronder wordt vermeld.

   * Naam: allowProxy
   * Type: Boolean
   * Waarde: true
   * Beveiligd: Onwaar
   * Verplicht: Onwaar
   * Meerdere: Onwaar
   * Automatisch gemaakt: Fase

Met deze eigenschap hebben de clientbibliotheken in de runtimemap toegang tot proxy&#39;s. (CQ-4268679)

