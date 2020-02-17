---
title: Toepassingen importeren en beheren
seo-title: Toepassingen importeren en beheren
description: Leer hoe u toepassingen kunt importeren en beheren.
seo-description: Leer hoe u toepassingen kunt importeren en beheren.
uuid: 7fba6c4e-1a3e-4a4b-9201-acf2ff66a9df
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dc53a6d0-317a-4abd-990c-455e13f8b824
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Toepassingen importeren en beheren{#import-and-manage-applications}

In AEM-formulieren is een *toepassing* een container waarin elementen worden opgeslagen die vereist zijn voor de implementatie van een AEM-formulieroplossing. Voorbeelden van elementen zijn formulierontwerpen, formulierfragmenten, afbeeldingen, processen, DDX-bestanden, formulierhulplijnen, HTML-pagina&#39;s en SWF-bestanden. Tijdens de ontwikkelingsfase van een project, kunnen de gebruikers Workbench toepassingen van de mening van Toepassingen in Workbench direct opstellen. Zodra opgesteld, verschijnen deze toepassingen in beleidsconsole, op het lusje van Toepassingen op de pagina van het Beheer van de Toepassing.

Wanneer een toepassing klaar is voor implementatie op een productieserver, verpakt de Workbench-gebruiker de toepassing in een *AEM-formuliertoepassingsbestand* (.lca). Dan gebruikt een beheerder beleidsconsole om het toepassingsdossier in te voeren en op te stellen, gebruikend het lusje van Toepassingen op de pagina van het Beheer van de Toepassing.

U kunt het archieflusje op de pagina van het Beheer van de Toepassing ook gebruiken om LCAs in te voeren die gebruikend werkbank 8.x werden gecreeerd.

>[!NOTE]
>
>Er is een bekend probleem dat LCA-bestanden uit een toekomstige release niet altijd compatibel zijn met oudere versies. Het is mogelijk om LCA-bestanden uit een toekomstige versie van AEM-formulieren (bijvoorbeeld een voorbeeldversie) weer te geven en te importeren, maar dit wordt niet ondersteund en kan leiden tot afwijkend gedrag.

Met het tabblad Toepassingen kunt u toepassingen importeren en beheren die in Workbench zijn gemaakt. Toepassingsbeheerders kunnen ook de runtimeconfiguratie voor een toepassing exporteren. Wanneer u de runtimeconfiguratie exporteert, hoeft u instellingen in de productieomgeving handmatig opnieuw te configureren voordat u de geïmplementeerde toepassingen start. Het runtime configuratiebestand bevat:

* serviceconfiguratie-instellingen
* groepconfiguratie-instellingen
* eindpuntconfiguratie-instellingen
* beveiligingsprofielen

## Een toepassing of archief importeren {#import-an-application-or-archive}

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Klik op Importeren.
1. Klik op Bladeren en selecteer het .lca-bestand dat u wilt importeren en klik op Voorvertoning. Op de pagina Voorvertoning toepassing wordt informatie over de toepassing weergegeven.
1. (Optioneel) Als u een lijst wilt weergeven met de elementen in de toepassing, klikt u op Elementen weergeven.
1. (Optioneel) Als u de elementen in de runtime wilt implementeren, selecteert u Elementen bij het importeren in runtime implementeren. Als u deze optie niet selecteert, kunt u de elementen later implementeren.
1. Klik op Importeren. De toepassing wordt weergegeven op het tabblad Toepassingen.
1. Meld u aan bij de CRX-opslagplaats met beheerdersreferenties.
1. Navigeren naar inhoud/dam/toepassingen

   >[!NOTE]
   >
   >De geïmporteerde toepassingen worden weergegeven in het knooppunt Toepassingen.

1. Klik op een van de geïmporteerde toepassingen.

   Op het tabblad Eigenschappen aan de rechterkant worden de eigenschappen van het geselecteerde CRX-knooppunt weergegeven.

   De **eigenschap syncState** geeft de status aan van de synchronisatie van gegevens tussen de AEM-formulierserver en de CRX-opslagplaats. Zodra het importproces begint, wordt deze status ingesteld op 0 (nul). Deze status geeft aan dat de gegevens momenteel niet zijn gesynchroniseerd. Wanneer de gegevens worden gesynchroniseerd, wordt de status ingesteld op 1.

## Een toepassing implementeren {#deploy-an-application}

U kunt toepassingen implementeren die u hebt geïmporteerd of die Workbench-gebruikers hebben geïmporteerd uit Workbench.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Schakel het selectievakje naast de toepassing die u wilt implementeren in en klik op Implementeren.
1. Klik op OK in het bevestigingsvenster dat wordt weergegeven.

## Implementatie van een toepassing ongedaan maken {#undeploy-an-application}

U kunt toepassingen verwijderen uit de runtime.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Schakel het selectievakje naast de toepassing die u wilt verwijderen in en klik op Distribueren ongedaan maken.
1. Klik op OK in het bevestigingsvenster dat wordt weergegeven.

## Een toepassing van de server verwijderen {#remove-an-application-from-the-server}

Verwijder de toepassing voordat u deze van de server verwijdert.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Schakel het selectievakje naast de toepassing die u wilt verwijderen in en klik op Verwijderen.
1. Klik op OK in het bevestigingsvenster dat wordt weergegeven.

## De runtimeconfiguratie van een toepassing importeren {#import-an-application-s-runtime-configuration}

Als een toepassingsbeheerder de runtime configuratie voor een toepassing heeft uitgevoerd, kunt u het in de opgestelde toepassing invoeren. U kunt het invoeren gebruikend of de beleidsconsole of via gescripte plaatsing LCA.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Klik op de naam van de toepassing.
1. Klik op Runtime Config importeren.
1. Klik op Bladeren en selecteer het XML-bestand dat de runtimeconfiguratie bevat.
1. Klik op Importeren.

## De runtimeconfiguratie van een toepassing exporteren {#export-an-application-s-runtime-configuration}

U kunt de runtime configuratieinformatie voor opgestelde toepassingen uitvoeren.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Klik op de naam van de toepassing.
1. Klik op Runtime Config exporteren en sla het configuratiebestand (XML) op dat wordt gemaakt.

## Scripts implementeren van AEM-formuliertoepassingen {#scripted-deployment-of-aem-forms-applications}

U kunt ook een gescripte implementatie gebruiken om toepassingsbestanden in te voeren, inclusief een bestand settings.xml dat de volgende instellingen opgeeft:

* serviceconfiguratie-instellingen
* groepconfiguratie-instellingen
* eindpuntconfiguratie-instellingen
* beveiligingsprofielen

De plaatsing Scripted elimineert de behoefte om montages in het productiemilieu manueel aan te passen alvorens opgezette toepassingen te beginnen.

1. Navigeer vanuit een opdrachtprompt naar *[em-forms root]*/sdk/misc/Foundation/ArchiveManagement.
1. Controleer het bestand ReadMe.txt voor meer gedetailleerde instructies.
1. Wijzig handmatig de bestanden scriptedDeploy.bat en sample-files/sample.xml, zoals beschreven in het bestand readme.txt.
1. Voer het bestand scriptedDeploy.bat uit. Met deze actie implementeert u het archiefbestand voor AEM-formulieren met de overschrijvingsinstellingen.

