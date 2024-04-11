---
title: Inhoud voorbereiden voor vertaling
description: Leer hoe u inhoud voorbereidt voor vertaling in Adobe Experience Manager.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 81978733-89a6-4436-bcf1-4bde962ed54f
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Inhoud voorbereiden voor vertaling{#preparing-content-for-translation}

Meertalige websites bieden over het algemeen inhoud in meerdere talen. De site is gemaakt in één taal en wordt vervolgens vertaald in andere talen. In het algemeen bestaan meertalige sites uit vertakkingen van pagina&#39;s, waarbij elke vertakking de pagina&#39;s van de site in een andere taal bevat.

De voorbeeldsite voor demo-demo bevat verschillende taalvertakkingen en gebruikt de volgende structuur:

```xml
/content
    |- geometrixx
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Elke taalvertakking van een site wordt een taalkopie genoemd. De hoofdpagina van een taalkopie, ook wel de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. Bijvoorbeeld: `/content/geometrixx/fr` Dit is de hoofdtaalkennis van de Franse taalkopie. Taalkopieën moeten een [correct gevormde taalwortel](/help/sites-administering/tc-prep.md#creating-a-language-root) zodat de juiste taal wordt gebruikt wanneer vertalingen van een bronsite worden uitgevoerd.

De taalkopie waarvoor u oorspronkelijk site-inhoud hebt gemaakt, is de hoofdtaal. De taalmaster is de bron die in andere talen wordt vertaald.

Gebruik de volgende stappen om uw site voor te bereiden op vertaling:

1. Maak de hoofdmap van de taal van het stramien. De hoofdtaalsite van de demo-site Engelse Geometrixx is bijvoorbeeld /content/geometrixx/en. Zorg ervoor dat de taalwortel correct volgens de informatie in wordt gevormd [Een hoofdmap voor talen maken](/help/sites-administering/tc-prep.md#creating-a-language-root).
1. Ontwerp de inhoud van uw taalstramien.
1. Maak de hoofdmap van elke taalkopie voor uw site. De Franse taalkopie van de voorbeeldsite Geometrixx is bijvoorbeeld /content/geometrixx/fr.

Nadat u de inhoud hebt voorbereid voor vertaling, kunt u automatisch ontbrekende pagina&#39;s maken in uw taalkopieën en bijbehorende vertaalprojecten. (Zie [Een vertaalproject maken](/help/sites-administering/tc-manage.md).) Voor een overzicht van het vertaalproces van de inhoud in AEM raadpleegt u [Inhoud vertalen voor meertalige websites](/help/sites-administering/translation.md).

## Een hoofdmap voor talen maken {#creating-a-language-root}

Maak een taalhoofdmap als de hoofdpagina van een taalkopie die de taal van de inhoud identificeert. Nadat u de taalwortel creeert, kunt u vertaalprojecten tot stand brengen die het taalexemplaar omvatten.

Als u de hoofdtaal wilt maken van de taal, maakt u een pagina en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. De taalcode moet een van de volgende notaties hebben:

* `<language-code>`De ondersteunde taalcode is bijvoorbeeld een tweelettercode zoals gedefinieerd in ISO-639-1. `en`.

* `<language-code>_<country-code>` of `<language-code>-<country-code>`De ondersteunde landcode is bijvoorbeeld een tweelettercode in kleine letters of hoofdletters, zoals gedefinieerd in ISO 3166, `en_US`, `en_us`, `en_GB`, `en-gb`.

U kunt beide indelingen gebruiken op basis van de structuur die u voor uw globale site hebt gekozen.  De hoofdpagina van de Franse taalkopie van de site Geometrixx heeft bijvoorbeeld `fr` als de eigenschap Name. Het bezit van de Naam wordt gebruikt als naam van de paginaknooppunt in de bewaarplaats, en bepaalt daarom de weg van de pagina. http://localhost:4502/content/geometrixx/fr.html)

In de volgende procedure wordt de voor aanrakingen geoptimaliseerde interface gebruikt om een taalkopie van een website te maken. Voor instructies die de klassieke gebruikersinterface gebruiken, raadpleegt u [Een taalbasis maken met de klassieke gebruikersinterface](/help/sites-administering/tc-lroot-classic.md).

1. Navigeer naar sites.
1. Klik op de site waarvoor u een taalkopie wilt maken.

   Als u bijvoorbeeld een taalkopie van de site Geometrixx Outdoors wilt maken, klikt u op Site Geometrixx Outdoors.

1. Klik op Maken en klik vervolgens op Pagina maken.

   ![chlimage_1-21](assets/chlimage_1-21a.png)

1. Selecteer de paginasjabloon en klik op Volgende.
1. Typ in het veld Naam de landcode in de notatie `<language-code>` of `<language-code>_<country-code>`, bijvoorbeeld `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Typ een titel voor de pagina.

   ![chlimage_1-22](assets/chlimage_1-22a.png)

1. Klik op Maken. Klik in het bevestigingsdialoogvenster op **Gereed** om naar de console van Plaatsen terug te keren, of **Openen** om de taalkopie te openen.

## De status van taalwortels bekijken {#seeing-the-status-of-language-roots}

De interface die is geoptimaliseerd voor aanrakingen biedt een paneel Referenties met een lijst van taalwortels die zijn gemaakt.

![chlimage_1-23](assets/chlimage_1-23a.png)

In de volgende procedure wordt de geoptimaliseerde interface voor aanrakingen gebruikt om het deelvenster Verwijzingen voor een pagina te openen.

1. Selecteer in de Sites-console een pagina van de site en klik vervolgens op **Verwijzingen**.

   ![chlimage_1-24](assets/chlimage_1-24a.png)

1. Klik in het venster Referenties op **Taalkopieën**. In het deelvenster Taalkopieën worden de taalkopieën van de website weergegeven.
