---
title: AEM Mobile - GDPR-gereedheid
seo-title: AEM Mobile - GDPR-gereedheid
description: 'null'
seo-description: 'null'
uuid: 817c434f-4b78-40f7-99d6-6efafdedb77e
contentOwner: trushton
discoiquuid: 9399dd3d-a485-4f53-a6f2-7b190da4235b
translation-type: tm+mt
source-git-commit: 85a3dac5db940b81da9e74902a6aa475ec8f1780
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---


# AEM Mobile - GDPR-gereedheid {#aem-mobile-gdpr-readiness}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy; zoals GDPR, CCPA enz.

## AEM Mobile GDPR-ondersteuning {#aem-mobile-gdpr-support}

AEM Mobile is bereid klanten te helpen bij hun verplichtingen om aan de GDPR-norm te voldoen. Er worden geen persoonsgegevens opgeslagen in AEM Mobile. Als u de provisioning ontvangt, kunt u zich aanmelden bij Adobe Experience Mobile met uw Adobe ID.

[https://aemmobile.adobe.com/signin/index.html](https://aemmobile.adobe.com/signin/index.html)

## Adobe Digital Publishing Suite {#adobe-digital-publishing-suite}

Het digitale publicatieproduct van Adobe (dat aan AEM Mobile voorafgaat) ondersteunt de GDPR-gereedheidsinitiatieven van Adobe. Zie [https://www.adobe.com/privacy/general-data-protection-regulation.html](https://www.adobe.com/privacy/general-data-protection-regulation.html). Hieronder vindt u specifieke informatie over ondersteuning voor GDPR-functies die relevant zijn voor het Digital Publishing Suite-product, zoals hoe u met Adobe kunt werken om GDPR-aanvragen te initiëren.

U kunt zich hier aanmelden bij het Digital Publishing Suite-product om ervoor te zorgen dat AEM Mobile niet wordt verward met het oudere Digital Publishing Suite-product:

[https://digitalpublishing.acrobat.com/welcome.html](https://digitalpublishing.acrobat.com/welcome.html)

### Een GDPR-verzoek {#initiating-a-gdpr-request} starten

Neem contact op met de klantenservice van Adobe om een GDPR-aanvraag voor de Digital Publishing Suite te starten.

De volgende id&#39;s zijn vereist om klantgegevens te zoeken. Alle ontvangen subsets betekenen dat de andere id&#39;s niet van toepassing waren op deze gebruiker.

Verplicht:

* Contractnummer van de klant: *dpsc-contractId*

Geef ten minste 1 van de volgende gegevens op:

* De klant van de eindgebruiker verstrekte OAuth identiteitskaart (identiteitskaart die in het directe machtigingssysteem van de klant wordt gebruikt): *dpsc-directEntitlementId*
* Voor gebruikers van de Windows-app gebruikt u de id van de App Store van de eindgebruiker: *dpsc-windowsAppStoreId*
* Het e-mailadres dat de eindgebruiker heeft gebruikt om te communiceren met de DPS App: *e-mail*

### Veelgestelde vragen (FAQ) {#frequently-asked-questions-faq}

**Zal Adobe mijn App Store-aankopen verwijderen wanneer een DELETE-aanvraag wordt gestart?**

Adobe verwijdert de informatie over aankopen in de App Store (abonnementen, enz.) maar aankopen worden wel geregistreerd in de App-winkels. Als de app (eindgebruiker) is aangemeld bij de App Store, worden deze ontvangstbewijzen opnieuw opgehaald en verzonden naar Adobe en vervolgens worden deze beschouwd als nieuwe aankopen en worden ze door de App hersteld zodat ze weer toegang hebben.

**Zal Adobe klant verstrekte rechten schrappen wanneer het in werking stellen van een DELETE verzoek?**

Adobe zal informatie verwijderen die hij heeft over de extra directe rechten van de klant. Als de app (eindgebruiker) zich aanmeldt bij het OAuth-mechanisme dat de klant heeft gebruikt, stuurt het informatie naar Adobe en nemen de services de extra rechten weer op.

**Wat wordt van de eindgebruiker verwacht?**

Aangezien de sleutel voor het toewijzen van rechten aan de toepassing zich op het apparaat bevindt als onderdeel van de viewersoftware, moet de eindgebruiker de toepassing verwijderen. De eindgebruiker moet zich realiseren dat als hij de app opnieuw installeert, bestaande aankopen (gekoppeld aan de gebruiker van de App store) en directe machtigingsrechten (gekoppeld aan de OAuth-gebruiker van de klant) nog steeds worden hersteld.

**Wat gebeurt er als een app wordt gedeeld tussen mensen op een apparaat?**

Adobe heeft zeer weinig informatie die direct terug naar een specifieke gebruiker associeert. Het associeert de gegevens gebruikend een willekeurig gecreeerde UUID die in de gegevens van de App wordt gehouden en in elk verzoek wordt overgegaan App initieert. Dit betekent dat eindgebruikers die de app delen op hetzelfde apparaat dezelfde UUID gebruiken en dat alle gegevens worden beschouwd als eigendom van de persoon die het GDPR-verzoek indient. Voor zowel de Toegang als van de Schrapping verzoeken, zal DPSC mensen overwegen die een App als één persoon delen.

**Welke persoonlijke gegevens worden bij Analytics bijgehouden?**

Geen. Er worden gegevens bijgehouden, maar deze bevinden zich op toepassingsniveau (niet persoonlijk). Dit zijn gebeurtenissen zoals lanceringen, vastlopen, sluiten, activiteiten, aankopen of folio-overlays. Geografische locaties, namen, apparaat-id&#39;s of IP-adressen worden niet bijgehouden.

**De eindgebruiker heeft zijn gegevens verstrekt, maar er is niets gevonden. Waarom niet?**

Naarmate het Digital Publishing Suite-product zich ontwikkelde, zijn serviceimplementaties gewijzigd en zijn meer gegevens verduisterd. Als er geen gegevens zijn gevonden met behulp van de door de gebruiker opgegeven gegevens, betekent dit dat de gegevens van de gebruiker niet naar die persoon kunnen worden bijgehouden.

### Voorbeeld {#example}

Neem contact op met de klantenservice van Adobe om een GDPR-aanvraag te starten.

Hier volgt een voorbeeld van de invoer en de resulterende uitvoer van een Digital Publishing Suite GDPR-aanvraag:

#### Invoer: {#inputs}

```
dpsc-contractId = “12345-1234-12416234” 
directEntitlementId = “1234-1234-1234” 
windowsAppStoreId = “testWinAppStoreId” 
email = “test@what.com”
```

#### Uitvoer {#outputs}

```
{

    "jobId": "test-1524750204384",

    "product": "DPSC",

    "action": "access",

    "userIDS": [

        {

        "namespace": "email",

        "value": "test@what.com"

        },

        {

        "namespace": "windowsAppStoreId",

        "value": "testWinAppStoreId"

        },

        {

        "namespace": "directEntitlementId",

        "value": "1234-1234-1234"

        }

    ],

    "receiptData": {

    "recordsFound": 6,

    "recordsAffected": 0,

    "tablesModified": 0,

    "subscriptionsFound": 24,

    "entitlementsFound": 24

    },

    "records": {

        "DPS_Stage_EntitlementUserDevices": [

        {

            "user_id": "testc685-c9ca-4c1e-a11b-07d10ec724cf",

            "device_id": "appleStore:test1b16-f032-4d9c-9200-0d19999405c4",

            "account_id": "test@what.com"

        },

        {

            "user_id": "test967d-5179-4dc6-958c-facd9d94da38",

            "device_id": "appleStore:test3f07-d5aa-4b32-8fac-b2b690b7ccd7",

            "account_id": "test@what.com"

        },

        {

            "user_id": "test1838-6494-4e74-912c-1edf61581d0e",

            "device_id": "appleStore:test3813-f8cc-49ce-b021-50eb0814a3bb",

            "account_id": "1234-1234-1234"

        },

        {

            "user_id": "test5468-1a11-4e4c-be43-274181a9ef81",

            "device_id": "appleStore:testf082-2783-498d-ab62-b1b2e3eb67ae",

            "account_id": "1234-1234-1234"

        }

        ],

            "DPS_Stage_EntitlementUsers": [

        {

            "id": "store:test04a7-33a3-4b90-863d-79981ead0f19:appleStore",

            "part_id": "0",

            "alias_user_id": "testWinAppStoreId"

        },

        {

            "id": "internal:testd2da-0606-4444-87ef-0d5a1d4a121d:adobe",

            "part_id": "0",

            "user_id": "test@what.com"

        }

        ],

            "DPS_Stage_Subscriptions": [

        {

            "id": "appleStore:testc685-c9ca-4c1e-a11b-07d10ec724cf",

            "account_id": "test3531-a209-4391-beb9-951c7822244e",

            "overflow": "test4e59-86a8-4b75-b699-77e980c287ab",

            "entitlement_count": "12"

        },

        {

            "id": "appleStore:test5468-1a11-4e4c-be43-274181a9ef81",

            "account_id": "test491b-379e-4d24-96ef-e481bf8d3062",

            "overflow": "test931b-7422-485d-85a5-134828187b6c",

            "entitlement_count": "12"

        }

        ],

            "DPS_Stage_Entitlements": [

        {

            "id": "samsungStore:testc685-c9ca-4c1e-a11b-07d10ec724cf",

            "account_id": "test7332-60a0-42b8-a508-474668d83d2e",

            "overflow": "test9bc3-94d0-43cf-b132-0629868f7d9d",

            "entitlement_count": "12"

        },

        {

            "id": "appleStore:test5468-1a11-4e4c-be43-274181a9ef81",

            "account_id": "testf766-102a-460d-8f5a-42f7bb9d68b7",

            "overflow": "test4d96-2197-45a8-9caf-2aa2846b770c",

            "entitlement_count": "12"

        }

        ],

            "s3Buckets": {

            "name": "DPS-Entitlements-Overflow",

            "folder": "stage/",

            "overflows": {

            "subscriptions": [

            "test4e59-86a8-4b75-b699-77e980c287ab",

            "test931b-7422-485d-85a5-134828187b6c"

        ],

            "entitlements": [

            "test9bc3-94d0-43cf-b132-0629868f7d9d",

            "test4d96-2197-45a8-9caf-2aa2846b770c"

                ]

            }

        }

    }

}
```

