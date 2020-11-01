---
title: Integratie met Adobe Sign | Gebruikersgegevens verwerken
seo-title: Integratie met Adobe Sign | Gebruikersgegevens verwerken
description: Integratie met Adobe Sign | Gebruikersgegevens verwerken
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Integratie met Adobe Sign | Gebruikersgegevens verwerken {#integration-with-adobe-sign-handling-user-data}

[!DNL AEM Forms] geïntegreerd met[!DNL  Adobe Sign] het oog op het mogelijk maken van workflows voor e-handtekeningen in adaptieve formulieren voor het verwerken van formulieren of overeenkomsten voor juridische, verkoop-, loon- en personeelsbeheerworkflows. Het staat voor enig en multiuser het ondertekenen, opeenvolgende en gelijktijdige het ondertekenen werkschema&#39;s toe, het ondertekenen van formulieren als anonieme of het programma geopende gebruiker, en veelvoudige manieren om gebruikers voor authentiek te verklaren.

Wanneer een ondertekenaar of meerdere ondertekenaars een adaptief formulier ondertekenen en verzenden, wordt een [!DNL Adobe Sign] overeenkomst gegenereerd die informatie over de ondertekenaars bevat.

Zie Adobe Sign in een adaptieve vorm [!DNL AEM Forms] gebruiken voor meer informatie over [!DNL Adobe Sign]integratie met [](/help/forms/using/working-with-adobe-sign.md).

## Gebruikersgegevens en gegevensopslag {#data}

[!DNL Adobe Sign] Het ingeschakelde adaptieve formulier bevat informatie over de ondertekenaars en kan andere gebruikersgegevens bevatten die door het adaptieve formulier zijn verzameld. De [!DNL Adobe Sign] service slaat gebruikersgegevens op met de handtekening in de overeenkomst. De overeenkomst wordt opgeslagen op een [!DNL Adobe Sign] server die is geconfigureerd in [!DNL AEM Forms] cloudservices. Als het adaptieve formulier is geconfigureerd om de verzendactie Forms Portal te gebruiken, worden de gegevens van de overeenkomst samen met de formuliergegevens opgeslagen in de gegevensopslag van de portal Formulieren.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Gebruikersgegevens worden verzameld binnen de overeenkomst, maar niet opgeslagen in een van de servicetabellen. [!DNL Adobe Sign] laat beheerders toe om hun eigen keuzen te maken bij het beheren van gegevens die zij in de dienst controleren. De beheerders van de privacy op de [!DNL Adobe Sign] dienst kunnen van overeenkomsten een lijst maken of verwijderen die op het e-mailadres van een aanvrager worden gebaseerd.

[!DNL Adobe Sign] biedt een webtoepassing aan die het zoeken naar overeenkomsten door deelnemers toestaat en, indien vereist, het verwijderen ervan. Zie [Adobe Sign - Functie voor meer informatie: Gebruikersgegevens](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html)verwijderen.

Overeenkomstgegevens voor adaptieve formulieren die zijn geconfigureerd om de handeling voor het verzenden van het Forms Portal te gebruiken, worden ook opgeslagen in de gegevensopslag van het formulierportaal. Ga naar [Forms Portal voor toegang tot gegevens uit de gegevensopslag van het formulierportaal en om deze te verwijderen. | Gebruikersgegevens](/help/forms/using/forms-portal-handling-user-data.md)verwerken.
