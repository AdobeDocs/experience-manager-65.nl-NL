---
title: Overwegingen bij het uitvoeren van AdministrationConsole
seo-title: Overwegingen bij het uitvoeren van AdministrationConsole
description: Dit document bevat een aantal punten waarmee u rekening kunt houden wanneer u de beheerconsole uitvoert.
seo-description: Dit document bevat een aantal punten waarmee u rekening kunt houden wanneer u de beheerconsole uitvoert.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Overwegingen bij het uitvoeren van beheerconsole {#considerations-when-running-administrationconsole}

Dit zijn sommige dingen om te overwegen wanneer het runnen van de Console van het Beleid:

* Als u tot beleidsconsole toegang hebt gebruikend URL `https://[hostname]:'port'/adminui`, kan de gespecificeerde gastheernaam geen onderstrepingstekens bevatten. Anders, werken de verbindingen aan sommige gebieden van de beleidsconsole niet behoorlijk.
* Als u beleidsconsole in de Ontdekkingsreiziger van Vensters op Japans OS in werking stelt, kunt u deze problemen omringen:

   * Als u op een koppeling klikt, keert u terug naar de aanmeldingspagina in plaats van naar de verwachte koppeling.
   * Als u op een koppeling klikt, wordt een machtigingsfout weergegeven.
   De beste praktijken worden in werking gesteld beleidsconsole van andere browser, zoals Mozilla Firefox, om ervoor te zorgen dat geen verbindingen zullen ontbreken.

* Gebruik geen backslash-tekens () wanneer u zoekopdrachten uitvoert in de beheerconsole.

