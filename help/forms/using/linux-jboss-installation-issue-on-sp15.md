---
title: Probleem met installatie van AEM Forms JEE 6.5.15.0-servicepack in JBoss® Linux®-omgeving
description: AEM Forms JEE 6.5.15.0-servicepack is niet correct geïnstalleerd in de JBoss® Linux®-omgeving. Eventuele patchwijzigingen worden niet toegepast op de toepassingsserver. Voeg het bestand RUP_BOM.xml toe aan de XML-map.
exl-id: 96ecbe58-a859-4432-a2d8-3d5dc0eaf989
source-git-commit: b8c9e5cd3192b51954091b677d700c51617c9460
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# AEM Forms 6.5.15.0 JEE Service Pack-installatieprobleem voor JBoss®-omgeving {#aem-forms-installation-issue-environment}

## Probleem {#issue}

AEM Forms JEE 6.5.15.0-servicepack is niet correct geïnstalleerd in de JBoss® Linux®-omgeving. In `PatchInstallerProcessing[1-9*].log` de logbestandvermelding in te dienen, `[AEM_Forms_JEE_DIR]/patch/AEMForms-6.5.0-0057/xml/RUP_BOM.xml not found! Assuming this component isn't in the installation. Skipping Processing`, wordt geregistreerd. Deze vermelding geeft aan dat het servicepakket AEM Forms JEE 6.5.15.0 niet is geïnstalleerd.

## Van toepassing op {#applies-to}

Deze oplossing is van toepassing op:
* JBoss® Linux®-omgeving

>[!NOTE]
>
> Zorg ervoor dat het AEM Forms JEE 6.5.15.0-servicepakket minstens één keer op de toepassingsserver is geïnstalleerd voordat u de stappen uitvoert van [het bestand RUP_BOM.xml toevoegen aan de XML-map](#solution-solution).

## Oplossing {#solution}

Als u het installatieprobleem wilt verhelpen met AEM Forms JEE 6.5.15.0-servicepakket, voegt u het volgende toe: `RUP_BOM.xml` bestand naar de XML-map:
1. Ga naar de map waar u de patch hebt uitgepakt `AEMForms-6.5.0-0057_jboss_linux.tar.gz`.
1. Navigeren naar `/CDROM_Installers/Linux/Disk1/InstData` locatie en locatie van de `Resource1.zip` bestand.
1. Kopieer de `Resource1.zip` bestand op een andere locatie buiten de uitgepakte map en decomprimeren `Resource1.zip` bestand.
1. Navigeren naar `/C_/builds/dev_releng/branches/rrt/aem6.5.0_rollup/tier1/install/patch/fileset_dir/xml` en kopieert u de `RUP_BOM.xml` bestand.
1. Plak het bestand RUP_BOM.xml in `[aem_forms_jee_installation_dir]/patch/AEMForms-6.5.0-0057/xml`.
1. Installeer de [AEM Forms JEE 6.5.15.0 servicepack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
