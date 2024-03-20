---
title: SAML 2.0-verificatiehandler
description: Leer over de Handler van de Authentificatie SAML 2.0 in AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 8e54bccf-0ff1-448d-a237-ec42fd3bfa23
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# SAML 2.0-verificatiehandler{#saml-authentication-handler}

AEM schepen [SAML](https://saml.xml.org/saml-specifications) verificatiehandler. Deze handler ondersteunt de [SAML](https://saml.xml.org/saml-specifications) 2.0 het Protocol van het Verzoek van de Authentificatie (Web-SSO profiel) gebruikend `HTTP POST` binding.

Het steunt:

* ondertekening en versleuteling van berichten
* automatisch maken van gebruikers
* groepen synchroniseren met bestaande groepen in AEM
* Serviceleverancier en identiteitsprovider hebben verificatie gestart

Deze handler slaat het gecodeerde SAML-responsbericht op in het user-node ( `usernode/samlResponse`) om de communicatie met een externe serviceprovider te vergemakkelijken.

>[!NOTE]
>
>Zie [een demonstratie van AEM en SAML-integratie](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17481.html).

## De SAML 2.0-verificatiehandler configureren {#configuring-the-saml-authentication-handler}

De [Webconsole](/help/sites-deploying/configuring-osgi.md) verleent toegang tot [SAML](https://saml.xml.org/saml-specifications) 2.0 de geroepen Configuratie van de Handler van de Authentificatie **Adobe graniet SAML 2.0-verificatiehandler**. De volgende eigenschappen kunnen worden ingesteld.

>[!NOTE]
>
>De SAML 2.0-verificatiehandler is standaard uitgeschakeld. Stel ten minste een van de volgende eigenschappen in om de handler in te schakelen:
>
>* De POST-URL van Identiteitsprovider of de IDP-URL.
>* De Service Provider Entiteit ID.
>

>[!NOTE]
>
>SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de Identiteitsprovider in de TrustStore opgeeft. Zie [Het IdP-certificaat toevoegen aan de TrustStore](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore) voor meer informatie.

**Pad** Pad naar opslagplaats waarvoor deze verificatiehandler door Sling moet worden gebruikt. Als dit leeg is, zal de authentificatiemanager worden onbruikbaar gemaakt.

**Servicereeks** OSGi de Rangschikkende waarde van de Dienst van het Kader om op de orde te wijzen waarin om deze dienst te roepen. Dit is een geheel getal waarbij hogere waarden een hogere prioriteit aangeven.

**IdP-certificaatalias** De alias van het certificaat van IdP in globale truststore. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld. Zie het hoofdstuk &quot;Add the IdP Certificate to the AEM TrustStore&quot; hieronder over hoe u het instelt.

**IDP-URL** URL van IDP waar het verzoek van de Authentificatie van SAML zou moeten worden verzonden naar. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

>[!CAUTION]
>
>De hostnaam van de identiteitsprovider moet worden toegevoegd aan de **Filter Apache Sling Referrer** OSGi-configuratie. Zie de [Webconsole](/help/sites-deploying/configuring-osgi.md) voor meer informatie.

**Entiteit Service Provider ID** Id die deze serviceprovider op unieke wijze identificeert met de identiteitsprovider. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

**Standaardomleiding** De standaardlocatie waarnaar moet worden omgeleid na geslaagde verificatie.

>[!NOTE]
>
>Deze locatie wordt alleen gebruikt als de `request-path` cookie is niet ingesteld. Als u om het even welke pagina onder de gevormde weg zonder geldig login-teken verzoekt, wordt het gevraagde weg opgeslagen in een koekje
>en de browser wordt opnieuw omgeleid naar deze locatie nadat de verificatie is voltooid.

**Kenmerk gebruikersnaam** De naam van het kenmerk met de gebruikers-id die wordt gebruikt voor het verifiëren en maken van de gebruiker in de CRX-opslagruimte.

>[!NOTE]
>
>De gebruikersnaam wordt niet overgenomen uit de `saml:Subject` knooppunt van de SAML-bewering, maar vanuit dit `saml:Attribute`.

**Codering gebruiken** Of deze authentificatiemanager gecodeerde beweringen van SAML verwacht of niet.

**CRX-gebruikers automatisch maken** Al dan niet automatisch niet-bestaande gebruikers in de repository maken na succesvolle verificatie.

>[!CAUTION]
>
>Als het automatisch maken van CRX-gebruikers is uitgeschakeld, moeten de gebruikers handmatig worden gemaakt.

**Toevoegen aan groepen** Of een gebruiker automatisch aan CRX groepen na succesvolle authentificatie zou moeten worden toegevoegd of niet.

**Groepslidmaatschap** The name of the sample:Attribute containing a list of CRX groups this user should be added to.

## Het IdP-certificaat toevoegen aan de AEM TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de IdP in de opslagplaats verstrekt. Hiervoor moet u:

1. Ga naar *http:/serveraddress:serverport/libs/granite/security/content/truststore.html*
1. Druk op **[!UICONTROL Create TrustStore link]**
1. Voer het wachtwoord voor de TrustStore in en druk op **[!UICONTROL Save]**.
1. Klikken op **[!UICONTROL Manage TrustStore]**.
1. Upload het IdP-certificaat.
1. Noteer het certificaat Alias. De alias is **[!UICONTROL admin#1436172864930]** in het onderstaande voorbeeld.

   ![chlimage_1-372](assets/chlimage_1-372.png)

## De sleutel en certificaatketen van de Serviceleverancier toevoegen aan het AEM sleutelarchief {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>De onderstaande stappen zijn verplicht, anders wordt de volgende uitzondering gegenereerd: `com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. Ga naar: [http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html)
1. Bewerk de `authentication-service` gebruiker.
1. Een KeyStore maken door op **KeyStore maken** krachtens **Accountinstellingen**.

>[!NOTE]
>
>De onderstaande stappen zijn alleen vereist als de handler berichten kan ondertekenen of ontsleutelen.

1. Maak het certificaat/sleutelpaar voor AEM. Het bevel om het via open te produceren zou op het onderstaande voorbeeld moeten lijken:

   `openssl req -newkey rsa:2048 -new -x509 -days 3652 -nodes -out certificate.crt -keyout key.pem`

1. Zet de sleutel in PKCS#8 formaat met DER het coderen om. Dit is de indeling die wordt vereist door het AEM sleutelarchief.

   `openssl pkcs8 -topk8 -inform PEM -outform DER -in key.pem -out key.der -nocrypt`

1. Upload het bestand met de persoonlijke sleutel door op **Bestand met persoonlijke sleutel selecteren**.
1. Het certificaatbestand uploaden door op **Certificaatketenbestanden selecteren**.
1. Een alias toewijzen, zoals hieronder wordt getoond:

   ![chlimage_1-373](assets/chlimage_1-373.png)

## Vorm Logger voor SAML {#configure-a-logger-for-saml}

U kunt opstelling een Logger om het even welke kwesties te zuiveren die uit het misconfigureren van SAML zouden kunnen voortvloeien. U kunt dit doen door:

1. Ga naar de webconsole, op *http://localhost:4502/system/console/configMgr*
1. Zoeken naar en klikken op de aangeroepen vermelding **Logboekconfiguratie Apache Sling Logging**
1. Maak een logger met de volgende configuratie:

   * **Logniveau:** Foutopsporing
   * **Logbestand:** logs/saml.log
   * **Logger:** com.adobe.granite.auth.saml
