---
title: Aangepaste e-mailsjablonen gebruiken in de stap Taak toewijzen
seo-title: Aangepaste e-mailsjablonen gebruiken in de stap Taak toewijzen
description: 'Aangepaste e-mailsjablonen voor e-mailmeldingen in de formulierwerkstroom '
seo-description: 'Aangepaste e-mailsjablonen voor e-mailmeldingen in de formulierwerkstroom '
uuid: ba453d54-813f-4a4f-a82e-1a6a28b6939c
topic-tags: publish
discoiquuid: 2ad4b7b5-2162-4599-af3f-9476f1256de6
docset: aem65
translation-type: tm+mt
source-git-commit: 76908a565bf9e6916db39d7db23c04d2d40b3247
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# Aangepaste e-mailsjablonen gebruiken in een stap Taak toewijzen{#use-custom-email-templates-in-an-assign-task-step}

Met de stap Taak toewijzen kunt u taken maken en toewijzen aan een gebruiker of groep. Wanneer een taak aan een gebruiker of een groep wordt toegewezen, wordt een e-mailbericht verzonden naar de bepaalde gebruiker of naar elk lid van de bepaalde groep. Een typisch e-mailbericht bevat een koppeling naar de toegewezen taak en informatie met betrekking tot de taak. In de volgende afbeelding wordt een voorbeeld-e-mailmelding weergegeven:

![E-mailmelding met een e-mailadres uit de vaksjabloon](do-not-localize/default_email_template_new.png)

U kunt de weergave aanpassen en aangepaste metagegevens in een e-mailmelding gebruiken. AEM Forms geeft een sjabloon buiten het vak voor e-mailberichten op. U kunt de sjabloon buiten het vak aanpassen of een nieuwe sjabloon maken.

Sjablonen voor e-mailmeldingen zijn gebaseerd op [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). Deze e-mailberichten worden aangepast aan verschillende e-mailclients en schermgrootten. Bovendien wordt de opmaak van de e-mail gedefinieerd in de sjabloon.

In de volgende afbeelding wordt een aangepast e-mailbericht weergegeven:

![E-mailmelding met aangepaste sjabloon](do-not-localize/customized-email.png)

## De bestaande sjabloon {#customize-the-existing-template} aanpassen

AEM Forms beschikt over een sjabloon voor e-mailberichten. De sjabloon bevat een beschrijving van de titel, de vervaldatum, de prioriteit, de naam van de workflow en de koppeling naar de toegewezen taak. U kunt de sjabloon aanpassen om de weergave te wijzigen. Voer de volgende stappen uit om de sjabloon aan te passen:

1. Meld u aan bij CRXDE met beheerdersaccount.

1. Navigeer naar /libs/fd/dashboard/templates/email.

1. Open het bestand htmlEmailTemplate.txt. Het bevat de standaardsjabloon.

1. Vervang de inhoud van het bestand htmlEmailTemplate.txt door aangepaste inhoud.

   Een sjabloon voor e-mailmeldingen is een [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). U kunt de bestaande HTML-code vervangen door uw aangepaste code om de weergave van de sjabloon te wijzigen.

1. Sla het bestand op. De aangepaste sjabloon is nu gebruiksklaar.

## Een e-mailsjabloon maken {#create-an-email-template}

AEM Forms beschikt over een sjabloon voor e-mailberichten. De sjabloon bevat een beschrijving van de titel, de vervaldatum, de prioriteit, de naam van de workflow en de koppeling naar de toegewezen taak. U kunt ook een aangepaste e-mailsjabloon (uw eigen sjabloon) toevoegen voor taakstappen toewijzen. Voer de volgende stappen uit om een aangepaste e-mailsjabloon toe te voegen:

1. Meld u aan bij CRXDE met beheerdersaccount.

1. Navigeer naar /libs/fd/dashboard/templates/email.

1. Maak een TXT-bestand. Bijvoorbeeld EmailOnTaskAssign.txt.

1. Voeg aangepaste HTML-code toe aan het bestand.

   Een sjabloon voor e-mailmeldingen is een [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). U kunt aangepaste HTML-code aan het bestand toevoegen om een nieuwe sjabloon te maken.

1. Sla het bestand op. Het malplaatje is klaar voor gebruik in de stap van de Taak toewijzen.

## Een e-mailsjabloon gebruiken in een taakstap toewijzen {#use-an-email-template-in-an-assign-task-step}

Uit de doos, wordt de taakstap van de Toewijzing gevormd om het standaardmalplaatje, htmlEmailTemplate.txt te gebruiken. U kunt een aangepaste sjabloon gebruiken. De sjabloon wijzigen:

1. Open de stap Taak toewijzen.

1. Navigeer naar Toegewezen > HTML-e-mailsjabloon.

1. Selecteer de nieuwe HTML-e-mailsjabloon.

1. Klik op??OK. De sjabloon is gewijzigd.

Een e-mailmelding gebruikt ook [metadata](../../forms/using/use-metadata-in-email-notifications.md). Bijvoorbeeld datum, prioriteit, naam van workflow en meer. U kunt het malplaatje ook vormen om [douanemetagegevens](../../forms/using/use-metadata-in-email-notifications.md#using-custom-metadata-in-an-email-notification) te gebruiken.
