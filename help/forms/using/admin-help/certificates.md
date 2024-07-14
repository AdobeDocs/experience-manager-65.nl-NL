---
title: Certificaten beheren
description: Leer hoe u een certificaat importeert en exporteert en de vertrouwensinstellingen ervan bewerkt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1fe0e7b4-6109-4f7a-8858-8237a1c5c93b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Certificaten beheren {#managing-certificates}

Met het Betrouwbaarheidsopslagbeheer kunt u certificaten die u op de server vertrouwt, importeren, bewerken en verwijderen voor validatie van digitale handtekeningen en certificaatverificatie. U kunt om het even welk aantal certificaten invoeren en uitvoeren. Nadat een certificaat is geïmporteerd, kunt u de vertrouwensinstellingen bewerken en het type vertrouwde opslag vertrouwen. Houd rekening met de volgende opties wanneer u vertrouwenswinkeltypen combineert:

* **Vertrouwen voor de Authentificatie van het Certificaat met CA:** voor bevestiging CRL, ook uitgezochte Vertrouwen voor Identiteit.
* **Vertrouwen voor de Authentificatie van het Certificaat met ICA:** Selecteer slechts Vertrouwen voor Identiteit. Een ICA zou niet voor CertificaatAuthentificatie moeten worden vertrouwd. Als u ICA voor de Authentificatie van het Certificaat vertrouwt, wordt ICA CA voor wegbouw. Als ICA voor zowel CertificaatAuthentificatie als Identiteit wordt vertrouwd, wordt het de verkoperscertificaat van CA genegeerd omdat ICA CA wordt.
* **Vertrouwen voor Server OCSP met HTTPs:** als de OSCP geënquêteerde server bij een plaats van HTTPs verblijft, moet u ook Vertrouwen voor SSL Verbindingen selecteren. Als de OSCP-geënquêteerde CRL-validatie vereist, moet u ook Vertrouwd op identiteit selecteren.
* **Hoofdmap van de Adobe:** selecteer geen SSL Verbindingen of de Types van Opslag van het Vertrouwen van de Server OCSP. Hoofdmap van Adobe wordt niet vertrouwd voor SSL-verbindingen en OCSP-server. Adobe geeft geen OCSP- en SSL-certificaten uit. Adobe Root wordt impliciet vertrouwd met een alias name=&quot;ADOBEROOT&quot;.

Alleen X509v3-certificaten worden ondersteund. Dit certificaattype kan in een binair DER-Gecodeerd dossier (.cer dossier) of een tekstdossier worden geleverd dat een Base64-Gecodeerde versie van het zelfde DER-Gecodeerde certificaat bevat (met inbegrip van X509 certificaten in het formaat van de Verbeterde Post van de Privacy (PEM)).

Certificaten die vereist zijn om de verificatie van een handtekening te voltooien, moeten zich in dezelfde opslagplaats (HSM of database) bevinden.

U kunt certificaten ook importeren en verwijderen met de Betrouwbaarheidsbeheer-API. Voor details, zie &quot;het Invoeren van certificaten gebruikend de Manager API van het Vertrouwen&quot;en &quot;het Schrappen van certificaten gebruikend de Manager API van het Vertrouwen&quot;in [ Programmering met AEM vormen ](https://www.adobe.com/go/learn_aemforms_programming_63).

## Certificaat importeren {#import-a-certificate}

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]** .
1. Klik op Importeren en selecteer een van de volgende opties onder Winkeltype vertrouwen:

   * **Vertrouwen voor SSL Verbindingen:** specificeert dat AEM vormen certificaten kunnen gebruiken om met externe systemen over SSL te verbinden.
   * **Vertrouwen voor Certificeer Handtekening:** specificeert dat de certificaten in document het ondertekenen verrichtingen voor het certificeren van auteur digitale handtekeningen worden vertrouwd.
   * **Vertrouwen voor Handtekening:** specificeert dat de certificaten in document het ondertekenen verrichtingen voor niet-auteur digitale handtekeningen worden vertrouwd.
   * **Vertrouwen voor de Authentificatie van het Certificaat:** specificeert AEM vormen gebruikt certificaten voor het voor authentiek verklaren van gebruikers die certificaat of slimme kaartauthentificatie gebruiken.
   * **Vertrouwen voor Server OCSP:** specificeert dat de AEM vormen certificaten kunnen gebruiken om met externe OCSP responders te verbinden
   * **Vertrouwen voor Identiteit:** specificeert dat de certificaten aan vertrouwensinformatie buiten hierboven gespecificeerde types kunnen worden gebruikt.

   >[!NOTE]
   >
   >De vertrouwde opslag vertrouwt impliciet een Adobe basiscertificaat voor certificaatverificatie, ondertekening, certificatie handtekening en identiteit.

1. Typ in het vak Alias de id voor het certificaat.
1. Klik op **[!UICONTROL Browse]** om het certificaat te zoeken en klik vervolgens op **[!UICONTROL OK]** .

## Een certificaat exporteren {#export-a-certificate}

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]** .
1. Klik op de aliasnaam van het certificaat dat u wilt exporteren. De pagina **[!UICONTROL Certificate Details]** wordt weergegeven.
1. Klik op **[!UICONTROL Export]** , volg de aanwijzingen om het certificaat te exporteren en klik op **[!UICONTROL OK]** .

## De vertrouwensinstellingen van een certificaat bewerken en het type vertrouwde opslag vertrouwen {#edit-a-certificate-s-trust-settings-and-trust-store-type}

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]** .
1. Klik op de aliasnaam van het certificaat dat u wilt bewerken.
1. Klik op **[!UICONTROL Update Certificate]**.
1. Als u de naam van de alias van het certificaat wilt wijzigen, typt u een nieuwe naam in het vak Alias.
1. Als u het vertrouwensarchieftype voor het certificaat wilt bijwerken, selecteert u het juiste vertrouwensarchieftype.
1. Als u de beleidsbeperkingen wilt bijwerken, typt u de beleidsinformatie in het vak Certificaatbeleid en klikt u op **[!UICONTROL OK]** .

## Een certificaat verwijderen {#delete-a-certificate}

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]** .
1. Selecteer de selectievakjes voor de certificaten die u wilt verwijderen, klik op **[!UICONTROL Delete]** en klik op **[!UICONTROL OK]** .
