---
title: Projecten beheren
seo-title: Projecten beheren
description: De projecten laten u uw project organiseren door middelen in één entiteit te groeperen die in de console van Projecten kan worden betreden en worden geleid
seo-description: De projecten laten u uw project organiseren door middelen in één entiteit te groeperen die in de console van Projecten kan worden betreden en worden geleid
uuid: ac937582-181f-429b-9404-3c71d1241495
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
discoiquuid: fb354c72-debb-4fb6-9ccf-56ff5785c3ae
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Projecten beheren{#managing-projects}

Met projecten kunt u uw project ordenen door bronnen in één entiteit te groeperen.

In de console van **Projecten** , hebt u toegang tot en voert actie op uw projecten:

![chlimage_1-255](assets/chlimage_1-255.png)

In Projecten, kunt u een project tot stand brengen, middelen met uw project associëren, en ook een project of verbindingen van het Middel schrappen. U kunt een tegel openen om de inhoud van de tegel weer te geven en items aan een tegel toe te voegen. In dit onderwerp worden deze procedures beschreven.

>[!NOTE]
>
>6.2 introduceerde de capaciteit om Projecten in omslagen te organiseren. Voor de pagina van Projecten, hebt u de capaciteit om een project of een omslag tot stand te brengen.
>
>Als er een map wordt gemaakt, gaat de gebruiker naar die map waar hij of zij een andere map of een project kan maken. Het helpt om projecten in omslagen te organiseren die op categorieën zoals productcampagnes, plaats, vertaaltalen, etc. worden gebaseerd.
>
>De projecten en omslagen kunnen in een lijstmening worden bekeken en ook worden gezocht.

>[!CAUTION]
>
>Voor gebruikers in projecten om andere gebruikers/groepen te zien terwijl het gebruiken van de functionaliteit van Projecten zoals het creëren van projecten, het creëren van taken/werkschema&#39;s, het zien van en het leiden van het team, die gebruikers moeten lees toegang op **/huis/gebruikers** en **/huis/groepen** hebben. De gemakkelijkste manier om dit uit te voeren is de **project-gebruikers** groep lees toegang tot **/huis/gebruikers** en **/huis/groepen**.

## Een project maken {#creating-a-project}

Uit de doos, verstrekt AEM deze malplaatjes om van te kiezen wanneer u een project creeert:

* Eenvoudig project
* Mediaproject
* Fotoproject van product
* Omzettingsproject

De procedure om een project tot stand te brengen is het zelfde van project aan project. Het verschil tussen de soorten projecten omvat beschikbare [gebruikersrollen](/help/sites-authoring/projects.md) en [werkschema](/help/sites-authoring/projects-with-workflows.md).  Een nieuw project maken:

1. Tik/klik in **Projecten** op **Maken** om de wizard Project **** maken te openen:
1. Selecteer een sjabloon. Eenvoudig project, Mediaproject, [Vertaalproject](/help/sites-administering/tc-manage.md)en Product Photo Shoot Product [zijn beschikbaar en klik op](/help/sites-authoring/managing-product-information.md) Volgende ****.

   ![chlimage_1-256](assets/chlimage_1-256.png)

1. Definieer de **titel** en de **beschrijving** en voeg desgewenst een **miniatuurafbeelding** toe. U kunt ook gebruikers toevoegen of verwijderen en tot welke groep zij behoren. Klik bovendien op **Geavanceerd** om een naam toe te voegen die wordt gebruikt in de URL.

   ![chlimage_1-257](assets/chlimage_1-257.png)

1. Tik/klik op **Maken**. De bevestiging vraagt of wilt u uw nieuw project openen of aan de console terugkeren.

### Middelen koppelen aan uw project {#associating-resources-with-your-project}

Aangezien de projecten u toelaten om middelen in één entiteit te groeperen, wilt u middelen aan uw project associëren. Deze bronnen worden **Tegels** genoemd. De typen bronnen die u kunt toevoegen, worden beschreven in [Projecttegels](/help/sites-authoring/projects.md#project-tiles).

Bronnen aan uw project koppelen:

1. Open uw project van de console van **Projecten** .
1. Tik/klik op **Naast elkaar** toevoegen en selecteer de tegel die u aan uw project wilt koppelen. U kunt meerdere typen tegels selecteren.

   ![chlimage_1-258](assets/chlimage_1-258.png)

   >[!NOTE]
   >
   >De tegels van het project die met een project kunnen worden geassocieerd worden beschreven in de tegels van het [Project.](/help/sites-authoring/projects.md#project-tiles)

1. Tik/klik op **Maken**. Uw bron is gekoppeld aan uw project en vanaf nu hebt u toegang tot deze bron vanuit uw project.

### Een project- of bronnenkoppeling verwijderen {#deleting-a-project-or-resource-link}

De zelfde methode wordt gebruikt om een project van de console of een verbonden middel van uw project te schrappen:

1. Navigeer naar de juiste locatie:

   * Om een project te schrappen gaat naar het hoogste niveau van de console van **Projecten** .
   * Om een middelverbinding binnen een project te schrappen, open uw project in de console van **Projecten** .

1. Ga selectiewijze door te klikken **Uitgezocht** en uw project of middelverbinding te selecteren.
1. Tik/klik op **Verwijderen**.

1. U moet de verwijdering bevestigen in een dialoogvenster. Indien bevestigd, wordt het project of de middelverbinding geschrapt. Tik/klik op **Deselecteren** om de selectiemodus te sluiten.

>[!NOTE]
>
>Wanneer u het project creeert en gebruikers aan de diverse rollen toevoegt, worden de groepen verbonden aan het project automatisch gecreeerd om bijbehorende toestemmingen te beheren. Bijvoorbeeld, zou een project genoemd Mijn project drie groepen **MijnProjecteigenaars**, **Mijn Projecteditors**, **Mijn projectwaarnemers** hebben. Als het project echter wordt verwijderd, worden deze groepen niet automatisch verwijderd. Een beheerder moet de groepen handmatig verwijderen in **Gereedschappen** > **Beveiliging** > **Groepen**.

### Items toevoegen aan een tegel {#adding-items-to-a-tile}

In sommige tegels wilt u mogelijk meerdere items toevoegen. U kunt bijvoorbeeld meer dan één workflow tegelijk uitvoeren of meer dan één ervaring.

Items toevoegen aan een tegel:

1. In **Projecten**, navigeer aan het project en klik Add + pictogram op de tegel u een punt aan wilt toevoegen.

   ![chlimage_1-259](assets/chlimage_1-259.png)

1. Voeg een item aan de tegel toe zoals u dat zou doen bij het maken van een nieuwe tegel. Projectielen worden [hier](/help/sites-authoring/projects.md#project-tiles)beschreven. In dit voorbeeld is een andere workflow toegevoegd.

   ![chlimage_1-260](assets/chlimage_1-260.png)

### Een tegel openen {#opening-a-tile}

Mogelijk wilt u zien welke items zijn opgenomen in een huidige tegel, of wilt u items wijzigen of verwijderen in de tegel.

Een tegel openen zodat u items kunt weergeven of wijzigen:

1. Tik in de projectenconsole op de ovalen (...) of klik op deze.

   ![chlimage_1-261](assets/chlimage_1-261.png)

1. In AEM worden de items in die tegel weergegeven. U kunt de selectiemodus activeren om de items te wijzigen of te verwijderen.

   ![chlimage_1-262](assets/chlimage_1-262.png)

## Projectstatistieken weergeven {#viewing-project-statistics}

Om projectstatistieken, in de console van **Projecten** te bekijken, klik **tonen de Mening** van Statistieken. Het voltooiingsniveau voor elk project wordt weergegeven. Klik **tonen opnieuw de Mening** van Statistieken om naar de console van **Projecten** te gaan.

![chlimage_1-263](assets/chlimage_1-263.png)

### Een projecttijdlijn weergeven {#viewing-a-project-timeline}

De projecttijdlijn biedt informatie over wanneer de elementen in het project het laatst zijn gebruikt. Als u de projecttijdlijn wilt weergeven, klikt of tikt u op de **tijdlijn**, gaat u naar de selectiemodus en selecteert u het project. Elementen worden weergegeven in het linkervenster. Klik/tik **Chronologie** om aan de console van **Projecten** terug te keren.

![chlimage_1-264](assets/chlimage_1-264.png)

### Actieve/Inactieve projecten weergeven {#viewing-active-inactive-projects}

Om tussen uw actieve en inactieve projecten, in de console van **Projecten** van een knevel te voorzien, klik de Actieve **Projecten** van de knevel. Als naast het pictogram een vinkje staat, worden de actieve projecten weergegeven.

![chlimage_1-265](assets/chlimage_1-265.png)

Als het pictogram een x naast heeft, toont het de inactieve projecten.

![chlimage_1-266](assets/chlimage_1-266.png)

## Projecten inactief of actief maken {#making-projects-inactive-or-active}

U kunt een project willen inactief maken als u het hebt voltooid maar u wilt nog de informatie over het project houden.

Een project inactief (of actief) maken:

1. In de console van **Projecten** , open uw project en vind dan de de informatietegel **van het** Project.

   >[!NOTE]
   Mogelijk moet u deze tegel toevoegen als deze nog niet in uw project staat. Zie Tegels [toevoegen](#adding-items-to-a-tile).

1. Tik/klik op **Bewerken**.
1. Wijzig de kiezer van **Actief** in **Inactief** (of andersom).

   ![chlimage_1-267](assets/chlimage_1-267.png)

1. Tik/klik op **Gereed** om uw wijzigingen op te slaan.

