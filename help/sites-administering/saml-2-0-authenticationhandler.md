---
title: SAML 2.0-verificatiehandler
description: Leer over de Handler van de Authentificatie SAML 2.0 in AEM.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 8e54bccf-0ff1-448d-a237-ec42fd3bfa23
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# SAML 2.0-verificatiehandler{#saml-authentication-handler}

AEM schepen met a [ SAML ](https://saml.xml.org/saml-specifications) authentificatiemanager. Deze manager steunt het ](https://saml.xml.org/saml-specifications) 2.0 Protocol van het Verzoek van de Authentificatie van 0} SAML {(Web-SSO profiel) gebruikend de `HTTP POST` band.[

Het steunt:

* ondertekening en versleuteling van berichten
* automatisch maken van gebruikers
* groepen synchroniseren met bestaande groepen in AEM
* Serviceleverancier en identiteitsprovider hebben verificatie gestart

Deze handler slaat het gecodeerde SAML-antwoordbericht op in het user-node ( `usernode/samlResponse` ) om de communicatie met een externe serviceprovider te vergemakkelijken.

>[!NOTE]
>
>Zie [ een demonstratie van AEM en integratie SAML ](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17481.html).

## De SAML 2.0-verificatiehandler configureren {#configuring-the-saml-authentication-handler}

De [ console van het Web ](/help/sites-deploying/configuring-osgi.md) verleent toegang tot [ SAML ](https://saml.xml.org/saml-specifications) 2.0 de configuratie van de Handler van de Authentificatie geroepen **Adobe granite SAML 2.0 de Handler van de Authentificatie**. De volgende eigenschappen kunnen worden ingesteld.

>[!NOTE]
>
>De SAML 2.0-verificatiehandler is standaard uitgeschakeld. Stel ten minste een van de volgende eigenschappen in om de handler in te schakelen:
>
>* De POST-URL van Identiteitsprovider of de IDP-URL.
>* De Service Provider Entiteit ID.
>

>[!NOTE]
>
>SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de Identiteitsprovider in de TrustStore opgeeft. Zie [ Toevoegend het certificaat IdP aan de ](/help/sites-administering/saml-2-0-authenticationhandler.md#add-the-idp-certificate-to-the-aem-truststore) sectie TrustStore voor meer informatie.

**weg van de Weg** Bewaarplaats waarvoor deze authentificatiemanager door het Sling zou moeten worden gebruikt. Als dit leeg is, zal de authentificatiemanager worden onbruikbaar gemaakt.

**OSGi van het Kader van de Dienst Rangschikkende waarde van de Dienst van 0} de Dienst { om op de orde te wijzen waarin om deze dienst te roepen.** Dit is een geheel getal waarbij hogere waarden een hogere prioriteit aangeven.

**Alias van het Certificaat IDP** De alias van het certificaat IdP in globale truststore. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld. Zie het hoofdstuk &quot;Add the IdP Certificate to the AEM TrustStore&quot; hieronder over hoe u het instelt.

**IDP URL** URL van IDP waar het Verzoek van de Authentificatie van SAML zou moeten worden verzonden naar. Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

>[!CAUTION]
>
>De hostname van de Leverancier van de Identiteit moet aan de **Apache Verschuivende Filter** OSGi configuratie worden toegevoegd. Zie de [ console van het Web ](/help/sites-deploying/configuring-osgi.md) sectie voor meer informatie.

{identiteitskaart van de Entiteit van de Leverancier van 0} **identiteitskaart die uniek deze dienstverlener met de identiteitsleverancier identificeert.** Als deze eigenschap leeg is, wordt de verificatiehandler uitgeschakeld.

**Gebrek richt** opnieuw om de standaardplaats aan na succesvolle authentificatie om te leiden.

>[!NOTE]
>
>Deze locatie wordt alleen gebruikt als het cookie `request-path` niet is ingesteld. Als u om het even welke pagina onder de gevormde weg zonder geldig login-teken verzoekt, wordt het gevraagde weg opgeslagen in een koekje
>en de browser wordt opnieuw omgeleid naar deze locatie nadat de verificatie is voltooid.

**gebruiker-identiteitskaart Attribuut** De naam van de attributen die gebruiker - identiteitskaart bevatten die wordt gebruikt om de gebruiker in de bewaarplaats van CRX voor authentiek te verklaren en tot stand te brengen.

>[!NOTE]
>
>De gebruikers-id wordt niet ontleend aan het knooppunt `saml:Subject` van de SAML-bewering, maar aan deze `saml:Attribute` .

**Versleuteling van het Gebruik** Of of deze authentificatiemanager gecodeerde beweringen van SAML verwacht.

**autocreate de Gebruikers van CRX** Al dan niet om automatisch niet-bestaande gebruikers in de bewaarplaats na succesvolle authentificatie tot stand te brengen.

>[!CAUTION]
>
>Als het automatisch maken van CRX-gebruikers is uitgeschakeld, moeten de gebruikers handmatig worden gemaakt.

**voeg aan Groepen** toe al dan niet een gebruiker automatisch aan de groepen van CRX na succesvolle authentificatie zou moeten worden toegevoegd.

**Lidmaatschap van de Groep** De naam van voorbeeld:Attribuut dat een lijst van de groepen van CRX bevat deze gebruiker zou moeten worden toegevoegd aan.

## Het IdP-certificaat toevoegen aan de AEM TrustStore {#add-the-idp-certificate-to-the-aem-truststore}

SAML-beweringen worden ondertekend en kunnen optioneel worden versleuteld. Dit werkt alleen als u ten minste het openbare certificaat van de IdP in de opslagplaats verstrekt. Hiervoor moet u:

1. Ga naar *http:/serveraddress:serverport/libs/granite/security/content/truststore.html*
1. Druk op **[!UICONTROL Create TrustStore link]**
1. Voer het wachtwoord voor de TrustStore in en druk op **[!UICONTROL Save]** .
1. Klik op **[!UICONTROL Manage TrustStore]** .
1. Upload het IdP-certificaat.
1. Noteer het certificaat Alias. De alias is **[!UICONTROL admin#1436172864930]** in het onderstaande voorbeeld.

   ![ chlimage_1-372 ](assets/chlimage_1-372.png)

## De sleutel en certificaatketen van de Serviceleverancier toevoegen aan het AEM sleutelarchief {#add-the-service-provider-key-and-certificate-chain-to-the-aem-keystore}

>[!NOTE]
>
>De onderstaande stappen zijn verplicht, anders wordt de volgende uitzondering gegenereerd: `com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised system trust store`

1. Ga naar: [ http://localhost:4502/libs/granite/security/content/useradmin.html](http://localhost:4502/libs/granite/security/content/useradmin.html)
1. Bewerk de gebruiker `authentication-service` .
1. Creeer een KeyStore door **te klikken Create KeyStore** onder **de Montages van de Rekening**.

>[!NOTE]
>
>De onderstaande stappen zijn alleen vereist als de handler berichten kan ondertekenen of ontsleutelen.

1. Maak het certificaat/sleutelpaar voor AEM. Het bevel om het via open te produceren zou op het onderstaande voorbeeld moeten lijken:

   `openssl req -newkey rsa:2048 -new -x509 -days 3652 -nodes -out certificate.crt -keyout key.pem`

1. Zet de sleutel in PKCS#8 formaat met DER het coderen om. Dit is de indeling die wordt vereist door het AEM sleutelarchief.

   `openssl pkcs8 -topk8 -inform PEM -outform DER -in key.pem -out key.der -nocrypt`

1. Upload het Persoonlijke zeer belangrijke dossier door **Uitgezochte Persoonlijke Zeer belangrijke Dossier** te klikken.
1. Upload het certificaatdossier door **Uitgezochte Dossiers van de Keten van het Certificaat te klikken**.
1. Een alias toewijzen, zoals hieronder wordt getoond:

   ![ chlimage_1-373 ](assets/chlimage_1-373.png)

## Vorm Logger voor SAML {#configure-a-logger-for-saml}

U kunt opstelling een Logger om het even welke kwesties te zuiveren die uit het misconfigureren van SAML zouden kunnen voortvloeien. U kunt dit doen door:

1. Ga naar de Console van het Web, in *http://localhost:4502/system/console/configMgr*
1. Zoek naar en klik de ingang genoemd **Apache die de Configuratie van de Logger van het Logboek van het Registreren van de Sling**
1. Maak een logger met de volgende configuratie:

   * **Niveau van het Logboek:** zuivert
   * **Dossier van het Logboek:** logs/saml.log
   * **Logger:** com.adobe.granite.auth.saml
