---
title: Vertaalprojecten beheren
description: Leer hoe u vertaalprojecten beheert in Adobe Experience Manager.
exl-id: 968bba02-98fe-4eaf-9937-ce5cfdf5b413
solution: Experience Manager, Experience Manager Sites
feature: Language Copy
role: Admin
source-git-commit: 26ac50aa27501fe6a80b38a474e9811338c4fb56
workflow-type: tm+mt
source-wordcount: '3519'
ht-degree: 0%

---

# Vertaalprojecten beheren{#managing-translation-projects}

Nadat u de inhoud hebt voorbereid voor vertaling, moet u de taalstructuur voltooien door ontbrekende taalkopieën te maken en vertaalprojecten te maken.

Met vertaalprojecten kunt u de vertaling van AEM inhoud beheren. Een vertaalproject is een type van AEM [&#x200B; project &#x200B;](/help/sites-authoring/projects.md) dat middelen bevat die in andere talen moeten worden vertaald. Deze middelen zijn de pagina&#39;s en de activa van de [&#x200B; taalexemplaren &#x200B;](/help/sites-administering/tc-prep.md) die van de taalmeester worden gecreeerd.

Wanneer middelen aan een vertaalproject worden toegevoegd, wordt een vertaalbaan gecreeerd voor hen. Taken bieden opdrachten en statusinformatie die u gebruikt om de workflows voor het vertalen van mensen en computers die op de bronnen worden uitgevoerd, te beheren.

>[!NOTE]
>
>Een vertaalproject kan meerdere vertaaltaken bevatten.

Vertaalprojecten zijn langlopende items, die door taal- en vertaalmethode/provider worden gedefinieerd om te worden afgestemd op organisatorisch bestuur voor globalization. Zij moeten eenmaal worden gestart, hetzij tijdens de eerste vertaling, hetzij handmatig, en blijven van kracht gedurende de gehele update van inhoud en vertaling.

Vertaalprojecten en -taken worden gecreëerd met workflows voor het voorbereiden van vertalingen. Deze workflows hebben drie opties, voor zowel de eerste vertaling (Maken&amp;Vertalen) als de updates (Vertaling bijwerken):

1. [Nieuw project maken](#creating-translation-projects-using-the-references-panel)
1. [Toevoegen aan bestaand project](#adding-pages-to-a-translation-project)
1. [Alleen inhoudsstructuur](#creating-the-structure-of-a-language-copy)

>[!NOTE]
>
>Optie 3 houdt geen verband met vertaalwerk/project. Hiermee kunt u inhoud en structurele wijzigingen in de hoofdtaal kopiëren naar (onvertaalde) taalkopieën. U kunt dit gebruiken om uw taalmeesters synchroon te houden, zelfs zonder vertaling.

## Eerste vertalingen uitvoeren en bestaande vertalingen bijwerken {#performing-initial-translations-and-updating-existing-translations}

AEM ontdekt of een vertaalproject voor de aanvankelijke vertaling van inhoud wordt gecreeerd, of reeds-vertaalde taalexemplaren bijwerken. Wanneer u een vertaalproject voor een pagina creeert en de taalexemplaren aangeeft waarvoor u vertaalt, AEM ontdekt of de bronpagina reeds in de gerichte taalexemplaren bestaat:

* **het taalexemplaar omvat niet de pagina:** AEM behandelt deze situatie als aanvankelijke vertaling. De pagina wordt onmiddellijk gekopieerd naar de taalkopie en opgenomen in het project. Wanneer de vertaalde pagina in AEM wordt geïmporteerd, AEM deze rechtstreeks naar de taalkopie gekopieerd.
* **het taalexemplaar omvat reeds de pagina:** AEM behandelt deze situatie als bijgewerkte vertaling. Er wordt een startpagina gemaakt en een kopie van de pagina wordt toegevoegd aan de startpagina en opgenomen in het project. Met behulp van Starten kunt u bijgewerkte vertalingen controleren voordat u deze doorgeeft aan de taalkopie:

   * Wanneer de vertaalde pagina in AEM wordt geïmporteerd, wordt de pagina tijdens het opstarten overschreven.
   * De vertaalde pagina overschrijft de taalkopie alleen wanneer de introductie wordt bevorderd.

Bijvoorbeeld, wordt de /content/geometrixx/fr taalwortel gecreeerd voor de Franse vertaling van de /content/geometrixx/en hoofdtaal. Er zijn geen andere pagina&#39;s in de Franse taalkopie.

* Er wordt een vertaalproject gemaakt voor de pagina /content/geometrixx/nl/products en alle onderliggende pagina&#39;s, met als doelversie de Franse taalkopie. Omdat de taalkopie niet de pagina /content/geometrixx/fr/products bevat, kopieert AEM onmiddellijk de pagina /content/geometrixx/en/products en alle onderliggende pagina&#39;s naar de Franse taalkopie. De kopieën worden ook in het vertaalproject opgenomen.
* Er wordt een vertaalproject gemaakt voor de pagina /content/geometrixx/nl en alle onderliggende pagina&#39;s die zich richten op de Franse taalkopie. Omdat de taalkopie de pagina bevat die overeenkomt met de pagina /content/geometrixx/nl (de hoofdtaal), AEM de pagina /content/geometrixx/nl en alle onderliggende pagina&#39;s gekopieerd en toegevoegd aan een opstart. De kopieën worden ook in het vertaalproject opgenomen.

## Vertaalprojecten maken met het deelvenster Verwijzingen {#creating-translation-projects-using-the-references-panel}

Maak vertaalprojecten zodat u de workflow voor het vertalen van de bronnen van uw taalmaster kunt uitvoeren en beheren. Wanneer u projecten maakt, geeft u de pagina op in het taalstramien dat u vertaalt en de taalkopieën waarvoor u de vertaling uitvoert:

* De wolkenconfiguratie van het kader van de vertaalintegratie dat met de geselecteerde pagina wordt geassocieerd bepaalt vele eigenschappen van de vertaalprojecten, zoals het vertaalwerkschema aan gebruik.
* Er wordt een project gemaakt voor elke geselecteerde taalkopie.
* Er wordt een kopie van de geselecteerde pagina en de bijbehorende elementen gemaakt en aan elk project toegevoegd. Deze kopieën worden later naar de vertaalprovider verzonden voor vertaling.

U kunt opgeven dat de onderliggende pagina&#39;s van de geselecteerde pagina ook worden geselecteerd. In dit geval worden ook kopieën van de onderliggende pagina&#39;s aan elk project toegevoegd, zodat deze worden vertaald. Wanneer om het even welke kindpagina&#39;s met verschillende configuraties van het kader van de vertaalintegratie worden geassocieerd, AEM leidt tot extra projecten.

U kunt ook [&#x200B; manueel vertaalprojecten &#x200B;](#creating-a-translation-project-using-the-projects-console) tot stand brengen.

>[!NOTE]
>
>Uw account moet lid zijn van de `project-administrators` -groep om een project te maken.

**Eerste Vertalingen en het Bijwerken Vertalingen**

In het deelvenster Referenties wordt aangegeven of de bestaande taalkopieën worden bijgewerkt of dat de eerste versie van de taalkopieën wordt gemaakt. Wanneer een taalexemplaar voor de geselecteerde pagina bestaat, lijkt het lusje van de Exemplaren van de Taal van de Update toegang tot project-verwante bevelen te verlenen.

![&#x200B; chlimage_1-239 &#x200B;](assets/chlimage_1-239.png)

Na het vertalen, kunt u [&#x200B; de vertaling &#x200B;](#reviewing-and-promoting-updated-content) herzien alvorens het taalexemplaar met het te beschrijven. Als er geen taalkopie voor de geselecteerde pagina bestaat, wordt op het tabblad Maken en vertalen toegang weergegeven tot opdrachten die betrekking hebben op het project.

![&#x200B; chlimage_1-240 &#x200B;](assets/chlimage_1-240.png)

### Vertaalprojecten maken voor een kopie van nieuwe taal {#create-translation-projects-for-a-new-language-copy}

1. Gebruik de console van Plaatsen om de pagina te selecteren die u aan vertaalprojecten toevoegt.

   Als u bijvoorbeeld de Engelse pagina&#39;s van de demo-site van Geometrixx wilt vertalen, selecteert u Geometrixx demo-site > Engels.

1. Klik op Referenties op de werkbalk.

   ![&#x200B; chlimage_1-241 &#x200B;](assets/chlimage_1-241.png)

1. Selecteer Exemplaren van de Taal, en selecteer dan de taalexemplaren waarvoor u de bronpagina&#39;s vertaalt.
1. Klik op Maken en vertalen en configureer de vertaaltaak vervolgens:

   * Gebruik de drop-down Talen om een taalexemplaar te selecteren waarvoor u wilt vertalen. Selecteer desgewenst extra talen. Talen die in de lijst verschijnen beantwoorden aan de [&#x200B; taalwortels die u &#x200B;](/help/sites-administering/tc-prep.md#creating-a-language-root) hebt gecreeerd.
   * Selecteer Alle subpagina&#39;s selecteren als u de geselecteerde pagina en alle onderliggende pagina&#39;s wilt vertalen. Als u alleen de geselecteerde pagina wilt vertalen, schakelt u de optie uit.
   * Selecteer Nieuw vertaalproject maken bij Project.
   * Typ een naam voor het project.

   ![&#x200B; chlimage_1-242 &#x200B;](assets/chlimage_1-242.png)

1. Klik op Maken.

### Vertaalprojecten maken voor een bestaande taalkopie {#create-translation-projects-for-an-existing-language-copy}

1. Gebruik de console van Plaatsen om de pagina te selecteren die u aan de vertaalprojecten toevoegt.

   Als u bijvoorbeeld de Engelse pagina&#39;s van de demo-site van Geometrixx wilt vertalen, selecteert u Geometrixx demo-site > Engels.

1. Klik op Referenties op de werkbalk.

   ![&#x200B; chlimage_1-243 &#x200B;](assets/chlimage_1-243.png)

1. Selecteer Exemplaren van de Taal, en selecteer dan de taalexemplaren waarvoor u de bronpagina&#39;s vertaalt.
1. Klik op Taalkopieën bijwerken en configureer de vertaaltaak vervolgens:

   * Selecteer Alle subpagina&#39;s selecteren als u de geselecteerde pagina en alle onderliggende pagina&#39;s wilt vertalen. Als u alleen de geselecteerde pagina wilt vertalen, schakelt u de optie uit.
   * Selecteer Nieuw vertaalproject maken bij Project.
   * Typ een naam voor het project.

   ![&#x200B; chlimage_1-244 &#x200B;](assets/chlimage_1-244.png)

1. Klik op Start.

## Pagina&#39;s toevoegen aan een vertaalproject {#adding-pages-to-a-translation-project}

Nadat u een vertaalproject hebt gecreeerd, kunt u de ruit van Middelen gebruiken om pagina&#39;s aan het project toe te voegen. Het toevoegen van pagina&#39;s is handig wanneer u pagina&#39;s van verschillende vertakkingen in hetzelfde project opneemt.

Wanneer u pagina&#39;s toevoegt aan een vertaalproject, worden de pagina&#39;s opgenomen in een nieuwe vertaaltaak. U kunt ook [&#x200B; pagina&#39;s aan een bestaande baan &#x200B;](#adding-pages-assets-to-a-translation-job) toevoegen.

Net als bij het maken van een project worden bij het toevoegen van pagina&#39;s kopieën van de pagina&#39;s zo nodig toegevoegd aan een opstart om te voorkomen dat bestaande taalkopieën worden overschreven. (Zie [&#x200B; Creërend Vertaalprojecten voor Bestaande Exemplaren van de Taal &#x200B;](#performing-initial-translations-and-updating-existing-translations).)

1. Gebruik de console van Plaatsen om de pagina te selecteren die u aan het vertaalproject toevoegt.

   Als u bijvoorbeeld de Engelse pagina&#39;s van de demo-site van Geometrixx wilt vertalen, selecteert u Geometrixx demo-site > Engels.

1. Klik op Referenties op de werkbalk.

   ![&#x200B; chlimage_1-245 &#x200B;](assets/chlimage_1-245.png)

1. Selecteer Exemplaren van de Taal, en selecteer dan de taalexemplaren waarvoor u de bronpagina&#39;s vertaalt.

   ![&#x200B; chlimage_1-35 &#x200B;](assets/chlimage_1-35.jpeg)

1. Klik op Taalkopieën bijwerken en configureer vervolgens de eigenschappen:

   * Selecteer Alle subpagina&#39;s selecteren als u de geselecteerde pagina en alle onderliggende pagina&#39;s wilt vertalen. Als u alleen de geselecteerde pagina wilt vertalen, schakelt u de optie uit.
   * Selecteer bij Project de optie Toevoegen aan bestaand vertaalproject.
   * Selecteer het project.

   >[!NOTE]
   >
   >De doeltaal die is ingesteld in het vertaalproject moet overeenkomen met het pad van de taalkopie zoals wordt weergegeven in het deelvenster Verwijzingen.

   ![&#x200B; chlimage_1-36 &#x200B;](assets/chlimage_1-36.jpeg)

1. Klik op Start.

## Pagina&#39;s/Assets toevoegen aan een vertaaltaak {#adding-pages-assets-to-a-translation-job}

U kunt pagina&#39;s, elementen, tags of i18n-woordenboeken toevoegen aan de vertaaltaak van uw vertaalproject. Pagina&#39;s of elementen toevoegen:

1. Klik onder aan de tegel Vertaal taak van het vertaalproject op de ellips.

   ![&#x200B; chlimage_1-246 &#x200B;](assets/chlimage_1-246.png)

1. Klik op Add and Pages/Assets.

   ![&#x200B; chlimage_1-247 &#x200B;](assets/chlimage_1-247.png)

1. Selecteer het bovenste item van de vertakking die u wilt toevoegen en klik op het pictogram van het vinkje. U kunt meerdere selecties maken.

   ![&#x200B; chlimage_1-248 &#x200B;](assets/chlimage_1-248.png)

1. U kunt ook het zoekpictogram selecteren om gemakkelijk te zoeken naar pagina&#39;s of elementen die u aan uw vertaaltaak wilt toevoegen.

   ![&#x200B; chlimage_1-249 &#x200B;](assets/chlimage_1-249.png)

Uw pagina&#39;s en/of middelen worden toegevoegd aan uw vertaalbaan.

## i18n-woordenboeken toevoegen aan een vertaaltaak {#adding-i-n-dictionaries-to-a-translation-job}

U kunt pagina&#39;s, elementen, tags of i18n-woordenboeken toevoegen aan de vertaaltaak van uw vertaalproject. Een i18n-woordenboek toevoegen:

1. Klik onder aan de tegel Vertaal taak van het vertaalproject op de ellips.

   ![&#x200B; chlimage_1-250 &#x200B;](assets/chlimage_1-250.png)

1. Klik op Toevoegen en I18N-woordenboek.

   ![&#x200B; chlimage_1-251 &#x200B;](assets/chlimage_1-251.png)

1. Selecteer de **Folder van de Wortel**, en woordenboek (indien nodig), die u wilt toevoegen, en dan selecteren **&#x200B;**&#x200B;toevoegen.

   ![&#x200B; i18N Woordenboek &#x200B;](assets/tc-manage-i18n-dictionary.png)

1. Selecteer desgevraagd de aard van de update:

   ![&#x200B; vertaal &#x200B;](assets/tc-manage-translate.png)

Uw woordenboek staat nu in uw vertaalbaan.

![&#x200B; chlimage_1-253 &#x200B;](assets/chlimage_1-253.png)

>[!NOTE]
>
>Voor meer informatie over i18n woordenboeken, lees [&#x200B; Gebruikend Vertaler om Woordenboeken &#x200B;](/help/sites-developing/i18n-translator.md) te beheren.

## Tags toevoegen aan een vertaaltaak {#adding-tags-to-a-translation-job}

U kunt pagina&#39;s, elementen, tags of i18n-woordenboeken toevoegen aan de vertaaltaak van uw vertaalproject. Tags toevoegen:

1. Klik onder aan de tegel Vertaal taak van het vertaalproject op de ellips.

   ![&#x200B; chlimage_1-254 &#x200B;](assets/chlimage_1-254.png)

1. Klik op Toevoegen en vervolgens op Labels.

   ![&#x200B; chlimage_1-255 &#x200B;](assets/chlimage_1-255.png)

1. Selecteer de tags die u wilt toevoegen en klik op het pictogram van het vinkje. U kunt meerdere selecties maken.

   ![&#x200B; chlimage_1-256 &#x200B;](assets/chlimage_1-256.png)

Uw labels worden nu toegevoegd aan uw vertaaltaak.

![&#x200B; chlimage_1-257 &#x200B;](assets/chlimage_1-257.png)

## Details van vertaalproject bekijken {#seeing-translation-project-details}

De tegel Vertaaloverzicht bevat de eigenschappen die voor een vertaalproject worden gevormd. Naast de generische [&#x200B; projectinformatie &#x200B;](/help/sites-authoring/projects.md#project-info), bevat het lusje van de Vertaling vertaling-specifieke eigenschappen:

* Source Language: De taal van de pagina&#39;s die worden vertaald.
* Doeltaal: de taal waarin de pagina&#39;s worden vertaald.
* Vertaalmethode: de vertaalworkflow. Menselijke vertaling of Machine Translation wordt ondersteund.
* Vertaalprovider: de vertaalserviceprovider die de vertaling uitvoert.
* Inhoudscategorie: (Machine Translation) de inhoudscategorie die wordt gebruikt voor het vertalen.
* Cloud Config: De wolkenconfiguratie voor de schakelaar van de vertaaldienst die voor het project wordt gebruikt.

Wanneer een project gebruikend de ruit van Middelen van een pagina wordt gecreeerd, worden deze eigenschappen automatisch gevormd gebaseerd op de eigenschappen van de bronpagina.

![&#x200B; chlimage_1-258 &#x200B;](assets/chlimage_1-258.png)

## De status van een vertalingstaak controleren {#monitoring-the-status-of-a-translation-job}

De tegel Vertaal baan van een Vertaalproject verstrekt de status van een vertaalbaan, en het aantal pagina&#39;s en activa in de baan.

![&#x200B; chlimage_1-259 &#x200B;](assets/chlimage_1-259.png)

In de volgende tabel wordt elke status beschreven die een taak of een item in de taak kan hebben:

| Status | Beschrijving |
|---|---|
| Concept | De vertaaltaak is niet gestart. Vertaal banen zijn in de status van het CONCEPT wanneer zij worden gecreeerd. |
| Verzonden | Bestanden in de vertaaltaak hebben deze status wanneer ze naar de vertaalservice zijn verzonden. Deze status kan voorkomen nadat het bevel van het Toepassingsgebied van het Verzoek of het bevel van het Begin wordt uitgegeven. |
| Gevraagd bereik | Voor de workflow Menselijke vertaling zijn de bestanden in de taak voor bereiking naar de leverancier van de vertaling verzonden. Deze status wordt weergegeven nadat de opdracht Toepassingsgebied aanvragen is uitgevoerd. |
| Bereik voltooid | De leverancier heeft het bereik van de vertaaltaak. |
| Toegewezen voor vertaling | De eigenaar van het project heeft het toepassingsgebied geaccepteerd. Deze status geeft aan dat de leverancier van de vertaling moet beginnen met het vertalen van de bestanden in de taak. |
| Bezig met omzetten | Voor een taak is de vertaling van een of meer bestanden in de taak nog niet voltooid. Voor een item in de taak wordt het item vertaald. |
| Vertaald | Voor een taak is de vertaling van alle bestanden in de taak voltooid. Voor een item in de taak wordt het item vertaald. |
| Gereed voor revisie | Het item in de taak wordt omgezet en het bestand is geïmporteerd in AEM. |
| Voltooid | De eigenaar van het project heeft aangegeven dat het vertaalcontract volledig is. |
| Annuleren | Geeft aan dat de leverancier van de vertaling moet stoppen met het werken aan een vertaaltaak. |
| Foutupdate | Er is een fout opgetreden bij het overdragen van bestanden tussen AEM en de vertaalservice. |
| Onbekende status | Er is een onbekende fout opgetreden. |

Als u de status van elk bestand in de taak wilt zien, klikt u op de ellips onder aan de tegel.

## Vaststelling van de vervaldatum van de vertaaltaken {#setting-the-due-date-of-translation-jobs}

Geef de datum op waarop de leverancier van de vertaling vertaalde bestanden moet retourneren. U kunt de vervaldatum voor het project of voor een specifieke baan plaatsen:

* **Project:** de banen van de Vertaling in het project erven de vervaldatum.
* **Baan:** de vervaldatum die u voor de baan plaatst treedt de vervaldatum met voeten die voor het project wordt geplaatst.

Het instellen van de vervaldatum werkt alleen correct wanneer de leverancier van de vertaling die u gebruikt deze functie ondersteunt.

In de volgende procedure wordt de vervaldatum voor een project vastgesteld.

1. Klik op de ellips onder aan de tegel Vertaaloverzicht.

   ![&#x200B; chlimage_1-260 &#x200B;](assets/chlimage_1-260.png)

1. Gebruik op het tabblad Standaard de datumkiezer van de eigenschap Einddatum om de vervaldatum te selecteren.

   ![&#x200B; chlimage_1-261 &#x200B;](assets/chlimage_1-261.png)

1. Klik op Gereed.

De volgende procedure stelt de vervaldatum voor een vertaalbaan vast.

1. Klik in de tegel Vertaaltaak op het menu Opdrachten en klik vervolgens op Vervaldatum.

   ![&#x200B; chlimage_1-262 &#x200B;](assets/chlimage_1-262.png)

1. Klik in het dialoogvenster op het kalenderpictogram, selecteer vervolgens de datum en tijd die u als vervaldatum wilt gebruiken en klik op Opslaan.

   ![&#x200B; chlimage_1-263 &#x200B;](assets/chlimage_1-263.png)

## Een vertaaltaak splitsen {#scoping-a-translation-job}

Bereik een vertaalbaan om een schatting van de kosten van vertaling van uw vertaaldienstverlener te verkrijgen. Wanneer u een taak instelt, worden bronbestanden verzonden naar de leverancier van de vertaling die de tekst vergelijkt met de groep met opgeslagen vertalingen (vertaalgeheugen). Doorgaans is het bereik het aantal woorden dat moet worden vertaald.

Neem contact op met uw vertaalleverancier voor meer informatie over bereikresultaten.

>[!NOTE]
>
>Scoping is optioneel. U kunt een vertaalbaan zonder scoping beginnen.

Wanneer u een vertaalbaan werkingsgebied, is de status van de baan `Scope Requested`. Wanneer de leverancier van de vertaling het bereik retourneert, wordt de status gewijzigd in `Scope Completed` . Wanneer het werkingsgebied wordt voltooid, kunt u het tonen bevel van het Toepassingsgebied gebruiken om het scoping resultaten te herzien.

De functie Scoping werkt alleen correct wanneer de leverancier van de vertaling die u gebruikt deze functie ondersteunt.

1. In de console van Projecten, open uw vertaalproject.
1. Klik in de tegel Vertaaltaak op het menu met opdrachten en klik vervolgens op Toepassingsgebied aanvragen.

   ![&#x200B; chlimage_1-264 &#x200B;](assets/chlimage_1-264.png)

1. Wanneer de baanstatus in SCOPE_COMPLETED verandert, op de tegel van de Taak van de Vertaling klikt het bevelenmenu, dan klik tonen Werkgebied.

## Een vertaaltaak starten {#starting-a-translation-job}

Start een vertaaltaak om de bronpagina&#39;s naar de doeltaal te vertalen. De vertaling wordt uitgevoerd volgens de bezitswaarden van de Omzettingssummiere tegel.

Nadat u de vertaaltaak hebt gestart, wordt in de tegel Vertaal-taak de status Vertaling in uitvoering weergegeven.

![&#x200B; chlimage_1-265 &#x200B;](assets/chlimage_1-265.png)

1. In de console van Projecten, open het vertaalproject.
1. Klik in de tegel Vertaal taak op het menu met opdrachten en klik vervolgens op Start.

   ![&#x200B; chlimage_1-266 &#x200B;](assets/chlimage_1-266.png)

1. Klik op Sluiten in het dialoogvenster Handeling waarin het starten van de vertaling wordt bevestigd.

## Een vertaaltaak annuleren {#canceling-a-translation-job}

Een vertaaltaak annuleren om het vertaalproces te stoppen en te voorkomen dat de leverancier van de vertaling verdere vertalingen uitvoert. U kunt een taak annuleren wanneer de taak de status `Committed For Translation` of `Translation In Progress` heeft.

1. In de console van Projecten, open het vertaalproject.
1. Klik in de tegel Vertaaltaak op het menu met opdrachten en klik vervolgens op Annuleren.
1. Klik op OK in het dialoogvenster Handeling waarin de annulering van de vertaling wordt bevestigd.

## Workflow accepteren/afwijzen {#accept-reject-workflow}

Wanneer de inhoud na de vertaling terug komt en klaar voor revisie is, kunt u de vertaalbaan in gaan en inhoud goedkeuren/verwerpen.

![&#x200B; chlimage_1-267 &#x200B;](assets/chlimage_1-267.png)

Als u Vertaling negeren selecteert, kunt u een opmerking toevoegen.

![&#x200B; chlimage_1-268 &#x200B;](assets/chlimage_1-268.png)

Als u inhoud afwijst, wordt deze teruggestuurd naar de leverancier van de vertaling waar de opmerking kan worden weergegeven.

## Bijgewerkte inhoud controleren en promoten {#reviewing-and-promoting-updated-content}

Wanneer de inhoud voor een bestaand taalexemplaar wordt vertaald, herzie de vertalingen, breng veranderingen indien nodig aan, en publiceer dan de vertalingen om het naar het taalexemplaar te bewegen. U kunt vertaalde bestanden reviseren wanneer in de vertaaltaak de status Gereed voor revisie wordt weergegeven.

![&#x200B; chlimage_1-269 &#x200B;](assets/chlimage_1-269.png)

1. Selecteer de pagina in het taalstramien, klik op Verwijzingen en klik vervolgens op Taalkopieën.
1. Klik op de taalkopie die u wilt reviseren.

   ![&#x200B; chlimage_1-270 &#x200B;](assets/chlimage_1-270.png)

1. Klik op Starten om de opdrachten voor het starten weer te geven.

   ![&#x200B; chlimage_1-271 &#x200B;](assets/chlimage_1-271.png)

1. Klik op Pagina openen om het startexemplaar van de pagina te openen om de inhoud te bekijken en bewerken.
1. Klik op Promote nadat u de inhoud hebt bekeken en de benodigde wijzigingen hebt aangebracht om de opstartafbeelding te promoten.
1. Geef op de pagina Starten bevorderen op welke pagina&#39;s u wilt promoten en klik vervolgens op Promote.

## Taalkopieën vergelijken {#comparing-language-copies}

Taalkopieën vergelijken met de taalmaster:

1. In de **console van Plaatsen**, navigeer aan het taalexemplaar u wilt vergelijken.
1. Open het **[paneel van Verwijzingen](/help/sites-authoring/basic-handling.md#references)**.
1. Onder de **koppen** kopbal selecteren **de Kopieën van de Taal.**
1. Selecteer uw specifieke taalkopie en klik op **Vergelijken met stramien &#x200B;** of op **Vergelijken met vorige &#x200B;** indien van toepassing.

   ![&#x200B; chlimage_1-37 &#x200B;](assets/chlimage_1-37.jpeg)

1. De twee pagina&#39;s (opstart en bron) worden naast elkaar geopend.

   Voor volledige informatie over het gebruiken van deze eigenschap zie [&#x200B; Afschuiving van de Pagina &#x200B;](/help/sites-authoring/page-diff.md).

## Vertaaltaken voltooien en archiveren {#completing-and-archiving-translation-jobs}

Voltooi een vertaalbaan nadat u de vertaalde dossiers van de verkoper hebt herzien. Voor workflows voor menselijke vertaling geeft het voltooien van een vertaling de verkoper aan dat het vertaalcontract is uitgevoerd en dat hij de vertaling in zijn vertaalgeheugen moet opslaan.

Nadat u de taak hebt voltooid, heeft de taak de status Voltooid.

![&#x200B; chlimage_1-272 &#x200B;](assets/chlimage_1-272.png)

Archiveer een vertaaltaak nadat deze is voltooid en u hoeft de gegevens over de taakstatus niet meer te zien. Wanneer u de taak archiveert, wordt de tegel Vertaal van de Baan verwijderd uit het project.

## De structuur van een taalkopie maken {#creating-the-structure-of-a-language-copy}

Vul de taalkopie zodanig dat deze inhoud bevat uit de hoofdtaal die u vertaalt. Alvorens u uw taalexemplaar bevolkt, moet u [&#x200B; tot de taalwortel &#x200B;](/help/sites-administering/tc-prep.md#creating-a-language-root) van het taalexemplaar hebben gecreeerd.

1. Gebruik de console van Plaatsen om de taalwortel van de hoofdtaal te selecteren die u als bron gebruikt. Als u bijvoorbeeld de Engelse pagina&#39;s van de demo-site van Geometrixx wilt vertalen, selecteert u Inhoud > Geometrixx demo-site > Engels.
1. Klik op Referenties op de werkbalk.

   ![&#x200B; chlimage_1-273 &#x200B;](assets/chlimage_1-273.png)

1. Selecteer Taalkopieën en selecteer vervolgens de taalkopieën die u wilt vullen.

   ![&#x200B; chlimage_1-38 &#x200B;](assets/chlimage_1-38.jpeg)

1. Klik op Taalkopieën bijwerken om de vertaalgereedschappen weer te geven en de eigenschappen te configureren:

   * Selecteer de optie Alle subpagina&#39;s selecteren.
   * Selecteer bij Project de optie Alleen structuur maken.

   ![&#x200B; chlimage_1-39 &#x200B;](assets/chlimage_1-39.jpeg)

1. Klik op Start.

## Source-pagina&#39;s verplaatsen of hernoemen {#move-source}

Als een reeds vertaalde bronpagina [&#x200B; moet worden anders genoemd of worden bewogen &#x200B;](/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page), leidt het vertalen van de pagina opnieuw na de beweging tot een taalexemplaar dat op de nieuwe paginanaam/de plaats wordt gebaseerd. De oude taalkopie op basis van de vorige naam/locatie is er nog. Om dit te voorkomen, kunt u de functionaliteit voor het kopiëren van de updatetaal na de verplaatsing gebruiken:

1. Verplaats een pagina met een taalkopie.
1. Selecteer de hoofdmap van de taalkopie.
1. Open het **paneel van Verwijzingen**.
1. Selecteer **Exemplaren van Talen**.
1. Selecteer de doeltalen die u wilt bijwerken.
1. Selecteer **de taalexemplaren van de Update**.

   ![&#x200B; het bijwerken-taal-exemplaren &#x200B;](assets/translation-move-to.png)

1. Klik **Update**. A [&#x200B; Lancering &#x200B;](/help/sites-authoring/launches-promoting.md) zal worden gecreeerd.
1. Navigeer naar de vereiste hoofdtaal en selecteer deze.
1. Gebruikend het **paneel van Verwijzingen**, uitgezochte **Lanceringen**.

   ![&#x200B; bevorderen-lancering-vertaling &#x200B;](assets/promote-launch-translation.png)

1. Klik op de Lancering die werd gecreeerd en klik **bevorderen lancering**.

Nu is de bronpagina verplaatst en de bijbehorende taalkopie.

## Een vertaalproject maken met de projectconsole {#creating-a-translation-project-using-the-projects-console}

U kunt een vertaalproject manueel tot stand brengen als u verkiest de console van Projecten te gebruiken.

>[!NOTE]
>
>Uw account moet lid zijn van de `projects-administrators` -groep om een project te maken.

Wanneer u manueel een vertaalproject creeert, moet u waarden voor de volgende op vertaling betrekking hebbende eigenschappen naast de [&#x200B; basiseigenschappen &#x200B;](/help/sites-authoring/touch-ui-managing-projects.md#creating-a-project) verstrekken:

* **Naam:** de naam van het Project.
* **Taal van Source:** De taal van de broninhoud.
* **Taal van het Doel:** De taal waarin de inhoud wordt vertaald.
* **Vertaalmethode:** Uitgezochte Menselijke Vertaling om erop te wijzen dat de vertaling manueel moet worden uitgevoerd.

1. Klik op de werkbalk van de projectenconsole op Maken.
1. Selecteer het malplaatje van het Project van de Vertaling en klik dan daarna.
1. Voer waarden in voor de eigenschappen Standaard.
1. Klik op Geavanceerd en geef waarden op voor de eigenschappen die betrekking hebben op vertaling.
1. Klik op Maken. Klik in het bevestigingsvak op Gereed om terug te keren naar de projectenconsole of klik op Project openen om het project te openen en te beheren.

## Een vertaaltaak exporteren {#exporting-a-translation-job}

U kunt de inhoud van een vertaalbaan downloaden, bijvoorbeeld, om naar een vertaalleverancier te verzenden die niet met AEM via een schakelaar geïntegreerd is, of de inhoud te herzien.

1. Klik in het keuzemenu van het onderdeel Vertaal taak op Exporteren.
1. Klik in het dialoogvenster Exporteren op Geëxporteerd bestand downloaden en gebruik indien nodig het dialoogvenster van de webbrowser om het bestand op te slaan.
1. Klik in het dialoogvenster Exporteren op Sluiten.

## Een vertaaltaak importeren {#importing-a-translation-job}

U kunt vertaalde inhoud bijvoorbeeld importeren in AEM, wanneer uw vertaalbureau de inhoud naar u stuurt omdat deze niet is geïntegreerd met AEM via een connector.

1. Klik in het keuzemenu van het onderdeel Vertaal taak op Importeren.
1. Selecteer in het dialoogvenster van de webbrowser het bestand dat u wilt importeren.
1. Klik in het dialoogvenster Importeren op Sluiten.
