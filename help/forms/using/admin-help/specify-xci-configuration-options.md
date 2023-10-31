---
title: XCI-configuratieopties opgeven
description: Leer hoe u de XCI-configuratieopties opgeeft. U kunt aangepaste waarden voor XCI-bestanden opgeven voor Adaptief formulier, zodat dit kan worden gebruikt tijdens het genereren van formulieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 8fbff12a-4923-4151-a758-c1e44dee9160
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# XCI-configuratieopties opgeven {#specify-xci-configuration-options}

Met Output kunt u een aangepast XCI-bestand opgeven dat wordt gebruikt voor rendering. Zie [Bestandslocaties voor uitvoer opgeven](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

Standaard overschrijft Output enkele opties die in het XCI-bestand zijn opgegeven, waaronder de volgende:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

U kunt opties selecteren waarmee de overschrijving voor de bovenstaande opties wordt geannuleerd. In dat geval gebruikt Output de waarden die zijn opgegeven in het aangepaste XCI-bestand.

1. Klik in de beheerconsole op **Services** > uitvoer.
1. Schakel het selectievakje Systeemstandaard XCI-opties gebruiken in of uit. Wanneer deze optie is geselecteerd, gebruikt Output de standaardwaarden voor de pakketten, de maker, de producent en de compressObjectStream-instellingen. Als deze optie is uitgeschakeld, gebruikt Output de waarden die zijn opgegeven in het aangepaste XCI-bestand.
1. Klikken **Opslaan**.
