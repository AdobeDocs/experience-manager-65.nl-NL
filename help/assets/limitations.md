---
title: Dynamic Media-beperkingen
description: Leer over de beste praktijken en de gedwongen grenzen wanneer u een Reeks van het Beeld of een Reeks van de Rotatie creeert, of een PDF uploadt. Meer informatie over niet-ondersteunde combinaties van webbrowsers en besturingssystemen voor Dynamic Media Viewers.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/Dynamic-Media-Classic
geptopics: SG_SCENESEVENONDEMAND_PK/categories/ecatalogs
feature: Dynamic Media Classic,Asset Management,Viewers,Image Sets,Spin Sets,eCatalog
role: User
exl-id: e4d4059e-ac0b-42e7-910c-001310796574
source-git-commit: 098c52720d08ad294a745addb8bd3ca3f1c63b5c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 4%

---

# Dynamic Media-beperkingen

In de volgende secties worden beperkingen in Dynamic Media beschreven.

Dit onderwerp omvat de volgende secties:

* [Aanbevolen werkwijzen en door Dynamic Media opgelegde limieten voor soorten activa](#best-practice-enforced-limits)
* [Niet-ondersteunde combinaties van webbrowsers en besturingssystemen voor Dynamic Media Viewers](#unsupported-browser-os)

## Aanbevolen werkwijzen en door Dynamic Media opgelegde limieten voor soorten activa {#best-practice-enforced-limits}

Als u een centrifugeset of een afbeeldingsset maakt of PDF uploadt voor het uitnemen van pagina&#39;s, raadt Adobe u de volgende aanbevolen procedures aan en worden de volgende limieten in acht genomen:

| Element - Type limiet | Beste praktijken | Oplegde limiet | Wijziging tot limiet op 31 december 2022 |
| --- | --- | --- | --- |
| **Afbeelding** - Aantal slimme uitsnijdingen per afbeelding | 5 | 100 | 20 |
| **Alle sets** - Aantal dubbele elementen per set | Geen duplicaten | 20 | Niet van toepassing |
| **Alle sets** - Maximumaantal activa per set | 5-10 afbeeldingen per set | 1000 | Niet van toepassing |
| **Set draaien** - Maximumaantal rijen/kolommen per 2D-set | 12-18 afbeeldingen per set | 1000 | Niet van toepassing |
| **PDF** - Maximumaantal pagina&#39;s voor een PDF dat in aanmerking komt voor extractie |  | 5000 (voor nieuwe uploads) | 100 (voor alle PDF) |

<!-- See also [Dynamic Media limitations](/help/assets/limitations.md). -->

## Niet-ondersteunde combinaties van webbrowsers en besturingssystemen voor Dynamic Media Viewers {#unsupported-browser-os}

Dynamic Media Viewers ondersteunen de volgende webbrowser- en besturingssysteemcombinaties niet.

* Internet Explorer 11 + Windows 7
* Internet Explorer 11 + Windows 8.1
* Internet Explorer 11 + Windows Phone 8.1
* Internet Explorer 11 + Windows Phone 8.1-update
* Safari 6 + iOS 6.0.1
* Safari 7 + iOS 7.1
* Safari 7 + OS X 10.9 Mavericks
* Safari 8 + iOS 8.4
* Safari 8 + OS X 10.10 Yosemite

## Einde ondersteuning voor TLS 1.0 en 1.1 {#tls}

<!-- CQDOC-19433 -->

Vanaf 30 september 2022 beëindigt Adobe Dynamic Media Viewers de ondersteuning voor:

* TLS (Transport Layer Security) 1.0 en 1.1
* De volgende zwakke ciphers in TLS 1.2:
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
   * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_RSA_WITH_AES_256_GCM_SHA384`
   * `TLS_RSA_WITH_AES_256_CBC_SHA256`
   * `TLS_RSA_WITH_AES_256_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_AES_128_GCM_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA256`
   * `TLS_RSA_WITH_AES_128_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
   * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
   * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
   * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`

