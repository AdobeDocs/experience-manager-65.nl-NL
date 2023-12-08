---
title: Verbindingsproblemen met Output, Forms en (Document of Record) DoR Services
description: Los AEM Forms-verbindingsfouten na SP19 op. Stop, installeer Microsoft Visual C++, herstart server voor een naadloze oplossing. Problemen met uitvoer, Forms en DoR oplossen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin
source-git-commit: cf5da092fabbc7834108dc54d65eb97e160984ce
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Kan de Output-service, Forms-service of Document of Record-service (DoR) niet gebruiken {#unable-to-use-output-service-forms-service-or-document-of-record-service}

## Probleem

Wanneer u AEM Forms 6.5 Service Pack 19 hebt geïnstalleerd, kan het zijn dat een poging om de Output-service, Forms-service of Document of Record (DoR)-service te gebruiken, resulteert in een `Connection to failed service` fout.

## Oplossing

Het probleem oplossen:

1. Stop uw AEM 6.5 Forms-exemplaar.
1. Download en installeer de [64-bits versie van Microsoft Visual C++ Redistributable pakketten voor Visual Studio 2015, 2017, 2019, en 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) op de computer waarop AEM 6.5 Forms is geïnstalleerd.
1. Start de AEM Forms-server opnieuw.


>[!NOTE]
>
>
> Zorg ervoor dat u Redistributable installeert, zelfs als een vorige versie geïnstalleerd is.
