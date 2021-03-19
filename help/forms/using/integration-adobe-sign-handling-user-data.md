---
title: Integratie met Adobe Sign | Gebruikersgegevens verwerken
seo-title: Integratie met Adobe Sign | Gebruikersgegevens verwerken
description: Integratie met Adobe Sign | Gebruikersgegevens verwerken
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Beheerder
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---


# Integratie met Adobe Sign | Gebruikersgegevens {#integration-with-adobe-sign-handling-user-data} verwerken

[!DNL AEM Forms] integreert [!DNL  Adobe Sign] met om werkstromen voor e-handtekeningen mogelijk te maken in adaptieve formulieren voor het verwerken van formulieren of overeenkomsten voor juridische, verkoop-, loon- en personeelsbeheerworkflows. Het staat voor enig en multiuser het ondertekenen, opeenvolgende en gelijktijdige het ondertekenen werkschema&#39;s toe, het ondertekenen van formulieren als anonieme of het programma geopende gebruiker, en veelvoudige manieren om gebruikers voor authentiek te verklaren.

Wanneer een ondertekenaar of meerdere ondertekenaars een adaptief formulier ondertekenen en verzenden, wordt een [!DNL Adobe Sign]-overeenkomst gegenereerd die informatie over de ondertekenaars bevat.

Zie [Adobe Sign gebruiken in een adaptieve vorm](/help/forms/using/working-with-adobe-sign.md) voor meer informatie over [!DNL AEM Forms]-integratie met [!DNL Adobe Sign].

## Gebruikersgegevens en gegevensopslag {#data}

[!DNL Adobe Sign] Het ingeschakelde adaptieve formulier bevat informatie over de ondertekenaars en kan andere gebruikersgegevens bevatten die door het adaptieve formulier zijn verzameld. De [!DNL Adobe Sign]-service slaat gebruikersgegevens op met de handtekening in de overeenkomst. De overeenkomst wordt opgeslagen op [!DNL Adobe Sign]-server die is geconfigureerd in [!DNL AEM Forms]-cloudservices. Als het adaptieve formulier is geconfigureerd om de verzendactie Forms Portal te gebruiken, worden de gegevens van de overeenkomst samen met de formuliergegevens opgeslagen in de gegevensopslag van de portal Formulieren.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Gebruikersgegevens worden verzameld binnen de overeenkomst, maar niet opgeslagen in een van de servicetabellen. [!DNL Adobe Sign] laat beheerders toe om hun eigen keuzen te maken bij het beheren van gegevens die zij in de dienst controleren. De beheerders van de privacy op de [!DNL Adobe Sign] dienst kunnen van overeenkomsten een lijst maken of verwijderen die op het e-mailadres van een aanvrager worden gebaseerd.

[!DNL Adobe Sign] biedt een webtoepassing aan die het zoeken naar overeenkomsten door deelnemers toestaat en, indien vereist, het verwijderen ervan. Zie [Adobe Sign - Functie voor meer informatie: Gebruikersgegevens verwijderen](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Overeenkomstgegevens voor adaptieve formulieren die zijn geconfigureerd om de handeling voor het verzenden van het Forms Portal te gebruiken, worden ook opgeslagen in de gegevensopslag van het formulierportaal. Zie [Forms portal voor toegang tot gegevens en verwijdering uit de opslag met formulierportalgegevens | Gebruikersgegevens verwerken](/help/forms/using/forms-portal-handling-user-data.md).
