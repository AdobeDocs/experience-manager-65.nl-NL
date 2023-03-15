---
title: Startprocessen
seo-title: Starting processes
description: 'Hoe u de LiveCycle AEM Forms-werkruimte gebruikt: processen selecteren, notities en bijlagen toevoegen, conceptkopieën opslaan en toevoegen aan favorieten.'
seo-description: How to use LiveCycle AEM Forms workspace--select processes, add notes and attachments, save draft copies, and add to favorites.
uuid: a61da785-25b4-4482-bd72-02e250d35dc7
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c9d3f369-3744-41d5-b340-390ab7e03f36
exl-id: b2a6ba3a-0f4c-44b1-8f9a-c15c6fb8c305
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1343'
ht-degree: 0%

---

# Startprocessen {#starting-processes}

De werkruimte van AEM Forms organiseert processen door de categorieën die de beheerder of de procesontwerper opstelling. U kunt processen die u vaak gebruikt ook in uw categorie Favorieten plaatsen zodat u ze snel kunt vinden.

Wanneer u een proces start, moet u mogelijk een formulier invullen om een bedrijfsproces te starten dat door de AEM Forms-workflow wordt beheerd. Als in een formulier het proces Gegevens voorbereiden wordt gebruikt, kunnen sommige gegevens vooraf in een leeg formulier worden ingevuld wanneer een nieuw proces wordt gestart.

U wilt bijvoorbeeld een nieuwe computermonitor aanschaffen en daarom een proces starten dat *Inkooporder*. Wanneer u het proces start, wordt een formulier geopend en wordt u gevraagd om meer informatie over het item dat u wilt bestellen. Mogelijk zijn uw naam, werknemersnummer en de naam van de manager al vooraf ingevuld in het formulier. Wanneer u het verzoek indient, wordt een bedrijfsproces in werking gesteld. Gebaseerd op de procesdefinitie, leidt de server automatisch het verzoek aan uw manager. De taak begint in de te doen lijst van uw manager te verschijnen. Wanneer uw manager het verzoek goedkeurt, vormt het werkschema het verzoek aan de aankoopafdeling en verzendt u een e-mailbericht.

## Te starten processen selecteren {#selecting-processes-to-start}

U kunt een proces selecteren om het te beginnen of meer informatie over het te bekijken.

Wanneer u een proces selecteert om te starten, moet u mogelijk een formulier invullen dat aan dat proces is gekoppeld. Het verzenden van het formulier start het proces.

Forms in verschillende bestandsindelingen wordt ondersteund, waaronder Adobe PDF-, HTML- en SWF-bestanden. Een formulier kan er uitzien als een traditioneel afdrukbaar of op het web gebaseerd formulier, of kan u door een reeks wizardstijldeelvensters leiden om informatie te verzamelen.

Als het formulier en het proces dit toestaan, kunt u het formulier ook offline opslaan, het invullen en vervolgens verzenden om de taak te voltooien. Wanneer het formulier wordt verzonden, wordt uw e-mailclient gestart met het juiste e-mailadres van de server als het eindpunt van de e-mail is geconfigureerd. U kunt het ingevulde formulier vervolgens via e-mail naar de server verzenden.

Wanneer u een proces selecteert, worden het tabblad Formulier en het tabblad Details weergegeven. Als u tijdens het proces notities of bijlagen kunt toevoegen, worden ook het tabblad Bijlagen en Notities weergegeven. Als u de samenvatting-URL ook met het proces hebt gevormd, dan verschijnt het Summiere lusje ook. Op het tabblad Forms wordt het bijbehorende formulier weergegeven en op het tabblad Details wordt informatie weergegeven over de huidige taak en het proces waarvan het deel uitmaakt.

### Een bedrijfsproces starten {#start-a-business-process}

1. Selecteer een categorie in de lijst links op de pagina Proces starten. Alle processen tot u toegang hebt in de categorie verschijnen op het recht.

   >[!NOTE]
   >
   >Als het venster Categorieën is samengevouwen, klikt u op Categorieën openen linksboven in de AEM Forms-werkruimte om het venster te openen.

1. Selecteer een proces door op een taak te klikken. Het formulier dat aan het proces is gekoppeld, wordt geopend op het tabblad Formulier.

   Elk formulier in een proces heeft een unieke URL. U kunt de unieke URL gebruiken om de HTML Workspace met het specifieke proces en formulier rechtstreeks te starten. De opmaak van de URL is https://&lt;server>:&lt;port>/lc/libs/ws/index.html#/startprocess/&lt;applicationname>%2F&lt;processname>. De &lt;applicationname>%2F&lt;processname> tekenreeks is altijd URL-gecodeerd. Een voorbeeld-URL is http://localhost:8080/lc/libs/ws/index.html#/startprocess/MyApplication%2FNewProcess. De tekenreeks ApplicationName%2FPProcessName in het voorbeeld is URL-gecodeerd.

1. Vul het formulier in volgens de instructies die bij het formulier worden geleverd. Klik indien nodig op **Maximaliseren** om het zichtbare gebied van het formulier te vergroten.
1. Als het tabblad Bijlagen beschikbaar is, voegt u naar wens bijlagen toe.
1. Geef desgewenst notities op als het tabblad Notities beschikbaar is.
1. Voer een van de volgende stappen uit:

   * Klik op de knop Verzenden op het formulier als het formulier een knop Verzenden heeft.
   * Klik op Voltooien onder het formulier als het formulier geen knop Verzenden heeft.

   Het Beheer van het proces begint het proces en leidt de vorm aan te doen lijsten van de aangewezen mensen die de volgende taak in het proces moeten voltooien.

   Als u een formulier moet sluiten voordat het wordt verzonden en zonder dat de ingevoerde gegevens verloren gaan, slaat u een concept op en vult u het later in als dit tijdens het proces mogelijk is. Als het formulier en het proces dit toestaan, kunt u ook op **Off line** en later indienen vanuit Adobe® Reader® of Adobe® Acrobat® Professional of Acrobat Standard.

   >[!NOTE]
   >
   >De optie Offline is alleen beschikbaar voor PDF forms.

