---
title: Overzicht van het configureren van SSL
seo-title: Overzicht van het configureren van SSL
description: Leer over hoe te om veiligheid van mededeling te verbeteren door SSL te vormen.
seo-description: Leer over hoe te om veiligheid van mededeling te verbeteren door SSL te vormen.
uuid: 3e99d2bf-137b-45ba-8384-309624094623
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8e107abb-861f-4063-b600-c87e34639019
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Overzicht van het configureren van SSL {#overview-of-configuring-ssl}

U kunt SSL-referenties (Secure Sockets Layer) maken en SSL op de toepassingsserver configureren om de communicatie met uw toepassingsserver te verbeteren.

Voor Rights Management is als beveiligingsproduct de configuratie van SSL vereist. Wanneer het vormen van SSL certificaten, zorg ervoor dat u slechts sleutels RSA gebruikt. SSL-certificaten met DSA-sleutels worden niet ondersteund.

De verstrekte informatie is van toepassing op kant-en-klare, automatische en handmatige installaties. Het biedt een voorbeeld van een methode voor het vormen van SSL aan. U kunt andere methodes ook gebruiken die voor uw netwerk of organisatie geschikter zijn.

>[!NOTE]
>
>Het wordt aanbevolen de installatie, configuratie en implementatie van uw AEM-formuliermodules te voltooien en ervoor te zorgen dat de producten correct worden uitgevoerd voordat u SSL op de toepassingsserver configureert.

>[!NOTE]
>
>Wanneer u SSL-beveiligingscertificaten en -referenties maakt, gebruikt u dezelfde gebruikersaccountrechten als waarmee u de toepassingsserver hebt uitgevoerd. Als de toepassingsserver wordt uitgevoerd met andere gebruikersrechten, wordt het formulier mogelijk niet correct weergegeven voor PDFForm-uitvoeringen wanneer ContentRootURI naar https wijst.

Als u een LDAP-server met SSL-functionaliteit hebt, configureert u Gebruikersbeheer voor samenwerking met deze server. (Zie Gebruikersbeheer [configureren voor een LDAP-server](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server)waarvoor SSL is ingeschakeld.)
