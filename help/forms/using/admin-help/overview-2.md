---
title: Basisbeginselen van het beheer van certificaten en referenties
description: Leer over de grondbeginselen van het beheren van certificaten en geloofsbrieven.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 74bf0e77-f47b-475a-b2a7-52cfb3baaa22
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Basisbeginselen van het beheer van certificaten en referenties {#basics-of-managing-certificates-and-credentials}

A *referentie* bevat uw privé zeer belangrijke informatie nodig voor het ondertekenen van of het identificeren van documenten. A *certificaat* is openbare zeer belangrijke informatie die u voor vertrouwen vormt. AEM formulieren gebruiken certificaten en referenties voor verschillende doeleinden:

* Acrobat Reader DC-extensies gebruiken een referentie om Adobe Reader-gebruiksrechten in PDF-documenten in te schakelen. (Zie [ Vormende geloofsbrieven voor gebruik met de uitbreidingen van Acrobat Reader DC ](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* U kunt Rights Management zodanig configureren dat referenties alleen door vertrouwde uitgevers worden weergegeven voor gebruik in Acrobat. (Zie [ de vertoningsmontages van het Rights Management ](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings) vormen.) De gemeenschappelijke benaming (CN) moet in het certificaat aanwezig zijn.
* De handtekeningservice heeft toegang tot certificaten en referenties. Voor details op de dienst van de Handtekening, zie {de Verwijzing van de Diensten 0} [&#128279;](https://www.adobe.com/go/learn_aemforms_services_65).

**die een paarsleutel** produceren

AEM formulieren gebruiken de vertrouwde opslag om certificaten, referenties en certificaatintrekkingslijsten (CRL&#39;s) op te slaan en te beheren. Bovendien kunt u een onafhankelijk apparaat van de Module van de Veiligheid van de Hardware (HSM) gebruiken om privé sleutels op te slaan.

AEM formulieren bieden geen enkele optie om een sleutelpaar te genereren. U kunt het echter genereren met gereedschappen, zoals Java-trefgereedschappen, en het importeren in AEM formulieren Trust Store. Raadpleeg de volgende secties voor meer informatie over Java-keytool:

[ https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[ https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[ https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL](https://helpcenter.gsx.com/hc/en-us/articles/115015960428-How-to-Generate-a-Self-Signed-Certificate-and-Private-Key-using-OpenSSL)

De volgende handtekeningtypen worden ondersteund en kunnen in AEM formulieren worden geïmporteerd:

* XML-handtekening
* XMLTimeStampToken
* RFC 3161: TimeStampToken
* PKCS#7
* PKCS#1
* DSA-handtekeningen

**Verloren of gecompromitteerde sleutel van de Behandeling**

Als u vermoedt dat uw sleutel verloren is gegaan of is gewijzigd, voert u de volgende handelingen uit:

1. Informeer de certificeringsinstantie, zodat deze de gecompromitteerde sleutel toevoegt aan de certificaatintrekkingslijst om de sleutel in te trekken.
1. Verkrijg een nieuwe sleutel en de bijbehorende certificaten van de certificeringsautoriteit.
1. Onderteken de documenten die zijn ondertekend met de gecompromitteerde sleutel opnieuw gebruikend de nieuwe sleutel.
