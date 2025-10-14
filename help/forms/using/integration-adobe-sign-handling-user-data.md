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

[!DNL AEM Forms] kan worden geïntegreerd met [!DNL &#x200B; Adobe Sign] om workflows voor e-handtekeningen in adaptieve formulieren in te schakelen voor het verwerken van formulieren of overeenkomsten voor juridische workflows, verkoop, salarisverwerking en workflows voor personeelsbeheer. Het staat voor enig en multiuser het ondertekenen, opeenvolgende en gelijktijdige het ondertekenen werkschema&#39;s toe, het ondertekenen van formulieren als anonieme of het programma geopende gebruiker, en veelvoudige manieren om gebruikers voor authentiek te verklaren.

Wanneer een ondertekenaar of meerdere ondertekenaars een adaptief formulier ondertekenen en verzenden, wordt een [!DNL Adobe Sign] -overeenkomst gegenereerd die informatie over de ondertekenaars bevat.

Voor meer informatie over [!DNL AEM Forms] integratie met [!DNL Adobe Sign], zie [&#x200B; Gebruikend Adobe Sign in een adaptieve vorm &#x200B;](/help/forms/using/working-with-adobe-sign.md).

## Gebruikersgegevens en gegevensopslag {#data}

[!DNL Adobe Sign] -compatibel adaptief formulier bevat informatie over de ondertekenaars en kan andere gebruikersgegevens bevatten die door het adaptieve formulier zijn verzameld. De service [!DNL Adobe Sign] slaat gebruikersgegevens op met de handtekening in de overeenkomst. De overeenkomst wordt opgeslagen op een [!DNL Adobe Sign] -server die is geconfigureerd in [!DNL AEM Forms] -cloudservices. Als het adaptieve formulier is geconfigureerd om de actie Forms Portal verzenden te gebruiken, worden de gegevens van de overeenkomst samen met de formuliergegevens opgeslagen in de Forms Portal-gegevensopslag.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Gebruikersgegevens worden verzameld binnen de overeenkomst, maar niet opgeslagen in een van de servicetabellen. Met [!DNL Adobe Sign] kunnen beheerders hun eigen keuzes maken voor het beheer van de gegevens die ze in de service beheren. Privacy-beheerders van de [!DNL Adobe Sign] -service kunnen op basis van het e-mailadres van een aanvrager overeenkomsten weergeven of verwijderen.

[!DNL Adobe Sign] biedt een webtoepassing waarmee u overeenkomsten door deelnemers kunt zoeken en deze zo nodig kunt verwijderen. Voor meer informatie, zie [&#x200B; Adobe Sign - Eigenschap: de Informatie van de Gebruiker van de Schrapping &#x200B;](https://helpx.adobe.com/nl/sign/help/adobesign_gdpr_user_deletion.html).

Overeenkomstgegevens voor adaptieve formulieren die zijn geconfigureerd voor het gebruik van de handeling Forms Portal verzenden, worden ook opgeslagen in de Forms Portal-gegevensopslag. Om tot gegevens van de Poortgegevensopslag van Forms toegang te hebben en te schrappen, zie [&#x200B; Forms Portal | Behandeling van gebruikersgegevens &#x200B;](/help/forms/using/forms-portal-handling-user-data.md).
