---
title: Adobe Experience Manager Mobile - GDPR-gereedheid
description: Meer informatie over hoe Adobe Experience Manager u kan helpen met uw verplichtingen om aan de GDPR-standaard te voldoen.
contentOwner: trushton
exl-id: d06e675f-fb61-47da-85de-e0b50dd44153
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# AEM Mobile - GDPR-gereedheid {#aem-mobile-gdpr-readiness}

>[!IMPORTANT]
>
>De GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals de GDPR en de CCPA.

{{ue-over-mobile}}

## AEM Mobile GDPR-ondersteuning {#aem-mobile-gdpr-support}

AEM Mobile is bereid klanten te helpen bij hun verplichtingen om aan de GDPR-norm te voldoen. Er worden geen persoonsgegevens opgeslagen in AEM Mobile. Als u provisioned bent, kunt u aan Adobe Ervaring Mobiel met uw Adobe ID aanmelden.

<!-- [https://aemmobile.adobe.com/signin/index.html](https://aemmobile.adobe.com/signin/index.html) -->

## Adobe Digital Publishing Suite {#adobe-digital-publishing-suite}

Het digitale publicatieproduct van Adobe (dat aan AEM Mobile voorafgaat) ondersteunt de GDPR-initiatieven van Adobe. Zie [ https://business.adobe.com/privacy/general-data-protection-regulation.html ](https://business.adobe.com/privacy/general-data-protection-regulation.html). Hieronder vindt u specifieke informatie over de ondersteuning van GDPR-functies in het product van de Digital Publishing Suite, zoals hoe met Adobe kan worden gewerkt om GDPR-aanvragen te initiëren.

U kunt zich hier aanmelden bij het product van de Digital Publishing Suite om ervoor te zorgen dat AEM Mobile niet wordt verward met het oudere product van de Digital Publishing Suite:

[ https://acrobat.adobe.com/us/en/](https://acrobat.adobe.com/us/en/)

### Een GDPR-verzoek starten {#initiating-a-gdpr-request}

Neem contact op met de klantenservice van de Adobe zodat u een GDPR-aanvraag voor de Digital Publishing Suite kunt starten.

De volgende id&#39;s zijn vereist om klantgegevens te zoeken. Een ontvangen subset houdt in dat de andere id&#39;s niet van toepassing waren op deze gebruiker.

Verplicht:

* Identiteitskaart van het contract van de klant: *dpsc-contractId*

Geef ten minste 1 van de volgende gegevens op:

* De klant van de eindgebruiker verstrekte OAuth identiteitskaart (identiteitskaart die in het directe het machtigingssysteem van de klant wordt gebruikt): *dpsc-directEntitlementId*
* Voor Windows app gebruikers, identiteitskaart van App Store van de eindgebruiker: *dpsc-windowsAppStoreId*
* Het e-mailadres de eindgebruiker gebruikte om met DPS App in wisselwerking te staan: *e-mail*

### Veelgestelde vragen (FAQ) {#frequently-asked-questions-faq}

**Adobe schrappend mijn aankopen van App Store wanneer het in werking stellen van een DELETE verzoek?**

Adobe verwijdert informatie over aankopen in de App store (abonnementen, enzovoort), maar aankopen worden nog steeds geregistreerd in de App-winkels. Als de app (eindgebruiker) is aangemeld bij de App Store, worden deze ontvangstbewijzen opnieuw opgehaald en naar de Adobe verzonden. Later worden deze beschouwd als nieuwe aankopen en worden ze door de app hersteld, met nieuwe toegang.

**Adobe schrappend klant-Geleide rechten wanneer het in werking stellen van een verzoek van de DELETE?**

De Adobe schrapt informatie die het van de extra directe toestemmingstoelagen van de klant heeft. Als de app (eindgebruiker) zich aanmeldt bij het OAuth-mechanisme dat de klant heeft gebruikt, stuurt het informatie naar de Adobe en halen de services de extra rechten opnieuw op.

**wat van de eindgebruiker wordt verwacht?**

Aangezien de sleutel voor het toewijzen van rechten aan de app zich op het apparaat bevindt als onderdeel van de viewersoftware, moet de eindgebruiker de toepassing verwijderen. De eindgebruiker moet zich realiseren dat als hij de app opnieuw installeert, bestaande aankopen (gekoppeld aan de gebruiker van de App store) en directe machtigingsrechten (gekoppeld aan de OAuth-gebruiker van de klant) nog steeds worden hersteld.

**wat gebeurt wanneer app tussen mensen op een apparaat wordt gedeeld?**

De Adobe heeft minimale informatie die direct terug naar een specifieke gebruiker associeert. Het associeert de gegevens gebruikend een willekeurig gecreeerde UUID die in de gegevens van de App wordt gehouden en in elk verzoek wordt overgegaan App initieert. Dit betekent dat eindgebruikers die de app delen op hetzelfde apparaat dezelfde UUID gebruiken en dat alle gegevens worden beschouwd als eigendom van de persoon die het GDPR-verzoek indient. Voor zowel de Toegang als verzoeken van de Schrapping, beschouwt DPSC mensen die een App als één persoon delen.

**wat Persoonlijke Gegevens met Analytics worden gevolgd?**

Geen. Er worden gegevens bijgehouden, maar deze bevinden zich op toepassingsniveau (niet persoonlijk). Dit zijn gebeurtenissen zoals lanceringen, vastlopen, sluiten, activiteiten, aankopen of folio-overlays. Geografische locaties, namen, apparaat-id&#39;s of IP-adressen worden niet bijgehouden.

**de eindgebruiker verstrekte hun informatie maar niets werd gevonden. Waarom niet?**

Aangezien het product van de Digital Publishing Suite evolueerde, werden de de dienstimplementaties veranderd en meer gegevens werd verduisterd. Als er geen gegevens zijn gevonden met behulp van de door de gebruiker opgegeven gegevens, betekent dit dat de gegevens van de gebruiker niet naar die persoon kunnen worden bijgehouden.

### Voorbeeld {#example}

Neem contact op met de klantenservice van de Adobe zodat u een GDPR-verzoek kunt starten.

Hier is een voorbeeld van de input en de resulterende output van een Digital Publishing Suite GDPR verzoek:

#### Invoer: {#inputs}

```
dpsc-contractId = "12345-1234-12416234" 
directEntitlementId = "1234-1234-1234" 
windowsAppStoreId = "testWinAppStoreId" 
email = "test@what.com"
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
