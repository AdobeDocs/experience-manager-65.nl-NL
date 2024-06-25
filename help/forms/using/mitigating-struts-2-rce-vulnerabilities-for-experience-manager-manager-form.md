---
title: Oplossing voor problemen met Struts 2-kwetsbaarheden voor Experience Manager Forms op JEE
description: Oplossing voor problemen met Struts 2-kwetsbaarheden voor Experience Manager Forms op JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
exl-id: 73b5aff2-1320-4d9a-8972-54c4fdd3a2c2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---

# Oplossingen oplossen 2 kwetsbaarheden voor Experience Manager Forms {#mitigatin-struts2-rce-vulnerabilities-for-aem-forms}

## Probleem

Er zijn kritieke beveiligingskwetsbaarheden gemeld voor Struts 2, een populair en open-source webtoepassingsframework voor het ontwikkelen van Java EE-webtoepassingen. De volgende kwetsbaarheden zijn geanalyseerd:

| Kwetsbaarheid | Wat heeft dat effect? | Wat heeft dit niet tot gevolg? |
|---|---|---|
| [CVE-2023-50164](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2023-50164) | Experience Manager 6.5 Forms op JEE (alle versies van 6.5 GA naar 6.5.19.0) | <ul><li> Experience Manager Forms Workbench (alle versies)</li> <li> Experience Manager Forms op OSGi (alle versies) </li> <li> Experience Manager Forms as a Cloud Service </li> <ul> |

## Resolutie

De volgende tabel bevat een resolutie voor alle betrokken versies:

| Geen | Huidige versie | Handeling door gebruiker |
|---|---|---|
| Experience Manager 6.5 Forms in juni | 6.5.19,0 | [Installeer het nieuwste servicepack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=en) |
| Experience Manager 6.5 Forms in juni | 6.5.13.0 - 6.5.18.0 | Gebruik een van de volgende methoden: <ul><li>  <a href="https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=en"> Installeer het nieuwste servicepack </a> </li> <li> <a href ="#use-manual-mitigation-steps"> Handmatige onderdrukkingsstappen gebruiken </a> |
| Experience Manager 6.5 Forms in juni | 6.5 - 6.5.12.0 | [Installeer het nieuwste servicepack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=en)  </br> </br> **OPMERKING:** AEM Forms ondersteunt momenteel versies 6.5.13.0 tot en met 6.5.19.0. Als u een oudere versie gebruikt, raden we u aan een upgrade naar 6.5.13.0 of een latere versie uit te voeren. Zie de opmerkingen bij de release voor instructies voor het installeren van AEM 6.5.13.0 of hoger. |

### Handmatige onderdrukkingsstappen gebruiken {#use-manual-mitigation-steps}

U kunt de handmatige matigingsstappen gebruiken om de kwestie op AEM 6.5 Server die Service Pack 13 in werking stellen aan AEM 6.5 Server van de Vorm die Service Pack 18 (6.5.13.0 - 6.5.18.0 in werking stellen) op te lossen:

1. Download de [struts-core 2.5.33 jar](https://repo1.maven.org/maven2/org/apache/struts/struts2-core/2.5.33/struts2-core-2.5.33.jar) naar een lokale map. Bijvoorbeeld C:\Users\labuser\Desktop\struts2-core-2.5.3.jar.
1. Download de AEM Forms on JEE Manual Patching Tool van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/patch_utility/archive-patcher-1.0.0.zip).
1. Pak het archief van het handmatige patchgereedschap uit. Extraheer bijvoorbeeld naar de map `/Users/labuser/Desktop/archive-patcher-1.0.0 folder`. De volgende bestanden worden geëxtraheerd:
   * archive-patcher-1.0.0.jar
   * patch-archive.bat
   * patch-archive.sh

>[!BEGINTABS]

>[!TAB Windows]

1. Sluit alle serverinstanties en locators af.

1. Open het terminalvenster en navigeer naar de map met het AEM Forms-gereedschap Handmatig repareren (geëxtraheerde bestanden).

1. Voer de volgende opdracht uit om alle bestanden te zoeken met oudere struts2-bibliotheken. Voordat u de opdracht uitvoert, vervangt u het pad in de opdracht door het pad van de AEM Forms-server:


   ```
   patch-archive.bat -root=C:\Adobe\Adobe_Experience_Manager_Forms\configurationManager\export -pattern=.*struts2-core.*jar$
   ```

   >[!NOTE]
   >
   >
   >Het hulpprogramma vereist internetverbinding omdat afhankelijkheden tijdens runtime worden gedownload. Zorg er dus voor dat u verbinding hebt met internet voordat u het hulpprogramma uitvoert.

1. Voer de volgende opdrachten in de vermelde volgorde uit voor recursieve vervanging op locatie. Voordat u de opdracht uitvoert, vervangt u het pad in de opdracht door het pad van de AEM Forms-server en de `struts2-core-2.5.33.jar` bestand.



   ```
   patch-archive.bat -root=C:\Adobe\Adobe_Experience_Manager_Forms\configurationManager\export -pattern=.*struts2-core.*jar$ -action=replace C:\Users\labuser\Desktop\struts2-core-2.5.33.jar
   ```

   Met de bovenstaande stappen worden alle oorbestanden gerepareerd met oudere struts2-bibliotheken.

1. Verwijder de implementatie van het oudere EAR en implementeer het gepatcheerde EAR-bestand, dat beschikbaar is in de exportmap, op uw toepassingsserver.

