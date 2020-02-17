---
title: Basisbeginselen van het beheer van certificaten en referenties
seo-title: Basisbeginselen van het beheer van certificaten en referenties
description: Leer over de grondbeginselen van het beheren van certificaten en geloofsbrieven.
seo-description: Leer over de grondbeginselen van het beheren van certificaten en geloofsbrieven.
uuid: f421e206-e7b5-416c-b9fb-974094f10a66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 986d16fc-4c81-4785-b1f3-fe8bd7ff669e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Basisbeginselen van het beheer van certificaten en referenties {#basics-of-managing-certificates-and-credentials}

Een *referentie* bevat uw persoonlijke sleutelgegevens die nodig zijn voor het ondertekenen of identificeren van documenten. Een *certificaat* is openbare zeer belangrijke informatie die u voor vertrouwen vormt. AEM-formulieren gebruiken certificaten en referenties voor verschillende doeleinden:

* Acrobat Reader DC-extensies gebruiken een referentie om gebruiksrechten voor Adobe Reader in PDF-documenten in te schakelen. (Zie Referenties [configureren voor gebruik met Acrobat Reader DC-extensies](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).)
* U kunt Rights Management zodanig configureren dat referenties alleen door vertrouwde uitgevers worden weergegeven voor gebruik in Acrobat. (Zie Weergave-instellingen [voor rechtenbeheer](/help/forms/using/admin-help/configuring-client-server-options.md#configure-document-security-display-settings)configureren.) De gemeenschappelijke benaming (CN) moet in het certificaat aanwezig zijn.
* De handtekeningservice heeft toegang tot certificaten en referenties. Zie [Services Reference](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service Handtekening.

**Een paarsleutel genereren**

AEM-formulieren gebruiken de vertrouwde opslag om certificaten, gegevens en certificaatintrekkingslijsten (CRL&#39;s) op te slaan en te beheren. Bovendien kunt u een onafhankelijk apparaat van de Module van de Veiligheid van de Hardware (HSM) gebruiken om privé sleutels op te slaan.

AEM-formulieren bieden geen enkele optie om een sleutelpaar te genereren. U kunt het echter genereren met gereedschappen, zoals Java-trefgereedschappen, en het importeren in AEM-formulieren Trust Store. Raadpleeg de volgende secties voor meer informatie over Java-keytool:

[https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html](https://docs.oracle.com/javase/tutorial/security/toolsign/step3.html)

[https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html](https://docs.oracle.com/cd/E19798-01/821-1841/gjrgy/index.html)

[https://blogs.adobe.com/livecycle/2010/01/creating_ssl_keys_and_certific.html](https://blogs.adobe.com/livecycle/2010/01/creating_ssl_keys_and_certific.html)

De volgende handtekeningtypen worden ondersteund en kunnen in AEM-formulieren worden geïmporteerd:

* XML-handtekening
* XMLTimeStampToken
* RFC 3161: TimeStampToken
* PKCS#7
* PKCS#1
* DSA-handtekeningen

**Vermiste of gecompromitteerde sleutel behandelen**

Als u vermoedt dat uw sleutel verloren is gegaan of is gewijzigd, voert u de volgende handelingen uit:

1. Informeer de certificeringsinstantie, zodat deze de gecompromitteerde sleutel toevoegt aan de certificaatintrekkingslijst om de sleutel in te trekken.
1. Verkrijg een nieuwe sleutel en de bijbehorende certificaten van de certificeringsautoriteit.
1. Onderteken de documenten die zijn ondertekend met de gecompromitteerde sleutel opnieuw gebruikend de nieuwe sleutel.

