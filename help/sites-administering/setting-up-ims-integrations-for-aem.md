---
title: IMS-integratie instellen voor AEM
description: Leer hoe u IMS-integratie instelt voor AEM
source-git-commit: bca98907b79f12572879273ece41ec8d82fed1b8
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# IMS-integratie instellen voor AEM {#setting-up-ims-integrations-for-aem}


>[!NOTE]
>
>Adobe die klanten gebruiken [Adobe Developer Console](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Één van die credentietypes, de geloofsbrieven van de Rekening van de Dienst (JWT), is afgekeurd ten gunste van de Server-aan-Server geloofsbrieven OAuth met Service Pack 20. Deze verandering kan aan oudere Packs van de Dienst, die met Service Pack 11 tot Service Pack 20 met het gebruik van een hotfix worden teruggevoerd die u kunt downloaden [hier](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/ims-jwt-compatibility-package-6.5-1.0.zip).

Adobe Experience Manager (AEM) kan met vele andere oplossingen van de Adobe worden geïntegreerd. Bijvoorbeeld Adobe Target, Adobe Analytics en andere.

De integratie gebruikt een integratie IMS, die met S2S OAuth wordt gevormd.

* Nadat u het volgende hebt gemaakt:

   * [Referenties in de Developer Console](#credentials-in-the-developer-console)

* Dan kunt u:

   * Een (nieuw) maken [OAuth-configuratie](#creating-oauth-configuration)

   * [Een bestaande JWT-configuratie migreren naar een OAuth-configuratie](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>Eerder werden configuraties gemaakt met [JWT-referenties die nu zijn afgekeurd in de Adobe Developer-console](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md).
>
>Dergelijke configuraties kunnen niet meer worden gemaakt of bijgewerkt, maar kunnen worden gemigreerd naar OAuth-configuraties.

## Referenties in de Developer Console {#credentials-in-the-developer-console}

Als eerste stap moet u de OAuth geloofsbrieven in de Console van Adobe Developer vormen.

Raadpleeg de documentatie bij de Developer Console, afhankelijk van uw vereisten, voor meer informatie over hoe u dit kunt doen:

* Overzicht:

   * [Server-naar-server verificatie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* Een nieuwe OAuth-referentie maken:

   * [OAuth Server-to-Server referentie implementatiegids](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)

* Een bestaande JWT-referentie migreren naar een OAuth-referentie:

   * [Migratie van JWT-referentie (Service Account) naar OAuth Server-to-Server-referentie](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)

Bijvoorbeeld:

![OAuth Credential in de Developer Console](assets/ims-configuration-developer-console.png)

## Een OAuth-configuratie maken {#creating-oauth-configuration}

Een nieuwe Adobe IMS-integratie maken met OAuth:

1. Navigeer in AEM naar **Gereedschappen**, **Beveiliging**, **Adobe IMS-integratie**.

1. Selecteren **Maken**.

1. Voltooi de configuratie op basis van de gegevens van de [Ontwerpconsole](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/). Bijvoorbeeld:

   ![OAuth-configuratie maken](assets/ims-create-oauth-configuration.png)

1. **Opslaan** uw wijzigingen.

## Een bestaande JWT-configuratie migreren naar een OAuth-configuratie {#migrating-existing-JWT-configuration-to-oauth}

Een bestaande Adobe IMS-integratie migreren op basis van JWT-referenties:

>[!NOTE]
>
>Dit voorbeeld toont een Configuratie van IMS van de Lancering.

1. Navigeer in AEM naar **Gereedschappen**, **Beveiliging**, **Adobe IMS-integratie**.

1. Selecteer de JWT-configuratie die moet worden gemigreerd. JWT-configuraties worden gemarkeerd met de waarschuwing **JWT Credentials (afgekeurd)**.

1. Selecteren **Eigenschappen**:

   ![JWT-configuratie selecteren](assets/ims-migrate-jwt-select-configuration.png)

1. De configuratie wordt geopend als alleen-lezen:

   ![Configuratieeigenschappen - alleen-lezen](assets/ims-migrate-jwt-properties-read-only.png)

1. Selecteren **OAuth** van de **Type verificatie** vervolgkeuzelijst:

   ![Verificatietype selecteren](assets/ims-migrate-jwt-authentication-type.png)

1. De beschikbare eigenschappen worden bijgewerkt. Gebruik de gegevens in de Developer Console om deze te voltooien:

   ![Volledige details OAuth](assets/ims-migrate-jwt-complete-oauth-details.png)

1. Gebruiken **Opslaan en sluiten** om uw updates voort te zetten.
Wanneer u op de console terugkeert **JWT Credentials (afgekeurd)** de waarschuwing is verdwenen.