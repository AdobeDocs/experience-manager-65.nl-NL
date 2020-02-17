---
title: Integratie met Adobe Sign| Gebruikersgegevens verwerken
seo-title: Integratie met Adobe Sign| Gebruikersgegevens verwerken
description: 'null'
seo-description: 'null'
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Integratie met Adobe Sign| Gebruikersgegevens verwerken {#integration-with-adobe-sign-handling-user-data}

AEM Forms integreert met Adobe Sign om workflows voor e-handtekeningen in adaptieve formulieren in te schakelen voor het verwerken van formulieren of overeenkomsten voor juridische, verkoop-, salaris- en personeelsbeheerworkflows. Het staat voor enig en multiuser het ondertekenen, opeenvolgende en gelijktijdige het ondertekenen werkschema&#39;s toe, het ondertekenen van formulieren als anonieme of het programma geopende gebruiker, en veelvoudige manieren om gebruikers voor authentiek te verklaren.

Wanneer een ondertekenaar of meerdere ondertekenaars een adaptief formulier ondertekenen en verzenden, wordt een Adobe-ondertekeningsovereenkomst gegenereerd die informatie over de ondertekenaars bevat.

Zie Adobe Sign in een adaptief formulier [](/help/forms/using/working-with-adobe-sign.md)gebruiken voor meer informatie over de integratie van AEM Forms met Adobe Sign.

## Gebruikersgegevens en gegevensopslag {#data}

Het adaptieve formulier dat is ingeschakeld voor ondertekening door Adobe bevat informatie over de ondertekenaars en kan andere gebruikersgegevens bevatten die zijn verzameld door het adaptieve formulier. De Adobe-ondertekeningsservice slaat gebruikersgegevens op met de handtekening in de overeenkomst. De overeenkomst wordt opgeslagen op de Adobe-ondertekeningsserver die is geconfigureerd in de cloudservices van AEM Forms. Als het adaptieve formulier is geconfigureerd om de verzendactie Forms Portal te gebruiken, worden de gegevens van de overeenkomst samen met de formuliergegevens opgeslagen in de gegevensopslag van de portal Formulieren.

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

Gebruikersgegevens worden verzameld binnen de overeenkomst, maar niet opgeslagen in een van de servicetabellen. Met Adobe Sign kunnen beheerders hun eigen keuzes maken voor het beheer van gegevens die ze in de service beheren. Privacy-beheerders op de Adobe-ondertekeningsservice kunnen overeenkomsten weergeven of verwijderen op basis van het e-mailadres van een aanvrager.

Adobe Sign biedt een webtoepassing waarmee deelnemers kunnen zoeken naar overeenkomsten en deze zo nodig kunnen verwijderen. Zie [Ondertekenen door Adobe - Functie voor meer informatie: Gebruikersgegevens](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html)verwijderen.

Overeenkomstgegevens voor adaptieve formulieren die zijn geconfigureerd om de handeling Formulierportal verzenden te gebruiken, worden ook opgeslagen in de gegevensopslag van de portal Formulieren. Zie Formulierportal voor toegang tot gegevens en het verwijderen van gegevens uit de opslagplaats van formulierportal [| Gebruikersgegevens](/help/forms/using/forms-portal-handling-user-data.md)verwerken.
