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
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# XCI-configuratieopties opgeven {#specifying-xci-configuration-options}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Met Forms kunt u een aangepast XCI-bestand opgeven dat kan worden gebruikt voor rendering. (Zie [&#x200B; Vormende plaatsen voor Forms &#x200B;](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Door gebrek, treedt Forms enkele opties met voeten die in het XCI dossier, met inbegrip van het volgende worden gespecificeerd:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

U kunt opties selecteren waarmee de overschrijving voor de bovenstaande opties wordt geannuleerd. In dat geval gebruikt Forms de waarden die zijn opgegeven in het aangepaste XCI-bestand.

1. In beleidsconsole, klik **Diensten** > **Forms**.
1. Schakel het selectievakje Systeemstandaard XCI-opties gebruiken in of uit. Wanneer deze optie is geselecteerd, gebruikt Forms de standaardwaarden voor de pakketten, de maker, de producent en de compressObjectStream-instellingen. Als deze optie is uitgeschakeld, gebruikt Forms de waarden die zijn opgegeven in het aangepaste XCI-bestand.
1. Klik **sparen**.
