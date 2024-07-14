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

Elke taalvertakking van een site wordt een taalkopie genoemd. De hoofdpagina van een taalkopie, ook wel de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. `/content/geometrixx/fr` is bijvoorbeeld de hoofdtaal van de Franse taalkopie. De exemplaren van de taal moeten a [ correct gevormde taalwortel ](/help/sites-administering/tc-prep.md#creating-a-language-root) gebruiken zodat de correcte taal wordt gericht wanneer de vertalingen van een bronplaats worden uitgevoerd.

De taalkopie waarvoor u oorspronkelijk site-inhoud hebt gemaakt, is de hoofdtaal. De taalmaster is de bron die in andere talen wordt vertaald.

Gebruik de volgende stappen om uw site voor te bereiden op vertaling:

1. Maak de hoofdmap van de taal van het stramien. De hoofdtaalsite van de demo-site Engelse Geometrixx is bijvoorbeeld /content/geometrixx/en. Zorg ervoor dat de taalwortel correct volgens de informatie in [ Creërend een Wortel van de Taal ](/help/sites-administering/tc-prep.md#creating-a-language-root) wordt gevormd.
1. Ontwerp de inhoud van uw taalstramien.
1. Maak de hoofdmap van elke taalkopie voor uw site. De Franse taalkopie van de voorbeeldsite Geometrixx is bijvoorbeeld /content/geometrixx/fr.

Nadat u de inhoud hebt voorbereid voor vertaling, kunt u automatisch ontbrekende pagina&#39;s maken in uw taalkopieën en bijbehorende vertaalprojecten. (Zie [ Creërend een Vertaal Project ](/help/sites-administering/tc-manage.md).) Voor een overzicht van het proces van de inhoudvertaling in AEM, zie [ Vertaalend Inhoud voor Meertalige Websites ](/help/sites-administering/translation.md).

## Een hoofdmap voor talen maken {#creating-a-language-root}

Maak een taalhoofdmap als de hoofdpagina van een taalkopie die de taal van de inhoud identificeert. Nadat u de taalwortel creeert, kunt u vertaalprojecten tot stand brengen die het taalexemplaar omvatten.

Als u de hoofdtaal wilt maken van de taal, maakt u een pagina en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. De taalcode moet een van de volgende notaties hebben:

* `<language-code>` de gesteunde taalcode is een twee-lettercode zoals die door ISO-639-1 wordt bepaald, bijvoorbeeld, `en`.

* `<language-code>_<country-code>` of `<language-code>-<country-code>` De ondersteunde landcode is een code van twee kleine letters of hoofdletters zoals gedefinieerd in ISO 3166, bijvoorbeeld `en_US` , `en_us` , `en_GB` , `en-gb` .

U kunt beide indelingen gebruiken op basis van de structuur die u voor uw globale site hebt gekozen.  De hoofdpagina van de Franse taalkopie van de site Geometrixx heeft bijvoorbeeld `fr` als de eigenschap Naam. Het bezit van de Naam wordt gebruikt als naam van de paginaknooppunt in de bewaarplaats, en bepaalt daarom de weg van de pagina. http://localhost:4502/content/geometrixx/fr.html)

In de volgende procedure wordt de voor aanrakingen geoptimaliseerde interface gebruikt om een taalkopie van een website te maken. Voor instructies die Klassieke UI gebruiken, zie [ Creërend een Wortel van de Taal Gebruikend Klassieke UI ](/help/sites-administering/tc-lroot-classic.md).

1. Navigeer naar sites.
1. Klik op de site waarvoor u een taalkopie wilt maken.

   Als u bijvoorbeeld een taalkopie van de site Geometrixx Outdoors wilt maken, klikt u op Site Geometrixx Outdoors.

1. Klik op Maken en klik vervolgens op Pagina maken.

   ![ chlimage_1-21 ](assets/chlimage_1-21a.png)

1. Selecteer de paginasjabloon en klik op Volgende.
1. Typ in het veld Naam de landcode in de notatie `<language-code>` of `<language-code>_<country-code>` , bijvoorbeeld `en` , `en_US` , `en_us` , `en_GB` , `en_gb` . Typ een titel voor de pagina.

   ![ chlimage_1-22 ](assets/chlimage_1-22a.png)

1. Klik op Maken. In de bevestigingsdialoogdoos, klik of **Gedaan** om aan de console van Plaatsen terug te keren, of **Open** om het taalexemplaar te openen.

## De status van taalwortels bekijken {#seeing-the-status-of-language-roots}

De interface die is geoptimaliseerd voor aanrakingen biedt een paneel Referenties met een lijst van taalwortels die zijn gemaakt.

![ chlimage_1-23 ](assets/chlimage_1-23a.png)

In de volgende procedure wordt de geoptimaliseerde interface voor aanrakingen gebruikt om het deelvenster Verwijzingen voor een pagina te openen.

1. Voor de console van Plaatsen, selecteer een pagina van de plaats en klik dan **Verwijzingen**.

   ![ chlimage_1-24 ](assets/chlimage_1-24a.png)

1. In het verwijzingenpaneel, klik {de Kopieën van 0} Taal **.** In het deelvenster Taalkopieën worden de taalkopieën van de website weergegeven.
