---
title: Probleem met installatie van AEM Forms JEE 6.5.15.0-servicepack in JBoss® Linux®-omgeving
description: AEM Forms JEE 6.5.15.0-servicepack is niet correct geïnstalleerd in de JBoss® Linux®-omgeving. Eventuele patchwijzigingen worden niet toegepast op de toepassingsserver. Voeg het bestand RUP_BOM.xml toe aan de XML-map.
exl-id: 96ecbe58-a859-4432-a2d8-3d5dc0eaf989
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# AEM Forms 6.5.15.0 JEE Service Pack-installatieprobleem voor JBoss®-omgeving {#aem-forms-installation-issue-environment}

## Probleem {#issue}

AEM Forms JEE 6.5.15.0-servicepack is niet correct geïnstalleerd in de JBoss® Linux®-omgeving. In `PatchInstallerProcessing[1-9*].log` wordt de logbestandvermelding `[AEM_Forms_JEE_DIR]/patch/AEMForms-6.5.0-0057/xml/RUP_BOM.xml not found! Assuming this component is not in the installation. Skipping Processing` vastgelegd. Deze vermelding geeft aan dat het servicepakket AEM Forms JEE 6.5.15.0 niet is geïnstalleerd.

## Van toepassing op {#applies-to}

Deze oplossing geldt voor:
* JBoss® Linux®-omgeving

>[!NOTE]
>
> Zorg ervoor dat AEM Forms JEE 6.5.15.0 de dienstpak op de toepassingsserver minstens eens geïnstalleerd is alvorens de stappen van [ uit te voeren toevoegend het RUP_BOM.xml- dossier aan de folder van XML ](#solution-solution).

## Oplossing {#solution}

Als u het installatieprobleem in het AEM Forms JEE 6.5.15.0-servicepack wilt verhelpen, voegt u het bestand `RUP_BOM.xml` toe aan de XML-map:
1. Navigeer naar de map waarin u de patch hebt uitgepakt `AEMForms-6.5.0-0057_jboss_linux.tar.gz` .
1. Navigeer naar de locatie `/CDROM_Installers/Linux/Disk1/InstData` en zoek het `Resource1.zip` -bestand.
1. Kopieer het `Resource1.zip` -bestand naar een andere locatie buiten de uitgepakte map en decomprimeer het `Resource1.zip` -bestand.
1. Navigeer naar `/C_/builds/dev_releng/branches/rrt/aem6.5.0_rollup/tier1/install/patch/fileset_dir/xml` en kopieer het `RUP_BOM.xml` -bestand.
1. Plak het bestand RUP_BOM.xml in `[aem_forms_jee_installation_dir]/patch/AEMForms-6.5.0-0057/xml` .
1. Installeer opnieuw [ AEM Forms JEE 6.5.15.0 de dienstpak ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL).
