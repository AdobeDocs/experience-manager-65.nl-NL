---
title: Detectie van dubbele elementen inschakelen
description: Leer hoe u dubbele elementen in AEM kunt detecteren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Detectie van dubbele elementen inschakelen {#enable-detection-of-duplicate-assets}

Als u probeert middelen te uploaden die in de Middelen van de Manager van de Ervaring van Adobe (AEM) bestaan, identificeert de dubbele opsporingseigenschap het als dubbel. Dubbele detectie is standaard uitgeschakeld. Voer de volgende stappen uit om de functie in te schakelen:

1. Open de pagina Configuratie AEM-webconsole door toegang te krijgen tot `https://[aem_server]:[port]/system/console/configMgr`.
1. Bewerk de configuratie voor de serlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecteer de optie Dupliceren **** detecteren en klik op **[!UICONTROL Opslaan]**.

   ![Selecteer de optie Duplicaat detecteren in de servlet](assets/chlimage_1-377.png)

   *Afbeelding: Selecteer de optie Duplicaat detecteren in de servlet*

De functie Dupliceren detecteren is nu ingeschakeld in AEM Assets. Wanneer een gebruiker een middel probeert te uploaden dat in AEM bestaat, controleert het systeem op conflict en wijst op het. De elementen worden geïdentificeerd met behulp van SHA-1-hash opgeslagen op `jcr:content/metadata/dam:sha1`, wat betekent dat dubbele elementen worden gedetecteerd, ongeacht de bestandsnamen.

>[!MORELIKETHIS]
>
>* [Dubbele middelen in bestaande opslagplaats (een zelfstudie van een lid van de gemeenschap)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

