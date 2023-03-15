---
title: Het vormen uit de Montages van het Bureau
seo-title: Configuring Out of Office Settings
description: Met de functie Buiten-kantoor kunt u opgeven wanneer een gebruiker buiten het kantoor komt en geen taken kan uitvoeren die door AEM formulieren zijn toegewezen.
seo-description: The Out of Office feature enables you to specify when a user will be out of the office and unable to complete tasks assigned by AEM forms.
uuid: 0d01df0a-aa6a-40e5-bf24-423ed1c932cc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 30312159-58a5-4781-b554-29dcbce696cb
exl-id: 1c8ad09b-d44a-4d90-86d5-d4c66cf5c57c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Het vormen uit de Montages van het Bureau {#configuring-out-of-office-settings}

De functie Buiten het Bureau laat gebruikers of beheerders toe om te specificeren wanneer een gebruiker uit het bureau zal zijn en niet om taken te voltooien die door AEM vormen worden toegewezen. Terwijl een gebruiker aan uit Bureau wordt geplaatst, worden hun taken toegewezen aan één of meerdere aangewezen gebruikers. Gebruikers kunnen hun instellingen voor Buiten-Office wijzigen in Workspace of beheerders kunnen de instellingen namens een gebruiker wijzigen in de formulierworkflow.

Wanneer het creëren van een proces, kan de gebruiker Workbench specificeren of een taak wegens uit de montages van het Bureau kan worden opnieuw gericht.

## De informatie van een gebruiker van het Bureau van de mening {#view-a-user-s-out-of-office-information}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Buiten Office.
1. In de doos dichtbij de bovenkant van uit de pagina van het Bureau, kunt u één van het volgende doen:

   **Zoeken op naam**

   Selecteer de optie Zoeken op naam. Typ de gebruikersnaam volledig of gedeeltelijk en klik op Zoeken. Als u het veld leeg laat, wordt een lijst met alle gebruikers geretourneerd in de Forms-workflow

   **Zoeken op datumbereik**

   Selecteer de optie Zoeken op datumbereik. Geef de datums van en tot en met de gewenste tijdstempels op om het zoekresultaat te beperken. Klik op Zoeken.

1. Klik op een gebruikersnaam om de gegevens van de gebruiker buiten het kantoor onder de lijst met gebruikers weer te geven.

## De status van een gebruiker buiten het kantoor wijzigen {#change-a-user-s-out-of-office-status}

1. Zoek de gebruiker, zoals beschreven in [De informatie van een gebruiker van het Bureau van de mening](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
1. Klik op de naam van de gebruiker die u wilt wijzigen.
1. Van de *Gebruikersnaam* is momenteel lijst, uitgezocht of in het Bureau of uit het Bureau.
1. Klik op Opslaan.

## Voeg een uit de datumwaaier van het Bureau voor een gebruiker toe {#add-an-out-of-office-date-range-for-a-user}

1. Zoek de gebruiker, zoals beschreven in [De informatie van een gebruiker van het Bureau van de mening](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
1. Klik op de naam van de gebruiker die u wilt wijzigen.
1. Klik op Datumbereik toevoegen.
1. Voer een begintijd en eindtijd in. U kunt op het pictogram Kalender klikken om een datum te selecteren. Als u geen eindtijd specificeert, zal de gebruiker onbeperkt uit bureau worden geplaatst.
1. Klik op Opslaan.

## Wijs een gebruiker voor uit de taken van het Bureau toe {#assign-a-user-for-out-of-office-tasks}

Wanneer een gebruiker buiten het kantoor is, kunt u een of meer gebruikers toewijzen om nieuwe taken voor de gebruiker uit te voeren. U kunt de volgende configuraties instellen:

* Wijs alle nieuwe taken aan een aangewezen standaardgebruiker toe.
* Wijs geen taken opnieuw toe. De nieuwe taken blijven toegewezen aan de gebruiker die uit het bureau is.
* Wijs een standaardgebruiker toe die de meeste taken van de gebruiker zal ontvangen, maar specificeer dat de taken van bepaalde processen aan andere gebruikers opnieuw worden toegewezen of aan de gebruiker blijven die uit het bureau is toegewezen.
* Wijs geen standaardgebruiker toe, maar wijs bepaalde taken van bepaalde processen aan specifieke gebruikers toe.

   1. Zoek de gebruiker, zoals beschreven in [De informatie van een gebruiker van het Bureau van de mening](configuring-out-office-settings.md#view-a-user-s-out-of-office-information).
   1. Klik op de naam van de gebruiker die u wilt wijzigen.
   1. In de StandaardGebruiker voor uit de lijst van Taken van het Bureau, selecteer een gebruiker van de lijst. Als u geen standaardgebruiker wilt aanwijzen om opnieuw toegewezen punten te ontvangen, uitgezocht wijs niet toe.

      Als de juiste gebruikersnaam niet in de lijst staat, klikt u op Gebruiker zoeken en gebruikt u het dialoogvenster Gebruiker zoeken om naar de gebruiker te zoeken. Selecteer de gewenste gebruiker in de lijst en klik op Gebruiker selecteren. U kunt ook op Gebruikersoverzicht weergeven in het dialoogvenster Gebruiker zoeken klikken om de geselecteerde planning voor een gebruiker buiten het kantoor te bekijken.

   1. Als er processen zijn die niet naar de standaardgebruiker zouden moeten worden verzonden, voegt de klik een Uitzondering toe, dan selecteert het proces en selecteert een andere gebruiker van de lijst. U kunt ook selecteren niet toewijst om de taak te hebben toegewezen aan de gebruiker die uit het bureau is.
   1. Klik op Opslaan.
