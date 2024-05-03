---
title: Integratie met Adobe Sign | Gebruikersgegevens verwerken
description: Leer AEM Forms-integratie met Adobe Sign voor e-handtekeningen in adaptieve formulieren. Het steunt veelvoudige het ondertekenen opties voor diverse werkschema's.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Acrobat Sign
role: Admin, User, Developer
exl-id: b43ed9b7-b1ef-4878-ae3b-643b558eed7b
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Integratie met Adobe Sign | Gebruikersgegevens verwerken {#integration-with-adobe-sign-handling-user-data}

[!DNL AEM Forms] integreert met[!DNL  Adobe Sign] workflows voor e-handtekeningen in adaptieve formulieren mogelijk te maken om formulieren of overeenkomsten te verwerken voor workflows voor juridische, verkoop-, salaris- en personeelsbeheer. Het staat voor enig en multiuser het ondertekenen, opeenvolgende en gelijktijdige het ondertekenen werkschema&#39;s toe, het ondertekenen van formulieren als anonieme of het programma geopende gebruiker, en veelvoudige manieren om gebruikers voor authentiek te verklaren.

Wanneer een ondertekenaar of meerdere ondertekenaars een adaptief formulier ondertekenen en verzenden, kan een [!DNL Adobe Sign] er wordt een overeenkomst gegenereerd die informatie over de ondertekenaars bevat.

Voor meer informatie over [!DNL AEM Forms] integratie met [!DNL Adobe Sign], zie [Adobe Sign in een adaptieve vorm gebruiken](/help/forms/using/working-with-adobe-sign.md).

## Gebruikersgegevens en gegevensopslag {#data}

[!DNL Adobe Sign] Het ingeschakelde adaptieve formulier bevat informatie over de ondertekenaars en kan andere gebruikersgegevens bevatten die door het adaptieve formulier zijn verzameld. De [!DNL Adobe Sign] de dienst bewaart gebruikersgegevens met de handtekening binnen de overeenkomst. De overeenkomst wordt opgeslagen op een [!DNL Adobe Sign] server geconfigureerd in [!DNL AEM Forms] cloudservices. Als het adaptieve formulier is geconfigureerd om de actie Forms Portal verzenden te gebruiken, worden de gegevens van de overeenkomst samen met de formuliergegevens opgeslagen in de Forms Portal-gegevensopslag.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Gebruikersgegevens worden verzameld binnen de overeenkomst, maar niet opgeslagen in een van de servicetabellen. [!DNL Adobe Sign] laat beheerders toe om hun eigen keuzen te maken bij het beheren van de gegevens die zij in de dienst controleren. Privacy-beheerders op de [!DNL Adobe Sign] de dienst kan overeenkomsten op het e-mailadres van een aanvrager een lijst maken of verwijderen.

[!DNL Adobe Sign] biedt een webtoepassing aan die het zoeken naar overeenkomsten door deelnemers toestaat en, indien nodig, het verwijderen ervan. Zie voor meer informatie [Adobe Sign - Functie: Gebruikersgegevens verwijderen](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Overeenkomstgegevens voor adaptieve formulieren die zijn geconfigureerd voor het gebruik van de handeling Forms Portal verzenden, worden ook opgeslagen in de Forms Portal-gegevensopslag. Als u gegevens uit de Forms Portal-gegevensopslag wilt openen en verwijderen, raadpleegt u [Forms Portal | Gebruikersgegevens verwerken](/help/forms/using/forms-portal-handling-user-data.md).
