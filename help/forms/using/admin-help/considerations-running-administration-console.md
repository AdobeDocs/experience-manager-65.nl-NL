---
title: Overwegingen bij het uitvoeren van beheerconsole
description: Dit document bevat een aantal punten waarmee u rekening kunt houden wanneer u de beheerconsole uitvoert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e15dae6f-d30d-4770-a5ca-34f522a01d31
source-git-commit: e33816b3b8d190e185d2b23dad3a05aca272f01c
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Overwegingen bij het uitvoeren van beheerconsole {#considerations-when-running-administrationconsole}

Dit zijn sommige dingen om te overwegen wanneer het runnen van de Console van het Beleid:

* Als u tot beleidsconsole toegang hebt gebruikend URL `https://[hostname]:'port'/adminui`, mag de opgegeven hostnaam geen onderstrepingstekens bevatten. Anders, werken de verbindingen aan sommige gebieden van de beleidsconsole misschien niet behoorlijk.
* Als u een beleidsconsole in de Ontdekkingsreiziger van Vensters op Japans OS in werking stelt, kunt u deze problemen ontmoeten:

   * Als u op een koppeling klikt, keert u terug naar de aanmeldingspagina in plaats van naar de verwachte koppeling.
   * Als u op een koppeling klikt, wordt een machtigingsfout weergegeven.

  De beste praktijken moeten de beleidsconsole van andere browser, zoals Mozilla Firefox in werking stellen, om ervoor te zorgen dat geen verbindingen ontbreken.

* Gebruik geen backslash-tekens () wanneer u zoekopdrachten uitvoert in de beheerconsole.
