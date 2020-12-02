---
title: SAML 2.0-verificatiehandler
seo-title: SAML 2.0-verificatiehandler
description: Leer over de Handler van de Authentificatie SAML 2.0 in AEM.
seo-description: Leer over de Handler van de Authentificatie SAML 2.0 in AEM.
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

AEM wordt geleverd met een [SAML](http://saml.xml.org/saml-specifications)-verificatiehandler. Deze manager verleent steun voor [SAML](http://saml.xml.org/saml-specifications) 2.0 het Protocol van het Verzoek van de Authentificatie (Web-SSO profiel) gebruikend de `HTTP POST` band.

Het steunt:

* ondertekening en versleuteling van berichten
* automatisch maken van gebruikers
* groepen synchroniseren met bestaande groepen in AEM
* Serviceleverancier en identiteitsprovider hebben verificatie gestart

Deze handler slaat het gecodeerde SAML-antwoordbericht op in het user-node ( `usernode/samlResponse`) om de communicatie met een externe serviceprovider te vergemakkelijken.

>[!NOTE]
>
>Zie [een demonstratie van AEM en integratie SAML](https://helpx.adobe.com/experience-manager/kb/simple-saml-demo.html).
>
>Als u het einde van het communityartikel wilt lezen, klikt u op: [SAML integreren met Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/aem63_saml.html).

## De SAML 2.0-verificatiehandler {#configuring-the-saml-authentication-handler} configureren

De [Webconsole](/help/sites-deploying/configuring-osgi.md) biedt toegang tot de [SAML](http://saml.xml.org/saml-specifications) 2.0-verificatiehandlerconfiguratie met de naam **Adobe Granite SAML 2.0-verificatiehandler**. De volgende eigenschappen kunnen worden ingesteld.

>[!NOTE]
>
>De SAML 2.0-verificatiehandler is standaard uitgeschakeld. U moet minstens één van de volgende eigenschappen plaatsen om de manager toe te laten:
>
>* De URL van de POST Identity Provider.
>* De Service Provider Entiteit ID.

>



>[!NOTE]
>
>SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de identiteitsprovider in de TrustStore opgeeft. Zie [Het certificaat IdP toevoegen aan de sectie TrustStore](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore) voor meer informatie.

**Pad** PathRepository waarvoor deze verificatiehandler moet worden gebruikt door Sling. Als dit leeg is, zal de authentificatiemanager worden onbruikbaar gemaakt.

**Dienst** RankingOSGi de Rangschikkende waarde van de Dienst van het Kader om op de orde te wijzen waarin om deze dienst te roepen. Dit is een geheel getal waarbij hogere waarden een hogere prioriteit aangeven.

**IDP-** certificaatalias - De alias van het IdP-certificaat in de algemene vertrouwde opslag. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld. Zie het hoofdstuk &quot;Add the IdP Certificate to the AEM TrustStore&quot; hieronder over hoe u het instelt.

**De** URLURL van de identiteitsprovider van de IDP waarnaar de SAML-verificatieaanvraag moet worden verzonden. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

>[!CAUTION]
>
>De hostnaam van de identiteitsprovider moet worden toegevoegd aan de OSGi-configuratie **Apache Sling Referrer Filter**. Zie de sectie [Webconsole](/help/sites-deploying/configuring-osgi.md) voor meer informatie.

**De Entiteit van de Dienstverlener** IDID die uniek deze dienstverlener met de identiteitsleverancier identificeert. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

**Standaard** omleidingDe standaardlocatie voor omleiding na geslaagde verificatie.

>[!NOTE]
>
>Deze locatie wordt alleen gebruikt als het cookie `request-path` niet is ingesteld. Als u om het even welke pagina onder de gevormde weg zonder geldig login-teken verzoekt, wordt het gevraagde weg opgeslagen in een koekje
>en de browser wordt opnieuw omgeleid naar deze locatie nadat de verificatie is voltooid.

**** Kenmerk van de gebruiker-identiteitskaartDe naam van het attribuut dat de gebruiker - identiteitskaart bevat die wordt gebruikt om de gebruiker in de bewaarplaats van CRX voor authentiek te verklaren en te creëren.

>[!NOTE]
>
>De gebruikers-id wordt niet overgenomen uit het knooppunt `saml:Subject` van de SAML-bevestiging, maar uit `saml:Attribute`.

**Het gebruik** Encryptionwhether of niet deze authentificatiemanager verwacht gecodeerde beweringen van SAML.

**Autocreate CRX** UsersOr of niet om automatisch niet-bestaande gebruikers in de bewaarplaats na succesvolle authentificatie tot stand te brengen.

>[!CAUTION]
>
>Als het automatisch maken van CRX-gebruikers is uitgeschakeld, moeten de gebruikers handmatig worden gemaakt.

**Toevoegen aan** groepenOf een gebruiker automatisch aan CRX-groepen moet worden toegevoegd na geslaagde verificatie.

**Group** MembershipThe name of the sample:Attribute containing a list of CRX groups this user should be added to.

## Het IdP-certificaat toevoegen aan de AEM TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de IdP in de opslagplaats verstrekt. Hiervoor moet u:

1. Ga naar *http:/serveraddress:serverport/libs/granite/security/content/truststore.html*
1. Druk op **[!UICONTROL Create TrustStore link]**
1. Ga het wachtwoord voor TrustStore in en druk **[!UICONTROL Save]**.
1. Klik op **[!UICONTROL Manage TrustStore]**.
1. Upload het IdP-certificaat.
1. Noteer het certificaat Alias. De alias is **[!UICONTROL admin#1436172864930]** in het onderstaande voorbeeld.

   ![chlimage_1-372](assets/chlimage_1-372.png)

## Voeg de sleutel en certificaatketen van de Serviceleverancier toe aan het AEM sleutelarchief {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>De onderstaande stappen zijn verplicht, anders wordt de volgende uitzondering gegenereerd: `com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. Ga naar: [http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html)
1. Bewerk de `authentication-service` gebruiker.
1. Maak een KeyStore door te klikken op **Create KeyStore** onder **Accountinstellingen**.

>[!NOTE]
>
>De onderstaande stappen zijn alleen vereist als de handler berichten kan ondertekenen of ontsleutelen.

1. Upload het bestand met de persoonlijke sleutel door te klikken op **Persoonlijk sleutelbestand selecteren**. De sleutel moet in PKCS#8 formaat met DER het coderen zijn.
1. Upload het certificaatbestand door te klikken op **Certificaatketenbestanden selecteren**.
1. Een alias toewijzen, zoals hieronder wordt getoond:

   ![chlimage_1-373](assets/chlimage_1-373.png)

## Een logger configureren voor SAML {#configure-a-logger-for-saml}

U kunt opstelling een Logger om het even welke kwesties zuiveren die uit het misconfigureren SAML zouden kunnen voortvloeien. U kunt dit doen door:

1. Ga naar de webconsole op *http://localhost:4502/system/console/configMgr*
1. Zoek naar en klik op de vermelding **Configuratie van Apache Sling Logging Logger**
1. Maak een logger met de volgende configuratie:

   * **Logniveau:** Foutopsporing
   * **logbestand:** logs/saml.log
   * **Logger:** com.adobe.granite.auth.saml

