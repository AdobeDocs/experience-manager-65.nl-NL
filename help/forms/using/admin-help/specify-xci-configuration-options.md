---
title: XCI-configuratieopties opgeven
seo-title: XCI-configuratieopties opgeven
description: Leer hoe u XCI-configuratieopties kunt opgeven.
seo-description: Leer hoe u XCI-configuratieopties kunt opgeven.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# XCI-configuratieopties opgeven {#specify-xci-configuration-options}

Met Output kunt u een aangepast XCI-bestand opgeven dat wordt gebruikt voor rendering. (Zie [Bestandslocaties opgeven voor Uitvoer](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) Standaard overschrijft Output enkele opties die in het XCI-bestand zijn opgegeven, waaronder de volgende:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

U kunt opties selecteren waarmee de overschrijving voor de bovenstaande opties wordt geannuleerd. In dat geval gebruikt Output de waarden die zijn opgegeven in het aangepaste XCI-bestand.

1. Klik in de beheerconsole op Services > Uitvoer.
1. Schakel het selectievakje Systeemstandaard XCI-opties gebruiken in of uit. Wanneer deze optie is geselecteerd, gebruikt Output de standaardwaarden voor de pakketten, de maker, de producent en de compressObjectStream-instellingen. Als deze optie is uitgeschakeld, gebruikt Output de waarden die zijn opgegeven in het aangepaste XCI-bestand.
1. Klik op Opslaan.

