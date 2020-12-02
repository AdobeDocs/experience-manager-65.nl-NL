---
title: Certificaten beheren
seo-title: Certificaten beheren
description: Leer hoe u een certificaat importeert en exporteert en de vertrouwensinstellingen ervan bewerkt.
seo-description: Leer hoe u een certificaat importeert en exporteert en de vertrouwensinstellingen ervan bewerkt.
uuid: 46b1dbe5-517c-4294-bb52-cc6700a768e8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9fd531c0-5206-4be0-a450-13e0dc806068
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---


# Certificaten {#managing-certificates} beheren

Met het Betrouwbaarheidsopslagbeheer kunt u certificaten die u op de server vertrouwt, importeren, bewerken en verwijderen voor validatie van digitale handtekeningen en certificaatverificatie. U kunt om het even welk aantal certificaten invoeren en uitvoeren. Nadat een certificaat is geïmporteerd, kunt u de vertrouwensinstellingen bewerken en het type vertrouwde opslag vertrouwen. Houd rekening met de volgende opties wanneer u vertrouwenswinkeltypen combineert:

* **Vertrouwen voor certificaatverificatie met CA:** Voor CRL-validatie selecteert u ook Vertrouwd op identiteit.
* **Vertrouwen voor certificaatverificatie met ICA:Alleen vertrouwen op identiteit** selecteren. Een ICA zou niet voor CertificaatAuthentificatie moeten worden vertrouwd. Als u ICA voor de Authentificatie van het Certificaat vertrouwt, wordt ICA CA voor wegbouw. Als ICA voor zowel CertificaatAuthentificatie als Identiteit wordt vertrouwd, wordt het de verkoperscertificaat van CA genegeerd omdat ICA CA wordt.
* **Vertrouwen voor OCSP Server met HTTPs:** Als de OSCP geënquêteerde server bij een plaats van HTTPs verblijft, moet u ook Vertrouwen voor SSL Verbindingen selecteren. Als de OSCP-geënquêteerde CRL-validatie vereist, moet u ook Vertrouwd op identiteit selecteren.
* **Adobe-hoofdmap:** selecteer geen SSL-verbindingen of OCSP Server Trust Store-typen. Adobe Root wordt niet vertrouwd voor SSL-verbindingen en OCSP-server. Adobe geeft geen OCSP- en SSL-certificaten uit. Adobe Root wordt impliciet vertrouwd met een alias name=&quot;ADOBEROOT&quot;.

Alleen X509v3-certificaten worden ondersteund. Dit certificaattype kan in een binair DER-Gecodeerd dossier (.cer dossier) of een tekstdossier worden geleverd dat een Base64-Gecodeerde versie van het zelfde DER-Gecodeerde certificaat bevat (met inbegrip van X509 certificaten in het formaat van de Verbeterde Post van de Privacy (PEM)).

Certificaten die vereist zijn om een handtekeningverificatie te voltooien, moeten zich in dezelfde opslagplaats (HSM of database) bevinden.

U kunt certificaten ook importeren en verwijderen met de Betrouwbaarheidsbeheer-API. Zie &quot;Certificaten importeren met de Betrouwbaarheidsbeheer-API&quot; en &quot;Certificaten verwijderen met de Betrouwbaarheidsbeheer-API&quot; in [Programmeren met AEM formulieren](https://www.adobe.com/go/learn_aemforms_programming_63).

## Certificaat {#import-a-certificate} importeren

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]**.
1. Klik op Importeren en selecteer een van de volgende opties onder Winkeltype vertrouwen:

   * **Vertrouwen op SSL-verbindingen:** Hiermee geeft u op dat AEM certificaten kunnen gebruiken om via SSL verbinding te maken met externe systemen.
   * **Vertrouwen voor handtekening certificeren:** Hiermee geeft u op dat certificaten worden vertrouwd in documenthandtekeningbewerkingen voor certificerende auteur digitale handtekeningen.
   * **Vertrouwen voor handtekening:** Hiermee geeft u op dat certificaten worden vertrouwd in documentondertekeningsbewerkingen voor digitale handtekeningen die niet van de auteur afkomstig zijn.
   * **Vertrouwd op certificaatverificatie:** Hiermee geeft u op AEM formulieren certificaten gebruiken voor het verifiëren van gebruikers met certificaat of smartcardverificatie.
   * **Vertrouwen op OCSP-server:** Geeft aan dat AEM formulieren certificaten kunnen gebruiken om verbinding te maken met externe OCSP-responders
   * **Vertrouwd op Identiteit:** Specificeert dat de certificaten kunnen worden gebruikt om informatie buiten hierboven gespecificeerde types te vertrouwen.

   >[!NOTE]
   >
   >De vertrouwde opslag vertrouwt impliciet een Adobe-basiscertificaat voor certificaatverificatie, ondertekening, certificatie van handtekening en identiteit.

1. Typ in het vak Alias de id voor het certificaat.
1. Klik **[!UICONTROL Browse]** om van het certificaat de plaats te bepalen en dan **[!UICONTROL OK]** te klikken.

## Certificaat {#export-a-certificate} exporteren

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]**.
1. Klik op de aliasnaam van het certificaat dat u wilt exporteren. De pagina **[!UICONTROL Certificate Details]** wordt weergegeven.
1. Klik **[!UICONTROL Export]**, volg de richtingen om het certificaat uit te voeren, en klik dan **[!UICONTROL OK]**.

## De vertrouwensinstellingen van een certificaat bewerken en het winkeltype {#edit-a-certificate-s-trust-settings-and-trust-store-type} vertrouwen

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]**.
1. Klik op de aliasnaam van het certificaat dat u wilt bewerken.
1. Klik op **[!UICONTROL Update Certificate]**.
1. Als u de naam van de alias van het certificaat wilt wijzigen, typt u een nieuwe naam in het vak Alias.
1. Als u het vertrouwensarchieftype voor het certificaat wilt bijwerken, selecteert u het juiste vertrouwensarchieftype.
1. Als u de beleidsbeperkingen wilt bijwerken, typt u de beleidsinformatie in het vak Certificaatbeleid en klikt u op **[!UICONTROL OK]**.

## Certificaten {#delete-a-certificate} verwijderen

1. Klik in de beheerconsole op **[!UICONTROL Settings > Trust Store Management > Certificates]**.
1. Selecteer de selectievakjes voor de certificaten die u wilt verwijderen, klik op **[!UICONTROL Delete]** en klik vervolgens op **[!UICONTROL OK]**.

