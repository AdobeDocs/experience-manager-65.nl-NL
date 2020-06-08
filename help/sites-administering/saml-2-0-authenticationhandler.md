---
title: SAML 2.0-verificatiehandler
seo-title: SAML 2.0-verificatiehandler
description: Leer over SAML 2.0 de Handler van de Authentificatie in AEM.
seo-description: Leer over SAML 2.0 de Handler van de Authentificatie in AEM.
uuid: 51f97315-350a-42a4-af2c-2de87307c6ad
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 6ed09b5d-5089-43d2-b9d5-e7db57be5c02
translation-type: tm+mt
source-git-commit: d559a15e3c1c65c39e38935691835146f54a356e
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---


# SAML 2.0-verificatiehandler{#saml-authentication-handler}

AEM wordt geleverd met een [SAML](http://saml.xml.org/saml-specifications) -verificatiehandler. Deze manager verleent steun voor het [SAML](http://saml.xml.org/saml-specifications) 2.0 Protocol van het Verzoek van de Authentificatie (Web-SSO profiel) gebruikend de `HTTP POST` band.

Het steunt:

* ondertekening en versleuteling van berichten
* automatisch maken van gebruikers
* groepen synchroniseren met bestaande groepen in AEM
* Serviceleverancier en identiteitsprovider hebben verificatie gestart

Deze manager slaat het gecodeerde SAML antwoordbericht in gebruiker-knoop ( `usernode/samlResponse`) op om communicatie met een derde Dienstverlener te vergemakkelijken.

>[!NOTE]
>
>Zie [een demonstratie van de integratie](https://helpx.adobe.com/experience-manager/kb/simple-saml-demo.html)van AEM en SAML.
>
>Als u het einde van het communityartikel wilt lezen, klikt u op: [SAML integreren met Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/aem63_saml.html).

## De SAML 2.0-verificatiehandler configureren {#configuring-the-saml-authentication-handler}

De [webconsole](/help/sites-deploying/configuring-osgi.md) biedt toegang tot de configuratie van de [SAML](http://saml.xml.org/saml-specifications) 2.0-verificatiehandler met de naam **Adobe Granite SAML 2.0-verificatiehandler**. De volgende eigenschappen kunnen worden ingesteld.

>[!NOTE]
>
>De SAML 2.0-verificatiehandler is standaard uitgeschakeld. U moet minstens één van de volgende eigenschappen plaatsen om de manager toe te laten:
>
>* De POST-URL van de identiteitsprovider.
>* De Service Provider Entiteit ID.
>



>[!NOTE]
>
>SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de identiteitsprovider in de TrustStore opgeeft. Zie Het IdP-certificaat [toevoegen aan de sectie TrustStore](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore) voor meer informatie.

**Pad** Repository voor pad waarvoor deze verificatiehandler door Sling moet worden gebruikt. Als dit leeg is, zal de authentificatiemanager worden onbruikbaar gemaakt.

**De Rangschikkende waarde van de Dienst van het Kader van de dienst OSGi om op de orde te wijzen waarin om deze dienst te roepen.** Dit is een geheel getal waarbij hogere waarden een hogere prioriteit aangeven.

**IDP-certificaatalias** De alias van het IdP-certificaat in de algemene truststore. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld. Zie het hoofdstuk &quot;Add the IdP Certificate to the AEM TrustStore&quot; hieronder over hoe u het instelt.

**De URL** van de identiteitsprovider van de IDP waarnaar de SAML-verificatieaanvraag moet worden verzonden. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

>[!CAUTION]
>
>De hostnaam van Identiteitsprovider moet worden toegevoegd aan de OSGi-configuratie van het filter **Apache Sling Referrer** . Zie de de consolesectie [van het](/help/sites-deploying/configuring-osgi.md) Web voor meer informatie.

**Identiteitskaart** van de Entiteit van de Dienstverlener identiteitskaart die uniek deze dienstverlener met de identiteitsleverancier identificeert. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

**Standaard leidt** de standaardlocatie om naar na succesvolle verificatie om te leiden.

>[!NOTE]
>
>Deze locatie wordt alleen gebruikt als de `request-path` cookie niet is ingesteld. Als u om het even welke pagina onder de gevormde weg zonder geldig login-teken verzoekt, wordt het gevraagde weg opgeslagen in een koekje
>en de browser wordt opnieuw omgeleid naar deze locatie nadat de verificatie is voltooid.

**Kenmerk** gebruiker-ID De naam van het kenmerk dat de gebruikers-id bevat die wordt gebruikt om de gebruiker te verifiëren en te maken in de CRX-opslagruimte.

>[!NOTE]
>
>De gebruiker - identiteitskaart zal niet uit de `saml:Subject` knoop van de bevestiging van SAML maar van dit worden genomen `saml:Attribute`.

**De Encryptie** van het gebruik Al dan niet deze authentificatiemanager gecodeerde beweringen van SAML verwacht.

**Autocreate CRX Gebruikers** Al dan niet om automatisch niet-bestaande gebruikers in de bewaarplaats na succesvolle authentificatie tot stand te brengen.

>[!CAUTION]
>
>Als het automatisch maken van CRX-gebruikers is uitgeschakeld, moeten de gebruikers handmatig worden gemaakt.

**Voeg toe aan Groepen** al dan niet een gebruiker automatisch aan CRX groepen na succesvolle authentificatie zou moeten worden toegevoegd.

**Groepslidmaatschap** De naam van voorbeeld:Attribuut die een lijst van CRX groepen bevat deze gebruiker zou moeten worden toegevoegd aan.

## Het IdP-certificaat toevoegen aan de AEM TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de IdP in de opslagplaats verstrekt. Hiervoor moet u:

1. Ga naar *http:/serveraddress:serverport/libs/granite/security/content/truststore.html*
1. Druk op **[!UICONTROL Create TrustStore link]**
1. Voer het wachtwoord voor de TrustStore in en druk op **[!UICONTROL Save]**.
1. Klik op **[!UICONTROL Manage TrustStore]**.
1. Upload het IdP-certificaat.
1. Noteer het certificaat Alias. De alias staat **[!UICONTROL admin#1436172864930]** in het onderstaande voorbeeld.

   ![chlimage_1-372](assets/chlimage_1-372.png)

## De sleutel en certificaatketen van de Serviceleverancier toevoegen aan het AEM-sleutelarchief {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>De onderstaande stappen zijn verplicht, anders wordt de volgende uitzondering gegenereerd: `com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. Ga naar: [http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html)
1. Bewerk de `authentication-service` gebruiker.
1. Maak een KeyStore door op **Create KeyStore** onder **Accountinstellingen** te klikken.

>[!NOTE]
>
>De onderstaande stappen zijn alleen vereist als de handler berichten kan ondertekenen of ontsleutelen.

1. Upload het bestand met de persoonlijke sleutel door te klikken op Bestand **persoonlijke sleutel** selecteren. De sleutel moet in PKCS#8 formaat met DER het coderen zijn.
1. Upload het certificaatbestand door op Certificaatketenbestanden **** selecteren te klikken.
1. Een alias toewijzen, zoals hieronder wordt getoond:

   ![chlimage_1-373](assets/chlimage_1-373.png)

## Vorm Logger voor SAML {#configure-a-logger-for-saml}

U kunt opstelling een Logger om het even welke kwesties zuiveren die uit het misconfigureren SAML zouden kunnen voortvloeien. U kunt dit doen door:

1. Ga naar de webconsole op *http://localhost:4502/system/console/configMgr*
1. Zoek naar en klik op de vermelding **Apache Sling Logging Logger Configuration**
1. Maak een logger met de volgende configuratie:

   * **Logniveau:** Foutopsporing
   * **Logbestand:** logs/saml.log
   * **Logger:** com.adobe.granite.auth.saml