## Notities en bijlagen toevoegen {#adding-notes-and-attachments}

U kunt notities en bestandsbijlagen aan een proces toevoegen als dit tijdens het proces mogelijk is. U kunt machtigingen opgeven voor andere gebruikers die deelnemen aan het proces om de notities of bijlagen weer te geven, bij te werken en te verwijderen.

### Een notitie toevoegen {#add-a-note}

U kunt meerdere notities toevoegen, de geschreven notities bewerken en deze verwijderen. Elke notitie heeft een titel, een beschrijving en een toegangsmachtiging die eraan zijn gekoppeld. U kunt een van de volgende toegangsmachtigingen instellen voor een notitie:

* Alleen-lezen (de standaardmachtiging)
* Lezen/Bewerken/Verwijderen
* Lezen/Bewerken
* Lezen/Verwijderen
* Geen toegang

1. Open een taak en klik op de knop **Notities** als dit mogelijk is.
1. Typ een titel voor de notitie in het dialoogvenster **Titel** en typ de tekst van de notitie in het dialoogvenster **Opmerking** doos.
1. Selecteer **Machtigingen** niveau voor de nota voor andere gebruikers die aan het proces deelnemen.
1. Klikken **OK**. Een tekstbestand dat uw notitie bevat, wordt aan het formulier gekoppeld. U kunt een notitie bijwerken door erop te klikken en de tekst rechtstreeks te wijzigen. U kunt een notitie verwijderen door op de knop **Verwijderen** knop ![Afbeelding van een prullenbak](assets/icondelete.png) naast de notitie.

### Een bijlage toevoegen {#add-an-attachment}

U kunt ook opmerkingen over de bijlage toevoegen. U kunt een van de volgende toegangsmachtigingen instellen voor een bijlage:

* Alleen-lezen (de standaardmachtiging)
* Lezen/Bewerken/Verwijderen
* Lezen/Bewerken
* Lezen/Verwijderen
* Geen toegang

1. Klik op de knop **Bijlagen** en selecteert u **Bijlage**.
1. Klikken **Bladeren** om het bestand te selecteren dat u wilt bijvoegen.
1. Selecteer **Machtigingen** niveau voor de bijlage voor andere gebruikers die aan het proces deelnemen. Als u **Lezen**, kunnen andere gebruikers het bestand lokaal opslaan. Als u een van de bewerkingsmachtigingen selecteert, kunnen andere gebruikers ook een nieuw bestand uploaden om de bijlage te vervangen.
1. Klikken **OK**. Het bestand wordt aan het formulier gekoppeld. U kunt een bestand verwijderen door op de knop **Verwijderen** knop ![Afbeelding van een prullenbak](assets/icondelete.png) naast de bijlage.

## Concepten van formulieren opslaan {#saving-draft-copies-of-forms}

Als u een formulier later moet invullen en verzenden, kunt u een conceptkopie van een formulier opslaan zodat u uw bestaande werk niet verliest. Er worden conceptkopieën toegevoegd aan de categorie Concepten op de pagina Te doen.

Nadat u een conceptformulier opnieuw hebt geopend en verzonden, wordt het concept verwijderd uit de categorie Concepten.

Ook, kunt u werkruimte vormen om de informatie die door een gebruiker als ontwerp wordt ingegaan automatisch op te slaan. Zie voor meer informatie [Voorkeuren beheren](/help/forms/using/getting-started-livecycle-html-workspace.md).

>[!NOTE]
>
>De knop Opslaan is in sommige formulieren niet beschikbaar, afhankelijk van de procedure waaraan de knop is gekoppeld.

### Concepten opslaan {#save-a-draft-copy}

1. Klikken **Opslaan** in de linkerbenedenhoek van een willekeurig tabblad. Het formulier wordt toegevoegd aan de categorie Concepten op de pagina Aan. Alle wijzigingen die u in het formulier hebt aangebracht, worden opgeslagen.

### Concepten opnieuw openen {#reopen-a-draft-copy}

1. Selecteer op de pagina Aan-bewerking de optie **Concepten** en klik op de conceptkopie van het formulier.

   Als het formulier een reeks deelvensters bevat, moet u mogelijk naar het deelvenster gaan waar u de laatste sessie hebt beëindigd.

## Processen toevoegen aan de categorie Favorieten {#adding-processes-to-the-favorites-category}

U kunt elk proces toevoegen aan de categorie Favorieten. Door favorieten in te stellen, kunt u alle processen groeperen die u vaak in één enkele categorie begint zodat u hen snel kunt vinden.

>[!NOTE]
>
>Als u gewoonlijk processen start wanneer u de AEM Forms-werkruimte gebruikt, kunt u bij Locatie starten de categorie Favorieten automatisch weergeven wanneer u de AEM Forms-werkruimte start. Zie Voorkeuren beheren in [Aan de slag met de AEM Forms-werkruimte](/help/forms/using/getting-started-livecycle-html-workspace.md).

Als u een proces als favoriet wilt markeren, selecteert u de taak in de desbetreffende categorie en klikt u op de holle ster. De ster wordt gouden. Als u de markering van een proces als favoriet wilt opheffen, klikt u nogmaals op de gouden ster.
