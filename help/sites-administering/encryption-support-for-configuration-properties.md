---
title: Coderingsondersteuning voor configuratieeigenschappen
description: Leer over de encryptiesteun voor configuratieeigenschappen die in AEM worden verstrekt.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: security
exl-id: 3c3db1c8-5b22-45dd-aeaf-5cf830a9486b
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Coderingsondersteuning voor configuratieeigenschappen{#encryption-support-for-configuration-properties}

## Overzicht {#overview}

Met deze functie kunnen alle OSGi-configuratie-eigenschappen worden opgeslagen in een beveiligd versleuteld formulier in plaats van tekst te wissen. Met het formulier in de webconsolefunctie wordt gecodeerde tekst gemaakt op basis van duidelijke tekst met behulp van de systeembrede coderingshoofdsleutel.

De steun van de Insteekmodule van de Configuratie OSGi werd toegevoegd om het bezit te decrypteren alvorens het door de dienst wordt gebruikt.

>[!NOTE]
>
>De diensten die een gecodeerde waarde verwachten moeten de controle gebruiken IsProtected om te zien of wordt de waarde gecodeerd alvorens te proberen om het te decrypteren, aangezien het reeds kan gedecrypteerd zijn.

## Coderingsondersteuning inschakelen {#enabling-encryption-support}

Deze stappen tonen hoe te om het wachtwoord SMTP voor de dienst van de Post te coderen. U kunt deze stappen uitvoeren voor een OSGI-eigenschap die u wilt coderen.

1. Ga naar de AEM webconsole op *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Ga in de linkerbovenhoek naar **Hoofd - Crypto Steun**

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. De **Adobe Experience Manager Web Console Crypto-ondersteuning** wordt weergegeven.

   ![screen_shot_2018-08-01at113417am](assets/screen_shot_2018-08-01at113417am.png)

1. In de **Onbewerkte tekst** Voer de tekst in van de vertrouwelijke gegevens die u wilt beveiligen.
1. Selecteren **Protect**. De beveiligde tekst wordt weergegeven als gecodeerde tekst.

   ![screen_shot_2018-08-01at113844am](assets/screen_shot_2018-08-01at113844am.png)

1. Kopieer de beveiligde tekst uit Stap#5 en plak deze in de waarde OSGI-formulier. In dit voorbeeld worden de versleutelde **SMTP-wachtwoord** wordt toegevoegd aan de *Day CQ Mail Service*.

   ![screen_shot_2016-12-18at105809pm](assets/screen_shot_2016-12-18at105809pm.png)

1. Sla de eigenschappen van de Day CQ Mail Service op. Het SMTP-wachtwoord wordt nu verzonden als een gecodeerde waarde.

## Decoderingsondersteuning {#decryption-support}

AEM verstrekt nu een Insteekmodule van de Configuratie om configuratieeigenschappen te decrypteren. Deze AEM insteekmodule zal automatisch de duidelijke teksteigenschappen decoderen en terugwinnen.
