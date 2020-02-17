---
title: XCI-configuratieopties opgeven
seo-title: XCI-configuratieopties opgeven
description: Leer hoe u XCI-configuratieopties kunt opgeven.
seo-description: Leer hoe u XCI-configuratieopties kunt opgeven.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# XCI-configuratieopties opgeven {#specifying-xci-configuration-options}

Met Forms kunt u een aangepast XCI-bestand opgeven dat wordt gebruikt voor rendering. (Zie Locaties [configureren voor Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Forms overschrijft standaard enkele van de opties die in het XCI-bestand zijn opgegeven, waaronder de volgende:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

U kunt opties selecteren waarmee de overschrijving voor de bovenstaande opties wordt geannuleerd. In dat geval gebruikt Forms de waarden die zijn opgegeven in het aangepaste XCI-bestand.

1. Klik in de beheerconsole op Services > Forms.
1. Schakel het selectievakje Systeemstandaard XCI-opties gebruiken in of uit. Wanneer deze optie is geselecteerd, gebruikt Forms de standaardwaarden voor de pakketten, de maker, de producent en de compressObjectStream-instellingen. Als deze optie is uitgeschakeld, gebruikt Forms de waarden die zijn opgegeven in het aangepaste XCI-bestand.
1. Klik op Opslaan.