1. Start uw AEM Forms-server.

>[!TAB Linux]

1. Sluit alle serverinstanties en locators af.

1. Open het terminalvenster en navigeer naar de map met het AEM Forms-gereedschap Handmatig repareren (geëxtraheerde bestanden).

1. Voer de volgende opdracht uit om alle bestanden te zoeken met oudere struts2-bibliotheken. Voordat u de opdracht uitvoert, vervangt u het pad in de opdracht door het pad van de AEM Forms-server:


   ```
   ./patch-archive.sh -root=/opt/Adobe/Adobe_Experience_Manager_Forms/configurationManager/export/ -pattern=.*struts2-core.*jar$
   ```

   >[!NOTE]
   >
   >
   >Het hulpprogramma vereist internetverbinding omdat afhankelijkheden tijdens runtime worden gedownload. Zorg er dus voor dat u verbinding hebt met internet voordat u het hulpprogramma uitvoert.

1. Voer de volgende opdrachten in de vermelde volgorde uit voor recursieve vervanging op locatie. Voordat u de opdracht uitvoert, vervangt u het pad in de opdracht door het pad van de AEM Forms-server en de `struts2-core-2.5.33.jar` bestand.



   ```
   ./patch-archive.sh -root=/opt/Adobe/Adobe_Experience_Manager_Forms/configurationManager/export/ -pattern=.*struts2-core.*jar$ -action=replace /opt/struts2-core-2.5.33.jar
   ```

   Met de bovenstaande stappen worden alle oorbestanden gerepareerd met oudere struts2-bibliotheken.

1. Verwijder de implementatie van het oudere EAR en implementeer het gepatcheerde EAR-bestand, dat beschikbaar is in de exportmap, op uw toepassingsserver.

1. Start uw AEM Forms-server.

>[!ENDTABS]




<!-- 
### Manual patching tool 


>[!BEGINTABS]

>[!TAB Windows]

    ```
    
    patch-archive.bat [-root=dir-or-file] [-pattern=regex] [-action=list(default)|delete|replace <replacement-file>]

    ```

* **dir-or-file**: Specifies path of directory containing multiple archives to patch. The default path for AEM Forms on JEE is <>. 
* **regex**: Specifies regular expression identifying a file or an archive entry to patch. It is tested against each file's or archive entry's absolute path. For example, the pattern `.*struts2-core-2.5.30.jar$` search for all the lines that end with the exact string `struts2-core-2.5.30.jar`.
* **list**: Lists the matched files or archive entries. It recursively searches for and reports all instances of the supplied pattern matched in any entry present in any archive file (zip/jar/war/ear) inside the supplied root directory. No changes are made to any file. It is the default action of the tool, when no action is specified.
* **delete**: Deletes the matched files or archive entries. If the matched entity is an archive, deletion happens before traversing it. This prevents any potentially matching entries inside it from being reported.  
* **replace**: Substitutes the matched files or archive entries with the supplied replacement. If the matched entity is an archive, replacement happens before traversing it. This prevents any potentially matching entries inside it from being reported.

>[!TAB macOS]

    ```
    
    patch-archive.sh [-root=dir-or-file] [-pattern=regex] [-action=list(default)|delete|replace <replacement-file>]

    ```

* **dir-or-file**: Specifies path of directory containing multiple archives to patch. The default path for AEM Forms on JEE is <>. 
* **regex**: Specifies regular expression identifying a file or an archive entry to patch. It is tested against each file's or archive entry's absolute path. For example, the pattern `.*struts2-core-2.5.30.jar$` search for all the lines that end with the exact string `struts2-core-2.5.30.jar`.
* **list**: Lists the matched files or archive entries. It recursively searches for and reports all instances of the supplied pattern matched in any entry present in any archive file (zip/jar/war/ear) inside the supplied root directory. No changes are made to any file. It is the default action of the tool, when no action is specified.
* **delete**: Deletes the matched files or archive entries. If the matched entity is an archive, deletion happens before traversing it. This prevents any potentially matching entries inside it from being reported.  
* **replace**: Substitutes the matched files or archive entries with the supplied replacement. If the matched entity is an archive, replacement happens before traversing it. This prevents any potentially matching entries inside it from being reported.  

>[!TAB Linux]

    ```
    
    patch-archive.sh [-root=dir-or-file] [-pattern=regex] [-action=list(default)|delete|replace <replacement-file>]

    ```

* **dir-or-file**: Specifies path of directory containing multiple archives to patch. The default path for AEM Forms on JEE is <>. 
* **regex**: Specifies regular expression identifying a file or an archive entry to patch. It is tested against each file's or archive entry's absolute path. For example, the pattern `.*struts2-core-2.5.30.jar$` search for all the lines that end with the exact string `struts2-core-2.5.30.jar`.
* **list**: Lists the matched files or archive entries. It recursively searches for and reports all instances of the supplied pattern matched in any entry present in any archive file (zip/jar/war/ear) inside the supplied root directory. No changes are made to any file. It is the default action of the tool, when no action is specified.
* **delete**: Deletes the matched files or archive entries. If the matched entity is an archive, deletion happens before traversing it. This prevents any potentially matching entries inside it from being reported.  
* **replace**: Substitutes the matched files or archive entries with the supplied replacement. If the matched entity is an archive, replacement happens before traversing it. This prevents any potentially matching entries inside it from being reported.  



>[!ENDTABS]









-->
