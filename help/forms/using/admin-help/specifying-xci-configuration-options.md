---
title: XCI-configuratieopties opgeven
description: Leer hoe u de XCI-configuratieopties opgeeft. U kunt aangepaste waarden voor XCI-bestanden opgeven voor Adaptief formulier, zodat dit kan worden gebruikt tijdens het genereren van formulieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7cd10389-63e6-41f2-a132-92fd9e40a9b7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# XCI-configuratieopties opgeven {#specifying-xci-configuration-options}

Met Forms kunt u een aangepast XCI-bestand opgeven dat kan worden gebruikt voor rendering. (Zie [Locaties configureren voor Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Forms overschrijft standaard enkele van de opties die in het XCI-bestand zijn opgegeven, waaronder de volgende:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

U kunt opties selecteren waarmee de overschrijving voor de bovenstaande opties wordt geannuleerd. In dat geval gebruikt Forms de waarden die zijn opgegeven in het aangepaste XCI-bestand.

1. Klik in de beheerconsole op **Services** > **Forms**.
1. Schakel het selectievakje Systeemstandaard XCI-opties gebruiken in of uit. Wanneer deze optie is geselecteerd, gebruikt Forms de standaardwaarden voor de pakketten, de maker, de producent en de compressObjectStream-instellingen. Als deze optie is uitgeschakeld, gebruikt Forms de waarden die zijn opgegeven in het aangepaste XCI-bestand.
1. Klikken **Opslaan**.
